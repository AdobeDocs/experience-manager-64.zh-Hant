---
title: 將AEM資產與Adobe InDesign Server整合
description: 瞭解如何將AEM Assets與InDesign Server整合。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 31d652ee04fe75e96f96c9ddc5a6f2c3c64bd630
workflow-type: tm+mt
source-wordcount: '1685'
ht-degree: 4%

---


# 將AEM Assets與Adobe InDesign Server {#integrating-aem-assets-with-indesign-server}整合

Adobe Experience Manager(AEM)資產使用：

* 一個代理，用於分配特定處理任務的負載。 Proxy是AEM例項，可與Proxy工作者通訊以完成特定工作，而其他AEM例項則可傳送結果。
* 用於定義和管理特定任務的代理工作器。

這些工作可以涵蓋各種任務；例如，使用Adobe InDesign Server處理檔案。

若要將檔案完整上傳至您使用Adobe InDesign建立的AEM資產，會使用Proxy。 這會使用代理工作者與Adobe InDesign Server通訊，其中[指令碼](https://www.adobe.com/devnet/indesign/documentation.html#idscripting)會執行以擷取中繼資料並產生AEM Assets的各種轉譯。 Proxy工作者可讓InDesign Server和雲端組態中的AEM例項進行雙向通訊。

>[!NOTE]
>
>Adobe InDesign提供兩種產品：
>
>* [InDesign](https://www.adobe.com/products/indesign.html)\
   >  這可讓您設計用於列印和／或數位散發的頁面版面。
   >
   >
* [InDesign Server](https://www.adobe.com/products/indesignserver.html)\
   >  此引擎可讓您根據您使用InDesign建立的內容，以程式設計方式建立自動化檔案。 它以服務的形式運行，為其[ExtendScript](https://www.adobe.com/devnet/scripting.html)引擎提供介面。\
   >  這些指令碼是以ExtendScript編寫，類似於javascript。 有關Indesign指令碼的資訊，請參見[https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting)。

>



## 抽取的運作方式{#how-the-extraction-works}

InDesign Server可與AEM Assets整合，讓使用InDesign(`.indd`)建立的檔案可以上傳、產生轉譯、提取&#x200B;*所有*&#x200B;媒體（例如視訊）並儲存為資產：

>[!NOTE]
>
>舊版AEM可以擷取XMP和縮圖，現在所有媒體都可以擷取。

1. 將您的`.indd`檔案上傳至AEM Assets。
1. 架構會透過SOAP（簡單物件存取通訊協定）將指令指令碼傳送至InDesign Server。

   此命令指令碼將：

   * 檢索`.indd`檔案。
   * 執行InDesign Server命令：

      * 會擷取結構、文字和任何媒體檔案。
      * 產生PDF和JPG轉譯。
      * 產生HTML和IDML轉譯。
   * 將產生的檔案張貼回AEM Assets。

   >[!NOTE]
   >
   >IDML是以XML為基礎的格式，可在InDesign檔案中轉譯&#x200B;*everything*。 它使用[Zip](https://www.techterms.com/definition/zip)壓縮儲存為壓縮包。
   >
   >如需詳細資訊，請參閱[Adobe InDesign Interchange Formats INX和IDML](http://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8)。

   >[!CAUTION]
   >
   >如果InDesign Server未安裝或未設定，則您仍可將`.indd`檔案上傳至AEM。 但產生的轉譯將限制為`png`和`jpeg`，您將無法產生`html`、`idml`或頁面轉譯。

1. 擷取和轉譯產生後：

   * 此結構會複製到`cq:Page`（轉譯類型）。
   * 擷取的文字和檔案會儲存在AEM Assets中。
   * 所有轉譯都儲存在AEM Assets、資產本身。

## 將InDesign Server與AEM {#integrating-the-indesign-server-with-aem}整合

若要整合InDesign Server以便與AEM Assets搭配使用，以及在設定Proxy後，您必須：

1. [安裝InDesign Server](#installing-the-indesign-server)。
1. 如果需要，請[設定AEM Assets Workflow](#configuring-the-aem-assets-workflow)。

   只有當預設值不適用於您的例項時，才需要這麼做。

1. 為InDesign Server](#configuring-the-proxy-worker-for-indesign-server)配置[代理工作器。

### 安裝InDesign Server {#installing-the-indesign-server}

若要安裝並啟動InDesign Server以搭配AEM使用：

1. 下載並安裝Adobe InDesign Server。

   >[!NOTE]
   >
   >InDesign Server（CS6和更新版本）。

1. 如有需要，您可自訂InDesign Server例項的設定。

1. 從命令行啟動伺服器：

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   這會在連接埠8080上以SOAP外掛程式監聽來啟動伺服器。 所有日誌消息和輸出都直接寫入命令窗口。

   >[!NOTE]
   >
   >如果要將輸出消息保存到檔案，則使用重定向；例如，在Windows下：
   >
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### 設定AEM Assets Workflow {#configuring-the-aem-assets-workflow}

AEM Assets具有預先設定的工作流程&#x200B;**DAM Update Asset**，其中具有數個InDesign的特定程式步驟：

* [媒體提取](#media-extraction)
* [頁面提取](#page-extraction)

此工作流程會以預設值設定，這些預設值可適用於您在各種作者例項上的設定（這是標準工作流程，因此在[編輯工作流程](/help/sites-developing/workflows-models.md#configuring-a-workflow-step)下可取得更多資訊）。 如果您使用預設值（包括SOAP埠），則不需要任何設定。

在設定後，上傳InDesign檔案至AEM Assets（透過任何一種常用方法）將觸發處理資產和準備各種轉譯所需的工作流程。 將`.indd`檔案上傳至AEM Assets以測試您的設定，以確認您看到IDS在`<*your_asset*>.indd/Renditions`下建立的不同轉譯

#### 媒體提取 {#media-extraction}

此步驟控制從`.indd`檔案抽取介質。

若要自訂，您可以編 **[!UICONTROL 輯]** 「媒體擷 **[!UICONTROL 取」步驟的「引]** 數」標籤。

![媒體擷取引數和指令碼路徑](assets/media_extraction_arguments_scripts.png)

媒體擷取引數和指令碼路徑

* **ExtendScript程式庫**:這是其他指令碼所需的簡單http get/post方法程式庫。

* **擴充指令碼**:您可以在此處指定不同的指令碼組合。如果您想要在InDesign Server上執行您自己的指令碼，請將指令碼儲存在`/apps/settings/dam/indesign/scripts`。

   有關Indesign指令碼的資訊，請參見[https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting)。

>[!CAUTION]
>
>請 勿變更ExtendScript程式庫。程式庫提供與Sling通訊所需的HTTP功能。 此設定會指定要傳送至Adobe InDesign Server以供其使用的程式庫。

由「媒體擷取」工作流程步驟執行的`ThumbnailExport.jsx`指令碼會產生。jpg格式的縮圖轉譯。 「處理縮圖」工作流程步驟會使用此轉譯，以產生AEM所需的靜態轉譯。

您可以設定「處理縮圖」工作流程步驟，以產生不同大小的靜態轉譯。 請確定您不會移除預設值，因為AEM Assets UI需要這些預設值。 最後，「刪除影像預覽轉譯」工作流程步驟會移除。jpg縮圖轉譯，因為不再需要它。

#### 頁面提取 {#page-extraction}

這會從擷取的元素建立AEM頁面。 擷取處理常式可用來從轉譯（目前為HTML或IDML）擷取資料。 然後，此資料會用於使用PageBuilder建立頁面。

若要自訂，您可以編輯「頁 **[!UICONTROL 面擷取]** 」步驟 **的「引** 數」標籤。

![chlimage_1-289](assets/chlimage_1-289.png)

* **頁面擷取處理常式**:從下拉式清單中，選取您要使用的處理常式。擷取處理常式會針對由相關人員選擇的特定轉譯 `RenditionPicker` 進行操作(請參 `ExtractionHandler` 閱API)。
依預設，IDML匯出擷取處理常式可供使用。 它對在MediaExtract步驟中生成的`IDML`轉譯進行操作。

* **頁面名稱**:指定您要指派給產生頁面的名稱。若保留空白，則名稱為「page」（若「page」已存在，則為衍生值）。

* **頁面標題**:指定您要指派給產生頁面的標題。

* **頁面根路徑**:結果頁面的根位置路徑。如果保留為空白，則會使用保存資產轉譯的節點。

* **頁面範本**:產生產生頁面時要使用的範本。

* **頁面設計**:產生產生頁面時要使用的頁面設計。

### 配置InDesign Server的代理工作器{#configuring-the-proxy-worker-for-indesign-server}

>[!NOTE]
>
>該工作器駐留在代理實例上。

1. 在「工具」控制台中，展開左窗格中的&#x200B;**[!UICONTROL 雲端服務配置]**。 然後展開&#x200B;**[!UICONTROL 雲端代理設定]**。

1. 連按兩下 **[!UICONTROL IDS工作器]** ，以開啟以進行設定。

1. 按一下&#x200B;**[!UICONTROL 編輯]**&#x200B;開啟配置對話框並定義所需設定：

   ![proxy_idsworkerconfig](assets/proxy_idsworkerconfig.png)

   * **IDS池**:用於與InDesign Server通訊的SOAP端點。您可以新增、移除和訂購項目。

1. 按一下&#x200B;**[!UICONTROL 確定]**&#x200B;保存。

### 配置Day CQ Link Externalizer {#configuring-day-cq-link-externalizer}

如果InDesign伺服器和AEM在不同的主機上執行，或是這兩種應用程式皆未在預設埠上執行，請設定&#x200B;**Day CQ Link Externalizer**&#x200B;以設定InDesign伺服器的主機名稱、埠和內容路徑。

1. 訪問URL `https://[AEM_server]:[port]/system/console/configMgr`中的Configuration Manager。
1. 找到設定 **[!UICONTROL Day CQ Link Externalizer]**，然後按一下 **[!UICONTROL Edit]** 圖示以開啟它。
1. 指定Indesign伺服器的主機名稱和內容路徑，然後按一下「儲存」。****

   ![chlimage_1-290](assets/chlimage_1-290.png)

### 為InDesign Server {#enabling-parallel-job-processing-for-indesign-server-s}啟用並行作業處理

您現在可以啟用IDS的並行作業處理。

首先，您需要確定InDesign Server可處理的最大並行作業數(`x`):

* 在單一多處理器機器上，InDesign Server可處理的並行作業(x)最大數目比執行IDS的處理器數目少1。
* 在多台電腦上運行IDS時，您需要計算可用處理器總數（即所有電腦上），然後減去電腦總數。

要配置並行IDS作業數：

1. 開啟Felix控制台的&#x200B;**[!UICONTROL Configurations]**&#x200B;頁籤；例如：

   `http://localhost:4502/system/console/configMgr`

1. 在以下位置選擇IDS處理隊列：

   `Apache Sling Job Queue Configuration`

1. 設定:

   * **[!UICONTROL 類型]** -  `Parallel`
   * **[!UICONTROL 最大並行作業]** -  `<*x*>` （如上所計算）

1. 儲存這些變更。
1. 若要啟用Adobe CS6和更新版本的多重作業支援，請勾選`com.day.cq.dam.ids.impl.IDSJobProcessor.name configuration`下方的`enable.multisession.name`核取方塊。
1. 通過將SOAP端點添加到IDS Worker配置](#configuring-the-proxy-worker-for-indesign-server)中，建立`*x*>` IDS工作器的[池。

   如果有多部電腦執行InDesign Server，請為每個電腦新增SOAP端點（每部電腦的處理器數-1）。

   >[!NOTE]
   >
   >使用工作池時，可以啟用IDS工作池的阻止清單。
   >
   >要執行此操作，請啟用`com.day.cq.dam.ids.impl.IDSJobProcessor.name`配置下的「enable.retry.name」複選框，該複選框將啟用IDS作業檢索。
   >
   >此外，在`com.day.cq.dam.ids.impl.IDSPoolImpl.name`配置下，為`max.errors.to.blacklist`參數設定正值，該值在將IDS從作業處理程式清單中禁止之前確定作業檢索的數量
   >
   >預設情況下，在以分鐘為單位的可配置(`retry.interval.to.whitelist.name`)時間後，IDS工作器將重新驗證。 如果線上找到該工作器，則會將其從被阻止的清單中刪除。

<!-- TBD: Make updates to configurations for allow and block list after product updates are done. See CQ-4298427.
-->

## 啟用對Adobe InDesign Server 10.0或更新版本{#enabling-support-for-indesign-server-or-higher}的支援

對於InDesign Server 10.0或更新版本，請執行下列步驟以啟用多階段作業支援。

1. 從[!DNL Assets]實例`https://[aem_server]:[port]/system/console/configMgr`開啟配置管理器。
1. 編輯配置`com.day.cq.dam.ids.impl.IDSJobProcessor.name`。
1. 選擇&#x200B;**[!UICONTROL ids.cc.enable]**&#x200B;選項，然後按一下&#x200B;**[!UICONTROL 保存]**。

>[!NOTE]
>
>對於與[!DNL Assets]整合的[!DNL InDesign Server]，請使用多核處理器，因為單核系統不支援整合所需的會話支援功能。

## 配置Experience Manager憑據{#configure-aem-credentials}

您可以變更從AEM例項存取InDesign伺服器的預設管理員認證（使用者名稱和密碼），而不會中斷與Adobe InDesign伺服器的整合。

1. 前往 `/etc/cloudservices/proxy.html`.
1. 在對話方塊中，指定新的使用者名稱和密碼。
1. 儲存認證。

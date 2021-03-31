---
title: 將AEM Assets與Adobe InDesign Server整合
description: 瞭解如何將AEM Assets與InDesign Server整合。
contentOwner: AG
feature: 發佈
role: 管理員
translation-type: tm+mt
source-git-commit: 4acf159ae1b9923a9c93fa15faa38c7f4bc9f759
workflow-type: tm+mt
source-wordcount: '1704'
ht-degree: 4%

---


# 將AEM Assets與Adobe InDesign Server整合{#integrating-aem-assets-with-indesign-server}

Adobe Experience Manager(AEM)資產用途：

* 一個代理，用於分配特定處理任務的負載。 代理是與代理工AEM作者通信以完成特定任務的實例，而其AEM他實例則用於傳遞結果。
* 用於定義和管理特定任務的代理工作器。

這些工作可以涵蓋各種任務；例如，使用Adobe InDesign Server來處理檔案。

若要將您使用Proxy建立的檔案完整上傳至AEM Assets。 這會使用代理工作器與Adobe InDesign Server通訊，其中[scripts](https://www.adobe.com/devnet/indesign/documentation.html#idscripting)會執行以擷取中繼資料並產生各種AEM Assets轉譯。 代理工作器啟用InDesign Server與雲配置中實AEM例之間的雙向通信。

>[!NOTE]
>
>Adobe InDesign有兩種產品：
>
>* [InDesign](https://www.adobe.com/products/indesign.html)\
   >  這可讓您設計用於列印和／或數位散發的頁面版面。
   >
   >
* [InDesign Server](https://www.adobe.com/products/indesignserver.html)\
   >  此引擎可讓您根據您使用InDesign建立的檔案，以程式設計方式建立自動化檔案。 它作為服務運行，提供其[ExtendScript](https://www.adobe.com/devnet/scripting.html)引擎的介面。\
   >  這些指令碼是在ExtendScript編寫，類似javascript。 有關Indesign指令碼的資訊，請參見[https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting)。

>



## 抽取的運作方式{#how-the-extraction-works}

InDesign Server可與AEM Assets整合，以便上傳使用InDesign(`.indd`)建立的檔案、產生轉譯、提取&#x200B;*所有*&#x200B;媒體（例如視訊）並儲存為資產：

>[!NOTE]
>
>舊版可AEM以摘取縮XMP圖，現在所有媒體都可摘取。

1. 將您的`.indd`檔案上傳至AEM Assets。
1. 框架通過SOAP（簡單對象訪問協定）向InDesign Server發送命令指令碼。

   此命令指令碼將：

   * 檢索`.indd`檔案。
   * 執行InDesign Server命令：

      * 會擷取結構、文字和任何媒體檔案。
      * 產生PDF和JPG轉譯。
      * 產生HTML和IDML轉譯。
   * 將產生的檔案發回AEM Assets。

   >[!NOTE]
   >
   >IDML是以XML為基礎的格式，可在InDesign檔案中轉譯&#x200B;*everypthing*。 它使用[Zip](https://www.techterms.com/definition/zip)壓縮儲存為壓縮包。
   >
   >如需詳細資訊，請參閱[Adobe InDesign交換格式INX和IDML](http://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8)。

   >[!CAUTION]
   >
   >如果未安裝或未配置InDesign Server，則仍可將`.indd`檔案上載到AEM。 但產生的轉譯將限制為`png`和`jpeg`，您將無法產生`html`、`idml`或頁面轉譯。

1. 擷取和轉譯產生後：

   * 此結構會複製到`cq:Page`（轉譯類型）。
   * 提取的文本和檔案儲存在AEM Assets。
   * 所有轉譯都儲存在AEM Assets，在資產本身。

## 將InDesign Server與AEM{#integrating-the-indesign-server-with-aem}整合

若要整合InDesign Server以與AEM Assets搭配使用，並在設定您的Proxy後，您必須：

1. [安裝InDesign Server](#installing-the-indesign-server)。
1. 如果需要，[配置AEM Assets工作流](#configuring-the-aem-assets-workflow)。

   只有當預設值不適用於您的例項時，才需要這麼做。

1. 為InDesign Server配置[代理工作器。](#configuring-the-proxy-worker-for-indesign-server)

### 安裝InDesign Server{#installing-the-indesign-server}

要安裝並啟動InDesign Server以便與AEM:

1. 下載並安裝Adobe InDesign Server。

   >[!NOTE]
   >
   >InDesign Server（CS6和更新版本）。

1. 如果需要，您可以自訂InDesign Server實例的配置。

1. 從命令行啟動伺服器：

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   這會在連接埠8080上以SOAP外掛程式監聽來啟動伺服器。 所有日誌消息和輸出都直接寫入命令窗口。

   >[!NOTE]
   >
   >如果要將輸出消息保存到檔案，則使用重定向；例如，在Windows下：
   >
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### 配置AEM Assets工作流{#configuring-the-aem-assets-workflow}

AEM Assets有預先設定的工作流程&#x200B;**DAM更新資產**，其中具有幾個專門用於InDesign的流程步驟：

* [媒體提取](#media-extraction)
* [頁面提取](#page-extraction)

此工作流程會以預設值設定，這些預設值可適用於您在各種作者例項上的設定（這是標準工作流程，因此在[編輯工作流程](/help/sites-developing/workflows-models.md#configuring-a-workflow-step)下可取得更多資訊）。 如果您使用預設值（包括SOAP埠），則不需要任何設定。

在設定後，將InDesign檔案上傳至AEM Assets（透過任何常用方法）將觸發處理資產和準備各種轉譯所需的工作流程。 將`.indd`檔案上傳至AEM Assets以測試您的設定，以確認您看到IDS在`<*your_asset*>.indd/Renditions`下建立的不同轉譯

#### 媒體提取 {#media-extraction}

此步驟控制從`.indd`檔案抽取介質。

若要自訂，您可以編 **[!UICONTROL 輯]** 「媒體擷 **[!UICONTROL 取」步驟的「引]** 數」標籤。

![媒體擷取引數和指令碼路徑](assets/media_extraction_arguments_scripts.png)

媒體擷取引數和指令碼路徑

* **ExtendScript圖書館**:這是其他指令碼所需的簡單http get/post方法程式庫。

* **擴充指令碼**:您可以在此處指定不同的指令碼組合。如果希望在InDesign Server上執行自己的指令碼，請將指令碼保存在`/apps/settings/dam/indesign/scripts`。

   有關InDesign指令碼的資訊，請參見[https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting)。

>[!CAUTION]
>
>請 勿變更ExtendScript程式庫。程式庫提供與Sling通訊所需的HTTP功能。 此設定指定要傳送至Adobe InDesign Server以供其使用的程式庫。

由「媒體擷取」工作流程步驟執行的`ThumbnailExport.jsx`指令碼會產生JPG格式的縮圖轉譯。 「處理縮圖」工作流程步驟會使用此轉譯來產生所需的靜態轉AEM譯。

您可以設定「處理縮圖」工作流程步驟，以產生不同大小的靜態轉譯。 請確定您不要移除預設值，因為這些預設值是AEM AssetsUI的必要項。 最後，「刪除影像預覽轉譯」工作流程步驟會移除。jpg縮圖轉譯，因為不再需要它。

#### 頁面提取 {#page-extraction}

這會從擷AEM取的元素建立頁面。 擷取處理常式可用來從轉譯（目前為HTML或IDML）擷取資料。 然後，此資料會用於使用PageBuilder建立頁面。

若要自訂，您可以編輯「頁 **[!UICONTROL 面擷取]** 」步驟 **的「引** 數」標籤。

![chlimage_1-289](assets/chlimage_1-289.png)

* **頁面擷取處理常式**:從下拉式清單中，選取您要使用的處理常式。擷取處理常式會針對由相關人員選擇的特定轉譯 `RenditionPicker` 進行操作(請參 `ExtractionHandler` 閱API)。
依預設，IDML匯出擷取處理常式可供使用。 它對在MediaExtract步驟中生成的`IDML`轉譯進行操作。

* **頁面名稱**:指定您要指派給產生頁面的名稱。若保留空白，則名稱為「page」（若「page」已存在，則為衍生值）。

* **頁面標題**:指定您要指派給產生頁面的標題。

* **頁面根路徑**:結果頁面的根位置路徑。如果保留為空白，則會使用保存資產轉譯的節點。

* **頁面範本**:產生產生頁面時要使用的範本。

* **頁面設計**:產生產生頁面時要使用的頁面設計。

### 配置InDesign Server{#configuring-the-proxy-worker-for-indesign-server}的代理工作器

>[!NOTE]
>
>該工作器駐留在代理實例上。

1. 在「工具」控制台中，展開左窗格中的「Cloud Services配置」。 ****&#x200B;然後展開&#x200B;**[!UICONTROL 雲端代理設定]**。

1. 連按兩下 **[!UICONTROL IDS工作器]** ，以開啟以進行設定。

1. 按一下&#x200B;**[!UICONTROL 編輯]**&#x200B;開啟配置對話框並定義所需設定：

   ![proxy_idsworkerconfig](assets/proxy_idsworkerconfig.png)

   * **IDS池**:用於與InDesign Server通信的SOAP端點。您可以新增、移除和訂購項目。

1. 按一下&#x200B;**[!UICONTROL 確定]**&#x200B;保存。

### 配置Day CQ Link Externalizer {#configuring-day-cq-link-externalizer}

如果InDesign Server和位於不AEM同的主機上，或者其中一個或兩個應用程式都未在預設埠上工作，請配置&#x200B;**Day CQ Link Externalizer**&#x200B;以設定InDesign Server的主機名、埠和內容路徑。

1. 訪問URL `https://[AEM_server]:[port]/system/console/configMgr`中的Configuration Manager。
1. 找到配置&#x200B;**[!UICONTROL Day CQ Link Externalizer]**。 按一下&#x200B;**[!UICONTROL 編輯]**&#x200B;以開啟。
1. 連結外部化設定可協助建立[!DNL Experience Manager]部署和[!DNL InDesign Server]的絕對URL。 使用&#x200B;**[!UICONTROL 域]**&#x200B;欄位指定[!DNL Adobe InDesign Server]的主機名和上下文路徑。 依照螢幕上的指示進行。 按一下「**[!UICONTROL 儲存]**」。

   ![連結外部化設定](assets/link-externalizer-config.png)

### 啟用InDesign Server{#enabling-parallel-job-processing-for-indesign-server}的並行作業處理

您現在可以啟用IDS的並行作業處理。

首先，您需要確定InDesign Server可以處理的並行作業的最大數量(`x`):

* 在單個多處理器機器上，InDesign Server可處理的並行作業(x)的最大數量比運行IDS的處理器數少1。
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
1. 若要啟用AdobeCS6和更新版本的多階段作業支援，請勾選`com.day.cq.dam.ids.impl.IDSJobProcessor.name configuration`下方的`enable.multisession.name`核取方塊。
1. 通過將SOAP端點添加到IDS Worker配置](#configuring-the-proxy-worker-for-indesign-server)中，建立`*x*>` IDS工作器的[池。

   如果有多台電腦運行InDesign Server，請為每個電腦添加SOAP端點（每台電腦的處理器數-1）。

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

## 啟用對Adobe InDesign伺服器10.0或更高版本{#enabling-support-for-indesign-server-or-higher}的支援

對於InDesign伺服器10.0或更高版本，請執行以下步驟以啟用多會話支援。

1. 從[!DNL Assets]實例`https://[aem_server]:[port]/system/console/configMgr`開啟配置管理器。
1. 編輯配置`com.day.cq.dam.ids.impl.IDSJobProcessor.name`。
1. 選擇&#x200B;**[!UICONTROL ids.cc.enable]**&#x200B;選項，然後按一下&#x200B;**[!UICONTROL 保存]**。

>[!NOTE]
>
>對於與[!DNL Assets]整合的[!DNL InDesign Server]，請使用多核處理器，因為單核系統不支援整合所需的會話支援功能。

## 配置Experience Manager憑據{#configure-aem-credentials}

您可以更改預設的管理員憑據（用戶名和密碼），以便從實例訪問InDesign伺服器，AEM而不中斷與Adobe InDesign伺服器的整合。

1. 前往 `/etc/cloudservices/proxy.html`.
1. 在對話方塊中，指定新的使用者名稱和密碼。
1. 儲存認證。

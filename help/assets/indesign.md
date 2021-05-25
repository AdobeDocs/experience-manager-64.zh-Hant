---
title: 整合AEM Assets與Adobe InDesign Server
description: 了解如何整合AEM Assets與InDesign Server。
contentOwner: AG
feature: 發佈
role: Administrator
exl-id: d80562f7-071c-460a-9c68-65f48d36fbd9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1703'
ht-degree: 3%

---

# 將AEM Assets與Adobe InDesign Server整合{#integrating-aem-assets-with-indesign-server}

Adobe Experience Manager(AEM)Assets使用：

* 分配特定處理任務的負載的代理。 Proxy是與Proxy工作人員通訊以完成特定任務的AEM例項，以及傳送結果的其他AEM例項。
* 定義和管理特定任務的代理工作。

這可以涵蓋各種任務；例如，使用Adobe InDesign Server來處理檔案。

若要將您使用AEM Assets Proxy建立的檔案完全上傳至Adobe InDesign。 這會使用代理工作程式與Adobe InDesign Server通訊，其中會執行[scripts](https://www.adobe.com/devnet/indesign/documentation.html#idscripting)以擷取中繼資料，並為AEM Assets產生各種轉譯。 在雲配置中，代理工作程式可啟用InDesign Server和AEM實例之間的雙向通信。

>[!NOTE]
>
>Adobe InDesign有兩種產品：
>
>* [InDesign](https://www.adobe.com/products/indesign.html)\
   >  這可讓您設計用於列印和/或數位分送的頁面配置。
   >
   >
* [InDesign Server](https://www.adobe.com/products/indesignserver.html)\
   >  此引擎使您能夠根據您使用InDesign建立的內容以寫程式方式建立自動化文檔。 其運作方式為提供其[ExtendScript](https://www.adobe.com/devnet/scripting.html)引擎介面的服務。\
   >  指令碼是在ExtendScript中撰寫，類似javascript。 有關Indesign指令碼的資訊，請參見[https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting)。

>



## 提取的運作方式{#how-the-extraction-works}

InDesign Server可與AEM Assets整合，以便上傳以InDesign(`.indd`)建立的檔案、產生轉譯、擷取&#x200B;*所有*&#x200B;媒體（例如視訊）並儲存為資產：

>[!NOTE]
>
>舊版AEM可擷取XMP和縮圖，現在可擷取所有媒體。

1. 將`.indd`檔案上傳至AEM Assets。
1. 框架通過SOAP（簡單對象訪問協定）將命令指令碼發送到InDesign Server。

   此命令指令碼將：

   * 檢索`.indd`檔案。
   * 執行InDesign Server命令：

      * 會擷取結構、文字和任何媒體檔案。
      * 會產生PDF和JPG轉譯。
      * 會產生HTML和IDML轉譯。
   * 將產生的檔案發回AEM Assets。

   >[!NOTE]
   >
   >IDML是以XML為基礎的格式，可在InDesign檔案中呈現&#x200B;*everything*。 會使用[Zip](https://www.techterms.com/definition/zip)壓縮，以壓縮套件形式儲存。
   >
   >有關詳細資訊，請參閱[Adobe InDesign交換格式INX和IDML](http://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8)。

   >[!CAUTION]
   >
   >如果未安裝或未設定InDesign Server，您仍可將`.indd`檔案上傳至AEM。 不過，產生的轉譯將限制為`png`和`jpeg`，您將無法產生`html`、`idml`或頁面轉譯。

1. 擷取和轉譯產生後：

   * 此結構會複製到`cq:Page`（轉譯類型）。
   * 擷取的文字和檔案會儲存在AEM Assets中。
   * 所有轉譯都會儲存在AEM Assets中、資產本身。

## 將InDesign Server與AEM {#integrating-the-indesign-server-with-aem}整合

若要整合InDesign Server以便與AEM Assets搭配使用，並在設定Proxy後，您需要：

1. [安裝InDesign Server](#installing-the-indesign-server)。
1. 如果需要，請[設定AEM Assets工作流程](#configuring-the-aem-assets-workflow)。

   只有在預設值不適合您的例項時，才需要這個選項。

1. 為InDesign Server](#configuring-the-proxy-worker-for-indesign-server)配置[代理工作器。

### 安裝InDesign Server{#installing-the-indesign-server}

若要安裝並啟動InDesign Server以搭配AEM使用：

1. 下載並安裝Adobe InDesign Server。

   >[!NOTE]
   >
   >InDesign Server（CS6及更新版本）。

1. 如有需要，您可以自訂InDesign Server例項的設定。

1. 從命令行啟動伺服器：

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   這會在連接埠8080上以SOAP外掛程式監聽來啟動伺服器。 所有日誌消息和輸出都直接寫入命令窗口。

   >[!NOTE]
   >
   >如果要將輸出消息保存到檔案，則使用重定向；例如，在Windows下：
   >
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### 設定AEM Assets工作流程{#configuring-the-aem-assets-workflow}

AEM Assets有預先設定的工作流程&#x200B;**DAM更新資產**，其中包含數個InDesign專屬的處理步驟：

* [媒體提取](#media-extraction)
* [頁面提取](#page-extraction)

此工作流程是以預設值設定的，這些預設值可針對您在各種製作執行個體上的設定進行調整（這是標準工作流程，因此可在[編輯工作流程](/help/sites-developing/workflows-models.md#configuring-a-workflow-step)下取得詳細資訊）。 如果您使用預設值（包括SOAP埠），則無需配置。

設定後，將InDesign檔案上傳至AEM Assets（透過任何一般方法）將觸發處理資產和準備各種轉譯所需的工作流程。 將`.indd`檔案上傳至AEM Assets以確認您看見ID在`<*your_asset*>.indd/Renditions`下建立的不同轉譯，借此測試您的設定

#### 媒體提取 {#media-extraction}

此步驟控制從`.indd`檔案中提取介質。

若要自訂，您可以編 **[!UICONTROL 輯]** 「媒體擷 **[!UICONTROL 取」步驟的「引]** 數」標籤。

![媒體擷取引數和指令碼路徑](assets/media_extraction_arguments_scripts.png)

媒體擷取引數和指令碼路徑

* **ExtendScript資料庫**:這是其他指令碼所需的簡單http get/post方法程式庫。

* **擴充指令碼**:您可以在此處指定不同的指令碼組合。如果希望在InDesign Server上執行自己的指令碼，請將指令碼保存在`/apps/settings/dam/indesign/scripts`。

   有關InDesign指令碼的資訊，請參見[https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting)。

>[!CAUTION]
>
>請 勿變更ExtendScript程式庫。程式庫提供與Sling通訊所需的HTTP功能。 此設定會指定要傳送至Adobe InDesign Server以供其使用的程式庫。

由「媒體擷取」工作流程步驟執行的`ThumbnailExport.jsx`指令碼會產生JPG格式的縮圖轉譯。 「處理縮圖」工作流程步驟會使用此轉譯，以產生AEM所需的靜態轉譯。

您可以設定「處理縮圖」工作流程步驟，以產生不同大小的靜態轉譯。 請確定您沒有移除預設值，因為AEM Assets UI需要這些預設值。 最後，「刪除影像預覽轉譯」工作流程步驟會移除.jpg縮圖轉譯，因為這已不再需要。

#### 頁面提取 {#page-extraction}

這會從擷取的元素建立AEM頁面。 擷取處理常式可用來從轉譯（目前為HTML或IDML）中擷取資料。 然後，系統會使用此資料建立使用PageBuilder的頁面。

若要自訂，您可以編輯「頁 **[!UICONTROL 面擷取]** 」步驟 **的「引** 數」標籤。

![chlimage_1-289](assets/chlimage_1-289.png)

* **頁面擷取處理常式**:從下拉式清單中，選取您要使用的處理常式。擷取處理常式會針對由相關人員選擇的特定轉譯 `RenditionPicker` 進行操作(請參 `ExtractionHandler` 閱API)。
預設情況下，可使用IDML導出提取處理程式。 它會對在MediaExtract步驟中產生的`IDML`轉譯進行操作。

* **頁面名稱**:指定要指派給產生頁面的名稱。若保留為空白，則名稱為「page」（若「page」已存在，則為衍生項目）。

* **頁面標題**:指定您要指派給產生頁面的標題。

* **頁面根路徑**:產生頁面的根位置路徑。如果保留為空白，系統會使用保留資產轉譯的節點。

* **頁面範本**:產生產生的頁面時要使用的範本。

* **頁面設計**:產生產生的頁面時要使用的頁面設計。

### 為InDesign Server{#configuring-the-proxy-worker-for-indesign-server}配置代理工作器

>[!NOTE]
>
>工作程式駐留在代理實例上。

1. 在「工具」控制台中，展開左窗格中的&#x200B;**[!UICONTROL Cloud Services配置]**。 然後展開&#x200B;**[!UICONTROL 雲代理配置]**。

1. 連按兩下 **[!UICONTROL IDS工作器]** ，以開啟以進行設定。

1. 按一下&#x200B;**[!UICONTROL 編輯]**&#x200B;以開啟配置對話框並定義所需設定：

   ![proxy_idsworkerconfig](assets/proxy_idsworkerconfig.png)

   * **IDS池**:用於與InDesign Server通信的SOAP端點。您可以新增、移除和訂購項目為必要項目。

1. 按一下&#x200B;**[!UICONTROL OK]**&#x200B;以儲存。

### 配置Day CQ連結外部化程式{#configuring-day-cq-link-externalizer}

如果InDesign Server和AEM位於不同的主機上，或其中一個或兩個應用程式在預設埠上無法正常工作，請配置&#x200B;**Day CQ Link Externalizer**&#x200B;以設定InDesign Server的主機名、埠和內容路徑。

1. 在URL `https://[AEM_server]:[port]/system/console/configMgr`訪問Configuration Manager。
1. 找到配置&#x200B;**[!UICONTROL Day CQ Link Externalizer]**。 按一下&#x200B;**[!UICONTROL 編輯]**&#x200B;以開啟。
1. 連結外部化程式設定有助於為[!DNL Experience Manager]部署和[!DNL InDesign Server]建立絕對URL。 使用&#x200B;**[!UICONTROL Domains]**&#x200B;欄位指定[!DNL Adobe InDesign Server]的主機名和上下文路徑。 按照螢幕上的說明操作。 按一下「**[!UICONTROL 儲存]**」。

   ![連結外部化程式設定](assets/link-externalizer-config.png)

### 啟用InDesign Server{#enabling-parallel-job-processing-for-indesign-server}的並行作業處理

您現在可以為ID啟用平行作業處理。

首先，您需要確定InDesign Server可以處理的最大並行作業數(`x`):

* 在單台多處理器電腦上，InDesign Server可處理的並行作業(x)的最大數量比運行IDS的處理器數少1。
* 在多台電腦上運行ID時，您需要計算可用處理器總數（即所有電腦上的），然後減去電腦總數。

要配置並行IDS作業的數量：

1. 開啟Felix Console的&#x200B;**[!UICONTROL Configurations]**&#x200B;標籤；例如：

   `http://localhost:4502/system/console/configMgr`

1. 在下方選取IDS處理佇列：

   `Apache Sling Job Queue Configuration`

1. 設定:

   * **[!UICONTROL 類型]**  -  `Parallel`
   * **[!UICONTROL 最大並行作業]**  -  `<*x*>` （如上所計算）

1. 儲存這些變更。
1. 要啟用AdobeCS6和更晚的多會話支援，請選中`com.day.cq.dam.ids.impl.IDSJobProcessor.name configuration`下的`enable.multisession.name`複選框。
1. 通過向IDS工作器配置](#configuring-the-proxy-worker-for-indesign-server)添加SOAP端點，建立[ ID工作器池。`*x*>`

   如果有多台電腦運行InDesign Server，請為每台電腦添加SOAP端點（每台電腦的處理器數–1）。

   >[!NOTE]
   >
   >使用工作池時，您可以啟用IDS工作池的封鎖清單。
   >
   >要執行此操作，請啟用`com.day.cq.dam.ids.impl.IDSJobProcessor.name`配置下的「enable.retry.name」複選框，該複選框可啟用IDS作業檢索。
   >
   >此外，在`com.day.cq.dam.ids.impl.IDSPoolImpl.name`配置下，為`max.errors.to.blacklist`參數設定一個正值，該值確定在從作業處理程式清單中禁止ID之前的作業檢索數
   >
   >預設情況下，在可設定(`retry.interval.to.whitelist.name`)的時間（以分鐘為單位）之後，IDS工作器會重新驗證。 如果聯機找到該工作，則會從阻止清單中刪除該工作。

<!-- TBD: Make updates to configurations for allow and block list after product updates are done. See CQ-4298427.
-->

## 啟用對Adobe InDesign伺服器10.0或更新版本{#enabling-support-for-indesign-server-or-higher}的支援

對於InDesign伺服器10.0或更高版本，請執行以下步驟以啟用多會話支援。

1. 從您的[!DNL Assets]實例`https://[aem_server]:[port]/system/console/configMgr`中開啟Configuration Manager。
1. 編輯配置`com.day.cq.dam.ids.impl.IDSJobProcessor.name`。
1. 選擇&#x200B;**[!UICONTROL ids.cc.enable]**&#x200B;選項，然後按一下&#x200B;**[!UICONTROL 保存]**。

>[!NOTE]
>
>對於與[!DNL Assets]的[!DNL InDesign Server]整合，請使用多核處理器，因為單核系統不支援整合所需的會話支援功能。

## 配置Experience Manager憑據{#configure-aem-credentials}

您可以變更從AEM例項存取InDesign伺服器的預設管理員憑證（使用者名稱和密碼），而不會中斷與Adobe InDesign伺服器的整合。

1. 前往 `/etc/cloudservices/proxy.html`.
1. 在對話方塊中，指定新的使用者名稱和密碼。
1. 儲存憑證。

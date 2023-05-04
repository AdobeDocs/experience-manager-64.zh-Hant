---
title: 整合 [!DNL Experience Manager] 使用Adobe InDesign Server的資產
description: 了解如何整合 [!DNL Experience Manager] 具有InDesign Server的資產。
contentOwner: AG
feature: Publishing
role: Admin
exl-id: d80562f7-071c-460a-9c68-65f48d36fbd9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1710'
ht-degree: 4%

---

# 整合資產與Adobe InDesign Server {#integrating-aem-assets-with-indesign-server}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets使用：

* 分配特定處理任務的負載的代理。 代理是 [!DNL Experience Manager] 與代理工作人員通信以完成特定任務的實例，以及 [!DNL Experience Manager] 執行個體來傳送結果。
* 定義和管理特定任務的代理工作。

這可以涵蓋各種任務；例如，使用Adobe InDesign Server來處理檔案。

若要將檔案完全上傳至 [!DNL Experience Manager] 您使用Adobe InDesign Proxy建立的資產已使用。 這會使用代理工作程式來與Adobe InDesign Server通訊， [指令碼](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) 執行以擷取中繼資料，並為 [!DNL Experience Manager] 資產。 代理工作器可啟用InDesign Server與 [!DNL Experience Manager] 雲端設定中的例項。

>[!NOTE]
>
>Adobe InDesign有兩種產品：
>
>* [InDesign](https://www.adobe.com/products/indesign.html)\
   >  這可讓您設計用於列印和/或數位分送的頁面配置。
>
>* [InDesign Server](https://www.adobe.com/products/indesignserver.html)\
   >  此引擎使您能夠根據您使用InDesign建立的內容以寫程式方式建立自動化文檔。 它作為一種服務，為它提供介面 [ExtendScript](https://www.adobe.com/devnet/scripting.html) 引擎。\
   >  指令碼是以類似JavaScript的ExtendScript撰寫。 如需Adobe InDesign指令碼的相關資訊，請參閱 [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).
>


## 提取的運作方式 {#how-the-extraction-works}

InDesign Server可與 [!DNL Experience Manager] 資產，讓檔案以InDesign( `.indd`)、產生轉譯、 *all* 擷取的媒體（例如視訊）並儲存為資產：

>[!NOTE]
>
>舊版 [!DNL Experience Manager] 能擷取XMP和縮圖，現在可擷取所有媒體。

1. 上傳 `.indd` 檔案 [!DNL Experience Manager] 資產。
1. 框架通過SOAP（簡單對象訪問協定）將命令指令碼發送到InDesign Server。

   此命令指令碼將：

   * 擷取 `.indd` 檔案。
   * 執行InDesign Server命令：

      * 會擷取結構、文字和任何媒體檔案。
      * PDF和JPG轉譯會產生。
      * HTML和IDML轉譯會產生。
   * 將產生的檔案發佈回 [!DNL Experience Manager] 資產。

   >[!NOTE]
   >
   >IDML是以XML為基礎的格式，可轉譯 *一切* 在InDesign檔案中。 會以壓縮套件的形式儲存，使用 [郵遞區號](https://www.techterms.com/definition/zip) 壓縮。
   >
   >請參閱 [Adobe InDesign Interchange Formats INX和IDML](https://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8) 以取得更多資訊。

   >[!CAUTION]
   >
   >如果未安裝或未設定InDesign Server，您仍可上傳 `.indd` 檔案 [!DNL Experience Manager]. 不過，產生的轉譯將限制為 `png` 和 `jpeg`，您將無法產生 `html`, `idml` 或頁面轉譯。

1. 擷取和轉譯產生後：

   * 該結構被複製到 `cq:Page` （轉譯類型）。
   * 擷取的文字和檔案會儲存在 [!DNL Experience Manager] 資產。
   * 所有轉譯都儲存在 [!DNL Experience Manager] 資產，在資產本身。

## 將InDesign Server與 [!DNL Experience Manager] {#integrating-the-indesign-server-with-aem}

整合InDesign Server以便與 [!DNL Experience Manager] 資產和設定Proxy後，您需要：

1. [安裝InDesign Server](#installing-the-indesign-server).
1. 如果需要， [設定 [!DNL Experience Manager] Assets工作流程](#configuring-the-aem-assets-workflow).

   只有在預設值不適合您的例項時，才需要這個選項。

1. 設定 [代理工作InDesign Server](#configuring-the-proxy-worker-for-indesign-server).

### 安裝InDesign Server {#installing-the-indesign-server}

安裝並啟動InDesign Server以用於 [!DNL Experience Manager]:

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

### 設定 [!DNL Experience Manager] Assets工作流程 {#configuring-the-aem-assets-workflow}

[!DNL Experience Manager] 資產具有預先設定的工作流程 **DAM更新資產**，此功能有數個具體的處理步驟供InDesign:

* [媒體提取](#media-extraction)
* [頁面提取](#page-extraction)

此工作流程會設定預設值，這些值可針對您在各種製作例項上的設定進行調整(這是標準工作流程，因此可在下方取得詳細資訊 [編輯工作流程](/help/sites-developing/workflows-models.md#configuring-a-workflow-step))。 如果您使用預設值（包括SOAP埠），則無需配置。

設定後，將InDesign檔案上傳至 [!DNL Experience Manager] 資產（透過任何一般方法）會觸發處理資產和準備各種轉譯所需的工作流程。 上傳 `.indd` 檔案 [!DNL Experience Manager] 資產，確認您在 `<*your_asset*>.indd/Renditions`

#### 媒體提取 {#media-extraction}

此步驟可控制從 `.indd` 檔案。

若要自訂，您可以編 **[!UICONTROL 輯]** 「媒體擷 **[!UICONTROL 取」步驟的「引]** 數」標籤。

![媒體擷取引數和指令碼路徑](assets/media_extraction_arguments_scripts.png)

媒體擷取引數和指令碼路徑

* **ExtendScript資料庫**:這是其他指令碼所需的簡單http get/post方法程式庫。

* **擴充指令碼**:您可以在此處指定不同的指令碼組合。 如果您希望在InDesign Server上執行自己的指令碼，請將指令碼儲存在 `/apps/settings/dam/indesign/scripts`.

   如需InDesign指令碼的相關資訊，請參閱 [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

>[!CAUTION]
>
>請 勿變更ExtendScript程式庫。程式庫提供與Sling通訊所需的HTTP功能。 此設定會指定要傳送至Adobe InDesign Server以供其使用的程式庫。

此 `ThumbnailExport.jsx` 由「媒體擷取」工作流程步驟執行的指令碼會產生JPG格式的縮圖轉譯。 「處理縮圖」工作流程步驟會使用此轉譯，以產生所需的靜態轉譯 [!DNL Experience Manager].

您可以設定「處理縮圖」工作流程步驟，以產生不同大小的靜態轉譯。 請確定您不會移除預設值，因為 [!DNL Experience Manager] 資產UI。 最後，「刪除影像預覽轉譯」工作流程步驟會移除.jpg縮圖轉譯，因為這已不再需要。

#### 頁面提取 {#page-extraction}

這會建立 [!DNL Experience Manager] 頁面。 擷取處理常式可用來從轉譯(目前為HTML或IDML)中擷取資料。 然後，系統會使用此資料建立使用PageBuilder的頁面。

若要自訂，您可以編輯「頁 **[!UICONTROL 面擷取]** 」步驟 **的「引** 數」標籤。

![chlimage_1-289](assets/chlimage_1-289.png)

* **頁面擷取處理常式**:從下拉式清單中，選取您要使用的處理常式。 擷取處理常式會針對由相關人員選擇的特定轉譯 `RenditionPicker` 進行操作(請參 `ExtractionHandler` 閱API)。
預設情況下，可使用IDML導出提取處理程式。 其運作於 `IDML` 在MediaExtract步驟中產生的轉譯。

* **頁面名稱**:指定要指派給產生頁面的名稱。 若保留為空白，則名稱為「page」（若「page」已存在，則為衍生項目）。

* **頁面標題**:指定您要指派給產生頁面的標題。

* **頁面根路徑**:產生頁面的根位置路徑。 如果保留為空白，系統會使用保留資產轉譯的節點。

* **頁面範本**:產生產生的頁面時要使用的範本。

* **頁面設計**:產生產生的頁面時要使用的頁面設計。

### 配置代理工作器以InDesign Server {#configuring-the-proxy-worker-for-indesign-server}

>[!NOTE]
>
>工作程式駐留在代理實例上。

1. 在工具主控台中，展開 **[!UICONTROL Cloud Services配置]** 中。 然後展開 **[!UICONTROL 雲端代理設定]**.

1. 連按兩下 **[!UICONTROL IDS工作器]** ，以開啟以進行設定。

1. 按一下 **[!UICONTROL 編輯]** 要開啟「配置」對話框並定義所需的設定：

   ![proxy_idsworkerconfig](assets/proxy_idsworkerconfig.png)

   * **IDS池**:用於與InDesign Server通信的SOAP端點。 您可以新增、移除和訂購項目為必要項目。

1. 按一下 **[!UICONTROL 確定]** 儲存。

### 配置Day CQ Link Externalizer {#configuring-day-cq-link-externalizer}

若InDesign Server和 [!DNL Experience Manager] 位於不同的主機上，或者其中一個或兩個應用程式在預設埠上不工作，請配置 **Day CQ Link Externalizer** 設定InDesign Server的主機名、埠和內容路徑。

1. 在URL存取Configuration Manager `https://[AEM_server]:[port]/system/console/configMgr`.
1. 找出設定 **[!UICONTROL Day CQ Link Externalizer]**. 按一下 **[!UICONTROL 編輯]** 來開啟。
1. 連結外部化程式設定可協助為 [!DNL Experience Manager] 部署和 [!DNL InDesign Server]. 使用 **[!UICONTROL 網域]** 欄位，指定的主機名稱和內容路徑 [!DNL Adobe InDesign Server]. 按照螢幕上的說明操作。 按一下「**[!UICONTROL 儲存]**」。

   ![連結外部化程式設定](assets/link-externalizer-config.png)

### 為InDesign Server啟用並行作業處理 {#enabling-parallel-job-processing-for-indesign-server}

您現在可以為ID啟用平行作業處理。

首先，您需要確定並行作業的最大數量( `x`)InDesign Server可以處理：

* 在單台多處理器電腦上，InDesign Server可處理的並行作業(x)的最大數量比運行IDS的處理器數少1。
* 在多台電腦上運行ID時，您需要計算可用處理器總數（即所有電腦上的），然後減去電腦總數。

要配置並行IDS作業的數量：

1. 開啟 **[!UICONTROL 配置]** Felix Console的標籤；例如：

   `http://localhost:4502/system/console/configMgr`

1. 在下方選取IDS處理佇列：

   `Apache Sling Job Queue Configuration`

1. 設定:

   * **[!UICONTROL 類型]** - `Parallel`
   * **[!UICONTROL 最大並行作業數]** - `<*x*>` （如上文計算）

1. 儲存這些變更。
1. 要啟用對AdobeCS6和更晚的多會話支援，請檢查 `enable.multisession.name` 核取方塊 `com.day.cq.dam.ids.impl.IDSJobProcessor.name configuration`.
1. 建立 [&lt;池 `*x*>` 將SOAP端點新增至IDS工作器設定，以啟用IDS工作器](#configuring-the-proxy-worker-for-indesign-server).

   如果有多台電腦運行InDesign Server，請為每台電腦添加SOAP端點（每台電腦的處理器數–1）。

   >[!NOTE]
   >
   >使用工作池時，您可以啟用IDS工作池的封鎖清單。
   >
   >若要這麼做，請啟用 `com.day.cq.dam.ids.impl.IDSJobProcessor.name` 設定，可啟用IDS作業擷取。
   >
   >此外，在 `com.day.cq.dam.ids.impl.IDSPoolImpl.name` 設定，請為 `max.errors.to.blacklist` 參數，它確定在從作業處理程式清單中禁止ID之前的作業檢索數
   >
   >依預設，在可設定(`retry.interval.to.whitelist.name`)重新驗證IDS背景工作的分鐘數。 如果聯機找到該工作，則會從阻止清單中刪除該工作。

<!-- TBD: Make updates to configurations for allow and block list after product updates are done. See CQ-4298427.
-->

## 啟用對Adobe InDesign server 10.0或更新版本的支援 {#enabling-support-for-indesign-server-or-higher}

對於InDesign伺服器10.0或更高版本，請執行以下步驟以啟用多會話支援。

1. 從 [!DNL Assets] 執行個體 `https://[aem_server]:[port]/system/console/configMgr`.
1. 編輯設定 `com.day.cq.dam.ids.impl.IDSJobProcessor.name`.
1. 選擇 **[!UICONTROL ids.cc.enable]** ，然後按一下 **[!UICONTROL 儲存]**.

>[!NOTE]
>
>針對 [!DNL InDesign Server] 整合 [!DNL Assets]，請使用多核處理器，因為單核系統不支援整合所需的會話支援功能。

## 配置Experience Manager憑據 {#configure-aem-credentials}

您可以更改預設的管理員憑據（用戶名和密碼），以便從您的 [!DNL Experience Manager] 例項，而不中斷與Adobe InDesign伺服器的整合。

1. 前往 `/etc/cloudservices/proxy.html`.
1. 在對話方塊中，指定新的使用者名稱和密碼。
1. 儲存憑證。

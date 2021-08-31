---
title: Adobe Experience Manager 6.4的一般發行說明
seo-title: Release Notes
description: 'Adobe Experience Manager 6.4說明，概述發行資訊、新增功能、安裝方式和詳細的變更清單。 '
seo-description: Adobe Experience Manager 6.4 notes outlining the release information, what's new, how to install and detailed change lists.
uuid: 5a220301-2727-4078-ba19-4a2dbf9657f4
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 2be468e7-2b4e-4e04-881b-b9bdd1f55e57
exl-id: ee034595-2d2a-4887-86c4-6bf0770da6a2
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '2754'
ht-degree: 6%

---

# Adobe Experience Manager 6.4的一般發行說明 {#general-release-notes-for-adobe-experience-manager}

## 發行資訊 {#release-information}

| 產品 | Adobe Experience Manager |
|---|---|
| 版本 | 6.4 |
| 類型 | 主要版本 |
| 正式發行日期 | 2018 年 4 月 4 日 |
| 建議的更新 | 請參閱[AEM發行版本和更新](https://helpx.adobe.com/tw/experience-manager/aem-releases-updates.html) |

### Trivia {#trivia}

此版Adobe Experience Manager的發行週期從2017年4月27日開始，經過22次反覆品質保證和錯誤修正，並於2018年3月22日結束。 這一版發行中修正的客戶相關問題，包括加強與新功能，總共有 704 個。

Adobe Experience Manager 6.4自2018年4月4日起全面推出。

>[!NOTE]
>
>Adobe建議安裝最新的Service Pack，因為所有新功能套件僅透過[Service Pack](https://helpx.adobe.com/tw/experience-manager/maintenance-releases-roadmap.html)提供。

## 新功能 {#what-s-new}

Adobe Experience Manager 6.4 是 Adobe Experience Manager 6.3 程式碼庫的升級版本。此版本提供全新的增強功能、重要客戶修正、高優先順序的客戶增強功能，以及針對產品穩定化的一般錯誤修正。其中也包含大部分的Adobe Experience Manager 6.3 Feature Pack、Hotfix和Service Pack版本。

以下清單提供概觀，而後續頁面則列出完整詳細資訊。

### Experience Manager基礎 {#experience-manager-foundation}

[AEM Foundation](wcm-platform.md)中的更改的完整清單。

Adobe Experience Manager 6.4平台以更新版本的OSGi型架構（Apache Sling和Apache Felix）和Java Content Repository為基礎而建置：Apache Jackrabbit Oak 1.8.2。

快速入門使用Eclipse Jetty 9.3.22作為servlet引擎。

#### 使用者介面 {#user-interface}

UI已經過多種增強功能，讓工作效率更高，使用更輕鬆。

* [新內容樹](/help/sites-authoring/basic-handling.md#content-tree) 欄位，快速導覽階層。這會與清單檢視結合，還原傳統UI互動模型。
* 改善大型資料夾的卡片和清單檢視中的捲動體驗。
* [改善與搜尋結果的互動](/help/sites-authoring/search.md)  — 返回按鈕可還原先前的搜尋結果。
* [其他鍵盤快速鍵](/help/sites-authoring/keyboard-shortcuts.md)，用於大多數常見的動作，例如開啟特定邊欄、編輯、移動和刪除項目，或開啟屬性。
* [可停用鍵盤快速鍵](/help/sites-authoring/user-properties.md) （在「偏好設定」中啟用/停用）。
* [在7天後停止顯示所有](/help/sites-authoring/user-properties.md) UI相對的時間戳記（在「偏好設定」中設定預設值）。

如需這些功能的詳細資訊，請參閱[製作檔案](/help/sites-authoring/home.md) 。

>[!CAUTION]
>
>Adobe不打算對傳統UI進行進一步的增強。 AEM 6.4已包含傳統UI，而從舊版升級的客戶可繼續依原樣使用。 請注意，舊版UI仍完全受支援。 [了解詳情](/help/sites-deploying/ui-recommendations.md)。

#### 內容儲存庫 {#content-repository}

* 透過「線上修訂清除」更快速且更有效率地壓縮。 內部測試表明，新的尾部壓縮速度比AEM 6.3快10倍，而且與Online 6.3相比，IOPS更少，可以回收更多磁碟空間。這在運行線上修訂清除時，將導致效能影響更小。 如需詳細資訊，請參閱[檔案頁面](/help/sites-deploying/revision-cleanup.md#full-and-tail-compaction-modes)。

* MongoMK的持續修訂清除取代了排程的清除維護
* 改善檔案記錄檔的修訂清除效率

#### 搜尋與索引 {#search-indexing}

* 通過oak-run(CLI)對索引操作的增強支援：

   * 索引一致性檢查
   * 索引統計
   * 導入或導出索引配置
   * 重新索引

* 降低Lucene相關儲存庫的增長，以全面提高系統效能

如需詳細資訊，請造訪[本檔案頁面](/help/sites-deploying/indexing-via-the-oak-run-jar.md)。

#### 監控 {#monitoring}

* 新的[系統概述](/help/sites-administering/operations-dashboard.md#system-overview)提供了與效能相關的所有系統狀態和活動的快照視圖。
* 圍繞索引、查詢和維護的一組新的[運行狀況檢查](/help/sites-administering/operations-dashboard.md#health-checks)

#### 專案和工作流程 {#projects-and-workflows}

* 全新[工作流編輯器，用於建立和編輯工作流模型](/help/sites-developing/workflows-models.md)。

![screen_shot_2018-04-04at71143am](assets/screen_shot_2018-04-04at71143am.png)

#### 從舊版升級 {#upgrade-from-earlier-version}

* [向後相容性](/help/sites-deploying/backward-compatibility.md):6.4版中回溯相容的功能，可協助您的自訂程式碼在大多數情況下保持相容，並降低升級工作量。
* [升級複雜性評估](/help/sites-deploying/pattern-detector.md):全新模式偵測器工具，可在升級前評估升級的複雜性。
* [存放庫重新調整](/help/sites-deploying/repository-restructuring.md):大幅重組（主要是/etc），以便更輕鬆地升級並促進實施最佳做法
* 有關升級的更一般資訊，請參閱[此頁](/help/sites-deploying/upgrade.md)以了解更多詳細資訊。

### Experience Manager網站 {#experience-manager-sites}

[AEM Sites和Add-ons](sites.md)中變更的完整清單。

#### 流暢的體驗 {#fluid-experiences}

2017年初推出的流暢體驗，以內容片段、體驗片段和內容服務為後盾，是邁向多管道優先內容管理的開端。 AEM 6.4大幅擴展了每個區域：

**[內容片段](/help/assets/content-fragments.md)**

6.4中的新增功能為視覺化[內容模型](/help/assets/content-fragments-models.md)編輯器，以及新的[可設定元件](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/content-fragment-component.html)，可提供彈性的HTML輸出，以及要納入內容服務的JSON。

**體驗片段**

有了「建置區塊」功能，以相同內容但不同版面的片段建立變體現在更有效率。 除了將體驗片段傳送至Facebook和Pinterest之外，現在也能以優惠方式將它們傳送至Adobe Target。

**Content Services**

Sling模型匯出工具和核心元件的各種增強功能都包含在內，提供強大的JSON輸出，將內容內嵌在行動應用程式中，並透過單頁應用程式建立體驗。

#### 讓網站更快建置 {#gettings-sites-built-quicker}

AEM 6.4完成對下一代元件模型的轉換。 AEM 6.3中推出的核心元件概念，現已與樣式系統結合，提供建立新網站和擴充現有網站的有效方式。

若要了解如何最佳運用新元件模型，建議的教學課程：[AEM Sites快速入門 — WKND教學課程](https://docs.adobe.com/content/help/zh-Hant/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)

#### Screens附加元件 {#screens-add-on}

AEM Screens代表的是在所有行銷管道（包括數位看板和資訊站網路）中提供一致的訊息。 AEM 6.4新增在Microsoft Windows和Google Chrome OS硬體上執行Signage Player的支援。 此外，還提供了對遠程設備管理和計畫（通道組）的增強功能。

如需Screens更新的詳細資訊，請參閱[AEM Screens使用手冊](https://docs.adobe.com/content/help/zh-Hant/experience-manager-screens/user-guide/aem-screens-introduction.html)。

### Experience Manager社群 {#experience-manager-communities}

AEM 6.4為Communities新增了許多新功能和增強功能。 [AEM Communities](communities-release-notes.md)提供完整的變更清單。 此版本的重點為：

#### 協調的增強功能 {#enhancements-to-moderation}

**自動垃圾郵件檢測**

提供新的垃圾郵件偵測引擎，可篩選掉社群網站和群組上不想要的使用者產生的內容。 一旦從系統/控制台/configMgr啟用，它就會根據預先定義的一組垃圾郵件字詞，將用戶生成的內容標籤為垃圾郵件。 要了解有關垃圾郵件檢測引擎的詳細資訊，請參閱[自動生成內容的社區用戶](/help/communities/moderate-ugc.md#spam-detection)。

![垃圾郵件檢測](assets/spamdetection.png)

**QnA的新篩選器**

已將名為「已回答」和「未回答」的新篩選器新增至大量協調控制台，以篩選QnA問題。 要了解「已應答」和「未應答」狀態篩選器的工作方式，請參閱[批量調節用戶生成的內容](/help/communities/moderation.md#main-pars-note-521961797)。

**書籤協調篩選器**

已提供在協調控制台上為預先定義的協調篩選建立書籤的功能。 這些篩選器會附加至URL字串的結尾，因此可以共用、重複使用，並在稍後重新檢視。 了解如何在[大量協調控制台](/help/communities/moderation.md#main-pars-note-429176623)中將篩選器加入書籤。

#### 刪除UGC和使用者設定檔 {#delete-ugc-and-user-profiles}

AEM 6.4 Communities會公開[現成可用的API](/help/communities/user-ugc-management-service.md)和範例[servlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-ugc-management-servlet)，讓一般使用者能夠控制其資料。 這些API也可讓資料處理與資料控管組織提供EU GDPR法規遵循要求。

#### 增強網站和群組管理 {#enhancements-to-site-and-group-management}

**在單一步驟中建立多地區設定群組**

提供了在單次操作中建立多語言組的功能。 若要建立這類群組，使用者可從Sites主控台導覽至所需社群網站的「群組集合」 。 建立群組，並在「社群群組範本」頁面中指定所需的語言。 若要深入了解此功能，請參閱[社群群組主控台](/help/communities/groups.md)。

![多語種組](assets/multilingualgroup.png)

**[按一下即可刪除社群網站和群組](/help/communities/groups.md)**

從全域導覽時，刪除圖示現在可在個別網站和群組上使用。 使用此圖示會刪除與網站或群組相關聯的所有項目和內容，並移除所有使用者關聯。 要了解有關此功能的詳細資訊，請參閱[管理社群網站](/help/communities/create-site.md#main-pars-text-fe17)和[管理社群群組](/help/communities/groups.md#main-pars-text-5e8c)。

#### 啟用的增強功能 {#enhancements-to-enablement}

現在，群組內可使用指派和目錄功能。 這可讓學習內容針對特定一組目標社群成員建立、管理和發佈。 要了解有關啟用社區組的詳細資訊，請參閱[管理啟用資源](/help/communities/resource.md)。

![assignmentcatalog](assets/assignmentcatalog.png)

### Experience Manager資產 {#experience-manager-assets}

AEM 6.4為Assets提供數項新功能和增強功能，包括全新、改良的CreativeCloud整合、重要的人工智慧創新、改善的中繼資料管理、報表增強功能，以及整體使用者體驗改善。 [AEM Assets](assets.md)中可用更改的完整清單。 此版本的重點為：

**Adobe資產連結**

AdobeCreative Cloud中的企業資產連結可簡化創意人員與行銷人員在內容建立程式中的協作。 這是Creative Cloud中企業的新原生功能，可將Photoshop CC、Illustrator CC和InDesignCC連接至AEM ，創意人員無需離開其首選工具。

若要深入了解此功能、必要條件及存取方式，請參閱[Adobe資產連結](https://www.adobe.com/tw/creativecloud/business/enterprise/adobe-asset-link.html)。

![adobe_asset_link](assets/adobe_asset_link.png)

**AEM 桌面應用程式**

AEM案頭應用程式已更新至與AEM 6.4相容的1.8版。AEM案頭應用程式的完整變更清單位於專用的[AEM案頭應用程式發行說明](https://docs.adobe.com/content/help/zh-Hant/experience-manager-desktop-app/using/release-notes.html)檔案中。

自AEM 6.3版推出以來的改良功能包括可在背景上傳階層式資料夾、使用新UI來監控資產背景操作、增強快取、建立網路和登入，以及整體穩定性改善。 本檔案也包含[最佳實務指南](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html)。

**Adobe Sensei服務**

新功能包括增強智慧標籤，可學習客戶業務分類法，使用客戶專屬標籤自動標籤數位資產，以及智慧翻譯搜尋，這可透過即時翻譯搜尋詞來改善多種語言的探索能力。 若要深入了解此功能，請參閱[增強智慧標籤](/help/assets/enhanced-smart-tags.md)。

![enhanced_smart_tags2](assets/enhanced_smart_tags2.png)

**中繼資料**

各種增強功能包括能夠同時匯入和匯出大量資產和進階中繼資料建構的中繼資料，例如[階層式中繼資料](/help/assets/cascading-metadata.md)。

**報表**

AEM 6.4中的資產報表已進行大幅修改，其中包含新的報表架構、使用者體驗，以及更多適用於客戶使用案例的OOTB報表。 若要了解如何產生各種報表，請參閱[資產報表](/help/assets/asset-reports.md)。

**使用者體驗**

多項增強功能可改善Assets使用者的瀏覽、搜尋和管理體驗，例如捲動體驗、搜尋返回按鈕、改良的搜尋篩選條件等。 [AEM Assets](assets.md)中可用的完整清單。

**品牌入口網站**

中繼資料、報表、數位權限、登入體驗和發佈資產發佈效能等領域的各種增強功能。 若要了解新的增強功能，請參閱[AEM Assets Brand Portal的新功能](https://docs.adobe.com/content/help/zh-Hant/experience-manager-brand-portal/using/introduction/whats-new.html)。

#### Dynamic Media附加元件 {#dynamic-media-add-on}

AEM 6.4包含許多Dynamic Media的新功能和增強功能。 完整清單可在[AEM Assets](assets.md)中取得。 關鍵重點包括：

**智慧型裁切**

由Adobe Sensei提供技術支援的智慧型裁切功能會自動提供非破壞性的影像裁切功能，保留回應式設計的興趣點。 您可以預覽已裁切的影像建議，並視需要手動調整。 此功能還支援為產品影像自動生成色票。

請參閱[影像描述檔](/help/assets/image-profiles.md)檔案，進一步了解如何使用智慧型裁切。

請參閱[將Dynamic Media資產新增至頁面](/help/assets/adding-dynamic-media-assets-to-pages.md)以進一步了解如何在Dynamic Media元件中使用智慧型裁切。

**智慧型影像**

智慧型影像處理利用每個用戶的獨特觀看特性，自動提供針對其體驗而優化的影像，從而獲得更好的效能和參與度。

請參閱[智慧影像](/help/assets/imaging-faq.md)檔案以深入了解。

![smart_crop](assets/smart_crop.png)

**新興媒體和檢視器增強功能**

全新檢視器（包括全景和VR）可讓您提供更身臨其境的體驗。

請參閱[全景影像](/help/assets/panoramic-images.md)檔案以深入了解。

### Experience ManagerForms {#experience-manager-forms}

AEM 6.4 Forms提供數項新功能和增強功能。 重點包括：

* 多通道互動式通訊
* 從業務應用程式預填互動式通信
* 工作流程現代化和行動背景工作支援
* 延遲載入片段
* 單跳從LiveCycle升級到Experience ManagerForms 6.4

有關[AEM Forms](forms.md)發行說明頁面的更多詳細資訊。 此外，如需新功能和改善功能及檔案資源的相關資訊，請參閱AEM 6.4 Forms的[新功能和增強功能摘要。](/help/forms/using/whats-new.md)

### Experience ManagerLivefyre {#experience-manager-livefyre}

您可以將Livefyre與AEM 6.4執行個體整合。 有關如何將Livefyre與AEM整合的資訊，請前往：

* [整合 Livefyre](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html)

### 利用以客戶為中心的開發 {#leverage-customer-focused-development}

Adobe使用以客戶為中心的開發模型，允許客戶在規格、開發和測試期間為開發流程的所有階段作出貢獻。 在此過程中，我們感謝所有貢獻客戶和合作夥伴。

Adobe已制定程式和程式，以收集、排定優先順序及追蹤以客戶為重點的錯誤解決方法和增強功能要求開發。 [Adobe Marketing Cloud支援入口網站](https://helpx.adobe.com/tw/contact/enterprise-support.ec.html)與Adobe增強和缺陷追蹤系統整合。 如有可能，可向客戶服務確認並解決客戶問題。 呈報至研發時，會擷取所有客戶資訊，並用於優先順序和報告用途。 在開發中，優先考慮付費支援和保證問題以及付費客戶增強功能。

此優先順序排列程式已產生500多項以客戶為重點的變更，已在AEM 6.4中修正。

## 屬於此版本的檔案清單 {#list-of-files-that-are-part-of-the-release}

**Foundation**

* 獨立快速入門：cq-quickstart-6.4.0.jar
* 應用程式伺服器快速入門：cq-quickstart-6.4.0.war
* 適用於各種Web伺服器和平台的Dispatcher 4.3.1或更新版本。 請參閱[下載連結](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/getting-started/release-notes.html)。
* Eclipse IDE的外掛程式。 [深入了解並下載](/help/sites-developing/aem-eclipse.md)。

* Brackets程式碼編輯器的擴充功能。 [深入了解並下載](/help/sites-developing/aem-brackets.md)。
* Maven/Gradle相依性。 請參閱[下載連結](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/aem/uber-jar/6.1.0/)。

**網站**

* 核心元件（[GitHub專案](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components)）
* We.Retail參考實作（[了解詳情](/help/sites-developing/we-retail.md)）
* 專案Blueprint原型（[GitHub專案](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype)）
* AEM Screens播放器([download](https://download.macromedia.com/screens/))
* 智慧內容語言模型。 已預先安裝英文 — 可下載更多語言

   * [德文](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-de)
   * [西班牙文](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-es)
   * [義大利文](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-it)
   * [法文](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-fr)

* [AEM現代化](/help/sites-developing/modernization-tools.md) 工具，將傳統UI元件移轉至Coral 3

**資產**

* Adobe Experience Manager案頭應用程式（[閱讀更多內容](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html)和[下載](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/release-notes.html)）

* 新增增強PDF模擬轉譯器（[了解詳情](/help/assets/aem-pdf-rasterizer.md)和[download](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/product/assets/aem-assets-pdf-rasterizer-pkg)）的套件

* 添加擴展RAW影像支援的包（[了解詳情](/help/assets/camera-raw.md)）

**表單**

* AEM Forms功能的套件：

   * [adobe-aemfd-aix-pkg](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)
   * [adobe-aemfd-linux-pkg](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)
   * [adobe-aemfd-solaris-pkg](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.htmlL)
   * [adobe-aemfd-win-pkg](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)
   * [adobe-aemfd-osx-pkg](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)

## 語言 {#languages}

使用者介面提供下列語言：

* 英文
* 德文
* 法文
* 西班牙文
* 義大利文
* 巴西葡萄牙文
* 日文
* 簡體中文
* 繁體中文（有限支援）
* 韓文

Experience Manager6.4已通過GB18030-2005 CITS認證，可使用中文編碼標準。

## 安裝和更新 {#install-update}

有關安裝要求，請參閱[安裝說明](/help/sites-deploying/custom-standalone-install.md)。

有關詳細說明，請參閱[升級文檔](/help/sites-deploying/upgrade.md)。

## 支援平台 {#supported-platforms}

請尋找支援平台的完整矩陣，包括 [AEM 6.4技術要求](/help/sites-deploying/technical-requirements.md)的支援級別。

>[!NOTE]
>
>Oracle已改用OracleJava SE產品的「長期支援」(LTS)模型。 Java 9和10是按Oracle列出的非LTS版本(請參見[OracleJava SE支援路線圖](https://www.oracle.com/technetwork/java/eol-135779.html))。 Adobe僅支援LTS版的Java，以在生產環境中執行AEM。 因此，建議使用AEM 6.4的版本為Java 8。

## 過時和移除的功能 {#deprecated-and-removed-features}

Adobe不斷評估產品中的功能，並隨著時間的推移計畫用更強大的版本替換功能，或者決定重新實施選定的部件，以便更好地為將來的期望或擴展做好準備。

若為Adobe Experience Manager 6.4，請[閱讀已棄用和已移除功能清單](deprecated-removed-features.md)。 此頁面也包含2019年變更的預先公告，以及客戶從舊版更新的重要通知。

## 詳細更改清單 {#detailed-changes-lists}

[AEM Sites](sites.md)

[AEM Assets](assets.md)

[AEM Communities](communities-release-notes.md)

[AEM Forms](forms.md)

[AEM Foundation](wcm-platform.md)

## 已知問題 {#known-issues}

[已知問題清單](known-issues.md)

### 產品下載與支援（受限網站） {#product-download-and-support-restricted-sites}

這些網站僅供客戶使用。 如果您是Adobe，且需要存取權，請連絡您的客戶經理。

* [請前往licensing.adobe.com下載產品](https://licensing.adobe.com/)。
* [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)上其他功能的產品更新、修補程式和套件。
* [透過Admin Console提供客戶支援](https://adminconsole.adobe.com/)。如需詳細資訊，請參閱[新Adobe客戶支援體驗](https://docs.adobe.com/content/help/en/customer-one/using/home.html)。

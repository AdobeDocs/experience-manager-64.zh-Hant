---
title: Adobe Experience Manager6.4的一般發行說明
seo-title: 發行說明
description: 'Adobe Experience Manager6.4說明，其中列出發行資訊、新增功能、安裝方式和詳細的變更清單。 '
seo-description: 'Adobe Experience Manager6.4說明，其中列出發行資訊、新增功能、安裝方式和詳細的變更清單。 '
uuid: 5a220301-2727-4078-ba19-4a2dbf9657f4
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 2be468e7-2b4e-4e04-881b-b9bdd1f55e57
exl-id: ee034595-2d2a-4887-86c4-6bf0770da6a2
translation-type: tm+mt
source-git-commit: eb55489da5e390578b2ae71be424930e9bf3efd3
workflow-type: tm+mt
source-wordcount: '2813'
ht-degree: 8%

---

# Adobe Experience Manager6.4 {#general-release-notes-for-adobe-experience-manager}的一般發行說明

## 發行資訊 {#release-information}

| 產品 | Adobe Experience Manager |
|---|---|
| 版本 | 6.4 |
| 類型 | 主要版本 |
| 正式上市日期 | 2018 年 4 月 4 日 |
| 建議的更新 | 請參閱[AEM發行和更新](https://helpx.adobe.com/tw/experience-manager/aem-releases-updates.html) |

### Trivia {#trivia}

本版Adobe Experience Manager的發行週期始於2017年4月27日，經過22次反複的品質保證與錯誤修正，並於2018年3月22日結束。 這一版發行中修正的客戶相關問題，包括加強與新功能，總共有 704 個。

Adobe Experience Manager6.4於2018年4月4日正式發行。

>[!NOTE]
>
>Adobe建議安裝最新的Service Pack，因為所有新功能包僅通過[Service Packs](https://helpx.adobe.com/tw/experience-manager/maintenance-releases-roadmap.html)提供。

## 新功能 {#what-s-new}

Adobe Experience Manager 6.4 是 Adobe Experience Manager 6.3 程式碼庫的升級版本。此版本提供全新的增強功能、重要客戶修正、高優先順序的客戶增強功能，以及針對產品穩定化的一般錯誤修正。它還包含Adobe Experience Manager6.3功能套件、Hot Fix和Service Pack版本的大部份。

下列清單提供概觀——而後續頁面則列出完整的詳細資訊。

### Experience Manager基金會{#experience-manager-foundation}

[Foundation&lt;a1/AEM>中更改的完整清單。](wcm-platform.md)

Adobe Experience Manager6.4平台以OSGi架構（Apache Sling和Apache Felix）的更新版本和Java Content Repository為基礎：Apache Jackrabbit Oak 1.8.2.

快速入門使用Eclipse Jetty 9.3.22做為servlet引擎。

#### 使用者介面{#user-interface}

UI已做了各種增強功能，讓它更有生產力，也更容易使用。

* [新的內容樹](/help/sites-authoring/basic-handling.md#content-tree) 狀結構可快速導覽階層。這會與清單檢視結合，還原Classic UI互動模型。
* 改善卡片和大型檔案夾清單檢視中的捲動體驗。
* [改善與搜尋結果的互動](/help/sites-authoring/search.md) -返回按鈕可還原先前的搜尋結果。
* [其他鍵盤快速鍵](/help/sites-authoring/keyboard-shortcuts.md)，適用於大多數常見動作，例如開啟特定邊欄、編輯、移動和刪除項目，或開啟屬性。
* [可停用鍵盤快速鍵](/help/sites-authoring/user-properties.md) （在偏好設定中啟用／停用）。
* [在7天後(在「偏好設定」中設](/help/sites-authoring/user-properties.md) 定預設值)，停止顯示所有UIrelative的時間戳記。

如需這些功能的詳細資訊，請參閱[編寫檔案](/help/sites-authoring/home.md)。

>[!CAUTION]
>
>Adobe不打算對Classic UI做進一步的增強。 AEM 6.4包含Classic UI，而舊版升級的客戶可依原樣繼續使用。 請注意，Classic UI在遭淘汰時仍完全受支援。 [閱讀更多資訊](/help/sites-deploying/ui-recommendations.md)。

#### 內容儲存庫 {#content-repository}

* 透過「線上修訂清除」更快速有效地壓縮。 內部測試表明，新的尾部壓縮速度提高了10倍，與6.3相比，它可以以更少的IOPS回收更多磁碟空AEM間。這樣，在運行「線上修訂清除」時，對效能的影響會降低。 如需詳細資訊，請參閱[說明檔案頁面](/help/sites-deploying/revision-cleanup.md#full-and-tail-compaction-modes)。

* MongoMK的「連續修訂清除」取代計畫的清除維護
* 改善檔案記錄檔的修訂清除效率

#### 搜索和索引{#search-indexing}

* 通過oak-run(CLI)增強對索引操作的支援：

   * 索引一致性檢查
   * 索引統計資料
   * 索引配置導入或導出
   * 重新索引

* 降低與Lucene相關的儲存庫增長，以提高整體系統效能

如需詳細資訊，請造訪[本檔案頁面](/help/sites-deploying/indexing-via-the-oak-run-jar.md)。

#### 監控 {#monitoring}

* 新的[系統概述](/help/sites-administering/operations-dashboard.md#system-overview)提供了所有與效能相關的系統狀態和活動的快照視圖。
* 關於索引、查詢和維護的一組新的[健康檢查](/help/sites-administering/operations-dashboard.md#health-checks)

#### 專案和工作流程{#projects-and-workflows}

* 全新的[工作流程編輯器，以建立和編輯工作流程模型](/help/sites-developing/workflows-models.md)。

![screen_shot_2018-04-04at71143am](assets/screen_shot_2018-04-04at71143am.png)

#### 從舊版{#upgrade-from-earlier-version}升級

* [向後相容性](/help/sites-deploying/backward-compatibility.md):6.4版中向後相容的功能可協助您的自訂程式碼在大多數情況下仍能相容，並降低升級工作量。
* [升級複雜性評估](/help/sites-deploying/pattern-detector.md):全新的模式偵測器工具，可在您升級之前，先評估升級的複雜性。
* [儲存庫重組](/help/sites-deploying/repository-restructuring.md):大幅重組（主要是/etc），以利更輕鬆的升級並促進實施最佳做法
* 有關升級的更多一般資訊，請參閱[本頁](/help/sites-deploying/upgrade.md)以取得詳細資訊。

### Experience Manager站點{#experience-manager-sites}

[AEM Sites和Add-ons](sites.md)中的更改的完整清單。

#### 流暢體驗{#fluid-experiences}

在2017年初推出以內容片段、體驗片段和內容服務為後盾的流暢體驗，是邁向多通道優先內容管理的開端。 AEM 6.4將每個區域顯著擴展：

**[內容片段](/help/assets/content-fragments.md)**

6.4中的新功能包括視覺化[內容模型](/help/assets/content-fragments-models.md)編輯器和新的[可設定元件](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/content-fragment-component.html)，以提供彈性的HTML輸出，以及JSON，可加入Content Services中。

**體驗片段**

有了「建置區塊」功能，使用相同內容但不同版面的片段建立變化變得更有效率。 除了將體驗片段傳送至Facebook和Pinterest之外，現在也可以視需要傳送至Adobe Target。

**Content Services**

Sling Model Exporter和Core Components的各種增強功能已包含在內，以提供強穩的JSON輸出，將內容內嵌在使用單頁應用程式建立的行動應用程式和體驗中。

#### 更快建立網站{#gettings-sites-built-quicker}

AEM6.4完成了對下一代元件模型的轉換。 6.3版中引入的核心元件概念AEM，現在與樣式系統結合，提供建立新網站和擴充現有網站的有效方式。

建議的教學課程，以瞭解如何最佳運用新元件模型：[開始使用AEM Sites- WKND Tutorial](https://docs.adobe.com/content/help/zh-Hant/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)

#### 畫面附加元件{#screens-add-on}

AEM Screens所代表的是在所有行銷通道（包括數位標牌和資訊站網路）中傳遞一致訊息。 AEM 6.4新增在Microsoft Windows和Google Chrome OS硬體上執行Signage Player的支援。 此外，還提供遠端裝置管理與排程（頻道群組）的增強功能。

有關螢幕更新的詳細資訊，請參閱[AEM Screens使用手冊](https://docs.adobe.com/content/help/zh-Hant/experience-manager-screens/user-guide/aem-screens-introduction.html)。

### Experience Manager社區{#experience-manager-communities}

AEM 6.4為社群新增了許多新功能和增強功能。 [AEM Communities](communities-release-notes.md)提供完整的變更清單。 此版本的重點說明為：

#### 協調{#enhancements-to-moderation}的增強功能

**自動偵測垃圾訊息**

已提供新的垃圾訊息偵測引擎，可篩選社群網站和群組上不想要的使用者產生的內容。 在系統／控制台/configMgr中啟用後，它會根據預先定義的垃圾訊息字組，將使用者產生的內容標示為垃圾訊息。 若要進一步瞭解垃圾訊息偵測引擎，請參閱[自動化社群使用者產生內容](/help/communities/moderate-ugc.md#spam-detection)。

![垃圾郵件檢測](assets/spamdetection.png)

**QnA的新濾鏡**

已將名為「已回覆」和「未回覆」的新篩選器新增至大量協調主控台，以篩選QnA問題。 若要瞭解「已回答」和「未回應」狀態篩選的運作方式，請參閱[大量協調使用者產生的內容](/help/communities/moderation.md#main-pars-note-521961797)。

**書籤協調篩選**

已提供在協調主控台上為預先定義的協調篩選建立書籤的功能。 這些篩選器會附加至URL字串的結尾，因此可以共用、重複使用並稍後重新檢視。 瞭解如何在[大量協調控制台](/help/communities/moderation.md#main-pars-note-429176623)中為篩選建立書籤。

#### 刪除UGC和用戶配置檔案{#delete-ugc-and-user-profiles}

AEM 6.4 Communities公開了[現成可用的API](/help/communities/user-ugc-management-service.md)和範例[servlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-ugc-management-servlet)，讓最終用戶能夠控制其資料。 這些API也可讓資料處理和資料控制組織提供歐盟GDPR合規性要求。

#### 網站和群組管理的增強功能{#enhancements-to-site-and-group-management}

**在單一步驟中建立多地區設定群組**

已提供在單一操作中建立多語言組的能力。 若要建立此類群組，使用者可從「網站」主控台導覽至所需社群網站的「群組集合」。 建立群組，並在「社群群組範本」頁面中指定所要的語言。 要瞭解有關此功能的更多資訊，請參閱[社區組console](/help/communities/groups.md)。

![多語言群](assets/multilingualgroup.png)

**[按一下即可刪除社群網站和群組](/help/communities/groups.md)**

從全域導覽時，刪除圖示現在可在個別網站和群組上使用。 使用此圖示會刪除與網站或群組相關的所有項目和內容，並移除所有使用者關聯。 若要進一步瞭解此功能，請參閱[管理社群網站](/help/communities/create-site.md#main-pars-text-fe17)和[管理社群群組](/help/communities/groups.md#main-pars-text-5e8c)。

#### 啟用{#enhancements-to-enablement}的增強功能

現在可在群組中使用指派和目錄功能。 這可讓針對特定群體成員建立、管理和發佈學習內容。 若要進一步瞭解啟用社群群組，請參閱[管理啟用資源](/help/communities/resource.md)。

![指派目錄](assets/assignmentcatalog.png)

### Experience Manager資產{#experience-manager-assets}

AEM6.4為資產提供多項新功能和增強功能，包括全新、改良的CreativeCloud整合、重要的人工智慧創新、改良的中繼資料管理、報告增強功能，以及整體使用者體驗改善。 [AEM Assets](assets.md)中可用更改的完整清單。 本版次的亮點為：

**Adobe資產連結**

Adobe企業Creative Cloud中的資產連結可簡化創意人員與行銷人員在內容建立程式中的協作。 它是企業Creative Cloud的新原生功能，可將PhotoshopCC、IllustratorCC和InDesignCC連接至AEM— 創意人員不必離開自己的選擇工具。

如需進一步瞭解此功能、必要條件及如何存取，請參閱[Adobe資產連結](https://www.adobe.com/tw/creativecloud/business/enterprise/adobe-asset-link.html)。

![adobe_asset_link](assets/adobe_asset_link.png)

**AEM 桌面應用程式**

案頭應AEM用程式已更新為1.8版，與AEM6.4相容。案頭應用程式的AEM完整變更清單會在專用的[案頭應AEM用程式版本注意事項](https://docs.adobe.com/content/help/zh-Hant/experience-manager-desktop-app/using/release-notes.html)檔案中提供。

自6.3版本AEM以來推出的改良功能包括：能夠在背景上傳階層式資料夾、可監控資產背景作業的新使用者介面、增強的快取、網路和登入功能，以及整體穩定性的改善。 說明檔案也包含[最佳實務指南](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html)。

**Adobe Sensei服務**

新功能包括「增強的智慧型標籤」(Enhanced Smart Tags)，它可學習客戶業務分類法、使用客戶特定標籤自動標籤數位資產，以及「智慧型翻譯搜尋」(Smart Translation Search)，它可透過即時翻譯搜尋詞，改善多種語言的發現能力。 若要進一步瞭解此功能，請參閱[增強的智慧標籤](/help/assets/enhanced-smart-tags.md)。

![enhanced_smart_tags2](assets/enhanced_smart_tags2.png)

**中繼資料**

各種增強功能包括能夠同時匯入和匯出大量資產和進階中繼資料建構的中繼資料，例如[階層式中繼資料](/help/assets/cascading-metadata.md)。

**報表**

在6.4版中，資產報告進行了大幅AEM改革，新的報告架構、使用者體驗，以及更多適用於客戶使用案例的OOTB報告。 若要瞭解如何產生各種報表，請參閱[資產報表](/help/assets/asset-reports.md)。

**使用者體驗**

多項增強功能可改善資產使用者的瀏覽、搜尋和管理體驗，例如捲動體驗、搜尋上一頁按鈕、改良的搜尋篩選條件等。 [AEM Assets](assets.md)中的完整清單。

**品牌入口網站**

中繼資料、報告、數位權限、登入體驗和發佈效能等方面的各種增強功能，以利資產散發。 如需新增增強功能的詳細資訊，請參閱[AEM Assets品牌入口網站的新增功能](https://docs.adobe.com/content/help/zh-Hant/experience-manager-brand-portal/using/introduction/whats-new.html)。

#### Dynamic Media附加元件{#dynamic-media-add-on}

AEM6.4包含許多Dynamic Media的新功能和增強功能。 完整清單可在[AEM Assets](assets.md)中找到。 主要亮點包括：

**智慧型裁切**

由Adobe Sensei提供支援的Smart Crop會自動提供影像的非破壞性裁切，保留回應式設計的興趣。 您可以預覽裁切的影像建議，並視需要手動調整。 此功能也可讓產品影像產生自動色票。

請參閱[影像描述檔](/help/assets/image-profiles.md)檔案，進一步瞭解使用智慧型裁切。

請參閱[將Dynamic Media資產新增至頁面](/help/assets/adding-dynamic-media-assets-to-pages.md)，進一步瞭解如何在Dynamic Media元件中使用智慧型裁切。

**智慧型影像**

智慧型影像處理運用每位使用者獨特的檢視特性，自動提供最佳化的影像體驗，進而提供更佳的效能和參與度。

請參閱[智慧型影像](/help/assets/imaging-faq.md)說明檔案以瞭解更多資訊。

![smart_crop](assets/smart_crop.png)

**新興媒體與檢視器增強功能**

全景和VR等全新檢視器可讓您提供更身歷其境的體驗。

請參閱[全景影像](/help/assets/panoramic-images.md)檔案以瞭解更多資訊。

### Experience ManagerForms{#experience-manager-forms}

AEM6.4Forms推出多項新功能和增強功能。 重點包括：

* 多頻道互動式通訊
* 預先填寫商業應用程式的互動式通訊
* 工作流程現代化與行動工作者支援
* 延遲載入片段
* 單跳從LiveCycle升級至Experience ManagerForms6.4

有關[AEM Forms](forms.md)發行說明頁的更多詳細資訊。 此外，如需有關新功能和改進功能及檔案資源的資訊，請參閱AEM6.4Forms的[新功能和增強功能摘要。](/help/forms/using/whats-new.md)

### Experience ManagerLivefyre {#experience-manager-livefyre}

您可將Livefyre與AEM6.4執行個體整合。 有關如何將Livefyre與整合的資AEM訊，請參閱：

* [整合 Livefyre](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html)

### 運用以客戶為中心的開發{#leverage-customer-focused-development}

Adobe使用以客戶為中心的開發模型，讓客戶在規格、開發和測試期間，對開發流程的所有階段都有所貢獻。 在此過程中，我們感謝所有有貢獻的客戶和合作夥伴。

Adobe已制定程式和流程，以便收集、排定優先順序並追蹤以客戶為中心的錯誤解決方案和增強功能要求開發。 [Adobe Marketing Cloud支援門戶](https://helpx.adobe.com/tw/contact/enterprise-support.ec.html)與Adobe增強和缺陷跟蹤系統整合。 客戶問題會盡可能與客戶服務確認並解決。 呈報至研發時，會擷取所有客戶資訊，並用於優先排序和報告用途。 在開發時，優先考慮付費支援和擔保問題以及付費客戶增強功能。

此優先順序已在6.4中修正了500多項以客戶為主的變AEM更。

## 屬於{#list-of-files-that-are-part-of-the-release}版本的檔案清單

**Foundation**

* 獨立快速入門：cq-quickstart-6.4.0.jar
* 應用程式伺服器快速啟動：cq-quickstart-6.4.0.war
* Dispatcher 4.3.1或更新版本，適用於各種Web伺服器和平台。 請參閱[下載連結](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/getting-started/release-notes.html)。
* Eclipse IDE的增效模組。 [閱讀更多內容並下載](/help/sites-developing/aem-eclipse.md)。

* Brackets程式碼編輯器的擴充功能。 [閱讀更多內容並下載](/help/sites-developing/aem-brackets.md)。
* Maven/Gradle相依性。 請參閱[下載連結](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/aem/uber-jar/6.1.0/)。

**網站**

* 核心元件（[GitHub項目](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components)）
* We.Retail Reference實作（[閱讀更多](/help/sites-developing/we-retail.md)）
* 專案藍圖原型（[GitHub專案](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype)）
* AEM Screens播放器適用於各種目標平台([download](https://download.macromedia.com/screens/))
* 智慧型內容語言模型。 已預先安裝英文——可下載更多語言

   * [德文](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-de)
   * [西班牙文](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-es)
   * [義大利文](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-it)
   * [法文](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-fr)

* [將AEMClassic  UI元件移轉至Coral 3的現代化工具](/help/sites-developing/modernization-tools.md) 

**資產**

* Adobe Experience Manager案頭應用程式（[閱讀更多](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html)和[下載](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/release-notes.html)）

* 封裝以新增增強的PDF點陣化器（[閱讀更多](/help/assets/aem-pdf-rasterizer.md)和[下載](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/product/assets/aem-assets-pdf-rasterizer-pkg)）

* 封裝以新增擴充的RAW影像支援（[閱讀更多](/help/assets/camera-raw.md)）

**表單**

* AEM Forms功能的軟體包：

   * [adobe-aemfd-aix-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-AIX)
   * [adobe-aemfd-linux-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-LX)
   * [adobe-aemfd-solaris-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-SOL)
   * [adobe-aemfd-win-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-WIN)
   * [adobe-aemfd-osx-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-OSX)

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

## 安裝與更新{#install-update}

有關安裝要求，請參見[安裝說明](/help/sites-deploying/custom-standalone-install.md)。

請參閱[升級檔案](/help/sites-deploying/upgrade.md)以取得詳細指示。

## 支援的平台{#supported-platforms}

請尋找完整的支援平台矩陣，包括 [AEM 6.4技術要求](/help/sites-deploying/technical-requirements.md)的支援級別。

>[!NOTE]
>
>Oracle已改為OracleJava SE產品的「長期支援」(LTS)模型。 Java 9和10是非LTS版本，依Oracle區分(請參閱OracleJava SE支援路線圖](https://www.oracle.com/technetwork/java/eol-135779.html))。 [Adobe將僅提供LTS版Java的支援，以在生產AEM中執行。 因此，建議使用Java 8與AEM6.4。

## 過時和移除的功能 {#deprecated-and-removed-features}

Adobe會持續評估產品中的功能，並隨著時間推移，以更強大的版本來取代功能，或決定重新建置選取的部件，以便為未來的期望或擴充做好更好的準備。

對於Adobe Experience Manager6.4, [請閱讀已過時和已刪除的功能清單](deprecated-removed-features.md)。 本頁亦包含2019年變更的預先公告，以及客戶從舊版更新的重要通知。

## 詳細更改清單{#detailed-changes-lists}

[AEM Sites](sites.md)

[AEM Assets](assets.md)

[AEM Communities](communities-release-notes.md)

[AEM Forms](forms.md)

[基AEM礎](wcm-platform.md)

## 已知問題 {#known-issues}

[已知問題清單](known-issues.md)

### 產品下載與支援（受限制的網站）{#product-download-and-support-restricted-sites}

這些網站僅提供給客戶使用。 如果您是客戶，需要存取權，請聯絡您的Adobe客戶經理。

* [產品下載，請造訪licensing.adobe.com](https://licensing.adobe.com/)。
* 產品更新、修補程式和套件，以取得[軟體散發](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)的其他功能。
* [透過Admin Console提供客戶支援](https://adminconsole.adobe.com/)。如需詳細資訊，請參閱[新Adobe客戶支援體驗](https://docs.adobe.com/content/help/en/customer-one/using/home.html)。

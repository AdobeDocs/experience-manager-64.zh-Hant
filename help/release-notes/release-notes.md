---
title: 《Adobe Experience Manager6.4一般發行說明》
seo-title: Release Notes
description: 'Adobe Experience Manager6.4說明，概述發行資訊、新增內容、如何安裝和詳細更改清單。 '
seo-description: Adobe Experience Manager 6.4 notes outlining the release information, what's new, how to install and detailed change lists.
uuid: 5a220301-2727-4078-ba19-4a2dbf9657f4
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 2be468e7-2b4e-4e04-881b-b9bdd1f55e57
exl-id: ee034595-2d2a-4887-86c4-6bf0770da6a2
source-git-commit: 722a82c1048105c18d59dfc35815548f9b7eace4
workflow-type: tm+mt
source-wordcount: '2751'
ht-degree: 7%

---

# 《Adobe Experience Manager6.4一般發行說明》 {#general-release-notes-for-adobe-experience-manager}

## 發行資訊 {#release-information}

| 產品 | Adobe Experience Manager |
|---|---|
| 版本 | 6.4 |
| 類型 | 主要版本 |
| 一般可用性日期 | 2018 年 4 月 4 日 |
| 建議的更新 | 請參閱 [AEM版本和更新](https://helpx.adobe.com/tw/experience-manager/aem-releases-updates.html) |

### Trivia {#trivia}

此版Adobe Experience Manager的發佈週期從2017年4月27日開始，經過22次質量保證和缺陷修復，於2018年3月22日結束。 這一版發行中修正的客戶相關問題，包括加強與新功能，總共有 704 個。

Adobe Experience Manager6.4自2018年4月4日起正式提供。

>[!NOTE]
>
>Adobe建議安裝最新的Service Pack，因為所有新功能包僅通過 [服務包](https://helpx.adobe.com/tw/experience-manager/maintenance-releases-roadmap.html)。

## 新功能 {#what-s-new}

Adobe Experience Manager 6.4 是 Adobe Experience Manager 6.3 程式碼庫的升級版本。此版本提供全新的增強功能、重要客戶修正、高優先順序的客戶增強功能，以及針對產品穩定化的一般錯誤修正。它還包括所有Adobe Experience Manager6.3功能包、熱修復和Service Pack版本中的大多數。

下面的清單提供了概述 — 而後續頁面則列出了全部詳細資訊。

### Experience Manager基金會 {#experience-manager-foundation}

更改的完整清單 [基AEM礎](wcm-platform.md)。

Adobe Experience Manager6.4的平台建立在基於OSGi的框架（Apache Sling和Apache Felix）和Java內容儲存庫的更新版本之上：阿帕奇·傑克拉比·橡1.8.2。

Quickstart將Eclipse Jetty 9.3.22用作Servlet引擎。

#### 使用者介面 {#user-interface}

對用戶介面進行了各種增強，使其更高效，更易於使用。

* [新建內容樹欄](/help/sites-authoring/basic-handling.md#content-tree) 以快速瀏覽層次結構。 與清單視圖結合，這將恢復經典UI交互模型。
* 在大資料夾的卡和清單視圖中改進了滾動體驗。
* [改進與搜索結果的交互](/help/sites-authoring/search.md)  — 後退按鈕將恢復先前的搜索結果。
* [其他鍵盤快捷鍵](/help/sites-authoring/keyboard-shortcuts.md)，以執行大多數常見操作，如開啟特定滑軌、編輯、移動和刪除項目或開啟屬性。
* [能夠禁用鍵盤快捷鍵](/help/sites-authoring/user-properties.md) （在首選項中啟用/禁用）。
* [停止在所有UI中顯示時間戳](/help/sites-authoring/user-properties.md) 7天後相對（在「首選項」中設定預設值）。

查看 [創作文檔](/help/sites-authoring/home.md) 的子菜單。

>[!CAUTION]
>
>Adobe不打算對經典用戶介面進行進一步的增強。 AEM6.4包含經典UI，從早期版本升級的客戶可以繼續按原樣使用它。 請注意，不建議使用時，Classic UI仍完全受支援。 [閱讀更多內容](/help/sites-deploying/ui-recommendations.md)。

#### 內容儲存庫 {#content-repository}

* 通過線上修訂版清理，更快、更高效地壓縮。 內部test顯示，新的尾部壓縮速度比6.3快10倍，可以以更少的IOPS回收更多的AEM磁碟空間。這將在運行「線上修訂版清除」時降低效能影響。 有關詳細資訊，請參閱 [文檔頁面](/help/sites-deploying/revision-cleanup.md#full-and-tail-compaction-modes)。

* MongoMK的連續修訂版清理取代了計畫的清理維護
* 提高文檔節點上修訂版清除的效率

#### 搜索和索引 {#search-indexing}

* 通過Oak-Run(CLI)增強對索引操作的支援：

   * 索引一致性檢查
   * 索引統計資訊
   * 索引配置導入或導出
   * 重新索引

* 降低了與Lucene相關的儲存庫增長，提高了總體系統效能

有關詳細資訊，請訪問 [本文檔頁](/help/sites-deploying/indexing-via-the-oak-run-jar.md)。

#### 監控 {#monitoring}

* 新 [系統概述](/help/sites-administering/operations-dashboard.md#system-overview) 提供了所有與效能相關的系統狀態和活動的快照視圖。
* 新集 [運行狀況檢查](/help/sites-administering/operations-dashboard.md#health-checks) 圍繞索引、查詢和維護

#### 項目和工作流 {#projects-and-workflows}

* 全新 [建立和編輯工作流模型的工作流編輯器](/help/sites-developing/workflows-models.md)。

![screen_shot_2018-04-04at71143am](assets/screen_shot_2018-04-04at71143am.png)

#### 從早期版本升級 {#upgrade-from-earlier-version}

* [向後相容性](/help/sites-deploying/backward-compatibility.md):6.4中向後相容的功能，有助於您的自定義代碼在大多數情況下保持相容，並減少升級工作量。
* [升級複雜性評估](/help/sites-deploying/pattern-detector.md):在升級之前，使用新的模式檢測器工具評估升級的複雜性。
* [儲存庫重組](/help/sites-deploying/repository-restructuring.md):大量重組（主要是/etc），以便於更輕鬆的升級和促進實施最佳做法
* 有關升級的更多一般資訊，請參閱 [此頁](/help/sites-deploying/upgrade.md) 的子菜單。

### Experience Manager Sites {#experience-manager-sites}

更改的完整清單 [AEM Sites和附加](sites.md)。

#### 流體體驗 {#fluid-experiences}

2017年初推出了以內容片段、經驗片段和內容服務為後盾的Fluid Experiences，這是向多渠道優先內容管理發展的開始。 AEM6.4顯著擴展了每個區域：

**[內容片段](/help/assets/content-fragments.md)**

6.4中的新增功能是視覺 [內容模型](/help/assets/content-fragments-models.md) 編輯和新 [可配置元件](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/content-fragment-component.html) 提供靈活的HTML輸出和JSON以包括在Content Services中。

**體驗片段**

由於「構建塊」功能，在具有相同內容但不同佈局的片段中建立變體現在更加高效。 除了向Facebook和Pinterest發送體驗片段外，現在還可以將它們作為提議送至Adobe Target。

**Content Services**

包括對Sling Model Exporter和核心元件的各種增強功能，以提供強大的JSON輸出，將內容嵌入到使用單頁應用程式構建的移動應用和體驗中。

#### 加快站點構建 {#gettings-sites-built-quicker}

AEM6.4完成對下一代元件模型的轉換。 6.3中引入的核心元件概念AEM，現在又與樣式系統相結合，它提供了構建新站點和擴展現有站點的有效方法。

建議的教程，瞭解如何最好地利用新元件模型： [AEM Sites入門 — WKND教程](https://docs.adobe.com/content/help/zh-Hant/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)

#### 螢幕載入項 {#screens-add-on}

在包括數字標牌和亭台網路在內的所有營銷渠道中傳遞一致的資訊是AEM Screens所代表的。 6.AEM4增加了在MicrosoftWindows和GoogleChrome作業系統硬體上運行標牌播放器的支援。 此外，對遠程設備管理和時間表（通道組）的增強功能也可用。

有關「螢幕」更新的詳細資訊，請參見 [AEM Screens使用手冊](https://docs.adobe.com/content/help/zh-Hant/experience-manager-screens/user-guide/aem-screens-introduction.html)。

### Experience Manager社區 {#experience-manager-communities}

AEM6.4為社區添加了許多新功能和增強功能。 更改的完整清單可在 [AEM Communities](communities-release-notes.md)。 此版本的亮點是：

#### 對審核的增強 {#enhancements-to-moderation}

**自動垃圾郵件檢測**

已提供新的垃圾郵件檢測引擎，以過濾社區站點和組上不希望的用戶生成的內容。 一旦從系統/控制台/configMgr啟用，它會根據預定義的一組垃圾郵件詞將用戶生成的內容標籤為垃圾郵件。 有關垃圾郵件檢測引擎的詳細資訊，請參閱 [自動化社區用戶生成內容](/help/communities/moderate-ugc.md#spam-detection)。

![垃圾檢測](assets/spamdetection.png)

**QnA的新篩選器**

已將名為「已應答」和「未應答」的新篩選器添加到批量審核控制台以篩選QnA問題。 要瞭解「Answered（已應答）」和「Unsequent（未應答）」狀態篩選器的工作原理，請參閱 [批量調節用戶生成的內容](/help/communities/moderation.md#main-pars-note-521961797)。

**書籤審核篩選器**

提供了在裁決控制台上為預定義的裁決篩選器添加書籤的功能。 這些篩選器被附加到URL字串的末尾，因此可以共用、重新使用並稍後重新訪問。 瞭解如何將篩選器加入書籤 [批量調整控制台](/help/communities/moderation.md#main-pars-note-429176623)。

#### 刪除UGC和用戶配置檔案 {#delete-ugc-and-user-profiles}

AEM6.4社區暴露 [開箱即用API](/help/communities/user-ugc-management-service.md) 樣本 [servlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-ugc-management-servlet) 使最終用戶能夠控制其資料。 這些API還使資料處理和資料控制組織能夠為EU GDPR合規性請求提供服務。

#### 對站點和組管理的增強 {#enhancements-to-site-and-group-management}

**在單步中建立多區域設定組**

提供了在單個操作中建立多語言組的功能。 要建立此類組，用戶可以從「站點」控制台導航到所需社區站點的「組集合」。 建立組，並在「社區組模板」頁中指定所需的語言。 要瞭解有關此功能的詳細資訊，請參閱 [團體組控制台](/help/communities/groups.md)。

![多語種組](assets/multilingualgroup.png)

**[在按一下中刪除社區站點和組](/help/communities/groups.md)**

從全局導航時，刪除表徵圖現在可在相應的站點和組上使用。 使用此表徵圖可刪除與站點或組關聯的所有項目和內容，並刪除所有用戶關聯。 要瞭解有關此功能的詳細資訊，請參閱 [管理社區站點](/help/communities/create-site.md#main-pars-text-fe17) 和 [管理社區組](/help/communities/groups.md#main-pars-text-5e8c)。

#### 增強支援 {#enhancements-to-enablement}

分配和目錄功能現在可在組內使用。 這允許為一組特定目標社區成員建立、管理和發佈學習內容。 有關啟用社區組的詳細資訊，請參閱 [管理啟用資源](/help/communities/resource.md)。

![分配目錄](assets/assignmentcatalog.png)

### Experience Manager Assets {#experience-manager-assets}

AEM6.4為資產帶來了多項新功能和增強功能，包括新的、改進的CreativeCloud整合、關鍵的人工智慧創新、改進的元資料管理、報告增強功能和總體用戶體驗改進。 中可用更改的完整清單 [AEM Assets](assets.md)。 本新聞稿的亮點是：

**Adobe資產連結**

Adobe企業Creative Cloud中的資產連結簡化了內容建立過程中創意人員和營銷人員之間的協作。 它是企業Creative Cloud的新本機能力，將Photoshop、Illustrator和InDesign連AEM接在一起 — 而創意人員不必留下自己選擇的工具。

要瞭解有關此功能、先決條件以及如何訪問它的詳細資訊，請參見 [Adobe資產連結](https://www.adobe.com/tw/creativecloud/business/enterprise/adobe-asset-link.html)。

![adobe_asset_link](assets/adobe_asset_link.png)

**AEM 桌面應用程式**

桌AEM面應用已更新為與6.4相容的AEM1.8版。案頭應用的完AEM整更改清單位於專用 [AEM案頭應用發行說明](https://docs.adobe.com/content/help/zh-Hant/experience-manager-desktop-app/using/release-notes.html) 的子菜單。

自6.3版本AEM以來引入的改進包括：能夠在後台上載分層資料夾、監視資產後台操作的新UI、增強的快取、聯網和登錄，以及總體穩定性改進。 文檔還包括 [最佳做法指南](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html)。

**Adobe Sensei服務**

新功能包括增強智慧標籤，它能夠學習客戶業務分類，自動使用客戶特定標籤為數字資產添加標籤，以及智慧翻譯搜索，通過即時翻譯搜索詞來改進多語言的可發現性。 要瞭解有關此功能的詳細資訊，請參閱 [增強的智慧標籤](/help/assets/enhanced-smart-tags.md)。

![enhanced_smart_tags2](assets/enhanced_smart_tags2.png)

**中繼資料**

各種增強功能包括能夠同時導入和導出大量資產的元資料和高級元資料結構，如 [級聯元資料](/help/assets/cascading-metadata.md)。

**報表**

資產報告在6.4中進行了大AEM修，新報告框架、用戶體驗和更多OOTB報告用於客戶使用案例。 要瞭解如何生成各種報告，請參見 [資產報表](/help/assets/asset-reports.md)。

**用戶體驗**

多種增強功能，可改進Assets用戶的瀏覽、搜索和管理體驗，如滾動體驗、搜索回按鈕、改進的搜索篩選器等。 可用的完整清單 [AEM Assets](assets.md)。

**Brand Portal**

在元資料、報告、數字權限、登錄體驗和發佈資產分配效能等方面進行了各種增強。 要瞭解新的增強功能，請參見 [AEM Assets Brand Portal有什麼新聞嗎](https://docs.adobe.com/content/help/zh-Hant/experience-manager-brand-portal/using/introduction/whats-new.html)。

#### Dynamic Media附加 {#dynamic-media-add-on}

AEM6.4包括許多新功能和對Dynamic Media的增強。 完整清單可在 [AEM Assets](assets.md)。 主要亮點包括：

**智慧型裁切**

由Adobe Sensei提供動力的Smart Crop自動提供影像的無損裁剪，為反應性設計保留興趣點。 您可以預覽裁剪的影像建議，並根據需要手動調整這些建議。 此功能還支援產品影像的自動色板生成。

請參閱 [影像配置檔案](/help/assets/image-profiles.md) 文檔，以瞭解有關使用Smart Crop的詳細資訊。

請參閱 [將Dynamic Media資產添加到頁面](/help/assets/adding-dynamic-media-assets-to-pages.md) 瞭解有關在Dynamic Media元件中與Smart Crop協作的更多資訊。

**智慧型影像**

智慧映像利用每個用戶的獨特觀看特性自動為針對其體驗而優化的映像提供服務，從而獲得更好的效能和參與度。

請參閱 [智慧映像](/help/assets/imaging-faq.md) 文檔以瞭解詳細資訊。

![智慧裁剪](assets/smart_crop.png)

**新興媒體和查看器增強功能**

全景和VR等新觀眾可為您提供更身臨其境的體驗。

請參閱 [全景影像](/help/assets/panoramic-images.md) 文檔以瞭解詳細資訊。

### Experience Manager Forms {#experience-manager-forms}

AEM6.4Forms提供了一些新功能和增強功能。 重點包括：

* 多通道交互通信
* 從業務應用程式預填充互動式通信
* 工作流現代化和移動工作人員支援
* 延遲載入片段
* 單跳從LiveCycle升級到Experience Manager Forms6.4

有關 [AEM Forms](forms.md) 發行說明頁。 另請參見 [6.4Forms的新功能和AEM增強概述](/help/forms/using/whats-new.md) 獲取有關新增和改進的功能和文檔資源的資訊。

### Experience Manager利韋費爾 {#experience-manager-livefyre}

您可以將Livefyre與AEM6.4實例整合。 有關如何將Livefyre與整合的信AEM息位於以下位置：

* [整合 Livefyre](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html)

### 利用以客戶為中心的開發 {#leverage-customer-focused-development}

Adobe正在使用以客戶為中心的開發模型，該模型允許客戶在規範、開發和測試期間為開發過程的所有階段作出貢獻。 在此過程中，我們將向所有有貢獻的客戶和合作夥伴致謝。

Adobe已制定相應的流程和流程，以便收集、排定優先順序並跟蹤以客戶為中心的錯誤解決和增強請求開發。 的 [Adobe Marketing Cloud支援門戶](https://helpx.adobe.com/tw/contact/enterprise-support.ec.html) 與Adobe增強和缺陷跟蹤系統整合。 客戶問題在可能時通過客戶服務確定並解決。 升級到R&amp;D後，將捕獲所有客戶資訊，並用於優先順序和報告目的。 在開發時優先考慮有償支援和保證問題以及有償客戶增強。

這一優先順序排列過程在6.4中完成了500多項以客戶為AEM重點的更改。

## 作為版本一部分的檔案清單 {#list-of-files-that-are-part-of-the-release}

**Foundation**

* 獨立快速入門：cq-quickstart-6.4.0.jar
* 應用程式伺服器快速啟動：cq-quickstart-6.4.0.war
* 用於各種Web伺服器和平台的Dispatcher 4.3.1或更高版本。 請參閱 [下載連結](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/getting-started/release-notes.html)。
* 用於Eclipse IDE的插件。 [閱讀更多內容並下載](/help/sites-developing/aem-eclipse.md)。

* 括弧代碼編輯器的擴展。 [閱讀更多內容並下載](/help/sites-developing/aem-brackets.md)。
* Maven/Gradle依賴項。 請參閱 [下載連結](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/aem/uber-jar/6.1.0/)。

**網站**

* 核心元件([GitHub項目](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components))
* We.Retail Reference實施([閱讀更多](/help/sites-developing/we-retail.md))
* 項目藍圖原型([GitHub項目](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype))
* AEM Screens各目標平台玩家([下載](https://download.macromedia.com/screens/))
* 智慧內容語言模型。 預裝英語 — 可下載更多語言

   * [德文](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-de)
   * [西班牙文](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-es)
   * [義大利文](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-it)
   * [法文](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-fr)

* [現代化AEM工具](/help/sites-developing/modernization-tools.md) 將經典UI元件遷移到Coral 3

**資產**

* Adobe Experience Manager案頭應用[閱讀更多](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html) 和 [下載](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/release-notes.html))

* 要添加增強的PDF光柵化器([閱讀更多](/help/assets/aem-pdf-rasterizer.md) 和 [下載](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/product/assets/aem-assets-pdf-rasterizer-pkg))

* 要添加擴展RAW映像支援的包([閱讀更多](/help/assets/camera-raw.md))

**Forms**

* 用於AEM Forms功能的包：

   * [adobe-aemfd-aix-pkg](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)
   * [adobe-aemfd-linux-pkg](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)
   * [adobe-aemfd-solaris-pkg](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)
   * [adobe-aemfd-win-pkg](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)
   * [adobe-aemfd-osx-pkg](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)

## 語言 {#languages}

用戶介面可以使用以下語言：

* 英文
* 德文
* 法文
* 西班牙文
* 義大利文
* 巴西葡萄牙語
* 日文
* 簡體中文
* 繁體中文（有限支援）
* 韓文

Experience Manager6.4已通過GB18030-2005 CITS的認證，可使用中文編碼標準。

## 安裝和更新 {#install-update}

請參閱 [安裝說明](/help/sites-deploying/custom-standalone-install.md) 設定要求。

請參閱 [升級文檔](/help/sites-deploying/upgrade.md) 的上界。

## 支援的平台 {#supported-platforms}

請查找支援的平台的完整清單，包括 支援級別 [六AEM點四技術要求](/help/sites-deploying/technical-requirements.md)。

>[!NOTE]
>
>Oracle已經轉向了OracleJava SE產品的&quot;長期支援&quot;(LTS)模型。 Java 9和10按Oracle為非LTS版本(請參見 [OracleJava SE支援路線圖](https://www.oracle.com/technetwork/java/eol-135779.html))。 Adobe將僅支援Java的LTS版本，以在生產AEM中運行。 因此，建議將Java 8與AEM6.4一起使用。

## 過時和移除的功能 {#deprecated-and-removed-features}

Adobe不斷評估產品中的功能，並隨著時間推移，計畫用更強大的版本替換功能，或者決定重新實施選定的部件，以便更好地為將來的期望或擴展做好準備。

對於Adobe Experience Manager6.4 [讀取已棄用和已刪除權能的清單](deprecated-removed-features.md)。 該頁還包含2019年變更的預告和從先前版本更新的客戶的重要通知。

## 詳細更改清單 {#detailed-changes-lists}

[AEM Sites](sites.md)

[AEM Assets](assets.md)

[AEM Communities](communities-release-notes.md)

[AEM Forms](forms.md)

[基AEM礎](wcm-platform.md)

## 已知問題 {#known-issues}

[已知問題清單](known-issues.md)

### 產品下載和支援（受限站點） {#product-download-and-support-restricted-sites}

這些站點僅可供客戶使用。 如果您是客戶，需要訪問，請與Adobe客戶經理聯繫。

* [產品下載，網址為licensing.adobe.com](https://licensing.adobe.com/)。
* 產品更新、修補程式和包，以獲得 [軟體分發](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)。
* [客戶支援(通過Admin Console)](https://adminconsole.adobe.com/)。 有關詳細資訊，請參見 [新Adobe客戶支援體驗](https://docs.adobe.com/content/help/en/customer-one/using/home.html)。

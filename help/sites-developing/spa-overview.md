---
title: SPA 編輯器概觀
seo-title: SPA Editor Overview
description: 本文全面概述了 SPA 編輯器及其運作原理，包括 SPA 編輯器在 AEM 中互動的詳細工作流程。
seo-description: This article gives a comprehensive overview of the SPA Editor and how it works included detailed workflows of interaction of the SPA Editor within AEM.
uuid: 600f1100-5cfa-4b75-a58c-f773395b5e05
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 897ff73f-15a5-484f-a3a2-616de8ac59dc
exl-id: 5145b6ab-588a-458f-946f-b730ae319f61
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1711'
ht-degree: 85%

---

# SPA 編輯器概觀{#spa-editor-overview}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

單頁應用程式 (SPA) 可為網站使用者提供引人入勝的體驗。開發人員希望能使用 SPA 框架建立網站，而作者則想在 AEM 中為使用這類框架建立網站，順暢地編輯內容。

SPA 編輯器提供了一個全面的解決方案來支援在 AEM 中使用 SPA。此頁面概述了在 AEM 中 SPA 支援結構、SPA 編輯器的運作原理以及 SPA 框架和 AEM 如何保持同步。

>[!NOTE]
>
>單頁應用程式(SPA)編輯器功能需要 [AEM 6.4 service pack 2](/help/release-notes/sp-release-notes.md) 或更新版本。
>
>若專案需要SPA架構的用戶端轉譯(例如React或Angular),SPA Editor是建議的解決方案。

## 簡介 {#introduction}

使用 React 和 Angular 等常見 SPA 框架建置的網站，透過動態 JSON 載入其內容，並且不提供 AEM 頁面編輯器需要用來放置編輯控制項的 HTML 結構。

若要能在 AEM 中編輯 SPA，SPA 的 JSON 輸出與 AEM 存放庫中的內容模型之間必須要有對應，才能儲存內容的變更。

AEM 中的 SPA 支援帶入一個薄 JS 層，在頁面編輯器中載入內容時會與 SPA JS 程式碼互動，如此可以傳送事件，可以啟動編輯控制項的位置以允許進行情境式編輯。此功能是內容服務 API 端點概念為建置基礎，因為來自 SPA 的內容需要透過內容服務載入。

有關 AEM 中 SPA 的更多詳細資訊，請參閱以下文件：

* [SPA 藍圖](/help/sites-developing/spa-blueprint.md)：說明 SPA 的技術要求
* [AEM中的SPA快速入門](/help/sites-developing/spa-getting-started-react.md) 快速導覽簡單SPA

## 設計 {#design}

SPA 的頁面元件不會透過 JSP 或 HTL 檔案提供其子元件的 HTML 元素。此操作委託給 SPA 框架。子元件或模型的表示是以 JSON 資料結構形式從 JCR 中提取。然後根據該結構將 SPA 元件新增到頁面。此行為將頁面元件的初始內文組合與非 SPA 對應部分區分開來。

### 頁面模型管理 {#page-model-management}

頁面模型的解析和管理委託給提供的 `PageModel` 庫。SPA 必須使用頁面模型庫才能由 SPA 編輯器初始化和編寫。頁面模型庫透過 `aem-react-editable-components` npm 間接提供給 AEM 頁面元件。頁面模型是 AEM 和 SPA 之間的解譯器，因此必須存在。編寫頁面時，必須新增額外的程式庫 `cq.authoring.pagemodel.messaging` 才能與頁面編輯器通訊。

如果 SPA 頁面元件從頁面核心元件繼承，則有兩個方式可以使 `cq.authoring.pagemodel.messaging` 用戶端程式庫類別可用：

* 如果範本可編輯，請將其新增到頁面原則中。
* 或者使用 `customfooterlibs.html` 新增類別。

對於匯出模型中的每個資源，SPA會對應實際元件，以執行\
呈現。 然後，使用容器內的元件對應呈現以 JSON 表示的模型。\
![screen_shot_2018-08-20at144152](assets/screen_shot_2018-08-20at144152.png)

>[!CAUTION]
>
>`cq.authoring.pagemodel.messaging` 類別的納入應限於 SPA 編輯器情境。

### 通訊資料類型 {#communication-data-type}

當 `cq.authoring.pagemodel.messaging` 類別被新增至頁面時，它會向頁面編輯器傳送訊息以建立 JSON 通訊資料類型。當通訊資料類型設定為 JSON 時，GET 要求將與元件的 Sling 模型端點通訊。在頁面編輯器中完成更新後，已更新元件的 JSON 表示將傳送到頁面模型庫。然後，頁面模型庫通知 SPA 有更新。

![screen_shot_2018-08-20at143628](assets/screen_shot_2018-08-20at143628.png)

## 工作流程 {#workflow}

您可以透過將 SPA 編輯器視為 SPA 和 AEM 之間的中介者，了解 SPA 和 AEM 的互動流程。

* 頁面編輯器和 SPA 之間的通訊是使用 JSON 而不是 HTML 進行的。
* 頁面編輯器透過 iframe 和傳訊 API 向 SPA 提供最新版本的頁面模型。
* 頁面模型管理器會通知編輯器它已準備好進行編輯，並將頁面模型作為 JSON 結構傳遞。
* 編輯器不會更改或甚至存取正在編寫之頁面的 DOM 結構，而是提供最新的頁面模型。

![screen_shot_2018-08-20at144324](assets/screen_shot_2018-08-20at144324.png)

### 基本 SPA 編輯器工作流程 {#basic-spa-editor-workflow}

請記住 SPA 編輯器的關鍵元素，對作者而言，在 AEM 中編輯 SPA 的高階工作流程如下所示。

![untitled1](assets/untitled1.gif)

1. SPA 編輯器載入。

1. SPA 載入到單獨的框架中。
1. SPA 要求 JSON 內容並在用戶端呈現元件。
1. SPA 編輯器偵測到呈現的元件並產生覆蓋。
1. 作者按一下覆蓋，顯示元件的編輯工具列。
1. SPA 編輯器透過向伺服器發出 POST 要求來保留編輯。
1. SPA 編輯器要求 SPA 編輯器的已更新 JSON，該更新透過 DOM 事件傳送到 SPA。
1. SPA 重新呈現相關元件，更新其 DOM。

>[!NOTE]
>
>請記住：
>
>* SPA 一律負責其顯示作業。
>* SPA 編輯器與 SPA 本身隔離。
>* 在生產 (發佈) 中，SPA 編輯器從不載入。
>


### 用戶端-伺服器頁面編輯工作流程 {#client-server-page-editing-workflow}

這是編輯 SPA 時用戶端-伺服器互動情況的更詳細概述。

![page_editor_spa_authoringmediator-2](assets/page_editor_spa_authoringmediator-2.png)

1. SPA 自行初始化並要求 Sling 模型匯出工具提供頁面模型。

1. Sling 模型匯出工具要求存放庫提供組成頁面的資源。

1. 存放庫會傳回資源。

1. Sling 模型匯出工具傳回頁面模型。

1. SPA 根據頁面模型執行個體化其元件。

1. **6a** 內容會通知編輯器它已準備好進行編寫。

   **6b** 頁面編輯器要求元件編寫設定。

   **6c** 頁面編輯器接收元件設定。

1. 當作者編輯元件時，頁面編輯器將修改要求發送到預設 POST servlet。

1. 資源在存放庫中更新。

1. 更新的資源會提供給 POST servlet。

1. 預設 POST servlet 會通知頁面編輯器資源已更新。

1. 頁面編輯器要求新的頁面模型。

1. 組成頁面的資源是要求存放庫提供的。

1. 存放庫將組成頁面的資源提供給 Sling 模型匯出工具。

1. 更新後的頁面模型傳回給編輯器。

1. 頁面編輯器會更新 SPA 頁面模型參考。

1. SPA 根據新的頁面模型參考執行個體化其元件。

1. 頁面編輯器的元件設定已更新。

   **17a** SPA 會通知頁面編輯器內容已準備就緒。

   **17b** 頁面編輯器會將元件設定提供給 SPA。

   **17c** SPA 提供更新的元件設定。

### 編寫工作流程 {#authoring-workflow}

這是重點放在編寫體驗的更詳細概述。

![spa_content_authoringmodel](assets/spa_content_authoringmodel.png)

1. SPA 取得頁面模型。

1. **2a** 頁面模型將編寫所需資料提供給編輯器。

   **2b** 當收到通知時，元件協調器更新頁面的內容結構。

1. 元件協調器查詢 AEM 資源類型和 SPA 元件之間的對應。

1. 元件協調器根據頁面模型和元件對應動態執行個體化 SPA 元件。

1. 頁面編輯器會更新頁面模型。

1. **6a** 頁面模型將更新的編寫資料提供給頁面編輯器。

   **6b** 頁面模型將變更分派給元件協調器。

1. 元件協調器取得元件對應。

1. 元件協調器會更新頁面內容。

1. 當 SPA 完成更新頁面內容時，頁面編輯器會載入編寫環境。

## 要求和限制 {#requirements-limitations}

若要使作者能夠使用頁面編輯器編輯 SPA 的內容，必須實作 SPA 應用程式以與 AEM SPA Editor SDK 互動。請參閱 [AEM中的SPA快速入門](/help/sites-developing/spa-getting-started-react.md) 檔案，以便讓您執行。

### 支援的框架 {#supported-frameworks}

SPA Editor SDK 支援以下最低版本：

* React 16.x 及更新版本
* Angular 6.x 及更新版本

這些框架的舊版本可能可以與 AEM SPA Editor SDK 搭配運作，但不受支援。

### 其他的框架 {#additional-frameworks}

可以實作其他 SPA 框架以與 AEM SPA Editor SDK 搭配運作。請參閱 [SPA 藍圖](/help/sites-developing/spa-blueprint.md) 文件，了解框架必須滿足的要求，以便建立由模組、元件和服務組成的框架特定層，以與 AEM SPA 編輯器搭配運作。

### 使用多個選擇器 {#multiple-selectors}

可以定義其他自訂選擇器，並將其納入為 AEM SPA SDK 開發的 SPA 中。但此支援需要 `model` 選取器是第一個選取器，擴充功能是 `.json` as [JSON匯出工具所需。](json-exporter-components.md#multiple-selectors)

### 文字編輯器要求 {#text-editor-requirements}

如果您想使用在 SPA 中建立之文字元件的就地編輯器，則需要額外的設定。

1. 在包含文本 HTML 的容器包裝函式元素上設定一個屬性 (可以是任何屬性)。若是WKND日誌範例內容，則是 `<div>` 元素和已使用的選取器 `data-rte-editelement`.
1. 設定 `editElementQuery` 對應AEM文字元件的 `cq:InplaceEditingConfig` 指向該選取器，例如 `data-rte-editelement`. 這讓編輯器知道哪個 HTML 元素包裝 HTML 文字。

如需如何執行此作業的範例，請參閱 [WKND日誌示例內容。](https://github.com/adobe/aem-sample-we-retail-journal/pull/16/files)

如需關於 `editElementQuery` 屬性和 RTF 文字編輯器設定的其他資訊，請參閱[設定 RTF 文字編輯器](/help/sites-administering/rich-text-editor.md)

### 限制 {#limitations}

AEM SPA Editor SDK已隨AEM 6.4 Service Pack 2推出。 它得到Adobe的充分支援，並作為一項新功能繼續得到增強和擴展。 SPA編輯器尚未涵蓋下列AEM功能：

* 目標模式
* ContextHub
* 內聯影像編輯
* 編輯設定 (例如接聽程式)
* 樣式系統
* 還原/取消復原
* 頁面差異和時間彎曲
* 執行 HTML 重寫伺服器端的功能，例如連結檢查程式、CDN 重寫程式服務、URL 縮短等。
* 開發人員模式
* AEM Launches

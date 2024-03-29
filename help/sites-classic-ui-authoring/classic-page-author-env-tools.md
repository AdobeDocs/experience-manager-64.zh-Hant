---
title: 製作 — 環境和工具
seo-title: Authoring - the Environment and Tools
description: 網站主控台可讓您管理和導覽您的網站。 使用兩個窗格，即可展開網站的結構並對所需元素採取動作。
seo-description: The Websites console allows you to manage and navigate your website. Using two panes, the structure of your website can be expanded and actions taken on the required elements.
uuid: ec4ccc63-a3b8-464c-9c1a-204fd5d3b121
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 278195a6-3452-4966-9d56-022815cf6fb4
exl-id: f073c876-94cd-405d-885f-bfe433817ff4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '935'
ht-degree: 4%

---

# 製作 — 環境和工具{#authoring-the-environment-and-tools}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

AEM的製作環境提供多種組織及編輯內容的機制。 提供的工具可從各種主控台和頁面編輯器存取。

## 網站管理 {#site-administration}

此 **網站** console可讓您管理和導覽您的網站。 使用兩個窗格，即可展開網站的結構，並對必要元素採取動作：

![chlimage_1-153](assets/chlimage_1-153.png)

## 編輯頁面內容 {#editing-your-page-content}

傳統UI提供個別的頁面編輯器，使用內容尋找器和sidekick:

`http://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

![chlimage_1-154](assets/chlimage_1-154.png)

## 存取說明 {#accessing-help}

各種 **說明** 可從AEM內直接存取資源：

以及存取 [控制台工具列的說明](/help/sites-classic-ui-authoring/author-env-basic-handling.md#accessing-help)，您也可以從sidekick(使用？ 圖示)編輯頁面時：

![](do-not-localize/sidekick-collapsed-2.png)

或使用 **說明** 按鈕（位於特定元件的編輯對話框中）;這將顯示上下文相關幫助。

## Sidekick {#sidekick}

此 **元件** sidekick的索引標籤可讓您瀏覽可新增至目前頁面的元件。 可展開所需的群組，然後將元件拖曳至頁面上的必要位置。

![chlimage_1-155](assets/chlimage_1-155.png)

## 內容尋找器 {#the-content-finder}

「內容尋找器」是您在編輯頁面時，在存放庫內快速輕鬆尋找資產和/或內容的方法。

您可以使用內容尋找器來尋找一系列資源。 您可以視需要將項目拖曳至頁面上的段落中：

* [影像](#finding-images)
* [文件](#finding-documents)
* [影片](#finding-movies)
* [Dynamic Media瀏覽器](/help/sites-administering/scene7.md#scene7contentbrowser)
* [頁面](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#finding-pages)
* [段落](#referencing-paragraphs-from-other-pages)
* [產品](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#products)
* 或 [按儲存庫結構瀏覽網站](#the-content-finder)

使用所有選項 [搜尋特定項目](#the-content-finder).

### 尋找影像 {#finding-images}

此索引標籤會列出儲存庫中的任何影像。

在頁面上建立影像段落後，可以拖曳項目並將其拖放至段落中。

![chlimage_1-156](assets/chlimage_1-156.png)

### 查找文檔 {#finding-documents}

此頁簽列出儲存庫中的任何文檔。

在頁面上建立「下載」段落後，您可以拖曳項目並將其拖放至段落中。

![chlimage_1-157](assets/chlimage_1-157.png)

### 尋找電影 {#finding-movies}

此索引標籤會列出存放庫中的任何影片(例如Flash項目)。

在頁面上建立適當的段落(例如Flash)後，您可以拖曳項目並將其拖曳至段落中。

![chlimage_1-158](assets/chlimage_1-158.png)

### 產品 {#products}

此索引標籤會列出任何產品。 在頁面上建立適當的段落（例如「產品」）後，您可以拖曳項目並將其拖曳至段落中。

![chlimage_1-159](assets/chlimage_1-159.png)

### 尋找頁面 {#finding-pages}

此索引標籤會顯示所有頁面。 按兩下任何頁面以開啟它進行編輯。

![chlimage_1-160](assets/chlimage_1-160.png)

### 參考其他頁面的段落 {#referencing-paragraphs-from-other-pages}

此索引標籤可讓您搜尋其他頁面。 該頁面的所有段落都將列出。 然後，您可以將段落拖動到當前頁面，這將建立對原始段落的引用。

![chlimage_1-161](assets/chlimage_1-161.png)

### 使用完整儲存庫視圖 {#using-the-full-repository-view}

此頁簽顯示儲存庫中的所有資源。

![chlimage_1-162](assets/chlimage_1-162.png)

### 搭配內容瀏覽器使用搜尋 {#using-search-with-the-content-browser}

在所有選項上，您可以搜尋特定項目。 會列出符合搜尋模式的任何標籤和任何資源：

![screen_shot_2012-02-08at100746am](assets/screen_shot_2012-02-08at100746am.png)

您也可以使用萬用字元來搜尋。 支援的萬用字元包括：

* `*`  — 匹配零個或多個字元的序列。

* `?`  — 符合單一字元。

>[!NOTE]
>
>有偽屬性「name」，必須用於執行通配符搜索。

例如，如果有一個影像可用，其名稱為：

`ad-nmvtis.jpg`

下列搜尋模式會找到它（以及符合該模式的任何其他影像）:

* `name:*nmv*`
* `name:AD*`  — 字元比對為 *not* 區分大小寫。
* `name:ad?nm??is.*`  — 您可以在查詢中使用任意數量的萬用字元。

>[!NOTE]
>
>您也可以使用 [SQL2](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/commons/query/sql2/package-summary.html) 搜尋。

## 顯示引用 {#showing-references}

AEM可讓您檢視哪些頁面連結至您目前正在使用的頁面。

若要顯示直接頁面參考：

1. 在sidekick中，選取 **頁面** 頁簽。

   ![screen_shot_2012-02-16at83127pm](assets/screen_shot_2012-02-16at83127pm.png)

1. 選擇 **顯示引用……** AEM會開啟「參考」視窗，並顯示哪些頁面參照選取的頁面，包括其路徑。

   ![screen_shot_2012-02-16at83311pm](assets/screen_shot_2012-02-16at83311pm.png)

在某些情況下，可從Sidekick取得其他動作，包括：

* [Launch](/help/sites-classic-ui-authoring/classic-launches.md)
* [Live Copy](/help/sites-administering/msm.md)

* [藍圖](/help/sites-administering/msm-best-practices.md)

其他 [可在網站主控台中看到頁面間關係](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console).

## 稽核記錄 {#audit-log}

此 **稽核記錄** 可從 **資訊** sidekick的標籤。 列出目前頁面上最近採取的動作；例如：

![chlimage_1-163](assets/chlimage_1-163.png)

## 頁面資訊 {#page-information}

網站主控台也 [提供頁面目前狀態的相關資訊](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console) 例如發佈、修改、鎖定、livecopy等。

## 頁面模式 {#page-modes}

使用傳統UI編輯頁面時，可以使用sidekick底部的圖示來存取各種模式：

![](do-not-localize/chlimage_1-15.png)

Sidekick底部的一列圖示可用來切換使用頁面的模式：

* [編輯](/help/sites-classic-ui-authoring/classic-page-author-edit-mode.md)

   這是預設模式，可讓您編輯頁面、新增或刪除元件以及進行其他變更。

* [預覽](/help/sites-classic-ui-authoring/classic-page-author-edit-content.md#previewing-pages)

   此模式可讓您預覽頁面，如同頁面以最終形式顯示在您的網站上。

* [Design](/help/sites-classic-ui-authoring/classic-page-author-design-mode.md#main-pars-procedure-0)

   在此模式中，您可以設定可存取的元件，以編輯頁面的設計。

>[!NOTE]
>
>也提供其他選項：
>
>* [支架](/help/sites-classic-ui-authoring/classic-feature-scaffolding.md)
>* [ClientContext](/help/sites-administering/client-context.md)
>* 網站 — 將開啟網站主控台。
>* 重新載入 — 將重新整理頁面。


## 鍵盤快速鍵 {#keyboard-shortcuts}

各種 [鍵盤快捷鍵](/help/sites-classic-ui-authoring/classic-page-author-keyboard-shortcuts.md) 的URL區段。

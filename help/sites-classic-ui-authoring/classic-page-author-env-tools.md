---
title: 製作 — 環境和工具
seo-title: 製作 — 環境和工具
description: 網站主控台可讓您管理和導覽您的網站。 使用兩個窗格，即可展開網站的結構並對所需元素採取動作。
seo-description: 網站主控台可讓您管理和導覽您的網站。 使用兩個窗格，即可展開網站的結構並對所需元素採取動作。
uuid: ec4ccc63-a3b8-464c-9c1a-204fd5d3b121
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 278195a6-3452-4966-9d56-022815cf6fb4
exl-id: f073c876-94cd-405d-885f-bfe433817ff4
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 2%

---

# 編寫 — 環境和工具{#authoring-the-environment-and-tools}

AEM的製作環境提供多種組織及編輯內容的機制。 提供的工具可從各種主控台和頁面編輯器存取。

## 站點管理{#site-administration}

**網站**&#x200B;主控台可讓您管理和導覽您的網站。 使用兩個窗格，即可展開網站的結構，並對必要元素採取動作：

![chlimage_1-153](assets/chlimage_1-153.png)

## 編輯頁面內容{#editing-your-page-content}

傳統UI提供個別的頁面編輯器，使用內容尋找器和sidekick:

`http://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

![chlimage_1-154](assets/chlimage_1-154.png)

## 訪問幫助{#accessing-help}

您可以從AEM內直接存取各種&#x200B;**Help**&#x200B;資源：

除了從控制台工具欄[訪問幫助外，您還可以從sidekick(使用？ ](/help/sites-classic-ui-authoring/author-env-basic-handling.md#accessing-help)圖示)編輯頁面時：

![](do-not-localize/sidekick-collapsed-2.png)

或使用特定元件編輯對話方塊中的&#x200B;**Help**&#x200B;按鈕；這將顯示上下文相關幫助。

## Sidekick {#sidekick}

sidekick的&#x200B;**Components**&#x200B;標籤可讓您瀏覽可新增至目前頁面的元件。 可展開所需的群組，然後將元件拖曳至頁面上的必要位置。

![chlimage_1-155](assets/chlimage_1-155.png)

## 內容尋找器{#the-content-finder}

「內容尋找器」是您在編輯頁面時，在存放庫內快速輕鬆尋找資產和/或內容的方法。

您可以使用內容尋找器來尋找一系列資源。 您可以視需要將項目拖曳至頁面上的段落中：

* [影像](#finding-images)
* [文件](#finding-documents)
* [影片](#finding-movies)
* [Dynamic Media瀏覽器](/help/sites-administering/scene7.md#scene7contentbrowser)
* [頁面](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#finding-pages)
* [段落](#referencing-paragraphs-from-other-pages)
* [產品](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#products)
* 或按儲存庫結構](#the-content-finder)瀏覽網站[

使用所有選項，您可以[搜索特定項](#the-content-finder)。

### 查找影像{#finding-images}

此索引標籤會列出儲存庫中的任何影像。

在頁面上建立影像段落後，可以拖曳項目並將其拖放至段落中。

![chlimage_1-156](assets/chlimage_1-156.png)

### 查找文檔{#finding-documents}

此頁簽列出儲存庫中的任何文檔。

在頁面上建立「下載」段落後，您可以拖曳項目並將其拖放至段落中。

![chlimage_1-157](assets/chlimage_1-157.png)

### 查找電影{#finding-movies}

此索引標籤會列出存放庫中的任何影片(例如Flash項目)。

在頁面上建立適當的段落(例如Flash)後，您可以拖曳項目並將其拖曳至段落中。

![chlimage_1-158](assets/chlimage_1-158.png)

### 產品 {#products}

此索引標籤會列出任何產品。 在頁面上建立適當的段落（例如「產品」）後，您可以拖曳項目並將其拖曳至段落中。

![chlimage_1-159](assets/chlimage_1-159.png)

### 查找頁面{#finding-pages}

此索引標籤會顯示所有頁面。 按兩下任何頁面以開啟它進行編輯。

![chlimage_1-160](assets/chlimage_1-160.png)

### 參考其他頁面的段落{#referencing-paragraphs-from-other-pages}

此索引標籤可讓您搜尋其他頁面。 該頁面的所有段落都將列出。 然後，您可以將段落拖動到當前頁面，這將建立對原始段落的引用。

![chlimage_1-161](assets/chlimage_1-161.png)

### 使用完整儲存庫視圖{#using-the-full-repository-view}

此頁簽顯示儲存庫中的所有資源。

![chlimage_1-162](assets/chlimage_1-162.png)

### 使用內容瀏覽器{#using-search-with-the-content-browser}進行搜尋

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
* `name:AD*`  — 字元比對不 ** 區分大小寫。
* `name:ad?nm??is.*`  — 您可以在查詢中使用任意數量的萬用字元。

>[!NOTE]
>
>您也可以使用[SQL2](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/commons/query/sql2/package-summary.html)搜索。

## 顯示引用{#showing-references}

AEM可讓您檢視哪些頁面連結至您目前正在使用的頁面。

若要顯示直接頁面參考：

1. 在sidekick中，選取&#x200B;**Page**&#x200B;標籤圖示。

   ![screen_shot_2012-02-16at83127pm](assets/screen_shot_2012-02-16at83127pm.png)

1. 選擇&#x200B;**顯示引用……** AEM會開啟「參考」視窗，並顯示哪些頁面參照選取的頁面，包括其路徑。

   ![screen_shot_2012-02-16at83311pm](assets/screen_shot_2012-02-16at83311pm.png)

在某些情況下，可從Sidekick取得其他動作，包括：

* [啟動](/help/sites-classic-ui-authoring/classic-launches.md)
* [即時副本](/help/sites-administering/msm.md)

* [Blueprint](/help/sites-administering/msm-best-practices.md)

其他[頁面間關係可在網站主控台](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console)中看到。

## 稽核記錄 {#audit-log}

可從sidekick的&#x200B;**Information**&#x200B;標籤存取&#x200B;**Audit Log**。 列出目前頁面上最近採取的動作；例如：

![chlimage_1-163](assets/chlimage_1-163.png)

## 頁面資訊 {#page-information}

網站主控台也[提供關於頁面](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console)目前狀態的資訊，例如發佈、修改、鎖定、LiveCopy等。

## 頁面模式{#page-modes}

使用傳統UI編輯頁面時，可以使用sidekick底部的圖示來存取各種模式：

![](do-not-localize/chlimage_1-15.png)

Sidekick底部的一列圖示可用來切換使用頁面的模式：

* [編輯](/help/sites-classic-ui-authoring/classic-page-author-edit-mode.md)

   這是預設模式，可讓您編輯頁面、新增或刪除元件以及進行其他變更。

* [預覽](/help/sites-classic-ui-authoring/classic-page-author-edit-content.md#previewing-pages)

   此模式可讓您預覽頁面，如同頁面以最終形式顯示在您的網站上。

* [設計](/help/sites-classic-ui-authoring/classic-page-author-design-mode.md#main-pars-procedure-0)

   在此模式中，您可以設定可存取的元件，以編輯頁面的設計。

>[!NOTE]
>
>也提供其他選項：
>
>* [支架](/help/sites-classic-ui-authoring/classic-feature-scaffolding.md)
* [ClientContext](/help/sites-administering/client-context.md)
* 網站 — 將開啟網站主控台。
* 重新載入 — 將重新整理頁面。


## 鍵盤快速鍵 {#keyboard-shortcuts}

有各種[鍵盤快速鍵](/help/sites-classic-ui-authoring/classic-page-author-keyboard-shortcuts.md)可用。

---
title: 編寫——環境和工具
seo-title: 編寫——環境和工具
description: 「網站」主控台可讓您管理和導覽您的網站。 使用兩個窗格，您的網站結構可以展開，並對所需元素採取動作。
seo-description: 「網站」主控台可讓您管理和導覽您的網站。 使用兩個窗格，您的網站結構可以展開，並對所需元素採取動作。
uuid: ec4ccc63-a3b8-464c-9c1a-204fd5d3b121
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 278195a6-3452-4966-9d56-022815cf6fb4
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 2%

---


# 編寫——環境和工具{#authoring-the-environment-and-tools}

AEM的製作環境提供多種機制來組織和編輯您的內容。 提供的工具可從各種控制台和頁面編輯器中存取。

## 站點管理{#site-administration}

**Websites**&#x200B;主控台可讓您管理和導覽您的網站。 使用這兩個窗格，可展開網站的結構，並對所需元素採取動作：

![chlimage_1-153](assets/chlimage_1-153.png)

## 編輯頁面內容{#editing-your-page-content}

使用傳統UI（使用內容搜尋器和sidekick）的個別頁面編輯器：

`http://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

![chlimage_1-154](assets/chlimage_1-154.png)

## 訪問幫助{#accessing-help}

您可從AEM直接存取各種&#x200B;**Help**&#x200B;資源：

除了從控制台工具列存取[說明外，您也可以從sidekick存取說明(使用？ ](/help/sites-classic-ui-authoring/author-env-basic-handling.md#accessing-help)圖示):

![](do-not-localize/sidekick-collapsed-2.png)

或者，使用特定元件編輯對話方塊中的&#x200B;**Help**&#x200B;按鈕；這會顯示內容相關的說明。

## Sidekick {#sidekick}

sidekick的&#x200B;**Components**&#x200B;標籤可讓您瀏覽可新增至目前頁面的元件。 您可以展開所需的群組，然後將元件拖曳至頁面上的所需位置。

![chlimage_1-155](assets/chlimage_1-155.png)

## 內容搜尋器{#the-content-finder}

Content Finder是編輯頁面時在儲存庫中尋找資產和／或內容的快速而簡單的方法。

您可以使用內容搜尋器來尋找一系列資源。 您可以視需要將項目拖曳至頁面上的段落：

* [影像](#finding-images)
* [文件](#finding-documents)
* [影片](#finding-movies)
* [Scene7 媒體瀏覽器](/help/sites-administering/scene7.md#scene7contentbrowser)
* [頁面](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#finding-pages)
* [段落](#referencing-paragraphs-from-other-pages)
* [產品](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#products)
* 或者，要按儲存庫結構[瀏覽網站](#the-content-finder)

使用所有選項，您可以[搜索特定項目](#the-content-finder)。

### 尋找影像{#finding-images}

此頁籤列出了儲存庫中的所有映像。

在頁面上建立影像段落後，您可以拖曳項目並放入段落中。

![chlimage_1-156](assets/chlimage_1-156.png)

### 查找文檔{#finding-documents}

此頁籤列出了儲存庫中的所有文檔。

在頁面上建立「下載」段落後，您可以拖曳項目並放入段落中。

![chlimage_1-157](assets/chlimage_1-157.png)

### 尋找影片{#finding-movies}

此標籤列出儲存庫中的所有影片（如Flash項目）。

在頁面上建立適當的段落（例如Flash）後，您可以拖曳項目並放入段落中。

![chlimage_1-158](assets/chlimage_1-158.png)

### 產品 {#products}

此標籤列出任何產品。 在頁面上建立適當的段落（例如「產品」）後，您可以拖曳項目並拖曳至段落中。

![chlimage_1-159](assets/chlimage_1-159.png)

### 尋找頁面{#finding-pages}

此標籤顯示所有頁面。 連按兩下任何頁面以開啟頁面進行編輯。

![chlimage_1-160](assets/chlimage_1-160.png)

### 參考其他頁面的段落{#referencing-paragraphs-from-other-pages}

此標籤可讓您搜尋其他頁面。 該頁面的所有段落都將列出。 然後，您可以將段落拖曳至目前頁面，這會建立對原始段落的參考。

![chlimage_1-161](assets/chlimage_1-161.png)

### 使用完整資料庫視圖{#using-the-full-repository-view}

此頁籤顯示儲存庫中的所有資源。

![chlimage_1-162](assets/chlimage_1-162.png)

### 使用內容瀏覽器{#using-search-with-the-content-browser}進行搜尋

在所有選項中，您可以搜尋特定項目。 會列出符合搜尋模式的任何標籤和任何資源：

![screen_shot_2012-02-08at100746am](assets/screen_shot_2012-02-08at100746am.png)

您也可以使用萬用字元進行搜尋。 支援的萬用字元包括：

* `*` -匹配零個或多個字元的序列。

* `?` -與單個字元匹配。

>[!NOTE]
>
>有一個偽屬性&quot;name&quot;，必須用於執行通配符搜索。

例如，如果有影像可以使用名稱：

`ad-nmvtis.jpg`

下列搜尋模式會找到它（以及任何符合模式的其他影像）:

* `name:*nmv*`
* `name:AD*` -字元比對不區分大小寫 ** 的情況。
* `name:ad?nm??is.*` -您可以在查詢中使用任意數量的通配符。

>[!NOTE]
>
>您也可以使用[SQL2](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/commons/query/sql2/package-summary.html)搜尋。

## 顯示引用{#showing-references}

AEM可讓您檢視哪些頁面已連結至您目前正在處理的頁面。

要顯示直接頁面參考：

1. 在sidekick中，選擇&#x200B;**Page**&#x200B;標籤圖示。

   ![screen_shot_2012-02-16at83127pm](assets/screen_shot_2012-02-16at83127pm.png)

1. 選擇&#x200B;**顯示引用……** AEM會開啟「參考」視窗，並顯示哪些頁面參照所選頁面，包括其路徑。

   ![screen_shot_2012-02-16at83311pm](assets/screen_shot_2012-02-16at83311pm.png)

在某些情況下，Sidekick會提供進一步的動作，包括：

* [啟動](/help/sites-classic-ui-authoring/classic-launches.md)
* [即時副本](/help/sites-administering/msm.md)

* [Blueprint](/help/sites-administering/msm-best-practices.md)

其他[頁面間關係可在網站主控台](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console)中看到。

## 稽核記錄 {#audit-log}

可從側腳的&#x200B;**資訊**&#x200B;頁籤訪問&#x200B;**審計日誌**。 它列出了當前頁面上最近採取的行動；例如：

![chlimage_1-163](assets/chlimage_1-163.png)

## 頁面資訊 {#page-information}

網站控制台也[提供有關頁面](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console)目前狀態的資訊，例如出版物、修改、鎖定、livecopy等。

## 頁面模式{#page-modes}

使用傳統UI編輯頁面時，可使用sidekick底部的圖示存取各種模式：

![](do-not-localize/chlimage_1-15.png)

Sidekick底部的一列圖示可用來切換使用頁面的模式：

* [編輯](/help/sites-classic-ui-authoring/classic-page-author-edit-mode.md)

   這是預設模式，允許您編輯頁面、添加或刪除元件以及進行其他更改。

* [預覽](/help/sites-classic-ui-authoring/classic-page-author-edit-content.md#previewing-pages)

   此模式可讓您預覽頁面，就像頁面以最終形式出現在您的網站上一樣。

* [設計](/help/sites-classic-ui-authoring/classic-page-author-design-mode.md#main-pars-procedure-0)

   在此模式下，您可以通過配置可訪問的元件來編輯頁面設計。

>[!NOTE]
>
>其他選項也可供使用：
>
>* [支架](/help/sites-classic-ui-authoring/classic-feature-scaffolding.md)
>* [ClientContext](/help/sites-administering/client-context.md)
>* 網站——將開啟網站主控台。
>* 重新載入——將重新整理頁面。


## 鍵盤快速鍵 {#keyboard-shortcuts}

有各種[鍵盤快速鍵](/help/sites-classic-ui-authoring/classic-page-author-keyboard-shortcuts.md)可供使用。

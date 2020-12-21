---
title: 建立範例頁面
seo-title: 建立範例頁面
description: 建立範例社群網站
seo-description: 建立範例社群網站
uuid: 04a8f027-b7d8-493a-a9bd-5c4a6715d754
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: developing
discoiquuid: a03145f7-6697-4797-b73e-6f8d241ce469
translation-type: tm+mt
source-git-commit: 8c66f2b0053882bd1c998d8e01dbb0573881bc87
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 1%

---


# 建立範例頁面{#create-a-sample-page}

自AEM 6.1 Communities起，建立範例頁面最簡單的方式就是建立簡單的社群網站，只包含頁面功能。

這將包括parsys元件，以便您能夠[啟用用於編寫的元件](basics.md#accessing-communities-components)。

另一個探索範例元件的選項是使用[社群元件指南](components-guide.md)中的功能。

## 建立社區站點{#create-a-community-site}

這與建立新網站非常類似，如[AEM Communities](getting-started.md)快速入門中所述。

主要區別在於，本教學課程將建立僅包含[Page函式](functions.md#page-function)的新社群網站範本，以建立不含其他功能的簡單社群網站（所有社群網站的連線功能除外）。

### 建立新網站範本{#create-new-site-template}

若要開始，請建立簡單的[社群網站範本](sites.md)。

從作者實例的全局導航中，選擇&#x200B;**[!UICONTROL 工具>社區>站點模板]**。

![chlimage_1-82](assets/chlimage_1-82.png)

* 選取 `Create button`
* 基本資訊

   * `Name`:單頁範本
   * `Description`:由單一頁面函陣列成的範本。
   * 選擇`Enabled`

![chlimage_1-83](assets/chlimage_1-83.png)

* 結構

   * 將`Page`函式拖曳至範本產生器
   * 對於配置函式詳細資訊，請輸入

      * `Title`:單頁
      * `URL`: 頁面

![chlimage_1-84](assets/chlimage_1-84.png)

* 為配置選擇&#x200B;**`Save`**
* 為站點模板選擇&#x200B;**`Save`**

### 建立新社區站點{#create-new-community-site}

現在，根據簡單網站範本建立新的社群網站。

建立網站範本後，從全域導覽中選取「**[!UICONTROL 社群>網站]**」。

![chlimage_1-85](assets/chlimage_1-85.png)

* 選擇&#x200B;**`Create`**&#x200B;表徵圖

* 步驟 `1 - Site Template`

   * `Title`:簡單社群網站
   * `Description`:由單一頁面組成的社群網站，可供實驗。
   * `Community Site Root: (leave blank)`
   * `Community Site Base Language: English`
   * `Name`:樣本

      * url = http://localhost:4502/content/sites/sample
   * `Template`:選擇  `Single Page Template`


![chlimage_1-86](assets/chlimage_1-86.png)

* 選取 `Next`
* 步驟 `2 - Design`

   * 選擇任何設計

* 選取 `Next`
* 選取 `Next`

   （接受所有預設設定）

* 選取 `Create`

![chlimage_1-87](assets/chlimage_1-87.png)

## 發佈網站{#publish-the-site}

![chlimage_1-88](assets/chlimage_1-88.png)

從[社群網站主控台](sites-console.md)中，選取發佈圖示以發佈網站，預設為http://localhost:4503。

## 以編輯模式{#open-the-site-on-author-in-edit-mode}開啟作者網站

![chlimage_1-89](assets/chlimage_1-89.png)

選取開啟的網站圖示，以編輯模式檢視網站。

URL將為[http://localhost:4502/editor.html/content/sites/sample/en.html](http://localhost:4502/editor.html/content/sites/sample/en.html)

![chlimage_1-90](assets/chlimage_1-90.png)

在簡單的首頁上，您可以透過社群功能和範本查看預先串連的內容，並播放新增和設定社群元件的功能。

## 在發佈時檢視網站{#view-site-on-publish}

發佈頁面後，請開啟[publish instance](http://localhost:4503/content/sites/sample/en.html)上的頁面，以匿名網站訪客、登入成員或管理員的身分來實驗這些功能。 除非管理員登入，否則作者環境中可見的「管理」連結不會出現在發佈環境中。

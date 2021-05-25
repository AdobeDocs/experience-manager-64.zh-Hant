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
exl-id: 00ac29fb-cc8f-4dd9-a261-839a4bf664c2
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 1%

---

# 建立範例頁面{#create-a-sample-page}

與AEM 6.1 Communities相同，建立範例頁面最簡單的方式是建立簡單的社群網站，只包含Page函式。

這將包含parsys元件，以便您可以[啟用元件以編寫](basics.md#accessing-communities-components)。

使用樣本元件探索的另一個選項是使用[Community Components Guide](components-guide.md)中提供的功能。

## 建立社區站點{#create-a-community-site}

這非常類似於建立新網站，如[AEM Communities快速入門](getting-started.md)所述。

主要差異在於，本教學課程將建立僅包含[Page函式](functions.md#page-function)的新社群網站範本，以建立簡單的社群網站，不含其他功能（除了所有社群網站的基本連線功能外）。

### 建立新站點模板{#create-new-site-template}

若要開始使用，請建立簡單的[社群網站範本](sites.md)。

從製作例項上的全域導覽中，選取&#x200B;**[!UICONTROL 工具>社群>網站範本]**。

![chlimage_1-82](assets/chlimage_1-82.png)

* 選取 `Create button`
* 基本資訊

   * `Name`:單頁範本
   * `Description`:由單一頁面函陣列成的範本。
   * 選擇`Enabled`

![chlimage_1-83](assets/chlimage_1-83.png)

* 結構

   * 將`Page`函式拖曳至範本產生器
   * 有關配置函式詳細資訊，請輸入

      * `Title`:單頁
      * `URL`: 頁面

![chlimage_1-84](assets/chlimage_1-84.png)

* 為配置選擇&#x200B;**`Save`**
* 為站點模板選擇&#x200B;**`Save`**

### 建立新社區站點{#create-new-community-site}

現在，根據簡單網站範本建立新的社群網站。

建立網站範本後，從全域導覽中選取&#x200B;**[!UICONTROL Communities > Sites]**。

![chlimage_1-85](assets/chlimage_1-85.png)

* 選擇&#x200B;**`Create`**&#x200B;表徵圖

* 步驟 `1 - Site Template`

   * `Title`:簡單社群網站
   * `Description`:一個社群網站，包含單一實驗頁面。
   * `Community Site Root: (leave blank)`
   * `Community Site Base Language: English`
   * `Name`:範例

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

## 發佈站點{#publish-the-site}

![chlimage_1-88](assets/chlimage_1-88.png)

從[社群網站控制台](sites-console.md)中，選取要發佈網站的發佈圖示，依預設會發佈至http://localhost:4503。

## 在編輯模式{#open-the-site-on-author-in-edit-mode}中開啟作者網站

![chlimage_1-89](assets/chlimage_1-89.png)

選取開啟的網站圖示，以編輯模式檢視網站。

URL將為[http://localhost:4502/editor.html/content/sites/sample/en.html](http://localhost:4502/editor.html/content/sites/sample/en.html)

![chlimage_1-90](assets/chlimage_1-90.png)

在簡單的首頁上，您可以查看透過社群功能和範本預先連線的內容，並播放新增和設定社群元件的過程。

## 在發佈時查看站點{#view-site-on-publish}

發佈頁面後，請開啟[publish instance](http://localhost:4503/content/sites/sample/en.html)上的頁面，以匿名網站訪客、登入成員或管理員的身分來試驗這些功能。 除非管理員登入，否則製作環境中可見的管理連結不會出現在發佈環境中。

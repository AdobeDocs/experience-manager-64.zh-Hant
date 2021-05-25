---
title: 活動趨勢
seo-title: 活動趨勢
description: 新增社群活動清單元件至頁面
seo-description: 新增社群活動清單元件至頁面
uuid: 6a030340-0e69-432a-98f1-3effb2b97136
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 93a112fc-ef34-4281-89b8-a0f1b3d3aca9
exl-id: a2cb9738-98a5-4ea6-8d5a-a6c0aa04cd32
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 4%

---

# 活動趨勢{#activity-trends}

## 簡介 {#introduction}

`Community Activity List`元件可新增關於依成員及貼文和內容檢視之貼文和檢視的趨勢資訊。

本檔案的本節說明

* 將`Community Activity List`元件新增至[社群網站](overview.md#community-sites)

* `Community Activity List`元件的組態設定

## 需求 {#requirement}

`Community Activity List`的資料僅在為社群網站授權並配置Adobe Analytics時可用。

請參閱[Analytics For Communities](analytics.md)。

## 將社群活動清單新增至頁面{#adding-a-community-activity-list-to-a-page}

若要以製作模式將`Community Activity List`元件新增至頁面，請找出元件`Communities / Community Activity List`，並將其拖曳至頁面上的位置。

如需必要資訊，請造訪[Communities Components Basics](basics.md)。

首次放置在社群網站的頁面時，元件的顯示方式如下：

![chlimage_1-227](assets/chlimage_1-227.png)

## 配置社區活動清單{#configuring-community-activity-list}

選取要存取的放置`Community Activity List`元件，並選取開啟編輯對話方塊的`Configure`圖示。

![chlimage_1-228](assets/chlimage_1-228.png)

在&#x200B;**[!UICONTROL Comments]**&#x200B;標籤下，指定上傳檔案的備注是否及顯示方式：

![chlimage_1-229](assets/chlimage_1-229.png)

* **[!UICONTROL 類型]**

   指定要顯示社群成員或使用者產生內容(UGC)的相關資料。

   從
   * `Members`
   * `Content`

   預設值為`Members`。

* **[!UICONTROL 顯示標題]**

   要在資料上方顯示的描述性標題，例如`Trending Content`。

   預設為無標題。

* **[!UICONTROL 顯示計數]**

   要列出的項目數。

   預設為10。

* **[!UICONTROL 活動類型]**

   選取其中一個
   * `Views`（頁面瀏覽次數）
   * `Posts`（建立UGC）
   * `Follows`
   * `Likes`

   預設為檢視。

* **[!UICONTROL 時間段]**

   選取其中一個
   * `Last 24 hours`
   * `Last 7 days`
   * `Last 30 days`
   * `Last 90 days`
   * `This year (since Jan 1st)`
   * `Total`

   預設值為`Total`。

* **[!UICONTROL 內容路徑]**

   提供將活動範圍限定為網站子集（如特定部落格）的能力。

   預設值是整個社群網站。

* **[!UICONTROL 成員人數彙總]**

   取消勾選後（關閉），只會計算最上層貼文。 例如，如果內容是根頁面（預設值），則`Posts`的`Activity Type`將不會顯示任何活動，因為無法將內容張貼至根頁面。 若勾選此選項，則會包含所有子系頁面上的計數。

   已勾選預設值。

## 4個元件的範例頁面{#example-page-with-components}

**頂** 級Visitorsconfig:類型=成員，活動類型=檢視

**排名在** 前的貢獻者設定：類型=成員，活動類型=貼文

**排名在** 前的Contentconfig:類型=內容，活動類型=檢視，

**趨勢** 內容設定：類型=內容，活動類型=貼文

![chlimage_1-230](assets/chlimage_1-230.png)

---
title: 活動趨勢
seo-title: 活動趨勢
description: 將社群活動清單元件添加到頁面
seo-description: 將社群活動清單元件添加到頁面
uuid: 6a030340-0e69-432a-98f1-3effb2b97136
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 93a112fc-ef34-4281-89b8-a0f1b3d3aca9
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 4%

---


# 活動趨勢{#activity-trends}

## 簡介 {#introduction}

`Community Activity List`元件可新增成員的貼文和檢視、貼文和內容檢視等趨勢資訊。

本節說明

* 將`Community Activity List`元件添加到[社區站點](overview.md#community-sites)

* `Community Activity List`元件的配置設定

## 需求 {#requirement}

`Community Activity List`的資料僅在Adobe Analytics取得社群網站的授權並設定時才可用。

請參閱[社群功能分析設定](analytics.md)。

## 將社群活動清單添加到頁面{#adding-a-community-activity-list-to-a-page}

若要在作者模式下將`Community Activity List`元件新增至頁面，請找出該元件`Communities / Community Activity List`並將它拖曳至頁面上。

如需必要資訊，請造訪[Communities Components Basics](basics.md)。

首次放置在社群網站頁面時，元件的顯示方式如下：

![chlimage_1-227](assets/chlimage_1-227.png)

## 配置社區活動清單{#configuring-community-activity-list}

選擇要訪問的已放置的`Community Activity List`元件，並選擇`Configure`表徵圖以開啟編輯對話框。

![chlimage_1-228](assets/chlimage_1-228.png)

在&#x200B;**[!UICONTROL Comments]**&#x200B;標籤下，指定上傳檔案的注釋是否及顯示方式：

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

   預設值為10。

* **[!UICONTROL 活動類型]**

   選擇其中一個
   * `Views`（頁面瀏覽）
   * `Posts`（建立UGC）
   * `Follows`
   * `Likes`

   預設為「檢視」。

* **[!UICONTROL 時間段]**

   選擇其中一個
   * `Last 24 hours`
   * `Last 7 days`
   * `Last 30 days`
   * `Last 90 days`
   * `This year (since Jan 1st)`
   * `Total`

   預設值為`Total`。

* **[!UICONTROL 內容路徑]**

   提供將活動範圍限定在網站子集的能力，例如特定部落格。

   預設為整個社群網站。

* **[!UICONTROL 成員人數彙總]**

   取消勾選（關閉）時，只會計入頂層貼文。 例如，如果內容是根頁面（預設值），則`Posts`的`Activity Type`將不會顯示任何活動，因為無法將內容張貼至根頁面。 勾選後，會包含所有子系頁面的計數。

   已勾選預設值。

## 包含4個元件{#example-page-with-components}的示例頁

**頂級** 訪客組態：類型=成員，活動類型=視圖

**熱門貢** 獻者組態：類型=成員，活動類型=貼文

**主要** 內容組態：類型=內容，活動類型=檢視，

**趨勢** Contentconfig:類型=內容，活動類型=貼文

![chlimage_1-230](assets/chlimage_1-230.png)

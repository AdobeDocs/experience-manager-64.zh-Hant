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


# 活動趨勢 {#activity-trends}

## 簡介 {#introduction}

元 `Community Activity List` 件可新增成員的貼文和檢視以及內容貼文和檢視的相關趨勢資訊。

本節說明

* 將元件 `Community Activity List` 新增至社 [群網站](overview.md#community-sites)

* 元件的配置設 `Community Activity List` 置

## 需求 {#requirement}

只有在Adobe Analytics `Community Activity List` 取得社群網站的授權並設定後，才能取得社群網站的資料。

請參閱 [社群功能的Analytics設定](analytics.md)。

## 將社群活動清單添加到頁面 {#adding-a-community-activity-list-to-a-page}

若要在作 `Community Activity List` 者模式下將元件新增至頁面，請找出元 `Communities / Community Activity List` 件並將它拖曳至頁面上。

如需必要資訊，請造 [訪Communities Components Basics](basics.md)。

首次放置在社群網站頁面時，元件的顯示方式如下：

![chlimage_1-227](assets/chlimage_1-227.png)

## 配置社區活動清單  {#configuring-community-activity-list}

選擇要訪問 `Community Activity List` 的已放置元件，並選 `Configure` 擇開啟編輯對話框的表徵圖。

![chlimage_1-228](assets/chlimage_1-228.png)

在「注 **[!UICONTROL 釋]** 」標籤下，指定上傳檔案的注釋是否及顯示方式：

![chlimage_1-229](assets/chlimage_1-229.png)

* **[!UICONTROL 類型]**

   指定要顯示社群成員或使用者產生內容(UGC)的相關資料。

   從
   * `Members`
   * `Content`

   預設為 `Members`。

* **[!UICONTROL 顯示標題]**

   要顯示在資料上方的描述性標題，例如 `Trending Content`。

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

   預設為 `Total`。

* **[!UICONTROL 內容路徑]**

   提供將活動範圍限定在網站子集的能力，例如特定部落格。

   預設為整個社群網站。

* **[!UICONTROL 成員人數彙總]**

   取消勾選（關閉）時，只會計入頂層貼文。 例如，如果內容是根頁面（預設值），則 `Activity Type`中 `Posts`的不會顯示任何活動，因為無法將內容張貼至根頁面。 勾選後，會包含所有子系頁面的計數。

   已勾選預設值。

## 包含4個元件的範例頁面 {#example-page-with-components}

**熱門訪客** 設定： 類型=成員，活動類型=視圖

**熱門參與者** (Top Contributors)設定： 類型=成員，活動類型=貼文

**主要內容** (Top Content)設定： 類型=內容，活動類型=檢視，

**趨勢內容** 設定： 類型=內容，活動類型=貼文

![chlimage_1-230](assets/chlimage_1-230.png)

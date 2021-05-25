---
title: 活動資料流功能
seo-title: 活動資料流功能
description: 已登錄社區成員的活動
seo-description: 已登錄社區成員的活動
uuid: 8a05a5ed-0edf-4528-a145-f9dc37d10247
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ccaebb4c-cc1c-4ee7-b080-99667f348427
exl-id: e62b7c0d-5004-4672-9fdc-566ece2785c9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# 活動資料流功能{#activity-streams-feature}

## 簡介 {#introduction}

已登錄社區成員的活動，例如發佈到論壇或部落格，被收集到流中，該流可以通過`Activity Streams`元件的配置以各種方式被過濾和顯示。

當社群成員關注感興趣的帖子或關注其他社區成員的活動時，跟隨的能力將添加另一個活動視圖。

本檔案的本節說明

* 新增活動資料流元件至AEM網站
* 活動資料流元件的組態設定

## 新增活動資料流至頁面{#adding-activity-streams-to-a-page}

如果想在製作模式中將`Activity Streams`元件新增至頁面，請使用元件瀏覽器來找出

* `Communities / Activity Streams`

並將其拖曳至應該顯示活動資料流的頁面上。

如需必要資訊，請造訪[Communities Components Basics](basics.md)。

包含[必要的用戶端程式庫](essentials-activities.md#essentials-for-client-side)時，以下是`Activity Streams`元件的顯示方式：

![chlimage_1-195](assets/chlimage_1-195.png)

## 配置活動流{#configuring-activity-streams}

選取要存取的放置`Activity Streams`元件，並選取開啟編輯對話方塊的`Configure`圖示。

![chlimage_1-196](assets/chlimage_1-196.png)

在&#x200B;**[!UICONTROL 使用者活動]**&#x200B;標籤下，指定要顯示的活動：

![chlimage_1-197](assets/chlimage_1-197.png)

* **[!UICONTROL 活動數目]**
上限要顯示的活動數
* **[!UICONTROL 流資源]**
路徑保留為空，以預設為社區站點或社區組。資料流資源路徑標識活動源。 預設為空白。
* **[!UICONTROL 顯示用戶活]**
動視圖選中後，活動頁將包含一個頁簽，該頁簽將根據當前成員在社區內生成的活動來篩選活動。已勾選預設值。
* **[!UICONTROL 顯示所有活]**
動視圖如果選中此選項，則活動頁將包含一個頁簽，其中包含當前成員有權訪問的社區內生成的所有活動。已勾選預設值。
* **[!UICONTROL 顯示]**
後視圖如果選中此選項，則活動頁將包含一個頁簽，該頁簽根據當前成員正在跟蹤的活動篩選活動。已勾選預設值。

## 正在查看{#following-view}

必須配置元件以啟用以下功能。 允許下列功能：[blog](blog-feature.md)、[forum](forum.md)、[QnA](working-with-qna.md)、[日曆](calendar.md)、[filelibrary](file-library.md)和[注釋](comments.md)。

![chlimage_1-198](assets/chlimage_1-198.png)

**Follow**&#x200B;按鈕提供了一種方法，可以將條目作為活動跟蹤，[notifications](notifications.md)和/或[訂閱](subscriptions.md)。 每次選擇&#x200B;**Follow**&#x200B;按鈕時，都可以開啟或關閉選擇。 `Email Subscriptions`選項僅在配置時存在。

如果選擇了下列任何方法，則按鈕的文本將更改為&#x200B;**Following**。 為方便起見，可以選取`Unfollow All`來關閉所有方法。

將顯示&#x200B;**Follow**&#x200B;按鈕：

* 查看其他成員的配置檔案時
* 在主功能頁面，如論壇、QnA和部落格
   * 遵循該一般功能的所有活動

* 對於特定條目，如論壇主題、QnA問題或部落格文章
   * 跟蹤該特定條目的所有活動

## 其他資訊 {#additional-information}

如需詳細資訊，請參閱開發人員的[Activity Streams Essentials](essentials-activities.md)頁面。

---
title: 活動串流功能
seo-title: 活動串流功能
description: 已登入社區成員的活動
seo-description: 已登入社區成員的活動
uuid: 8a05a5ed-0edf-4528-a145-f9dc37d10247
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ccaebb4c-cc1c-4ee7-b080-99667f348427
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---


# 活動串流功能{#activity-streams-feature}

## 簡介 {#introduction}

在社區成員中籤名的活動（如張貼到論壇或部落格）被收集到流中，該流可通過配置`Activity Streams`元件以各種方式被過濾和顯示。

關注能力為社區成員關注感興趣的帖子或關注其他社區成員的活動添加了另一種活動視圖。

本節說明

* 新增活動串流元件至AEM網站
* Activity Streams元件的組態設定

## 新增活動串流至頁面{#adding-activity-streams-to-a-page}

如果想要在作者模式下將`Activity Streams`元件新增至頁面，請使用元件瀏覽器來尋找

* `Communities / Activity Streams`

並將它拖曳至應顯示活動串流的頁面上。

如需必要資訊，請造訪[Communities Components Basics](basics.md)。

當包含[必要的用戶端程式庫](essentials-activities.md#essentials-for-client-side)時，`Activity Streams`元件的顯示方式如下：

![chlimage_1-195](assets/chlimage_1-195.png)

## 配置活動流{#configuring-activity-streams}

選擇要訪問的已放置的`Activity Streams`元件，並選擇`Configure`表徵圖以開啟編輯對話框。

![chlimage_1-196](assets/chlimage_1-196.png)

在&#x200B;**[!UICONTROL 使用者活動]**&#x200B;標籤下，指定要顯示的活動：

![chlimage_1-197](assets/chlimage_1-197.png)

* **[!UICONTROL 活動數目]**
上限要顯示的活動數
* **[!UICONTROL 串流資源]**
路徑留空，以預設為社群網站或社群群組。串流資源路徑可識別活動的來源。 預設為空白。
* **[!UICONTROL 「顯示用戶活]**
動視圖」選中後，活動頁將包含一個頁籤，該頁籤根據當前成員在社區中生成的活動進行篩選。已勾選預設值。
* **[!UICONTROL 顯示所有活]**
動視圖如果選中此選項，則活動頁將包含一個頁籤，其中包含當前成員有權訪問的社區內生成的所有活動。已勾選預設值。
* **[!UICONTROL 顯示以下]**
視圖如果選中，活動頁將包含一個頁籤，該頁籤會根據當前成員正在跟蹤的活動進行篩選。已勾選預設值。

## 查看{#following-view}後

必須配置元件以啟用以下功能。 允許下列功能：[blog](blog-feature.md)、[論壇](forum.md)、[QnA](working-with-qna.md)、[日曆](calendar.md)、[filebrary](file-library.md)和[注釋](comments.md)。

![chlimage_1-198](assets/chlimage_1-198.png)

**Follow**&#x200B;按鈕提供了以活動、[通知](notifications.md)和／或[訂閱](subscriptions.md)跟蹤條目的方法。 每次選擇&#x200B;**Follow**&#x200B;按鈕時，都可以開啟或關閉選擇。 `Email Subscriptions`選項僅在配置時顯示。

如果選擇了任何下列方法，則按鈕的文本將更改為&#x200B;**Following**。 為方便起見，您可以選取`Unfollow All`來關閉所有方法。

將顯示&#x200B;**Follow**&#x200B;按鈕：

* 查看其他成員的配置檔案時
* 在主要功能頁面上，例如論壇、QnA和部落格
   * 遵循該一般功能的所有活動

* 針對特定項目，例如論壇主題、QnA問題或部落格文章
   * 跟蹤該特定條目的所有活動

## 其他資訊 {#additional-information}

有關詳細資訊，請參閱開發人員的[Activity Streams Essentials](essentials-activities.md)頁面。

---
title: Communities通知
seo-title: Communities Notifications
description: AEM Communities會通知顯示已登入社群成員感興趣的事件
seo-description: AEM Communities has notifications that display events of interest to the signed-in community member
uuid: d6ef12f1-7367-49a5-b891-56800a38b2ab
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 47201e2d-338d-40e0-af82-c681a552807b
role: Admin
exl-id: f6c6619e-b386-4d34-9d17-654d7c97aedd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 2%

---

# Communities通知 {#communities-notifications}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 概觀 {#overview}

AEM Communities提供通知區段，顯示已登入社群成員感興趣的事件。

通知類似 [活動](essentials-activities.md) 和 [訂閱](subscriptions.md) 因為

* 成員發佈內容
* 選擇跟隨另一成員的成員
* 選擇遵循特定主題、文章和其他內容主題的成員

活動和訂閱中的通知的區別為

* 通知區段的連結一律會顯示在社群網站的標題中
   * 活動需要 [活動流函式](functions.md#activity-stream-function) 包含在社群網站結構中
   * 訂閱需要 [電子郵件設定](email.md)
* 通知的實施是通過可擴展和可插拔的通道
   * 活動僅可在Web上使用
   * 訂閱僅限使用電子郵件

As of Communities [FP1](deploy-communities.md#latestfeaturepack)，可用的通知通道為

* 網路通道，使用 `Notifications` 連結
* 電子郵件通道，正確設定電子郵件時可用

未來的通道包括行動裝置和案頭裝置。

### 要求 {#requirements}

**設定電子郵件**

必須設定電子郵件，電子郵件通道才能運作通知。

如需設定電子郵件的指示，請參閱 [設定電子郵件](analytics.md).

**啟用跟蹤**

必須配置元件以啟用以下功能。 允許下列項目的功能 [部落格](blog-feature.md), [論壇](forum.md), [QnA](working-with-qna.md), [日曆](calendar.md), [檔案庫](file-library.md)，和 [評論](comments.md).

請注意

* 社群中使用的元件 [網站範本](sites.md) 和 [群組範本](tools-groups.md) 可能已配置為允許以下操作

* 成員配置檔案已配置為允許其他成員遵循

## 來自下列的通知 {#notifications-from-following}

![chlimage_1-254](assets/chlimage_1-254.png)

此 **追隨** 按鈕提供可在活動、訂閱和/或通知後跟隨項目的方法。 每次 **追隨** 按鈕，則可以開啟或關閉選取項。 此 `Email Subscriptions` 只有在配置後才會顯示選擇。

如果選取下列任何方法，按鈕的文字會變更為 **追隨**. 為方便起見，您可以選擇 `Unfollow All` 切換所有方法。

此 **追隨** 按鈕將出現

* 查看其他成員的配置檔案時
* 在主功能頁面，如論壇、QnA和部落格
   * 遵循該一般功能的所有活動
* 對於特定條目，如論壇主題、QnA問題或部落格文章
   * 跟蹤該特定條目的所有活動

## 管理通知設定 {#managing-notification-settings}

通過從「通知」頁中選擇「通知設定」連結，每個成員都可以管理接收通知的方式。

一律會啟用Web通道。

![chlimage_1-255](assets/chlimage_1-255.png)

依賴適當 [電子郵件設定](email.md)，提供與網頁頻道相同的設定。

電子郵件通道預設為關閉。

![chlimage_1-256](assets/chlimage_1-256.png)

成員可以開啟它，但仍取決於所配置的電子郵件。

![chlimage_1-257](assets/chlimage_1-257.png)

## 檢視通知 {#viewing-notifications}

### Web通知 {#web-notifications}

A [嚮導建立的社群站點](sites-console.md) 現在包含連結至 `Notifications` 功能。 與訊息不同，會為每個社群網站建立通知，而訊息必須在網站建立程式期間啟用。

造訪已發佈的網站時，請選取 `Notifications` 連結將顯示成員的所有通知。

![chlimage_1-258](assets/chlimage_1-258.png)

### 電子郵件通知 {#email-notifications}

啟用電子郵件通道時，成員會收到包含指向Web上內容的連結的電子郵件。

![chlimage_1-259](assets/chlimage_1-259.png)

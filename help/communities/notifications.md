---
title: Communities通知
seo-title: Communities通知
description: AEM Communities會通知顯示已登入社群成員感興趣的事件
seo-description: AEM Communities會通知顯示已登入社群成員感興趣的事件
uuid: d6ef12f1-7367-49a5-b891-56800a38b2ab
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 47201e2d-338d-40e0-af82-c681a552807b
role: Admin
exl-id: f6c6619e-b386-4d34-9d17-654d7c97aedd
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# Communities通知 {#communities-notifications}

## 概覽 {#overview}

AEM Communities提供通知區段，顯示已登入社群成員感興趣的事件。

通知類似於[activities](essentials-activities.md)和[subscriptions](subscriptions.md)，因為它們可能是由

* 成員發佈內容
* 選擇跟隨另一成員的成員
* 選擇遵循特定主題、文章和其他內容主題的成員

活動和訂閱中的通知的區別為

* 通知區段的連結一律會顯示在社群網站的標題中
   * 活動要求將[活動資料流函式](functions.md#activity-stream-function)包含在社群網站的結構中
   * 訂閱需要[電子郵件的設定](email.md)
* 通知的實施是通過可擴展和可插拔的通道
   * 活動僅可在Web上使用
   * 訂閱僅限使用電子郵件

自Communities [FP1](deploy-communities.md#latestfeaturepack)起，可用的通知通道為

* 使用`Notifications`連結存取的Web通道
* 電子郵件通道，正確設定電子郵件時可用

未來的通道包括行動裝置和案頭裝置。

### 需求 {#requirements}

**設定電子郵件**

必須設定電子郵件，電子郵件通道才能運作通知。

有關設定電子郵件的說明，請參閱[配置電子郵件](analytics.md)。

**啟用跟蹤**

必須配置元件以啟用以下功能。 允許下列功能：[blog](blog-feature.md)、[forum](forum.md)、[QnA](working-with-qna.md)、[日曆](calendar.md)、[filelibrary](file-library.md)和[注釋](comments.md)。

請注意

* 在社區[站點模板](sites.md)和[組模板](tools-groups.md)中使用的元件可能已配置為允許以下操作

* 成員配置檔案已配置為允許其他成員遵循

## 來自下列的通知 {#notifications-from-following}

![chlimage_1-254](assets/chlimage_1-254.png)

**Follow**&#x200B;按鈕提供了一種方法，可以將條目作為活動、訂閱和/或通知跟蹤。 每次選擇&#x200B;**Follow**&#x200B;按鈕時，都可以開啟或關閉選擇。 `Email Subscriptions`選項僅在配置時存在。

如果選擇了下列任何方法，則按鈕的文本將更改為&#x200B;**Following**。 為方便起見，可以選取`Unfollow All`來關閉所有方法。

將顯示&#x200B;**Follow**&#x200B;按鈕

* 查看其他成員的配置檔案時
* 在主功能頁面，如論壇、QnA和部落格
   * 遵循該一般功能的所有活動
* 對於特定條目，如論壇主題、QnA問題或部落格文章
   * 跟蹤該特定條目的所有活動

## 管理通知設定 {#managing-notification-settings}

通過從「通知」頁中選擇「通知設定」連結，每個成員都可以管理接收通知的方式。

一律會啟用Web通道。

![chlimage_1-255](assets/chlimage_1-255.png)

電子郵件通道依賴於電子郵件](email.md)的適當[配置，提供與Web通道相同的設定。

電子郵件通道預設為關閉。

![chlimage_1-256](assets/chlimage_1-256.png)

成員可以開啟它，但仍取決於所配置的電子郵件。

![chlimage_1-257](assets/chlimage_1-257.png)

## 檢視通知 {#viewing-notifications}

### Web通知 {#web-notifications}

建立的[精靈社群網站](sites-console.md)現在包含橫幅上方網站標題列中`Notifications`功能的連結。 與訊息不同，會為每個社群網站建立通知，而訊息必須在網站建立程式期間啟用。

訪問已發佈的站點時，選擇`Notifications`連結將顯示該成員的所有通知。

![chlimage_1-258](assets/chlimage_1-258.png)

### 電子郵件通知 {#email-notifications}

啟用電子郵件通道時，成員會收到包含指向Web上內容的連結的電子郵件。

![chlimage_1-259](assets/chlimage_1-259.png)

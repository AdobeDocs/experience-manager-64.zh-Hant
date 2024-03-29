---
title: Communities 訂閱
seo-title: Communities Subscriptions
description: 社群成員透過電子郵件與其他成員互動
seo-description: Community members interact with other members through email
uuid: a4b98769-c219-4e18-8e80-9a806ab979ff
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 33c85af4-4c56-487a-ba60-55211cb9f72c
role: Admin
exl-id: 8a756328-0405-49b7-b94d-3dd5a87c782a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 3%

---

# Communities 訂閱 {#communities-subscriptions}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 概觀 {#overview}

As of Communities [FP1](deploy-communities.md#latestfeaturepack)，社群成員可能會使用稱為訂閱的功能，透過電子郵件與社群互動。

訂閱類似於 [通知](notifications.md) 在關注部落格文章、論壇主題或QnA問題時，可以訂閱。

訂閱與通知的區別在於：

* 跟隨其他成員時，成員不得訂閱
* 成員只需選擇 `Email Subscriptions` 追隨
* 設定電子郵件回覆時，成員只要回覆收到的電子郵件，即可有效地張貼內容

### 要求 {#requirements}

**設定電子郵件**

必須設定電子郵件，訂閱才能正常運作，成員才能透過電子郵件回覆。

如需設定電子郵件的指示，請參閱 [設定電子郵件](email.md).

**啟用訂閱與追蹤**

必須配置元件以啟用訂閱 *和* 下。 允許訂閱的功能為 [部落格](blog-feature.md), [論壇](forum.md) 和 [QnA](working-with-qna.md).

## 來自下列項目的訂閱 {#subscriptions-from-following}

![chlimage_1-5](assets/chlimage_1-5.png)

此 **追隨** 按鈕提供可在活動、訂閱和/或通知後跟隨項目的方法。 每次 **追隨** 按鈕，則可以開啟或關閉選取項。

如果選取下列任何方法，按鈕的文字會變更為 **追隨**. 為方便起見，您可以選擇 `Unfollow All` 切換所有方法。

此 **追隨** 按鈕將包含 `Email Subscriptions` 選項（僅當將論壇、QnA或部落格配置為啟用電子郵件訂閱時）。 此按鈕隨即顯示

* 在啟用的論壇、QnA或部落格的主功能頁面上

   * 會針對該功能下的所有活動傳送電子郵件

* 對於特定條目，如論壇主題、QnA問題或部落格文章

   * 當該特定項目有活動時，會傳送電子郵件

## 透過電子郵件回覆 {#reply-by-email}

電子郵件為 [已設定為以電子郵件回覆](email.md#configure-polling-importer)，訂閱的成員將會收到一封包含已張貼內容的電子郵件，以及線上內容的連結。

如果他們回覆電子郵件，他們在回覆中輸入的內容將顯示為線上內容。

![chlimage_1-6](assets/chlimage_1-6.png)

張貼回覆所花的時間，由 [輪詢匯入工具的更新間隔](email.md#configure-polling-importer).

![chlimage_1-7](assets/chlimage_1-7.png)

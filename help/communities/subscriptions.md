---
title: 社群訂閱
seo-title: 社群訂閱
description: 'Community members interact with other members through email '
seo-description: 'Community members interact with other members through email '
uuid: a4b98769-c219-4e18-8e80-9a806ab979ff
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 33c85af4-4c56-487a-ba60-55211cb9f72c
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---


# 社群訂閱 {#communities-subscriptions}

## 概覽 {#overview}

As of Communities [FP1](deploy-communities.md#latestfeaturepack), community members may interact with the community through email using a feature referrred to as subscriptions.

Subscriptions are similar to [notifications](notifications.md) as members may subscribe when following blog articles, forum topics or QnA questions.

What distinguishes subscriptions from notifications is:

* 當追隨其他成員時，成員不得訂閱
* 成員唯一要執行的操作是選擇以 `Email Subscriptions` 下操作
* 設定電子郵件回覆時，會員只要回覆收到的電子郵件，就可以有效地張貼內容

### 需求 {#requirements}

**設定電子郵件**

Email must be configured in order for subscriptions to be functional and for members to reply by email.

如需設定電子郵件的指示，請參閱 [設定電子郵件](email.md)。

**Enable Subscriptions and Follow**

Components must be configured to enable subscriptions *and* following. Features that allow subscriptions are [blog](blog-feature.md), [forum](forum.md) and [QnA](working-with-qna.md).

## Subscriptions from Following {#subscriptions-from-following}

![chlimage_1-5](assets/chlimage_1-5.png)

The **Follow** button provides a means to follow entries as activities, subscriptions and/or notifications. Each time the **Follow** button is selected, it is possible to toggle on or off a selection.

If any method of following is selected, the text of the button changes to **Following**. For convenience, it is possible to select `Unfollow All` to toggle off all methods.

只有在 **將論壇、QnA或部**`Email Subscriptions` 落格設定為啟用電子郵件訂閱時，「關注」按鈕才會包含此選項。 此按鈕將會出現

* 在啟用論壇、QnA或部落格的主要功能頁面上

   * 會針對該功能下的所有活動傳送電子郵件

* For a specific entry, such as a forum topic, QnA question, or blog article

   * Will send an email when there is activity for that specific entry

## Reply by Email {#reply-by-email}

當電子郵件設 [定為以電子郵件回覆](email.md#configure-polling-importer)，訂閱的會員將會收到電子郵件，內含已張貼的內容和線上內容的連結。

If they reply to the email, the content they enter in the reply will appear as content online.

![chlimage_1-6](assets/chlimage_1-6.png)

The amount of time it takes for a reply to be posted is controlled by the [polling importer&#39;s update interval](email.md#configure-polling-importer).

![chlimage_1-7](assets/chlimage_1-7.png)


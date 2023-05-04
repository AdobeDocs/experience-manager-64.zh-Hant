---
title: 使用投票
seo-title: Using Voting
description: 將投票元件新增至頁面
seo-description: Adding the Voting component to a page
uuid: 56e6cced-2f2d-434a-8fde-92a6c2478a04
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 071cac6d-05c5-47ab-85bc-ead6693ca1f4
exl-id: 660a7106-0c21-4073-8319-4d6d20b9bc49
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 7%

---

# 使用投票 {#using-voting}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

此 `Voting` 元件是一種有用的工具，它允許社區成員對特定內容片段（如QnA元件內的答案）進行評分。 使用 `Voting` 元件，成員選擇向上或向下箭頭以指示其意見。

## 新增投票至頁面 {#adding-voting-to-a-page}

新增 `Voting` 在製作模式中，使用元件瀏覽器來尋找 `Communities / Voting` 並將其拖曳至頁面上的位置，例如與功能相對的位置，供使用者投票。

如需必要資訊，請造訪 [Communities元件基本知識](basics.md).

當 [必要的用戶端程式庫](essentials-voting.md#essentials-for-client-side) 包含在內，以下為方式 `Voting` 元件隨即顯示。

![chlimage_1-307](assets/chlimage_1-307.png)

## 配置投票 {#configuring-voting}

選取已放置的 `Voting` 要存取的元件並選取 `Configure` 表徵圖，開啟「編輯」對話框。

![chlimage_1-308](assets/chlimage_1-308.png)

在 **[!UICONTROL 文字與標籤]** 頁簽，指定用於記錄投票的屬性。

![chlimage_1-309](assets/chlimage_1-309.png)

* **[!UICONTROL 正面回應標籤]**
(
*必填*)正面回應的內部屬性名稱。

* **[!UICONTROL 負面回應標籤]**
(
*必填*)負回應的內部屬性名稱。

* **[!UICONTROL 記帳名稱]**
(
*必填*)此投票元件例項的內部、可識別屬性名稱。

## 網站訪客體驗 {#site-visitor-experience}

### 成員 {#members}

成員只能投一票，但可隨時更改其投票。

### 匿名 {#anonymous}

不支援匿名投票。 網站訪客必須註冊（成為會員）並登入以參與一次投票。

## 其他資訊 {#additional-information}

如需詳細資訊，請參閱 [投票要點](essentials-voting.md) 頁面。

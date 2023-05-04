---
title: 使用贊
seo-title: Using Liking
description: 新增及設定按贊元件
seo-description: Adding and configuring the Liking component
uuid: 12103ab7-1a1c-49cd-8dad-6c7508b4550e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: dcde4e03-78ab-4779-96a1-05ac41f14701
exl-id: b5918a54-ef7b-4b3f-bca7-ed0344bab4aa
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 7%

---

# 使用贊 {#using-liking}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

此 `Liking`元件是實用的工具，可讓使用者對特定內容（例如論壇內的意見）發表意見。 使用 `Liking`元件，成員選擇心臟表徵圖以指示正面意見。

## 對頁面按贊 {#adding-liking-to-a-page}

新增 `Liking` 在製作模式中，使用元件瀏覽器來尋找

* `Communities / Liking`

並將其拖曳至頁面上的位置，例如與功能相對的位置，供使用者按贊。

如需必要資訊，請造訪 [Communities元件基本知識](basics.md).

當 [必要的用戶端程式庫](essentials-liking.md#essentials-for-client-side) 包含在內，以下為方式 `Liking` 元件隨即顯示。

![chlimage_1-93](assets/chlimage_1-93.png)

## 設定贊 {#configuring-liking}

選取已放置的 `Liking` 要存取的元件並選取 `Configure` 表徵圖，開啟「編輯」對話框。

![chlimage_1-94](assets/chlimage_1-94.png)

在 **[!UICONTROL 文字與標籤]** 頁簽，指定用於記錄按贊的屬性。

![chlimage_1-95](assets/chlimage_1-95.png)

* **[!UICONTROL 正面回應標籤]**
(
*必填*)正面回應的屬性名稱。

* **[!UICONTROL 負面回應標籤]**
(
*必填*)負回應的屬性名稱。

* **[!UICONTROL 記帳名稱]**
(
*必填*)此投票元件例項的內部、可識別屬性名稱。

## 網站訪客體驗 {#site-visitor-experience}

### 成員 {#members}

會員可隨時變更其喜好。

### 匿名 {#anonymous}

不支援匿名贊。 網站訪客必須註冊（成為會員）並登入以參與按贊。

## 其他資訊 {#additional-information}

如需詳細資訊，請參閱 [按贊要點](essentials-liking.md) 頁面。

---
title: 精選內容功能
seo-title: Featured Content Feature
description: 「精選內容」功能可讓登入的網站訪客反白標示內容
seo-description: The Featured Content feature lets signed-in site visitors highlight content
uuid: 7a2ff570-01bb-46fb-8d66-3b47e2efa72e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ee39435d-80f5-4758-ae01-1ea0d221b00b
exl-id: a0dcffed-1040-4d6d-b8e9-3bbe5f30deb4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 6%

---

# 精選內容功能 {#featured-content-feature}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 簡介 {#introduction}

精選內容功能提供發佈環境中登入網站訪客（社群成員）的區域，突顯

* [部落格](blog-feature.md)
* [日曆](calendar.md)
* [論壇](forum.md)
* [構思](ideation-feature.md)
* [QnA](working-with-qna.md)

一旦將內容標示為特色內容，就會列在此元件中，這些內容可能會放置在特定登陸頁面或容易吸引社群成員注意的區域中。

每個元件可能允許或不允許使用特徵內容的功能。

本檔案的本節說明

* 將精選內容新增至社群網站
* 的組態設定 `Featured Content`元件

## 將精選內容新增至頁面 {#adding-featured-content-to-a-page}

新增 `Featured Content` 在製作模式中，使用元件瀏覽器來尋找

* `Communities / Featured Content`

並將其拖曳至應出現精選內容的頁面上。

如需必要資訊，請造訪 [Communities元件基本知識](basics.md).

當 [必要的用戶端程式庫](essentials-featured.md#essentials-for-client-side) 包含在內，以下為方式 `Featured Content`元件隨即出現：

![chlimage_1-13](assets/chlimage_1-13.png)

## 設定精選內容 {#configuring-featured-content}

選取已放置的 `Featured Content` 要存取的元件並選取 `Configure` 表徵圖，開啟「編輯」對話框。

![chlimage_1-14](assets/chlimage_1-14.png) ![chlimage_1-15](assets/chlimage_1-15.png)

### 設定標籤 {#settings-tab}

在 **[!UICONTROL 設定]** 標籤，識別要功能的內容：

* **[!UICONTROL 顯示名稱]**
精選內容清單的標題。 例如 
`Featured Questions` 或 `Featured Ideas`. 預設為 `Featured Content` 如果留空。

* **[!UICONTROL 主要內容的位置]**

   *（必要）* 瀏覽至包含可能具有功能之內容的頁面（該頁面的元件必須設定為「允許精選內容」）。 例如 `/content/sites/engage/en/forum`

* **[!UICONTROL 顯示限制]**
要顯示的精選內容數量上限。 預設為5。

## 網站訪客體驗 {#site-visitor-experience}

將內容標幟為精選內容的功能需要版主權限。

版主檢視張貼內容時，可存取內容內協調旗標，包括新的 `Feature` 標籤。

![chlimage_1-16](assets/chlimage_1-16.png)

標幟為功能後，模型標幟就會變成 `Unfeature`.

包含 `Featured Content` 元件，現在將包含此貼文。

![chlimage_1-17](assets/chlimage_1-17.png)

`Read More` 是實際貼文的連結。

## 其他資訊 {#additional-information}

如需詳細資訊，請參閱 [精選內容](essentials-featured.md) 頁面。

若要將內容標幟為特色，請參閱 [協調使用者產生的內容](moderate-ugc.md).

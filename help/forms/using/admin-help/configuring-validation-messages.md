---
title: 設定驗證訊息
seo-title: Configuring validation messages
description: 了解如何指定驗證訊息的顯示方式及其相對於網頁瀏覽器中傳回的表單的位置。
seo-description: Learn how to specify how validation messages are displayed and their location relative to the form returned in the web browser.
uuid: f6bff4fa-f90f-4135-ae40-7ab3d3613122
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 5f2f8129-e45e-4f3f-ae30-c09330d0e152
exl-id: 2016ac85-12a1-42cb-bc03-fced94947010
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 3%

---

# 設定驗證訊息 {#configuring-validation-messages}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

對於呈現為HTML的表單，會為使用者顯示發生的表單驗證錯誤。 您可以自訂驗證訊息的顯示方式。 根據驗證消息的顯示位置，您還可以控制窗體中消息的位置和框架邊框的大小。

## 指定驗證訊息的顯示方式 {#specify-how-validation-messages-are-displayed}

1. 在管理控制台中，按一下「服務>表單」。
1. 在「驗證輸出」下，在「報告」清單中，選擇以下選項之一：

   **消息框：** 在單獨的對話框中顯示驗證消息。

   **框架：** 在同一窗口的框架內顯示驗證消息。

   **無框架：** 在同一窗口中顯示驗證消息。 此值為預設值。

   **透過API（含資料）:** 透過API（含資料）傳回驗證訊息。 驗證訊息不會顯示在畫面上。

   **透過API（含表單）:** 若要透過API傳回驗證訊息（透過表單）。 驗證訊息不會顯示在畫面上。

   **無：** 不顯示驗證訊息。

1. 按一下「儲存」。

## 指定驗證消息相對於在Web瀏覽器中返回的表單的位置 {#specify-the-location-of-validation-messages-relative-to-the-form-returned-in-the-web-browser}

當「報告」設定為「幀」或「無幀」時，可以指定驗證消息的位置。

1. 在「驗證輸出」(Validation Output)下，在「位置」(Position)清單中，選擇以下選項之一：

   **左：** 在Web瀏覽器左側顯示驗證消息。

   **對：** 在Web瀏覽器的右側顯示驗證消息。

   **頂端**:在Web瀏覽器頂部顯示驗證消息。 此值為預設值。

   **底部**:在Web瀏覽器底部顯示驗證消息。

1. 按一下「儲存」。

## 指定邊框大小 {#specify-the-frame-border-size}

當「報告」設定為「框架」時，可以指定框架邊框大小。

1. 在「驗證輸出」下的「邊框大小」框中，以像素為單位鍵入邊框的大小。

   邊框大小必須等於或大於0。 預設值為 1。

1. 按一下「儲存」。

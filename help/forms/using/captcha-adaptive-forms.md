---
title: 在最適化表單中使用CAPTCHA
seo-title: Using CAPTCHA in adaptive forms
description: 了解如何在最適化表單中設定AEM CAPTCHA或Google reCAPTCHA服務。
seo-description: Learn how to configure AEM CAPTCHA or Google reCAPTCHA service in adaptive forms.
uuid: 8bcb0dd7-b43c-4a36-8f6b-7875b68f9ba1
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author, adaptive_forms
discoiquuid: 32369b0b-5abf-487d-ae6b-972c254eb7e2
feature: Adaptive Forms
exl-id: 1129004b-5e8b-42fd-98ed-f203edde93b9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%

---

# 在最適化表單中使用CAPTCHA {#using-captcha-in-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

驗證碼（Captcha，完全自動化的公共圖靈測試，可區分電腦和人）是線上交易中常用的一種程式，用於區分人和自動程式或機器人。 這會帶來挑戰並評估使用者回應，以判斷其為與網站互動的人或機器人。 它可防止機器人張貼垃圾訊息或惡意用途，讓使用者在測試失敗時繼續執行，有助於確保線上交易的安全。

AEM Forms支援適用性表單中的驗證碼。 您可以使用Google的reCAPTCHA服務來實作CAPTCHA。

>[!NOTE]
>
>AEM Forms僅支援reCaptcha v2。 不支援任何其他版本。
>
>AEM Forms應用程式的離線模式不支援適用性表單中的驗證碼。

## 配置ReCAPTCHA服務(由Google提供) {#google-recaptcha}

表單作者可使用Google提供的reCAPTCHA服務，在最適化表單中實作CAPTCHA。 它提供進階驗證碼功能，可保護您的網站。 如需reCAPTCHA如何運作的詳細資訊，請參閱 [Google reCAPTCHA](https://developers.google.com/recaptcha/).

![recapcha](assets/recaptcha.png)

若要在AEM Forms中實作reCAPTCHA服務：

1. 取得 [reCAPTCHA API金鑰組](https://www.google.com/recaptcha/admin) 從Google。 其中包含網站金鑰和機密。
1. 為雲端服務建立設定容器。

   1. 前往 **[!UICONTROL 工具>一般>設定瀏覽器]**.
      * 請參閱 [設定瀏覽器檔案](/help/sites-administering/configurations.md) 以取得更多資訊。
   1. 請執行下列操作以啟用雲配置的全局資料夾，或跳過此步驟以建立和配置雲服務配置的其他資料夾。

      1. 在設定瀏覽器中，選取 **[!UICONTROL 全球]** 資料夾和點選 **[!UICONTROL 屬性]**.
      1. 在「配置屬性」對話框中，啟用 **[!UICONTROL 雲端設定]**.
      1. 點選 **[!UICONTROL 儲存並關閉]** 以保存配置並退出對話框。
   1. 在「設定瀏覽器」中，點選 **[!UICONTROL 建立]**.
   1. 在「建立配置」對話框中，指定資料夾的標題並啟用 **[!UICONTROL 雲端設定]**.
   1. 點選 **[!UICONTROL 建立]** 建立雲端服務設定啟用的資料夾。


1. 為reCAPTCHA設定雲端服務。

   1. 在AEM Author例項上，前往 ![工具](assets/tools.png) >  **Cloud Services**.
   1. 點選 **[!UICONTROL reCAPTCHA]**. 「設定」頁面隨即開啟。 選取在上一步驟中建立的設定容器，然後點選 **[!UICONTROL 建立]**.
   1. 為reCAPTCHA服務指定名稱、網站金鑰和密鑰，然後點選 **[!UICONTROL 建立]** 來建立雲端服務設定。
   1. 在「編輯元件」對話方塊中，指定在步驟1取得的網站和機密金鑰。 點選 **[!UICONTROL 儲存設定]** 然後點選 **[!UICONTROL 確定]** 以完成設定。

   設定reCAPTCHA服務後，即可在最適化表單中使用。 如需詳細資訊，請參閱 [在最適化表單中使用CAPTCHA](#using-captcha).

## 在最適化表單中使用CAPTCHA {#using-captcha}

若要在最適化表單中使用CAPTCHA:

1. 在編輯模式中開啟最適化表單。

   >[!NOTE]
   >
   >建立最適化表單時，請確定選取的設定容器包含reCAPTCHA雲端服務。 您也可以編輯最適化表單屬性，以變更與表單相關聯的設定容器。

1. 從元件瀏覽器中，拖放 **[!UICONTROL 驗證碼]** 元件至最適化表單。

   >[!NOTE]
   >
   >不支援在最適化表單中使用多個驗證碼元件。 此外，不建議在標示為延遲載入的面板或片段中使用CAPTCHA。

   >[!NOTE]
   >
   >驗證碼具有時效性，約一分鐘後過期。 因此，建議將驗證碼元件放置在最適化表單中的提交按鈕之前。

1. 選取您新增的驗證碼元件，然後點選 ![cppr](assets/cmppr.png) 來編輯其屬性。
1. 指定驗證碼介面工具集的標題。 預設值為 **驗證碼**. 選擇 **[!UICONTROL 隱藏標題]** 如果您不想顯示標題。
1. 從 **[!UICONTROL 驗證碼服務]** 下拉式清單，選取 **[!UICONTROL reCaptcha]** 啟用reCAPTCHA服務(如果您已按照 [ReCAPTCHA服務，由Google提供](#google-recaptcha). 從「設定」下拉式清單中選取設定。 同時，選取大小為 **[!UICONTROL 正常]** 或 **[!UICONTROL 緊湊]** 用於reCAPTCHA介面工具集。

   >[!NOTE]
   >
   >不選擇 **[!UICONTROL 預設]** 從驗證碼服務下拉式清單中取消使用，因為預設的AEM CAPTCHA服務已遭取代。

1. 儲存屬性。

reCAPTCHA服務已在最適化表單上啟用。 您可以預覽表單，並查看驗證碼正常運作。

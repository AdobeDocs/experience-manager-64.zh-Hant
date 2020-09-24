---
title: 在最適化表單中使用CAPTCHA
seo-title: 在最適化表單中使用CAPTCHA
description: 瞭解如何在最適化表單中設定AEM CAPTCHA或Google reCAPTCHA服務。
seo-description: 瞭解如何在最適化表單中設定AEM CAPTCHA或Google reCAPTCHA服務。
uuid: 8bcb0dd7-b43c-4a36-8f6b-7875b68f9ba1
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author, adaptive_forms
discoiquuid: 32369b0b-5abf-487d-ae6b-972c254eb7e2
translation-type: tm+mt
source-git-commit: a172fc329a2f73b563690624dc361aefdcb5397e
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 0%

---


# 在最適化表單中使用CAPTCHA {#using-captcha-in-adaptive-forms}

CAPTCHA（完全自動化的公共圖靈測試，可區分電腦和人類）是線上交易常用的程式，用來區分人類和自動化程式或機器人。 它會帶來挑戰，並評估使用者回應，以判斷它是人還是機器人與網站互動。 它可防止使用者在測試失敗時繼續作業，並防止機器人張貼垃圾訊息或惡意目的，以確保線上交易的安全。

AEM Forms支援最適化表單中的CAPTCHA。 您可以使用Google的reCAPTCHA服務來實作CAPTCHA。

>[!NOTE]
>
>AEM Forms僅支援reCaptcha v2。 不支援任何其他版本。
>
>AEM Forms應用程式的離線模式不支援最適化表單中的CAPTCHA。

## 依Google設定ReCAPTCHA服務 {#google-recaptcha}

表單作者可以使用Google的reCAPTCHA服務，在最適化表單中實作CAPTCHA。 它提供進階的CAPTCHA功能，以保護您的網站。 如需reCAPTCHA運作方式的詳細資訊，請參 [閱Google reCAPTCHA](https://developers.google.com/recaptcha/)。

![recaptcha](assets/recaptcha.png)

若要在AEM Forms中實作reCAPTCHA服務：

1. 從 [Google取得reCAPTCHA API金鑰](https://www.google.com/recaptcha/admin) 對。 它包含網站金鑰和機密。
1. 建立雲端服務的設定容器。

   1. 前往「工 **[!UICONTROL 具>一般>設定瀏覽器]**」。
   1. 請執行下列動作，為雲端設定啟用全域資料夾，或略過此步驟，為雲端服務設定建立並設定另一個資料夾。

      1. 在「設定瀏覽器」中，選取全域 **[!UICONTROL 資料夾]** ，然後點選「 **[!UICONTROL 屬性」]**。
      1. 在「設定屬性」對話方塊中，啟用「 **[!UICONTROL 雲端設定」]**。
      1. 點選 **[!UICONTROL 「儲存並關閉]** 」以儲存設定並退出對話方塊。
   1. 在「設定瀏覽器」中，點選「 **[!UICONTROL 建立]**」。
   1. 在「建立設定」對話方塊中，指定資料夾的標題並啟用「雲 **[!UICONTROL 端設定」]**。
   1. 點選 **[!UICONTROL 「建立]** 」以建立適用於雲端服務設定的資料夾。


1. 為reCAPTCHA設定雲端服務。

   1. 在您的AEM作者例項上，前往「工 ![具](assets/tools.png) > **Cloud服務」**。
   1. 點選 **[!UICONTROL reCAPTCHA]**。 將開啟「配置」頁。 選取在上一個步驟中建立的設定容器，然後點選「 **[!UICONTROL 建立]**」。
   1. 指定reCAPTCHA服務的名稱、網站金鑰和機密金鑰，並點選「 **[!UICONTROL 建立]** 」以建立雲端服務設定。
   1. 在「編輯元件」對話方塊中，指定在步驟1中取得的網站和機密金鑰。 點選 **[!UICONTROL 「Save Settings]** (儲存設定 **[!UICONTROL )」，然後點選「]** OK（確定）」以完成設定。

   在設定reCAPTCHA服務後，就可在最適化表單中使用。 如需詳細資訊，請參 [閱在最適化表單中使用CAPTCHA](#using-captcha)。

## 在最適化表單中使用CAPTCHA {#using-captcha}

若要在最適化表單中使用CAPTCHA:

1. 在編輯模式中開啟最適化表單。

   >[!NOTE]
   >
   >請確定建立最適化表單時選取的組態容器包含reCAPTCHA雲端服務。 您也可以編輯最適化表單屬性，以變更與表單關聯的組態容器。

1. 從元件瀏覽器，將 **[!UICONTROL Captcha]** 元件拖放至最適化表單。

   >[!NOTE]
   >
   >不支援在最適化表單中使用多個Captcha元件。 此外，建議不要在標示為延遲載入的面板或片段中使用CAPTCHA。

   >[!NOTE]
   >
   >驗證碼是時間敏感的，約一分鐘後過期。 因此，建議將Captcha元件置於最適化表單中「提交」按鈕之前。

1. 選取您新增的Captcha元件，並點選 ![cmppr](assets/cmppr.png) 以編輯其屬性。
1. 指定CAPTCHA介面工具集的標題。 預設值為 **Captcha**。 如果您 **[!UICONTROL 不想顯示標題]** ，請選取「隱藏標題」。
1. 如果您依 **[!UICONTROL Google的]** ReCAPTCHA服務中所述設定reCAPTCHA服務，請從 **[!UICONTROL Captcha服務下拉式清單中選取reCaptcha]** ，以啟用reCAPTCHA服務 [](#google-recaptcha)。 從「設定」下拉式清單中選取設定。 此外，請為reCAPTCHA介面工具集選 **[!UICONTROL 取「一般]** 」或「 **[!UICONTROL 精簡]** 」的大小。

   >[!NOTE]
   >
   >請勿從「 **[!UICONTROL Captcha]** 」服務下拉式清單中選取「預設值」，因為預設的AEM CAPTCHA服務已停用。

1. 儲存屬性。

reCAPTCHA服務在最適化表單上啟用。 您可以預覽表單，並檢視CAPTCHA運作。

---
title: 在最適化表單中使用CAPTCHA
seo-title: 在最適化表單中使用CAPTCHA
description: 了解如何以最適化表單設定AEM CAPTCHA或Google reCAPTCHA服務。
seo-description: 了解如何以最適化表單設定AEM CAPTCHA或Google reCAPTCHA服務。
uuid: 8bcb0dd7-b43c-4a36-8f6b-7875b68f9ba1
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author, adaptive_forms
discoiquuid: 32369b0b-5abf-487d-ae6b-972c254eb7e2
feature: 適用性表單
exl-id: 1129004b-5e8b-42fd-98ed-f203edde93b9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 0%

---

# 在最適化表單{#using-captcha-in-adaptive-forms}中使用驗證碼

驗證碼（Captcha，完全自動化的公共圖靈測試，可區分電腦和人）是線上交易中常用的一種程式，用於區分人和自動程式或機器人。 這會帶來挑戰並評估使用者回應，以判斷其為與網站互動的人或機器人。 它可防止機器人張貼垃圾訊息或惡意用途，讓使用者在測試失敗時繼續執行，有助於確保線上交易的安全。

AEM Forms支援適用性表單中的驗證碼。 您可以使用Google的reCAPTCHA服務來實作CAPTCHA。

>[!NOTE]
>
>AEM Forms僅支援reCaptcha v2。 不支援任何其他版本。
>
>AEM Forms應用程式的離線模式不支援適用性表單中的驗證碼。

## 通過Google配置ReCAPTCHA服務{#google-recaptcha}

表單作者可使用Google的reCAPTCHA服務，在最適化表單中實作CAPTCHA。 它提供進階驗證碼功能，可保護您的網站。 如需reCAPTCHA如何運作的詳細資訊，請參閱[Google reCAPTCHA](https://developers.google.com/recaptcha/)。

![recapcha](assets/recaptcha.png)

若要在AEM Forms中實作reCAPTCHA服務：

1. 從Google取得[reCAPTCHA API金鑰組](https://www.google.com/recaptcha/admin)。 其中包含網站金鑰和機密。
1. 為雲端服務建立設定容器。

   1. 前往「**[!UICONTROL 工具>一般>設定瀏覽器]**」。
      * 如需詳細資訊，請參閱[設定瀏覽器檔案](/help/sites-administering/configurations.md) 。
   1. 請執行下列操作以啟用雲配置的全局資料夾，或跳過此步驟以建立和配置雲服務配置的其他資料夾。

      1. 在「配置瀏覽器」中，選擇&#x200B;**[!UICONTROL global]**&#x200B;資料夾，然後點選&#x200B;**[!UICONTROL Properties]**。
      1. 在「配置屬性」對話框中，啟用&#x200B;**[!UICONTROL 雲配置]**。
      1. 點選&#x200B;**[!UICONTROL 儲存並關閉]**&#x200B;以儲存設定並退出對話方塊。
   1. 在「設定瀏覽器」中，點選「**[!UICONTROL 建立]**」。
   1. 在「建立配置」對話框中，指定資料夾的標題並啟用&#x200B;**[!UICONTROL 雲配置]**。
   1. 點選&#x200B;**[!UICONTROL 建立]**&#x200B;以建立為雲端服務設定啟用的資料夾。


1. 為reCAPTCHA設定雲端服務。

   1. 在您的AEM製作例項上，前往![tools](assets/tools.png) > **Cloud Services**。
   1. 點選&#x200B;**[!UICONTROL reCAPTCHA]**。 「設定」頁面隨即開啟。 選取在上一步中建立的設定容器，然後點選&#x200B;**[!UICONTROL Create]**。
   1. 指定reCAPTCHA服務的名稱、網站金鑰和密鑰，然後點選&#x200B;**[!UICONTROL Create]**&#x200B;以建立雲端服務設定。
   1. 在「編輯元件」對話方塊中，指定在步驟1取得的網站和機密金鑰。 點選「**[!UICONTROL 儲存設定]**」，然後點選「**[!UICONTROL 確定」以完成設定。]**

   設定reCAPTCHA服務後，即可在最適化表單中使用。 如需詳細資訊，請參閱[在最適化表單中使用CAPTCHA](#using-captcha) 。

## 在最適化表單{#using-captcha}中使用CAPTCHA

若要在最適化表單中使用CAPTCHA:

1. 在編輯模式中開啟最適化表單。

   >[!NOTE]
   >
   >建立最適化表單時，請確定選取的設定容器包含reCAPTCHA雲端服務。 您也可以編輯最適化表單屬性，以變更與表單相關聯的設定容器。

1. 從元件瀏覽器，將&#x200B;**[!UICONTROL Captcha]**&#x200B;元件拖放至最適化表單。

   >[!NOTE]
   >
   >不支援在最適化表單中使用多個驗證碼元件。 此外，不建議在標示為延遲載入的面板或片段中使用CAPTCHA。

   >[!NOTE]
   >
   >驗證碼具有時效性，約一分鐘後過期。 因此，建議將驗證碼元件放置在最適化表單中的提交按鈕之前。

1. 選取您新增的驗證碼元件，然後點選![cmpr](assets/cmppr.png)以編輯其屬性。
1. 指定驗證碼介面工具集的標題。 預設值為&#x200B;**Captcha**。 如果不想顯示標題，請選擇&#x200B;**[!UICONTROL 隱藏標題]**。
1. 如果您依照[Google](#google-recaptcha)ReCAPTCHA服務所述來設定reCAPTCHA服務，請從&#x200B;**[!UICONTROL Captcha服務]**&#x200B;下拉式清單中選取&#x200B;**[!UICONTROL reCaptcha]**&#x200B;以啟用reCAPTCHA服務。 從「設定」下拉式清單中選取設定。 此外，為reCAPTCHA介面工具集選擇大小為&#x200B;**[!UICONTROL Normal]**&#x200B;或&#x200B;**[!UICONTROL Compact]**。

   >[!NOTE]
   >
   >請勿從驗證碼服務下拉式清單中選取&#x200B;**[!UICONTROL 預設]**，因為預設的AEM驗證碼服務已遭取代。

1. 儲存屬性。

reCAPTCHA服務已在最適化表單上啟用。 您可以預覽表單，並查看驗證碼正常運作。

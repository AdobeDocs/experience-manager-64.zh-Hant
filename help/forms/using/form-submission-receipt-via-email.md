---
title: 透過電子郵件傳送表單提交確認
seo-title: Sending a form submission acknowledgement via email
description: AEM Forms可讓您設定電子郵件提交動作，在提交表單時向使用者傳送確認。
seo-description: AEM Forms allows you to configure the email submit action that sends an acknowledgement to a user on submitting the form.
uuid: 77b3c836-6011-48bd-831c-ebc214218efb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 7ffe6317-174b-4d80-9ac6-9bfb5eed7e29
exl-id: e850d2a5-cb5f-4bd4-81dd-57951923b6d3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 1%

---

# 透過電子郵件傳送表單提交確認 {#sending-a-form-submission-acknowledgement-via-email}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 最適化表單資料提交 {#adaptive-form-data-submission}

適用性表單提供數種現成可用的 [提交動作](/help/forms/using/configuring-submit-actions.md) 將表單資料提交至不同端點的工作流程。

例如， **電子郵件動作** 提交動作會在成功提交最適化表單時傳送電子郵件。 您也可以設定它，以傳送電子郵件中的表單資料和PDF。

本文詳細說明在最適化表單及其提供的不同設定上啟用「電子郵件」動作的步驟。

>[!NOTE]
>
>您也可以使用 **電子郵件PDF動作** 以電子郵件形式以PDF附件的形式傳送已完成的表單。 此動作可用的設定選項與「電子郵件」動作可用的選項相同。 「電子郵件PDF」動作僅適用於XFA型適用性表單

## 電子郵件動作 {#email-action}

「電子郵件」動作可讓作者在成功提交最適化表單時，自動傳送電子郵件給一或多個收件者。

>[!NOTE]
>
>若要使用「電子郵件」動作，您需要依照 [設定郵件服務](/help/sites-administering/notification.md#configuring-the-mail-service).

### 在最適化表單上啟用「電子郵件」動作 {#enabling-email-action-on-an-adaptive-form}

1. 在編輯模式中開啟最適化表單。

1. 按一下 **編輯** 旁邊 **開始最適化表單** 工具欄。

   「編輯元件」(Edit Component)對話框開啟。

   ![編輯最適化表單的元件對話方塊](assets/start_of_adp_form.png)

1. 選取 **提交操作** 標籤和選擇 **電子郵件動作** 從「提交動作」下拉式清單。

   索引標籤會顯示為目前表單設定「電子郵件」動作的選項。

   ![提交操作標籤](assets/dialog.png)

1. 在「郵件地址」、「抄送」和「密件副本」欄位中指定有效的電子郵件ID。

   分別在「主旨」和「電子郵件」範本欄位中指定電子郵件的主旨和內文。

   您也可以在欄位中指定變數預留位置，在此情況下，當使用者成功提交表單時，會處理欄位的值。 如需詳細資訊，請參閱 [使用最適化表單欄位名稱以動態建立電子郵件內容](/help/forms/using/form-submission-receipt-via-email.md#p-using-adaptive-form-field-names-to-dynamically-create-email-content-p).

   如果表單包含檔案附件，而您想在電子郵件中附加這些檔案，請選擇「包含附件」。

   >[!NOTE]
   >
   >如果您選擇 **電子郵件PDF動作**，您必須選取「包含附件」選項。

1. 按一下 **確定** 以儲存變更。

### 使用最適化表單欄位名稱以動態建立電子郵件內容 {#using-adaptive-form-field-names-to-dynamically-create-email-content}

適用性表單中的欄位名稱稱為預留位置，在使用者提交表單後，會以該欄位的值取代。

在「電子郵件」動作標籤中，您可以使用執行動作時處理的預留位置。 這表示使用者提交表單時，會產生電子郵件的標題（例如Mailto、CC、BCC、主旨）。

要定義佔位符，請指定 `${<field name>}` 在「提交動作」索引標籤的欄位中。

例如，如果表單包含 **電子郵件地址** 欄位，已命名 `email_addr`，若要擷取使用者的電子郵件ID，您可以在「郵件至」、「抄送」或「密件副本」欄位中指定下列項目。

`${email_addr}`

當使用者提交表單時，會傳送電子郵件至 `email_addr` 欄位。

>[!NOTE]
>
>您可以在 **編輯** 對話框。

變數預留位置也可用於 **主旨** 和 **電子郵件範本** 欄位。

例如：

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>可重複面板中的欄位無法作為變數預留位置。

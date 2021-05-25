---
title: 透過電子郵件傳送表單提交確認
seo-title: 透過電子郵件傳送表單提交確認
description: AEM Forms可讓您設定電子郵件提交動作，在提交表單時向使用者傳送確認。
seo-description: AEM Forms可讓您設定電子郵件提交動作，在提交表單時向使用者傳送確認。
uuid: 77b3c836-6011-48bd-831c-ebc214218efb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 7ffe6317-174b-4d80-9ac6-9bfb5eed7e29
exl-id: e850d2a5-cb5f-4bd4-81dd-57951923b6d3
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 0%

---

# 通過電子郵件{#sending-a-form-submission-acknowledgement-via-email}發送表單提交確認

## 適用性表單資料提交{#adaptive-form-data-submission}

適用性表單提供數種現成可用的[提交動作](/help/forms/using/configuring-submit-actions.md)工作流程，用於將表單資料提交至不同端點。

例如，**電子郵件動作**&#x200B;提交動作會在成功提交最適化表單時傳送電子郵件。 您也可以設定此檔案，以傳送電子郵件中的表單資料和PDF。

本文詳細說明在最適化表單及其提供的不同設定上啟用「電子郵件」動作的步驟。

>[!NOTE]
>
>您也可以使用&#x200B;**電子郵件PDF動作**，以電子郵件形式以PDF附件傳送已完成的表單。 此動作可用的設定選項與「電子郵件」動作可用的選項相同。 「電子郵件PDF」動作僅適用於XFA型最適化表單

## 電子郵件操作{#email-action}

「電子郵件」動作可讓作者在成功提交最適化表單時，自動傳送電子郵件給一或多個收件者。

>[!NOTE]
>
>若要使用「電子郵件」動作，您需要依照[設定郵件服務](/help/sites-administering/notification.md#configuring-the-mail-service)中所述來配置AEM郵件服務。

### 在最適化表單{#enabling-email-action-on-an-adaptive-form}上啟用「電子郵件」動作

1. 在編輯模式中開啟最適化表單。

1. 按一下&#x200B;**Edit**（位於&#x200B;**Start of a Adaptive Form**&#x200B;工具列旁）。

   「編輯元件」(Edit Component)對話框開啟。

   ![編輯最適化表單的元件對話方塊](assets/start_of_adp_form.png)

1. 選擇&#x200B;**提交操作**&#x200B;頁簽，然後從提交操作下拉清單中選擇&#x200B;**電子郵件操作**。

   索引標籤會顯示為目前表單設定「電子郵件」動作的選項。

   ![提交操作標籤](assets/dialog.png)

1. 在「郵件地址」、「抄送」和「密件副本」欄位中指定有效的電子郵件ID。

   分別在「主旨」和「電子郵件」範本欄位中指定電子郵件的主旨和內文。

   您也可以在欄位中指定變數預留位置，在此情況下，當使用者成功提交表單時，會處理欄位的值。 如需詳細資訊，請參閱[使用最適化表單欄位名稱以動態建立電子郵件內容](/help/forms/using/form-submission-receipt-via-email.md#p-using-adaptive-form-field-names-to-dynamically-create-email-content-p)。

   如果表單包含檔案附件，而您想在電子郵件中附加這些檔案，請選擇「包含附件」。

   >[!NOTE]
   >
   >如果選擇&#x200B;**電子郵件PDF操作**，則必須選擇「包含附件」選項。

1. 按一下&#x200B;**OK**&#x200B;以儲存變更。

### 使用最適化表單欄位名稱以動態建立電子郵件內容{#using-adaptive-form-field-names-to-dynamically-create-email-content}

適用性表單中的欄位名稱稱為預留位置，在使用者提交表單後，會以該欄位的值取代。

在「電子郵件」動作標籤中，您可以使用執行動作時處理的預留位置。 這表示使用者提交表單時，會產生電子郵件的標題（例如Mailto、CC、BCC、主旨）。

要定義佔位符，請在「提交操作」頁簽的欄位中指定`${<field name>}`。

例如，如果表單包含名為`email_addr`的&#x200B;**電子郵件地址**&#x200B;欄位，以擷取使用者的電子郵件ID，您可以在「Mailto」、「CC」或「BCC」欄位中指定下列項目。

`${email_addr}`

當用戶提交表單時，會向表單`email_addr`欄位中輸入的電子郵件ID發送電子郵件。

>[!NOTE]
>
>您可以在&#x200B;**Edit**&#x200B;對話方塊中找到欄位的名稱。

變數預留位置也可用於&#x200B;**Subject**&#x200B;和&#x200B;**Email template**&#x200B;欄位中。

例如：

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>可重複面板中的欄位無法作為變數預留位置。

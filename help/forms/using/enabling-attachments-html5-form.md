---
title: 啟用HTML5表單的附件
seo-title: Enabling attachments for an HTML5 form
description: 依預設，會停用HTML5表單的附件支援。
seo-description: By default, the attachment support for HTML5 forms is disabled.
uuid: 2c62ac3e-4b27-46c7-a61d-a805fb5d26fb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 8eebfcd6-0597-44ed-b718-bf9a1baa6c12
feature: Mobile Forms
exl-id: 82a843c4-5cb2-4f5e-ad4d-cf2e9ea6cdb8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 1%

---

# 啟用HTML5表單的附件 {#enabling-attachments-for-an-html-form}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

您可以使用HTML5表單上傳、預覽和提交附件。 依預設，附件支援會停用。 要啟用附件支援，請執行以下操作：

1. 建立 [自訂設定檔](/help/forms/using/custom-profile.md) 使用mutiselect字串屬性 `mfAttachmentOptions`.
1. 在自訂設定檔中，指定屬性 `fileSizeLimit`, `multiSelect`，和 `buttonTex`設定檔案附件小工具集的選項。 您也可以視需要指定更多自訂屬性。

1. 在自訂設定檔中，使用下列設定：

   * **multiSelect** -> true或false（預設為true）
   * **fileSizeLimit** -> value_in_mb（例如5）（預設為2 MB）
   * **buttonText** ->彈出窗口的按鈕文本（預設為「附加」）
   * **接受** ->要接受的檔案類型（預設為「audio/&amp;ast;, video/&amp;ast;, image/&amp;ast;, text/&amp;ast;, .pdf」）

   >[!NOTE]
   >
   >在Microsoft Internet Explorer 9中，用戶可以附加大於指定限制的檔案。 這是已知問題。

1. 使用 [中繼資料編輯器](/help/forms/using/manage-form-metadata.md) 選取您為HTML5表單上建立的自訂設定檔。
1. 使用自訂設定檔呈現您的表單範本，附件圖示會出現在表單工具列上。

   >[!NOTE]
   >
   >表單入口網站會立即提供已啟用草稿和附件功能的自訂設定檔。 如需 **另存為草稿** 設定檔，請參閱 [將HTML5表單儲存為草稿](/help/forms/using/saving-html5-form-draft.md).

1. 按一下附件表徵圖，隨即出現附件選擇對話框。 瀏覽並選取附件，然後按一下 **附加**.

   >[!NOTE]
   >
   >若要預覽附件，請按一下附件名稱。

   >[!NOTE]
   >
   >匿名用戶無法使用檔案預覽選項。

## 附件提交格式 {#attachment-submission-format}

啟用附件時，HTML5表單會提交多部分資料。 多部分提交資料包含兩部分 **dataXml** 和 **附件**.

>[!NOTE]
>
>為了回溯相容性，如果 `mfAllowAttachments`選項關閉，則HTML5表單不會傳送多部分資料。 它會在 **application/xml** 格式。

如果mfAllowAttachments標幟已開啟，則 [提交服務代理服務](/help/forms/using/service-proxy.md) 也會發佈包含dataXml和附件的多部分資料。

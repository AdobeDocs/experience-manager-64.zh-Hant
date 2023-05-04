---
title: 在「指派任務」步驟中使用自訂電子郵件範本
seo-title: Use custom email templates in an Assign Task step
description: 表單工作流程電子郵件通知的自訂電子郵件範本
seo-description: Custom email templates for forms workflow email notifications
uuid: bc2af94d-d4ad-417e-b3d2-bcfffc1b306d
topic-tags: publish
discoiquuid: c447fc39-c0f3-4932-ac6c-465d1fb83f8c
exl-id: 5af73823-2c32-41b3-9ab8-a7ad9fd9532f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 2%

---

# 在「指派任務」步驟中使用自訂電子郵件範本 {#use-custom-email-templates-in-an-assign-task-step}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

表單工作流程電子郵件通知的自訂電子郵件範本

您可以使用「分配任務」步驟來建立任務並將其分配給用戶或組。 將任務分配給用戶或組時，會向定義的用戶或定義組的每個成員發送電子郵件通知。 典型的電子郵件通知包含指派任務的連結以及與任務相關的資訊。 下列影像顯示範例電子郵件通知：

![具有現成可用範本的電子郵件通知](do-not-localize/default-email-template.png)

您可以在電子郵件通知中自訂外觀並使用自訂中繼資料。 AEM Forms提供立即可用的電子郵件通知範本。 您可以自訂現成可用的範本，或從頭建立新範本。

電子郵件通知範本是根據 [HTML電子郵件](https://en.wikipedia.org/wiki/HTML_email). 這些電子郵件可適應不同的電子郵件用戶端和螢幕大小。 此外，電子郵件的樣式是在範本中定義。

下列影像顯示自訂的電子郵件通知：

![使用自訂範本的電子郵件通知](do-not-localize/customized-email.png)

## 自訂現有範本 {#customize-the-existing-template}

AEM Forms提供電子郵件通知的範本，且立即可用。 模板提供了標題說明、到期日期、優先順序、工作流名稱以及分配任務的連結。 您可以自訂範本以變更外觀。 執行下列步驟來自訂範本：

1. 使用管理員帳戶登入CRXDE。

1. 導覽至/libs/fd/dashboard/templates/email。

1. 開啟htmlEmailTemplate.txt檔案。 它包含預設範本。

1. 以自訂內容取代htmlEmailTemplate.txt檔案的內容。

   電子郵件通知範本是 [HTML電子郵件](https://en.wikipedia.org/wiki/HTML_email). 您可以將現有的html程式碼取代為自訂程式碼，以變更範本的外觀。

1. 儲存檔案。現在，自訂範本已可供使用。

## 建立電子郵件範本 {#create-an-email-template}

AEM Forms提供電子郵件通知的範本，且立即可用。 模板提供了標題說明、到期日期、優先順序、工作流名稱以及分配任務的連結。 您也可以為「指派」任務步驟新增自訂電子郵件範本（您自己的範本）。 執行下列步驟以新增自訂電子郵件範本：

1. 使用管理員帳戶登入CRXDE。

1. 導覽至/libs/fd/dashboard/templates/email。

1. 建立.txt檔案。 例如， EmailOnTaskAssign.txt。

1. 將自訂HTML程式碼新增至檔案。

   電子郵件通知範本是 [HTML電子郵件](https://en.wikipedia.org/wiki/HTML_email). 您可以將自訂HTML程式碼新增至檔案以建立新範本。

1. 儲存檔案。模板已準備好在「分配任務」步驟中使用。

## 在「分配任務」步驟中使用電子郵件模板 {#use-an-email-template-in-an-assign-task-step}

現成可用的「指定任務」步驟已配置為使用預設模板htmlEmailTemplate.txt。 您可以選擇使用自訂範本。 若要變更範本：

1. 開啟 **[!UICONTROL 分配任務]** 步驟。

1. 導覽至 **[!UICONTROL 受託人>HTML電子郵件範本]**.

1. 選取新建立的HTML電子郵件範本。

1. 按一下&#x200B;**[!UICONTROL 「確定」]**。範本已變更。

電子郵件通知也會使用 [中繼資料](/help/forms/using/use-metadata-in-email-notifications.md). 例如，到期日、優先順序、工作流程名稱等。 您也可以設定範本以使用 [自訂中繼資料](/help/forms/using/use-metadata-in-email-notifications.md#using-custom-metadata-in-an-email-notification).

---
title: 私人資料夾共用
description: 瞭解如何在Adobe Experience Manager(AEM)資產中建立私人資料夾，並與其他使用者共用資料夾，以及為他們指派各種權限。
contentOwner: AG
feature: Collaboration
role: Business Practitioner
translation-type: tm+mt
source-git-commit: 4acf159ae1b9923a9c93fa15faa38c7f4bc9f759
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 6%

---


# 共用{#private-folder-sharing}的專用資料夾

您可以在Adobe Experience Manager(AEM)Assets使用者介面中建立專屬於您的私人資料夾。 您可以將此私人資料夾共用給其他使用者，並指派不同的權限給他們。 根據您指派的權限層級，使用者可以對資料夾執行各種工作，例如檢視資料夾內的資產或編輯資產。

1. 在「資產」控制台中，從工具列點選／按一下「建立&#x200B;**[!UICONTROL a1/>」，然後從選單選擇「資料夾**[!UICONTROL 」。]**]**

   ![chlimage_1-411](assets/chlimage_1-411.png)

1. 在&#x200B;**[!UICONTROL 添加資料夾]**&#x200B;對話框中，輸入資料夾的標題和名稱（可選），然後選擇&#x200B;**[!UICONTROL 專用]**。

   ![chlimage_1-412](assets/chlimage_1-412.png)

1. 點選／按一下&#x200B;**[!UICONTROL Create]**。 UI中會建立私人資料夾。

   ![chlimage_1-413](assets/chlimage_1-413.png)

1. 要與其他用戶共用資料夾以及為其分配權限，請選擇該資料夾，然後按一下工具欄中的「屬性 **** 」表徵圖。

   ![chlimage_1-414](assets/chlimage_1-414.png)

   >[!NOTE]
   >
   >在您共用資料夾之前，該資料夾不會顯示給任何其他使用者。

1. 在「資料夾屬性」頁中，從&#x200B;**[!UICONTROL 添加用戶]**&#x200B;清單中選擇用戶，在私人資料夾上為用戶分配角色，然後按一下&#x200B;**[!UICONTROL 添加]**。

   ![chlimage_1-415](assets/chlimage_1-415.png)

   >[!NOTE]
   >
   >您可以將各種角色（例如編輯者、擁有者或檢視器）指派給您共用資料夾的使用者。 如果您為用戶分配了「所有者」角色，則用戶對資料夾具有編輯者權限。 此外，使用者也可以與其他人共用資料夾。 如果您指派了編輯者角色，使用者可以編輯私人資料夾中的資產。 如果您指派檢視器角色，使用者只能檢視您私人資料夾中的資產。

1. 按一下「**[!UICONTROL 儲存]**」。根據您指派的角色，當使用者登入AEM Assets時，會為使用者指派一組權限給您的私人資料夾。
1. 按一下&#x200B;**[!UICONTROL 確定]**&#x200B;以關閉確認消息。
1. 與您共用資料夾的使用者會收到共用通知。 使用使用者的認證登入AEM Assets以檢視通知。

   ![chlimage_1-416](assets/chlimage_1-416.png)

1. 點選／按一下「通知」圖示以開啟通知清單。

   ![chlimage_1-417](assets/chlimage_1-417.png)

1. 按一下／點選管理員共用的專用資料夾條目以開啟該資料夾。

>[!NOTE]
>
>要能夠建立專用資料夾，您需要對要建立專用資料夾的父資料夾具有讀取和編輯ACL權限。 如果您不是管理員，則在&#x200B;*/content/dam*&#x200B;上，預設不會為您啟用這些權限。 在此情況下，請先取得使用者ID/群組的這些權限，再嘗試建立私人資料夾或檢視資料夾設定。


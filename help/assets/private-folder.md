---
title: 私人資料夾共用
description: 了解如何在Adobe Experience Manager Assets中建立私人資料夾，並與其他使用者共用資料夾，以及為其指派各種權限。
contentOwner: AG
feature: Collaboration
role: User
exl-id: b6aa3cba-4085-47ac-a249-7461baee2a00
source-git-commit: a778c3bbd0e15bb7b6de2d673b4553a7bd146143
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 6%

---

# 私人資料夾共用 {#private-folder-sharing}

您可以在Adobe Experience Manager Assets使用者介面中建立專供您使用的私人資料夾。 您可以將此私人資料夾共用給其他使用者，並為其指派各種權限。 根據您指派的權限層級，使用者可以對資料夾執行各種工作，例如在資料夾內檢視資產或編輯資產。

1. 在「資產」主控台中，從工具列點選/按一下「建立&#x200B;**** 」，然後從功能表選擇「 **[!UICONTROL 資料夾]** 」。

   ![chlimage_1-411](assets/chlimage_1-411.png)

1. 在&#x200B;**[!UICONTROL 添加資料夾]**&#x200B;對話框中，輸入資料夾的標題和名稱（可選），然後選擇&#x200B;**[!UICONTROL Private]**。

   ![chlimage_1-412](assets/chlimage_1-412.png)

1. 點選/按一下&#x200B;**[!UICONTROL 建立]**。 UI中會建立私人資料夾。

   ![chlimage_1-413](assets/chlimage_1-413.png)

1. 要與其他用戶共用資料夾以及為其分配權限，請選擇該資料夾，然後按一下工具欄中的「屬性 **** 」表徵圖。

   ![chlimage_1-414](assets/chlimage_1-414.png)

   >[!NOTE]
   >
   >在您共用資料夾之前，該資料夾不會顯示給任何其他使用者。

1. 在「資料夾屬性」頁中，從&#x200B;**[!UICONTROL 添加用戶]**&#x200B;清單中選擇用戶，將角色分配給私人資料夾中的用戶，然後按一下&#x200B;**[!UICONTROL 添加]**。

   ![chlimage_1-415](assets/chlimage_1-415.png)

   >[!NOTE]
   >
   >您可以將各種角色（例如編輯者、擁有者或檢視者）指派給您共用資料夾的使用者。 如果您將「擁有者」角色指派給使用者，則使用者對資料夾具有「編輯者」權限。 此外，使用者可與其他人共用資料夾。 如果您指派編輯者角色，使用者可以編輯您私人資料夾中的資產。 如果您指派檢視器角色，使用者只能檢視您私人資料夾中的資產。

1. 按一下「**[!UICONTROL 儲存]**」。根據您指派的角色，當使用者登入[!DNL Experience Manager]資產時，系統會為使用者指派一組私人資料夾的權限。
1. 按一下&#x200B;**[!UICONTROL 確定]**&#x200B;以關閉確認訊息。
1. 您與其共用資料夾的使用者會收到共用通知。 使用使用者的憑證登入[!DNL Experience Manager]資產以檢視通知。

   ![chlimage_1-416](assets/chlimage_1-416.png)

1. 點選/按一下「通知」圖示以開啟通知清單。

   ![chlimage_1-417](assets/chlimage_1-417.png)

1. 按一下/點選管理員共用之私人資料夾的項目，以開啟資料夾。

>[!NOTE]
>
>要建立專用資料夾，需要對要建立專用資料夾的父資料夾進行讀取和編輯ACL權限。 如果您不是管理員，系統預設不會在&#x200B;*/content/dam*&#x200B;上為您啟用這些權限。 在此情況下，請先取得使用者ID/群組的這些權限，再嘗試建立私人資料夾或檢視資料夾設定。

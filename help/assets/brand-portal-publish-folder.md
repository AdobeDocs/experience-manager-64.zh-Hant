---
title: 將資料夾發佈至 Brand Portal
description: 了解如何將資料夾發佈和取消發佈至Brand Portal。
contentOwner: VG
feature: Brand Portal
role: User
exl-id: f41ab750-5780-42ae-a131-5bc748280215
source-git-commit: de5632ff0ee87a4ded88e792b57e818baf4c01a3
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 27%

---

# 將資料夾發佈至 Brand Portal {#publish-folders-to-brand-portal}

身為Adobe Experience Manager Assets管理員，您可以將資產和資料夾發佈至組織的[!DNL Experience Manager Assets Brand Portal]例項（或將發佈工作流程排程至稍後的日期/時間）。 但您必須先將[!DNL Experience Manager Assets]與[!DNL Brand Portal]整合。 如需詳細資訊，請參閱[使用Brand Portal](configure-aem-assets-with-brand-portal.md)設定 [!DNL Experience Manager Assets] 。

發佈資產或資料夾後，Brand Portal的使用者就能使用它。

如果您後續修改[!DNL Assets]中的原始資產或資料夾，在您重新發佈資產或資料夾之前，變更不會反映在Brand Portal中。 這項功能可確保對進行中工作所作的變更不會出現在 Brand Portal 中。Brand Portal 僅提供管理員發佈的已核准變更。

## 將資料夾發佈至 Brand Portal {#publish-folders-to-brand-portal-1}

1. 從[!DNL Assets]介面中，暫留在所需的資料夾上，然後從快速操作中選擇&#x200B;**[!UICONTROL Publish]**&#x200B;選項。

   或者，選取所需的資料夾，然後依照進一步步驟操作。

   ![publish2bp](assets/publish2bp.png)

2. **現在發佈資料夾**

   若要將所選資料夾發佈至 Brand Portal，請執行下列其中一項操作：

   * 在工具列中選取&#x200B;**[!UICONTROL 快速發佈]**。然後，從功能表中選取&#x200B;**[!UICONTROL 發佈至Brand Portal]**。
   * 在工具列中選取&#x200B;**[!UICONTROL 管理出版物]**。

3. 然後，從&#x200B;**[!UICONTROL Action]**&#x200B;中選擇&#x200B;**[!UICONTROL 發佈到Brand Portal]**，從&#x200B;**[!UICONTROL Scheduling]**&#x200B;中選擇&#x200B;**[!UICONTROL Now]**。 點選&#x200B;**[!UICONTROL Next]。**
4. 在&#x200B;**[!UICONTROL 範圍]**&#x200B;中，確認您的選取項目，然後點選&#x200B;**[!UICONTROL 發佈至Brand Portal]**。

   系統會顯示訊息，指出資料夾已排入佇列，等候發佈至 Brand Portal。登入Brand Portal介面，查看已發佈的資料夾。

   **稍後發佈資料夾**

   若要將資產資料夾的發佈至Brand Portal工作流程排程至之後的日期或時間：

   1. 選取要發佈的資產/資料夾後，請從頂端的工具列選取&#x200B;**[!UICONTROL 管理出版物]**。
   2. 在&#x200B;**[!UICONTROL 管理出版物]**&#x200B;頁面上，從&#x200B;**[!UICONTROL Action]**&#x200B;中選擇&#x200B;**[!UICONTROL 發佈到Brand Portal]**，然後從&#x200B;**[!UICONTROL Scheduling]**&#x200B;中選擇&#x200B;**[!UICONTROL Later]**。

      ![publishlaterbp](assets/publishlaterbp.png)

   3. 選取&#x200B;**[!UICONTROL 啟用日期]**&#x200B;並指定時間。點選&#x200B;**[!UICONTROL Next]**。
   4. 在&#x200B;**[!UICONTROL 範圍]**&#x200B;中確認您的選取項目。點選&#x200B;**[!UICONTROL Next]**。
   5. 在&#x200B;**[!UICONTROL 工作流程]**&#x200B;底下指定「工作流程標題」。點選「**[!UICONTROL 稍後發佈」]**。

      ![managerchedulepub](assets/manageschedulepub.png)

## 從 Brand Portal 取消發佈資料夾 {#unpublish-folders-from-brand-portal}

您可以從[!DNL Experience Manager]製作例項中取消發佈，以移除已發佈至Brand Portal的任何資產資料夾。 取消發佈原始資料夾後，Brand Portal 使用者將無法再取用資料夾副本。

您可以選擇從Brand Portal快速取消發佈資料夾，或排程以後的日期和時間。 若要從 Brand Portal 取消發佈資產資料夾：

1. 在[!DNL Experience Manager]製作例項的[!DNL Assets]介面中，選取您要取消發佈的資料夾。

   ![publish2bp-1](assets/publish2bp-1.png)

2. 在工具列中，點選/按一下&#x200B;**[!UICONTROL 管理出版物]**。

3. **立即從Brand Portal取消發佈**

   若要從Brand Portal快速取消發佈所需的資料夾：

   1. 在&#x200B;**[!UICONTROL 管理出版物]**&#x200B;頁面上，從&#x200B;**[!UICONTROL Action]**&#x200B;選擇&#x200B;**[!UICONTROL 從Brand Portal]**&#x200B;取消發佈，從&#x200B;**[!UICONTROL Scheduling]**&#x200B;選擇&#x200B;**[!UICONTROL Now]**。
   2. 點選/按一下&#x200B;**[!UICONTROL Next]。**
   3. 在&#x200B;**[!UICONTROL 範圍]**&#x200B;中，確認您的選取項目，然後點選&#x200B;**[!UICONTROL 從Brand Portal取消發佈]**。

   ![confirm-unpublish](assets/confirm-unpublish.png)

   **稍後從Brand Portal取消發佈**

   若要將資料夾從Brand Portal發佈排程到之後的日期和時間：

   1. 在&#x200B;**[!UICONTROL 管理出版物]**&#x200B;頁面上，從&#x200B;**[!UICONTROL Action]**&#x200B;中選擇&#x200B;**[!UICONTROL 從Brand Portal]**&#x200B;取消發佈，並從&#x200B;**[!UICONTROL Scheduling]**&#x200B;中選擇&#x200B;**[!UICONTROL Later]。**
   2. 選取&#x200B;**[!UICONTROL 啟用日期]**&#x200B;並指定時間。點選&#x200B;**[!UICONTROL Next]**。
   3. 在&#x200B;**[!UICONTROL Scope]**&#x200B;中，確認您的選擇並點選&#x200B;**[!UICONTROL Next]**。
   4. 在&#x200B;**[!UICONTROL Workflows]**&#x200B;下指定&#x200B;**[!UICONTROL 工作流標題]**。 點選&#x200B;**[!UICONTROL 稍後取消發佈]。**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>將資產發佈/取消發佈至Brand Portal/從資料夾的程式類似於對應的程式。

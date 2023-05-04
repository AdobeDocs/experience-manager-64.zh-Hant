---
title: 將資料夾發佈至 Brand Portal
description: 了解如何將資料夾發佈和取消發佈至Brand Portal。
contentOwner: VG
feature: Brand Portal
role: User
exl-id: f41ab750-5780-42ae-a131-5bc748280215
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 26%

---

# 將資料夾發佈至 Brand Portal {#publish-folders-to-brand-portal}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

身為Adobe Experience Manager Assets管理員，您可以將資產和資料夾發佈至 [!DNL Experience Manager Assets Brand Portal] 例項（或將發佈工作流程排程至稍後的日期/時間）。 不過，您必須先整合 [!DNL Experience Manager Assets] with [!DNL Brand Portal]. 如需詳細資訊，請參閱 [設定 [!DNL Experience Manager Assets] 搭配Brand Portal](configure-aem-assets-with-brand-portal.md).

發佈資產或資料夾後，Brand Portal的使用者就能使用它。

如果您後續修改中的原始資產或資料夾 [!DNL Assets]，在您重新發佈資產或資料夾之前，Brand Portal不會反映這些變更。 這項功能可確保對進行中工作所作的變更不會出現在 Brand Portal 中。Brand Portal 僅提供管理員發佈的已核准變更。

## 將資料夾發佈至 Brand Portal {#publish-folders-to-brand-portal-1}

1. 從 [!DNL Assets] 介面，將滑鼠移到所需的資料夾上，然後選取 **[!UICONTROL 發佈]** 選項。

   或者，選取所需的資料夾，然後依照進一步步驟操作。

   ![publish2bp](assets/publish2bp.png)

2. **現在發佈資料夾**

   若要將所選資料夾發佈至 Brand Portal，請執行下列其中一項操作：

   * 在工具列中選取&#x200B;**[!UICONTROL 快速發佈]**。然後，從功能表中選取 **[!UICONTROL 發佈至Brand Portal]**.
   * 在工具列中選取&#x200B;**[!UICONTROL 管理出版物]**。

3. 然後從 **[!UICONTROL 動作]** 選取 **[!UICONTROL 發佈至Brand Portal]**，從 **[!UICONTROL 排程]** 選取 **[!UICONTROL 現在]**. 點選 **[!UICONTROL 下一個].**
4. 內 **[!UICONTROL 範圍]**，確認您的選取項目並點選 **[!UICONTROL 發佈至Brand Portal]**.

   系統會顯示訊息，指出資料夾已排入佇列，等候發佈至 Brand Portal。登入Brand Portal介面，查看已發佈的資料夾。

   **稍後發佈資料夾**

   若要將資產資料夾的發佈至Brand Portal工作流程排程至之後的日期或時間：

   1. 選取要發佈的資產/資料夾後，請選取 **[!UICONTROL 管理出版物]** 從頂端的工具列。
   2. 開啟 **[!UICONTROL 管理出版物]** 頁面，選取 **[!UICONTROL 發佈至Brand Portal]** 從 **[!UICONTROL 動作]** 選取 **[!UICONTROL 稍後]** 從 **[!UICONTROL 排程]**.

      ![publishlaterbp](assets/publishlaterbp.png)

   3. 選取&#x200B;**[!UICONTROL 啟用日期]**&#x200B;並指定時間。點選 **[!UICONTROL 下一個]**.
   4. 在&#x200B;**[!UICONTROL 範圍]**&#x200B;中確認您的選取項目。點選 **[!UICONTROL 下一個]**.
   5. 在&#x200B;**[!UICONTROL 工作流程]**&#x200B;底下指定「工作流程標題」。點選 **[!UICONTROL 稍後發佈]**.

      ![managerchedulepub](assets/manageschedulepub.png)

## 從 Brand Portal 取消發佈資料夾 {#unpublish-folders-from-brand-portal}

您可以從以下位置取消發佈，移除已發佈至Brand Portal的任何資產資料夾： [!DNL Experience Manager] 製作例項。 取消發佈原始資料夾後，Brand Portal 使用者將無法再取用資料夾副本。

您可以選擇從Brand Portal快速取消發佈資料夾，或排程以後的日期和時間。 若要從 Brand Portal 取消發佈資產資料夾：

1. 從 [!DNL Assets] 介面 [!DNL Experience Manager]  製作例項，選取您要取消發佈的資料夾。

   ![publish2bp-1](assets/publish2bp-1.png)

2. 從工具列，點選/按一下 **[!UICONTROL 管理出版物]**.

3. **立即從Brand Portal取消發佈**

   若要從Brand Portal快速取消發佈所需的資料夾：

   1. 開啟 **[!UICONTROL 管理出版物]** 頁面，從 **[!UICONTROL 動作]** 選取 **[!UICONTROL 從Brand Portal取消發佈]** 從 **[!UICONTROL 排程]** 選取 **[!UICONTROL 現在]**.
   2. 點選/按一下 **[!UICONTROL 下一個].**
   3. 內 **[!UICONTROL 範圍]**，確認您的選取項目並點選 **[!UICONTROL 從Brand Portal取消發佈]**.

   ![confirm-unpublish](assets/confirm-unpublish.png)

   **稍後從Brand Portal取消發佈**

   若要將資料夾從Brand Portal發佈排程到之後的日期和時間：

   1. 開啟 **[!UICONTROL 管理出版物]** 頁面，從 **[!UICONTROL 動作]** 選取 **[!UICONTROL 從Brand Portal取消發佈]** 從 **[!UICONTROL 排程]** 選取 **[!UICONTROL 稍後].**
   2. 選取&#x200B;**[!UICONTROL 啟用日期]**&#x200B;並指定時間。點選 **[!UICONTROL 下一個]**.
   3. 內 **[!UICONTROL 範圍]**，確認您的選取項目並點選 **[!UICONTROL 下一個]**.
   4. 指定 **[!UICONTROL 工作流程標題]** 在 **[!UICONTROL 工作流程]**. 點選 **[!UICONTROL 稍後取消發佈].**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>將資產發佈/取消發佈至Brand Portal/從資料夾的程式類似於對應的程式。

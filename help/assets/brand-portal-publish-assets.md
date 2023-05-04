---
title: 將資料夾發佈至 Brand Portal
description: 了解如何將資產發佈和取消發佈至Brand Portal。
contentOwner: VG
feature: Brand Portal
role: User
exl-id: 6b78124d-4022-452f-8d0f-b667de337bf4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 29%

---

# 將資產發佈至 Brand Portal {#publish-assets-to-brand-portal}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

身為Adobe Experience Manager Assets管理員，您可以將資產發佈至 [!DNL Experience Manager Assets Brand Portal] 例項（或將發佈工作流程排程至稍後的日期/時間）。 不過，您必須先設定 [!DNL Assets] with [!DNL Brand Portal]. 如需詳細資訊，請參閱 [設定 [!DNL Assets] with [!DNL Brand Portal]](configure-aem-assets-with-brand-portal.md).

發佈資產後，Brand Portal的使用者即可使用資產。

若您後續在 [!DNL Assets]，在您重新發佈資產之前，Brand Portal不會反映這些變更。 這項功能可確保對進行中工作所作的變更不會出現在 Brand Portal 中。Brand Portal 僅提供管理員發佈的已核准變更。

復寫成功後，您可以將資產、資料夾和集合發佈至 [!DNL Brand Portal]. 若要將資產發佈至Brand Portal，請依照下列步驟操作：

>[!NOTE]
>
>Adobe建議將發佈時間錯開，最好在非尖峰時段進行，以便 [!DNL Experience Manager] 作者不會佔用過多資源。

1. 在「資產」主控台中，將滑鼠移至所需的資產上並選取 **[!UICONTROL 發佈]** 選項。

   或者，選取您要發佈至Brand Portal的資產。

   ![publish2bp-2](assets/publish2bp-2.png)

2. 若要將資產發佈至Brand Portal，可使用下列兩個選項：
   * [立即發佈資產](#publish-now)
   * [稍後發佈資產](#publish-later)

## 現在發佈資產 {#publish-now}

若要將所選資產發佈至 Brand Portal，請執行下列其中一項操作：

* 在工具列中選取&#x200B;**[!UICONTROL 快速發佈]**。然後，從功能表中選取 **[!UICONTROL 發佈至Brand Portal]**.

* 在工具列中選取&#x200B;**[!UICONTROL 管理出版物]**。

   1. 然後從 **[!UICONTROL 動作]** 選取 **[!UICONTROL 發佈至Brand Portal]**，從 **[!UICONTROL 排程]** 選取 **[!UICONTROL 現在]**. 點選/按一下 **[!UICONTROL 下一個].**

   2. 內 **[!UICONTROL 範圍]**，確認您的選取項目，點選/按一下 **[!UICONTROL 發佈至Brand Portal]**.

系統會顯示訊息，指出資產已排入佇列，等候發佈至 Brand Portal。登入Brand Portal介面以查看已發佈的資產。

## 稍後發佈資產 {#publish-later}

若要將資產發佈至 Brand Portal 的動作安排在之後的日期或時間：

1. 選取要發佈的資產/資料夾後，請選取 **[!UICONTROL 管理出版物]** 從頂端的工具列。
2. 開啟 **[!UICONTROL 管理出版物]** 頁面，選取 **[!UICONTROL 發佈至Brand Portal]** 從 **[!UICONTROL 動作]** 選取 **[!UICONTROL 稍後]** 從 **[!UICONTROL 排程]**.

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

3. 選取&#x200B;**[!UICONTROL 啟用日期]**&#x200B;並指定時間。點選/按一下 **[!UICONTROL 下一個]**.
4. 選取&#x200B;**[!UICONTROL 啟用日期]**&#x200B;並指定時間。點選/按一下 **[!UICONTROL 下一個]**.
5. 在&#x200B;**[!UICONTROL 工作流程]**&#x200B;底下指定「工作流程標題」。點選/按一下 **[!UICONTROL 稍後發佈]**.

   ![publishworkflow](assets/publishworkflow.png)

現在，登入Brand Portal ，查看已發佈的資產是否可在Brand Portal介面上使用。

![bp_631_landing_page](assets/bp_landing_page.png)

---
title: 將資料夾發佈至 Brand Portal
description: 了解如何將資產發佈和取消發佈至Brand Portal。
contentOwner: VG
feature: 品牌入口網站
role: Business Practitioner
exl-id: 6b78124d-4022-452f-8d0f-b667de337bf4
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 36%

---

# 將資產發佈至 Brand Portal {#publish-assets-to-brand-portal}

身為Adobe Experience Manager(AEM)Assets管理員，您可以將資產發佈至貴組織的AEM Assets Brand Portal例項（或將發佈工作流程排程至稍後的日期/時間）。 不過，您必須先使用Brand Portal設定AEM Assets。 如需詳細資訊，請參閱[使用 Brand Portal 設定 AEM Assets](configure-aem-assets-with-brand-portal.md)。

發佈資產後，Brand Portal的使用者即可使用資產。

如果您後續修改AEM Assets中的原始資產，在您重新發佈資產之前，這些變更不會反映在Brand Portal中。 這項功能可確保對進行中工作所作的變更不會出現在 Brand Portal 中。Brand Portal 僅提供管理員發佈的已核准變更。

復寫成功後，您就可以將資產、資料夾和集合發佈至Brand Portal。 若要將資產發佈至Brand Portal，請依照下列步驟操作：

>[!NOTE]
>
>Adobe 建議將發佈時間交錯開來，尤其建議選擇非尖峰時段，如此 AEM 作者才不會佔用過多資源。

1. 從「資產」主控台，暫留在所需的資產上，並從快速動作中選取&#x200B;**[!UICONTROL 發佈]**&#x200B;選項。

   或者，選取您要發佈至Brand Portal的資產。

   ![publish2bp-2](assets/publish2bp-2.png)

2. 若要將資產發佈至Brand Portal，可使用下列兩個選項：
   * [立即發佈資產](#publish-now)
   * [稍後發佈資產](#publish-later)

## 現在發佈資產 {#publish-now}

若要將所選資產發佈至 Brand Portal，請執行下列其中一項操作：

* 在工具列中選取&#x200B;**[!UICONTROL 快速發佈]**。然後，從功能表中選取&#x200B;**[!UICONTROL 發佈至Brand Portal]**。

* 在工具列中選取&#x200B;**[!UICONTROL 管理出版物]**。

   1. 然後，從&#x200B;**[!UICONTROL Action]**&#x200B;中選擇&#x200B;**[!UICONTROL 發佈到Brand Portal]**，從&#x200B;**[!UICONTROL Scheduling]**&#x200B;中選擇&#x200B;**[!UICONTROL Now]**。 點選/按一下&#x200B;**[!UICONTROL Next]。**

   2. 在&#x200B;**[!UICONTROL Scope]**&#x200B;中，確認您的選取項目，並點選/按一下&#x200B;**[!UICONTROL 發佈至Brand Portal]**。

系統會顯示訊息，指出資產已排入佇列，等候發佈至 Brand Portal。登入Brand Portal介面以查看已發佈的資產。

## 稍後發佈資產 {#publish-later}

若要將資產發佈至 Brand Portal 的動作安排在之後的日期或時間：

1. 選取要發佈的資產/資料夾後，請從頂端的工具列選取&#x200B;**[!UICONTROL 管理出版物]**。
2. 在&#x200B;**[!UICONTROL 管理出版物]**&#x200B;頁面上，從&#x200B;**[!UICONTROL Action]**&#x200B;中選擇&#x200B;**[!UICONTROL 發佈到Brand Portal]**，然後從&#x200B;**[!UICONTROL Scheduling]**&#x200B;中選擇&#x200B;**[!UICONTROL Later]**。

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

3. 選取&#x200B;**[!UICONTROL 啟用日期]**&#x200B;並指定時間。點選/按一下&#x200B;**[!UICONTROL Next]**。
4. 選取&#x200B;**[!UICONTROL 啟用日期]**&#x200B;並指定時間。點選/按一下&#x200B;**[!UICONTROL Next]**。
5. 在&#x200B;**[!UICONTROL 工作流程]**&#x200B;底下指定「工作流程標題」。點選/按一下&#x200B;**[!UICONTROL 稍後發佈]**。

   ![publishworkflow](assets/publishworkflow.png)

現在，登入Brand Portal ，查看已發佈的資產是否可在Brand Portal介面上使用。

![bp_631_landing_page](assets/bp_landing_page.png)

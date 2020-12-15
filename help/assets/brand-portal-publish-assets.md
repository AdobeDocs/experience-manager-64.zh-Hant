---
title: 將資料夾發佈至 Brand Portal
description: 瞭解如何將資產發佈及解除發佈至品牌入口網站。
contentOwner: VG
translation-type: tm+mt
source-git-commit: f09853921dec6602952f369982a1563c7e4a9727
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 35%

---


# 將資產發佈至 Brand Portal {#publish-assets-to-brand-portal}

身為Adobe Experience Manager(AEM)Assets管理員，您可以將資產發佈至組織的AEM Assets品牌入口網站例項（或將發佈工作流程排程至稍後的日期／時間）。 不過，您必須先將AEM資產與品牌入口網站一起設定。 如需詳細資訊，請參閱[使用 Brand Portal 設定 AEM Assets](configure-aem-assets-with-brand-portal.md)。

在您發佈資產後，品牌入口網站的使用者即可使用它。

如果您在AEM Assets中對原始資產進行後續修改，則在您重新發佈資產之前，這些變更不會反映在品牌入口網站中。 這項功能可確保對進行中工作所作的變更不會出現在 Brand Portal 中。Brand Portal 僅提供管理員發佈的已核准變更。

複製成功後，您可以將資產、檔案夾和系列發佈至品牌入口網站。 若要將資產發佈至品牌入口網站，請依照下列步驟進行：

>[!NOTE]
>
>Adobe 建議將發佈時間交錯開來，尤其建議選擇非尖峰時段，如此 AEM 作者才不會佔用過多資源。

1. 從「資產」主控台，將滑鼠指標暫留在所要的資產上，然後從快速動作中選取「發佈」(**[!UICONTROL Publish)]**&#x200B;選項。

   或者，選取您要發佈至品牌入口網站的資產。

   ![publish2bp-2](assets/publish2bp-2.png)

2. 若要將資產發佈至品牌入口網站，可使用下列兩個選項：
   * [立即發佈資產](#publish-now)
   * [稍後發佈資產](#publish-later)

## 現在發佈資產 {#publish-now}

若要將所選資產發佈至 Brand Portal，請執行下列其中一項操作：

* 在工具列中選取&#x200B;**[!UICONTROL 快速發佈]**。然後，從功能表中選擇「發佈至品牌入口網站」]**。**[!UICONTROL 

* 在工具列中選取&#x200B;**[!UICONTROL 管理出版物]**。

   1. 然後，從&#x200B;**[!UICONTROL Action]**&#x200B;選擇&#x200B;**[!UICONTROL 發佈至品牌入口網站]**，從&#x200B;**[!UICONTROL Scheduling]**&#x200B;選擇&#x200B;**[!UICONTROL Now]**。 點選／按一下&#x200B;**[!UICONTROL Next]。**

   2. 在&#x200B;**[!UICONTROL Scope]**&#x200B;中，確認您的選擇，並點選／按一下「發佈至品牌入口網站」。****

系統會顯示訊息，指出資產已排入佇列，等候發佈至 Brand Portal。登入品牌入口網站介面，以檢視已發佈的資產。

## 稍後發佈資產 {#publish-later}

若要將資產發佈至 Brand Portal 的動作安排在之後的日期或時間：

1. 在您選取要發佈的資產／檔案夾後，請從頂端的工具列選取「管理出版物」(**[!UICONTROL Manage Publication)。]**
2. 在&#x200B;**[!UICONTROL 管理出版物]**&#x200B;頁面上，從&#x200B;**[!UICONTROL Action]**&#x200B;選擇&#x200B;**[!UICONTROL 發佈至品牌入口網站]**，並從&#x200B;**[!UICONTROL Scheduling]**&#x200B;選擇&#x200B;**[!UICONTROL Later]**。

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

3. 選取&#x200B;**[!UICONTROL 啟用日期]**&#x200B;並指定時間。點選／按一下&#x200B;**[!UICONTROL Next]**。
4. 選取&#x200B;**[!UICONTROL 啟用日期]**&#x200B;並指定時間。點選／按一下&#x200B;**[!UICONTROL Next]**。
5. 在&#x200B;**[!UICONTROL 工作流程]**&#x200B;底下指定「工作流程標題」。點選／按一下&#x200B;**[!UICONTROL 稍後發佈]**。

   ![publishworkflow](assets/publishworkflow.png)

現在，請登入品牌入口網站，查看發佈的資產是否可在品牌入口網站介面上使用。

![bp_631_landing_page](assets/bp_landing_page.png)

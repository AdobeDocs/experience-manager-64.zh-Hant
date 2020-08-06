---
title: 將集合發佈至 Brand Portal
description: 瞭解如何將系列發佈及解除發佈至品牌入口網站。
contentOwner: VG
translation-type: tm+mt
source-git-commit: 33210032c45e38963aed429e70eec4095c5d75f1
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 21%

---


# 將集合發佈至 Brand Portal {#publish-collections-to-brand-portal}

身為Adobe Experience Manager(AEM)Assets管理員，您可以發佈系列至您組織的AEM Assets品牌入口網站例項。 不過，您必須先將AEM Assets與品牌入口網站整合。 如需詳細資訊，請參閱[使用 Brand Portal 設定 AEM Assets](configure-aem-assets-with-brand-portal.md)。

如果您在AEM Assets中對原始系列進行後續修改，這些變更將不會反映在品牌入口網站中，直到您再次發佈系列為止。 此特性可確保在品牌入口網站中無法使用進行中的變更。 Brand Portal 僅提供管理員發佈的已核准變更。

>[!NOTE]
>
>內容片段無法發佈至 Brand Portal。Therefore, if you select content fragment(s) on AEM Author, then **[Publish to Brand Portal]** action is not available.
>
>如果包含內容片段的系列是從AEM Author發佈至品牌入口網站，則資料夾的所有內容（內容片段除外）都會複製至品牌入口網站介面。

## 將系列發佈至品牌入口網站 {#publish-a-collection-to-brand-portal}

1. 在AEM Assets UI中，點選／按一下AEM標誌。 然後，從「導 **[!UICONTROL 覽」頁面前往「資產]** > **[!UICONTROL 系列]** 」。
2. 從「系列」主控台中，選取您要發佈至品牌入口網站的系列。

   ![select_collection](assets/select_collection.png)

3. From the toolbar, tap/click **[!UICONTROL Publish to Brand Portal]**.

   ![publish_to_bp_icon](assets/publish_to_bp_icon.png)

4. In the confirmation dialog, tap/click **[!UICONTROL Publish]**.
5. 關閉確認訊息。
6. 以管理員身分登入品牌入口網站。 已發佈的集合可在「集合」控制台中使用。

   ![published_collection](assets/published_collection.png)

## 取消發佈集合 {#unpublish-collections}

您可以解除發佈您從AEM Assets發佈至品牌入口網站的系列。 在您解除發佈原始系列後，品牌入口網站使用者將無法再使用其副本。

1. 從AEM Assets例項的「系列」主控台，選取您要解除發佈的系列。

   ![select_collection-1](assets/select_collection-1.png)

2. From the toolbar, tap/click the **[!UICONTROL Remove from Brand Portal]** icon.

   ![remove_from_bp_icon](assets/remove_from_bp_icon.png)

3. In the dialog, tap/click **[!UICONTROL Unpublish]**.
4. 關閉確認訊息。集合會從 Brand Portal 介面中移除。

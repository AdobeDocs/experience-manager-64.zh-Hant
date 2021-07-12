---
title: 將集合發佈至 Brand Portal
description: 了解如何將集合發佈和取消發佈至Brand Portal。
contentOwner: VG
feature: 品牌入口網站
role: User
exl-id: c2c6759e-f763-405e-9e45-5a90b9d32df2
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 21%

---

# 將集合發佈至 Brand Portal {#publish-collections-to-brand-portal}

身為Adobe Experience Manager(AEM)Assets管理員，您可以將集合發佈至貴組織的AEM Assets Brand Portal例項。 不過，您必須先整合AEM Assets與Brand Portal。 如需詳細資訊，請參閱[使用 Brand Portal 設定 AEM Assets](configure-aem-assets-with-brand-portal.md)。

如果您後續修改了AEM Assets中的原始系列，在您再次發佈系列之前，Brand Portal不會反映這些變更。 此特性可確保Brand Portal中無法使用進行中的變更。 Brand Portal 僅提供管理員發佈的已核准變更。

>[!NOTE]
>
>內容片段無法發佈至 Brand Portal。因此，如果您在AEM作者上選取內容片段，則無法使用&#x200B;**[發佈至Brand Portal]**&#x200B;動作。
>
>如果從AEM Author將包含內容片段的集合發佈至Brand Portal，則除了內容片段以外，資料夾的所有內容都會複製到Brand Portal介面。

## 將集合發佈至Brand Portal {#publish-a-collection-to-brand-portal}

1. 在AEM Assets UI中，點選/按一下AEM標誌。 然後，從&#x200B;**[!UICONTROL 導覽]**&#x200B;頁面前往&#x200B;**[!UICONTROL 資產>集合]**。
2. 在集合控制台中，選取您要發佈至Brand Portal的集合。

   ![select_collection](assets/select_collection.png)

3. 在工具列中，點選/按一下「**[!UICONTROL 發佈至Brand Portal]**」。

   ![publish_to_bp_icon](assets/publish_to_bp_icon.png)

4. 在確認對話方塊中，點選/按一下&#x200B;**[!UICONTROL Publish]**。
5. 關閉確認訊息。
6. 以管理員身分登入Brand Portal。 已發佈的集合可在「集合」控制台中使用。

   ![published_collection](assets/published_collection.png)

## 取消發佈集合 {#unpublish-collections}

您可以取消發佈從AEM Assets發佈至Brand Portal的集合。 取消發佈原始集合後，Brand Portal使用者將無法再使用集合的副本。

1. 在AEM Assets例項的集合控制台中，選取您要取消發佈的集合。

   ![select_collection-1](assets/select_collection-1.png)

2. 在工具列中，點選/按一下「從Brand Portal移除」圖示。****

   ![remove_from_bp_icon](assets/remove_from_bp_icon.png)

3. 在對話方塊中，點選/按一下&#x200B;**[!UICONTROL 取消發佈]**。
4. 關閉確認訊息。集合會從 Brand Portal 介面中移除。

---
title: 將集合發佈至 Brand Portal
description: 了解如何將集合發佈和取消發佈至Brand Portal。
contentOwner: VG
feature: Brand Portal
role: User
exl-id: c2c6759e-f763-405e-9e45-5a90b9d32df2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 21%

---

# 將集合發佈至 Brand Portal {#publish-collections-to-brand-portal}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

身為Adobe Experience Manager Assets管理員，您可以將集合發佈至 [!DNL Experience Manager Assets Brand Portal] 例項。 不過，您必須先將Assets與Brand Portal整合。 如需詳細資訊，請參閱[使用 Brand Portal 設定 Assets](configure-aem-assets-with-brand-portal.md)。

如果您後續在Assets中修改原始集合，在您再次發佈集合之前，Brand Portal不會反映這些變更。 此特性可確保Brand Portal中無法使用進行中的變更。 Brand Portal 僅提供管理員發佈的已核准變更。

>[!NOTE]
>
>內容片段無法發佈至 Brand Portal。因此，如果您在上選取內容片段 [!DNL Experience Manager] 然後是作者 **[發佈至Brand Portal]** 無法使用動作。
>
>如果從發佈包含內容片段的集合 [!DNL Experience Manager] 製作至Brand Portal，然後資料夾（內容片段除外）的所有內容都會複製至Brand Portal介面。

## 將集合發佈至Brand Portal {#publish-a-collection-to-brand-portal}

1. 在「資產」UI中，點選/按一下 [!DNL Experience Manager] 標誌。 然後，前往 **[!UICONTROL 資產>集合]** 從 **[!UICONTROL 導覽]** 頁面。
2. 在集合控制台中，選取您要發佈至Brand Portal的集合。

   ![select_collection](assets/select_collection.png)

3. 從工具列，點選/按一下 **[!UICONTROL 發佈至Brand Portal]**.

   ![publish_to_bp_icon](assets/publish_to_bp_icon.png)

4. 在確認對話方塊中，點選/按一下 **[!UICONTROL 發佈]**.
5. 關閉確認訊息。
6. 以管理員身分登入Brand Portal。 已發佈的集合可在「集合」控制台中使用。

   ![published_collection](assets/published_collection.png)

## 取消發佈集合 {#unpublish-collections}

您可以從Assets取消發佈集合到Brand Portal。 取消發佈原始集合後，Brand Portal使用者將無法再使用集合的副本。

1. 從 [!DNL Assets] 例項，然後選取您要取消發佈的集合。

   ![select_collection-1](assets/select_collection-1.png)

2. 從工具列，點選/按一下 **[!UICONTROL 從Brand Portal移除]** 表徵圖。

   ![remove_from_bp_icon](assets/remove_from_bp_icon.png)

3. 在對話方塊中，點選/按一下 **[!UICONTROL 取消發佈]**.
4. 關閉確認訊息。集合會從 Brand Portal 介面中移除。

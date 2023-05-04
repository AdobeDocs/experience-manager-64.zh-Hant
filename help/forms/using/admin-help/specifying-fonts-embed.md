---
title: 指定要嵌入的字型
seo-title: Specifying fonts to embed
description: 了解如何指定要內嵌的字型。
seo-description: Learn how to specify fonts to embed.
uuid: 97de6f98-ed3b-4a93-854a-193a967b4672
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 4c83694c-b00f-40be-9ac4-f5785cd60741
exl-id: 0bde7192-9d21-40b4-9164-314c9a30153b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 2%

---

# 指定要嵌入的字型 {#specifying-fonts-to-embed}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

您可以指定一律嵌入或絕不嵌入Forms服務所產生表單的字型。 嵌入字型會增加表單的檔案大小。 嵌入用戶在其系統上很少使用的異常字型。 請勿嵌入他們通常安裝的通用字型。

>[!NOTE]
>
>如果您已指定Forms的自訂XCI檔案，XCI檔案中的內嵌字型選項會覆寫這些設定。 (請參閱 [配置Forms位置](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).)

1. 在管理控制台中，按一下 **[!UICONTROL 服務>Forms]**.
1. 在 **[!UICONTROL 字型內嵌設定]**，在 **[!UICONTROL 始終嵌入字型]** 框中，鍵入要與表單一起嵌入的字型的名稱，並以逗號分隔。 指定的字型只有在窗體中使用時才會嵌入生成的窗體。 如果已在傳遞至服務的XCI檔案中開啟內嵌字型選項，則會忽略此設定，因為在這種情況下，PDF中使用的所有字型一律會內嵌。
1. 在 **[!UICONTROL 永不嵌入字型]** 框中，鍵入不要與表單嵌入的字型的名稱，並以逗號分隔。 您指定的字型不會嵌入到PDF中，即使這些字型用於生成的PDF中亦然。 如果傳遞至服務的XCI檔案中的內嵌字型選項已關閉，則會忽略此設定，因為在這種情況下，PDF中使用的字型不會嵌入。
1. 按一下「**[!UICONTROL 儲存]**」。

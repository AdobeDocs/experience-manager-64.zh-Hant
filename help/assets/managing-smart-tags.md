---
title: 管理智慧標籤
description: 更新或移除不正確的智慧標籤，以改善標籤的相關性
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: fd3eedf0-f222-45bf-aac7-90da6b7b7087
contentOwner: AG
discoiquuid: 3394b56a-3054-419b-9547-5740f8c35071
feature: Smart Tags,Tagging,Search
role: User
exl-id: 05f43e43-ac72-4ab1-a373-687c137d2bed
source-git-commit: 937c9425e276f67486fba1d4563799fe68d35cc7
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 2%

---

# 管理智慧標籤 {#managing-smart-tags}

您可以組織智慧標籤來移除任何可能指派給品牌影像的不準確標籤，以便僅顯示最相關的標籤。

協調智慧標籤也可確保影像顯示在最相關標籤的搜尋結果中，以利調整影像的標籤式搜尋。 從本質上講，這有助於消除不相關影像在搜索結果中出現的可能性。

您也可以指派較高的排名給標籤，以增加與影像相關的版本。 根據特定標籤執行搜尋時，提升影像的標籤會增加影像出現在搜尋結果中的機率。

1. 在OmniSearch方塊中，根據標籤搜尋資產。
1. Inspect搜尋結果，以識別您找不到與搜尋相關的影像。
1. 選取影像，然後按一下/點選工具列中的&#x200B;**[!UICONTROL 管理標籤]**&#x200B;圖示。
1. 從&#x200B;**[!UICONTROL 管理標籤]**&#x200B;頁面檢查標籤。 如果您不想要根據特定標籤來搜尋影像，請選取標籤，然後按一下/點選工具列中的&#x200B;**[!UICONTROL Delete]**&#x200B;圖示。 或者，按一下/點選標籤旁出現的(**[!UICONTROL X]**)符號。
1. 若要指派較高的排名給標籤，請選取標籤，然後按一下/點選工具列中的&#x200B;**[!UICONTROL Promote]**&#x200B;圖示。 您促銷的標籤會移至&#x200B;**[!UICONTROL Tags]**&#x200B;區段。
1. 按一下/點 **[!UICONTROL 選「儲存]**」，然後按一下/點選「 **[!UICONTROL 確定]** 」以關閉「成功」對話方塊。
1. 導覽至影像的屬性頁面。 請注意，您促銷的標籤被指派為高關聯性，因此在搜尋結果中會顯示得較高。

## 了解使用智慧標籤的[!DNL Experience Manager]搜尋結果 {#understand-search-results-with-smart-tags}

預設情況下， [!DNL Experience Manager]搜索將搜索詞與`AND`子句組合。 使用智慧標籤不會變更此預設行為。 使用智慧標籤會新增額外的`OR`子句，以尋找套用智慧標籤中的任何搜尋詞。 例如，請考慮搜尋`woman running`。 依預設，中繼資料中只有`woman`或只有`running`關鍵字的資產不會出現在搜尋結果中。 不過，使用智慧標籤標示的`woman`或`running`資產會顯示在這類搜尋查詢中。 搜索結果是，

* 元資料中同時包含關鍵字`woman`和`running`的資產。
* 使用任一關鍵字標示的資產智慧型。

會先顯示符合中繼資料欄位中所有搜尋詞的搜尋結果，接著顯示符合智慧標籤中任何搜尋詞的搜尋結果。 在上述範例中，搜尋結果的顯示約略順序為：

1. 在各種中繼資料欄位中符合`woman running`。
1. 在智慧標籤中符合`woman running`。
1. 在智慧標籤中符合`woman`或`running`。

---
title: 管理智慧標籤
description: 更新或移除不正確的智慧型標籤，以改善標籤的相關性
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: fd3eedf0-f222-45bf-aac7-90da6b7b7087
contentOwner: AG
discoiquuid: 3394b56a-3054-419b-9547-5740f8c35071
feature: Smart Tags,Tagging,Search
role: Business Practitioner
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 3%

---


# 管理智慧標籤{#managing-smart-tags}

您可以組織智慧型標籤，移除可能指派給品牌影像的任何不正確標籤，以便只顯示最相關的標籤。

協調智慧型標籤也有助於調整以標籤為基礎的影像搜尋，確保影像出現在搜尋結果中，以找出最相關的標籤。 基本上，它有助於消除不相關影像在搜尋結果中顯示的機率。

您也可以指派較高的排名給標籤，以增加與影像相關的相關性。 促銷影像的標籤會增加當根據特定標籤執行搜尋時，在搜尋結果中出現影像的機率。

1. 在OmniSearch方塊中，根據標籤搜尋資產。
1. Inspect搜尋結果，以識別與您的搜尋無關的影像。
1. 選取影像，然後按一下／點選工具列中的「管理標籤&#x200B;]**」圖示。**[!UICONTROL 
1. 從&#x200B;**[!UICONTROL 管理標籤]**&#x200B;頁面檢查標籤。 如果您不想根據特定標籤來搜尋影像，請選取標籤，然後從工具列按一下／點選「刪除」圖示。 ****&#x200B;或者，按一下／點選標籤旁邊顯示的(**[!UICONTROL X]**)符號。
1. 若要指派較高的排名給標籤，請選取標籤，然後從工具列按一下／點選&#x200B;**[!UICONTROL Promote]**&#x200B;圖示。 您促銷的標籤會移至&#x200B;**[!UICONTROL Tags]**&#x200B;區段。
1. 按一下/點 **[!UICONTROL 選「儲存]**」，然後按一下/點選「 **[!UICONTROL 確定]** 」以關閉「成功」對話方塊。
1. 導覽至影像的屬性頁面。 請注意，您促銷的標籤已指派高關聯性，因此在搜尋結果中會顯示高度。

## 使用AEM智慧型標籤{#understand-search-results-with-smart-tags}瞭解搜尋結果

依預設，AEM搜尋會將搜尋詞與`AND`子句結合。 使用智慧型標籤不會變更此預設行為。 使用智慧型標籤會新增額外的`OR`子句，以尋找套用智慧型標籤中的任何搜尋詞。 例如，請考慮搜索`woman running`。 預設情況下，中繼資料中只包含`woman`或`running`關鍵字的資產不會出現在搜尋結果中。 不過，使用智慧型標籤標籤以`woman`或`running`標籤的資產會出現在此類搜尋查詢中。 所以搜索結果是，

* 資產，其中包含中繼資料中的`woman`和`running`關鍵字。
* 資產智慧標籤為其中一個關鍵字。

會先顯示符合中繼資料欄位中所有搜尋詞的搜尋結果，接著顯示符合智慧標籤中任何搜尋詞的搜尋結果。 在上述範例中，搜尋結果的顯示近似順序為：

1. 與各中繼資料欄位中`woman running`的相符項目。
1. 與智慧型標籤中`woman running`的相符項目。
1. 在智慧型標籤中符合`woman`或`running`。

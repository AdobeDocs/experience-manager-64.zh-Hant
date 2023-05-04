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
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 3%

---

# 管理智慧標籤 {#managing-smart-tags}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

您可以組織智慧標籤來移除任何可能指派給品牌影像的不準確標籤，以便僅顯示最相關的標籤。

協調智慧標籤也可確保影像顯示在最相關標籤的搜尋結果中，以利調整影像的標籤式搜尋。 從本質上講，這有助於消除不相關影像在搜索結果中出現的可能性。

您也可以指派較高的排名給標籤，以增加與影像相關的版本。 根據特定標籤執行搜尋時，提升影像的標籤會增加影像出現在搜尋結果中的機率。

1. 在OmniSearch方塊中，根據標籤搜尋資產。
1. Inspect搜尋結果，以識別您找不到與搜尋相關的影像。
1. 選取影像，然後按一下/點選 **[!UICONTROL 管理標籤]** 圖示。
1. 從 **[!UICONTROL 管理標籤]** 頁面，檢查標籤。 如果您不想要根據特定標籤來搜尋影像，請選取標籤，然後按一下/點選 **[!UICONTROL 刪除]** 圖示。 或者，按一下/點選(**[!UICONTROL X]**)符號。
1. 若要指派較高的排名給標籤，請選取標籤，然後按一下/點選 **[!UICONTROL 提升]** 圖示。 您促銷的標籤會移至 **[!UICONTROL 標籤]** 區段。
1. 按一下/點 **[!UICONTROL 選「儲存]**」，然後按一下/點選「 **[!UICONTROL 確定]** 」以關閉「成功」對話方塊。
1. 導覽至影像的屬性頁面。 請注意，您促銷的標籤被指派為高關聯性，因此在搜尋結果中會顯示得較高。

## 了解 [!DNL Experience Manager] 使用智慧標籤搜尋結果 {#understand-search-results-with-smart-tags}

依預設， [!DNL Experience Manager] 搜尋會將搜尋詞與 `AND` 條。 使用智慧標籤不會變更此預設行為。 使用智慧標籤會新增 `OR` 子句，查找應用智慧標籤中的任何搜索詞。 例如，請考慮搜尋 `woman running`. 只有 `woman` 或 `running` 預設情況下，中繼資料中的關鍵字不會出現在搜尋結果中。 不過，標籤有 `woman` 或 `running` 使用智慧標籤會出現在這類搜尋查詢中。 搜索結果是，

* 具有兩個關鍵字的資產， `woman` 和 `running` 在中繼資料中。
* 使用任一關鍵字標示的資產智慧型。

會先顯示符合中繼資料欄位中所有搜尋詞的搜尋結果，接著顯示符合智慧標籤中任何搜尋詞的搜尋結果。 在上述範例中，搜尋結果的顯示約略順序為：

1. 比對 `woman running` 在各種中繼資料欄位中。
1. 比對 `woman running` 在智慧標籤中。
1. 比對 `woman` 或 `running` 在智慧標籤中。

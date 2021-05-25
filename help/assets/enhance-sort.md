---
title: 增強AEM中的資產排序功能
description: 了解AEM Assets如何透過伺服器端排序功能，一次性排序資料夾資產或搜尋查詢，而非在用戶端以批次方式排序資產。
contentOwner: AG
feature: 搜尋
role: Business Practitioner
exl-id: aa24ca68-d94e-4bd4-a5cc-113906650a2e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 3%

---

# 增強AEM {#enhanced-sorting-of-assets-in-aem}中的資產排序功能

了解AEM Assets如何透過伺服器端排序功能，一次性排序資料夾資產或搜尋查詢，而非在用戶端以批次方式排序資產。

Adobe Experience Manager(AEM)Assets的搜尋功能已經過增強，現在可以在資料夾清單檢視和搜尋結果頁面中，有效排序大量資產。 您也可以排序時間軸項目。

AEM Assets部署了伺服器端排序功能，可一次排序資料夾或搜尋查詢中的整組資產（無論大小），而非在用戶端依批次排序。 這樣，預先擷取的結果便可快速顯示在使用者介面上，讓排序操作更具回應性和快速性。

## 在清單檢視{#sorting-assets-in-list-view}中排序資產

AEM Assets可讓您根據下列欄位來排序資料夾資產：

* 地區設定
* 狀態
* 類型
* 大小
* 評等
* 修改日期
* 發佈日期
* 使用狀況
* 點按數
* 印象
* 已簽出

1. 導覽至包含大量資產的資料夾。
1. 按一下/點選「版面」圖示，然後切換至清單檢視。

   ![chlimage_1-394](assets/chlimage_1-394.png)

1. 按一下/點選資產清單中任何欄標題旁的「排序」圖示。

   ![chlimage_1-395](assets/chlimage_1-395.png)

   資產清單會根據欄位值排序。

   ![chlimage_1-396](assets/chlimage_1-396.png)

>[!NOTE]
>
>若要排序`Name`或`Title`欄中的值，請覆蓋`/libs/dam/gui/content/commons/availablecolumns`並將`sortable`的值變更為`True`。

## 排序搜尋結果中的資產{#sorting-assets-in-search-results}

您可以根據下列欄位來排序搜尋結果：

* 標題
* 狀態
* 類型
* 大小
* 修改日期
* 發佈日期

1. 從OmniSearch方塊，根據所需條件搜尋資產。

   ![chlimage_1-397](assets/chlimage_1-397.png)

1. 按一下/點選「版面」圖示，然後切換至清單檢視。 如果搜索結果已顯示在清單視圖中，請跳過此步驟。
1. 按一下/點選資產清單中任何欄標題旁的「排序」圖示。 資產清單會根據欄位值排序。

   ![chlimage_1-398](assets/chlimage_1-398.png)

## 在時間軸{#sorting-assets-in-timeline}中排序資產

AEM Assets可讓您按時間順序排序時間軸項目，例如註解、版本、工作流程和活動。

1. 從「資產」UI中，選取您要顯示時間軸的資產。
1. 按一下/點選GolbalNav圖示，然後選取&#x200B;**[!UICONTROL 時間軸]**。

   ![chlimage_1-399](assets/chlimage_1-399.png)

1. 在時間軸中，從清單中選取項目。 例如，選取&#x200B;**[!UICONTROL Comments]**&#x200B;以顯示與資產相關聯的註解清單。

   ![chlimage_1-400](assets/chlimage_1-400.png)

1. 按一下/點選&#x200B;**[!UICONTROL Date]**&#x200B;標籤旁的&#x200B;**[!UICONTROL 排序]**&#x200B;圖示。 註解會根據您的選取，以時間順序/反向時間順序列出，並依此順序新增至資產。

   ![chlimage_1-401](assets/chlimage_1-401.png)

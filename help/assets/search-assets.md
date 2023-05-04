---
title: 在AEM中搜尋資產
description: 了解如何在 [!DNL Experience Manager] ，以及如何使用顯示在搜尋中的資產。
contentOwner: AG
feature: Search,Metadata
role: User
exl-id: cc1a5946-e13d-4433-a25a-d297fd07e2e4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 3%

---

# 搜尋 [!DNL Experience Manager] 中的資產 {#search-assets-in-aem}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

了解如何在 [!DNL Experience Manager] ，以及如何使用顯示在搜尋中的資產。

使用「篩選」面板來搜尋資產、資料夾、標籤和中繼資料。 您可以使用萬用字元星號來搜尋字串的部分。

「篩選器」面板提供多種選項，讓您以多種方式來搜尋資產和資料夾，而非以一般分類順序來搜尋。

您可以根據下列選項（述詞）進行搜尋：

* 檔案類型
* 檔案大小
* 欄位名稱
* 上次修改時間
* 狀態
* 方向
* 樣式
* Insights

<!-- TBD keystroke 65 article and port applicable changes here. This content goes. -->

您可以自訂「篩選器」面板，並使用 [搜尋面向](search-facets.md). 要顯示「篩選器」面板，請執行以下步驟：

1. 在「資產」使用者介面中，點選/按一下 ![search_icon](assets/search_icon.png) ，以顯示「Omnisearch」方塊。
1. 輸入您的搜索詞並按Enter鍵。 或者，只需按Enter鍵，而不輸入任何搜索詞。 請勿輸入任何前導空格，否則搜尋無法運作。

1. 點選/按一下GlobalNav圖示。 隨即顯示「篩選器」面板。

   ![filters_panel-1](assets/filters_panel-1.png)

   會根據您搜尋的項目類型，在搜尋結果頂端指出符合的數量。

   ![number_of_searches](assets/number_of_searches.png)

## 搜尋檔案類型 {#search-for-file-types}

「篩選器」面板可協助您為搜尋體驗增加更精細的度，並讓搜尋功能更為通用。 您可以輕鬆深入到所需的詳細程度。

例如，如果您要尋找影像，請使用 **[!UICONTROL 檔案類型]** 謂詞，選擇要點陣圖影像還是向量影像。

![image_type](assets/image_type.png)

您可以指定影像的MIME類型，以進一步縮小搜尋範圍。

![mime_type](assets/mime_type.png)

同樣，在搜索文檔時，可以指定格式，例如PDF或MS Word。

![檔案](assets/documents.png)

## 根據檔案大小搜尋 {#search-based-on-file-size}

使用 **檔案大小** 述詞以根據資產大小來搜尋資產。 您可以指定大小範圍的下限和上限以縮小搜尋範圍。 您也可以指定單位，例如千位元組、兆位元組等。

![unit_of_measure](assets/unit_of_measure.png)

## 根據上次修改資產的時間進行搜尋 {#search-based-on-when-assets-are-last-modified}

如果您管理進行中資產或監控審核工作流程，則可以根據準確的時間戳記搜尋上次修改資產的時間。 例如，指定資產修改前後的日期。

![last_modified_dates](assets/last_modified_dates.png)

您也可以使用下列選項，在搜尋中達到更高的精細度：

![timestamp](assets/timestamp.png)

## 根據狀態進行搜索 {#search-based-on-status}

使用 **狀態** 述詞，以根據各種狀態類型（例如發佈、核准、結帳和到期）來搜尋資產。

![狀態](assets/status.png)

例如，在監控資產發佈時，您可以使用適當的選項來搜尋已發佈的資產。

![發佈](assets/publish.png)

在監控資產的審閱狀態時，請使用適當的選項查找已批准的資產或等待批准的資產。

![核准](assets/approval.png)

## 根據前瞻分析資料進行搜尋 {#search-based-on-insights-data}

使用 **前瞻分析** 述詞，以根據從各種創意應用程式取得的使用量統計資料來搜尋資產。 使用資料分組如下：

* 使用分數
* 印象
* 點擊次數
* 顯示資產的媒體管道

![分析](assets/insights.png)

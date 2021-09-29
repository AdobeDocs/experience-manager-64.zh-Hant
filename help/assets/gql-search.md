---
title: GQL全文搜索
description: 在 [!DNL Experience Manager] Assets中探索GQL全文搜索功能。 使用它根據特定中繼資料（例如標題、說明和作者名稱）來搜尋資產。
contentOwner: AG
feature: Search,Metadata
role: User
exl-id: e819501c-4ac3-447f-944c-67adc42e8c61
source-git-commit: cc9b6d147a93688e5f96620d50f8fc8b002e2d0d
workflow-type: tm+mt
source-wordcount: '873'
ht-degree: 2%

---

# GQL全文搜索 {#gql-full-text-search}

探索[!DNL Experience Manager]資產中的GQL全文搜索功能。 使用它根據特定中繼資料（例如標題、說明和作者名稱）來搜尋資產。

GQL全文搜尋功能可讓您根據特定中繼資料來搜尋資產，例如標題、說明、作者等。

若要根據資產的中繼資料（例如標題）來搜尋資產，請在搜尋面板中指定中繼資料關鍵字及其後的值。 GQL全文搜尋功能只會擷取其中繼資料與您輸入之對應值完全相符的資產。

例如，若要搜尋標題為「Target」的資產，請執行下列步驟：

## 搜尋資產 {#searching-assets}

1. 在「資產」使用者介面的工具列中，按一下或點選&#x200B;**[!UICONTROL Search]**&#x200B;圖示，以顯示「Omnisearch」方塊。

   ![](assets/do-not-localize/chlimage_1.png)

1. 將游標置於Omnisearch框中，按Enter鍵。
1. 按一下或點選「全域導覽」圖示，以顯示&#x200B;**[!UICONTROL Filters]**&#x200B;面板。
1. 在「全域搜尋」方塊中，指定值「Target」。 若要將搜尋限制在特定資料夾，請按一下或點選「篩選」面板中的「瀏覽」圖示，然後選取資料夾。 在這種情況下，只會在資料夾及其下的子資料夾中搜尋相符項目。

   >[!NOTE]
   >
   >您也可以對資料夾執行全文搜尋。 在這種情況下，必須指定非空白的全文搜索詞。

   ![gql_search](assets/gql_search.png)

1. 按&#x200B;**[!UICONTROL Enter]**&#x200B;鍵。 [!DNL Assets]使用者介面只會顯示標題完全符合「Target」的資產。

GQL全文搜尋功能可讓您根據下列項目來搜尋資產：

* 透過And運算結合您為多個中繼資料欄位（屬性）指定的值，所建立的複雜查詢
* 單一中繼資料欄位的多個值
* 子字串比對

GQL全文搜尋功能可讓您根據下列中繼資料屬性來搜尋資產。 屬性的名稱（例如作者、標題等）和值會區分大小寫。

>[!NOTE]
>
>GQL全文搜索僅適用於全文謂詞。

| 屬性 | 搜尋格式（Facet值） |
|---|---|
| [!UICONTROL 標題] | 標題：John |
| [!UICONTROL 產生器] | 建立者：約翰 |
| [!UICONTROL 參與者] | 貢獻者：John |
| [!UICONTROL 位置] | 位置：印度 |
| [!UICONTROL 說明] | 說明：&quot;範例影像&quot; |
| [!UICONTROL 建立者工具] | 建立工具：「Adobe Photoshop 7.0」 |
| [!UICONTROL 版權擁有者] | 版權人：&quot;Adobe Systems&quot; |
| [!UICONTROL 參與者] | 貢獻者：John |
| [!UICONTROL 使用條款] | 使用條款：「保留CopyRights」 |
| [!UICONTROL 已建立] | 已建立:YYYY-MM-DDTHH:MM:SS.000+05:30。YYYY-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL 到期日] | expires:YYYY-MM-DDTHH:MM:SS.000+05:30.YYYY-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL 準時] | ontime:YYYY-MM-DDTHH:MM:SS.000+05:30.YYYY-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL 關閉時間] | offtime:YYYY-MM-DDTHH:MM:SS.000+05:30.YYYY-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL 時間範圍] （過期日期、時間） | 面向欄位：下界……上界限 |
| [!UICONTROL 路徑] | /content/dam/&lt;資料夾名稱> |
| [!UICONTROL PDF 標題] | pdftitle:&quot;Adobe檔案&quot; |
| [!UICONTROL 主旨] | 主題：「培訓」 |
| [!UICONTROL 標記] | 標籤：&quot;Location And Travel&quot; |
| [!UICONTROL 類型] | 類型：&quot;image\png&quot; |
| [!UICONTROL 影像寬度] | width:lowerbound..上界限 |
| [!UICONTROL 影像高度] | height:lowerbound..上界限 |
| [!UICONTROL 人員] | person:John |

以下是複雜查詢的搜尋格式的一些範例：

* 若要顯示具有多個Facet欄位的所有資產(例如：title=John Doe and creator tool = Adobe Photoshop):

蒂爾特：&quot;John Doe&quot;創作工具：Adobe&amp;ast;

* 若要在Facet值不是單一字詞而是句子時顯示所有資產(例如：title=Scott Reynolds)

標題： 「Scott Reynolds」

* 若要顯示具有單一屬性多個值的資產(例如：title=Scott Reynolds或John Doe)

標題：「Scott Reynolds」或「John Doe」

* 若要顯示屬性值以特定字串開頭的資產(例如：標題是斯科特·雷諾茲)

標題：&quot;Scott&quot;

* 若要顯示屬性值結尾為特定字串的資產(例如：標題是斯科特·雷諾茲)

標題： 「Reynolds」

* 若要顯示包含特定字串之屬性值的資產(例如：title =巴塞爾會議室)

標題：&quot;會議&quot;;

* 若要顯示包含特定字串且具有特定屬性值的資產(例如：在標題=John Doe的資產中搜尋字串Adobe)

&amp;ast;Adobe&amp;ast;title:&quot;John Doe &quot;OR title:&quot;John Doe&quot; &amp;ast;Adobe&amp;ast;

>[!NOTE]
>
>屬性路徑、限制、大小和orderby不能與任何其他屬性連接。
>
>使用者產生屬性的關鍵字是其屬性編輯器中的欄位標籤（以小寫顯示），並移除空格。

>[!NOTE]
>
>如果您撰寫JCR查詢僅搜尋子資產，也會顯示相符的參考資產以及相符的子資產。

全文搜索還支援 — 、^等運算子。 若要將這些字母作為字串文本進行搜索，請以雙引號將搜索表達式括住。 例如，使用「筆記本 — 美容」，而不是「筆記本 — 美容」。

## Boosting Search {#boosting-search}

您可以改善特定資產的關鍵字相關性，以協助根據關鍵字提升搜尋。 換句話說，當您根據這些關鍵字進行搜尋時，您促銷特定關鍵字的影像會顯示在搜尋結果頂端。

1. 從資產UI，開啟您要促銷關鍵字之資產的屬性頁面。
1. 切換至&#x200B;**[!UICONTROL Advanced]**&#x200B;標籤，然後按一下/點選&#x200B;**[!UICONTROL Elevate for search keywords]**&#x200B;下的&#x200B;**[!UICONTROL Add]**。

   ![elevate_for_search](assets/elevate_for_search.png)

1. 在&#x200B;**[!UICONTROL 搜尋促銷]**&#x200B;方塊中，指定您要加大影像搜尋的關鍵字，然後按一下/點選&#x200B;**[!UICONTROL 新增]**。 如有必要，請以相同的方式指定多個關鍵字。

   ![add_search_word](assets/add_search_word.png)

1. 按一下/點選&#x200B;**[!UICONTROL 儲存並關閉]**。
1. 使用Omnisearch方塊搜尋關鍵字。 您促銷此關鍵字的資產會顯示在最上層搜尋結果中。

---
title: RTF 編輯器
seo-title: Rich Text Editor
description: RTF編輯器是將文字內容輸入AEM的基本建置區塊。
seo-description: The Rich Text Editor is a basic building block for inputting textual content into AEM.
uuid: 42001071-f7a7-475d-8aab-a8054303db68
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: adc697e1-4a1c-4985-8690-79ed77736fec
exl-id: 44cd0092-de40-4a72-a682-1e8f5906b2e5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1832'
ht-degree: 3%

---

# RTF 編輯器{#rich-text-editor}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

RTF編輯器是將文字內容輸入AEM的基本建置區塊。 它構成了各種元件的基礎，包括：

* 文字
* 文字影像
* 表格

## RTF 編輯器 {#rich-text-editor-2}

WYSIWYG編輯對話框提供了多種功能：

![cq55_rte_basicchars](assets/cq55_rte_basicchars.png)

>[!NOTE]
>
>可用的功能可針對個別專案進行設定，因此安裝時可能會有所不同。

## 就地編輯 {#in-place-editing}

除了以對話方塊為基礎的RTF編輯模式外，AEM也提供就地編輯模式，當文字顯示在頁面版面中時，可直接編輯文字。

在段落上按兩下（按兩下滑鼠即可進入就地編輯模式）（元件邊框現在會是橘色）。

您將能直接編輯頁面上的文字，而非在對話方塊視窗內。 只需進行變更，系統就會自動儲存。

![cq55_rte_inlineediting](assets/cq55_rte_inlineediting.png)

>[!NOTE]
>
>如果您已開啟內容尋找器，則索引標籤頂端會顯示包含RTE格式選項的工具列（如上所示）。
>
>如果未開啟內容尋找器，則不會顯示工具列。

目前，已針對 **文字** 和 **標題** 元件。

>[!NOTE]
>
>此 **標題** 元件設計為包含不帶換行符的短文本。 在「就地編輯模式」中編輯標題時，輸入換行符將開啟新的 **文字** 元件。

## RTF編輯器的功能 {#features-of-the-rich-text-editor}

RTF編輯器提供一系列功能，這些 [取決於設定](/help/sites-administering/rich-text-editor.md) 個別元件中。 觸控最佳化和傳統UI皆提供這些功能。

### 基本字元格式 {#basic-character-formats}

![](do-not-localize/cq55_rte_basicchars.png)

您可以在此將格式套用至選取（反白顯示）的字元；有些選項也有快捷鍵：

* 粗體(Ctrl-B)
* 斜體(Ctrl-I)
* 下划線(Ctrl-U)
* 下標
* 上標

![cq55_rte_basicchars_use](assets/cq55_rte_basicchars_use.png)

所有選項都會切換，因此重新選取會移除格式。

### 預先定義的樣式和格式 {#predefined-styles-and-formats}

![cq55_rte_stylesparagh](assets/cq55_rte_stylesparagraph.png)

您的安裝可包含預先定義的樣式和格式。 這些可搭配 **樣式** 和 **格式** 下拉式清單，可套用至您選取的文字。

樣式可套用至特定字串（與CSS關聯的樣式）:

![cq55_rte_styles_use](assets/cq55_rte_styles_use.png)

雖然格式被應用於整個文本段落(格式是基於HTML的):

![cq55_rte_paragh_use](assets/cq55_rte_paragraph_use.png)

只能更改特定格式(預設為 **段落**)。

樣式可移除；將游標置於已應用樣式的文本中，然後按一下移除表徵圖：

>[!CAUTION]
>
>實際上，請不要重新選擇已應用樣式或表徵圖將被停用的任何文本。

### 剪下，複製，貼上 {#cut-copy-paste}

![](do-not-localize/cq55_rte_cutcopypaste.png)

標準函式 **剪下** 和 **複製** 的URL區段。 幾種 **貼上** 被提供以適應不同的格式。

* 剪下(**Ctrl-X**)
* 複製(**Ctrl-C**)
* 貼上

   這是預設的貼上機制(**Ctrl-V**)(適用於元件；當安裝為現成可用時，此設定為「從字貼上」。

* 貼上為文字

   移除所有樣式和格式，僅貼上純文字。

* 從 Word 貼上

   這會將內容貼上為HTML（含一些必要的重新格式設定）。

### 還原，重做 {#undo-redo}

![](do-not-localize/cq55_rte_undoredo.png)

AEM會依時間順序保留目前元件中最近50個動作的記錄。 如有需要，這些動作可以嚴格依序復原（然後重新完成）。

>[!CAUTION]
>
>僅為當前編輯會話保留歷史記錄。 每次開啟元件進行編輯時，都會重新啟動。

>[!NOTE]
>
>50是預設的任務數。 對於您的安裝而言，這可能有所不同。

### 對齊方式 {#alignment}

![](do-not-localize/cq55_rte_alignment.png)

文字可以左對齊、中對齊或右對齊。

![cq55_rte_alignment_use](assets/cq55_rte_alignment_use.png)

### 縮排 {#indentation}

![](do-not-localize/cq55_rte_indent.png)

段落的縮進可以增加或減少。 所選段落將縮進，輸入的任何新文本將保留當前縮進級別。

![cq55_rte_indent_use](assets/cq55_rte_indent_use.png)

### 清單 {#lists}

![](do-not-localize/cq55_rte_lists.png)

可在文字中建立項目符號和編號清單。 選擇清單類型並開始鍵入或突出顯示要轉換的文本。 在這兩種情況下，行摘要都會啟動新的清單項目。

嵌套清單可透過縮進一或多個清單項目來達成。

只需將游標置於清單內，然後選取其他樣式，即可更改清單的樣式。 子清單也可以與包含清單有不同的樣式。 建立子清單後（透過縮排），即可套用此項目。

![cq55_rte_lists_use](assets/cq55_rte_lists_use.png)

### 連結 {#links}

![](do-not-localize/cq55_rte_links.png)

URL的連結（在您的網站內或外部位置）會透過醒目提示所需文字，然後按一下 **超連結** 圖示：

![](do-not-localize/chlimage_1-12.png)

對話方塊可讓您指定目標URL;以及是否應在新視窗中開啟它。

![cq55_rte_link_use](assets/cq55_rte_link_use.png)

您可以：

* 直接在URI中鍵入
* 使用網站地圖在您的網站中選取頁面
* 輸入URI，然後附加目標錨點；例如 `www.TargetUri.org#AnchorName`
* 僅輸入錨點（以參考「目前頁面」）;例如 `#anchor`
* 在內容尋找器中搜尋頁面，然後將頁面圖示拖放至超連結對話方塊中

>[!NOTE]
>
>URI可以前面加上為安裝配置的任何協定。 在標準安裝中，這些 `https://`, `ftp://`，和 `mailto:`. 未為安裝配置的協定將被拒絕，並標籤為無效。

要將游標置於連結文本內的任意位置，請按一下 **取消連結** 圖示：

![](do-not-localize/chlimage_1-13.png)

### 錨點 {#anchors}

![](do-not-localize/cq55_rte_anchor.png)

錨點可以通過定位游標或選擇某些文本在文本中的任意位置建立。 然後按一下 **錨點** 圖示以開啟對話方塊。

輸入錨點名稱，然後按一下 **確定** 儲存。

![cq55_rte_anchor_use](assets/cq55_rte_anchor_use.png)

編輯元件時會顯示錨點，現在可用於目標內的連結。

![chlimage_1-145](assets/chlimage_1-145.png)

### 查找和替換 {#find-and-replace}

![](do-not-localize/cq55_rte_findreplace.png)

AEM提供 **查找** 和 **取代** （尋找和取代）函式。

都有 **查找下一個** 按鈕，搜索開啟的元件以查找指定的文本。 您也可以指定是否需要比對大小寫（上/下）。

搜索將始終從文本中的當前游標位置開始。 到達元件結尾時，會顯示訊息，通知您下一個搜尋作業將從頂端開始。

![cq55_rte_find_use](assets/cq55_rte_find_use.png)

此 **取代** 選項 **查找**，然後 **取代** 具有指定文字的個別例項，或 **全部替換** 例項。

![cq55_rte_findreplace_use](assets/cq55_rte_findreplace_use.png)

### 影像 {#images}

您可以從內容尋找器拖曳影像，將其新增至文字。

![cq55_rte_image_use](assets/cq55_rte_image_use.png)

>[!NOTE]
>
>AEM也提供專用元件，以供進行更詳細的影像設定。 例如 **影像** 和 **文字影像** 元件可供使用。

### 拼寫檢查程式 {#spelling-checker}

![](do-not-localize/cq55_rte_spellchecker.png)

拼寫檢查器將檢查當前元件中的所有文本。

會強調顯示任何不正確的拼字：

![cq55_rte_spellchecker_use](assets/cq55_rte_spellchecker_use.png)

>[!NOTE]
>
>拼字檢查程式會以網站的語言執行，方法是取用子樹狀結構的語言屬性或從URL擷取語言。 例如 `en` 將檢查分支是否為英文， `de` 德文分行。

### 表格 {#tables}

表格可同時使用：

* 作為 **表格** 元件

   ![chlimage_1-146](assets/chlimage_1-146.png)

* 從 **文字** 元件

   ![](do-not-localize/chlimage_1-14.png)

   >[!NOTE]
   >
   >雖然表格可在RTE中使用，但建議使用 **表格** 元件。

在 **文字** 和 **表格** 元件表格功能可透過內容功能表（通常是滑鼠右鍵）按一下表格內；例如：

![cq55_rte_tablemenu](assets/cq55_rte_tablemenu.png)

>[!NOTE]
>
>在 **表格** 元件，也提供專用工具列，包括各種標準RTF編輯器函式，以及表特定函式的子集。

表的特定函式為：

<table> 
 <tbody> 
  <tr> 
   <td><a href="#table-properties">表屬性</a><br /> </td> 
  </tr> 
  <tr> 
   <td><a href="#cell-properties">儲存格屬性<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#add-or-delete-rows">新增或刪除列<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#add-or-delete-columns">添加或刪除列<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#selecting-entire-rows-or-columns">選擇整行或列<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#merge-cells">合併儲存格<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#split-cells">分割儲存格<br /> </a></td> 
  </tr> 
  <tr> 
   <td><a href="#creating-nested-tables">嵌套表</a></td> 
  </tr> 
  <tr> 
   <td><a href="#remove-table">刪除表</a> </td> 
  </tr> 
 </tbody> 
</table>

#### 表屬性 {#table-properties}

![cq55_rte_tableproperties_icon](assets/cq55_rte_tableproperties_icon.png)

按一下「 」之前，可以設定表格的基本屬性 **確定** 要保存：

![cq55_rte_tableproperties_dialog](assets/cq55_rte_tableproperties_dialog.png)

* **寬度**

   表格的總寬度。

* **高度**

   表的總高度。

* **邊框**

   表格邊框的大小。

* **儲存格邊距**

   這會定義儲存格內容與其邊界之間的空白。

* **儲存格間距**

   這會定義儲存格之間的距離。

>[!NOTE]
>
>**寬度**, **高度** 和某些儲存格屬性可定義於：
>
>* 像素
>* 百分比


>[!CAUTION]
>
>Adobe強烈建議您定義 **寬度** 為你的桌子。

#### 儲存格屬性 {#cell-properties}

![cq55_rte_cellproperties_icon](assets/cq55_rte_cellproperties_icon.png)

可設定特定儲存格或一系列儲存格的屬性：

![cq55_rte_cellproperties_dialog](assets/cq55_rte_cellproperties_dialog.png)

* **寬度**
* **高度**
* **水準對齊**  — 左、中或右
* **垂直對齊**  — 頂部、中間、底部或基線
* **儲存格類型**  — 資料或標題
* **套用到:**
   * 單一儲存格
   * 整列
   * 整欄

#### 新增或刪除列 {#add-or-delete-rows}

![cq55_rte_rows](assets/cq55_rte_rows.png)

可在目前列的上方或下方新增列。

也可刪除目前的列。

#### 添加或刪除列 {#add-or-delete-columns}

![cq55_rte_columns](assets/cq55_rte_columns.png)

欄可新增至目前欄的左側或右側。

也可以刪除當前列。

#### 選擇整行或列 {#selecting-entire-rows-or-columns}

![chlimage_1-147](assets/chlimage_1-147.png)

選擇整個當前行或列。 之後即可使用特定動作（例如合併）。

#### 合併儲存格 {#merge-cells}

![cq55_rte_cellmerge](assets/cq55_rte_cellmerge.png) ![cq55_rte_cellmerge-1](assets/cq55_rte_cellmerge-1.png)

* 如果您已選取一組儲存格，則可將這些儲存格合併為一個。
* 如果您只選取一個儲存格，則可將其與右下方的儲存格合併。

#### 分割儲存格 {#split-cells}

![cq55_rte_cellsplit](assets/cq55_rte_cellsplit.png)

選取要分割的單一儲存格：

* 水準分割儲存格會在目前欄內，產生目前儲存格右側的新儲存格。
* 垂直分割儲存格會在目前儲存格下方，但在目前列內產生新儲存格。

#### 建立嵌套表 {#creating-nested-tables}

![chlimage_1-148](assets/chlimage_1-148.png)

建立巢狀表格會在目前儲存格內建立新的獨立表格。

>[!NOTE]
>
>瀏覽器會依賴某些其他行為：
>
>* Windows IE:按住Ctrl鍵+主鍵 — 滑鼠按鈕 — 按一下（通常為左側）以選取多個儲存格。
>* Firefox:拖曳滑鼠以選取儲存格範圍。
>


#### 刪除表 {#remove-table}

![cq55_rte_removetable](assets/cq55_rte_removetable.png)

這會從 **文字** 元件。

### 特殊字元 {#special-characters}

![](do-not-localize/cq55_rte_specialchars.png)

RTF編輯器可使用特殊字元；這些值可能會因您的安裝而異。

![cq55_rte_specialchars_use](assets/cq55_rte_specialchars_use.png)

使用滑鼠查看該字元的放大版本，然後按一下以將其包含在文本中的當前位置。

### 源編輯模式 {#source-editing-mode}

![](do-not-localize/cq55_rte_sourceedit.png)

來源編輯模式可讓您查看和編輯元件的基礎HTML。

因此，文字是：

![cq55_rte_sourcemode_1](assets/cq55_rte_sourcemode_1.png)

在源模式下，會如下所示（通常源長得多，因此您必須滾動）:

![cq55_rte_sourcemode_2](assets/cq55_rte_sourcemode_2.png)

>[!CAUTION]
>
>離開來源模式時，AEM會進行特定驗證檢查（例如，確保區塊中的文字正確包含/巢狀）。 這可能會導致您的編輯變更。

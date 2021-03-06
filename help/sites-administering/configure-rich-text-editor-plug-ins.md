---
title: 設定RTF編輯器外掛程式
description: 了解如何設定Adobe Experience Manager RTF編輯器外掛程式以啟用個別功能。
contentOwner: AG
exl-id: c9ab462d-b7d4-42c1-a4cf-80d16722910b
source-git-commit: 9d1d6357c79e864e1fef89f713534dd074cf20ab
workflow-type: tm+mt
source-wordcount: '4210'
ht-degree: 0%

---


# 設定RTF編輯器外掛程式 {#configure-the-rich-text-editor-plug-ins}

可透過一系列外掛程式使用RTE功能，每個外掛程式都具有features屬性。 您可以配置功能屬性以啟用或禁用一個或多個RTE功能。 本文說明如何具體設定RTE外掛程式。

如需其他RTE設定的詳細資訊，請參閱[設定RTF編輯器](/help/sites-administering/rich-text-editor.md)。

>[!NOTE]
>
>使用CRXDE Lite時，建議使用[!UICONTROL Save All]選項定期保存更改。

## 啟動外掛程式並設定features屬性 {#activateplugin}

若要啟用外掛程式，請依照下列步驟操作。 只有在您首次設定外掛程式時，才需要執行某些步驟，因為對應的節點不存在。

預設會在RTE中啟用`format`、`link`、`list`、`justify`和`control`外掛程式及其所有功能。

>[!NOTE]
>
>各自的`rtePlugins`節點稱為`<rtePlugins-node>`，以避免本文中的重複。

1. 使用CRXDE Lite，找出專案的文字元件。
1. 在配置任何RTE插件之前，建立`<rtePlugins-node>`的父節點（如果不存在）:

   * 根據您的元件，父節點為：

      * `config: .../text/cq:editConfig/cq:inplaceEditing/config`
      * 替代配置節點：`.../text/cq:editConfig/cq:inplaceEditing/inplaceEditingTextConfig`
      * `text: .../text/dialog/items/tab1/items/text`
   * 類型：**jcr:primaryType** `cq:Widget`
   * 兩者皆具有下列屬性：

      * **名稱** `name`
      * **類型** `String`
      * **值** `./text`


1. 根據您為配置的介面，如果節點不存在，請建立節點`<rtePlugins-node>`:

   * **名稱** `rtePlugins`
   * **類型** `nt:unstructured`

1. 在下方，為每個您要啟用的外掛程式建立節點：

   * **類型** `nt:unstructured`
   * **** 命名所需外掛程式的外掛程式ID

啟動外掛程式後，請依照下列准則設定`features`屬性。

<table> 
 <tbody> 
  <tr> 
   <td><strong> </strong></td> 
   <th><strong>啟用所有功能<br /> </strong></th> 
   <th><strong>啟用一些特定功能</strong></th> 
   <th><strong>禁用所有功能<br /> </strong></th> 
  </tr> 
  <tr> 
   <td><strong>名稱</strong></td> 
   <td>功能</td> 
   <td>功能</td> 
   <td>功能</td> 
  </tr> 
  <tr> 
   <td><strong>類型</strong></td> 
   <td>字串</td> 
   <td>字串(多字串；將類型設為字串，然後按一下多CRXDE Lite)</td> 
   <td>字串</td> 
  </tr> 
  <tr> 
   <td><strong>值</strong></td> 
   <td>*（星號）<br /> </td> 
   <td>設定為一個或多個特徵值</td> 
   <td><strong>-</strong></td> 
  </tr> 
 </tbody> 
</table>

## 了解Findreplace外掛程式 {#understand-findreplace-plugin}

`findreplace`外掛程式不需要任何設定。 它是現成的。

使用取代功能時，應在輸入要取代的取代字串時與尋找字串同時輸入。 不過，在替換字串之前，您仍可以按一下「尋找」來搜尋字串。 如果在按一下「查找」後輸入替換字串，則搜索將重置為文本的開頭。

點擊查找時，查找和替換對話框變為透明，點擊替換時變為不透明。 這可讓作者檢閱作者將取代的文字。 如果用戶按一下「全部替換」(replace all)，對話框將關閉並顯示已進行替換的數量。

## 設定貼上模式 {#paste-modes}

使用RTE時，作者可以在下列三種模式之一中貼上內容：

* **瀏覽器模式**:使用瀏覽器的預設貼上實作來貼上文字。它不是推薦的方法，因為它可能引入不想要的標籤。

* **純文字模式**:將剪貼簿內容貼為純文字。在[!DNL Experience Manager]元件中插入之前，它會先從複製的內容中移除樣式和格式的所有元素。

* **MS Word模式**:從MS Word複製時，貼上帶有格式的文本（包括表格）。不支援從其他源（如網頁或MS Excel）複製和貼上文本，並且僅保留部分格式。

### 配置RTE工具欄上可用的「貼上」選項  {#configure-paste-options-toolbar}

您可以在RTE工具列中提供以下三個圖示的一部分、全部或全部不提供給作者：

* **[!UICONTROL 貼上(Ctrl+V)]**:可以預先設定，以對應上述三種「貼上」模式之一。

* **[!UICONTROL 貼上為文字]**:提供純文字檔案模式功能。

* **[!UICONTROL 從Word貼上]**:提供MS Word模式功能。

若要設定RTE以顯示必要的圖示，請遵循下列步驟。

1. 導覽至您的元件，例如`/apps/<myProject>/components/text`。
1. 導航到節點`rtePlugins/edit`。 如果節點不存在，請參閱[啟用外掛程式](#activateplugin)。
1. 在`edit`節點上建立`features`屬性，並添加一個或多個功能。 儲存所有變更。

### 配置「貼上」(Ctrl+V)表徵圖和快捷方式的行為 {#configure-paste-icon-shortcut}

您可以使用下列步驟預先設定「貼上」(Ctrl+V)]**圖示的行為。**[!UICONTROL &#x200B;此設定也定義作者用來貼上內容的鍵盤快速鍵Ctrl+V的行為。

此設定允許下列三種使用案例：

* 使用瀏覽器的預設貼上實作來貼上文字。 它不是推薦的方法，因為它可能引入不想要的標籤。 使用下方的`browser`進行配置。

* 將剪貼簿內容貼為純文字。 在AEM元件中插入之前，它會先從複製的內容中移除所有樣式和格式元素。 使用下方的`plaintext`進行配置。

* 從MS Word複製時，貼上帶有格式的文本（包括表格）。 不支援從其他源（如網頁或MS Excel）複製和貼上文本，並且僅保留部分格式。 使用下方的`wordhtml`進行配置。

1. 在元件中，導覽至`<rtePlugins-node>/edit`節點。 如果節點不存在，請建立這些節點。 如需詳細資訊，請參閱[啟用外掛程式](#activateplugin)。
1. 在`edit`節點中，使用以下詳細資訊建立屬性：

   * **名稱** `defaultPasteMode`
   * **類型** `String`
   * **** 值：必要貼上模 `browser`式之 `plaintext`一、或 `wordhtml`。

### 配置貼上內容時允許的格式 {#paste-formats}

可以進一步配置貼上方式 — Microsoft-Word(`paste-wordhtml`)模式，以便您可以明確定義從其他程式（如Microsoft Word）在AEM中貼上時允許使用哪些樣式。

例如，如果在貼入AEM時只允許使用粗體格式和清單，則可以篩選掉其他格式。 這稱為可設定的貼上篩選，可針對下列兩項執行：

* [文字](#paste-modes)
* [連結](#link-styles)

對於連結，您也可以定義自動接受的通訊協定。

要配置從其他程式將文本貼入AEM時允許的格式：

1. 在元件中，導覽至節點`<rtePlugins-node>/edit`。 如果節點不存在，請建立這些節點。 如需詳細資訊，請參閱[啟用外掛程式](#activateplugin)。
1. 在`edit`節點下建立節點以保存HTML貼上規則：

   * **名稱** `htmlPasteRules`
   * **類型** `nt:unstructured`

1. 在`htmlPasteRules`下建立節點，以保存允許的基本格式的詳細資訊：

   * **名稱** `allowBasics`
   * **類型** `nt:unstructured`

1. 要控制接受的單個格式，請在`allowBasics`節點上建立以下一個或多個屬性：

   * **名稱** `bold`
   * **名稱** `italic`
   * **名稱** `underline`
   * **名稱** `anchor` （適用於連結和命名錨點）
   * **名稱** `image`

   所有屬性均為&#x200B;**Type** `Boolean`，因此，在相應的&#x200B;**Value**&#x200B;中，可以選擇或刪除複選標籤以啟用或禁用該功能。

   >[!NOTE]
   >
   >若未明確定義，則會使用預設值true，並接受格式。

1. 也可以使用其他屬性或節點範圍來定義其他格式，這些格式也應用於`htmlPasteRules`節點。 儲存所有變更。

可以對`htmlPasteRules`使用以下屬性。

| 屬性 | 類型 | 說明 |
|---|---|---|
| `allowBlockTags` | 字串 | 定義允許的區塊標籤清單。 一些可能的區塊標籤包括： <ul> <li>標題(h1、h2、h3)</li> <li>第(p)段</li> <li>清單(ol, ul)</li> <li>表（表）</li> </ul> |
| `fallbackBlockTag` | 字串 | 定義用於任何塊的塊標籤，這些塊標籤具有未包含在`allowBlockTags`中的塊標籤。 `p` 在大多數情況下都足夠了。 |
| 表格 | nt:unstructured | 定義貼上表格時的行為。 此節點必須具有屬性`allow`（類型布林值），才能定義是否允許貼上表。 如果允許設定為`false`，則必須指定屬性`ignoreMode`（類型字串）以定義如何處理貼上的表內容。 `ignoreMode`的有效值為： <ul> <li>`remove`:刪除表內容。</li> <li>`paragraph`:將表格儲存格轉換為段落。</li> </ul> |
| 清單 | nt：非結構化 | 定義貼上清單時的行為。 必須具有屬性`allow`（類型布林值），才能定義是否允許貼上清單。 如果將`allow`設定為`false`，則必須指定屬性`ignoreMode`（類型字串）以定義如何處理貼上的任何清單內容。 `ignoreMode`的有效值為： <ul><li> `remove`:移除清單內容。</li> <li>`paragraph`:將清單項目轉換為段落。</li> </ul> |

以下是有效`htmlPasteRules`結構的示例。

```xml
"htmlPasteRules": {
    "allowBasics": {
        "italic": true,
        "link": true
    },
    "allowBlockTags": [
        "p", "h1", "h2", "h3"
    ],
    "list": {
        "allow": false,
        "ignoreMode": "paragraph"
    },
    "table": {
        "allow": true,
        "ignoreMode": "paragraph"
    }
}
```

## 配置文本樣式 {#text-styles}

作者可套用樣式以變更部分文字的外觀。 樣式以您在CSS樣式表中預先定義的CSS類別為基礎。 程式化內容會使用`class`屬性括在`span`標籤中，以參照CSS類別。 例如， `<span class=monospaced>Monospaced Text Here</span>`。

首次啟用樣式外掛程式時，沒有可用的預設樣式。 快顯清單為空。 若要為作者提供樣式，請執行下列動作：

* 啟用樣式下拉式選取器。
* 指定樣式表的位置。
* 指定可從「樣式」下拉清單中選取的個別樣式。

對於以後的配置，例如要添加更多樣式，請僅按照說明參考新樣式表並指定其他樣式。

>[!NOTE]
>
>您可以定義[表或表單元格](/help/sites-administering/configure-rich-text-editor-plug-ins.md#table-styles)的樣式。 這些設定需要個別的程式。

### 啟用樣式下拉式選取器清單 {#style-selector-list}

若要這麼做，請啟用樣式外掛程式。

1. 在元件中，導覽至節點`<rtePlugins-node>/styles`。 如果節點不存在，請建立這些節點。 如需詳細資訊，請參閱[啟用外掛程式](#activateplugin)。
1. 在`styles`節點上建立`features`屬性：

   * **名稱** `features`
   * **類型** `String`
   * **值** `*` （星號）

1. 儲存所有變更。

>[!NOTE]
>
>啟用樣式外掛程式後，樣式下拉式清單會顯示在編輯對話方塊中。 但清單為空，因為未設定樣式。

### 指定樣式表位置 {#location-stylesheet}

然後，指定要參照的樣式表的位置：

1. 導覽至文字元件的根節點，例如`/apps/<myProject>/components/text`。
1. 將屬性`externalStyleSheets`添加到`<rtePlugins-node>`的父節點：

   * **名稱** `externalStyleSheets`
   * **類型** `String[]` (多字串；按一 **** 下多重CRXDE)
   * **值** 您要包括的每個樣式表的路徑和檔案名。使用存放庫路徑。

   >[!NOTE]
   >
   >您隨後可以將參照添加到其他樣式表。

1. 儲存所有變更。

在對話框（傳統UI）中使用RTE時，可以指定為RTF編輯而優化的樣式表。 由於技術限制，CSS內容在編輯器中會遺失，因此您可以模擬此內容以改善WYSIWYG體驗。 RTF編輯器使用ID為`CQrte`的容器DOM元素，可用來提供不同樣式以供檢視和編輯：

```TXT
#CQ td {
// defines the style for viewing }

#CQrte td {
// defines the style for editing }
```

### 指定快顯清單中可用的樣式 {#styles-popup-list}

1. 在元件定義中，按照在[啟用樣式下拉式選擇器](#style-selector-list)中建立的方式導航到節點`<rtePlugins-node>/styles`。
1. 在節點`styles`下，建立新節點（也稱為`styles`）以保留要提供的清單：

   * **名稱** `styles`
   * **類型** `cq:WidgetCollection`

1. 在`styles`節點下建立新節點以表示單個樣式：

   * **名稱**，您可以指定名稱，但該名稱應適合樣式
   * **類型** `nt:unstructured`

1. 將屬性`cssName`添加到此節點以引用CSS類：

   * **名稱** `cssName`
   * **類型** `String`
   * **** 值CSS類的名稱(不帶前面的「。」;例如， `cssClass`而非`.cssClass`

1. 將屬性`text`新增至相同節點；這會定義選取方塊中顯示的文字：

   * **名稱** `text`
   * **類型** `String`
   * **** 值樣式的說明；顯示在「樣式」(Style)下拉選擇框中。

1. 儲存變更。

   對每個所需樣式重複上述步驟。

## 配置段落格式 {#para-formats}

在RTE中創作的任何文本都放置在塊標籤中，預設值為`<p>`。 啟用`paraformat`外掛程式後，可使用下拉式選取清單，指定可指派給段落的其他區塊標籤。 段落格式通過分配正確的塊標籤來確定段落類型。 作者可使用「格式」選取器來選取及指派。 範例區塊標籤除其他外包括標準段落&lt;p>和標題&lt;h1>、&lt;h2>等。

>[!CAUTION]
>
>此外掛程式不適用於結構複雜的內容，例如清單或表格。

>[!NOTE]
>
>如果無法將塊標籤（例如&lt;hr>標籤）分配給段落，則對於參數格式插件來說，它不是有效的使用案例。

首次啟用「段落格式」插件時，沒有預設的段落格式可用。 快顯清單為空。 要向作者提供段落格式，請執行以下操作：

* 啟用「格式」下拉式選取器清單。
* 指定可從下拉式清單中選取為段落格式的區塊標籤。

對於以後的（重新）配置，例如要添加更多格式，請只遵循說明的相關部分。

### 啟用「格式」下拉式選取器 {#format-selector-list}

首先啟用`paraformat`外掛程式：

1. 在元件中，導覽至節點`<rtePlugins-node>/paraformat`。 如果節點不存在，請建立這些節點。 如需詳細資訊，請參閱[啟用外掛程式](#activateplugin)。
1. 在`paraformat`節點上建立`features`屬性：

   * **名稱** `features`
   * **類型** `String`
   * **值** `*` （星號）

>[!NOTE]
如果外掛程式未進一步設定，則會啟用下列預設格式：
* 段落 ( `<p>`)
* 標題 1 ( `<h1>`)
* 標題 2 ( `<h2>`)
* 標題 3 ( `<h3>`)



>[!CAUTION]
配置RTE的段落格式時，請勿刪除段落標籤&lt;p>作為格式選項。 如果移除&lt;p>標籤，則內容作者即使設定了其他格式，也無法選取&#x200B;**段落格式**&#x200B;選項。

### 指定可用的段落格式 {#para-formats-popup}

可通過下列方式選擇段落格式：

1. 在元件定義中，按照在[啟用格式下拉選擇器](#style-selector-list)中建立的方式導航到節點`<rtePlugins-node>/paraformat`。
1. 在`paraformat`節點下建立新節點，以保存格式清單：

   * **名稱** `formats`
   * **類型** `cq:WidgetCollection`

1. 在`formats`節點下建立新節點，此節點保留單個格式的詳細資訊：

   * **名稱**，您可以指定名稱，但此名稱應適用於格式（例如myparagraph、myheading1）。
   * **類型** `nt:unstructured`

1. 向此節點新增屬性以定義所使用的區塊標籤：

   * **名稱** `tag`
   * **類型** `String`
   * **** 值格式的區塊標籤；例如：p、h1、h2等

      您不需要輸入定界角括弧。

1. 同一個節點新增另一個屬性，讓描述性文字顯示在下拉式清單中：

   * **名稱** `description`
   * **類型** `String`
   * **** 值此格式的描述性文字；例如，段落、標題1、標題2等。此文本將顯示在「格式」選擇清單中。

1. 儲存變更。

   對每個必要格式重複步驟。

>[!CAUTION]
如果您定義自訂格式，則會移除預設格式（`<p>`、`<h1>`、`<h2>`及`<h3>`）。 重新建立`<p>`格式，因為它是預設格式。

## 設定特殊字元 {#special-char}

在標準AEM安裝中，當`misctools`外掛程式針對特殊字元(`specialchars`)啟用時，預設選項立即可供使用；例如，版權符號和商標符號。

您可以設定RTE，讓您自己選取的字元可供使用；定義不同字元或整個序列。

>[!CAUTION]
新增您自己的特殊字元會覆寫預設選取項目。 如有需要，（重新）在您自己的選取項目中定義這些字元。

### 定義單一字元 {#define-single-char}

1. 在元件中，導覽至節點`<rtePlugins-node>/misctools`。 如果節點不存在，請建立這些節點。 如需詳細資訊，請參閱[啟用外掛程式](#activateplugin)。
1. 在`misctools`節點上建立`features`屬性：

   * **名稱** `features`
   * **類型** `String[]`
   * **值** `specialchars`

          （或`String / *`，若套用此外掛程式的所有功能）

1. 在`misctools`下建立節點以保存特殊字元配置：

   * **名稱** `specialCharsConfig`
   * **類型** `nt:unstructured`

1. 在`specialCharsConfig`下建立另一個節點以保存字元清單：

   * **名稱** `chars`
   * **類型** `nt:unstructured`

1. 在`chars`下添加一個新節點以保存單個字元定義：

   * **** 您可以指定名稱，但名稱應反映字元；例如，一半。
   * **類型** `nt:unstructured`

1. 向此節點添加以下屬性：

   * **名稱** `entity`
   * **類型** `String`
   * **** 評估所需字元的HTML表示；例如， `&189;` 對於1/5。

1. 儲存變更。

屬性儲存後，代表的字元會顯示在CRXDE中。 請參閱下方的一半範例。 重複上述步驟，讓作者可使用更多特殊字元。

![在CRXDE中，添加要在RTE工具欄中可用的單個字](assets/chlimage_1-412.png "元在CRXDE中，添加要在RTE工具欄中可用的單個字元")



### 定義字元範圍 {#define-range-char}

1. 使用[定義單字元](#define-single-char)中的步驟1到3。
1. 在`chars`下添加一個新節點以保存字元範圍的定義：

   * **** 您可以指定名稱，但名稱應反映字元範圍；比如鉛筆。
   * **類型** `nt:unstructured`

1. 在此節點下（根據您的特殊字元範圍命名）新增下列兩個屬性：

   * **名稱** `rangeStart`

      **類型** `Long`
      **** 值範圍 [](https://unicode.org/) 中第一個字元的Unicoderepresentation（小數）

   * **名稱** `rangeEnd`

      **類型** `Long`
      **** 值範圍 [](https://unicode.org/) 中最後一個字元的Unicoderepresentation（小數）

1. 儲存變更。

   例如，定義9998 - 10000範圍時，會提供下列字元。

   ![在CRXDE中，定義要在RTE中可用的字元範圍](assets/chlimage_1-413.png)

         *在CRXDE中，定義要在RTE*&#x200B;中提供的字元範圍

   ![RTE中可用的特殊字元會在快顯視窗中顯示給作者](assets/rtepencil.png)

         *RTE中可用的特殊字元會在快顯視窗*&#x200B;中顯示給作者

## 配置表樣式 {#table-styles}

樣式通常會套用在文字上，但也可以在表格或一些表格儲存格上套用個別的樣式集。 在「單元格屬性」或「表屬性」對話框的「樣式選擇器」框中，作者可以使用此類樣式。 在文本元件（或衍生元件）內編輯表時，這些樣式可用，在標準表元件中不可用。

>[!NOTE]
您只能為傳統UI定義表格和儲存格的樣式。

>[!NOTE]
在RTE元件中或從RTE元件複製和貼上表格取決於瀏覽器。 並非所有瀏覽器都可立即使用。 根據表格結構和瀏覽器，您可能會獲得不同的結果。 例如，當您在傳統UI和觸控式UI的Mozilla Firefox中，將表格複製並貼到RTE元件時，不會保留表格的版面。

1. 在元件內導覽至節點`<rtePlugins-node>/table`。 如果節點不存在，請建立這些節點。 如需詳細資訊，請參閱[啟用外掛程式](#activateplugin)。
1. 在`table`節點上建立`features`屬性：

   * **名稱** `features`
   * **類型** `String`
   * **值** `*` （星號）

   >[!NOTE]
   如果不想啟用所有表功能，可以建立`features`屬性，如下所示：
   * **類型** `String[]`

   * **視需要為下列項目之一或兩者設定值**:
      * `table` 允許編輯表屬性；包括樣式。
      * `cellprops` 來允許編輯儲存格屬性，包括樣式。


1. 定義CSS樣式表的位置以參照這些樣式表。 請參閱[指定樣式表的位置](#location-stylesheet)，因為這與定義文字](#text-styles)的樣式時相同。 [如果您定義其他樣式，則可定義位置。
1. 在`table`節點下，建立以下新節點（視需要）:

   * 要定義整個表的樣式（可在&#x200B;**表屬性**&#x200B;下使用）:

      * **名稱** `table-styles`
      * **類型** `cq:WidgetCollection`
   * 要定義單個單元格的樣式（可在&#x200B;**單元格屬性**&#x200B;下使用）:

      * **名稱** `cellStyles`
      * **類型** `cq:WidgetCollection`


1. 建立新節點（在`table-styles`或`cellStyles`節點下，視情況）以表示個別樣式：

   * **** 您可以指定名稱，但名稱應該反映樣式。
   * **類型** `nt:unstructured`

1. 在此節點上建立屬性：

   * 定義要參考的CSS樣式

      * **名稱** `cssName`
      * **類型** `String`
      * **** 值CSS類別的名稱(不含前 `.`文，例 `cssClass` 如，而 `.cssClass`非)
   * 若要定義要在下拉式選取器中顯示的描述性文字

      * **名稱** `text`
      * **類型** `String`
      * **** 值要在選擇清單中顯示的文本


1. 儲存所有變更。

對每個所需樣式重複上述步驟。

### 配置表中隱藏的標題以便訪問 {#hidden-header}

有時，您可能會建立資料表，而欄標題中沒有視覺文字，假設標題的用途是由欄與其他欄的視覺關係所隱含。 在此情況下，必須在標題儲存格的儲存格內提供隱藏的內部文字，讓螢幕助讀程式和其他輔助技術可協助有各種需求的讀者了解欄的目的。

為了在這類情況下增強協助工具，RTE支援隱藏的標題儲存格。 此外，它還提供與表格中隱藏標題相關的配置設定。 這些設定可讓您在編輯和預覽模式中，對隱藏的標題套用CSS樣式。 若要協助作者在編輯模式中識別隱藏的標題，請在程式碼中加入下列參數：

* `hidden-headerEditingCSS`:指定在編輯RTE時，在隱藏標題儲存格上套用的CSS類別名稱。
* `hidden-headerEditingStyle`:指定在編輯RTE時，在隱藏標題單元格上應用的樣式字串。

如果在代碼中同時指定CSS和樣式字串，則CSS類優先於樣式字串，並且可能覆蓋樣式字串所做的任何配置更改。

若要協助作者在預覽模式中對隱藏的標題套用CSS，您可以在程式碼中加入下列參數：

* `hidden-headerClassName`:指定在預覽模式中在隱藏的標題單元格上應用的CSS類的名稱。
* `hidden-headerStyle`:指定在預覽模式中在隱藏標題單元格上應用的樣式字串。

如果在代碼中同時指定CSS和樣式字串，則CSS類優先於樣式字串，並且可能覆蓋樣式字串所做的任何配置更改。

## 為拼寫檢查程式添加字典 {#add-dict}

啟動拼字檢查外掛程式時，RTE會針對每種適當語言使用字典。 然後根據網站的語言來選取這些檔案，方法是提取子樹的語言屬性或從URL中提取語言；例如， `/en/`分支被檢查為英文，`/de/`分支被檢查為德文。

>[!NOTE]
如果嘗試檢查未安裝的語言，則會看到消息`Spell checking failed`。 標準字典位於`/libs/cq/spellchecker/dictionaries`，以及相應的自述檔案。 請勿修改檔案。

標準AEM安裝包括美式英語(`en_us`)和英式英語(`en_gb`)的字典。 若要新增更多字典，請遵循下列步驟。

1. 導覽至頁面[https://extensions.openoffice.org/](https://extensions.openoffice.org/)。

1. 執行下列任一操作以查找您選擇的語言的字典：

   * 搜尋您所選擇語言的字典。 在字典頁面上，找到原始來源或作者網頁的連結。 在此頁面上找出v2.x的字典檔案。
   * 在[https://wiki.openoffice.org/wiki/User:Khirano/Dictionaries](https://wiki.openoffice.org/wiki/User:Khirano/Dictionaries)搜尋v2.x字典檔案。

1. 下載包含拼字定義的封存。 解壓縮檔案系統上的封存內容。

   >[!CAUTION]
   僅支援`MySpell`格式的OpenOffice.org v2.0.1或更早版本的字典。 由於字典現在是封存檔案，因此建議您在下載後驗證封存。

1. 找到.aff和.dic檔案。 將檔案名保持為小寫。 例如， `de_de.aff`和`de_de.dic`。
1. 在`/apps/cq/spellchecker/dictionaries`的存放庫中載入.aff和.dic檔案。

>[!NOTE]
RTE拼字檢查器可隨選使用。 當您開始輸入文字時，它不會自動執行。 要運行拼寫檢查器，請從工具欄按一下[!UICONTROL Spellchecker]。 RTE會檢查字詞拼寫，並反白標示拼錯的字詞。
如果您納入拼寫檢查程式建議的任何更改，文本更改的狀態和拼寫錯誤的單詞將不再突出顯示。 若要執行拼字檢查程式，請再次點選/按一下「拼字檢查程式」按鈕。

## 設定還原和重做動作的歷史記錄大小 {#undo-history}

RTE可讓作者還原或重做最後幾次編輯。 依預設，歷史記錄中會儲存50個編輯項目。 您可以視需要設定此值。

1. 在元件內導覽至節點`<rtePlugins-node>/undo`。 如果這些節點不存在，請建立這些節點。 如需詳細資訊，請參閱[啟用外掛程式](#activateplugin)。
1. 在`undo`節點上建立屬性：

   * **名稱** `maxUndoSteps`
   * **類型** `Long`
   * **** 值要保存在歷史記錄中的撤消步驟數。

      * 預設為50。
      * 使用0可完全禁用撤消/重做。

1. 儲存變更。

## 配置頁簽大小 {#tab-size}

在任何文本中按定位字元時，插入預定數量的空格；依預設，這是三個不中斷的空格和一個空格。 要定義頁簽大小，請執行以下操作：

1. 在元件中，導覽至節點`<rtePlugins-node>/keys`。 如果節點不存在，請建立這些節點。 如需詳細資訊，請參閱[啟用外掛程式](#activateplugin)。
1. 在`keys`節點上建立屬性：

   * **名稱** `tab-size`
   * **類型** `String`
   * **** 值要用於表格的空格字元數

1. 儲存變更。

## 設定縮進邊界 {#indent-margin}

啟用縮進時（預設值），可以定義縮進的大小：

>[!NOTE]
此縮進大小僅應用於文本的段落（塊）;它不會影響實際清單的縮排。

1. 在元件內導覽至節點`<rtePlugins-node>/lists`。 如果這些節點不存在，請建立這些節點。 如需詳細資訊，請參閱[啟用外掛程式](#activateplugin)。
1. 在`lists`節點上建立`identSize`參數：

   * **名稱**:  `identSize`
   * **類型**:  `Long`
   * **值**:縮進邊距所需的像素數

## 配置可編輯空間的高度 {#editable-space}

您可以定義元件對話方塊中顯示的可編輯空間的高度：

1. 在元件的對話框定義的`../items/text`節點上，建立新屬性：

   * **名稱** `height`
   * **類型** `Long`
   * **** 以像素為單位評估編輯畫布的高度

   >[!NOTE]
   這不會變更對話方塊視窗的高度。

1. 儲存變更。

>[!NOTE]
這僅適用於在對話方塊中使用RTE時（不適用於傳統UI中的就地編輯）。

## 設定連結的樣式和通訊協定 {#link-styles}

在AEM中新增連結時，您可以定義：

* 要使用的CSS樣式
* 自動接受協定

若要設定如何從其他程式在AEM中新增連結，請定義HTML規則。

1. 使用CRXDE Lite，找出專案的文字元件。
1. 在與`<rtePlugins-node>`相同的級別建立新節點，即在`<rtePlugins-node>`的父節點下建立節點：

   * **名稱** `htmlRules`
   * **類型** `nt:unstructured`

   >[!NOTE]
   `../items/text`節點具有以下屬性：
   * **名稱** `xtype`
   * **類型** `String`
   * **值** `richtext`

   `../items/text`節點的位置可能因對話框的結構而異；兩個範例包括：
   * `/apps/myProject>/components/text/dialog/items/text`
   * `/apps/<myProject>/components/text/dialog/items/panel/items/text`


1. 在`htmlRules`下，建立新節點。

   * **名稱** `links`
   * **類型** `nt:unstructured`

1. 在`links`節點下，根據需要定義屬性：

   * 內部連結的CSS樣式：

      * **名稱** `cssInternal`
      * **類型** `String`
      * **** 值CSS類的名稱(不含前面的「。」;例如， `cssClass`而非`.cssClass`
   * 外部連結的CSS樣式

      * **名稱** `cssExternal`
      * **類型** `String`
      * **** 值CSS類的名稱(不含前面的「。」;例如， `cssClass`而非`.cssClass`
   * 有效&#x200B;**協定**&#x200B;的陣列。 支援的協定有`http://`、`https://`、`file://`和`mailto:`。

      * **名稱** `protocols`
      * **類型** `String[]`
      * **值**&#x200B;一或多個通訊協定
   * **defaultProtocol** (字串類型 **的屬性**):若使用者未明確指定通訊協定，則使用的通訊協定。

      * **名稱** `defaultProtocol`
      * **類型** `String`
      * **值**&#x200B;一個或多個預設協定
   * 如何處理連結目標屬性的定義。 建立新節點：

      * **名稱** `targetConfig`
      * **類型** `nt:unstructured`

      在節點`targetConfig`上：定義所需屬性：

      * 指定目標模式：

         * **名稱** `mode`
         * **類型** `String`)
         * **值**(s):

            * `auto`:表示已選擇自動目標

               （由外部連結的`targetExternal`屬性指定，或內部連結的`targetInternal`指定）。

            * `manual`:不適用於此情境
            * `blank`:不適用於此情境
      * 內部連結的目標：

         * **名稱** `targetInternal`
         * **類型** `String`
         * **** 評估內部連結的目標(僅在模式為時使 `auto`用)
      * 外部連結的目標：

         * **名稱** `targetExternal`
         * **類型** `String`
         * **** 值外部連結的目標(僅在模式為時使 `auto`用)。








1. 儲存所有變更。

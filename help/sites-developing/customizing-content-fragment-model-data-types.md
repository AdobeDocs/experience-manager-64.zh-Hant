---
title: 不要發佈，但不要刪除為內容片段模型自訂資料類型
seo-title: 自訂內容片段模型的資料類型
description: 可自訂內容片段模型中使用的資料類型。
seo-description: 可自訂內容片段模型中使用的資料類型。
page-status-flag: de-activated
uuid: d8215dbf-2dbe-43cb-a5c1-dc1cb412a204
contentOwner: aheimoz
discoiquuid: a8b8155c-852c-4d16-b59b-7e19527c2bd4
noindex: true
translation-type: tm+mt
source-git-commit: 3bdff366a0d455b405c1f9de371ced98d25ae2e2
workflow-type: tm+mt
source-wordcount: '1642'
ht-degree: 1%

---


# 不要發佈，但不要刪除為內容片段模型自訂資料類型{#do-not-publish-but-do-not-delete-customizing-data-types-for-content-fragment-models}

[內容片段](/help/assets/content-fragments.md) ，是以內容 [片段模型為基礎](/help/assets/content-fragments-models.md)。 這些模型是由不同資 [料類型](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) 的元素所建立。

各種資料類型都可立即使用，包括單行文字、多行豐富式文字、數值欄位、布林選擇器、下拉式選單選項、日期和時間等。 AEM使用者可以根據對應片段的編輯意圖來選取資料類型。 這可讓您透過使用各種不同內容的複雜模型，以及相關的片段製作體驗，來迎合簡單的文字模型。

資料類型由存放在儲存庫 [中特定位置的節點](#properties)[屬性的組合定義](#locations-in-the-repository)。 您也可以建立自己的 [資料類型](#creating-your-data-type)[和fieldProperties](#creating-your-own-fieldproperties-property)。

<!-- Please uncomment when files are used>
>[!NOTE]
>
>See also [Customizing Content Fragment Models](/help/sites-developing/customizing-content-fragment-models.md).
-->

## 儲存庫中的位置 {#locations-in-the-repository}

所有現成可用的資料類型都在以下位置聲明：

`/libs/settings`

按如下所述覆蓋節點結構，可以添加新資料類型 `/apps`:

`/apps/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

>[!CAUTION]
>
>您不得變更路徑中的任 `/libs` 何項目。
>
>在下次升級或安裝服務或修正套件時，任何項目都有可能變更。

## 屬性 {#properties}

節點屬性用於定義資料類型：

* [資料類型屬性](#data-type-properties)
* 和這些欄位屬 [性](#fieldproperties)

### 資料類型屬性 {#data-type-properties}

所有資料類型都以節點結構表示，如下所示：

`/libs/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

下面的每個節 `/items` 點都具有一些屬性，這些屬性定義了模型編輯器中應如何表示該資料類型。

要使資料類型在模型編輯器中顯示，必須存在以下所有屬性：

* `fieldIcon`

   [CoralUI圖示](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableicons) ，代表模型編輯器UI中的資料類型。

* ` [fieldProperties](#fieldproperties)`

   代表每種資料類型配置屬性的陣列。

* `fieldResourceType`

   用於在內容片段中呈現資料類型的Sling資源類型。 對於能以不同方式呈現的資料類型（例如，作為簡單文本輸入和／或多行文本輸入），必須將此屬性建立為包含所有資源類型的陣列。 屬性 `renderasfield` 將自動添加，以 `fieldProperties` 便用戶選擇需要添加到模型的資源類型。

* `fieldPropResourceType`

   The Sling resource type used to render the default property for the data type.

   例如，對於資料類型：

   * 單行文字， `fieldPropResourceType` 將是元 `textfield` 件
   * 布爾值， `fieldPropResourceType` 將是元 `checkbox` 件

* `fieldViewResourceType`

   建立模型時，用來在預覽中演算資料類型的Sling資源類型。 當用戶將資料類型拖動到模型編輯器的左側時，屬 `fieldViewResourceType` 性表示在該處呈現的元件。 這適用於不想渲染完整元件，但只想渲染替代項，以最大限度地減少模型編輯器的開銷的情況。

* `fieldTitle`

   定義此資料類型標題的屬性。 例如，元 **件的單行文字** ，多欄 `textfield` 元件的 **多行文字** 。

* `valueType`

   這是資料類型在內部儲存時傳回的值類型。 請參 [閱映射](#mappings)。

* `renderType`

   這是資料類型的內部表示法。 它會將 `valueType` 連線至UI元件。 請參 [閱映射](#mappings)。

* `listOrder`

   每個資料類型都需要一個值，代表其在清單中的順序。 這可確保保存模型編輯器時各個欄位（通過拖放添加／移動）的順序正確。 此值必須是整數，建議以升序、有序的方式指派數字。 建立新資料類型時，最好根據清單中最後一個資料類型(資料類型中所顯示之最 `listOrder` 高值)指派值。

#### 映射 {#mappings}

<table> 
 <tbody> 
  <tr> 
   <td>資料類型<br /> </td> 
   <td>數值類型<br /> </td> 
   <td>呈現類型</td> 
  </tr> 
  <tr> 
   <td>單行文字</td> 
   <td>字串</td> 
   <td>單文本</td> 
  </tr> 
  <tr> 
   <td>多行文字</td> 
   <td>字串，含內容類型<br /> </td> 
   <td>文本——多重</td> 
  </tr> 
  <tr> 
   <td>數字（整數／長）<br /> </td> 
   <td>long</td> 
   <td>數字</td> 
  </tr> 
  <tr> 
   <td>數字（雙／浮點數）</td> 
   <td>雙倍</td> 
   <td>數字</td> 
  </tr> 
  <tr> 
   <td>布林值 (Boolean)</td> 
   <td>布林值</td> 
   <td>布林值</td> 
  </tr> 
  <tr> 
   <td>日期時間</td> 
   <td>日曆</td> 
   <td>次</td> 
  </tr> 
  <tr> 
   <td>列舉</td> 
   <td>字串/long</td> 
   <td>枚舉</td> 
  </tr> 
  <tr> 
   <td>標記</td> 
   <td>字串</td> 
   <td>標記</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>某些類型(例如 `string`, `long`其他類型)可能是多值的。 在此例中，用於轉換和編輯的元件通常由多欄位元件( `granite/ui/components/coral/foundation/form/multifield`)包住。 例外是標籤，編輯元件負責正確呈現標籤。

### fieldProperties {#fieldproperties}

每種資料類型的配置屬性。 值 `fieldProperties`:

* `base`

   這是所有元件的基 `fieldProperties` 礎。 定義位於下 `/libs/dam/cfm/models/editor/components/datatypeproperties/base`。

   它包含變數 `fieldRoot`，後續在 `fieldProperties` 建立輸入以擷取正確路徑時可使用此變數。

   範例： 要獲取欄位標籤的正 **確路徑** ，您需要使用鍵來標識此標籤所屬的元件，此欄位的輸入應為 `fieldRoot` + `<*fieldLabel*>`

* `checkboxfields`

   此元件會新增資料類型的 `Boolean` 預設核取方塊，以及Sling參數 `checked@Delete` 和 `checked@TypeHint`。

* `datepickerfields`

   將日期選擇器元件所需的隱藏輸入添加到函式中的元件。 包括建立屬 `defaultDateField`性、 `displayedFormat`、 `emptyText`、 `valueFormat``minDate` 和 `maxDate`。

* `datetimepickerfields`

   這會新增資料類型的選 `Date&Time` 取欄位，以區分 `Date` 和 `Date&Time` 選項。

* `datevaluefield`

   這會將日期選擇器新增至屬性，讓使用者可以選取資料類型的 `Date&Time` 預設值。

* `descriptionfield`

   此元件將添加一個多行文本欄位，該欄位表示多行編輯器中當前所選元件的說明。 模型編輯器渲染器會自動添加到每個資料類型屬性的末尾。

* `labelfield`

   新增輸入的元 `textfield` 件，可新增可具有欄位標籤之資料類型的欄位標籤。

* `maptopropertyfield`

   此元件將在屬 `Name` 性中添加欄位，為所選資料類型的元件提供標識符。 它應存在於所有資料類型中。

* `maxlengthfield`

   它用於添加屬性， `maxLength` 以便與接受此屬性的資料類型一起使用。 例如，使用 **單行文字**、 **數字**&#x200B;等。

* `multieditorfield`

   這會新增多行編輯器運作所需的所有隱藏欄位，由多行文字資 **料類型表示** 。

* `mvfields`

   新增多欄位元件運作所需所有隱藏欄位的元件。 例如，對於「單行文本」資料類 **型的第二個選項** 。 應針對任何呈現為多欄位的元件新增此項。

* `numbertypefield`

   為「數字 **」資料類型選擇選項，該資料類型在「整數** 」或「數字分 **數」資料********** 類型之間選擇。

* `numbervaluefield`

   Number `numberfield` This adds the **Default value selector for the** Enumeration `type.options`**** data type, this is used to determine the values for the select box component.

* `placeholderfield`

   這是一個文本欄位，用作元件屬 `emptyText` 性的輸入。 所有接受預留位置的資料類型(這並不複雜； 例如，單 **行文字**、 **編號**&#x200B;等)。

* `renderasfield`

   當資料類型節點的屬性中存在 `fieldResourceTypes` 多個元件時，會自動呈現此元件。

* `requiredfield`

   此複選框表示組 `required` 件的屬性。 由於大部分元件都接 `required` 受欄位，因此此欄位可用於大部分的資料類型。

* `tagsfields`

   新增要呈現元件所需輸入 `tagfield` 的元件，由「標籤」資 **料類型使用** 。

* `tagsroot`

   「標籤」資料類型用 **於設定元件根路徑的路徑選**`tagsfield` 擇器。

* `textfield`

   資料類型 `Boolean` 用於設定由此資料類型定義的複選框的欄位標籤。

* `textvaluefield`

   「單行文本」資料類 **型的預設值** 屬性。

## 建立您的資料類型 {#creating-your-data-type}

若要建立您自己的資料類型，您必須：

* [建立節點結構](#creating-the-node-structure)
* [定義您的資料類型的屬性](#defining-the-properties-for-your-data-type)

然後，您就 [可以使用您的資料類型](#using-your-data-type)。

您也可以 [自行建立 `fieldProperties`](#creating-your-own-fieldproperties-property)。

### 建立節點結構 {#creating-the-node-structure}

必須在下建立節點結 `/apps` 構，才能覆蓋資料類型。 如果它不存在，您必須建立：

1. 如果它不存在，您必須建立：

   ```
   + apps 
     + settings
       + dam 
         + cfm (cq:Page) 
           + models (nt:folder)
             + formbuilderconfig (sling:folder)
               + datatypes (nt:unstructured)
                 + items (nt:unstructured)
   ```

   >[!NOTE]
   >
   >`/apps/settings/dam` 應已存在。
   >
   >`/cfm/models/formbuilderconfig/datatypes/items` 可能需要使用指定的節點類型建立。

1. 在下 `/items` 面，您可以添加新節點來表示新的資料類型：

   * 節點類型： `nt:unstructured`
   * &quot;屬性： 請參 [閱定義資料類型的屬性](#defining-the-properties-for-your-data-type)

### 定義資料類型的屬性 {#defining-the-properties-for-your-data-type}

1. 確定以下資料 [類型屬性](#data-type-properties) （資料類型需要）的值：

   * `fieldResourceType`
   * `fieldPropResourceType`
   * `fieldViewResourceType`

   這些定義了如何呈現您的資料類型的元件。 它們可以是任何元件； 包括您自己的自訂元件(需要一組相符的 ` [fieldProperties](#fieldproperties)`元件)。

   在您的資料類型節點上，以適當的值定義這些屬性。

1. 確定要 ` [fieldProperties](#fieldproperties)` 使用的。 這取決於您所需的屬性或 `fieldResourceType` 屬性。

   例如，應 `granite/ui/components/coral/foundation/form/textfield`該有 **Label Name**、Maximum Length **、** Placeholder Text ******** 和Default Value Property。

   您可以從現成可用的欄位Properties中 [選擇](#fieldproperties)，或 [建立屬性](#creating-your-own-fieldproperties-property)。

   在您的資料類型節點上，以適當的值定義這些屬性。

1. 確定以下資料類 [型屬性的值](#data-type-properties):

   * `fieldIcon`
   * `fieldTitle`
   * `renderType`
   * `valueType`
   * `listOrder`

   在您的資料類型節點上，以適當的值定義這些屬性。

### 使用您的資料類型 {#using-your-data-type}

保存此節點結構後，在應用了所有屬性的情況下，可以使用模型編輯器開啟任何模型，查看並使用新資料類型。

## 建立自己的欄位屬性屬性 {#creating-your-own-fieldproperties-property}

您可以從現成可用的欄位Properties中 [選擇](#fieldproperties)，或建立您自己的欄位：

1. 在下面建立元件：

   `/apps/dam/cfm/models/editor/components/datatypeproperties/`

   如果路徑不存在，則可以使用節點建立 `nt:folder` 路徑。

   1. 若要存取變數，此元件應延伸：

      `/libs/dam/cfm/models/editor/components/datatypeproperties/base`* *

   1. 該元件應能夠通過以下方式包括：

      `sling:include`

   1. 此元件應轉譯欄位（如果使用者需要引入資料）或隱藏輸入，並包含您的資料類型所需的屬性。 例如，多欄位元件需要子節點，其應複製的欄位類型，因此應有可建立（透過sling POST mechanics）特定類型子節點的輸入。

1. 應將此元件的基本名稱添加到 `fieldProperties`。
1. 請重複執行您所需的所有屬性。


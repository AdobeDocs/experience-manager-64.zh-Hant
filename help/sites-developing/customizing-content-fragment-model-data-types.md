---
title: 不發佈，但不DELETE為內容片段模型自訂資料類型
seo-title: Customizing Data Types for Content Fragment Models
description: 可用於內容片段模型的資料類型可自訂。
seo-description: Data types used in Content Fragment Models can be customized.
page-status-flag: de-activated
uuid: d8215dbf-2dbe-43cb-a5c1-dc1cb412a204
contentOwner: AEM Docs
discoiquuid: a8b8155c-852c-4d16-b59b-7e19527c2bd4
noindex: true
source-git-commit: 3358f6b8b492ff2b5858867a1f48a57b06944b1e
workflow-type: tm+mt
source-wordcount: '1625'
ht-degree: 1%

---


# 不發佈，但不DELETE為內容片段模型自訂資料類型{#do-not-publish-but-do-not-delete-customizing-data-types-for-content-fragment-models}

[內容片段](/help/assets/content-fragments.md) 根據 [內容片段模型](/help/assets/content-fragments-models.md). 這些模型是由 [元素](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment) 不同資料類型。

各種資料類型都可立即使用，包括單行文字、多行RTF、數值欄位、布林選取器、下拉式功能表選項、日期和時間等。 AEM使用者可以根據對應片段的編輯目的來選取資料類型。 這可讓您透過各種不同內容的複雜模型及相關的片段製作體驗，來迎合簡單的文字模型。

資料類型由 [節點屬性組合](#properties) 持有 [儲存庫中的特定位置](#locations-in-the-repository). 您也可以建立自己的 [資料類型](#creating-your-data-type) 和 [fieldProperties](#creating-your-own-fieldproperties-property).

<!-- Please uncomment when files are used>
>[!NOTE]
>
>See also [Customizing Content Fragment Models](/help/sites-developing/customizing-content-fragment-models.md).
-->

## 儲存庫中的位置 {#locations-in-the-repository}

所有現成的資料類型都會在下方宣告：

`/libs/settings`

您可以覆蓋節點結構，以新增新資料類型，如下所示 `/apps`:

`/apps/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

>[!CAUTION]
>
>您不得變更 `/libs` 路徑。
>
>在下次升級或安裝服務或修復包時，任何內容都可能發生更改。

## 屬性 {#properties}

節點屬性用於定義資料類型：

* [資料類型屬性](#data-type-properties)
* 和 [fieldProperties](#fieldproperties)

### 資料類型屬性 {#data-type-properties}

所有資料類型都以節點結構表示，如下所示：

`/libs/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

底下的每個節點 `/items` 具有可定義模型編輯器中應如何表示該資料類型的屬性。

資料類型必須存在以下所有屬性，才能在模型編輯器中存在：

* `fieldIcon`

   [CoralUI圖示](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableicons) 表示模型編輯器UI中的資料類型。

* ` [fieldProperties](#fieldproperties)`

   代表每種資料類型之設定屬性的陣列。

* `fieldResourceType`

   用於在內容片段中轉譯資料類型的Sling資源類型。 對於能以不同方式呈現的資料類型（例如，作為簡單文本輸入和/或多行文本輸入），必須將此屬性建立為包含所有資源類型的陣列。 此 `renderasfield` 屬性會自動新增至 `fieldProperties` 若要讓使用者選擇需要新增至模型的資源類型，

* `fieldPropResourceType`

   用於轉譯資料類型預設屬性的Sling資源類型。

   例如，對於資料類型：

   * 單行文字， `fieldPropResourceType` 會是 `textfield` 元件
   * 布林值， `fieldPropResourceType` 會是 `checkbox` 元件

* `fieldViewResourceType`

   建構模型時，用於在預覽中轉譯資料類型的Sling資源類型。 當使用者將資料類型拖曳至模型編輯器的左側時， `fieldViewResourceType` 屬性代表呈現於該處的元件。 當您不想呈現完整元件，但只想呈現替代項，以最大限度地減少模型編輯器的開銷時，將用於這種情況。

* `fieldTitle`

   定義此資料類型標題的屬性。 例如， **單行文字** a `textfield` 元件， **多行文本** ，適用於多欄位元件。

* `valueType`

   這是資料類型在內部儲存時傳回的值類型。 請參閱 [對應](#mappings).

* `renderType`

   這是資料類型的內部表示法。 它連接 `valueType` 至UI元件。 請參閱 [對應](#mappings).

* `listOrder`

   每個資料類型都需要一個值來代表其在清單中的順序。 這可用來確保儲存模型編輯器時各欄位（透過拖放新增/移動）的正確順序。 此值必須是整數，建議以遞增順序方式指派數字。 建立新資料類型時，最好根據清單中的最後一個資料類型( `listOrder` 值（存在於資料類型中）。

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
   <td>單文</td> 
  </tr> 
  <tr> 
   <td>多行文字</td> 
   <td>字串，含內容類型<br /> </td> 
   <td>文本 — 多</td> 
  </tr> 
  <tr> 
   <td>數字（整數/長）<br /> </td> 
   <td>long</td> 
   <td>數字</td> 
  </tr> 
  <tr> 
   <td>數字（雙倍/浮點數）</td> 
   <td>兩次</td> 
   <td>數字</td> 
  </tr> 
  <tr> 
   <td>布林值</td> 
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
   <td>分項清單</td> 
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
>某些類型(例如 `string`, `long`（其中包括）可能是多值的。 在此情況下，用於轉譯和編輯的元件通常會由多欄位元件包住( `granite/ui/components/coral/foundation/form/multifield`)。 標籤是例外，編輯元件需負責正確轉譯。

### fieldProperties {#fieldproperties}

每種資料類型的配置屬性。 的值 `fieldProperties`:

* `base`

   這是所有人的基礎 `fieldProperties` 元件。 定義位於 `/libs/dam/cfm/models/editor/components/datatypeproperties/base`.

   其中包含變數 `fieldRoot`，後續 `fieldProperties` 可在建立輸入時使用，以擷取正確的路徑。

   範例：為 **欄位標籤** 您需要鍵以識別此屬於的元件，此欄位的輸入應為 `fieldRoot` + `<*fieldLabel*>`

* `checkboxfields`

   此元件會新增 `Boolean` 資料類型，以及Sling參數 `checked@Delete` 和 `checked@TypeHint`.

* `datepickerfields`

   新增日期選擇器元件運作所需隱藏輸入的元件。 包括建立屬性 `defaultDateField`, `displayedFormat`, `emptyText`, `valueFormat`, `minDate` 和 `maxDate`.

* `datetimepickerfields`

   這會新增的選取欄位 `Date&Time` 要區分的資料類型 `Date` 和 `Date&Time` 選項。

* `datevaluefield`

   這會將日期選擇器新增至屬性，讓使用者可以為 `Date&Time` 資料類型。

* `descriptionfield`

   此元件將添加一個多行文本欄位，該欄位表示多行編輯器中當前所選元件的說明。 模型編輯器會在每個資料類型屬性的結尾自動添加它。

* `labelfield`

   新增 `textfield` 為可以具有欄位標籤的資料類型添加欄位標籤的輸入。

* `maptopropertyfield`

   此元件會新增 `Name` 欄位，為資料類型的所選元件指定標識符。 所有資料類型中都應包含此變數。

* `maxlengthfield`

   用於新增 `maxLength` 屬性，以與接受此屬性的資料類型搭配使用。 例如，使用 **單行文字**, **數字**、等

* `multieditorfield`

   這會新增多行編輯器運作所需的所有隱藏欄位，由 **多行文本** 資料類型。

* `mvfields`

   新增多欄位元件運作所需所有隱藏欄位的元件。 例如，對於 **單行文字** 資料類型。 應針對以多欄位呈現的任何元件新增此項目。

* `numbertypefield`

   選取 **數字** 資料類型 **整數** 或 **分數** 針對 **數字** 資料類型。

* `numbervaluefield`

   A `numberfield` 預設值選取器 **數字** `type.options` 這會新增 **枚舉** 資料類型，用於確定選取方塊元件的值。

* `placeholderfield`

   這是用作 `emptyText` 元件的屬性。 所有接受預留位置的資料類型都應使用此方法(這並不十分複雜；例如 **單行文字**, **數字**&#x200B;等)。

* `renderasfield`

   這是在數個 `fieldResourceTypes` 在資料類型節點的屬性中。

* `requiredfield`

   此核取方塊代表 `required` 元件的屬性。 因為大部分元件都接受 `required` 欄位，此欄位可用於大部分資料類型。

* `tagsfields`

   新增 `tagfield` 要呈現的元件，由 **標籤** 資料類型。

* `tagsroot`

   使用的路徑選擇器 **標籤** 設定根路徑的資料類型 `tagsfield` 元件。

* `textfield`

   由 `Boolean` 資料類型，用於設定由此資料類型定義的複選框的欄位標籤。

* `textvaluefield`

   的預設值屬性 **單行文字** 資料類型。

## 建立資料類型 {#creating-your-data-type}

若要建立您自己的資料類型，您必須：

* [建立節點結構](#creating-the-node-structure)
* [定義資料類型的屬性](#defining-the-properties-for-your-data-type)

然後 [使用您的資料類型](#using-your-data-type).

您也可以 [建立自己的 `fieldProperties`](#creating-your-own-fieldproperties-property).

### 建立節點結構 {#creating-the-node-structure}

必須在下建立節點結構 `/apps` 來覆蓋資料類型。 如果它不存在，您必須建立：

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
   >`/cfm/models/formbuilderconfig/datatypes/items` 可能需要使用指定的nodetype來建立。

1. 在 `/items` 您可以新增節點來代表您的新資料類型：

   * 節點類型： `nt:unstructured`
   * &quot;屬性：請參閱 [定義資料類型的屬性](#defining-the-properties-for-your-data-type)

### 定義資料類型的屬性 {#defining-the-properties-for-your-data-type}

1. 決定下列值 [資料類型屬性](#data-type-properties) 資料類型所需的項目：

   * `fieldResourceType`
   * `fieldPropResourceType`
   * `fieldViewResourceType`

   這些定義將如何呈現資料類型的元件。 它們可以是任何元件；包括您自己的自訂元件(需要 ` [fieldProperties](#fieldproperties)`)。

   在資料類型的節點上，以適當的值定義這些屬性。

1. 決定 ` [fieldProperties](#fieldproperties)` 來使用。 這取決於您的 `fieldResourceType` 需要。

   例如， `granite/ui/components/coral/foundation/form/textfield`應該有 **標籤名稱**, **最大長度**, **佔位符文本** 和 **預設值** 屬性。

   您可以從現成可用的 [fieldProperties](#fieldproperties)，或 [建立您自己的屬性](#creating-your-own-fieldproperties-property).

   在資料類型的節點上，以適當的值定義這些屬性。

1. 決定下列值 [資料類型屬性](#data-type-properties):

   * `fieldIcon`
   * `fieldTitle`
   * `renderType`
   * `valueType`
   * `listOrder`

   在資料類型的節點上，以適當的值定義這些屬性。

### 使用您的資料類型 {#using-your-data-type}

保存此節點結構後，在應用了所有屬性的情況下，可以使用模型編輯器開啟任何模型，並查看和使用新的資料類型。

## 建立自己的欄位屬性屬性 {#creating-your-own-fieldproperties-property}

您可以從現成可用的 [fieldProperties](#fieldproperties)，或建立自己的：

1. 在下方建立元件：

   `/apps/dam/cfm/models/editor/components/datatypeproperties/`

   如果路徑不存在，則可使用 `nt:folder` 節點。

   1. 若要存取變數，此元件應延伸：

      `/libs/dam/cfm/models/editor/components/datatypeproperties/base`*

   1. 元件應可透過下列方式納入：

      `sling:include`

   1. 此元件應呈現欄位（如果使用者需要導入資料）或隱藏輸入，內含您資料類型所需的屬性。 例如，多欄位元件需要子節點，且其應複製的欄位類型，因此應有可建立(透過SlingPOST機制)特定類型子節點的輸入。

1. 此元件的基本名稱應新增至 `fieldProperties`.
1. 對您需要的所有屬性重複執行。


---
title: 不要發佈，但不要刪除為內容片段模型自訂資料類型
seo-title: 自訂內容片段模型的資料類型
description: 您可自訂內容片段模型中使用的資料類型。
seo-description: 您可自訂內容片段模型中使用的資料類型。
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


# 不要發佈，但不要刪除為內容片段模型自定義資料類型{#do-not-publish-but-do-not-delete-customizing-data-types-for-content-fragment-models}

[內容](/help/assets/content-fragments.md) 片段是以內容 [片段模型為基礎](/help/assets/content-fragments-models.md)。這些模型是由不同資料類型的[elements](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment)建立的。

各種資料類型都可立即使用，包括單行文字、多行豐富式文字、數值欄位、布林選擇器、下拉式選單選項、日期和時間等。 AEM使用者可以根據對應片段的編輯意圖來選取資料類型。 這可讓您透過使用各種不同內容的複雜模型，以及相關的片段製作體驗，來迎合簡單的文字模型。

資料類型由保存在儲存庫中的[特定位置的[節點屬性](#properties)組合定義。 ](#locations-in-the-repository)您也可以建立自己的[資料類型](#creating-your-data-type)和[fieldProperties](#creating-your-own-fieldproperties-property)。

<!-- Please uncomment when files are used>
>[!NOTE]
>
>See also [Customizing Content Fragment Models](/help/sites-developing/customizing-content-fragment-models.md).
-->

## 儲存庫中的位置{#locations-in-the-repository}

所有現成可用的資料類型都在以下位置聲明：

`/libs/settings`

可以按如下方式在`/apps`下覆蓋節點結構，以添加新資料類型：

`/apps/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

>[!CAUTION]
>
>您不得變更`/libs`路徑中的任何項目。
>
>在下次升級或安裝服務或修正套件時，任何項目都有可能變更。

## 屬性 {#properties}

節點屬性用於定義資料類型：

* [資料類型屬性](#data-type-properties)
* 和在[fieldProperties](#fieldproperties)中

### 資料類型屬性{#data-type-properties}

所有資料類型都以節點結構表示，如下所示：

`/libs/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

`/items`下的每個節點都具有一些屬性，這些屬性定義了模型編輯器中應如何表示該資料類型。

要使資料類型在模型編輯器中顯示，必須存在以下所有屬性：

* `fieldIcon`

   [CoralUI](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableicons) 圖示代表模型編輯器UI中的資料類型。

* ` [fieldProperties](#fieldproperties)`

   代表每種資料類型配置屬性的陣列。

* `fieldResourceType`

   用於在內容片段中呈現資料類型的Sling資源類型。 對於能以不同方式呈現的資料類型（例如，作為簡單文本輸入和／或多行文本輸入），必須將此屬性建立為包含所有資源類型的陣列。 `renderasfield`屬性會自動新增至`fieldProperties`，讓使用者選擇需要新增至模型的資源類型，

* `fieldPropResourceType`

   The Sling resource type used to render the default property for the data type.

   例如，對於資料類型：

   * 單行文本， `fieldPropResourceType`將是`textfield`元件
   * 布林值， `fieldPropResourceType`會是`checkbox`元件

* `fieldViewResourceType`

   建立模型時，用來在預覽中演算資料類型的Sling資源類型。 當用戶將資料類型拖動到模型編輯器的左側時，`fieldViewResourceType`屬性表示在該處呈現的元件。 這適用於不想渲染完整元件，但只想渲染替代項，以最大限度地減少模型編輯器的開銷的情況。

* `fieldTitle`

   定義此資料類型標題的屬性。 例如，**`textfield`元件的單行文字**，多欄元件的多行文字&#x200B;**。**

* `valueType`

   這是資料類型在內部儲存時傳回的值類型。 請參閱[映射](#mappings)。

* `renderType`

   這是資料類型的內部表示法。 它將`valueType`連接到UI元件。 請參閱[映射](#mappings)。

* `listOrder`

   每個資料類型都需要一個值，代表其在清單中的順序。 這可確保保存模型編輯器時各個欄位（通過拖放添加／移動）的順序正確。 此值必須是整數，建議以升序、有序的方式指派數字。 建立新資料類型時，最好根據清單中最後一個資料類型指派值（資料類型中存在的`listOrder`值的最高值）。

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
   <td>字串，內容類型為<br /> </td> 
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
>某些類型（例如`string`、`long`等）可能是多值的。 在這種情況下，用於渲染和編輯的元件通常由多欄位元件(`granite/ui/components/coral/foundation/form/multifield`)包住。 例外是標籤，編輯元件負責正確呈現標籤。

### fieldProperties {#fieldproperties}

每種資料類型的配置屬性。 `fieldProperties`的值：

* `base`

   這是所有`fieldProperties`元件的基礎。 定義位於`/libs/dam/cfm/models/editor/components/datatypeproperties/base`下。

   它包含`fieldRoot`變數，後續`fieldProperties`在建立輸入以擷取正確路徑時可使用此變數。

   範例：要獲取&#x200B;**欄位標籤**&#x200B;的正確路徑，您需要使用鍵來標識此標籤所屬的元件，此欄位的輸入應為`fieldRoot` + `<*fieldLabel*>`

* `checkboxfields`

   此元件會新增`Boolean`資料類型的預設核取方塊，以及Sling參數`checked@Delete`和`checked@TypeHint`。

* `datepickerfields`

   將日期選擇器元件所需的隱藏輸入添加到函式中的元件。 包括建立屬性`defaultDateField`、`displayedFormat`、`emptyText`、`valueFormat`、`minDate`和`maxDate`。

* `datetimepickerfields`

   這會新增`Date&Time`資料類型的選取欄位，以區分`Date`和`Date&Time`選項。

* `datevaluefield`

   這會將日期選擇器新增至屬性，讓使用者可以為`Date&Time`資料類型選取預設值。

* `descriptionfield`

   此元件將添加一個多行文本欄位，該欄位表示多行編輯器中當前所選元件的說明。 模型編輯器渲染器會自動添加到每個資料類型屬性的末尾。

* `labelfield`

   添加`textfield`輸入的元件，該元件為可具有欄位標籤的資料類型添加欄位標籤。

* `maptopropertyfield`

   此元件將在屬性中添加`Name`欄位，為所選資料類型的元件提供標識符。 它應存在於所有資料類型中。

* `maxlengthfield`

   它用於添加`maxLength`屬性，以便用於接受此屬性的資料類型。 例如，使用&#x200B;**單行文字**、**數字**&#x200B;等。

* `multieditorfield`

   這會新增多行編輯器運作所需的所有隱藏欄位，由&#x200B;**多行文字**&#x200B;資料類型表示。

* `mvfields`

   新增多欄位元件運作所需所有隱藏欄位的元件。 例如，對於&#x200B;**單行文本**&#x200B;資料類型的第二個選項。 應針對任何呈現為多欄位的元件新增此項。

* `numbertypefield`

   選擇&#x200B;**Number**&#x200B;資料類型的選項，該資料類型選擇&#x200B;**Integer**&#x200B;或&#x200B;**Fraction****Number**&#x200B;資料類型。

* `numbervaluefield`

   **Number** `type.options`的`numberfield`預設值選擇器。這將添加&#x200B;**Enumeration**&#x200B;資料類型的選項輸入，該資料類型用於確定選擇框元件的值。

* `placeholderfield`

   這是一個文本欄位，用作元件`emptyText`屬性的輸入。 所有接受預留位置的資料類型(這並不複雜；例如，**單行文字**、**數字**&#x200B;等)。

* `renderasfield`

   當資料類型節點的屬性中存在多個`fieldResourceTypes`時，會自動呈現此元件。

* `requiredfield`

   此複選框表示元件的`required`屬性。 由於大多數元件都接受`required`欄位，因此此欄位可用於大多數資料類型。

* `tagsfields`

   添加要呈現`tagfield`元件所需輸入的元件，由&#x200B;**Tags**&#x200B;資料類型使用。

* `tagsroot`

   **Tags**&#x200B;資料類型用來設定`tagsfield`元件根路徑的路徑選擇器。

* `textfield`

   `Boolean`資料類型用於設定由此資料類型定義的複選框的欄位標籤。

* `textvaluefield`

   **單行文本**&#x200B;資料類型的預設值屬性。

## 建立資料類型{#creating-your-data-type}

若要建立您自己的資料類型，您必須：

* [建立節點結構](#creating-the-node-structure)
* [定義您的資料類型的屬性](#defining-the-properties-for-your-data-type)

然後，您可以[使用您的資料類型](#using-your-data-type)。

您也可以建立自己的`fieldProperties`](#creating-your-own-fieldproperties-property)。[

### 建立節點結構{#creating-the-node-structure}

必須在`/apps`下建立節點結構，才能覆蓋資料類型。 如果它不存在，您必須建立：

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

1. 在`/items`下，您可以添加新節點來表示新的資料類型：

   * 節點類型：`nt:unstructured`
   * &quot;屬性：請參閱[定義您的資料類型的屬性](#defining-the-properties-for-your-data-type)

### 定義資料類型{#defining-the-properties-for-your-data-type}的屬性

1. 確定以下[資料類型屬性](#data-type-properties)的值，這些屬性是資料類型所需的：

   * `fieldResourceType`
   * `fieldPropResourceType`
   * `fieldViewResourceType`

   這些定義了如何呈現您的資料類型的元件。 它們可以是任何元件；包括您自己的自訂元件（需要一組相符的` [fieldProperties](#fieldproperties)`）。

   在您的資料類型節點上，以適當的值定義這些屬性。

1. 確定要使用的` [fieldProperties](#fieldproperties)`。 這取決於`fieldResourceType`需要的屬性或屬性。

   例如，`granite/ui/components/coral/foundation/form/textfield`應具有&#x200B;**標籤名稱**、**最大長度**、**預留位置文字**&#x200B;和&#x200B;**預設值**&#x200B;屬性。

   您可以從現成可用的[fieldProperties](#fieldproperties)或[建立您自己的屬性](#creating-your-own-fieldproperties-property)中選擇。

   在您的資料類型節點上，以適當的值定義這些屬性。

1. 確定以下[資料類型屬性](#data-type-properties)的值：

   * `fieldIcon`
   * `fieldTitle`
   * `renderType`
   * `valueType`
   * `listOrder`

   在您的資料類型節點上，以適當的值定義這些屬性。

### 使用您的資料類型{#using-your-data-type}

保存此節點結構後，在應用了所有屬性的情況下，可以使用模型編輯器開啟任何模型，查看並使用新資料類型。

## 建立自己的欄位屬性屬性{#creating-your-own-fieldproperties-property}

您可以從現成可用的[fieldProperties](#fieldproperties)中選擇，或建立您自己的：

1. 在下面建立元件：

   `/apps/dam/cfm/models/editor/components/datatypeproperties/`

   如果路徑不存在，則可使用`nt:folder`節點建立路徑。

   1. 若要存取變數，此元件應延伸：

      `/libs/dam/cfm/models/editor/components/datatypeproperties/base`* *

   1. 該元件應能夠通過以下方式包括：

      `sling:include`

   1. 此元件應轉譯欄位（如果使用者需要引入資料）或隱藏輸入，並包含您的資料類型所需的屬性。 例如，多欄位元件需要子節點，其應複製的欄位類型，因此應有可建立（透過sling POST mechanics）特定類型子節點的輸入。

1. 此元件的基本名稱應添加到`fieldProperties`。
1. 請重複執行您所需的所有屬性。


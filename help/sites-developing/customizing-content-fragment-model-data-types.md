---
title: 不發佈，但不DELETE為內容片段模型自訂資料類型
seo-title: 自訂內容片段模型的資料類型
description: 可用於內容片段模型的資料類型可自訂。
seo-description: 可用於內容片段模型的資料類型可自訂。
page-status-flag: de-activated
uuid: d8215dbf-2dbe-43cb-a5c1-dc1cb412a204
contentOwner: aheimoz
discoiquuid: a8b8155c-852c-4d16-b59b-7e19527c2bd4
noindex: true
source-git-commit: 3bdff366a0d455b405c1f9de371ced98d25ae2e2
workflow-type: tm+mt
source-wordcount: '1642'
ht-degree: 1%

---


# 請勿發佈，但不DELETE自訂內容片段模型的資料類型{#do-not-publish-but-do-not-delete-customizing-data-types-for-content-fragment-models}

[內](/help/assets/content-fragments.md) 容片段是以內容 [片段模型為基礎](/help/assets/content-fragments-models.md)。這些模型是從不同資料類型的[元素](/help/assets/content-fragments.md#constituent-parts-of-a-content-fragment)建立。

各種資料類型都可立即使用，包括單行文字、多行RTF、數值欄位、布林選取器、下拉式功能表選項、日期和時間等。 AEM使用者可以根據對應片段的編輯目的來選取資料類型。 這可讓您透過各種不同內容的複雜模型及相關的片段製作體驗，來迎合簡單的文字模型。

資料類型由存放在[存放庫](#locations-in-the-repository)中特定位置的[節點屬性](#properties)組合來定義。 您也可以建立自己的[資料類型](#creating-your-data-type)和[fieldProperties](#creating-your-own-fieldproperties-property)。

<!-- Please uncomment when files are used>
>[!NOTE]
>
>See also [Customizing Content Fragment Models](/help/sites-developing/customizing-content-fragment-models.md).
-->

## 儲存庫{#locations-in-the-repository}中的位置

所有現成的資料類型都會在下方宣告：

`/libs/settings`

您可以按如下所示在`/apps`下覆蓋節點結構，以添加新資料類型：

`/apps/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

>[!CAUTION]
>
>您不得變更`/libs`路徑中的任何項目。
>
>在下次升級或安裝服務或修復包時，任何內容都可能發生更改。

## 屬性 {#properties}

節點屬性用於定義資料類型：

* [資料類型屬性](#data-type-properties)
* 和在這些[fieldProperties](#fieldproperties)內

### 資料類型屬性{#data-type-properties}

所有資料類型都以節點結構表示，如下所示：

`/libs/settings/dam/cfm/models/formbuilderconfig/datatypes/items`

`/items`下的每個節點都具有定義模型編輯器中應如何表示該資料類型的屬性。

資料類型必須存在以下所有屬性，才能在模型編輯器中存在：

* `fieldIcon`

   [CoralUI圖示](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableicons) 代表模型編輯器UI中的資料類型。

* ` [fieldProperties](#fieldproperties)`

   代表每種資料類型之設定屬性的陣列。

* `fieldResourceType`

   用於在內容片段中轉譯資料類型的Sling資源類型。 對於能以不同方式呈現的資料類型（例如，作為簡單文本輸入和/或多行文本輸入），必須將此屬性建立為包含所有資源類型的陣列。 將自動將`renderasfield`屬性添加到`fieldProperties`中，以便用戶選擇需要添加到模型的資源類型，

* `fieldPropResourceType`

   用於轉譯資料類型預設屬性的Sling資源類型。

   例如，對於資料類型：

   * 單行文本，`fieldPropResourceType`將是`textfield`元件
   * 布林值， `fieldPropResourceType`會是`checkbox`元件

* `fieldViewResourceType`

   建構模型時，用於在預覽中轉譯資料類型的Sling資源類型。 當用戶將資料類型拖到模型編輯器的左側時，`fieldViewResourceType`屬性表示在該處呈現的元件。 當您不想呈現完整元件，但只想呈現替代項，以最大限度地減少模型編輯器的開銷時，將用於這種情況。

* `fieldTitle`

   定義此資料類型標題的屬性。 例如，`textfield`元件的&#x200B;**單行文本**，多欄位元件的&#x200B;**多行文本**。

* `valueType`

   這是資料類型在內部儲存時傳回的值類型。 請參閱[Mappings](#mappings)。

* `renderType`

   這是資料類型的內部表示法。 它會將`valueType`連接至UI元件。 請參閱[Mappings](#mappings)。

* `listOrder`

   每個資料類型都需要一個值來代表其在清單中的順序。 這可用來確保儲存模型編輯器時各欄位（透過拖放新增/移動）的正確順序。 此值必須是整數，建議以遞增順序方式指派數字。 建立新資料類型時，最好根據清單中的最後一個資料類型指派值（資料類型中存在的`listOrder`值的最高值）。

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
   <td>字串，內容類型為<br /> </td> 
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
>某些類型（例如`string`、`long`等）可能是多值的。 在此情況下，用於呈現和編輯的元件通常由多欄位元件(`granite/ui/components/coral/foundation/form/multifield`)包住。 標籤是例外，編輯元件需負責正確轉譯。

### fieldProperties {#fieldproperties}

每種資料類型的配置屬性。 `fieldProperties`的值：

* `base`

   這是所有`fieldProperties`元件的基礎。 定義位於`/libs/dam/cfm/models/editor/components/datatypeproperties/base`下。

   它包含變數`fieldRoot`，後續的`fieldProperties`在建立輸入以檢索正確路徑時可以使用該變數。

   範例：要獲取&#x200B;**欄位標籤**&#x200B;的正確路徑，您需要用鍵標識此元件所屬的元件，此欄位的輸入應為`fieldRoot` + `<*fieldLabel*>`

* `checkboxfields`

   此元件會新增`Boolean`資料類型的預設核取方塊，以及Sling參數`checked@Delete`和`checked@TypeHint`。

* `datepickerfields`

   新增日期選擇器元件運作所需隱藏輸入的元件。 包括建立屬性`defaultDateField`、`displayedFormat`、`emptyText`、`valueFormat`、`minDate`和`maxDate`。

* `datetimepickerfields`

   這會新增`Date&Time`資料類型的選取欄位，以區分`Date`和`Date&Time`選項。

* `datevaluefield`

   這會將日期選擇器新增至屬性，讓使用者可以為`Date&Time`資料類型選取預設值。

* `descriptionfield`

   此元件將添加一個多行文本欄位，該欄位表示多行編輯器中當前所選元件的說明。 模型編輯器會在每個資料類型屬性的結尾自動添加它。

* `labelfield`

   添加`textfield`輸入的元件，該輸入為可以具有欄位標籤的資料類型添加欄位標籤。

* `maptopropertyfield`

   此元件在屬性中添加`Name`欄位，為資料類型的選定元件提供標識符。 所有資料類型中都應包含此變數。

* `maxlengthfield`

   它可用來新增`maxLength`屬性，以便與接受此屬性的資料類型搭配使用。 例如，使用&#x200B;**單行文字**、**數字**&#x200B;等。

* `multieditorfield`

   這會新增多行編輯器運作所需的所有隱藏欄位，由&#x200B;**多行文字**&#x200B;資料類型表示。

* `mvfields`

   新增多欄位元件運作所需所有隱藏欄位的元件。 例如，對於&#x200B;**單行文本**&#x200B;資料類型的第二個選項。 應針對以多欄位呈現的任何元件新增此項目。

* `numbertypefield`

   為&#x200B;**Number**&#x200B;資料類型選擇選項，該資料類型在&#x200B;**Integer**&#x200B;或&#x200B;**Fraction**&#x200B;之間為&#x200B;**Number**&#x200B;資料類型選擇。

* `numbervaluefield`

   **Number** `type.options`的`numberfield`預設值選擇器這將添加&#x200B;**Enumeration**&#x200B;資料類型的選項輸入，用於確定所選框元件的值。

* `placeholderfield`

   這是用作元件`emptyText`屬性的輸入的文本欄位。 所有接受預留位置的資料類型都應使用此方法(這並不十分複雜；例如&#x200B;**單行文本**、**數字**&#x200B;等)。

* `renderasfield`

   當資料類型節點的屬性中存在多個`fieldResourceTypes`時，即自動呈現此元件。

* `requiredfield`

   這是代表元件`required`屬性的核取方塊。 因為大多數元件都接受`required`欄位，所以此欄位可用於大多數資料類型。

* `tagsfields`

   為要呈現的`tagfield`元件添加所需輸入的元件，由&#x200B;**Tags**&#x200B;資料類型使用。

* `tagsroot`

   **Tags**&#x200B;資料類型用來設定`tagsfield`元件的根路徑的路徑選擇器。

* `textfield`

   `Boolean`資料類型用於設定由此資料類型定義的複選框的欄位標籤。

* `textvaluefield`

   **單行文本**&#x200B;資料類型的預設值屬性。

## 建立資料類型{#creating-your-data-type}

若要建立您自己的資料類型，您必須：

* [建立節點結構](#creating-the-node-structure)
* [定義資料類型的屬性](#defining-the-properties-for-your-data-type)

然後，您就可以[使用資料類型](#using-your-data-type)。

您也可以[建立自己的`fieldProperties`](#creating-your-own-fieldproperties-property)。

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
   >`/cfm/models/formbuilderconfig/datatypes/items` 可能需要使用指定的nodetype來建立。

1. 在`/items`下，可以添加新節點來表示新的資料類型：

   * 節點類型：`nt:unstructured`
   * &quot;屬性：請參閱[定義資料類型的屬性](#defining-the-properties-for-your-data-type)

### 定義資料類型{#defining-the-properties-for-your-data-type}的屬性

1. 確定資料類型所需的以下[資料類型屬性](#data-type-properties)的值：

   * `fieldResourceType`
   * `fieldPropResourceType`
   * `fieldViewResourceType`

   這些定義將如何呈現資料類型的元件。 它們可以是任何元件；包括您自己的自訂元件（需要` [fieldProperties](#fieldproperties)`的相符集）。

   在資料類型的節點上，以適當的值定義這些屬性。

1. 確定要使用的` [fieldProperties](#fieldproperties)`。 這取決於您的`fieldResourceType`需要的屬性或屬性。

   例如，`granite/ui/components/coral/foundation/form/textfield`應具有&#x200B;**標籤名稱**、**最大長度**、**佔位符文本**&#x200B;和&#x200B;**預設值**&#x200B;屬性。

   您可以從現成可用的[fieldProperties](#fieldproperties)或[建立您自己的屬性](#creating-your-own-fieldproperties-property)中進行選擇。

   在資料類型的節點上，以適當的值定義這些屬性。

1. 確定以下[資料類型屬性](#data-type-properties)的值：

   * `fieldIcon`
   * `fieldTitle`
   * `renderType`
   * `valueType`
   * `listOrder`

   在資料類型的節點上，以適當的值定義這些屬性。

### 使用資料類型{#using-your-data-type}

保存此節點結構後，在應用了所有屬性的情況下，可以使用模型編輯器開啟任何模型，並查看和使用新的資料類型。

## 建立自己的欄位屬性屬性{#creating-your-own-fieldproperties-property}

您可以從現成可用的[fieldProperties](#fieldproperties)中選擇，或建立您自己的屬性：

1. 在下方建立元件：

   `/apps/dam/cfm/models/editor/components/datatypeproperties/`

   如果路徑不存在，可以使用`nt:folder`節點建立路徑。

   1. 若要存取變數，此元件應延伸：

      `/libs/dam/cfm/models/editor/components/datatypeproperties/base`*

   1. 元件應可透過下列方式納入：

      `sling:include`

   1. 此元件應呈現欄位（如果使用者需要導入資料）或隱藏輸入，內含您資料類型所需的屬性。 例如，多欄位元件需要子節點，其類型應為其重複的欄位，因此應有一個輸入可建立(透過SlingPOST機制)特定類型的子節點。

1. 應將此元件的基本名稱添加到`fieldProperties`。
1. 對您需要的所有屬性重複執行。


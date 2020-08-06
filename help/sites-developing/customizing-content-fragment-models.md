---
title: 不要發佈，但不要刪除自訂內容片段模型
seo-title: 自訂內容片段模型
description: 可自訂和擴充內容片段模型。
seo-description: 可自訂和擴充內容片段模型。
page-status-flag: de-activated
uuid: 5bcfb5d8-37d4-4a0e-882d-bc8a1bac6ba7
contentOwner: aheimoz
discoiquuid: 208225ee-9052-4a45-9cfd-f8d27d4d70ed
noindex: true
translation-type: tm+mt
source-git-commit: 3bdff366a0d455b405c1f9de371ced98d25ae2e2
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---


# 不要發佈，但不要刪除自訂內容片段模型{#do-not-publish-but-do-not-delete-customizing-content-fragment-models}

「內容片段模型」編輯器是基於的嚮導， `Formbuilder`繼承自：

`granite/ui/components/foundation/form/formbuilder`

此元件具有渲染模型編輯器的拖放介面所需的工具，其中包括每種元件的資料類型和屬性。

## 位置 {#locations}

模型會儲存並建立在啟 `/conf`用「內容片段模型」屬 [性的資料夾下](/help/assets/content-fragments-models.md#enable-content-fragment-models) 。 此設定也可在「設定屬性」中 **看到**，您可從「設定瀏 **覽器」存取**。

1. 透過工具、一般 **、設定瀏覽**&#x200B;器導覽 **至瀏**&#x200B;覽 ****&#x200B;器例如， 
`http://localhost:4502/libs/granite/configurations/content/view.html/conf`

1. 從瀏覽器中，從工具列中選擇適當的 **配置** 「屬性」。

   例如，下列項目的屬 `global`性： `http://localhost:4502/libs/granite/configurations/content/edit.html/conf/global`

在模型控制台中，將顯示所有具有「內 **容片段模型」屬性的資料夾** 。 透過工 **具**、資產 **、內**&#x200B;容片段模型導覽 ****; 例如， `http://localhost:4502/libs/dam/cfm/models/console/content/models.html/conf`。

使用者可 [以使用「建立模型](/help/assets/content-fragments-models.md#creating-a-content-fragment-model) 」精靈(使用 **從主控台建立****** )來建立內容片段模型。

>[!CAUTION]
>
>您 ***不得*** 更改路徑中的任 `/libs` 何內容。
>
>這是因為下次升級 `/libs` 實例時會覆寫的內容（套用修補程式或功能套件時可能會覆寫）。

## 模型結構 {#structure-of-a-model}

嚮導將建立具有以下結構的條目：

![cf-54](assets/cf-54.png)

* `../settings/dam/cfm/models`

   所有模型都保存在此資料夾的子資料夾下。

* `jcr:content`

   每個模型都包含一 `jcr:content` 個節點：

   * 包含有關模型的資訊屬 `jcr:title`性， `lastModified`如 `lastModifiedBy`
   * 通常 `sling:ResourceType` 為 `dam/cfm/models/console/components/data/entity/default`,

      與 `sling:ResourceSuperType` of `dam/cfm/models/console/components/data/entity`

* `model`

   節 `model` 點包含一個屬性， `dataTypesConfig`用於確定模型編輯器中使用的資料類型。

* `items`

   在節 `items` 點下，添加到模型的所有資料類型都將保存（在模型編輯器中拖放）。 每個項目都有隨機節點名稱，但為了讓內容片段編輯器使用此模型，每個項目都必須有屬 `name` 性。 此外，在此節點上，將保存特定資料類型的所有配置屬性，包括渲染元件所需的預設屬性。

>[!CAUTION]
>
>在模型編輯器中拖放的所有資料類型，如此執行個體化， **必須**`name` 由使用者輸入屬性。
>
>這被視為屬 **性名稱&amp;ast;** 在模型編 **輯器的** 「屬性」(Properties)頁籤中。

## 模型編輯器的結構 {#structure-of-the-model-editor}

「內 **容片段模型編輯器** 」包含兩個部分：

* 左側的預覽（或檢視）面板，您可在其中放置項目。 此特性：

   * 顯示已實例化 **的「資料類型** 」的預覽。
   * 允許在模型編輯器中進行排序。

* 右側 **面板中的**「資料類型/**** 屬性」標籤。 此特性：

   * 顯示可拖曳和執行個體化的資料類型清單。
   * 對於現成可用的模型編輯器，清單位於：

      `/libs/settings/dam/cfm/models/formbuilderconfig/datatypes`

      <!-- Please uncomment when file is used
      This node contains all the data types currently supported in the model editor. For more information on how to configure the data types, see [Customizing Data Types for Content Fragment Models](/help/sites-developing/customizing-content-fragment-model-data-types.md).
      -->

   * 所有轉換的資料類型都有兩個指令碼標籤，當實例化時，這些標籤將形成視圖（在左側呈現的元件）和「屬性」頁籤，該頁籤定義用戶可以為給定元件定義的屬性。 ****

>[!CAUTION]
>
>您 ***不得*** 更改路徑中的任 `/libs` 何內容。
>
>這是因為下次升級 `/libs` 實例時會覆寫的內容（套用修補程式或功能套件時可能會覆寫）。

<!-- Please uncomment when files are used
The properties on the right side define a form that is submitted directly into JCR under `/conf`; see the path in the example [Structure of a Model](/help/sites-developing/customizing-content-fragment-models.md#structure-of-a-model).
-->

當資料類型實例化時，會針對需要在內容片段中呈現元件的每個屬性建立HTML輸入。 例如，這些包括：

* **屬性名稱&amp;ast;** ( `name`)-做為元件的識別碼

* **渲染方式** ( `metaType`)-鍵入要渲染為

* **說明** ( `fieldDescription`)-內容片段中的元件說明

* 等等。


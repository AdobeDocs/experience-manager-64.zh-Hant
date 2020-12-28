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
source-git-commit: b61c20c65ceade0153f5cd04fbedfd02e919d483
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---


# 不要發佈，但不要刪除自定義內容片段模型{#do-not-publish-but-do-not-delete-customizing-content-fragment-models}

「內容片段模型」編輯器是基於`Formbuilder`的嚮導，繼承自：

`granite/ui/components/foundation/form/formbuilder`

此元件具有渲染模型編輯器的拖放介面所需的工具，其中包括每種元件的資料類型和屬性。

## 位置 {#locations}

在`/conf`下，在[啟用「內容片段模型」屬性](/help/assets/content-fragments-models.md#enable-content-fragment-models)的資料夾下儲存並建立模型。 此設定也可在&#x200B;**配置屬性**&#x200B;中看到，可從&#x200B;**[配置瀏覽器](/help/sites-administering/configurations.md)**&#x200B;訪問。

1. 通過&#x200B;**工具**、**一般**、**配置瀏覽器**瀏覽器
例如， 
`http://localhost:4502/libs/granite/configurations/content/view.html/conf`

1. 從瀏覽器中，從工具欄中選擇相應的配置，然後選擇&#x200B;**屬性**。

   例如，`global`的屬性：`http://localhost:4502/libs/granite/configurations/content/edit.html/conf/global`

在模型控制台中，將顯示具有&#x200B;**內容片段模型**&#x200B;屬性的所有資料夾。 透過&#x200B;**工具**、**資產**、**內容片段模型**&#x200B;導覽；例如，`http://localhost:4502/libs/dam/cfm/models/console/content/models.html/conf`。

使用者可以使用「建立模型」精靈（使用主控台的「建立」精靈）來建立內容片段模型。[](/help/assets/content-fragments-models.md#creating-a-content-fragment-model)********

>[!CAUTION]
>
>您&#x200B;***必須***&#x200B;不要變更`/libs`路徑中的任何項目。
>
>這是因為下次升級實例時會覆寫`/libs`的內容（當您套用修補程式或功能套件時可能會覆寫）。

## 模型{#structure-of-a-model}的結構

嚮導將建立具有以下結構的條目：

![cf-54](assets/cf-54.png)

* `../settings/dam/cfm/models`

   所有模型都保存在此資料夾的子資料夾下。

* `jcr:content`

   每個型號都包含一個`jcr:content`節點，該節點：

   * 包含有關模型的資訊屬性，如`jcr:title`、`lastModified`、`lastModifiedBy`
   * 通常`sling:ResourceType`為`dam/cfm/models/console/components/data/entity/default`,

      的`sling:ResourceSuperType`，共`dam/cfm/models/console/components/data/entity`

* `model`

   `model`節點包含一個屬性`dataTypesConfig`，用於確定模型編輯器中使用的資料類型。

* `items`

   在`items`節點下，將保存添加到模型的所有資料類型（在模型編輯器中拖放）。 每個項目都有隨機節點名稱，但為了讓內容片段編輯器使用此模型，每個項目必須有`name`屬性。 此外，在此節點上，將保存特定資料類型的所有配置屬性，包括渲染元件所需的預設屬性。

>[!CAUTION]
>
>在模型編輯器中拖放的所有資料類型，因此&#x200B;**必須**&#x200B;由用戶輸入`name`屬性。
>
>在模型編輯器的&#x200B;**Properties**&#x200B;標籤中，這被視為&#x200B;**屬性名稱&amp;ast;**。

## 模型編輯器的結構{#structure-of-the-model-editor}

**內容片段模型編輯器**&#x200B;包含兩個部分：

* 左側的預覽（或檢視）面板，您可在其中放置項目。 此特性：

   * 顯示實例化的&#x200B;**資料類型**&#x200B;的預覽。
   * 允許在模型編輯器中進行排序。

* 右側面板中的&#x200B;**資料類型**/**屬性**&#x200B;頁籤。 此特性：

   * 顯示可拖曳和執行個體化的資料類型清單。
   * 對於現成可用的模型編輯器，清單位於：

      `/libs/settings/dam/cfm/models/formbuilderconfig/datatypes`

      <!-- Please uncomment when file is used
      This node contains all the data types currently supported in the model editor. For more information on how to configure the data types, see [Customizing Data Types for Content Fragment Models](/help/sites-developing/customizing-content-fragment-model-data-types.md).
      -->

   * 所有轉換的資料類型都有兩個指令碼標籤，當實例化時，這些標籤將形成視圖（在左側轉換的元件）和&#x200B;**Properties**&#x200B;頁籤，該頁籤定義用戶可以為給定元件定義的屬性。

>[!CAUTION]
>
>您&#x200B;***必須***&#x200B;不要變更`/libs`路徑中的任何項目。
>
>這是因為下次升級實例時會覆寫`/libs`的內容（當您套用修補程式或功能套件時可能會覆寫）。

<!-- Please uncomment when files are used
The properties on the right side define a form that is submitted directly into JCR under `/conf`; see the path in the example [Structure of a Model](/help/sites-developing/customizing-content-fragment-models.md#structure-of-a-model).
-->

當資料類型實例化時，會針對需要在內容片段中呈現元件的每個屬性建立HTML輸入。 例如，這些包括：

* **屬性名稱&amp;ast;** ( `name`)-用作元件的標識符

* **Render As** ( `metaType`)-鍵入要呈現為

* **Description** ( `fieldDescription`)-內容片段中的元件說明

* 等等。


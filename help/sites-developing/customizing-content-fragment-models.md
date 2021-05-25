---
title: 不發佈，但不DELETE自訂內容片段模型
seo-title: 自訂內容片段模型
description: 內容片段模型可自訂和延伸。
seo-description: 內容片段模型可自訂和延伸。
page-status-flag: de-activated
uuid: 5bcfb5d8-37d4-4a0e-882d-bc8a1bac6ba7
contentOwner: aheimoz
discoiquuid: 208225ee-9052-4a45-9cfd-f8d27d4d70ed
noindex: true
source-git-commit: b61c20c65ceade0153f5cd04fbedfd02e919d483
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---


# 不發佈，但不DELETE自訂內容片段模型{#do-not-publish-but-do-not-delete-customizing-content-fragment-models}

內容片段模型編輯器是以`Formbuilder`為基礎的精靈，繼承自：

`granite/ui/components/foundation/form/formbuilder`

此元件具有渲染模型編輯器的拖放介面所必需的工具，並包含每個編輯器的資料類型和屬性。

## 位置 {#locations}

模型會儲存並建立在`/conf`下，位於已啟用[內容片段模型屬性](/help/assets/content-fragments-models.md#enable-content-fragment-models)的資料夾下。 此設定也可在&#x200B;**配置屬性**&#x200B;中顯示，可從&#x200B;**[配置瀏覽器](/help/sites-administering/configurations.md)**&#x200B;訪問。

1. 透過&#x200B;**工具**、**一般**、**設定瀏覽器**導覽至瀏覽器
例如， 
`http://localhost:4502/libs/granite/configurations/content/view.html/conf`

1. 從瀏覽器中，從工具列依序選取適當的設定和&#x200B;**屬性**。

   例如，`global`的屬性：`http://localhost:4502/libs/granite/configurations/content/edit.html/conf/global`

在模型控制台中，將顯示具有&#x200B;**內容片段模型**&#x200B;屬性的所有資料夾。 透過&#x200B;**工具**、**資產**、**內容片段模型**&#x200B;導覽；例如`http://localhost:4502/libs/dam/cfm/models/console/content/models.html/conf`。

使用者可以使用&#x200B;**建立模型**&#x200B;精靈（從主控台使用&#x200B;**建立**）[建立內容片段模型](/help/assets/content-fragments-models.md#creating-a-content-fragment-model)。

>[!CAUTION]
>
>您&#x200B;***必須***&#x200B;不要變更`/libs`路徑中的任何項目。
>
>這是因為下次升級執行個體時會覆寫`/libs`的內容（當您套用Hotfix或Feature Pack時，則會覆寫）。

## 模型{#structure-of-a-model}的結構

嚮導將使用以下結構建立條目：

![cf-54](assets/cf-54.png)

* `../settings/dam/cfm/models`

   所有模型都保存在此資料夾的子資料夾下。

* `jcr:content`

   每個模型都包含一個`jcr:content`節點，該節點包括：

   * 包含有關模型的資訊屬性，如`jcr:title`、`lastModified`、`lastModifiedBy`
   * 通常`sling:ResourceType`為`dam/cfm/models/console/components/data/entity/default`,

      `sling:ResourceSuperType`搭配`dam/cfm/models/console/components/data/entity`

* `model`

   `model`節點包含屬性`dataTypesConfig` ，用於確定模型編輯器中使用的資料類型。

* `items`

   在`items`節點下，將保存添加到模型的所有資料類型（如在模型編輯器中拖放的資料類型）。 每個項目都會獲得隨機節點名稱，但為了讓內容片段編輯器與此模型搭配使用，每個項目必須具有`name`屬性。 此外，在此節點上，將保存特定資料類型的所有配置屬性，包括呈現元件所需的預設屬性。

>[!CAUTION]
>
>拖放到模型編輯器中的所有資料類型，因此具現化&#x200B;**必須**&#x200B;由使用者輸入`name`屬性。
>
>在模型編輯器的&#x200B;**Properties**&#x200B;標籤中，這會被視為&#x200B;**屬性名稱&amp;ast;**。

## 模型編輯器{#structure-of-the-model-editor}的結構

**內容片段模型編輯器**&#x200B;包含兩個部分：

* 左側的預覽或檢視面板，您可在其中放置項目。 此特性：

   * 顯示已實例化的&#x200B;**資料類型**&#x200B;的預覽。
   * 允許在模型編輯器內排序。

* 右側面板中的&#x200B;**資料類型**/**屬性**&#x200B;標籤。 此特性：

   * 顯示可拖曳和具現化的資料類型清單。
   * 對於現成可用的模型編輯器，清單位於：

      `/libs/settings/dam/cfm/models/formbuilderconfig/datatypes`

      <!-- Please uncomment when file is used
      This node contains all the data types currently supported in the model editor. For more information on how to configure the data types, see [Customizing Data Types for Content Fragment Models](/help/sites-developing/customizing-content-fragment-model-data-types.md).
      -->

   * 所有呈現的資料類型都有兩個指令碼標籤，在實例化後，這些標籤將形成視圖（在左側呈現的元件）和&#x200B;**Properties**&#x200B;頁簽，該頁簽定義用戶可以為指定元件定義的屬性。

>[!CAUTION]
>
>您&#x200B;***必須***&#x200B;不要變更`/libs`路徑中的任何項目。
>
>這是因為下次升級執行個體時會覆寫`/libs`的內容（當您套用Hotfix或Feature Pack時，則會覆寫）。

<!-- Please uncomment when files are used
The properties on the right side define a form that is submitted directly into JCR under `/conf`; see the path in the example [Structure of a Model](/help/sites-developing/customizing-content-fragment-models.md#structure-of-a-model).
-->

將資料類型實例化時，會針對需要在內容片段中轉譯元件的每個屬性建立HTML輸入。 例如，這些包括：

* **屬性名稱&amp;ast;** ( `name`) — 用作元件的標識符

* **呈現方式** ( `metaType`) — 輸入要呈現為的元件

* **說明** ( `fieldDescription`) — 內容片段中元件的說明

* 還有其他。


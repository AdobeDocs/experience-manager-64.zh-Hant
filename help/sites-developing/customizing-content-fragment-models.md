---
title: 不發佈，但不DELETE自訂內容片段模型
seo-title: Customizing Content Fragment Models
description: 內容片段模型可自訂和延伸。
seo-description: Content Fragment Models can be customized and extended.
page-status-flag: de-activated
uuid: 5bcfb5d8-37d4-4a0e-882d-bc8a1bac6ba7
contentOwner: AEM Docs
discoiquuid: 208225ee-9052-4a45-9cfd-f8d27d4d70ed
noindex: true
source-git-commit: 3358f6b8b492ff2b5858867a1f48a57b06944b1e
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 0%

---


# 不發佈，但不DELETE自訂內容片段模型{#do-not-publish-but-do-not-delete-customizing-content-fragment-models}

內容片段模型編輯器是以 `Formbuilder`，繼承自：

`granite/ui/components/foundation/form/formbuilder`

此元件具有渲染模型編輯器的拖放介面所必需的工具，並包含每個編輯器的資料類型和屬性。

## 位置 {#locations}

模型會儲存並建立於 `/conf`，位於具有 [內容片段模型屬性](/help/assets/content-fragments-models.md#enable-content-fragment-models) 已啟用。 此設定也可在 **配置屬性**，可從 **[配置瀏覽器](/help/sites-administering/configurations.md)**.

1. 透過導覽至瀏覽器 **工具**, **一般**, **配置瀏覽器**
例如， 
`http://localhost:4502/libs/granite/configurations/content/view.html/conf`

1. 從瀏覽器中，依序選取適當的設定 **屬性** 的上界。

   例如， `global`: `http://localhost:4502/libs/granite/configurations/content/edit.html/conf/global`

在模型控制台中，所有資料夾 **內容片段模型** 屬性隨即顯示。 透過導覽 **工具**, **資產**, **內容片段模型**;例如， `http://localhost:4502/libs/dam/cfm/models/console/content/models.html/conf`.

使用者可以 [建立內容片段模型](/help/assets/content-fragments-models.md#creating-a-content-fragment-model) 使用 **建立模型** 精靈(使用 **建立** )。

>[!CAUTION]
>
>您 ***必須*** 不會變更 `/libs` 路徑。
>
>這是因為 `/libs` 會在您下次升級執行個體時覆寫（當您套用Hotfix或Feature Pack時，則會覆寫）。

## 模型結構 {#structure-of-a-model}

嚮導將使用以下結構建立條目：

![cf-54](assets/cf-54.png)

* `../settings/dam/cfm/models`

   所有模型都保存在此資料夾的子資料夾下。

* `jcr:content`

   每個模型都包含 `jcr:content` 節點：

   * 包含有關模型的資訊屬性，例如 `jcr:title`, `lastModified`, `lastModifiedBy`
   * 通常有 `sling:ResourceType` of `dam/cfm/models/console/components/data/entity/default`,

      和 `sling:ResourceSuperType` of `dam/cfm/models/console/components/data/entity`

* `model`

   此 `model` 節點包含屬性 `dataTypesConfig`，用於判斷模型編輯器中使用的資料類型。

* `items`

   在 `items` 節點，則會儲存新增至模型的所有資料類型（如在模型編輯器中拖放）。 每個項目都會獲得隨機節點名稱，但為了讓內容片段編輯器能與此模型搭配使用，每個項目必須具有 `name` 屬性。 此外，在此節點上，將保存特定資料類型的所有配置屬性，包括呈現元件所需的預設屬性。

>[!CAUTION]
>
>拖放至模型編輯器中的所有資料類型，因此已實例化， **必須** 有 `name` 由使用者輸入的屬性。
>
>這視為 **屬性名稱&amp;ast;** 在 **屬性** 模型編輯器的頁簽。

## 模型編輯器的結構 {#structure-of-the-model-editor}

此 **內容片段模型編輯器** 有兩部分：

* 左側的預覽或檢視面板，您可在其中放置項目。 此特性：

   * 顯示的預覽 **資料類型** 已實例化。
   * 允許在模型編輯器內排序。

* 此 **資料類型**/**屬性** 標籤。 此特性：

   * 顯示可拖曳和具現化的資料類型清單。
   * 對於現成可用的模型編輯器，清單位於：

      `/libs/settings/dam/cfm/models/formbuilderconfig/datatypes`

      <!-- Please uncomment when file is used
      This node contains all the data types currently supported in the model editor. For more information on how to configure the data types, see [Customizing Data Types for Content Fragment Models](/help/sites-developing/customizing-content-fragment-model-data-types.md).
      -->

   * 所有轉譯的資料類型都有兩個指令碼標籤，在實例化後，會形成檢視（在左側轉譯的元件）和 **屬性** 索引標籤，定義使用者可為指定元件定義的屬性。

>[!CAUTION]
>
>您 ***必須*** 不會變更 `/libs` 路徑。
>
>這是因為 `/libs` 會在您下次升級執行個體時覆寫（當您套用Hotfix或Feature Pack時，則會覆寫）。

<!-- Please uncomment when files are used
The properties on the right side define a form that is submitted directly into JCR under `/conf`; see the path in the example [Structure of a Model](/help/sites-developing/customizing-content-fragment-models.md#structure-of-a-model).
-->

將資料類型實例化時，會針對需要在內容片段中呈現元件的每個屬性建立HTML輸入。 例如，這些包括：

* **屬性名稱&amp;ast;** ( `name`) — 做為元件的識別碼

* **呈現為** ( `metaType`) — 輸入要呈現為的元件

* **說明** ( `fieldDescription`) — 內容片段中的元件說明

* 還有其他。


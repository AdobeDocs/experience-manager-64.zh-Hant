---
title: 設定RTE以製作無障礙網站
seo-title: 設定RTE以製作無障礙網站
description: 了解如何設定AEM RTF編輯器，以產生無障礙的網站。
seo-description: 了解如何設定AEM RTF編輯器，以產生無障礙的網站。
uuid: 87539fee-3ecc-49f4-af3d-8dde72399c28
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: ff0f006d-461c-4cc4-b6eb-d665f3f3b498
exl-id: 245e1c28-f702-4300-81cf-5139db9d95ec
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 0%

---

# 配置RTE以生成可訪問站點{#configuring-rte-for-producing-accessible-sites}

AEM支援兩者：

* 標準協助工具功能，包括影像的替代文字
* 以及使用RTF編輯器(RTE)的元件建立內容時可存取的其他功能

>[!NOTE]
>
>* [WCAG 2.0快速指南](/help/managing/qg-wcag.md)
* [建立可存取的內容（符合WCAG 2.0）](/help/sites-authoring/creating-accessible-content.md)


內容作者可使用RTE的功能，在將內容新增至頁面時提供協助工具資訊。 這可以包括通過標題和段落元素添加結構資訊。

您可以透過為元件設定RTE外掛程式](#configuring-the-plugin-features)來[設定和自訂這些功能。 例如， `paraformat`外掛程式可讓您新增其他區塊層級語意元素，包括將支援的標題層級數量擴展至預設提供的基本`H1`、`H2`和`H3`以外。

RTE可在觸控式和傳統UI的多種元件中使用。 但是，使用RTE的主要元件是&#x200B;**Text**&#x200B;元件。

AEM中的&#x200B;**Text**&#x200B;元件適用於觸控式和傳統UI。 下列影像顯示已啟用一系列外掛程式的RTF編輯器，包括`paraformat`:

* 觸控式UI中的&#x200B;**Text**&#x200B;元件：

   ![觸控式UI中以全螢幕模式顯示的文字元件(RTE)。](assets/chlimage_1-206.png)

* 傳統UI中的&#x200B;**Text**&#x200B;元件：

   ![在傳統UI中編輯文字元件的對話方塊(RTE)。](assets/chlimage_1-207.png)

>[!NOTE]
傳統UI和觸控式UI中可用的RTE功能之間有所差異。 如需更多詳細資訊，請參閱
* [外掛程式及其功能](/help/sites-administering/rich-text-editor.md#aboutplugins)
* [外掛程式及其功能 — 觸控式UI](/help/sites-administering/rich-text-editor.md#aboutplugins)



## 配置插件功能{#configuring-the-plugin-features}

[設定RTF編輯器](/help/sites-administering/rich-text-editor.md)頁面提供設定RTE的完整指示。 涵蓋所有問題，包括關鍵步驟：

* [外掛程式及其功能](/help/sites-administering/rich-text-editor.md#aboutplugins)
* [配置位置](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations)
* [啟動外掛程式並設定功能屬性](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)
* [設定RTE的其他功能](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)

在CRXDE Lite中適當的`rtePlugins`子分支內設定外掛程式（請參閱下圖），即可啟用該外掛程式的所有或特定功能。

![CRXDE Lite顯示範例rtePlugin。](assets/chlimage_1-208.png)

### 示例 — 指定RTE選擇欄位{#example-specifying-paragraph-formats-available-in-rte-selection-field}中可用的段落格式

新的語義塊格式可通過以下方式提供供選擇：

1. 視您的RTE而定，決定並導覽至[設定位置](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations)。
1. [啟用「段落」選擇欄位](/help/sites-administering/rich-text-editor.md);來 [啟用外掛程式](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)。
1. [在「段落」選取欄位中指定您要使用的格式](/help/sites-administering/rich-text-editor.md)。
1. 然後，內容作者可從RTE中的選取欄位使用段落格式。 可存取：

   * 在觸控式UI中使用段落([pilcrow](https://en.wikipedia.org/wiki/Pilcrow))圖示：

   ![段落圖示。](do-not-localize/chlimage_1-7.png)

   * 使用傳統UI中的&#x200B;**Format**&#x200B;欄位（下拉式選取器）。


透過段落格式選項，在RTE中提供結構元素，AEM為開發無障礙內容提供了良好的基礎。 內容作者無法使用RTE來設定字型大小、顏色或其他相關屬性的格式，因而無法建立內嵌格式。 相反，它們必須選取適當的結構元素，例如標題，並使用從樣式選項中選擇的全域樣式。 這可確保標籤簡潔，為使用自己的樣式表和正確結構化內容瀏覽的用戶提供更多選項。

## 使用源編輯功能{#use-of-the-source-edit-feature}

在某些情況下，內容作者會發現必須檢查並調整使用RTE建立的HTML原始碼。 例如，在RTE內建立的內容片段可能需要額外的標籤，以確保符合WCAG 2.0。這可以透過RTE的[來源edit](/help/sites-administering/rich-text-editor.md#aboutplugins)選項來完成。 您可以在`misctools`外掛程式](/help/sites-administering/rich-text-editor.md#aboutplugins)上指定[ `sourceedit`功能。

>[!CAUTION]
請小心使用`sourceedit`功能。 輸入錯誤和/或不支援的功能可能會導致更多問題。

## 新增對其他HTML元素和屬性的支援{#adding-support-for-additional-html-elements-and-attributes}

若要進一步擴充AEM的協助功能，可以根據RTE（例如&#x200B;**Text**&#x200B;和&#x200B;**Table**&#x200B;元件）擴充現有元件，並附加元素和屬性。

以下過程說明如何使用&#x200B;**Caption**&#x200B;元素擴展&#x200B;**Table**&#x200B;元件，該元素向輔助技術用戶提供有關資料表的資訊：

### 示例 — 將標題添加到表屬性對話框{#example-adding-the-caption-to-the-table-properties-dialog}

在`TablePropertiesDialog`的建構子中，添加用於編輯標題的附加文本輸入欄位。 請注意，`itemId`必須設為`caption`（即DOM屬性的名稱），才能自動處理其內容。

在&#x200B;**Table**&#x200B;中，您必須明確設定或從DOM元素移除屬性。 該值由`config`對象中的對話框傳遞。 請注意，應使用對應的`CQ.form.rte.Common`方法（`com`是`CQ.form.rte.Common`的捷徑）來設定/移除DOM屬性，以避免瀏覽器實作的常見陷阱。

>[!NOTE]
此程式僅適用於傳統UI。

### 逐步說明{#step-by-step-instructions}

1. 開始CRXDE Lite。 例如：[http://localhost:4502/crx/de/](http://localhost:4502/crx/de/)
1. 複製:

   `/libs/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   至:

   `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   >[!NOTE]
   如果中間資料夾尚未存在，則可能需要建立這些資料夾。

1. 複製:

   `/libs/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`

   至:

   `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`。

1. 開啟下列檔案以進行編輯（按兩下開啟）:

   `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`

1. 在`constructor`方法中，行讀取前：

   ```
   var dialogRef = this;
   ```

   新增下列程式碼：

   ```
   editItems.push({
       "itemId": "caption",
       "name": "caption",
       "xtype": "textfield",
       "fieldLabel": CQ.I18n.getMessage("Caption"),
       "value": (this.table && this.table.caption ? this.table.caption.textContent : "")
   });
   ```

1. 開啟下列檔案：

   `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`。

1. 在`transferConfigToTable`方法的結尾處新增下列程式碼：

   ```
   /**
    * Adds Caption Element
   */
   var captionElement;
   if (dom.firstChild && dom.firstChild.tagName.toLowerCase() == "caption")
   {
      captionElement = dom.firstChild;
   }
   if (config.caption)
   {
       var captionTextNode = document.createTextNode(config.caption)
       if (captionElement)
       {
          dom.replaceNode(captionElement.firstChild,captionTextNode);
       } else
       {
           captionElement = document.createElement("caption");
           captionElement.appendChild(captionTextNode);
           if (dom.childNodes.length>0)
           {
              dom.insertBefore(captionElement, dom.firstChild);
           } else
           {
              dom.appendChild(captionElement);
           }
       }
   } else if (captionElement)
   {
     dom.removeChild(captionElement);
   }
   ```

1. 使用&#x200B;**Save All**&#x200B;保存更改

>[!NOTE]
純文字欄位並非字幕元素值允許的唯一輸入類型。 任何透過`getValue()`方法提供註解值的ExtJS介面工具集皆可使用。
若要新增其他元素和屬性的編輯功能，請確定兩者：
* 每個對應欄位的`itemId`屬性設為適當DOM屬性(`TablePropertiesDialog`)的名稱。
* 在DOM元素上明確設定和/或移除屬性(`Table`)。


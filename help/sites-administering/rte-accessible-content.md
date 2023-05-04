---
title: 設定RTE以製作無障礙網站
seo-title: Configuring RTE for Producing Accessible Sites
description: 了解如何設定AEM RTF編輯器，以產生無障礙的網站。
seo-description: Learn how to configure the AEM Rich Text Editor to produce accessible sites.
uuid: 87539fee-3ecc-49f4-af3d-8dde72399c28
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: ff0f006d-461c-4cc4-b6eb-d665f3f3b498
exl-id: 245e1c28-f702-4300-81cf-5139db9d95ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 0%

---

# 設定RTE以製作無障礙網站 {#configuring-rte-for-producing-accessible-sites}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

AEM支援兩者：

* 標準協助工具功能，包括影像的替代文字
* 以及使用RTF編輯器(RTE)的元件建立內容時可存取的其他功能

>[!NOTE]
>
>* [WCAG 2.0快速指南](/help/managing/qg-wcag.md)
>* [建立可存取的內容（符合WCAG 2.0）](/help/sites-authoring/creating-accessible-content.md)


內容作者可使用RTE的功能，在將內容新增至頁面時提供協助工具資訊。 這可以包括通過標題和段落元素添加結構資訊。

您可以 [透過設定RTE外掛程式來設定和自訂這些功能](#configuring-the-plugin-features) （元件）。 例如， `paraformat` 外掛程式可讓您新增其他區塊層級語義元素，包括將支援的標題層級數量擴展至基本 `H1`, `H2` 和 `H3` 預設提供。

RTE可在觸控式和傳統UI的多種元件中使用。 不過，使用RTE的主要元件為 **文字** 元件。

此 **文字** AEM中的元件適用於觸控式和傳統UI。 下列影像顯示已啟用一系列外掛程式的RTF編輯器，包括 `paraformat`:

* 此 **文字** 元件（在觸控式UI中）:

   ![觸控式UI中以全螢幕模式顯示的文字元件(RTE)。](assets/chlimage_1-206.png)

* 此 **文字** 傳統UI中的元件：

   ![在傳統UI中編輯文字元件的對話方塊(RTE)。](assets/chlimage_1-207.png)

>[!NOTE]
>
>傳統UI和觸控式UI中可用的RTE功能之間有所差異。 如需更多詳細資訊，請參閱
>
>* [外掛程式及其功能](/help/sites-administering/rich-text-editor.md#aboutplugins)
>* [外掛程式及其功能 — 觸控式UI](/help/sites-administering/rich-text-editor.md#aboutplugins)
>


## 設定外掛程式功能 {#configuring-the-plugin-features}

有關配置RTE的完整說明，請參見 [設定RTF編輯器](/help/sites-administering/rich-text-editor.md) 頁面。 涵蓋所有問題，包括關鍵步驟：

* [外掛程式及其功能](/help/sites-administering/rich-text-editor.md#aboutplugins)
* [配置位置](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations)
* [啟動外掛程式並設定功能屬性](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)
* [設定RTE的其他功能](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)

在適當的 `rtePlugins` CRXDE Lite的子分支（請參閱下圖），您可以啟用該外掛程式的所有或特定功能。

![CRXDE Lite顯示範例rtePlugin。](assets/chlimage_1-208.png)

### 示例 — 指定RTE選擇欄位中可用的段落格式 {#example-specifying-paragraph-formats-available-in-rte-selection-field}

新的語義塊格式可通過以下方式提供供選擇：

1. 視您的RTE而定，決定並導覽至 [配置位置](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations).
1. [啟用「段落」選擇欄位](/help/sites-administering/rich-text-editor.md);by [啟用外掛程式](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins).
1. [在「段落」選擇欄位中指定要提供的格式](/help/sites-administering/rich-text-editor.md).
1. 然後，內容作者可從RTE中的選取欄位使用段落格式。 可存取：

   * 使用段落([皮克羅](https://en.wikipedia.org/wiki/Pilcrow))圖示（位於觸控式UI中）:

   ![段落圖示。](do-not-localize/chlimage_1-7.png)

   * 使用 **格式** 欄位（下拉式選取器）。


透過段落格式選項，在RTE中提供結構元素，AEM為開發無障礙內容提供了良好的基礎。 內容作者無法使用RTE來設定字型大小、顏色或其他相關屬性的格式，因而無法建立內嵌格式。 相反，它們必須選取適當的結構元素，例如標題，並使用從樣式選項中選擇的全域樣式。 這可確保標籤簡潔，為使用自己的樣式表和正確結構化內容瀏覽的用戶提供更多選項。

## 使用源編輯功能 {#use-of-the-source-edit-feature}

在某些情況下，內容作者會發現必須檢查並調整使用RTE建立的HTML原始碼。 例如，在RTE中建立的內容片段可能需要額外的標籤，以確保符合WCAG 2.0。這可以使用 [來源編輯](/help/sites-administering/rich-text-editor.md#aboutplugins) 選項。 您可以指定 [ `sourceedit` 功能 `misctools` 外掛程式](/help/sites-administering/rich-text-editor.md#aboutplugins).

>[!CAUTION]
>
>使用 `sourceedit` 特徵。 輸入錯誤和/或不支援的功能可能會導致更多問題。

## 新增對其他HTML元素和屬性的支援 {#adding-support-for-additional-html-elements-and-attributes}

若要進一步擴充AEM的協助工具功能，您可以根據RTE擴充現有元件(例如 **文字** 和 **表格** 元件)，以及其他元素和屬性。

下列程式說明如何擴充 **表格** 元件 **註解** 為輔助技術使用者提供資料表格相關資訊的元素：

### 示例 — 將標題添加到表屬性對話框 {#example-adding-the-caption-to-the-table-properties-dialog}

在 `TablePropertiesDialog`，添加用於編輯標題的附加文本輸入欄位。 請注意 `itemId` 必須設為 `caption` （即DOM屬性的名稱）以自動處理其內容。

在 **表格** 您必須明確將屬性設為DOM元素或從中移除。 值會由 `config` 物件。 請注意，DOM屬性應使用對應的 `CQ.form.rte.Common` 方法( `com` 是 `CQ.form.rte.Common`)，以避免瀏覽器實作的常見陷阱。

>[!NOTE]
>
>此程式僅適用於傳統UI。

### 逐步指示 {#step-by-step-instructions}

1. 開始CRXDE Lite。 例如： [http://localhost:4502/crx/de/](http://localhost:4502/crx/de/)
1. 複製:

   `/libs/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   至:

   `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   >[!NOTE]
   >
   >如果中間資料夾尚未存在，則可能需要建立這些資料夾。

1. 複製:

   `/libs/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`

   至:

   `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`。

1. 開啟下列檔案以進行編輯（按兩下開啟）:

   `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`

1. 在 `constructor` 方法，在讀取行之前：

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

1. 在 `transferConfigToTable` 方法：

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

1. 使用 **全部儲存**

>[!NOTE]
>
>純文字欄位並非字幕元素值允許的唯一輸入類型。 任何ExtJS介面工具集，透過其提供註解的值 `getValue()` 方法。
>
>若要新增其他元素和屬性的編輯功能，請確定兩者：
>
>* 此 `itemId` 每個對應欄位的屬性會設為適當DOM屬性的名稱(`TablePropertiesDialog`)。
>* 已在DOM元素上明確設定和/或移除屬性(`Table`)。


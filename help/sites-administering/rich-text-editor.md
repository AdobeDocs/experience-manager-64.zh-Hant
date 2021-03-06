---
title: 設定RTF編輯器
description: 了解如何設定AEM RTF編輯器。
contentOwner: AG
exl-id: 2d5e9ada-1567-43dc-ab19-6891e20e1d0b
source-git-commit: 160f403d2ec9bfbede75fac2c4315314f98ab27e
workflow-type: tm+mt
source-wordcount: '2661'
ht-degree: 0%

---

# 設定RTF編輯器 {#configure-the-rich-text-editor}

RTF編輯器(RTE)為作者提供多種編輯文字內容的功能。 WYSIWYG文字編輯體驗提供圖示、選取方塊、工具列和功能表。

若要了解如何使用RTE功能進行製作，請參閱[使用RTF編輯器進行製作](/help/sites-authoring/rich-text-editor.md)。 RTE可以設定為啟用、停用和擴充製作元件中可用的功能。 以下工作流程說明在Experience Manager中完成RTE設定工作的建議順序。

![設定RTF編輯器的典型工作流程](assets/rte_workflow_v1.png)

*圖：設定RTF編輯器的典型工作流程*

## 了解觸控式UI和傳統UI {#understand-touch-enabled-ui-and-classic-ui}

觸控式UI是AEM的標準UI。 Adobe在5.6版中推出觸控式UI，其中[回應式設計](/help/sites-authoring/responsive-layout.md)適用於製作環境。觸控式UI專為觸控和桌上型裝置而設計。 UI與原始的傳統UI有很大不同。

![觸控式UI中的RTF編輯器工具列](assets/chlimage_1-404.png)

*圖：觸控式UI中的RTF編輯器工具列*

![傳統UI中的RTF編輯器工具列](assets/rtedefault.png)

*圖：傳統UI中的RTF編輯器工具列*

>[!MORELIKETHIS]
>
>* [UI建議](/help/sites-deploying/ui-recommendations.md)
* 有關淘汰傳統UI的資訊，請參閱[AEM 6.4發行說明](/help/release-notes/deprecated-removed-features.md)
* 如需UI之間的差異，請參閱[觸控式UI和傳統UI](https://aemcq5pedia.wordpress.com/2018/01/05/touch-enabled-ui-aem6-3/)
* 若要詳細了解啟用觸控的UI，請參閱[AEM觸控UI的概念](/help/sites-developing/touch-ui-concepts.md)


## 各種編輯模式 {#editingmodes}

作者可以使用不同的元件模式，在AEM中建立和編輯文字內容。 用於編寫和格式化內容的工具列選項以及不同編輯模式下啟用RTE的元件的用戶體驗，會因RTE配置而異。

| 編輯模式 | 編輯區域 | 要啟用的建議功能 | 觸控式 UI | 傳統 UI |
|--- |--- |--- |--- |--- |
| 內嵌 | 就地編輯，以快速、微幅編輯；不開啟對話框的格式 | 最小RTE功能 | Y | Y |
| RTE全螢幕 | 涵蓋整個頁面 | 所有必要的RTE功能 | Y | N |
| 對話方塊 | 對話方塊，但不涵蓋整個頁面 | 傳統UI中所有必要的RTE功能；審慎啟用觸控式UI中的功能 | Y | Y |
| 全螢幕對話方塊 | 與全螢幕模式相同；包含與RTE一起顯示的對話框欄位 | 所有必要的RTE功能 | Y | N |

>[!NOTE]
在觸控式UI的內嵌編輯模式中，無法使用來源編輯功能。 您無法以全螢幕模式拖曳影像。 所有其他功能都可在所有模式中運作。

### 內嵌編輯 {#inline-editing}

開啟時（按兩下/按一下速度緩慢），您可以在頁面內編輯內容。 提供包含基本選項的緊湊型工具列。

![在觸控式UI中與基本工具列內嵌編輯](assets/chlimage_1-405.png)

*圖：在觸控式UI中與基本工具列內嵌編輯*

在傳統UI中，按兩下元件時速度緩慢，可進行內嵌編輯，而橘色外框會醒目顯示內容。 如果「內容尋找器」已開啟，則視窗頂端會顯示包含可用RTE格式選項的工具列。 如果「內容尋找器」未開啟，則不會顯示格式選項，您只能編輯基本文字。

### 全螢幕編輯 {#full-screen-editing}

AEM元件可以以全螢幕檢視開啟，隱藏頁面內容並佔據可用螢幕。 請考慮以全螢幕編輯詳細的內嵌編輯版本，因為它提供最多的編輯選項。 使用內嵌編輯模式時，可從緊湊工具列按一下![rte_fullscreen](assets/rte_fullscreen.png)以開啟。

對話框全螢幕模式提供了詳細的RTE工具欄，以及對話框模式中可用的選項和元件。 此變數僅適用於包含RTE與其他元件的對話方塊。

![在觸控式UI中以全螢幕模式編輯時，詳細的RTE工具列](assets/chlimage_1-406.png)

*圖：在觸控式UI中以全螢幕模式編輯時，詳細的RTE工具列*

### 對話方塊編輯 {#dialog-editing}

在傳統UI中按兩下元件時，會開啟一個對話方塊以編輯內容。 對話框將在現有頁面的頂部開啟。 在某些特定情況下，對話方塊會以快顯視窗的形式開啟。 例如，當文本元件是多列頁面佈局中列的一部分時，對話框的可用區域較小。

![在觸控式UI中編輯對話方塊模式](assets/dialog_editing_modetouchui.png)

*圖：在觸控式UI中編輯對話方塊模式*

![傳統UI中包含編輯詳細工具列的對話框](assets/chlimage_1-407.png)

*圖：傳統UI中包含編輯詳細工具列的對話框*

## 關於RTE外掛程式和相關功能 {#aboutplugins}

此功能可透過一系列外掛程式提供，每個外掛程式都具備：

* `features`屬性：

   * 這可用來啟用或停用該外掛程式的基本功能。
   * 可使用標準化程式來設定。

* 需要專門配置的更多屬性和選項（如果適用）。

RTE的基本功能會由適當外掛程式特定節點上的`features`屬性值來啟動或停用。

下表列出目前的外掛程式，顯示：

* 具有API檔案連結的外掛程式ID。 在[啟用外掛程式](/help/sites-administering/configure-rich-text-editor-plug-ins.md#activateplugin)時，會將ID用作節點名稱。
* `features`屬性的允許值。
* 外掛程式所提供功能的說明。

| 外掛程式ID | 功能 | 說明 |
|--- |--- |--- |
| 編輯 | 剪下複製貼上 — 預設貼上 — plaintext paste-wordhtml | [剪下、複製和三種貼上模式](/help/sites-administering/configure-rich-text-editor-plug-ins.md#text-styles)。 |
| [芬德雷普萊斯](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FindReplacePlugin) | 查找替換 | 查找和替換。 |
| [格式](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FormatPlugin) | 粗體斜體下划線 | [基本文字格式](/help/sites-administering/configure-rich-text-editor-plug-ins.md#text-styles)。 |
| [影像](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ImagePlugin) | 影像 | 基本影像支援（從內容或內容尋找器拖曳）。 根據瀏覽器，支援對作者有不同的行為 |
| [鍵](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.KeyPlugin) |  | 若要定義此值，請參閱[標籤大小](/help/sites-administering/configure-rich-text-editor-plug-ins.md#tab-size)。 |
| [證明](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.JustifyPlugin) | justifleft justifycenter justifyright | 段落對齊。 |
| [連結](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.LinkPlugin) | 修改連結取消連結錨點 | [超連結和錨點](/help/sites-administering/configure-rich-text-editor-plug-ins.md#link-styles)。 |
| [清單](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ListPlugin) | 已訂購的縮進 | 此外掛程式可同時控制[縮排和清單](/help/sites-administering/configure-rich-text-editor-plug-ins.md#indent-margin);包括巢狀清單。 |
| [miscools](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.MiscToolsPlugin) | specialchars sourceedit | 其他工具允許作者輸入[特殊字元](/help/sites-administering/configure-rich-text-editor-plug-ins.md#special-char)或編輯HTML源。 此外，如果要定義自己的清單，也可以新增整個[範圍的特殊字元](/help/sites-administering/configure-rich-text-editor-plug-ins.md#define-range-char)。 |
| Paraformat | paraformat | 預設段落格式為段落、標題1、標題2和標題3（`<p>`、`<h1>`、`<h2>`和`<h3>`）。 您可以[添加更多段落格式](/help/sites-administering/configure-rich-text-editor-plug-ins.md#para-formats)或擴展清單。 |
| 拼字檢查 | 核取文字 | [語言感知的拼字檢查程式](/help/sites-administering/configure-rich-text-editor-plug-ins.md#add-dict)。 |
| 樣式 | 樣式 | 支援使用CSS類別的樣式。 [如果您想](/help/sites-administering/configure-rich-text-editor-plug-ins.md#text-styles) 要新增（或擴充）您自己的樣式範圍以搭配文字使用，請新增文字樣式。 |
| 上標 | 下標上標 | 基本格式的擴充功能，新增子指令碼和超指令碼。 |
| 表格 | 表remotetable insertrow removerow insertcolumn removecolumn cellprops mergells sliptcellselectrow選擇列 | 如果要為整個表或單個單元格添加自己的樣式，請參閱[配置表樣式](/help/sites-administering/configure-rich-text-editor-plug-ins.md#table-styles)。 |
| 復原 | 撤消重做 | [還原和重做](/help/sites-administering/configure-rich-text-editor-plug-ins.md#undo-history)操作的歷史記錄大小。 |

>[!NOTE]
對話方塊模式中不支援全螢幕外掛程式。 使用`dialogFullScreen`設定將工具列配置為全螢幕模式。

## 了解設定路徑和位置 {#understand-the-configuration-paths-and-locations}

當您[啟用RTE外掛程式](/help/sites-administering/configure-rich-text-editor-plug-ins.md#activateplugin)時，您為作者提供的[RTE編輯（和UI）](#editingmodes)模式會決定設定詳細資訊的位置：

| 編輯模式 | 觸控式UI的位置 | 傳統UI的位置 |
|---|---|---|
| 內嵌 | `cq:editConfig/cq:inplaceEditing` | `cq:editConfig/cq:inplaceEditing` |
| 全螢幕 | `cq:editConfig/cq:inplaceEditing` | 不適用 |
| 對話方塊 | `cq:dialog` | `dialog` |
| 全螢幕對話方塊 | `cq:dialog` | 不適用 |

>[!NOTE]
請勿將`cq:inplaceEditing`下的節點命名為`config`。 在`cq:inplaceEditing`節點上，定義以下屬性：
* **名稱**:  `configPath`
* **類型**:  `String`
* **值**:包含實際配置的節點的路徑

請勿將RTE設定節點命名為`config`。 否則，RTE配置只對管理員有效，對組`content-author`中的用戶無效。

設定下列僅適用於觸控式UI中對話方塊編輯模式的屬性：

* `useFixedInlineToolbar`:將RTE節點上定義的此Boolean屬性(一個具有sling:resourceType=  `cq/gui/components/authoring/dialog/richtext`)設 `True`定為，使RTE工具列固定而非浮動。

   此屬性為true時，RTF編輯預設會在「foundation-contentloaded」事件上啟動。

   要防止此情況，請將屬性`customStart`設定為`True`並觸發「rte-start」事件以開始RTE編輯。 當此屬性為「true」時，預設行為（點擊時開始的rte）無法運作。

* `customStart`:將RTE節點上定義的此布林屬性設 `True`定為，以透過觸發事件來控制何時啟動 `rte-start`RTE。

* `rte-start`:開始編輯RTE `contenteditable-div` 時在RTE上觸發此事件。只有在`customStart`已設為true時，才能使用。

在觸控式對話方塊中使用RTE時，必須將屬性`useFixedInlineToolbar`設為true，才能避免問題。

## 就地自訂編輯 {#customizing-in-place-editing}

您可以設定下列屬性，以定義文字編輯器開始的HTML選取器：

* **`editElementQuery`**  — 在上定 `cq:InplaceEditingConfig`義，此屬性用於指定HTML元素的選取器，在該選取器上將啟動文字元件的內嵌編輯。如果未指定，則直接在文本元件HTML上啟動內嵌編輯。
* **`textPropertyName`**  — 在上定 `cq:InplaceEditingConfig`義，此屬性用於指定要儲存在內容節點上的屬性名稱，在內嵌編輯後，文本元件的HTML值將保存在該節點上。

對話框模式的對應屬性為`name`。

## 啟用外掛程式以啟用RTE功能 {#enable-rte-functionalities-by-activating-plug-ins}

可透過一系列外掛程式使用RTE功能，每個外掛程式都具有features屬性。 您可以配置features屬性，以啟用或停用每個外掛程式的各種功能。

如需RTE外掛程式的詳細設定，請參閱[如何啟用和設定RTE外掛程式](/help/sites-administering/configure-rich-text-editor-plug-ins.md)。

下載此範例設定，以了解如何設定RTE。 在此包中，所有功能都已啟用。

[取得檔案](/help/assets/assets/rte-sample-all-features-enabled-10.zip)

>[!NOTE]
[核心元件文字元件](https://helpx.adobe.com/experience-manager/core-components/using/text.html)允許範本編輯器將使用者介面中的許多RTE外掛程式設定為內容原則，而不需要進行技術設定。 內容原則可搭配RTE使用者介面設定使用，如所述。 如需詳細資訊，請參閱[RTE使用者介面設定和內容政策](/help/sites-administering/rich-text-editor.md#rtecontentpolicies)、[建立頁面範本](/help/sites-authoring/templates.md)和[核心元件開發人員檔案](https://helpx.adobe.com/experience-manager/core-components/using/developing.html)。

>[!NOTE]
如需參考，可在以下網址找到預設的文字元件（在標準安裝中提供）:
* `/libs/wcm/foundation/components/text`
* `/libs/foundation/components/text`

若要建立您自己的文字元件，請複製上述元件，而非編輯這些元件。

## 配置RTE工具欄 {#dialogfullscreen}

AEM可讓您針對不同的編輯模式，以不同方式設定RTF編輯器的UI。 預設設定如下。 您可以根據需求改寫這些預設值。

為獲得最佳製作體驗：

* 在浮動對話方塊中，僅啟用沒有快顯視窗的外掛程式，因為浮動對話方塊的大小較小。
* 在全螢幕對話方塊中，啟用所有必要的外掛程式，甚至具有較大彈出式視窗的外掛程式，例如`Paste`外掛程式。 使用下面描述的`dialogFullScreen`配置。

```java
<uiSettings jcr:primaryType="nt:unstructured">
  <cui jcr:primaryType="nt:unstructured">
    <inline
      jcr:primaryType="nt:unstructured"
      toolbar="[format#bold,format#italic,format#underline,#justify,#lists,links#modifylink,links#unlink,#paraformat]">
      <popovers jcr:primaryType="nt:unstructured">
        <justify
          jcr:primaryType="nt:unstructured"
          items="[justify#justifyleft,justify#justifycenter,justify#justifyright]"
          ref="justify"/>
        <lists
          jcr:primaryType="nt:unstructured"
          items="[lists#unordered,lists#ordered,lists#outdent,lists#indent]"
          ref="lists"/>
        <paraformat
          jcr:primaryType="nt:unstructured"
          items="paraformat:getFormats:paraformat-pulldown"
          ref="paraformat"/>
      </popovers>
    </inline>
    <dialogFullScreen
      jcr:primaryType="nt:unstructured"
      toolbar="[format#bold,format#italic,format#underline,justify#justifyleft,justify#justifycenter,justify#justifyright,lists#unordered,lists#ordered,lists#outdent,lists#indent,links#modifylink,links#unlink,table#createoredit,#paraformat,image#imageProps]">
      <popovers jcr:primaryType="nt:unstructured">
        <paraformat
          jcr:primaryType="nt:unstructured"
          items="paraformat:getFormats:paraformat-pulldown"
          ref="paraformat"/>
      </popovers>
    </dialogFullScreen>
    <tableEditOptions
      jcr:primaryType="nt:unstructured"
      toolbar="[table#insertcolumn-before,table#insertcolumn-after,table#removecolumn,-,table#insertrow-before,table#insertrow-after,table#removerow,-,table#mergecells-right,table#mergecells-down,table#mergecells,table#splitcell-horizontal,table#splitcell-vertical,-,table#selectrow,table#selectcolumn,-,table#ensureparagraph,-,table#modifytableandcell,table#removetable,-,undo#undo,undo#redo,-,table#exitTableEditing,-]">
    </tableEditOptions>
  </cui>
</uiSettings>
```

內嵌模式和全螢幕模式會使用不同的UI設定。 工具欄屬性用於指定工具欄的按鈕。 例如，如果按鈕本身是功能（例如`Bold`），則會指定為`PluginName#FeatureName`（例如`links#modifylink`）。 如果按鈕為彈出式視窗（包含外掛程式的某些功能），則會指定為`#PluginName`（例如`#format`）。 分隔符號( |)可以使用「 — 」指定一組按鈕之間的值。

內嵌或全螢幕模式下的快顯視窗節點包含所使用游標的清單。 `popovers`節點下的每個子節點都以外掛程式的名稱命名（例如`format`）。 其屬性`items`包含外掛程式的功能清單（例如`format#bold`）。

## RTE使用者介面設定和內容原則 {#rtecontentpolicies}

管理員可以使用內容原則來控制RTE選項，例如，不必如上所述執行設定。 內容策略在作為[可編輯模板](../sites-authoring/templates.md)的一部分時定義元件的設計屬性。 例如，如果使用RTE的文本元件與可編輯的模板一起使用，則內容策略可以定義粗體選項可用，並可以定義幾個段落格式選項。 內容原則可重複使用，可套用至多個範本。

AEM 6.4 Service Pack 3之後，RTE中從使用者介面設定到內容原則下游的可用選項。

* 用戶介面配置設定定義了哪些選項可用於內容策略。
* 如果RTE的用戶介面配置已刪除或未啟用項目，則內容策略無法配置它。
* 作者只能存取使用者介面設定和內容原則所提供的功能。

例如，您可以看到[文字核心元件檔案](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/text.html#the-text-component-and-the-rich-text-editor)。

## 自定義工具欄表徵圖和命令之間的映射 {#iconstoolbar}

您可以自訂RTE工具列上顯示的珊瑚圖示和可用命令之間的對應。 除了Coral圖示，您無法使用其他任何圖示。

1. 在`uiSettings/cui`下建立名為`icons`的節點。

1. 為其下的各個表徵圖建立節點。
1. 在每個個別圖示節點上，指定一個Coral圖示和一個命令來對應該圖示。

以下是將命令Bold對應至名為`textItalic`的Coral圖示的范常式式碼片段。

```java
<text jcr:primaryType="nt:unstructured" sling:resourceType="cq/gui/components/authoring/dialog/richtext" name="./text" useFixedInlineToolbar="{Boolean}true"> 
    <rtePlugins jcr:primaryType="nt:unstructured"> 
        <format jcr:primaryType="nt:unstructured" features="bold,italic"/> 
    </rtePlugins> 
    <uiSettings jcr:primaryType="nt:unstructured"> 
        <cui jcr:primaryType="nt:unstructured"> 
            <inline jcr:primaryType="nt:unstructured" 
                toolbar="[format#bold,format#italic,format#underline,links#modifylink,links#unlink]"> 
            </inline> 
            <icons jcr:primaryType="nt:unstructured"> 
                <bold jcr:primaryType="nt:unstructured" 
                    command="format#bold" 
                    icon="textItalic"/> 
            </icons> 
        </cui> 
    </uiSettings> 
</text>
```

## 切換至CoralUI 2 RTF編輯器 {#switch-to-coralui-rich-text-editor}

在頁面上，您可以包含CoralUI 2 RTE clientlib或CoralUI 3 RTE clientlib。 依預設，RTF編輯器包含CoralUI 3 RTE clientlib。 若要切換至CoralUI 2 RTE，請執行下列步驟。

>[!NOTE]
Adobe不建議將切換作為最佳實務。 切換至CoralUI 2 RTE作為最後手段。 如果外掛程式不依賴RTE內部（例如類別）,CoralUI 2 RTE的自訂外掛程式可與CoralUI 3 RTE搭配使用。 如果您使用CoralUI 3 RTE的自訂外掛程式，請使用`rte.coralui3`資料庫。

1. 在`/apps`下覆蓋節點`/libs/cq/gui/components/authoring/editors/clientlibs/core`，並執行下列操作：

   * 為dependencies屬性將`rte.coralui3`替換為`rte.coralui2`。
   * 將內嵌屬性的`cq.authoring.editor.core.inlineediting.rte.coralui3`取代為`cq.authoring.editor.core.inlineediting.rte.coralui2`。
   * 將內嵌屬性的`cq.authoring.rte.coralui3`取代為`cq.authoring.rte.coralui2`。

1. 在`/apps`下覆蓋節點`/libs/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui3`和`/libs/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui2`。

   從`/apps/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui3`中刪除類別`cq.authoring.dialog`並將其添加到`/apps/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui2`中。

1. 將頁面上包含的任何其他相依性從`rte.coralui3`變更為`rte.coralui2`。 例如，在`/apps`下覆蓋節點`/libs/mcm/campaign/components/touch-ui/clientlibs/rte`後，將對該節點的任何依賴項從`rte.coralui3`更改為`rte.coralui2`。

1. 在`/apps`下覆蓋節點`cq/ui/widgets`。 將節點`/apps/cq/ui/widgets`上的相依性`cq.rte`替換為`cq.coralui2.rte`。

>[!NOTE]
CoralUI 2 RTE使用handlebars範本進行外掛程式對話。 因此，CoralUI 2 RTE clientlib對handlebars clientlib有相依性。 CoralUI 3 RTE不使用handlebars範本，且沒有任何相關的相依性。 如果您的自訂外掛程式使用handlebars範本，請在網頁中加入handlebars clientlib。

## 更多資訊 {#further-information}

如需設定RTE的詳細資訊，請參閱[AEM Widget API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html)參考。

尤其要查看可用的外掛程式和相關選項：

* [CQ.form.RichText](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.RichText)元件提供用於編輯已設定樣式的文本資訊(RTF)的表單欄位。 若要了解RTF表單可用的所有參數，請參閱設定選項。
* RichText元件使用[CQ.form.rte.plugins.Plugin](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.Plugin)下方列出的外掛程式，提供多種功能。 對於每個外掛程式：

   * 如需可啟用（或停用）功能的詳細資訊，請參閱功能。
   * 如需適當外掛程式的詳細設定，請參閱設定選項以取得所有可用參數。

* 也提供連結之HTML規則的詳細資訊。

上述選項可用來擴充和自訂您自己的RTE。 例如，若要在建立連結時列出頁面中可用的錨點，您可以提供您自己的`LinkPlugin`實作。

## 已知限制 {#known-limitations}

AEM RTE功能有下列限制：

* 只有AEM元件對話方塊才支援RTE功能。 在觸控式UI上，精靈或基礎表單（例如[頁面屬性](/help/sites-developing/page-properties-views.md)和[Stable](/help/sites-authoring/scaffolding.md)）不支援RTE。

* AEM在[混合裝置](/help/release-notes/known-issues.md)上無法運作。

* 請勿將RTE配置節點命名為`config`。 否則，RTE配置只對管理員有效，對組`content-author`中的用戶無效。

* RTE不支援內嵌框架或iframe來內嵌內容。

>[!MORELIKETHIS]
* [設定RTE外掛程式](configure-rich-text-editor-plug-ins.md)
* [使用RTF編輯器進行編寫](../sites-authoring/rich-text-editor.md)
* [為可存取的網站配置RTE](rte-accessible-content.md)
* [Touch UI與傳統UI功能比較](../release-notes/touch-ui-features-status.md)
* [建立複合多欄位元件的教學課程範例](https://experience-aem.blogspot.com/2019/05/aem-65-touchui-composite-multifield-with-coral3-rte-rich-text.html)


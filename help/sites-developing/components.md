---
title: 元件概觀
seo-title: Components
description: 元件是模組化單元，可實現特定功能以在您的網站上展示您的內容
seo-description: Components are modular units which realize specific functionality to present your content on your website
uuid: fb39aeb8-8f43-4091-8083-ebfab89e6e63
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: components
content-type: reference
discoiquuid: 45efff93-2fe5-4313-83a0-0e23a540da93
exl-id: 3444d7df-fc43-4383-87b0-0f00fef116bc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 49%

---

# 元件概觀{#components-overview}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

此頁面概述了 Adobe Experience Manager (AEM) 元件，例如那些[用於頁面編寫](/help/sites-authoring/default-components-foundation.md) 的元件。

## 元件有哪些？ {#what-exactly-is-a-component}

* 一種模組化單元，可實現特定功能以在您的網站上展示您的內容。
* 可重複使用。
* 在存放庫的一個資料夾中開發為獨立單元。
* 沒有隱藏的設定檔案。
* 可以包含其他元件。
* 可在任何AEM系統內的任何位置執行。 也可以限制在特定元件下執行。
* 具有標準化的使用者介面。
* 具有可以設定的編輯行為。
* 使用根據Granite UI元件使用子元素建立的對話方塊
* 使用 [HTL](https://helpx.adobe.com/experience-manager/htl/user-guide.html) （建議）或JSP。
* 可以開發以建立擴充預設功能的自訂元件。

因為元件是模組化的，所以您可以：

* 在您的本機執行個體上開發新元件。
* 將其部署到測試環境。
* 將其部署到即時編寫環境，作者和/或管理員可以在其中新增和設定內容。
* 將其部署到即時發佈環境，它們用於為您網站訪客呈現內容。某些元件（例如Communities）也接受使用者的輸入。

每個 AEM 元件：

* 是資源類型。
* 是完整實現特定功能的指令碼集合。
* 可在中運作 *隔離*，即AEM或入口網站內。

## AEM內的現成元件 {#out-of-the-box-components-within-aem}

AEM隨附各種 [現成可用的元件](/help/sites-authoring/default-components.md) 提供全面功能，包括：

* 段落系統 ( `parsys`)
* 頁面( `responsivegrid`  — 僅支援觸控式UI)
* 文字
* 影像，附帶的文字
* 工具列

提供的元件及其在 [範例We.Retail網站](/help/sites-developing/we-retail.md) 提供了如何實作和使用元件的說明。 這些元件隨附所有原始程式碼，可以按原狀使用，也可以做為修改或擴充元件的起點。

### 核心元件與基礎元件 {#core-components-and-foundation-components}

提供兩組Adobe提供的AEM元件：

* [核心元件](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)
* [基礎元件](/help/sites-authoring/default-components-foundation.md)

**核心元件** AEM 6.3已推出，提供彈性且功能豐富的製作功能。 此 [We.Retail參考網站](/help/sites-developing/we-retail.md) 說明如何使用核心元件，並代表元件開發的目前最佳實務。

**基礎元件** 適用於許多版本，且可在標準AEM安裝中立即使用。 雖然仍受支援，但大部分已遭取代、不再增強，且以舊版技術為基礎。

>[!NOTE]
>
>[核心元件](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) 代表元件設計和開發的目前最佳實務，並可作為參考實作。
>
>[AEM現代化工具](modernization-tools.md) 有助於移轉至核心元件。

### 檢視可用元件 {#viewing-available-components}

如需 AEM 執行個體中所有可用元件的概觀，請使用[元件主控台](/help/sites-authoring/default-components-console.md)。

或者，您也可以使用 CRXDE Lite 取得存放庫中所有可用元件的清單。

1. 在 **[!UICONTROL CRXDE Lite]** 中，從工具列中選擇&#x200B;**[!UICONTROL 工具]**，然後選擇&#x200B;**[!UICONTROL 查詢]**，**[!UICONTROL 查詢]**&#x200B;索引標籤會隨即開啟。

1. 在&#x200B;**[!UICONTROL 查詢]**&#x200B;索引標籤中，選擇 `XPath` 作為 **[!UICONTROL 類型]**。

1. 在&#x200B;**[!UICONTROL 查詢]** 輸入欄位，輸入以下字串：

   `//element(*, cq:Component)`

1. 按一下&#x200B;**[!UICONTROL 執行]**，元件隨即列出。

## 其他資源 {#further-reading}

以下頁面提供有關開發這些元件和其他元件的更詳細資訊：

* [AEM元件 — 基本概念](/help/sites-developing/components-basics.md)
* [開發AEM元件](/help/sites-developing/developing-components.md)
* [開發AEM元件 — 程式碼範例](/help/sites-developing/developing-components-samples.md)
* [配置多個就地編輯器](/help/sites-developing/multiple-inplace-editors.md)
* [開發人員模式](/help/sites-developing/developer-mode.md)
* [測試您的UI](/help/sites-developing/hobbes.md)
* [內容片段的元件](/help/sites-developing/components-content-fragments.md)
* [取得JSON格式的頁面資訊](/help/sites-developing/pageinfo.md)
* [國際化元件](/help/sites-developing/i18n.md)
* [核心元件](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)
* [使用隱藏條件](/help/sites-developing/hide-conditions.md)
* 傳統 UI

   * [AEM元件（傳統UI）](/help/sites-developing/developing-components-classic.md)
   * [使用和擴充Widget（傳統UI）](/help/sites-developing/widgets.md)
   * [使用xtype（傳統UI）](/help/sites-developing/xtypes.md)
   * [開發Forms（傳統UI）](/help/sites-developing/developing-forms.md)

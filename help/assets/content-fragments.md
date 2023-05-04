---
title: 使用內容片段
seo-title: Working with Content Fragments
description: 了解內容片段可如何讓您設計、建立、組織及使用不受頁面影響的內容。
seo-description: Learn how Content Fragments allow you to design, create, curate and use page-independent content.
uuid: aa5acda2-4c20-4fe7-929d-6c065b252cf2
contentOwner: AEM Docs
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: 22ae0d3a-083f-40e4-bf4a-7a755ae9e312
exl-id: e2804707-7b75-4fae-937e-9e258481878f
feature: Content Fragments
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2020'
ht-degree: 3%

---

# 使用內容片段 {#working-with-content-fragments}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>某些內容片段功能需要應用 [AEM 6.4 Service Pack 2(6.4.2.0)或更新版本](/help/release-notes/sp-release-notes.md).

Adobe Experience Manager(AEM)內容片段可讓您設計、建立、組織和 [發佈頁面無關內容](/help/sites-authoring/content-fragments.md). 它們可讓您準備內容，以便在多個位置/多個頻道中使用。

使用AEM核心元件的Sling模型(JSON)匯出功能，也能以JSON格式傳送內容片段。 此傳遞形式：

* 可讓您使用元件來管理要傳送的片段元素
* 在用於API傳送的頁面上新增多個內容片段核心元件，以允許大量傳送

本頁及以下頁面涵蓋建立、設定和維護內容片段的工作：

* [管理內容片段](content-fragments-managing.md)  — 建立內容片段；然後編輯、發佈和參考

* [內容片段模型](content-fragments-models.md)  — 啟用、建立和定義模型

* [變化 — 編寫片段內容](content-fragments-variations.md)  — 製作片段內容並建立主版的變體

* [Markdown](content-fragments-markdown.md)  — 使用您的片段的markdown語法

* [使用關聯內容](content-fragments-assoc-content.md)  — 新增關聯內容

* [中繼資料 — 片段屬性](content-fragments-metadata.md)  — 查看和編輯片段屬性

>[!NOTE]
>
>這些頁面應與 [使用內容片段進行頁面編寫](/help/sites-authoring/content-fragments.md).

通信渠道的數量每年都在增加。 通常管道是指傳送機制，如下所示：

* 物理通道；例如案頭、行動。
* 物理通道中的傳遞形式；例如案頭版的「產品詳細資料頁面」、「產品類別頁面」或行動版的「行動網頁」、「行動應用程式」。

不過，您（可能）不想對所有頻道使用完全相同的內容，您需要根據特定頻道最佳化內容。

內容片段可讓您：

* 考慮如何跨管道有效觸及目標對象。
* 建立和管理不受管道影響的編輯內容。
* 為一系列頻道建立內容池。
* 設計特定頻道的內容變數。
* 透過插入資產（混合媒體片段），將影像新增至文字。

然後，可組合這些內容片段，以透過各種管道提供體驗。

## 內容片段與內容服務 {#content-fragments-and-content-services}

AEM Content Services的設計目的，是為了將AEM中/來自的內容的說明和傳送，歸納為網頁上的重點以外。

它們使用可供任何用戶端使用的標準化方法，將內容傳遞至非傳統AEM網頁的頻道。 這些管道可包括：

* 單頁應用程式
* 原生行動應用程式
* AEM外部的其他通道和接觸點

會以JSON格式傳送。

AEM內容片段可用來說明及管理結構化內容。 結構化內容定義於可包含多種內容類型的模型中；包括文字、數值資料、布林值、日期和時間等。

此結構化內容再加上AEM核心元件的JSON匯出功能，便可用來將AEM內容傳送至AEM頁面以外的管道。

>[!NOTE]
>
>**內容片段** 和 **[體驗片段](/help/sites-authoring/experience-fragments.md)** 是AEM中的不同功能：
>
>* **內容片段** 是編輯內容，主要是文字和相關影像。 它們是純內容，沒有設計和佈局。
>* **體驗片段** 內容全面；網頁的片段。
>
>體驗片段可以包含內容片段形式的內容，但不能以相反的方式。
>
>如需詳細資訊，另請參閱 [了解AEM中的內容片段和體驗片段](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/content-fragments-experience-fragments-article-understand.html).

>[!CAUTION]
>
>傳統UI中沒有內容片段。
>
>內容片段元件可在傳統UI Sidekick中看到，但無法使用其他功能。

>[!NOTE]
>
>AEM也支援片段內容的翻譯。 請參閱 [建立內容片段的翻譯專案](creating-translation-projects-for-content-fragments.md) 以取得更多資訊。

## 內容片段類型 {#types-of-content-fragment}

內容片段可以是：

* 簡單片段

   * 這些沒有預先定義的結構。 它們僅包含文字和影像。
   * 這些是以簡單片段範本為基礎。

* 包含結構化內容的片段

   * 這些是以 [內容片段模型](content-fragments-models.md)，會預先定義產生片段的結構。
   * 這些功能也可用於使用JSON匯出工具來實現內容服務。

## 內容類型 {#content-type}

內容片段包括：

* 儲存為 **資產**:

   * 內容片段（及其變體）可從 **資產** 控制台。
   * 在內容片段編輯器中撰寫和編輯。

* 用於 [透過內容片段元件進行頁面編輯器](/help/sites-authoring/content-fragments.md) （參考元件）:

   * 此 **內容片段** 元件可供頁面作者使用。 它可讓使用者以HTML或JSON格式參照和傳送所需的內容片段。

內容片段是內容結構，可：

* 沒有版面或設計（在RTF模式中可能有一些文字格式）。
* 包含一或多個 [組成部分](#constituent-parts-of-a-content-fragment).
* 可 [包含或連接到影像](#fragments-with-visual-assets).
* 可使用 [中間內容](#in-between-content-when-page-authoring-with-content-fragments) 在頁面上參考時。

* 與傳送機制（即頁面、通道）無關。

### 具有視覺資產的片段 {#fragments-with-visual-assets}

為了讓作者更能控制其內容，可將影像新增至內容片段及/或與其整合。

資產可透過數種方式搭配內容片段使用；各有其優點：

* **插入資產** 進入片段（混合媒體片段）

   * 是片段的必要部分(請參閱 [內容片段的組成部分](#constituent-parts-of-a-content-fragment))。
   * 定義資產的位置。
   * 請參閱 [在片段中插入資產](content-fragments-variations.md#inserting-assets-into-your-fragment) ，以取得詳細資訊。

   >[!NOTE]
   >
   >插入內容片段本身的視覺資產會附加至前一段。 將片段新增至頁面時，當內容介於之間時，這些資產會相對於該段落移動。

* **相關聯的內容**

   * 連接到片段；但不是片段的固定部分(請參閱 [內容片段的組成部分](#constituent-parts-of-a-content-fragment))。
   * 允許一些定位靈活性。
   * 在頁面上使用片段時，可輕鬆供使用（作為中間內容）。
   * 請參閱 [關聯內容](content-fragments-assoc-content.md) 以取得更多資訊。

* 頁面編輯器的「 **資產** 」瀏覽器可用的資產

   * 允許完全彈性地選取資產。
   * 允許一些定位靈活性。
   * 不提供針對特定片段核准的概念。
   * 請參閱 [資產瀏覽器](/help/sites-authoring/author-environment-tools.md#assets-browser) 以取得更多資訊。

### 內容片段的組成部分 {#constituent-parts-of-a-content-fragment}

內容片段資產由下列部分組成（直接或間接）:

* **片段元素**

   * 元素與包含內容的資料欄位相關聯。
   * 對於具有結構化內容的片段，您可以使用內容模型來建立內容片段。 模型中指定的元素（欄位）定義片段的結構。 這些元素（欄位）可以是多種資料類型。
   * 對於簡單片段：

      * 內容保存在一（或多個）多行文本欄位或元素中。
      * 元素是在片段範本中定義(編寫片段時無法定義，請參閱 [內容片段範本](/help/sites-developing/content-fragment-templates.md))。

* **片段段落**

   * 文本塊，即：

      * 由垂直空格分隔（歸位）
      * 在多行文本元素中；簡單或結構化片段
   * 在富 [文本](content-fragments-variations.md#rich-text)[](content-fragments-variations.md#markdown) 和標籤下拉模式中，段落可以格式化為標題，在這種情況下，它和以下段落作為一個單位一起組成。
   * 在頁面製作期間啟用內容控制。


* **插入片段中的資產（混合媒體片段）**

   * 插入實際片段中並用作片段內部內容的資產（影像）。
   * 內嵌於片段的段落系統中。
   * 可在 [頁面上使用/參考片段](/help/sites-authoring/content-fragments.md).
   * 只能使用片段編輯器，在片段中新增、刪除或移動。 無法在頁面編輯器中執行這些動作。
   * 只能使用 [片段編輯器中的RTF格式](content-fragments-variations.md#inserting-assets-into-your-fragment).
   * 只能新增至多行文字元素（任何片段類型）。
   * 附於前文（段）。

   >[!CAUTION]
   >
   >可切換為純文字格式，以（無意中）從片段中移除。

   >[!NOTE]
   >
   >資產也可新增為 [其他（中間）內容](/help/sites-authoring/content-fragments.md#using-associated-content) 在頁面上使用片段時；使用「資產」瀏覽器中的「關聯內容」或「資產」。

* **相關聯的內容**

   * 這是片段外部的內容，但與編輯相關。 通常是影像、視訊或其他片段。
   * 將集合內的個別資產新增至頁面時，可與頁面編輯器中的片段搭配使用。 這表示這些量度為選用，視特定管道的需求而定。
   * 資產包括 [透過集合關聯至片段](content-fragments-assoc-content.md);相關聯的集合可讓作者在編寫頁面時決定要使用的資產。

      * 集合可以透過範本、預設內容或由作者在片段製作期間，與片段建立關聯。
      * [資產(DAM)集合](managing-collections-touch-ui.md) 是片段相關聯內容的基礎。
   * （可選）您也可以將片段本身新增至集合以輔助追蹤。


* **片段中繼資料**

   * 使用 [資產中繼資料結構](metadata.md).
   * 標籤可在下列情況下建立：

      * 建立及製作片段
      * 或更新版本：

         * 檢視/編輯片段 **屬性** 從主控台
         * 編輯 **中繼資料** 片段編輯器中時

   >[!CAUTION]
   >
   >中繼資料處理設定檔不適用於內容片段。

* **主版**

   * 片段的一個完整部分

      * 每個內容片段都有一個主版例項。
      * 無法刪除主版。
   * 主版可在片段編輯器中的 **[變異](content-fragments-variations.md)**.
   * 主版並非如此，而是所有變異的基礎。


* **變數**

   * 轉譯專用於編輯目的的片段文字；可與管道相關，但非強制性，也可用於臨機本機修改。
   * 建立為 **主版**，但之後可視需要編輯；變異本身之間通常會有內容重疊。
   * 可在片段製作期間定義，或在片段範本中預先定義。
   * 儲存在片段中，以協助避免內容復本的分散。
   * 變數可以是 [已同步](content-fragments-variations.md#synchronizing-with-master) 主內容（若已更新）。
   * 可以是 [摘要](content-fragments-variations.md#summarizing-text) 將文本快速截斷到預定義的長度。
   * 可在 [變異](content-fragments-variations.md) 頁簽。

### 使用內容片段製作頁面時的內容之間 {#in-between-content-when-page-authoring-with-content-fragments}

中間內容：

* 可在 [使用內容片段時的頁面編輯器](/help/sites-authoring/content-fragments.md).
* 是 [片段流程中新增的其他內容](/help/sites-authoring/content-fragments.md#adding-in-between-content) 在頁面上使用/參照後。
* 中間內容可新增至任何片段，其中只會顯示一個元素。
* 您也可以使用相關內容，使用適當瀏覽器的資產和/或元件。

>[!CAUTION]
>
>中間內容是頁面內容。 它不會儲存在內容片段中。

### 片段所需 {#required-by-fragments}

若要建立、編輯和使用內容片段，您也需要：

* **內容模型**

   * 是 [啟用，然後使用工具建立](content-fragments-models.md).
   * 需要 [建立結構化片段](content-fragments-managing.md#creating-content-fragments).
   * 定義片段的結構（標題、內容元素、標籤定義）。
   * 內容模型定義需要標題和一個資料元素；其他所有項目均為選用。 模型會定義片段和預設內容的最小範圍（若適用）。 製作片段內容時，作者無法變更已定義的結構。

* **片段範本**

   * 需要 [建立簡單片段](content-fragments-managing.md#creating-content-fragments).
   * 通常 [在項目實施中開發](/help/sites-developing/content-fragment-templates.md);無法在製作時建立。
   * 定義簡單片段的基本屬性 (標題、文字元素數目、標記定義)。
   * 範本定義需要標題和一個文字元素；其他所有項目均為選用。 範本會定義片段和預設內容的最小範圍（若適用）。 作者稍後可將片段擴充至範本中定義的以外。

* **內容片段元件**

   * 協助以HTML和/或JSON格式傳送片段。
   * 需要 [參考頁面上的片段](/help/sites-authoring/content-fragments.md).
   * 負責片段的版面配置和傳送；即頻道。
   * 片段需要一或多個專用元件來定義版面，並傳送部分或所有元素/變異和相關內容。
   * 在製作時將片段拖曳至頁面會自動建立所需元件的關聯。

## 使用範例 {#example-usage}

片段及其元素和變數可用來建立多個頻道的一致內容。 設計片段時，您需要考慮要在哪個位置使用。

### We.Retail範例 {#we-retail-sample}

範例片段可於下列位置查看：

[http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten](http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten)

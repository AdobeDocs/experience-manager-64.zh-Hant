---
title: 管理表單簡介
seo-title: Introduction to managing forms
description: AEM Forms提供管理適用性Forms和相關資產的工具。 本文會介紹重要的表單管理功能和使用者介面元素。
seo-description: AEM Forms provides tools to manage Adaptive Forms and related assets. This article introduces you to the key forms management capabilities and user interface elements.
uuid: 8a9fe83a-e9dc-410e-9bae-eca936c6eb8a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager, introduction
discoiquuid: 6f9cb26a-ac7f-4218-827f-9d4d55b859b4
exl-id: 08686ad6-85cc-4de5-86d8-05d55acec418
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1612'
ht-degree: 1%

---

# 管理表單簡介 {#introduction-to-managing-forms}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

AEM Forms提供簡化且功能強大的使用者介面，可建立及管理表單、檔案、主題、信函、檔案片段、資料字典和相關資產。 它有助於管理表單、檔案和相關資產的完整生命週期 — 從開發人員的案頭到產品\
在入口伺服器上為最終用戶提供。 您可以使用AEM Forms使用者介面來：

* 存取AEM Forms元件
* 存取AEM Forms設定

>[!NOTE]
>
>如需其他AEM工具和選項的詳細資訊，請參閱 [使用作者環境](/help/sites-authoring/home.md).

## 存取AEM Forms元件 {#access-aem-forms-components}

除了建立表單、檔案和相關資產的選項之外，AEM還提供建立網站、資產、管理AEM例項等選項。 您可以按一下 ![adobeexperiencemanager](assets/adobeexperiencemanager.png) Experience Manager標誌，導覽至所有可用的工具。 此外，它還包含AEM Forms的連結，以及其他元件的主控台。 若要導覽至AEM Forms，請按一下 **Experience Manager標誌** ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > **導覽** ![羅盤](assets/compass.png) > **Forms**. 畫面上會顯示下列主控台的連結：

* 表單與文件
* 主題
* 字母
* 文件片段
* 資料字典

![aem-forms-console](assets/aem-forms-console.png)

### 表單與文件  {#forms-documents}

Forms與檔案提供建立互動式通訊、最適化表單、最適化表單片段和表單集的選項。 僅適用於JEE上的AEM Forms，「Forms與檔案」提供從本機儲存匯入檔案，以及使用Workbench同步AEM Forms資產的選項。

「建立」按鈕是建立或上傳AEM Forms資產的程式起點。 它提供建立的選項：

* **互動式通訊**:互動式通訊是個人化、互動式且適合裝置的HTML式數位通信、陳述或檔案。 互動式通訊具有回應性，且會根據使用者裝置和設定自動變更版面和設計。 如需詳細資訊，請參閱 [互動式通訊概述](/help/forms/using/interactive-communications-overview.md).

* **適用性表單：** 最適化表單是吸引人且回應式的表單。 您可以根據使用者回應、裝置或工作環境，新增或移除表單區段，以動態調整以適應使用者輸入。 此 [製作最適化表單簡介](/help/forms/using/introduction-forms-authoring.md) 文章提供最適化表單的詳細資訊。

* **適用性表單片段：** 雖然每個表單都是為特定目的而設計，但大部分表單中都有一些常見的區段，例如提供個人詳細資訊，例如姓名和地址、家庭詳細資訊、收入詳細資訊等。 您可以為這類區段建立個別資產。 這些可重複使用的獨立區段稱為最適化表單片段。 如需詳細資訊，請參閱 [適用性表單片段](/help/forms/using/adaptive-form-fragments.md) 文章。

* **表單集：** 表單集是HTML5份表單的集合，這些表單分組在一起，並以單一表單集的形式向使用者呈現。 當最終用戶開始填寫表單集時，表單將從一個表單無縫轉換到另一個表單。 最後，使用者只需按一下，即可以以單一實體提交所有表單。 如需詳細資訊，請參閱 [表單集於AEM Forms](/help/forms/using/formset-in-aem-forms.md).

* **資料夾：** AEM Forms使用者介面使用資料夾來排列資產。 它支援兩種類型的資料夾：

   * **一般資料夾：** 這些資料夾可用於AEM Forms使用者介面中建立的資產。 這些資料夾沒有嚴格的資料夾結構。 您可以重新命名、建立子檔案夾，以及儲存這些資料夾中的最適化表單、互動式通訊、最適化表單片段、表單範本(XDP)、PDF forms、檔案和相關資產。
   * **Forms Workflow資料夾：** Forms工作流程資料夾是在Workbench程式(LiveCycle封存檔)進行移轉並與AEM Forms使用者介面同步時建立。 不得重新命名、建立子資料夾、建立互動式通訊、最適化表單片段或互動式通訊。 此外，您也無法刪除版本資料夾，或建立及上傳最適化表單、最適化表單片段或與版本資料夾平行的互動式通訊。

![資料夾](assets/folders.png)

**答：** 一般資料夾 **B.** Forms Workflow資料夾

「Forms」和「檔案」面板也提供下列選項：

* **從本機儲存匯入檔案：** 您可以匯入PDF forms與檔案、表單範本（XFA表單）和其他資源（XSD的影像和XML結構）。 如需逐步指示，請參閱 [匯入和匯出資產至AEM Forms](/help/forms/using/import-export-forms-templates.md).

* **將AEM Forms資產與Workbench同步：** 您可以使用「來自Workbench的檔案」選項，將AEM Forms使用者介面與Workbench之間的資產同步。 它可確保所有資產都可在AEM Forms使用者介面和Workbench的crx-repository資產選取中使用。

### 主題  {#themes}

主題包含元件和面板的樣式詳細資料。 主題具有獨立身份。 因此，您可以在多個最適化表單上重複使用主題。 您可以指定元件的樣式，或修改表單中所使用各種元件的CSS屬性。 樣式包括背景顏色、狀態顏色、透明度和大小等屬性。 您可以將自訂項目儲存在主題中，並將它們連接到表單的元件上作為預設集。 將主題添加到表單時，指定的樣式會反映在表單的相應元件上。 透過AEM 6.2 Forms，您可以建立主題並將其套用至表單。

如需建立和使用主題的相關資訊，請參閱 [AEM Forms主題](/help/forms/using/themes.md).

### 字母  {#letters}

AEM表單信函是安全、個人化和互動式的通信。 您可以透過簡化的程式，從預先核准和自訂撰寫的內容快速組合信函（也稱為通信）。

有關建立和使用字母的資訊，請參閱 [建立信函](/help/forms/using/create-letter.md).

### 文件片段 {#document-fragments}

檔案片段是可重複使用的通信部分或元件，您可使用這些元件來撰寫信函。 文檔片段的類型為文本、清單、條件和佈局片段。 如需建立和使用檔案片段的相關資訊，請參閱 [建立檔案片段](/help/forms/using/document-fragments.md).

### 資料字典 {#data-dictionaries}

通常，業務用戶不需要XSD（XML架構）和Java類等元資料表示的知識。 但是，通常需要存取這些資料結構和屬性才能建立解決方案。 AEM Forms使用資料字典，讓商務使用者無需了解其基礎資料模型的技術詳細資訊，便能使用後端資料來源的資訊。

有關建立和使用資料字典的資訊，請參閱建立 [資料字典文章](/help/forms/using/data-dictionary.md)

## 存取AEM Forms設定 {#accessing-aem-forms-configurations}

AEM工具面板包含各種元件的工具。 若要導覽至AEM Forms專用工具，請按一下 **Experience Manager標誌** ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > **工具** ![錘](assets/hammer.png) > **Forms**. 將顯示用於執行以下功能的工具：

* **配置監視資料夾：** 管理員可以配置網路資料夾（稱為監看資料夾），以便當用戶將檔案(如PDF檔案)放在監看資料夾時，啟動預先配置的操作並操作該檔案。 <!-- Fix broken link For detailed information, see Create and Configure a watched folder. -->

* **設定Forms App Offline Service:** AEM Forms應用程式離線服務會快取表單中使用之資源的路徑或URL。 快取表單中所使用資源的路徑或URL可改善伺服器端效能。 若要設定AEM Forms應用程式的伺服器端離線元件，請參閱 [在離線模式下工作](/help/forms/using/work-offline-mode.md).

![aem-forms-tools](assets/aem-forms-tools.png)

* **設定PDF產生器：** 管理員可以設定AEM FormsPDF產生器設定、新增使用者帳戶，以及匯入或匯出設定至PDF產生器。
* **發佈通信管理資產：** AEM Forms可讓您一次從製作例項發佈所有字母、檔案片段、資料字典和相關相依性。 已發佈的資產包含所有通信管理資產和相關相依性。 如需詳細資訊，請參閱 [發佈和取消發佈表單與檔案](/help/forms/using/publishing-unpublishing-forms.md#publishallthecorrespondencemanagementassets).
* **匯出通信管理資產：** 您可以從AEM表單例項以套件形式下載所有通信管理資產和相關相依性。 如需詳細步驟，請參閱 [匯入和匯出資產至AEM Forms](/help/forms/using/import-export-forms-templates.md#importandexportassetsincorrespondencemanagement)

## 使用者介面的常見元素 {#commonelements}

* **左側邊欄：** 您可以按一下左側邊欄圖示 ![raillefpng](assets/railleftpng.png) 以顯示AEM Forms的時間軸和參考功能。

   * **時間表：** 您可以在時間軸中新增及檢視可供檢閱的資產備注。 如需詳細指示，請參閱 [建立和管理表單中資產的審核](/help/forms/using/create-reviews-forms.md).
   * **參考：** AEM Forms資產可用於多個AEM Forms資產。 例如，文檔片段可以用於多個字母。 參考是指所選資產用於的資產清單（其他表單或資源），以及所選資產正在使用的其他資產清單。

* **階層連結：** 階層連結代表目前主控台或資料夾的標題。 您可以按一下階層連結選項，在階層中較高的資料夾層級之間導覽。
* **檢視切換器：** 您可以按一下「檢視切換器」圖示 ![檢視清單](assets/viewlist.png) 或 ![viewcard](assets/viewcard.png) 快速切換清單和卡片檢視。 如需常見使用者介面元件的詳細資訊，請參閱 [使用作者環境](/help/sites-authoring/basic-handling.md).
* **搜尋：** 搜尋選項 ![搜尋](assets/search.png) 提供快速查找並跳轉到所需內容和工具的功能。 輸入內容或產品功能的名稱，然後從建議中選取，例如輸入「檔案」以快速尋找並導覽至Forms與檔案或檔案片段主控台。 如需搜尋的詳細資訊，請參閱AEM 6.2 [搜尋](/help/sites-authoring/search.md) 文章
* **動作工具列**:選取資產時，動作工具列會顯示在資產清單上方。 它包含所選資產的所有管理工具。 您可以將滑鼠移至工具圖示上，檢視說明其功能的工具提示

>[!NOTE]
>
>當使用者執行Forms與檔案的任何主控台搜尋時，邊欄僅包含 **篩選器和選項**. 您可以使用「篩選器與選項」來執行進階搜尋。

* **動作工具列**:選取資產時，動作工具列會顯示在資產清單上方。 它包含所選資產的所有管理工具。 您可以將滑鼠移至工具圖示上，檢視說明其功能的工具提示

![最適化表單的動作工具列](assets/action-tool-bar.png)

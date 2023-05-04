---
title: 社群功能
seo-title: Community Functions
description: 了解如何存取社群功能主控台
seo-description: Learn how to access the Community Functions console
uuid: 5cce05f5-1dd7-496d-94c2-8fccc0177d13
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: cc993b71-e2f2-48e7-ad4e-469cb5ce2dc1
role: Admin
exl-id: 2007336d-d75c-4e01-af81-181751c04cfe
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2568'
ht-degree: 3%

---

# 社群功能 {#community-functions}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

社群體驗預期的功能類型眾所周知。 社群功能可作為社群功能使用。 基本上，這些頁面是預先連線以實作社群功能的一或多個頁面，而這項功能不僅需要以製作模式將元件新增至頁面。 這些是用來定義 [社群網站範本](sites.md) 從哪些社區站點 [已建立](sites-console.md).

建立社群網站後，即可使用標準將內容新增至產生的頁面 [AEM製作模式](../../help/sites-authoring/editing-content.md).

許多社群功能可立即使用，如社群功能主控台所示。 未來版本將提供更多社群功能，並可建立自訂功能。

>[!NOTE]
>
>建立 [社群網站](sites-console.md), [社群網站範本](sites.md), [社群群組範本](tools-groups.md) 和 [社群功能](functions.md) 僅供製作環境使用。

## 社區功能控制台 {#community-functions-console}

在製作環境中，若要進入社群功能主控台

* 從全局導航： **[!UICONTROL 「工具」>「社區」>「社區功能」]**

![chlimage_1-379](assets/chlimage_1-379.png)

## 預先建立的函式 {#pre-built-functions}

以下是隨AEM Communities提供的功能簡要說明。 每個函式都由一或多個AEM頁面組成，這些頁面包含連線在一起的功能中的Communities元件，這些元件可輕鬆整合至 [社群網站範本](sites.md).

社群網站範本提供社群網站的結構，包括登入、使用者設定檔、通知、傳訊、網站功能表、搜尋、貼圖和品牌推廣功能。

### 標題和URL設定 {#title-and-url-settings}

**標題** 和 **URL** 是所有社群函式的共同屬性。

當社群功能新增至社群網站範本，或在 [修改](sites-console.md#modifying-site-properties) 社群網站的結構中，會開啟函式的對話方塊，以便設定標題和URL。

#### 設定功能詳細資料 {#configuration-function-details}

![chlimage_1-380](assets/chlimage_1-380.png)

* **[!UICONTROL 標題]**
(
*必填*)顯示在網站功能選單中的文字

* **[!UICONTROL URL]**
(*必填*)用於生成URI的名稱。 名稱必須符合 [命名慣例](../../help/sites-developing/naming-conventions.md) 由AEM和JCR強加。

例如，使用從以下項目建立的網站： [快速入門](getting-started.md) 教學課程，如果

* 標題=網頁
* URL =頁面

然後頁面的URL為http://local_host:4503/content/sites/engage/en/page.html，頁面的功能表連結會顯示為：

![chlimage_1-381](assets/chlimage_1-381.png)

### 活動資料流功能 {#activity-stream-function}

活動資料流函式是具有 [活動資料流元件](activities.md) 已選取所有檢視（所有活動、使用者活動及後續）。 另請參閱 [活動資料流要點](essentials-activities.md) 供開發人員使用。

將新增至範本時，會開啟下列對話方塊：

#### 設定功能詳細資料 {#configuration-function-details-1}

![chlimage_1-382](assets/chlimage_1-382.png)

* 請參閱 [標題和URL設定](#title-and-url-settings)
* **[!UICONTROL 顯示「我的活動」檢視]**
如果選中此選項，「活動」頁將包含一個頁簽，該頁簽將根據當前成員在社區內生成的活動來篩選活動。 已勾選預設值。

* **[!UICONTROL 顯示「所有活動」檢視]**
如果選中此選項，則「活動」頁將包含一個頁簽，該頁簽包含當前成員有權訪問的社區內生成的所有活動。 已勾選預設值。

* **[!UICONTROL 顯示「新聞摘要」檢視]**
如果選中此選項，則「活動」頁將包含一個頁簽，該頁簽將根據當前成員正在跟蹤的活動來篩選活動。 已勾選預設值。

### 指定任務功能 {#assignments-function}

指配函式是定義 [啟用社群網站](overview.md#enablement-community). 它可為社群成員指派啟用資源。 另請參閱 [工作總攬](essentials-assignments.md) 供開發人員使用。

此函式是 [啟用附加元件](enablement.md). 啟用附加元件需要額外的授權才能在生產環境中使用。

新增至範本時，唯一的設定是 [標題和URL設定](#title-and-url-settings).

### 部落格功能 {#blog-function}

部落格功能是具有 [部落格元件](blog-feature.md) 已配置，用於標籤、檔案上傳、跟蹤、成員自我編輯、投票和協調。 另請參閱 [部落格要點](blog-developer-basics.md) 供開發人員使用。

將新增至範本時，會開啟下列對話方塊：

![chlimage_1-383](assets/chlimage_1-383.png)

* 請參閱 [標題和URL設定](#title-and-url-settings)
* **[!UICONTROL 允許特權成員]**
若勾選此選項，部落格將僅允許有權限的成員透過允許選取 [特權成員組](users.md#privileged-members-group). 如果未選中，則允許所有社區成員建立。 預設為未勾選。

* **[!UICONTROL 允許檔案上載]**
如果勾選此選項，部落格將包含成員上傳檔案的功能。 已勾選預設值。

* **[!UICONTROL 允許線程化回復]**
如果未勾選，部落格將允許對文章的回覆（留言），但是不允許回覆評論。 已勾選預設值。

* **[!UICONTROL 允許精選內容]**
若勾選，可將構想識別為 [精選內容](featured.md). 已勾選預設值。

### 日曆功能 {#calendar-function}

日曆函式是具有 [日曆元件](calendar.md) 配置為允許標籤。 另請參閱 [日曆要點](calendar-basics-for-developers.md) 供開發人員使用。

將新增至範本時，會開啟下列對話方塊：

![chlimage_1-384](assets/chlimage_1-384.png)

* 請參閱 [標題和URL設定](#title-and-url-settings)
* **[!UICONTROL 允許釘選]**
如果選中，論壇將允許將主題回復固定到評論清單的開頭。 已勾選預設值。

* **[!UICONTROL 允許特權成員]**
若勾選此選項，部落格將僅允許有權限的成員透過允許選取 [特權成員組](users.md#privileged-members-group). 如果未選中，則允許所有社區成員建立。 預設為未勾選。

* **[!UICONTROL 允許檔案上載]**
如果勾選此選項，部落格將包含成員上傳檔案的功能。 已勾選預設值。

* **[!UICONTROL 允許線程化回復]**
如果未勾選，部落格將允許對文章的回覆（留言），但是不允許回覆評論。 已勾選預設值。

* **[!UICONTROL 允許精選內容]**
若勾選，可將構想識別為 [精選內容](featured.md). 已勾選預設值。

### 目錄功能 {#catalog-function}

目錄函式提供 [啟用社群](overview.md#enablement-community) 成員以瀏覽未分配給它們的啟用資源。 請參閱 [標籤啟用資源](tag-resources.md) 和 [目錄要點](catalog-developer-essentials.md) 供開發人員使用。

社群網站的所有啟用資源和學習路徑（如果屬性為，則會顯示在所有目錄中） ` [Show in Catalog](resources.md)`，則會設為true。 若要明確包含資源和學習路徑，必須套用 [預先篩選](catalog-developer-essentials.md#pre-filters) 到目錄。

新增至範本時，設定可指定用於設定向網站訪客呈現的標籤篩選器的標籤命名空間：

![目錄函式](assets/catalogfunc.png)

* 請參閱 [標題和URL設定](#title-and-url-settings)
* **[!UICONTROL 選取所有命名空間]**

   * 選取的標籤命名空間會定義訪客可選取的標籤，以篩選目錄中所列的啟用資源清單。
   * 如果勾選此選項，社群網站允許的所有標籤命名空間都可用。
   * 如果未勾選，則可選取社群網站允許的一或多個命名空間。
   * 已勾選預設值。

### 精選內容功能 {#featured-content-function}

精選內容功能是具有 [精選內容元件](featured.md) 配置為允許添加和刪除注釋。

每個元件可能允許或不允許使用特徵內容(請參閱 [部落格功能](#blog-function), [日曆功能](#calendar-function), [論壇功能](#forum-function), [標識函式](#ideation-function)，和 [QnA函式](#qna-function))。

新增至範本時，唯一的設定是 [標題和URL設定](#title-and-url-settings).

### 檔案庫功能 {#file-library-function}

檔案庫函式是具有 [檔案庫元件](file-library.md) 配置為允許添加和刪除注釋。

新增至範本時，唯一的設定是 [標題和URL設定](#title-and-url-settings).

### 論壇功能 {#forum-function}

論壇功能是具有 [論壇元件](forum.md) 已配置，用於標籤、檔案上傳、跟蹤、成員自我編輯、投票和協調。

將新增至範本時，會開啟下列對話方塊：

#### 設定功能詳細資料 {#configuration-function-details-2}

![chlimage_1-385](assets/chlimage_1-385.png)

* 請參閱 [標題和URL設定](#title-and-url-settings)
* **[!UICONTROL 允許釘選]**
如果選中，論壇將允許將主題回復固定到評論清單的開頭。 已勾選預設值。

* **[!UICONTROL 允許特權成員]**
如果勾選此選項，論壇將僅允許有權限的成員透過允許選取 [特權成員組](users.md#privileged-members-group). 如果未勾選，則允許所有社群成員張貼。 預設為未勾選。

* **[!UICONTROL 允許檔案上載]**
如果勾選此選項，論壇將包含成員上傳檔案的功能。 已勾選預設值。

* **[!UICONTROL 允許線程化回復]**
如果未勾選此選項，論壇將允許對某個主題進行評論，但不允許對這些評論進行回覆。 已勾選預設值。

* **[!UICONTROL 允許精選內容]**
若勾選，可將構想識別為 [精選內容](featured.md). 已勾選預設值。

### 組函式 {#groups-function}

>[!CAUTION]
>
>組函式必須 *not* be *第一，也不是唯一* 功能（在網站結構中或社群網站範本中）。
>
>任何其他函式，例如 [頁面函式](#page-function)，必須包含在內並列出。

群組功能可讓社群成員在發佈環境的社群網站內建立子社群。

視 [設定](sites-console.md#groupmanagement) 當群組函式包含在 [社群網站範本](sites.md)，群組可以是公開或私人的，且一或多個社群群組範本可設定為在實際建立社群群組時（例如從發佈環境）提供範本選擇。 A [社群群組範本](tools-groups.md) 指定為組頁面（如論壇和日曆）建立的Communities功能。

建立社區組時，會為新組動態建立成員組，可將成員分配或加入到新組。 如需詳細資訊，請參閱 [管理使用者和使用者群組](users.md).

As of Communities [功能包1](deploy-communities.md#latestfeaturepack)，社群群組會使用 [Communities站點的組控制台](groups.md)、和時，可在啟用後於發佈環境中建立。

將新增至範本時，會開啟下列對話方塊：

![chlimage_1-386](assets/chlimage_1-386.png)

* 請參閱 [標題和URL設定](#title-and-url-settings)
* **[!UICONTROL 選擇組模板]**
下拉式功能表，可選取一或多個已啟用的群組範本，新社群群組的未來建立者（在發佈環境中）可從中選擇。

* **[!UICONTROL 允許特權成員]**
如果勾選此選項，論壇將僅允許有權限的成員透過允許選取 [特權成員安全組](users.md#privileged-members-group). 如果未勾選，則允許所有社群成員張貼。 預設為未勾選。

* **[!UICONTROL 允許建立發佈]**
若勾選此選項，獲授權的社群成員就可以在發佈環境中建立群組。 如果取消勾選，則只能從「社群網站」的「群組」主控台在製作環境中建立新群組（子社群）。

   預設為 `checked`.

### 創意力功能 {#ideation-function}

識別函式是含有 [識別元件](ideation-feature.md).

將其添加到模板時，將開啟以下對話框，該對話框指定預設的標題和URL名稱以及模板的預設顯示設定：

![chlimage_1-387](assets/chlimage_1-387.png)

* 請參閱 [標題和URL設定](#title-and-url-settings)
* **[!UICONTROL 允許特權成員]**
如果勾選此選項，論壇將僅允許有權限的成員透過允許選取 [特權成員安全組](users.md#privileged-members-group). 如果未勾選，則允許所有社群成員張貼。 預設為未勾選。

* **[!UICONTROL 允許檔案上載]**
如果勾選此選項，構想將包含成員上傳檔案的功能。 已勾選預設值。

* **[!UICONTROL 允許線程化回復]**
如果未勾選，該構想將允許對主題的回覆（留言），但不允許對留言的回覆。 已勾選預設值。

* **[!UICONTROL 允許精選內容]**
若勾選，可將構想識別為 [精選內容](featured.md). 已勾選預設值。

### 排行榜功能 {#leaderboard-function}

排行榜功能是包含1的頁面 [排行榜元件](enabling-leaderboard.md).

**注意**:排行榜元件需要進一步配置 *after* 從包含「排行榜」功能的社區模板建立社區站點。 排行榜部分 [規則](enabling-leaderboard.md#rules-tab) 需要指定，這取決於 [計分和徽章](implementing-scoring.md) 為社群網站。

將其添加到模板時，將開啟以下對話框，該對話框指定預設的標題和URL名稱以及模板的預設顯示設定：

![chlimage_1-388](assets/chlimage_1-388.png)

* 請參閱 [標題和URL設定](#title-and-url-settings)
* **[!UICONTROL 顯示徽章]**
如果勾選此選項，排行榜中會包含徽章圖示的欄。

   預設為未勾選。

* **[!UICONTROL 顯示徽章名稱]**
如果選中，則排行榜中將包含徽章名稱的列。

   預設為未勾選。

* **[!UICONTROL 顯示頭像]**
如果選中，成員的頭像影像將包含在排行榜中，位於其成員配置檔案的名稱連結旁。

   預設為未勾選。

### 頁面功能 {#page-function}

頁面函式會在社群網站中新增一個空白頁面，將其連線至社群網站的功能：登入、功能表、通知、傳訊、主題和品牌推廣。 內容可使用 [標準AEM製作模式](../../help/sites-authoring/editing-content.md).

新增至範本時，唯一的設定是 [標題和URL設定](#title-and-url-settings).

### QnA 功能 {#qna-function}

QnA函式是具有 [QnA元件](working-with-qna.md) 已配置，用於標籤、檔案上傳、跟蹤、成員自我編輯、投票和協調。

將新增至範本時，設定會允許限制有權限的成員：

![chlimage_1-389](assets/chlimage_1-389.png)

* 請參閱 [標題和URL設定](#title-and-url-settings)
* **[!UICONTROL 允許釘選]**
如果選中，論壇將允許將主題回復固定到評論清單的開頭。 已勾選預設值。

* **[!UICONTROL 允許特權成員]**
如果選中，則QnA論壇將僅允許特權成員通過允許選擇 [特權成員組](users.md#privileged-members-group). 如果未勾選，則允許所有社群成員張貼。 預設為未勾選。

* **[!UICONTROL 允許檔案上載]**
如果選中，QnA論壇將包括成員上載檔案的功能。 已勾選預設值。

* **[!UICONTROL 允許線程化回復]**
如果未選中，則QnA論壇將允許對已發佈的問題進行評論（回答），但不允許對答案進行答復。 已勾選預設值。

* **[!UICONTROL 允許精選內容]**
若勾選，可將構想識別為 [精選內容](featured.md). 已勾選預設值。

## 建立社群功能 {#create-community-function}

選取 `Create Community Function` 表徵圖。 您可以建立以相同AEM Blueprint為基礎的多個函式，然後在製作編輯模式中開啟，以唯一自訂。

![chlimage_1-390](assets/chlimage_1-390.png)

### 社群功能名稱 {#community-function-name}

![chlimage_1-391](assets/chlimage_1-391.png)

在「社區函式名稱」面板中，將配置名稱、說明以及函式是啟用還是禁用：

* **[!UICONTROL 社區函式名稱]**
用於顯示和儲存的函式名

* **[!UICONTROL 社群功能說明]**
顯示的功能說明

* **[!UICONTROL 禁用/啟用]**
控制函式是否可引用的切換開關

### AEM 藍圖 {#aem-blueprint}

![chlimage_1-392](assets/chlimage_1-392.png)

在 `AEM Blueprint` ，您可以選取作為社群功能基礎實作的blueprint。

社群功能是一個微型網站，由一或多個頁面組成，預先連線以納入社群網站，包括登入、使用者設定檔、通知、傳訊、網站功能表、搜尋、貼圖和品牌功能。 建立函式後，即可 [開啟函式](#open-community-function) 在製作編輯模式中自訂頁面和/或元件設定。

由於社群功能是以 [即時副本](../../help/sites-administering/msm.md#live-copies) a [Blueprint](../../help/sites-administering/msm-livecopy.md#creatingablueprint)，則可轉出對函式所做的變更，而影響從 [社群網站範本](sites.md) 或 [社群群組範本](tools-groups.md) 包含函式。 您也可以將頁面與其上層Blueprint取消關聯，以便進行頁面層級的修改。

另請參閱 [多網站管理員](../../help/sites-administering/msm.md).

### 縮圖 {#thumbnail}

![chlimage_1-393](assets/chlimage_1-393.png)

在縮圖面板上，可上傳影像以顯示在 [社群功能主控台](#community-functions-console).

## 開啟社群功能 {#open-community-function}

![chlimage_1-394](assets/chlimage_1-394.png)

選取 `Open Community Function` 圖示，以進入製作頁面內容和修改功能元件的設定的作者編輯模式。

### 配置元件 {#configuring-components}

社群函式是以AEM Blueprint的即時副本的形式實作，其詳細資訊記錄於 [多網站管理員](../../help/sites-administering/msm.md).

不僅可製作頁面內容，也可設定元件。

如果在已建立的社群網站的頁面上設定元件，則可能需要取消 [繼承](../../help/sites-administering/msm-livecopy.md#changing-live-copy-content) 以設定元件。 完成設定時，應重新建立繼承。

如需設定詳細資訊，請造訪 [Communities元件](author-communities.md) 供作者使用。

## 編輯社群功能 {#edit-community-function}

![chlimage_1-395](assets/chlimage_1-395.png)

選取 `Edit Community Function` 圖示，使用與 [建立社群功能](#create-community-function)，包括啟用或停用函式。

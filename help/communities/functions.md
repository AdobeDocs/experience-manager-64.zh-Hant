---
title: 社群功能
seo-title: 社群功能
description: 了解如何存取社群功能主控台
seo-description: 了解如何存取社群功能主控台
uuid: 5cce05f5-1dd7-496d-94c2-8fccc0177d13
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: cc993b71-e2f2-48e7-ad4e-469cb5ce2dc1
role: Admin
exl-id: 2007336d-d75c-4e01-af81-181751c04cfe
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '2542'
ht-degree: 2%

---

# 社群功能 {#community-functions}

社群體驗預期的功能類型眾所周知。 社群功能可作為社群功能使用。 基本上，這些頁面是預先連線以實作社群功能的一或多個頁面，而這項功能不僅需要以製作模式將元件新增至頁面。 它們是用來定義[社群網站範本](sites.md)的結構的建置塊，從中建立社群網站[](sites-console.md)。

建立社群網站後，可使用標準[AEM製作模式](../../help/sites-authoring/editing-content.md)將內容新增至產生的頁面。

許多社群功能可立即使用，如社群功能主控台所示。 未來版本將提供更多社群功能，並可建立自訂功能。

>[!NOTE]
>
>建立[社群網站](sites-console.md)、[社群網站範本](sites.md)、[社群群組範本](tools-groups.md)和[社群功能](functions.md)的主控台僅用於製作環境。

## 社區功能控制台 {#community-functions-console}

在製作環境中，若要進入社群功能主控台

* 從全局導航：**[!UICONTROL 工具>社區>社區函式]**

![chlimage_1-379](assets/chlimage_1-379.png)

## 預先建立的函式 {#pre-built-functions}

以下是隨AEM Communities提供的功能簡要說明。 每個函式都由一或多個AEM頁面組成，這些頁面包含連線到功能中的Communities元件，該功能可輕鬆整合到[社群網站範本](sites.md)中。

社群網站範本提供社群網站的結構，包括登入、使用者設定檔、通知、傳訊、網站功能表、搜尋、貼圖和品牌推廣功能。

### 標題和URL設定 {#title-and-url-settings}

**** 標題和 **** URL是所有社群函式通用的屬性。

當[修改](sites-console.md#modifying-site-properties)社區站點結構時，將社區函式添加到社區站點模板或添加社區函式時，將開啟該函式的對話框，以便可以配置標題和URL。

#### 設定功能詳細資料 {#configuration-function-details}

![chlimage_1-380](assets/chlimage_1-380.png)

* **[!UICONTROL 標題]**
(
*必要*)顯示在網站功能功能表中的文字

* **[!UICONTROL URL]**
(*必要*)用於產生URI的名稱。名稱必須符合AEM和JCR所強加的[命名慣例](../../help/sites-developing/naming-conventions.md)。

例如，使用在[快速入門](getting-started.md)教學課程之後建立的網站，如果

* 標題=網頁
* URL =頁面

然後頁面的URL為http://local_host:4503/content/sites/engage/en/page.html，頁面的功能表連結會顯示為：

![chlimage_1-381](assets/chlimage_1-381.png)

### 活動資料流功能 {#activity-stream-function}

活動流函式是具有[活動流元件](activities.md)的頁面，其中已選擇所有視圖（所有活動、用戶活動和以下）。 另請參閱開發人員適用的[Activity Stream Essentials](essentials-activities.md) 。

將新增至範本時，會開啟下列對話方塊：

#### 設定功能詳細資料 {#configuration-function-details-1}

![chlimage_1-382](assets/chlimage_1-382.png)

* 請參閱[標題和URL設定](#title-and-url-settings)
* **[!UICONTROL 顯示「我的活動」]**
視圖如果選中此選項，「活動」頁將包含一個頁簽，該頁簽將根據當前成員在社區內生成的活動篩選活動。已勾選預設值。

* **[!UICONTROL 顯示「所有活動」]**
視圖如果選中此選項，「活動」頁將包含一個頁簽，其中包含當前成員有權訪問的社區內生成的所有活動。已勾選預設值。

* **[!UICONTROL 顯示「動態消息」]**
視圖如果選中此選項，「活動」頁將包含一個頁簽，該頁簽根據當前成員正在跟蹤的活動篩選活動。已勾選預設值。

### 指定任務功能 {#assignments-function}

工作總攬函式是定義[社區站點以啟用](overview.md#enablement-community)的基本功能。 它可為社群成員指派啟用資源。 另請參閱開發人員的[Assignments Essentials](essentials-assignments.md)。

此函式是[啟用附加元件](enablement.md)的功能。 啟用附加元件需要額外的授權才能在生產環境中使用。

新增至範本時，唯一的設定是[標題和URL設定](#title-and-url-settings)。

### 部落格功能 {#blog-function}

部落格函式是一個具有[部落格元件](blog-feature.md)的頁面，該元件用於標籤、檔案上傳、跟蹤、成員自我編輯、投票和調節。 另請參閱開發人員適用的[部落格要點](blog-developer-basics.md) 。

將新增至範本時，會開啟下列對話方塊：

![chlimage_1-383](assets/chlimage_1-383.png)

* 請參閱[標題和URL設定](#title-and-url-settings)
* **[!UICONTROL 允許特]**
權成員如果選中此選項，則部落格將僅允許特權成員通過允許選擇特權成員組來 [建立文章](users.md#privileged-members-group)。如果未選中，則允許所有社區成員建立。 預設為未勾選。

* **[!UICONTROL 允許檔]**
案上載如果選中此選項，部落格將包括成員上載檔案的功能。已勾選預設值。

* **[!UICONTROL 允許串]**
連回復如果未選中，部落格將允許對文章的回復（評論），但不允許對評論的回復。已勾選預設值。

* **[!UICONTROL 允許精]**
選內容如果勾選此選項，就能將構想識別為精 [選內容](featured.md)。已勾選預設值。

### 日曆功能 {#calendar-function}

日曆函式是一個具有[日曆元件](calendar.md)的頁面，該元件配置為允許進行標籤。 對於開發人員，另請參閱[Calendar Essentials](calendar-basics-for-developers.md)。

將新增至範本時，會開啟下列對話方塊：

![chlimage_1-384](assets/chlimage_1-384.png)

* 請參閱[標題和URL設定](#title-and-url-settings)
* **[!UICONTROL 允]**
許固定如果選中，論壇將允許主題回覆被固定到評論清單的開頭。已勾選預設值。

* **[!UICONTROL 允許特]**
權成員如果選中此選項，則部落格將僅允許特權成員通過允許選擇特權成員組來 [建立文章](users.md#privileged-members-group)。如果未選中，則允許所有社區成員建立。 預設為未勾選。

* **[!UICONTROL 允許檔]**
案上載如果選中此選項，部落格將包括成員上載檔案的功能。已勾選預設值。

* **[!UICONTROL 允許串]**
連回復如果未選中，部落格將允許對文章的回復（評論），但不允許對評論的回復。已勾選預設值。

* **[!UICONTROL 允許精]**
選內容如果勾選此選項，就能將構想識別為精 [選內容](featured.md)。已勾選預設值。

### 目錄功能 {#catalog-function}

目錄函式使[啟用社區](overview.md#enablement-community)成員能夠瀏覽未分配給他們的啟用資源。 開發人員請參閱[標籤啟用資源](tag-resources.md)和[目錄要點](catalog-developer-essentials.md)。

如果社群網站的屬性` [Show in Catalog](resources.md)`設為true，所有目錄中都會顯示該網站的所有啟用資源和學習路徑。 若要明確包含資源和學習路徑，必須將[pre-filter](catalog-developer-essentials.md#pre-filters)套用至目錄。

新增至範本時，設定可指定用於設定向網站訪客呈現的標籤篩選器的標籤命名空間：

![目錄函式](assets/catalogfunc.png)

* 請參閱[標題和URL設定](#title-and-url-settings)
* **[!UICONTROL 選取所有命名空間]**

   * 選取的標籤命名空間會定義訪客可選取的標籤，以篩選目錄中所列的啟用資源清單。
   * 如果勾選此選項，社群網站允許的所有標籤命名空間都可用。
   * 如果未勾選，則可選取社群網站允許的一或多個命名空間。
   * 已勾選預設值。

### 精選內容功能 {#featured-content-function}

精選內容函式是一個頁面，其中[精選內容元件](featured.md)設定為允許新增及刪除註解。

每個元件可允許或禁止功能內容（請參閱[部落格函式](#blog-function)、[日曆函式](#calendar-function)、[論壇函式](#forum-function)、[標識函式](#ideation-function)和[QnA函式](#qna-function)）。

新增至範本時，唯一的設定是[標題和URL設定](#title-and-url-settings)。

### 檔案庫功能 {#file-library-function}

檔案庫函式是一個頁，其[檔案庫元件](file-library.md)被配置為允許添加和刪除注釋。

新增至範本時，唯一的設定是[標題和URL設定](#title-and-url-settings)。

### 論壇功能 {#forum-function}

論壇函式是一個具有[論壇元件](forum.md)的頁面，該元件用於標籤、檔案上載、跟蹤、成員自我編輯、投票和調節。

將新增至範本時，會開啟下列對話方塊：

#### 設定功能詳細資料 {#configuration-function-details-2}

![chlimage_1-385](assets/chlimage_1-385.png)

* 請參閱[標題和URL設定](#title-and-url-settings)
* **[!UICONTROL 允]**
許固定如果選中，論壇將允許主題回覆被固定到評論清單的開頭。已勾選預設值。

* **[!UICONTROL 允許特]**
權成員如果選中此選項，則論壇將僅允許特權成員通過允許選擇特權成員組來 [發佈主題](users.md#privileged-members-group)。如果未勾選，則允許所有社群成員張貼。 預設為未勾選。

* **[!UICONTROL 允許檔]**
案上載如果選中此選項，論壇將包括成員上載檔案的功能。已勾選預設值。

* **[!UICONTROL 允許串]**
連回復如果未選中，論壇將允許對主題進行評論，但不允許對這些評論進行回復。已勾選預設值。

* **[!UICONTROL 允許精]**
選內容如果勾選此選項，就能將構想識別為精 [選內容](featured.md)。已勾選預設值。

### 組函式 {#groups-function}

>[!CAUTION]
>
>群組函式必須&#x200B;*不*&#x200B;是網站結構或社群網站範本中的&#x200B;*第一個或唯一的*&#x200B;函式。
>
>必須先包含並列出任何其他函式，例如[page函式](#page-function)。

群組功能可讓社群成員在發佈環境的社群網站內建立子社群。

根據[settings](sites-console.md#groupmanagement)，當「組」函式包含在[社區站點模板](sites.md)中時，這些組可以是公用或專用組，並且一個或多個社區組模板可配置為在實際建立社區組時（例如從發佈環境）提供模板的選擇。 [社區組模板](tools-groups.md)指定為組頁面（如論壇和日曆）建立的社區功能。

建立社區組時，會為新組動態建立成員組，可將成員分配或加入到新組。 如需詳細資訊，請參閱[管理使用者和使用者群組](users.md)。

自Communities [Feature Pack 1](deploy-communities.md#latestfeaturepack)起，社群群組是使用[Communities網站的群組主控台](groups.md)在製作環境中建立，且可於啟用時在發佈環境中建立。

將新增至範本時，會開啟下列對話方塊：

![chlimage_1-386](assets/chlimage_1-386.png)

* 請參閱[標題和URL設定](#title-and-url-settings)
* **[!UICONTROL 選擇「]**
組模板」(Group Templates)下拉菜單允許選擇一個或多個啟用的組模板，新社區組的將來建立者（在發佈環境中）可從中選擇這些模板。

* **[!UICONTROL 允許特]**
權成員如果選中此選項，則論壇將僅允許特權成員通過允許選擇特權成員安全組 [來發佈主題](users.md#privileged-members-group)。如果未勾選，則允許所有社群成員張貼。 預設為未勾選。

* **[!UICONTROL 允許發]**
布建立如果選中此選項，授權的社區成員可以在發佈環境中建立組。如果取消勾選，則只能從「社群網站」的「群組」主控台在製作環境中建立新群組（子社群）。

   預設值為`checked`。

### 創意力功能 {#ideation-function}

標識函式是一個包含[標識元件](ideation-feature.md)的頁。

將其添加到模板時，將開啟以下對話框，該對話框指定預設的標題和URL名稱以及模板的預設顯示設定：

![chlimage_1-387](assets/chlimage_1-387.png)

* 請參閱[標題和URL設定](#title-and-url-settings)
* **[!UICONTROL 允許特]**
權成員如果選中此選項，則論壇將僅允許特權成員通過允許選擇特權成員安全組 [來發佈主題](users.md#privileged-members-group)。如果未勾選，則允許所有社群成員張貼。 預設為未勾選。

* **[!UICONTROL 允許檔]**
案上載如果選中此選項，則構想將包括成員上載檔案的能力。已勾選預設值。

* **[!UICONTROL 允許串]**
連回復如果未選中，則該構想將允許對主題的回復（評論），但不允許對評論的回復。已勾選預設值。

* **[!UICONTROL 允許精]**
選內容如果勾選此選項，就能將構想識別為精 [選內容](featured.md)。已勾選預設值。

### 排行榜功能 {#leaderboard-function}

排行榜功能是一個[排行榜元件](enabling-leaderboard.md)的頁面。

**注意**:從社區模板建立社區站點(包 ** 括「排行榜」功能)後，排行榜元件需要進一步配置。需要指定排行榜元件的[rules](enabling-leaderboard.md#rules-tab)，這取決於社區站點的[評分和徽章](implementing-scoring.md)的配置。

將其添加到模板時，將開啟以下對話框，該對話框指定預設的標題和URL名稱以及模板的預設顯示設定：

![chlimage_1-388](assets/chlimage_1-388.png)

* 請參閱[標題和URL設定](#title-and-url-settings)
* **[!UICONTROL 顯]**
示徽章如果選中此選項，則排行榜中將包含徽章表徵圖的列。

   預設為未勾選。

* **[!UICONTROL 顯示徽]**
章名稱如果選中此選項，則該徽章名稱的列將包含在排行榜中。

   預設為未勾選。

* **[!UICONTROL 顯]**
示頭像如果選中，成員的頭像影像將包含在排行榜中，位於其成員配置檔案的名稱連結旁。

   預設為未勾選。

### 頁面功能 {#page-function}

頁面函式會在社群網站中新增一個空白頁面，將其連線至社群網站的功能：登入、功能表、通知、傳訊、主題和品牌推廣。 可使用[標準AEM製作模式](../../help/sites-authoring/editing-content.md)將內容新增至頁面。

新增至範本時，唯一的設定是[標題和URL設定](#title-and-url-settings)。

### QnA 功能 {#qna-function}

QnA函式是一個具有[QnA元件](working-with-qna.md)的頁，該元件用於標籤、檔案上載、跟蹤、成員以自我編輯、投票和調節。

將新增至範本時，設定會允許限制有權限的成員：

![chlimage_1-389](assets/chlimage_1-389.png)

* 請參閱[標題和URL設定](#title-and-url-settings)
* **[!UICONTROL 允]**
許固定如果選中，論壇將允許主題回覆被固定到評論清單的開頭。已勾選預設值。

* **[!UICONTROL 允許特]**
權成員如果選中此選項，則QnA論壇將僅允許特權成員通過允許選擇特權成員組 [來發佈問題](users.md#privileged-members-group)。如果未勾選，則允許所有社群成員張貼。 預設為未勾選。

* **[!UICONTROL 允許檔]**
案上載如果選中此選項，QnA論壇將包括成員上載檔案的功能。已勾選預設值。

* **[!UICONTROL 允許線程]**
式答復如果未選中，則QnA論壇將允許對已發佈的問題提供評論（答案），但不允許對答案進行答復。已勾選預設值。

* **[!UICONTROL 允許精]**
選內容如果勾選此選項，就能將構想識別為精 [選內容](featured.md)。已勾選預設值。

## 建立社群功能 {#create-community-function}

通過選擇位於「社區功能」控制台頂部的`Create Community Function`表徵圖，可以建立社區功能。 您可以建立以相同AEM Blueprint為基礎的多個函式，然後在製作編輯模式中開啟，以唯一自訂。

![chlimage_1-390](assets/chlimage_1-390.png)

### 社群功能名稱 {#community-function-name}

![chlimage_1-391](assets/chlimage_1-391.png)

在「社區函式名稱」面板中，將配置名稱、說明以及函式是啟用還是禁用：

* **[!UICONTROL 社區函]**
式名稱用於顯示和儲存的函式名稱

* **[!UICONTROL 社區函式]**
說明顯示的功能說明

* **[!UICONTROL 禁用/啟]**
用控制函式是否可引用的切換開關

### AEM 藍圖 {#aem-blueprint}

![chlimage_1-392](assets/chlimage_1-392.png)

在`AEM Blueprint`面板上，可以選取作為社群函式基礎實作的Blueprint。

社群功能是一個微型網站，由一或多個頁面組成，預先連線以納入社群網站，包括登入、使用者設定檔、通知、傳訊、網站功能表、搜尋、貼圖和品牌功能。 建立函式後，您就可以[在作者編輯模式中開啟函式](#open-community-function)，並自訂頁面和/或元件設定。

由於社群函式被實作為[blueprint](../../help/sites-administering/msm-livecopy.md#creatingablueprint)的[即時副本](../../help/sites-administering/msm.md#live-copies)，因此可以轉出對函式所做的更改，該更改影響從[社區站點模板](sites.md)或[社區組模板](tools-groups.md)建立的所有社區站點頁，該模板包括該函式。 您也可以將頁面與其上層Blueprint取消關聯，以便進行頁面層級的修改。

另請參閱[多站點管理器](../../help/sites-administering/msm.md)。

### 縮圖 {#thumbnail}

![chlimage_1-393](assets/chlimage_1-393.png)

在「縮圖」面板上，可以上傳影像以顯示在[社群功能控制台](#community-functions-console)中。

## 開啟社群功能 {#open-community-function}

![chlimage_1-394](assets/chlimage_1-394.png)

選取`Open Community Function`圖示，以進入作者編輯模式，以編寫頁面內容及修改功能元件的設定。

### 配置元件 {#configuring-components}

社群函式以AEM Blueprint的即時副本的形式實施，其詳細資訊記錄在[Multi Site Manager](../../help/sites-administering/msm.md)下。

不僅可製作頁面內容，也可設定元件。

如果在已建立的社區站點的頁面上配置元件，則可能需要取消[繼承](../../help/sites-administering/msm-livecopy.md#changing-live-copy-content)才能配置該元件。 完成設定時，應重新建立繼承。

如需設定詳細資訊，請造訪作者的[Communities元件](author-communities.md)。

## 編輯社群功能 {#edit-community-function}

![chlimage_1-395](assets/chlimage_1-395.png)

選取`Edit Community Function`圖示，使用與[建立社群函式](#create-community-function)相同的面板來編輯函式的屬性，包括啟用或停用函式。

---
title: Communities Sites主控台
seo-title: Communities Sites主控台
description: 如何存取Communities Sites主控台
seo-description: 如何存取Communities Sites主控台
uuid: 85017055-b8af-4eeb-a8ab-1cbbba0f5a6a
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5ac2fcef-05b8-46f7-9a15-997cdd79a3db
role: Admin
exl-id: f1408709-5402-4f55-bd37-9943fe828af0
source-git-commit: 9178c3a01e7f450d3794f41605fb3788231c88c0
workflow-type: tm+mt
source-wordcount: '3237'
ht-degree: 3%

---

# Communities Sites主控台 {#communities-sites-console}

Communities Sites控制台提供對以下內容的訪問：

* 網站建立
* 網站編輯
* 網站管理
* [建立和編輯巢狀群組](groups.md) （子社群）

請參閱[AEM Communities快速入門](getting-started.md)以體驗在製作環境中建立社群網站的速度，以及如何從製作和發佈環境建立社群群組。

>[!NOTE]
>
>建立[社群網站](sites-console.md)、[社群網站範本](sites.md)、[社群群組範本](tools-groups.md)和[社群功能](functions.md)的主要社群功能表僅供作者環境使用。

## 必備條件 {#prerequisites}

建立社群網站之前，它是&#x200B;*required*&#x200B;以：

* 確認一或多個發佈執行個體執行中
* 啟用[隧道服務](deploy-communities.md#tunnel-service-on-author)以管理成員和成員組
* 識別[主要發佈者](deploy-communities.md#primary-publisher)
* [當主](deploy-communities.md#replication-agents-on-author) 發佈伺服器埠不是預設埠時配置複製(4503)

最佳實務是，為確保網站已準備好支援許多功能，請採取下列步驟：

* 安裝[最新的Feature Pack](deploy-communities.md#latestfeaturepack)
* 為AEM Communities啟用[Adobe Analytics](analytics.md)
* 配置[email](email.md)
* 確定[社區管理員](users.md#creating-community-members)
* [啟用OAuth處理](social-login.md#adobe-granite-oauth-authentication-handler) 器以進行社交登入

## 訪問Communities Sites控制台 {#accessing-communities-sites-console}

在製作環境中，若要存取Communities Sites主控台：

* 從全局導航：**[!UICONTROL Communities > Sites]**

Communities Sites控制台顯示任何現有的社區站點。 在此控制台中，可以建立、編輯、管理和刪除社區站點。

要建立新社區站點，請選擇&#x200B;**Create**&#x200B;表徵圖。

若要存取現有的社群網站，為了製作、修改、發佈、匯出或新增巢狀群組，請選取網站的資料夾圖示。

例如，下圖顯示主要的Communities Sites控制台，顯示兩個社群網站的資料夾：[enable](getting-started-enablement.md)和[engage](getting-started.md):

![chlimage_1-448](assets/chlimage_1-448.png)

## 網站建立 {#site-creation}

站點建立控制台提供了根據所選[社區站點模板](sites.md)和設定來組合站點功能的逐步方法。

所建立的每個網站都包含登入功能，因為網站訪客必須先登入，才能張貼內容、傳送訊息或參與群組。 其他包含的功能包括使用者設定檔、傳訊、通知、網站功能表、搜尋、主題和品牌推廣。

通過選擇位於Communities站點控制台頂部的`Create`按鈕來啟動該進程。

建立過程是一系列步驟，以面板的形式呈現，其中包含要配置的一組特徵（以子面板的形式呈現）。 在最後一步中提交站點之前，可以前進到&#x200B;**Next**&#x200B;步驟或&#x200B;**Back**&#x200B;到前一步。

### 步驟1:網站範本 {#step-site-template}

![newsitetemplate](assets/newsitetemplate.png)

在「網站範本」面板中，會指定「標題」、「說明」、「網站根」、「基本語言」、「名稱」和「網站範本」：

* **[!UICONTROL 社群網站標題]**:網站的顯示標題。

   標題會顯示在已發佈的網站上，以及網站管理員UI中。

* **[!UICONTROL 社群網站說明]**:網站的說明。

   說明不會出現在已發佈的網站上。

* **[!UICONTROL 社區站點根]**:網站的根路徑。

   預設根為`/content/sites`，但根可移至網站內的任何位置。

* **[!UICONTROL 社區站點基語言]**:(單一語言不受影響：英文)使用下拉式選單，從 *可用* 的語言中選擇一或多種基本語言 — 德文、義大利文、法文、日文、西班牙文、葡萄牙文（巴西）、中文（繁體）和中文（簡體）。系統會針對每個新增的語言建立一個社群網站，並依照[多語言網站轉譯內容](../../help/sites-administering/translation.md)中所述的最佳作法，存在於相同的網站資料夾中。 每個網站的根頁面都會包含一個子頁面，其名稱是所選語言之一的語言代碼，例如英文為「en」，法文為「fr」。

* **[!UICONTROL 社群網站名稱]**:顯示在URL中的網站根頁面的名稱

   * 仔細檢查名稱，因為建立網站後不易變更
   * 基本URL(`https://*server:port/site root/site name*)`)將顯示在`Community Site Name`下方
   * 為了有效的URL，請附加基本語言代碼+ &quot;。html&quot;

      *例如*、  `http://localhost:4502/content/sites/mysight/en.html`

* **[!UICONTROL 社區站點模]** 板菜單：使用下拉式功能表來選擇可用的 [社群網站範本](tools.md)。

選擇&#x200B;**[!UICONTROL Next]**

### 步驟2:設計 {#step-design}

「設計」面板包含2個子面板，用於選取主題和品牌橫幅：

#### 社群網站主題 {#community-site-theme}

![Sitetheme-1](assets/sitetheme-1.png)

架構使用`Twitter Bootstrap`為網站帶來回應式、彈性的設計。 可以選擇多個預載的Bootstrap主題之一來設定所選社區站點模板的樣式，或者可以上傳Bootstrap主題。

選取時，主題將會以不透明的藍色核取記號覆蓋。

發佈社群網站後，可以[編輯屬性](#modifying-site-properties)並選取不同的主題。

#### 社群網站品牌推廣 {#community-site-branding}

![chlimage_1-449](assets/chlimage_1-449.png)

社群網站品牌化是顯示為頁首的影像，橫跨每個頁面。

影像的大小應與瀏覽器中頁面的預期顯示大小一樣寬，高度應為120像素。

建立或選取影像時，請記住：

* 影像高度會裁切為120個像素，從影像的上邊緣測量
* 影像會固定至瀏覽器視窗的左側邊緣
* 影像沒有大小調整，因此當影像寬度為……

   * 小於瀏覽器寬度，影像會水準重複
   * 大於瀏覽器的寬度，影像就會看起來被裁切

選擇&#x200B;**[!UICONTROL Next]**。

### 步驟3:設定 {#step-settings}

「設定」面板包含數個子面板，顯示在移至建立網站的最後一個步驟之前要設定的功能。

* [使用者管理](#user-management)
* [標籤](#tagging)
* [角色](#roles)
* [協調](#moderation)
* [ANALYTICS](#analytics)
* [翻譯](#translation)
* [啟用](#enablement)

>[!NOTE]
>
>**啟用通道服務**
>
>數個「設定」子面板可指派受信任的成員來協調UGC、管理群組，或成為發佈環境中啟用資源的連絡人。
>
>此慣例適用於發佈端[使用者和使用者群組](users.md)（成員和成員群組）不會在製作環境中重複。
>
>因此，在製作環境中建立社群網站並指派受信任成員至各種角色時，必須從發佈環境中擷取成員資料。
>
>若要這麼做，請為製作環境啟用` [AEM Communities Publish Tunnel Service](deploy-communities.md#tunnel-service-on-author)`。

#### 使用者管理 {#user-management}

![createsitesettings-1](assets/createsitesettings-1.png)

>[!NOTE]
>
>建議將[啟用社群網站](overview.md#enablement-community)設為私人網站（如需詳細資訊，請連絡您的帳戶代表）。
>
>當匿名網站訪客被拒絕訪問、不能自行註冊，以及不能使用社交登錄時，社群網站是私有的。

* **[!UICONTROL 允許使用者註冊]**

   若勾選此選項，網站訪客可透過自行註冊成為社群成員。

   如果取消勾選，則社群網站為&#x200B;*restricted*，必須將網站訪客指派給社群網站的成員群組、提出要求或透過電子郵件傳送邀請。 如果取消勾選，則不允許匿名存取。

   取消選中&#x200B;*private*&#x200B;社區站點。 已勾選預設值。

* **[!UICONTROL 允許匿名存取]**

   若勾選此選項，社群網站為&#x200B;*open*，任何網站訪客都可存取該網站。

   如果未選中，則只有登錄成員才能訪問該站點。

   取消選中&#x200B;*private*&#x200B;社區站點。 已勾選預設值。

* **[!UICONTROL 允許傳訊]**

   如果選中此選項，成員可以相互發送消息，併發送到社區站點內的組。

   如果未勾選，則不會為社群設定傳訊。

   預設為未勾選。

* **[!UICONTROL 允許社交登入: Facebook]**

   若勾選此選項，允許網站訪客以其Facebook帳戶憑證登入。 選定的[Facebook雲配置](social-login.md#create-a-facebook-connect-cloud-service)應配置為在建立社區站點後將用戶添加到社區站點的成員組。

   如果未勾選，則不會顯示Facebook登入。

   對&#x200B;*private*&#x200B;社群網站保留未選中狀態。 預設為未勾選。

* **[!UICONTROL 允許社交登入: Twitter]**

   若勾選此選項，允許網站訪客以其Twitter帳戶憑證登入。 選定的[Twitter雲配置](social-login.md#create-a-twitter-connect-cloud-service)應配置為在建立社區站點後將用戶添加到社區站點的成員組。

   如果未勾選，則不會顯示Twitter登入。

   對&#x200B;*private*&#x200B;社群網站保留未選中狀態。 預設為未勾選。

>[!NOTE]
>
>**[!UICONTROL 允許社交登入]**
>
>雖然範例Facebook和Twitter設定可能存在且可供選取，但若為[生產環境](../../help/sites-administering/production-ready.md)，則需要建立自訂Facebook和Twitter應用程式。 請參閱[使用Facebook和Twitter進行社交登入](social-login.md)。

#### 標籤 {#tagging}

![chlimage_1-450](assets/chlimage_1-450.png)

可套用至社群內容的標籤，是透過選取先前透過[標籤控制台](../../help/sites-administering/tags.md#tagging-console)定義的「標籤命名空間」來控制。

此外，為社群網站選取標籤命名空間會限制定義目錄和資源時顯示的選取範圍。 如需重要資訊，請參閱[標籤啟用資源](tag-resources.md) 。

* 文本搜索框：開始鍵入以標識允許在站點上使用的標籤

#### 角色 {#roles}

![chlimage_1-451](assets/chlimage_1-451.png)

為社區成員](users.md)的[角色分配了這些設定。

使用預先輸入搜尋可輕鬆找到社群成員。

* **[!UICONTROL 社群管理員]**

   開始鍵入以選擇一個或多個社區成員或成員組，這些成員可以管理社區成員和成員組。

* **[!UICONTROL 社群版主]**

   開始鍵入以選擇一個或多個社區成員或成員組，這些成員或組將作為用戶生成內容的協調者受信任。

* **[!UICONTROL 社群有特殊權限的成員]**

   開始鍵入以選擇一個或多個社區成員或成員組，當為[社區函式](functions.md)選擇了`Allow Privileged Member`時，該成員組可以建立新內容。

#### 協調 {#moderation}

![chlimage_1-452](assets/chlimage_1-452.png)

協調使用者產生的內容(UGC)的全域設定是由這些設定所控制。 個別元件有其他可控制協調的設定。

* **[!UICONTROL 內容已預先審核]**

   如果勾選「 」，張貼的社群內容要等到協調者核准後才會顯示。 預設為未勾選。 如需詳細資訊，請參閱[調節社群內容](moderate-ugc.md#premoderation)。

* **[!UICONTROL 隱藏內容之前的標幟臨界值]**

   如果大於0，則必須標籤主題或貼文，之後才能從公開檢視中隱藏該主題或貼文的次數。 如果設為–1，則標籤的主題或貼文永遠不會在公開檢視中隱藏。 預設為5。

#### ANALYTICS {#analytics}

![chlimage_1-453](assets/chlimage_1-453.png)

* **[!UICONTROL 啟動 Analytics]**

   只有在Adobe Analytics已[針對Communities功能設定](analytics.md)時才可用。

   預設為未勾選。 勾選後，會出現其他選取功能表：

![chlimage_1-454](assets/chlimage_1-454.png)

* **[!UICONTROL 雲端設定框架引用]**

   從下拉式功能表中，選取為此社群網站設定的Analytics雲端服務架構。

   `Communities`是Analytics Configuration for Communities [功能檔案的架](analytics.md#aem-analytics-framework-configuration) 構範例。

#### 翻譯 {#translation}

![chlimage_1-455](assets/chlimage_1-455.png)

* **[!UICONTROL 允許機]**
器翻譯選中此選項（預設為未選中）後，將為站點內的UGC啟用機器翻譯。這不會影響任何其他內容，例如頁面內容，即使網站設定為多語言網站亦然。 有關為AEM Communities配置授權翻譯服務的資訊，請參閱[轉譯用戶生成的內容](translate-ugc.md)。 如需完整概覽，請參閱[多語言網站的轉譯內容](../../help/sites-administering/translation.md) 。

![chlimage_1-456](assets/chlimage_1-456.png)

* **[!UICONTROL 為選取的語言啟用機器翻譯]**

   為機器翻譯啟用的語言預設為[翻譯整合配置](translate-ugc.md#translation-integration-configuration)指定的系統設定。 通過刪除預設值和/或從下拉菜單中選擇其他語言，可以覆蓋此站點的這些預設設定。

* **[!UICONTROL 選擇翻譯提供者]**

   預設情況下，服務提供商是試用服務，僅用於演示。 `microsoft`如果未授權翻譯服務提供商，則應取消選中「允許機器翻譯」**。**

* **[!UICONTROL 選擇全域共用存放區]**

   對於具有多個語言副本的網站，全域共用存放區會提供單一對話執行緒，可從每個語言副本中看到。 這是通過選擇其中一種語言作為語言副本來實現的。 預設值為&#x200B;*無全局共用儲存*。

* **[!UICONTROL 選擇翻譯提供者設定]**

   選擇為許可翻譯提供程式建立的[翻譯整合框架](../../help/sites-administering/tc-tic.md)。

* **選取您社群網站的翻譯選項**

   * **[!UICONTROL 翻譯整個頁面]**

      如果選取，則頁面上的所有UGC都會翻譯成頁面的基本語言。

      預設值為&#x200B;*未選擇*。

   * **[!UICONTROL 只翻譯選取項目]**

      如果選取「 」，則每個貼文旁會出現一個翻譯選項，允許將個別貼文翻譯成頁面的基本語言。

      預設值為&#x200B;*selected*。

* **選取保留選項**

   * **[!UICONTROL 翻譯使用者要求上的貢獻並於之後繼續保留]**

      如果選取此選項，則在提出要求前，內容不會翻譯。 翻譯後，翻譯會儲存在存放庫中。

      預設值為&#x200B;*未選擇*。

   * **[!UICONTROL 不保留翻譯]**

      如果選中，翻譯不會儲存在儲存庫中。

      如果未選取，則會保存翻譯。

      預設值為&#x200B;*未選擇*。

* **[!UICONTROL 智慧]**
渲染選擇

   * `Always show contributions in the original language` (預設)
   * `Always show contributions in user preferred language`
   * `Show contributions in user preferred language for only logged-in users`

#### 啟用 {#enablement}

![chlimage_1-457](assets/chlimage_1-457.png)

當選擇的社區站點模板包含[賦值函式](functions.md#assignments-function)時，`ENABLEMENT`設定適用，該函式在授權功能時可用，[已配置](enablement.md)。 包含分配函式的參考站點模板為`Reference Structured Learning Site Template.`

* **[!UICONTROL 啟用管理員]**

   （必要）僅可選擇`Community Enablementmanagers`組的成員以管理此啟用社區。 啟用管理員負責將成員指派給資源。 另請參閱[管理使用者和使用者群組](users.md)。

* **[!UICONTROL Marketing Cloud 組織 ID]**

   （選用）[視訊心率Analytics](analytics.md#video-heartbeat-analytics)授權的ID。

選擇&#x200B;**[!UICONTROL Next]**。

### 步驟4:建立社區網站 {#step-create-communities-site}

如果需要任何調整，請使用&#x200B;**Back**&#x200B;按鈕進行調整。

一旦選取並啟動&#x200B;**Create**，建立網站的程式就無法中斷。

建立網站後：

* 不支援變更url（節點名稱）
* 未來對社群網站範本所做的變更不會影響已建立的社群網站
* 禁用社區站點模板不會影響已建立的社區站點
* 可以通過修改社區站點的屬性來編輯其[STRUCTURE](#modify-structure)

![chlimage_1-458](assets/chlimage_1-458.png)

過程完成後，新站點的資料夾將顯示在Communities Sites控制台中，供作者添加頁面內容或管理員修改站點的屬性。

![chlimage_1-459](assets/chlimage_1-459.png)

要修改社區站點，請選擇其項目資料夾以開啟它：

![Siteactions-2](assets/siteactions-2.png)

使用滑鼠暫留在網站上，或觸碰網站卡片時，會出現圖示，允許以作者模式](#authoring-site-content)、[開啟網站屬性以進行修改](#modifying-site-properties)、[發佈網站](#publishing-the-site)、[匯出網站](#exporting-the-site)和[刪除網站](#deleting-the-site)。[

## 製作網站內容 {#authoring-site-content}

![chlimage_1-460](assets/chlimage_1-460.png)

網站的內容可使用與任何其他AEM網站相同的工具製作。 若要開啟網站進行製作，請選取滑鼠游標暫留網站時顯示的`Open Site`圖示。 該站點將在新頁簽中開啟，以便Communities Sites控制台仍可訪問。

![chlimage_1-461](assets/chlimage_1-461.png)

>[!NOTE]
>
>若不熟悉AEM，請檢視[basic handling](../../help/sites-authoring/basic-handling.md)和[製作頁面快速指南](../../help/sites-authoring/qg-page-authoring.md)的相關檔案。

## 修改網站屬性 {#modifying-site-properties}

![chlimage_1-462](assets/chlimage_1-462.png)

在網站建立過程中指定的現有網站屬性，可通過選擇`Edit Site`表徵圖來修改，該表徵圖顯示在滑鼠懸停的站點上。

`Details of the following properties match the descriptions provided in the` [網站](#site-creation) 建立區段。

![chlimage_1-463](assets/chlimage_1-463.png)

### 修改基本 {#modify-basic}

BASIC面板允許修改

* 社群網站標題
* 社群網站說明

不能修改社區站點名稱。

選擇不同的社區站點模板對現有的社區站點沒有影響，因為模板和站點之間沒有連接。

相反，可以修改社區站點的[STRUCTURE](#modify-structure)。

### 修改結構 {#modify-structure}

「結構」面板允許修改最初從所選社區站點模板建立的結構。 從面板，您可以

* 將其他[社群函式](functions.md)拖放至網站結構中
* 在網站結構中的社群函式例項上：

   * **`gear icon`**

      編輯設定，包括顯示標題和URL名稱&amp;ast;

      以及[特權成員組](users.md#privilegedmembersgroups)

   * **`trashcan icon`**

      從站點結構中刪除（刪除）函式

   * **`grid icon`**

      修改網站頂層導覽列中顯示的函式順序

>[!NOTE]
>
>您可以變更「網站結構」中除頂端函式外所有函式的順序。 因此，無法變更社群網站的首頁。

>[!CAUTION]
>
>雖然顯示標題可以不產生副作用而變更，但不建議編輯屬於社群網站之社群函式的URL名稱。
>
>例如，重新命名URL不會移動現有的UGC，因此會產生「遺失」UGC的效果。

>[!CAUTION]
>
>群組函式必須&#x200B;*不*&#x200B;是站點結構中的&#x200B;*第一個或唯一的*&#x200B;函式。
>
>必須先包含並列出任何其他函式，例如[page函式](functions.md#page-function)。

#### 範例：將目錄函式添加到社區站點結構 {#example-adding-a-catalog-function-to-a-community-site-structure}

![chlimage_1-464](assets/chlimage_1-464.png)

### 修改設計 {#modify-design}

「設計」面板允許應用新主題：

* [社群網站主題](#community-site-theme)
* [社群網站品牌](#community-site-branding)
   * 捲動至面板底部以變更品牌影像

### 修改設定 {#modify-settings}

「設定」面板可讓您存取社群網站建立步驟3之子面板下的大部分設定：

* [使用者管理](#user-management)
* [標記](#tagging)
* [審核](#moderation)
* [會員角色](#roles)
* [分析](#analytics)
* [轉換](#translation)

### 修改縮圖 {#modify-thumbnail}

「縮圖」面板允許上傳影像以在Communities Sites控制台中表示站點。

### 修改啟用 {#modify-enablement}

「啟用」面板可讓您存取建立社群網站期間提供的設定。

請參閱[啟用](#enablement)說明。

## 發佈網站 {#publishing-the-site}

在新建立或修改社群網站後，您可以選取`Publish Site`圖示來發佈（啟動）網站，此圖示會顯示在將滑鼠游標暫留在網站上。

![chlimage_1-465](assets/chlimage_1-465.png)

網站成功發佈後，會出現指示。

![chlimage_1-466](assets/chlimage_1-466.png)

### 使用巢狀群組發佈 {#publishing-with-nested-groups}

發佈社群網站後，必須個別發佈使用[群組主控台](groups.md)建立的每個子社群（巢狀群組）。

## 匯出網站 {#exporting-the-site}

![chlimage_1-467](assets/chlimage_1-467.png)

選取將滑鼠游標暫留在網站上的匯出圖示，以建立同時儲存在[套件管理器](../../help/sites-administering/package-manager.md)中和下載的社群網站套件。\
請注意，網站套件中未包含UGC。

## 刪除網站 {#deleting-the-site}

![deleteicon-1](assets/deleteicon-1.png)

要刪除社區站點，請選擇「社區站點控制台」中滑鼠懸停在站點上時顯示的「刪除站點」表徵圖。 此動作會移除與網站相關聯的所有項目，例如UGC、使用者群組、資產和資料庫記錄。

## 建立的社區用戶組 {#created-community-user-groups}

發佈新社群網站後，新成員群組（在發佈環境中建立使用者群組）會對各種管理和成員角色設定適當的權限。

為成員組建立的名稱包括&#x200B;*站點名稱*，該名稱在[步驟1](#step13asitetemplate)中指定站點（在URL中顯示的名稱），以及唯一ID，以避免與社區站點和組發生衝突，這些站點和組具有不同的社區站點名稱。

例如，如果標題為「快速入門教學課程」的網站名稱為「參與」，則協調者的使用者群組會是：

* 標題：社群參與協調者
* 名稱：community-*engage-uid*-moderator

請注意，在建立網站時，任何成員都會將角色指派為協調者或群組管理員，並指派給適當的群組以及成員群組。 這些組和成員分配是在發佈新站點時在發佈時建立的。

如需詳細資訊，請參閱[管理使用者和使用者群組](users.md)。

>[!NOTE]
>
>如果[允許社交登入：Facebook](#user-management)啟用後，使用者群組即會啟用
>
>* community-*&lt;site-name>*-*&lt;uid>*&#x200B;成員

已建立，則應將套用的[Facebook雲端服務](social-login.md#createafacebookcloudservice)設定為將使用者新增至此群組。

## 配置身份驗證錯誤 {#configure-for-authentication-error}

依預設，當使用者輸入錯誤的憑證且無法登入時，社群網站會重新導向至範例登入頁面。 此示例登錄名將不存在於[生產伺服器](../../help/sites-administering/production-ready.md)上。

若要正確重新導向，當網站經設定並推送至發佈後，請完成下列步驟以取得驗證失敗，而無法重新導向至社群網站：

* 在每個AEM發佈例項上
* 首先使用管理員權限登錄
* 訪問[Web控制台](../../help/sites-deploying/configuring-osgi.md)
   * 例如， [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* 找到`Adobe Granite Login Selector Authentication Handler`
* 選擇`pencil`表徵圖以開啟要編輯的配置
* 輸入&#x200B;**[!UICONTROL 登錄頁映射]**，如下所示：

   `/content/sites/<site-name>/path/to/login/page:/content/sites/<site-name>`

   例如：

   `/content/sites/engage/en/signin:/content/sites/engage/en`

* 選擇&#x200B;**[!UICONTROL 保存]**

![chlimage_1-468](assets/chlimage_1-468.png)

### 測試驗證重定向 {#test-authentication-redirection}

在相同的AEM發佈執行個體上，使用社群網站的登入頁面對應進行設定：

* 瀏覽到社區站點首頁
   * 例如， [http://localhost:4503/content/sites/engage/en.html](http://localhost:4503/content/sites/engage/en.html)

* 選擇註銷
* 選擇登錄
* 輸入明顯不正確的憑據，例如用戶名&quot;x&quot;和密碼&quot;x&quot;
* 登入頁面應顯示「無效登入」錯誤

![chlimage_1-469](assets/chlimage_1-469.png)

## 從主站點控制台訪問社區站點 {#accessing-community-sites-from-main-sites-console}

從全局導航站點控制台，社區站點位於`Community Sites`資料夾中。

雖然可以以此方式訪問社區站點，但對於管理任務，應從社區站點控制台訪問社區站點。

![chlimage_1-470](assets/chlimage_1-470.png)

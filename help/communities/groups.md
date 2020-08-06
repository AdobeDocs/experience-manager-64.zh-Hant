---
title: 社群群組主控台
seo-title: 社群群組主控台
description: 群組主控台可讓您建立社群群組
seo-description: 群組主控台可讓您建立社群群組
uuid: 7dac2d1b-78fc-4b39-a2cb-100f1e220c23
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 1293c01a-7308-494a-ab48-bd9938205b81
pagetitle: Community Groups Console
translation-type: tm+mt
source-git-commit: 28948f1f8678512f8fc970a4289cb01cde86c5c2
workflow-type: tm+mt
source-wordcount: '1642'
ht-degree: 1%

---


# 社群群組主控台 {#community-groups-console}

當社群網站的範本結構包含群組功能時，「群組」控制台 [可讓您存](sites-console.md#step1) 取建 [立社群群組](functions.md#groups-function)。

* 群組可以巢狀內嵌在其他群組中。 當新群組的 [結構包含群組函式時](tools-groups.md) ，就會發生此情況。
* 僅對於作者環境，有一個與站點建立嚮導類似的組建立嚮導。
* 將「群組」功能新增至社群網站結構或社群群組結構時，成員是否可從發佈環境建立群組是可設定的。

在包含的三個組模板中，只有模 `Reference Group` 板在其結構中包含組函式。

社群群群組的幾個方面包括：

* 建立： 可在作者上建立新群組，也可在發佈時選擇性建立新群組
* 控制： 群組可能是開放或機密
* 巢狀： 組可能包含零個或多個組

>[!NOTE]
>
>在「社群群組」主控台存在之前 [在發佈環境中建立的社群群組](https://helpx.adobe.com/in/experience-manager/6-3/communities/using/version-history.html#FeaturePack1FP1)，不會列在「社群群組」主控台中，因此無法使用主控台來修改。

>[!NOTE]
>
>此組控制台僅能從Communities Sites控制台訪問，不要與管理成員組的成員 [組控制台](members.md) 混淆。
>
>成員組是在發佈環境中註冊的用戶組，可通過隧道服務從作者環境 [訪問](deploy-communities.md#tunnel-service-on-author)。

## 群組建立 {#group-creation}

要訪問組控制台：

* 在作者上，以管理員權限登入
* 從全域導覽： **[!UICONTROL 社群>網站]**
* 選擇現有的社群站點資料夾以將其開啟
* 在資料夾中選擇社區站點的實例

   * 社群網站的結構必須包含群組功能
   * 在發佈時建立群組後，這些螢幕擷取畫面來自「快速入 [門」教學課程](published-site.md)

![chlimage_1-133](assets/chlimage_1-133.png)

選擇「 **[!UICONTROL Groups」（組）資料夾]** ，將其開啟。

開啟時，會顯示所有現有群組，不論是在作者或發佈上建立。

在此「群組」主控台中，可以編寫新群組。

![chlimage_1-134](assets/chlimage_1-134.png)

* 「選擇 **[!UICONTROL 建立組]** 」按鈕

### 步驟1: 社群群組範本 {#step-community-group-template}

![多語言群](assets/multilingualgroup.png)

* **[!UICONTROL 社群群組標題]**: 群組的顯示標題。

   標題會顯示在群組的發佈網站上。

* **[!UICONTROL 社群群組說明]**: 群組的說明。
* **[!UICONTROL 社群群組根]**: 群組的根路徑。

   預設根目錄是父網站，但根目錄可移至網站內的任何位置。 建議不要變更它。

* **[!UICONTROL 其他可用的社群群組語言功能表]** : 使用下拉式功能表來選取可用的社群群組語言。 功能表會顯示建立父社群網站的所有語言。 使用者可在這些語言中選擇，以在此單一步驟中建立多個地區設定的群組。 在相應社群網站的「群組」主控台中，以多種指定語言建立相同的群組。

* **[!UICONTROL 社群群組名稱]**: 顯示在URL中的群組根頁面名稱

   * 重複檢查名稱，因為在建立群組後不易變更
   * 基本URL將顯示在 `Community Group Name`
   * 若為有效的URL，請附加&quot;。html&quot;

      *例如*, `http://localhost:4502/content/sites/mysight/en/mygroup.html`

* **[!UICONTROL 社群群組範本功能表]** : 使用下拉式功能表選擇可用的 [社群群組範本](tools.md)。

### 步驟2: 設計 {#step-design}

#### COMMUNITY GROUP THEME {#community-group-theme}

![社群群體主題](assets/communitygrouptheme.png)

此架構使 [用Twitter引導](https://twitterbootstrap.org/) ，為網站提供回應式、有彈性的設計。 可以選擇多個預載入的引導主題之一來設定所選社區組模板的樣式，或者可以上載引導主題。

選取後，主題將會以不透明的藍色核取標籤覆蓋。

您可以選取與父網站主題不同的主題。

社群網站發佈後，您可以編輯 [屬性](#modifying-group-properties) ，並選取不同的主題。

#### COMMUNITY GROUP BRANDING {#community-group-branding}

![chlimage_1-135](assets/chlimage_1-135.png)

社群網站品牌是顯示為每個頁面上方標題的影像。 可顯示不同於其他網站頁面之群組的橫幅。

影像的大小應與預期的頁面在瀏覽器中顯示的大小相同，高度應為120像素。

建立或選取影像時，請記住：

* 影像高度會裁切為120像素，從影像的上邊緣測量
* 影像會固定在瀏覽器視窗的左邊緣
* 影像沒有調整大小，因此當影像寬度為……

   * 小於瀏覽器寬度，影像將會水準重複
   * 大於瀏覽器寬度時，影像會看起來會遭到裁切

### 步驟3: 設定 {#step-settings}

#### MODERATION {#moderation}

![chlimage_1-136](assets/chlimage_1-136.png)

依預設，會繼承父社群網站的協調者清單。

您可以新增群組專屬的協調者：

* 搜尋成員（從發佈環境）以新增成員為協調者

#### MEMBERSHIP {#membership}

成員資格設定允許選擇三種保護社區組的方法之一。

![chlimage_1-137](assets/chlimage_1-137.png)

* 可選成員資格

   如果選中此選項，則社區組是公共組。 網站成員可參與群組，並在未明確加入群組的情況下張貼。 已選取預設值。
* 必要的成員資格

   如果選取此選項，則社群群群組為開啟的群組。 社群網站成員可以檢視群組的內容，但必須先加入群組，才能張貼內容。 成員通過選擇發佈環 `Join` 境中的按鈕加入。 未選擇預設值。

* 限制的成員資格

   如果選中，則社群組是機密組。 必須明確邀請社群成員。 已邀請的成員將輸入到搜索框中。 以後可以使用作者環境的「成 [員」和「組」控制台](members.md) ，添加成員。 未選擇預設值。

#### 縮圖 {#thumbnail}

![chlimage_1-138](assets/chlimage_1-138.png)

縮圖是要在作者和發佈時針對群組顯示的影像。

群組影像的最佳大小為170 x 90像素，且支援的影像格式為（例如JPG或PNG）。

如果未新增影像，則會顯示預設影像。

![chlimage_1-139](assets/chlimage_1-139.png)

### 步驟4: 建立群組 {#step-create-group}

![chlimage_1-140](assets/chlimage_1-140.png)

如果需要調整，請使用「上 **一步** 」按鈕進行調整。

一旦選 **取並啟動** 「建立」後，建立群組的程式便無法中斷。

當程式完成時，新子社群網站（群組）的資訊卡會顯示在「社群網站群組」主控台中，供作者新增頁面內容或管理員修改網站屬性。

![createcommunitygroup-1](assets/createcommunitygroup-1.png)

>[!NOTE]
>
>群組會以所有語言建立，如步驟1所 [指定： 社群群組範本](groups.md#step1communitygrouptemplate) ，位於各社群網站的社群群組主控台中，以其他可用社群群組語言提供。

## 編寫群組內容 {#authoring-group-content}

![chlimage_1-141](assets/chlimage_1-141.png)

群組的頁面內容可能與任何其他AEM頁面使用相同的工具撰寫。 若要開啟群組以進行製作，請選取將滑鼠指標暫留在群組卡片上時顯示的「開啟網站」圖示。

## 修改組屬性 {#modifying-group-properties}

在社群群組建立程式中指定的現有子社群網站屬性，可以透過選取將滑鼠指標暫留在群組卡片上時顯示的「編輯網站」圖示來修改：

![chlimage_1-142](assets/chlimage_1-142.png)

下列屬性的詳細資料與「群組建立」區段中提供的 [說明相符](#group-creation) 。 無論是在發佈環境或作者環境中建立，任何巢狀群組皆可加以修改。

![chlimage_1-143](assets/chlimage_1-143.png)

### 修改基本 {#modify-basic}

BASIC面板允許修改

* 社群群組標題
* 社群群組說明

不得修改社群群組名稱。

選擇不同的社群群組範本對現有社群群組網站不會有任何影響，因為範本和網站之間沒有任何連接。

可以改 [變子社區](#modify-structure) 的STRUCTURE。

### 修改結構 {#modify-structure}

STRUCTURE面板允許修改最初從作者或發佈環境建立子社區站點時選定的社區組模板建立的結構。 從面板，您可以

* 將其他社群功能拖放 [至網站結](functions.md) 構中
* 在網站結構中的社群功能例項上：

   * **`gear icon`**

      編輯設定，包括顯示標題和URL名稱，以及特權 [成員群組](users.md#privilegedmembersgroups)

   * **`trashcan icon`**

      從網站結構移除（刪除）函式

   * **`grid icon`**

      修改網站頂層導覽列中顯示的功能順序

>[!CAUTION]
>
>雖然顯示標題可以不產生副作用而變更，但不建議編輯屬於社群網站之社群函式的URL名稱。
>
>例如，重新命名URL不會移動現有的UGC，因此會產生「遺失」UGC的效果。

>[!CAUTION]
>
>群組函式不 *能是**網站結構中的* 第一個函式，也不能是唯一函式。
>
>任何其他函式(例如頁 [面函式](functions.md#page-function))必須先包含並列出。

#### 範例： 將日曆函式添加到子社區（組）結構 {#example-adding-a-calendar-function-to-a-sub-community-group-structure}

![chlimage_1-144](assets/chlimage_1-144.png)

### 修改設計 {#modify-design}

DESIGN面板允許修改主題：

* [社群群組主題](#community-group-theme)
* [社群群組品牌](#community-group-branding)

   * 捲動至面板底部以變更品牌影像

### 修改設定 {#modify-settings}

「設定」面板可讓您新增社群協調 [者](#moderation)。

### 修改會籍 {#modify-membership}

「 [MEMBERSHIP](#membership) 」面板僅供參考。 無論是選用、必要或受限制，都無法變更已建立的群組成員資格類型。

### 修改縮圖 {#modify-thumbnail}

THUMBNAIL [(縮圖](#thumbnail) )面板允許上傳影像，以在發佈環境以及作者環境的「社群網站」的「群組」主控台中，將社群群組呈現給網站訪客。

## 發佈群組 {#publishing-the-group}

![chlimage_1-145](assets/chlimage_1-145.png)

在新建立或修改社群群組後，您可以選取圖示來發佈（啟用）群 `Publish Site` 組。

成功發佈群組後，會出現訊息：

![chlimage_1-146](assets/chlimage_1-146.png)

>[!CAUTION]
>
>父社區站點和父組應已發佈。
>
>社群網站和巢狀群組應以自上而下的方式發佈。

## 刪除群組 {#deleting-the-group}

![deleteicon](assets/deleteicon.png)

從社群群組主控台中刪除群組，方法是選取「刪除群組」圖示，此圖示會顯示在將滑鼠暫留在群組上。

這會移除與群組相關的所有項目，例如永久刪除群組的所有內容，並從系統中移除使用者成員資格。

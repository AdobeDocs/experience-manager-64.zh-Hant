---
title: 編寫巢狀群組
seo-title: Authoring Nested Groups
description: 建立巢狀群組
seo-description: Create nested groups
uuid: b478454a-24c6-4e1c-a6e0-afeb1bc4992c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 955a1876-4882-4926-82e9-846bc8bb332c
exl-id: 87be7ffe-d937-4e85-8d90-5b7c356f0876
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 4%

---

# 編寫巢狀群組 {#authoring-nested-groups}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 在作者上建立群組 {#creating-groups-on-author}

在作者上，從全域導覽

* 選擇 **[!UICONTROL 社群>網站]**
* 選擇 **[!UICONTROL 參與資料夾]** 開啟
* 選取 **[!UICONTROL 快速入門教學課程]**  英文網站
   * 選取卡片影像
   * 做 *not* 選取圖示

結果會是到達 [群組主控台](groups.md):

![chlimage_1-53](assets/chlimage_1-53.png)

群組函式會顯示為資料夾，其中會建立群組的例項。 選擇「組」資料夾以開啟它。 在發佈時建立的群組可見。

![chlimage_1-54](assets/chlimage_1-54.png)

## 建立主要藝術群組 {#create-main-arts-group}

可以建立此組，因為參與的站點結構包括組功能。 網站的 `Reference Template` 預設值為允許選擇任何已啟用的組模板。 因此，為此新群組選擇的範本為 `Reference Group`.

這些主控台與Communities Sites主控台非常類似。

* 選擇 **[!UICONTROL 建立群組]**
* `1 Community Group Template`:
   * 社群群組標題：藝術
   * 社區組描述：不同藝術團體的父團體。
   * 社區組根： *保留為預設值*
   * 其他可用的社區組語言：使用下拉菜單選擇可用的社區組語言。 功能表會顯示建立父社群網站的所有語言。 使用者可在這些語言中選取，以在這個單一步驟中建立多個地區設定中的群組。 系統會在個別社群網站的群組控制台中，以多種指定語言建立相同的群組。
   * 社區組名稱：藝術
   * 範本：下拉式選取 `Reference Group`
   * 選取 `Next`

      ![parenttonestedgroup](assets/parenttonestedgroup.png)

繼續使用下列設定瀏覽其他面板：

* **2設計**
   * 您可以變更設計或允許預設為父網站的設計
   * 選擇 **[!UICONTROL 下一個]**
* **3設定**
   * **審核**
      * 保留為空（繼承自父站點）
   * **成員資格**
      * 使用預設值 `Optional Membership`
   * **縮圖**
      * `optional`
   * 選取 `Next`
* 選擇 **[!UICONTROL 建立]**

### 藝術組中的嵌套組 {#nesting-groups-within-arts-group}

此 `groups` 資料夾現在應包含兩個群組（可能需要重新整理頁面）。

![createcommunitygroup](assets/createcommunitygroup.png)

#### 發佈群組 {#publish-group}

在內建立巢狀群組之前 `arts`群組，暫留在 `arts` 卡片並選取「發佈」圖示以發佈。

![chlimage_1-55](assets/chlimage_1-55.png)

等待群組已發佈的確認。

![chlimage_1-56](assets/chlimage_1-56.png)

此 `arts` 群組也應包含 `groups` ，但空白且可建立新群組的資料夾。 導覽至藝術群組資料夾，並建立3個巢狀群組，每個群組具有不同的成員資格設定：

1. 視覺
   * 標題: `Visual Arts`
   * 名稱: `visual`
   * 範本: `Reference Group`
   * 會籍：選取 `Optional Membership`
公開群組，開放給所有成員
1. 聽覺
   * 標題: `Auditory Arts`
   * 名稱: `auditory`
   * 範本: `Reference Group`
   * 會籍：選取 `Required Membership`
一個開放的組，可供成員加入

1. 歷史

   * 標題: `Art History`
   * 名稱: `history`
   * 範本: `Reference Group`
   * 會籍：選取 `Restricted Membership`
秘密組（僅對受邀成員可見，例如，邀請） 
[示範使用者](tutorials.md#demo-users) `emily.andrews@mailinator.com`

重新整理頁面以查看所有三個巢狀群組（子社群）。

如有必要，請從Communities Sites控制台導覽至巢狀群組：

* 選擇 **[!UICONTROL 參與資料夾]**
* 選擇 **[!UICONTROL 快速入門教學課程]** 卡片
* 選擇 **[!UICONTROL 群組資料夾]**
* 選擇 **[!UICONTROL 藝術卡]**
* 選擇 **[!UICONTROL 群組資料夾]**

![chlimage_1-57](assets/chlimage_1-57.png)

## 發佈群組 {#publishing-groups}

![chlimage_1-58](assets/chlimage_1-58.png)

發佈主要社群網站後，必須

* 個別發佈每個群組
   * 等待群組已發佈的確認
* 發佈內嵌的任何群組之前先發佈父群組
   * 所有群組都必須以由上而下的方式發佈。

![chlimage_1-59](assets/chlimage_1-59.png)

## 發佈體驗 {#experience-on-publish}

登入時(例如使用 [示範使用者](tutorials.md#demo-users) 用於

* 藝術/歷史組成員：emily.andrews@mailinator.com
   * 受限（秘密）組，藝術/歷史，將可見
   * 可以看到選用（公開）群組
   * 可以加入受限制（開啟）組
* 群組管理員：aaron.mcdonald@mailinator.com
   * 可以看到選用（公開）群組
   * 可以加入受限制（開啟）組
   * 不會看到受限（秘密）群組

訪問社區 [成員和組控制台](members.md) 在作者上，將其他使用者新增至與社群群組相對應的各種成員群組。

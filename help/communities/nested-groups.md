---
title: 編寫巢狀群組
seo-title: 編寫巢狀群組
description: 建立巢狀群組
seo-description: 建立巢狀群組
uuid: b478454a-24c6-4e1c-a6e0-afeb1bc4992c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 955a1876-4882-4926-82e9-846bc8bb332c
translation-type: tm+mt
source-git-commit: 2d1e39120d79de029927011d48f7397b53ad91bc
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 2%

---


# 編寫巢狀群組{#authoring-nested-groups}

## 在作者上建立組{#creating-groups-on-author}

在作者上，從全域導覽

* 選擇&#x200B;**[!UICONTROL 社區>站點]**
* 選擇&#x200B;**[!UICONTROL engage資料夾]**&#x200B;將其開啟
* 選擇&#x200B;**[!UICONTROL Getting Started Tutorial]**&#x200B;英文網站的資訊卡
   * 選取卡片影像
   * 選擇表徵圖&#x200B;**

結果是到達[組控制台](groups.md) :

![chlimage_1-53](assets/chlimage_1-53.png)

群組函式將顯示為建立群組例項的資料夾。 選擇「群組」檔案夾以開啟它。 在發佈時建立的群組可見。

![chlimage_1-54](assets/chlimage_1-54.png)

## 建立主要藝術群組{#create-main-arts-group}

可以建立此組，因為參與的站點結構包括組功能。 站點`Reference Template`中函式的配置預設為允許選擇任何已啟用的組模板。 因此，為此新組選擇的模板將是`Reference Group`。

這些控制台與Communities Sites控制台非常相似。

* 選擇&#x200B;**[!UICONTROL 建立組]**
* `1 Community Group Template`:
   * 社群群組標題：藝術
   * 社群群組說明：不同藝術團體的父項團體。
   * 社群群組根：*leave as default*
   * 其他可用社群群組語言：使用下拉式功能表來選取可用的社群群組語言。 功能表會顯示建立父社群網站的所有語言。 使用者可在這些語言中選擇，以在此單一步驟中建立多個地區設定的群組。 在相應社群網站的「群組」主控台中，以多種指定語言建立相同的群組。
   * 社群群組名稱：藝術
   * 範本：下拉式選擇`Reference Group`
   * 選取 `Next`

      ![parentttentedgroup](assets/parenttonestedgroup.png)

使用下列設定，繼續檢視其他面板：

* **2設計**
   * 您可以變更設計或允許預設為父網站的設計
   * 選擇&#x200B;**[!UICONTROL Next]**
* **3設定**
   * **審核**
      * 留空（繼承父站點）
   * **成員資格**
      * 使用預設值`Optional Membership`
   * **縮圖**
      * `optional`
   * 選取 `Next`
* 選擇&#x200B;**[!UICONTROL 建立]**

### Arts Group {#nesting-groups-within-arts-group}中的巢狀群組

`groups`資料夾現在應包含兩個群組（可能需要重新整理頁面）。

![createcommunitygroup](assets/createcommunitygroup.png)

#### 發佈群組 {#publish-group}

在建立巢狀內嵌於`arts`群組中的群組之前，請將滑鼠指標暫留在`arts`卡片上，並選取發佈圖示來發佈。

![chlimage_1-55](assets/chlimage_1-55.png)

等候確認群組已發佈。

![chlimage_1-56](assets/chlimage_1-56.png)

`arts`群組也應包含`groups`資料夾，但是其中一個資料夾是空的，可在其中建立新群組。 導覽至藝術群組資料夾並建立3個巢狀群組，每個群組具有不同的成員資格設定：

1. 視覺化
   * 標題: `Visual Arts`
   * 名稱: `visual`
   * 範本: `Reference Group`
   * 會籍：選擇`Optional Membership`
公開群組，對所有成員開放
1. 聽覺
   * 標題: `Auditory Arts`
   * 名稱: `auditory`
   * 範本: `Reference Group`
   * 會籍：選擇`Required Membership`
開放群組，可供成員加入

1. 歷史

   * 標題: `Art History`
   * 名稱: `history`
   * 範本: `Reference Group`
   * 會籍：選擇`Restricted Membership`
僅對受邀成員可見的機密群組（例如，邀請） 
[示範使用者](tutorials.md#demo-users) `emily.andrews@mailinator.com`

重新整理頁面，查看所有三個巢狀群組（子社群）。

如有必要，請從「社群站點」控制台導航到嵌套組：

* 選擇&#x200B;**[!UICONTROL engage資料夾]**
* 選擇&#x200B;**[!UICONTROL 快速入門教程]**&#x200B;卡
* 選擇&#x200B;**[!UICONTROL Groups資料夾]**
* 選擇&#x200B;**[!UICONTROL arts card]**
* 選擇&#x200B;**[!UICONTROL Groups資料夾]**

![chlimage_1-57](assets/chlimage_1-57.png)

## 發佈群組{#publishing-groups}

![chlimage_1-58](assets/chlimage_1-58.png)

發佈主社群網站後，必須

* 個別發佈每個群組
   * 等候確認群組已發佈
* 發佈內嵌的任何群組前，先發佈父群組
   * 所有群組都必須以自上而下的方式發佈。

![chlimage_1-59](assets/chlimage_1-59.png)

## 發佈體驗{#experience-on-publish}

登入時，可能會體驗不同的群組，例如與[demo使用者](tutorials.md#demo-users)一起登入

* 圖稿／歷史記錄組成員：emily.andrews@mailinator.com/密碼
   * 受限制的（機密）群組（藝術／歷史）將可見
   * 可以看到可選（公開）群組
   * 可以加入受限制（開啟）的群組
* 群組管理員：aaron.mcdonald@mailinator.com/密碼
   * 可以看到可選（公開）群組
   * 可以加入受限制（開啟）的群組
   * 將看不到受限制的（秘密）組

訪問作者上的「社區[成員和組」控制台](members.md) ，以將其他用戶添加到與社區組相對應的各種成員組。

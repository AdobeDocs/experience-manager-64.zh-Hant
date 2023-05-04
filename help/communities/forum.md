---
title: 論壇功能
seo-title: Forum Feature
description: 如何新增和設定論壇功能
seo-description: How to add and configure the forum feature
uuid: ced860ef-6f8a-4df2-acc8-6a48140fca83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3495f983-d71e-4704-be4e-8a42a63f72db
exl-id: fa6f28b4-3217-4b6a-b223-506da0ecca9e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1082'
ht-degree: 0%

---

# 論壇功能 {#forum-feature}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 簡介 {#introduction}

論壇功能提供發佈環境中登入網站訪客（社群成員）的區域，以執行下列作業：

* 建立新主題
* 檢視和回覆主題
* 關注主題
* 搜尋論壇
* 協助協調論壇內容
* 將論壇主題從一個頁面移至另一個頁面

本檔案的本節說明

* 將論壇功能新增至AEM網站
* 的組態設定 `Forum`元件

## 將論壇新增至頁面 {#adding-a-forum-to-a-page}

新增 `Forum` 在製作模式中，使用元件瀏覽器來尋找

* `Communities / Forum`

並將其拖曳至應該出現論壇的頁面上。

如需必要資訊，請造訪 [Communities元件基本知識](basics.md).

當 [必要的用戶端程式庫](essentials-forum.md#essentials-for-client-side) 包含在內，以下為方式 `Forum`元件隨即出現：

![chlimage_1-60](assets/chlimage_1-60.png)

## 設定論壇 {#configuring-a-forum}

選取已放置的 `Forum` 要存取的元件並選取 `Configure` 表徵圖，開啟「編輯」對話框。

![chlimage_1-61](assets/chlimage_1-61.png) ![chlimage_1-62](assets/chlimage_1-62.png)

### 設定標籤 {#settings-tab}

在 **[!UICONTROL 設定]** 索引標籤，指定主題和回覆的設定：

* **[!UICONTROL 每頁主題]**
定義每頁顯示的主題/貼文數量。 預設為10。

* **[!UICONTROL 已審核]**
若勾選此選項，則張貼主題和留言必須經過核准，才會顯示在發佈網站上。 預設為未勾選。

* **[!UICONTROL 已關閉]**
如果選中，則論壇將不會顯示新主題和評論。 預設為未勾選。

* **[!UICONTROL RTF編輯器]**
如果選中，則可以使用標籤輸入主題和注釋。 預設為未勾選。

* **[!UICONTROL 允許標籤]**
若勾選此選項，允許成員將標籤新增至其貼文(請參閱 **[!UICONTROL 標籤欄位]** 標籤)。 預設為未勾選。

* **[!UICONTROL 允許檔案上載]**
如果選中，則允許將檔案附件添加到主題或注釋中。 預設為未勾選。

* **[!UICONTROL 允許下列]**
若勾選此選項，請加入下列論壇貼文功能，讓成員可 [通知](notifications.md) 新貼文。 預設為未勾選。

* **[!UICONTROL 允許釘選]**
如果選中，論壇主題可以固定到主題清單的頂部。 預設為未勾選。

* **[!UICONTROL 允許精選內容]**
若勾選，可將構想識別為 [精選內容](featured.md). 預設為未勾選。

* **[!UICONTROL 允許電子郵件訂閱]**
若勾選此選項，可允許成員透過電子郵件([訂閱](subscriptions.md))。 需要 `Allow Following` 要檢查和 [電子郵件已設定](email.md). 預設為未勾選。

* **[!UICONTROL 檔案大小上限]**
只有在 
`Allow File Uploads` 已勾選。 此欄位將限制上傳檔案的大小（以位元組為單位）。 預設為104857600(10 Mb)。

* **[!UICONTROL 允許的檔案類型]**
只有在 
`Allow File Uploads` 已勾選。 副檔名清單（以逗號分隔）以「點」分隔。 例如：.jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定了任何檔案類型，則不允許上載未指定的檔案類型。 未指定預設值，因此允許所有檔案類型。

* **[!UICONTROL 附加影像檔案的最大大小]**
僅在勾選「允許檔案上傳」時相關。 上傳的影像檔案可能具有的最大位元組數。 預設為2097152(2 Mb)。

* **[!UICONTROL 允許線程化回復]**
如果選中，則允許對發佈到主題的評論的回覆。 預設為未勾選。

* **[!UICONTROL 允許使用者刪除留言和主題]**
如果選中此選項，則允許成員刪除他們發佈的評論和主題。 預設為未勾選。

* **[!UICONTROL 允許投票]**
若勾選，請加入包含主題的投票功能。 預設為未勾選。

* **[!UICONTROL 顯示階層連結]**
若勾選此選項，則在主題頁面上顯示導覽導覽路徑標示。 已勾選預設值。

* **[!UICONTROL 顯示徽章]**
如果選中，則顯示已獲得和已分配 [徽章](implementing-scoring.md) 會員的部落格條目。 預設為未勾選。

>[!NOTE]
>
>可能需要檢查兩者 `AllowThreaded Replies` 和 `Allow users to Delete Comments and Topics` 啟用主題的注釋。

### 使用者協調標籤 {#user-moderation-tab}

在 **[!UICONTROL 使用者協調]** 索引標籤，指定如何管理已張貼的主題和回覆（使用者產生的內容）。 如需詳細資訊，請參閱 [協調使用者產生的內容](moderate-ugc.md).

* **[!UICONTROL 拒絕貼文]**
若勾選此選項，信任的成員協調者將可拒絕貼文，並防止貼文出現在公開論壇上。 預設為未勾選。

* **[!UICONTROL 關閉/重新開啟主題]**
如果選中，受信任的成員協調者可以關閉主題以進一步編輯和評論，也可以重新開啟主題。 預設為未勾選。

* **[!UICONTROL 移動主題]**
如果勾選此選項，允許發佈端協調者移動主題。 已勾選預設值。

* **[!UICONTROL 標幟貼文]**
如果選中，則允許成員將其他主題或評論標籤為不適當。 預設為未勾選。

* **[!UICONTROL 標誌原因清單]**
如果選中，則允許成員從下拉清單中選擇其標籤主題或注釋為不適當的原因。 預設為未勾選。

* **[!UICONTROL 自訂標幟原因]**
如果選中，則允許成員輸入自己的原因，將主題或評論標籤為不適當。 預設為未勾選。

* **[!UICONTROL 協調臨界值]**
輸入在通知協調者之前，成員必須標籤主題或評論的次數。 預設為1（一次）。

* **[!UICONTROL 標幟限制]**
輸入主題或留言在從公共視圖中隱藏之前必須標籤的次數。 如果設為–1，則標籤的主題或評論永遠不會在公共視圖中隱藏。 否則，此數字必須大於或等於協調臨界值。 預設為5。

### 標籤欄位標籤 {#tag-field-tab}

在 **[!UICONTROL 標籤欄位]** 標籤中，如果允許，則可套用的標籤 **[!UICONTROL 設定]** 標籤，會根據所選的命名空間而受到限制。

* **[!UICONTROL 允許的命名空間]**
若 `Allow Tagging` 在 **[!UICONTROL 設定]** 標籤。 可套用的標籤僅限於所檢查命名空間類別中的標籤。 命名空間清單包含「標準標籤」（預設命名空間）以及「包含所有標籤」。 預設值未勾選，這表示允許所有命名空間。

* **[!UICONTROL 建議限制]**
輸入要作為建議顯示給論壇成員的標籤數。 預設為 
**-** 1（無限制）。

### 翻譯標籤 {#translation-tab}

在 **[!UICONTROL 翻譯]** 標籤，如果為社群網站啟用翻譯，則可設定翻譯以翻譯整個主題或選取的貼文。

* **[!UICONTROL 全部翻譯]**
如果選中，則論壇線程將轉換為用戶的首選語言。 預設為未勾選。

### 排序設定標籤 {#sort-settings-tab}

在 **[!UICONTROL 排序設定]** 頁簽，指定在顯示張貼的留言時排序的方式。

* **[!UICONTROL 排序依據]**
檢查所有允許的排序選擇： 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`。預設為 `Newest, Oldest, Last Updated`.

* **[!UICONTROL 設為預設值]**
下拉式清單以選取其中一個核取的排序選項，以顯示為預設值。 預設為 
`Newest`。

* **[!UICONTROL 選取Analytics排序的時間選項]**
下拉式清單以選取其中一個 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`。預設為 `All`.

## 其他資訊 {#additional-information}

如需詳細資訊，請參閱 [論壇要點](essentials-forum.md) 頁面。

如需已張貼主題和留言的協調，請參閱 [協調使用者產生的內容](moderate-ugc.md).

有關標籤已發佈的主題和評論，請參閱 [標籤使用者產生的內容](tag-ugc.md).

如需已張貼主題和留言的翻譯，請參閱 [轉譯使用者產生的內容](translate-ugc.md).

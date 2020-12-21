---
title: 論壇功能
seo-title: 論壇功能
description: 如何新增和設定論壇功能
seo-description: 如何新增和設定論壇功能
uuid: ced860ef-6f8a-4df2-acc8-6a48140fca83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3495f983-d71e-4704-be4e-8a42a63f72db
translation-type: tm+mt
source-git-commit: 28948f1f8678512f8fc970a4289cb01cde86c5c2
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 0%

---


# 論壇功能{#forum-feature}

## 簡介 {#introduction}

論壇功能為登入網站訪客（社群成員）在發佈環境中提供一個區域，供您：

* 建立新主題
* 檢視並回覆主題
* 關注主題
* 搜尋論壇
* 協助協調論壇內容
* 將論壇主題從一個頁面移至另一個頁面

本節說明

* 新增論壇功能至AEM網站
* `Forum`元件的配置設定

## 將論壇添加到頁面{#adding-a-forum-to-a-page}

若要在作者模式下將`Forum`元件新增至頁面，請使用元件瀏覽器來尋找

* `Communities / Forum`

並將它拖曳至應該出現論壇的頁面上。

如需必要資訊，請造訪[Communities Components Basics](basics.md)。

當包含[必要的用戶端程式庫](essentials-forum.md#essentials-for-client-side)時，`Forum`元件的顯示方式如下：

![chlimage_1-60](assets/chlimage_1-60.png)

## 配置論壇{#configuring-a-forum}

選擇要訪問的已放置的`Forum`元件，並選擇`Configure`表徵圖以開啟編輯對話框。

![chlimage_1-61](assets/chlimage_1-61.png) ![chlimage_1-62](assets/chlimage_1-62.png)

### 「設定」頁籤{#settings-tab}

在&#x200B;**[!UICONTROL Settings]**&#x200B;標籤下，指定主題和回覆的設定：

* **[!UICONTROL 每頁主]**
題定義每頁顯示的主題／貼文數。預設值為10。

* **[!UICONTROL 協調]**
的話題和留言若勾選，則必須先核准張貼主題和留言，才會顯示在發佈網站上。預設為未勾選。

* **[!UICONTROL 關閉]**
如果選中，則論壇將關閉新主題和注釋。預設為未勾選。

* **[!UICONTROL 富格文本編]**
輯器如果選中此選項，則主題和注釋可以與標籤一起輸入。預設為未勾選。

* **[!UICONTROL 允許]**
標籤如果勾選此選項，允許成員將標籤標籤新增至其貼文(請參 **[!UICONTROL 閱標]** 記欄位標籤)。預設為未勾選。

* **[!UICONTROL 允許文]**
件上載如果選中，允許將檔案附件添加到主題或注釋。預設為未勾選。

* **[!UICONTROL 允許]**
下列若勾選，請為論壇貼文加入下列功能，讓會員得 [](notifications.md) 知新貼文。預設為未勾選。

* **[!UICONTROL 允許]**
釘選如果勾選，論壇主題可能會釘選至主題清單的頂端。預設為未勾選。

* **[!UICONTROL 若勾選「]**
允許精選內容」，此構想即可識別為 [精選內容](featured.md)。預設為未勾選。

* **[!UICONTROL 允許電子]**
郵件訂閱如果勾選，允許會員透過電子郵件（訂閱）收到新[貼文](subscriptions.md)。需要檢查`Allow Following`並配置[電子郵件](email.md)。 預設為未勾選。

* **[!UICONTROL 最大檔案大]**
小僅在 
`Allow File Uploads` 已勾選。此欄位將限制已上傳檔案的大小（以位元組為單位）。 預設值為104857600(10 Mb)。

* **[!UICONTROL 允許的檔案類]**
型僅在 
`Allow File Uploads` 已勾選。以逗號分隔的副檔名清單，並以&quot;dot&quot;分隔。 例如：.jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定任何檔案類型，則不允許上傳未指定的檔案類型。 未指定預設值，因此允許所有檔案類型。

* **[!UICONTROL 最大附加影像檔案大]**
小只有在勾選「允許檔案上傳」時，才相關。上傳的影像檔案的位元組數上限。 預設值為2097152(2 Mb)。

* **[!UICONTROL 允許線程]**
化回覆如果勾選，允許回覆張貼至主題的留言。預設為未勾選。

* **[!UICONTROL 允許用戶刪除注釋和主]**
題如果選中，允許成員刪除他們發佈的注釋和主題。預設為未勾選。

* **[!UICONTROL 允許]**
投票如果選中，請將「投票」功能與主題一起包含。預設為未勾選。

* **[!UICONTROL 顯示網]**
路導覽路徑標示如果勾選，則顯示主題頁面上的導覽網站導覽路徑標示。已勾選預設值。

* **[!UICONTROL 顯示]**
標章如果勾選，請使用成員的 [](implementing-scoring.md) 部落格項目顯示已獲得和已指派的標章。預設為未勾選。

>[!NOTE]
>
>可能需要同時檢查`AllowThreaded Replies`和`Allow users to Delete Comments and Topics`以啟用對主題的注釋。

### 使用者協調標籤{#user-moderation-tab}

在&#x200B;**[!UICONTROL 使用者協調]**&#x200B;標籤下，指定如何管理已張貼的主題和回覆（使用者產生的內容）。 如需詳細資訊，請參閱[協調使用者產生的內容](moderate-ugc.md)。

* **[!UICONTROL 拒絕]**
貼文如果勾選，可信任的會員協調者將可拒絕貼文，並防止貼文出現在公開論壇。預設為未勾選。

* **[!UICONTROL 關閉／重新開]**
啟主題如果勾選，受信任的成員協調者可以關閉主題以進一步編輯和留言，也可以重新開啟主題。預設為未勾選。

* **[!UICONTROL 移動]**
主題如果勾選，則允許發佈端協調者移動主題。已勾選預設值。

* **[!UICONTROL 標幟]**
貼文如果勾選，允許成員將其他主題或留言標幟為不適當。預設為未勾選。

* **[!UICONTROL 標幟原]**
因清單如果勾選，允許成員從下拉式清單中選擇標幟主題或留言的不適當原因。預設為未勾選。

* **[!UICONTROL 自訂標幟原]**
因如果勾選，允許成員輸入自己將主題或留言標籤為不適當的原因。預設為未勾選。

* **[!UICONTROL 協調]**
臨界值輸入在通知協調者之前，成員必須標籤主題或留言的次數。預設值為1（一次）。

* **[!UICONTROL 標幟]**
限制輸入主題或留言在公開檢視中隱藏前必須標幟的次數。如果設為-1，則標籤的主題或留言絕不會從公開檢視中隱藏。 否則，此數字必須大於或等於「協調臨界值」。 預設值為5。

### 標籤欄位標籤{#tag-field-tab}

在&#x200B;**[!UICONTROL Tag欄位]**&#x200B;頁籤下，如果允許在&#x200B;**[!UICONTROL Settings]**&#x200B;頁籤下應用的標籤會根據選擇的名稱空間進行限制。

* **[!UICONTROL 允許的]**
名稱空間 `Allow Tagging` 相關(如果已勾選「設定」 **** 標籤)。可套用的標籤僅限於已勾選之命名空間類別中的標籤。 名稱空間清單包含「標準標籤」（預設命名空間）和「包含所有標籤」。 預設值未勾選，表示允許所有命名空間。

* **[!UICONTROL 建議]**
限制輸入要作為建議顯示給發佈到論壇的成員的標籤數。預設值為 
**-** 1（無限制）。

### 翻譯頁籤{#translation-tab}

在&#x200B;**[!UICONTROL Translation]**&#x200B;標籤下，如果為社區站點啟用了翻譯，則可以設定翻譯來翻譯整個主題或選定的帖子。

* **[!UICONTROL Translate]**
AllIf checked, the forum thread in translated in to the user&#39;s preferred language.預設為未勾選。

### 排序設定頁籤{#sort-settings-tab}

在&#x200B;**[!UICONTROL 排序設定]**&#x200B;標籤下，指定顯示張貼留言的排序方式。

* **[!UICONTROL 排序依]**
據檢查所有允許的排序選擇： 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. 預設值為`Newest, Oldest, Last Updated`。

* **[!UICONTROL 設定為「]**
預設」(Default)「下拉式」(Pulldown)，以選擇一個選定的排序選項作為預設選項顯示。預設值為 
`Newest`。

* **[!UICONTROL 選取Analytics排序的時間選]**
項下拉式選取其中一個 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`.預設值為`All`。

## 其他資訊 {#additional-information}

如需詳細資訊，請參閱開發人員的[Forum Essentials](essentials-forum.md)頁面。

如需協調已張貼主題和留言的資訊，請參閱[協調使用者產生的內容](moderate-ugc.md)。

如需標籤已張貼的主題和留言，請參閱[標籤使用者產生的內容](tag-ugc.md)。

如需已張貼主題和留言的轉譯，請參閱[轉譯使用者產生的內容](translate-ugc.md)。

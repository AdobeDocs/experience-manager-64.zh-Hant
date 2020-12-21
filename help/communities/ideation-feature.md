---
title: 創意功能
seo-title: 創意功能
description: 新增和設定構想功能
seo-description: 新增和設定構想功能
uuid: b21507da-10c8-4149-9e2c-a4ff5dec582b
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 7c0a9120-2edb-431b-b460-68398832d5ec
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '1066'
ht-degree: 0%

---


# 創意功能{#ideation-feature}

## 簡介 {#introduction}

識別功能為登入網站訪客（社群成員）在發佈環境中提供一個區域，以便：

* 建立想法以與社群分享
* 觀念與評論
* 遵循構想
* 就構想投票

本節說明

* 新增創意功能至AEM網站
* Ideation元件的組態設定

## 新增構想至頁面{#adding-a-ideation-to-a-page}

若要在作者模式下將`Ideation`元件新增至頁面，請使用元件瀏覽器來找出`Communities / Ideation`，並將它拖曳至應該出現構想的頁面上。

如需必要資訊，請造訪[Communities Components Basics](basics.md)。

當包含[必要的用戶端程式庫](ideation.md#essentials-for-client-side)時，`Ideation`元件的顯示方式如下：

![chlimage_1-21](assets/chlimage_1-29.png)

## 配置構想{#configuring-an-ideation}

選擇要訪問的已放置的`Ideation`元件，並選擇`Configure`表徵圖以開啟編輯對話框。

![chlimage_1-30](assets/chlimage_1-30.png) ![chlimage_1-31](assets/chlimage_1-31.png)

### 「設定」頁籤{#settings-tab}

在&#x200B;**[!UICONTROL Settings]**&#x200B;標籤下，指定構想和留言的設定：

* **[!UICONTROL 構想]**
標題構想的顯示標題。預設值為 
`Ideation`。

* **[!UICONTROL 構想]**
說明要顯示為構想子標題的說明。預設值為無說明。

* **[!UICONTROL 每頁主]**
題定義每頁顯示的構想／貼文數。預設值為10。

* **[!UICONTROL 協調]**
化：如果勾選，張貼構想和留言必須先經過核准，才能顯示在發佈網站上。預設為未勾選。

* **[!UICONTROL 已]**
關閉如果勾選，則會關閉構想論壇以取得新想法和留言。預設為未勾選。

* **[!UICONTROL Rich Text]**
Editor如果勾選，則可使用標籤輸入構想和註解。預設為未勾選。

* **[!UICONTROL 允許]**
標籤如果勾選此選項，允許成員將標籤標籤新增至其貼文(請參 **[!UICONTROL 閱標]** 記欄位標籤)。預設為未勾選。

* **[!UICONTROL 允許文]**
件上載如果選中，允許將檔案附件添加到構想或注釋中。預設為未勾選。

* **[!UICONTROL 最大檔案大]**
小僅在 
`Allow File Uploads` 已勾選。此欄位將限制已上傳檔案的大小（以位元組為單位）。 預設值為104857600(10 Mb)。

* **[!UICONTROL 允許的檔案類]**
型僅在 
`Allow File Uploads` 已勾選。以逗號分隔的副檔名清單，並以&quot;dot&quot;分隔。 例如：.jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定任何檔案類型，則不允許上傳未指定的檔案類型。 未指定預設值，因此允許所有檔案類型。

* **[!UICONTROL 最大附加影像檔案大]**
小只有在勾選「允許檔案上傳」時，才相關。上傳的影像檔案的位元組數上限。 預設值為2097152(2 Mb)。

* **[!UICONTROL 允許]**
回覆如果勾選，允許回覆張貼至構想的留言。預設為未勾選。

* **[!UICONTROL 允許使用者刪除留言和主]**
題如果勾選，允許成員刪除他們張貼的留言和想法。預設為未勾選。

* **[!UICONTROL 允許]**
追蹤如果勾選，請為構想貼文加入下列功能，讓成員得 [](notifications.md) 到新貼文的通知。預設為未勾選。

* **[!UICONTROL 允許電子]**
郵件訂閱如果勾選，允許會員透過電子郵件（訂閱）收到新[貼文](subscriptions.md)。需要檢查`Allow Following`並配置[電子郵件](email.md)。 預設為未勾選。

* **[!UICONTROL Allow]**
PottingIf勾選後，允許對構想的注釋進行投票。預設為未勾選。

* **[!UICONTROL 顯示]**
標章如果勾選，則使用成員的構 [](implementing-scoring.md) 想顯示已獲得和已分配的徽章。預設為未勾選。

* **[!UICONTROL 若勾選「]**
允許精選內容」，此構想即可識別為 [精選內容](featured.md)。預設為未勾選。

### 使用者協調標籤{#user-moderation-tab}

在&#x200B;**[!UICONTROL 使用者協調]**&#x200B;標籤下，指定如何管理已張貼的想法和留言（使用者產生的內容）。 如需詳細資訊，請參閱[協調使用者產生的內容](moderate-ugc.md)。

* **[!UICONTROL 拒絕]**
貼文如果勾選，可信任的會員協調者將可拒絕貼文，並防止貼文出現在公開論壇。預設為未勾選。

* **[!UICONTROL 關閉／重新開]**
啟主題如果勾選，受信任的成員協調者可以關閉主題以進一步編輯和留言，也可以重新開啟主題。預設為未勾選。

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
名稱空間相關(如果 
`Allow Tagging` 在「設定」(Setting)選 **** 項卡下。可套用的標籤僅限於已勾選之命名空間類別中的標籤。 名稱空間清單包含「標準標籤」（預設命名空間）和「包含所有標籤」。 預設值未勾選，表示允許所有命名空間。

* **[!UICONTROL 建議]**
限制輸入要作為建議顯示給發佈到論壇的成員的標籤數。值 
**-** 1表示無限制。預設值為0。

### 排序設定頁籤{#sort-settings-tab}

在&#x200B;**[!UICONTROL 排序設定]**&#x200B;標籤下，指定顯示張貼留言的排序方式。

* **[!UICONTROL 排序依]**
據檢查所有允許的排序選擇： 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`.預設值為`Newest, Oldest, Last Updated`。

* **[!UICONTROL 設定為「]**
預設」(Default)「下拉式」(Pulldown)，以選擇一個選定的排序選項作為預設選項顯示。預設值為 
`Newest`。

* **[!UICONTROL 選取Analytics排序的時間選]**
項下拉式選取其中一個 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`.預設值為`All`。

## 網站訪客體驗{#site-visitor-experience}

### 建立構想{#creating-idea}

與所有社群功能一樣，若未登入，網站訪客只能閱讀構想並檢視其他意見（透過留言和投票／按贊）。

一旦登入，會員就可能會建立新構想。

![chlimage_1-32](assets/chlimage_1-32.png)

在提交構想之前，會員可儲存草稿。

通過選擇`Save as Draft`按鈕，將保存草稿。

![chlimage_1-33](assets/chlimage_1-33.png)

在`My Drafts`頁籤中查看保存的草稿時，選擇`Read More`以重新進入編輯模式：

![chlimage_1-34](assets/chlimage_1-34.png)

#### 提供反饋{#providing-feedback}

一旦發佈構想後，其他成員可以登入、開啟構想(`Read More`)並贊成構想，從而增加投票計數，並加上意見。

![chlimage_1-35](assets/chlimage_1-35.png)

### 其他資訊 {#additional-information}

如需詳細資訊，請參閱開發人員的[Ideation Essentials](ideation.md)頁面。

如需協調已張貼主題和留言的資訊，請參閱[協調使用者產生的內容](moderate-ugc.md)。

如需標籤已張貼的主題和留言，請參閱[標籤使用者產生的內容](tag-ugc.md)。

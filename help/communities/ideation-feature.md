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


# 創意功能 {#ideation-feature}

## 簡介 {#introduction}

識別功能為登入網站訪客（社群成員）在發佈環境中提供一個區域，以便：

* 建立想法以與社群分享
* 觀念與評論
* 遵循構想
* 就構想投票

本節說明

* 新增創意功能至AEM網站
* Ideation元件的組態設定

## 新增構想至頁面 {#adding-a-ideation-to-a-page}

若要在作 `Ideation` 者模式下將元件新增至頁面，請使用元件瀏覽器來 `Communities / Ideation` 尋找並拖曳元件至應該出現構想的頁面。

如需必要資訊，請造 [訪Communities Components Basics](basics.md)。

當包含 [所需的用戶端程式庫](ideation.md#essentials-for-client-side) ，元件的顯示 `Ideation`方式如下：

![chlimage_1-29](assets/chlimage_1-29.png)

## 設定構想 {#configuring-an-ideation}

選擇要訪問 `Ideation` 的已放置元件，並選 `Configure` 擇開啟編輯對話框的表徵圖。

![chlimage_1-30](assets/chlimage_1-30.png) ![chlimage_1-31](assets/chlimage_1-31.png)

### 「設定」頁籤 {#settings-tab}

在「設 **[!UICONTROL 定]** 」標籤下，指定構想和留言的設定：

* **[!UICONTROL 構想標]**&#x200B;題構想的顯示標題。 預設值為 
`Ideation`。

* **[!UICONTROL 構想描]**&#x200B;述要顯示為構想子標題的說明。 預設值為無說明。

* **[!UICONTROL 每頁主題]**&#x200B;定義每頁顯示的構想／貼文數。 預設值為10。

* **[!UICONTROL 已協調]**：如果勾選，則必須先核准張貼構想和留言，才能將其顯示在發佈網站上。 預設為未勾選。

* **[!UICONTROL 關閉]**&#x200B;如果勾選此選項，則會關閉構想論壇以取得新想法和留言。 預設為未勾選。

* **[!UICONTROL 富格文本編]**&#x200B;輯器如果選中此選項，則可使用標注輸入構想和注釋。 預設為未勾選。

* **[!UICONTROL 允許標籤]**：如果勾選，允許成員將標籤標籤新增至其貼文(請參 **[!UICONTROL 閱標籤欄位]** 標籤)。 預設為未勾選。

* **[!UICONTROL 允許檔案上載]**&#x200B;如果選中此選項，則允許將檔案附件添加到構想或注釋中。 預設為未勾選。

* **[!UICONTROL 最大檔案大小]**&#x200B;僅在 
`Allow File Uploads` 已勾選。 此欄位將限制已上傳檔案的大小（以位元組為單位）。 預設值為104857600(10 Mb)。

* **[!UICONTROL 允許的檔案類型]**&#x200B;僅與 
`Allow File Uploads` 已勾選。 以逗號分隔的副檔名清單，並以&quot;dot&quot;分隔。 例如： .jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定任何檔案類型，則不允許上傳未指定的檔案類型。 未指定預設值，因此允許所有檔案類型。

* **[!UICONTROL 僅當勾選「允許上傳檔案]**」時，附加影像檔案大小的上限才相關。 上傳的影像檔案的位元組數上限。 預設值為2097152(2 Mb)。

* **[!UICONTROL 允許回覆]**&#x200B;如果勾選，則允許回覆張貼至構想的留言。 預設為未勾選。

* **[!UICONTROL 允許使用者刪除留言和主題]**&#x200B;如果勾選，允許成員刪除他們張貼的留言和想法。 預設為未勾選。

* **[!UICONTROL 允許下]**&#x200B;列：如果勾選，請為構想貼文加入下列功能，讓成員可 [以收到](notifications.md) 新貼文的通知。 預設為未勾選。

* **[!UICONTROL 允許電子郵件]**&#x200B;訂閱如果勾選，允許會員透過電子郵件（訂閱）收到新[貼文](subscriptions.md)。 需要 `Allow Following` 檢查並設定電 [子郵件](email.md)。 預設為未勾選。

* **[!UICONTROL 允許投票]**&#x200B;如果勾選，則允許對構想的注釋進行投票。 預設為未勾選。

* **[!UICONTROL 顯示標章]**&#x200B;如果勾選，則使用成員的構想 [顯示已獲得](implementing-scoring.md) 和已分配的標章。 預設為未勾選。

* **[!UICONTROL 如果勾選]**「允許特色內容」，即可將構想識別為 [特色內容](featured.md)。 預設為未勾選。

### 使用者協調標籤 {#user-moderation-tab}

在「使用 **[!UICONTROL 者協調]** 」標籤下，指定如何管理已張貼的想法和留言（使用者產生的內容）。 如需詳細資訊，請參閱 [協調使用者產生的內容](moderate-ugc.md)。

* **[!UICONTROL 拒絕貼文]**&#x200B;如果勾選，可信任的會員協調者將可拒絕貼文，並防止貼文出現在公開論壇。 預設為未勾選。

* **[!UICONTROL 關閉／重新開啟主]**&#x200B;題如果勾選，受信任的成員協調者可以關閉主題以進一步編輯和留言，也可以重新開啟主題。 預設為未勾選。

* **[!UICONTROL 標幟貼文]**&#x200B;如果勾選，允許成員將其他主題或留言標幟為不適當。 預設為未勾選。

* **[!UICONTROL 標幟原因清]**&#x200B;單如果勾選，允許成員從下拉式清單中選擇其標籤主題或留言的不適當原因。 預設為未勾選。

* **[!UICONTROL 自訂標幟原]**&#x200B;因如果勾選，允許成員輸入自己將主題或留言標籤為不適當的原因。 預設為未勾選。

* **[!UICONTROL 協調臨]**&#x200B;界值輸入在通知協調者之前，成員必須標籤主題或留言的次數。 預設值為1（一次）。

* **[!UICONTROL 標籤限]**&#x200B;制輸入主題或留言在公開檢視中隱藏之前必須標籤的次數。 如果設為-1，則標籤的主題或留言永遠不會隱藏在公開檢視中。 否則，此數字必須大於或等於「協調臨界值」。 預設值為5。

### 「標籤」欄位頁籤 {#tag-field-tab}

在「標 **[!UICONTROL 記」欄位]** (Tag field **** )標籤下，可套用的標籤（如果允許）會根據選擇的名稱空間加以限制。

* **[!UICONTROL 允許的名稱空間]**&#x200B;相關(如果 
`Allow Tagging` 已勾選「設定」 **標籤** 。 可套用的標籤僅限於已勾選之命名空間類別中的標籤。 名稱空間清單包含「標準標籤」（預設命名空間）和「包含所有標籤」。 預設值未勾選，表示允許所有命名空間。

* **[!UICONTROL 建議限]**&#x200B;制輸入要作為建議顯示給發佈到論壇的成員的標籤數。 值 
**-** 1表示無限制。 預設值為0。

### 「排序設定」頁籤 {#sort-settings-tab}

在「排 **[!UICONTROL 序設定]** 」標籤下，指定顯示張貼留言的排序方式。

* **[!UICONTROL 排序依據]**&#x200B;檢查所有允許的排序選擇： 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. 預設為 `Newest, Oldest, Last Updated`。

* **[!UICONTROL 設定為「預設]**」(Default)下拉式選項，以選擇一個選定的排序選項作為預設選項顯示。 預設值為 
`Newest`。

* **[!UICONTROL 選取Analytics排序下拉式選]**&#x200B;項以選取其中一個 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`. 預設為 `All`。

## 網站訪客體驗 {#site-visitor-experience}

### 創意 {#creating-idea}

與所有社群功能一樣，若未登入，網站訪客只能閱讀構想並檢視其他意見（透過留言和投票／按贊）。

一旦登入，會員就可能會建立新構想。

![chlimage_1-32](assets/chlimage_1-32.png)

在提交構想之前，會員可儲存草稿。

通過選擇 `Save as Draft` 按鈕，將保存草稿。

![chlimage_1-33](assets/chlimage_1-33.png)

在頁籤中查看保存的草 `My Drafts` 稿時，選擇 `Read More` 以重新進入編輯模式：

![chlimage_1-34](assets/chlimage_1-34.png)

#### 提供意見回應 {#providing-feedback}

一旦發佈構想，其他成員就可以登入、開啟構想( `Read More`)並像構想一樣，進而增加選票計數，並加上意見。

![chlimage_1-35](assets/chlimage_1-35.png)

### 其他資訊 {#additional-information}

如需詳細資訊，請參閱開發 [人員的Ideation Essentials](ideation.md) 頁面。

如需協調已張貼主題和留言的資訊，請參 [閱協調使用者產生的內容](moderate-ugc.md)。

如需標籤已張貼的主題和留言，請參 [閱標籤使用者產生的內容](tag-ugc.md)。

---
title: 構思功能
seo-title: 構思功能
description: 新增和設定構想功能
seo-description: 新增和設定構想功能
uuid: b21507da-10c8-4149-9e2c-a4ff5dec582b
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 7c0a9120-2edb-431b-b460-68398832d5ec
exl-id: 391885f2-e46d-4eb4-9c88-509233505df8
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1066'
ht-degree: 0%

---

# 構思功能{#ideation-feature}

## 簡介 {#introduction}

構想功能提供發佈環境中登入網站訪客（社群成員）的區域，以執行下列作業：

* 建立想法以與社群分享
* 觀看和評論意見
* 遵循想法
* 就某個想法投票

本檔案的本節說明

* 將構思功能新增至AEM網站
* Identiation元件的組態設定

## 將構思新增至頁面{#adding-a-ideation-to-a-page}

若要在製作模式中將`Ideation`元件新增至頁面，請使用元件瀏覽器來找出`Communities / Ideation`，並將其拖曳至應該出現構想的頁面上。

如需必要資訊，請造訪[Communities Components Basics](basics.md)。

當包含[必要的用戶端程式庫](ideation.md#essentials-for-client-side)時，以下是`Ideation`元件的顯示方式：

![chlimage_1-21](assets/chlimage_1-29.png)

## 配置標識{#configuring-an-ideation}

選取要存取的放置`Ideation`元件，並選取開啟編輯對話方塊的`Configure`圖示。

![chlimage_1-30](assets/chlimage_1-30.png) ![chlimage_1-31](assets/chlimage_1-31.png)

### 設定頁簽{#settings-tab}

在&#x200B;**[!UICONTROL Settings]**&#x200B;標籤下，指定思想和注釋的設定：

* **[!UICONTROL 構想]**
標題構想的顯示標題。預設為 
`Ideation`。

* **[!UICONTROL 構]**
想說明要顯示為構想子標題的說明。預設值為無說明。

* **[!UICONTROL 每頁主]**
題定義每頁顯示的意見/貼文數。預設為10。

* ****
已審核如果勾選此選項，張貼意見和留言必須經過核准，才會顯示在發佈網站上。預設為未勾選。

* ****
已關閉如果勾選此選項，將不會顯示新想法和評論。預設為未勾選。

* **[!UICONTROL RTF編]**
輯器如果選中此選項，則可使用標籤輸入構想和注釋。預設為未勾選。

* **[!UICONTROL 允許]**
標籤如果選中此選項，允許成員向其貼文中添加標籤標籤(請參閱 **[!UICONTROL 標籤]** 欄位頁簽)。預設為未勾選。

* **[!UICONTROL 允許檔]**
案上載如果選中此選項，允許將檔案附件添加到思想或注釋中。預設為未勾選。

* **[!UICONTROL 檔案大小]**
上限僅與 
`Allow File Uploads` 已勾選。此欄位將限制上傳檔案的大小（以位元組為單位）。 預設為104857600(10 Mb)。

* **[!UICONTROL 允許的檔案]**
類型僅與 
`Allow File Uploads` 已勾選。副檔名清單（以逗號分隔）以「點」分隔。 例如：.jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定了任何檔案類型，則不允許上載未指定的檔案類型。 未指定預設值，因此允許所有檔案類型。

* **[!UICONTROL 最大附加影像檔案]**
大小僅在勾選「允許檔案上傳」時相關。上傳的影像檔案可能具有的最大位元組數。 預設為2097152(2 Mb)。

* **[!UICONTROL 允許]**
回覆如果勾選，則允許回覆張貼至構想的留言。預設為未勾選。

* **[!UICONTROL 允許使用者刪除留言和主]**
題如果勾選此選項，允許成員刪除他們張貼的留言和想法。預設為未勾選。

* **[!UICONTROL 允]**
許下列若勾選此選項，即可為構想貼文加入下列功能，以便 [](notifications.md) 通知成員新貼文。預設為未勾選。

* **[!UICONTROL 允許電子]**
郵件訂閱如果勾選此選項，允許成員透過電子郵件([訂閱](subscriptions.md))接收新貼文的通知。需要檢查`Allow Following`，並配置[電子郵件](email.md)。 預設為未勾選。

* **[!UICONTROL 允許]**
投票如果選中，則允許對構想的評論進行投票。預設為未勾選。

* **[!UICONTROL 顯]**
示徽章如果選中此選項，則用成員的 [](implementing-scoring.md) 想法顯示已獲得和已分配徽章。預設為未勾選。

* **[!UICONTROL 若勾選]**
「允許精選內容」，即可將構想識別為精選 [內容](featured.md)。預設為未勾選。

### 使用者協調標籤{#user-moderation-tab}

在&#x200B;**[!UICONTROL 使用者協調]**&#x200B;標籤下，指定如何管理已張貼的想法和留言（使用者產生的內容）。 如需詳細資訊，請參閱[協調使用者產生的內容](moderate-ugc.md)。

* **[!UICONTROL 拒]**
絕貼文如果勾選此選項，可信任的成員協調者將可拒絕貼文，並防止貼文出現在公開論壇。預設為未勾選。

* **[!UICONTROL 關閉/重新開]**
啟主題如果選中此選項，受信任的成員協調者可以關閉主題以進一步編輯和評論，也可以重新開啟主題。預設為未勾選。

* **[!UICONTROL 標]**
幟貼文如果勾選此選項，可讓成員將其他主題或留言標幟為不適當。預設為未勾選。

* **[!UICONTROL 標幟原]**
因清單如果勾選此選項，允許成員從下拉式清單中選擇其標幟主題或評論為不適當的原因。預設為未勾選。

* **[!UICONTROL 自定義標]**
簽原因如果選中此選項，允許成員輸入自己的原因來標籤主題或注釋不適當。預設為未勾選。

* **[!UICONTROL 協調]**
臨界值輸入通知協調者之前，成員必須標籤主題或留言的次數。預設為1（一次）。

* **[!UICONTROL 標]**
簽限制輸入在從公共視圖中隱藏主題或評論之前必須標籤該主題或評論的次數。如果設為–1，則標籤的主題或評論永遠不會在公共視圖中隱藏。 否則，此數字必須大於或等於協調臨界值。 預設為5。

### 標籤欄位標籤{#tag-field-tab}

在&#x200B;**[!UICONTROL 標籤欄位]**&#x200B;標籤下，如果&#x200B;**[!UICONTROL 設定]**&#x200B;標籤下允許，則可以套用的標籤會根據所選的命名空間受到限制。

* **[!UICONTROL 允許的命]**
名空間相關(若 
`Allow Tagging` 在「設定」標籤下 **** 被檢查。可套用的標籤僅限於所檢查命名空間類別中的標籤。 命名空間清單包含「標準標籤」（預設命名空間）以及「包含所有標籤」。 預設值未勾選，這表示允許所有命名空間。

* **[!UICONTROL 建]**
議限制輸入要作為建議顯示給論壇的成員的標籤數。值 
**-** 1表示無限制。預設為0。

### 排序設定頁簽{#sort-settings-tab}

在&#x200B;**[!UICONTROL 排序設定]**&#x200B;標籤下，指定顯示張貼留言時的排序方式。

* **[!UICONTROL 按檢]**
查所有允許的排序選擇： 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`.預設值為`Newest, Oldest, Last Updated`。

* **[!UICONTROL 設定為「預]**
設」(Default)「下拉清單」(Downloak)，以選擇選定的排序選項之一，以顯示為預設選項。預設為 
`Newest`。

* **[!UICONTROL 選取Analytics的時間選項排序]**
下拉式清單以選取其中一個 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`.預設值為`All`。

## 網站訪客體驗{#site-visitor-experience}

### 建立構想{#creating-idea}

與所有Communities功能一樣，如果未登入，網站訪客只能閱讀意見並檢視其他意見（透過留言和投票/按贊）。

登入後，成員可以建立新的構想。

![chlimage_1-32](assets/chlimage_1-32.png)

在提交構想之前，成員可以保存草稿。

選擇`Save as Draft`按鈕後，將保存草稿。

![chlimage_1-33](assets/chlimage_1-33.png)

在`My Drafts`頁簽中查看保存的草稿時，選擇`Read More`以重新進入編輯模式：

![chlimage_1-34](assets/chlimage_1-34.png)

#### 提供反饋{#providing-feedback}

構想發佈後，其他成員即可登入、開啟構想(`Read More`)，並像構想一樣，進而增加投票數，並提出意見。

![chlimage_1-35](assets/chlimage_1-35.png)

### 其他資訊 {#additional-information}

如需詳細資訊，請參閱開發人員的[Ideation Essentials](ideation.md)頁面。

有關已張貼主題和留言的調節，請參閱[調節用戶生成的內容](moderate-ugc.md)。

有關標籤已發佈的主題和評論，請參閱[標籤用戶生成的內容](tag-ugc.md)。

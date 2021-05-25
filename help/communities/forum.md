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
exl-id: fa6f28b4-3217-4b6a-b223-506da0ecca9e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 0%

---

# 論壇功能{#forum-feature}

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
* `Forum`元件的組態設定

## 將論壇添加到頁面{#adding-a-forum-to-a-page}

若要在製作模式中將`Forum`元件新增至頁面，請使用元件瀏覽器來找出

* `Communities / Forum`

並將其拖曳至應該出現論壇的頁面上。

如需必要資訊，請造訪[Communities Components Basics](basics.md)。

當包含[必要的用戶端程式庫](essentials-forum.md#essentials-for-client-side)時，以下是`Forum`元件的顯示方式：

![chlimage_1-60](assets/chlimage_1-60.png)

## 配置論壇{#configuring-a-forum}

選取要存取的放置`Forum`元件，並選取開啟編輯對話方塊的`Configure`圖示。

![chlimage_1-61](assets/chlimage_1-61.png) ![chlimage_1-62](assets/chlimage_1-62.png)

### 設定頁簽{#settings-tab}

在&#x200B;**[!UICONTROL Settings]**&#x200B;標籤下，指定主題和回覆的設定：

* **[!UICONTROL 每頁主]**
題定義每頁顯示的主題/貼文數目。預設為10。

* ****
已審核如果勾選此選項，則必須先核准張貼主題和留言，才會顯示在發佈網站上。預設為未勾選。

* ****
已關閉如果選中此選項，則論壇不會顯示新主題和評論。預設為未勾選。

* **[!UICONTROL RTF編]**
輯器如果選中此選項，則主題和注釋可以用標籤輸入。預設為未勾選。

* **[!UICONTROL 允許]**
標籤如果選中此選項，允許成員向其貼文中添加標籤標籤(請參閱 **[!UICONTROL 標籤]** 欄位頁簽)。預設為未勾選。

* **[!UICONTROL 允許檔]**
案上載如果選中此選項，允許將檔案附件添加到主題或注釋中。預設為未勾選。

* **[!UICONTROL 允]**
許下列若勾選此選項，則為論壇貼文加入下列功能，可通知 [](notifications.md) 成員新貼文。預設為未勾選。

* **[!UICONTROL 允]**
許固定如果選中，論壇主題可能會固定到主題清單的頂部。預設為未勾選。

* **[!UICONTROL 若勾選]**
「允許精選內容」，即可將構想識別為精選 [內容](featured.md)。預設為未勾選。

* **[!UICONTROL 允許電子]**
郵件訂閱如果勾選此選項，允許成員透過電子郵件([訂閱](subscriptions.md))接收新貼文的通知。需要檢查`Allow Following`，並配置[電子郵件](email.md)。 預設為未勾選。

* **[!UICONTROL 檔案大小]**
上限僅與 
`Allow File Uploads` 已勾選。此欄位將限制上傳檔案的大小（以位元組為單位）。 預設為104857600(10 Mb)。

* **[!UICONTROL 允許的檔案]**
類型僅與 
`Allow File Uploads` 已勾選。副檔名清單（以逗號分隔）以「點」分隔。 例如：.jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定了任何檔案類型，則不允許上載未指定的檔案類型。 未指定預設值，因此允許所有檔案類型。

* **[!UICONTROL 最大附加影像檔案]**
大小僅在勾選「允許檔案上傳」時相關。上傳的影像檔案可能具有的最大位元組數。 預設為2097152(2 Mb)。

* **[!UICONTROL 允許線程]**
式答復如果選中，則允許對發佈到主題的評論進行答復。預設為未勾選。

* **[!UICONTROL 允許用戶刪除評論和主]**
題如果選中此選項，允許成員刪除他們發佈的評論和主題。預設為未勾選。

* **[!UICONTROL 允許]**
投票如果選中，則將「投票」功能與主題一起包含。預設為未勾選。

* **[!UICONTROL 顯示階]**
層連結如果勾選此選項，則會在主題頁面上顯示導覽階層連結。已勾選預設值。

* **[!UICONTROL 顯示]**
徽章如果選中，則使用成員的部落 [](implementing-scoring.md) 格條目顯示已獲得和已分配徽章。預設為未勾選。

>[!NOTE]
>
>可能需要同時檢查`AllowThreaded Replies`和`Allow users to Delete Comments and Topics`以啟用對主題的注釋。

### 使用者協調標籤{#user-moderation-tab}

在&#x200B;**[!UICONTROL 使用者協調]**&#x200B;標籤下，指定如何管理已張貼的主題和回覆（使用者產生的內容）。 如需詳細資訊，請參閱[協調使用者產生的內容](moderate-ugc.md)。

* **[!UICONTROL 拒]**
絕貼文如果勾選此選項，可信任的成員協調者將可拒絕貼文，並防止貼文出現在公開論壇。預設為未勾選。

* **[!UICONTROL 關閉/重新開]**
啟主題如果選中此選項，受信任的成員協調者可以關閉主題以進一步編輯和評論，也可以重新開啟主題。預設為未勾選。

* **[!UICONTROL 移動]**
主題如果勾選此選項，允許發佈端協調者移動主題。已勾選預設值。

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

* **[!UICONTROL 允許的]**
命名空間如果 `Allow Tagging` 在「設定」標籤下勾選，則 **** 相關。可套用的標籤僅限於所檢查命名空間類別中的標籤。 命名空間清單包含「標準標籤」（預設命名空間）以及「包含所有標籤」。 預設值未勾選，這表示允許所有命名空間。

* **[!UICONTROL 建]**
議限制輸入要作為建議顯示給論壇的成員的標籤數。預設為 
**-** 1（無限制）。

### 翻譯標籤{#translation-tab}

在&#x200B;**[!UICONTROL 翻譯]**&#x200B;標籤下，如果為社群網站啟用翻譯，則可以設定翻譯以翻譯整個主題或選取的貼文。

* **[!UICONTROL 翻]**
譯全部如果選中，則論壇線程將翻譯為用戶的首選語言。預設為未勾選。

### 排序設定頁簽{#sort-settings-tab}

在&#x200B;**[!UICONTROL 排序設定]**&#x200B;標籤下，指定顯示張貼留言時的排序方式。

* **[!UICONTROL 按檢]**
查所有允許的排序選擇： 
`Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. 預設值為`Newest, Oldest, Last Updated`。

* **[!UICONTROL 設定為「預]**
設」(Default)「下拉清單」(Downloak)，以選擇選定的排序選項之一，以顯示為預設選項。預設為 
`Newest`。

* **[!UICONTROL 選取Analytics的時間選項排序]**
下拉式清單以選取其中一個 
`All, Last 24 Hours, Last 7 Days, Last 30 Days`.預設值為`All`。

## 其他資訊 {#additional-information}

如需詳細資訊，請參閱開發人員的[Forum Essentials](essentials-forum.md)頁面。

有關已張貼主題和留言的調節，請參閱[調節用戶生成的內容](moderate-ugc.md)。

有關標籤已發佈的主題和評論，請參閱[標籤用戶生成的內容](tag-ugc.md)。

有關已張貼主題和評論的翻譯，請參閱[翻譯用戶生成的內容](translate-ugc.md)。

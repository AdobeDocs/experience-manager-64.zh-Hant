---
title: 問答論壇功能
seo-title: 問答論壇功能
description: 將QnA論壇功能添加到頁面
seo-description: 將QnA論壇功能添加到頁面
uuid: 006c0bf0-c230-4890-8080-65651f4b4dac
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: bbbe32bb-9d97-461e-822f-a7ddc6c9f9ef
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '1216'
ht-degree: 0%

---


# 問答論壇功能{#q-a-forum-feature}

## 簡介 {#introduction}

QnA（問題與答案）論壇功能為社群成員提供了提問與回答問題的區域：

* 建立新問題
* 內嵌影像（支援拖放）
* 檢視並回答問題
* 搜尋問題
* 協助協調QnA內容
* 找出最佳答案
* 將QnA問題從一個頁面移至另一個頁面

本節說明

* 新增QnA論壇功能至AEM網站
* `QnA`元件的配置設定

## 新增問答論壇至頁面{#adding-a-q-a-forum-to-a-page}

要在作者模式下將`QnA`元件添加到頁面，請使用元件瀏覽器找到`Communities / QnA`並將其拖放到應出現QnA論壇的頁面上。

如需必要資訊，請造訪[Communities Components Basics](basics.md)。

當包含[必要的用戶端程式庫](qna-essentials.md#essentials-for-client-side)時，`QnA`元件的顯示方式如下：

![chlimage_1-280](assets/chlimage_1-280.png)

### 配置QnA {#configuring-qna}

選擇要訪問的已放置的`QnA`元件，並選擇`Configure`表徵圖以開啟編輯對話框。

![chlimage_1-281](assets/chlimage_1-281.png) ![chlimage_1-282](assets/chlimage_1-282.png)

#### 「設定」頁籤{#settings-tab}

在&#x200B;**[!UICONTROL Settings]**&#x200B;標籤下，指定主題（問題）和回覆（答案）的設定：

* **[!UICONTROL 每頁主題]**
定義每頁顯示的問題／貼文數。預設值為10。

* **[!UICONTROL 協調]**
的話題和留言若勾選，則必須先核准張貼主題和留言，才會顯示在發佈網站上。預設為未勾選。

* **[!UICONTROL 關閉]**
如果勾選，論壇將不會出現新問題和評論。預設為未勾選。

* **[!UICONTROL 富格文本編]**
輯器如果選中此選項，則主題和注釋可以與標籤一起輸入。預設為未勾選。

* **[!UICONTROL 允許]**
標籤如果勾選此選項，允許成員將標籤標籤新增至其貼文(請參 **[!UICONTROL 閱標]** 記欄位標籤)。預設為未勾選。

* **[!UICONTROL 允許文]**
件上載如果選中，允許將檔案附件添加到問題或注釋中。預設為未勾選。

* **[!UICONTROL 最大檔案大]**
小僅在 
`Allow File Uploads` 已勾選。此欄位將限制已上傳檔案的大小（以位元組為單位）。 預設值為104857600(10 Mb)。

* **[!UICONTROL 允許的檔案類]**
型僅在 
`Allow File Uploads` 已勾選。以逗號分隔的副檔名清單，並以&quot;dot&quot;分隔。 例如：.jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定任何檔案類型，則不允許上傳未指定的檔案類型。 未指定預設值，因此允許所有檔案類型。

* **[!UICONTROL 最大附加影像檔案大]**
小只有在勾選「允許檔案上傳」時，才相關。上傳的影像檔案的位元組數上限。 預設值為2097152(2 Mb)。

* **[!UICONTROL 允許]**
下列若勾選，請為論壇貼文加入下列功能，讓會員得 [](notifications.md) 知新貼文。預設為未勾選。

* **[!UICONTROL 允許]**
釘選如果勾選，論壇主題可能會釘選至主題清單的頂端。預設為未勾選。

* **[!UICONTROL 允許電子]**
郵件訂閱如果勾選，允許會員透過電子郵件（訂閱）收到新[貼文](subscriptions.md)。需要檢查`Allow Following`並配置[電子郵件](email.md)。 預設為未勾選。

* **[!UICONTROL 允許]**
回覆如果勾選，允許回覆張貼至問題的留言。預設為未勾選。

* **[!UICONTROL 允許使用者刪除留言和主]**
題如果勾選，允許成員刪除他們張貼的留言和問題。預設為未勾選。

* **[!UICONTROL 允許投]**
票如果勾選，請將「投票」功能加入問題。預設為未勾選。

* **[!UICONTROL 將選定答案移至頂]**
端如果勾選，第一個顯示的答案是選定答案。已勾選預設值。

* **[!UICONTROL 顯示]**
標章如果勾選，請使用成員的 [](implementing-scoring.md) 部落格項目顯示已獲得和已指派的標章。預設為未勾選。

* **[!UICONTROL 若勾選「]**
允許精選內容」，此構想即可識別為 [精選內容](featured.md)。預設為未勾選。

#### 使用者協調標籤{#user-moderation-tab}

在&#x200B;**[!UICONTROL 使用者協調]**&#x200B;標籤下，指定如何管理已張貼的主題（問題）和答案（使用者產生的內容）。 如需詳細資訊，請參閱[協調使用者產生的內容](moderate-ugc.md)。

* **[!UICONTROL 拒絕]**
答案如果勾選，可信任的成員協調者將可拒絕張貼的答案，並防止答案出現在公開問答論壇中。預設為未勾選。

* **[!UICONTROL 關閉／重新開]**
啟主題如果勾選，受信任的成員協調者可關閉問題（主題）以進一步編輯和回答，也可重新開啟問題。預設為未勾選。

* **[!UICONTROL 移動]**
主題如果勾選，允許發佈端協調者移動問題。預設為未勾選。

* **[!UICONTROL 標籤]**
貼文如果勾選，允許成員將其他問題或答案標籤為不適當。預設為未勾選。

* **[!UICONTROL 標幟原]**
因清單如果勾選，允許成員從下拉式清單中選擇將問題或答案標籤為不適當的原因。預設為未勾選。

* **[!UICONTROL 自訂標幟原]**
因如果勾選，允許成員輸入其自己將問題或答案標示為不適當的原因。預設為未勾選。

* **[!UICONTROL 協調]**
臨界值輸入成員在通知協調者之前必須標籤問題或答案的次數。預設值為1（一次）。

* **[!UICONTROL 標幟]**
限制輸入問題或答案在隱藏於公開檢視之前必須標幟的次數。如果設為-1，則標籤的問題或答案永遠不會隱藏在公開檢視中。 否則，此數字必須大於或等於「協調臨界值」。 預設值為5。

#### 標籤欄位標籤{#tag-field-tab}

在&#x200B;**[!UICONTROL Tag欄位]**&#x200B;頁籤下，如果允許在&#x200B;**[!UICONTROL Settings]**&#x200B;頁籤下應用的標籤會根據選擇的名稱空間進行限制。

* **[!UICONTROL 允許的]**
名稱空間相關(如果 
`Allow Tagging` 在「設定」(Setting)選 **** 項卡下。可套用的標籤僅限於已勾選之命名空間類別中的標籤。 名稱空間清單包含「標準標籤」（預設命名空間）和「包含所有標籤」。 預設值未勾選，表示允許所有命名空間。

* **[!UICONTROL 建議]**
限制輸入要作為建議顯示給發佈到論壇的成員的標籤數。值 
`-1` 意味著沒有限制。預設值為0。

#### 排序設定頁籤{#sort-settings-tab}

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

## 網站訪客體驗{#site-visitor-experience}

### 確定答案{#identifying-answers}

使用`Select Answer`按鈕，一個答案可標示為正確或有用的答案。 一旦將「問題」標示為「已回答」，則必須使用`Unmark Chosen Answer`按鈕取消選取第一個答案，才能選取另一個答案。

一旦選擇為可行答案，則可使用`Unmark Chosen Answer`按鈕取消選擇。

在將答案選為可行答案後，主QnA頁面上的問題主題旁將顯示問題`Answered`的指示。

### 協調者和管理員{#moderators-and-administrators}

當登入的使用者具有協調者或管理員權限時，他們可以執行元件設定所允許的協調工作，不論問題或答案的作者為何。

他們也能識別答案。

### 成員 {#members}

當網站訪客登入時（視設定而定），他們可能會

* 張貼新問題
* 編輯或刪除他們撰寫的問題
* 也可以標籤其他人的問題或答案
* 可能會找出他們撰寫之問題的解答

### 匿名 {#anonymous}

未登入的網站訪客只能閱讀已張貼的問題和回覆、翻譯（如果支援），但不得新增任何問題或回覆，也不得標籤其他人的貼文。

## 其他資訊 {#additional-information}

如需詳細資訊，請參閱開發人員的[QnA Essentials](qna-essentials.md)頁面。

如需協調已張貼主題和留言的資訊，請參閱[協調使用者產生的內容](moderate-ugc.md)。

如需標籤已張貼的主題和留言，請參閱[標籤使用者產生的內容](tag-ugc.md)。

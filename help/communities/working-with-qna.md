---
title: 問答論壇功能
seo-title: Q&A Forum Feature
description: 將QnA論壇功能添加到頁
seo-description: Adding the QnA forum feature to a page
uuid: 006c0bf0-c230-4890-8080-65651f4b4dac
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: bbbe32bb-9d97-461e-822f-a7ddc6c9f9ef
exl-id: af16f4df-ed8e-40e4-b117-3d612e122947
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1240'
ht-degree: 0%

---

# 問答論壇功能 {#q-a-forum-feature}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 簡介 {#introduction}

QnA（問題和解答）論壇功能為社區成員提供了一個問題和解答區域：

* 建立新問題
* 內嵌影像（支援拖放）
* 檢視及回答問題
* 搜尋問題
* 幫助協調QnA內容
* 找出最佳答案
* 將QnA問題從一個頁面移至另一個頁面

本檔案的本節說明

* 將QnA論壇功能添加到AEM站點
* 的組態設定 `QnA`元件

## 新增問答論壇至頁面 {#adding-a-q-a-forum-to-a-page}

新增 `QnA` 在製作模式中，使用元件瀏覽器來尋找 `Communities / QnA` 並將其拖到應顯示QnA論壇的頁面上。

如需必要資訊，請造訪 [Communities元件基本知識](basics.md).

當 [必要的用戶端程式庫](qna-essentials.md#essentials-for-client-side) 包含在內，以下為方式 `QnA` 元件隨即出現：

![chlimage_1-280](assets/chlimage_1-280.png)

### 配置QnA {#configuring-qna}

選取已放置的 `QnA` 要存取的元件並選取 `Configure` 表徵圖，開啟「編輯」對話框。

![chlimage_1-281](assets/chlimage_1-281.png) ![chlimage_1-282](assets/chlimage_1-282.png)

#### 設定標籤 {#settings-tab}

在 **[!UICONTROL 設定]** 索引標籤，指定主題（問題）和回覆（答案）的設定：

* **[!UICONTROL 每頁主題]**
定義每頁顯示的問題/貼文數量。 預設為10。

* **[!UICONTROL 已審核]**
若勾選此選項，則張貼主題和留言必須經過核准，才會顯示在發佈網站上。 預設為未勾選。

* **[!UICONTROL 已關閉]**
如果勾選此選項，論壇將不會顯示新問題和評論。 預設為未勾選。

* **[!UICONTROL RTF編輯器]**
如果選中，則可以使用標籤輸入主題和注釋。 預設為未勾選。

* **[!UICONTROL 允許標籤]**
若勾選此選項，允許成員將標籤新增至其貼文(請參閱 **[!UICONTROL 標籤欄位]** 標籤)。 預設為未勾選。

* **[!UICONTROL 允許檔案上載]**
如果選中，則允許將檔案附件添加到問題或注釋中。 預設為未勾選。

* **[!UICONTROL 檔案大小上限]**
只有在 
`Allow File Uploads` 已勾選。 此欄位將限制上傳檔案的大小（以位元組為單位）。 預設為104857600(10 Mb)。

* **[!UICONTROL 允許的檔案類型]**
只有在 
`Allow File Uploads` 已勾選。 副檔名清單（以逗號分隔）以「點」分隔。 例如：.jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定了任何檔案類型，則不允許上載未指定的檔案類型。 未指定預設值，因此允許所有檔案類型。

* **[!UICONTROL 附加影像檔案的最大大小]**
僅在勾選「允許檔案上傳」時相關。 上傳的影像檔案可能具有的最大位元組數。 預設為2097152(2 Mb)。

* **[!UICONTROL 允許下列]**
若勾選此選項，請加入下列論壇貼文功能，讓成員可 [通知](notifications.md) 新貼文。 預設為未勾選。

* **[!UICONTROL 允許釘選]**
如果選中，論壇主題可以固定到主題清單的頂部。 預設為未勾選。

* **[!UICONTROL 允許電子郵件訂閱]**
若勾選此選項，可允許成員透過電子郵件([訂閱](subscriptions.md))。 需要 `Allow Following` 要檢查和 [電子郵件已設定](email.md). 預設為未勾選。

* **[!UICONTROL 允許回覆]**
如果勾選此選項，則允許對張貼至問題的留言進行回覆。 預設為未勾選。

* **[!UICONTROL 允許使用者刪除留言和主題]**
如果選中此選項，則允許成員刪除他們發佈的評論和問題。 預設為未勾選。

* **[!UICONTROL 允許投票]**
如果勾選此選項，請加入含有問題的投票功能。 預設為未勾選。

* **[!UICONTROL 將選定答案移到頂部]**
如果選中，則顯示的第一個答案為選定的答案。 已勾選預設值。

* **[!UICONTROL 顯示徽章]**
如果選中，則顯示已獲得和已分配 [徽章](implementing-scoring.md) 會員的部落格條目。 預設為未勾選。

* **[!UICONTROL 允許精選內容]**
若勾選，可將構想識別為 [精選內容](featured.md). 預設為未勾選。

#### 使用者協調標籤 {#user-moderation-tab}

在 **[!UICONTROL 使用者協調]** 索引標籤，指定如何管理已張貼的主題（問題）和答案（使用者產生的內容）。 如需詳細資訊，請參閱 [協調使用者產生的內容](moderate-ugc.md).

* **[!UICONTROL 拒絕回答]**
若勾選此選項，信任的成員協調者將可拒絕張貼的答案，並防止答案出現在公開的問答論壇上。 預設為未勾選。

* **[!UICONTROL 關閉/重新開啟主題]**
如果選中，受信任的成員協調者可以關閉問題（主題）以進一步編輯和回答，也可以重新開啟問題。 預設為未勾選。

* **[!UICONTROL 移動主題]**
如果勾選此選項，允許發佈端協調者移動問題。 預設為未勾選。

* **[!UICONTROL 標幟貼文]**
如果選中，則允許成員將他人的問題或答案標為不適當。 預設為未勾選。

* **[!UICONTROL 標誌原因清單]**
如果選中，則允許成員從下拉清單中選擇其標籤問題或答案為不適當的理由。 預設為未勾選。

* **[!UICONTROL 自訂標幟原因]**
如果選中，則允許成員輸入自己的理由，以標出問題或答案不適當。 預設為未勾選。

* **[!UICONTROL 協調臨界值]**
輸入在通知協調者之前，成員必須標籤某個問題或答案的次數。 預設為1（一次）。

* **[!UICONTROL 標幟限制]**
輸入在從公共視圖中隱藏某個問題或答案之前必須標籤的次數。 如果設為–1，則標籤的問題或答案永遠不會在公共視圖中隱藏。 否則，此數字必須大於或等於協調臨界值。 預設為5。

#### 標籤欄位標籤 {#tag-field-tab}

在 **[!UICONTROL 標籤欄位]** 標籤中，如果允許，則可套用的標籤 **[!UICONTROL 設定]** 標籤，會根據所選的命名空間而受到限制。

* **[!UICONTROL 允許的命名空間]**
若 
`Allow Tagging` 在 **設定** 標籤。 可套用的標籤僅限於所檢查命名空間類別中的標籤。 命名空間清單包含「標準標籤」（預設命名空間）以及「包含所有標籤」。 預設值未勾選，這表示允許所有命名空間。

* **[!UICONTROL 建議限制]**
輸入要作為建議顯示給論壇成員的標籤數。 值 
`-1` 表示沒有限制。 預設為0。

#### 排序設定標籤 {#sort-settings-tab}

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

## 網站訪客體驗 {#site-visitor-experience}

### 確定答案 {#identifying-answers}

一個答案可使用 `Select Answer` 按鈕。 將「問題」標示為「已回答」後，必須使用取消選取第一個答案，才能選取另一個答案 `Unmark Chosen Answer`按鈕。

一旦選取為可行答案，則可使用 `Unmark Chosen Answer` 按鈕。

一旦選擇了一個答案作為可行答案，就表明問題已經 `Answered`會顯示在QnA首頁面上的問題主題旁邊。

### 協調者與管理員 {#moderators-and-administrators}

當登入的使用者擁有版主或管理員權限時，無論是撰寫問題或回答的人，都能執行元件組態所允許的協調工作。

他們也有能力找出答案。

### 成員 {#members}

網站訪客登入時（視設定而定），可能會

* 發佈新問題
* 編輯或刪除他們撰寫的問題
* 也可以標示他人的問題或答案
* 可針對他們撰寫的問題找出答案

### 匿名 {#anonymous}

未登入的網站訪客只能閱讀已張貼的問題和答案、翻譯（如有支援），但不得新增問題和答案，也不得標籤其他人的貼文。

## 其他資訊 {#additional-information}

如需詳細資訊，請參閱 [QnA要點](qna-essentials.md) 頁面。

如需已張貼主題和留言的協調，請參閱 [協調使用者產生的內容](moderate-ugc.md).

有關標籤已發佈的主題和評論，請參閱 [標籤使用者產生的內容](tag-ugc.md).

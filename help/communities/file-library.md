---
title: 檔案庫功能
seo-title: 檔案庫功能
description: 「檔案庫」功能可讓登入的網站訪客上傳、管理和下載檔案
seo-description: 「檔案庫」功能可讓登入的網站訪客上傳、管理和下載檔案
uuid: 7da94703-8334-4c02-ba2a-55b5cde22e6c
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: cdcae09f-c3cb-471e-863f-b33130e9df0f
exl-id: c72b246d-442e-4841-810d-1045e83f60f9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 0%

---

# 檔案庫功能{#file-library-feature}

## 簡介 {#introduction}

檔案庫功能提供一個位置，讓登入網站訪客（社群成員）可以上傳、管理和下載社群網站中的檔案。

本檔案的本節說明

* 將檔案庫功能新增至AEM網站
* `File Library`元件的組態設定

## 將檔案庫添加到頁{#adding-a-file-library-to-a-page}

若要在製作模式中將`File Library`元件新增至頁面，請找出元件

* `Communities / File Library`

並將其拖曳到頁面上。

如需必要資訊，請造訪[Communities Components Basics](basics.md)。

包含[必要的用戶端程式庫](essentials-file-library.md#essentials-for-client-side)時，以下是`File Library`元件的顯示方式：

![chlimage_1-430](assets/chlimage_1-430.png)

## 配置檔案庫{#configuring-file-library}

選取要存取的放置`File Library`元件，並選取開啟編輯對話方塊的`Configure`圖示。

![chlimage_1-431](assets/chlimage_1-431.png) ![chlimage_1-432](assets/chlimage_1-432.png)

### 「注釋」頁簽{#comments-tab}

在&#x200B;**[!UICONTROL Comments]**&#x200B;標籤下，指定上傳檔案的備注是否及顯示方式：

* **[!UICONTROL 允許對檔案進行注]**
釋如果選中此選項，則允許對已上載的檔案進行注釋。預設為未勾選。

* **[!UICONTROL 每頁]**
留言數限制每頁顯示的留言數以及顯示的回覆數。預設為 
**10**.

* **[!UICONTROL 檔案大]**
小上限此值將限制上載的檔案大小。預設限制為104857600(10 Mb)。

* **[!UICONTROL 最大消]**
息長度可輸入到文本框中的最大字元數。預設為4096個字元。

* **[!UICONTROL 允許的檔]**
案類型以逗號分隔的副檔名清單，帶有&quot;點&quot;分隔符。例如：.jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定了任何檔案類型，則不允許指定那些未指定的檔案類型。 未指定預設值，因此允許所有檔案類型。

* **[!UICONTROL RTF編]**
輯器如果選中此選項，則可以使用標籤輸入注釋。預設為未勾選。

* **[!UICONTROL 刪]**
除注釋如果選中此選項，則允許用戶刪除自己的注釋。已勾選預設值。

* **[!UICONTROL 允]**
許標籤如果選中此選項，將啟用向檔案添加標籤的功能。預設為未勾選。

* **[!UICONTROL 允許]**
的命名空間如果勾選「允許標籤」，可用的標籤將僅限於已勾選的命名空間。如果未勾選任何項目，則允許所有項目。 預設值為所有命名空間。

* **[!UICONTROL 建議]**
限制如果勾選「允許標籤」，此設定會限制要顯示的建議標籤數。如果設為–1，則沒有限制。 預設為–1。

* **[!UICONTROL 允]**
許投票如果選中，將啟用檔案的投票能力。預設為未勾選。

* **[!UICONTROL 允]**
許下列若勾選此選項，則為部落格文章加入下列功能，以便通知 [](notifications.md) 成員新貼文。預設為未勾選。

* **[!UICONTROL 允許線程]**
式答復如果選中，則允許對已發佈的評論進行答復。預設為未勾選。

### 使用者協調標籤{#user-moderation-tab}

在&#x200B;**[!UICONTROL 使用者協調]**&#x200B;標籤下，設定留言的協調（如果允許留言）:

* **[!UICONTROL 預先協]**
調如果勾選此選項，留言必須先經過核准，才會顯示在發佈網站上。預設為未勾選。

* **[!UICONTROL 刪]**
除留言如果勾選此選項，則發佈留言的訪客將能夠刪除留言。已勾選預設值。

* **[!UICONTROL 拒絕]**
評論如果選中，允許受信任的成員審核者拒絕評論。預設為未勾選。

* **[!UICONTROL 關閉/重新開]**
啟注釋如果選中，允許受信任的成員協調者關閉和重新開啟注釋。預設為未勾選。

* **[!UICONTROL 標幟]**
留言如果勾選此選項，可讓訪客將留言標幟為不適當。預設為未勾選。

* **[!UICONTROL 標幟原]**
因清單若勾選此選項，允許訪客從下拉式清單中選擇將留言標幟為不適當的原因。預設為未勾選。

* **[!UICONTROL 自訂標]**
幟原因如果勾選此選項，可讓訪客輸入自己的原因，將留言標示為不適當。預設為未勾選。

* **[!UICONTROL 協調]**
臨界值輸入在通知協調者之前，訪客必須標籤留言的次數。預設為一次(
**1**)。

* **[!UICONTROL 標]**
簽限制輸入在從公共視圖中隱藏評論之前必須標籤它的次數。此數字必須大於或等於 
**協調臨界值**。預設為5。

## 其他資訊 {#additional-information}

如需詳細資訊，請參閱開發人員的[File Library Essentials](essentials-file-library.md)頁面。

有關已張貼主題和留言的調節，請參閱[調節用戶生成的內容](moderate-ugc.md)。

有關標籤已發佈的主題和評論，請參閱[標籤用戶生成的內容](tag-ugc.md)。

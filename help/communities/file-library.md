---
title: 檔案庫功能
seo-title: 檔案庫功能
description: 「檔案庫」功能可讓登入網站的訪客上傳、管理和下載檔案
seo-description: 「檔案庫」功能可讓登入網站的訪客上傳、管理和下載檔案
uuid: 7da94703-8334-4c02-ba2a-55b5cde22e6c
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: cdcae09f-c3cb-471e-863f-b33130e9df0f
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 0%

---


# 檔案庫功能{#file-library-feature}

## 簡介 {#introduction}

檔案庫功能提供登入網站訪客（社群成員）在社群網站上傳、管理和下載檔案的位置。

本節說明

* 新增檔案庫功能至AEM網站
* `File Library`元件的配置設定

## 將檔案庫添加到頁面{#adding-a-file-library-to-a-page}

若要在作者模式下將`File Library`元件新增至頁面，請找出該元件

* `Communities / File Library`

並將它拖曳至頁面上的位置。

如需必要資訊，請造訪[Communities Components Basics](basics.md)。

當包含[必要的用戶端程式庫](essentials-file-library.md#essentials-for-client-side)時，`File Library`元件的顯示方式如下：

![chlimage_1-430](assets/chlimage_1-430.png)

## 配置檔案庫{#configuring-file-library}

選擇要訪問的已放置的`File Library`元件，並選擇`Configure`表徵圖以開啟編輯對話框。

![chlimage_1-431](assets/chlimage_1-431.png) ![chlimage_1-432](assets/chlimage_1-432.png)

### 「注釋」頁籤{#comments-tab}

在&#x200B;**[!UICONTROL Comments]**&#x200B;標籤下，指定上傳檔案的注釋是否及顯示方式：

* **[!UICONTROL 允許對檔案加上注]**
釋如果勾選，則允許對已上傳檔案加上注釋。預設為未勾選。

* **[!UICONTROL 每頁]**
留言數限制每頁顯示的留言數，以及顯示的回覆數。預設值為 
**10**.

* **[!UICONTROL 檔案大]**
小上限此值將限制已上傳的檔案大小。預設限制為104857600(10 Mb)。

* **[!UICONTROL 最大消]**
息長度可輸入到文本框中的字元數上限。預設為4096個字元。

* **[!UICONTROL 允許的文]**
件類型以逗號分隔的副檔名清單，並使用&quot;dot&quot;分隔符。例如：.jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定了任何檔案類型，則不允許指定那些未指定的檔案類型。 未指定預設值，因此允許所有檔案類型。

* **[!UICONTROL Rich Text]**
Editor如果勾選，則可以輸入標注的注釋。預設為未勾選。

* **[!UICONTROL 刪除]**
注釋如果勾選，則允許使用者刪除自己的注釋。已勾選預設值。

* **[!UICONTROL 允許]**
標籤如果選中，則將啟用向檔案添加標籤的功能。預設為未勾選。

* **[!UICONTROL 允許的]**
名稱空間如果選中「允許標籤」，則可用的標籤將限制為選中的名稱空間。如果未勾選任何項目，則允許所有項目。 預設值是所有名稱空間。

* **[!UICONTROL 建議]**
限制如果勾選「允許標籤」，此設定會限制要顯示的建議標籤數。如果設定為-1，則沒有限制。 預設值為-1。

* **[!UICONTROL 允]**
許投票如果勾選，則會啟用檔案的投票能力。預設為未勾選。

* **[!UICONTROL 允許]**
下列若勾選，請為部落格文章加入下列功能，讓成員可獲 [](notifications.md) 知新貼文。預設為未勾選。

* **[!UICONTROL 允許線程化]**
回覆如果勾選，則允許回覆已張貼的留言。預設為未勾選。

### 使用者協調標籤{#user-moderation-tab}

在&#x200B;**[!UICONTROL 使用者協調]**&#x200B;標籤下，設定留言的協調（如果允許留言）:

* **[!UICONTROL 預先協]**
調如果勾選，留言必須先經過核准，才會顯示在發佈網站上。預設為未勾選。

* **[!UICONTROL 刪除]**
留言如果勾選，則張貼留言的訪客可加以刪除。已勾選預設值。

* **[!UICONTROL 拒絕]**
注釋如果選中，則允許受信任成員協調者拒絕注釋。預設為未勾選。

* **[!UICONTROL 關閉／重新開啟注]**
釋如果勾選，則允許受信任的成員協調者關閉並重新開啟注釋。預設為未勾選。

* **[!UICONTROL 標籤]**
注釋如果勾選，允許訪客將注釋標籤為不適當。預設為未勾選。

* **[!UICONTROL 標幟原]**
因清單如果勾選，允許訪客從下拉式清單中選擇將留言標籤為不適當的原因。預設為未勾選。

* **[!UICONTROL 自訂標幟原]**
因如果勾選，允許訪客輸入自己將留言標示為不適當的原因。預設為未勾選。

* **[!UICONTROL 協調]**
臨界值輸入訪客在通知協調者之前必須標籤留言的次數。預設值為一次(
**1**)。

* **[!UICONTROL 標幟]**
限制輸入在公開檢視中隱藏留言前，必須標幟留言的次數。此數字必須大於或等於 
**協調臨界值**。預設值為5。

## 其他資訊 {#additional-information}

如需詳細資訊，請參閱開發人員的[File Library Essentials](essentials-file-library.md)頁面。

如需協調已張貼主題和留言的資訊，請參閱[協調使用者產生的內容](moderate-ugc.md)。

如需標籤已張貼的主題和留言，請參閱[標籤使用者產生的內容](tag-ugc.md)。

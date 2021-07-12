---
title: 網站範本
seo-title: 網站範本
description: 如何存取網站範本主控台
seo-description: 如何存取網站範本主控台
uuid: d2f7556e-7e43-424e-82f1-41790aeb2d98
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 202d7dba-2b34-431d-b10f-87775632807f
role: Admin
exl-id: 5049c5df-c874-4c34-a96b-7944cd0353d5
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 3%

---

# 網站範本 {#site-templates}

站點模板控制台與[組模板](tools-groups.md)控制台非常相似，該控制台側重於社區組所關心的功能。

>[!NOTE]
>
>建立[社群網站](sites-console.md)、[社群網站範本](sites.md)、[社群群組範本](tools-groups.md)和[社群功能](functions.md)的主控台僅用於製作環境。

## 網站範本主控台 {#site-templates-console}

在製作環境中，前往社群網站主控台

* 從全局導航：**[!UICONTROL 工具>社群>網站範本]**

此控制台顯示可從中建立[社區站點](sites-console.md)的模板，並允許建立新的站點模板。

![chlimage_1-18](assets/chlimage_1-18.png)

## 建立網站範本 {#create-site-template}

若要開始建立新網站範本，請選取`Create`。

這會顯示包含3個子面板的網站編輯器面板：

### 基本資訊 {#basic-info}

![chlimage_1-19](assets/chlimage_1-19.png)

在「基本資訊」面板上，會設定名稱、說明，以及範本是否啟用或停用：

* **[!UICONTROL 社區站點模板名]**
稱模板名稱id

* **[!UICONTROL 社區站點模板說]**
明模板說明

* **[!UICONTROL 禁用/啟]**
用切換開關控制模板是否可引用

### 縮圖 {#thumbnail}

![chlimage_1-20](assets/chlimage_1-20.png)

（可選）選取「上傳影像」圖示，以向社群網站的建立者顯示縮圖以及名稱和說明。

### 結構 {#structure}

![chlimage_1-21](assets/chlimage_1-21.png)

若要新增社群功能，請依網站功能表連結的顯示順序從右側拖曳至左側。 建立網站時，樣式會套用至範本。

例如，如果您想要首頁，請從程式庫拖曳Page函式，並放置在範本產生器下。 這會導致頁面設定對話方塊開啟。 有關配置對話框的資訊，請參閱[函式控制台](functions.md)。

根據此範本，繼續拖放社群網站所需的任何其他社群功能。

頁面函式提供空白頁面。 群組功能提供在社群網站內建立群組網站（子社群）的功能。

>[!CAUTION]
>
>群組函式必須&#x200B;*不*&#x200B;是站點結構中的&#x200B;*第一個或唯一的*&#x200B;函式。
>
>必須先包含並列出任何其他函式，例如[page函式](functions.md#page-function)。

![chlimage_1-22](assets/chlimage_1-22.png)

### 組功能的組模板 {#group-templates-for-groups-function}

在網站範本中加入群組函式時，設定需要指定在發佈環境中建立新群組時允許的群組範本選擇。

>[!CAUTION]
>
>組函式必須&#x200B;*不*&#x200B;是站點結構中的&#x200B;*第一個或唯一的*&#x200B;函式。

![chlimage_1-23](assets/chlimage_1-23.png)

通過選擇兩個或多個社區組模板，在社區中實際建立新組時，可向組管理員提供選擇。

![chlimage_1-24](assets/chlimage_1-24.png)

## 編輯網站範本 {#edit-site-template}

在主[站點模板控制台](#site-templates-console)中查看站點模板時，可以選擇現有站點模板進行編輯。

此程式提供與建立網站範本[相同的面板。](#create-site-template)

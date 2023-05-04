---
title: 網站範本
seo-title: Site Templates
description: 如何存取網站範本主控台
seo-description: How to access the Site Templates console
uuid: d2f7556e-7e43-424e-82f1-41790aeb2d98
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 202d7dba-2b34-431d-b10f-87775632807f
role: Admin
exl-id: 5049c5df-c874-4c34-a96b-7944cd0353d5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 4%

---

# 網站範本 {#site-templates}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

「網站範本」主控台與 [群組範本](tools-groups.md) 主控台，專注於社群群組感興趣的功能。

>[!NOTE]
>
>建立 [社群網站](sites-console.md), [社群網站範本](sites.md), [社群群組範本](tools-groups.md) 和 [社群功能](functions.md) 僅供製作環境使用。

## 網站範本主控台 {#site-templates-console}

在製作環境中，前往社群網站主控台

* 從全局導航： **[!UICONTROL 工具>社群>網站範本]**

此主控台會顯示 [社群網站](sites-console.md) 可建立，並允許建立新網站範本。

![chlimage_1-18](assets/chlimage_1-18.png)

## 建立網站範本 {#create-site-template}

若要開始建立新網站範本，請選取 `Create`.

這會顯示包含3個子面板的網站編輯器面板：

### 基本資訊 {#basic-info}

![chlimage_1-19](assets/chlimage_1-19.png)

在「基本資訊」面板上，會設定名稱、說明，以及範本是否啟用或停用：

* **[!UICONTROL 社區站點模板名稱]**
範本名稱id

* **[!UICONTROL 社群網站範本說明]**
範本說明

* **[!UICONTROL 禁用/啟用]**
控制模板是否可引用的切換開關

### 縮圖 {#thumbnail}

![chlimage_1-20](assets/chlimage_1-20.png)

（可選）選取「上傳影像」圖示，以向社群網站的建立者顯示縮圖以及名稱和說明。

### 結構 {#structure}

![chlimage_1-21](assets/chlimage_1-21.png)

若要新增社群功能，請依網站功能表連結的顯示順序從右側拖曳至左側。 建立網站時，樣式會套用至範本。

例如，如果您想要首頁，請從程式庫拖曳Page函式，並放置在範本產生器下。 這會導致頁面設定對話方塊開啟。 請參閱 [函式主控台](functions.md) ，了解有關配置對話框的資訊。

根據此範本，繼續拖放社群網站所需的任何其他社群功能。

頁面函式提供空白頁面。 群組功能提供在社群網站內建立群組網站（子社群）的功能。

>[!CAUTION]
>
>組函式必須 *not* be *第一，也不是唯一* 功能。
>
>任何其他函式，例如 [頁面函式](functions.md#page-function)，必須包含在內並列出。

![chlimage_1-22](assets/chlimage_1-22.png)

### 組功能的組模板 {#group-templates-for-groups-function}

在網站範本中加入群組函式時，設定需要指定在發佈環境中建立新群組時允許的群組範本選擇。

>[!CAUTION]
>
>組函式必須 *not* be *第一，也不是唯一* 功能。

![chlimage_1-23](assets/chlimage_1-23.png)

通過選擇兩個或多個社區組模板，在社區中實際建立新組時，可向組管理員提供選擇。

![chlimage_1-24](assets/chlimage_1-24.png)

## 編輯網站範本 {#edit-site-template}

在主要 [網站範本主控台](#site-templates-console)，您可以選取現有網站範本進行編輯。

此程式提供與 [建立網站範本](#create-site-template).

---
title: 群組範本
seo-title: Group Templates
description: 如何存取群組範本主控台
seo-description: How to access the Group Templates console
uuid: a3c6dfe6-f973-4dcf-9c66-ea52cbe56630
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 9a862756-58e8-47c0-a4b4-5d4aaac021e4
role: Admin
exl-id: ac399a66-0f3b-4f95-969e-a4109c260d1d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 3%

---

# 群組範本 {#group-templates}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

群組範本主控台與 [網站範本](sites.md) 控制台。 這兩者都是構成社區站點的一組預佈線頁面和功能的藍圖。 區別在於，網站範本是用於主要社群，而群組範本是用於社群群組（巢狀內嵌於主要社群中的子社群）。

社群群組已整合至網站範本，方法是將 [組函式](functions.md#groups-function) （這不能是範本中的第一個或唯一函式）。

As of Communities [功能包1](deploy-communities.md#latestfeaturepack)，則可在群組範本中加入「群組」函式，以巢狀內嵌群組。

在採取動作建立新社群群組時，會選取群組的範本（結構）。 選擇取決於將「組」功能添加到站點或組模板時的配置方式。

>[!NOTE]
>
>建立 [社群網站](sites-console.md), [社群網站範本](sites.md), [社群群組範本](tools-groups.md) 和 [社群功能](functions.md) 僅供製作環境使用。

## 群組範本主控台 {#group-templates-console}

在製作環境中，若要存取群組範本主控台

* 從全局導航： **[!UICONTROL 工具>社群>群組範本]**

此主控台會顯示 [社群網站](sites-console.md) 可以建立，並允許建立新的群組範本。

![組板](assets/groupstemplate.png)

## 建立群組範本 {#create-goup-template}

若要開始建立新群組範本，請選取 **[!UICONTROL 建立]**

這會顯示包含3個子面板的網站編輯器面板：

### 基本資訊 {#basic-info}

![chlimage_1-96](assets/chlimage_1-96.png)

在「基本資訊」面板上，會設定名稱、說明，以及範本是否啟用或停用：

* **[!UICONTROL 新群組範本名稱]**
範本名稱id

* **[!UICONTROL 說明]**
範本說明

* **[!UICONTROL 禁用/啟用]**
控制模板是否可引用的切換開關

### 縮圖 {#thumbnail}

![chlimage_1-97](assets/chlimage_1-97.png)

（可選）選取「上傳影像」圖示，以向社群網站的建立者顯示縮圖以及名稱和說明。

### 結構 {#structure}

>[!CAUTION]
>
>若使用AEM 6.1 Communities FP4或更舊版本，請勿將群組函式新增至群組範本。
>
>巢狀群組功能可從Communities開始使用 [FP1](communities.md#latestfeaturepack).
>
>仍不允許將群組函式新增為範本中的第一個或唯一的函式。

![grtemplateeditor](assets/grptemplateeditor.png)

若要新增社群功能，請依網站功能表連結的顯示順序從右側拖曳至左側。 建立網站時，樣式會套用至範本。

例如，如果您想要論壇，請從程式庫拖曳論壇函式，放置到範本產生器下。 這會導致論壇設定對話方塊開啟。 請參閱 [函式主控台](functions.md) ，了解有關配置對話框的資訊。

根據此範本，繼續拖放子社群網站（群組）所需的任何其他社群功能。

![拖曳功能](assets/dragfunctions.png)

將所有所需函式拖放至範本產生器區域並完成設定後，請選取 **[!UICONTROL 儲存]** 在右上角。

## 編輯群組範本 {#edit-group-template}

在主目錄中檢視社群群組時 [群組範本主控台](#group-templates-console)，您可以選取現有的群組範本進行編輯。

編輯群組範本不會影響已從範本建立的社群網站。 可以直接 [編輯社群網站](sites-console.md#modify-structure)的結構。

此程式提供與 [建立群組範本](#create-goup-template).

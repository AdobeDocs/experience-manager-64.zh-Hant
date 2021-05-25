---
title: 群組範本
seo-title: 群組範本
description: 如何存取群組範本主控台
seo-description: 如何存取群組範本主控台
uuid: a3c6dfe6-f973-4dcf-9c66-ea52cbe56630
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 9a862756-58e8-47c0-a4b4-5d4aaac021e4
role: Administrator
exl-id: ac399a66-0f3b-4f95-969e-a4109c260d1d
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 2%

---

# 群組範本 {#group-templates}

「組模板」控制台與「[站點模板](sites.md)」控制台非常相似。 這兩者都是構成社區站點的一組預佈線頁面和功能的藍圖。 區別在於，網站範本是用於主要社群，而群組範本是用於社群群組（巢狀內嵌於主要社群中的子社群）。

社區組通過包括[組函式](functions.md#groups-function)（該函式可能不是模板中的第一個或唯一函式）而合併到站點模板中。

自Communities [Feature Pack 1](deploy-communities.md#latestfeaturepack)起，可將「群組」功能加入群組範本內，以巢狀內嵌群組。

在採取動作建立新社群群組時，會選取群組的範本（結構）。 選擇取決於將「組」功能添加到站點或組模板時的配置方式。

>[!NOTE]
>
>建立[社群網站](sites-console.md)、[社群網站範本](sites.md)、[社群群組範本](tools-groups.md)和[社群功能](functions.md)的主控台僅用於製作環境。

## 組模板控制台{#group-templates-console}

在製作環境中，若要存取群組範本主控台

* 從全局導航：**[!UICONTROL 工具>社區>組模板]**

此控制台顯示可從中建立[社區站點](sites-console.md)的模板，並允許建立新的組模板。

![組板](assets/groupstemplate.png)

## 建立組模板{#create-goup-template}

若要開始建立新的組模板，請選擇&#x200B;**[!UICONTROL Create]**

這會顯示包含3個子面板的網站編輯器面板：

### 基本資訊 {#basic-info}

![chlimage_1-96](assets/chlimage_1-96.png)

在「基本資訊」面板上，會設定名稱、說明，以及範本是否啟用或停用：

* **[!UICONTROL 新組模板名]**
稱模板名稱id

* ****
說明範本說明

* **[!UICONTROL 禁用/啟]**
用切換開關控制模板是否可引用

### 縮圖 {#thumbnail}

![chlimage_1-97](assets/chlimage_1-97.png)

（可選）選取「上傳影像」圖示，以向社群網站的建立者顯示縮圖以及名稱和說明。

### 結構 {#structure}

>[!CAUTION]
>
>若使用AEM 6.1 Communities FP4或更舊版本，請勿將群組函式新增至群組範本。
>
>自Communities [FP1](communities.md#latestfeaturepack)起，巢狀群組功能即可使用。
>
>仍不允許將群組函式新增為範本中的第一個或唯一的函式。

![grtemplateeditor](assets/grptemplateeditor.png)

若要新增社群功能，請依網站功能表連結的顯示順序從右側拖曳至左側。 建立網站時，樣式會套用至範本。

例如，如果您想要論壇，請從程式庫拖曳論壇函式，放置到範本產生器下。 這會導致論壇設定對話方塊開啟。 有關配置對話框的資訊，請參閱[函式控制台](functions.md)。

根據此範本，繼續拖放子社群網站（群組）所需的任何其他社群功能。

![拖曳功能](assets/dragfunctions.png)

將所有需要的函式拖放至範本產生器區域並完成設定後，請選取右上角的&#x200B;**[!UICONTROL Save]**。

## 編輯群組範本{#edit-group-template}

在主[組模板控制台](#group-templates-console)中查看社區組時，可以選擇現有組模板進行編輯。

編輯群組範本不會影響已從範本建立的社群網站。 可以直接[編輯社區站點](sites-console.md#modify-structure)的結構。

此程式提供與建立群組範本[相同的面板。](#create-goup-template)

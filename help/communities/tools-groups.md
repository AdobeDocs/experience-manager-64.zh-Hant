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
translation-type: tm+mt
source-git-commit: 13d890d08a032fe4eef1dac793dcf2a3e682a52c
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 2%

---


# 群組範本 {#group-templates}

「群組範本」主控台與[網站範本](sites.md)主控台非常類似。 兩者都是構成社群網站的預先連線頁面和功能的藍圖。 區別在於，網站範本是主社群的範本，而群組範本是社群群組（主社群內巢狀的子社群）的範本。

社區組通過包括[Groups函式](functions.md#groups-function)（該函式可能不是模板中的第一個或唯一的函式）而合併到站點模板中。

從Communities [功能套件1](deploy-communities.md#latestfeaturepack)開始，您就可將群組功能加入群組範本中，以巢狀內嵌群組。

在採取建立新社群群組的動作時，會選取群組的範本（結構）。 選取範圍取決於新增至網站或群組範本時，群組功能的設定方式。

>[!NOTE]
>
>用於建立[社區站點](sites-console.md)、[社區站點模板](sites.md)、[社區組模板](tools-groups.md)和[社區功能](functions.md)的控制台僅用於作者環境。

## 群組範本主控台{#group-templates-console}

在作者環境中，若要觸及群組範本主控台

* 從全域導覽：**[!UICONTROL 工具>社群>群組範本]**

此控制台顯示可從中建立[社區站點](sites-console.md)的模板，並允許建立新的組模板。

![組板](assets/groupstemplate.png)

## 建立組模板{#create-goup-template}

若要開始建立新群組範本，請選取&#x200B;**[!UICONTROL Create]**

這會顯示「網站編輯器」面板，其中包含3個子面板：

### 基本資訊 {#basic-info}

![chlimage_1-96](assets/chlimage_1-96.png)

在「基本資訊」面板上，會設定名稱、說明以及範本是啟用還是停用：

* **[!UICONTROL 新群組範本名]**
稱範本名稱ID

* **[!UICONTROL 說]**
明範本說明

* **[!UICONTROL 停用／啟]**
用切換開關控制範本是否可參考

### 縮圖 {#thumbnail}

![chlimage_1-97](assets/chlimage_1-97.png)

（可選）選取「上傳影像」圖示，以向社群網站的建立者顯示縮圖以及名稱和說明。

### 結構 {#structure}

>[!CAUTION]
>
>如果使用AEM 6.1 Communities FP4或更舊版本，請勿將群組函式新增至群組範本。
>
>從Communities [FP1](communities.md#latestfeaturepack)開始，即可使用巢狀群組功能。
>
>仍不允許將群組函式新增為範本中的第一個或唯一函式。

![grptemplateeditor](assets/grptemplateeditor.png)

若要新增社群功能，請依網站功能表連結的顯示順序，從右側拖曳至左側。 在建立網站時，樣式會套用至範本。

例如，如果您想要論壇，請將論壇函式從程式庫拖曳至範本產生器下方。 這將導致論壇配置對話框開啟。 有關配置對話框的資訊，請參見[functions console](functions.md)。

根據此範本，繼續拖放子社群網站（群組）所需的任何其他社群功能。

![拖曳功能](assets/dragfunctions.png)

將所有所需功能拖放到範本產生器區域並加以設定後，請選取右上角的「儲存」。****

## 編輯群組範本{#edit-group-template}

在主[組模板控制台](#group-templates-console)中查看社區組時，可以選擇現有的組模板進行編輯。

編輯群組範本不會影響已從範本建立的社群網站。 可以直接[編輯社區站點](sites-console.md#modify-structure)的結構。

此程式提供與[建立群組範本](#create-goup-template)相同的面板。

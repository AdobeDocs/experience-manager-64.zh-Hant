---
title: 使用任務
seo-title: Working with Tasks
description: 任務表示要針對內容完成的工作項，用於確定當前任務的完整程度
seo-description: Tasks represent items of work to be done on content and are used in projects to determine the level of completeness of current tasks
uuid: df4efb3f-8298-4159-acfe-305ba6b46791
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: projects
content-type: reference
discoiquuid: 1b79d373-73f4-4228-b309-79e74d191f3e
exl-id: 6480a0ba-ff65-42af-a14f-ce9fdbb7945f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 13%

---

# 使用任務{#working-with-tasks}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

任務表示要針對內容完成的工作項目。 當您被分配任務時，該任務將顯示在工作流收件箱中。 任務項在「類型」列中具有任務值。

項目中還使用任務來確定當前任務（包括工作流任務）的完整性級別。

## 追蹤專案進度 {#tracking-project-progress}

您可以透過查看專案內的活動/完成任務(由 **工作** 方塊。 項目進度可由以下方式確定：

* **** 任務表徵圖：項目詳細資訊頁面上的「任務表徵圖」(Task Tile)中描述了項目的整體進度。

* **** 任務清單：按一下「任務」表徵圖時，將顯示任務清單。此清單包含與項目相關的所有任務的詳細資訊。

同時列出工作流程任務，以及您直接在 **工作** 方塊。

### 任務表徵圖 {#task-tile}

如果項目有任何相關任務，則項目內將顯示「任務表徵圖」。 「任務表徵圖」(Task Tile)顯示項目的當前狀態。 這是以工作流程內的現有任務為基礎，不包含隨著工作流程進行而將產生的任何任務。 任務表徵圖中顯示以下資訊：

* 已完成任務的百分比
* 活動任務的百分比
* 逾期任務百分比

![chlimage_1-98](assets/chlimage_1-98.png)

### 查看或修改項目中的任務 {#viewing-or-modifying-the-tasks-in-a-project}

除了追蹤進度外，您也可能想要檢視或修改專案的詳細資訊。

#### 任務清單 {#task-list}

按一下「任務」表徵圖中的刪節號(...)，以顯示與項目相關的任務清單。 工作會依父工作流程分隔。 任務詳細資訊與元資料一起顯示，如到期日、受託人、優先順序和狀態。

![chlimage_1-99](assets/chlimage_1-99.png)

#### 任務詳細資料 {#task-details}

有關特定任務的詳細資訊，請在「任務清單」中，點選/按一下任務，然後開啟**任務詳細資**。

![chlimage_1-100](assets/chlimage_1-100.png)

### 查看和修改任務注釋 {#viewing-and-modifying-task-comments}

在「任務詳細資訊」中，您可以編輯或添加註釋。 此外，項目中的所有注釋都顯示在「注釋」區域中。

![chlimage_1-101](assets/chlimage_1-101.png)

### 添加任務 {#adding-tasks}

您可以新增任務至專案。 然後，這些任務會顯示在「任務」表徵圖中，並可在「通知收件箱」中使用，以對執行操作。

添加任務：

1. 在專案中，在「工 **作」方塊** ，點選/按一下+圖示。將打 **開「添加任務** 」窗口。
1. 輸入有關任務的資訊。 任務的標題及其分配給的組是必需的。 其他資訊（如內容路徑、說明、任務優先順序和到期日）為可選。 此外，您可以選取 **進階** 頁簽，輸入用於命名URL的任務名稱。

   ![chlimage_1-102](assets/chlimage_1-102.png)

1. 點選/按一下 **建立**.

## 使用收件箱中的任務 {#working-with-tasks-in-the-inbox}

訪問任務的另一種方法是從收件箱。 從收件匣，您可以開啟內容以實作所需的變更。 完成後，將任務狀態設定為「已完成」。 將任務分配給您所屬的用戶組時，任務也會顯示在收件箱中。 在這種情況下，組的任何成員都可以執行工作並完成任務。

![chlimage_1-103](assets/chlimage_1-103.png)

要完成任務，請選擇任務並按一下 **完成**. 向任務添加資訊，然後按一下 **完成**. 請參閱 [您的收件匣](/help/sites-authoring/inbox.md) 以取得更多資訊。

![chlimage_1-104](assets/chlimage_1-104.png)

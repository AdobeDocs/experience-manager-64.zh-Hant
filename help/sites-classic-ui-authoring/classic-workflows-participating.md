---
title: 參與工作流程
seo-title: 參與工作流程
description: 工作流程通常包括要求人員在頁面或資產上執行活動的步驟。 工作流選擇要執行活動的用戶或組，並將工作項指派給該人員或組。
seo-description: 工作流程通常包括要求人員在頁面或資產上執行活動的步驟。 工作流選擇要執行活動的用戶或組，並將工作項指派給該人員或組。
uuid: 04dcc8f2-dc11-430f-b0ae-47ef2cb069a2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 1d7a4889-82c5-4096-8567-8f66215a8458
exl-id: a4f0f0c4-3050-4348-8d51-2ca91839208c
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 5%

---

# 參與工作流程{#participating-in-workflows}

工作流程通常包括要求人員在頁面或資產上執行活動的步驟。 工作流選擇要執行活動的用戶或組，並將工作項指派給該人員或組。

## 處理工作項{#processing-your-work-items}

您可以執行以下操作來處理工作項：

* **完成**

   您可以完成項目，讓工作流程繼續進行下一個步驟。

* **委派**

   如果已指派步驟給您，但由於任何原因您無法採取動作，您可以將步驟委派給其他使用者或群組。

   可用於委派的用戶取決於為誰分配了工作項：

   * 如果工作項已分配給組，則組成員可用。
   * 如果工作項目被指派給某個組，然後被委派給某個用戶，則可使用組成員和組。
   * 如果工作項已分配給單個用戶，則無法委派工作項。

* **後退**

   如果您發現需要重複某個步驟或一系列步驟，您可以退後一步。 這可讓您選取先前在工作流程中發生的步驟，以進行重新處理。 工作流程會回到您指定的步驟，然後從那裡繼續。

## 參與工作流{#participating-in-a-workflow}

### 分配的工作流操作通知{#notifications-of-assigned-workflow-actions}

當您被指派工作項目時(例如「核准內 **容**」)，會出現各種警報和/或通知：

* 網站控制台的&#x200B;**狀態**&#x200B;欄會指出頁面何時處於工作流程中：

   ![workflowstatus-1](assets/workflowstatus-1.png)

* 當您或您所屬的組被分配工作項目作為工作流的一部分時，該工作項目將出現在您的AEM工作流收件箱中。

   ![工作流程收件匣](assets/workflowinbox.png)

### 完成參與者步驟{#completing-a-participant-step}

在您採取此動作後，表示您可以完成工作項目，從而允許工作流程繼續。 請使用以下過程完成工作項。

1. 選擇工作流步驟，然後按一下頂部導航欄中的&#x200B;**Complete**&#x200B;按鈕。
1. 在產生的對話方塊中，選取&#x200B;**下一步**;即，下一個執行步驟。 下拉式清單會顯示所有適當的目的地。 也可以輸入&#x200B;**注釋**。

   ![工作流程完成](assets/workflowcomplete.png)

   列出的步驟數取決於工作流模型的設計。

1. 按一下&#x200B;**OK**&#x200B;以確認動作。

### 委派參與者步驟{#delegating-a-participant-step}

使用以下過程來委派工作項。

1. 按一下頂端導覽列中的&#x200B;**委派**&#x200B;按鈕。
1. 在對話方塊中，使用下拉清單選擇&#x200B;**User**&#x200B;以委派工作項目。 您也可以新增&#x200B;**Comment**。

   ![workflowdelegate](assets/workflowdelegate.png)

1. 按一下&#x200B;**OK**&#x200B;以確認動作。

### 對參與者步驟{#performing-step-back-on-a-participant-step}執行退步

請依照下列程式退後。

1. 按一下頂端導覽列中的「上一步」按鈕。
1. 在產生的對話方塊中，選取上一步；也就是說，後續執行的步驟，即使這是在工作流程較早時發生的步驟。 下拉式清單會顯示所有適當的目的地。

   ![screen_shot_2018-08-10at155325](assets/screen_shot_2018-08-10at155325.jpg)

1. 按一下「確定」以確認動作。

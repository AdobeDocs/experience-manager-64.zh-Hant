---
title: 將工作流程套用至頁面
seo-title: 將工作流程套用至頁面
description: 工作流程可從網站主控台啟動，或在編輯頁面時從Sidekick啟動。
seo-description: 工作流程可從網站主控台啟動，或在編輯頁面時從Sidekick啟動。
uuid: 55f6f1d7-da54-4732-b9ff-b7479622db51
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 22712b73-90f2-4329-b32f-dbb7ce802d1d
exl-id: f10680e5-e8ae-49a0-ae52-3aa1f22b2d3e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 11%

---

# 將工作流程套用至頁面{#applying-workflows-to-pages}

套用工作流程時，需指定下列資訊：

* 要套用的工作流程。

   您可以套用您有權存取的任何工作流程 (由AEM管理員指派)。
* （可選）:

   * 提供啟動工作流程原因的資訊的備注。
   * 可協助識別使用者收件匣中工作流程例項的標題。

>[!NOTE]
>
>AEM管理員可使用[其他數種方法](/help/sites-administering/workflows-starting.md)來開始工作流程。

## 套用工作流程{#applying-workflows}

工作流程可從網站主控台啟動，或在編輯頁面時從Sidekick啟動。

**Websites**&#x200B;控制台中的&#x200B;**Status**&#x200B;列指示是否已將工作流應用到頁面：

![工作流程狀態](assets/workflowstatus.png)

### 從網站控制台{#starting-a-workflow-from-the-websites-console}啟動工作流

1. 開啟網站主控台。 ([http://localhost:4502/siteadmin](http://localhost:4502/siteadmin))
1. 在「網站」樹中，選擇要應用工作流的頁面的父級。
1. 在頁面清單中，選取頁面，然後按一下「工作流程」。
1. 在「開始工作流」對話框中，選擇要應用的工作流。 或者，輸入注釋和標題。 然後，按一下「開始」。

### 使用Sidekick {#starting-a-workflow-using-sidekick}啟動工作流

1. 開啟網站主控台。
1. 開啟必要的頁面。
1. 從Sidekick中選取Workflow索引標籤。
1. 展開&#x200B;**Workflow**&#x200B;對話框，允許您選擇&#x200B;**Workflow**，並可選地輸入&#x200B;**Workflow Title**&#x200B;和&#x200B;**Comment**。

   ![workflowstartsidekick](assets/workflowstartsidekick.png)

1. 按一下&#x200B;**「啟動工作流**」以啟動新的工作流實例，其中包含您配置的屬性和當前頁面作為裝載。 現在工作流程正在執行。

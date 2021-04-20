---
title: 將資產與活動串流整合
description: 說明的錄制功能AEM，以及如何設定AEM以錄制特定事件。
contentOwner: AG
feature: Asset Management
role: Developer
translation-type: tm+mt
source-git-commit: 4acf159ae1b9923a9c93fa15faa38c7f4bc9f759
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 1%

---


# 將資產與活動資料流{#integrating-assets-with-activity-stream}整合

Adobe Experience Manager(AEM)資產使用者會執行許多動作，例如建立、上傳和刪除資產。 您可以記錄這些動作，以便提供使用者所執行動作的記錄。 本節說明的錄制功AEM能，以及如AEM何設定以記錄特定事件。

## 效能注意事項和預設行為{#performance-considerations-and-default-behavior}

例如，進行批量導入時，此整合可能會佔用CPU和磁碟空間。 基於這些原因，AEM Assets與活動串流的整合預設會停用。

## 支援的動作事件{#supported-action-events}

可將下列事件設定為記錄：

* 已接受授權（已接受）
* 已建立資產(ASSET_CREATED)
* 已移動資產(ASSET_MOVED)
* 資產已移除(ASSET_REMOVED)
* 已拒絕授權（已拒絕）
* 已下載資產（已下載）
* 資產版本化（版本化）
* 資產版本已還原（已還原）
* 資產中繼資料已更新(METADATA_UPDATED)
* 已發佈至外部系統的資產(PUBLISHED_EXTERNAL)
* 資產的原始已更新(ORIGINAL_UPDATED)
* 資產轉譯已更新(RENDITION_UPDATED)
* 資產轉譯已移除(RENDITION_REMOVED)
* 已更新子資產(SUBASSET_UPDATED)
* 已移除子資產(SUBASSET_REMOVED)

## 配置AEM Assets事件記錄{#configuring-aem-assets-events-recording}

[Web控制台](/help/sites-deploying/configuring-osgi.md)提供對AEM Assets事件記錄器調諧的訪問。 要配置「AEM Assets事件記錄器」，請執行以下步驟：

1. 導航至&#x200B;**[!UICONTROL Web控制台]**

1. 按一下&#x200B;**[!UICONTROL Configuration]**。

1. 連按兩下&#x200B;**[!UICONTROL Day CQ DAM Event Recorder]**。

1. 選中&#x200B;**[!UICONTROL 啟用此服務]**。

1. 檢查您希望在用戶活動流中記錄哪些&#x200B;**[!UICONTROL 事件類型]**。

1. 按一下「**[!UICONTROL 儲存]**」。

## 讀取記錄的事件{#reading-recorded-events}

記錄的事件會儲存為活動。 您可以使用[ActivityManager API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html)以程式設計方式讀取它們。

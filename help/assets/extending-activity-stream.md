---
title: 將資產與活動資料流整合
description: 說明 [!DNL Experience Manager] 以及如何設定 [!DNL Experience Manager] 來記錄特定事件。
contentOwner: AG
feature: Asset Management
role: Developer
exl-id: c25a4da7-1c58-41cf-9ff6-c094b50208e6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 2%

---

# 將資產與活動資料流整合 {#integrating-assets-with-activity-stream}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets使用者可執行許多動作，例如建立、上傳和刪除Assets。 您可以記錄這些動作，以便提供使用者所執行動作的歷史記錄。 本節說明 [!DNL Experience Manager] 以及如何設定 [!DNL Experience Manager] 以記錄特定事件。

## 效能考量事項和預設行為 {#performance-considerations-and-default-behavior}

例如，進行批量導入時，此整合可能佔用CPU和磁碟空間。 基於這些原因 [!DNL Experience Manager] 預設會停用與活動資料流的資產整合。

## 支援的動作事件 {#supported-action-events}

可將下列事件設定為記錄：

* 已接受許可（已接受）
* 已建立資產(ASSET_CREATED)
* 已移動資產(ASSET_MOVED)
* 已移除資產(ASSET_REMOVED)
* 許可證已拒絕（已拒絕）
* 已下載資產（已下載）
* 資產版本控制（版本控制）
* 資產版本已還原（已還原）
* 已更新資產中繼資料(METADATA_UPDATED)
* 已發佈至外部系統的資產(PUBLISHED_EXTERNAL)
* 資產的原始更新(ORIGINAL_UPDATED)
* 已更新資產轉譯(RENDITION_UPDATED)
* 已移除資產轉譯(RENDITION_REMOVED)
* 子資產已更新(SUBASSET_UPDATED)
* 已移除子資產(SUBASSET_REMOVED)

## 設定 [!DNL Assets] 事件記錄 {#configuring-aem-assets-events-recording}

此 [Web主控台](/help/sites-deploying/configuring-osgi.md) 提供 [!DNL Assets] 事件記錄器調整。 若要設定 [!DNL Assets] 事件記錄器，請繼續：

1. 導覽至 **[!UICONTROL Web主控台]**

1. 按一下 **[!UICONTROL 設定]**.

1. 按兩下 **[!UICONTROL Day CQ DAM事件記錄器]**.

1. 檢查 **[!UICONTROL 啟用此服務]**.

1. 檢查 **[!UICONTROL 事件類型]** 您要記錄在使用者活動資料流中。

1. 按一下「**[!UICONTROL 儲存]**」。

## 讀取記錄的事件 {#reading-recorded-events}

記錄的事件會儲存為活動。 您可以使用 [ActivityManager API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html).

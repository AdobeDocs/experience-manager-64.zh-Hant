---
title: 設定通信管理解決方案
seo-title: Configuring a Correspondence Management solution
description: 了解如何為製作執行個體版本還原定義製作執行個體URL，並為公用執行個體啟用管理器定義發佈執行個體URL。
seo-description: Learn how to define an author instance URL for the author instance version restore and define the Publish instance URL for public instance activation manager.
uuid: 76b25004-fe47-44d7-9bed-7c0fd963306b
topic-tags: correspondence-management
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 186ca75c-638b-4057-826e-cd5d56aa0397
feature: Correspondence Management
exl-id: a062957d-a526-4c4b-bbc5-0cda8ab007a3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 2%

---

# 設定通信管理解決方案 {#configuring-a-correspondence-management-solution}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 定義VersionRestoreManagerImpl的作者實例URL {#defining-author-instance-url-for-versionrestoremanagerimpl}

使用下列步驟來定義製作執行個體版本還原的製作執行個體URL:

1. 前往 *https://網站：&lt;publishhost>:&lt;publishport>/lc/system/console/configMgr*. 使用OSGi Management Console使用者憑證登入。 預設憑證為管理員/管理員。
1. 尋找並按一下 **[!UICONTROL 編輯]** 表徵圖 **[!UICONTROL com.adobe.livecycle.content.activate.impl.VersionRestoreManagerImpl.name]** 設定。
1. 在 **[!UICONTROL VersionRestoreManager作者URL]** 欄位，指定VersionRestoreManager的Author實例的URL。

   **URL字串**:

   `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.VersionRestoreManager`

   >[!NOTE]
   >
   >如果負載平衡器前端有多個製作執行個體（叢集），請在 **[!UICONTROL VersionRestoreManager作者URL]** 欄位。

1. 按一下「**[!UICONTROL 儲存]**」。

## 定義ActivationManager實施的發佈執行個體URL（公用執行個體啟用管理器） {#defining-the-publish-instance-url-for-activationmanagerimpl-public-instance-activation-manager}

請依照下列步驟，定義公用執行個體啟動管理器的發佈執行個體URL:

1. 前往 *https://網站：&lt;authorhost>:&lt;authorport>/lc/system/console/configMgr*. 使用OSGi Management Console使用者憑證登入。 預設憑證為管理員/管理員。
1. 尋找並按一下 **[!UICONTROL 編輯]** 表徵圖 **[!UICONTROL com.adobe.livecycle.content.activate.impl.ActivationManagerImpl.name]** 設定。
1. 在 **[!UICONTROL ActivationManager發佈URL]** 欄位中，指定用於存取Publish執行個體ActivationManager的URL。 您可以提供下列URL。

   * **負載平衡器URL（建議）**:提供負載平衡器URL，如果在發佈伺服器陣列（多個非叢集發佈執行個體）前面有Web伺服器作為負載平衡器。
   * **發佈執行個體URL**:提供任何發佈執行個體URL，如果您有單一發佈執行個體，或發佈伺服器陣列前端的Web伺服器因任何限制而無法從製作環境存取。 如果指定的發佈例項停止運作，作者端會有一個要處理的備援機制。
   * **URL字串**:

      `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.activationManager`

1. 按一下「**[!UICONTROL 儲存]**」。

如需設定通信管理的詳細資訊，請參閱 [通信管理配置屬性](https://helpx.adobe.com/aem-forms/6-2/cm-configuration-properties.html).

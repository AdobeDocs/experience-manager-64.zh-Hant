---
title: 配置同步調度程式
seo-title: Configuring the synchronization scheduler
description: 了解如何移轉和同步資產、設定同步排程器，以及使用資料夾來排列資產。
seo-description: Learn how to migrate and sync assets, configure sync scheduler, and use folders to arrange assets.
uuid: a6445b45-9c1c-4483-a32e-453648c488c5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 2c8cea3c-8d8b-41d4-8ef9-a0ada8f86be6
role: Admin
exl-id: 7f1c4bac-accf-43e4-9439-89c5420d50f2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 1%

---

# 配置同步調度程式 {#configuring-the-synchronization-scheduler}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

依預設，同步排程器會每3分鐘執行一次，以透過LiveCycle工作台11同步儲存庫中修改和更新的所有資產。 同步程式完成後，包含表單和資源的應用程式就會顯示在AEM Forms使用者介面中。

## 更改同步調度程式的間隔 {#change-interval-of-the-synchronization-scheduler}

執行以下步驟更改同步調度程式的間隔：

1. 登入AEM Configuration Manager。 Configuration Manager的URL為 `https://[Server]:[Port]/lc/system/console/configMgr`

1. 找出並開啟 **FormsManager配置** 捆綁。

1. 指定 **同步調度程式頻率** 選項。

   頻率單位為分鐘。 例如，若要將排程器設定為每60分鐘執行一次，請指定60。

## 同步資產 {#synchronizing-assets}

您可以使用 **從存放庫同步資產** 選項，以手動同步資產。 執行下列步驟以手動同步資產：

1. 登入AEM Forms。 預設URL為 `https://[Server]:[Port]/lc/aem/forms/`.

   ![AEM Forms使用者介面](assets/aem_forms_ui.png)

   **圖：** *AEM Forms使用者介面*

1. 按一下 ![aem6forms_sync](assets/aem6forms_sync.png) 圖示。 如果您在最後設定的路徑上沒有任何資產，則會顯示對話方塊，如下所示。 按一下 **開始** 啟動同步。

   ![同步對話框](assets/migrate-and-syncronize.png)

   **圖：** *同步對話框*

## 排除同步錯誤 {#troubleshooting-synchronization-error}

您可以在工作流設計工具(LiveCycle工作台)中建立新應用程式。

如果新建立的應用程式和/content/dam/formsanddocuments上的資料夾名稱相同，則會出現錯誤「*根層級已存在與此應用程式同名的資產。*「 」已記錄。

若要解決衝突，請重新命名應用程式，並手動同步資產。

![資產同步對話方塊中的衝突](assets/sync-conflict.png)

**圖：** *資產同步對話方塊中的衝突*

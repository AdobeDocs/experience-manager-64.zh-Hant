---
title: 配置同步調度程式
seo-title: 配置同步調度程式
description: 了解如何移轉和同步資產、設定同步排程器，以及使用資料夾來排列資產。
seo-description: 了解如何移轉和同步資產、設定同步排程器，以及使用資料夾來排列資產。
uuid: a6445b45-9c1c-4483-a32e-453648c488c5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 2c8cea3c-8d8b-41d4-8ef9-a0ada8f86be6
role: Administrator
exl-id: 7f1c4bac-accf-43e4-9439-89c5420d50f2
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# 配置同步調度程式{#configuring-the-synchronization-scheduler}

依預設，同步排程器會每3分鐘執行一次，以透過LiveCycle工作台11同步儲存庫中修改和更新的所有資產。 同步程式完成後，包含表單和資源的應用程式就會顯示在AEM Forms使用者介面中。

## 更改同步調度程式{#change-interval-of-the-synchronization-scheduler}的間隔

執行以下步驟更改同步調度程式的間隔：

1. 登入AEM Configuration Manager。 Configuration Manager的URL為`https://[Server]:[Port]/lc/system/console/configMgr`

1. 找到並開啟&#x200B;**FormsManagerConfiguration**&#x200B;套件組合。

1. 為&#x200B;**同步調度程式頻率**&#x200B;選項指定新值。

   頻率單位為分鐘。 例如，若要將排程器設定為每60分鐘執行一次，請指定60。

## 同步資產{#synchronizing-assets}

您可以使用&#x200B;**從存放庫同步資產**&#x200B;選項，以手動同步資產。 執行下列步驟以手動同步資產：

1. 登入AEM Forms。 預設URL為`https://[Server]:[Port]/lc/aem/forms/`。

   ![AEM Forms使用者介面](assets/aem_forms_ui.png)

   **圖：** *AEM Forms使用者介面*

1. 按一下工具列中的![aem6forms_sync](assets/aem6forms_sync.png)圖示。 如果您在最後設定的路徑上沒有任何資產，則會顯示對話方塊，如下所示。 按一下&#x200B;**Start**&#x200B;以啟動同步。

   ![同步對話框](assets/migrate-and-syncronize.png)

   **圖：** *同步對話框*

## 排除同步錯誤{#troubleshooting-synchronization-error}

您可以在工作流設計工具(LiveCycle工作台)中建立新應用程式。

如果新建立的應用程式和/content/dam/formsanddocuments上的資料夾具有相同的名稱，則根級別已存在「*與此應用程式同名的資產」錯誤。*「 」已記錄。

若要解決衝突，請重新命名應用程式，並手動同步資產。

![資產同步對話方塊中的衝突](assets/sync-conflict.png)

**圖：** *資產同步對話方塊中的衝突*

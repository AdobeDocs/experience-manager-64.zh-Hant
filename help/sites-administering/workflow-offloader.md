---
title: 資產工作流程卸載程式
seo-title: Assets Workflow Offloader
description: 了解Assets工作流程卸載程式。
seo-description: Learn about the Assets Workflow Offloader.
uuid: d1c93ef9-a0e1-43c7-b591-f59d1ee4f88b
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: 91f0fd7d-4b49-4599-8f0e-fc367d51aeba
exl-id: 2ca8e786-042b-44f6-ac60-834eca64f79f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 3%

---

# 資產工作流程卸載程式{#assets-workflow-offloader}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Assets工作流程卸載程式可讓您啟用Adobe Experience Manager(AEM)Assets的多個例項，以減少主要（領導）例項的處理負載。 處理負載分配在領導實例和您添加到的各種卸載程式（工作器）實例之間。 分配資產的處理負載可提高AEM Assets處理資產的效率和速度。 此外，它可協助分配專用資源以處理特定MIME類型的資產。 例如，您可以在拓撲中分配特定節點，以僅處理InDesign資產。

## 配置卸載器拓撲 {#configure-offloader-topology}

使用Configuration Manager為領導實例添加URL，為領導實例上的連接請求添加卸載程式實例的主機名。

1. 點選/按一下AEM標誌，然後選擇 **工具** > **操作** > **Web主控台** 以開啟Configuration Manager。
1. 在Web控制台中，選擇 **Sling** >  **拓撲管理**.

   ![chlimage_1-44](assets/chlimage_1-44.png)

1. 在「拓撲管理」頁中，點選/按一下 **配置Discovery.Oak服務** 連結。

   ![chlimage_1-45](assets/chlimage_1-45.png)

1. 在「發現服務配置」頁中，指定領導實例的連接器URL，位於 **拓撲連接器URL** 欄位。

   ![chlimage_1-46](assets/chlimage_1-46.png)

1. 在 **拓撲連接器白名單** 欄位中，指定允許與引導實例連接的卸載程式實例的IP地址或主機名。 點選/按一下 **儲存**.

   ![chlimage_1-47](assets/chlimage_1-47.png)

1. 要查看連接到引線實例的卸載程式實例，請轉至 **工具** > **部署** > **拓撲** 並點選/按一下「叢集」檢視。

## 停用卸載 {#disable-offloading}

1. 點選/按一下AEM標誌，然後選擇 **工具** > **部署** > **卸載**. 此 **卸載瀏覽器** 頁面顯示主題和可使用主題的伺服器實例。

   ![chlimage_1-48](assets/chlimage_1-48.png)

1. 停用 *com/adobe/granite/workflow/offloading* 關於使用者互動以上傳或變更AEM資產的leader例項主題。

   ![chlimage_1-49](assets/chlimage_1-49.png)

## 在領導實例上配置工作流啟動器 {#configure-workflow-launchers-on-the-leader-instance}

設定工作流程啟動器以使用 **DAM更新資產卸載** 領導實例上的工作流，而不是 **Dam更新資產** 工作流程。

1. 點選/按一下AEM標誌，然後選擇 **工具** > **工作流程** > **啟動器** 開啟 **工作流程啟動器** 控制台。

   ![chlimage_1-50](assets/chlimage_1-50.png)

1. 找出事件類型的兩個啟動器設定 **已建立節點** 和 **已修改節點** 分別執行 **DAM更新資產** 工作流程。
1. 對於每個設定，請選取其前面的核取方塊，然後點選/按一下 **檢視屬性** 圖示來顯示 **啟動器屬性** 對話框。

   ![chlimage_1-51](assets/chlimage_1-51.png)

1. 從 **工作流程** 清單，選擇 **DAM更新資產卸載** 點選/按一下 **儲存**.

   ![chlimage_1-52](assets/chlimage_1-52.png)

1. 點選/按一下AEM標誌，然後選擇 **工具** > **工作流程** > **模型** 開啟 **工作流程模型** 頁面。
1. 選取 **DAM更新資產卸載** 工作流程，然後點選/按一下 **編輯** 顯示其詳細資訊。

   ![chlimage_1-53](assets/chlimage_1-53.png)

1. 顯示 **DAM工作流程卸載** 步驟，然後選擇 **編輯**. 驗證 **作業主題** 欄位 **一般引數** 頁簽。

   ![chlimage_1-54](assets/chlimage_1-54.png)

## 在卸載程式實例上禁用工作流啟動器 {#disable-the-workflow-launchers-on-the-offloader-instances}

停用執行 **DAM更新資產** 領導實例上的工作流。

1. 點選/按一下AEM標誌，然後選擇 **工具** > **工作流程** > **啟動器** 開啟 **工作流程啟動器** 控制台。

   ![chlimage_1-55](assets/chlimage_1-55.png)

1. 找出事件類型的兩個啟動器設定 **已建立節點** 和 **已修改節點** 分別執行 **DAM更新資產** 工作流程。
1. 對於每個設定，請選取其前面的核取方塊，然後點選/按一下 **檢視屬性** 圖示來顯示 **啟動器屬性** 對話框。

   ![chlimage_1-56](assets/chlimage_1-56.png)

1. 在**啟動**區段中，拖曳滑桿以停用工作流程啟動器，然後點選/按一下 **儲存** 來停用。

   ![chlimage_1-57](assets/chlimage_1-57.png)

1. 在領導者例項上傳任何類型的影像資產。 驗證縮圖是否產生，並由已卸載執行個體移回資產。

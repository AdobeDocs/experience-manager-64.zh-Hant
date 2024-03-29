---
title: 管理工作流程存取權
seo-title: Managing Access to Workflows
description: 了解如何管理工作流程的存取權。
seo-description: Learn how to manage access to Workflows.
uuid: 58f79b89-fe56-4565-a869-8179c1ac68de
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 5150867a-02a9-45c9-b2fd-e536b60ffa8c
exl-id: 9c588691-0649-4d59-ab97-ebadfcd1252c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 2%

---

# 管理工作流程存取權{#managing-access-to-workflows}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

根據使用者帳戶設定ACL以允許（或停用）啟動和參與工作流程。

## 工作流程所需的使用者權限 {#required-user-permissions-for-workflows}

若符合以下條件，可對工作流程採取動作：

* 您正在使用 `admin` 帳戶
* 帳戶已指派給預設群組 `workflow-users`:

   * 此組保留用戶執行工作流操作所需的所有權限。
   * 帳戶在此群組中時，它只能存取其啟動的工作流程。

* 帳戶已指派給預設群組 `workflow-administrators`:

   * 此群組擁有特權使用者監控及管理工作流程所需的所有權限。
   * 帳戶在此群組中時，它可以存取所有工作流程。

>[!NOTE]
>
>這些是最低要求。 您的帳戶也必須是指派的參與者或指派群組的成員，才能執行特定步驟。

## 設定工作流程存取權 {#configuring-access-to-workflows}

工作流模型繼承預設訪問控制清單(ACL)，以控制用戶與工作流交互的方式。 要自定義工作流的用戶訪問，請修改包含工作流模型節點的資料夾的儲存庫中的訪問控制清單(ACL):

* [將特定工作流模型的ACL應用於/var/workflow/models](/help/sites-administering/workflows-managing.md#apply-an-acl-for-the-specific-workflow-model-to-var-workflow-models)
* [在/var/workflow/models中建立子資料夾，並將ACL套用至該資料夾](/help/sites-administering/workflows-managing.md#create-a-subfolder-in-var-workflow-models-and-apply-the-acl-to-that)

>[!NOTE]
>
>有關使用CRXDE Lite配置ACL的資訊，請參見 [訪問權限管理](/help/sites-administering/user-group-ac-admin.md#access-right-management).

### 將特定工作流模型的ACL應用於/var/workflow/models {#apply-an-acl-for-the-specific-workflow-model-to-var-workflow-models}

如果工作流模型儲存在 `/var/workflow/models` 然後，您可以在資料夾中指定與該工作流相關的特定ACL:

1. 在網頁瀏覽器中開啟CRXDE Lite(例如 [http://localhost:4502/crx/de](http://localhost:4502/crx/de))。
1. 在節點樹中，選擇工作流模型資料夾的節點：

   `/var/workflow/models`

1. 按一下 **存取控制** 標籤。
1. 在 **本地訪問控制策略** (**訪問控制清單**)表格，按一下加號圖示 **添加條目**.
1. 在 **新增參加項目** 對話框添加具有以下屬性的新ACE:

   * **主體**: `content-authors`
   * **類型**: `Deny`
   * **權限**: `jcr:read`
   * **rep:glob**:特定工作流程的參考

   ![wf-108](assets/wf-108.png)

   此 **訪問控制清單** 表格現在包含 `content-authors` 在 `prototype-wfm-01` 工作流程模型。

   ![wf-109](assets/wf-109.png)

1. 按一下 **全部儲存**.

   此 `prototype-wfm-01` 工作流程不再適用於 `content-authors` 群組。

### 在/var/workflow/models中建立子資料夾，並將ACL套用至該資料夾 {#create-a-subfolder-in-var-workflow-models-and-apply-the-acl-to-that}

您的 [開發團隊可在子資料夾中建立工作流程](/help/sites-developing/workflows-models.md#creating-a-new-workflow) of

`/var/workflow/models`

可比較儲存在

`/var/workflow/models/dam/`

然後，您可以將ACL添加到資料夾本身。

1. 在網頁瀏覽器中開啟CRXDE Lite(例如 [http://localhost:4502/crx/de](http://localhost:4502/crx/de))。
1. 在節點樹中，為工作流模型資料夾中的單個資料夾選擇節點；例如：

   `/var/workflow/models/prototypes`

1. 按一下 **存取控制** 標籤。
1. 在 **適用的訪問控制策略** 表格，按一下加號圖示 **新增** 項目。
1. 在 **本地訪問控制策略** (**訪問控制清單**)表格，按一下加號圖示 **添加條目**.
1. 在 **新增參加項目** 對話框添加具有以下屬性的新ACE:

   * **主體**: `content-authors`
   * **類型**: `Deny`
   * **權限**: `jcr:read`

   >[!NOTE]
   >
   >與 [將特定工作流模型的ACL應用於/var/workflow/models](/help/sites-administering/workflows-managing.md#apply-an-acl-for-the-specific-workflow-model-to-var-workflow-models) 您可以包含rep:glob ，以限制對特定工作流程的存取。

   ![wf-110](assets/wf-110.png)

   此 **訪問控制清單** 表格現在包含 `content-authors` 在 `prototypes` 檔案夾。

   ![wf-111](assets/wf-111.png)

1. 按一下 **全部儲存**.

   中的模型 `prototypes` 資料夾不再可供 `content-authors` 群組。

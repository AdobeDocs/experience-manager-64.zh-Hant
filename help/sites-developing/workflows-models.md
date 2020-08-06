---
title: 建立工作流模型
seo-title: 建立工作流模型
description: 您可以建立工作流模型，以定義當使用者啟動工作流時執行的一系列步驟。
seo-description: 您可以建立工作流模型，以定義當使用者啟動工作流時執行的一系列步驟。
uuid: 53d94176-4d5f-4ab3-9628-6b7d44f81139
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 9d2dba11-0d2d-4aed-b941-c8ade9bb7bfa
translation-type: tm+mt
source-git-commit: 93d0bb274c87ecb272583aaf2cb04b0f5df9f4f7
workflow-type: tm+mt
source-wordcount: '2468'
ht-degree: 1%

---


# 建立工作流模型{#creating-workflow-models}

>[!CAUTION]
>
>如需使用傳統UI，請參閱 [AEM 6.3檔案以取得參考](https://helpx.adobe.com/experience-manager/6-3/sites-developing/workflows-models.html) 。

您可以建立工 [作流程模型](/help/sites-developing/workflows.md#model) ，以定義使用者啟動工作流程時所執行的一系列步驟。 您也可以定義模型屬性，例如工作流程是暫時性的，還是使用多個資源。

當用戶啟動工作流時，會啟動一個實例； 這是對應的執行時期模型，在您同步變更時 [建立](#sync-your-workflow-generate-a-runtime-model) 。

## 建立新工作流程 {#creating-a-new-workflow}

首次建立新的工作流模型時，它包含：

* 步驟：流 **[!UICONTROL 開始]** 和 **[!UICONTROL 流結束]**。

   這些代表工作流程的開始和結束。 這些步驟是必要步驟，無法編輯或移除。

* 名為「步 **驟** 1」的「參與 **者」步驟示例**。

   此步驟配置為將工作項目分配給工作流啟動器。 編輯或刪除此步驟，並視需要新增步驟。

要使用編輯器建立新工作流，請執行以下操作：

1. 開啟「工 **[!UICONTROL 作流模型]** 」控制台； 通過工 **[!UICONTROL 具]**、工 **[!UICONTROL 作流]**、 **[!UICONTROL 模型]** ，或例如：

   [http://localhost:4502/aem/workflow](http://localhost:4502/aem/workflow)

1. 依次選擇 **[!UICONTROL 建立]**、創 **[!UICONTROL 建模型]**。
1. 將出 **[!UICONTROL 現「添加工作流模型]** 」(Add Workflow Model)對話框。 在選擇「 **[!UICONTROL 完成]** 」之前，輸入「標題 **[!UICONTROL 」和「名稱」（可選）]******。
1. 新模型列在「工作流模型」( **[!UICONTROL Workflow Models]** )控制台中。
1. 選擇您的新工作流程，然後使用「編 [**[!UICONTROL 輯&#x200B;]**」將其開啟以進行設定](#editing-a-workflow):

   ![wf-01](assets/wf-01.png)

>[!NOTE]
>
>如果以寫程式方式建立模型（使用crx包），則還可以在以下位置建立子資料夾：
>
>`/var/workflow/models`
>
>例如， `/var/workflow/models/prototypes`
>
>然後，此資料夾可用於管 [理對該資料夾中模型的訪問](/help/sites-administering/workflows-managing.md#create-a-subfolder-in-var-workflow-models-and-apply-the-acl-to-that)。

## 編輯工作流程 {#editing-a-workflow}

您可以編輯任何現有的工作流模型，以：

* [定義步驟](#adding-a-step-to-a-model) 及其參 [數](#configuring-a-workflow-step)

* 配置工作流屬性 [，包括](#configuring-workflow-stages-that-show-workflow-progress)階段 [,](#creating-a-transient-workflow) 工作流是否為暫時性 [和／或使用多個資源](#configuring-a-workflow-for-multi-resource-support)

編輯 [**預設或舊版&#x200B;**（現成可用）工作流程有額外的步驟，以確保在您進行變更之前](#editing-a-default-or-legacy-workflow-for-the-first-time)[](/help/sites-developing/workflows-best-practices.md#locations-workflow-models)先進行安全復本。

完成工作流程的更新後，您必須使用「同步 **[!UICONTROL 」(Sync]** ) **[!UICONTROL 來生成運行時模型]**。 如需詳 [細資訊，請參閱同步您的工作流](#sync-your-workflow-generate-a-runtime-model) 。

### 同步您的工作流程——產生執行階段模型 {#sync-your-workflow-generate-a-runtime-model}

**Sync** （位於編輯器工具列中）會產生執行 [時期模型](/help/sites-developing/workflows.md#runtime-model)。 執行時期模型是使用者啟動工作流程時實際使用的模型。 如果您未同 **[!UICONTROL 步變更]** ，則在執行時期將無法使用變更。

當您（或任何其他使用者）對工作流程進行任何變更時，您必須使用 **[!UICONTROL Sync]** 來產生執行階段模型，即使個別對話方塊（例如步驟）有其自己的儲存選項亦然。

當變更與執行階段（儲存）模型同步時， **[!UICONTROL 會改]** 為顯示同步。

有些步驟包含必填欄位和／或內建驗證。 當這些條件不滿足時，當您嘗試同步模型時，會顯示 **[!UICONTROL 錯誤]** 。 例如，當沒有為「參與者」( **[!UICONTROL Participant]** )步驟定義參與者時：

![wf-21](assets/wf-21.png)

### 首次編輯預設或舊版工作流程 {#editing-a-default-or-legacy-workflow-for-the-first-time}

開啟「預設」( [Default)和／或「舊模型](/help/sites-developing/workflows.md#workflow-types) 」(Legacy model)進行編輯時：

* 步驟 **[!UICONTROL 瀏覽器]** （左側）不可用。
* 工具列( **[!UICONTROL 右側]** )中提供「編輯」(Edit)動作。
* 最初，模型及其屬性以只讀模式顯示為：

   * 預設工作流程位於 `/libs`
   * 舊版工作流程位於 `/etc`

選擇 **[!UICONTROL 編輯]** :

* 將工作流程復本放入 `/conf`
* 使步驟 **[!UICONTROL 瀏覽器]** 可用
* 可讓您進行變更

>[!NOTE]
>
>如需詳 [細資訊，請參閱工作流程模型](/help/sites-developing/workflows-best-practices.md#locations-workflow-models) 的位置。

![wf-22](assets/wf-22.png)

### 向模型添加步驟 {#adding-a-step-to-a-model}

您需要將步驟新增至模型以表示要執行的活動——每個步驟都會執行特定活動。 標準AEM例項中提供一系列步驟元件。

編輯模型時，可用步驟會顯示在「步驟」( **[!UICONTROL Steps]** )瀏覽器的各組中。 例如：

![wf-10](assets/wf-10.png)

>[!NOTE]
>
>如需隨AEM安裝的主要步驟元件的詳細資訊，請參閱工作 [流程步驟參考](/help/sites-developing/workflows-step-ref.md)。

**要向模型添加步驟**:

1. 開啟現有的工作流程模型以進行編輯。 從「工作 **[!UICONTROL 流模型]** 」(Workflows Model **[!UICONTROL )控制台中，選擇所需模型，然後選]**&#x200B;擇編輯。
1. 開啟「步 **[!UICONTROL 驟]** 」瀏覽器； 使用 **[!UICONTROL 頂端工具列最左側的「切換側面板]**」(Toggle Side Panel)。 您可以：

   * **[!UICONTROL 篩選]** ，以瞭解特定步驟。
   * 使用下拉式選擇器，將選取範圍限制為特定的步驟群組。
   * 選擇「顯示說明」圖 ![標wf-stepinfo-icon](assets/wf-stepinfo-icon.png) ，以顯示有關相應步驟的詳細資訊。

   ![wf-02](assets/wf-02.png)

1. 將適當的步驟拖動到模型中的所需位置。

   例如，參與 **[!UICONTROL 者步驟]**。

   將它新增至流程後，您就可 [以設定步驟](#configuring-a-workflow-step)。

   ![wf-03](assets/wf-03.png)

1. 視需要新增多個步驟或其他更新。

   在運行時，會按照步驟在模型中的顯示順序執行步驟。 添加步驟元件後，可將它們拖動到模型中的不同位置。

   您也可以複製、剪下、貼上、群組或刪除現有步驟； 和頁面編輯 [器一樣。](/help/sites-authoring/editing-content.md)

   使用工具欄選項也可以折疊／展開拆分步驟： ![wf-corvense-expand-toolbar-icon](assets/wf-collapseexpand-toolbar-icon.png)

1. 使用 **[!UICONTROL Sync]** （編輯器工具列）確認變更，以產生執行階段模型。

   如需詳 [細資訊，請參閱同步您的工作流](#sync-your-workflow-generate-a-runtime-model) 。

### 設定工作流程步驟 {#configuring-a-workflow-step}

您可以 **使用** 「步驟屬性」( **[!UICONTROL Step Properties)對話框來配置和自定義工作流步驟]** 的行為。

1. 要開啟步 **[!UICONTROL 驟的「步驟屬性]** 」對話框，請執行以下操作：

   * 點選工作流模型中的步驟，然後從元件工具列 **[!UICONTROL 選取「設定]** 」(Configure)。
   * 按兩下該步驟。

   >[!NOTE]
   >
   >如需隨AEM安裝的主要步驟元件的詳細資訊，請參閱工作 [流程步驟參考](/help/sites-developing/workflows-step-ref.md)。

1. 視需要 **[!UICONTROL 設定步驟]** 「屬性」; 可用的屬性取決於步驟類型，可能還有幾個頁籤可用。 例如，新工作流中 **[!UICONTROL 的預設「參與者步驟]**」(Participant Step `Step 1`)顯示為：

   ![wf-11](assets/wf-11.png)

1. 以勾號確認更新。
1. 使用 **[!UICONTROL Sync]** （編輯器工具列）確認變更，以產生執行階段模型。

   如需詳 [細資訊，請參閱同步您的工作流](#sync-your-workflow-generate-a-runtime-model) 。

### 建立臨時工作流 {#creating-a-transient-workflow}

建立新模型時， [可以建立「瞬態](/help/sites-developing/workflows.md#transient-workflows) 」工作流模型，或通過編輯現有模型來建立：

1. 開啟工作流程模 [型](#editing-a-workflow)。
1. 從工 **[!UICONTROL 具欄中選擇「工作流模型]** 」(Workflow Model)「屬性」(Properties)。
1. 在對話方塊中，啟用「暫 **[!UICONTROL 態工作流程]** 」(Transient Workflow)（或視需要停用）:

   ![wf-07](assets/wf-07.png)

1. 使用「儲存並關閉」 **[!UICONTROL 確認變更]**; 接著是 **[!UICONTROL Sync]** （編輯器工具列），以產生執行時期模型。

   如需詳 [細資訊，請參閱同步您的工作流](#sync-your-workflow-generate-a-runtime-model) 。

>[!NOTE]
>
>當您在瞬態模式中執行 [工作流程](/help/sites-developing/workflows.md#transient-workflows) ,AEM不會儲存任何工作流程記錄。 因此， [Timeline](/help/sites-authoring/basic-handling.md#timeline) 不會顯示任何與該工作流程相關的資訊。 [](/help/sites-authoring/basic-handling.md#timeline)

### 在Touch UI中提供工作流程模型 {#make-workflow-models-available-in-touchui}

如果Classic UI中有工作流程模型，但Touch UI的 **[!UICONTROL Timeline]** rail中的選取範圍快顯功能表中遺失，請依照設定進行，以便使用。 以下步驟說明如何使用稱為「請求啟 **[!UICONTROL 動」的工作流程模型]**。

1. 確認該型號未在啟用觸控的UI中使用。 使用路徑存取 `/assets.html/content/dam` 資產。 選取資產。 在左 **[!UICONTROL 側欄中]** ，開啟時間軸。 按一 **[!UICONTROL 下「開始工作流程]** 」，並確認快顯 **[!UICONTROL 清單中不存在「要求啟動]** 」模型。

1. 瀏覽「工 **[!UICONTROL 具>一般>標籤」]**。 選擇「 **[!UICONTROL 工作流]**」。

1. 選擇「 **[!UICONTROL 建立>建立標籤]**」。 將「 **[!UICONTROL 標題]** 」設 `DAM` 為 **[!UICONTROL ，將「]** 名稱 `dam`」設為。 選擇 **[!UICONTROL 提交]**。
   ![在工作流程模型中建立標籤](assets/workflow_create_tag.png)

1. 導覽至「 **[!UICONTROL 工具>工作流程>模型」]**。 選取「 **[!UICONTROL 要求啟動」]**，然後選 **[!UICONTROL 取「編輯」]**。

1. 選擇「 **[!UICONTROL 編輯]** 」，然後開啟「 **[!UICONTROL 工作流模型屬性」]**。 前往「基 **[!UICONTROL 本]** 」標籤。

1. 新增 `Workflow : DAM` 至 **[!UICONTROL 標籤]** 欄位。 使用勾選（勾選）確認選取範圍。

1. 確認新增標籤與「儲存並 **[!UICONTROL 關閉」]**。
   ![編輯模型的頁面屬性](assets/workflow_model_edit_activation1.png)

1. 使用同步完成 **[!UICONTROL 程式]**。 現在可在觸控式UI中使用工作流程。

### 為多資源支援配置工作流 {#configuring-a-workflow-for-multi-resource-support}

建立新模型或編輯現有模 [型時](/help/sites-developing/workflows.md#multi-resource-support) ，可為「多資源支援」配置工作流模型：

1. 開啟工作流程模 [型](#editing-a-workflow)。
1. 從工 **[!UICONTROL 具欄中選擇「工作流模型]** 」(Workflow Model)「屬性」(Properties)。

1. 在對話方塊中，啟 **[!UICONTROL 用多資源支援]** （或視需要停用）:

   ![wf-08](assets/wf-08.png)

1. 使用「儲存並關閉」 **[!UICONTROL 確認變更]**; 接著是 **[!UICONTROL Sync]** （編輯器工具列），以產生執行時期模型。

   如需詳 [細資訊，請參閱同步您的工作流](#sync-your-workflow-generate-a-runtime-model) 。

### 配置工作流階段（顯示工作流進度） {#configuring-workflow-stages-that-show-workflow-progress}

[工作流程階段](/help/sites-developing/workflows.md#workflow-stages) ，有助於在處理工作時視覺化工作流程的進度。

>[!CAUTION]
>
>如果工作流階段在「頁面屬性 ****」中定義，但未用於任何工作流步驟，則進度列將不顯示任何進度（無論當前工作流步驟如何）。

可用階段在工作流模型中定義； 可更新現有的工作流程模型以包含階段定義。 可以為工作流模型定義任意數量的階段。

要為工作流 **[!UICONTROL 定義階段]** ，請執行以下操作：

1. 開啟您的工作流程模型以進行編輯。
1. 從工 **[!UICONTROL 具欄中選擇「工作流模型]** 」(Workflow Model)「屬性」(Properties)。 然後開啟「階 **[!UICONTROL 段]** 」標籤。
1. 新增（並定位）您所需的 **[!UICONTROL 階段]**。 可以為工作流模型定義任意數量的階段。

   例如：

   ![wf-08-1](assets/wf-08-1.png)

1. 按一 **[!UICONTROL 下「儲存並關閉]** 」以儲存屬性。
1. 為工作流模型中的每個步驟指定一個階段。 例如：

   ![wf-09](assets/wf-09.png)

   一個階段可指派給多個步驟。 例如：

   | **步驟** | **分段** |
   |---|---|
   | 步驟 1 | 建立 |
   | 步驟 2 | 建立 |
   | 步驟 3 | 評論 |
   | 步驟 4 | 批准 |
   | 步驟 5 | 批准 |
   | 步驟 6 | 完成 |

1. 使用 **[!UICONTROL Sync]** （編輯器工具列）確認變更，以產生執行階段模型。

   如需詳 [細資訊，請參閱同步您的工作流](#sync-your-workflow-generate-a-runtime-model) 。

## 導出包中的工作流模型 {#exporting-a-workflow-model-in-a-package}

1. 使用「包管理器」( [Package Manager)建立新包](/help/sites-administering/package-manager.md#package-manager):

   1. 通過「工具」、「部署」、「包」導 **[!UICONTROL 航到「包管]**&#x200B;理器」 ********。
   1. 按一 **[!UICONTROL 下「建立套件]**」。
   1. 根據需要 **[!UICONTROL 指定「包名]**」和任何其他詳細資訊。
   1. 按一下&#x200B;**[!UICONTROL 「確定」]**。

1. 按一下 **[!UICONTROL 新包工具欄]** 上的「編輯」(Edit)。

1. 開啟「篩 **[!UICONTROL 選器]** 」標籤。

1. 選取「 **[!UICONTROL 新增篩選]** 」並指定工作流程模型設計的 *路徑*:

   `/conf/global/settings/workflow/models/<*your-model-name*>`

   按一 **[!UICONTROL 下完成]**。

1. 選取「 **[!UICONTROL 新增篩選]** 」並指定執行階段工作 *流程模型的路徑* :

   `/var/workflow/models/<*your-model-name*>`

   按一 **[!UICONTROL 下完成]**。

1. 為模型使用的任何自訂指令碼新增其他篩選器。
1. 按一 **[!UICONTROL 下「儲存]** 」以確認您的篩選定義。
1. 從包定 **[!UICONTROL 義的工具欄]** 中選擇「生成」。
1. 從包工 **[!UICONTROL 具欄]** ，選擇「下載」。

## 使用工作流程處理表單提交 {#using-workflows-to-process-form-submissions}

您可以設定表單，以便由選取的工作流程處理。 當使用者送出表單時，會建立新的工作流程例項，並將表單提交的資料當做其負載。

要配置要與表單一起使用的工作流，請執行以下操作：

1. 建立新頁面並開啟以供編輯。
1. 將表 **[!UICONTROL 單元]** 件新增至頁面。
1. 設定出 **[!UICONTROL 現在頁面中的]** 「表單開始」元件。
1. 使用「 **[!UICONTROL 開始工作流程]** 」，從可用的工作流程中選擇所需的工作流程：

   ![wf-12](assets/wf-12.png)

1. 使用勾號確認新表格設定。

## 測試工作流程 {#testing-workflows}

在測試工作流使用多種負載類型時，這是一個很好的做法； 包括與已開發的不同類型。 例如，如果您想要處理「資產」的工作流程，請將「頁面」設為裝載來測試，並確定不會擲回錯誤。

例如，請依下列方式測試您的新工作流程：

1. [從主控台啟動您的](/help/sites-administering/workflows-starting.md) 「工作流程」模型。
1. 定義裝 **[!UICONTROL 載]** ，並確認。

1. 視需要採取動作，以便工作流程繼續進行。
1. 在工作流程執行時監控記錄檔。

您也可以設定AEM，在記錄檔 **[!UICONTROL 中顯示]** DEBUG訊息。 請參 [閱記錄](/help/sites-deploying/configure-logging.md) ，以取得詳細資訊，當開發完成時，將「記錄層級 **[!UICONTROL 」設回]** 資訊 ****。

## Examples {#examples}

### 範例： 建立（簡單）工作流以接受或拒絕發佈請求 {#example-creating-a-simple-workflow-to-accept-or-reject-a-request-for-publication}

為了說明建立工作流的一些可能性，以下示例建立了工作流的變 `Publish Example` 化。

1. [建立新的工作流程模型](#creating-a-new-workflow)。

   新工作流程將包含：

   * **[!UICONTROL 流程啟動]**
   * `Step 1`
   * **[!UICONTROL 流程結束]**

1. 刪 `Step 1` 除（因為此示例的步驟類型錯誤）:

   * 按一下該步驟，然後從元件工具欄 **[!UICONTROL 中選擇]** 「刪除」(Delete)。 確認動作。

1. 從步驟瀏 **[!UICONTROL 覽器的「工作流]** 」選擇中，將「參與者步驟 **[!UICONTROL 」拖放到工作流上，並將其置於]** Flow Start **[!UICONTROL 和**]**Flow End**之間。
1. 要開啟屬性對話框，請執行以下操作：

   * 按一下參與者步驟，然後從元件工具欄 **[!UICONTROL 中選擇]** 「配置」(Configure)。
   * 按兩下參與者步驟。

1. 在「公 **[!UICONTROL 用]** 」標籤 `Validate Content` 中，輸入「 **[!UICONTROL 標題]** 」和「 **[!UICONTROL 說明」]**。
1. 開啟「使 **[!UICONTROL 用者／群組]** 」標籤：

   * Activate **[!UICONTROL Notify user via email]**.
   * 為「 `Administrator` 使用者/ `admin`群組」欄 **[!UICONTROL 位選取(]** )。

   >[!NOTE]
   >
   >對於要發送的電子郵件， [需要配置郵件服務和用戶帳戶詳細資訊](/help/sites-administering/notification.md)。

1. 用勾號確認更新。

   您將返回至工作流模型的概述，其中參與者步驟將重新命名為 `Validate Content`。

1. 將「或 **[!UICONTROL 分割]** 」拖曳至工作流程，並將其置於 `Validate Content` 「流程 **[!UICONTROL 端」之間]**。
1. 開啟 **[!UICONTROL Or Split]** for configuration。
1. 設定：

   * **[!UICONTROL 常見]**: 選擇 **[!UICONTROL 2分支]**
   * **[!UICONTROL 分支1]**: 選擇 **[!UICONTROL 預設路由]**。
   * **[!UICONTROL 分支2]**: 確 **[!UICONTROL 保未選擇預設路由]** 。

1. 確認您對 **[!UICONTROL OR Split的更新]**。
1. 將「參 **[!UICONTROL 與者步驟]** 」拖曳至左側分支、開啟屬性、指定下列值，然後確認變更：

   * **[!UICONTROL 標題]**: `Reject Publish Request`
   * **[!UICONTROL 使用者／群組]**: 例如， `projects-administrators`
   * **[!UICONTROL 透過電子郵件通知使用者]**: 啟用，讓使用者透過電子郵件獲得通知。

1. 將「 **[!UICONTROL 流程步驟]** 」拖曳至右側的分支，開啟屬性，指定下列值，然後確認變更：

   * **[!UICONTROL 標題]**: `Publish Page as Requested`
   * **[!UICONTROL 流程]**: 選擇「 `Activate Page`Select（選擇）」。 此程式會將選取的頁面發佈至發佈者例項。

1. 按一 **[!UICONTROL 下「同步]** （編輯器工具列）」以產生執行時期模型。

   如需詳 [細資訊，請參閱同步您的工作流](#sync-your-workflow-generate-a-runtime-model) 。

   您的新工作流程模型如下：

   ![wf-13](assets/wf-13.png)

1. 將此工作流應用到您的頁面，這樣當用戶移至「完成驗證內容 **** 」步驟時，他們可以選擇是按請求發佈頁面 **[!UICONTROL ，還是]**********&#x200B;按請求發佈請求拒絕發佈。

   ![chlimage_1-182](assets/chlimage_1-182.png)

### 範例： 定義OR分解的規則 {#example-defining-a-rule-for-an-or-split}

**[!UICONTROL 「OR分割]** 」步驟可讓您在工作流程中引入條件式處理路徑。

要定義OR規則，請執行以下操作：

1. 建立兩個指令碼並將其保存到儲存庫中，例如：

   `/apps/myapp/workflow/scripts`

   >[!NOTE]
   >
   >指令碼必須具有傳 [回 `check()`](#function-check) 布林值的函式。

1. 編輯工作流並將 **[!UICONTROL OR分割]** 添加到模型。
1. 編輯 **[!UICONTROL OR Split]** 的 **[!UICONTROL Branch 1屬性]**:

   * 將「值」(Value)設 **[!UICONTROL 置為]** ，將其定義為「缺 **[!UICONTROL 省路由]** 」(Default Route) `true`。
   * 作為 **[!UICONTROL 規則]**，設定指令碼的路徑。 例如：

      `/apps/myapp/workflow/scripts/myscript1.ecma`
   >[!NOTE]
   >
   >您可以視需要切換分支順序。

1. 編輯 **[!UICONTROL OR Split]** 的 **[!UICONTROL Branch 2屬性]**。

   * 作為 **[!UICONTROL 規則]**，設定指向其他指令碼的路徑。 例如：

      `/apps/myapp/workflow/scripts/myscript2.ecma`

1. 設定每個分支中各步驟的屬性。 請確定已 **[!UICONTROL 設定「使用者]** /群組」。
1. 按一 **下「同步** （編輯器工具列）」，將變更保留至執行階段模型。

   如需詳 [細資訊，請參閱同步您的工作流](#sync-your-workflow-generate-a-runtime-model) 。

#### 函式檢查() {#function-check}

>[!NOTE]
>
>請參 [閱使用ECMAScript](/help/sites-developing/workflows-customizing-extending.md#using-ecmascript)。

如果節點位於 `true` 以下位置，則返回以 `JCR_PATH` 下示例指令碼 `/content/we-retail/us/en`:

```
function check() {
    if (workflowData.getPayloadType() == "JCR_PATH") {
      var path = workflowData.getPayload().toString();
      var node = jcrSession.getItem(path);

      if (node.getPath().indexOf("/content/we-retail/us/en") >= 0) {
       return true;
      } else {
       return false;
      } 
     } else {
      return false;
     }
}
```

### 範例： 自訂啟動要求 {#example-customized-request-for-activation}

您可以自訂任何現成可用的工作流程。 若要進行自訂行為，請覆蓋適當工作流程的詳細資訊。

例如，請 **[!UICONTROL 求啟動]**。 此工作流程用於發佈 **[!UICONTROL Sites]** 內的頁面，當內容作者沒有適當的複製權限時會自動觸發。 如需詳 [細資訊，請參閱自訂頁面製作——自訂啟動工作流程要求](/help/sites-developing/customizing-page-authoring-touch.md#customizing-the-request-for-activation-workflow) 。

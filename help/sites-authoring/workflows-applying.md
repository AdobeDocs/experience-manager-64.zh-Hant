---
title: 將工作流程套用至頁面
seo-title: 將工作流程套用至頁面
description: 編寫時，您可以叫用工作流程以在頁面上執行動作；也可以套用多個工作流程。
seo-description: 編寫時，您可以叫用工作流程以在頁面上執行動作；也可以套用多個工作流程。
uuid: 8a1d16f8-69fc-4e3a-b72a-b799ea381024
contentOwner: Alison Heimoz
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 8556d20a-99bd-4942-b7b8-2db69f64e67c
exl-id: 05c52802-adfd-4b5f-a273-d6a261a00659
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 15%

---

# 將工作流程套用至頁面{#applying-workflows-to-pages}

編寫時，您可以叫用工作流程以在頁面上執行動作；您也可以套用多個工作流程。

套用工作流程時，需指定下列資訊：

* 要套用的工作流程。

   您可以套用您有權存取的任何工作流程 (由AEM管理員指派)。

* （可選）幫助標識用戶收件箱中工作流實例的標題。
* 工作流程裝載；這可以是一或多個頁面。

工作流程可從以下位置開始：

* **[Sites](#starting-a-workflow-from-the-sites-console)**&#x200B;控制台。
* 編輯頁面時，請從&#x200B;**[頁面資訊](#starting-a-workflow-from-the-page-editor)**。

>[!NOTE]
>
>另請參閱:
>
>* [如何將工作流程套用至DAM資產](/help/assets/assets-workflow.md)。
>* [使用專案工作流程](/help/sites-authoring/projects-with-workflows.md).
>



>[!NOTE]
>
>AEM管理員可以[使用數種其他方法開始工作流程](/help/sites-administering/workflows-starting.md)。

## 從Sites Console啟動工作流 {#starting-a-workflow-from-the-sites-console}

您可以從以下任一位置啟動工作流程：

* 「站點」工具欄的&#x200B;**[「建立」](#starting-a-workflow-from-the-sites-toolbar)**&#x200B;選項。
* Sites控制台的&#x200B;**[時間軸](#starting-a-workflow-from-the-timeline)**&#x200B;邊欄。

在這兩種情況下，您需要：

* [在「建立工作流程精靈」中指定「工作流程詳細資訊」](#specifying-workflow-details-in-the-create-workflow-wizard)。

### 從Sites工具欄啟動工作流{#starting-a-workflow-from-the-sites-toolbar}

您可以從&#x200B;**Sites**&#x200B;控制台的工具欄啟動工作流：

1. 導覽至並選取所需頁面。

1. 從工具列的&#x200B;**Create**&#x200B;選項中，您現在可以選取&#x200B;**Workflow**。

   ![screen_shot_2019-03-06at121237pm](assets/screen_shot_2019-03-06at121237pm.png)

1. **建立工作流**&#x200B;嚮導將幫助您[指定工作流詳細資訊](#specifying-workflow-details-in-the-create-workflow-wizard)。

### 從時間軸啟動工作流{#starting-a-workflow-from-the-timeline}

從&#x200B;**時間軸**&#x200B;中，可以啟動要應用到選定資源的工作流。

1. [選取資](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) 源並開 [啟時間軸](/help/sites-authoring/basic-handling.md#timeline) （或開啟時間軸，然後選取資源）。
1. 注釋欄位旁的箭頭可用來顯示&#x200B;**開始工作流程**:

   ![wf-51](assets/wf-51.png)

1. **建立工作流**&#x200B;嚮導將幫助您[指定工作流詳細資訊](#specifying-workflow-details-in-the-create-workflow-wizard)。

### 在建立工作流嚮導中指定工作流詳細資訊{#specifying-workflow-details-in-the-create-workflow-wizard}

**建立工作流**&#x200B;嚮導將幫助您選擇工作流並指定所需的詳細資訊。

開啟&#x200B;**建立工作流**&#x200B;嚮導後，請執行以下任一操作：

* 「站點」工具欄的&#x200B;**[「建立」](#starting-a-workflow-from-the-sites-toolbar)**&#x200B;選項。
* Sites控制台的&#x200B;**[時間軸](#starting-a-workflow-from-the-timeline)**&#x200B;邊欄。

您可以指定詳細資訊：

1. 在&#x200B;**屬性**&#x200B;步驟中，定義工作流的基本選項：

   * **工作流程模型**
   * **工作流程標題**

      * 您可以指定此例項的標題，以協助您在稍後階段進行識別。

   根據工作流模型，也提供下列選項。 這可讓工作流程完成後，保留建立為裝載的套件。

   * **保留工作流程封裝**
   * **封裝標題**

      * 您可以指定套件的標題，以協助識別。

   >[!NOTE]
   >
   >當為「 **** 多資源支援」配置了工作流且已選擇多個資源時，「保留工作流包」選項可用。[](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support)

   完成後，使用&#x200B;**Next**&#x200B;繼續。

   ![wf-52](assets/wf-52.png)

1. 在&#x200B;**範圍**&#x200B;步驟中，您可以選取：

   * **新增** 內容以開啟路徑瀏 [覽](/help/sites-authoring/author-environment-tools.md#path-browser) 器並選取其他資源；在瀏覽器中時，按一下/點選「選 **** 取」以將內容新增至工作流程例項。
   * 可查看其他動作的現有資源：

      * **包** 含子項以指定將該資源的子項包含在工作流中。

         將會開啟一個對話框，允許您根據以下內容優化選擇：

         * 僅包含直接子項.
         * 僅包含修改過的頁面.
         * 僅包含已發佈的頁面.

         指定的任何子項將添加到將應用工作流的資源清單中。

      * **移除** 選取項目，從工作流程中移除該資源。

   ![wf-53](assets/wf-53.png)

   >[!NOTE]
   >
   >如果添加其他資源，則可以使用「上 **一步** 」( **Back** )在「屬性」(Properties)步驟中調整「保留工作流程包 **」(Keep workflow package** )的設定。

1. 使用&#x200B;**Create**&#x200B;關閉嚮導並建立工作流實例。 通知會顯示在Sites主控台中。

## 從頁面編輯器啟動工作流程{#starting-a-workflow-from-the-page-editor}

編輯頁面時，您可以從工具列選取&#x200B;**頁面資訊**。 下拉式功能表具有選項&#x200B;**在工作流程中開始**。 這會開啟一個對話方塊，您可在其中指定所需的工作流程，並視需要加上標題：

![wf-54](assets/wf-54.png)

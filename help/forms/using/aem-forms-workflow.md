---
title: Forms以OSGi為中心的工作流程
seo-title: Rapidly build adaptive forms-based processes, automate document services operations, and use Acrobat Sign with AEM workflows
description: 使用AEM Forms工作流程來自動化並快速建立審核和核准、啟動檔案服務(例如，將PDF檔案轉換為其他格式)、與Acrobat Sign簽章工作流程整合等。
seo-description: Use AEM Forms Workflow to automate and rapidly build review and approvals, to start document services (For example, to convert a PDF document to another format), integrate with Acrobat Sign signature workflow, and more.
uuid: 46be7ec6-d5cc-498a-9484-e66a29527064
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: document_services, publish
discoiquuid: f8df5fa3-3843-4110-a46d-9a524d2657cd
noindex: true
exl-id: fa39a4e8-ae22-4356-8935-44fdf1f4f609
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2902'
ht-degree: 1%

---

# Forms以OSGi為中心的工作流程 {#forms-centric-workflow-on-osgi}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

![](do-not-localize/header.png)

企業從數以百計的表單、各種後端系統以及線上或離線資料來源收集資料。 他們還擁有一組動態的使用者，可對資料做出決策，這涉及反覆審核和核准程式。

除了內部和外部受眾的審核和核准工作流程外，大型組織和企業都有重複性的工作。 例如，將PDF文檔轉換為其他格式。 手動完成時，這些工作需要大量時間和資源。 企業還有法律要求以數字方式簽署文檔和存檔表單資料，以便以後以預先定義的格式使用。

## OSGi上以Forms為中心的工作流程簡介 {#introduction-to-forms-centric-workflow-on-osgi}

您可以使用AEM工作流程快速建立最適化表單式工作流程。 這些工作流程可用於審核和批准、業務流程流程、啟動文檔服務、與Acrobat Sign簽名工作流整合以及類似的操作。 例如，信用卡申請處理、員工離開審批工作流程、將表單另存為PDF文檔。 此外，這些工作流程可用於組織內或跨網路防火牆。

透過OSGi上以Forms為中心的工作流程，您可以快速建立並部署OSGi堆疊上各種工作的工作流程，而無須在JEE堆疊上安裝完整的流程管理功能。 工作流程的開發和管理使用熟悉的AEM工作流程和AEM收件匣功能。 工作流構成了自動化實際業務流程的基礎，這些業務流程跨越多個軟體系統、網路、部門甚至組織。

設定後，即可手動觸發這些工作流程以完成定義的程式，或在使用者提交表單或 [通信管理](/help/forms/using/cm-overview.md) 字母。 透過這項增強的AEM Workflow（工作流程）功能，AEM Forms提供兩項不同但類似的功能。 作為部署策略的一部分，您需要決定哪一個適合您。 請參閱 [比較](/help/forms/using/capabilities-osgi-jee-workflows.md) OSGi和JEE上的程式管理以Forms為中心的AEM工作流程。 此外，對於部署拓撲，請參閱 [適用於AEM Forms的架構和部署拓撲](/help/forms/using/aem-forms-architecture-deployment.md).

Forms以OSGi為中心的工作流程延伸 [AEM收件匣](/help/sites-authoring/inbox.md) 以及為AEM工作流程編輯器提供額外的元件（步驟），以新增對以AEM Forms為中心的工作流程的支援。 延伸AEM收件匣的功能與 [AEM Forms Workspace](/help/forms/using/introduction-html-workspace.md). 除了管理以人為中心的工作流程（核准、審核等）之外，您還可以使用AEM工作流程來自動化 [檔案服務](/help/sites-developing/workflows-step-ref.md) — 相關操作(例如生成PDF)和電子簽名(Acrobat Sign)文檔。

下圖描述了在OSGi上建立、執行和監控以Forms為中心的工作流程的端對端程式。

![aem-forms-workflow簡介](assets/introduction-to-aem-forms-workflow.jpg)

## 開始之前 {#before-you-start}

* 工作流是真實業務流程的表示。 讓您的實際業務流程和業務流程參與者清單保持就緒。 此外，在開始建立工作流程之前，請先準備好宣傳資料(最適化表單、PDF檔案等)。
* 工作流程可以有多個階段。 這些階段會顯示在「AEM收件匣」中，並說明報告工作流程的進度。 將業務流程劃分為邏輯階段。
* 您可以設定AEM工作流程的指派任務步驟，將電子郵件通知傳送給使用者或受指派者。 所以， [啟用電子郵件通知](#configure-email-service).
* 工作流程也可將Acrobat Sign用於數位簽名。 如果您打算在工作流程中使用Acrobat Sign, [設定Acrobat Sign for AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md) 在工作流程中使用它之前。

## 建立工作流模型 {#create-a-workflow-model}

工作流模型由業務流程的邏輯和流程組成。 它由一系列步驟組成。 這些步驟為AEM元件。 您可以視需要使用參數和指令碼來擴充工作流程步驟，以提供更多功能和控制。 除了可立即使用的AEM步驟外，AEM Forms還提供一些步驟。 如需AEM和AEM Forms步驟的詳細清單，請參閱 [AEM工作流程步驟參考](/help/sites-developing/workflows-step-ref.md) 和 [Forms上以OSGi為中心的工作流程 — 步驟參考](/help/forms/using/aem-forms-workflow.md).

AEM提供直覺式使用者介面，可使用提供的工作流程步驟來建立工作流程模型。 如需建立工作流程模型的逐步指示，請參閱 [建立工作流模型](/help/sites-developing/workflows-models.md). 以下示例提供了逐步說明，以為審批和審核工作流建立工作流模型：

>[!NOTE]
>
>您必須是工作流編輯器組的成員，才能建立或編輯工作流模型。

### 建立核准和審核工作流的模型 {#create-a-model-for-an-approval-and-review-workflow}

審批和審核工作流適用於需要人為干預才能做出決策的任務。 下面的示例為由前台銀行代理填寫的抵押貸款申請建立工作流模型。 填妥申請後，即會傳送以取得核准。 稍後，將核准的申請發送給申請人，請其使用Acrobat Sign進行電子簽名。

此範例以下附加的套件形式提供。 使用套件管理器匯入並安裝範例。 您也可以執行下列步驟來手動建立應用程式的工作流程模型：

該示例建立了由前台銀行代理填寫的抵押申請的工作流模型。 填妥後，即會傳送申請以取得核准。 稍後，會將核准的應用程式傳送給客戶，以透過Acrobat Sign進行電子簽名。 您可以使用套件管理器匯入和安裝範例。

[取得檔案](assets/example-mortgage-loan-application.zip)

1. 開啟「工作流模型」控制台。 預設URL為 `https://[Server]:[port]/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`
1. 選擇 **[!UICONTROL 建立]**，然後 **[!UICONTROL 建立模型]**. 將出現「添加工作流模型」(Add Workflow Model)對話框。
1. 輸入 **[!UICONTROL 標題]** 和 **[!UICONTROL 名稱]** （可選）。 例如，抵押申請。 點選 **[!UICONTROL 完成]**.
1. 選取新建立的工作流程模型並點選 **編輯。** 現在，您可以新增工作流程步驟來建立業務邏輯。 首次建立工作流模型時，它包含：

   * 步驟：流量開始和流量結束。 這些步驟代表工作流程的開始和結束。 這些步驟為必要步驟，無法編輯或移除。
   * 名為步驟1的參與者步驟示例。 此步驟已設定為將工作項目指派給管理員使用者。 移除此步驟。

1. 啟用電子郵件通知。 您可以在OSGi上設定以Forms為中心的工作流程，以傳送電子郵件通知給使用者或受指派者。 執行下列設定以啟用電子郵件通知：

   1. 前往AEM Configuration Manager，網址為 `https://[server]:[port]/system/console/configMgr`.
   1. 開啟 **[!UICONTROL Day CQ Mail Service]** 設定。 指定 **[!UICONTROL SMTP伺服器主機名]**, **[!UICONTROL SMTP伺服器埠，]** 和 **[!UICONTROL 「寄件者」地址]** 欄位。 按一下「**[!UICONTROL 儲存]**」。
   1. 開啟 **[!UICONTROL Day CQ Link Externalizer]** 設定。 在 **[!UICONTROL 網域]** 欄位，指定本機、製作和發佈執行個體的實際主機名稱/IP位址和連接埠號。 按一下「**[!UICONTROL 儲存]**」。

1. 建立工作流程階段。 工作流程可以有多個階段。 這些階段會顯示在AEM收件匣中，並報告工作流程的進度。

   若要定義舞台，請點選 ![資訊圈](assets/info-circle.png) 表徵圖，開啟工作流模型屬性， **[!UICONTROL 階段]** 頁簽，為工作流模型添加階段，並點選 **[!UICONTROL 儲存並關閉]**. 對於抵押申請示例，請建立階段：貸款申請、貸款申請狀態、待簽檔案、已簽貸款檔案。

1. 拖放 **[!UICONTROL 分配任務]** 步驟瀏覽至工作流程模型。 將其設為模型的第一步。

   分配任務元件將由工作流建立的任務分配給用戶或組。 除了指定任務外，您還可以使用元件為任務指定最適化表單或非互動式PDF。 需要最適化表單才能接受使用者的輸入，而非互動式PDF，或只供審核工作流程使用的唯讀最適化表單。

   您也可以使用步驟來控制任務的行為。 例如，建立自動記錄文檔，將任務分配給特定用戶或組、已提交資料的路徑、要預先填入的資料路徑以及預設操作。 有關分配任務步驟選項的詳細資訊，請參閱 [Forms上以OSGi為中心的工作流程 — 步驟參考](/help/forms/using/aem-forms-workflow.md) 檔案。

   ![工作流程編輯器](assets/workflow-editor.png)

   對於抵押申請示例，請配置分配任務步驟以使用只讀適用性表單，並在任務完成後顯示PDF文檔。 此外，選擇允許批准貸款請求的用戶組。 在 **[!UICONTROL 動作]** 頁簽，禁用 **[!UICONTROL 提交]** 選項。 指定 **[!UICONTROL 路由變數]**. 例如actionTaked。 同時，添加批准和拒絕路由。 路由在AEM收件匣中會顯示為個別動作（按鈕）。 工作流程會根據使用者點選的動作（按鈕）來選取分支。

   您可以導入示例包，該示例包可在部分的開頭下載，以獲取為例如抵押申請配置的分配任務步驟的所有欄位的完整值集。

1. 從步驟瀏覽器將OR分割元件拖放至工作流程模型。 「或分割」在工作流中建立分割，之後只有一個分支處於作用中狀態。 此步驟可讓您將條件式處理路徑引入工作流程中。 您可以視需要將工作流程步驟新增至每個分支。

   開啟OR Split的屬性，並將下列程式碼片段新增至Branch1和Branch2。 這些程式碼片段有助於根據AEM收件匣中的使用者動作來選擇分支。

   **分支1的程式碼片段**

   使用者點選 **[!UICONTROL 核准]** 在AEM收件匣中，已啟用分支1。

   ```
   function check(){
      var action = workflowData.getMetaDataMap().get("actionTaken","");
   log.info("action " + action);
      return action=="Approve";
   }
   ```

   **分支2的程式碼片段**

   使用者點選 **[!UICONTROL 拒絕]** 在AEM收件匣中，已啟用分支2。

   ```
   function check(){
      var action = workflowData.getMetaDataMap().get("actionTaken","");
   log.info("action " + action);
      return action=="Reject";
   }
   ```

1. 新增其他工作流程步驟以建立業務邏輯。

   對於抵押示例，將生成記錄文檔、兩個分配任務步驟和一個簽名文檔步驟添加到模型的分支1，如下圖所示。 一個分配任務步驟是顯示併發送 **簽發貸款檔案** 和另一個分配任務元件 **顯示已簽名文檔**. 另外，將分配任務元件添加到分支2。 當使用者點選「 AEM收件匣」中的「拒絕」時，就會啟動此功能。

   對於為抵押申請配置的分配任務步驟、記錄步驟的文檔和簽名文檔步驟的所有欄位的完整值集，請導入示例包，該示例包可在此部分的開頭下載。

   工作流模型已就緒。 您可以透過各種方法啟動工作流程。 如需詳細資訊，請參閱 [在OSGi上啟動以Forms為中心的工作流程](#launch).

   ![workflow-editor-mortgage](assets/workflow-editor-mortgage.png)

## 建立以Forms為中心的工作流程應用程式 {#create-a-forms-centric-workflow-application}

應用程式是與工作流程相關聯的最適化表單。 透過收件匣提交應用程式時，會啟動相關的工作流程。 若要讓Forms工作流程可作為AEM收件匣和AEM Forms應用程式中的應用程式使用，請執行下列操作以建立工作流程應用程式：

>[!NOTE]
>
>您必須是fd-administrator組的成員，才能建立和管理工作流應用程式。

1. 在AEM Author例項上，前往 ![工具](assets/tools.png) > **[!UICONTROL Forms]** > **[!UICONTROL 管理工作流應用程式]** 和水龍頭 **[!UICONTROL 建立]**.
1. 在「建立工作流應用程式」窗口中，為以下欄位提供輸入，然後點選 **[!UICONTROL 建立]**. 將建立新應用程式，並在「工作流應用程式」螢幕中列出。

<table> 
 <tbody> 
  <tr> 
   <td>欄位</td> 
   <td>說明</td> 
  </tr> 
  <tr> 
   <td>標題</td> 
   <td>標題會顯示在AEM收件匣中，並協助使用者選擇應用程式。 保留描述性。 例如，儲蓄帳戶開戶應用程式。<br /> </td> 
  </tr> 
  <tr> 
   <td>名稱 </td> 
   <td>指定應用程式的名稱。 除了字母、數字、連字型大小和底線以外，所有字元都會取代為連字型大小。 </td> 
  </tr> 
  <tr> 
   <td>說明</td> 
   <td>說明會顯示在AEM收件匣中。 在說明欄位中提供應用程式的詳細資訊。 例如，應用程式的用途。<br /> </td> 
  </tr> 
  <tr> 
   <td>適用性表單</td> 
   <td><p>指定最適化表單的路徑。 當使用者啟動應用程式時，會顯示指定的最適化表單。</p> <p><strong>附註</strong>:工作流程應用程式不支援超過一頁或需要在Apple iPad上捲動的表單和PDF檔案。 在Apple iPad上開啟應用程式，且最適化表單或PDF檔案長於頁面時，第二頁的表單欄位和內容會遺失。</p> </td> 
  </tr> 
  <tr> 
   <td>存取群組</td> 
   <td><p>選取群組。 應用程式只會顯示在所選群組的成員的AEM收件匣中。 訪問組選項使工作流用戶組的所有組都可供選擇。 </p> <br /> </td> 
  </tr> 
  <tr> 
   <td>預填服務</td> 
   <td>選取 <a href="/help/forms/using/prepopulate-adaptive-form-fields.md#aem-forms-custom-prefill-service" target="_blank">預填服務</a> （適用於最適化表單）。<br /> </td> 
  </tr> 
  <tr> 
   <td>工作流程模型</td> 
   <td>選取 <a href="/help/forms/using/aem-forms-workflow.md#create-a-workflow-model">工作流模型</a> 的URL。 工作流模型由業務流程的邏輯和流程組成。 </td> 
  </tr> 
  <tr> 
   <td>資料檔案路徑</td> 
   <td>在crx-repository中指定資料檔案的路徑。 路徑相對於適用性表單裝載，且包含資料檔案的名稱。 一律包含檔案的完整名稱，包括副檔名（若適用）。 例如， [payload]/data.xml。 </td> 
  </tr> 
  <tr> 
   <td>附件路徑</td> 
   <td>在crx-repository中指定附件資料夾的路徑。 附件路徑是相對於裝載位置。 例如， [payload]/data.xml。 </td> 
  </tr> 
  <tr> 
   <td>記錄文件路徑</td> 
   <td>在crx-repository中指定記錄檔案的文檔路徑。 路徑相對於最適化表單裝載位置。 一律包含檔案的完整名稱，包括副檔名（若適用）。 例如， [payload]/DOR/creditcard.pdf。</td> 
  </tr> 
 </tbody> 
</table>

## 在OSGi上啟動以Forms為中心的工作流程 {#launch}

您可以透過下列方式啟動或觸發以Forms為中心的工作流程：

* [從AEM收件匣提交應用程式](#inbox)
* [從AEM Forms應用程式提交應用程式](#afa)

* [提交最適化表單](#af)
* [使用監看資料夾](#watched)

* [提交互動式通訊或信函](#letter)

### 從AEM收件匣提交應用程式 {#inbox}

您建立的工作流應用程式在收件箱中作為應用程式可用。 屬於工作流程使用者群組成員的使用者可以填寫並提交觸發相關工作流程的應用程式。 有關使用AEM收件匣來提交應用程式和管理任務的資訊，請參閱 [在AEM收件匣中管理Forms應用程式和任務](/help/forms/using/manage-applications-inbox.md).

### 從AEM Forms應用程式提交應用程式 {#afa}

AEM Forms應用程式會與AEM Forms伺服器同步，並可讓您變更帳戶中的表單資料、工作、工作流程應用程式和已儲存的資訊（草稿/範本）。 如需詳細資訊，請參閱 [AEM Forms應用程式](/help/forms/using/aem-forms-app.md) 和相關文章。

### 提交最適化表單 {#af}

您可以設定最適化表單的提交動作，以在提交最適化表單時啟動工作流程。 適用性表單提供 **[!UICONTROL 叫用AEM工作流程]** 提交動作，以在提交最適化表單時啟動工作流程。 如需提交動作的詳細資訊，請參閱 [設定提交動作](/help/forms/using/configuring-submit-actions.md). 若要透過AEM Forms應用程式提交最適化表單，請啟用最適化表單屬性中的與AEM Forms應用程式同步。

您可以設定最適化表單，以從AEM Forms應用程式同步、提交和觸發工作流程。 如需詳細資訊，請參閱 [使用表單](/help/forms/using/working-with-form.md).

### 使用已監看的資料夾 {#watched}

管理員（fd-administrators組的成員）可以配置網路資料夾，以在用戶將檔案(如PDF檔案)放在資料夾時運行預配置的工作流。 工作流完成後，它可以將結果檔案保存到指定的輸出資料夾。 此類資料夾稱為 [監看資料夾](/help/forms/using/watched-folder-in-aem-forms.md). 執行下列程式來設定已觀看的資料夾以啟動工作流程：

1. 在AEM Author例項上，前往 ![工具](assets/tools.png) **[!UICONTROL Forms >設定監看資料夾]**. 將顯示已配置的監視資料夾清單。
1. 點選 **[!UICONTROL 新增]**. 隨即顯示欄位清單。 指定下列欄位的值，以設定工作流程的「監看資料夾」：

<table> 
 <tbody> 
  <tr> 
   <td>欄位</td> 
   <td>說明</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">名稱</span></td> 
   <td>指定「觀看的資料夾」的名稱。 此欄位僅支援英數字元。</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">路徑</span></td> 
   <td>指定「觀看的資料夾」的物理位置。 在群集環境中，使用可從AEM叢集節點存取的共用網路資料夾。</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">處理檔案使用</span></td> 
   <td>選取 <span class="uicontrol">工作流程 </span>選項。 </td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">工作流程模型</span></td> 
   <td>選擇工作流模型。<br /> </td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">輸出檔案模式</span></td> 
   <td>指定輸出檔案和目錄的目錄結構。 您也可以指定 <a href="/help/forms/using/admin-help/configuring-watched-folder-endpoints.md" target="_blank">輸出檔案和目錄的模式</a>.</td> 
  </tr> 
 </tbody> 
</table>

1. 點選 **[!UICONTROL 進階]**. 指定下列欄位的值，然後點選 **[!UICONTROL 建立]**. 「已觀看資料夾」已設定為啟動工作流程。 現在，每當檔案置於「觀看資料夾」的輸入目錄中時，就會觸發指定的工作流程。

   | 欄位 | 說明 |
   |---|---|
   | 承載對應程式篩選條件 | 建立受監視的資料夾時，會在crx-repository中建立資料夾結構。 資料夾結構可作為工作流程的裝載。 您可以撰寫指令碼來對應AEM工作流程，以接受來自已觀看資料夾結構的輸入。 現成可用的實作，會列在裝載映射器篩選器中。 如果您沒有自訂實作，請選取預設實作。 |

   「進階」標籤包含更多欄位。 這些欄位大多包含預設值。 若要了解所有欄位，請參閱 [建立或設定已觀看的資料夾](/help/forms/using/creating-configure-watched-folder.md) 文章。

### 提交互動式通訊或信函 {#letter}

您可以在提交互動式通訊或信函時，在OSGi上建立關聯並執行以Forms為中心的工作流程。 在通信管理工作流中，用於後處理互動式通信和信函。 例如，通過電子郵件發送、打印、傳真或歸檔最終信函。 如需詳細步驟，請參閱 [互動式通信和信函的後處理](/help/forms/using/submit-letter-topostprocess.md).

## 其他配置 {#additional-configurations}

### 設定電子郵件服務 {#configure-email-service}

您可以使用AEM工作流程的指派任務和傳送電子郵件步驟來傳送電子郵件。 執行下列步驟來指定電子郵件伺服器以及傳送電子郵件所需的其他設定：

1. 前往AEM Configuration Manager，網址為 `https://[server]:[port]/system/console/configMgr`.
1. 開啟 **[!UICONTROL Day CQ Mail Service]** 設定。 指定 **[!UICONTROL SMTP伺服器主機名]**, **[!UICONTROL SMTP伺服器埠，]** 和 **[!UICONTROL 「寄件者」地址]** 欄位。 按一下「**[!UICONTROL 儲存]**」。
1. 開啟 **[!UICONTROL Day CQ Link Externalizer]** 設定。 在 **[!UICONTROL 網域]** 欄位，指定本機、製作和發佈執行個體的實際主機名稱/IP位址和連接埠號。 按一下「**[!UICONTROL 儲存]**」。

### 清除工作流實例 {#purge-workflow-instances}

將工作流實例數減到最少會提高工作流引擎的效能，因此您可以定期從儲存庫中清除已完成或正在運行的工作流實例。 如需詳細資訊，請參閱 [定期清除工作流實例](/help/sites-administering/workflows-administering.md#regular-purging-of-workflow-instances).

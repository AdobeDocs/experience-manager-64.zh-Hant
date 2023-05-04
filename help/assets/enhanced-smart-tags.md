---
title: 增強型智慧標記
description: 增強型智慧標記
uuid: 4452ca05-1f20-4f80-884a-a739ae7b8b0e
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
discoiquuid: c1b52aac-1eaf-4cfa-801f-77aeca0d90ea
feature: Smart Tags,Search
role: User
exl-id: 21a9f130-ea91-45bf-adc8-8a73a2a00c77
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1550'
ht-degree: 14%

---

# 增強型智慧標記 {#enhanced-smart-tags}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 增強智慧標籤概觀 {#overview-of-enhanced-smart-tags}

處理數位資產的組織，在資產中繼資料中越來越多地使用分類法控制的辭匯。 基本上，它包含員工、合作夥伴和客戶通常用來參考和搜尋特定類別的數位資產的關鍵字清單。 使用分類控制的辭匯來標籤資產，以確保透過標籤式搜尋輕鬆識別及擷取資產。

與自然語言辭匯相比，根據商業分類法標籤數位資產有助於使其與公司的業務一致，並確保搜尋中出現最相關的資產。

例如，汽車製造商可以用型號標籤汽車影像，以便在搜索各種型號的影像以設計促銷活動時，只顯示相關影像。

為了讓智慧內容服務套用正確的標籤，您必須對其進行訓練，以識別您的分類法。 若要訓練服務，請先組織一組最能說明這些資產的資產和標籤。 將這些標籤套用至資產，並執行訓練工作流程以協助服務學習。

標籤完成訓練並準備就緒後，服務現在可以透過標籤工作流程將這些標籤套用至資產。

在背景中，智慧內容服務會使用Adobe Sensei的AI架構，根據您的標籤結構和商業分類訓練其影像識別演算法。 然後，系統會使用此內容智慧，將相關標籤套用至不同的資產集。

智慧內容服務是托管於 [!DNL Adobe I/O]. 若要在Adobe Experience Manager中使用，系統管理員必須整合 [!DNL Experience Manager] 例項 [!DNL Adobe I/O].

總而言之，以下是使用智慧內容服務的主要步驟：

* 上線
* 檢閱資產和標籤（分類法定義）
* 訓練智慧內容服務
* 自動標籤

![流程圖](assets/flowchart.gif)

## 必備條件 {#prerequisites}

您必須先確定下列項目，才能建立上的整合 [!DNL Adobe I/O]:

* Adobe ID 帳戶具有組織的管理員權限。
* 貴組織已啟用智慧內容服務。

## 上線 {#onboarding}

智慧內容服務可作為 [!DNL Experience Manager] . 購買後，系統會傳送電子郵件給您組織的管理員，並附上連結 [!DNL Adobe I/O].

管理員可以遵循該連結，將智慧內容服務與 [!DNL Experience Manager] . 將服務與 [!DNL Experience Manager] 資產，請參閱 [設定智慧標籤](config-smart-tagging.md).

當管理員設定服務並將使用者新增至 [!DNL Experience Manager] .

## 檢閱資產和標籤 {#reviewing-assets-and-tags}

上線後，您首先要識別一組標籤，以便在您的業務環境中最能描述這些影像。

接下來，查看影像，以識別最能代表您產品滿足特定業務需求的一組影像。 確定組織集中的資產符合 [智慧內容服務訓練准則](smart-tags-training-guidelines.md).

將資產新增至資料夾，並從屬性頁面將標籤套用至每個資產。 然後，對此資料夾運行培訓工作流。 已組織的資產集可讓智慧內容服務使用您的分類定義，有效訓練更多資產。

>[!NOTE]
>
>1. 培訓是一個不可撤銷的過程。 Adobe建議您先檢閱已組織資產集中的標籤，再訓練標籤上的智慧內容服務。
>1. 請閱讀 [智慧內容服務訓練准則](smart-tags-training-guidelines.md) 開始任何標籤的訓練前。
>1. 第一次訓練智慧內容服務時，Adobe建議您至少在兩個不同的標籤上訓練智慧內容服務。

>


## 訓練智慧內容服務 {#training-the-smart-content-service}

為了讓智慧內容服務識別您的業務分類，請在已包含與您的業務相關標籤的一組資產上執行該分類。 經過培訓後，此服務可對類似的資產集套用相同的分類法。

您可以多次訓練服務，以改善其套用相關標籤的能力。 在每個訓練週期後，執行標籤工作流程並檢查資產是否已適當標籤。

您可以定期或根據需求對智慧內容服務進行培訓。

>[!NOTE]
>
>培訓工作流程僅在資料夾上執行。

### 定期培訓 {#periodic-training}

您可以啟用智慧內容服務，以定期訓練資料夾內的資產和相關標籤。 開啟資產資料夾的屬性頁面，選取 **[!UICONTROL 啟用智慧標籤]** 在 **[!UICONTROL 詳細資料]** ，然後儲存變更。

![enable_smart_tags](assets/enable_smart_tags.png)

為資料夾選取此選項後， [!DNL Experience Manager] 會自動執行訓練工作流程，以訓練資料夾資產及其標籤上的智慧內容服務。 預設情況下，培訓工作流程每週在星期六的凌晨12:30運行。

### 隨選培訓 {#on-demand-training}

您可以視需要從工作流程主控台訓練智慧內容服務。

1. 點選/按一下 [!DNL Experience Manager] 標誌，然後 **[!UICONTROL 「工具」>「工作流」>「模型」]**.
1. 從「工 **[!UICONTROL 作流模型]** 」頁面中，選擇「智 **[!UICONTROL 慧標籤培訓」工作流程，然後從工具列點選/]** 按一下「開始工作流程 **** 」。
1. 在 **[!UICONTROL 執行工作流程]** 對話方塊，瀏覽至裝載資料夾，其中包含用於訓練服務的已標籤資產。
1. 指定工作流程的標題並新增註解。 然後，點選/按一下 **[!UICONTROL 執行]**. 資產和標籤會提交以供訓練。

   ![workflow_dialog](assets/workflow_dialog.png)

>[!NOTE]
>
>處理資料夾中的資產以進行訓練後，後續訓練週期中只會處理修改的資產。

### 查看培訓報告 {#viewing-training-reports}

若要檢查智慧內容服務是否在資產訓練集的標籤上接受訓練，請從報表控制台檢閱訓練工作流程報表。

1. 點選/按一下 [!DNL Experience Manager] 標誌，然後 **[!UICONTROL 工具>資產>報表]**.
1. 在「資產 **[!UICONTROL 報表」頁面]** ，點選/按一下「 **[!UICONTROL 建立」]**。
1. 選取「智 **[!UICONTROL 慧標籤訓練]** 」報表，然後從工具列點選/ **[!UICONTROL 按「下一步]** 」。
1. 指定報表的標題和說明。在「 **[!UICONTROL 排程報表]**」下，保 **[!UICONTROL 留「現在]** 」選項。如果您想要排程報表以供稍後使用，請選 **[!UICONTROL 取]** 「稍後」並指定日期和時間。然後，點選/按一 **[!UICONTROL 下工具列]** 中的「建立」。
1. 在「資 **[!UICONTROL 產報表]** 」頁面中，選取您產生的報表。若要檢視報表，請點選/按一下工 **[!UICONTROL 具列中的]** 「檢視」圖示。
1. 檢閱報表的詳細資訊。

   報表會顯示您所訓練之標籤的訓練狀態。「培訓狀態」欄 **[!UICONTROL 中的綠色]** ，表示智慧型內容服務已接受標籤的培訓。黃色表示服務未針對特定標籤進行完整訓練。在這種情況下，請使用特定標籤新增更多影像，並執行培訓工作流程，以完全在標籤上訓練服務。

   如果在此報告中看不到您的標籤，請針對這些標籤再次執行訓練工作流程。

1. 若要下載報表，請從清單中選取報表，然後點選/按一下 **[!UICONTROL 下載]** 圖示。 報表會以Excel檔案的形式下載。

## 自動標籤資產 {#tagging-assets-automatically}

在您訓練智慧內容服務後，可以觸發標籤工作流程，自動對不同的一組類似資產套用適當標籤。

您可以定期或在需要時運行標籤工作流。

>[!NOTE]
>
>標籤工作流程會同時在資產和資料夾上執行。

### 定期標籤 {#periodic-tagging}

您可以啟用智慧內容服務，以定期標籤資料夾中的資產。 開啟資產資料夾的屬性頁面，選取 **[!UICONTROL 啟用智慧標籤]** 在 **[!UICONTROL 詳細資料]** ，然後儲存變更。

為資料夾選取此選項後，智慧內容服務就會自動為資料夾中的資產加上標籤。 預設情況下，標籤工作流程每天凌晨12:00執行。

### 隨需標籤 {#on-demand-tagging}

您可以從下列項目觸發標籤工作流程，以立即標籤您的資產：

* 工作流程主控台
* 時間軸

>[!NOTE]
>
>如果您從時間軸執行標籤工作流程，一次最多可對15個資產套用標籤。

#### 從工作流程主控台標籤資產 {#tagging-assets-from-the-workflow-console}

1. 點選/按一下 [!DNL Experience Manager] 標誌，然後 **[!UICONTROL 「工具」>「工作流」>「模型」]**.
1. 從「工 **[!UICONTROL 作流程模型]** 」頁面中，選擇 **[!UICONTROL DAM智慧標籤資產工作流程，然後從工具列點選/按]** 一下「開始工作流程 **** 」。

   ![dam_smart_tag_workflow](assets/dam_smart_tag_workflow.png)

1. 在 **[!UICONTROL 執行工作流程]** 對話方塊，瀏覽至包含您要自動套用標籤之資產的裝載資料夾。
1. 指定工作流程的標題和可選注釋。 然後，點選/按一下 **[!UICONTROL 執行]**.

   ![tagging_dialog](assets/tagging_dialog.png)

   導覽至資產資料夾並檢閱標籤，以確認智慧內容服務是否已正確標籤您的資產。 如需詳細資訊，請參閱 [管理智慧標籤](managing-smart-tags.md).

#### 從時間軸標籤資產 {#tagging-assets-from-the-timeline}

1. 從「資產」使用者介面，選取包含您要套用智慧標籤之資產或特定資產的資料夾。
1. 點選/按一下GlobalNav圖示，然後開啟時間軸。
1. 點選/按一下底部的箭頭，然後點選/按一下 **[!UICONTROL 開始工作流程]**.

   ![start_workflow](assets/start_workflow.png)

1. 選取 **[!UICONTROL DAM智慧標籤資產]** ，並指定工作流程的標題。
1. 點選/按一下 **[!UICONTROL 開始]**. 工作流程會將標籤套用至資產。 導覽至資產資料夾並檢閱標籤，以確認智慧內容服務是否已正確標籤您的資產。 如需詳細資訊，請參閱 [管理智慧標籤](managing-smart-tags.md).

>[!NOTE]
>
>在後續的標籤週期中，只有修改的資產會以新訓練的標籤再次標籤。
>
>不過，如果標籤工作流程的最後一個與目前標籤週期之間的間隙超過24小時，即使未更改的資產也會加上標籤。
>
>對於定期標籤工作流程，當間隙超過6個月時，會標籤未更改的資產。

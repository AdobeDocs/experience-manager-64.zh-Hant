---
title: 發佈頁面
seo-title: 發佈頁面
description: 'null'
seo-description: 'null'
uuid: 1222859d-ef8d-462e-a125-b76e6cfec26d
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 8f2714bc-9d6c-4e6f-97a1-3b4f977348c5
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# 發佈頁面{#publishing-pages}

在您建立並檢視內容至作者環境後，其目的 [是讓內容可在您的公開網站](/help/sites-authoring/author.md#concept-of-authoring-and-publishing) （您的發佈環境）上使用。

這稱為發佈頁面。 當您想從發佈環境中移除頁面時，稱為取消發佈。 發佈和取消發佈頁面時，在作者環境中仍可使用頁面進行進一步變更，直到您刪除為止。

您也可以立即發佈／取消發佈頁面，或在未來的預先定義日期／時間發佈／取消發佈頁面。

>[!NOTE]
>
>與發佈相關的某些術語可能會混淆：
>
>* **發佈／取消發佈**
   >  這些是讓您的內容在發佈環境（或非）上公開提供之動作的主要條款。
   >
   >
* **啟用／停用**
   >  這些詞語與publish/unpublish同義。
   >
   >
* **複製／複製**
   >  這些技術術語描述資料（例如頁面內容、檔案、程式碼、使用者註解）在某個環境之間的移動，例如發佈或反向複製使用者註解時。
>



>[!NOTE]
>
>如果您沒有發佈特定頁面的必要權限：
>
>* 系統會觸發工作流程，通知您發佈請求的適當人員。
>* 您 [的開發團隊可能已自訂此](/help/sites-developing/workflows-models.md) 工作流程。
>* 系統會短暫顯示訊息，通知您工作流程已觸發。
>



## 發佈頁面 {#publishing-pages-2}

視您的位置而定，您可以發佈：

* [從頁面編輯器](/help/sites-authoring/publishing-pages.md#publishing-from-the-editor)
* [從站點控制台](/help/sites-authoring/publishing-pages.md#publishing-from-the-console)

### 從編輯器發佈 {#publishing-from-the-editor}

如果您正在編輯頁面，則可直接從編輯器發佈頁面。

1. 選取「 **頁面資訊** 」圖示以開啟功能表，然後選 **取「發佈頁面** 」選項。

   ![screen_shot_2018-03-21at152734](assets/screen_shot_2018-03-21at152734.png)

1. 視頁面是否有需要發佈的參考而定：

   * 如果沒有要發佈的參考，頁面將直接發佈。
   * 如果頁面有需要發佈的參考，這些參考將列在「發 **布** 」精靈中，您可以在其中：

      * 指定哪些資產／標籤／等。 您想要與頁面一起發佈，然後使用「 **發佈** 」完成程式。
      * Use **Cancel** to abort the action.
   ![chlimage_1-50](assets/chlimage_1-50.png)

1. 選取 **「發佈** 」會將頁面複製至發佈環境。 在頁面編輯器中，會顯示確認發佈動作的資訊橫幅。

   ![screen_shot_2018-03-21at152840](assets/screen_shot_2018-03-21at152840.png)

   在控制台中查看相同頁面時，更新的發佈狀態可見。

   ![screen_shot_2018-03-21at152951](assets/screen_shot_2018-03-21at152951.png)

>[!NOTE]
>
>從編輯器發佈是淺層發佈，即僅會發佈選定的頁面／頁面，而未發佈任何子頁面。

### 從主控台發佈 {#publishing-from-the-console}

在網站主控台中，有兩種發佈選項：

* [快速發佈](/help/sites-authoring/publishing-pages.md#quick-publish)
* [管理發佈](/help/sites-authoring/publishing-pages.md#manage-publication)

#### 快速發佈 {#quick-publish}

**「快速發佈** 」適用於簡單的情況，並立即發佈選取的頁面，而不需進行任何進一步的互動。 因此，任何未發佈的參考也會自動發佈。

若要使用「快速發佈」來發佈頁面：

1. 在網站主控台中選取頁面或頁面，然後按一下「快速 **發佈** 」按鈕。

   ![screen_shot_2018-03-21at153115](assets/screen_shot_2018-03-21at153115.png)

1. 在「快速發佈」對話方塊中，按一下「發佈」以確認出版物，或按一 **下** 「取消」以 **取消出版物**。 請記住，任何未發佈的參照也會自動發佈。

   ![chlimage_1-51](assets/chlimage_1-51.png)

1. 發佈頁面時，會顯示確認發佈的警報。

>[!NOTE]
>
>「快速發佈」是淺層發佈，即僅會發佈所選頁面／頁面，且未發佈任何子頁面。

#### 管理發佈 {#manage-publication}

**「管理出版物** 」提供的選項比「快速發佈」更多，允許包含子頁面、自訂參照、啟動任何適用的工作流程，以及提供稍後發佈的選項。

若要使用「管理出版物」來發佈或取消發佈頁面：

1. 在站點控制台中選擇頁或頁，然後按一下「管理 **出版物** 」按鈕。

   ![screen_shot_2018-03-21at153309](assets/screen_shot_2018-03-21at153309.png)

1. 「管 **理出版物** 」嚮導將啟動。第一個步驟 **Options**&#x200B;可讓您：

   * 選擇發佈或取消發佈所選頁面。
   * 選擇立即或稍後採取該動作。
   稍後發佈會啟動工作流程，以在指定時間發佈選取的頁面。 相反地，稍後取消發佈會啟動工作流程，在特定時間取消發佈選取的頁面。

   如果您想在稍後取消發佈／取消發佈，請前往 [Workflow Console](/help/sites-administering/workflows.md) ，以終止對應的工作流程。

   ![chlimage_1-52](assets/chlimage_1-52.png)

   按一 **下** 「下一步」繼續。

1. 在「管理出版物」嚮導的下一個步驟 **Scope**，您可以定義出版物／取消出版物的範圍，例如包含子頁面和／或包含引用。

   ![screen_shot_2018-03-21at153354](assets/screen_shot_2018-03-21at153354.png)

   您可以使用「新 **增內容** 」按鈕，在要發佈的頁面清單中新增其他頁面，以防您在啟動「管理出版物」精靈之前未選取其中一個頁面。

   按一下「新增內容」按鈕會啟動路 [徑瀏覽器](/help/sites-authoring/author-environment-tools.md#path-browser) ，以允許選取內容。

   選擇所需頁面，然後按一下「 **Select** （選擇）」將內容添加到嚮導中，或按一下「**Cancel **」取消選擇並返回嚮導。

   回到精靈中，您可以選取清單中的項目，以設定其他選項，例如：

   * 包括其子系。
   * 從選取範圍中移除它。
   * 管理其已發佈的參考。
   ![screen_shot_2018-03-21at153450](assets/screen_shot_2018-03-21at153450.png)

   按一下 **「包括子項** 」(Include Children)將開啟一個對話框，允許您：

   * 僅包含直接子項.
   * 僅包含修改過的頁面.
   * 僅包含已發佈的頁面.
   按一 **下「新增** 」，根據選取選項，將子頁面新增至要發佈或未發佈的頁面清單。 按一下 **取消** ，取消選擇並返回嚮導。

   ![chlimage_1-53](assets/chlimage_1-53.png)

   返回到嚮導時，您會根據您在「包含子項」對話框中選擇的選項看到添加的頁。

   您可以通過選擇某個頁面，然後按一下「已發佈參照」(Published References)按鈕，來查看和修改要發佈或未發佈該頁面 **的參照** 。

   ![screen_shot_2018-03-21at153801](assets/screen_shot_2018-03-21at153801.png)

   「發 **布參照** 」(Published References)對話框顯示所選內容的參照。 依預設，這些檔案都已選取，而且會發佈／取消發佈，但您可以取消勾選，以便將它們排除在動作中。

   單 **擊「完成** 」保存更改，或按一下「取消 **** 」取消選擇並返回嚮導。

   ![screen_shot_2018-03-21at153824](assets/screen_shot_2018-03-21at153824.png)

   回到精靈中，「參 **考」欄將會更新** ，以反映您選取要發佈或未發佈的參考。

   ![screen_shot_2018-03-21at153925](assets/screen_shot_2018-03-21at153925.png)

1. 按一 **下「發佈** 」以完成。

   在站點控制台中，通知消息將確認發佈。

   ![screen_shot_2018-03-21at153951](assets/screen_shot_2018-03-21at153951.png)

1. 如果已發佈頁面與工作流程相關聯，則可能會顯示在出版物精靈的最 **後「工作流** 」步驟中。

   >[!NOTE]
   >
   >「工 **作流程** 」步驟將根據您的使用者可能擁有或可能沒有的權限顯示。 如需詳細 [資訊，請參閱本頁上的上一](/help/sites-authoring/publishing-pages.md) 個附註 [，其中說明發佈權限以及管理](/help/sites-administering/workflows-managing.md) 對工作流程的存取權 [,](/help/sites-authoring/workflows-applying.md) 以及套用工作流程至頁面。

   資源會依觸發的工作流程和每個指定選項分組，以：

   * 定義工作流的標題。
   * 請保留工作流程套件，前提是工作流程具 [有多資源支援](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support)。
   * 如果選擇了保留工作流包的選項，則定義工作流包的標題。
   Click **Publish** or **Publish Later **to complete the publication.

   ![chlimage_1-54](assets/chlimage_1-54.png)

## 取消發佈頁面 {#unpublishing-pages}

取消發佈頁面會將其從您的發佈環境中移除，如此讀者就無法再使用它。

以類 [似發佈的方式](/help/sites-authoring/publishing-pages.md#publishing-pages)，可以取消發佈一或多個頁面：

* [從頁面編輯器](/help/sites-authoring/publishing-pages.md#unpublishing-from-the-editor)
* [從站點控制台](/help/sites-authoring/publishing-pages.md#unpublishing-from-the-console)

### 從編輯器取消發佈 {#unpublishing-from-the-editor}

編輯頁面時，如果您想要解除發佈該頁面，請在「頁面資訊」功能表中選取「解除發佈頁面 **」(Unpublish Page** )，就像您發 **布頁面一樣**[](/help/sites-authoring/publishing-pages.md#publishing-from-the-editor)。

### 從主控台取消發佈 {#unpublishing-from-the-console}

就像您使 [用「管理出版物」選項發佈](/help/sites-authoring/publishing-pages.md#manage-publication)，您也可以使用它取消發佈。

1. 在站點控制台中選擇頁或頁，然後按一下「管理 **出版物** 」按鈕。
1. 「管 **理出版物** 」嚮導將啟動。在第一個步驟中， **選項**，選擇「取消發佈」(Unpublish **)，而非「發佈」(Publish)的預設** 選項 ****。

   ![chlimage_1-55](assets/chlimage_1-55.png)

   就像稍後發佈會啟動工作流程以在指定時間發佈此版本的頁面一樣，稍後停用會啟動工作流程以在特定時間解除發佈選取的頁面。

   如果您想在稍後取消發佈／取消發佈，請前往 [Workflow Console](/help/sites-administering/workflows.md) ，以終止對應的工作流程。

1. 若要完成取消發佈，請繼續執行精靈，就像您要發 [布頁面一樣](/help/sites-authoring/publishing-pages.md#manage-publication)。

## 發佈和取消發佈樹狀結構 {#publishing-and-unpublishing-a-tree}

當您輸入或更新大量內容頁面（所有頁面都位於相同的根頁面下）時，在單一動作中發佈整個樹狀結構會比較容易。

您可以使用站 [點控制台上的](/help/sites-authoring/publishing-pages.md#manage-publication) 「管理出版物」選項來執行此操作。

1. 在站點控制台中，選擇要發佈或取消發佈的樹的根頁面，然後選擇「管 **理出版物」**。
1. 「管 **理出版物** 」嚮導將啟動。選擇發佈或取消發佈，並選擇「下一步」以繼 **續** 。
1. 在「范 **圍** 」步驟中，選擇根頁面，然後選擇「包 **含子項」**。

   ![chlimage_1-56](assets/chlimage_1-56.png)

1. 在「包 **括子代** 」對話框中，取消選中以下選項：

   * 僅包含直接子項
   * 僅包含已發佈的頁面
   這些選項預設為選取，因此您必須記得取消選取。 按一 **下「新增** 」以確認內容並將內容新增至出版物／取消出版物。

   ![chlimage_1-57](assets/chlimage_1-57.png)

1. 「管 **理出版物** 」嚮導列出要查看的樹的內容。 您可以新增其他頁面或移除選取的頁面，進一步自訂選取範圍。

   ![screen_shot_2018-03-21at154237](assets/screen_shot_2018-03-21at154237.png)

   請記住，您也可以查看要通過「已發佈參照」(Published References)選項發 **布的參照** 。

1. [按正常方式繼續「管理出版物」嚮導](#manage-publication) ，以完成樹的出版物或取消出版物。

## 確定發佈狀態 {#determining-publication-status}

您可以確定頁面的發佈狀態：

* 在站點 [控制台上的資源概述資訊中](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)

   ![screen_shot_2018-03-21at154336](assets/screen_shot_2018-03-21at154336.png)

   發佈狀態會顯示在 [網站主控台](/help/sites-authoring/basic-handling.md#card-view)[的卡片](/help/sites-authoring/basic-handling.md#column-view)、欄和 [清單檢視中](/help/sites-authoring/basic-handling.md#list-view) 。

* 在時間軸 [中](/help/sites-authoring/basic-handling.md#timeline)

   ![screen_shot_2018-03-21at154420](assets/screen_shot_2018-03-21at154420.png)

* 編輯頁 [面時在「頁面資訊](/help/sites-authoring/author-environment-tools.md#page-information) 」功能表中

   ![screen_shot_2018-03-21at154456](assets/screen_shot_2018-03-21at154456.png)


---
title: 啟動流程
seo-title: Starting processes
description: 如何使用LiveCycleAEM Forms工作區 — 選取程式、新增附註和附件、儲存草稿復本，以及新增至我的最愛。
seo-description: How to use LiveCycle AEM Forms workspace--select processes, add notes and attachments, save draft copies, and add to favorites.
uuid: a61da785-25b4-4482-bd72-02e250d35dc7
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: c9d3f369-3744-41d5-b340-390ab7e03f36
exl-id: bd5a247f-cd4b-41c8-b5f6-8def4f5c93ef
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1379'
ht-degree: 0%

---

# 啟動流程 {#starting-processes}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

AEM Forms工作區依管理員或程式設計工具所設定的類別來組織程式。 您也可以將經常使用的程式放入您的我的最愛類別中，以便快速找到它們。

啟動流程時，您可能需要填寫表單，以啟動AEM Forms工作流程控制的業務流程。 如果表單使用「準備資料處理」，則某些資訊可在起始新處理時以空白表單預先填入。

例如，您想要購買新的電腦監視器，因此，請啟動以下程式： *採購訂單*. 啟動流程時，將開啟一個表單，提示您輸入有關要訂購的項目的詳細資訊。 您的姓名、員工編號和經理姓名可能已在表單中預填。 提交請求時，將啟動業務流程。 伺服器會根據程式定義，自動將請求路由傳送給您的管理員。 任務開始顯示在您的經理的待辦事項清單中。 經理批准請求後，表單工作流會將請求路由傳送給採購部門，並向您發送電子郵件通知。

## 選擇要啟動的進程 {#selecting-processes-to-start}

您可以選取要啟動的程式，或檢視其相關資訊。

選擇要啟動的流程時，您可能需要填寫與該流程關聯的表單。 提交表單會啟動程式。

支援各種檔案格式的Forms，包括Adobe PDF、HTML和SWF檔案。 表單看起來可能像傳統的可列印或網頁型表單，或引導您完成一系列精靈樣式的面板，以收集資訊。

如果表單和流程允許，您也可以離線保存表單、填寫表單，然後提交它以完成任務。 提交表單時，如果已配置電子郵件終端，則使用適當的伺服器電子郵件地址啟動電子郵件客戶端。 然後，您可以透過電子郵件將完成的表單傳送至伺服器。

選擇流程時，將顯示「表單」頁簽和「詳細資訊」頁簽。 如果該過程允許您添加附註或附件，則也會顯示「附件」頁簽和「附註」頁簽。 如果您也已使用程式設定摘要url，則也會顯示「摘要」標籤。 「Forms」頁簽顯示關聯的表單，而「詳細資訊」頁簽顯示有關當前任務及其所屬的流程的資訊。

### 啟動業務流程 {#start-a-business-process}

1. 在「開始流程」頁的左側清單中，選擇類別。 類別中您有權存取的所有程式都會顯示在右側。

   >[!NOTE]
   >
   >如果折疊了「類別」窗格，請按一下AEM Forms工作區左上角的「開啟類別」以開啟窗格。

1. 按一下任務以選擇進程。 與流程關聯的表單將在「表單」頁簽上開啟。

   程式中的每個表單都有唯一的URL。 您可以使用唯一URL，透過特定的程式和表單直接啟動HTML工作區。 URL的格式為https://&lt;server>:&lt;port>/lc/libs/ws/index.html#/startprocess/&lt;applicationname>%2F&lt;processname>. 此 &lt;applicationname>%2F&lt;processname> 字串一律以URL編碼。 範例URL為http://localhost:8080/lc/libs/ws/index.html#/startprocess/MyApplication%2FNewProcess。 示例中的ApplicationName%2FProcessName字串是URL編碼的。

1. 按照隨附的說明填寫表格。 如有必要，請按一下 **最大化** 以增加表單的可見區域。
1. 如果「附件」頁簽可用，請根據需要添加附件。
1. 如果「附註」標籤可用，請視需要提供任何附註。
1. 執行以下步驟之一：

   * 如果表單有「提交」按鈕，請按一下表單上的「提交」按鈕。
   * 如果表單沒有「提交」按鈕，請按一下表單下方的「完成」 。

   流程管理將啟動流程並將表單路由至需要完成流程中下一個任務的相應人員的待辦事項清單。

   如果您必須在提交表單之前關閉表單，且未遺失所輸入的資料，請儲存草稿，如果程式允許，稍後再完成。 如果表單和程式允許，您也可以按一下 **離線** 之後再從Adobe®Reader®或Adobe®Acrobat®專業版或Acrobat Standard提交。

   >[!NOTE]
   >
   >離線選項僅適用於PDF forms。

## 新增附註和附件 {#adding-notes-and-attachments}

如果進程允許，可以向進程添加註釋和檔案附件。 您可以為參與此程式的其他使用者提供檢視、更新和刪除附註或附件的權限。

### 新增附註 {#add-a-note}

您可以新增多個附註、編輯已寫入的附註，以及刪除這些附註。 每個附註都有一個標題、一個說明，以及一個與其相關聯的存取權限。 您可以在附註上設定下列其中一項存取權限：

* 唯讀（預設權限）
* 讀取/編輯/刪除
* 讀取/編輯
* 讀取/刪除
* 無權存取

1. 開啟任務，然後按一下 **附註** 頁簽，如果進程允許。
1. 在 **標題** ，並在 **附註** 框。
1. 選取 **權限** 供其他參與此過程的用戶使用的注釋級別。
1. 按一下&#x200B;**「確定」**。包含附註的文字檔案會附加至表單。 您可以按一下附註並直接修改文字，以更新附註。 您可以按一下 **刪除** 按鈕 ![垃圾桶影像](assets/icondelete.png) 在注釋旁邊。

### 新增附件 {#add-an-attachment}

您也可以新增關於附件的註解。 您可以對附件設定下列其中一個存取權限：

* 唯讀（預設權限）
* 讀取/編輯/刪除
* 讀取/編輯
* 讀取/刪除
* 無權存取

1. 按一下 **附件** 索引標籤和選取 **附件**.
1. 按一下 **瀏覽** 來選擇要附加的檔案。
1. 選取 **權限** 參與此流程的其他用戶的附件級別。 如果您選取 **閱讀**，其他使用者可將檔案儲存在本機。 如果您選取其中一個編輯權限，其他使用者也可以上傳新檔案來取代您的附件。
1. 按一下&#x200B;**「確定」**。檔案已附加至表單。 您可以按一下 **刪除** 按鈕 ![垃圾桶影像](assets/icondelete.png) 在附件旁邊。

## 保存表單草稿副本 {#saving-draft-copies-of-forms}

如果您必須稍後完成並提交表單，則可以保存表單的草稿副本，這樣您就不會丟失現有的工作。 草稿復本會新增至「待辦事項」頁面上的「草稿」類別。

重新開啟並提交草稿表單後，草稿即會從「草稿」類別中移除。

此外，您也可以設定工作區，將使用者輸入的資訊自動儲存為草稿。 如需詳細資訊，請參閱 [管理偏好設定](/help/forms/using/getting-started-livecycle-html-workspace.md).

>[!NOTE]
>
>「保存」按鈕對某些表單不可用，具體取決於它關聯的過程。

### 儲存草稿副本 {#save-a-draft-copy}

1. 按一下 **儲存** 的下方。 表單會新增至您「待辦事項」頁面上的「草稿」類別。 您對表單所做的所有變更都會儲存。

### 重新開啟草稿副本 {#reopen-a-draft-copy}

1. 在「待辦事項」頁面上，選取 **草稿** 排入佇列，然後按一下表單的草稿副本。

   如果表單包含一系列面板，您可能需要前往結束上次工作階段的面板。

## 將進程添加到收藏夾類別 {#adding-processes-to-the-favorites-category}

您可以將任何程式新增至您的我的最愛類別。 通過設定收藏夾，可以將您經常啟動的所有進程分組到單個類別中，以便快速找到它們。

>[!NOTE]
>
>如果您通常在使用AEM Forms工作區時啟動程式，可以設定「開始位置」偏好設定，以在您啟動AEM Forms工作區時自動顯示「我的最愛」類別。 如需詳細資訊，請參閱管理偏好設定，位於 [AEM Forms工作區快速入門](/help/forms/using/getting-started-livecycle-html-workspace.md).

要將進程標籤為收藏夾，請在其類別中選擇該任務，然後按一下空心星號。 這顆星變黃了。 若要將程式取消標示為我的最愛，請再次按一下金星號。

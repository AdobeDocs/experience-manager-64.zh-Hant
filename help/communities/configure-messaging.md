---
title: 傳訊功能
seo-title: Messaging Feature
description: 配置報文傳送元件
seo-description: Configuring Messaging components
uuid: 29ab63b6-67a1-4eb8-8cf8-c1ff52ff2bac
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 88ee8573-58c4-42cd-8e36-2ea4a0d654e4
exl-id: e03cf05c-2469-4883-ae7b-9d7e6660b71f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 2%

---

# 傳訊功能 {#messaging-feature}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

除了論壇和留言中公開顯示的互動外，AEM Communities的傳訊功能還可讓社群成員更私下互動。

若 [社群網站](overview.md#communitiessites) 中所有規則的URL區段。

傳訊功能提供以下功能：

* 傳送訊息給一或多個社群成員
* 向社區成員組發送消息
* 傳送含附件的訊息
* 轉送訊息
* 回覆訊息
* 刪除訊息
* 還原已刪除的消息

若要啟用和修改傳訊功能，請造訪

* [設定傳訊](messaging.md) 管理員
* [Messaging Essentials](essentials-messaging.md) 開發人員

>[!NOTE]
>
>不支援添加 `Compose Message, Message, or Message List` 元件(可在 `Communities`元件群組)至作者編輯模式中的頁面。

## 配置報文傳送元件 {#configuring-messaging-components}

為社群網站啟用傳訊功能時，系統會完全設定訊息，不需要進一步設定。 如果需要變更預設設定，則會提供此資訊。

### 配置消息清單（消息框） {#configuring-message-list-messagebox}

為了修改 **收件匣**, **已傳送項目**，和 **垃圾** 頁面，在 [作者編輯模式](sites-console.md#authoring-site-content).

在 `Preview` 模式，請選擇 **[!UICONTROL 訊息]** 連結以開啟主要傳訊頁面。 然後選取 **[!UICONTROL 收件匣、已傳送項目或清除]** 以便為該訊息清單配置元件。

在 `Edit` 模式，請在頁面上選取元件。

若要存取設定對話方塊，必須選取 `link`表徵圖。

完成設定後，必須選取 `broken link` 表徵圖。

![chlimage_1-396](assets/chlimage_1-396.png)

一旦取消繼承，就可以選取 `configure` 圖示以開啟設定對話方塊。

![chlimage_1-397](assets/chlimage_1-397.png)

#### 基本標籤 {#basic-tab}

![chlimage_1-398](assets/chlimage_1-398.png)

* **[!UICONTROL 服務選擇器]**
(*必填*)將此值設為屬性的值 `serviceSelector.name` 從 [AEM Communities傳訊作業服務](messaging.md#messaging-operations-service).

* **[!UICONTROL 撰寫頁面]**
(*必填*)成員點按 `Reply` 按鈕。 目標頁面應包含 **[!UICONTROL 撰寫訊息]** 表單。

* **[!UICONTROL 回覆/檢視為資源]**
如果勾選此選項，回覆URL和檢視URL將參考資源，否則資料會在URL中以查詢參數的形式傳遞。

* **[!UICONTROL 設定檔顯示表單]**
用於顯示發件人配置檔案的配置檔案表單。

* **[!UICONTROL 清除資料夾]**
如果選中此選項，則此「消息清單」元件僅顯示標籤為已刪除（清除）的消息。

* **[!UICONTROL 資料夾路徑]**
(*必填*)參考為 `inbox.path.name` 和 `sentitems.path.name` 在 [AEM Communities傳訊作業服務](messaging.md#messaging-operations-service). 為 `Inbox`，請使用 `inbox.path.name`. 為 `Outbox`，請使用 `sentitems.path.name`. 為配置時 `Trash`，請新增兩個包含這兩個值的項目。

#### 顯示標籤 {#display-tab}

![chlimage_1-399](assets/chlimage_1-399.png)

* **[!UICONTROL 標籤讀取按鈕]**
若勾選，則會顯示 
`Read`按鈕，允許將消息標籤為已讀。

* **[!UICONTROL 標籤未讀按鈕]**
若勾選，則會顯示 
`Mark Unread` 按鈕，允許將消息標籤為已讀。

* **[!UICONTROL 刪除按鈕]**
若勾選，則會顯示 
`Delete`按鈕，允許將消息標籤為已讀。 若 **`Message Options`** 也會勾選。

* **[!UICONTROL 訊息選項]**
若勾選，則顯示 
**`Reply`**, **`Reply All`**, **`Forward`** 和 **`Delete`** 按鈕允許重新發送或刪除消息。 若 **`Delete Button`** 也會勾選。

* **[!UICONTROL 每頁報文]**
指定的數量是分頁方案中每頁顯示的最大郵件數。 若未指定數字（保留為空白），則會顯示所有訊息，且沒有分頁。

* **[!UICONTROL 時間戳記模式]**
提供一或多種語言的時間戳記模式。 預設值為en、de、fr、it、es、ja、zh_CN、ko_KR。

* **[!UICONTROL 顯示用戶]**
選擇 
**`Sender`** 或 **`Recipients`** ，以決定要顯示寄件者或收件者。

### 設定撰寫訊息 {#configuring-compose-message}

若要修改撰寫訊息頁面的設定，請在中開啟網站 [作者編輯模式](sites-console.md#authoring-site-content).

在 `Preview`模式，請選擇 **[!UICONTROL 訊息]** 連結以開啟主要傳訊頁面。 然後選取「新增訊息」按鈕以開啟 `Compose Message` 頁面……

在 `Edit` 模式，在包含消息正文的頁上選擇主元件。

若要存取設定對話方塊，必須選取 `link`表徵圖。

完成設定後，必須選取 `broken link` 表徵圖。

![chlimage_1-400](assets/chlimage_1-400.png)

一旦取消繼承，就可以選取 `configure` 圖示以開啟設定對話方塊。

![chlimage_1-401](assets/chlimage_1-401.png)

#### 基本標籤 {#basic-tab-1}

![chlimage_1-402](assets/chlimage_1-402.png)

* **[!UICONTROL 重新導向URL]**
輸入訊息傳送後顯示之頁面的URL。 例如， 
`../messaging.html`。

* **[!UICONTROL 取消URL]**
如果發件人取消郵件，請輸入顯示的頁面URL。 例如， 
`../messaging.html`。

* **[!UICONTROL 消息主體的最大長度]**
「主旨」欄位中允許的字元數上限。 例如500。 預設為無限制。

* **[!UICONTROL 消息正文的最大長度]**
「內容」欄位中允許的字元數上限。 例如10000。 預設為無限制。

* **[!UICONTROL 服務選擇器]**
(*必填*)將此值設為屬性的值 **`serviceSelector.name`** 從 [AEM Communities傳訊作業服務](messaging.md#messaging-operations-service).

#### 顯示標籤 {#display-tab-1}

![chlimage_1-403](assets/chlimage_1-403.png)

* **[!UICONTROL 顯示主題欄位]**
若勾選，則顯示 
`Subject` 欄位，並啟用將主旨新增至訊息。 未勾選預設值。

* **[!UICONTROL 主旨標籤]**
輸入要顯示在 
`Subject` 欄位. 預設為 `Subject`.

* **[!UICONTROL 顯示附加檔案欄位]**
若勾選，則顯示 
`Attachment` 欄位，並啟用將檔案附件新增至訊息的功能。 未勾選預設值。

* **[!UICONTROL 附加檔案標籤]**
輸入要顯示在 
`Attachment` 欄位. 預設為 **`Attach File`**.

* **[!UICONTROL 顯示內容欄位]**
若勾選，則顯示 
`Content` 欄位並啟用添加消息正文。 未勾選預設值。

* **[!UICONTROL 內容標籤]**
輸入要顯示在 
`Content` 欄位. 預設為 **`Body`**.

* **[!UICONTROL 使用RTF編輯器]**
若勾選此選項，表示使用自訂內容文字方塊及其專屬的RTF編輯器。 未勾選預設值。

* **[!UICONTROL 時間戳記模式]**
提供一或多種語言的時間戳記模式。 預設值為en、de、fr、it、es、ja、zh_CN、ko_KR。

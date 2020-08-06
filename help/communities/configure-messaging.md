---
title: 訊息功能
seo-title: 訊息功能
description: 配置消息傳遞元件
seo-description: 配置消息傳遞元件
uuid: 29ab63b6-67a1-4eb8-8cf8-c1ff52ff2bac
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 88ee8573-58c4-42cd-8e36-2ea4a0d654e4
translation-type: tm+mt
source-git-commit: 8c66f2b0053882bd1c998d8e01dbb0573881bc87
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 0%

---


# 訊息功能 {#messaging-feature}

除了在論壇和留言中發生的公開可見互動外，AEM Communities的傳訊功能還可讓社群成員彼此私下互動。

建立社群網站時，可能會 [包含此](overview.md#communitiessites) 功能。

訊息功能可讓您：

* 傳送訊息給一或多個社群成員
* 向社區成員組發送消息
* 傳送包含附件的郵件
* 轉送訊息
* 回覆訊息
* 刪除訊息
* 恢復已刪除的消息

若要啟用並修改訊息功能，請造訪

* [為管理員配置消息](messaging.md) ,
* [適用於開發人員的Messaging](essentials-messaging.md) Essentials

>[!NOTE]
>
>不支援在作者編輯 `Compose Message, Message, or Message List` 模式中將元件( `Communities`位於元件群組)新增至頁面。

## 配置消息傳遞元件 {#configuring-messaging-components}

為社群網站啟用訊息時，系統會完全設定訊息，不需進一步設定。 如果需要更改預設配置，則提供此資訊。

### 配置消息清單（消息框） {#configuring-message-list-messagebox}

為了修改收件箱、已發送項目和 **垃圾筒傳訊功能的「收件匣**」、「已發送項目 **」和「垃圾筒」頁面的訊息清單配置，請在作者編輯模式******[](sites-console.md#authoring-site-content)中開啟站點。

在模 `Preview` 式中，選擇「 **[!UICONTROL 消息]** 」連結以開啟主消息傳遞頁。 然後選取「收 **[!UICONTROL 件匣」、「已傳送項目」或「垃圾桶]** 」，以設定該訊息清單的元件。

在模 `Edit` 式中，選擇頁面上的元件。

要訪問配置對話框，必須通過選擇表徵圖取消繼 `link`承。

配置完成後，必須通過選擇表徵圖來恢復繼 `broken link` 承。

![chlimage_1-396](assets/chlimage_1-396.png)

取消繼承後，將可以選擇表徵圖以 `configure` 開啟配置對話框。

![chlimage_1-397](assets/chlimage_1-397.png)

#### Basic tab {#basic-tab}

![chlimage_1-398](assets/chlimage_1-398.png)

* **[!UICONTROL 服務選擇器]**(*必要*)將此值設為 `serviceSelector.name` AEM Communities Messaging Operations Service中屬性的值 [](messaging.md#messaging-operations-service)。

* **[!UICONTROL 合成頁]**(必&#x200B;*要*)成員按一下按鈕時要開啟的 `Reply` 頁。 目標頁應包含合成 **[!UICONTROL 消息表單]** 。

* **[!UICONTROL 回覆／檢視為資源]**&#x200B;如果勾選，回覆URL和檢視URL將參考資源，否則資料會作為URL中的查詢參數傳遞。

* **[!UICONTROL 描述檔顯示表]**&#x200B;單用於顯示傳送者描述檔的描述檔表單。

* **[!UICONTROL 垃圾筒資]**&#x200B;料夾：如果勾選，此「訊息清單」元件只會顯示標示為已刪除（垃圾筒）的訊息。

* **[!UICONTROL 資料夾路徑]**(*必要*)參考AEM Communities Messaging Operations Service中為 `inbox.path.name` 和 `sentitems.path.name` 設定的 [值](messaging.md#messaging-operations-service)。 為配置時， `Inbox`請使用值添加一個條目 `inbox.path.name`。 為配置時， `Outbox`請使用值添加一個條目 `sentitems.path.name`。 在配置時， `Trash`添加兩個同時具有兩個值的條目。

#### 顯示頁籤 {#display-tab}

![chlimage_1-399](assets/chlimage_1-399.png)

* **[!UICONTROL 標籤讀取按鈕]**&#x200B;如果勾選，則顯示 
`Read`按鈕，允許將消息標籤為已讀取。

* **[!UICONTROL 標籤未讀按鈕]**&#x200B;如果勾選，則顯示 
`Mark Unread` 按鈕，允許將消息標籤為已讀取。

* **[!UICONTROL 刪除按鈕]**&#x200B;如果勾選，則會顯示 
`Delete`按鈕，允許將消息標籤為已讀取。 如果也勾選，將複製 **`Message Options`** 刪除功能。

* **[!UICONTROL 訊息選項]**&#x200B;如果勾選，會顯示 
**`Reply`**、 **`Reply All`**&#x200B;和 **`Forward`****`Delete`** 按鈕，允許重新發送或刪除消息。 如果也勾選，將複製 **`Delete Button`** 刪除功能。

* **[!UICONTROL 每頁消息]**&#x200B;指定的數量是分頁方案中每頁顯示的最大消息數。 如果未指定數字（留空），則會顯示所有訊息，且無分頁。

* **[!UICONTROL 時間戳記模]**&#x200B;式提供一或多種語言的時間戳記模式。 預設值為en、de、fr、it、es、ja、zh_CN、ko_KR。

* **[!UICONTROL 顯示用戶]**&#x200B;選擇 
**`Sender`** 或確 **`Recipients`** 定要顯示「傳送者」或「收件者」。

### 配置合成消息 {#configuring-compose-message}

要修改合成消息頁的配置，請以作者編輯模式打 [開站點](sites-console.md#authoring-site-content)。

在模 `Preview`式中，選擇「 **[!UICONTROL 消息]** 」連結以開啟主消息傳遞頁。 然後選擇「新建消息」按鈕以打 `Compose Message` 開頁面。

在模 `Edit` 式中，選擇包含消息主體的頁面上的主元件。

要訪問配置對話框，必須通過選擇表徵圖取消繼 `link`承。

配置完成後，必須通過選擇表徵圖來恢復繼 `broken link` 承。

![chlimage_1-400](assets/chlimage_1-400.png)

取消繼承後，將可以選擇表徵圖以 `configure` 開啟配置對話框。

![chlimage_1-401](assets/chlimage_1-401.png)

#### Basic tab {#basic-tab-1}

![chlimage_1-402](assets/chlimage_1-402.png)

* **[!UICONTROL 重新導向URL]**&#x200B;輸入訊息傳送後所顯示之頁面的URL。 例如， 
`../messaging.html`。

* **[!UICONTROL 取消URL]**&#x200B;輸入傳送者取消訊息時顯示之頁面的URL。 例如， 
`../messaging.html`。

* **[!UICONTROL 消息主題的最大長]**&#x200B;度「主題」欄位中允許的字元數上限。 例如，500。 預設為無限制。

* **[!UICONTROL 消息正文的最大長]**&#x200B;度「內容」欄位中允許的最大字元數。 例如，10000。 預設為無限制。

* **[!UICONTROL 服務選擇器]**(*必要*)將此值設為 **`serviceSelector.name`** AEM Communities Messaging Operations Service中屬性的值 [](messaging.md#messaging-operations-service)。

#### 顯示頁籤 {#display-tab-1}

![chlimage_1-403](assets/chlimage_1-403.png)

* **[!UICONTROL 顯示主題欄位]**&#x200B;如果勾選，則顯示 
`Subject` 欄位，並啟用將主旨新增至訊息。 未勾選預設值。

* **[!UICONTROL 主題標]**&#x200B;簽輸入要顯示在 
`Subject` 欄位. 預設為 `Subject`。

* **[!UICONTROL 顯示附加檔案欄位]**&#x200B;如果選中，則顯示 
`Attachment` 欄位，並啟用將檔案附件新增至訊息的功能。 未勾選預設值。

* **[!UICONTROL 附加檔案標]**&#x200B;簽輸入要在 
`Attachment` 欄位. 預設為 **`Attach File`**。

* **[!UICONTROL 顯示內容欄位]**&#x200B;如果勾選，則顯示 
`Content` 欄位並啟用新增訊息內文。 未勾選預設值。

* **[!UICONTROL 內容標]**&#x200B;簽輸入要在 
`Content` 欄位. 預設為 **`Body`**。

* **[!UICONTROL With Rich Text Editor]**（富格文本編輯器）如果選中，則表示使用自定義「內容」文本框及其自己的富格文本編輯器。 未勾選預設值。

* **[!UICONTROL 時間戳記模]**&#x200B;式提供一或多種語言的時間戳記模式。 預設值為en、de、fr、it、es、ja、zh_CN、ko_KR。


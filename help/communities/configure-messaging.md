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


# 消息傳遞功能{#messaging-feature}

除了在論壇和留言中發生的公開可見互動外，AEM Communities的傳訊功能還可讓社群成員彼此私下互動。

建立[社區站點](overview.md#communitiessites)時，可包括此功能。

訊息功能可讓您：

* 傳送訊息給一或多個社群成員
* 向社區成員組發送消息
* 傳送包含附件的郵件
* 轉送訊息
* 回覆訊息
* 刪除訊息
* 恢復已刪除的消息

若要啟用並修改訊息功能，請造訪

* [為管理](messaging.md) 員配置消息
* [對開發人員](essentials-messaging.md) 而言的訊息本質

>[!NOTE]
>
>不支援將`Compose Message, Message, or Message List`元件（位於`Communities`元件組中）添加到作者編輯模式下的頁面。

## 配置消息傳遞元件{#configuring-messaging-components}

為社群網站啟用訊息時，系統會完全設定訊息，不需進一步設定。 如果需要更改預設配置，則提供此資訊。

### 配置消息清單（消息框）{#configuring-message-list-messagebox}

要修改消息傳送功能的&#x200B;**收件箱**、**已發送項目**&#x200B;和&#x200B;**垃圾筒**&#x200B;頁面的消息清單配置，請以[作者編輯模式](sites-console.md#authoring-site-content)開啟站點。

在`Preview`模式中，選擇&#x200B;**[!UICONTROL 消息]**&#x200B;連結以開啟主消息傳遞頁。 然後，選擇「收件匣」、「已傳送項目」或「垃圾筒」，以設定該訊息清單的元件。****

在`Edit`模式中，選擇頁面上的元件。

要訪問配置對話框，必須通過選擇`link`表徵圖取消繼承。

配置完成後，必須通過選擇`broken link`表徵圖恢復繼承。

![chlimage_1-396](assets/chlimage_1-396.png)

取消繼承後，可以選擇`configure`表徵圖以開啟配置對話框。

![chlimage_1-397](assets/chlimage_1-397.png)

#### 基本頁籤{#basic-tab}

![chlimage_1-398](assets/chlimage_1-398.png)

* **[!UICONTROL 服務選擇器]**
(*必要*)將此值設為 `serviceSelector.name` AEM Communities Messaging Operations Service中屬 [性的](messaging.md#messaging-operations-service)值。

* **[!UICONTROL 合成頁]**
(必*要*)成員按一下按鈕時要開啟的 `Reply` 頁。目標頁應包含&#x200B;**[!UICONTROL 合成消息]**&#x200B;表單。

* **[!UICONTROL 回覆／檢視為]**
資源如果勾選，回覆URL和檢視URL將參考資源，否則資料會作為URL中的查詢參數傳遞。

* **[!UICONTROL 描述檔顯]**
示表單用於顯示傳送者描述檔的描述檔表單。

* **[!UICONTROL 垃圾]**
筒資料夾如果勾選，此訊息清單元件只會顯示標示為已刪除（垃圾筒）的訊息。

* **[!UICONTROL 資料夾路徑]**
(*必要*)參考 `inbox.path.name` AEM Communities Messaging Operations Service中為 `sentitems.path.name` 和設定 [的值](messaging.md#messaging-operations-service)。為`Inbox`配置時，請使用`inbox.path.name`值添加一個條目。 為`Outbox`配置時，請使用`sentitems.path.name`值添加一個條目。 為`Trash`配置時，請添加兩個具有兩個值的條目。

#### 顯示頁籤{#display-tab}

![chlimage_1-399](assets/chlimage_1-399.png)

* **[!UICONTROL 標籤讀取]**
按鈕如果勾選，則顯示 
`Read`按鈕，允許將消息標籤為已讀取。

* **[!UICONTROL 標籤未讀]**
按鈕如果勾選，會顯示 
`Mark Unread` 按鈕，允許將消息標籤為已讀取。

* **[!UICONTROL 刪除按]**
鈕如果勾選，會顯示 
`Delete`按鈕，允許將消息標籤為已讀取。如果&#x200B;**`Message Options`**&#x200B;也已勾選，將複製刪除功能。

* **[!UICONTROL 訊息選]**
項若勾選，會顯示 
**`Reply`**、 **`Reply All`**&#x200B;和 **`Forward`**  **`Delete`** 按鈕，允許重新傳送或刪除訊息。如果&#x200B;**`Delete Button`**&#x200B;也已勾選，將複製刪除功能。

* **[!UICONTROL 每頁消]**
息指定的數目是分頁方案中每頁顯示的最大消息數。如果未指定數字（留空），則會顯示所有訊息，且無分頁。

* **[!UICONTROL 時間戳]**
記模式提供一或多種語言的時間戳記模式。預設值為en、de、fr、it、es、ja、zh_CN、ko_KR。

* **[!UICONTROL 顯示用]**
戶選擇 
**`Sender`** 或確 **`Recipients`** 定要顯示「傳送者」或「收件者」。

### 配置合成消息{#configuring-compose-message}

要修改合成消息頁的配置，請在[作者編輯模式](sites-console.md#authoring-site-content)中開啟該站點。

在`Preview`模式中，選擇&#x200B;**[!UICONTROL 消息]**&#x200B;連結以開啟主消息傳遞頁。 然後選擇「新建消息」按鈕以開啟`Compose Message`頁。

在`Edit`模式中，選擇包含消息主體的頁面上的主元件。

要訪問配置對話框，必須通過選擇`link`表徵圖取消繼承。

配置完成後，必須通過選擇`broken link`表徵圖恢復繼承。

![chlimage_1-400](assets/chlimage_1-400.png)

取消繼承後，可以選擇`configure`表徵圖以開啟配置對話框。

![chlimage_1-481](assets/chlimage_1-401.png)

#### 基本頁籤{#basic-tab-1}

![chlimage_1-402](assets/chlimage_1-402.png)

* **[!UICONTROL 重新]**
導向輸入訊息傳送後所顯示之頁面的URL。例如， 
`../messaging.html`。

* **[!UICONTROL 取消]**
URL輸入傳送者取消訊息時顯示之頁面的URL。例如， 
`../messaging.html`。

* **[!UICONTROL 消息主題的最]**
大長度「主題」欄位中允許的字元數上限。例如，500。 預設為無限制。

* **[!UICONTROL 消息正文的最]**
大長度「內容」欄位中允許的最大字元數。例如，10000。 預設為無限制。

* **[!UICONTROL 服務選擇器]**
(*必要*)將此值設為 **`serviceSelector.name`** AEM Communities Messaging Operations Service中屬 [性的](messaging.md#messaging-operations-service)值。

#### 顯示頁籤{#display-tab-1}

![chlimage_1-403](assets/chlimage_1-403.png)

* **[!UICONTROL 顯示主題欄]**
位如果勾選，則顯示 
`Subject` 欄位，並啟用將主旨新增至訊息。未勾選預設值。

* **[!UICONTROL 主題]**
標籤輸入要顯示在 
`Subject` 欄位. 預設值為`Subject`。

* **[!UICONTROL 顯示附加檔案]**
欄位如果選中，則顯示 
`Attachment` 欄位，並啟用將檔案附件新增至訊息的功能。未勾選預設值。

* **[!UICONTROL 附加檔]**
案標籤輸入要在 
`Attachment` 欄位. 預設值為&#x200B;**`Attach File`**。

* **[!UICONTROL 顯示內容欄]**
位如果勾選，則顯示 
`Content` 欄位並啟用新增訊息內文。未勾選預設值。

* **[!UICONTROL 內容]**
標籤輸入要顯示在 
`Content` 欄位. 預設值為&#x200B;**`Body`**。

* **[!UICONTROL With Rich Text]**
Editor如果勾選，表示自訂「內容」文字方塊與其專屬的Rich Text編輯器已使用。未勾選預設值。

* **[!UICONTROL 時間戳]**
記模式提供一或多種語言的時間戳記模式。預設值為en、de、fr、it、es、ja、zh_CN、ko_KR。


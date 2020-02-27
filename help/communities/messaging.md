---
title: 配置消息
seo-title: 配置消息
description: 社群訊息
seo-description: 社群訊息
uuid: 35d98667-a82e-4ed1-b6a1-1ffbbe1d08b5
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5cb571ae-eeb5-4943-a6b8-92e346e85be2
translation-type: tm+mt
source-git-commit: 13d890d08a032fe4eef1dac793dcf2a3e682a52c

---


# 配置消息 {#configuring-messaging}

## 概覽 {#overview}

AEM Communities的訊息功能可讓登入網站訪客（成員）彼此傳送訊息，當登入網站時，這些訊息可供存取。

在社群網站建立期間核取方塊，即可啟用社群 [網站的訊息](sites-console.md)。

本頁提供有關預設配置和可能調整的資訊。

如需開發人員的詳細資訊，請參 [閱Messaging Essentials](essentials-messaging.md)。

## 消息傳遞操作服務 {#messaging-operations-service}

[AEM Communities Messaging Operations Service](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) (AEM Communities Messaging Operations Service)可識別處理訊息相關要求的端點、服務應用來儲存訊息的資料夾，以及如果訊息可能包含檔案附件，允許使用哪些檔案類型。

對於使用 [Communities Sites控制台建立的社區站點](sites-console.md)，服務實例已存在，收件箱設定為 `/mail/community/inbox`。

### 社群訊息運作服務 {#community-messaging-operations-service}

如下所示，對於使用站點建立嚮導建立的站點，服務 [的配置存在](sites-console.md)。 選取設定旁的鉛筆圖示，即可檢視或編輯設定：

![chlimage_1-63](assets/chlimage_1-63.png)

### 新設定 {#new-configuration}

要添加新配置，請選擇服務名稱旁邊的加&#x200B;**號&#39;+**&#39;表徵圖：

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL 消息欄位白]**&#x200B;名單指定合成消息元件用戶可以編輯和保存的屬性。 如果新增了表單元素，則需要新增元素ID，才能儲存在SRP中。 預設為兩個項目：主 *題**與內容*。

* **[!UICONTROL 消息框大小限]**&#x200B;制每個用戶消息框中的最大位元組數。 預設 *為1073741824* (1 GB)。

* **[!UICONTROL 消息計數限制]**&#x200B;每個用戶允許的消息總數。 值-1表示允許的消息數不限，但須受消息框大小限制。 預設值 *為1000* (10k)。

* **[!UICONTROL 通知傳送失敗]**&#x200B;如果勾選，則在某些收件者無法傳送訊息時通知傳送者。 已勾選預 *設值*。

* **[!UICONTROL 失敗傳送傳送者id]**&#x200B;傳送失敗訊息中顯示之傳送者名稱。 預設值為 *failureNotifier*。

* **[!UICONTROL 失敗消息模板路徑]**&#x200B;傳遞失敗消息模板根的絕對路徑。 預設值 *為/etc/notification/messaging/default*。

* **[!UICONTROL maxRetries.name]**&#x200B;嘗試重新傳送失敗訊息的次數。 預設值 *為3*。

* **[!UICONTROL minWaitBetweenRetries.name]**&#x200B;在嘗試重新傳送訊息失敗時，等待的秒數。 預設值為*100 *（秒）。

* **[!UICONTROL 計數更新池大]**&#x200B;小用於計數更新的併發線程數。 預設值 *為10*。

* **[!UICONTROL inbox.path.name]**(*必要*)用於資料夾的路徑(相對於用戶節點(/home/users/*username*) **`inbox`** 。 路徑不能以尾隨正斜線&#39;/&#39;結束。 預設值 *為/mail/inbox* 。

* **[!UICONTROL sentitems.path.name]**(*必要*)用於資料夾的路徑，相對於使用者節點(/home/users/*username*) **`senditems`** 。 路徑不能以尾隨正斜線&#39;/&#39;結束。 預設值 *為/mail/sentitems* 。

* **[!UICONTROL supportAttachments.name]**&#x200B;如果選中，用戶可以將附件添加到其郵件中。 已勾選預 *設值*。

* **[!UICONTROL batchSize.name傳]**&#x200B;送給大量收件者時，要一起批次傳送的訊息數。 預設值 *為100*。

* **[!UICONTROL maxTotalAttachmentSize.name]**&#x200B;如果選中supportAttachments，此值將指定所有附件的最大允許總大小（以位元組為單位）。 預設值 *為104857600* (100 MB)。

* **[!UICONTROL attachmentTypeBlickst.name]**&#x200B;副檔名的黑名單，前置詞為&#39;**。**&#x200B;被制度拒絕。 如果未列入黑名單，則允許分機。 可使用「**+**」和「**-**」圖示新增或移除延伸模組。 預設值 *為DEFAULT*。

* **[!UICONTROL allowedAttachmentTypes.name]**
   **(需&#x200B;*要操作*** )副檔名的白名單，與黑名單相反。 若要允許除列入黑名單外的所有副檔名，請使用「**-**」圖示來移除單一空白項目。

* **[!UICONTROL serviceSelector.name]**(*必要*)調用服務的絕對路徑（端點）（虛擬資源）。 所選路徑的根必須包含在OSGi配置的「 *Execution Paths* （執行路徑）」配 [ 置設定中， `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver)如 `/bin/`、 `/apps/`和中 `/services/`。 要為站點的消息功能選擇此配置，此端點將作為 **`Service selector`** 的值提 `Message List and Compose Message components` 供(請 [參閱消息功能](configure-messaging.md))。 預設值為 */bin/messaging* 。

* **[!UICONTROL fieldWhitelist.name]**&#x200B;使用 **消息欄位白名單**。

>[!CAUTION]
>
>每次開啟 `Messaging Operations Service` 配置進行編輯時，如果已刪 `allowedAttachmentTypes.name` 除，則會重新添加一個空條目，使屬性可配置。 單個空條目有效地禁用檔案附件。
>
>若要允許所有副檔名（黑名單除外），請使用「**-**」圖示（再次）移除單一空白項目，再按一下「儲存」 ****。

## 疑難排解 {#troubleshooting}

疑難排解問題的一種方式是啟用 [記錄檔中的除錯訊息。](../../help/sites-administering/troubleshooting.md)

另請參閱 [個別服務的記錄者和撰寫者](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services)。

要監視的包是 `com.adobe.cq.social.messaging`。

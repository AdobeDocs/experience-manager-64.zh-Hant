---
title: 設定傳訊
seo-title: Configuring Messaging
description: Communities傳訊
seo-description: Communities messaging
uuid: 35d98667-a82e-4ed1-b6a1-1ffbbe1d08b5
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5cb571ae-eeb5-4943-a6b8-92e346e85be2
role: Admin
exl-id: 0e906f67-b908-4c41-b243-e4f90100ce5d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 1%

---

# 設定傳訊 {#configuring-messaging}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 概觀 {#overview}

AEM Communities的傳訊功能可讓登入的網站訪客（成員）相互傳送訊息，這些訊息在登入網站時便可存取。

在 [社群網站建立](sites-console.md).

此頁面提供預設配置和可能調整的資訊。

如需開發人員的其他資訊，請參閱 [Messaging Essentials](essentials-messaging.md).

## 報文傳送操作服務 {#messaging-operations-service}

此 [AEM Communities傳訊作業服務](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) 標識處理郵件相關請求的端點、服務應用於儲存郵件的資料夾，以及如果郵件中可能包含檔案附件，則允許哪些檔案類型。

針對使用 [Communities Sites主控台](sites-console.md)，服務的例項已存在，而收件匣設為 `/mail/community/inbox`.

### 社區消息傳送操作服務 {#community-messaging-operations-service}

如下所示，使用建立的網站已具備服務的設定 [網站建立精靈](sites-console.md). 選取設定旁的鉛筆圖示，即可檢視或編輯設定：

![chlimage_1-63](assets/chlimage_1-63.png)

### 新配置 {#new-configuration}

要添加新配置，請選擇加號「**+**&#x200B;服務名稱旁的「 」表徵圖：

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL 訊息欄位允許清單]**
指定撰寫訊息元件使用者可編輯及保留的屬性。 如果新增了新的表單元素，則需要新增元素ID，才能儲存在SRP中。 預設值為兩個項目： 
*主旨* 和 *內容*.

* **[!UICONTROL 訊息方塊大小限制]**
每個用戶消息框中的最大位元組數。 預設為 
*1073741824* (1 GB)。

* **[!UICONTROL 消息計數限制]**
每個使用者允許的訊息總數。 值為–1表示允許的消息數量不限，但以消息框大小限制為前提。 預設為 
*10000* (10k)。

* **[!UICONTROL 通知傳送失敗]**
如果已勾選此選項，則在某些收件者無法傳送訊息時通知寄件者。 預設為 
*已勾選*.

* **[!UICONTROL 失敗傳送寄件者ID]**
傳送失敗訊息中顯示的寄件者名稱。 預設為 
*failureNotifier*.

* **[!UICONTROL 失敗消息模板路徑]**
傳送失敗的訊息範本根的絕對路徑。 預設為 
*/etc/notification/messaging/default*.

* **[!UICONTROL maxRetries.name]**
嘗試重新傳送失敗訊息的次數。 預設為 
*3*.

* **[!UICONTROL minWaitBetweenRetries.name]**
嘗試在無法發送時重新發送消息之間等待的秒數。 預設為*100 *（秒）。

* **[!UICONTROL 計數更新池大小]**
用於計數更新的併發線程數。 預設為 
*10*.

* **[!UICONTROL inbox.path.name]**
(
*必填*)相對於使用者節點(/home/users/*用戶名*)，以用於 **`inbox`** 檔案夾。 路徑不得以尾隨正斜線「/」結尾。 預設為 */mail/inbox* .

* **[!UICONTROL sentitems.path.name]**
(
*必填*)相對於使用者節點(/home/users/*用戶名*)，以用於 **`senditems`** 檔案夾。 路徑不得以尾隨正斜線「/」結尾。 預設為 */mail/sentitems* .

* **[!UICONTROL supportAttachments.name]**
如果勾選此選項，使用者就能將附件新增至其訊息。 預設為 
*已勾選*.

* **[!UICONTROL batchSize.name]**
傳送給大群收件者時，要一起批次傳送的訊息數。 預設為 
*100*.

* **[!UICONTROL maxTotalAttachmentSize.name]**
如果選中了supportAttachments，此值將指定所有附件的最大允許總大小（以位元組為單位）。 預設為 
*104857600* (100 MB)。

* **[!UICONTROL attachmentTypeBlocklist.name]**
副檔名的封鎖清單，首碼為「
**。**&#39;，系統將拒絕此選項。 如果未列入封鎖名單，則允許擴充功能。 可使用&#x200B;**+**&#39;和&#39;**-**」表徵圖。 預設為 *預設*.

* **[!UICONTROL allowedAttachmentTypes.name]**

   **(*需要的操作*)** 副檔名的允許清單，與封鎖清單相反。 若要允許所有副檔名，但列入封鎖名單的除外，請使用「**-**「 」表徵圖，刪除單個空條目。

* **[!UICONTROL serviceSelector.name]**
(*必填*)叫用服務的絕對路徑（端點）（虛擬資源）。 所選路徑的根必須包含在 *執行路徑* OSGi配置的配置設定 [ `Apache Sling Servlet/Script Resolver and Error Handler`](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver)，例如 `/bin/`, `/apps/`，和 `/services/`. 要為站點的消息傳送功能選擇此配置，將提供此端點作為 **`Service selector`** 值 `Message List and Compose Message components` (請參閱 [訊息功能](configure-messaging.md))。 預設為 */bin/messaging* .

* **[!UICONTROL fieldAllowlist.name]**
使用 
**訊息欄位允許清單**.

>[!CAUTION]
>
>每次a `Messaging Operations Service` 若要編輯，請開啟設定 `allowedAttachmentTypes.name` 已移除，則會重新新增空白項目，以讓屬性可設定。 單個空條目有效地禁用了檔案附件。
>
>若要允許所有副檔名，但列入封鎖名單的除外，請使用「**-**「 」表徵圖，在按一下 **[!UICONTROL 儲存]**.

## 疑難排解 {#troubleshooting}

疑難排解的一種方式是啟用 [在日誌中調試消息。](../../help/sites-administering/troubleshooting.md)

另請參閱 [個人服務的記錄器和撰寫器](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

要監視的包是 `com.adobe.cq.social.messaging`.

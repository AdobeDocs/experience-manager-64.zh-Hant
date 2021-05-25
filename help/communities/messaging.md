---
title: 設定傳訊
seo-title: 設定傳訊
description: Communities傳訊
seo-description: Communities傳訊
uuid: 35d98667-a82e-4ed1-b6a1-1ffbbe1d08b5
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5cb571ae-eeb5-4943-a6b8-92e346e85be2
role: Administrator
exl-id: 0e906f67-b908-4c41-b243-e4f90100ce5d
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# 配置消息{#configuring-messaging}

## 概覽 {#overview}

AEM Communities的傳訊功能可讓登入的網站訪客（成員）相互傳送訊息，這些訊息在登入網站時便可存取。

在[社群網站建立](sites-console.md)期間勾選方塊，即可為社群網站啟用傳訊功能。

此頁面提供預設配置和可能調整的資訊。

如需開發人員的其他資訊，請參閱[Messaging Essentials](essentials-messaging.md)。

## 報文傳送操作服務{#messaging-operations-service}

[AEM Communities報文傳送操作服務](http://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl)標識處理報文傳送相關請求的端點、服務應用於儲存報文的資料夾，如果報文可能包含檔案附件，則允許哪些檔案類型。

對於使用[Communities Sites控制台](sites-console.md)建立的社區站點，服務實例已存在，收件箱設定為`/mail/community/inbox`。

### 社區消息傳送操作服務{#community-messaging-operations-service}

如下所示，使用[站點建立嚮導](sites-console.md)建立的站點存在服務的配置。 選取設定旁的鉛筆圖示，即可檢視或編輯設定：

![chlimage_1-63](assets/chlimage_1-63.png)

### 新配置{#new-configuration}

若要新增新設定，請選取服務名稱旁的加號「**+**」圖示：

![chlimage_1-64](assets/chlimage_1-64.png)

* **[!UICONTROL 消息欄位允]**
許清單指定撰寫消息元件用戶可以編輯和保留的屬性。如果新增了新的表單元素，則需要新增元素ID，才能儲存在SRP中。 預設值為兩個項目： 
** 主旨 *與內容*。

* **[!UICONTROL 消息框大]**
小限制每個用戶的消息框中的最大位元組數。預設為 
*1073741824* (1 GB)。

* **[!UICONTROL 消息計數]**
限制每個用戶允許的消息總數。值為–1表示允許的消息數量不限，但以消息框大小限制為前提。 預設為 
*1000* (10k)。

* **[!UICONTROL 通知傳送失]**
敗如果勾選此選項，則在某些收件者無法傳送訊息時通知寄件者。預設為 
*已勾選*.

* **[!UICONTROL 傳送失敗的寄件]**
者id傳送失敗訊息中顯示的寄件者名稱。預設為 
*failureNotifier*。

* **[!UICONTROL 失敗消息模]**
板path傳遞的絕對路徑失敗消息模板根。預設為 
*/etc/notification/messaging/default*。

* **[!UICONTROL maxReties.]**
name嘗試重新傳送失敗訊息的次數。預設為 
*3*.

* **[!UICONTROL minWaitBetweenReties.]**
name在嘗試重新發送消息失敗時，兩次等待的秒數。預設為*100 *（秒）。

* **[!UICONTROL 計數更新池]**
大小用於計數更新的併發線程數。預設為 
*10*.

* **[!UICONTROL inbox.path.name]**
(
*必要*)要用於資料夾的相對於使用者節點(/home/users/*username*)的 **`inbox`** 路徑。路徑不得以尾隨正斜線「/」結尾。 預設值為&#x200B;*/mail/inbox* 。

* **[!UICONTROL sentitems.path.name]**
(
*必要*)要用於資料夾的相對於使用者節點(/home/users/*username*)的 **`senditems`** 路徑。路徑不得以尾隨正斜線「/」結尾。 預設值為&#x200B;*/mail/sentitems* 。

* **[!UICONTROL supportAttachments.]**
name如果選中此選項，用戶可以向其郵件中添加附件。預設為 
*已勾選*.

* **[!UICONTROL batchSize.]**
name傳送至大群收件者時，要一起批次傳送的訊息數。預設為 
*100*。

* **[!UICONTROL maxTotalAttachmentSize.]**
name如果已勾選supportAttachments，此值將指定所有附件的允許最大總大小（以位元組為單位）。預設為 
*104857600* (100 MB)。

* **[!UICONTROL attachmentTypeBlocklist.]**
name檔案副檔名的封鎖清單，首碼為「
**。**&#39;，系統將拒絕此選項。如果未列入封鎖名單，則允許擴充功能。 可以使用「**+**」和「**-**」表徵圖添加或刪除擴展。 預設值為&#x200B;*DEFAULT*。

* **[!UICONTROL allowedAttachmentTypes.name]**

   **(*需要動作*)** 副檔名的允許清單，與封鎖清單相反。若要允許所有副檔名，但列入封鎖名單的副檔名除外，請使用「**-**」圖示來移除單一空白項目。

* **[!UICONTROL serviceSelector.name]**
(*必要*)用來叫用服務的絕對路徑（端點）（虛擬資源）。所選路徑的根必須包含在OSGi配置[ `Apache Sling Servlet/Script Resolver and Error Handler` ](http://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver)的&#x200B;*執行路徑*&#x200B;配置設定中，如`/bin/`、`/apps/`和`/services/`。 要為站點的消息功能選擇此配置，此端點將作為`Message List and Compose Message components`的&#x200B;**`Service selector`**&#x200B;值提供（請參閱[消息功能](configure-messaging.md)）。 預設值為&#x200B;*/bin/messaging* 。

* **[!UICONTROL fieldAllowlist.]**
nameUse 
**訊息欄位允許清單**。

>[!CAUTION]
>
>每次開啟`Messaging Operations Service`配置進行編輯時，如果已刪除`allowedAttachmentTypes.name`，則會重新添加一個空條目，以使屬性可配置。 單個空條目有效地禁用了檔案附件。
>
>若要允許所有副檔名，除列入封鎖名稱外，請使用「**-**」圖示，在按一下&#x200B;**[!UICONTROL 儲存]**&#x200B;前先（再次）移除單一空白項目。

## 疑難排解 {#troubleshooting}

疑難排解問題的一種方式是啟用日誌中的[調試消息。](../../help/sites-administering/troubleshooting.md)

另請參閱[個別服務的記錄器和寫入器](../../help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services)。

要監視的包為`com.adobe.cq.social.messaging`。

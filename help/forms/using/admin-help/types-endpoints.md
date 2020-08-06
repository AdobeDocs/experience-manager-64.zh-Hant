---
title: 端點類型
seo-title: 端點類型
description: 瞭解不同類型的端點。
seo-description: 瞭解不同類型的端點。
uuid: c899245c-14cc-4035-9440-95a5b6c1e47f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 8fe572e0-8a53-4129-940f-3fdb990073fe
translation-type: tm+mt
source-git-commit: d04e08e105bba2e6c92d93bcb58839f1b5307bd8
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---


# 端點類型 {#types-of-endpoints}

必須先配置並啟用端點，才能使用服務。 端點指定如何調用服務。

>[!NOTE]
>
>在Workbench中，端點稱為起點。

可以將下列類型的端點添加到服務中。 並非所有服務都支援所有端點：

**電子郵件：** 允許用戶通過向指定的電子郵件帳戶發送包含一個或多個檔案附件的電子郵件來調用服務。 在設定電子郵件端點之前，您必須設定所需的電子郵件帳戶。 （請參閱設定電子郵件端點。）

**Watched資料夾：** 允許用戶通過將檔案放置在以定義間隔掃描的資料夾中來調用服務。 （請參閱設定監看的資料夾端點。）

**TaskManager:** 使工作區用戶能夠調用服務。

**遠端：** 讓使用Flex建立的應用程式可使用（AEM表單不建議使用）AEM表單Remoting來叫用服務。 系統會為每個激活的服務自動建立遠程端點。 建立的Flex目標與端點名稱相同，而Flex用戶端可建立指向此目標的遠端物件，以叫用相關服務的作業。

**SOAP:** 可讓使用AEM表單程式設計API開發的用戶端應用程式，使用SOAP模式來叫用服務。 系統會為每個已激活的服務自動建立SOAP端點。

**注意**: *當在Adobe Acrobat或Adobe Reader中檢視檔案時，使用SOAP端點時，可從檔案安全性檔案中移除安全性。 For details on how to disable SOAP enpoints on your LCRM documents, see[Disable SOAP endpoints for document security documents](/help/forms/using/admin-help/configuring-client-server-options.md#disable-soap-endpoints-for-document-security-documents)*

**EJB:** Enables a client application developed using the AEM forms programming APIs to invoke the service using Enterprise JavaBeans (EJB) mode. An EJB endpoint is automatically created for each activated service.

**WSDL:** Enables a client application developed using the AEM forms programming APIs to invoke the service using Web Service Definition Language (WSDL). The Core Configurations page contains an option to enable WSDL generation for all services that are part of AEM forms. (See Configure general AEM forms settings.)

**REST:** Processes created in Workbench can be configured so that you can invoke them through Representational State Transfer (REST) requests. REST requests are sent from HTML pages. That is, you can invoke a AEM forms process directly from a web page using a REST request.

電子郵件、TaskManager、Watched資料夾和遠程端點僅顯示服務的特定操作。 添加這些端點需要第二個配置步驟來選擇調用服務、設定配置參數以及指定輸入和輸出參數映射的方法。

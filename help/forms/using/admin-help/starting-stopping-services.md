---
title: 啟動和停止服務
seo-title: Starting and stopping services
description: 了解如何啟動和停止與AEM Forms模組以及應用程式伺服器和資料庫相關聯的服務。
seo-description: Learn how to start and stop services associated with AEM Forms modules and the application server and database.
uuid: 8c831cb2-4165-4118-8a09-764cec4e5e05
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_services
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: b93060bd-c6e1-40d2-8acd-ccafb8ed56da
exl-id: 6e0607d6-171c-4119-95a1-373b30fb63c1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 1%

---

# 啟動和停止服務 {#starting-and-stopping-services}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

AEM表單包含兩種服務：

* 控制AEM表單應用程式伺服器和資料庫的服務。
* 控制AEM表單模組的服務

## 啟動或停止與AEM表單模組相關聯的服務 {#start-or-stop-the-services-associated-with-aem-forms-modules}

AEM表單模組(例如Forms、Rights Management、輸出)以服務形式運作。 有時，您可能需要停止或啟動這些AEM表單模組的服務。 例如，變更服務的設定後，您必須停止並重新啟動AEM Forms服務。

1. 在管理控制台中，按一下 **服務** > **應用程式和服務** > **服務管理**.
1. 在「服務管理」頁上，選擇要停止或啟動的服務旁邊的複選框，然後按一下停止或啟動。

## 啟動或停止應用程式伺服器和資料庫的服務 {#start-or-stop-services-for-the-application-server-and-database}

AEM表單的完整實作包括應用程式伺服器和資料庫服務：

* *`[application server]`* 適用於AEM forms
* *`[database]`* 適用於AEM forms

在Windows上，可透過 **管理工具** > **服務面板**. 例如，如果您使用統包方法在JBoss上安裝AEM表單，則您的系統可使用下列服務：

* 適用於Adobe Experience Manager表單的JBoss
* MySQL for Adobe Experience Manager表單

從「服務」面板的清單中選擇這些服務，然後按一下面板上的適當操作按鈕，以啟動或停止這些服務。

在UNIX®或Linux上，從命令行輸入以下文本，其中 *`[service name]`* 是您正在驗證的服務的名稱：

```as3
     ps -A | grep [service name]
```

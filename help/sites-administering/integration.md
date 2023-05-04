---
title: 解決方案整合
seo-title: Solutions Integration
description: 進一步了解AEM中的解決方案整合。
seo-description: Learn more about Solutions Integration in AEM.
uuid: 3bf56b1b-284d-4f14-8974-0a595ece5028
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: b5ff918d-08ab-4307-a807-693468fc083b
exl-id: 1ee7ccbd-8654-4d03-8a67-2c41863ae951
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 3%

---

# 解決方案整合{#solutions-integration}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

* [與Adobe Marketing Cloud整合](/help/sites-administering/marketing-cloud.md)
* [與第三方服務整合](/help/sites-administering/third-party-services.md)
* [Analytics與外部提供者](/help/sites-administering/external-providers.md)
* [目錄製作者](/help/sites-administering/catalog-producer.md)
* [SharePoint Connector](/help/sites-administering/sharepoint-connector.md)

有關將AEM與其他Adobe或協力廠商服務整合的資訊如下：

>[!NOTE]
>
>如果您使用自訂代理設定與整合，則需要同時設定兩個HTTP用戶端代理設定，因為AEM的某些功能使用3.x API，而其他一些功能則使用4.x API:
>
>* 3.x的設定 [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x的設定 [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>


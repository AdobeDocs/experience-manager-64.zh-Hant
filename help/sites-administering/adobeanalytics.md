---
title: 整合 Adobe Analytics
seo-title: 整合 Adobe Analytics
description: 了解如何整合AEM與Adobe Analytics。
seo-description: 了解如何整合AEM與Adobe Analytics。
uuid: 8329d891-1897-46f6-80ee-40244b079c0e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 0089394f-0107-49eb-ad73-52e9cabe71b1
exl-id: ca11bfcd-06d1-4ca9-9069-afa91d8a6610
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 21%

---

# 整合 Adobe Analytics{#integrating-with-adobe-analytics}

整合Adobe Analytics和AEM可讓您追蹤網頁活動：

* Adobe Analytics設定可讓AEM使用Adobe Analytics驗證。
* 架構可識別傳送至Adobe Analytics報表套裝的資料。

資料包括頁面和用戶資料；例如：

* AEM元件收集的資料
* 連結點按
* 視訊使用資訊
* 來自Adobe Analytics的頁面瀏覽次數

下列頁面可協助您設定整合：

* [連接Adobe Analytics和建立框架](/help/sites-administering/adobeanalytics-connect.md)
* [設定Adobe Analytics的連結追蹤](/help/sites-administering/adobeanalytics-link.md)
* [將元件資料與Adobe Analytics屬性對應](/help/sites-administering/adobeanalytics-mapping.md)
* [設定Adobe Analytics的視訊追蹤](/help/sites-administering/adobeanalytics-video.md)

您也可以使用[選擇加入精靈](/help/sites-administering/opt-in.md)輕鬆執行整合。

>[!NOTE]
>
>另請參閱作法文章：[使用DTM](https://helpx.adobe.com/experience-manager/using/integrate-digital-marketing-solutions.html)將AEM與Adobe Target和Adobe Analytics整合。

## 更多資訊 {#further-information}

請參閱：

* [擴充Adobe Analytics整](/help/sites-developing/extending-analytics.md) 合，以取得開發可收集使用者資料的元件和自訂Adobe Analytics架構的相關資訊。
* 知識庫文章[Adobe Analytics整合 — 疑難排解問題](https://helpx.adobe.com/experience-manager/kb/sitecatalystintegrationtroubleshooting.html)，以取得疑難排解Adobe Analytics整合的相關資訊。

>[!NOTE]
>
>如果您使用Adobe Analytics搭配自訂的代理設定，則需要 [設定](/help/sites-deploying/configuring-osgi.md) Apache HTTP Client **** Proxy設定所需的兩個OSGi組合 (例如，搭配Web主控台)。由於AEM的某些功能使用3.x API，而其他功能則使用4.x API，因此這兩者皆為必要。設定：
>
>* **Day Commons HTTP Client 3.1** 以設定3.x API;\
   >  例如， [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
   >
   >
* **Apache HTTP元件Proxy** 設定以設定4.x API;
>
>  
例如， [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)

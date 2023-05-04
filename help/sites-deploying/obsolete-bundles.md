---
title: 升級後卸載的過時套件組合清單
seo-title: List of Obsolete Bundles Uninstalled After the Upgrade
description: 詳細說明升級至AEM 6.3時自動解除安裝的套件組合的清單。
seo-description: A list detailing the bundles that are automatically uninstalled when upgrading to AEM 6.3.
uuid: b015e857-31c1-4982-b71c-f3201b49ec8e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: 797a6f3b-d2a8-4835-81ab-a1602677417f
feature: Upgrading
exl-id: 0f075a01-f286-4e16-9061-4e902c553eb9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 2%

---

# 升級後卸載的過時套件組合清單{#list-of-obsolete-bundles-uninstalled-after-the-upgrade}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>如果您的程式碼需仰賴這些套件組合，請務必聯絡Adobe支援，並要求受影響地區的相容性套件。

升級至AEM 6.3時，系統會根據執行升級的AEM版本，自動解除安裝下列套件組合：

**AEM 6.1:**

* org.eclipse.equinox.region,1.1.0.v20120522-1841版，活動
* org.apache.sling.installer.factory.subsems，版本1.0.0，活動
* org.apache.aries.subsystem.core，版本1.2.0，活動
* org.apache.aries.subsystem.api，版本1.1.0，活動
* org.apache.felix.resolver，版本1.0.0，作用中
* org.osgi.service.subsystem.region.context.0，版本1.0.0，活動
* com.adobe.cq.cq-creativecloud-cloudims，版本0.0.10，活動
* com.adobe.cq.cq-creativecloud-commons，版本0.0.8，活動
* com.adobe.cq.cq-creativecloud-filesync，版本0.0.12，已安裝
* com.adobe.cq.cq-creativecloud-storage，版本0.0.8，已安裝
* biz.aQute.bndlib, 1.43.0版，活動
* com.day.cq.dam.commons.nekohtml，版本0.9.5，活動
* com.day.cq.mcm.cq-mcm-silverpop-integration, 1.2.2版， Active

**AEM 6.0:**

* org.apache.sling.discovery.impl，版本1.1.6，活動
* com.adobe.granite.installer.patch，版本0.4.0，活動
* biz.aQute.bndlib, 1.43.0版，活動
* com.day.cq.cq-jobs-core,5.4.0版，活動
* com.day.cq.cq-opensocial，版本5.7.2，活動
* com.day.cq.cq-pinauthhandler，版本1.1.2，活動
* com.day.cq.dam.commons.nekohtml，版本0.9.5，活動
* com.day.cq.mcm.cq-mcm-silverpop-integration, 1.1.6版， Active
* com.day.cq.wcm.cq-wcm-mobile-phonegap-build-integration，版本5.7.18，活動

**CQ 5.6.1:**

* biz.aQute.bndlib, 1.43.0版，活動
* com.day.cq.cq-pinauthhandler，版本1.0.0，活動
* com.day.cq.dam.commons.nekohtml，版本0.9.5，活動
* com.day.crx.crxde-support，版本2.3.14，已安裝
* com.day.cq.mcm.cq-mcm-silverpop-integration, 1.0.2版， Active

**CQ 5.6.0:**

* com.day.cq.cq-pinauthhandler，版本1.0.0，活動
* com.day.cq.dam.commons.nekohtml，版本0.9.5，活動
* com.day.crx.crxde-support，版本2.3.14，已安裝

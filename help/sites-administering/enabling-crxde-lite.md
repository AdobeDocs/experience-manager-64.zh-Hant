---
title: 在AEM中啟用CRXDE Lite
seo-title: Enabling CRXDE Lite in AEM
description: 了解如何在AEM中啟用CRXDE Lite。
seo-description: Learn how to enable CRXDE Lite in AEM.
uuid: d7a3db67-6384-463b-9aa9-f08ecc6c99c6
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 72df3ece-badf-466b-8f9a-0ec985d87741
exl-id: 3d8dc987-2ff9-4f71-bc07-48018caa3af4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 3%

---

# 在AEM中啟用CRXDE Lite{#enabling-crxde-lite-in-aem}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

為確保AEM安裝盡可能安全，安全性檢查清單建議 [禁用WebDAV](/help/sites-administering/security-checklist.md#disable-webdav) 在生產環境中。

然而，CRXDE Lite取決於 `org.apache.sling.jcr.davex` 捆綁以正常運行，因此禁用WebDAV將有效地禁用CRXDE Lite。

發生此情況時，請瀏覽至 `https://serveraddress:4502/crx/de/index.jsp` 將顯示空的根節點，而所有CRXDE Lite資源的HTTP請求將會失敗：

```xml
404 Resource at '/crx/server/crx.default/jcr:root/.1.json' not found: No resource found
```

雖然此建議旨在盡可能減少攻擊面，但系統管理員有時需要存取CRXDE Lite，才能瀏覽生產執行個體的內容或除錯問題。

如果禁用，則可以按照以下過程開啟CRXDE Lite:

1. 前往OSGi元件主控台，網址為 `http://localhost:4502/system/console/components`
1. 搜尋下列元件：

   * `org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet`

1. 按一下扳手旁的圖示，即可查看其設定選項：

   ![chlimage_1-80](assets/chlimage_1-80.png)

1. 建立下列設定：

   * **根路徑:** `/crx/server`
   * 勾選下方的方塊 **使用絕對URI**.

1. 使用完CRXDE Lite後，請務必再次停用WebDAV。

您也可以執行以下命令，透過cURL啟用CRXDE Lite:

```shell
curl -u admin:admin -F "jcr:primaryType=sling:OsgiConfig" -F "alias=/crx/server" -F "dav.create-absolute-uri=true" -F "dav.create-absolute-uri@TypeHint=Boolean" http://localhost:4502/apps/system/config/org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet
```

## 其他資源 {#other-resources}

如需AEM 6安全性功能的詳細資訊，請參閱下列頁面：

* [AEM安全性檢查清單](/help/sites-administering/security-checklist.md)
* [以生產就緒模式執行AEM](/help/sites-administering/production-ready.md)

---
title: Admin Console
seo-title: Admin Consoles
description: 了解如何使用AEM中可用的Admin Console。
seo-description: Lear how to use the Admin Consoles available in AEM.
uuid: 701dc57c-f7b4-421e-a847-577ae2585e80
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 98ba3093-1edb-4891-abbe-47cf6e4f1feb
exl-id: f3c03562-aaeb-4d43-aee1-d92d661ee329
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 3%

---

# Admin Console{#admin-consoles}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

依預設，已停用透過管理控制台切換至傳統UI的功能。 因此，將滑鼠游標移至特定控制台圖示上時會顯示的快顯圖示（可存取傳統UI）將不再顯示。

![screen_shot_2018-03-23at111956](assets/screen_shot_2018-03-23at111956.png)

每個主控台的 `/libs/cq/core/content/nav` 可個別重新啟用，以便 **傳統UI** 將滑鼠移到控制台圖示上時，選項會再次彈出。

在此範例中，我們將重新啟用Sites主控台的傳統UI。

1. 使用CRXDE Lite，尋找與要重新啟用傳統UI之Admin Console對應的節點。 可在下方找到：

   `/libs/cq/core/content/nav`

   例如

   [ `http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav`](http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav)

1. 選取與要重新啟用傳統UI之主控台相對應的節點。 例如，我們將重新啟用Sites主控台的傳統UI。

   `/libs/cq/core/content/nav/sites`

1. 使用 **覆蓋節點** 選項；例如：

   * **路徑**: `/apps/cq/core/content/nav/sites`
   * **重疊位置**: `/apps/`
   * **匹配節點類型**:活動（選取核取方塊）

1. 將下列布林屬性新增至覆蓋節點：

   `enableDesktopOnly = {Boolean}true`

1. 此 **傳統UI** 「管理控制台」中的彈出視窗選項可再次使用「 」選項。

   ![screen_shot_2018-03-23at111924](assets/screen_shot_2018-03-23at111924.png)

對您要重新啟用傳統UI版本存取權的每個主控台重複這些步驟。

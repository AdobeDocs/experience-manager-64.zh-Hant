---
title: Admin Console
seo-title: Admin Console
description: 了解如何使用AEM中可用的Admin Console。
seo-description: 了解如何使用AEM中可用的Admin Console。
uuid: 701dc57c-f7b4-421e-a847-577ae2585e80
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 98ba3093-1edb-4891-abbe-47cf6e4f1feb
exl-id: f3c03562-aaeb-4d43-aee1-d92d661ee329
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Admin Console{#admin-consoles}

依預設，已停用透過管理控制台切換至傳統UI的功能。 因此，將滑鼠游標移至特定控制台圖示上時會顯示的快顯圖示（可存取傳統UI）將不再顯示。

![screen_shot_2018-03-23at111956](assets/screen_shot_2018-03-23at111956.png)

`/libs/cq/core/content/nav`中具有傳統UI版本的每個控制台都可以單獨重新啟用，這樣&#x200B;**傳統UI**&#x200B;選項就會在將滑鼠移到控制台表徵圖上時再次彈出。

在此範例中，我們將重新啟用Sites主控台的傳統UI。

1. 使用CRXDE Lite，尋找與要重新啟用傳統UI之Admin Console對應的節點。 可在下方找到：

   `/libs/cq/core/content/nav`

   例如

   [ `http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav`](http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav)

1. 選取與要重新啟用傳統UI之主控台相對應的節點。 例如，我們將重新啟用Sites主控台的傳統UI。

   `/libs/cq/core/content/nav/sites`

1. 使用&#x200B;**覆蓋節點**&#x200B;選項建立覆蓋；例如：

   * **路徑**:  `/apps/cq/core/content/nav/sites`
   * **重疊位置**: `/apps/`
   * **匹配節點類型**:活動（選取核取方塊）

1. 將下列布林屬性新增至覆蓋節點：

   `enableDesktopOnly = {Boolean}true`

1. 在管理控制台中，「**傳統UI**」選項會再次顯示為彈出式選項。

   ![screen_shot_2018-03-23at111924](assets/screen_shot_2018-03-23at111924.png)

對您要重新啟用傳統UI版本存取權的每個主控台重複這些步驟。

---
title: 管理控制台
seo-title: 管理控制台
description: 瞭解如何使用AEM中提供的管理控制台。
seo-description: 瞭解如何使用AEM中提供的管理控制台。
uuid: 701dc57c-f7b4-421e-a847-577ae2585e80
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 98ba3093-1edb-4891-abbe-47cf6e4f1feb
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# 管理控制台{#admin-consoles}

依預設，已停用透過管理控制台切換至傳統UI的功能。 因此，將滑鼠游標移至特定控制台圖示上時所看到的彈出式圖示（允許存取傳統UI）不再顯示。

![screen_shot_2018-03-23at111956](assets/screen_shot_2018-03-23at111956.png)

每個包含Classic UI版本的控制台都可 `/libs/cq/core/content/nav` 以個別重新啟用，如此當將滑鼠游標移至控制台圖示時， **Classic UI** 選項就會再次彈出至控制台圖示上。

在此範例中，我們將重新啟用Sites主控台的Classic UI。

1. 使用CRXDE Lite，尋找與您要重新啟用Classic UI之管理控制台對應的節點。 它們位於：

   `/libs/cq/core/content/nav`

   例如

   [ `http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav`](http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav)

1. 選擇與要為其重新啟用Classic UI的控制台對應的節點。 例如，我們將重新啟用Sites主控台的傳統UI。

   `/libs/cq/core/content/nav/sites`

1. 使用「覆蓋節點」選 **項建立覆蓋** ; 例如：

   * **路徑**: `/apps/cq/core/content/nav/sites`
   * **重疊位置**: `/apps/`
   * **匹配節點類型**: 活動（選擇複選框）

1. 將下列布爾屬性添加到覆蓋節點：

   `enableDesktopOnly = {Boolean}true`

1. 「傳 **統型UI** 」選項在管理控制台中會再次顯示為快顯選項。

   ![screen_shot_2018-03-23at111924](assets/screen_shot_2018-03-23at111924.png)

針對您想要重新啟用Classic UI版本存取權的每個主控台重複這些步驟。

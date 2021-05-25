---
title: 編輯者
seo-title: 編輯者
description: 了解如何切換回傳統UI編輯器。
seo-description: 了解如何切換回傳統UI編輯器。
uuid: 78ba4db0-affa-4081-bf29-a3306720c968
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 5fca5401-502d-483b-bfc1-ef53e2c041b7
exl-id: 04a9c595-9a73-4a8a-99ae-c2292882338f
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 4%

---

# 編輯者{#editor}

依預設，已停用從編輯器切換至傳統UI的功能。

![chlimage_1-9](assets/chlimage_1-9.png)

若要重新啟用&#x200B;**頁面資訊**&#x200B;功能表中的「在傳統UI中開啟」選項&#x200B;**，請遵循下列步驟。**

1. 使用CRXDE Lite，查找以下節點：

   `/libs/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

   例如

   `http://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui](http://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

1. 使用&#x200B;**覆蓋節點**&#x200B;選項建立覆蓋；例如：

   * **路徑**:  `/apps/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`
   * **重疊位置**: `/apps/`
   * **匹配節點類型**:活動（選取核取方塊）

1. 將下列多值文字屬性新增至覆蓋節點：

   `sling:hideProperties = ["granite:hidden"]`

1. 編輯頁面時， **頁面資訊**&#x200B;功能表中會再次提供&#x200B;**在傳統UI中開啟**&#x200B;選項。

   ![chlimage_1-10](assets/chlimage_1-10.png)

---
title: 編輯者
seo-title: 編輯者
description: 瞭解如何切換回Classic UI Editor。
seo-description: 瞭解如何切換回Classic UI Editor。
uuid: 78ba4db0-affa-4081-bf29-a3306720c968
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 5fca5401-502d-483b-bfc1-ef53e2c041b7
translation-type: tm+mt
source-git-commit: 9fa15a44cf83a50538cea3fb37bcccf405f66738
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 4%

---


# 編輯者{#editor}

依預設，從編輯器切換至傳統UI的功能已停用。

![chlimage_1-9](assets/chlimage_1-9.png)

要重新啟用&#x200B;**頁面資訊**&#x200B;功能表中Classic UI **中的**&#x200B;開啟選項，請遵循下列步驟。

1. 使用CRXDE Lite，查找以下節點：

   `/libs/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

   例如

   `http://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui](http://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

1. 使用&#x200B;**覆蓋節點**&#x200B;選項建立覆蓋；例如：

   * **路徑**:  `/apps/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`
   * **重疊位置**: `/apps/`
   * **匹配節點類型**:活動（選擇複選框）

1. 將下列多值文字屬性新增至覆蓋節點：

   `sling:hideProperties = ["granite:hidden"]`

1. 編輯頁面時，**在傳統UI中開啟**&#x200B;選項會再次出現在&#x200B;**頁面資訊**&#x200B;選單中。

   ![chlimage_1-10](assets/chlimage_1-10.png)


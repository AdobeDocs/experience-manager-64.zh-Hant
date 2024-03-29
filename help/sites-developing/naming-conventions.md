---
title: 命名慣例
seo-title: Naming Conventions
description: 儲存庫中的節點受Java內容儲存庫的命名慣例的約束
seo-description: Nodes in the repository are subject to naming conventions of the Java Content Repository
uuid: 0515c5c5-3e93-4710-983f-c08c146467fc
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 198098c0-432b-4a93-a94e-2552337435dd
exl-id: 741043c7-2ebb-455d-8163-a246b874a7b3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 8%

---

# 命名慣例{#naming-conventions}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

儲存庫中的節點受 [Java內容儲存庫](/help/sites-developing/the-basics.md#java-content-repository). 不過，AEM會對頁面節點名稱實施進一步的慣例。

## 頁面的命名慣例 {#naming-conventions-for-pages}

這些命名慣例會在不同層級實作：

* JcrUtil:AEM實作 [JCR實用程式](#jcr-utilities).
* PageManager:the [頁面管理員](#page-manager) 提供頁面層級操作的方法。
* 根據使用的UI:

   * [標準、觸控式UI](#standard-ui)
   * [傳統 UI](#classic-ui)

### JCR實用程式 {#jcr-utilities}

[JcrUtil](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/commons/jcr/JcrUtil.html) 是JCR公用程式的AEM實施。 要驗證名稱，特別需要的是它所控制的字元映射，以及以下驗證：

* `isValidName`

   * 檢查名稱是否非空白，且僅包含有效字元。
   * 可用來檢查建議的名稱是否有效。

* `createValidName`

   * 這會以任意字串建立有效標籤。
   * 它可用來從標題建立名稱。

### 頁面管理員 {#page-manager}

[PageManager](https://helpx.adobe.com/tw/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) 提供頁面層級操作的方法，根據 [JCRUtil](#jcr-utilities).

### 標準 UI {#standard-ui}

標準觸控式UI:

* 在下列情況下，根據PageManager施加的限制驗證名稱：

   * 提供頁面標題以轉換為節點名稱
   * 提供了顯式節點名

### 傳統 UI {#classic-ui}

傳統UI實施更嚴格的限制：

* 在以下情況下驗證顯式節點名稱時的名稱：

   * 提供頁面標題以轉換為節點名稱
   * 提供了顯式節點名

* 有效的字元(即使從傳統UI內建立頁面，也只有這些字元有效 `PageManagerImpl` 會允許額外字元):

   * &#39;a&#39;到&#39;z&#39;
   * &#39;A&#39;到&#39;Z&#39;
   * &#39;0&#39;到&#39;9&#39;
   * _（下划線）
   * `-` （破折號/減號）

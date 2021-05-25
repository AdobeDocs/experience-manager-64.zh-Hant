---
title: 使用SRP存取UGC
seo-title: 使用SRP存取UGC
description: 將網站設定為使用ASRP或MSRP時，實際UGC不會儲存在AEM節點存放區(JCR)中
seo-description: 將網站設定為使用ASRP或MSRP時，實際UGC不會儲存在AEM節點存放區(JCR)中
uuid: 5f9f8c9b-4c6a-45b0-96ff-14934380eba7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ee786a5c-b985-4d78-9063-6c79ae5e13e6
exl-id: 3a16a771-e1c5-4ae4-9fc6-17a47064db54
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# 使用SRP {#accessing-ugc-with-srp}存取UGC

## 關於SRP {#about-srp}

所有AEM Communities元件和功能都建置在[social元件架構(SCF)](scf.md)上，此架構會叫用SocialResourceProvider API來存取所有使用者產生的內容(UGC)。

在建立社區站點之前，必須配置[儲存資源提供程式(SRP)](working-with-srp.md)以選擇與基礎[拓撲](topologies.md)一致的實施。 SRP實施以三種儲存選項為基礎：

1. [ASRP](asrp.md)  -Adobe按需儲存
2. [MSRP](msrp.md)  - MongoDB
3. [JSRP](jsrp.md)  - JCR

## 關於UGC儲存{#about-ugc-storage}

有關UGC儲存的重要知識是，當站點配置為使用ASRP或MSRP時，實際UGC不會儲存在AEM [node store](../../help/sites-deploying/data-store-config.md)(JCR)中。

雖然JCR中可能有節點陰影UGC以提供有用的中繼資料，但這些節點不會與實際UGC混淆。

請參閱[儲存資源提供程式概述。](srp.md)

## 最佳做法{#best-practice}

在開發自定義元件時，開發人員應注意獨立於當前選擇的拓撲進行編碼，從而保留將來遷移到新拓撲的靈活性。

### 假設JCR不可用{#assume-jcr-not-available}

應避免JCR專屬方法。

使用方法：

* Sling API（Sling資源）
   * 不要假設有JCR節點

* OSGi事件
   * 請勿假設有JCR事件

* [社交資源公用程式](socialutils.md#socialresourceutilities-package)
* [SCF實用程式](socialutils.md#scfutilities-package)

避免的方法：

* 節點API
* JCR事件
* 工作流程啟動器（使用JCR事件）

### 使用搜索集合{#use-search-collections}

不同的SRP可以有不同的原生查詢語言。 建議使用[com.adobe.cq.social.ugc.api](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html)套件中的方法來叫用適當的查詢語言。

如需詳細資訊，請參閱[搜尋要點](search-implementation.md)。

## 資源 {#resources}

* [社群內容儲存](working-with-srp.md)  — 討論UGC通用商店可用的SRP選項
* [儲存資源提供程式概述](srp.md)  — 簡介和儲存庫使用概述
* [SRP和UGC Essentials](srp-and-ugc.md)  - SRP公用程式方法與範例
* [Search Essentials](search-implementation.md)  — 搜尋UGC的基本資訊
* [SocialUtils重構](socialutils.md)  — 將棄用的公用程式方法對應至目前的SRP公用程式方法

---
title: 使用SRP存取UGC
seo-title: 使用SRP存取UGC
description: 當網站設定為使用ASRP或MSRP時，實際UGC不會儲存在AEM的節點儲存區(JCR)中
seo-description: 當網站設定為使用ASRP或MSRP時，實際UGC不會儲存在AEM的節點儲存區(JCR)中
uuid: 5f9f8c9b-4c6a-45b0-96ff-14934380eba7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ee786a5c-b985-4d78-9063-6c79ae5e13e6
translation-type: tm+mt
source-git-commit: 565604feff7fa365a1c6b52b62a0b0eb681bb192
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---


# 使用SRP存取UGC {#accessing-ugc-with-srp}

## 關於SRP {#about-srp}

所有AEM Communities元件和功能都建立在 [social元件架構(SCF)上](scf.md)，此架構會叫用SocialResourceProvider API以存取所有使用者產生的內容(UGC)。

在建立社區站點之前，必 [須配置儲存資源提供器(SRP)](working-with-srp.md) ，以選擇與底層拓撲一致的 [實施](topologies.md)。 SRP實施基於三種儲存選項：

1. [ASRP](asrp.md) - Adobe隨選儲存空間
2. [MSRP](msrp.md) - MongoDB
3. [JSRP](jsrp.md) - JCR

## 關於UGC儲存 {#about-ugc-storage}

有關UGC儲存的重要資訊是，當網站設定為使用ASRP或MSRP時，實際UGC不會儲存在AEM的 [節點儲存](../../help/sites-deploying/data-store-config.md) (JCR)。

雖然JCR中可能有節點將UGC陰影化，以提供有用的中繼資料，但這些節點不會與實際的UGC混淆。

請參 [閱儲存資源提供方概述。](srp.md)

## 最佳實務 {#best-practice}

在開發自定義元件時，開發人員應當注意獨立於當前所選拓撲編碼，從而保留將來遷移到新拓撲的靈活性。

### 假設JCR不可用 {#assume-jcr-not-available}

應避免JCR的特定方法。

使用方法：

* Sling API(Sling Resource)
   * 不要假設有JCR節點

* OSGi活動
   * 不要假設有JCR事件

* [社交資源公用程式](socialutils.md#socialresourceutilities-package)
* [SCF實用程式](socialutils.md#scfutilities-package)

避免的方法：

* 節點API
* JCR事件
* 工作流程啟動器（使用JCR事件）

### 使用搜尋系列 {#use-search-collections}

不同的SRP可以有不同的原生查詢語言。 建議您使用com.adobe.cq.so [](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) cial.ugc.api套件中的方法來叫用適當的查詢語言。

如需詳細資訊，請參 [閱Search Essentials](search-implementation.md)。

## 資源 {#resources}

* [社群內容儲存](working-with-srp.md) -討論UGC公用商店的可用SRP選擇
* [儲存資源提供方概述](srp.md) -簡介和儲存庫使用概述
* [SRP和UGC Essentials](srp-and-ugc.md) - SRP實用程式方法和示例
* [Search Essentials](search-implementation.md) —— 搜尋UGC的基本資訊
* [SocialUtils重構](socialutils.md) -將不建議使用的公用程式方法對應至目前的SRP公用程式方法

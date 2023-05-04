---
title: 使用SRP存取UGC
seo-title: Accessing UGC with SRP
description: 將網站設定為使用ASRP或MSRP時，實際UGC不會儲存在AEM節點存放區(JCR)中
seo-description: When a site is configured to use ASRP or MSRP, the actual UGC is not be stored in AEM's node store (JCR)
uuid: 5f9f8c9b-4c6a-45b0-96ff-14934380eba7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ee786a5c-b985-4d78-9063-6c79ae5e13e6
exl-id: 3a16a771-e1c5-4ae4-9fc6-17a47064db54
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 1%

---

# 使用SRP存取UGC {#accessing-ugc-with-srp}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 關於SRP {#about-srp}

所有AEM Communities元件和功能都建置在 [社會構成框架](scf.md)，會叫用SocialResourceProvider API來存取所有使用者產生的內容(UGC)。

在建立社群網站之前， [儲存資源提供程式(SRP)](working-with-srp.md) 必須設定為選取與基礎一致的實作 [拓撲](topologies.md). SRP實施以三種儲存選項為基礎：

1. [ASRP](asrp.md) -Adobe按需儲存
2. [MSRP](msrp.md) - MongoDB
3. [JSRP](jsrp.md) - JCR

## 關於UGC儲存 {#about-ugc-storage}

有關UGC儲存的重要資訊是，當網站設定為使用ASRP或MSRP時，實際UGC不會儲存在AEM中 [節點存放區](../../help/sites-deploying/data-store-config.md) (JCR)。

雖然JCR中可能有節點陰影UGC以提供有用的中繼資料，但這些節點不會與實際UGC混淆。

請參閱 [儲存資源提供程式概述。](srp.md)

## 最佳實務 {#best-practice}

在開發自定義元件時，開發人員應注意獨立於當前選擇的拓撲進行編碼，從而保留將來遷移到新拓撲的靈活性。

### 假設JCR不可用 {#assume-jcr-not-available}

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

### 使用搜尋集合 {#use-search-collections}

不同的SRP可以有不同的原生查詢語言。 建議您使用 [com.adobe.cq.social.ugc.api](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) 調用相應查詢語言的包。

如需詳細資訊，請參閱 [搜尋要點](search-implementation.md).

## 資源 {#resources}

* [社群內容儲存](working-with-srp.md)  — 討論UGC通用商店的可用SRP選擇
* [儲存資源提供程式概述](srp.md)  — 簡介和存放庫使用概觀
* [SRP和UGC要點](srp-and-ugc.md) - SRP實用程式方法和示例
* [搜尋要點](search-implementation.md)  — 搜索UGC的基本資訊
* [SocialUtils重構](socialutils.md)  — 將已棄用的實用程式方法映射到當前SRP實用程式方法

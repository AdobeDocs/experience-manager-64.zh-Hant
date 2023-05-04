---
title: 程式碼陷阱
seo-title: Code pitfalls
description: 為AEM開發時應避免的常見編碼陷阱
seo-description: Common coding pitfalls to avoid when developing for AEM
uuid: e7413bdc-4889-45ff-bdcb-b0893d33a3b7
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 01362026-a696-4a5d-94e9-ea784eaa6e4b
exl-id: f39910cf-1875-43fc-bfb5-259b9d8f135d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 4%

---

# 程式碼陷阱{#code-pitfalls}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 避免Java程式碼中的Sling系結 {#avoid-sling-bindings-in-java-code}

在90%的情況下，Sling系結是存取服務的不適當方式。 反之，您應使用 *@Reference* 或 *@Inject* 註解。

## 避免Java代碼中的Thread.interrupt {#avoid-thread-interrupt-in-java-code}

*線程。中斷* 是危險的，因為當在錯誤的時間呼叫時，它可能會關閉檔案，包括Lucene檔案和永久快取檔案。

## 避免將Java同步與ReadWriteLocks混合 {#avoid-mixing-java-synchronization-with-readwritelocks}

這可能會導致競爭條件，其中程式碼最終會死鎖。

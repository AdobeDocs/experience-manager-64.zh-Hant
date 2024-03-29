---
title: Dynamic Media 限制
description: 了解建立影像集、回轉集或上傳PDF時的最佳作法和強制限制。 另請了解Dynamic Media不支援的網頁瀏覽器和作業系統組合。
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/Dynamic-Media-Classic
geptopics: SG_SCENESEVENONDEMAND_PK/categories/ecatalogs
feature: Dynamic Media Classic,Asset Management,Image Sets,Spin Sets,eCatalog
role: User
exl-id: 0269ff24-582b-40f8-95e3-3ff4ac3a792f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 4%

---

# Dynamic Media限制

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

以下各節說明Dynamic Media的限制。

本主題包含下列章節：

* [Dynamic Media對資產類型的最佳實務和強制限制](#best-practice-enforced-limits)
* [Dynamic Media不支援的Web瀏覽器和作業系統組合](#unsupported-browser-os)

## Dynamic Media對資產類型的最佳實務和強制限制 {#best-practice-enforced-limits}

當您建立回轉集或影像集，或上傳頁面擷取PDF時，Adobe會建議下列最佳實務並強制執行下列限制：

| 資產 — 限制類型 | 最佳實務 | 限制 |
| --- | --- | --- |
| **影像**  — 每個影像的智慧作業數 | 5 | 100 |
| **所有集**  — 每組重複資產數 | 無重複項目 | 20 |
| **所有集**  — 每組資產的最大數量 | 每組5-10頁影像 | 1000 |
| **回轉集**  — 每2D集的最大行數/列數 | 每組12-18頁圖片 | 1000 |
| **PDF**  — 要考慮提取的PDF頁數上限 |  | 100(適用於所有PDF) |

<!-- See also [Dynamic Media limitations](/help/assets/limitations.md). -->

## Dynamic Media不支援的Web瀏覽器和作業系統組合 {#unsupported-browser-os}

Dynamic Media不支援下列網頁瀏覽器和作業系統組合：

* Internet Explorer 11 + Windows 7
* Internet Explorer 11 + Windows 8.1
* Internet Explorer 11 + Windows Phone 8.1
* Internet Explorer 11 + Windows Phone 8.1更新
* Safari 6 + iOS 6.0.1
* Safari 7 + iOS 7.1
* Safari 7 + OS X 10.9小牛隊
* Safari 8 + iOS 8.4
* Safari 8 + OS X 10.10 Yosemite

<!-- ## End of support for TLS 1.0 and 1.1 {#tls}

CQDOC-19433 (original ticket)
and CQDOC-19792 (removed as per this ticket December 5, 2022)

Effective September 30, 2022, Adobe Dynamic Media will end support for the following:

* TLS (Transport Layer Security) 1.0 and 1.1
* The following weak ciphers in TLS 1.2:
  * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384`
  * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA`
  * `TLS_RSA_WITH_AES_256_GCM_SHA384`
  * `TLS_RSA_WITH_AES_256_CBC_SHA256`
  * `TLS_RSA_WITH_AES_256_CBC_SHA`
  * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256`
  * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA`
  * `TLS_RSA_WITH_AES_128_GCM_SHA256`
  * `TLS_RSA_WITH_AES_128_CBC_SHA256`
  * `TLS_RSA_WITH_AES_128_CBC_SHA`
  * `TLS_RSA_WITH_CAMELLIA_256_CBC_SHA`
  * `TLS_RSA_WITH_CAMELLIA_128_CBC_SHA`
  * `TLS_ECDHE_RSA_WITH_3DES_EDE_CBC_SHA`
  * `TLS_RSA_WITH_SDES_EDE_CBC_SHA` -->

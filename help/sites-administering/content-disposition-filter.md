---
title: 內容處置篩選器
seo-title: 內容處置篩選器
description: 了解如何使用「內容處置篩選器」來防止XSS攻擊。
seo-description: 了解如何使用「內容處置篩選器」來防止XSS攻擊。
uuid: 145a88e0-9fa8-42db-b189-eda507c33049
contentOwner: trushton
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: Security
discoiquuid: badfaa18-472e-4777-a7dc-9c28441b38b7
exl-id: bb022f6b-938b-4421-8860-4c22aecf5b85
source-git-commit: 8cc85728be93d58e3aaee69c96f59ee98d5484a1
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# 內容處置篩選器{#content-disposition-filter}

內容處置篩選器是抵御SVG檔案的XSS攻擊的安全功能。

安裝後，篩選器會封鎖所有資產的存取權。 例如，您無法聯機查看PDF。 本節說明如何根據您的需求設定篩選器。

## 配置內容處置篩選器{#configure-content-disposition-filter}

您可以在GitHub中檢視[Apache Sling Content Disposition篩選器。](https://github.com/apache/sling-org-apache-sling-security/blob/master/src/main/java/org/apache/sling/security/impl/ContentDispositionFilterConfiguration.java)

「內容處置篩選器」選項提供下列功能：

* **內容處置路徑：** 將應用篩選器的路徑清單，其後面接著要在該路徑上排除的mime類型清單。此路徑必須是絕對路徑，並且尾端可能包含通配符(`*`)，以便與每個資源路徑與指定路徑前置詞匹配。例如：`/content/*:image/jpeg,image/svg+xml`會將篩選器套用至`/content`中除jpg和svg影像之外的每個節點

* **排除的資源路徑：** 排除的資源的清單，每個資源路徑都必須以絕對和完全限定的路徑指定。不支援前置詞匹配/通配符。

* **為所有資源路徑啟用：** 此標誌控制是否為所有路徑啟用此篩選器，排除資源路徑定義的排除路徑除外。若將此設為「true」，會導致忽略「內容處置路徑」。 僅覆蓋包含名為`jcr:data`或
   `jcr:content jcr:data`。

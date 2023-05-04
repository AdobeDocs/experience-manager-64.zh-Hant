---
title: 內容處置篩選器
seo-title: Content Disposition Filter
description: 了解如何使用「內容處置篩選器」來防止XSS攻擊。
seo-description: Learn how to use the Content Disposition Filter to prevent XSS attacks.
uuid: 145a88e0-9fa8-42db-b189-eda507c33049
contentOwner: trushton
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: Security
discoiquuid: badfaa18-472e-4777-a7dc-9c28441b38b7
exl-id: bb022f6b-938b-4421-8860-4c22aecf5b85
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 1%

---

# 內容處置篩選器 {#content-disposition-filter}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

內容處置篩選器是抵御SVG檔案XSS攻擊的安全功能。

安裝後，篩選器會封鎖所有資產的存取權。 例如，您無法聯機查看PDF。 本節說明如何根據您的需求設定篩選器。

## 設定內容處置篩選器 {#configure-content-disposition-filter}

您可以檢視 [GitHub中的Apache Sling內容處置篩選器。](https://github.com/apache/sling-org-apache-sling-security/blob/master/src/main/java/org/apache/sling/security/impl/ContentDispositionFilterConfiguration.java)

「內容處置篩選器」選項提供下列功能：

* **內容處置路徑：** 將應用篩選器的路徑清單，後跟要在該路徑上排除的mime類型清單。此路徑必須是絕對路徑，並且可能包含通配符(`*`)，以便將每個資源路徑與指定的路徑前置詞相符。 例如： `/content/*:image/jpeg,image/svg+xml` 會將篩選器套用至 `/content` jpg和svg影像除外

* **排除的資源路徑：** 排除的資源清單，每個資源路徑必須作為絕對和完全限定的路徑指定。 不支援前置詞匹配/通配符。

* **為所有資源路徑啟用：** 此標幟會控制是否對所有路徑啟用此篩選，排除資源路徑所定義的排除路徑除外。 若將此設為「true」，會導致忽略「內容處置路徑」。 僅覆蓋包含以下屬性的資源路徑（與配置無關） `jcr:data` 或
   `jcr:content jcr:data`。

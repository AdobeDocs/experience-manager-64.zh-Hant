---
title: 進階計分和徽章
seo-title: 進階計分和徽章
description: 設定進階計分
seo-description: 設定進階計分
uuid: 3854b668-729a-42b8-b7cd-5d5ec1ca8380
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 42fb3c50-8728-4897-ade9-6b839294a10e
translation-type: tm+mt
source-git-commit: ddf92a270835259998aa28f5960abcf55f56d1fc
workflow-type: tm+mt
source-wordcount: '1141'
ht-degree: 1%

---


# 進階計分和徽章 {#advanced-scoring-and-badges}

## 概覽 {#overview}

進階評分可授予徽章，以識別會員為專家。 進階計分會根據成員建立的 *內容數量* 和品質來指派點數，而基本計分則只會根據建立的內容數量來指派點數。

此差異是由於用來計算分數的計分引擎所致。 基本計分引擎採用簡單數學。 進階計分引擎是一種自適應算法，可獎勵通過主題的自然語言處理(NLP)推導而貢獻有價值和相關內容的主動成員。

除了內容相關性外，計分演算法也會考量成員活動，例如投票和答案百分比。 雖然基本計分包括了定量計分，但進階計分則採用演算法。

因此，高級計分引擎需要足夠的資料，使分析具有意義。 隨著演算法不斷調整所建立內容的量與品質，成為專家的成就臨界值會不斷重新評估。 還有一個概念 *是* ，成員的舊職位會衰落。 如果專家成員停止參與獲得專家地位的主題，在某個預先確定的點(請參閱計分引擎配置 [](#configurable-scoring-engine))，他們可能失去專家的地位。

設定進階計分與基本計分幾乎相同：

* 基本和進階計分與標籤規則 [會以相同方式套用](implementing-scoring.md#apply-rules-to-content) 至內容
   * 基本和進階計分與標籤規則可套用至相同內容
* [為元件啟用標章](implementing-scoring.md#enable-badges-for-component) ，是通用的

在設定計分和標籤規則方面的差異為：

* 可設定的進階計分引擎
* 進階計分規則：
   * `scoringType` 設為進 **[!UICONTROL 階]**
   * 需要秒數

* 進階標籤規則：
   * `badgingType` 設為進 **[!UICONTROL 階]**
   * `badgingLevels` 設為要授予的專家級數
   * 需要 `badgingPaths` 標籤陣列，而不是閾值陣列映射點到標籤

>[!NOTE]
>
>若要使用進階的計分和標籤功能，請安裝「專 [家識別」套件](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/cq-social-expert-identification-pkg)。

## 可配置計分引擎 {#configurable-scoring-engine}

進階計分引擎提供OSGi組態，其參數會影響進階計分演算法。

![chlimage_1-260](assets/chlimage_1-260.png)

* **[!UICONTROL 計分權]**&#x200B;重：對於主題，指定計算分數時應給予最高優先順序的動詞。 可以輸入一個或多個主題，但每個主題限 **定一個動詞**。 請參 [閱主題和動詞](implementing-scoring.md#topics-and-verbs)。

   以逗號逸 `topic,verb` 出方式輸入。 例如：

   `/social/forum/hbs/social/forum\,ADD`

   對於QnA和論壇元件，預設設定為ADD動詞。


* **[!UICONTROL 計分範圍]**

   進階分數的範圍由此值（最大可能分數）和0（最低可能分數）定義。

   預設值為100，因此計分範圍為0-100。


* **[!UICONTROL 實體衰減時間間隔]**

   此參數代表所有實體分數在其後延遲的小時數。 您必須在社群網站的分數中不再包含舊內容。

   預設值為216000小時（~24年）。


* **[!UICONTROL 得分增長率]**

   這會指定分數。 在0到得分區間之間，超過這一區間，增長將放緩，從而限制專家數量。

   預設值為 50。

## 進階計分規則 {#advanced-scoring-rules}

在基本評分中，獲得徽章所需的數量是已知的。

在進階計分中，需要的量是根據系統內的質量資料量不斷調整。 計分會以類似鐘形曲線的方式持續計算。

如果會員在已不活躍的主題上獲得專家徽章，他們可能會因時間流逝而失去徽章。

### 計分類型 {#scoringtype}

計分規則是一組計分子規則，每個子規則都聲明 `scoringType`。

若要叫用進階計分引擎， `scoringType`應將設為 `advanced`。

請參 [閱計分子規則](implementing-scoring.md#scoring-sub-rules)。

![chlimage_1-261](assets/chlimage_1-261.png)

### 秒詞 {#stopwords}

進階計分套件會安裝組態資料夾，其中包含秒數檔案：

* `/etc/community/scoring/configuration/stopwords`

進階計分演算法使用秒字檔案中包含的字詞清單，以識別在內容處理期間忽略的常見英文字詞。

您不希望修改此檔案。

如果秒數檔案遺失，進階計分引擎將會擲回錯誤。

## 進階標籤規則 {#advanced-badging-rules}

進階標籤規則屬性與基本標籤 [規則屬性不同](implementing-scoring.md#badging-rules)。

與其將點與徽章影像建立關聯，您只需識別允許的專家人數和要授予的徽章影像。

![chlimage_1-262](assets/chlimage_1-262.png)

| **屬性** | **類型** | **值說明** |
|---------------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| badgingPath | String[] | （必要）徽章影像的多值字串，最多可達badgingLevels的數目。 標章影像路徑必須依順序排列，因此第一個路徑會授與最高專家。 如果標籤數少於badgingLevels所指示的標籤數，則陣列中的最後一個標籤將填充陣列的其餘部分。 範例項目：/etc/community/badging/images/expert-badge/jcr:content/expert.png |
| badgingLevels | 長整數 | （可選）指定要授予的專業水準。 例如，如果應該有專家和幾乎的專家（兩個徽章），則值應設為2。 badgingLevel應與badgingPath屬性所列的專家相關標章影像數目相對應。 預設值為1。 |
| badgingType | 字串 | （必要）將計分引擎識別為「基本」或「進階」。 設為「進階」，則預設為「基本」。 |
| 計分規則 | String[] | （可選）多值字串，用於將標籤規則限制為由列出的計分規則識別的計分事件。範例輸入：/etc/community/scoring/rules/adv-comments-scoring預設值不受限制。 |

## 包含的規則和徽章 {#included-rules-and-badge}

### 隨附徽章 {#included-badge}

本測試版包含一個獎勵型專家徽章：

* 專家

   `/etc/community/badging/images/expert-badge/jcr:content/expert.png`

![chlimage_1-263](assets/chlimage_1-263.png)

為了讓專家徽章看起來像是對活動的獎勵，必須有兩件事：

* `badges` 必須為功能啟用，例如論壇或QnA元件
* 進階計分和標籤規則必須套用至元件所在的頁面（或上階）

請參閱以下基本資訊：

* [啟用元件徽章](implementing-scoring.md#enable-badges-for-component)
* [套用規則](implementing-scoring.md#apply-rules-to-content)

### 包含計分規則和子規則 {#included-scoring-rules-and-sub-rules}

測試版包含兩個論壇功能的進階計分 [規則](functions.md#forum-function) （每個用於論壇，而論壇功能的注釋元件則各一個）:

1. /etc/community/scoring/rules/adv-comments-scorting

   * `subRules[]` =

      /etc/community/scoring/rules/sub-rules/adv-comments-rule

      /etc/community/scoring/rules/sub-rules/adv-poting-rule-owner

      /etc/community/scoring/rules/sub-rules/adv-poting-rule

2. /etc/community/scoring/rules/adv-forums-scorning

   * `subRules[]` =

      /etc/community/scoring/rules/sub-rules/adv-forums-rule

      /etc/community/scoring/rules/sub-rules/adv-comments-rule

      /etc/community/scoring/rules/sub-rules/adv-poting-rule-owner

**附註:**

* 節 `rules`點和 `sub-rules` 節點都屬於 `cq:Page`
* `subRules` 是規則節點上類型[] 「字串」的屬 `jcr:content` 性
* `sub-rules` 可能與各種計分規則共用
* `rules` 應位於具有每個人的讀取權限的儲存庫位置
   * 規則名稱必須是唯一的，不論位置

### 包含的標籤規則 {#included-badging-rules}

此發行包含兩個與進階論壇和留言計分規則對 [應的進階標籤規則](#included-scoring-rules-and-sub-rules)。

* /etc/community/badging/rules/adv-comments-badging
* /etc/community/badging/rules/adv-forums-badging

**附註:**

* `rules` 節點的類型 `cq:Page`
* `rules`應位於具有每個人的讀取權限的儲存庫位置
   * 規則名稱必須是唯一的，不論位置

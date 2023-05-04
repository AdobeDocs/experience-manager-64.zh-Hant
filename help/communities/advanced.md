---
title: 進階計分和徽章
seo-title: Advanced Scoring and Badges
description: 設定進階計分
seo-description: Setting up advanced scoring
uuid: 3854b668-729a-42b8-b7cd-5d5ec1ca8380
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 42fb3c50-8728-4897-ade9-6b839294a10e
role: Admin
exl-id: c9406aae-288e-4cdf-ac01-cb26b423639e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1177'
ht-degree: 1%

---

# 進階計分和徽章 {#advanced-scoring-and-badges}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 概觀 {#overview}

高級評分允許授予徽章以將成員標識為專家。 進階計分會根據數量來指派點數 *和* 由成員建立的內容品質，而基本計分則僅根據建立的內容數量來分配點。

此差異是因為用於計算分數的分數引擎。 基本計分引擎採用簡單的數學。 進階計分引擎是一種自適應算法，用於獎勵通過主題的自然語言處理(NLP)推導而貢獻有價值和相關內容的活躍成員。

除了內容相關性外，評分演算法也會考量成員活動，例如投票和答案的百分比。 雖然基本評分會定量地納入，但進階評分會以演算法方式使用。

因此，進階計分引擎需要足夠的資料，使分析有意義。 隨著演算法持續根據所建立內容的數量和品質進行調整，系統會持續重新評估成為專家的成就臨界值。 還有 *衰變* 會員的舊職位。 如果專家成員停止參與他們獲得專家地位的主題事項，則在某個預先確定的點(見 [計分引擎配置](#configurable-scoring-engine))他們可能會失去專家的地位。

設定進階分數幾乎與基本分數相同：

* 基本和進階分數及徽章規則為 [套用至內容](implementing-scoring.md#apply-rules-to-content) 同樣
   * 基本和進階分數及徽章規則可套用至相同內容
* [為元件啟用徽章](implementing-scoring.md#enable-badges-for-component) 為一般

設定計分和徽章規則的差異為：

* 可配置的高級計分引擎
* 進階計分規則：
   * `scoringType` 設為 **[!UICONTROL 進階]**
   * 需要秒

* 進階簽章規則：
   * `badgingType` 設為 **[!UICONTROL 進階]**
   * `badgingLevels` 設定要授予的專家級數
   * 需要 `badgingPaths` 徽章陣列，而非臨界值陣列映射點到徽章

>[!NOTE]
>
>若要使用進階計分和徽章功能，請安裝 [專家識別套件](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq610%2Fsocial%2Ffeaturepack%2Fcq-social-expert-identification-pkg).

## 可配置計分引擎 {#configurable-scoring-engine}

進階計分引擎提供OSGi設定，其中包含影響進階計分演算法的參數。

![chlimage_1-260](assets/chlimage_1-260.png)

* **[!UICONTROL 計分權重]**
對於主題，指定計算分數時應給予最高優先順序的動詞。 可輸入一個或多個主題，但僅限於 **每個主題一個動詞**. 請參閱 [主題和動詞](implementing-scoring.md#topics-and-verbs).

   輸入為 `topic,verb` 逗號逸出。 例如：

   `/social/forum/hbs/social/forum\,ADD`

   預設設定為QnA和論壇元件的ADD謂詞。


* **[!UICONTROL 分數範圍]**

   進階分數的範圍由此值（最大可能分數）和0（最小可能分數）定義。

   預設值為100，因此分數範圍為0-100。


* **[!UICONTROL 實體耗散時間間隔]**

   此參數代表所有實體分數被延遲的小時數。 這必須不再將舊內容納入社群網站的分數中。

   預設值為216000小時（~24年）。


* **[!UICONTROL 得分增長率]**

   這會指定分數。 在0到分數範圍之間，超過0後，增長將放緩，從而限制專家人數。

   預設值為 50。

## 進階計分規則 {#advanced-scoring-rules}

在基本計分中，已知獲得徽章所需的數量。

在進階計分中，需要的數量會根據系統內的品質資料量不斷調整。 計分會以類似鐘形曲線的方式持續計算。

如果成員在已不活躍的主題上獲得了專家徽章，則他們可能會因時間流逝而失去徽章。

### ScoringType {#scoringtype}

計分規則是一組計分子規則，每個子規則都聲明 `scoringType`.

若要叫用進階計分引擎，請 `scoringType`應設為 `advanced`.

請參閱 [計分子規則](implementing-scoring.md#scoring-sub-rules).

![chlimage_1-261](assets/chlimage_1-261.png)

### 停字 {#stopwords}

高級計分包會安裝包含秒數檔案的配置資料夾：

* `/etc/community/scoring/configuration/stopwords`

進階計分演算法使用秒數檔案中包含的字詞清單，以識別內容處理期間會忽略的常見英文字詞。

不希望修改此檔案。

如果秒數檔案遺失，進階計分引擎會擲回錯誤。

## 進階徽章規則 {#advanced-badging-rules}

高級簽名規則屬性與 [基本簽名規則屬性](implementing-scoring.md#badging-rules).

與其將點與徽章影像關聯，只需識別允許的專家數量和要獎勵的徽章影像即可。

![chlimage_1-262](assets/chlimage_1-262.png)

| **屬性** | **類型** | **值說明** |
|---------------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| badgingPath | 字串[] | （必要）徽章影像的多值字串，長度為badgingLevels數。 必須排序徽章影像路徑，以便將第一個路徑授予最高專家。 如果徽章數少於badgingLevels所指示的，陣列中的最後一個徽章會填滿陣列的其餘部分。 範例項目：/etc/community/badging/images/expert-badge/jcr:content/expert.png |
| badgingLevels | 長整數 | （可選）指定要授予的專業水準。 例如，如果應該有專家和幾乎是專家（兩個徽章），則值應設為2。 badgingLevel應與為badgingPath屬性列出的專家相關徽章影像的數量相對應。 預設為1。 |
| badgingType | 字串 | （必要）將計分引擎識別為「基本」或「進階」。 若設為「進階」，則預設值為「basic」。 |
| scoringRules | 字串[] | （可選）一個多值字串，用於將標籤規則限制為由列出的評分規則標識的評分事件。示例項：/etc/community/scoring/rules/adv-comments-scoring預設值為無限制。 |

## 包含的規則和徽章 {#included-rules-and-badge}

### 包含的徽章 {#included-badge}

此測試版包含一個獎勵型專家徽章：

* 專家

   `/etc/community/badging/images/expert-badge/jcr:content/expert.png`

![chlimage_1-263](assets/chlimage_1-263.png)

為了讓專家徽章顯示為活動的獎勵，必須執行下列兩項作業：

* `badges` 必須為功能（如論壇或QnA元件）啟用
* 進階計分和標籤規則必須套用至放置元件的頁面（或上階）

請參閱以下項目的基本資訊：

* [啟用元件的徽章](implementing-scoring.md#enable-badges-for-component)
* [套用規則](implementing-scoring.md#apply-rules-to-content)

### 包含計分規則和子規則 {#included-scoring-rules-and-sub-rules}

測試版包含的兩個進階分數規則 [論壇功能](functions.md#forum-function) （論壇功能的論壇和評論元件各一個）:

1. /etc/community/scoring/rules/adv-comments計分

   * `subRules[]` =

      /etc/community/scoring/rules/subrules/adv-comments-rule

      /etc/community/scoring/rules/subrules/adv-voting-rule-owner

      /etc/community/scoring/rules/subrules/adv-voting-rule

2. /etc/community/scoring/rules/adv-forums計分

   * `subRules[]` =

      /etc/community/scoring/rules/subrules/adv-forums-rule

      /etc/community/scoring/rules/subrules/adv-comments-rule

      /etc/community/scoring/rules/subrules/adv-voting-rule-owner

**附註:**

* 兩者 `rules`和 `sub-rules` 節點的類型 `cq:Page`
* `subRules` 是字串類型的屬性[] 規則 `jcr:content` 節點
* `sub-rules` 可在各種計分規則之間共用
* `rules` 應位於具有每個人讀取權限的儲存庫位置
   * 規則名稱必須是唯一的，無論位置為何

### 包含徽章規則 {#included-badging-rules}

此發行包含與 [進階論壇和留言計分規則](#included-scoring-rules-and-sub-rules).

* /etc/community/badging/rules/adv-comments-badding
* /etc/community/badging/rules/adv-forums-badding

**附註:**

* `rules` 節點的類型 `cq:Page`
* `rules`應位於具有每個人讀取權限的儲存庫位置
   * 規則名稱必須是唯一的，無論位置為何

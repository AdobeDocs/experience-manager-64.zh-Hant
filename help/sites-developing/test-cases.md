---
title: 定義測試案例
seo-title: 定義測試案例
description: 您的測試案例應以使用案例和詳細的需求規格為基礎
seo-description: 您的測試案例應以使用案例和詳細的需求規格為基礎
uuid: 82dff825-da58-49a2-bf35-f5bb905e523d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 87a1f27a-765e-4882-9c06-5909e1610e1d
translation-type: tm+mt
source-git-commit: 0edddfde1e66ec487139f98e9ffafee885e61dfd
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---


# 定義測試案例{#defining-your-test-cases}

您的測試案例應以下列項目為基礎：

**使用案例**

* 這些功能定義了行為者（啟動某些動作的角色）與系統之間交互的必要功能。
* 使用案例應由客戶定義。

**詳細需求規格**

* 應測試所有功能和效能要求。

測試應明確定義：

* 先決條件； 這些可能涵蓋特定系統、組態或測試者的使用經驗。
* 應採取的步驟； 以適當的細節。
* 預期結果。
* 清除通過或失敗的標準。

自動化測試案例的前景顯然十分誘人，因為它可以消除重複性任務。

## 手動與自動測試 {#manual-versus-automated-tests}

不過，自動化測試案例是一項重大投資，因此應考慮到某些方面：

* 需要時間、精力和經驗來設定和設定。
* 如果以瀏覽器為基礎，則安裝瀏覽器更新時，問題的風險會增加； 需要更多時間進行修正。
* 只有大項目才真正可行。
* 當產生多個版本以用於測試或在長期版本計畫中時，就很好。

## 測試特定方面 {#testing-specific-aspects}

在測試AEM時，會特別關注一些特定細節：

作者和發佈環境

不過，在「環 [境](/help/sites-developing/the-basics.md#environments) 」中，有必要強調AEM在測試方面的決定性因素。

您必須將AEM視為兩個應用程式：

* the **Author** environment（作者環境）此實例允許作者輸入和發佈內容。
這有一小群(er)可預測的使用者，其特定功能和效能對使用者至關重要。
* publish **** environment（發佈環境）此例項以發佈的形式呈現網站，供訪客存取。
這通常會有較大的使用者集，其流量並不總是可以100%預測。 在回應要求時，效能仍然至關重要。 還必須考慮快取和負載平衡。

雖然軟體與之相同，但它們：

* 用於不同的用途
* 在功能和效能方面有不同的要求
* 以不同的方式設定
* 分別調諧
* 每個人都有自己的一套驗收測試

換言之，它們必須個別測試，並使用不同的測試案例。

**個性化**

在測試個人化時，應使用多個使用者帳戶重複每個個別使用案例，以證明行為。

此外，還必須檢查快取是否正確行為。

**The Dispatcher**

大多數項目將安裝Dispatcher以進行快取和負載平衡。

測試十分困難（快取會在不同層級和不同位置進行），而且必須使用黑匣子進行。 測試的主要方面包括：

* **準確性**; 確保網站訪客看到內容更新。
* **連續性**; 確保當一台伺服器關閉時網站仍然可用。
* **Clusters** Clusters用於提供：
   * **故障切換**&#x200B;如果一台伺服器出現故障，則群集中的其他伺服器將接管處理。
   * **Performance** Load balancing with full failover（效能負載平衡和完全故障切換）提高了群集的效能。

當用於客戶項目時，必須測試群集以確認配置的正確操作。

## 測試協力廠商軟體 {#testing-third-party-software}

所有與AEM介接的協力廠商軟體，都將在詳細需求規格中加以參考。

必須分析所需的任何測試（取決於定義的範圍），並獲得乾淨的測試。

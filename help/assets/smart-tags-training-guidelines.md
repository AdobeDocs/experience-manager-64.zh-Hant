---
title: 智慧型內容服務訓練方針
description: 訓練AI服務，將智慧標籤套用至資產
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: 1c011496-be6e-470b-9da8-48db8c6d1108
contentOwner: AG
discoiquuid: a5aab094-8b2d-4a23-890f-be6f9e5137bd
feature: 標籤，元資料，智慧標籤
role: 業務從業人員
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 11%

---


# 智慧型內容服務訓練指引{#smart-content-service-training-guidelines}

為了有效地標籤您的品牌影像，智慧型內容服務要求培訓影像符合特定准則。

## 訓練准則{#guidelines-for-training}

為獲得最佳效果，您的訓練集中的影像應符合下列准則：

**數量和大小：每** 個標 **簽至少30個影像**。長邊至少500像素。

**一致性**:標籤的影像應類似視覺效果。

例如，將所有這些影像標籤為&#x200B;*my-party*（針對訓練）並不好，因為它們在視覺上並不類似。

![示例性影像，以示訓練指南](assets/do-not-localize/coherence.png)

**涵蓋範圍**:培訓中的影像應該有足夠的多樣性。我們的想法是提供一些比較多樣化的例子，AEM讓學習將注意力放在正確的事上。 如果您要在視覺上不相同的影像上套用相同的標籤，請至少包含5種不同類型的範例。

例如，對於標籤&#x200B;*model-down-pose*，為服務加入更多類似下方反白顯示影像的訓練影像，以便在標籤期間更精確地識別類似影像。

![示例性影像，以示訓練指南](assets/do-not-localize/coverage_1.png)

**干擾／妨礙**:該服務更能訓練那些分散注意力的影像（突出的背景、不相關的伴奏，如主題的物體／人）。

例如，對於標籤&#x200B;*休閒鞋*，第二個影像不是好的訓練候選影像。

![示例性影像，以示訓練指南](assets/do-not-localize/distraction.png)

**** 完整性：如果影像符合多個標籤的資格，請先新增所有適用的標籤，再加入影像以進行訓練。例如，對於標籤(例如 *Raincoat***&#x200B;和模型側檢視)，請先在符合資格的資產上新增兩個標籤，然後再加入以進行訓練。

![示例性影像，以示訓練指南](assets/do-not-localize/completeness.png)

## 限制 {#limitations}

增強的智慧型標籤是以品牌影像及其標籤的學習模型為基礎。 這些模型在識別標籤時並不總是十分完美。 智慧型內容服務的目前版本有下列限制：

* 無法辨識影像的細微差異。 例如，修身與普通襯衫。
* 無法根據影像的微小圖樣／部分來識別標籤。 例如，T恤上的標誌。
* 在中支援的語言環境AEM中支援標籤。 如需語言清單，請參閱[智慧型內容服務發行說明](/help/release-notes/smart-content-service-release-notes.md)。

若要使用智慧標籤來搜尋資產（一般或增強功能），請使用資產全方位搜尋（全文搜尋）。 智慧型標籤沒有個別的搜尋述詞。

>[!NOTE]
>
>智慧型內容服務是否能夠訓練您的標籤並將它們套用至其他影像，取決於您用於訓練的影像品質。
>
>為獲得最佳效果，Adobe建議您使用視覺上類似的影像來訓練每個標籤的服務。


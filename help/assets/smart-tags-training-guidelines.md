---
title: 智慧型內容服務訓練方針
description: 訓練AI服務，將智慧標籤套用至資產
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: 1c011496-be6e-470b-9da8-48db8c6d1108
contentOwner: AG
discoiquuid: a5aab094-8b2d-4a23-890f-be6f9e5137bd
translation-type: tm+mt
source-git-commit: dc779a0d89dc4c044ca4f3e3f92c4a9b651d09a8
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 10%

---


# 智慧型內容服務訓練方針 {#smart-content-service-training-guidelines}

為了有效地標籤您的品牌影像，智慧型內容服務要求培訓影像符合特定准則。

## 培訓方針 {#guidelines-for-training}

為獲得最佳效果，您的訓練集中的影像應符合下列准則：

**數量和大小：** 每個 **標籤至少30個影像**。 長邊至少500像素。

**一致性**: 標籤的影像應類似視覺效果。

例如，將所有這些影像標籤為 *my-party* （用於培訓）並不是個好主意，因為它們在視覺上並不相似。

![示例性影像，以示訓練指南](assets/do-not-localize/coherence.png)

**涵蓋範圍**: 培訓中的影像應該有足夠的多樣性。 其想法是提供幾個相當多樣化的範例，讓AEM學會專注在正確的事物上。 如果您要在視覺上不相同的影像上套用相同的標籤，請至少包含5種不同類型的範例。

例如，對於標籤下模 *式姿勢*，請加入更多類似下方反白顯示影像的訓練影像，讓服務在標籤時更精確地識別類似影像。

![示例性影像，以示訓練指南](assets/do-not-localize/coverage_1.png)

**干擾／妨礙**: 該服務更能訓練那些分散注意力的影像（突出的背景、不相關的伴奏，如主題的物體／人）。

例如，對於標籤休閒 *鞋*，第二張影像不是好的訓練候選影像。

![示例性影像，以示訓練指南](assets/do-not-localize/distraction.png)

**** 完整性：如果影像符合多個標籤的資格，請先新增所有適用的標籤，再加入影像以進行訓練。例如，對於標籤(例如 *Raincoat***&#x200B;和模型側檢視)，請先在符合資格的資產上新增兩個標籤，然後再加入以進行訓練。

![示例性影像，以示訓練指南](assets/do-not-localize/completeness.png)

## 限制 {#limitations}

增強的智慧型標籤是以品牌影像及其標籤的學習模型為基礎。 這些模型在識別標籤時並不總是十分完美。 智慧型內容服務的目前版本有下列限制：

* 無法辨識影像的細微差異。 例如，修身與普通襯衫。
* 無法根據影像的微小圖樣／部分來識別標籤。 例如，T恤上的標誌。
* 在支援AEM的地區設定中支援標籤。 如需語言清單，請參閱智 [慧型內容服務版本注意事項](/help/release-notes/smart-content-service-release-notes.md)。

若要使用智慧標籤來搜尋資產（一般或增強功能），請使用資產全方位搜尋（全文搜尋）。 智慧型標籤沒有個別的搜尋述詞。

>[!NOTE]
>
>智慧型內容服務是否能夠訓練您的標籤並將它們套用至其他影像，取決於您用於訓練的影像品質。
>
>為獲得最佳效果，Adobe建議您使用視覺上類似的影像來訓練每個標籤的服務。


---
title: 智慧內容服務訓練准則
description: 訓練AI服務將智慧標籤套用至資產
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: 1c011496-be6e-470b-9da8-48db8c6d1108
contentOwner: AG
discoiquuid: a5aab094-8b2d-4a23-890f-be6f9e5137bd
feature: Tagging,Metadata,Smart Tags
role: User
exl-id: 14241f8d-fd0b-4bcf-b2bb-1d0e52bf7748
source-git-commit: a778c3bbd0e15bb7b6de2d673b4553a7bd146143
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 10%

---

# 智慧內容服務訓練准則 {#smart-content-service-training-guidelines}

為了能有效標籤您的品牌影像，智慧內容服務要求訓練影像符合特定准則。

## 培訓准則 {#guidelines-for-training}

為獲得最佳結果，培訓集中的影像應符合以下准則：

**數量和大小：** 每個標 **簽至少30個影像**。長邊至少500像素。

**一致性**:標籤的影像應在視覺上類似。

例如，將所有這些影像標籤為&#x200B;*my-party*（針對訓練）並非好主意，因為它們在視覺上並不類似。

![說明性影像，以說明訓練准則](assets/do-not-localize/coherence.png)

**涵蓋範圍**:訓練中的影像應該有足夠的多樣性。其理念是提供一些相當多樣的範例，讓[!DNL Experience Manager]學會專注於正確的事物。 如果您要在視覺上不同的影像上套用相同的標籤，請至少包含五種類型的範例。

例如，對於標籤&#x200B;*model-down-pose*，包括與下面突出顯示的影像類似的更多訓練影像，以便服務在標籤期間更準確地識別類似影像。

![說明性影像，以說明訓練准則](assets/do-not-localize/coverage_1.png)

**干擾/阻礙**:該服務對分散注意力較少的影像進行更好的訓練（顯著背景、不相關的伴奏，如主題對象/人）。

例如，對於標籤&#x200B;*休閒鞋*，第二個影像不是好的訓練候選影像。

![說明性影像，以說明訓練准則](assets/do-not-localize/distraction.png)

**** 完整性：如果影像符合多個標籤的資格，請先新增所有適用的標籤，再加入影像以進行訓練。例如，對於標籤(例如 *Raincoat***&#x200B;和模型側檢視)，請先在符合資格的資產上新增兩個標籤，然後再加入以進行訓練。

![說明性影像，以說明訓練准則](assets/do-not-localize/completeness.png)

## 限制 {#limitations}

增強的智慧標籤是以品牌影像及其標籤的學習模型為基礎。 這些模型在識別標籤時並非總是十分完美。 智慧內容服務的目前版本有下列限制：

* 無法識別影像中的細微差異。 例如，纖薄與普通襯衫。
* 無法根據影像的微小模式/部分識別標籤。 例如T恤上的標誌。
* 在支援[!DNL Experience Manager]的地區設定中支援標籤。 如需語言清單，請參閱[智慧內容服務發行說明](/help/release-notes/smart-content-service-release-notes.md)。

若要使用智慧標籤來搜尋資產（一般或增強），請使用「資產全域搜尋」（全文搜尋）。 智慧標籤沒有單獨的搜尋述詞。

>[!NOTE]
>
>智慧內容服務在您的標籤上進行訓練，並將它們套用至其他影像的能力，取決於您用於訓練的影像品質。
>
>為獲得最佳結果，Adobe建議您使用視覺上類似的影像來訓練每個標籤的服務。

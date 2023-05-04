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
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 11%

---

# 智慧內容服務訓練准則 {#smart-content-service-training-guidelines}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

為了能有效標籤您的品牌影像，智慧內容服務要求訓練影像符合特定准則。

## 培訓准則 {#guidelines-for-training}

為獲得最佳結果，培訓集中的影像應符合以下准則：

**數量和大小：** 最低 **每個標籤30個影像**. 長邊至少500像素。

**一致性**:標籤的影像應在視覺上類似。

例如，將這些影像標籤為 *my-party* （用於訓練），因為視覺上不類似。

![說明性影像，以說明訓練准則](assets/do-not-localize/coherence.png)

**涵蓋範圍**:訓練中的影像應該有足夠的多樣性。 我們的想法是提供一些比較多樣的例子，這樣 [!DNL Experience Manager] 學會專注於正確的事情。 如果您要在視覺上不同的影像上套用相同的標籤，請至少包含五種類型的範例。

例如，對於標籤 *下姿態*，請加入更多類似下方醒目提示影像的訓練影像，讓服務在標籤時更準確地識別類似影像。

![說明性影像，以說明訓練准則](assets/do-not-localize/coverage_1.png)

**干擾/障礙**:該服務對分散注意力較少的影像進行更好的訓練（顯著背景、不相關的伴奏，如主題對象/人）。

例如，對於標籤 *休閒鞋*)，第二張影像不是好的訓練候選者。

![說明性影像，以說明訓練准則](assets/do-not-localize/distraction.png)

**** 完整性：如果影像符合多個標籤的資格，請先新增所有適用的標籤，再加入影像以進行訓練。例如，對於標籤(例如 *Raincoat***&#x200B;和模型側檢視)，請先在符合資格的資產上新增兩個標籤，然後再加入以進行訓練。

![說明性影像，以說明訓練准則](assets/do-not-localize/completeness.png)

## 限制 {#limitations}

增強的智慧標籤是以品牌影像及其標籤的學習模型為基礎。 這些模型在識別標籤時並非總是十分完美。 智慧內容服務的目前版本有下列限制：

* 無法識別影像中的細微差異。 例如，纖薄與普通襯衫。
* 無法根據影像的微小模式/部分識別標籤。 例如T恤上的標誌。
* 在 [!DNL Experience Manager] 支援。 如需語言清單，請參閱 [智慧內容服務發行說明](/help/release-notes/smart-content-service-release-notes.md).

若要使用智慧標籤來搜尋資產（一般或增強），請使用「資產全域搜尋」（全文搜尋）。 智慧標籤沒有單獨的搜尋述詞。

>[!NOTE]
>
>智慧內容服務在您的標籤上進行訓練，並將它們套用至其他影像的能力，取決於您用於訓練的影像品質。
>
>為獲得最佳結果，Adobe建議您使用視覺上類似的影像來訓練每個標籤的服務。

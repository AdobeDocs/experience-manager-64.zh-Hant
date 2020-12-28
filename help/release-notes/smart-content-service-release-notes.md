---
title: 智慧型內容服務發行說明
seo-title: 智慧型內容服務發行說明
description: 智慧型內容服務概觀及服務相關的已知問題。
seo-description: 智慧型內容服務概觀及服務相關的已知問題。
uuid: 5f474b36-3451-48ea-8669-b2d793638b06
content-type: reference
products: SG_EXPERIENCEMANAGER
discoiquuid: 9f88c773-ddeb-4c66-ac07-7d3aa196c51b
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 4%

---


# 智慧型內容服務發行說明{#smart-content-service-release-notes}

智慧型內容服務概觀及服務相關的已知問題。

企業組織需要根據員工、合作夥伴和客戶用來參照和搜尋數位資產的分類法來標籤其數位資產。 與一般標籤相比，基於業務分類法標籤的資產更容易通過基於標籤的搜索來識別和檢索。

智慧型內容服務會使用您的AEM資產業務分類法，自動標籤數位資產，以確保最相關的資產出現在搜尋中。

您必須針對一組AEM資產和標籤來訓練Smart Content Service，以識別您的業務分類法。 經過培訓後，服務可將這些標籤套用在類似的資產集上。

智慧型內容服務採用Adobe Sensei平台，可讓您針對業務分類法訓練影像識別演算法。 然後，此內容智慧會用來對類似資產套用相關標籤。

## 主要改進{#key-improvements}

智慧型內容服務包含下列主要改進：

* 演算法最佳化以進一步提高模型精度、召回率值
* 支援重設租用戶層級所有標籤的模型訓練
* 支援增強的智慧標籤命名空間以避免衝突
* 新的模型更換政策，以避免再培訓造成任何退化
* 以租用戶為主的服務使用監控
* 修正叢集與連線相關的問題，以增強服務的穩健性

## 已修正的問題 {#fixed-issues}

此版本已修正下列問題：

* 如果無法連接到MySQL伺服器，則標籤和培訓工作流的工作進程將終止。 CQ-4242886

* 未正確計算有偏精度的分數。 CQ-4241797

* 模型的PR計算不正確。 CQ-4241381

* 從佇列CQ-4240901處理範例資產時，訓練工作流程會遺漏範例資產

* 精確召回的改進。 CQ-4239895

* 型號更換策略。 CQ-4239886

* 男式襯衫的圖片上標有女式夾克標籤。 CQ-4239650

* 在舞台部署時會遺漏訓練範例。 CQ-4239483

* 應對提交給培訓的一組資產進行培訓工作驗證。 CQ-4238834

* 即使標籤有最小的正／負值，負值篩選的模型建立也會失敗。 CQ-4240741

* 培訓人員記錄中負面覓食的誤導項目。 CQ-4240738

* 第一次培訓的問題：如果為培訓而提交的標籤是彼此隨機否定的。 CQ-4240118

* 即時製作記錄檔，以監控每位租用戶的服務使用情況。 CQ-4239781

## 語言 {#languages}

Smart Content Service適用於下列地區設定：

* 英文
* 德文
* 法文
* 西班牙文
* 義大利文
* 葡萄牙文
* 日文
* 簡體中文
* 韓文

## 連結 {#links}

* [adobe.com上的Adobe Experience Manager產品頁面](https://www.adobe.com/marketing-cloud/experience-manager.html)
* [增強的智慧型標籤檔案](/help/assets/enhanced-smart-tags.md)

## 產品存取與支援（受限制網站）{#product-access-and-support-restricted-sites}

這些網站僅提供給客戶使用。 如果您是客戶且需要存取權，請連絡您的Adobe客戶經理。

* [產品存取](https://login.marketing.adobe.com)
* [產品下載，請造訪licensing.adobe.com](https://licensing.adobe.com/)。
* 產品更新、修補程式和套件，以取得[軟體散發](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)的其他功能。
* [透過Admin Console的客戶支援](https://adminconsole.adobe.com/)。如需詳細資訊，請參閱[新的Adobe客戶支援體驗](https://docs.adobe.com/content/help/en/customer-one/using/home.html)。

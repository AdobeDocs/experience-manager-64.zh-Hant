---
title: 智慧內容服務發行說明
seo-title: 智慧內容服務發行說明
description: 智慧內容服務的概述及服務的已知問題。
seo-description: 智慧內容服務的概述及服務的已知問題。
uuid: 5f474b36-3451-48ea-8669-b2d793638b06
content-type: reference
products: SG_EXPERIENCEMANAGER
discoiquuid: 9f88c773-ddeb-4c66-ac07-7d3aa196c51b
exl-id: 6e7ac9d2-7181-48bb-82c4-61a90e594ff5
source-git-commit: a842c45f0a0597f4c7f143974a550874258e5382
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 5%

---

# 智慧內容服務發行說明{#smart-content-service-release-notes}

智慧內容服務的概述及服務的已知問題。

組織需要根據員工、合作夥伴和客戶用來參照和搜尋數位資產的分類法，來標籤其數位資產。 與一般標籤相比，以商業分類法標籤的資產更容易識別，也更容易透過標籤式搜尋擷取。

智慧內容服務會使用您的AEM Assets商業分類法，自動標籤數位資產，確保最相關的資產出現在搜尋中。

您必須針對已組織的AEM資產和標籤集訓練智慧內容服務，才能識別您的業務分類法。 一旦接受訓練，服務便可將這些標籤套用至類似的資產集。

智慧內容服務採用Adobe Sensei平台，可讓您根據業務分類訓練影像識別演算法。 然後，系統會使用此內容智慧，對類似資產套用相關標籤。

## 主要改進{#key-improvements}

智慧內容服務包含下列重要改善：

* 演算法最佳化以進一步改善模型精度、回叫值
* 支援重設租用戶層級所有標籤的模型訓練
* 支援增強智慧標籤命名空間，以避免衝突
* 新的模型替換策略，以避免因再培訓而導致任何降級
* 以租戶為基礎的服務使用監控
* 修正叢集和連線相關問題，可增強服務的健全性

## 已修正的問題 {#fixed-issues}

此版本已修正下列問題：

* 如果無法連接到MySQL伺服器，則用於標籤和培訓工作流的工作進程將終止。 CQ-4242886

* 未正確計算精度偏差分數。 CQ-4241797

* 模型的PR計算不正確。 CQ-4241381

* 從佇列CQ-4240901處理範例資產時，訓練工作流程會遺漏這些資產

* 改進精確召回。 CQ-4239895

* 型號替換策略。 CQ-4239886

* 男性襯衫的影像上標有女性夾克標籤。 CQ-4239650

* 預備部署時會遺漏訓練範例。 CQ-4239483

* 提交給培訓的一組資產應驗證培訓工作。 CQ-4238834

* 即使標籤有最小的正/負值，模型建立仍無法進行負值篩選。 CQ-4240741

* 培訓員記錄中負面覓食的誤導項目。 CQ-4240738

* 如果為訓練提交的標籤是彼此隨機的負值，則第一次訓練的問題。 CQ-4240118

* 即時製作記錄，以監控每個租用戶的服務使用情形。 CQ-4239781

## 語言 {#languages}

智慧內容服務適用於下列地區設定：

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

* [Adobe Experience Manager Product Page on adobe.com](https://www.adobe.com/marketing-cloud/experience-manager.html)
* [增強智慧標籤檔案](/help/assets/enhanced-smart-tags.md)

## 產品存取與支援（限制網站）{#product-access-and-support-restricted-sites}

這些網站僅供客戶使用。 如果您是Adobe，需要存取權，請聯絡您的客戶經理。

* [產品存取](https://login.experiencecloud.adobe.com/exc-content/login.html)
* [請前往licensing.adobe.com下載產品](https://licensing.adobe.com/)。
* [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)上其他功能的產品更新、修補程式和套件。
* [透過Admin Console提供客戶支援](https://adminconsole.adobe.com/)。如需詳細資訊，請參閱[新Adobe客戶支援體驗](https://docs.adobe.com/content/help/en/customer-one/using/home.html)。

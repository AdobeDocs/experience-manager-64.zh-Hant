---
title: 電子商務
seo-title: eCommerce
description: AEM eCommerce可協助行銷人員透過網路、行動裝置及社交接觸點，提供品牌化的個人化購物體驗。
seo-description: AEM eCommerce helps marketers deliver branded, personalized shopping experiences across web, mobile, and social touchpoints.
uuid: 14af7a3a-7211-4a56-aeef-1603128d5d8a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: 68799110-8183-40fe-be4f-2a7c7a7b3018
feature: Commerce Integration Framework
exl-id: 3c046e16-5f54-4a16-aa5b-256b679808fa
source-git-commit: bbc13d64a33d9033e04fb4f37d60bcfe223be337
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 1%

---

# 電子商務{#ecommerce}

* [概念](/help/sites-administering/concepts.md)
* [管理（一般）](/help/sites-administering/generic.md)
* [SAPCommerce Cloud](/help/sites-administering/sap-commerce-cloud.md)
* [SalesforceCommerce Cloud](https://github.com/adobe/commerce-salesforce)
* [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)

Adobe提供兩個版本的Commerce Integration Framework:

|  | CIF內部部署 | CIF雲 |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| 支援的 AEM 版本 | AEM內部部署或AMS 6.x | AEM AMS 6.4和6.5 |
| 後端 | - AEM,Java <br>  — 整體整合，預建映射（範本）<br> - JCR存放庫 | -Magento <br>- Java和Javascript <br> — 沒有儲存在JCR儲存庫中的商務資料 |
| 前端 | AEM伺服器端轉譯的頁面 | 混合頁面應用程式（混合演算） |
| 產品目錄 |  — 產品匯入工具、編輯器、AEM中的快取 <br> — 包含AEM或Proxy頁面的一般目錄 |  — 無產品匯入 <br> — 一般範本 <br> — 透過連接器提供隨選資料 |
| 可擴充性 |  — 最多可支援數百萬種產品（取決於使用案例） <br> - Dispatcher上的快取 |  — 無卷限制 <br> — 快取Dispatcher或CDN |
| 標準化資料模型 | 否 | 是，MagentoGraphQL架構 |
| 可用性 | 是：<br> - SAPCommerce Cloud(更新擴充功能以支援AEM 6.4和Hybris 5（預設），並維持與Hybris 4的相容性 <br>- SalesforceCommerce Cloud(Connector開源支援AEM 6.4) | 是，透過GitHub透過開放原始碼。 <br> Magento Commerce(支援Magento2.3.2（預設），並與Magento2.3.1相容)。 |
| 使用時機 | 有限的使用案例：對於可能需要匯入小型靜態目錄的情況 | 大多數使用案例中的首選解決方案 |

電子商務與產品資訊管理(PIM)一起處理網站的活動，重點是通過線上商店銷售產品：

* 產品的建立、存留期和淘汰
* 價格管理
* 交易管理
* 管理整個目錄
* 即時和集中儲存記錄
* Web介面

AEM eCommerce可協助行銷人員透過網路、行動裝置及社交接觸點，提供品牌化的個人化購物體驗。 AEM製作環境可讓您根據目標訪客內容和銷售策略來自訂頁面和元件；例如：

* 產品頁面
* 購物車元件
* 結帳元件

實施可讓您即時存取產品資訊。 這可用於強制：

* 產品資訊完整性
* 定價
* 庫存庫存
* 購物車狀態的變化

>[!NOTE]
>
>若要與外部電子商務提供者使用整合架構，您必須先安裝所需的套件。 如需詳細資訊，請參閱 [部署eCommerce](/help/sites-deploying/ecommerce.md).
>
>如需擴充電子商務功能的詳細資訊，請參閱 [開發電子商務](/help/sites-developing/ecommerce.md).

## 主要功能 {#main-features}

AEM eCommerce提供：

* 數 **現成可用的AEM元件** 以說明可為您的專案達成哪些目標：

   * 產品顯示
   * 購物車
   * 結帳
   * 最近查看的產品
   * 憑單
   * 其他

   ![chlimage_1-150](assets/chlimage_1-150.png)

   >[!NOTE]
   >
   >AEM提供的整合架構也可讓您針對商務功能建立其他AEM元件，而不受特定電子商務引擎影響。

* **搜尋**  — 使用下列其中一項：

   * AEM搜尋
   * 電子商務系統的搜索
   * 第三方搜尋
   * 或其組合。

   ![chlimage_1-151](assets/chlimage_1-151.png)

* 使用AEM功能 **在多個頻道上呈現內容**，可以是完整瀏覽器視窗或行動裝置。 這會以訪客所需的格式提供內容。

   ![chlimage_1-152](assets/chlimage_1-152.png)

* 能夠 **根據開發您自己的整合實作 [AEM eCommerce架構](#the-framework)**.

   目前可用的兩個實施都是以相同為基礎而建置，而非一般API（架構）。 實作新整合只涉及實作您的整合需求的功能。 任何新實作都可以使用前端元件，因為前端元件使用介面（因此與實作無關）。

* 發展 **基於購物者資料和活動的體驗導向商務**. 這可讓您了解許多情況：

   * 例如，當訂單總額超過特定金額時，可能會降低運費。
   * 另一個選件可讓您提供使用設定檔資料的季節性選件（例如位置）。 接著，視需要再視其他因素，再強調顯示這些項目。

   在以下範例中，一個宣傳預告顯示為購物車內容小於$75:

   ![chlimage_1-153](assets/chlimage_1-153.png)

   當購物車內容超過$75時，可以變更此項：

   ![chlimage_1-154](assets/chlimage_1-154.png)

* 以及其他功能，包括：

   * 跨工作階段保留的購物車內容
   * 完整訂單歷史記錄
   * 快速目錄更新

## 框架 {#the-framework}

此 [概念](/help/sites-administering/concepts.md) 一節更詳細地介紹了該框架，但下面提供了該框架的高級、高速視圖：

### 什麼？ {#what}

* 整合架構提供API、說明功能的一系列元件，以及提供連線方法範例的數個擴充功能。
* 該框架提供了項目實施所需的基本結構。
* 該框架是可擴展的。
* 框架不提供現成可用的網站。 要使框架適應您的規範，始終需要進行一定數量的開發工作。

### 為什麼？ {#why}

* 提供快速實現定制電子商務站點所需的基本機制。
* Tp提供開發真實電子商務站點所需的靈活性。
* 說明最佳實務。

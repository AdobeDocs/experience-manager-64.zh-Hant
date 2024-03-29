---
title: 與Adobe Marketing Cloud整合
description: 了解如何整合Adobe Experience Manager與Adobe Marketing Cloud。
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
exl-id: e2295f71-ea3a-483c-9d7b-29acd151845d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 2%

---

# 與Adobe Marketing Cloud整合{#integrating-with-the-adobe-marketing-cloud}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

此 [Adobe Marketing Cloud](https://www.adobe.com/solutions/digital-marketing.html)，包含功能強大的網站分析和網站最佳化產品，可提供可操作的即時資料和深入分析，以推動成功的線上計畫。 它為線上業務優化提供了整合而開放的平台。 雲包含整合式應用程式，可收集和釋放客戶洞察力，以優化客戶贏取、轉換和保留工作，以及內容的建立和分發。

透過Adobe Experience Manager，您可以與下列Adobe Marketing Cloud產品順暢整合：

* Adobe Analytics為行銷人員提供關於線上策略和行銷活動的可操作、即時資訊。
* Adobe Target可讓行銷人員持續讓其線上內容與客戶更相關，進而提供更高的轉換。
* Adobe Dynamic Media Classic可在托管環境中自動化媒體管理、簡化Web發佈並增強Web體驗。
* Adobe動態Tag Management為行銷人員提供直覺式工具，以快速輕鬆管理不限數量的Adobe和協力廠商標籤。
<!-- Search&Promote was end of life September 1, 2022. * Adobe Search&Promote gives marketers the ability to control and optimize the search results on their sites. -->
* Adobe Campaign可讓您直接在Adobe Experience Manager中管理電子郵件傳送內容。

此外，您可以將Adobe Experience Manager與 [Creative Cloud](/help/assets/aem-cc-integration-best-practices.md) 和 [協力廠商服務](/help/sites-administering/third-party-services.md).

## 整合 Adobe Analytics {#integrating-with-adobe-analytics}

[Adobe Analytics](https://www.omniture.com/en/products/analytics/sitecatalyst) 是領先業界的解決方案，可讓數位行銷人員在多個行銷管道中，透過單一位置測量、分析並最佳化所有線上活動的整合資料。 它為行銷人員提供關於數位策略和行銷計畫的可操作、即時的網頁分析智慧。 Adobe Analytics可協助行銷人員快速找出網站中最有利可圖的路徑、劃分流量以找出高價值網站訪客、判斷訪客在何處離開網站，以及識別線上行銷活動的關鍵成功量度。

您可以使用Adobe Analytics來分析網站的資料。

與Adobe Analytics整合可讓您執行下列工作：

* 啟用Analytics使用者追蹤。
* 將您的執行模式（例如製作、發佈）對應至不同的報表套裝。
* 提交用戶端內容變數作為轉換變數或流量屬性。
* 使用預先定義的變數對應。
* 一次設定完整的網站區域。
* 追蹤自訂事件。

如需整合Adobe Experience Manager與Analytics的相關資訊，請參閱 [與Adobe Analytics整合](/help/sites-administering/adobeanalytics.md).

您也可以使用 [選擇加入精靈](/help/sites-administering/opt-in.md) 輕鬆執行整合。

## 整合 Adobe Target {#integrating-with-adobe-target}

[Adobe Target](https://www.omniture.com/en/products/conversion/test-and-target) 行銷人員可使用來設計和執行線上測試、建立即時受眾區段（根據行為），以及自動鎖定內容和線上體驗。

當今的線上消費者有不斷變化的需求，並期望從他們可以選擇的各種網站和內容來源中獲得相關甚至個人化的內容。 若要吸引線上受眾，線上行銷人員必須快速找出哪些優惠方案和內容與其受眾相關且吸引人，這一點至關重要。 有了這些知識，行銷人員便需要能夠持續改進其網站，並將適當內容鎖定在不同的受眾。

[與Adobe Target整合](/help/sites-administering/target.md) 說明如何將您的網站與Adobe Target整合。

您也可以使用 [選擇加入精靈](/help/sites-administering/opt-in.md) 輕鬆執行整合。

## 選擇加入Analytics和Target {#opting-in-to-analytics-and-target}

Adobe Experience Manager提供簡單的選擇加入程式，以整合Adobe Analytics和Adobe Target。 以管理員身分登入並造訪專案主控台時，畫面會顯示選擇加入精靈。

![chlimage_1-107](assets/chlimage_1-107.png)

選擇加入與Analytics和/或Target的整合，以啟用其頁面追蹤和分析功能及個人化功能的使用。 選擇加入時，您需要提供使用者帳戶資訊，並指定要追蹤的頁面。

如需詳細資訊，請參閱 [選擇加入Adobe Analytics和Adobe Target。](/help/sites-administering/opt-in.md)

## 與Dynamic Media Classic整合 {#integrating-with-scene}

Adobe Dynamic Media Classic是一個托管解決方案，可發佈、管理、增強及傳遞動態行銷資產和豐富的視覺化銷售至網頁、行動裝置、電子郵件、社交媒體、網際網路連線顯示器及列印。

在Adobe Experience Manager中，您可以直接從Adobe Experience Manager發佈數位資產到Dynamic Media Classic，也可以從Dynamic Media Classic發佈數位資產到Adobe Experience Manager。

此外，您還可以在各種檢視器（例如「基本縮放」和「影片」）中檢視發佈於Dynamic Media Classic的Adobe Experience Manager資產。

如需Adobe Experience Manager如何與Dynamic Media Classic整合的詳細資訊，請參閱 [與Dynamic Media Classic整合](/help/sites-administering/scene7.md) 檔案。

## 與AdobeDynamic Tag Management整合 {#integrating-with-adobe-dynamic-tag-management}

[Adobe動態Tag Management](https://www.adobe.com/solutions/digital-marketing/dynamic-tag-management.html) 為行銷人員提供直覺式工具，讓他們快速輕鬆地管理不限數量的Adobe和協力廠商標籤。 您將擁有更多控制能力和靈活性，幾乎可以優化任何線上內容，同時減少對IT資源的依賴。

[整合AdobeDynamic Tag Management](/help/sites-administering/dtm.md) 使用Adobe Experience Manager，以便您能使用動態Tag Management Web屬性來追蹤Adobe Experience Manager網站。

## 與Adobe Audience Manager整合 {#integrating-with-adobe-audience-manager}

Adobe Experience Manager 6.3已移除Audience Manager整合。

<!-- Search&Promote was end of life September 1, 2022. ## Integrating with Search&Promote {#integrating-with-search-promote} -->

<!-- Search&Promote was end of life September 1, 2022. Adobe Search&Promote enables marketers to optimize how visitors browse, find, compare, and select relevant products and content on web and mobile sites. Businesses can easily promote priority items based on business objectives and visitor intent, as well as automate merchandising and promotions activity by way of KPI-based triggers or metrics. -->

<!-- Search&Promote was end of life September 1, 2022. Adobe Search&Promote is a reliable and scalable hosted site search application, capable of scaling to millions of pages or products, for heavily visited online businesses ranging from retail to news sites. It offers unprecedented levels of marketer control and metrics-based relevance. -->

<!-- Search&Promote was end of life September 1, 2022. For information about integrating Adobe Experience Manager and Search&Promote, see [Integrating with Adobe Search&Promote](/help/sites-administering/search-and-promote.md). -->

## 與 Adobe Campaign 整合 {#integrating-with-adobe-campaign}

[Adobe Campaign](https://www.adobe.com/solutions/campaign-management.html) 可讓您直接在Adobe Experience Manager中管理電子郵件傳送內容。

如需Adobe Experience Manager如何與Adobe Campaign整合的詳細資訊，請參閱 [與Adobe Campaign整合](/help/sites-administering/campaignstandard.md).

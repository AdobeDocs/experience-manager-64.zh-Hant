---
title: 個人化和內容目標鎖定
seo-title: Personalization and Content Targeting
description: 了解AEM如何建立個人化內容
seo-description: Learn how AEM can create personalized content
uuid: 3a1aaa3d-5f57-4fb7-a4be-523f0d274b79
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: personalization
discoiquuid: 850da0da-f7c3-4dd7-bb06-404c14a2a791
exl-id: 669e2509-e563-46ff-b01c-3f05ec196df5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 26%

---

# 個人化和內容目標鎖定 {#personalization}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 個人化和內容目標鎖定 {#personalization-and-content-targeting}

AEM提供工具架構，用於編寫目標內容及呈現個人化體驗。

## 定位模式 {#targeting-mode}

[製作目標內容](/help/sites-authoring/content-targeting-touch.md) 使用AEM的目標定位模式。 目標定位模式和目標元件提供用於建立行銷活動體驗內容的工具。

## 活動 {#activities}

活動可定義並組織您的行銷工作。 活動包含您要鎖定的對象，以及套用鎖定目標的時段。

例如，We.Retail產品目錄包含茶匙，它們關注季節性產品。 「夏季運動」活動會定義茶具在夏季月份鎖定的行銷區段。

活動也會識別 [目標引擎](/help/sites-authoring/personalization.md#targeting-engine) 頁面所使用。

使用 [活動主控台](/help/sites-authoring/activitylib.md) 來建立和管理您品牌的活動。 您也可以像您一樣建立活動 [作者目標內容](/help/sites-authoring/content-targeting-touch.md).

## 體驗 {#experiences}

您會針對每個活動定義一或多個體驗，以識別您要鎖定的對象。 AEM可讓您控制包含每個體驗的內容。

受眾是根據在AEM或Adobe Target中建立的行銷區段。 訪客開啟網頁時，頁面邏輯會決定其所屬的對象，並顯示您為該對象建立的內容。

例如，活動會定義兩個不同對象的體驗：30歲以上婦女和30歲以下婦女。 We.Retail網站的「女性」頁面會針對每個體驗顯示不同的產品。

您定義活動的體驗。 您可以使用 [活動主控台](/help/sites-authoring/activitylib.md#adding-editing-an-activity-using-the-activities-console) 或 [定位模式](/help/sites-authoring/content-targeting-touch.md#adding-and-removing-experiences-using-targeting-mode) 將體驗新增至活動。

## 優惠 {#offers}

選件是顯示在體驗之頁面上某個位置的內容。 針對不同的體驗使用不同的選件，以最大化內容對對象的效益。

例如，We.Retail範例網站的「女性」頁面可以使用選件作為預告影像，顯示在頁面頂端。 另一個優惠方案則用作30歲以上女性體驗和30歲以下女性體驗的預告。

使用 [選件主控台](/help/sites-authoring/offerlib.md) 來建立可在多個體驗中使用的選件。 建立單一使用選件，或在 [製作目標內容](/help/sites-authoring/content-targeting-touch.md).

## 目標定位引擎 {#targeting-engine}

定位引擎是驅動目標內容邏輯的機制。 [活動](/help/sites-authoring/activitylib.md)設定為使用兩個可用的目標定位引擎之一：AEM 和 Adobe Target。

### AEM {#aem}

AEM提供內建的定位引擎，可處理頁面要求並決定要顯示的內容。 使用 AEM 目標定位引擎時，您只能使用在 AEM 建立的區段來定義體驗的對象。

### Adobe Target {#adobe-target}

Adobe Target 目標定位引擎會使頁面被造訪時所收集的資訊在 Adobe Target 中被追蹤。

* 使用此目標定位引擎時，您可以使用從 Adobe Target 匯入的區段來定義體驗的對象。
* 使用 Adobe Target 引擎的活動[會同步到 Target](/help/sites-authoring/activitylib.md#synchronizing-activities-with-adobe-target)。

如果[已整合 Adobe Target](/help/sites-administering/opt-in.md)，即可使用此引擎。

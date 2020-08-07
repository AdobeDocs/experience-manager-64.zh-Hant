---
title: 建立文章匯出設定
seo-title: 建立文章匯出設定
description: Follow this page to learn about exporting content from Adobe Experience Manager (AEM) for upload to AEM Mobile.
seo-description: Follow this page to learn about exporting content from Adobe Experience Manager (AEM) for upload to AEM Mobile.
uuid: 089bc15b-669e-4623-bdbb-fd9abf46e098
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: bc681589-5d46-44cd-888d-b0722a2fd006
translation-type: tm+mt
source-git-commit: 622e613d556acda7cd98d4b3d20a20133756fd92
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# 建立文章匯出設定{#creating-article-export-configuration}

>[!NOTE]
>
>Adobe建議針對需要單頁應用程式架構用戶端轉換的專案使用SPA編輯器（例如React）。 [了解更多](/help/sites-developing/spa-overview.md).

>[!CAUTION]
>
>**先決條件**:
>
>Prior to learn about creating and modifying shared resources, see [Content Sync](/help/mobile/mobile-ondemand-contentsync.md) to understand the basic concepts.

AEM Mobile使用者使用「內容同步」將即時內容匯出為靜態內容，以便用於「行動應用程式」，當內容從AEM Mobile上傳至Mobile隨選服務時，就會發生此匯出。

上表 ***中提及的屬性dps-exportTemplate*** ，會定義應用程式匯出設定的路徑。 設定此屬性可建立和修改共用資源。

The following resources describes exporting content from Adobe Experience Manager (AEM) for upload to AEM Mobile.

文章有需要匯出和上傳的內容。 部分內容可在文章之間共用。

Use [ContentSync](/help/mobile/mobile-ondemand-contentsync.md) to gather the content together and create a ***Shared Resources*** package.

The ContentSync configuration found at **&lt;dps-exportTemplate>/dps-article>** should be configured to export all the content an article required for property static rendering on device.

>[!CAUTION]
>
>您只有在具備下列條件時，才能執行下列步驟來檢視範例共用資源：
>
>* 已安裝範例內容
>* 執行AEM例項
>* 未配置自定義上下文或不同埠

>



要查看共用資源示例，請參閱以下步驟：

1. 在AEM伺服器上開啟CRXDE Lite。
1. Browse to this path [/etc/contentsync/templates/dps-we-unlimited-app/dps-article](http://localhost:4502/crx/de/index.jsp#/etc/contentsync/templates/dps-we-unlimited-app/dps-article), to view the sample shared resources.

   You can view all the properties required for creating your shared resources as shown in the figure below:

   ![chlimage_1-134](assets/chlimage_1-134.png)

>[!NOTE]
>
>Articles should be uploaded or exported to AEM Mobile On-Demand Services when an articles content changes.


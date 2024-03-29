---
title: 雲端設定
seo-title: Cloud Configuration
description: 將隨需應用程式與雲端設定建立關聯，可讓Adobe Experience Manager(AEM)透過建立雙向連結，直接與以行動隨需托管的專案通訊。 請詳閱本頁以了解更多。
seo-description: Associating an On-Demand App to a Cloud Configuration allows Adobe Experience Manager (AEM) to communicate directly with a Mobile On-Demand hosted project by establishing a two way link. Follow this page to learn more.
uuid: f377f2af-864b-43df-9d42-4a5fd6cd70d5
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: authoring-on-demand-services-app
discoiquuid: d0d29b99-53d4-4b0d-947b-39d91b381de7
exl-id: eff852b0-99cd-4242-bac8-992ee10401e2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 4%

---

# 雲端設定{#cloud-configuration}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>Adobe建議針對需要單頁應用程式架構用戶端轉譯（例如React）的專案使用SPA編輯器。 [深入了解](/help/sites-developing/spa-overview.md).

將隨需應用程式與雲端設定建立關聯，可讓Adobe Experience Manager(AEM)透過建立雙向連結，直接與以行動隨需托管的專案通訊。 將應用程式連結至行動隨選專案後，您就能在AEM內執行內容建立，例如文章、橫幅和集合，同時將該內容提供給行動隨選。

從那裡，即可發佈、預覽和管理內容。 您也可以將現有的Mobile On-Demand內容匯入AEM，並執行內容編輯。

## 設定雲端設定 {#setting-up-cloud-configuration}

>[!CAUTION]
>
>開始為On-Demand應用程式設定雲端設定前，您必須先熟悉AEM Mobile布建和設定AEM Mobile On-demand Services用戶端。
>
>如需詳細資訊，請參閱 [設定AEM Mobile On-demand Services](/help/mobile/aem-mobile-setup.md) （在管理區段中）。

若要設定Mobile On-DemandCloud Services，請按一下 **管理連線** 從應用程式控制面板中拼貼。

您應該熟悉應用程式控制面板和可用的圖磚。 請參閱 [AEM Mobile應用程式控制面板](/help/mobile/mobile-apps-ondemand-application-dashboard.md) 以取得更多詳細資訊。

### 設定雲端設定的連結 {#setting-up-link-to-cloud-configuration}

>[!CAUTION]
>
>確定您有現有的On-Demand用戶端和雲端設定。
>
>如需詳細資訊，請參閱 [設定AEM Mobile On-demand Services](/help/mobile/aem-mobile-setup.md) （在管理區段中）。

下列步驟說明如何設定雲端設定的連結：

1. 從 **行動**，選擇 **應用程式** ，再從目錄中取得您的Mobile On-Demand應用程式。
1. 按一下 **管理連線** 方塊。

   ![chlimage_1-65](assets/chlimage_1-65.png)

1. 輸入已存在的配置，或通過輸入 **配置標題**, **裝置Id**，和 **裝置代號**.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. 一旦您 **裝置Id** 和 **裝置代號** 確認後，從清單中選擇您的按需項目。

   按一下 **提交**.

   ![chlimage_1-67](assets/chlimage_1-67.png)

   此 **管理連線** 圖磚會顯示您的雲端設定。

   ![chlimage_1-68](assets/chlimage_1-68.png)

   >[!CAUTION]
   >
   >如果您嘗試變更此應用程式與哪個專案相關聯，在控制面板中切換專案時，您會收到內容完整性問題的警告，如下圖所示：

   ![chlimage_1-69](assets/chlimage_1-69.png)

### 後續步驟 {#the-next-steps}

在您設定應用程式的雲端設定後，請參閱下列管理內容的資源：

* [管理文章](/help/mobile/mobile-on-demand-managing-articles.md)
* [管理橫幅](/help/mobile/mobile-on-demand-managing-banners.md)
* [管理集合](/help/mobile/mobile-on-demand-managing-collections.md)
* [上傳共用資源](/help/mobile/mobile-on-demand-shared-resources.md)
* [發佈/取消發佈內容](/help/mobile/mobile-on-demand-publishing-unpublishing.md)
* [使用預檢預覽](/help/mobile/aem-mobile-manage-ondemand-services.md)

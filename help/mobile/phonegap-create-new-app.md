---
title: 使用建立精靈建立新的AEM Mobile應用程式
seo-title: 使用建立精靈建立新的AEM Mobile應用程式
description: AEM Mobile應用程式以定義頁面結構和屬性的blueprint為基礎。 請依照本頁面了解如何根據應用程式範本建立新應用程式。
seo-description: AEM Mobile應用程式以定義頁面結構和屬性的blueprint為基礎。 請依照本頁面了解如何根據應用程式範本建立新應用程式。
uuid: c2bd63a5-3dff-4a72-b1fb-0c776e0afa33
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
discoiquuid: 27605eb7-59b2-42d4-8cc5-02cfa52b4491
exl-id: 79d2dbfb-5e44-4a96-ab9b-ba5d93fc3aae
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '681'
ht-degree: 0%

---

# 使用建立精靈{#creating-a-new-aem-mobile-app-using-create-wizard}建立新的AEM Mobile應用程式

>[!NOTE]
>
>Adobe建議針對需要單頁應用程式架構用戶端轉譯（例如React）的專案使用SPA編輯器。 [了解更多](/help/sites-developing/spa-overview.md).

AEM Mobile應用程式以定義頁面結構和屬性的blueprint為基礎。 您可以配置以下應用程式屬性：

* **標題：** 應用程式標題。
* **目標路徑：** 儲存應用程式的存放庫位置。保留預設值，以根據應用程式名稱建立路徑。

* **名稱：** 預設值為已移除空格字元之Title屬性的值。名稱在AEM內用來參照應用程式，例如代表應用程式的存放庫節點。
* **說明：** 應用程式的說明。
* **伺服器URL:** 為應用程式提供無線(OTA)內容更新的URL。預設值是用於建立應用程式（從外部化程式服務取用）的執行個體的發佈伺服器URL。 請注意，這必須是發佈伺服器例項，而非需要驗證的作者。

您也可以提供影像檔案作為應用程式縮圖、選取要使用的PhoneGap Build設定，然後選取要使用的行動應用程式分析設定。 此影像只會作為縮圖，在Experience Manager的行動應用程式主控台內呈現您的行動應用程式。

建置雲端服務及將AdobeMobile Services SDK外掛程式整合至您的應用程式中，已有其他（及選用）標籤。

* 建置：按一下「管理設定」，然後在這裡設定您的build.phonegap.com組建服務。 然後，您將可從下拉式清單中選取新建立的PhoneGap組建雲端服務。
* Analytics:按一下「管理設定」並設定您的[AdobeMobile Services SDK](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/download-sdk.html)雲端服務。 然後，您將可從下拉式清單中選取新建立的Mobile Service，以整合至您的行動應用程式。

## 使用應用程式範本{#using-app-templates}

應用程式範本可讓您輕鬆運用開發人員建立的現有設計，以在AEM內建立新應用程式。

什麼是應用程式範本？ 將其想像為頁面範本和元件的集合，這些範本和元件代表應用程式的基準或基礎。
根據其他應用程式的範本建立新應用程式時，您會看到某個應用程式的起始點代表，該應用程式即為建立該應用程式的來源。

您必須有現有的行動應用程式範本（或已安裝應用程式範本的應用程式）才能使用此功能。

最新的AEM應用程式範例套件包含含應用程式範本的更新版Geometrixx應用程式。 或者，您也可以安裝[StarterKit](https://github.com/Adobe-Marketing-Cloud-Apps/aem-phonegap-starter-kit)，該模板還提供模板。

根據應用程式範本建立新應用程式的步驟：

1. 導覽至AEM Mobile應用程式目錄：&lt;*server-url*>aem/apps.html/content/mobileapps
1. 選擇&#x200B;**Create**，然後選擇&#x200B;**App**，如下所示

![chlimage_1-158](assets/chlimage_1-158.png)

選取AEM開發人員提供給您的應用程式範本。 如需開發人員協助，請參閱[AEM Mobile應用程式結構](/help/mobile/phonegap-structure-an-app.md)。

![chlimage_1-159](assets/chlimage_1-159.png)

視需要填寫新應用程式的詳細資訊，包括選擇性變更其縮圖影像。 稍後可從&#x200B;**管理應用程式**&#x200B;方塊編輯這些值。

![chlimage_1-160](assets/chlimage_1-160.png)

## 後續步驟{#the-next-steps}

請參閱下列資源，以進一步了解其他製作角色：

* [管理應用程式圖磚](/help/mobile/phonegap-app-details-tile.md)
* [編輯應用程式中繼資料](/help/mobile/phonegap-editmetadata.md)
* [應用程式定義](/help/mobile/phonegap-app-definitions.md)
* [匯入現有的混合應用程式](/help/mobile/phonegap-adding-content-to-imported-app.md)
* [Content Services](/help/mobile/develop-content-as-a-service.md)

## 其他資源 {#additional-resources}

若要了解管理員和開發人員的角色和責任，請參閱下列資源：

* [使用AEM為Adobe PhoneGap企業開發](/help/mobile/developing-in-phonegap.md)
* [使用AEM管理Adobe PhoneGap Enterprise的內容](/help/mobile/administer-phonegap.md)

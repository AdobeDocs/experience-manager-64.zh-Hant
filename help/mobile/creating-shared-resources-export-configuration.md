---
title: 建立共用資源導出配置
seo-title: 建立共用資源導出配置
description: 請詳閱本頁，了解如何從Adobe Experience Manager(AEM)匯出共用資源以上傳至AEM Mobile。
seo-description: 請詳閱本頁，了解如何從Adobe Experience Manager(AEM)匯出共用資源以上傳至AEM Mobile。
uuid: 99b8ff94-8135-4643-a15b-aa6fb91f5401
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: 1edf6c76-ccb1-40b6-bdf6-924f1461cd28
exl-id: 92ee8c25-9f11-4743-a8e6-1f4986d09a6a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# 建立共用資源導出配置{#creating-shared-resources-export-configuration}

>[!NOTE]
>
>Adobe建議針對需要單頁應用程式架構用戶端轉譯（例如React）的專案使用SPA編輯器。 [了解更多](/help/sites-developing/spa-overview.md).

>[!CAUTION]
>
>**必備條件**:
>
>了解如何建立和修改共用資源之前，請參閱[內容同步](/help/mobile/mobile-ondemand-contentsync.md)以了解基本概念。

AEM Mobile使用者可使用「內容同步」，將即時內容匯出為靜態內容，以便在行動應用程式中使用。當內容從AEM Mobile上傳至Mobile On-Demand Services時，就會進行此匯出。

上表提及的屬性&#x200B;***dps-exportTemplate***&#x200B;定義應用程式匯出設定的路徑。 設定此屬性以建立和修改共用資源。

下列資源說明如何從Adobe Experience Manager(AEM)匯出共用資源，以上傳至AEM Mobile。

「共用HTML資源」可讓文章共用HTML資源，這些資源原本需要為所有文章重複，且可包含圖示、字型、javascript及CSS。

在&#x200B;**&lt;dps-exportTemplate>/dps-HTMLResources>**&#x200B;找到的內容同步設定應已設定為匯出裝置上屬性靜態呈現所需的所有內容和文章。

>[!CAUTION]
>
>您必須具備以下條件，才可執行下列步驟以檢視範例共用資源：
>
>* 已安裝範例內容
>* 執行AEM執行個體
>* 未配置自定義上下文或其他埠

>



若要檢視共用資源範例，請參閱下列步驟：

1. 在AEM伺服器上開啟CRXDE Lite。
1. 瀏覽至此路徑&#x200B;*[/etc/contentsync/templates/dps-we-unlimited-app/dps-HTMLResources](http://localhost:4502/crx/de/index.jsp#/etc/contentsync/templates/dps-we-unlimited-app/dps-HTMLResources)*，以檢視範例共用資源。

   您可以檢視建立共用資源所需的所有屬性，如下圖所示：

   ![chlimage_1-145](assets/chlimage_1-145.png)

>[!NOTE]
>
>任何共用資源變更時，應上傳或匯出至AEM Mobile On-demand Services。

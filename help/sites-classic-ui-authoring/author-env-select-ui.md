---
title: 選取您的UI
seo-title: Selecting your UI
description: 為方便編寫使用者，觸控式UI允許視需要切換至傳統UI。
seo-description: For convenience to authoring users, the touch-enabled UI does allow for switching to the classic UI when necessary.
uuid: 755e513e-990c-4dba-8316-623f17bf5c33
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: dcac2a3a-3241-47de-96ce-982ab0bc05eb
exl-id: 997040d4-cf8f-4240-8423-a98d562aae02
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 2%

---

# 選取您的UI{#selecting-your-ui}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

由於觸控式UI取代傳統UI，因此AEM例項的使用者或管理員必須主動決定繼續使用傳統UI。 由於傳統UI已不再維護，因此製作使用者無法只從傳統UI切換至觸控式UI中的對等UI。

為方便編寫使用者，觸控式UI允許視需要切換至傳統UI。 請參閱 [選取您的UI](/help/sites-authoring/select-ui.md) 以取得詳細資訊。

>[!NOTE]
>
>從舊版升級的執行個體將保留傳統UI以進行頁面編寫。
>
>升級後，頁面編寫不會自動切換至觸控式UI，但您可以使用 [OSGi配置](/help/sites-deploying/configuring-osgi.md) 的 **WCM編寫UI模式服務** ( `AuthoringUIMode` 服務)。 請參閱 [編輯器的UI覆寫](#uioverridesfortheeditor).

## 設定您執行個體的預設UI {#configuring-the-default-ui-for-your-instance}

系統管理員可以使用設定在啟動和登入時顯示的UI [根對應](/help/sites-deploying/osgi-configuration-settings.md#daycqrootmapping).

使用者預設值或工作階段設定可覆寫此值。

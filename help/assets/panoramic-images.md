---
title: 全景影像
description: 了解如何在Dynamic Media中使用全景影像。
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
exl-id: 51150d51-865e-4b8e-9990-ca755e4c7778
feature: Panoramic Images
role: User
source-git-commit: 0120fe1303aa3b7f5aa7db39eaf40ff127f2e338
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 4%

---

# 全景影像 {#panoramic-images}

本節介紹如何使用全景影像查看器來呈現球形全景影像，以提供沈浸式360°的房間、屬性、位置或景觀的觀看體驗。

另請參閱[管理檢視器預設集](managing-viewer-presets.md)。

![panoramic-image2](assets/panoramic-image2.png)

## 上傳資產以與全景影像檢視器搭配使用 {#uploading-assets-for-use-with-the-panoramic-image-viewer}

若要讓上傳的資產符合要與全景影像檢視器搭配使用之球面全景影像的資格，資產必須具備下列其中一項或兩項：

* 長寬比為2。

   您可以在以下位置覆蓋&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;中的預設外觀比例設定2:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* 使用關鍵字`equirectangular`、`spherical`和`panorama`、`spherical`和`panoramic`進行標籤。 請參閱[使用標籤](/help/sites-authoring/tags.md)。

外觀比例和關鍵字條件都適用於資產詳細資料頁面和全景媒體 **** 元件的全景資產。

若要上傳資產以便與全景影像檢視器搭配使用，請參閱[上傳資產](managing-assets-touch-ui.md#uploading-assets)。

## 配置Dynamic Media Classic {#configuring-dynamic-media-classic-scene}

為了讓全景影像檢視器在AEM中正常運作，您必須將全景影像檢視器預設集與Dynamic Media Classic和Dynamic Media Classic專用中繼資料同步，以便在JCR中更新檢視器預設集。 若要完成此操作，請以下列方式設定Dynamic Media Classic:

1. [針對每個公司帳戶登入您的Dynamic Media ](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html#system-requirements-dmc-app) Classic案頭應用程式。

1. 在頁面的右上角附近，按一下「**[!UICONTROL 設定>應用程式設定>發佈設定>影像伺服器]**」。
1. 在「**[!UICONTROL 影像伺服器發佈]**」頁面上，從頂端附近的「**[!UICONTROL 發佈內容]**」下拉式選單中，選取「**[!UICONTROL 影像伺服]**」。

1. 在相同的&#x200B;**[!UICONTROL 影像伺服器發佈]**&#x200B;頁面上，找到標題&#x200B;**[!UICONTROL 請求屬性]**。
1. 在&#x200B;**[!UICONTROL 請求屬性]**&#x200B;標題下，找到&#x200B;**[!UICONTROL 回覆影像大小限制]**。 然後，在相關的&#x200B;**[!UICONTROL Width]**&#x200B;和&#x200B;**[!UICONTROL Height]**&#x200B;欄位中，增加全景影像的最大允許影像大小。

   Dynamic Media Classic的限制為25,000,000像素。 寬高比為2:1的影像的最大允許大小為7000 x 3500。 但是，對於一般的案頭螢幕，4096 x 2048像素就足夠了。

   >[!NOTE]
   >
   >僅支援最大允許影像大小範圍內的影像。 若要求的影像大小超過上限，將會產生403回應。

1. 在&#x200B;**[Request Attributes]**&#x200B;標題下，執行下列操作：

   * 將「**[!UICONTROL 請求模糊化模式]**」設定為「**[!UICONTROL 停用]**」。
   * 將&#x200B;**[!UICONTROL 請求鎖定模式]**&#x200B;設定為&#x200B;**[!UICONTROL 禁用]**。

   在AEM中使用&#x200B;**[!UICONTROL 全景媒體]**&#x200B;元件時，必須進行這些設定。

1. 在&#x200B;**[!UICONTROL 影像伺服器發佈]**&#x200B;頁面底部，在左側，點選&#x200B;**[!UICONTROL 儲存]**。

1. 在右下角，點選&#x200B;**[!UICONTROL 關閉]**。

### 全景媒體元件疑難排解 {#troubleshooting-the-panoramic-media-wcm-component}

如果將影像放置到WCM的&#x200B;**[!UICONTROL 全景媒體]**&#x200B;元件中，且元件預留位置已收合，則您可能想要疑難排解下列問題：

* 如果您遇到403 Forbidden錯誤，則可能是因為請求的影像大小太大。 檢閱[設定Dynamic Media Classic](#configuring-dynamic-media-classic-scene)中的&#x200B;*回覆影像大小限制*&#x200B;設定。

* 對於資產上的&#x200B;*無效鎖定*&#x200B;或頁面上顯示的&#x200B;*解析錯誤*，請檢查&#x200B;**[!UICONTROL 請求模糊化模式]**&#x200B;和&#x200B;**[!UICONTROL 請求鎖定模式]**&#x200B;以確保它們被禁用。
* 針對污染畫布錯誤，請為影像資產的先前請求設定&#x200B;**[!UICONTROL 規則集定義檔案路徑和使CTN]**&#x200B;無效。
* 如果影像要求的大小超過所支援的限制後影像品質變得很低，請檢查&#x200B;**[!UICONTROL JPEG編碼屬性>品質]**&#x200B;設定是否非空白。 **[!UICONTROL Quality]**&#x200B;欄位的典型設定為`95`。 您可以在「**[!UICONTROL 影像伺服器發佈]**」頁面上找到設定。 若要存取頁面，請參閱[設定Dynamic Media Classic](#configuring-dynamic-media-classic-scene)。

## 預覽全景影像 {#previewing-panoramic-images}

請參閱「預覽資產」[。](previewing-assets.md)

## 發佈全景影像 {#publishing-panoramic-images}

請參閱[發佈資產](publishing-dynamicmedia-assets.md)。

---
title: 全景影像
seo-title: 全景影像
description: 瞭解如何在動態媒體中處理全景影像。
seo-description: 瞭解如何在動態媒體中處理全景影像。
uuid: dfd7a55c-7bcc-4d62-8c3a-a73726881103
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: fc285b25-2bce-493c-87bc-5f1a8a26eb42
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 4%

---


# 全景影像 {#panoramic-images}

本節將說明如何與全景影像檢視器搭配使用，以呈現球面全景影像，提供如臨現場的360°房間、屬性、位置或風景觀賞體驗。

另請參閱「 [管理檢視器預設集」](managing-viewer-presets.md)。

![panoramic-image2](assets/panoramic-image2.png)

## 上傳資產以搭配全景影像檢視器使用 {#uploading-assets-for-use-with-the-panoramic-image-viewer}

若要將已上傳的資產視為要搭配全景影像檢視器使用的球形全景影像，該資產必須具備下列其中一項或兩項：

* 寬高比為2。

   您可以在以下位置覆寫 **[!UICONTROL CRXDE Lite中的預設外觀比例]** 2設定：

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* 使用關鍵字 `equirectangular`、 `spherical`和 `panorama`、或 `spherical` 和標籤 `panoramic`。 請參 [閱使用標籤](/help/sites-authoring/tags.md)。

外觀比例和關鍵字條件都適用於資產詳細資料頁面和全景媒體 **** 元件的全景資產。

若要上傳資產以搭配全景影像檢視器使用，請參閱「上 [傳資產」](managing-assets-touch-ui.md#uploading-assets)。

## 設定Dynamic Media Classic {#configuring-dynamic-media-classic-scene}

若要讓全景影像檢視器在AEM中正常運作，您必須將全景影像檢視器預設集與Dynamic Media Classic和Dynamic Media Classic特定中繼資料同步化，如此檢視器預設集就會在JCR中更新。 若要完成此作業，請依下列方式設定Dynamic Media Classic:

1. [請針對每個公司帳戶登入您的Dynamic Media Classic](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) 執行個體。

1. 在頁面的右上角附近，按一下「設定>應 **[!UICONTROL 用程式設定>發佈設定>影像伺服器」]**。
1. 在「影 **[!UICONTROL 像伺服器發佈]** 」頁面上，從頂端的「發佈內容 **[!UICONTROL 」下拉式選單中，選取「影像]** 伺服」 ****。

1. 在相同的「影 **[!UICONTROL 像伺服器發佈]** 」頁面上，找出標題 **[!UICONTROL 「請求屬性」]**。
1. 在「請求 **[!UICONTROL 屬性」標題]** ，找出「 **[!UICONTROL 回覆影像大小限制」]**。 然後，在相關的「寬 **[!UICONTROL 度]** 」和「高 **** 度」欄位中，增加全景影像的最大允許影像大小。

   Dynamic Media Classic的限制為25,000,000像素。 寬高比為2:1的影像允許的最大大小為7000 x 3500。 不過，對於一般的桌上型電腦螢幕，4096 x 2048像素就足夠了。

   >[!NOTE]
   >
   >僅支援符合允許影像大小上限的影像。 若要求的影像大小超過限制，將會產生403個回應。

1. 在「請 **[求屬性]** 」標題下，執行下列動作：

   * 將「請 **[!UICONTROL 求模糊化模式]** 」設 **[!UICONTROL 為「停用」]**。
   * 將「請 **[!UICONTROL 求鎖定模式」設]** 置為 **[!UICONTROL 「禁用」]**。

   在AEM中使用 **[!UICONTROL Panoramic Media]** （全景媒體）元件時，必須進行這些設定。

1. 在「影像伺服器 **[!UICONTROL 發佈」頁面的左側]** ，點選「儲 **[!UICONTROL 存」]**。

1. 在右下角，點選「關 **[!UICONTROL 閉」]**。

### 全景媒體元件疑難排解 {#troubleshooting-the-panoramic-media-wcm-component}

如果您將影像放入WCM的 **[!UICONTROL Panoramic Media]** （全景媒體）元件中，而元件預留位置已收合，您可能會想要疑難排解：

* 如果您遇到403 Forbidden錯誤，可能是由於要求的影像大小過大所致。 檢閱「設 *定動態媒體經典* (Scene7)」 [中的「回覆影像大小限制」設定](#configuring-dynamic-media-classic-scene)。

* 對於頁面上 *顯示的資產上的無效鎖* 或「剖析」錯誤，請勾選「請求模糊化模式 *」和「請求鎖********* 定模式」以確保它們已禁用。
* 對於受污染的畫布錯誤，請為影 **[!UICONTROL 像資產的先前請求設定規則集定義檔案路徑並使CTN無效]** 。
* 如果影像要求的大小超過支援的限制，影像品質變得非常低，請檢查 **** JPEG編碼屬性>品質設定是否不為空。 「品質」( **[!UICONTROL Quality]** )欄位的典型設定為 `95`。 您可以在「影像伺服器發佈」頁 **[!UICONTROL 面上找到設定]** 。 若要存取頁面，請參 [閱設定Dynamic Media Classic](#configuring-dynamic-media-classic-scene)。

## 預覽全景影像 {#previewing-panoramic-images}

請參閱 [預覽資產](previewing-assets.md)。

## 發佈全景影像 {#publishing-panoramic-images}

請參閱 [發佈資產](publishing-dynamicmedia-assets.md)。

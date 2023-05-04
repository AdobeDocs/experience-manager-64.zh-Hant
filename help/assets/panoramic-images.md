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
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 5%

---

# 全景影像 {#panoramic-images}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

本節介紹如何使用全景影像查看器來呈現球形全景影像，以提供沈浸式360°的房間、屬性、位置或景觀的觀看體驗。

另請參閱 [管理檢視器預設集](managing-viewer-presets.md).

![panoramic-image2](assets/panoramic-image2.png)

## 上傳資產以與全景影像檢視器搭配使用 {#uploading-assets-for-use-with-the-panoramic-image-viewer}

若要讓上傳的資產符合要與全景影像檢視器搭配使用之球面全景影像的資格，資產必須具備下列其中一項或兩項：

* 長寬比為2。

   您可以覆寫2的預設外觀比例設定，位於 **[!UICONTROL CRXDE Lite]** （位於下列位置）:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* 使用關鍵字加上標籤 `equirectangular`，或 `spherical`和 `panorama`，或 `spherical` 和 `panoramic`. 請參閱 [使用標籤](/help/sites-authoring/tags.md).

外觀比例和關鍵字條件都適用於資產詳細資料頁面和全景媒體 **** 元件的全景資產。

若要上傳資產以搭配全景影像檢視器使用，請參閱 [上傳資產](managing-assets-touch-ui.md#uploading-assets).

## 設定Dynamic Media Classic {#configuring-dynamic-media-classic-scene}

為了讓全景影像檢視器在AEM中正常運作，您必須將全景影像檢視器預設集與Dynamic Media Classic和Dynamic Media Classic專用中繼資料同步，以便在JCR中更新檢視器預設集。 若要完成此操作，請以下列方式設定Dynamic Media Classic:

1. [登入Dynamic Media Classic案頭應用程式](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html#system-requirements-dmc-app) 每個公司帳戶。

1. 在頁面的右上角附近，按一下 **[!UICONTROL 「設定」 > 「應用程式設定」 > 「發佈設定」 > 「影像伺服器」]**.
1. 在 **[!UICONTROL 影像伺服器發佈]** 頁面，從 **[!UICONTROL 發佈內容]** 下拉式功能表（位於頂端附近），選取 **[!UICONTROL 影像提供]**.

1. 相同 **[!UICONTROL 影像伺服器發佈]** 頁面，找出標題 **[!UICONTROL 請求屬性]**.
1. 在 **[!UICONTROL 請求屬性]** 標題，定位 **[!UICONTROL 回覆影像大小限制]**. 然後，在 **[!UICONTROL 寬度]** 和 **[!UICONTROL 高度]** 欄位，增加全景影像的最大允許影像大小。

   Dynamic Media Classic的限制為25,000,000像素。 寬高比為2:1的影像的最大允許大小為7000 x 3500。 但是，對於一般的案頭螢幕，4096 x 2048像素就足夠了。

   >[!NOTE]
   >
   >僅支援最大允許影像大小範圍內的影像。 若要求的影像大小超過上限，將會產生403回應。

1. 在 **[請求屬性]** 標題，執行下列動作：

   * 設定 **[!UICONTROL 要求模糊化模式]** to **[!UICONTROL 已停用]**.
   * 設定 **[!UICONTROL 請求鎖定模式]** to **[!UICONTROL 已停用]**.

   使用 **[!UICONTROL 全景媒體]** 元件。

1. 在 **[!UICONTROL 影像伺服器發佈]** 頁面，在左側，點選 **[!UICONTROL 儲存]**.

1. 在右下角，點選 **[!UICONTROL 關閉]**.

### 全景媒體元件疑難排解 {#troubleshooting-the-panoramic-media-wcm-component}

如果您將影像放入 **[!UICONTROL 全景媒體]** 元件，且元件預留位置已收合，您可以疑難排解下列問題：

* 如果您遇到403 Forbidden錯誤，則可能是因為請求的影像大小太大。 檢閱 *回覆影像大小限制* 設定 [設定Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

* 對於 *鎖無效* 或 *解析錯誤* 顯示於頁面上，請核取 **[!UICONTROL 要求模糊化模式]** 和 **[!UICONTROL 請求鎖定模式]** 以確保已停用。
* 如果畫布有問題，請設定 **[!UICONTROL 規則集定義檔案路徑和使CTN無效]** 用於影像資產的先前請求。
* 如果影像要求的大小超過支援的限制，影像品質變得非常低，請檢查 **[!UICONTROL JPEG編碼屬性>品質]** 設定不為空。 的典型設定 **[!UICONTROL 品質]** 欄位為 `95`. 您可以在 **[!UICONTROL 影像伺服器發佈]** 頁面。 若要存取頁面，請參閱 [設定Dynamic Media Classic](#configuring-dynamic-media-classic-scene).

## 預覽全景影像 {#previewing-panoramic-images}

請參閱 [預覽資產](previewing-assets.md).

## 發佈全景影像 {#publishing-panoramic-images}

請參閱 [發佈資產](publishing-dynamicmedia-assets.md).

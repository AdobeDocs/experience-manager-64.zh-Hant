---
title: 將Dynamic Media視訊或影像檢視器內嵌在網頁上
seo-title: Embedding the Dynamic Media Video or Image viewer on a web page
description: 了解如何將Dynamic Media視訊或影像內嵌在網頁上
seo-description: Learn how to embed Dynamic media video or images on a web page
uuid: 6f786521-eb6c-4c80-8c15-9bf97b56818f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 4ae76d8a-208f-4099-9f17-a94df424685e
exl-id: bff564a8-e982-4e1a-a9b5-05e44e3e4d46
feature: Components
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 21%

---

# 將Dynamic Media視訊或影像檢視器內嵌在網頁上 {#embedding-the-video-or-image-viewer-on-a-web-page}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

當您想 **** 要播放視訊或檢視內嵌在網頁上的資產時，請使用「內嵌代碼」功能。您可將內嵌代碼複製到剪貼簿，以便貼到網頁中。「內嵌代碼」對話方塊中不允許編 **[!UICONTROL 輯代碼]** 。

只有在 _not_ 使用 [!DNL Experience Manager] 作為WCM。 如果您使用 [!DNL Experience Manager] 作為WCM [直接在頁面上新增資產。](adding-dynamic-media-assets-to-pages.md)

請參閱 [將URL連結至您的Web應用程式。](linking-urls-to-yourwebapplication.md)

請參閱 [為回應式網站傳送最佳化影像。](responsive-site.md)

>[!NOTE]
>
>在您發佈選取的資產後，內嵌程式碼才可供複製。 此外，您也必須發佈檢視器預設集或影像預設集。
>
>請參閱 [發佈資產](publishing-dynamicmedia-assets.md).
>
>請參閱 [發佈檢視器預設集](managing-viewer-presets.md#publishing-viewer-presets).
>
>請參閱 [發佈影像預設集](managing-image-presets.md#publishing-image-presets).

**將Dynamic Media視訊或影像檢視器內嵌在網頁上**:

1. 導覽至 *已發佈* 您要複製其內嵌程式碼的影片或影像資產。

   請記住，內嵌程式碼僅可在您首次 *發佈**資產後* 複製。此外，檢視器預設集或影像預設集也必須發佈。

   請參閱 [發佈資產。](publishing-dynamicmedia-assets.md)

   請參閱 [發佈檢視器預設集](managing-viewer-presets.md#publishing-viewer-presets).

   請參閱 [發佈影像預設集](managing-image-presets.md#publishing-image-presets).

1. 在左側導軌中，選取下拉式選單，然後點選 **[!UICONTROL 檢視器]**.
1. 在左側導軌中，點選檢視器預設集名稱。 檢視器預設集會套用至資產。
1. 點選 **[!UICONTROL 內嵌]**.
1. 在 **[!UICONTROL 內嵌程式碼]** 對話框，將整個代碼複製到剪貼簿，然後點選 **[!UICONTROL 關閉]**.
1. 將內嵌程式碼貼到您的網頁中。

## 使用HTTP/2傳遞Dynamic Media資產 {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2是全新、更新的Web通訊協定，可改善瀏覽器和伺服器的通訊方式。 它提供了更快的資訊傳輸，並降低了所需的處理能力。 Dynamic Media資產的傳送現在可透過HTTP/2，提供更理想的回應和載入時間。

請參閱 [HTTP2內容傳送](http2.md) 如需開始使用HTTP/2搭配您的Dynamic Media帳戶的完整詳細資訊。

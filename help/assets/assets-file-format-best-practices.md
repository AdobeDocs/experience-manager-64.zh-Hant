---
title: Assets檔案格式最佳實務
description: 檔案支援的最佳實務，於 [!DNL Experience Manager] 資產。
contentOwner: AG
feature: Asset Management,Developer Tools
role: Admin
exl-id: ff739a17-188e-4779-8820-9e4d9b7031d0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 1%

---

# Assets檔案格式最佳實務 {#assets-file-format-best-practices}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

[!DNL Experience Manager Assets] 支援許多專有和第三方檔案格式庫，以滿足用戶的不同檔案支援需求。 支援的Adobe程式庫包括Adobe Camera Raw、Gibson、Adobe PDF Rasterizer和Adobe InDesign Server。 此外， [!DNL Assets] 支援協力廠商程式庫，包括ImageMagick、TwelveMunkes等。

如需支援的檔案格式，請參閱 [Assets支援的格式](assets-formats.md).

## Adobe Camera Raw資料庫 {#adobe-camera-raw-library}

為獲得最佳效能，Adobe建議使用Adobe Camera Raw程式庫：

* 原始
* DNG

Adobe Camera Raw庫支援CMYK顏色配置檔案作為輸入。 但是，它會以RGB色域產生輸出，並僅支援以JPEG格式輸出。 它不會在縮圖中保留源檔案顏色空間（例如CMYK）。

如需詳細資訊，請參閱 [Camera Raw支援](camera-raw.md) in [!DNL Assets].

## Adobe PDF模擬轉譯器資料庫 {#adobe-pdf-rasterizer-library}

為獲得最佳結果，Adobe建議對下列檔案使用Adobe PDF模擬轉譯器程式庫：

* 大量且內容密集的PDF檔案
* 未在盒內產生縮圖的AI檔案
* 適用於具有專色(PMS)顏色的AI檔案

與現成的點陣輸出相比，使用PDF模擬轉譯器產生的縮圖和預覽的品質更佳。 Adobe PDF模擬轉譯器程式庫不支援任何色域轉換。 無論來源PDF檔案的色域為何，Adobe PDF模擬轉譯器只會產生RGB輸出。

## Adobe InDesign伺服器 {#adobe-indesign-cc-server}

Adobe建議您使用Adobe InDesign伺服器來擷取Adobe InDesign專用轉譯，例如IDML和HTML。 如需詳細資訊，請參閱 [新增 [!DNL Experience Manager] assets作為Adobe InDesign的參考](managing-linked-subassets.md#add-aem-assets-as-references-in-adobe-indesign).

## Dynamic Media  {#dynamic-media}

Dynamic Media透過其全球、可擴充且效能最佳化的網路，即時產生並提供多種豐富內容變異。 它提供互動式檢視體驗，並簡化數位行銷活動管理程式。 如需啟用Dynamic Media的詳細資訊，請參閱 [設定Dynamic Media](config-dynamic.md).

目前，Dynamic Media可支援每個檔案高達15 GB的內容影片。

## ImageMagick程式庫 {#imagemagick-library}

Adobe建議在下列情況下使用ImageMagick程式庫：

* 為EPS檔案產生縮圖轉譯
* 保留影像配置檔案資訊
* 保持透明度
* 處理PSD和PSB檔案

了解如何在 [!DNL Experience Manager]，請參閱 [使用ImageMagick](media-handlers.md#an-example-using-imagemagick). 如需最佳使用方式，請參閱 [設定ImageMagick的最佳作法](best-practices-for-imagemagick.md).

## 影像轉碼程式庫 {#image-transcoding-library}

Adobe影像轉碼程式庫是執行核心影像處理功能的影像處理解決方案，包括影像編碼、轉碼、重新取樣、調整大小等。

影像轉碼程式庫支援下列MIME類型：

* JPG/JPEG
* PNG（8位元和16位元）
* GIF
* BMP
* TIFF/壓縮TIFF（32位Tiff和PTiff除外）。
* 伊科
* ICN

如需詳細資訊，請參閱 [影像轉碼程式庫](imaging-transcoding-library.md).

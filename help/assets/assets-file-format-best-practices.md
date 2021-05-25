---
title: Assets檔案格式最佳實務
description: AEM Assets中檔案支援的最佳實務。
contentOwner: AG
feature: 資產管理，開發人員工具
role: Administrator
exl-id: ff739a17-188e-4779-8820-9e4d9b7031d0
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Assets檔案格式最佳實務{#assets-file-format-best-practices}

AEM Assets支援許多專屬和協力廠商檔案格式程式庫，以符合使用者的不同檔案支援需求。 支援的Adobe程式庫包括Adobe Camera Raw、Gibson、Adobe PDF Rasterizer和Adobe InDesign Server。 此外，AEM Assets支援協力廠商程式庫，包括ImageMagick、TwelveMunes等。

如需支援的檔案格式，請參閱[Assets supported formats](assets-formats.md)。

## Adobe Camera Raw資料庫{#adobe-camera-raw-library}

為獲得最佳效能，Adobe建議使用Adobe Camera Raw程式庫：

* 原始
* DNG

Adobe Camera Raw庫支援CMYK顏色配置檔案作為輸入。 但是，它只支援JPEG格式的輸出，並以RGB顏色空間生成輸出。 它不會在縮圖中保留源檔案顏色空間（例如CMYK）。

如需詳細資訊，請參閱AEM Assets中的[Camera Raw支援](camera-raw.md)。

## Adobe PDF模擬轉譯器庫{#adobe-pdf-rasterizer-library}

為獲得最佳結果，Adobe建議對下列檔案使用Adobe PDF模擬轉譯器程式庫：

* 大量且內容密集的PDF檔案
* 未在盒內產生縮圖的AI檔案
* 適用於具有專色(PMS)顏色的AI檔案

使用PDF模擬轉譯器產生的縮圖和預覽畫面品質比現成可用的點陣輸出好。 Adobe PDF模擬轉譯器程式庫不支援任何色域轉換。 不論來源PDF檔案的色域為何，Adobe PDF模擬轉譯器只會產生RGB輸出。

## Adobe InDesign伺服器{#adobe-indesign-cc-server}

Adobe建議您使用Adobe InDesign伺服器來擷取Adobe InDesign專用轉譯，例如IDML和HTML。 如需詳細資訊，請參閱[在Adobe InDesign](managing-linked-subassets.md#add-aem-assets-as-references-in-adobe-indesign)中將AEM資產新增為參考。

## 動態媒體  {#dynamic-media}

Dynamic Media透過其全球、可擴充且效能最佳化的網路，即時產生並提供多種豐富內容變異。 它提供互動式檢視體驗，並簡化數位行銷活動管理程式。 如需啟用Dynamic Media的詳細資訊，請參閱[設定Dynamic Media](config-dynamic.md)。

目前，Dynamic Media可支援每個檔案高達15 GB的內容影片。

## ImageMagick庫{#imagemagick-library}

Adobe建議在下列情況下使用ImageMagick程式庫：

* 為EPS檔案生成縮略圖格式副本
* 保留影像配置檔案資訊
* 保持透明度
* 處理PSD和PSB檔案

若要了解如何在AEM中設定ImageMagic程式庫，請參閱[使用ImageMagick](media-handlers.md#an-example-using-imagemagick)。 如需最佳用法，請參閱[設定ImageMagick](best-practices-for-imagemagick.md)的最佳實務。

## 影像轉碼庫{#image-transcoding-library}

Adobe影像轉碼程式庫是執行核心影像處理功能的影像處理解決方案，包括影像編碼、轉碼、重新取樣、調整大小等。

影像轉碼程式庫支援下列MIME類型：

* JPG/JPEG
* PNG（8位元和16位元）
* GIF
* BMP
* TIFF/壓縮TIFF（除32位Tiff和PTiff外）。
* 伊科
* ICN

如需詳細資訊，請參閱[影像轉碼程式庫](imaging-transcoding-library.md)。

---
title: 資產檔案格式最佳實務
description: 在AEM Assets提供檔案支援的最佳做法。
contentOwner: AG
feature: 資產管理，開發人員工具
role: 管理員
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---


# 資產檔案格式最佳實務{#assets-file-format-best-practices}

AEM Assets支援許多專屬和協力廠商的檔案格式程式庫，以符合使用者的多種檔案支援需求。 支援的Adobe程式庫包括Adobe Camera Raw、Gibson、Adobe PDF·拉斯捷瑞和Adobe InDesign Server。 此外，AEM Assets還支援協力廠商的資料庫，包括ImageMagick、TwelveMoxes等。

有關支援的檔案格式，請參見[Assets supported formats](assets-formats.md)。

## Adobe Camera Raw圖書館{#adobe-camera-raw-library}

為獲得最佳效能，Adobe建議使用Adobe Camera Raw程式庫：

* RAW
* DNG

Adobe Camera Raw庫支援CMYK顏色配置檔案作為輸入。 但是，它僅支援JPEG格式的輸出，並且在RGB顏色空間中生成輸出。 它不會在縮圖中保留原始檔案的色域（例如CMYK）。

如需詳細資訊，請參閱AEM Assets的[Camera Raw支援](camera-raw.md)。

## Adobe PDF光柵化器庫{#adobe-pdf-rasterizer-library}

為獲得最佳結果，Adobe建議對下列檔案使用Adobe PDF點陣化器程式庫：

* 大量、內容密集的PDF檔案
* 未在包裝盒中產生縮圖的AI檔案
* 對於具有專色(PMS)顏色的AI檔案

使用PDF點陣化器產生的縮圖和預覽，比現成可用的點陣化輸出更具品質。 Adobe PDF點陣化器程式庫不支援任何色域轉換。 不論來源PDF檔案的色域為何，Adobe PDF點陣化器只會產生RGB輸出。

## Adobe InDesign伺服器{#adobe-indesign-cc-server}

Adobe建議您使用Adobe InDesign伺服器來擷取Adobe InDesign特定轉譯，例如IDML和HTML。 如需詳細資訊，請參閱[在AEMAdobe InDesign](managing-linked-subassets.md#add-aem-assets-as-references-in-adobe-indesign)中新增資產作為參考。

## 動態媒體  {#dynamic-media}

Dynamic Media透過其全球、可擴充且最佳化效能的網路，即時產生並提供多種多樣化內容。 它提供互動式檢視體驗，並簡化數位宣傳管理程式。 有關啟用Dynamic Media的詳細資訊，請參閱[配置Dynamic Media](config-dynamic.md)。

目前，Dynamic Media支援每個檔案高達15 GB的內容。

## ImageMagick程式庫{#imagemagick-library}

Adobe建議在下列情況下使用ImageMagick程式庫：

* 為EPS檔案生成縮略圖轉譯
* 若要保留影像描述檔資訊
* 要保留透明度
* 要處理PSD和PSB檔案

要瞭解如何在中設定ImageMagic庫，請AEM參閱[使用ImageMagick](media-handlers.md#an-example-using-imagemagick)。 如需最佳使用方式，請參閱[設定ImageMagick](best-practices-for-imagemagick.md)的最佳實務。

## 影像轉碼程式庫{#image-transcoding-library}

Adobe影像轉碼程式庫是執行核心影像處理功能的影像處理解決方案，包括影像編碼、轉碼、重新取樣、調整大小等。

映像轉碼庫支援以下MIME類型：

* JPG/JPEG
* PNG（8位元和16位元）
* GIF
* BMP
* TIFF/壓縮TIFF（除32位元Tiff和PTiff外）。
* ICO
* ICN

如需詳細資訊，請參閱[影像轉碼程式庫](imaging-transcoding-library.md)。

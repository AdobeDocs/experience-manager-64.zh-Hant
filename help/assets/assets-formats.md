---
title: 支援的檔案格式 [!DNL Experience Manager] 資產
description: Assets支援的檔案格式和MIME類型清單以及每種格式支援的功能。
contentOwner: AG
feature: Asset Management,Renditions
role: User,Admin
exl-id: ee25fe8f-36fb-42b3-9f90-0ea77bc02e2f
source-git-commit: cc47644419f7b7f4f1f00bb848050aa4a98efa09
workflow-type: tm+mt
source-wordcount: '1645'
ht-degree: 10%

---

# 支援的檔案格式 [!DNL Adobe Experience Manager Assets] {#assets-supported-formats}

[!DNL Experience Manager Assets] 支援多種檔案格式，每種功能對不同的MIME類型都有不同的支援。

整合 [!DNL Assets] 使用其他符合標準的數字資產管理(DAM)解決方案和案頭軟體，使用Adobe的可擴展元資料平XMP台(EMP)。

請參閱圖例以了解支援程度。

| 支援程度 | 說明 |
|:---:|---|
| ✓ | 支援 |
| &#42; | 支援附加功能 |
| − | 不適用 |

## 光柵影像格式 {#supported-raster-image-formats}

資產管理功能支援的光柵影像格式如下：

| 格式 | 儲存 | 元資料管理 | 元資料提取 | 縮略圖生成 | 互動式編輯 | 元資料寫回 | 分析 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |  | ✓ |
| TIFF | ✓ | ✓ | ✓ | ✓ |  | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| BMP | ✓ | ✓ | ✓ | ✓ | ✓ |  | ✓ |
| PNM | ✓ | ✓ |  |  |  |  | ✓ |
| PGM | ✓ | ✓ |  |  |  |  | ✓ |
| PBM | ✓ | ✓ |  |  |  |  | ✓ |
| PPM | ✓ | ✓ |  |  |  |  | ✓ |
| PSD **?** | ✓ | ✓ | ✓ | ✓ |  |  | ✓ |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ |  | ✓ |  |
| 皮克 |  |  |  |  |  |  | ✓ |
| PSB | ✓ | ✓ | ✓ | ✓ |  |  |  |

**?** 從PSD檔案中提取合併的影像。 它是由Adobe Photoshop生成並包含在PSD檔案中的影像。 根據設定，合併的影像可能是實際影像，也可能不是實際影像。

支援Dynamic Media特徵的光柵影像格式如下：

| 格式 | 上載<br> （輸入格式） | 建立<br> 影像<br> 預設<br> （輸出格式） | 預覽<br> 動態<br> 格式 | 交付<br> 動態<br> 格式 | 下載<br> 動態<br> 格式 |
|---|:---:|:---:|:---:|:---:|:---:|
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| BMP | ✓ |  |  |  |  |
| PNM |  |  |  |  |  |
| PGM |  |  |  |  |  |
| PBM |  |  |  |  |  |
| PPM |  |  |  |  |  |
| PSD **?** | ✓ |  |  |  |  |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ |
| 皮克 | ✓ |  |  |  |  |
| PSB |  |  |  |  |  |

**?** 從PSD檔案中提取合併的影像。 它是由Adobe Photoshop生成並包含在PSD檔案中的影像。 根據設定，合併的影像可能是實際影像，也可能不是實際影像。

除上述資訊外，還應考慮以下事項：

* 對EPS檔案的支援僅適用於光柵影像。 例如，預設情況下不支援EPS向量影像的縮略圖生成。 要添加支援， [配置ImageMagick](best-practices-for-imagemagick.md)。 要整合第三方工具以啟用其他功能，請參見 [基於命令行的媒體處理程式](media-handlers.md#command-line-based-media-handler)。

* 將元資料寫回添加到 `NComm` 處理程式。

* 要使用Dynamic Media預覽和生成EPS檔案的動態格式副本，請參閱 [Adobe Illustrator（大赦國際）、Postscript(EPS)和PDF檔案格式。](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* 對於EPS檔案，PostScript文檔結構化約定(PS-Adobe)3.0版或更高版本支援元資料寫回。

## Dynamic Media不支援的光柵影像格式 {#unsupported-image-formats-dynamic-media}

下表描述了以下柵格影像檔案格式的子類型： *不* 在Dynamic Media。

另請參閱 [檢測不支援的Dynamic Media檔案格式](https://helpx.adobe.com/experience-manager/kb/detect-unsupported-assets-for-dynamic-media.html)。

* IDAT區塊大小大於100 MB的PNG檔案。
* PSB檔案。
* 不支援具有非CMYK、RGB、灰度或點陣圖的色彩空間的PSD檔案。 不支援DuoTone、Lab和索引顏色空間。
* PSD深度大於16的檔案。
* TIFF具有浮點資料的檔案。
* TIFF具有實驗室顏色空間的檔案。

## PDFRasterizer庫 {#supported-pdf-rasterizer-library}

Adobe PDFRasterizer庫為大型且內容密集型的Adobe Illustrator和PDF檔案生成高質量縮略圖和預覽。 Adobe建議使用PDF光柵化器庫進行以下操作：

* 要處理的資源密集型內容密集型AI/PDF檔案。
* AI/PDF檔案，預設情況下不生成縮略圖。
* AI檔案具有Pantone匹配系統(PMS)顏色。

請參閱 [使用PDF光柵化器](aem-pdf-rasterizer.md)。

## 影像轉碼庫 {#supported-image-transcoding-library}

Adobe影像轉碼庫是執行核心影像處理功能的影像處理解決方案，如編碼、轉碼、重採樣和調整大小。

映像轉碼庫支援JPG/JPEG、PNG（8位和16位）、GIF、BMP、TIFF/壓縮TIFF(32位TIFF檔案和PTIFF檔案除外)、ICO和ICN MIME類型。

請參閱 [映像轉碼庫](imaging-transcoding-library.md)。

## Camera Raw {#supported-camera-raw}

Adobe Camera Raw圖書館 [!DNL Assets] 來攝取原始影像。 請參閱 [Camera Raw支援](camera-raw.md)。

## 文檔格式 {#supported-document-formats}

資產管理功能支援的文檔格式如下：

| 格式 | 儲存 | 元資料<br> 管理 | 全文<br> 提取 | 元資料<br> 提取 | 縮略圖<br> 代 | 蘇巴塞<br> 提取 | 元資料<br> 寫 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ |  | ✓ | ✓ | ✓ | ✓ |
| DOC | ✓ | ✓ | ✓ | ✓ |  |  |  |
| DOCX | ✓ | ✓ | ✓ | ✓ |  |  |  |
| ODT | ✓ | ✓ | ✓ |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| HTML | ✓ | ✓ | ✓ |  |  |  |  |
| RTF | ✓ | ✓ | ✓ |  |  |  |  |
| TXT | ✓ | ✓ | ✓ |  |  |  |  |
| XLS | ✓ | ✓ | ✓ |  |  |  |  |
| XLSX | ✓ | ✓ | ✓ | ✓ |  |  |  |
| 耗氧物質 | ✓ | ✓ | ✓ |  |  |  |  |
| PPT | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| 耗氧潛能 | ✓ | ✓ | ✓ |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | ✓ | ✓ |  | ✓ | ✓ | ✓ | ✓ |
| PS | ✓ | ✓ |  |  |  |  |  |
| QXP | ✓ | ✓ |  |  |  |  |  |
| ePub | ✓ | ✓ |  | ✓ | ✓ |  |  |

支援Dynamic Media功能的文檔格式如下：

| 格式 | 上載<br> （輸入格式） | 建立<br> 影像<br> 預設<br> （輸出格式） | 預覽<br> 動態<br> 格式 | 交付<br> 動態<br> 格式 | 下載<br> 動態<br> 格式 |
|---|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ |  |  |  |  |
| 文檔 |  |  |  |  |  |
| DOCX |  |  |  |  |  |
| ODT |  |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) （請參閱下面的注釋） | ✓ | ✓ | ✓ | ✓ | ✓ |
| HTML |  |  |  |  |  |
| RTF |  |  |  |  |  |
| 文本 |  |  |  |  |  |
| XLS |  |  |  |  |  |
| XLSX |  |  |  |  |  |
| 耗氧物質 |  |  |  |  |  |
| PPT |  |  |  |  |  |
| PPTX |  |  |  |  |  |
| 耗氧潛能 |  |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | ✓ |  |  |  |  |
| PS |  |  |  |  |  |
| QXP |  |  |  |  |  |
| ePub |  |  |  |  |  |

>[!NOTE]
>
>對於安全PDF，僅支援上載。

除了上述功能外，請考慮以下內容：

* 要使用Dynamic Media生成PDF檔案的動態格式副本，請參閱 [Adobe Illustrator（大赦國際）、Postscript(EPS)和PDF檔案格式。](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* 要使用Dynamic Media預覽和生成AI檔案的動態格式副本，請參閱 [Adobe Illustrator（大赦國際）、Postscript(EPS)和PDF檔案格式。](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* 要使用Dynamic Media為INDD檔案生成動態格式副本，請參見 [InDesign(INDD)檔案格式](../assets/managing-image-presets.md#indesign-indd-file-format)。

## 多媒體格式 {#supported-multimedia-formats}

| 格式 | 儲存 | 元資料管理 | 元資料提取 | 縮略圖生成 | FFMPEG轉碼 |
|:---|:---:|:---:|:---:|:---:|:---:|
| AAC | ✓ | ✓ |  | - | &#42; |
| MIDI | ✓ | ✓ |  | - | &#42; |
| 3GP | ✓ | ✓ |  | - | &#42; |
| MP3 | ✓ | ✓ | ✓ | - | &#42; |
| MPG | ✓ | ✓ |  | - | &#42; |
| 奧加 | ✓ | ✓ |  | - | &#42; |
| OGG | ✓ | ✓ |  | - | &#42; |
| RA | ✓ | ✓ |  | - | &#42; |
| WAV | ✓ | ✓ |  | - | &#42; |
| WMA | ✓ | ✓ |  | - | &#42; |
| DVI | ✓ | ✓ |  | &#42; | &#42; |
| FLV | ✓ | ✓ |  | &#42; | &#42; |
| M4V | ✓ | ✓ |  | &#42; | &#42; |
| MPEG | ✓ | ✓ |  | &#42; | &#42; |
| OGV | ✓ | ✓ |  | &#42; | &#42; |
| MOV | ✓ | ✓ |  | &#42; | &#42; |
| WMV | ✓ | ✓ |  | &#42; | &#42; |
| SWF | ✓ | ✓ |  |  |  |

## 用於Dynamic Media轉碼的輸入視頻格式 {#supported-input-video-formats-for-dynamic-media-transcoding}

| 視頻檔案副檔名 | 容器 | 推薦的視頻編解碼器 | 不支援的視頻編解碼器 |
|---|---|---|---|
| MP4 | MPEG-4 | H264/AVC（所有配置檔案） |  |
| MOV,QT | Apple快速時間 | H264/AVC、AppleProRes422和HQ、Sony XDCAM、Sony DVCAM、HDV、松下DVCPro、AppleDV(DV25)、ApplePhotoSON、Avid DNxHD、JpegAVD AVR | Apple中級，Apple動畫 |
| FLV、F4V | AdobeFlash | H264/AVC、Flix VP6、H263、Sorenson | SWF（向量動畫檔案） |
| WMV | Windows Media 9 | WMV3(v9)、WMV2(v8)、WMV1(v7)、GoToMeeting(G2M2、G2M3、G2M4) | Microsoft螢幕(MSS2)、Microsoft照片(WVP2) |
| MPG、VOB、M2V、MP2 | MPEG-2 | MPEG-2 |  |
| M4V | AppleiTunes | H264/AVC |  |
| 艾維 | A/V交織 | XVID、DIVX、HDV、MiniDV(DV25)、Techsmith Camtasia、Huffyuv、Fraps、Panasonic DVCPro | Indeo3(IV30)、MJPEG、Microsoft視頻1(MS-CRAM) |
| WebM | WebM | GoogleVP8 |  |
| OGV,OGG | 奧格 | 蒂奧拉，VP3，狄拉克 |  |
| MXF | MXF | Sony XDCAM、MPEG-2、MPEG-4、松下DVCPro |  |
| MTS | AVCHD | H264/AVC |  |
| MKV | 馬特羅斯卡 | H264/AVC |  |
| R3D 、 RM | 紅色原始視頻 | MJPEG 2000 |  |
| RAM、RM | RealVideo | 不支援 | Real G2(RV20)、Real 8(RV30)、Real 10(RV40) |
| FLAC | 原生弗拉克語 | 免費無損音頻編解碼器 |  |
| MJ2 | 2000年JPEG | 運動JPEG2000編解碼器 |  |

## 存檔格式 {#supported-archive-formats}

下表介紹了支援的存檔格式和通用DAM工作流的適用性。

| 格式 | 儲存 | 版本設定 | 工作流程 | 發佈 | 存取控制 | Dynamic Media交付 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| TGZ | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| JAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| RAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| 塔爾 | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| ZIP **†** | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |

**†** 從PSD檔案中提取合併的影像。 它是由Adobe Photoshop生成並包含在PSD檔案中的影像。 根據設定，合併的影像可能是實際影像，也可能不是實際影像。 使用 `Deflate64` 算法在支援方面有限AEM。 不支援存檔和取消存檔操作。 但是，支援上載、瀏覽和下載等操作。

## 其他支援的格式 {#other-supported-formats}

下表說明了常用DAM工作流對幾種其他檔案格式的適用性。

| 格式 | 儲存 | 版本設定 | 工作流程 | 發佈 | 存取控制 | Dynamic Media交付 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| **#** | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| SVG | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| CSS | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| VTT | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| XML | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| JavaScript（當配置有自己的傳遞域時） |  |  |  |  |  | ✓ |

**#** DAM中支援其他格式，用於儲存、版本控制、ACL、工作流、發佈和元資料管理。

## 支援的MIME類型 {#supported-mime-types}

預設情況下， [!DNL Experience Manager] 使用檔案副檔名檢測檔案類型。 [!DNL Experience Manager] 可以從檔案內容中檢測。 對於後者，選擇 [!UICONTROL 從內容中檢測MIME] 選項 [!UICONTROL 第CQ天DAM MIME類型服務] 的 [!DNL Experience Manager] Web控制台。

支援的MIME類型清單可在CRXDE Lite中找到 `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`。

| 檔案副檔名 | MIME類型/ Internet媒體類型 | 預設jobParam值 | 允許的jobParam值 |
|---|---|---|---|
| 影像 | 映像/秒7資產 | `usmAmount=1.75&usmRadius=0.2`<br>`&usmThreshold=2&usmMonochrome=0&` | 預設jobParam適用於所有影像mime類型資產。<ul><li>[挖空背景選項](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-knockout-background-options.html)</li><li>[manualCropOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-manual-crop-options.html)</li><li>[自動顏色裁剪選項](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-color-crop-options.html)</li><li>[autoTransparentCropOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-transparent-crop-options.html)</li><li>[顏色管理選項](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-color-management-options.html)</li><li>[自動設定建立選項](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-set-creation-options.html)</li><li>[電子郵件設定](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/sting-constants/r-email-settings.html)</li><li>[xmp關鍵字](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-xmp-keywords.html)</li><li>[unsharpMask選項](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-unsharp-mask-options.html)</li></ul> |
| 3G2 | 視頻/3gpp2 |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| 3GP | 視頻/3gpp |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| AAC | audio/x-aac |  |  |
| 原子力顯微鏡 | application/xfont-type1 |  |  |
| AI | application/postscript | `aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScript選項](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li> [illustrator選項](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| AIFF | 音頻/x-aiff |  |  |
| 艾維 | 視頻/x-msvideo |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| BMP | image/bmp |  |  |
| CSS | 文本/css |  |  |
| 文檔 | application/msword |  |  |
| EPS | <ul><li>應用程式/後指令碼</li><li>應用程式/eps</li><li>應用程式/x-eps</li><li>影像/eps</li><li>影像/x-eps</li> |  |  |
| F4V | 視頻/x-f4v |  | ExcludeMasterVideoFromAVS |
| FLA | application/x-shockwave-flash |  |  |
| FLV | video/x-flv |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| FPX | image/vnd.fpx |  |  |
| GIF | image/gif |  |  |
| ICC | application/vnd.iccprofile |  |  |
| ICM | application/vnd.iccprofile |  |  |
| INDD | application/x-indesign |  |  |
| JPEG | image/jpeg |  |  |
| JPG | 影像/jpeg |  |  |
| M2V | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| M4V | 視頻/x-m4v |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MOV | video/quicktime |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MP3 | audio/mpeg |  |  |
| MP4 | video/mp4 |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPEG | 視頻/mpeg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPG | 視頻/mpeg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MTS | model/vnd.mts |  |  |
| OGV | video/ogg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| OTF | 應用程式/x字型 — otf |  |  |
| PDF | application/pdf | `pdfprocess=Rasterize&resolution=150`<br>`&colorspace=Auto&pdfbrochure=false`<br>`&keywords=false&links=false` | [pdf選項](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html) |
| PFB | application/xfont-type1 |  |  |
| PFM | application/xfont-type1 |  |  |
| 皮克 | 影像/x-pict |  |  |
| PNG | image/png |  |  |
| PPT | application/vnd.ms-powerpoint |  |  |
| PS | 應用程式/後指令碼 | `psprocess=Rasterize&psresolution=150`<br>`&pscolorspace=Auto&psalpha=false`<br>`&psextractsearchwords=false`<br>`&aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScript選項](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li>[illustrator選項](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| PSD | image/vnd.adobe.photoshop | `process=None&layerNaming=Layername`<br>`&anchor=Center&createTemplate=false`<br>`&extractText=false&extendLayers=false` | <ul><li>[photoshop選項](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html)</li><li>[photoshopLayer選項](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-layer-options.html)</li></ul> |
| RTF | application/rtf |  |  |
| SVG | image/svg+xml |  |  |
| SWF | 應用/x-shockwave-flash |  |  |
| 塔爾 | application/x-tar |  |  |
| TIF/TIFF | image/tiff |  |  |
| 測控 | 應用程式/xfont-ttf |  |  |
| TTF | 應用程式/xfont-ttf |  |  |
| VOB | 視頻/dvd |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| VTT | 文本/vtt |  |  |
| WAV | audio/x-wav |  |  |
| WEBM | video/webm |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| WMA | audio/x-ms-wma |  |  |
| WMV | video/x-ms-wmv |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| XLS | application/vnd.ms-excel |  |  |
| ZIP | application/zip |  |  |

>[!MORELIKETHIS]
>
>* [啟用基於MIME類型的資產/Dynamic Media Classic上載作業參數支援](/help/sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support)。
>* [配置基於MIME類型的上載作業參數支援](config-dynamic.md)。


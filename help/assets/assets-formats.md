---
title: ' [!DNL Experience Manager] Assets支援的檔案格式'
description: Assets支援的檔案格式和MIME類型清單以及每種格式支援的功能。
contentOwner: AG
feature: Asset Management,Renditions
role: User,Admin
exl-id: ee25fe8f-36fb-42b3-9f90-0ea77bc02e2f
source-git-commit: cc6de21180c9fff74f7d64067db82f0c11ac9333
workflow-type: tm+mt
source-wordcount: '1635'
ht-degree: 9%

---

# [!DNL Adobe Experience Manager Assets]中支援的檔案格式 {#assets-supported-formats}

[!DNL Experience Manager Assets] 支援多種檔案格式，而且每種功能對不同MIME類型的支援各不相同。

若要將[!DNL Assets]與其他符合標準的數位資產管理(DAM)解決方案和案頭軟體整合，請使用Adobe的可擴展元資料平台(XMP)。

使用圖例來了解支援層級。

| 支援層級 | 說明 |
|:---:|---|
| ✓ | 支援 |
| * | 支援附加功能 |
| - | 不適用 |

## 光柵影像格式 {#supported-raster-image-formats}

資產管理功能支援的點陣影像格式如下：

| 格式 | 儲存 | 中繼資料管理 | 中繼資料擷取 | 縮圖產生 | 互動式編輯 | 中繼資料回寫 | 分析 |
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
| PSD **‡** | ✓ | ✓ | ✓ | ✓ |  |  | ✓ |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ |  | ✓ |  |
| PICT |  |  |  |  |  |  | ✓ |
| PSB | ✓ | ✓ | ✓ | ✓ |  |  |  |

**** 從PSD檔案中提取合併的影像。它是由Adobe Photoshop產生並包含在PSD檔案中的影像。 根據設定，合併的影像可能是實際影像，也可能不是實際影像。

Dynamic Media功能支援的點陣影像格式如下：

| 格式 | 上傳<br>（輸入格式） | 建立<br>影像<br>預設集<br>（輸出格式） | 預覽<br> dynamic<br>轉譯 | 傳送<br> dynamic<br>轉譯 | 下載<br> dynamic<br>轉譯 |
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
| PSD **‡** | ✓ |  |  |  |  |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ |
| PICT | ✓ |  |  |  |  |
| PSB |  |  |  |  |  |

**** 從PSD檔案中提取合併的影像。它是由Adobe Photoshop產生並包含在PSD檔案中的影像。 根據設定，合併的影像可能是實際影像，也可能不是實際影像。

除了上述資訊外，請考量下列事項：

* 對EPS檔案的支援僅適用於光柵影像。 例如，預設不支援EPS向量影像的縮圖產生。 要添加支援，請[配置ImageMagick](best-practices-for-imagemagick.md)。 若要整合協力廠商工具以啟用其他功能，請參閱[命令列式媒體處理常式](media-handlers.md#command-line-based-media-handler)。

* 將元資料回寫添加到`NComm`處理程式時，該回寫對PSB檔案格式有效。

* 若要使用Dynamic Media來預覽和生成EPS檔案的動態格式副本，請參閱[Adobe Illustrator(AI)、Postscript(EPS)和PDF檔案格式。](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* 對於EPS檔案， PostScript文檔結構約定(PS-Adobe)3.0版或更新版本支援元資料回寫。

## Dynamic Media不支援的點陣影像格式 {#unsupported-image-formats-dynamic-media}

下列清單說明Dynamic Media支援的點陣影像檔案格式的子類型，這些格式為&#x200B;*not*。

另請參閱[偵測不支援的Dynamic Media](https://helpx.adobe.com/experience-manager/kb/detect-unsupported-assets-for-dynamic-media.html)檔案格式。

* IDAT區塊大小大於100 MB的PNG檔案。
* PSB檔案。
* 不支援使用CMYK、RGB、灰度或點陣圖以外的顏色空間的PSD檔案。 不支援DuoTone、Lab和索引色空間。
* 位深度大於16的PSD檔案。
* 具有浮點資料的TIFF檔案。
* 具有Lab色域的TIFF檔案。

## PDF模擬轉譯器程式庫 {#supported-pdf-rasterizer-library}

Adobe PDF模擬轉譯器程式庫會為大型且內容密集的Adobe Illustrator和PDF檔案產生高品質的縮圖和預覽。 Adobe建議針對下列項目使用PDF模擬轉譯器程式庫：

* 需要大量資源來處理的內容密集型AI/PDF檔案。
* AI/PDF檔案，預設不會產生縮圖。
* AI檔案具有Pantone Matching System(PMS)顏色。

請參閱[使用PDF模擬轉譯器](aem-pdf-rasterizer.md)。

## 影像轉碼程式庫 {#supported-image-transcoding-library}

Adobe影像轉碼程式庫是執行核心影像處理功能（例如編碼、轉碼、重新取樣和調整大小）的影像處理解決方案。

影像轉碼庫支援JPG/JPEG、PNG（8位和16位）、GIF、BMP、TIFF/壓縮TIFF（除了32位TIFF檔案和PTIFF檔案外）、ICO和ICN MIME類型。

請參閱[影像轉碼程式庫](imaging-transcoding-library.md)。

## Camera Raw {#supported-camera-raw}

Adobe Camera Raw程式庫可讓[!DNL Assets]擷取原始影像。 請參閱[Camera Raw支援](camera-raw.md)。

## 檔案格式 {#supported-document-formats}

資產管理功能支援的文檔格式如下：

| 格式 | 儲存 | 元資料<br>管理 | 全文<br>提取 | 中繼資料<br>擷取 | 縮圖<br>生成 | Subasset<br>提取 | 元資料<br>回寫 |
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
| ODS | ✓ | ✓ | ✓ |  |  |  |  |
| PPT | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| ODP | ✓ | ✓ | ✓ |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | ✓ | ✓ |  | ✓ | ✓ | ✓ | ✓ |
| PS | ✓ | ✓ |  |  |  |  |  |
| QXP | ✓ | ✓ |  |  |  |  |  |
| EPUB | ✓ | ✓ |  | ✓ | ✓ |  |  |

Dynamic Media功能支援的檔案格式如下：

| 格式 | 上傳<br>（輸入格式） | 建立<br>影像<br>預設集<br>（輸出格式） | 預覽<br> dynamic<br>轉譯 | 傳送<br> dynamic<br>轉譯 | 下載<br> dynamic<br>轉譯 |
|---|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ |  |  |  |  |
| 檔案 |  |  |  |  |  |
| DOCX |  |  |  |  |  |
| ODT |  |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ |
| HTML |  |  |  |  |  |
| RTF |  |  |  |  |  |
| TXT |  |  |  |  |  |
| XLS |  |  |  |  |  |
| XLSX |  |  |  |  |  |
| ODS |  |  |  |  |  |
| PPT |  |  |  |  |  |
| PPTX |  |  |  |  |  |
| ODP |  |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | ✓ |  |  |  |  |
| PS |  |  |  |  |  |
| QXP |  |  |  |  |  |
| EPUB |  |  |  |  |  |

除了上述功能外，請考量下列事項：

* 若要使用Dynamic Media為PDF檔案產生動態轉譯，請參閱[Adobe Illustrator(AI)、Postscript(EPS)和PDF檔案格式。](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* 若要使用Dynamic Media來預覽和產生AI檔案的動態轉譯，請參閱[Adobe Illustrator(AI)、Postscript(EPS)和PDF檔案格式。](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* 若要使用Dynamic Media為INDD檔案生成動態轉譯，請參閱[InDesign(INDD)檔案格式](../assets/managing-image-presets.md#indesign-indd-file-format)。

## 多媒體格式 {#supported-multimedia-formats}

| 格式 | 儲存 | 中繼資料管理 | 中繼資料擷取 | 縮圖產生 | FFMPEG轉碼 |
|:---|:---:|:---:|:---:|:---:|:---:|
| AAC | ✓ | ✓ |  | - | * |
| MIDI | ✓ | ✓ |  | - | * |
| 3GP | ✓ | ✓ |  | - | * |
| MP3 | ✓ | ✓ | ✓ | - | * |
| MPG | ✓ | ✓ |  | - | * |
| OGA | ✓ | ✓ |  | - | * |
| OGG | ✓ | ✓ |  | - | * |
| RA | ✓ | ✓ |  | - | * |
| WAV | ✓ | ✓ |  | - | * |
| WMA | ✓ | ✓ |  | - | * |
| DVI | ✓ | ✓ |  | * | * |
| FLV | ✓ | ✓ |  | * | * |
| M4V | ✓ | ✓ |  | * | * |
| MPEG | ✓ | ✓ |  | * | * |
| OGV | ✓ | ✓ |  | * | * |
| MOV | ✓ | ✓ |  | * | * |
| WMV | ✓ | ✓ |  | * | * |
| SWF | ✓ | ✓ |  |  |  |

## Dynamic Media轉碼的輸入視訊格式 {#supported-input-video-formats-for-dynamic-media-transcoding}

| 影片副檔名 | 容器 | 建議的視訊轉碼器 | 不支援的視訊轉碼器 |
|---|---|---|---|
| MP4 | MPEG-4 | H264/AVC（所有配置檔案） |  |
| MOV, QT | Apple QuickTime | H264/AVC、Apple ProRes422 &amp; HQ、Sony XDCAM、Sony DVCAM、HDV、Panasonic DVCPro、Apple DV(DV25)、Apple PhotoJPEG、Sorenson、Avid DNxHD、Avid AVR | Apple Meditrate,Apple動畫 |
| FLV、F4V | AdobeFlash | H264/AVC, Flix VP6, H263, Sorenson | SWF（向量動畫檔案） |
| WMV | Windows Media 9 | WMV3(v9)、WMV2(v8)、WMV1(v7)、GoToMeeting(G2M2、G2M3、G2M4) | Microsoft螢幕(MSS2)、Microsoft照片(WVP2) |
| MPG、VOB、M2V、MP2 | MPEG-2 | MPEG-2 |  |
| M4V | Apple iTunes | H264/AVC |  |
| AVI | A/V插播 | XVID、DIVX、HDV、MiniDV(DV25)、Techsmith Camtasia、Huffyuv、Fraps、Panasonic DVCPro | Indeo3(IV30)、MJPEG、Microsoft Video 1(MS-CRAM) |
| WebM | WebM | Google VP8 |  |
| 奧格夫、奧格 | 奧格 | 蒂奧拉，VP3，狄拉克 |  |
| MXF | MXF | Sony XDCAM、MPEG-2、MPEG-4、松下DVCPro |  |
| MTS | AVCHD | H264/AVC |  |
| MKV | 馬特羅斯卡 | H264/AVC |  |
| R3D、RM | 紅色原始視頻 | MJPEG 2000 |  |
| RAM、RM | RealVideo | 不支援 | Real G2(RV20)、Real 8(RV30)、Real 10(RV40) |
| FLAC | 原生片段 | 免費無損音頻編解碼器 |  |
| MJ2 | 動作JPEG 2000 | 運動JPEG 2000編解碼器 |  |

## 封存格式 {#supported-archive-formats}

下表說明支援的封存格式和通用DAM工作流程的適用性。

| 格式 | 儲存 | 版本設定 | 工作流程 | 發佈 | 存取控制 | Dynamic Media傳送 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| TGZ | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| JAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| RAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| TAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| ZIP **†** | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |

**†** 從PSD檔案中提取合併的影像。它是由Adobe Photoshop產生並包含在PSD檔案中的影像。 根據設定，合併的影像可能是實際影像，也可能不是實際影像。 使用`Deflate64`演算法建立的ZIP封存檔在AEM中的支援有限。 不支援存檔和取消存檔操作。 不過，上傳、瀏覽和下載等操作均受支援。

## 其他支援的格式 {#other-supported-formats}

下表說明常見DAM工作流程對其他幾種檔案格式的適用性。

| 格式 | 儲存 | 版本設定 | 工作流程 | 發佈 | 存取控制 | Dynamic Media傳送 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| **#** | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| SVG | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| CSS | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| VTT | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| XML | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| JavaScript（若已設定自己的傳送網域） |  |  |  |  |  | ✓ |

**#** DAM支援其他格式，用於儲存、版本設定、ACL、工作流程、發佈和中繼資料管理。

## 支援的MIME類型 {#supported-mime-types}

預設情況下， [!DNL Experience Manager]會使用副檔名檢測檔案類型。 [!DNL Experience Manager] 可從檔案的內容中偵測。對於後者，在[!DNL Experience Manager] Web控制台的[!UICONTROL Day CQ DAM Mime Type Service]中，選取[!UICONTROL 從內容]檢測MIME選項。

支援的MIME類型清單可在`/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`的CRXDE Lite中取得。

| 副檔名 | MIME類型/ Internet媒體類型 | 預設jobParam值 | 允許的jobParam值 |
|---|---|---|---|
| 影像 | image/s7asset | `usmAmount=1.75&usmRadius=0.2`<br>`&usmThreshold=2&usmMonochrome=0&` | 預設的jobParam會套用至所有影像mime類型資產。<ul><li>[trunkdownBackgroundOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-knockout-background-options.html)</li><li>[manualCropOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-manual-crop-options.html)</li><li>[autoColorCropOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-color-crop-options.html)</li><li>[autoTransparentCropOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-transparent-crop-options.html)</li><li>[colorManagementOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-color-management-options.html)</li><li>[autoSetCreationOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-set-creation-options.html)</li><li>[emailSetting](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/sting-constants/r-email-settings.html)</li><li>[xmpKeywords](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-xmp-keywords.html)</li><li>[unsharpMaskOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-unsharp-mask-options.html)</li></ul> |
| 3G2 | video/3gpp2 |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| 3GP | video/3gpp |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| AAC | audio/x-aac |  |  |
| AFM | application/x-font-type1 |  |  |
| AI | application/postscript | `aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li> [illustratorOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| AIFF | audio/x-aiff |  |  |
| AVI | video/x-msvideo |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| BMP | image/bmp |  |  |
| CSS | text/css |  |  |
| 檔案 | application/msword |  |  |
| EPS | <ul><li>application/postscript</li><li>應用程式/eps</li><li>application/x-eps</li><li>影像/eps</li><li>image/x-eps</li> |  |  |
| F4V | video/x-f4v |  | ExcludeMasterVideoFromAVS |
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
| M4V | video/x-m4v |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MOV | video/quicktime |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MP3 | audio/mpeg |  |  |
| MP4 | video/mp4 |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPEG | 視頻/mpeg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPG | 視頻/mpeg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MTS | model/vnd.mts |  |  |
| OGV | video/ogg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| OTF | application/x-font-otf |  |  |
| PDF | application/pdf | `pdfprocess=Rasterize&resolution=150`<br>`&colorspace=Auto&pdfbrochure=false`<br>`&keywords=false&links=false` | [pdfOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html) |
| PFB | application/x-font-type1 |  |  |
| PFM | application/x-font-type1 |  |  |
| PICT | image/x-pict |  |  |
| PNG | image/png |  |  |
| PPT | application/vnd.ms-powerpoint |  |  |
| PS | application/postscript | `psprocess=Rasterize&psresolution=150`<br>`&pscolorspace=Auto&psalpha=false`<br>`&psextractsearchwords=false`<br>`&aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li>[illustratorOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| PSD | image/vnd.adobe.photoshop | `process=None&layerNaming=Layername`<br>`&anchor=Center&createTemplate=false`<br>`&extractText=false&extendLayers=false` | <ul><li>[photoshopOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html)</li><li>[photoshopLayerOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-layer-options.html)</li></ul> |
| RTF | application/rtf |  |  |
| SVG | image/svg+xml |  |  |
| SWF | application/x-shockwave-flash |  |  |
| TAR | application/x-tar |  |  |
| TIF / TIFF | image/tiff |  |  |
| TTC | application/x-font-ttf |  |  |
| RTF | application/x-font-ttf |  |  |
| VOB | 視頻/dvd |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| VTT | text/vtt |  |  |
| WAV | audio/x-wav |  |  |
| WEBM | video/webm |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| WMA | audio/x-ms-wma |  |  |
| WMV | video/x-ms-wmv |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| XLS | application/vnd.ms-excel |  |  |
| ZIP | application/zip |  |  |

>[!MORELIKETHIS]
>
>* [啟用MIME類型型Assets/Dynamic Media Classic上傳工作參數支援](/help/sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support)。
>* [設定MIME類型，以支援上傳工作參數](config-dynamic.md)。


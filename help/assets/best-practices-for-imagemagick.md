---
title: 安裝並設定ImageMagick以搭配AEM Assets運作
description: 瞭解ImageMagick軟體、如何安裝、設定命令列處理步驟，以及使用它編輯、合成和產生影像縮圖。
contentOwner: AG
translation-type: tm+mt
source-git-commit: af5f8a24db589ecdbe28d603ab9583f11d29212c
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 0%

---


# 安裝並設定ImageMagick以搭配AEM Assets {#install-and-configure-imagemagick-to-work-with-aem-assets}運作

ImageMagick是建立、編輯、合成或轉換點陣圖影像的軟體外掛程式。 它可以讀取和寫入多種格式（超過200種）的影像，包括PNG、JPEG、JPEG-2000、GIF、TIFF、DPX、EXR、WebP、Postscript、PDF和SVG。 使用ImageMagick來調整影像大小、反向、鏡像、旋轉、扭曲、切變和變形。 您也可以使用ImageMagick調整影像顏色、套用各種特效，或繪製文字、線條、多邊形、橢圓和曲線。

從命令列使用Adobe Experience Manager(AEM)媒體處理常式，透過ImageMagick處理影像。 要使用ImageMagick使用各種檔案格式，請參閱[Assets檔案格式最佳實踐](assets-file-format-best-practices.md)。 若要瞭解所有支援的檔案格式，請參閱[Assets supported formats](assets-formats.md)。

要使用ImageMagick處理大型檔案，請考慮記憶體要求高於通常要求、IM策略需要的潛在更改以及對效能的整體影響。 記憶體需求取決於各種因素，例如解析度、位元深度、色彩描述檔和檔案格式。 如果您想要使用ImageMagick處理非常大的檔案，請正確對AEM伺服器進行基準測試。 最後提供了一些有用的資源。

>[!NOTE]
>
>如果您在Adobe Managed Services(AMS)上使用AEM，如果您打算處理大量大型PSD或PSB檔案，請聯絡Adobe客戶服務。 Experience Manager可能無法處理超過30000 x 23000像素的高解析度PSB檔案。

## 安裝ImageMagick {#installing-imagemagick}

多種版本的ImageMagic安裝檔案可用於各種作業系統。 請針對您的作業系統使用適當的版本。

1. 下載適合您作業系統的[ImageMagick安裝檔案](https://www.imagemagick.org/script/download.php)。
1. 若要在AEM伺服器所在磁碟上安裝ImageMagick，請啟動安裝檔案。

1. 將路徑環境變數設定為ImageMagic安裝目錄。
1. 要檢查安裝是否成功，請執行`identify -version`命令。

## 設定命令行進程步驟{#set-up-the-command-line-process-step}

您可以為特定使用案例設定命令行處理步驟。 每次在AEM伺服器上新增JPEG影像檔案至`/content/dam`時，請執行下列步驟以產生翻轉的影像和縮圖（140x100、48x48、319x319和1280x1280）:

1. 在AEM伺服器上，前往「工作流程」主控台(`https://[aem_server]:[Port]/workflow`)並開啟「DAM更新資產」工作流程模型。****
1. 從&#x200B;**[!UICONTROL DAM Update Asset]**&#x200B;工作流模型中，開啟&#x200B;**[!UICONTROL EPS縮圖（由ImageMagick提供）]**&#x200B;步驟。
1. 在&#x200B;**[!UICONTROL 參數頁籤]**&#x200B;中，將`image/jpeg`添加到&#x200B;**[!UICONTROL Mime類型]**&#x200B;清單中。

   ![mime_types_jpeg](assets/mime_types_jpeg.png)

1. 在&#x200B;**[!UICONTROL Commands]**&#x200B;框中，輸入以下命令：

   `convert ./${filename} -flip ./${basename}.flipped.jpg`

1. 選擇&#x200B;**[!UICONTROL 刪除生成的格式副本]**&#x200B;和&#x200B;**[!UICONTROL 生成Web格式副本]**&#x200B;標誌。

   ![select_flags](assets/select_flags.png)

1. 在「**[!UICONTROL 啟用Web的影像]**」標籤中，指定尺寸為1280x1280像素的轉譯詳細資訊。 此外，在&#x200B;**[!UICONTROL Mimetype]**&#x200B;方塊中指定i *mage/jpeg*。

   ![web_enabled_image](assets/web_enabled_image.png)

1. 點選／按一下&#x200B;**[!UICONTROL OK]**&#x200B;以儲存變更。

   >[!NOTE]
   >
   >`convert`命令可能無法與某些Windows版本（例如Windows SE）一起運行，因為它與Windows安裝中的本機`convert`實用程式衝突。 在這種情況下，請提及ImageMagick實用程式的完整路徑。 例如，指定
   >
   >`"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ./${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`

1. 開啟「處理縮圖&#x200B;**[!UICONTROL 」步驟，並在「略過Mime類型`image/jpeg`」下新增MIME類型]**。****

   ![skip_mime_types](assets/skip_mime_types.png)

1. 在&#x200B;**[!UICONTROL 啟用Web的映像]**&#x200B;頁籤中，在&#x200B;**[!UICONTROL 跳過清單]**&#x200B;下添加MIME類型`image/jpeg`。 點選／按一下&#x200B;**[!UICONTROL OK]**&#x200B;以儲存變更。

   ![web_enabled](assets/web_enabled.png)

1. 儲存工作流程。
1. 若要檢查ImageMagic是否能正確處理影像，請將JPG影像上傳至AEM Assets。 驗證是否為翻轉的影像和轉譯生成。

## 降低安全性弱點{#mitigating-security-vulnerabilities}

使用ImageMagick處理映像時存在多個安全漏洞。 例如，處理使用者提交的影像時，有遠端程式碼執行(RCE)的風險。

此外，各種影像處理外掛程式都依賴ImageMagick程式庫，包括但不限於PHP的影像快取、Ruby的快取和回形針，以及Node.js的影像快取。

如果您使用ImageMagick或受影響的程式庫，Adobe建議您至少執行下列其中一項工作（但最好同時執行兩項），以緩解已知的弱點：

1. 在將所有影像檔案傳送至ImageMagick進行處理之前，請先確認所有影像檔案的開頭皆為預期的[&quot;magic bytes&quot;](https://en.wikipedia.org/wiki/List_of_file_signatures)，並對應您支援的影像檔案類型。
1. 使用策略檔案禁用易受攻擊的ImageMagick編碼器。 ImageMagick的全局策略位於`/etc/ImageMagick`。

>[!MORELIKETHIS]
>
>* [使用AEM Assets處理各種檔案格式的最佳範例](assets-file-format-best-practices.md)
>* [ImageMagick的命令列選項](https://www.imagemagick.org/script/command-line-options.php)
>* [ImageMagick使用的基本和進階範例](https://www.imagemagick.org/Usage/)
>* [ImageMagick的資產效能調整](performance-tuning-guidelines.md)
>* [AEM Assets支援的檔案格式完整清單](assets-formats.md)
>* [瞭解檔案格式和影像的記憶體成本](https://www.scantips.com/basics1d.html)


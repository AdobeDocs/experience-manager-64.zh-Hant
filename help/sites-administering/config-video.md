---
title: 設定視訊元件
seo-title: Configure the Video component
description: 了解如何設定視訊元件。
seo-description: Learn how to configure the Video Component.
uuid: f4755a13-08ea-4096-a951-46a590f8d766
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: a1efef3c-0e4b-4a17-bcad-e3cc17adbbf7
exl-id: 46d0765d-fb77-4332-8fbb-5bd2abcd6806
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 1%

---

# 設定視訊元件 {#configure-the-video-component}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

此 [視訊元件](/help/sites-authoring/default-components-foundation.md#video) 可讓您將預先定義的OOTB（現成）影片元素放在頁面上。

若要正確轉碼，您的管理員必須 [安裝FFmpeg並配置AEM](#install-ffmpeg) 分開。 它們也可以 [設定您的視訊設定檔](#configure-video-profiles) 用於HTML5元素。

>[!CAUTION]
>
>若不進行廣泛的專案層級自訂，此元件將不再可立即運作。

## 設定視訊設定檔 {#configure-video-profiles}

您可能想要定義要用於HTML5元素的視訊描述檔。 此處選擇的依序使用。 若要存取，請使用 [設計模式](/help/sites-authoring/default-components-designmode.md) （僅限傳統UI），並選取 **[!UICONTROL 設定檔]** 標籤：

![chlimage_1-317](assets/chlimage_1-317.png)

您也可以為 [!UICONTROL 播放], [!UICONTROL Flash]，和 [!UICONTROL 進階].

## 安裝FFmpeg並配置AEM {#install-ffmpeg}

視訊元件需仰賴協力廠商的開放原始碼產品FFmpeg，才能正確轉碼可從下載的視訊 [https://ffmpeg.org/](https://ffmpeg.org/). 安裝FFmpeg後，必須配置AEM以使用特定的音頻編解碼器和特定的運行時選項。

**為您的平台安裝FFmpeg**:

* **在Windows上：**

   1. 將編譯的二進位檔下載為 `ffmpeg.zip`
   1. 解壓縮至資料夾。
   1. 設定系統環境變數 `PATH` to `<*your-ffmpeg-locatio*n>\bin`
   1. 重新啟動AEM。

* **在Mac OS X上：**

   1. 安裝Xcode([https://developer.apple.com/technologies/tools/xcode.html](https://developer.apple.com/technologies/tools/xcode.html))
   1. 安裝XQuartz/X11。
   1. 安裝MacPort([https://www.macports.org/](https://www.macports.org/))
   1. 在主控台中，執行下列命令並遵循指示：

      `sudo port install ffmpeg`

      `FFmpeg` 必須在 `PATH` AEM可以通過命令列來擷取。

* **使用OS X 10.6的預編譯版本：**

   1. 下載預編譯版本。
   1. 將其提取至 `/usr/local` 目錄。
   1. 從終端，執行：

      `sudo ln -s /usr/local/Cellar/ffmpeg/0.6/bin/ffmpeg /usr/bin/ffmpeg`

**設定AEM**:

1. 開啟 [!UICONTROL CRXDE Lite] 在網頁瀏覽器中。 ([http://localhost:4502/crx/de](http://localhost:4502/crx/de))
1. 選取 `/libs/settings/dam/video/format_aac/jcr:content` 節點，並確保節點屬性如下：

   * audioCodec:

      ```
       aac
      ```

   * customArgs:

      ```
       -flags +loop -me_method umh -g 250 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -b_strategy 1 -i_qfactor 0.71 -cmp chroma -subq 8 -me_range 16 -coder 1 -sc_threshold 40 -b-pyramid normal -wpredp 2 -mixed-refs 1 -8x8dct 1 -fast-pskip 1 -keyint_min 25 -refs 4 -trellis 1 -direct-pred 3 -partitions i8x8,i4x4,p8x8,b8x8
      ```

1. 若要自訂設定，請在中建立覆蓋 `/apps/settings/` 節點，並在 `/conf/global/settings/` 節點。 無法在中編輯 `/libs` 節點。 例如，若要覆蓋路徑 `/libs/settings/dam/video/fullhd-bp`，在建立 `/conf/global/settings/dam/video/fullhd-bp`.

   >[!NOTE]
   >
   >覆蓋並編輯整個設定檔節點，而不只是需要修改的屬性。 這類資源不會透過SlingResourceMerger解決。

1. 如果您變更了其中一個屬性，請按一下 **[!UICONTROL 全部儲存]**.

>[!NOTE]
>
>升級AEM執行個體時，不會保留OOTB工作流程模型。 Adobe建議您先複製OOTB工作流程模型，再加以編輯。 例如，在DAM更新資產模型中編輯FFmpeg轉碼步驟之前，請先複製OOTB DAM更新資產模型，以擷取升級前已存在的視訊設定檔名稱。 接著，您可以覆蓋 `/apps` 節點，讓AEM擷取對OOTB模型的自訂變更。

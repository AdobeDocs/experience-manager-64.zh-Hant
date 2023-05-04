---
title: Camera Raw支援
description: 了解如何在Adobe Experience Manager Assets中啟用Camera Raw支援。
contentOwner: AG
feature: Developer Tools
role: Admin
exl-id: 637c57ae-55a6-4032-9821-b55839b3e567
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 3%

---

# 使用Camera Raw處理影像 {#camera-raw-support}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

您可以啟用Camera Raw支援以處理原始檔案格式（如CR2、NEF和RAF），並以JPEG格式呈現影像。 Adobe Experience Manager Assets支援此功能，使用 [Camera Raw套件](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) 可從Software Distribution取得。

>[!NOTE]
>
>功能僅支援JPEG轉譯。 Windows 64位元、Mac OS和RHEL 7.x均支援此功能。

若要在Adobe Experience Manager Assets中啟用Camera Raw支援，請遵循下列步驟：

1. 下載 [Camera Raw套件](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) 從Software Distribution取得。

1. 存取 `https://[aem_server]:[port]/workflow`. 開啟 **[!UICONTROL DAM更新資產]** 工作流程。

1. 開啟 **[!UICONTROL 處理縮圖]** 步驟。

1. 在 **[!UICONTROL 縮圖]** 標籤：

   * **[!UICONTROL 縮圖]**: `140:100:false, 48:48:false, 319:319:false`
   * **[!UICONTROL 略過 Mime 類型]**: `skip:image/dng, skip:image/x-raw-(.*)`

   ![奇利馬奇](assets/chlimage_1-334.png)

1. 在 **[!UICONTROL 啟用Web的映像]** 標籤中 **[!UICONTROL 略過清單]** 欄位，指定 `audio/mpeg, video/(.*), image/dng, image/x-raw-(.*)`.

   ![奇利馬奇](assets/chlimage_1-335.png)

1. 從側面板，新增 **[!UICONTROL Camera Raw/DNG處理常式]** 在 **[!UICONTROL 縮圖建立]** 步驟。

1. 在 **[!UICONTROL Camera Raw/DNG處理常式]** 步驟，在 **[!UICONTROL 引數]** 標籤：

   * **[!UICONTROL Mime類型]**: `image/dng` 和 `image/x-raw-(.*)`
   * **[!UICONTROL 命令]**:

      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.web.1280.1280.jpeg 1280 1280`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.319.319.jpeg 319 319`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.140.100.jpeg 140 100`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.48.48.jpeg 48 48`

   ![chlimage_1-336](assets/chlimage_1-336.png)

1. 按一下「**[!UICONTROL 儲存]**」。

>[!NOTE]
>
>請確定上述設定與 **[!UICONTROL 使用Camera Raw和DNG處理步驟更新資產範例]** 設定。

您現在可以將相機原始檔案匯入 [!DNL Experience Manager] 資產。 安裝Camera Raw套件並設定所需的工作流程後， **[!UICONTROL 影像調整]** 選項。

![chlimage_1-337](assets/chlimage_1-337.png)

*圖：側窗格中的選項*

![chlimage_1-338](assets/chlimage_1-338.png)

*圖：使用選項對影像進行輕量型編輯*

將編輯項目儲存至Camera Raw影像後，會顯示新的轉譯 `AdjustedPreview.jpg` 會為影像產生。 對於除Camera Raw之外的其他影像類型，變更會反映在所有轉譯中。

## 最佳實務、已知問題和限制 {#best-practices}

功能有下列限制：

* 功能僅支援JPEG轉譯。 Windows 64位元、Mac OS和RHEL 7.x均支援此功能。
* RAW和DNG格式不支援中繼資料回寫。
* Camera Raw程式庫對一次可處理的總像素有限制。 目前，無論先遇到什麼條件，最多都可以處理65000個檔案長邊的像素，或512 MP。

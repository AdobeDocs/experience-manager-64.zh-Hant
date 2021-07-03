---
title: Camera Raw支援
description: 了解如何在Adobe Experience Manager Assets中啟用Camera Raw支援。
contentOwner: AG
feature: 開發人員工具
role: Admin
exl-id: 637c57ae-55a6-4032-9821-b55839b3e567
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 1%

---

# 使用Camera Raw處理影像 {#camera-raw-support}

您可以啟用Camera Raw支援以處理原始檔案格式（如CR2、NEF和RAF），並以JPEG格式呈現影像。 Adobe Experience Manager Assets支援使用Software Distribution提供的[Camera Raw套件](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg)來執行功能。

>[!NOTE]
>
>此功能僅支援JPEG轉譯。 Windows 64位元、Mac OS和RHEL 7.x均支援此功能。

若要在Adobe Experience Manager Assets中啟用Camera Raw支援，請遵循下列步驟：

1. 從Software Distribution下載[Camera Raw套件](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg)。

1. 存取 `https://[aem_server]:[port]/workflow`. 開啟&#x200B;**[!UICONTROL DAM更新資產]**&#x200B;工作流程。

1. 開啟「處理縮圖&#x200B;]**」步驟。**[!UICONTROL 

1. 在&#x200B;**[!UICONTROL 縮圖]**&#x200B;標籤中提供下列配置：

   * **[!UICONTROL 縮圖]**:  `140:100:false, 48:48:false, 319:319:false`
   * **[!UICONTROL 略過 Mime 類型]**: `skip:image/dng, skip:image/x-raw-(.*)`

   ![奇利馬奇](assets/chlimage_1-334.png)

1. 在&#x200B;**[!UICONTROL Web Enabled Image]**&#x200B;頁簽的&#x200B;**[!UICONTROL Skip List]**&#x200B;欄位中，指定`audio/mpeg, video/(.*), image/dng, image/x-raw-(.*)`。

   ![奇利馬奇](assets/chlimage_1-335.png)

1. 從側面板，在&#x200B;**[!UICONTROL 縮圖建立]**&#x200B;步驟下方新增&#x200B;**[!UICONTROL Camera Raw/DNG處理常式]**&#x200B;步驟。

1. 在&#x200B;**[!UICONTROL Camera Raw/DNG處理常式]**&#x200B;步驟中，在&#x200B;**[!UICONTROL Arguments]**&#x200B;標籤中新增下列設定：

   * **[!UICONTROL Mime類型]**: `image/dng` 和  `image/x-raw-(.*)`
   * **[!UICONTROL 命令]**:

      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.web.1280.1280.jpeg 1280 1280`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.319.319.jpeg 319 319`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.140.100.jpeg 140 100`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.48.48.jpeg 48 48`

   ![chlimage_1-336](assets/chlimage_1-336.png)

1. 按一下「**[!UICONTROL 儲存]**」。

>[!NOTE]
>
>請確定上述設定與&#x200B;**[!UICONTROL 使用Camera Raw和DNG處理步驟]**&#x200B;設定的範例DAM更新資產相同。

您現在可以將相機原始檔案匯入AEM Assets。 安裝Camera Raw包並配置所需的工作流後，側窗格清單中將顯示&#x200B;**[!UICONTROL Image Adjust]**&#x200B;選項。

![chlimage_1-337](assets/chlimage_1-337.png)

*圖：側窗格中的選項*

![chlimage_1-338](assets/chlimage_1-338.png)

*圖：使用選項對影像進行輕量型編輯*

儲存對Camera Raw影像的編輯後，會為該影像產生新的轉譯`AdjustedPreview.jpg`。 對於除Camera Raw之外的其他影像類型，變更會反映在所有轉譯中。

## 最佳實務、已知問題和限制 {#best-practices}

功能有下列限制：

* 此功能僅支援JPEG轉譯。 Windows 64位元、Mac OS和RHEL 7.x均支援此功能。
* RAW和DNG格式不支援中繼資料回寫。
* Camera Raw程式庫對一次可處理的總像素有限制。 目前，無論先遇到什麼條件，最多都可以處理65000個檔案長邊的像素，或512 MP。

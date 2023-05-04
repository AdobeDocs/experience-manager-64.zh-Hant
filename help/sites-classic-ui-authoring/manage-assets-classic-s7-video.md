---
title: 影片
description: Assets提供集中的視訊資產管理功能，您可以直接將視訊上傳至Assets，以自動編碼至Scene7，並直接從Assets存取Scene7視訊，以進行頁面編寫。
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
exl-id: 7cb3d58c-0d78-4414-9b66-0a10e52d0906
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1719'
ht-degree: 1%

---

# 影片{#video}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Assets提供集中的視訊資產管理功能，您可以直接將視訊上傳至Assets，以自動編碼至Dynamic Media Classic，並直接從Assets存取Dynamic Media Classic視訊，以進行頁面編寫。

Dynamic Media Classic視訊整合將最佳化視訊的觸角延伸至所有畫面（自動裝置和頻寬偵測）。

* Dynamic Media Classic(Scene7)視訊元件會自動執行裝置和頻寬偵測，以在桌上型電腦、平板電腦和行動裝置上播放適當的格式和適當品質的視訊。
* 資產 — 您可以包含最適化視訊集，而非僅包含單一視訊資產。 最適化視訊集是容器，可供在多個畫面間順暢播放視訊所需的所有視訊轉譯使用。 適用性視訊集將以不同位速率和格式（如400 kbps、800 kbps和1000 kbps）編碼的相同視訊的版本分組。 您可使用最適化視訊集以及S7視訊元件，在多個畫面(包括桌上型電腦、iOS、Android、Blackberry和Windows行動裝置)間進行最適化視訊串流。 請參閱 [Scene7檔案中的適用性視訊集以取得詳細資訊](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/application-setup.html#video-presets-for-encoding-video-files).

## 關於FFMPEG和Dynamic Media Classic {#about-ffmpeg-and-scene}

預設的視訊編碼程式是使用以FFMPEG為基礎的與視訊設定檔的整合為基礎。 因此，現成可用的DAM更新資產工作流程包含以下兩個以ffmpeg為基礎的工作流程步驟：

* FFMPEG縮圖
* FFMPEG編碼

請注意，啟用和設定Dynamic Media Classic整合不會從現成可用的DAM更新資產擷取工作流程自動移除或停用這兩個工作流程步驟。 如果您已在AEM中使用FFMPEG型視訊編碼，則您的製作環境很可能已安裝FFMPEG。 在此情況下，使用Assets擷取的新視訊會編碼兩次：一次來自FFMPEG編碼器，一次來自Dynamic Media Classic整合。

如果您已設定AEM中的FFMPEG型視訊編碼並安裝FFMPEG,Adobe建議您從DAM更新資產工作流程中移除兩個FFMPEG工作流程。

### 支援的格式 {#supported-formats}

Dynamic Media Classic視訊元件支援下列格式：

* F4V H.264
* MP4 H.264

### 決定要將視訊上傳到何處 {#deciding-where-to-upload-your-video}

決定要將視訊資產上傳至何處取決於下列項目：

* 您是否需要視訊資產的工作流程？
* 您是否需要視訊資產的版本控制？

如果這兩個問題的答案皆為「是」，請直接將影片上傳至AdobeDAM。 如果兩個問題的答案都是「否」，請直接將影片上傳至Dynamic Media Classic。 以下章節將說明每個案例的工作流程。

#### 如果您要直接上傳影片至Adobe資產 {#if-you-are-uploading-your-video-directly-to-adobe-assets}

如果您的資產需要工作流程或版本設定，應先上傳至Adobe資產。 建議的工作流程如下：

1. 上傳視訊資產以Adobe資產，並自動編碼及發佈至Dynamic Media Classic。
1. 在AEM中，存取WCM中的視訊資產，位於 **[!UICONTROL 電影]** 標籤。
1. 使用Dynamic Media Classic影片或Foundation影片元件製作。

#### 如果您要上傳影片至Dynamic Media Classic {#if-you-are-uploading-your-video-to-scene}

如果您的資產不需要工作流程或版本設定，應將資產上傳至Dynamic Media Classic。 建議的工作流程如下：

1. 在Dynamic Media Classic, [設定排程的FTP上傳和編碼至Dynamic Media Classic（系統自動化）](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/uploading-files.html#uploading-your-files).
1. 在AEM中，存取WCM中的視訊資產，位於 **[!UICONTROL Dynamic Media Classic]** 標籤。
1. 使用Dynamic Media Classic影片元件製作。

### 設定與Dynamic Media Classic影片的整合 {#configuring-integration-with-scene-video}

**配置通用預設集**:

1. 在 **[!UICONTROL Cloud Services]**，導覽至 **[!UICONTROL Dynamic Media Classic]** 設定，按一下 **[!UICONTROL 編輯]**.
1. 選取 **[!UICONTROL 影片]** 標籤。

   >[!NOTE]
   >
   >此 **[!UICONTROL 影片]** 如果頁面沒有雲端設定，則不會顯示索引標籤。 請參閱 [為WCM啟用Dynamic Media Classic](#enablingscene7forwcm).

1. 選取最適化視訊編碼設定檔、現成可用的單一視訊編碼設定檔，或自訂視訊編碼設定檔。

   >[!NOTE]
   >
   >如需視訊預設集含義的詳細資訊，請參閱 [Dynamic Media Classic檔案](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/application-setup.html#video-presets-for-encoding-video-files).
   >
   >Adobe建議您在設定通用預設集時同時選取兩個最適化視訊集，或選取 **[!UICONTROL 最適化視訊編碼]** 選項。

1. 選取的編碼設定檔會自動套用至您為此Dynamic Media Classic雲端設定所設定的CQ DAM Target資料夾。 您可以使用不同的目標資料夾來設定多個Dynamic Media Classic雲端設定，以視需要套用不同的編碼設定檔。

### 更新檢視器和編碼預設集 {#updating-viewer-and-encoding-presets}

如果您因為預設集已在Dynamic Media Classic中更新，而需要更新AEM中視訊的檢視器和編碼預設集，請導覽至雲端設定中的Dynamic Media Classic設定，然後按一下 **更新檢視器和編碼預設集**.

![chlimage_1-131](assets/chlimage_1-131.png)

### 上傳主視訊 {#uploading-your-master-video}

若要從AdobeDAM上傳主視訊至Dynamic Media Classic:

1. 導覽至CQ DAM Target資料夾，您已在該資料夾中使用Dynamic Media Classic編碼設定檔設定雲端設定。
1. 按一下 **[!UICONTROL 上傳]** 上傳主視訊。 視訊上傳和編碼在 [!UICONTROL DAM更新資產] 工作流程已完成， **[!UICONTROL 發佈至Dynamic Media Classic]** 已勾選。

   >[!NOTE]
   >
   >可能需要一些時間才能產生視訊縮圖。

   將DAM主視訊拖曳至視訊元件存取中 *all* 以傳送的Dynamic Media Classic編碼Proxy轉譯。

### Foundation視訊元件與Dynamic Media Classic視訊元件 {#foundation-video-component-versus-scene-video-component}

使用AEM時，您可以同時存取Sites和Dynamic Media Classic(Scene7)視訊元件中可用的視訊元件。 這些元件不可互換。

Dynamic Media Classic視訊元件只適用於Dynamic Media Classic視訊。 基礎元件可處理從AEM（使用ffmpeg）和Dynamic Media Classic影片儲存的影片。

下列矩陣說明何時應使用哪個元件：

![chlimage_1-132](assets/chlimage_1-132.png)

>[!NOTE]
>
>Dynamic Media Classic視訊元件立即可用，使用通用視訊設定檔。 不過，您可以取得HTML5型視訊播放器，以供AEM使用。 在Dynamic Media Classic中，複製現成可用的HTML5視訊播放器的內嵌程式碼，並將其放入您的AEM頁面。

## AEM視訊元件 {#aem-video-component}

即使建議使用Dynamic Media Classic視訊元件來檢視Dynamic Media Classic視訊，本節仍說明如何搭配使用Dynamic Media Classic視訊 [!UICONTROL Foundation視訊元件] 在AEM中，為了完整性。

### AEM影片和Dynamic Media Classic影片比較 {#aem-video-and-scene-video-comparison}

下表提供AEM Foundation Video元件與Scene7 Video元件之間所支援功能的高階比較：

|  | AEM Foundation影片 | Dynamic Media Classic影片 |
|---|---|---|
| 方法 | HTML5第一種方法。 Flash僅用於非HTML5後援。 | Flash在大多數案頭上。 HTML5用於行動裝置和平板電腦。 |
| 傳送 | 漸進式 | 最適化串流 |
| 追蹤 | 是 | 是 |
| 擴充性 | 是 | 是(含Dynamic Media Classic檢視器SDK) |
| 行動視訊 | 是 | 是 |

### 設定 {#setting-up}

#### 建立視訊設定檔 {#creating-video-profiles}

系統會根據Dynamic Media Classic雲端設定中選取的Dynamic Media Classic編碼預設集，建立各種視訊編碼。 為了讓基礎視訊元件能夠加以運用，必須為選取的每個Dynamic Media Classic編碼預設集建立視訊設定檔。 這可讓視訊元件據以選取DAM轉譯。

>[!NOTE]
>
>必須啟動新視訊設定檔及其變更才能發佈。

1. 在AEM中，前往 **[!UICONTROL 工具]**，然後選取 **[!UICONTROL 配置控制台]**. 在設定控制台中，導覽至 **[!UICONTROL 工具]** > **[!UICONTROL 資產]** > **[!UICONTROL 視訊設定檔]** 在導航樹中。
1. 建立新的Dynamic Media Classic影片設定檔。 在 **[!UICONTROL 新……]** 菜單，選擇 **[!UICONTROL 建立頁面]** 然後選取「Dynamic Media Classic視訊描述檔」範本。 為新視訊描述檔頁面命名，然後按一下 **[!UICONTROL 建立]**.

   ![chlimage_1-133](assets/chlimage_1-133.png)

1. 編輯新的視訊設定檔。 先選取雲端設定。 然後選取與雲端設定中選取的編碼預設集相同。

   ![chlimage_1-134](assets/chlimage_1-134.png)

   | 屬性 | 說明 |
   |---|---|
   | Dynamic Media Classic(Scene7)雲端設定 | 用於編碼預設集的雲端設定。 |
   | Dynamic Media Classic(Scene7)編碼預設集 | 用來對應此視訊設定檔的編碼預設集。 |
   | HTML5 視訊類型 | 此屬性可設定HTML5視訊來源元素的type屬性值。 Dynamic Media Classic編碼預設集未提供此資訊，但使用HTML5視訊元素正確轉譯視訊時需要此資訊。 提供了常用格式的清單，但可以覆蓋其他格式。 |

   對您要在視訊元件中使用的雲端設定中選取的所有編碼預設集，重複此步驟。

#### 配置設計 {#configuring-design}

基礎視訊元件必須知道要使用哪些視訊設定檔，才能建立視訊來源清單。 您必須開啟視訊元件設計對話方塊，並設定使用新視訊設定檔的元件設計。

>[!NOTE]
>
>如果您在行動頁面上使用基礎視訊元件，則可能需要在行動頁面的設計上重複這些步驟。

>[!NOTE]
>
>對設計所做的變更需要啟動設計，才能對發佈生效。

1. 開啟foundation視訊元件的設計對話方塊，並變更為 **[!UICONTROL 設定檔]** 標籤。 然後刪除現成可用的設定檔，並新增新的Dynamic Media Classic視訊設定檔。 設計對話方塊中的設定檔清單順序也會定義轉譯時的視訊來源元素順序。
1. 針對不支援HTML5的瀏覽器，視訊元件可允許設定Flash後援。 開啟視訊元件設計對話方塊，並變更為 **[!UICONTROL Flash]** 標籤。 配置Flash Player設定並為Flash Player分配一個後援配置檔案。

#### 檢查清單 {#checklist}

1. 建立Dynamic Media Classic(Scene7)雲端設定。 請確定已設定視訊編碼預設集且匯入工具正在執行。
1. 為雲端設定中選取的每個視訊編碼預設集建立Dynamic Media Classic視訊設定檔。
1. 必須啟動視訊設定檔。
1. 在頁面上配置基礎視訊元件的設計。
1. 完成設計變更後，啟動設計。

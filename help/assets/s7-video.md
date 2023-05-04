---
title: 影片
description: 了解集中式視訊資產管理，您可在其中上傳Experience Manager Assets的視訊，以自動編碼至Dynamic Media Classic。 您也可以直接從Experience Manager Assets存取Dynamic Media Classic影片。 Dynamic Media Classic視訊整合透過自動裝置和自動頻寬偵測，將最佳化視訊的觸及範圍延伸至所有畫面。
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: managing-assets
content-type: reference
exl-id: 081e7db0-95cc-4260-8f08-318cd7d9d5b4
feature: Video
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 1%

---

# 影片 {#video}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Assets提供集中的視訊資產管理功能，您可以直接將視訊上傳至Assets，以自動編碼至Dynamic Media Classic。 您也可以直接從Assets存取Dynamic Media Classic影片，以進行頁面編寫。

Dynamic Media Classic視訊整合將最佳化視訊的觸角延伸至所有畫面（自動裝置和頻寬偵測）。

此 **[!UICONTROL Scene7影片]** 元件會自動執行裝置和頻寬偵測，以在桌上型電腦、平板電腦和行動裝置上播放適當的格式和適當品質的視訊。

您可以包含最適化視訊集，而非僅包含單一視訊資產。 最適化視訊集是所有視訊轉譯的容器，這些轉譯需要在多個畫面間順暢地播放視訊。 適用性視訊集會將以不同位元速率和格式編碼的相同視訊版本分組。 例如400 kbps、800 kbps和1000 kbps。 您可以使用最適化視訊集以及S7視訊元件，以在多個螢幕類型間進行最適化視訊串流。 例如案頭、iOS、Android、BlackBerry和Windows行動裝置。

請參閱 [Dynamic Media Classic檔案中的適用性視訊集以取得詳細資訊](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/video-profiles.html#dynamicmedia).

## 關於FFMPEG和Dynamic Media Classic {#about-ffmpeg-and-scene}

預設的視訊編碼程式是使用以FFMPEG為基礎的與視訊設定檔的整合為基礎。 因此，現成的DAM擷取工作流程包含以下兩個以ffmpeg為基礎的工作流程步驟：

* FFMPEG縮圖
* FFMPEG編碼

啟用和設定Dynamic Media Classic整合不會從現成可用的DAM擷取工作流程中自動移除或停用這兩個工作流程步驟。 如果您已在Experience Manager中使用基於FFMPEG的視頻編碼，則您的創作環境可能已安裝了FFMPEG。 在此情況下，使用DAM擷取的新視訊會編碼兩次：一次來自FFMPEG編碼器，一次來自Dynamic Media Classic整合。

如果您已在AEM和FFMPEG中設定FFMPEG型視訊編碼，您可以從DAM擷取工作流程中移除兩個FFMPEG工作流程。

## 支援的格式 {#supported-formats}

Scene7視訊元件支援下列格式：

* F4V H.264
* MP4 H.264

## 決定要將視訊上傳到何處 {#deciding-where-to-upload-your-video}

決定要將視訊資產上傳至何處取決於下列項目：

* 您是否需要視訊資產的工作流程？
* 您是否需要視訊資產的版本控制？

如果這兩個問題的答案皆為「是」，請直接將影片上傳至AdobeDAM。 如果兩個問題的答案都是「否」，請直接將影片上傳至Dynamic Media Classic。 後續章節將說明每個案例的工作流程。

### 如果您要直接上傳影片至AdobeDAM {#if-you-are-uploading-your-video-directly-to-adobe-dam}

如果您的資產需要工作流程或版本設定，請先上傳至AdobeDAM。 建議的工作流程如下：

1. 上傳視訊資產以AdobeDAM，並自動編碼並發佈至Dynamic Media Classic。
1. 在Experience Manager中，在 **[!UICONTROL 電影]** 標籤。
1. 使用 **[!UICONTROL Scene7影片]** 或 **[!UICONTROL Foundation影片]** 元件。

### 如果您要上傳影片至Scene7 {#if-you-are-uploading-your-video-to-scene}

如果您的資產不需要工作流程或版本設定，請將資產上傳至Scene7。 建議的工作流程如下：

1. 在Dynamic Media Classic, [設定排程的FTP上傳和編碼至Scene7（系統自動化）](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/uploading-files.html#preparing-your-assets-and-folders-for-uploading).
1. 在Experience Manager中，在 **[!UICONTROL Scene7]** 標籤。
1. 使用 **[!UICONTROL Scene7影片]** 元件。

## 設定與Scene7影片的整合 {#configuring-integration-with-scene-video}

要配置通用預設集：

1. 在 **[!UICONTROL Cloud Services]**，導覽至 **[!UICONTROL Scene7]** 設定，按一下 **[!UICONTROL 編輯]**.
1. 選取 **[!UICONTROL 影片]** 標籤。

   ![chlimage_1-363](assets/chlimage_1-363.png)

   >[!NOTE]
   >
   >此 **[!UICONTROL 影片]** 如果頁面沒有雲端設定，則不會顯示索引標籤。

1. 選取最適化視訊編碼設定檔、現成可用的單一視訊編碼設定檔，或自訂視訊編碼設定檔。

   >[!NOTE]
   >
   >如需視訊預設集含義的詳細資訊，請參閱 [Dynamic Media Classic檔案](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/application-setup.html#video-presets-for-encoding-video-files).
   >
   >Adobe建議您在設定通用預設集時同時選取兩個最適化視訊集，或選取 **[!UICONTROL 最適化視訊編碼]** 選項。

1. 選取的編碼設定檔會自動套用至您為此Scene7雲端設定所設定的CQ DAM目標資料夾中所上傳的所有視訊。 您可以使用不同的目標資料夾來設定多個Scene7雲端設定，以視需要套用不同的編碼設定檔。

## 更新檢視器和編碼預設集 {#updating-viewer-and-encoding-presets}

如果預設集已在Scene7中更新，則必須更新Experience Manager中視訊的檢視器和編碼預設集。 在這種情況下，請導覽至雲端設定中的Scene7設定，然後按一下 **[!UICONTROL 更新檢視器和編碼預設集]**.

![chlimage_1-364](assets/chlimage_1-364.png)

## 從AdobeDAM上傳主視訊至Scene7 {#uploading-your-master-video}

1. 導覽至CQ DAM Target資料夾，您已在該資料夾中使用Scene7編碼設定檔設定雲端設定。
1. 按一下 **[!UICONTROL 上傳]** 上傳主視訊。 視訊上傳和編碼在DAM更新資產工作流程完成後完成，且 **[!UICONTROL 發佈至Scene7]** 有勾號。

   >[!NOTE]
   >
   >產生視訊縮圖需要一些時間。

   將DAM主視訊拖曳至視訊元件存取上 *all* Scene7編碼代理轉譯以供傳送。

## Foundation視訊元件與Scene7視訊元件 {#foundation-video-component-versus-scene-video-component}

使用Experience Manager時，您可以同時存取Sites中可用的視訊元件和Scene7視訊元件。 這些元件不可互換。

Scene7視訊元件只適用於Scene7視訊。 基礎元件可處理從Experience Manager（使用ffmpeg）和Scene7影片儲存的影片。

下列矩陣說明何時應使用哪個元件：

![chlimage_1-365](assets/chlimage_1-365.png)

>[!NOTE]
>
>S7視訊元件現成可用，使用通用視訊設定檔。 不過，您可以以Experience Manager取得以HTML5為基礎的視訊播放器。 只要複製現成可用HTML5視訊播放器的內嵌程式碼，並放入Experience Manager頁面即可。

## Experience Manager視訊元件 {#aem-video-component}

即使建議使用Scene7視訊元件來檢視Scene7視訊，為了完整起見，請搭配Foundation視訊元件使用Scene7視訊。

### Experience Manager影片和Scene7影片比較 {#aem-video-and-scene-video-comparison}

下表提供Experience ManagerFoundation視訊元件和Scene7視訊元件之間所支援功能的高階比較：

|  | Experience ManagerFoundation影片 | Scene7影片 |
|---|---|---|
| 方法 | HTML5第一種方法。 Flash僅用於非HTML5後援。 | Flash在大多數案頭上。 HTML5用於行動裝置和平板電腦。 |
| 傳送 | 漸進式 | 最適化串流 |
| 追蹤 | 是 | 是 |
| 擴充性 | 是 | 是(具有 [HTML5檢視器SDK API檔案](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html)) |
| 行動視訊 | 是 | 是 |

### 設定 {#setting-up}

#### 建立視訊設定檔 {#creating-video-profiles}

系統會根據您在Scene7雲端設定中選取的Scene7編碼預設集，建立各種視訊編碼。 為了讓Foundation Video元件使用它們，必須為每個選取的Scene7編碼預設集建立視訊設定檔。 此方法可讓視訊元件據以選取DAM轉譯。

>[!NOTE]
>
>必須啟動新視訊設定檔及其變更才能發佈。

1. 在Experience Manager中，點選 **[!UICONTROL 工具] > [!UICONTROL 配置控制台]**.
1. 從 **[!UICONTROL 配置控制台]** 導覽至 **[!UICONTROL 工具> DAM >視訊設定檔]** 在導航樹中。
1. 建立Scene7影片設定檔。 在 **[!UICONTROL 新……]** 下拉清單，選擇 **[!UICONTROL 建立頁面]** 然後選取「Scene7視訊描述檔」範本。 為新視訊描述檔頁面命名，然後按一下 **[!UICONTROL 建立]**.

   ![chlimage_1-366](assets/chlimage_1-366.png)

1. 編輯新的視訊設定檔。 先選取雲端設定。 然後選取與雲端設定中選取的編碼預設集相同。

   ![chlimage_1-367](assets/chlimage_1-367.png)

   | 屬性 | 說明 |
   |---|---|
   | Scene7 雲端設定 | 用於編碼預設集的雲端設定。 |
   | Scene7 編碼預設集 | 用來對應此視訊設定檔的編碼預設集。 |
   | HTML5 視訊類型 | 此屬性可讓您設定HTML5視訊來源元素的type屬性值。 S7編碼預設集未提供此資訊，但使用S75視訊元素正確轉譯視訊時需要此資訊。HTML5視訊元素 提供了常用格式的清單，但可以覆蓋其他格式。 |

   對您要在視訊元件中使用的雲端設定中選取的所有編碼預設集，重複此步驟。

#### 配置設計 {#configuring-design}

此 **[!UICONTROL Foundation影片]** 元件必須知道要使用哪些視訊設定檔來建立視訊來源清單。 開啟視訊元件設計對話方塊，並設定使用新視訊設定檔的元件設計。

>[!NOTE]
>
>如果您使用 **[!UICONTROL Foundation影片]** 元件，在行動頁面的設計上重複這些步驟。

>[!NOTE]
>
>對設計所做的變更需要啟動設計，以便在發佈時生效。

1. 開啟 **[!UICONTROL Foundation影片]** 元件的設計對話框，並更改為 **[!UICONTROL 設定檔]** 標籤。 然後刪除現成可用的設定檔，並新增新的S7視訊設定檔。 設計對話方塊中描述檔清單的順序會定義轉譯時視訊來源元素的順序。
1. 針對不支援HTML5的瀏覽器，視訊元件可讓您設定Flash後援。 開啟視訊元件設計對話方塊，並變更為 **[!UICONTROL Flash]** 標籤。 配置Flash Player設定，並為Flash Player指派後援設定檔。

#### 檢查清單 {#checklist}

1. 建立S7雲端設定。 請確定已設定視訊編碼預設集，且匯入工具正在執行。
1. 為雲端設定中選取的每個視訊編碼預設集建立S7視訊設定檔。
1. 必須啟動視訊設定檔。
1. 設定 **[!UICONTROL Foundation影片]** 元件。
1. 完成設計變更後，啟動設計。

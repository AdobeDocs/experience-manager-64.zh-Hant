---
title: 管理Dynamic Media檢視器預設集
seo-title: Managing Dynamic Media viewer presets
description: 如何建立和管理Dynamic Media檢視器預設集
seo-description: How to create and manage Dynamic Media viewer presets
uuid: 31ef7a4e-2053-43b5-ac6c-cdc4b30c3914
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e78bb08a-a923-4399-b3f7-13aa4b7994d5
legacypath: /content/docs/en/aem/6-0/administer/integration/dynamic-media/viewer-presets
exl-id: 53e53cb7-1854-44e9-9516-51bcc99378b4
feature: Viewer Presets
role: Admin,User
source-git-commit: 877eade71c2ec57ff534ba2649275111c5326d75
workflow-type: tm+mt
source-wordcount: '4220'
ht-degree: 10%

---

# 管理Dynamic Media檢視器預設集 {#managing-viewer-presets}

Dynamic Media檢視器預設集是一組設定，可決定使用者在電腦畫面和行動裝置上檢視多媒體資產的方式。 如果您是管理員，可以建立檢視器預設集。 設定適用於檢視器組態選項的陣列。 例如，您可以變更檢視器的顯示大小或縮放行為。

如需建立和自訂您自己的HTML5檢視器預設集的指示，請參閱AdobeDynamic Media *HTML5檢視器SDK API檔案*。 SDK可在內嵌於SDK本身的IS發佈伺服器上使用。 每個程式庫版本都有其專屬的SDK檔案。

路徑: `<scene7_domain>/s7sdk/<library_version>/docs/jsdocs/index.html`.\
例如3.10 SDK:[https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html)

另請參閱[AdobeDynamic Media檢視器參考指南](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html)。

本節說明如何建立、編輯和管理檢視器預設集。 您隨時可以預覽資產，將檢視器預設集套用至資產。 請參閱[套用檢視器預設集](viewer-presets.md)。

>[!NOTE]
>
>請注意，編輯任何預先定義的現成可用檢視器預設集&#x200B;*並不是支援的案例。*&#x200B;如果您嘗試編輯現成可用的檢視器預設集，系統會提示您使用新名稱儲存檢視器預設集。

## 檢視器的鍵盤協助工具 {#keyboard-accessibility-for-viewers}

所有現成可用的檢視器都支援鍵盤協助工具。

另請參閱[鍵盤可訪問性和導航](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/c-keyboard-accessibility.html)。

## 管理Dynamic Media檢視器預設集 {#managing-presets}

您可以點選&#x200B;**[!UICONTROL 「工具>資產>檢視器預設集」，在AEM中新增、編輯、刪除、發佈、取消發佈和預覽檢視器預設集]**。

![tools-assets](assets/tools-assets.png)

>[!NOTE]
>
>依預設，當您在資產的詳細資訊檢視中選取「檢視器」時，系統會顯示15個檢視器預設集。 您可以提高此限制。請參 [閱增加顯示的檢視器預設集數目](#increasing-the-number-of-viewer-presets-that-display)。

## 回應式設計網頁的檢視器支援 {#viewer-support-for-responsive-designed-web-pages}

不同的網頁有不同的需求。 例如，有時您想要的網頁提供連結，可在個別瀏覽器視窗中開啟HTML5檢視器。 在其他情況下，可能需要直接將HTML5檢視器內嵌在托管頁面上。 在後一種情況下，網頁可以具有靜態佈局。 或者，它可能&#x200B;*回應式*，且在不同裝置上或針對不同瀏覽器視窗大小顯示不同。 為符合這些需求，Dynamic Media隨附的所有預先定義且立即可用的HTML5檢視器，都支援靜態網頁和回應式設計的網頁。

如需如何將回應式檢視器內嵌至網頁的詳細資訊，請參閱&#x200B;*影像伺服API說明*&#x200B;中的[回應式影像庫](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/responsive-static-image-library/c-about-responsive-static-image-library.html)。

>[!NOTE]
>
>請注意，您必須先發佈所有現成可用的檢視器，才能首次使用。\
>請參閱[發佈檢視器預設集。](#publishing-viewer-presets)

## 查看器預設集系統相容性  {#viewer-preset-system-compatibility}

Dynamic Media隨附的所有現成可用的檢視器預設集都與下列系統完全相容：

* 台式機
* AppleiPhone
* AppleiPad
* Android智慧手機
* Android平板電腦
* 對於視頻，[Blackberry](https://developer.blackberry.com/devzone/develop/supported_media/bb_media_support_at_a_glance.html#kba1328730952678)和[Windows Phone 8](https://msdn.microsoft.com/library/windows/apps/ff462087%28v=vs.105%29.aspx)提供了對MP4播放的額外支援。

### 檢視器預設集的多媒體類型 {#rich-media-types-for-viewer-presets}

建立新的檢視器預設集時，管理員可新增及自訂下列多媒體類型。

| 多媒體類型 | 說明 |
|:---|:---|
| **傳送集** | 熱點（或影像映射）或兩者都添加到一系列兩個或多個影像中。 客戶可以向左或向右平移影像，然後按一下影像上的熱點以取得其他詳細資訊，或直接從網站的類別、首頁或登陸頁面購買。 |
| **彈出式縮放** | 在原始影像旁邊顯示縮放區域的第二個影像。 沒有可使用的控制項 — 用戶將選區移動到要查看的區域上。 |
|  | 在確定此檢視器的完整頻寬使用時，請考慮在檢視器中同時提供主影像和彈出影像。 主影像大小（階段寬度和高度）和縮放因子決定彈出影像的大小。 若要避免彈出檔案大小過大，請平衡以下兩個值：如果主影像大小很大，請降低「縮放因子」值。 （「飛出寬度」和「飛出高度」決定飛出視窗的大小，但不決定提供給檢視器的飛出影像的大小。） |
|  | 例如，如果您的主影像大小是350 x 350像素，而縮放因子是3，則產生的彈出影像是1050 x 1050像素。 如果您的主影像大小是300 x 300像素，而縮放系數是4，則彈出影像是1200 x 1200像素。 視JPEG品質設定而定（建議的設定介於80到90之間），您可以大幅縮小檔案大小。 建議的縮放因子為2.5到4，視主影像的大小而定。 |
| **內嵌縮放** | 顯示原始查看器內縮放區域的影像。 沒有可使用的控制項。 也就是說，使用者會將選取項目移至要檢視的區域上。 |
| **影像集** | 在「影像集」檢視器中，使用者可以按一下縮圖影像，以查看項目的不同檢視或顏色變化。 此檢視器也提供縮放工具，供您仔細檢查影像。 |
| **互動影像** | 熱點被添加到影像的某些部分，然後客戶可以按一下這些部分以獲取其他詳細資訊，或直接從網站的類別、首頁或登錄頁購買。 |
| **互動視訊** | 縮圖會新增至影片中的時間軸區段，客戶可以按一下該區段以取得其他詳細資料，或直接從網站的類別、首頁或登陸頁面購買。 |
| **混合媒體** | 在一個檢視器中顯示不同類型的媒體。 您可以包含回轉集、影像集、影像和視訊。 |
| **全景影像** | 全景影像和全景VR檢視器會轉譯球形全景影像，讓使用者沈浸於房間、屬性、位置或橫向的360°檢視體驗中。 |
|  | 上傳的影像若要符合球形全景，必須具備下列其中一項或兩項： <ul><li>長寬比為2:1。</li><li>使用等矩形、球形和全景、球形和全景的關鍵字標籤。 請參閱[使用標籤](../sites-authoring/tags.md)。</li></ul> |
|  | 外觀比例和關鍵字條件都適用於資產詳細資訊頁面和「全景媒體」WCM元件的全景資產。 |
|  | 重要：此檢視器僅適用於Dynamic Media - Scene7模式。 |
| **迴轉集** | 提供影像的多個視圖，以便用戶可以旋轉對象來檢查不同的邊和角度。 |
| **影片** | 使用漸進式或最適化位元速率串流播放視訊。 自適應位元速率串流會自動執行裝置和頻寬偵測，以適當格式提供適當品質的視訊。 |
| **垂直縮放** | 垂直縮放檢視器可讓您最大化產品影像檢視體驗，讓使用者能以最佳方式呈現產品。 色票的垂直位置會執行下列操作： <ul><li>確保色票位於折頁上方。 使用水準色票時，視使用者的案頭螢幕大小而定，在使用者向下捲動頁面之前，色票不可見。 將色票垂直放置在檢視器中，可確保無論使用者的螢幕大小皆可看見。</li><li>最大化主映像大小。 使用水準色票時，必須在頁面上保留空格，以確保其可見。 此定位縮小了主影像的大小。 但是，使用垂直色票版面時，您不需要分配此空間。 因此，您可以最大化主影像大小。</li></ul> |
| **縮放** | 可讓使用者按一下區域來放大。 使用者可以按一下控制項來放大、縮小，以及將影像重設為其預設大小。 |

## 現成可用的檢視器預設集清單 {#list-of-out-of-the-box-viewer-presets}

下表識別Dynamic Media隨附的所有預先定義且現成的檢視器預設集。

另請參閱[即時演示](https://landing.adobe.com/tw/na/dynamic-media/ctir-2755/live-demos.html)。

如需支援的網頁瀏覽器和檢視器作業系統版本的相關資訊，您可以檢閱檢視器發行說明。

請參閱[檢視器參考指南](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html)目錄中的&#x200B;*檢視器發行說明*。

>[!NOTE]
>
>Dynamic Media中所有現成可用的檢視器預設集皆已啟動（開啟），但您必須發佈。\
>請參閱[發佈檢視器預設集](#publishing-viewer-presets)。
>
>您建立和新增的任何新檢視器預設集都必須同時啟動&#x200B;*和*。\
>請參閱[啟用或停用檢視器預設集](#activating-or-deactivating-viewer-presets)和[發佈檢視器預設集](#publishing-viewer-presets)。

| 檢視器預設集標題 | 類型 | CSS 檔案名稱 |
|:---|:---|:---|
| 輪播_虛線_深色 | 輪播集(_S) | html5_carouselviewer_dotted_dark_css |
| 輪播_虛線_淺 | 輪播集(_S) | html5_carouselviewer_dotted_light_css |
| 轉盤_數值_深 | 輪播集(_S) | html5_carouselviewer_numeric_dark_css |
| 輪播_數值_light | 輪播集(_S) | html5_carouselviewer_numeric_light_css |
| 飛出 | 飛出_縮放 | html5_flyoutviewer.css |
| ImageSet_dark | 影像集 | html5_zoomviewer_dark.css |
| ImageSet_light | 影像集 | html5_zoomviewer_light.css |
| InlineMixedMedia_dark | Mixed_Media | html5_inlinemixedmediaviewer_dark.css |
| InlineMixedMedia_light | Mixed_Media | html5_inlinemixedmediaviewer_light.css |
| InlineZoom | 飛出_縮放 | html5_inlinezoomviewer.css |
| MixedMedia_dark | Mixed_Media | html5_mixedmediaviewer_dark.css |
| MixedMedia_light | Mixed_Media | html5_mixedmediaviewer_light.css |
| 全景影像 | 全景影像 | html5_panoramicimage.css |
| 全景影像VR | 全景影像 | html5_panoramicimage.css |
| Shopbable_Banner | Interactive_Image | html5_interactiveimage.css |
| Shopbable_Video_dark | Interactive_Video | html5_interactivevideoviewer_dark_css |
| Shopbable_Video_light | Interactive_Video | html5_interactivevideover_light_css |
| 回轉集深 | 回轉集(_S) | html5_spinviewer_dark.css |
| 回轉集光源 | 回轉集(_S) | html5_spinviewer_light.css |
| 影片（包括隱藏式字幕支援） | 影片 | html5_videoviewer.css |
| Video_social（包括對隱藏式字幕和社交媒體的支援） | 影片 | html5_videoviewersocial.css |
| 縮放深(_D) | 縮放 | html5_basiczoomviewer_dark.css |
| Zoom_light | 縮放 | html5_basiczoomviewer_light.css |
| ZoomVertical_dark | 垂直縮放 | html5_zoomverticalviewer_dark.css |
| ZoomVertical_light | 垂直縮放 | html5_zoomverticalviewer_light.css |

### 支援的行動檢視器手勢矩陣 {#supported-mobile-viewers-gestures-matrix}

下表識別iOS、Android 2.x和Android 3.x裝置上支援的行動檢視器手勢。

| 手勢 | 彈出式縮放 | 縮放 | 迴轉 |
|---|---|---|---|
| **拖曳** | 平板 | 平板 | 平板 |
| **點選** | 顯示彈出窗口 | 顯示或隱藏使用者介面 | 顯示或隱藏使用者介面 |
| **按兩下** | 不適用 | 放大或重設 | 放大或重設 |
| **夾開** | 不適用 | 放大(僅限iOS和Android 3x) | 放大(僅限iOS和Android 3x) |
| **夾緊關閉** | 不適用 | 縮小(僅限iOS和Android 3x) | 縮小(僅限iOS和Android 3x) |
| **撥動** | 捲動色票列 | 捲動影像 | 自旋 |
| **弗利克** | 捲動色票列 | 捲動影像 | 自旋 |

## 增加顯示的Dynamic Media檢視器預設集數目 {#increasing-the-number-of-viewer-presets-that-display}

AEM從&#x200B;**[!UICONTROL 「詳細資料檢視」>「檢視器」]**&#x200B;檢視資產時，會顯示多種檢視器預設集。 您可以增加或減少顯示的檢視器數量。

**若要增加顯示的Dynamic Media檢視器預設集數目**:

1. 導覽至&#x200B;**[!UICONTROL CRXDE Lite]**([http://localhost:4502/crx/de](http://localhost:4502/crx/de))。
1. 導覽至`/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist`處的檢視器預設集清單節點

   ![chlimage_1-221](assets/chlimage_1-221.png)

1. 在 **[!UICONTROL limit]** 屬性中，將預設設 ****&#x200B;定為15的值變更為所要的數字。
1. 導覽至`/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist/datasource`的檢視器預設集資料來源

   ![chlimage_1-222](assets/chlimage_1-222.png)

1. 在&#x200B;**[!UICONTROL limit]**&#x200B;屬性中，將數字變更為所需數字，例如`{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`
1. 點選「**[!UICONTROL 儲存全部]**」。

## 建立新的Dynamic Media檢視器預設集 {#creating-a-new-viewer-preset}

建立檢視器預設集可讓您套用各種設定，以檢視資產並與資產互動。 不過，您不需要建立新的檢視器預設集。 您也可以使用AEM Assets隨附的預設現成檢視器預設集。

如果您選擇建立新的檢視器預設集，儲存後，檢視器的狀態會在&#x200B;**[!UICONTROL 檢視器預設集]**&#x200B;頁面中自動啟動（設為&#x200B;**On**）。 此狀態表示在您預覽影像或視訊時，它會顯示在&#x200B;**[!UICONTROL Dynamic Media]**&#x200B;元件和&#x200B;**[!UICONTROL 互動式媒體]**&#x200B;元件中。

某些檢視器預設集具有排他性設定，這些設定可能會影響檢視器的使用和整體行為。 視您建立的檢視器預設集而定，您可能想要注意這些特殊考量事項。

請參閱[建立互動式檢視器預設集的特殊考量事項](#special-considerations-for-creating-an-interactive-viewer-preset)。

請參閱[建立轉盤橫幅檢視器預設集的特殊考量](#special-considerations-for-creating-a-carousel-banner-viewer-preset)。

**若要建立新的Dynamic Media檢視器預設集**:

1. 在AEM的左上角，點選AEM標誌，然後在左側導軌中，點選「 **[!UICONTROL 工具>資產>檢視器預設集]**」。

   ![檢視器預設集](assets/viewerpresets.png)

1. 在「**[!UICONTROL 檢視器預設集]**」頁面的工具列上，點選「 **[!UICONTROL Create]**」。
1. 在「**[!UICONTROL 新建查看器預設集]**」對話框的「預設集名稱&#x200B;]**」欄位中，輸入新預設集的名稱。**[!UICONTROL &#x200B;請謹慎選擇名稱 — 在您點選&#x200B;**[!UICONTROL Create]**&#x200B;後，這些名稱就無法編輯。

   稍後在這些步驟中儲存預設時，名稱會顯示在「檢視器預設集」頁面的&#x200B;**[!UICONTROL 「預設標題]**」欄標題下。

1. 在「**[!UICONTROL 多媒體類型]**」下拉式選單中，選取您要建立的檢視器預設集類型，然後在頁面的右上角，點選「**[!UICONTROL 建立」]**。

   請參閱[檢視器預設集的多媒體類型](#rich-media-types-for-viewer-presets)。

1. 在「**編輯檢視器預設集**」頁面上，點選「**[!UICONTROL Appearance]**」標籤。
1. 執行下列任一操作：

   * 在&#x200B;**[!UICONTROL Selected Type]**&#x200B;下拉菜單中，選擇要自定義其視覺設計的元件。 或者，您也可以點選檢視器中的任何視覺元素，以選取它進行設定。

      視覺編輯器可讓您查看特定屬性對樣式有何影響。 只要設定或調整任何屬性，即可使用編輯器左側的範例，立即查看其對檢視器有何影響。

      [檢視器參考指南](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html)中的任何「自訂&#x200B;*&lt;viewer_name>*&#x200B;檢視器」說明主題，都說明每種檢視器預設集類型的CSS樣式屬性。

      例如，如果您要建立`Mixed_Media`類型的檢視器預設集，請參閱[自訂混合媒體檢視器](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/mixed-media/customing-mixed-media/c-html5-mixedmedia-viewer-customizingviewer.html)以取得每個屬性的清單和說明。

   * 如果您已在個別的CSS檔案中定義樣式設定，則可將CSS檔案上傳至AEM Assets。 點選&#x200B;**[!UICONTROL **[!UICONTROL  Selected Type ]**下拉式選單（您可能需要向上捲動視覺編輯器才能查看它）下方的「匯入CSS]**」 ，以尋找已上傳的CSS檔案，並將其與檢視器預設集建立關聯。

      當您匯入CSS檔案時，視覺編輯器會檢查CSS是否使用正確的檢視器標籤。 例如，如果要建立縮放查看器，則您導入的所有CSS規則必須使用其父級查看器元素上定義的查看器類名稱`.s7mixedmediaviewer`來定義。

      只要正確定義指定檢視器的CSS標籤，您就可以匯入任意的手工CSS。 (CSS標籤會說明在[檢視器參考指南](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html)的任何「自訂&#x200B;*&lt;檢視器名稱>*&#x200B;檢視器」說明主題中。 例如，如果您想要閱讀縮放檢視器的CSS標籤，請參閱[自訂縮放檢視器](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/zoom/customizing-zoom/c-html5-20-zoom-viewer-customizingviewer.html)。) 不過，視覺編輯器可能不了解某些CSS值。 在這種情況下，視覺編輯器會嘗試覆寫錯誤，讓CSS仍可運作。
   >[!NOTE]
   >
   >如果您偏好直接以原始格式編輯CSS，請點選「選取類型」下拉式選單下方的「顯示/隱藏CSS **** 」 (您可能需要向上捲動視覺編輯器才能檢視)。****
   >
   >如同視覺編輯器，當您直接在CSS中變更屬性時，可以立即查看它對檢視器範例有何影響。 而且，同一屬性會在視覺編輯器中同時自動更新。 因此，您可以使用原始CSS編輯器或視覺編輯器，或兩者可交互使用。

   >[!NOTE]
   >
   >對於按鈕圖稿，請選擇2x影像並上傳高解析度藝術作品。 使用互動式影像和可購買的橫幅時，您也可以從各種現成可用的熱點按鈕中選取。

1. （可選）在&#x200B;**[!UICONTROL 「編輯查看器預設集」]**&#x200B;頁面頂部附近，點選&#x200B;**[!UICONTROL Desktop]**、**[!UICONTROL Tablet]**&#x200B;或&#x200B;**[!UICONTROL Phone]**&#x200B;以唯一定義不同設備和螢幕類型的視覺樣式。
1. 在「**[!UICONTROL 編輯檢視器預設集]**」頁面，點選「**行為**」標籤。 或者，您也可以點選或按一下檢視器中的任何視覺元素，以選取它進行設定。
1. 從「選 **[!UICONTROL 定類型]** 」(Selected Type)下拉菜單中，選擇要更改其行為的元件。

   可視化編輯器中的許多元件都有與其相關聯的詳細說明。 展開元件以顯示其相關參數時，這些說明會顯示在藍色方塊中。

   有些檢視器類型具有可讓您在「 **IS Command」 (IS命令) 文字欄位中指定「Image Serving** 」 (影像伺服) 命令的元件。如需您可使用的指令清單，請參 [閱影像伺服API參考](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-is-home.html)。

   >[!NOTE]
   >
   >**如果您使用觸控裝置，例如手機或平板電腦……**
   >
   >在文字欄位中輸入值後，請在使用者介面的其他位置點選以提交變更並關閉虛擬鍵盤。 如果您點選&#x200B;**[!UICONTROL Enter]**，則不會執行任何動作。

1. 在頁面的右上角附近，點選&#x200B;**[!UICONTROL Save]**。
1. 發佈新的檢視器預設集。 您必須先發佈預設集，才能在網站上使用。

   請參閱[發佈檢視器預設集](#publishing-viewer-presets)。

## 建立互動式檢視器預設集的特殊考量事項 {#special-considerations-for-creating-an-interactive-viewer-preset}

**關於面板中影像縮圖的顯示模式**

當您建立或編輯互動式視訊檢視器預設集時，可以選擇在&#x200B;**[!UICONTROL Behavior]**&#x200B;標籤下的&#x200B;**[!UICONTROL 選取的元件]**&#x200B;下拉式選單中選取`InteractiveSwatches`時要使用的&#x200B;**[!UICONTROL 顯示模式]**&#x200B;設定。 您選擇的顯示模式會影響縮圖在視訊播放時的顯示方式和時間。 您可以選擇`segment`顯示模式（預設）或`continuous`顯示模式。

| 顯示模式 | 說明 |
|---|---|
| [!UICONTROL 區段] |  為現成互動式視訊檢視器預設集Shopbable_Video_light和Shopbable_Video_dark的預設顯示模式，以及您自行建立的任何互動式視訊檢視器預設集。 |
|  | 在此模式中，如果指派給視訊區段的縮圖數少於顯示面板中的可見點數，則系統不會提取下一個或上一個子區段的縮圖，以填入面板中的任何空白點。 也就是說，它會保留指派給特定視訊區段的色票顯示。 |
| [!UICONTROL 連續] | 在[!UICONTROL Continuous]顯示模式中，如果區段中的縮圖數小於面板中顯示的數字，則檢視器會自動包括來自下一個區段或上一個區段的縮圖顯示，以防顯示最後一個縮圖。 |

**關於互動式視訊檢視器中的自動捲動行為**

互動式視訊檢視器中縮圖的自動捲動行為可獨立於您選擇的顯示模式運作。

當您建立或編輯互動式視訊檢視器預設集時，可從&#x200B;**[!UICONTROL Behavior]**&#x200B;標籤存取&#x200B;**[!UICONTROL 自動捲動]**。 在「行為」標籤中，從「選 **[!UICONTROL 取的元件]** 」下拉式選單中點選「 **[!UICONTROL 互動色票」]**。**[!UICONTROL 自動捲動]**&#x200B;複選框列在「IS命令」文本欄位下。

如果您在檢視器預設集中停用「自動捲動 **** 」 (清除核取方塊)，當使用者播放視訊時，面板只會顯示整個視訊長度的第一個縮圖影像。不過，使用者可視需要使用向上和向下箭頭圖示手動捲動縮圖。

當您在檢視器預設集中啟用 (選取) 「自動捲動 **** 」時，在視訊播放期間，指派給視訊區段的縮圖影像會在區段開始時捲動至檢視中。但是，有些例項會顯示區段中某些縮圖的長度，是其前後縮圖的兩倍。發生此行為是因為區段中的縮圖數目大於面板中顯示的數目，且不可平均分割。

舉例來說，假設您有一個30秒的視訊區段。 30秒內總共會顯示9個縮圖。 您的瀏覽器的大小調整為顯示面板中有四個可見的縮圖位置。 30秒視訊時間區段分為三個子區段。 下表顯示指定時間子區段顯示縮圖的劃分：

| **視訊子區段** | **子區段時間（以秒為單位）** | **面板中可見的縮圖** |
|---|---|---|
| 1 | 0-10 | 1, 2, 3, 4 |
| 2 | 10-20 | 4, 5, 6, 7 |
| 3 | 20-30 | 6, 7, 8, 9 |

視訊子區段3不會延伸至指派給它的縮圖以外。 另請注意，縮圖4、6和7在面板中的顯示長度是其他縮圖的兩倍。

檢視器根據可用位置數量，用於面板中顯示多少縮圖的邏輯如下：

* 子區段數=無條件捨去至下一個子區段（縮圖數/縮圖面板中可見位置數，根據瀏覽器視窗大小）。

   以上表格中的範例為例， 9個縮圖/ 4個槽= 2.25;檢視器邏輯會將其捨入為3個子區段。

* 縮圖數=捨入至下一個縮圖（縮圖數/視訊子區段數）。

   使用上表中的範例， 9縮圖/ 3個視訊子區段= 3個縮圖。

* 子區段的持續時間=總視訊持續時間/視訊子區段的數量。

   根據上表中的範例，30秒/3個視訊子區段=每個視訊子區段的10秒顯示。

### 建立轉盤橫幅檢視器預設集的特殊考量 {#special-considerations-for-creating-a-carousel-banner-viewer-preset}

建立轉盤橫幅檢視器預設集時，可依下列方式存取變更熱點的樣式：

|  | **說明** | **動作** |
|---|---|---|
| **熱點表徵圖** | 更改用於熱點的表徵圖 | 要更改熱點表徵圖影像，請在&#x200B;**[!UICONTROL Appearance]**&#x200B;頁簽的&#x200B;**[!UICONTROL Selected Component]**&#x200B;中，點選&#x200B;**[!UICONTROL ImageMapEffect]**。 在&#x200B;**[!UICONTROL Icon]**&#x200B;下，選擇&#x200B;**[!UICONTROL Background]**，然後在&#x200B;**[!UICONTROL Image]**&#x200B;欄位中導覽至您想要的背景影像。 |

## 啟用或停用Dynamic Media檢視器預設集 {#activating-or-deactivating-viewer-presets}

使用者介面中可用的檢視器預設集，取決於哪些檢視器預設集在「製作」模式中處於作用中狀態。 依預設，建立後的檢視器預設集為&#x200B;*On*。 如果關閉預設集，您不會在「製作」模式中看到它。 如果已發佈預設集。 無論開啟或關閉，都會一律發佈。 如果清單變得太龐雜，或您不想讓檢視器預設集可供使用，您可以停用檢視器預設集。

**若要啟用或停用Dynamic Media檢視器預設集**:

1. 在AEM的左上角，點選AEM標誌，然後在左側導軌中，點選「 **[!UICONTROL 工具>資產>檢視器預設集]**」。
1. 在&#x200B;**[!UICONTROL 檢視器預設集]**&#x200B;頁面的&#x200B;**[!UICONTROL State]**&#x200B;欄標題下，點選切換以啟用或停用檢視器預設集。

   已啟動的檢視器預設集會讓切換按鈕顯示在右側、藍色方塊內；停用的檢視器預設集會讓切換按鈕顯示在左側的淺灰色方塊內。

## 發佈Dynamic Media檢視器預設集 {#publishing-viewer-presets}

啟動（或將&#x200B;*開啟*）檢視器預設集的狀態表示它可在Dynamic Media元件、互動式媒體元件中，以及您每次檢視資產時顯示。

不過，若要傳送包含檢視器預設集的資產，檢視器預設集也必須發佈。 所有檢視器預設集都必須啟動&#x200B;*並發佈*，才能取得資產的URL或內嵌程式碼。 您必須啟動並發佈動態媒體隨附的所有現成可用的檢視器預設集。您建立和新增的自訂檢視器預設集會自動啟動，但也必須發佈。

請參閱[啟用或停用檢視器預設集](#activating-or-deactivating-viewer-presets)。

另請參閱[預覽資產](previewing-assets.md)。

**若要發佈Dynamic Media檢視器預設集**:

1. 在AEM的左上角，點選AEM標誌，然後在左側導軌中，點選「 **[!UICONTROL 工具>資產>檢視器預設集]**」。
1. 選取一或多個要發佈的檢視器預設集。
1. 在工具列上，點選&#x200B;**[!UICONTROL Publish]**&#x200B;圖示。

## 排序Dynamic Media檢視器預設集 {#sorting-viewer-presets}

**若要排序Dynamic Media檢視器預設集**:

1. 在AEM的左上角，點選AEM標誌，然後在左側導軌中，點選「工具 (槌子圖示) **>資產>檢視器預設集」******。
1. 按一 **[!UICONTROL 下「標題]**」、「類型」、「發佈國 **[!UICONTROL 」或「國]********** 家預設」，依該欄標題排序。例如，按一下「 **[!UICONTROL 類型]** 」，以字母或反字母順序排序檢視器預設集類型。

## 編輯Dynamic Media檢視器預設集 {#editing-viewer-presets}

請注意，編輯任何預先定義的現成可用檢視器預設集&#x200B;*並不是支援的案例。*&#x200B;如果您編輯現成可用的檢視器預設集，系統會提示您以新名稱儲存它。

**若要編輯Dynamic Media檢視器預設集**:

1. 在AEM的左上角，點選AEM標誌，然後在左側導軌中，點選「 **[!UICONTROL 工具>資產>檢視器預設集]**」。
1. 勾選檢視器預設集標題左側的方塊，以選取預設集。
1. 在工具列上，點選&#x200B;**[!UICONTROL Edit]**。
1. 在&#x200B;**[!UICONTROL 編輯檢視器預設集]**&#x200B;頁面上，對檢視器預設集進行您想要的變更。
1. 執行下列任一操作：

   * 點選&#x200B;**[!UICONTROL Save]**&#x200B;以儲存您的變更並返回&#x200B;**[!UICONTROL 檢視器預設集]**&#x200B;頁面。
   * 點選&#x200B;**[!UICONTROL 取消]**&#x200B;以撤消您所做的任何更改，並返回&#x200B;**[!UICONTROL 查看器預設集]**&#x200B;頁。

## 刪除自訂Dynamic Media檢視器預設集 {#deleting-custom-viewer-presets}

您可以刪除已建立並新增至Dynamic Media的檢視器預設集。

**若要刪除自訂Dynamic Media檢視器預設集**:

1. 在AEM的左上角，點選AEM標誌，然後在左側導軌中，點選「 **[!UICONTROL 工具>資產>檢視器預設集]**」。
1. 在「**[!UICONTROL 檢視器預設集]**」頁面上，檢查「預設標題&#x200B;]**」，然後點選「**[!UICONTROL &#x200B;垃圾筒&#x200B;]**」圖示。**[!UICONTROL 
1. 點選&#x200B;**[!UICONTROL Delete]**。

## 將Dynamic Media檢視器預設集套用至資產 {#applying-a-viewer-preset-to-an-asset}

如果您已發佈資產和選取的檢視器， **[!UICONTROL URL]** 和 **[!UICONTROL Embed]**  (內嵌) 按鈕會在您選取檢視器預設集後顯示。

**若要將Dynamic Media檢視器預設集套用至資產**:

1. 開啟資產，在頁面左上角附近，點選下拉式選單，然後選取「**[!UICONTROL 檢視器]**」。

   >[!NOTE]
   >
   >如果您已發佈資產和選取的檢視器， **[!UICONTROL URL]** 和 **[!UICONTROL Embed]**  (內嵌) 按鈕會在您選取檢視器預設集後顯示。

1. 從左窗格選取檢視器預設集，以將其套用至資產。

   您可以[複製URL以與其他使用者共用](linking-urls-to-yourwebapplication.md)。

## 使用Dynamic Media檢視器預設集傳送資產 {#delivering-assets-with-viewer-presets}

若要取得檢視器預設集的URL，請參閱[將URL連結至您的Web應用程式](linking-urls-to-yourwebapplication.md)。 另請參閱[在網頁上嵌入視頻查看器](embed-code.md)。

如果您使用AEM作為WCM，可以直接在頁面上使用檢視器預設集來新增資產。 請參閱[將Dynamic Media資產新增至頁面](adding-dynamic-media-assets-to-pages.md)。

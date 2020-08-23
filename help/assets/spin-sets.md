---
title: 迴轉集
seo-title: 迴轉集
description: 瞭解如何在動態媒體中處理回轉集
seo-description: 瞭解如何在動態媒體中處理回轉集
uuid: a80a0491-6500-463a-83c4-ff4b90a88182
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: afacb3ad-e4ad-4d06-a898-f3f2da8bbb64
translation-type: tm+mt
source-git-commit: 7cb0f63f0cd83e6e40ed51b2fd300f010278aa56
workflow-type: tm+mt
source-wordcount: '1838'
ht-degree: 6%

---


# 迴轉集 {#spin-sets}

「回轉集」(Spin Set)模擬實際操作，即旋轉對象來檢查對象。 「回轉集」可讓您從任何角度檢視項目，從任何角度獲得關鍵視覺細節。

回轉集可模擬360度檢視體驗。 動態媒體提供單軸回轉集，檢視器可在其中旋轉項目。 此外，使用者只需按幾下滑鼠，就可「自由格式」縮放和平移任何檢視。 這樣，用戶就可以更密切地從特定的角度檢查項目。

Spin Sets are designated by a banner with the word **[!UICONTROL SPINSET]**. In addition, if the Spin Set is published, then the publish date, indicated by the **[!UICONTROL World]** icon is on the banner along with the last modification date, indicated by the **[!UICONTROL Pencil]** icon displays.

![chlimage_1-380](assets/chlimage_1-380.png)

>[!NOTE]
>
>如需「資產」使用者介面的詳細資訊，請參 [閱「使用Touch UI管理資產」](managing-assets-touch-ui.md)。

## 快速入門：回轉集 {#quick-start-spin-sets}

若要快速啟動並執行回轉集，請遵循下列工作流程：

1. [上傳影像以進行多次檢視。](#uploading-assets-for-spin-sets)

   至少，一維自旋集需要8-12個項目鏡頭，二維自旋集需要16-24個項目鏡頭。 拍攝時間必須定期，以呈現項目旋轉和翻轉的印象。 例如，如果一維回轉集包含12個鏡頭，請針對每個鏡頭旋轉項目30度(360/12)。

1. [建立回轉集。](#creating-spin-sets)

   若要建立回轉集，請選取「 **[!UICONTROL 建立」>「回轉集」]** ，然後為該回轉集命名，選擇資產，然後依影像的顯示順序排序影像。

   See [Working with Selectors](working-with-selectors.md).

   >[!NOTE]
   >
   >You can also create Spin Sets automatically through [batch set presets](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).
   *批集由IPS(Image Production System)建立，作為資產提取的一部分，並且僅在動態媒體- Scene7模式中可用*。

1. 視需要 [設定回轉集檢視器預設](managing-viewer-presets.md)。

   管理員可以建立或修改回轉集檢視器預設集。 To see your Spin Set with a Viewer preset, select the Spin Set, and in the left-rail drop-down menu, select **[!UICONTROL Viewers]**.

   請參閱「 **[!UICONTROL 工具>資產>檢視器預設集]** 」以建立或編輯檢視器預設集。

   請參閱 [新增和編輯檢視器預設集。](managing-viewer-presets.md)

1. [查看回轉集](#viewing-spin-sets)。

   您可以三種不同的方式檢視和存取以批次集預設集方式建立的集合。 (使用批集預設集建立的集 *不會* 顯示在用戶介面中。)

1. [預覽回轉集。](previewing-assets.md)

   選取「回轉集」(Spin Set)，您就可以預覽它。 旋轉回轉集。 您可以從左側導軌下拉式選單 **[!UICONTROL 的「檢視器]** 」選單中選擇不同的檢視器。

1. [發佈回轉集。](publishing-dynamicmedia-assets.md)

   「發佈回轉集」會啟動影像在回轉集物件中的顯示順序。 請務必訂購，如此旋轉360度檢視就會順暢無礙。**[!UICONTROL URL]** 和 **[!UICONTROL 內嵌字串]** 。 此外，您必須發 [布檢視器預設集](managing-viewer-presets.md)。

1. [將URL連結至您的Web應用程式](linking-urls-to-yourwebapplication.md) ，或 [內嵌視訊或影像檢視器](embed-code.md)。

   AEM Assets會建立回轉集的URL呼叫，並在您發佈回轉集後啟動這些呼叫。 您可以在預覽資產時複製這些URL。 或者，您也可以將它們內嵌在您的網站上。

   選取「回轉集」，然後在左側導軌下拉式選單中選取「檢 **[!UICONTROL 視器]**」。

   請參 [閱將回轉集連結至網頁](linking-urls-to-yourwebapplication.md)[和內嵌視訊或影像檢視器](embed-code.md)。

如果需要，可以編 [輯回轉集](#editing-spin-sets)。 此外，您還可以檢視和編輯回轉 [集屬性](managing-assets-touch-ui.md#editing-properties)。

## 上傳回轉集的資產 {#uploading-assets-for-spin-sets}

至少，一維自旋集需要8-12個項目鏡頭，二維自旋集需要16-24個項目鏡頭。 拍攝時間必須定期，以呈現項目旋轉和翻轉的印象。 例如，如果一維回轉集包含12個鏡頭，請針對每個鏡頭旋轉項目30度(360/12)。

您可以像上傳AEM Assets中的任何其他資產一樣， [上傳回轉集的影像](managing-assets-touch-ui.md)。

### 拍攝回轉集影像的准則 {#guidelines-for-shooting-spin-set-images}

以下是回轉集影像的一些最佳實務。 一般而言，旋轉集中的影像越多，影像旋轉效果就越好。 不過，在集合中加入許多影像也會增加影像載入所花的時間。 AEM建議拍攝影像的下列准則，以用於回轉集：

* 至少，在一維回轉集中使用8-12張影像，在二維回轉集中使用16-24張影像。 至少需要8張影像才能旋轉360度。 一維回轉集比較常見，因為建立二維回轉集耗費大量人力。
* 使用無損格式；建議使用TIFF和PNG。
* 遮色所有影像，讓項目出現在純白色或其他高對比背景上。 （可選）添加陰影。
* 請確定產品詳細資訊已清楚標示，並且已集中注意。
* 為具有人體模型或模特兒的時尚服裝拍攝旋轉影像。 通常，假人模型要麼是完全遮色的（使用玻璃模型），要麼在圖中顯示風格化的假人模型／服裝。 通過定義角度數，可建立模型上的回轉集。 在地板上用磁帶標籤每個角度，以引導模型向每個拍攝方向步移和查看。

## 建立回轉集 {#creating-spin-sets}

影像在回轉集中的顯示順序。 請務必訂購，如此旋轉360度檢視就會順暢無礙。

>[!NOTE]
>
>您也可以透過批次集預設集自動 [建立回轉集](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)。批集由IPS(Image Production System)建立，作為資產提取的一部分，並且僅在動態媒體- Scene7模式中可用。
>
>請參閱「設定動態媒體- Scene7模式」中的「建立批次集預設集以自動產 [生影像集和回轉集」](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)。

**要建立回轉集：**

1. In Assets, navigate to where you want to create a spin set, tap **[!UICONTROL Create]**, and select **[!UICONTROL Spin Set]**. 您也可以從包含資產的資料夾內建立資產集。

   ![chlimage_1-381](assets/chlimage_1-381.png)

1. 在「回轉 **[!UICONTROL 集編輯器]** 」頁的「 **[!UICONTROL 標題]** 」欄位中，輸入回轉集的名稱。 名稱會顯示在回轉集的橫幅中。 （可選）輸入說明。

   ![chlimage_1-382](assets/chlimage_1-382.png)

   當您建立回轉集時，可以變更回轉集縮圖，或允許AEM根據回轉集中的資產自動選取縮圖。 若要選取縮圖，請點選「 **[!UICONTROL 變更縮圖」]**。選取任何影像（您也可以導覽至其他檔案夾以尋找影像）。 If you have selected a thumbnail and then decide that you want AEM to generate one from the spin set, select **[!UICONTROL Switch to Automatic thumbnail]**.

1. 執行下列任一項作業：

   * 在「回轉集編輯器」頁面的左上角 **[!UICONTROL 附近]** ，點選「 **[!UICONTROL 新增資產」]**。
   * 在「回轉集編輯器」頁 **[!UICONTROL 面的中間]** ，點選 **[!UICONTROL 以開啟資產選擇器]**。

   點選以選取您要納入回轉集中的資產。 選取的資產上面有核取標籤圖示。When you are finished, near the upper-right corner of the page, tap **[!UICONTROL Select]**.

   使用「資產選擇器」，您可以輸入關鍵字並點選「回報」來搜尋 **[!UICONTROL 資產]**。您也可以套用篩選條件來調整搜尋結果。您可以依路徑、系列、檔案類型和標籤來篩選。選取篩選，然後點選工具 **[!UICONTROL 列上的]** 「篩選」圖示。若要變更檢視，在頁面右上角附近點選「檢視」圖示，然後點選「 **[!UICONTROL 欄檢視」、「]** 卡片檢視 **[!UICONTROL 」或「清單檢]**********&#x200B;視」。

   See [Working with Selectors](working-with-selectors.md).

   ![chlimage_1-383](assets/chlimage_1-383.png)

1. 當您將資產新增至集合時，資產會自動以字母數字順序新增。 您可以在新增資產後手動重新排序或排序資產。 如有必要，請將資產的「重新排序」 **** 圖示拖曳至資產檔案名稱的右側，以在設定清單上或下重新排序影像。

   ![spin_set_assets6-4](assets/spin_set_assets6-4.png)

1. （可選）執行下列任一項作業：

   * 若要刪除影像，請選取影像，然後點選「刪 **[!UICONTROL 除資產」]**。
   * To apply a preset, near the upper-right corner of the page, tap **[!UICONTROL Preset]**, then select a preset to apply to all the assets at once.

1. 點選「 **[!UICONTROL 儲存]**」。 您新建立的「回轉集」會顯示在您所建立的檔案夾中。

## 查看回轉集 {#viewing-spin-sets}

您可以在使用者介面中建立回轉集，或使用批次集預 [設集自動建立](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)。 不過，使用批集預設集建立的集 *合* ，不會顯示在使用者介面中。 您可以三種不同的方式存取使用批次集預設集建立的集。 （即使您在使用者介面中建立回轉集，這些方法也可用）。

您也可以透過使用者介面來檢視集合，如編輯回轉集 [所述](#editing-spin-sets)。

**要查看回轉集，請執行以下操作：**

1. 開啟個別資產的屬性時。 屬性指明所選資產的成員集(在「集的成 **[!UICONTROL 員」下]**)。 點選集的名稱可查看整個集。

   ![chlimage_1-384](assets/chlimage_1-384.png)

1. 來自任何組的成員映像。Select the **[!UICONTROL Sets]** menu to display the sets that the asset is a member of.

   ![chlimage_1-385](assets/chlimage_1-385.png)

1. From search, you can select **[!UICONTROL Filters]**, then expand **[!UICONTROL Dynamic Media]** and select **[!UICONTROL Sets]**.

   搜尋會傳回在使用者介面中手動建立或透過批次集預設集自動建立的相符集。 對於自動集，搜尋查詢是使用「以搜尋標準開始 **[!UICONTROL 」（與以「包含」搜尋標準為基礎的AEM搜尋不同）來]****** 進行。 將篩選器設 **[!UICONTROL 置為]** 「集」是搜索自動集的唯一方法。

   ![chlimage_1-386](assets/chlimage_1-386.png)

## 編輯回轉集 {#editing-spin-sets}

您可以對回轉集執行多種編輯工作，例如：

* 將影像新增至回轉集。
* 在回轉集中重新排序影像。
* 刪除回轉集中的資產。
* 套用檢視器預設集。
* 刪除回轉集。

**要編輯回轉集：**

1. 執行下列任一項作業：

   * 將滑鼠指標暫留在「回轉集」資產上，然後點選「 **[!UICONTROL 編輯]** 」（鉛筆圖示）。
   * 將滑鼠指標暫留在回轉集資產上，點選 **[!UICONTROL 選]** （勾選圖示），然後點選工具列上的 **[!UICONTROL 編輯]** 。
   * 點選「回轉集」資產，然後點選工具列 **[!UICONTROL 上的「編輯]** （鉛筆圖示）」。

1. 若要編輯回轉集，請執行下列任一動作：

   * 若要重新排序影像，請將影像拖曳至新位置（選取重新排序圖示以移動項目）。
   * 若要依遞增或遞減順序排序項目，請點選欄標題。
   * 若要新增資產或更新現有資產，請點選「新 **[!UICONTROL 增資產」]**。 導覽至資產，選取資產，然後點選 **[!UICONTROL 右上]** 角附近的「選取」。
如果您將AEM用縮圖取代為其他影像，以刪除該縮圖所使用的影像，原始資產仍會顯示。
   * 若要刪除資產，請選取資產並點選「刪 **[!UICONTROL 除資產」]**。
   * 若要套用預設，請點選「預 **[!UICONTROL 設」圖示]** ，然後選取預設。
   * 要刪除整個回轉集，請導航至回轉集，選擇它，然後選擇刪 **[!UICONTROL 除]**

      >[!NOTE]
      >* You can edit the images in a Spin Set by navigating to the set, tap **[!UICONTROL Set Members]** in the left rail, and then tap the **[!UICONTROL Edit]** (pencil icon) on an individual asset to open the editing window.


1. 完成編 **[!UICONTROL 輯時]** ，按一下「儲存」。

## 預覽回轉集 {#previewing-spin-sets}

請參閱 [預覽資產](previewing-assets.md)。

## 發佈回轉集 {#publishing-spin-sets}

請參閱 [發佈資產](publishing-dynamicmedia-assets.md)。

---
title: 迴轉集
description: 了解如何使用Dynamic Media中的回轉集。 「回轉集」(Spin Set)模擬旋轉對象的真實行為，從任何角度檢查對象。
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: 47cb6d40-a5c4-4f6a-9794-bd2eddfaa7d0
feature: Spin Sets
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1959'
ht-degree: 6%

---

# 迴轉集 {#spin-sets}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

回轉集模擬轉動物件的真實行為，以檢查物件。 「回轉集」可讓您從任何角度檢視項目，從任何角度取得關鍵的視覺詳細資訊。

回轉集可模擬360度的檢視體驗。 Dynamic Media提供單軸回轉集，供檢視器旋轉項目。 此外，使用者只需按幾下滑鼠，即可「自由格式」縮放及平移任何檢視。 這樣，用戶可以從特定角度更仔細地檢查項目。

回轉集由包含單字的橫幅指定 **[!UICONTROL SPINSET]**. 此外，如果回轉集已發佈，則會是發佈日期(以 **[!UICONTROL 世界]** 圖示會與上次修改日期一起顯示在橫幅上，以 **[!UICONTROL 鉛筆]** 圖示。

![chlimage_1-380](assets/chlimage_1-380.png)

>[!NOTE]
>
>如需Assets使用者介面的資訊，請參閱 [使用觸控式UI管理資產](managing-assets-touch-ui.md).

當您建立回轉集時，Adobe會建議下列最佳作法並強制執行下列限制：

| 限制類型 | 最佳實務 | 限制 |
| --- | --- | --- |
| 每2D集的最大行/列數 | 每組12-18頁圖片 | 1000 |

另請參閱 [Dynamic Media限制](/help/assets/limitations.md).

## 快速入門：回轉集 {#quick-start-spin-sets}

若要使用回轉集快速上手並執行，請依照以下工作流程操作：

1. [上傳多次檢視的影像。](#uploading-assets-for-spin-sets)

   一維自旋集至少需要8-12個項目的鏡頭，二維自旋集至少需要16-24個。 必須定期拍攝照片，以給人以項目正在旋轉和被翻轉的印象。 例如，如果一維度回轉集包含12個鏡頭，則對每個鏡頭將項目旋轉30度(360/12)。

1. [建立回轉集。](#creating-spin-sets)

   若要建立回轉集，請選取 **[!UICONTROL 建立>回轉集]** 然後為集合命名，選擇資產，然後依照影像的顯示順序來排序影像。

   請參閱 [使用選取器](working-with-selectors.md).

   >[!NOTE]
   >
   >您也可以透過 [批次集預設集](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).
   >
   >*批集由IPS(Image Production System)建立，作為資產提取的一部分，僅可在Dynamic Media - Scene7模式中使用*.

1. 設定 [回轉集檢視器預設集](managing-viewer-presets.md)，視需要。

   管理員可以建立或修改回轉集檢視器預設集。 若要檢視含有檢視器預設集的回轉集，請選取「回轉集」，然後在左側導軌下拉式選單中選取 **[!UICONTROL 檢視器]**.

   請參閱 **[!UICONTROL 「工具>資產>檢視器預設集」]** 來建立或編輯查看器預設集。

   請參閱 [新增和編輯檢視器預設集。](managing-viewer-presets.md)

1. [檢視回轉集](#viewing-spin-sets).

   您可以透過三種不同方式的批次集預設集來檢視和存取所建立的集。 (使用批集預設集建立的集，可 *not* 顯示在使用者介面中。)

1. [預覽回轉集。](previewing-assets.md)

   選取回轉集，即可預覽。 旋轉回轉集。 您可以從 **[!UICONTROL 檢視器]** 功能表（從左側欄下拉式功能表）。

1. [發佈回轉集。](publishing-dynamicmedia-assets.md)

   「發佈回轉集」會啟動影像在回轉集物料中的顯示順序。 請務必訂購，使回轉為360度的平滑檢視。**[!UICONTROL URL]** 和 **[!UICONTROL 內嵌]** 字串。 此外，您必須 [發佈檢視器預設集](managing-viewer-presets.md).

1. [將URL連結至您的Web應用程式](linking-urls-to-yourwebapplication.md) 或 [內嵌視訊或影像檢視器](embed-code.md).

   AEM Assets會建立回轉集的URL呼叫，並在您發佈回轉集後啟用它們。 您可以在預覽資產時複製這些URL。 或者，您也可以將它們嵌入您的網站。

   選取「回轉集」，然後在左側導軌下拉式選單中選取「檢 **[!UICONTROL 視器]**」。

   請參 [閱將回轉集連結至網頁](linking-urls-to-yourwebapplication.md)[和內嵌視訊或影像檢視器](embed-code.md)。

如果需要，您可以 [編輯回轉集](#editing-spin-sets). 此外，您也可以檢視及編輯 [回轉集屬性](managing-assets-touch-ui.md#editing-properties).

## 上傳回轉集的資產 {#uploading-assets-for-spin-sets}

一維自旋集至少需要8-12個項目的鏡頭，二維自旋集至少需要16-24個。 必須定期拍攝照片，以給人以項目正在旋轉和被翻轉的印象。 例如，如果一維度回轉集包含12個鏡頭，則對每個鏡頭將項目旋轉30度(360/12)。

您可以像上傳一樣上傳回轉集的影像 [上傳AEM Assets中的任何其他資產](managing-assets-touch-ui.md).

### 拍攝回轉集影像的准則 {#guidelines-for-shooting-spin-set-images}

以下是回轉集影像的一些最佳實務。 一般而言，旋轉集中的影像越多，影像旋轉效果就越好。 但是，集合中包含許多影像也會增加影像載入所花費的時間。 AEM建議在回轉集中拍攝影像時使用下列准則：

* 至少在一維回轉集中使用8-12個影像，在二維回轉集中使用16-24個影像。 至少需要8張影像才能使旋轉360度。 一維回轉集較常見，因為建立二維回轉集需耗費大量人力。
* 使用無損格式；建議使用TIFF和PNG。
* 遮罩所有影像，使項目出現在純白色或其他高對比背景上。 （可選）添加陰影。
* 請確定產品詳細資訊清晰明瞭，且清晰明瞭。
* 給裝模特或模特的時尚服裝拍照。 通常，人體模型要麼是完全遮罩的（使用玻璃人體模型），要麼是影像中顯示了造型化的人體模型/服裝。 通過定義角度數，可以建立模型上的回轉集。 在地板上用膠帶標出每個角度，以引導模型向各拍攝方向走動和查看。

## 建立回轉集 {#creating-spin-sets}

影像在回轉集中的顯示順序。 請務必訂購，使回轉為360度的平滑檢視。

>[!NOTE]
>
>您也可以透過批次集預設集自動 [建立回轉集](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)。
>
>批集由IPS(Image Production System)建立，作為資產提取的一部分，僅可在Dynamic Media - Scene7模式中使用。
>
>請參閱以下主題中的「建立批集預設集以自動產生影像集和回轉集」： [設定Dynamic Media - Scene7模式](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).

當您建立回轉集時，Adobe會建議下列最佳作法並強制執行下列限制：

| 限制類型 | 最佳實務 | 限制 |
| --- | --- | --- |
| 每2D集的最大行/列數 | 每組12-18頁圖片 | 1000 |

另請參閱 [Dynamic Media限制](/help/assets/limitations.md).

**若要建立回轉集：**

1. 在「資產」中，導覽至您要建立回轉集的位置，點選 **[!UICONTROL 建立]**，然後選取 **[!UICONTROL 回轉集]**. 您也可以從包含資產的資料夾內建立資產集。

   ![chlimage_1-381](assets/chlimage_1-381.png)

1. 在 **[!UICONTROL 回轉集編輯器]** 頁面，在 **[!UICONTROL 標題]** 欄位，輸入回轉集的名稱。 名稱會顯示在回轉集的橫幅中。 （可選）輸入說明。

   ![chlimage_1-382](assets/chlimage_1-382.png)

   當您建立回轉集時，可以變更回轉集縮圖，或允許AEM根據回轉集中的資產自動選取縮圖。 若要選取縮圖，請點選 **[!UICONTROL 變更縮圖]**.選取任何影像（您也可以導覽至其他資料夾以尋找影像）。 如果您已選取縮圖，然後決定要讓AEM從回轉集產生縮圖，請選取 **[!UICONTROL 切換為自動縮圖]**.

1. 執行下列任一操作：

   * 在 **[!UICONTROL 回轉集編輯器]** 頁面，點選 **[!UICONTROL 新增資產]**.
   * 在 **[!UICONTROL 回轉集編輯器]** 頁面，點選 **[!UICONTROL 點選以開啟資產選擇器]**.

   點選以選取您要納入回轉集的資產。 選取的資產上面有核取標籤圖示。完成後，在頁面右上角附近點選 **[!UICONTROL 選擇]**.

   使用「資產選擇器」，您可以輸入關鍵字並點選「回報」來搜尋 **[!UICONTROL 資產]**。您也可以套用篩選條件來調整搜尋結果。您可以依路徑、系列、檔案類型和標籤來篩選。選取篩選，然後點選工具 **[!UICONTROL 列上的]** 「篩選」圖示。若要變更檢視，在頁面右上角附近，點選 **[!UICONTROL 檢視]** 圖示，然後點選 **[!UICONTROL 欄檢視]**, **[!UICONTROL 卡片檢視]**，或 **[!UICONTROL 清單檢視]**.

   請參閱 [使用選取器](working-with-selectors.md).

   ![chlimage_1-383](assets/chlimage_1-383.png)

1. 將資產新增至資產集時，資產會以英數字元順序自動新增。 新增資產後，您可以手動重新排序或排序資產。 如有必要，請拖曳資產的 **[!UICONTROL 重新排序]** 圖示（位於資產檔案名稱的右側），以在設定清單上或下重新排序影像。

   ![spin_set_assets6-4](assets/spin_set_assets6-4.png)

1. （選用）執行下列任一操作：

   * 若要刪除影像，請選取影像，然後點選 **[!UICONTROL 刪除資產]**.
   * 若要套用預設集，在頁面右上角附近，點選 **[!UICONTROL 預設集]**，然後選取要一次套用至所有資產的預設集。

1. 點選 **[!UICONTROL 儲存]**. 新建立的回轉集會顯示在建立該回轉集的資料夾中。

## 檢視回轉集 {#viewing-spin-sets}

您可以在使用者介面中建立回轉集，或自動使用 [批次集預設集](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets). 但是，使用批集預設集建立的集，請執行 *not* 顯示在使用者介面中。 您可以透過三種不同方式的批次集預設集來存取由建立的集。 （即使您在使用者介面中建立回轉集，這些方法仍可供使用）。

您也可以透過使用者介面來檢視集，如 [編輯回轉集](#editing-spin-sets).

**若要檢視回轉集：**

1. 開啟個別資產的屬性時。 屬性會指出選取資產是的成員的設定(位於 **[!UICONTROL 集的成員]**)。 點選集的名稱即可查看整個集。

   ![chlimage_1-384](assets/chlimage_1-384.png)

1. 來自任何組的成員映像。選取 **[!UICONTROL 集]** 功能表來顯示資產所屬的集。

   ![chlimage_1-385](assets/chlimage_1-385.png)

1. 在搜尋中，您可以選取 **[!UICONTROL 篩選器]**，然後展開 **[!UICONTROL Dynamic Media]** 選取 **[!UICONTROL 集]**.

   搜索返回在用戶介面中手動建立的匹配集，或通過批集預設集自動建立的匹配集。 對於自動化集，搜尋查詢是使用 **[!UICONTROL 開頭為]** 與AEM搜尋不同的搜尋條件，此搜尋是根據 **[!UICONTROL 包含]** 搜尋條件。 將篩選器設定為 **[!UICONTROL 集]** 是搜尋自動化集的唯一方式。

   ![chlimage_1-386](assets/chlimage_1-386.png)

## 編輯回轉集 {#editing-spin-sets}

您可以對回轉集執行各種編輯工作，例如：

* 將影像新增至回轉集。
* 重新排序回轉集中的影像。
* 刪除回轉集中的資產。
* 套用檢視器預設集。
* 刪除回轉集。

**若要編輯回轉集：**

1. 執行下列任一操作：

   * 將游標暫留在回轉集資產上，然後點選 **[!UICONTROL 編輯]** （鉛筆圖示）。
   * 將游標暫留在回轉集資產上，點選 **[!UICONTROL 選擇]** （勾選圖示），然後點選 **[!UICONTROL 編輯]** 的上界。
   * 點選回轉集資產，然後點選 **[!UICONTROL 編輯]** （鉛筆圖示）。

1. 若要編輯回轉集，請執行下列任一操作：

   * 若要重新排序影像，請拖曳影像至新位置（選取重新排序圖示以移動項目）。
   * 若要以遞增或遞減順序排序項目，請點選欄標題。
   * 若要新增資產或更新現有資產，請點選 **[!UICONTROL 新增資產]**. 導覽至資產，選取資產，然後點選 **[!UICONTROL 選擇]** 在右上角。
如果您以其他影像取代縮圖，以刪除AEM用於縮圖的影像，仍會顯示原始資產。
   * 若要刪除資產，請選取資產並點選 **[!UICONTROL 刪除資產]**.
   * 若要套用預設集，請點選 **[!UICONTROL 預設集]** 圖示並選取預設集。
   * 若要刪除整個回轉集，請導覽至該回轉集，選取它，然後選取 **[!UICONTROL 刪除]**

      >[!NOTE]
      >* 您可以導覽至回轉集，點選以編輯該回轉集中的影像 **[!UICONTROL 設定成員]** 在左側邊欄中，然後點選 **[!UICONTROL 編輯]** （鉛筆圖示）以開啟編輯視窗。


1. 按一下 **[!UICONTROL 儲存]** 編輯完畢。

## 預覽回轉集 {#previewing-spin-sets}

請參閱 [預覽資產](previewing-assets.md).

## 發佈回轉集 {#publishing-spin-sets}

請參閱 [發佈資產](publishing-dynamicmedia-assets.md).

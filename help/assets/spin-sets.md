---
title: 迴轉集
description: 瞭解如何使用Dynamic Media的Spin Sets。 「旋轉集」(Spin Set)模擬轉動對象以從任何角度檢查對象的真實行為。
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: 47cb6d40-a5c4-4f6a-9794-bd2eddfaa7d0
feature: Spin Sets
role: User
source-git-commit: 77b2643c91092a9a08b67fb5ad06a96a79f4deea
workflow-type: tm+mt
source-wordcount: '1923'
ht-degree: 6%

---

# 迴轉集 {#spin-sets}

「旋轉集」(Spin Set)模擬轉動對象以檢查對象的真實行為。 「旋轉集」(Spin Sets)允許從任何角度查看項目，從任何角度獲取關鍵可視詳細資訊。

「旋轉集」模擬360度的查看體驗。 Dynamic Media提供單軸旋轉集，查看者可以在其中旋轉項目。 此外，用戶只需點擊幾下滑鼠即可「自由格式」縮放和平移任何視圖。 這樣，用戶就可以從特定的角度更仔細地檢查項目。

「旋轉集」由帶單詞的標題指定 **[!UICONTROL 旋轉集]**。 此外，如果發佈了旋轉集，則發佈日期由 **[!UICONTROL 世界]** 表徵圖與上次修改日期一起在標題上，由 **[!UICONTROL 鉛筆]** 表徵圖。

![chlimage_1-380](assets/chlimage_1-380.png)

>[!NOTE]
>
>有關Assets用戶介面的資訊，請參閱 [使用Touch UI管理資產](managing-assets-touch-ui.md)。

建立「旋轉集」時，Adobe建議採用以下最佳做法並強制實施以下限制：

| 限制類型 | 最佳實踐 | 強加的限制 |
| --- | --- | --- |
| 每2D集的最大行/列數 | 每組12-18頁圖片 | 1000 |

另請參閱 [Dynamic Media限制](/help/assets/limitations.md)。

## 快速啟動：旋轉集 {#quick-start-spin-sets}

要使用「旋轉集」快速啟動並運行，請遵循以下工作流：

1. [上載多個視圖的影像。](#uploading-assets-for-spin-sets)

   對於一維自旋集，至少需要8-12個項的投影，對於二維自旋集，需要16-24個投影。 必須定期拍攝照片，以給出項目正在旋轉並被翻轉的印象。 例如，如果一維自旋集包含12個鏡頭，則對每個鏡頭旋轉項目30度(360/12)。

1. [建立旋轉集。](#creating-spin-sets)

   要建立旋轉集，請選擇 **[!UICONTROL 建立>旋轉集]** 然後命名集合，選擇資產，然後按照影像的顯示順序對影像進行排序。

   請參閱 [使用選擇器](working-with-selectors.md)。

   >[!NOTE]
   >
   >也可通過 [批集預設](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)。
   >
   >*批集由IPS（映像生產系統）建立，作為資產接收的一部分，僅在Dynamic Media-Scene7模式下可用*。

1. 設定 [旋轉集查看器預設](managing-viewer-presets.md)，根據需要。

   管理員可以建立或修改「旋轉集查看器」預設。 要使用查看器預設查看旋轉集，請選擇「旋轉集」，然後在左欄下拉菜單中選擇 **[!UICONTROL 查看者]**。

   請參閱 **[!UICONTROL 「工具」>「資產」>「查看器預設」]** 建立或編輯查看器預設。

   請參閱 [添加和編輯查看器預設。](managing-viewer-presets.md)

1. [查看旋轉集](#viewing-spin-sets)。

   可以以三種不同方式查看和訪問通過批集預設建立的集。 (使用批集預設建立的集，確定 *不* 顯示在用戶介面中。)

1. [預覽旋轉集。](previewing-assets.md)

   選擇「旋轉集」(Spin Set)，可預覽它。 旋轉旋轉集。 您可以從 **[!UICONTROL 查看者]** 菜單開啟它。

1. [發佈旋轉集。](publishing-dynamicmedia-assets.md)

   發佈旋轉集將激活影像在旋轉集物質中出現的順序。 請務必訂購它們，使旋轉為360度的平滑視圖。**[!UICONTROL URL]** 和 **[!UICONTROL 嵌入]** 的下界。 此外，您必須 [發佈查看器預設](managing-viewer-presets.md)。

1. [將URL連結到Web應用程式](linking-urls-to-yourwebapplication.md) 或 [嵌入視頻或影像查看器](embed-code.md)。

   AEM Assets為「旋轉集」建立URL調用，並在發佈「旋轉集」後激活它們。 您可以在預覽資產時複製這些URL。 或者，您也可以將它們嵌入到您的網站中。

   選取「回轉集」，然後在左側導軌下拉式選單中選取「檢 **[!UICONTROL 視器]**」。

   請參 [閱將回轉集連結至網頁](linking-urls-to-yourwebapplication.md)[和內嵌視訊或影像檢視器](embed-code.md)。

如果你需要，你可以 [編輯旋轉集](#editing-spin-sets)。 此外，您還可以查看和編輯 [旋轉集屬性](managing-assets-touch-ui.md#editing-properties)。

## 上載旋轉集的資產 {#uploading-assets-for-spin-sets}

對於一維自旋集，至少需要8-12個項的投影，對於二維自旋集，需要16-24個投影。 必須定期拍攝照片，以給出項目正在旋轉並被翻轉的印象。 例如，如果一維自旋集包含12個鏡頭，則對每個鏡頭旋轉項目30度(360/12)。

可以像上載一樣上載旋轉集的影像 [上傳任何其他資產到AEM Assets](managing-assets-touch-ui.md)。

### 拍攝旋轉集影像的准則 {#guidelines-for-shooting-spin-set-images}

以下是圍繞旋轉集映像的一些最佳做法。 通常，「旋轉集」中的影像越多，影像旋轉效果越好。 但是，在集合中包含許多影像也會增加載入影像所花的時間。 AEM建議在旋轉集中使用拍攝影像的以下准則：

* 至少在一維自旋集中使用8-12個影像，在二維自旋集中使用16-24個影像。 至少需要8張影像才能旋轉360度。 由於建立二維自旋集需要耗費大量人力，因此一維自旋集更為常見。
* 使用無損格式；建議使用TIFF和PNG。
* 遮罩所有影像，使項目出現在純白色或其它高對比度背景上。 （可選）添加陰影。
* 確保產品詳細資訊亮點良好，並集中注意。
* 為時尚服裝製作假人或模特的假象。 通常，人體模型要麼完全蒙版（使用玻璃人體模型），要麼在影像中顯示一個風格化的人體模型/服裝。 通過定義角度數，可建立模型上的旋轉集。 用底板上的磁帶標籤每個角度，以引導模型向每個鏡頭的方向步進和查看。

## 建立旋轉集 {#creating-spin-sets}

影像在自旋集中出現的順序。 請務必訂購它們，使旋轉為360度的平滑視圖。

>[!NOTE]
>
>您也可以透過批次集預設集自動 [建立回轉集](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)。
>
>批集由IPS（映像生產系統）建立，作為資產接收的一部分，並且僅在Dynamic Media-Scene7模式下可用。
>
>請參閱中的「建立批集預設以自動生成影像集和旋轉集」 [配置Dynamic Media-Scene7模式](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)。

建立「旋轉集」時，Adobe建議採用以下最佳做法並強制實施以下限制：

| 限制類型 | 最佳實踐 | 強加的限制 |
| --- | --- | --- |
| 每2D集的最大行/列數 | 每組12-18頁圖片 | 1000 |

另請參閱 [Dynamic Media限制](/help/assets/limitations.md)。

**要建立旋轉集：**

1. 在資產中，導航到要建立旋轉集的位置，點擊 **[!UICONTROL 建立]**，然後選擇 **[!UICONTROL 旋轉集]**。 您也可以從包含資產的資料夾內建立資產集。

   ![chlimage_1-381](assets/chlimage_1-381.png)

1. 在 **[!UICONTROL 旋轉集編輯器]** 的 **[!UICONTROL 標題]** 欄位中，輸入「旋轉集」的名稱。 該名稱出現在「旋轉集」的標題中。 （可選）輸入說明。

   ![chlimage_1-382](assets/chlimage_1-382.png)

   建立旋轉集時，可以更改旋轉集縮略圖，AEM或允許根據旋轉集中的資產自動選擇縮略圖。 要選擇縮略圖，請點擊 **[!UICONTROL 更改縮略圖]**。選擇任何影像（您也可以導航到其他資料夾以查找影像）。 如果已選擇縮略圖，然後決定要從旋AEM轉集生成縮略圖，請選擇 **[!UICONTROL 切換到自動縮略圖]**。

1. 執行下列任一操作：

   * 靠近 **[!UICONTROL 旋轉集編輯器]** 頁面，點擊 **[!UICONTROL 添加資產]**。
   * 靠近中部 **[!UICONTROL 旋轉集編輯器]** 頁面，點擊 **[!UICONTROL 點擊以開啟資產選擇器]**。

   點擊以選擇要包括在旋轉集中的資產。 選取的資產上面有核取標籤圖示。完成後，在頁面右上角附近點擊 **[!UICONTROL 選擇]**。

   使用「資產選擇器」，您可以輸入關鍵字並點選「回報」來搜尋 **[!UICONTROL 資產]**。您也可以套用篩選條件來調整搜尋結果。您可以依路徑、系列、檔案類型和標籤來篩選。選取篩選，然後點選工具 **[!UICONTROL 列上的]** 「篩選」圖示。要更改視圖，請在頁面右上角附近按一下 **[!UICONTROL 視圖]** 表徵圖 **[!UICONTROL 列視圖]**。 **[!UICONTROL 卡視圖]**&#x200B;或 **[!UICONTROL 清單視圖]**。

   請參閱 [使用選擇器](working-with-selectors.md)。

   ![chlimage_1-383](assets/chlimage_1-383.png)

1. 在將資產添加到集時，系統會按字母數字順序自動添加這些資產。 添加資產後，您可以手動重新排序或排序資產。 如有必要，拖動資產 **[!UICONTROL 重新排序]** 表徵圖，在設定清單上或下重新排序影像。

   ![spin_set_assets6-4](assets/spin_set_assets6-4.png)

1. （可選）執行下列任一操作：

   * 要刪除影像，請選擇影像，然後點擊 **[!UICONTROL 刪除資產]**。
   * 要應用預設，請點擊靠近頁面右上角的 **[!UICONTROL 預設]**，然後選擇一個預設以立即應用於所有資產。

1. 點擊 **[!UICONTROL 保存]**。 新建立的「旋轉集」(Spin Set)將出現在建立它的資料夾中。

## 查看旋轉集 {#viewing-spin-sets}

可以在用戶介面中或自動使用 [批集預設](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)。 但是，使用批集預設建立的集，請執行 *不* 在用戶介面中。 可以以三種不同方式訪問通過批集預設建立的集。 （即使在用戶介面中建立了「旋轉集」，這些方法也可用）。

也可以通過用戶介面查看集，如中所述 [編輯旋轉集](#editing-spin-sets)。

**要查看旋轉集：**

1. 開啟單個資產的屬性時。 屬性指明選定資產是的成員(在 **[!UICONTROL 集的成員]**)。 按一下集的名稱可查看整個集。

   ![chlimage_1-384](assets/chlimage_1-384.png)

1. 來自任何組的成員映像。選擇 **[!UICONTROL 集]** 的子菜單。

   ![chlimage_1-385](assets/chlimage_1-385.png)

1. 在搜索中，您可以選擇 **[!UICONTROL 篩選器]**，然後展開 **[!UICONTROL Dynamic Media]** 選擇 **[!UICONTROL 集]**。

   搜索返回在用戶介面中手動建立或通過批處理集預設自動建立的匹配集。 對於自動集，搜索查詢使用 **[!UICONTROL 開始於]** 與基於使用的AEM搜索不同的搜索標準 **[!UICONTROL 包含]** 搜索條件。 將篩選器設定為 **[!UICONTROL 集]** 是搜索自動集的唯一方法。

   ![chlimage_1-386](assets/chlimage_1-386.png)

## 編輯旋轉集 {#editing-spin-sets}

可以對旋轉集執行多種編輯任務，如：

* 將影像添加到旋轉集。
* 重新排序旋轉集中的影像。
* 刪除旋轉集中的資產。
* 應用查看器預設。
* 刪除旋轉集。

**編輯旋轉集：**

1. 執行下列任一操作：

   * 將滑鼠懸停在Spin Set資產上，然後點擊 **[!UICONTROL 編輯]** （鉛筆表徵圖）。
   * 將滑鼠懸停在旋轉集資產上，點擊 **[!UICONTROL 選擇]** （複選標籤表徵圖），然後點擊 **[!UICONTROL 編輯]** 的上界。
   * 點按Spin Set資產，然後點按 **[!UICONTROL 編輯]** 表徵圖)。

1. 要編輯「旋轉集」，請執行以下任一操作：

   * 要重新排序影像，請將影像拖到新位置（選擇重新排序表徵圖以移動項目）。
   * 要按升序或降序對項排序，請點擊列標題。
   * 要添加資產或更新現有資產，請點擊 **[!UICONTROL 添加資產]**。 導航到某個資產，選擇它，然後點擊 **[!UICONTROL 選擇]** 靠近右上角。
如果通過將縮略圖替換AEM為另一個影像來刪除用於縮略圖的影像，則仍會顯示原始資產。
   * 要刪除資產，請選擇該資產並點擊 **[!UICONTROL 刪除資產]**。
   * 要應用預設，請點擊 **[!UICONTROL 預設]** 表徵圖，然後選擇預設。
   * 要刪除整個旋轉集，請導航到旋轉集，選擇它，然後選擇 **[!UICONTROL 刪除]**

      >[!NOTE]
      >* 通過導航至「旋轉集」，可編輯該集中的影像，點擊 **[!UICONTROL 設定成員]** 在左欄上，然後點擊 **[!UICONTROL 編輯]** （鉛筆表徵圖），開啟編輯窗口。


1. 按一下 **[!UICONTROL 保存]** 編輯。

## 預覽旋轉集 {#previewing-spin-sets}

請參閱 [預覽資產](previewing-assets.md)。

## 發佈旋轉集 {#publishing-spin-sets}

請參閱 [發佈資產](publishing-dynamicmedia-assets.md)。

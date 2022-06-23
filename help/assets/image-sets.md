---
title: 影像集
seo-title: Image Sets
description: 瞭解如何在動態媒體中使用映像集
seo-description: Learn how to work with image sets in dynamic media
uuid: 16008278-f59f-4fa8-90e9-19c78f132439
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e00e7cc9-b777-4f9e-906d-824bcb2bbd41
exl-id: af3f95aa-a162-4212-a20a-68b5a0e72d6d
feature: Image Sets
role: User
source-git-commit: 77b2643c91092a9a08b67fb5ad06a96a79f4deea
workflow-type: tm+mt
source-wordcount: '2146'
ht-degree: 11%

---

# 影像集 {#image-sets}

「影像集」為用戶提供了整合的查看體驗，用戶可以通過按一下縮略圖來查看項目的不同視圖。 「影像集」(Image Sets)允許您顯示項目的替代視圖，而查看器提供了縮放工具，用於仔細檢查影像。

影像集由帶字的標題指定 **[!UICONTROL 映像集]**。 此外，如果已發佈影像集，則會顯示以 **[!UICONTROL World]** 圖示表示的發佈日期與上次修改日期(以 **** Pencil圖示表示)在橫幅上。

![chlimage_1-339](assets/chlimage_1-339.png)

在影像集中，還可以通過建立影像集和添加縮略圖來建立色板。

當您希望以不同顏色、圖案或完成顯示項目時，此應用程式特別有用。 要使用顏色色板建立影像集，您需要為要向用戶呈現的每種不同顏色、圖案或完成一幅影像。 每種顏色、圖案或光潔度還需要一個顏色、圖案或光潔度色板。

例如，假設您要顯示具有不同顏色鈔票的大寫影像；賬單是紅的，綠的，藍的。 在這個例子中，你需要三針相同的帽子。 你需要一張紅的，一張綠的，一張藍的。 還需要紅色、綠色和藍色色板。 顏色色板用作縮略圖，用戶在「色板集查看器」中按一下該縮略圖，以查看紅色開單、綠色開單或藍色開單的帽。

>[!NOTE]
>
>有關Assets用戶介面的資訊，請參閱 [使用Touch UI管理資產](managing-assets-touch-ui.md)。

建立映像集時，Adobe建議採用以下最佳做法並強制實施以下限制：

| 限制類型 | 最佳實踐 | 強加的限制 |
| --- | --- | --- |
| 每集重複的資產數 | 無重複項 | 20 |
| 每集的最大影像數 | 每組5-10頁影像 | 1000 |

另請參閱 [Dynamic Media限制](/help/assets/limitations.md)。

## 快速啟動：影像集 {#quick-start-image-sets}

要快速啟動並運行：

1. [上載多個視圖的主映像。](#uploading-assets-in-image-sets)

   首先上載映像集的映像。 由於用戶可以在「影像集查看器」中放大影像，因此在選擇影像時需要考慮放大。 確保影像在最大尺寸中至少為2000像素，以便獲得最佳縮放細節。 Dynamic Media可以每張2500萬像素的影像。 例如，您可以使用5000 x 5000兆像素影像或任何其他大小的組合，最多2500萬像素。

   AEM Assets支援多種影像檔案格式，但建議使用無損TIFF、PNG和EPS影像。

1. [建立映像集。](#creating-image-sets)

   在「影像集」中，用戶按一下「影像集查看器」中的縮略圖。

   要在資產中建立映像集，請點擊 **[!UICONTROL 建立>影像集]**。 然後，添加影像並點擊 **[!UICONTROL 保存]**。

   還可以通過 [批集預設](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)。

   **重要**  — 批集由IPS（映像生產系統）建立，作為資產接收的一部分，並且僅在Dynamic Media-Scene7模式下可用。

   請參閱 [準備映像集資產以上載和上載檔案](#uploading-assets-in-image-sets)。

   請參閱 [使用選擇器。](working-with-selectors.md)

1. 添加 [影像集查看器預設](managing-viewer-presets.md)，根據需要。

   管理員可以建立或修改映像 **[!UICONTROL 設定查看器預設]**。 要使用查看器預設查看影像集，請選擇影像集，然後在左欄下拉菜單中選擇 **[!UICONTROL 查看者]**。

   請參閱 **[!UICONTROL 「工具」>「資產」>「查看器預設」]** 建立或編輯查看器預設。

1. （可選） [查看影像集](image-sets.md#viewing-image-sets) 是使用批集預設建立的。
1. [預覽影像集。](previewing-assets.md)

   選擇「影像集」(Image Set)，您可以預覽它。 點擊縮略圖表徵圖檢查選定查看器中的影像集。 您可以從 **[!UICONTROL 查看者]** 菜單開啟它。

1. [發佈映像集。](publishing-dynamicmedia-assets.md)

   發佈影像集將激活URL和嵌入字串。 此外，您必須 [發佈任何自定義查看器預設](managing-viewer-presets.md) 你創造的。 已發佈現成查看器預設。

1. [將URL連結到Web應用程式](linking-urls-to-yourwebapplication.md) 或 [嵌入視頻或影像查看器](embed-code.md)。

   AEM Assets會建立映像集的URL調用，並在您發佈映像集後激活它們。 您可以在預覽資產時複製這些URL。 或者，您也可以將它們嵌入到您的網站中。

   選取「影像集」，然後在左側導軌下拉式選單中選取「檢 **[!UICONTROL 視器]**」。

   請參 [閱連結影像集至網頁](linking-urls-to-yourwebapplication.md)[和內嵌影片或影像檢視器](embed-code.md)。

要編輯映像集，請參閱 [編輯影像集。](#editing-image-sets) 此外，您還可以查看和編輯 [影像集屬性](managing-assets-touch-ui.md#editing-properties)。

如果建立集時遇到問題，請參閱中的影像和集 [診斷Dynamic Media-Scene7模式](troubleshoot-dms7.md#images-and-sets)。

## 在映像集中上載資產 {#uploading-assets-in-image-sets}

首先上載映像集的映像。 由於用戶可以在「影像集查看器」中放大影像，因此在選擇影像時需要考慮放大。 請確定影像在最大尺寸中至少為2000像素。影像集支援多種影像檔案格式，但建議使用無損TIFF、PNG和EPS影像。

可以像您一樣上載映像集的映像 [上載資產中的任何其他資產](managing-assets-touch-ui.md#uploading-assets)。

### 準備映像集資產以供上載 {#preparing-image-set-assets-for-upload}

在建立映像集之前，請確保映像的大小和格式正確。

要建立多視圖影像集，需要顯示來自不同視點的項目或顯示同一項目不同方面的影像。 其目標是突出顯示項目的重要功能，以便查看者能夠完整瞭解項目的外觀或行為。

因為用戶可以在影像集中縮放影像，所以請確保影像在最大尺寸中至少為2000像素。 資產支援多種影像檔案格式，但建議使用無損TIFF、PNG和EPS影像。

>[!NOTE]
>
>此外，如果使用縮略圖來指示產品色板，則需要執行以下操作：
>
>您需要使用小畫或同一影像的不同鏡頭，以不同的顏色、圖案或結束顯示。 您還需要與不同顏色、圖案或結束相對應的縮略圖檔案。 例如，要顯示縮略圖，並且影像集以黑色、棕色和綠色顯示同一夾克，您需要：
>
>* 同一件夾克的黑色，棕色和綠色。
>* 黑色、棕色和綠色縮略圖。
>


## 建立映像集 {#creating-image-sets}

可通過用戶介面或通過API建立映像集。 本節介紹如何在用戶介面中建立映像集。

>[!NOTE]
>
>還可以通過 [批集預設](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)。

**重要提示：** 批集由IPS（映像生產系統）建立，作為資產接收的一部分，並且僅在Dynamic Media-Scene7模式下可用。

在將資產添加到集時，系統會按字母數字順序自動添加這些資產。 添加資產後，您可以手動重新排序或排序資產。

>[!NOTE]
>
>不支援具有 `,` （逗號）。

建立映像集時，Adobe建議採用以下最佳做法並強制實施以下限制：

| 限制類型 | 最佳實踐 | 強加的限制 |
| --- | --- | --- |
| 每集重複的資產數 | 無重複項 | 20 |
| 每集的最大影像數 | 每組5-10頁影像 | 1000 |

另請參閱 [Dynamic Media限制](/help/assets/limitations.md)。

**建立影像集**:

1. 在 **資產**，導航至要建立影像集的位置，點擊 **[!UICONTROL 建立]**，然後選擇 **[!UICONTROL 影像集]**。 您也可以從包含資產的資料夾內建立資產集。

   ![chlimage_1-340](assets/chlimage_1-340.png)

1. 在「影像集編輯器」頁上， **[!UICONTROL 標題]** 欄位中，輸入影像集的名稱。 該名稱出現在影像集的標題中。 （可選）輸入說明。

   ![chlimage_1-341](assets/chlimage_1-341.png)

   >[!NOTE]
   >
   >建立影像集時，您可以變更影像集縮圖，或允許AEM根據影像集中的資產自動選取縮圖。要選擇縮略圖，請點擊 **[!UICONTROL 更改縮略圖]** 並選擇任何影像（您也可以導航到其他資料夾以查找影像）。 如果您已選取縮圖，然後決定要讓AEM從影像集產生縮圖，請選取「切換至 **[!UICONTROL 自動縮圖」]**。

1. 執行下列任一操作：

   * 靠近 **[!UICONTROL 影像集編輯器]** 頁面，點擊 **[!UICONTROL 添加資產]**。
   * 靠近中部 **[!UICONTROL 影像集編輯器]** 頁面，點擊 **[!UICONTROL 點擊以開啟資產選擇器]**。

   點擊以選擇要包括在映像集中的資產。 選取的資產上面有核取標籤圖示。完成後，在頁面右上角附近點擊 **[!UICONTROL 選擇]**。

   使用「資產選擇器」，您可以輸入關鍵字並點選「回報」來搜尋 **[!UICONTROL 資產]**。您也可以套用篩選條件來調整搜尋結果。您可以依路徑、系列、檔案類型和標籤來篩選。選取篩選，然後點選工具 **[!UICONTROL 列上的]** 「篩選」圖示。通過點擊 **[!UICONTROL 視圖]** 表徵圖和選擇 **[!UICONTROL 列視圖]**。 **[!UICONTROL 卡視圖]**&#x200B;或 **[!UICONTROL 清單視圖]**。

   請參閱 [使用選擇器。](working-with-selectors.md)

   ![chlimage_1-342](assets/chlimage_1-342.png)

1. 在將資產添加到集時，系統會按字母數字順序自動添加這些資產。 添加資產後，您可以手動重新排序或排序資產。

   如有必要，拖動資產 **[!UICONTROL 重新排序]** 表徵圖，在設定清單上或下重新排序影像。

   ![spin_set_assets](assets/spin_set_assets.png)

   如果要更改縮略圖或色板，請點擊 **[!UICONTROL 縮略圖]** 表徵圖，然後導航到所需的縮略圖或色板。 選擇完所有影像點擊後 **[!UICONTROL 保存]**。

1. （可選）執行下列任一操作：

   * 要刪除影像，請選擇影像，然後點擊 **[!UICONTROL 刪除資產]**。
   * 要應用預設，請點擊靠近頁面右上角的 **[!UICONTROL 預設]**，然後選擇一個預設以立即應用於所有資產。

1. 點擊 **[!UICONTROL 保存]**。 您新建立的映像集將顯示在您建立的資料夾中。

## 查看影像集 {#viewing-image-sets}

可以在用戶介面中建立影像集或自動使用 [批集預設](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)。

**重要**  — 批集由IPS建立 [影像生成系統] 作為資產攝取的一部分，僅在Dynamic Media-Scene7模式下提供。)

但是，使用批集預設建立的集，請執行 *不* 在用戶介面中。 您可以用三種不同的方式查看這些集。 （即使您在用戶介面中建立了影像集，這些方法也可用）。

* 開啟單個資產的屬性時。 屬性指明選定資產是的成員(在 **[!UICONTROL 集的成員]**)。 按一下集的名稱可查看整個集。

   ![chlimage_1-343](assets/chlimage_1-343.png)

* 來自任何組的成員映像。選擇 **[!UICONTROL 集]** 的子菜單。

   ![chlimage_1-344](assets/chlimage_1-344.png)

* 在搜索中，您可以選擇 **[!UICONTROL 篩選器]**，然後展開 **[!UICONTROL Dynamic Media]** 選擇 **[!UICONTROL 集]**。

   搜索返回在UI中手動建立或通過批集預設自動建立的匹配集。 對於自動集，搜索查詢使用「開始於」搜索標準進行，該搜索標準與基於使用「包含」搜AEM索標準的搜索不同。 將篩選器設定為 **[!UICONTROL 集]** 是搜索自動集的唯一方法。

   ![chlimage_1-345](assets/chlimage_1-345.png)

>[!NOTE]
>
>您可以通過用戶介面查看集，如中所述 [編輯影像集](#editing-image-sets)。

## 編輯影像集 {#editing-image-sets}

可以對影像集執行多種編輯任務，如：

* 向映像集添加映像。
* 在影像集中重新排序影像。
* 刪除映像集中的資產。
* 應用查看器預設。
* 刪除映像集。

**編輯影像集**:

1. 執行下列任一操作：

   * 將滑鼠懸停在影像集資產上，然後點擊 **[!UICONTROL 編輯]** （鉛筆表徵圖）。
   * 將滑鼠懸停在影像集資產上，點擊 **[!UICONTROL 選擇]** （複選標籤表徵圖），然後點擊 **[!UICONTROL 編輯]** 的上界。
   * 點擊「Image Set（映像集）」資產，然後點擊 **[!UICONTROL 編輯]** 表徵圖)。

1. 要編輯「影像集」中的影像，請執行以下任一操作：

   * 要重新排序資產，請將影像拖到新位置（選擇重新排序表徵圖以移動項目）。
   * 要按升序或降序對項排序，請點擊列標題。
   * 要添加資產或更新現有資產，請點擊 **[!UICONTROL 添加資產]**。 導航到某個資產，選擇它，然後點擊 **[!UICONTROL 選擇]** 靠近頁面右上角。

   >[!NOTE]
   >如果通過將縮略圖替換AEM為另一個影像來刪除用於縮略圖的影像，則仍會顯示原始資產。

   * 要刪除資產，請選擇它，然後點擊 **[!UICONTROL 刪除資產]**。
   * 要應用預設，請點擊靠近頁面右上角的 **[!UICONTROL 預設]**，然後選擇查看器預設。
   * 要添加或更改縮略圖，請選擇資產右側旁邊的縮略圖表徵圖。 導航到新縮略圖或色板資產，選擇它，然後點擊 **[!UICONTROL 選擇]**。
   * 要刪除整個映像集，請導航到映像集，選擇它，然後點擊 **[!UICONTROL 刪除]**。

   >[!NOTE]
   >
   >您可以導覽至影像集，點選左側導軌中的「設定成員 **** 」，然後點選個別資產上的「鉛筆」圖示以開啟編輯視窗，以編輯影像集中的影像。****

1. 點擊 **[!UICONTROL 保存]** 編輯。

## 預覽影像集 {#previewing-image-sets}

請參閱 [預覽資產](previewing-assets.md)。

## 發佈映像集 {#publishing-image-sets}

請參閱 [發佈資產](publishing-dynamicmedia-assets.md)。

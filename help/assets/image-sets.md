---
title: 影像集
seo-title: Image Sets
description: 了解如何在Dynamic Media中使用影像集
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
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2182'
ht-degree: 11%

---

# 影像集 {#image-sets}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

影像集可為使用者提供整合的檢視體驗，讓使用者按一下縮圖影像即可看見項目的不同檢視。 「影像集」可讓您呈現項目的替代檢視，而檢視器提供縮放工具，以密切檢查影像。

影像集由具有單字的橫幅指定 **[!UICONTROL 影像集]**. 此外，如果已發佈影像集，則會顯示以 **[!UICONTROL World]** 圖示表示的發佈日期與上次修改日期(以 **** Pencil圖示表示)在橫幅上。

![chlimage_1-339](assets/chlimage_1-339.png)

在影像集內，您也可以建立「影像集」並新增縮圖來建立色票。

當您想要以不同顏色、模式或完成來顯示項目時，此應用程式特別有用。 要使用顏色色板建立影像集，需要為要呈現給用戶的不同顏色、圖案或完成建立一個影像。 每種顏色、圖樣或完成還需要一個顏色、圖樣或完成色板。

例如，假設您想要呈現具有不同顏色鈔票的大寫影像；賬單是紅色、綠色和藍色的。 在這個情況下，你需要三槍一槍。 你需要一張紅色的，一張綠色的，一張藍色的。 您也需要紅色、綠色和藍色色票。 顏色色板用作縮圖，用戶可在「色板集查看器」中按一下該縮圖，以查看紅色計費、綠色計費或藍色計費的帽子。

>[!NOTE]
>
>如需Assets使用者介面的資訊，請參閱 [使用觸控式UI管理資產](managing-assets-touch-ui.md).

當您建立影像集時，Adobe會建議下列最佳作法並強制執行下列限制：

| 限制類型 | 最佳實務 | 限制 |
| --- | --- | --- |
| 每組重複資產數 | 無重複項目 | 20 |
| 每組影像的最大數量 | 每組5-10頁影像 | 1000 |

另請參閱 [Dynamic Media限制](/help/assets/limitations.md).

## 快速入門：影像集 {#quick-start-image-sets}

快速啟動並運行：

1. [上傳多個檢視的主要影像。](#uploading-assets-in-image-sets)

   首先，上傳影像集的影像。 由於使用者可以在影像集檢視器中放大影像，因此當您選擇影像時，請考量放大比例。 請確定影像在最大尺寸中至少為2000像素，以獲得最佳縮放詳細資訊。 Dynamic Media可以每張2500萬像素的影像呈現。 例如，您可以使用5000 x 5000百萬像素影像或任何其它大小組合，最高2500萬像素。

   AEM Assets支援許多影像檔案格式，但建議使用無損TIFF、PNG和EPS影像。

1. [建立影像集。](#creating-image-sets)

   在「影像集」中，用戶按一下「影像集查看器」中的縮圖影像。

   若要在資產中建立影像集，請點選 **[!UICONTROL 建立>影像集]**. 然後，新增影像並點選 **[!UICONTROL 儲存]**.

   您也可以透過 [批次集預設集](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).

   **重要**  — 批集由IPS(Image Production System)建立，作為資產提取的一部分，僅在Dynamic Media - Scene7模式中可用。

   請參閱 [準備影像集資產以上傳和上傳您的檔案](#uploading-assets-in-image-sets).

   請參閱 [使用選取器。](working-with-selectors.md)

1. 新增 [影像集查看器預設集](managing-viewer-presets.md)，視需要。

   管理員可以建立或修改映像 **[!UICONTROL 設定檢視器預設集]**. 若要檢視您的影像集與檢視器預設集，請選取該影像集，然後在左側導軌下拉式選單中選取 **[!UICONTROL 檢視器]**.

   請參閱 **[!UICONTROL 「工具>資產>檢視器預設集」]** 來建立或編輯查看器預設集。

1. （可選） [檢視影像集](image-sets.md#viewing-image-sets) 使用批集預設集建立的。
1. [預覽影像集。](previewing-assets.md)

   選取「影像集」，即可預覽。 點選縮圖圖示以檢查所選檢視器中的影像集。 您可以從 **[!UICONTROL 檢視器]** 功能表（從左側欄下拉式功能表）。

1. [發佈影像集。](publishing-dynamicmedia-assets.md)

   「發佈影像集」會啟用URL和「內嵌」字串。 此外，您必須 [發佈任何自訂檢視器預設集](managing-viewer-presets.md) 已建立的。 已發佈現成可用的檢視器預設集。

1. [將URL連結至您的Web應用程式](linking-urls-to-yourwebapplication.md) 或 [內嵌視訊或影像檢視器](embed-code.md).

   AEM Assets會建立影像集的URL呼叫，並在您發佈影像集後啟用它們。 您可以在預覽資產時複製這些URL。 或者，您也可以將它們嵌入您的網站。

   選取「影像集」，然後在左側導軌下拉式選單中選取「檢 **[!UICONTROL 視器]**」。

   請參 [閱連結影像集至網頁](linking-urls-to-yourwebapplication.md)[和內嵌影片或影像檢視器](embed-code.md)。

若要編輯影像集，請參閱 [編輯影像集。](#editing-image-sets) 此外，您也可以檢視及編輯 [影像集屬性](managing-assets-touch-ui.md#editing-properties).

如果建立集時遇到問題，請參閱 [疑難排解Dynamic Media - Scene7模式](troubleshoot-dms7.md#images-and-sets).

## 上傳影像集中的資產 {#uploading-assets-in-image-sets}

首先，上傳影像集的影像。 由於使用者可以在影像集檢視器中放大影像，因此當您選擇影像時，請考量放大比例。 請確定影像在最大尺寸中至少為2000像素。影像集支援多種影像檔案格式，但建議使用無損TIFF、PNG和EPS影像。

您可以像上傳一樣上傳影像集的影像 [上傳資產中的任何其他資產](managing-assets-touch-ui.md#uploading-assets).

### 準備要上傳的影像集資產 {#preparing-image-set-assets-for-upload}

建立影像集之前，請確定影像的大小和格式正確。

要建立多視圖影像集，您需要顯示不同視點的項目或顯示同一項目的不同方面的影像。 其目的是要反白標示項目的重要功能，讓檢視者能完整掌握項目的外觀或用途。

因為使用者可以在影像集中縮放影像，請確定影像在最大尺寸中至少為2000像素。 Assets支援許多影像檔案格式，但建議使用無損TIFF、PNG和EPS影像。

>[!NOTE]
>
>此外，如果您使用縮圖來指示產品色票，則需要執行下列操作：
>
>您需要同一影像的暈映或不同鏡頭，以不同的顏色、圖案或完整度顯示。 您還需要與不同顏色、圖案或結束相對應的縮圖檔案。 例如，若要以影像集呈現縮圖，並以黑色、棕色和綠色顯示相同的夾克，您需要：
>
>* 黑色、棕色和綠色的同一件夾克。
>* 黑色、棕色和綠色縮圖。
>


## 建立影像集 {#creating-image-sets}

您可以透過使用者介面或API來建立影像集。 本節說明如何在使用者介面中建立影像集。

>[!NOTE]
>
>您也可以透過 [批次集預設集](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).

**重要：** 批集由IPS(Image Production System)建立，作為資產提取的一部分，僅可在Dynamic Media - Scene7模式中使用。

將資產新增至資產集時，資產會以英數字元順序自動新增。 新增資產後，您可以手動重新排序或排序資產。

>[!NOTE]
>
>具有的資產不支援影像集 `,` （逗號）。

當您建立影像集時，Adobe會建議下列最佳作法並強制執行下列限制：

| 限制類型 | 最佳實務 | 限制 |
| --- | --- | --- |
| 每組重複資產數 | 無重複項目 | 20 |
| 每組影像的最大數量 | 每組5-10頁影像 | 1000 |

另請參閱 [Dynamic Media限制](/help/assets/limitations.md).

**建立影像集**:

1. 在 **資產**，導覽至您要建立影像集的位置，點選 **[!UICONTROL 建立]**，然後選取 **[!UICONTROL 影像集]**. 您也可以從包含資產的資料夾內建立資產集。

   ![chlimage_1-340](assets/chlimage_1-340.png)

1. 在「影像集編輯器」頁面上， **[!UICONTROL 標題]** 欄位，輸入影像集的名稱。 名稱會出現在影像集的橫幅中。 （可選）輸入說明。

   ![chlimage_1-341](assets/chlimage_1-341.png)

   >[!NOTE]
   >
   >建立影像集時，您可以變更影像集縮圖，或允許AEM根據影像集中的資產自動選取縮圖。若要選取縮圖，請點選 **[!UICONTROL 變更縮圖]** 並選擇任何影像（也可以導航到其他資料夾以查找影像）。 如果您已選取縮圖，然後決定要讓AEM從影像集產生縮圖，請選取「切換至 **[!UICONTROL 自動縮圖」]**。

1. 執行下列任一操作：

   * 在 **[!UICONTROL 影像集編輯器]** 頁面，點選 **[!UICONTROL 新增資產]**.
   * 在 **[!UICONTROL 影像集編輯器]** 頁面，點選 **[!UICONTROL 點選以開啟資產選擇器]**.

   點選以選取您要納入影像集的資產。 選取的資產上面有核取標籤圖示。完成後，在頁面右上角附近點選 **[!UICONTROL 選擇]**.

   使用「資產選擇器」，您可以輸入關鍵字並點選「回報」來搜尋 **[!UICONTROL 資產]**。您也可以套用篩選條件來調整搜尋結果。您可以依路徑、系列、檔案類型和標籤來篩選。選取篩選，然後點選工具 **[!UICONTROL 列上的]** 「篩選」圖示。點選 **[!UICONTROL 檢視]** 圖示並選取 **[!UICONTROL 欄檢視]**, **[!UICONTROL 卡片檢視]**，或 **[!UICONTROL 清單檢視]**.

   請參閱 [使用選取器。](working-with-selectors.md)

   ![chlimage_1-342](assets/chlimage_1-342.png)

1. 將資產新增至資產集時，資產會以英數字元順序自動新增。 新增資產後，您可以手動重新排序或排序資產。

   如有必要，請拖曳資產的 **[!UICONTROL 重新排序]** 圖示（位於資產檔案名稱的右側），以在設定清單上或下重新排序影像。

   ![spin_set_assets](assets/spin_set_assets.png)

   如果您想要變更縮圖或色票，請點選 **[!UICONTROL 縮圖]** 圖示並導覽至您想要的縮圖或色票。 選取完所有影像點選後 **[!UICONTROL 儲存]**.

1. （選用）執行下列任一操作：

   * 若要刪除影像，請選取影像，然後點選 **[!UICONTROL 刪除資產]**.
   * 若要套用預設集，在頁面右上角附近，點選 **[!UICONTROL 預設集]**，然後選取要一次套用至所有資產的預設集。

1. 點選 **[!UICONTROL 儲存]**. 新建立的「影像集」(Image Set)會顯示在您建立該影像集的資料夾中。

## 檢視影像集 {#viewing-image-sets}

您可以在使用者介面中建立影像集，或自動使用 [批次集預設集](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).

**重要**  — 批集由IPS建立 [影像製作系統] 作為資產擷取的一部分，僅可在Dynamic Media - Scene7模式中使用。)

但是，使用批集預設集建立的集，請執行 *not* 顯示在使用者介面中。 您可以透過三種不同方式來檢視這些集合。 （即使您在使用者介面中建立影像集，這些方法仍可供使用）。

* 開啟個別資產的屬性時。 屬性會指出選取資產是的成員的設定(位於 **[!UICONTROL 集的成員]**)。 點選集的名稱即可查看整個集。

   ![chlimage_1-343](assets/chlimage_1-343.png)

* 來自任何組的成員映像。選取 **[!UICONTROL 集]** 功能表來顯示資產所屬的集。

   ![chlimage_1-344](assets/chlimage_1-344.png)

* 在搜尋中，您可以選取 **[!UICONTROL 篩選器]**，然後展開 **[!UICONTROL Dynamic Media]** 選取 **[!UICONTROL 集]**.

   搜尋會傳回在UI中手動建立或透過批次集預設集自動建立的相符集。 對於自動化集，搜尋查詢是使用「開頭為」搜尋條件來執行，這與AEM搜尋不同（以「包含」搜尋條件為基礎）。 將篩選器設定為 **[!UICONTROL 集]** 是搜尋自動化集的唯一方式。

   ![chlimage_1-345](assets/chlimage_1-345.png)

>[!NOTE]
>
>您可以透過使用者介面來檢視集，如 [編輯影像集](#editing-image-sets).

## 編輯影像集 {#editing-image-sets}

您可以對影像集執行各種編輯任務，如：

* 將影像新增至影像集。
* 重新排序影像集中的影像。
* 刪除影像集中的資產。
* 套用檢視器預設集。
* 刪除影像集。

**要編輯影像集**:

1. 執行下列任一操作：

   * 將滑鼠指標暫留在「影像集」資產上，然後點選 **[!UICONTROL 編輯]** （鉛筆圖示）。
   * 將滑鼠指標暫留在「影像集」資產上，點選 **[!UICONTROL 選擇]** （勾選圖示），然後點選 **[!UICONTROL 編輯]** 的上界。
   * 點選「影像集」資產，然後點選 **[!UICONTROL 編輯]** （鉛筆圖示）。

1. 要編輯「影像集」中的影像，請執行以下操作之一：

   * 若要重新排序資產，請拖曳影像至新位置（選取重新排序圖示以移動項目）。
   * 若要以遞增或遞減順序排序項目，請點選欄標題。
   * 若要新增資產或更新現有資產，請點選 **[!UICONTROL 新增資產]**. 導覽至資產，選取資產，然後點選 **[!UICONTROL 選擇]** 靠近頁面的右上角。

   >[!NOTE]
   >如果您以其他影像取代縮圖，以刪除AEM用於縮圖的影像，仍會顯示原始資產。

   * 若要刪除資產，請選取資產，然後點選 **[!UICONTROL 刪除資產]**.
   * 若要套用預設集，在頁面右上角附近，點選 **[!UICONTROL 預設集]**，然後選取檢視器預設集。
   * 若要新增或變更縮圖，請選取資產右側的縮圖圖示。 導覽至新的縮圖或色票資產，選取它，然後點選 **[!UICONTROL 選擇]**.
   * 若要刪除整個影像集，請導覽至影像集，選取它，然後點選 **[!UICONTROL 刪除]**.

   >[!NOTE]
   >
   >您可以導覽至影像集，點選左側導軌中的「設定成員 **** 」，然後點選個別資產上的「鉛筆」圖示以開啟編輯視窗，以編輯影像集中的影像。****

1. 點選 **[!UICONTROL 儲存]** 編輯完畢。

## 預覽影像集 {#previewing-image-sets}

請參閱 [預覽資產](previewing-assets.md).

## 發佈影像集 {#publishing-image-sets}

請參閱 [發佈資產](publishing-dynamicmedia-assets.md).

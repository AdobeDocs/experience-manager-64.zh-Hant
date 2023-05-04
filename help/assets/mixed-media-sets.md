---
title: 混合媒體集
description: 了解如何在Dynamic Media中使用混合媒體集（影像、影像集、回轉集和視訊）。
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: 252c1a50-17ac-4412-88d6-49bb6850658d
feature: Mixed Media Sets
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1505'
ht-degree: 17%

---

# 混合媒體集 {#mixed-media-sets}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

混合媒體集可讓您在單一簡報中混合提供影像、影像集、回轉集和視訊。

混合媒體集由橫幅指定，並加上單字 **[!UICONTROL MixedMediaSet]**。此外，如果「混合媒體集」已發佈，則會顯示「鉛筆」圖示所指示的發佈日期(以 **[!UICONTROL World]** 圖示指示)與上次修改日期(以 **** Pencil圖示表示)。

![chlimage_1-348](assets/chlimage_1-348.png)

>[!NOTE]
>
>如需Assets使用者介面的資訊，請參閱 [使用觸控式UI管理資產](managing-assets-touch-ui.md).

## 快速入門：混合媒體集 {#quick-start-mixed-media-sets}

若要使用混合媒體集快速上手並執行，請執行下列步驟：

1. [上傳您的資產](#uploading-assets).

   首先，上傳混合媒體集的影像和視訊。如有必要，請建立 [影像集](image-sets.md)[和回轉集](spin-sets.md)。由於使用者可以在混合媒體集檢視器中放大影像，因此當您選擇影像時，請考量放大比例。請確定影像在最大尺寸中至少為2000像素。

1. [建立混合媒體集。](#creating-mixed-media-sets)

   若要建立混合媒體集，請從 **[!UICONTROL 資產]** 頁面，點選 **[!UICONTROL 建立>混合媒體集]**，然後為集合命名。 選擇資產，然後選擇影像的顯示順序。

   請參閱 [使用選取器。](working-with-selectors.md)

1. 設定 [混合媒體檢視器預設集](managing-viewer-presets.md)，視需要。

   管理員可以建立或修改混合媒體集檢視器預設集。若要檢視您的混合媒體與檢視器預設集，請選取混合媒體集，然後在左側導軌下拉式選單中選取「檢 **[!UICONTROL 視器]**」。

   請參閱 **[!UICONTROL 「工具>資產>檢視器預設集」]** 來建立或編輯查看器預設集。

   請參閱 [新增和編輯檢視器預設集。](managing-viewer-presets.md)

1. [預覽混合媒體集。](#previewing-mixed-media-sets)

   選取「混合媒體集」，即可預覽。 按一下縮圖圖示，檢查所選檢視器中的混合媒體集。 您可以從 **[!UICONTROL 檢視器]** 功能表（從左側欄下拉式功能表）。

1. [發佈混合媒體集。](#publishing-mixed-media-sets)

   發佈混合媒體集會啟用URL和內嵌字串。 此外，您必須 [發佈檢視器預設集](managing-viewer-presets.md#publishing-viewer-presets).

1. [將URL連結至您的Web應用程式](linking-urls-to-yourwebapplication.md) 或 [內嵌視訊或影像檢視器](embed-code.md).

   AEM Assets會為混合媒體集建立URL呼叫，並在您發佈混合媒體集後啟用它們。 您可以在預覽資產時複製這些URL。 或者，您也可以將它們嵌入您的網站。

   選取「混合媒體集」，然後在左側導軌下拉式選單中選取 **[!UICONTROL 檢視器]**.

   請參 [閱將混合媒體集連結至網頁](linking-urls-to-yourwebapplication.md)[和內嵌視訊或影像檢視器](embed-code.md)。

如有需要，您可以編輯 [混合媒體集](#editing-mixed-media-sets). 此外，您也可以檢視和修改 [混合媒體集屬性](managing-assets-touch-ui.md#editing-properties).

>[!NOTE]
>
>如果您在建立集時遇到問題，請參閱 [疑難排解Dynamic Media - Scene7模式](troubleshoot-dms7.md).

## 上傳資產 {#uploading-assets}

首先，上傳混合媒體集的影像和視訊。由於使用者可以在混合媒體集檢視器中放大影像，因此當您選擇影像時，請務必考量放大比例。 請確定影像在最大尺寸中至少為2000像素。

此外，如果您想要將回轉集或影像集新增至混合媒體集，也請建立這些回轉集或影像集。

## 建立混合媒體集 {#creating-mixed-media-sets}

您可以將影像、影像集、回轉集和視訊新增至混合媒體集。 在將檔案、影像集和回轉集新增至混合媒體集之前，請確定您的檔案、影像集和回轉集已準備好發佈。

將資產新增至資產集時，資產會以英數字元順序自動新增。 新增資產後，您可以手動重新排序或排序資產。

**建立混合媒體集的方式**:

1. 在「資產」中，導覽至您要建立混合媒體集的位置，然後按一下「建 **立**」，然後選 **[!UICONTROL 取「混合媒體集」]**。您也可以從包含資產的資料夾內建立資產集。

   ![chlimage_1-349](assets/chlimage_1-349.png)

1. 在 **[!UICONTROL 混合媒體集編輯器]** 頁面，在 **[!UICONTROL 標題]**，輸入混合媒體集的名稱。 名稱會出現在混合媒體集的橫幅中。 （可選）輸入說明。

   ![chlimage_1-350](assets/chlimage_1-350.png)

   >[!NOTE]
   >
   >建立混合媒體集時，您可以變更混合媒體集縮圖，或允許AEM根據混合媒體集中的資產自動選取縮圖。 若要選取縮圖，請按一下 **[!UICONTROL 變更縮圖]** 並選擇任何影像（也可以導航到其他資料夾以查找影像）。 如果您已選取縮圖，然後決定要讓AEM從混合媒體集產生縮圖，請選取 **[!UICONTROL 切換為自動縮圖]**.

1. 點選 **[!UICONTROL 資產選擇器]** 選取您要納入混合媒體集的資產。 選取它們並點選 **[!UICONTROL 選擇]**.

   使用 **[!UICONTROL 資產選擇器]**，您可以輸入關鍵字並點選 **[!UICONTROL 傳回]**. 您也可以套用篩選條件來調整搜尋結果。您可以依路徑、系列、檔案類型和標籤來篩選。選取篩選，然後從工具列點選 **[!UICONTROL 「篩選]** 」圖示。選擇「視圖」表徵圖並選擇 **[!UICONTROL 清單]**, **[!UICONTROL 欄]**，或 **[!UICONTROL 卡片]** 檢視。

   請參閱 [使用選取器](working-with-selectors.md).

   ![chlimage_1-351](assets/chlimage_1-351.png)

1. 視需要向上或向下拖曳資產，以重新排序資產（必須選取重新排序圖示）。

   ![chlimage_1-352](assets/chlimage_1-352.png)

   如果要新增縮圖，請按一下 **[!UICONTROL +]** 圖示並導覽至您想要的縮圖。 選取完所有縮圖影像點選後 **[!UICONTROL 儲存]**.

   >[!NOTE]
   >
   >如果您想要新增資產，請點選 **[!UICONTROL 新增資產]**.

1. 若要刪除資產，請選取對應的核取方塊並點選 **[!UICONTROL 刪除資產]**.
1. 若要套用預設集，請點選 **[!UICONTROL 預設集]** 在右上角，選取要套用至資產的預設集。
1. 按一下「**[!UICONTROL 儲存]**」。新建立的混合媒體集會顯示在您建立它的資料夾中。

## 編輯混合媒體集 {#editing-mixed-media-sets}

您可以直接在使用者介面中，對混合媒體集中的資產執行各種編輯工作 [就像您在Assets中](managing-assets-touch-ui.md). 您也可以在混合媒體集中執行下列動作：

* 新增資產至混合媒體集。
* 在混合媒體集中重新排序資產。
* 刪除混合媒體集中的資產。
* 套用檢視器預設集。
* 變更預設縮圖。

**編輯混合媒體集**:

1. 執行下列任一操作：

   * 將游標暫留在混合媒體集資產上，然後點選 **[!UICONTROL 編輯]** （鉛筆圖示）。
   * 將游標暫留在混合媒體集資產上，點選 **[!UICONTROL 選擇]** （勾選圖示），然後點選 **[!UICONTROL 編輯]** 的上界。
   * 點選「混合媒體集」資產，然後點選 **[!UICONTROL 編輯]** （鉛筆圖示）。

1. 在混合媒體集編輯器中，執行下列任一操作：

   * 若要重新排序資產 — 在左側面板中，點選 **[!UICONTROL 資產]** （圖示），將資產拖曳至新位置。
   * 若要新增資產 — 在工具列上，點選 **[!UICONTROL 新增資產]**. 導覽至資產。 對於您要新增的每個資產，將滑鼠指標暫留在資產的影像上（而非資產名稱），然後點選核取標籤圖示。 在右上角，點選 **[!UICONTROL 選擇]**.
   * 若要刪除資產 — 在左側面板，點選 **[!UICONTROL 資產]** （圖示），然後選取資產。 在工具列列點選 **[!UICONTROL 刪除資產]**.
   * 若要依資產名稱的遞增或遞減順序排序，請在左側面板中，點選 **[!UICONTROL 資產]** （圖示）。 在 **[!UICONTROL 資產]** 標題中，點選向上或向下插入號圖示。

   >[!NOTE]
   >
   >* 若要從任何檢視模式(例如 **[!UICONTROL 卡片]** 檢視或 **[!UICONTROL 欄]** 檢視)導覽至混合媒體集。 將滑鼠指標暫留在資產上，點選核取標籤圖示以加以選取。Press **[!UICONTROL 空格]** 在鍵盤上，或點選 **[!UICONTROL 更多]** （三個點），然後點選 **[!UICONTROL 刪除]**.
   >* 您可以導覽至混合媒體集，點選「 」，以編輯資產 **[!UICONTROL 設定成員]** 在左側邊欄中，然後點選 **[!UICONTROL 鉛筆]** 圖示以開啟編輯視窗。


1. 點選 **[!UICONTROL 儲存]** 編輯完畢。

   >[!NOTE]
   >
   >* 若要編輯混合媒體集中的資產 — 導覽至混合媒體集。 點選（不要選取）要在AEM中開啟的集合 **[!UICONTROL 設定預覽]** 頁面。 在左側導軌中，點選向下插入符號以開啟下拉式清單，然後點選 **[!UICONTROL 設定成員]**. 在 **[!UICONTROL 設定成員]** 頁面，將滑鼠暫留在資產上，然後點選 **[!UICONTROL 編輯]** （鉛筆圖示）以開啟編輯頁面。
   >* 刪除整個混合媒體集 — 從任何檢視模式(例如 **[!UICONTROL 卡片]** 檢視或 **[!UICONTROL 欄]** 檢視)，導覽至混合媒體集。 暫留在集合上，然後點選 **[!UICONTROL 選擇]** （勾選圖示）。 Press **[!UICONTROL 空格]** 在鍵盤上，或點選 **[!UICONTROL 更多]** （三點列），然後點選 **[!UICONTROL 刪除]**.


## 預覽混合媒體集 {#previewing-mixed-media-sets}

請參閱 [預覽資產](previewing-assets.md) 以取得如何預覽混合媒體集的詳細資訊。

## 發佈混合媒體集 {#publishing-mixed-media-sets}

請參閱 [發佈資產](publishing-dynamicmedia-assets.md) 以取得如何發佈混合媒體集的詳細資訊。

>[!NOTE]
>
>如果您第一次發佈混合媒體資料時未完全進入傳送服務，您可能需要第二次發佈混合媒體集。

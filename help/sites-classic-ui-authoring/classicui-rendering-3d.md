---
title: 演算3D資產
seo-title: 演算3D資產
description: 您可以演算在AEM中處理並儲存的3D資產，以建立2D影像，以便用於網頁內容頁面。
seo-description: 您可以演算在AEM中處理並儲存的3D資產，以建立2D影像，以便用於網頁內容頁面。
uuid: fbbe4fb4-cf21-4752-a2b8-bec2d40e8362
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: bf155d8c-c012-4cb4-89a6-ceead715630e
translation-type: tm+mt
source-git-commit: 284339ee1ce0ffae97f732b569f73c732f063273
workflow-type: tm+mt
source-wordcount: '707'
ht-degree: 0%

---


# 演算3D資產{#rendering-d-assets}

您可以演算在AEM中處理並儲存的3D資產，以建立2D影像，以便用於網頁內容頁面。

請參閱 [編輯您的頁面內容](/help/sites-authoring/qg-page-authoring.md#editing-your-page-content)。

## 轉譯3D資產時的效能考量 {#performance-considerations-when-rendering-d-assets}

轉換3D內容會耗用大量伺服器資源，例如CPU和記憶體。 因此，演算通常需要大量時間。 除了明顯的型號大小和伺服器硬體外，演算時間會因各種因素而顯著不同：

* **轉譯器選取範圍**。

   AEM 3D中預設的Rapid Refine™轉譯器會降低某些品質，以縮短轉譯時間。 不過，它仍可為許多應用程式產生高品質的結果。 透過協力廠商應用程式（例如部署在Autodesk® Maya®或Autodesk® 3ds Max®中的V-Ray™或NVIDIA® Mental Ray®）提供轉譯器，可進行廣泛的設定，而且在設計舞台時可進行效能與品質的權衡。

* **IBL與傳統照明相比**。

   雖然此因素對於預設的快速調整轉換器的影響較小，但與使用傳統點光源或專色光源時相比，Mental Ray等第三方轉換器使用IBL級進行轉換的速度要慢得多。

快速調整轉譯器通常需要幾分鐘的時間來轉換較大的影像。 不過，協力廠商轉譯者通常需要幾分鐘的時間，甚至數小時的時間，才能設定最高品質。

視需要將轉換、處理和演算工作排入伺服器佇列，以避免伺服器過載。 訊息「等待演算……」 顯示在「卡片檢視」中最近上傳的 [!UICONTROL 資產上]。 此狀態表示其他處理或呈現作業必須在當前呈現作業啟動之前完成。

>[!NOTE]
>
>無論AEM 3D互動檢視中顯示哪些材質，3D資產都一律會以原始材質呈現。 此功能同時適用於內建快速調整轉譯器和所有原生轉譯器。

**若要演算3D資產**:

1. 開啟3D資產供檢視。

   請參 [閱檢視3D資產](/help/sites-classic-ui-authoring/classicui-view-3d-assets.md)。

1. 從 **Adobe Experience Manager**，在「導覽」頁面上，點選「[! **[!UICONTROL UICONTROL資產」]******。
1. 在頁面的右上角附近，從 **[!UICONCONTROL檢視下拉式清單中，點選卡** 片檢視 ****。
1. 導覽至您要演算的3D物件。

1. 點選3D物件的卡片，以在資產詳細資訊頁面中開啟它。
1. 在頁面的左上角附近，點選下拉式清單，然後選取「演算 **[!UICONTROL 」]**。

   ![chlimage_1-13](assets/chlimage_1-13.png)

1. 在資產詳細資料頁面的右上角附近，點選「舞台選取器 **** 」圖示（精選），然後選取要套用至3D物件的背景和光源的舞台名稱。

   請 [參閱關於AEM 3D中的階段使用](/help/sites-classic-ui-authoring/classicui-stages-aem3d.md)。

   ![chlimage_1-14](assets/chlimage_1-14.png)

   [!UICONTROL 舞台選擇器] 圖示

1. 在資 **[!UICONTROL 產詳細資訊頁面左側的]** 「演算」下拉式清單中，選取演算器。

   預設的快 **[!UICONTROL 速調整轉譯器]** ，永遠可用。 如果您選取的舞台是原生格式，則清單中也會提供對應的協力廠商轉譯器供您選取。

   請 [參閱關於AEM 3D中的階段使用](/help/sites-classic-ui-authoring/classicui-stages-aem3d.md)。

1. 執行下列動作：

   * 在「寬 **[!UICONTROL 度」和「高度]** 」欄位中，輸入您要轉譯影像的像素寬度和高度。
   * 在「影 **[!UICONTROL 像名稱]** 」欄位中，輸入轉譯影像的名稱。
   * 在「匯 **[!UICONTROL 出路徑]** 」欄位中，輸入要儲存轉譯影像的路徑。 或者，點選「瀏 **[!UICONTROL 覽]** 」圖示並導覽至位置。
   * （可選）選取或取消選取「覆 **[!UICONTROL 寫現有影像]** 」核取方塊。

1. 在資產詳細資訊頁面的右上角附近，點選「 **[!UICONTROL Camera Selector]** 」圖示。 選取您要套用至轉譯影像的相機檢視。

   左、右橫條或上、下橫條是視覺指標，可顯示要將視圖的部分呈現給哪些部分。 當選取的舞台提供相機時，您可以選取預先定義的相機。

   ![chlimage_1-15](assets/chlimage_1-15.png)

   [!UICONTROL 相機選擇器] 圖示

1. 點選「 **[!UICONTROL 開始演算]** 」以開始演算程式。

   會暫時顯示一條消息，指示已開始渲染。 為方便起見，此訊息也包含選取之「輸出資料夾」的 [!UICONTROL 連結] ，以便您直接導覽至它。


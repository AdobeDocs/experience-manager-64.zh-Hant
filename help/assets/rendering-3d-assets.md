---
title: 演算3D資產
seo-title: 演算3D資產
description: 瞭解如何轉譯您在AEM中控制和儲存的3D資產，以建立網頁的2D影像。
seo-description: 瞭解如何轉譯您在AEM中控制和儲存的3D資產，以建立網頁的2D影像。
uuid: ee4d669c-72b1-4f7a-9a68-a7c6d59c7856
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 5b044519-d034-4f05-98c5-f1b299a3ea37
translation-type: tm+mt
source-git-commit: 8c6fdcea0def7720062edfc564c536f8d47e8402
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 0%

---


# 呈現3D資產{#rendering-d-assets}

您可以演算在AEM中處理並儲存的3D資產，以建立2D影像，以便用於網頁內容頁面。

請參閱[編輯您的頁面內容](/help/sites-authoring/qg-page-authoring.md#editing-your-page-content)。

## 呈現3D資產{#performance-considerations-when-rendering-d-assets}時的效能考量

轉換3D內容會耗用大量伺服器資源，例如CPU和記憶體。 因此，演算通常需要大量時間。 除了明顯的型號大小和伺服器硬體外，演算時間會因各種因素而顯著不同：

* **轉譯器選取範圍**。

   AEM 3D中預設的Rapid Refine™轉譯器會降低某些品質，以縮短轉譯時間。 不過，它仍可為許多應用程式產生高品質的結果。 透過協力廠商應用程式（例如部署在Autodesk® Maya®或Autodesk® 3ds Max®中的V-Ray™或NVIDIA® Mental Ray®）提供的轉譯器可廣泛設定，而且在設計舞台時可進行效能與品質的權衡。

* **IBL與傳統照明相比**。

   雖然此因素對於預設的快速調整轉換器的影響較小，但與使用傳統點光源或專色光源時相比，Mental Ray等第三方轉換器使用IBL級進行轉換的速度要慢得多。

快速調整轉譯器通常需要幾分鐘的時間來轉換較大的影像。 不過，協力廠商轉譯者通常需要幾分鐘的時間，甚至數小時的時間，才能設定最高品質。

視需要將轉換、處理和演算工作排入伺服器佇列，以避免伺服器過載。 訊息「等待演算……」 顯示在「卡片檢視」中最近上傳的資產上。 此狀態表示其他處理或呈現作業必須在當前呈現作業啟動之前完成。

>[!NOTE]
>
>無論AEM 3D互動檢視中顯示哪些材質，3D資產都一律會以原始材質呈現。 此功能同時適用於內建快速調整轉譯器和所有原生轉譯器。

**若要演算3D資產**:

1. 開啟3D資產供檢視。

   請參閱[檢視3D資產](viewing-3d-assets.md)。

1. 在Adobe Experience Manager的&#x200B;**[!UICONTROL Navigation]**&#x200B;頁面上，點選&#x200B;**[!UICONTROL Assets]**。
1. 在頁面的右上角附近，從&#x200B;**[!UICONTROL View]**&#x200B;下拉式清單中，點選&#x200B;**[!UICONTROL Card View]**。
1. 導覽至您要演算的3D物件。
1. 點選3D物件的卡片，以在資產詳細資訊頁面中開啟它。
1. 在頁面的左上角附近，點選下拉式清單，然後選取「Render **[!UICONTROL 」。]**

   ![chlimage_1-369](assets/chlimage_1-369.png)

1. 在資產詳細資料頁面的右上角，點選&#x200B;**[!UICONTROL 舞台選擇器]**&#x200B;圖示（精選），然後選取您要套用至3D物件的背景和光源的舞台名稱。

   請參閱[關於AEM 3D](about-the-use-of-stages-in-aem-3d.md)中階段的使用。

   ![chlimage_1-370](assets/chlimage_1-370.png)

   **[!UICONTROL 舞台選取]** 器圖示

1. 在資產詳細資料頁面左側的&#x200B;**[!UICONTROL Render]**&#x200B;下拉式清單中，選取轉譯器。

   預設的&#x200B;**快速調整**&#x200B;轉譯器永遠可用。 如果您選取的舞台是原生格式，則清單中也會提供對應的協力廠商轉譯器供您選取。

   請參閱[關於AEM 3D](about-the-use-of-stages-in-aem-3d.md)中階段的使用。

1. 執行下列動作：

   * 在&#x200B;**[!UICONTROL 寬度]**&#x200B;和&#x200B;**[!UICONTROL 高度]**&#x200B;欄位中，輸入您要呈現影像的像素寬度和高度。
   * 在&#x200B;**[!UICONTROL 影像名稱]**&#x200B;欄位中，輸入轉譯影像的名稱。
   * 在&#x200B;**[!UICONTROL 導出路徑]**&#x200B;欄位中，輸入要儲存渲染影像的路徑。 或者，點選&#x200B;**[!UICONTROL Browse]**&#x200B;圖示並導覽至位置。
   * （可選）選中或取消選擇「覆寫現有影像&#x200B;**[!UICONTROL e]」複選框。**

1. 在資產詳細資訊頁面的右上角，點選&#x200B;**[!UICONTROL 相機選擇器]**&#x200B;圖示。 選取您要套用至轉譯影像的相機檢視。

   左、右橫條或上、下橫條是視覺指標，可顯示要將視圖的部分呈現給哪些部分。 當選取的舞台提供相機時，您可以選取預先定義的相機。

   ![chlimage_1-371](assets/chlimage_1-371.png)

   **[!UICONTROL 相機選]** 擇器

1. 點選&#x200B;**[!UICONTROL 開始演算]**&#x200B;以開始演算程式。

   會暫時顯示一條消息，指示已開始渲染。 為方便起見，此訊息也包含選取之「輸出檔案夾」的連結，讓您直接導覽至該檔案夾。


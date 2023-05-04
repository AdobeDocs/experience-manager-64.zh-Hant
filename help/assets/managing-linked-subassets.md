---
title: 管理複合資產並產生子資產。
description: 了解如何建立參考 [!DNL Experience Manager] InDesign、Adobe Illustrator和Photoshop檔案中的資產。 也了解如何使用頁面檢視器功能來檢視多頁檔案的個別頁面。
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: 9fa44b26-76f7-48e2-a9df-4fd1c0074158
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1413'
ht-degree: 1%

---

# 使用子資產管理複合資產 {#managing-compound-assets}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets可識別上傳的檔案是否包含對存放庫中已存在資產的參考。 此功能僅支援檔案格式。 如果上傳的資產包含任何 [!DNL Experience Manager] 資產時，上傳和參考的資產之間會建立雙向連結。

除了消除冗餘外，引用 [!DNL Experience Manager] Adobe Creative Cloud應用程式中的資產可增強協作，並提高使用者的效率和生產力。

[!DNL Experience Manager] Assets支援 **雙向引用**. 您可以在上傳之檔案的資產詳細資料頁面中找到參考的資產。 此外，您還可以檢視 [!DNL Experience Manager] 資產（位於所參考資產的資產詳細資訊頁面）。

參考會根據所參考資產的路徑、檔案ID和例項ID來解析。

## Adobe Illustrator:新增資產作為參考 {#refai}

您可以參考現有 [!DNL Experience Manager] 從Adobe Illustrator檔案中取得資產。

1. 使用 [[!DNL Experience Manager] 案頭應用程式](https://helpx.adobe.com/tw/experience-manager/desktop-app/aem-desktop-app.html)，裝載 [!DNL Experience Manager] 將資產存放庫設為本機電腦上的磁碟機。 在已裝載的驅動器內，導航到要參考的資產的位置。
1. 將資產從已裝載的驅動器拖曳至Illustrator檔案。
1. 將Illustrator檔案保存到已裝載的驅動器，或 [上傳](managing-assets-touch-ui.md#uploading-assets) 到 [!DNL Experience Manager] 存放庫。
1. 工作流程完成後，前往資產的資產詳細資訊頁面。 對現有 [!DNL Experience Manager] 資產列於 **[!UICONTROL 相依性]** 在 **[!UICONTROL 參考]** 欄。

   ![chlimage_1-258](assets/chlimage_1-258.png)

1. 顯示於下方的參考資產 **[!UICONTROL 相依性]** 也可由目前檔案以外的檔案參照。 若要檢視資產參考檔案的清單，請按一下下方 **[!UICONTROL 相依性]**.

   ![chlimage_1-259](assets/chlimage_1-259.png)

1. 按一下 **[!UICONTROL 檢視屬性]** 圖示。 在屬性頁面中，參考目前資產的檔案清單會顯示在 **[!UICONTROL 參考]** 欄中 **[!UICONTROL 基本]** 標籤。

   ![chlimage_1-260](assets/chlimage_1-260.png)

## Adobe InDesign:新增資產作為參考 {#add-aem-assets-as-references-in-adobe-indesign}

參考 [!DNL Experience Manager] 從InDesign檔案中拖曳資產 [!DNL Experience Manager] InDesign檔案或將InDesign檔案匯出為ZIP檔案。

引用的資產已存在於 [!DNL Experience Manager] 資產。 您可以透過 [配置InDesign伺服器](indesign.md). InDesign檔案中的內嵌資產會擷取為子資產。

>[!NOTE]
>
>如果InDesign伺服器已代理，InDesign檔案的XMP中繼資料已內嵌其預覽。 在此情況下，不會明確要求縮圖擷取。 但是，如果未代理InDesign伺服器，則必須為InDesign檔案顯式提取縮圖。

上傳INDD檔案時，會查詢具有 `xmpMM:InstanceID` 和 `xmpMM:DocumentID` 屬性。

### 拖曳資產以建立參考 {#create-references-by-dragging-aem-assets}

此程式類似於 [在Adobe Illustrator中新增資產作為參考](#refai).

### 匯出ZIP檔案以建立資產的參考 {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. 執行 [建立工作流模型](/help/sites-developing/workflows-models.md) 建立新工作流。
1. 使用 [套件功能Adobe InDesign](https://helpx.adobe.com/indesign/how-to/indesign-package-files-for-handoff.html) 導出文檔。 Adobe InDesign可將檔案和連結的資產匯出為套件。 在此情況下，匯出的資料夾包含 `Links` 包含InDesign檔案子資產的資料夾。 此 `Links` 資料夾與INDD檔案位於同一資料夾中。
1. 建立ZIP檔案並將其上傳至 [!DNL Experience Manager] 存放庫。
1. 啟動「取消封存器」工作流程。
1. 工作流程完成時，「連結」資料夾中的參照會自動參照為子資產。 若要檢視參考資產的清單，請導覽至InDesign資產的資產詳細資訊頁面，然後關閉 [邊欄](/help/sites-authoring/basic-handling.md#rail-selector).

## Adobe Photoshop:新增資產作為參考 {#refps}

1. 使用WebDav客戶端，裝載 [!DNL Experience Manager] 資產作為驅動器。
1. 要建立引用，請執行以下操作 [!DNL Experience Manager] 在Photoshop檔案中，使用Photoshop中的「置入」連結功能，導覽至已裝載磁碟中對應的資產。

   ![chlimage_1-261](assets/chlimage_1-261.png)

1. 將Photoshop檔案保存到已裝載的驅動器或 [上傳](managing-assets-touch-ui.md#uploading-assets) 到 [!DNL Experience Manager] 存放庫。
1. 工作流程完成後，會參照現有 [!DNL Experience Manager] 資產會列在資產詳細資訊頁面中。

   若要檢視參考的資產，請關閉 [邊欄](/help/sites-authoring/basic-handling.md#rail-selector) （位於資產詳細資訊頁面）。

1. 參考的資產也包含參考的資產清單。 若要檢視參考資產的清單，請導覽至資產詳細資訊頁面，然後關閉 [邊欄](/help/sites-authoring/basic-handling.md#rail-selector).

>[!NOTE]
>
>複合資產內的資產也可根據其檔案ID和例項ID來參照。 此功能僅適用於Adobe Illustrator和Adobe Photoshop版本。 對於其他資產，參照是根據主要複合資產中連結資產的相對路徑，如舊版AEM所述。

## 建立子資產 {#generate-subassets}

針對支援的多頁格式資產(PDF檔案、AI檔案、Microsoft PowerPoint和Apple Keynote檔案，以及Adobe InDesign檔案), [!DNL Experience Manager] 可產生子資產，並對應至原始資產的每個個別頁面。 這些子資產連結至 *上層* 資產，並促進多頁檢視。 就所有其他用途而言，子資產在AEM中會被視為一般資產。

子資產產生預設為停用。 若要啟用子資產產生，請遵循下列步驟：

1. 以管理員身分登入Experience Manager。 存取 **[!UICONTROL 「工具」>「工作流」>「模型」]**.
1. 選擇 **[!UICONTROL DAM更新資產]** 工作流程，按一下 **[!UICONTROL 編輯]**.
1. 按一下 **[!UICONTROL 切換側面板]** 並找到 **[!UICONTROL 建立子資產]** 步驟。 將步驟新增至工作流程。 按一下&#x200B;**[!UICONTROL 「同步」]**。

若要產生子資產，請執行下列其中一項操作：

* 新資產：此 [!UICONTROL DAM更新資產] 工作流程會對上傳至AEM的任何新資產執行。 子資產會自動為新的多頁資產產生。
* 現有多頁資產：手動執行 [!UICONTROL DAM更新資產] 工作流程（遵循下列任一步驟）:

   * 選取資產，然後按一下 [!UICONTROL 時間表] 以開啟左側面板。 或者，使用鍵盤快速鍵 `alt + 3`. 按一下 [!UICONTROL 開始工作流程]，選取 [!UICONTROL DAM更新資產]，按一下 [!UICONTROL 開始]，然後按一下 [!UICONTROL 繼續].
   * 選取資產，然後按一下 [!UICONTROL 建立>工作流程] 的上界。 從彈出式對話方塊中，選取 [!UICONTROL DAM更新資產] 工作流程，按一下 [!UICONTROL 開始]，然後按一下 [!UICONTROL 繼續].

尤其是Microsoft Word檔案，請執行 **[!UICONTROL DAM剖析Word檔案]** 工作流程。 它會產生 `cq:Page` 元件。 從檔案擷取的影像會從 `cq:Page` 元件。 即使停用子資產產生，也會擷取這些影像。

## 檢視子資產 {#viewing-subassets}

只有產生子資產，且該子資產可供選取的多頁資產使用時，才會顯示子資產。 若要檢視產生的子資產，請開啟多頁面資產。 在頁面的左上方區域，按一下 ![左側邊欄圖示](assets/do-not-localize/aem_leftrail_contentonly.png) 按一下 **[!UICONTROL 子資產]** 從清單中。 選取 **[!UICONTROL 子資產]** 從清單中。 或者，使用鍵盤快速鍵 `alt + 5`.

![檢視多頁資產的子資產](assets/view_subassets_simulation.gif)

## 檢視多頁檔案的頁面 {#view-pages-of-a-multi-page-file}

您可以使用的「頁面檢視器」功能，檢視多頁檔案，例如PDF、INDD、PPT、PPTX和AI檔案 [!DNL Experience Manager] 資產。 開啟多頁資產，然後按一下 **[!UICONTROL 檢視頁面]** 從頁面的左上角。 開啟的「頁面檢視器」會顯示資產的頁面，以及瀏覽及縮放每個頁面的控制項。

![檢視及查看多頁資產的頁面](assets/view_multipage_asset_fmr.gif)

若是InDesign，您可以使用InDesign伺服器擷取頁面。 如果InDesign檔案建立期間儲存了頁面預覽，則頁面擷取不需要InDesign Server。

工具列、左側邊欄和「頁面檢視器」控制項中提供下列選項：

* **[!UICONTROL 案頭動作]** 若要開啟或顯示特定的子資產，請使用 [!DNL Experience Manager] 案頭應用程式。 了解如何 [配置案頭操作](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#desktopactions-v2) 如果您使用 [!DNL Experience Manager] 案頭應用程式。

* **[!UICONTROL 屬性]** 選項開啟 [!UICONTROL 屬性] 特定子資產的頁面。

* **[!UICONTROL 注釋]** 選項可讓您為特定子資產加上注釋。 開啟父資產以供檢視時，您在個別子資產上使用的註解會收集並一起顯示。

* **[!UICONTROL 頁面概述]** 選項會同時顯示所有子資產。

* **[!UICONTROL 時間表]** 選項 ![左側邊欄圖示](assets/do-not-localize/aem_leftrail_contentonly.png) 顯示檔案的活動資料流。

## 最佳實務和限制 {#best-practice-limitation-tips}

* 子資產產生對於任何Experience Manager部署都可能耗用大量資源。 如果您在上傳複雜資產時產生子資產，請在「DAM更新資產」工作流程中新增步驟。 如果您要隨需產生子資產，請建立個別的工作流程以產生子資產。 專用的工作流程可讓您略過DAM更新資產工作流程中的其他步驟，並儲存計算資源。

>[!MORELIKETHIS]
>
>* [使用Adobe Experience Manager案頭應用程式](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)


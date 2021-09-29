---
title: 管理複合資產並產生子資產。
description: 了解如何從InDesign、Adobe Illustrator和Photoshop檔案建立 [!DNL Experience Manager] 資產的參考。 也了解如何使用頁面檢視器功能來檢視多頁檔案的個別頁面。
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: 9fa44b26-76f7-48e2-a9df-4fd1c0074158
source-git-commit: 937c9425e276f67486fba1d4563799fe68d35cc7
workflow-type: tm+mt
source-wordcount: '1377'
ht-degree: 0%

---

# 使用子資產管理複合資產 {#managing-compound-assets}

Adobe Experience Manager Assets可識別上傳的檔案是否包含對存放庫中已存在資產的參考。 此功能僅支援檔案格式。 如果上傳的資產包含[!DNL Experience Manager]資產的任何參照，則會在上傳和參考的資產之間建立雙向連結。

除了消除冗餘，在Adobe Creative Cloud應用程式中參考[!DNL Experience Manager]資產還可增強協作，並提高使用者的效率和生產力。

[!DNL Experience Manager] Assets支援 **雙向參考**。您可以在上傳之檔案的資產詳細資料頁面中找到參考的資產。 此外，您可以在所參考資產的資產詳細資訊頁面中檢視[!DNL Experience Manager]資產的參考檔案。

參考會根據所參考資產的路徑、檔案ID和例項ID來解析。

## Adobe Illustrator:新增資產作為參考 {#refai}

您可以從Adobe Illustrator檔案中參考現有的[!DNL Experience Manager]資產。

1. 使用[[!DNL Experience Manager] 案頭應用程式](https://helpx.adobe.com/tw/experience-manager/desktop-app/aem-desktop-app.html)，將[!DNL Experience Manager]資產存放庫裝載為本機電腦上的磁碟。 在已裝載的驅動器內，導航到要參考的資產的位置。
1. 將資產從已裝載的驅動器拖曳至Illustrator檔案。
1. 將Illustrator檔案保存到掛載的驅動器，或將[上載](managing-assets-touch-ui.md#uploading-assets)保存到[!DNL Experience Manager]儲存庫。
1. 工作流程完成後，前往資產的資產詳細資訊頁面。 對現有[!DNL Experience Manager]資產的參考會列在&#x200B;**[!UICONTROL References]**&#x200B;欄的&#x200B;**[!UICONTROL Dependencies]**&#x200B;下。

   ![chlimage_1-258](assets/chlimage_1-258.png)

1. 顯示在&#x200B;**[!UICONTROL Dependencies]**&#x200B;下的參考資產也可由目前資產以外的檔案參照。 若要檢視資產參考檔案的清單，請按一下&#x200B;**[!UICONTROL 相依性]**&#x200B;下方的資產。

   ![chlimage_1-259](assets/chlimage_1-259.png)

1. 按一下工具列中的&#x200B;**[!UICONTROL 檢視屬性]**&#x200B;圖示。 在屬性頁中，引用當前資產的檔案清單顯示在&#x200B;**[!UICONTROL Basic]**&#x200B;頁簽的&#x200B;**[!UICONTROL References]**&#x200B;列下。

   ![chlimage_1-260](assets/chlimage_1-260.png)

## Adobe InDesign:新增資產作為參考 {#add-aem-assets-as-references-in-adobe-indesign}

若要從InDesign檔案中參考[!DNL Experience Manager]資產，請將[!DNL Experience Manager]資產拖曳至InDesign檔案，或將InDesign檔案匯出為ZIP檔案。

[!DNL Experience Manager]資產中已有參考的資產。 您可以透過[設定InDesign伺服器](indesign.md)擷取子資產。 InDesign檔案中的內嵌資產會擷取為子資產。

>[!NOTE]
>
>如果InDesign伺服器已代理，InDesign檔案的XMP中繼資料已內嵌其預覽。 在此情況下，不會明確要求縮圖擷取。 但是，如果未代理InDesign伺服器，則必須為InDesign檔案顯式提取縮圖。

上傳INDD檔案時，系統會查詢存放庫中具有`xmpMM:InstanceID`和`xmpMM:DocumentID`屬性的資產，以擷取參考。

### 拖曳資產以建立參考 {#create-references-by-dragging-aem-assets}

此程式類似於[在Adobe Illustrator](#refai)中新增資產作為參考。

### 匯出ZIP檔案以建立資產的參考 {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. 執行[建立工作流模型](/help/sites-developing/workflows-models.md)中的步驟以建立新工作流。
1. 使用Adobe InDesign的[封裝功能](https://helpx.adobe.com/indesign/how-to/indesign-package-files-for-handoff.html)匯出檔案。 Adobe InDesign可將檔案和連結的資產匯出為套件。 在此情況下，匯出的資料夾會包含`Links`資料夾，其中包含InDesign檔案中的子資產。 `Links`資料夾與INDD檔案位於同一資料夾中。
1. 建立ZIP檔案並將其上傳至[!DNL Experience Manager]存放庫。
1. 啟動「取消封存器」工作流程。
1. 工作流程完成時，「連結」資料夾中的參照會自動參照為子資產。 若要檢視參考資產的清單，請導覽至InDesign資產的資產詳細資訊頁面，然後關閉[邊欄](/help/sites-authoring/basic-handling.md#rail-selector)。

## Adobe Photoshop:新增資產作為參考 {#refps}

1. 使用WebDav客戶端，將[!DNL Experience Manager]資產裝載為驅動器。
1. 若要在Photoshop檔案中建立[!DNL Experience Manager]資產的參考，請使用Photoshop中的「置入」連結功能，導覽至已載入磁碟中的對應資產。

   ![chlimage_1-261](assets/chlimage_1-261.png)

1. 將Photoshop檔案保存到掛載的驅動器，或將[上載](managing-assets-touch-ui.md#uploading-assets)保存到[!DNL Experience Manager]儲存庫。
1. 工作流程完成後，資產詳細資訊頁面會列出對現有[!DNL Experience Manager]資產的參考。

   若要檢視參考的資產，請關閉資產詳細資訊頁面中的[邊欄](/help/sites-authoring/basic-handling.md#rail-selector)。

1. 參考的資產也包含參考的資產清單。 若要檢視參考資產的清單，請導覽至資產詳細資訊頁面並關閉[邊欄](/help/sites-authoring/basic-handling.md#rail-selector)。

>[!NOTE]
>
>複合資產內的資產也可根據其檔案ID和例項ID來參照。 此功能僅適用於Adobe Illustrator和Adobe Photoshop版本。 對於其他資產，參照是根據主要複合資產中連結資產的相對路徑，如舊版AEM所述。

## 建立子資產 {#generate-subassets}

針對支援的多頁格式資產(PDF檔案、AI檔案、Microsoft PowerPoint和Apple Keynote檔案，以及Adobe InDesign檔案)— [!DNL Experience Manager]可產生對應至原始資產每個個別頁面的子資產。 這些子資產連結至&#x200B;*parent*&#x200B;資產，並促進多頁檢視。 就所有其他用途而言，子資產在AEM中會被視為一般資產。

子資產產生預設為停用。 若要啟用子資產產生，請遵循下列步驟：

1. 以管理員身分登入Experience Manager。 訪問&#x200B;**[!UICONTROL 工具>工作流>模型]**。
1. 選擇「**[!UICONTROL DAM更新資產]**」工作流，然後按一下「**[!UICONTROL 編輯]**」。
1. 按一下「**[!UICONTROL 切換側面板]**」並找到「建立子資產&#x200B;]**」步驟。**[!UICONTROL &#x200B;將步驟新增至工作流程。 按一下&#x200B;**[!UICONTROL 「同步」]**。

若要產生子資產，請執行下列其中一項操作：

* 新資產：[!UICONTROL DAM更新資產]工作流程會對上傳至AEM的任何新資產執行。 子資產會自動為新的多頁資產產生。
* 現有多頁資產：依照下列任一步驟手動執行[!UICONTROL  DAM更新資產]工作流程：

   * 選取資產，然後按一下「[!UICONTROL 時間軸]」以開啟左側面板。 或者，使用鍵盤快捷鍵`alt + 3`。 按一下「[!UICONTROL 啟動工作流]」，選擇「[!UICONTROL DAM更新資產]」，按一下「[!UICONTROL 啟動]」，然後按一下「[!UICONTROL 繼續」。]
   * 選取資產，然後從工具列按一下「[!UICONTROL 建立>工作流程]」。 從彈出式對話方塊中，選取[!UICONTROL DAM更新資產]工作流程，按一下[!UICONTROL 開始]，然後按一下[!UICONTROL 繼續]。

尤其是Microsoft Word文檔，請執行&#x200B;**[!UICONTROL DAM Parse Word Documents]**&#x200B;工作流。 它從Microsoft Word文檔的內容生成`cq:Page`元件。 從文檔中提取的影像從`cq:Page`元件中引用。 即使停用子資產產生，也會擷取這些影像。

## 檢視子資產 {#viewing-subassets}

只有產生子資產，且該子資產可供選取的多頁資產使用時，才會顯示子資產。 若要檢視產生的子資產，請開啟多頁面資產。 在頁面的左上方區域，按一下「![左側邊欄圖示](assets/do-not-localize/aem_leftrail_contentonly.png)」，然後按一下清單中的「**[!UICONTROL 子資產]**」。 當您從清單中選取&#x200B;**[!UICONTROL 子資產]**&#x200B;時。 或者，使用鍵盤快捷鍵`alt + 5`。

![檢視多頁資產的子資產](assets/view_subassets_simulation.gif)

## 檢視多頁檔案的頁面 {#view-pages-of-a-multi-page-file}

您可以使用[!DNL Experience Manager]資產的頁面檢視器功能，檢視多頁檔案，例如PDF、INDD、PPT、PPTX和AI檔案。 開啟多頁資產，然後按一下頁面左上角的「**[!UICONTROL 檢視頁面]**」 。 開啟的「頁面檢視器」會顯示資產的頁面，以及瀏覽及縮放每個頁面的控制項。

![檢視及查看多頁資產的頁面](assets/view_multipage_asset_fmr.gif)

若是InDesign，您可以使用InDesign伺服器擷取頁面。 如果InDesign檔案建立期間儲存了頁面預覽，則頁面擷取不需要InDesign Server。

工具列、左側邊欄和「頁面檢視器」控制項中提供下列選項：

* **[!UICONTROL 案頭]** 動作，使用案頭應用程式開啟或顯示特 [!DNL Experience Manager] 定子資產。如果您使用[!DNL Experience Manager]案頭應用程式，請參閱如何[配置案頭操作](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#desktopactions-v2)。

* **** 「屬性」選項會開  啟特定子資產的「屬性」頁面。

* **** 「註解」選項可讓您為特定子資產加上注釋。開啟父資產以供檢視時，您在個別子資產上使用的註解會收集並一起顯示。

* **[!UICONTROL 「頁]** 面概述」選項會同時顯示所有子資產。

* **** 按一下左側邊欄圖示後，左側邊欄 ![的時](assets/do-not-localize/aem_leftrail_contentonly.png) 間線選項會顯示檔案的活動資料流。

## 最佳實務和限制 {#best-practice-limitation-tips}

* 子資產產生對於任何Experience Manager部署都可能耗用大量資源。 如果您在上傳複雜資產時產生子資產，請在「DAM更新資產」工作流程中新增步驟。 如果您要隨需產生子資產，請建立個別的工作流程以產生子資產。 專用的工作流程可讓您略過DAM更新資產工作流程中的其他步驟，並儲存計算資源。

>[!MORELIKETHIS]
>
>* [使用Adobe Experience Manager案頭應用程式](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)


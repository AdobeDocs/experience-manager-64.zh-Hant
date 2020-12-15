---
title: 管理複合資產並產生子資產。
description: 瞭解如何從InDesign、Adobe Illustrator和Photoshop檔案建立AEM資產的參考。 此外，也瞭解如何使用頁面檢視器功能來檢視多頁檔案的個別頁面，包括PDF、INDD、PPT、PPTX和AI檔案。
contentOwner: AG
translation-type: tm+mt
source-git-commit: ddfcb74451f41cea911700a64abceaaf47e7af49
workflow-type: tm+mt
source-wordcount: '1386'
ht-degree: 0%

---


# 使用子資產{#managing-compound-assets}管理複合資產

Adobe Experience Manager(AEM)資產可識別已上傳的檔案是否包含對儲存庫中已存在資產的參考。 此功能僅適用於支援的檔案格式。 如果已上傳的資產包含任何AEM資產的參考，則會在已上傳和參考的資產之間建立雙向連結。

除了消除冗餘外，在Adobe Creative Cloud應用程式中參考AEM資產可增強協同作業，並提高使用者的效率和生產力。

AEM Assets支援&#x200B;**雙向參照**。 您可以在已上傳檔案的資產詳細資料頁面中找到參考的資產。 此外，您也可以在參考資產的資產詳細資料頁面中，檢視AEM資產的參考檔案。

參考會根據參考資產的路徑、檔案ID和例項ID來解析。

## 在Adobe Illustrator {#refai}中新增AEM Assets做為參考

您可以從Adobe Illustrator檔案中參考現有的AEM資產。

1. 使用[AEM案頭應用程式](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html)，將AEM Assets存放庫載入本機電腦上的磁碟機。 在掛載的驅動器中，導航到要引用的資產的位置。
1. 將資產從已掛載的磁碟機拖曳至Illustrator檔案。
1. 將Illustrator檔案儲存至已載入的磁碟機，或將[upload](managing-assets-touch-ui.md#uploading-assets)儲存至AEM存放庫。
1. 工作流完成後，轉至資產的資產詳細資訊頁面。 現有AEM資產的參考會列在&#x200B;**[!UICONTROL References]**&#x200B;欄的&#x200B;**[!UICONTROL Dependencies]**&#x200B;下。

   ![chlimage_1-258](assets/chlimage_1-258.png)

1. 出現在&#x200B;**[!UICONTROL Dependencies]**&#x200B;下的引用資產也可以由當前檔案以外的檔案引用。 要查看資產的引用檔案清單，請按一下&#x200B;**[!UICONTROL Dependencies]**&#x200B;下的資產。

   ![chlimage_1-259](assets/chlimage_1-259.png)

1. 按一下工具欄中的&#x200B;**[!UICONTROL 查看屬性]**&#x200B;表徵圖。 在屬性頁中，引用當前資產的檔案清單顯示在&#x200B;**[!UICONTROL Basic]**&#x200B;頁籤的&#x200B;**[!UICONTROL References]**&#x200B;列下。

   ![chlimage_1-260](assets/chlimage_1-260.png)

## 在Adobe InDesign {#add-aem-assets-as-references-in-adobe-indesign}中新增AEM資產作為參考

若要從InDesign檔案中參考AEM資產，請將AEM資產拖曳至InDesign檔案，或將InDesign檔案匯出為ZIP檔案。

AEM Assets中已存在參考的資產。 您可以透過[設定InDesign伺服器](indesign.md)擷取子資產。 InDesign檔案中的內嵌資產會擷取為子資產。

>[!NOTE]
>
>如果InDesign伺服器已代理，InDesign檔案的預覽會內嵌在其XMP中繼資料中。 在這種情況下，不明確需要擷取縮圖。 不過，如果InDesign伺服器未代理，則必須明確擷取InDesign檔案的縮圖。

### 拖曳AEM資產{#create-references-by-dragging-aem-assets}以建立參考

此程式類似於「在Adobe Illustrator中新增AEM資產作為參考」。[](#refai)

### 匯出ZIP檔案{#create-references-to-aem-assets-by-exporting-a-zip-file}以建立AEM資產的參考

1. 執行[建立工作流模型](/help/sites-developing/workflows-models.md)中的步驟以建立新工作流。
1. 使用Adobe InDesign的「封裝」功能來匯出檔案。
Adobe InDesign可將檔案和連結的資產匯出為套件。 在這種情況下，匯出的檔案夾包含InDesign檔案中包含子資料的「連結」檔案夾。
1. 建立ZIP檔案並上傳至AEM儲存庫。
1. 啟動「取消存檔器」工作流。
1. 當工作流程完成時，「連結」檔案夾中的參照會自動參照為子資產。 若要檢視參考資產的清單，請導覽至InDesign資產的資產詳細資訊頁面，然後關閉[Rail](/help/sites-authoring/basic-handling.md#rail-selector)。

## 在Adobe Photoshop {#refps}中新增AEM資產作為參考

1. 使用WebDav用戶端，將AEM Assets裝載為磁碟機。
1. 若要在Photoshop檔案中建立AEM資產的參考，請使用Photoshop的「置入」連結功能，導覽至已載入磁碟機中的對應資產。

   ![chlimage_1-261](assets/chlimage_1-261.png)

1. 將Photoshop檔案儲存至已載入的磁碟機，或將[upload](managing-assets-touch-ui.md#uploading-assets)儲存至AEM存放庫。
1. 工作流程完成後，現有AEM資產的參考會列在資產詳細資料頁面中。

   若要檢視參考的資產，請關閉資產詳細資料頁面中的[Rail](/help/sites-authoring/basic-handling.md#rail-selector)。

1. 參考的資產也包含其參考的資產清單。 若要檢視參考資產的清單，請導覽至資產詳細資料頁面並關閉[rail](/help/sites-authoring/basic-handling.md#rail-selector)。

>[!NOTE]
>
>複合資產中的資產也可以根據其檔案ID和例項ID加以參考。 此功能僅適用於Adobe Illustrator和Adobe Photoshop版本。 對其他人而言，參照是以主要複合資產中連結資產的相對路徑為基礎，就像在舊版AEM中一樣。

## 建立子資產{#generate-subassets}

針對支援的多頁格式資產— PDF檔案、AI檔案、Microsoft PowerPoint和Apple Keynote檔案，以及Adobe InDesign檔案— AEM可產生子資產，以對應至原始資產的每個個別頁面。 這些子資產會連結至&#x200B;*parent*&#x200B;資產，並有助於多頁檢視。 對於所有其他用途，子資產在AEM中會視為一般資產。

子資產產生預設會停用。 若要啟用子資產產生，請依照下列步驟進行：

1. 以管理員身分登入Experience Manager。 訪問&#x200B;**[!UICONTROL 工具>工作流>型號]**。
1. 選擇「**[!UICONTROL DAM更新資產]**」工作流，然後按一下「編輯&#x200B;**[!UICONTROL 」。]**
1. 按一下「**[!UICONTROL 切換側面板]**」並找到「建立子資產&#x200B;]**」步驟。**[!UICONTROL &#x200B;將步驟新增至工作流程。 按一下&#x200B;**[!UICONTROL 「同步」]**。

若要產生子資產，請執行下列其中一項作業：

* 新資產：[!UICONTROL DAM更新資產]工作流程會針對任何上傳至AEM的新資產執行。 子資產會針對新的多頁資產自動產生。
* 現有多頁資產：遵循下列任一步驟手動執行[!UICONTROL DAM更新資產]工作流程：

   * 選取資產，然後按一下「時間軸]」以開啟左側面板。 [!UICONTROL 或者，使用鍵盤快速鍵`alt + 3`。 按一下「開始工作流程」，選擇「[!UICONTROL DAM更新資產」，按一下「[!UICONTROL 開始]」，然後按一下「[!UICONTROL 繼續」。]]
   * 選取資產，然後從工具列按一下「建立>工作流程]」。 [!UICONTROL 在彈出式對話方塊中，選擇[!UICONTROL DAM Update Asset]工作流程，按一下[!UICONTROL Start]，然後按一下[!UICONTROL Contered]。

特別是對於Microsoft Word文檔，請執行&#x200B;**[!UICONTROL DAM Parse Word Documents]**&#x200B;工作流。 它從Microsoft Word文檔的內容生成`cq:Page`元件。 從文檔中提取的影像是從`cq:Page`元件中引用的。 即使子資產產生已停用，這些影像也會擷取。

## 檢視子資產{#viewing-subassets}

只有當子資產已產生且可用於選取的多頁資產時，才會顯示子資產。 若要檢視產生的子資產，請開啟多頁資產。 在頁面的左上方區域，按一下「左側邊欄」圖示](assets/do-not-localize/aem_leftrail_contentonly.png)，然後從清單中按一下「子資產」。 ]****[!UICONTROL ![從清單中選擇&#x200B;**[!UICONTROL 子資產]**&#x200B;時。 或者，使用鍵盤快速鍵`alt + 5`。

![檢視多頁資產的子資產](assets/view_subassets_simulation.gif)

## 檢視多頁檔案{#view-pages-of-a-multi-page-file}的頁面

您可以使用AEM Assets的「頁面檢視器」功能，檢視多頁檔案，例如PDF、INDD、PPT、PPTX和AI檔案。 開啟多頁資產，然後從頁面左上角按一下「檢視頁面」。 ****&#x200B;開啟的「頁面檢視器」會顯示資產的頁面，以及瀏覽及縮放每個頁面的控制項。

![檢視並檢視多頁資產的頁面](assets/view_multipage_asset_fmr.gif)

若是InDesign，您可以使用InDesign伺服器擷取頁面。 如果在InDesign檔案建立期間儲存了頁面預覽，則頁面擷取不需要InDesign Server。

工具列、左側導軌和頁面檢視器控制項中提供下列選項：

* **[!UICONTROL Desktop]** Actions，以使用AEM案頭應用程式開啟或揭示特定子資產。瞭解如果您使用AEM案頭應用程式，如何[設定案頭動作](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=en#desktopactions-v2)。

* **[!UICONTROL 「屬]** 性」(Properties)選項打  開特定子資產的「屬性」(Properties)頁。

* **[!UICONTROL Annotateoption可]** 讓您為特定子資產加上註解。當開啟父資產供檢視時，您在個別子資產上使用的註解會一起收集和顯示。

* **[!UICONTROL 「頁面]** 概述」選項會同時顯示所有子資產。

* **[!UICONTROL 按一]** 下「左側欄」圖示後，左側 ![欄的](assets/do-not-localize/aem_leftrail_contentonly.png) 「時間線」選項會顯示檔案的活動串流。

## 最佳做法和限制{#best-practice-limitation-tips}

* 產生子資產對於任何Experience Manager部署都會耗費大量資源。 如果您要在上傳複雜資產時產生子資產，請在「DAM更新資產」工作流程中新增步驟。 如果您要隨選產生子資產，請建立個別的工作流程以產生子資產。 專用的工作流程可讓您略過DAM更新資產工作流程中的其他步驟，並儲存計算資源。

>[!MORELIKETHIS]
>
>* [使用Adobe Experience Manager案頭應用程式](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)


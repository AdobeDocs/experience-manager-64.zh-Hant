---
title: 檢視3D資產
seo-title: 檢視3D資產
description: 瞭解AEM中資產詳細資訊頁面提供的互動式3D檢視器，以及如何使用它檢視3D資產。
seo-description: 瞭解AEM中資產詳細資訊頁面提供的互動式3D檢視器，以及如何使用它檢視3D資產。
uuid: 7d8133ac-3110-4979-8e19-e65090e791be
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 65040923-a8a8-4e27-82c0-67a04348e238
translation-type: tm+mt
source-git-commit: 11b65cf2d180f04168d4c5d0929957c95a372e3c
workflow-type: tm+mt
source-wordcount: '1806'
ht-degree: 0%

---


# 檢視3D資產 {#viewing-d-assets}

>[!IMPORTANT]
>
>不再支援AEM 6.4中的AEM 3D。 Adobe建議您將 [AEM中的3D資產功能當做雲端服務](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html)[或AEM 6.5.3或更新版本使用。](https://docs.adobe.com/content/help/en/experience-manager-65/assets/dynamic/assets-3d.html) 檢視3D資產。

本檔案說明如何在資產詳細資料中檢視3D資產，以及如何在網站中檢視3D元件中的資產。

## 在「資產詳細資料」頁面中檢視3D資產 {#viewing-d-assets-in-the-asset-details-page}

您可從AEM的資產詳細資訊頁面取得互動式3D檢視器。 檢視器除了其他功能外，還包含一系列互動式相機控制項，可讓您環繞、縮放和平移3D資產。

![chlimage_1-139](assets/chlimage_1-139.png)

除了在AEM 3D中使用預設階段外，您也可以使用您在協力廠商應用程式中建立並上傳至AEM的階段。

請 [參閱關於AEM 3D中的階段使用](about-the-use-of-stages-in-aem-3d.md)。

>[!NOTE]
>
>若要檢視3D資產，您的裝置或案頭瀏覽器必須啟用WebGL。 此外，基礎圖形硬體必須具備足夠的功能和記憶體，才能呈現所需的尺寸和複雜度。 某些預覽功能（例如投影陰影）並不適用於所有瀏覽器。

### 檢視3D資產時的效能考量 {#performance-considerations-when-you-view-d-assets}

在資產詳細資料頁面檢視中開啟3D資產所花的時間，取決於數個因素。 這些因素包括：

* 伺服器的頻寬和延遲。
* 模型大小（面數）。
* 地圖的數目和大小。
* 舞台的複雜性。 例如，IBL影像的大小。

此外，在您以互動方式操作相機時，用戶端電腦（例如工作站、筆記型電腦或行動觸控裝置）的功能也很重要。 功能相當強大的系統，具備良好的圖形功能，可讓互動式3D檢視體驗更順暢更有利。

**若要檢視3D資產**:

1. 請確定您已將3D資產上傳至AEM。

   請參 [閱關於在AEM中上傳和處理3D資產](upload-processing-3d-assets.md)。

1. 從AEM，在「導覽」頁 **[!UICONTROL 面上]** ，點選「 **[!UICONTROL 資產」]**。
1. 在頁面的右上角附近，從「檢視」下拉式清單 **[!UICONTROL 中]** ，點選「卡 **[!UICONTROL 片檢視」]**。
1. 導覽至您要檢視的3D資產。
1. 點選3D資產的資訊卡，以在資產詳細資訊頁面中開啟它。
1. 執行下列任一操作：

   * 在資產詳細資訊頁面的右下角，使用相機控制浮動視窗來變更資產的各種檢視。

      如果您使用不含滾輪的非觸控輸入裝置（例如傳統的Apple單鍵滑鼠），則仍可在每個不同模式中變更3D資產的縮放或透視。 按下滑鼠按鈕並向上或向下拖 `SHIFT`動，按住鍵即可完成動作。

      在典型的筆記型電腦上使用觸摸板時，使用雙指手勢通常很難控制縮放或透視行為。 在這種情況下，您可以在動作期間按 `SHIFT`住並按住。 這種努力會降低夾捏手勢的速度，並讓您更容易達到所需的精確縮放等級或透視效果。 或者，當按下鍵時，您可以使用單指向上或向下拖 `SHIFT`曳，以影響縮放或透視行為。
   <table> 
    <tbody> 
      <tr> 
      <td><strong>相機控制項名稱</strong><br /> </td> 
      <td><strong>說明</strong></td> 
      </tr> 
      <tr> 
      <td><p>縮放</p> <p>或</p> <p>佩爾普</p> </td> 
      <td><p>點選或按一下，在「縮放」和「透視」模式之間切換。</p> <p>或者，在動作期間按 <code>ALT/OPTION</code> 下鍵，以暫時切換至「透視<br /> 」模式。 釋放鍵以回復為縮放模式。</p> 
      <ul> 
      <li><strong>Zoom</strong>-Dolly in and out behaviors that macera delles or delly forme the asset<br /> you beaving. 縮放是滑鼠上滾輪的預設行為（如果可用0），是行動裝置上兩指夾捏手勢的預設行為，或是當您使用滑鼠左鍵向上或向下拖曳時按住Shift鍵。</li> 
      <li><strong>透視</strong>-變更相機的焦距（也稱為視野），同時維持檢視中資產的相對大小。 透視是滾輪的替代行為（如果有的話）、行動裝置上的雙指夾捏手勢，或是當您使用滑鼠左鍵向上或向下拖曳時按住Shift鍵。</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td><p>軌道</p> <p>或</p> <p>潘</p> </td> 
      <td><p>點選或按一下，在「軌道」和「平移」模式之間切換。</p> <p>或者，在動作期間按 <code>ALT/OPTION</code> 住鍵，以暫時切換為「平移」模式。 釋放鍵以恢復為軌道模式。</p> 
      <ul> 
      <li><strong>軌道</strong>-在位於3D資產中心附近的目標點中心的球體上移動觀看攝像機。 Orbit是行動裝置上左鍵拖曳或單鍵拖曳的預設行為。</li> 
      <li><strong>平移</strong>(Pan)在查看平面中移動攝像機。 目標點相應移動，因此後續的軌道動作將使攝像機繞新目標點移動。 平移是左鍵拖曳和單鍵拖曳的替代行為。</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td><p>檢查</p> <p>或</p> <p>目標</p> </td> 
      <td><p>點選或按一下，在「檢查」和「目標」模式之間切換。</p> 
      <ul> 
      <li><strong>檢查</strong>-點選或按一下進入Target模式。</li> 
      <li><strong>Target</strong>-點選或按一下3D資產上任一點，以將該資產的檢視置中。<br /> 軌道動作使用新的目標點。</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td>重設</td> 
      <td>點選或按一下將視圖目標點恢復到模型的中心。 Reset也會使相機更近或更遠<br /> ，以便以合理的檢視大小完整顯示資產。</td> 
      </tr> 
    </tbody> 
    </table>

   * 在資產詳細資訊頁面的右上角附近，點選「舞台選 **[!UICONTROL 擇器]** 」圖示。 選取您要套用至3D資產的背景和光源的舞台名稱。

   ![chlimage_1-140](assets/chlimage_1-140.png)

   舞台提供環境——背景、地面和照明-3D模型可檢視。

   請 [參閱關於AEM 3D中的階段使用](about-the-use-of-stages-in-aem-3d.md)。

   * 在資產詳細資訊頁面的右上角，點選「 **[!UICONTROL Camera Selector]** 」圖示，然後選取您要套用至3D資產的相機檢視。

   ![chlimage_1-141](assets/chlimage_1-141.png)

   舞台通常提供預先定義的相機。 您可以重新選取目前的相機，將它還原為預先定義的設定。

   請 [參閱關於AEM 3D中的階段使用](about-the-use-of-stages-in-aem-3d.md)。

1. In the upper-right corner of the page, tap **[!UICONTROL Save]**.
1. 執行下列任一項作業：

   * 演算3D資產。

      請參 [閱演算3D資產](rendering-3d-assets.md)。

   * 在頁面的右上角，點選「關閉」 **** ，返回「資產」頁面。

## 在Sites 3D元件中檢視3D資產 {#viewing-d-assets-in-the-sites-d-component}

>[!NOTE]
>
>本節僅適用於用於3D資產類型（非Adobe Dimension）的傳統webGL檢視器。

視裝置類型而定，您可透過多種方式存取3D元件功能。

如需詳細資訊，請參閱下列：

* [觸控螢幕裝置](#touchscreen-devices)
* [觸摸板設備](#touchpad-devices)
* [滑鼠和軌跡球裝置](#mouse-and-trackball-devices)

另請參 [閱預覽具有3D元件的網頁](using-the-3d-sites-component.md#previewing-a-web-page-that-has-a-d-component)。

![screen_shot_2017-12-11at145654](assets/screen_shot_2017-12-11at145654.png)

### 觸控螢幕裝置 {#touchscreen-devices}

若要搭配觸控螢幕裝置使用3D元件：

1. 使用單指拖曳或滑動，即可圍繞物件移動（「環繞」）視點（「相機」）。 您可以從任何方向檢視物件。

1. 使用雙指夾捏將相機移至離物件更近或更遠的位置。 此動作類似於放大或縮小，可讓您檢查物件的詳細資訊。 或者，按住+或——按鈕，將相機移得更近或離物件更遠。

1. 使用雙指拖曳來平移相機。 此動作會橫向移動相機，讓您在放大時檢視物件的不同部分。 或者，點選「 **[!UICONTROL 軌道／平移切換」按鈕]** ，切換為「平移」模式，然後使用單指拖曳來平移相機。 點選「軌 **[!UICONTROL 道／平移切換]** 」按鈕，回復 **[!UICONTROL 為「軌道]** 」模式。

1. 點選「 **[!UICONTROL Reset Viewer]** （重設檢視器）」以重設相機。 此動作會將物件重新帶入完整檢視，如果啟用，則會繼續自動回轉。

1. 點選 **[!UICONTROL 全螢幕]** ，進入全螢幕模式（如果裝置支援）。 再次 **[!UICONTROL 點選「全螢幕]** 」，將3D檢視器還原為頁面內嵌模式。

### 觸摸板設備 {#touchpad-devices}

要使用帶觸摸板設備的3D元件：

1. 按住（左）觸摸板按鈕時，用一個手指拖曳，即可將視點（「相機」）圍繞對象移動（「軌道」）。 您可以從任何方向檢視物件。

1. 使用雙指向下或向上拖曳觸摸板按鈕，將相機向上或向上移動，使相機離物件更近或更遠。 此動作類似於放大或縮小，並允許檢查對象的詳細資訊。 或者，按一下並按住 **[!UICONTROL 「放大]** 」或「 **** 縮小」按鈕，將相機移得更近或更遠。

1. 按住 **ALT/option鍵和（左）觸摸板按鈕** ，單指拖曳即可平移相機。 此動作會橫向移動相機，讓您在放大時檢視物件的不同部分。 或者，按一下「 **[!UICONTROL 軌道／平移切換]** 」按鈕可切換為「平移 **** 」模式，然後在按住（左）按鈕的同時使用單指拖曳來平移相機。 再次按一下「 **[!UICONTROL 軌道／平移切換]** 」按鈕以回復 **[!UICONTROL 為「軌道]** 」模式。

1. 按一 **[!UICONTROL 下「重設檢視器]** 」以重設相機。 此動作會將物件重新帶入完整檢視，如果啟用，則會繼續自動回轉。

1. 按一 **[!UICONTROL 下全螢幕]** ，進入全螢幕模式。 使用鍵 **盤上的Escape** (逸出 **[!UICONTROL )鍵，或再次按一下「]** Full Screen」（全螢幕），將3D檢視器還原為頁面內嵌模式。

### 滑鼠和軌跡球裝置 {#mouse-and-trackball-devices}

若要搭配滑鼠和軌跡球裝置使用3D元件：

1. 按住滑鼠左鍵並拖曳，即可將視點（「相機」）圍繞物件移動（「環繞」）。 您可以從任何方向檢視物件。

1. 使用滾輪將相機移至離物件更近或更遠的位置。 這類似於放大或縮小，可讓您檢查物件的詳細資訊。 或者，按一下並按住 **[!UICONTROL 「放大]** 」或「 **** 縮小」按鈕，將相機移得更近或更遠。

1. 按住 **ALT/option鍵和滑鼠左鍵** ，拖動以平移相機。 這樣可橫向移動照相機以允許在放大時查看對象的不同部分。 或者，按一下「 **[!UICONTROL 軌道／平移切換]** 」按鈕，切換為「平移 **** 」模式，然後按住滑鼠左鍵拖曳以平移相機。 再次按一下「 **[!UICONTROL 軌道／平移」(Orbit/Pan]** Toggle **[!UICONTROL )以回復]** 為「軌道」模式。
1. 按一 **[!UICONTROL 下「重設檢視器]** 」以重設相機。 此動作會將物件重新帶入完整檢視，如果啟用，則會繼續自動回轉。
1. 按一 **[!UICONTROL 下全螢幕]** ，進入全螢幕模式。 使用鍵 **[!UICONTROL 盤上的Escape]** (逸出 **[!UICONTROL )鍵，或再次按一下「]** Full Screen」（全螢幕），將3D檢視器還原為頁面內嵌模式。


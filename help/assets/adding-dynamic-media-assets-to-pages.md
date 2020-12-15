---
title: 新增動態媒體資產至頁面
seo-title: 新增動態媒體資產至頁面
description: 如何在AEM中將Dynamic Media元件新增至頁面
seo-description: 如何在AEM中將Dynamic Media元件新增至頁面
uuid: 77abcb87-2df7-449b-be52-540d749890b6
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d1f45751-1761-4d6b-b17d-110b2f1117ea
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '2829'
ht-degree: 4%

---


# 將 Dynamic Media 資產新增至頁面 {#adding-dynamic-media-assets-to-pages}

若要將動態媒體功能新增至您在網站上使用的資產，您可以直接在頁面上新增&#x200B;**Dynamic Media**&#x200B;或&#x200B;**Interactive Media**&#x200B;元件。 若要這麼做，請進入「版面」模式並啟用動態媒體元件。 然後，您可以將這些元件新增至頁面，並新增資產至元件。動態媒體和互動式媒體元件是智慧型的——他們知道您要新增影像或視訊，而可用的選項也會隨之改變。

如果您使用AEM做為WCM，請直接將動態媒體資產新增至頁面。 如果您使用協力廠商來處理WCM，請連結 [或](linking-urls-to-yourwebapplication.md)[內嵌資](embed-code.md) 產。如需多方互動網站，請參閱將最佳化 [的影像傳送至多方互動網站](responsive-site.md)。

>[!NOTE]
>
>您必須先發佈資產，才能將資產新增至AEM中的頁面。 請參閱[發佈動態媒體資產](publishing-dynamicmedia-assets.md)。

## 新增動態媒體元件至頁面{#adding-a-dynamic-media-component-to-a-page}

新增動態媒體元件至頁面與新增元件至任何頁面相同。 Dynamic Media元件在下列章節中有詳細說明。

>[!NOTE]
>
>如果網頁上有動態媒體元件由具有唯讀權限的使用者存取，分頁和元件將無法正確呈現。 原因在於，重建頁面是為了確保元件的屬性良好，且可存取任何參考的資產和組態。 然後再次呈現頁面，導致元件中斷；由於使用者的唯讀存取權，無法重新轉譯頁面上的個別元件代碼。
>  
>若要避免此問題，請確定AEM Sites使用者擁有必要的存取資產權限。

1. 在AEM中，開啟您要新增動態媒體元件的頁面。
1. 在頁面左側的面板（您可能需要切換側面板的顯示）中，按一下「元件&#x200B;****」圖示。
1. 在&#x200B;**[!UICONTROL 元件]**&#x200B;標題下，在下拉式清單中，選取&#x200B;**[!UICONTROL 動態媒體]**。 如果沒有可用的動態媒體元件清單，您可能需要啟用您要使用的動態媒體元件。 請參閱[啟用動態媒體元件](#enabling-dynamic-media-components)。

   ![chlimage_1-537](assets/chlimage_1-537.png)

1. 將您要使用的動態媒體元件拖曳至所需位置的頁面。
1. 將滑鼠指標直接暫留在元件上。 當元件被藍色方塊包圍時，點選一次即可顯示元件的工具列。 點選「**[!UICONTROL Configuration]**（扳手）」圖示。
1. [視需要編](#dynamic-media-components) 輯元件，然後按一下核取標籤以儲存變更。

### 啟用動態媒體元件{#enabling-dynamic-media-components}

如果沒有可新增至頁面的動態媒體元件，可能表示您必須先啟用要使用的元件。

1. 在AEM中，開啟您要新增動態媒體元件的頁面。
1. 在工具列的靠近頁面頂端的左側，點選「頁面資訊」圖示，然後從下拉式清單中點選「編輯範本」。****

   ![edit-template](/help/assets/assets-dm/edit-template.png)

1. 在工具列右側靠近頁面頂部的下拉式清單中，點選&#x200B;**[!UICONTROL 結構]**。

   ![政策](/help/assets/assets-dm/structure-mode.png)

1. 在頁面底部附近，點選「Layout Container（版面容器）」以開啟其工具列，然後點選「Policy（原則）」圖示。****
1. 在&#x200B;**[!UICONTROL 版面容器]**&#x200B;頁面的&#x200B;**[!UICONTROL 屬性]**&#x200B;標題下，請確定已選取「允許的元件&#x200B;]**」標籤。**[!UICONTROL 

   ![允許的元件](/help/assets/assets-dm/allowed-components.png)

1. 捲動直到您看到&#x200B;**[!UICONTROL 動態媒體]**。
1. 點選&#x200B;**[!UICONTROL 動態媒體]**&#x200B;左側的>圖示以展開清單，選取您要啟用的動態媒體元件。

   ![動態媒體元件清單](/help/assets/assets-dm/dm-components-select.png)

1. 在&#x200B;**[!UICONTROL 版面容器]**&#x200B;頁面的右上角，點選「完成（勾選）」圖示。

1. 在工具列靠近頁面頂端的右側，從下拉式清單中，點選「初始內容」，然後按一下「a2/」，將動態媒體元件新增至頁面。[****](#adding-a-dynamic-media-component-to-a-page)

## 本地化動態媒體元件{#localizing-dynamic-media-components}

您可透過下列兩種方式將Dynamic Media元件當地語系化：

* 在「網站」的網頁中，開啟「屬 **[!UICONTROL 性]** 」並選 **[!UICONTROL 取「進階]** 」標籤。選擇所要的本地化語言。

   ![chlimage_1-538](assets/chlimage_1-538.png)

* 從網站選取器中，選取所要的頁面或頁面群組。 點選「**[!UICONTROL 屬性]**」並選取「**[!UICONTROL 進階]**」標籤。 選擇所要的本地化語言。

   >[!NOTE]
   >
   >請注意，**[!UICONTROL Language]**&#x200B;功能表中的所有語言目前並未指派Token。

## 動態媒體元件{#dynamic-media-components}

「動態媒體」和「互動媒體」位於「元件」中的「[!UICONTROL 「動態媒體」標籤下。 ]您可將[!UICONTROL 互動式媒體]元件用於任何互動式資產，例如互動式視訊、互動式影像或轉盤集。 對於所有其他動態媒體元件，請使用動態媒體元件。

>[!NOTE]
>
>這些元件預設不可用，在使用之前必須先透過範本編輯器提供。 [在範本編輯器](/help/sites-authoring/templates.md#editing-templates-template-authors) 中使用這些元件後，您可以像新增其他AEM元件一樣，將元件新增至您的頁面。

![chlimage_1-539](assets/chlimage_1-539.png)

### 動態媒體元件{#dynamic-media-component}

動態媒體元件是智慧型的——視您新增影像或視訊而定，您有各種選項。 此元件支援影像預設集、影像檢視器，例如影像集、回轉集、混合媒體集和視訊。 此外，檢視器回應速度快。 也就是說，螢幕大小會根據螢幕大小自動變更。 所有檢視器都是HTML5檢視器。

>[!NOTE]
>
>如果具有唯讀權限的使用者在網頁上存取動態媒體元件、互動式媒體元件或兩者，分頁和元件將無法正確呈現。 原因在於，重建頁面是為了確保元件的屬性良好，且可存取任何參考的資產和組態。 然後再次呈現頁面，導致元件中斷；由於使用者的唯讀存取權，無法重新轉譯頁面上的個別元件代碼。
>  
>若要避免此問題，請確定AEM Sites使用者擁有必要的存取資產權限。

>[!NOTE]
>
>當您新增動態媒體元件，且&#x200B;**[!UICONTROL 動態媒體設定]**&#x200B;為空白或無法正確新增資產時，請勾選下列項目：
>
>* 您已啟用[動態媒體](config-dynamic.md)。 動態媒體預設為停用。
>* 該影像具有金字塔tiff檔案。 在啟用動態媒體之前匯入的影像沒有金字塔tiff檔案。

>



#### 使用影像{#when-working-with-images}時

動態媒體元件可讓您新增動態影像，包括影像集、回轉集和混合媒體集。 您可以放大、縮小，如果適用，則可以在回轉集內旋轉影像，或從其他類型的回轉集選取影像。

您也可以直接在元件中設定檢視器預設集、影像預設集或影像格式。 若要讓影像回應，您可以設定中斷點或套用回應式影像預設集。

您必須按一下元件中的&#x200B;**[!UICONTROL 編輯]**&#x200B;圖示，然後按一下&#x200B;**[!UICONTROL 動態媒體設定]**，編輯下列動態媒體設定。

![dm-settings-image-preset](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>依預設，動態媒體影像元件是可調式的。如果要使其成為固定大小，請在&#x200B;**[!UICONTROL Advanced]**&#x200B;標籤的元件中設定它，並使用&#x200B;**[!UICONTROL Width]**&#x200B;和&#x200B;**[!UICONTROL Height]**&#x200B;設定。

* **[!UICONTROL 檢視]**
器預設從下拉式選單中選取現有的檢視器預設。如果您所尋找的檢視器預設集不可見，您可能需要將它顯示。 請參閱管理檢視器預設集。 如果您使用影像預設集，則無法選取檢視器預設集，反之亦然。
如果您要檢視影像集、回轉集或混合媒體集，這是唯一可用的選項。 顯示的檢視器預設集也很聰明——只會顯示相關的檢視器預設集。

* **[!UICONTROL 檢視]**
器修飾元檢視器修飾元採用名稱=值配對與&amp;分隔字元的形式，讓您變更檢視器，如檢視器參考指南所述。檢視器修飾元的範例為postemage=img.jpg&amp;caption=text.vtt,1，其為視訊縮圖設定不同的影像，並將隱藏字幕／子標題檔案與視訊建立關聯。

* **[!UICONTROL 影像]**
預設集從下拉式選單中選取現有的影像預設集。如果您要尋找的影像預設集不可見，您可能需要將它顯示。 請參閱管理影像預設集。 如果您使用影像預設集，則無法選取檢視器預設集，反之亦然。
如果您正在檢視影像集、回轉集或混合媒體集，則此選項不可用。

* **[!UICONTROL 影像修]**
飾元您可以提供額外的影像指令，以套用影像效果。這些說明在「影像預設集」和「影像伺服命令」參考中。
如果您正在檢視影像集、回轉集或混合媒體集，則此選項不可用。

* **[!UICONTROL 中斷]**
點如果您在回應式網站上使用此資產，則需要新增影像中斷點。影像中斷點必須以逗號(,)分隔。 當影像預設集中未定義高度或寬度時，此選項便可運作。
如果您正在檢視影像集、回轉集或混合媒體集，則此選項不可用。
按一下元件中的**[!UICONTROL Edit]**&#x200B;可以編輯以下高級設定。

* **[!UICONTROL 標]**
題變更影像的標題。

* **[!UICONTROL 替代]**
文字為關閉圖形的使用者新增影像標題。如果您正在檢視影像集、回轉集或混合媒體集，則此選項不可用。

* **[!UICONTROL URL, Open]**
inYou can set a sasset to open a link.設定URL，並在「開啟於」中指出您要在相同視窗或新視窗中開啟它。
如果您正在檢視影像集、回轉集或混合媒體集，則此選項不可用。

* **[!UICONTROL Width]** Height  ****
Enter值（以像素為單位），如果您希望影像大小固定。將這些值留空可讓資產具適應性。

#### 使用視頻{#when-working-with-video}時

使用動態媒體元件，將動態視訊新增至網頁。 當您編輯元件時，您可以選擇使用預先定義的視訊檢視器預設集來播放頁面上的視訊。

![chlimage_1-540](assets/chlimage_1-540.png)

您必須按一下元件中的&#x200B;**[!UICONTROL 編輯]**，編輯下列動態媒體設定。

>[!NOTE]
>
>依預設，動態媒體視訊元件是可調式的。 如果要使其成為固定大小，請在元件中將其設定為&#x200B;**[!UICONTROL Width]**&#x200B;和&#x200B;**[!UICONTROL Height]**([!UICONTROL Advanced])頁籤。

* **[!UICONTROL 檢視]**
器預設集從下拉式選單中選取現有的視訊檢視器預設集。如果您所尋找的檢視器預設集不可見，您可能需要將它顯示。 請參閱管理檢視器預設集。

* **[!UICONTROL 檢視]**
器修飾元檢視器修飾元採用名稱=值配對與&amp;分隔字元的形式，讓您變更檢視器，如Adobe檢視器參考指南所述。檢視器修飾元的範例為postemage=img.jpg&amp;caption=text.vtt,1

   例如，您可以使用檢視器修飾元執行下列動作：

   * 將標題檔案與視頻[標題關聯。](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html)
   * 將導覽檔案與視訊[導覽關聯。](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html)

按一下元件中的&#x200B;**[!UICONTROL 編輯]**&#x200B;可以編輯以下[!UICONTROL 高級設定]。

* **[!UICONTROL 標]**
題變更影片標題。

* **[!UICONTROL Width]** Height如果您 ****
希望視訊大小固定，請輸入像素值。將這些值留空可讓其適應性。

#### 使用Smart Crop {#when-working-with-smart-crop}時

使用動態媒體元件將智慧型裁切影像資產新增至您的網頁。 當您編輯元件時，您可以選擇使用預先定義的視訊檢視器預設集來播放頁面上的視訊。

另請參閱[映像配置檔案](image-profiles.md)。

![dm-settings-smart-crop](assets/dm-settings-smart-crop.png)

按一下元件中的&#x200B;**[!UICONTROL 編輯]**&#x200B;可編輯以下[!UICONTROL 動態媒體設定]。

>[!NOTE]
>
>依預設，動態媒體影像元件是可調式的。如果要使其成為固定大小，請在「高級」( [!UICONTROL Advanced] )頁籤的元件中使用「寬度」( **[!UICONTROL Width)和「高度」(Height]** )設定它 ****。

* **[!UICONTROL 影像修]**
飾元您可以提供額外的影像指令，以套用影像效果。這些說明在「影像預設集」和「影像伺服命令」參考中。
如果您正在檢視影像集、回轉集或混合媒體集，則此選項不可用。

按一下元件中的&#x200B;**[!UICONTROL 編輯]**&#x200B;可以編輯以下&#x200B;**[!UICONTROL 高級]**&#x200B;設定。

* **[!UICONTROL 標]**
題變更智慧型裁切影像的標題。

* **[!UICONTROL 替代]**
文字為關閉圖形的使用者新增智慧型裁切影像的標題。如果您正在檢視影像集、回轉集或混合媒體集，則此選項不可用。

* **[!UICONTROL URL, Open]**
inYou can set a sasset to open a link.設定URL，並在「開啟於」中指出您要在相同視窗或新視窗中開啟它。
如果您正在檢視影像集、回轉集或混合媒體集，則此選項不可用。

* **[!UICONTROL 高]** 度和寬 ****
度如果您想要智慧型裁切影像的大小固定，請輸入像素值。將這些值留空可讓其適應性。

### 互動式媒體元件{#interactive-media-component}

互動式媒體元件適用於這些資產上具有互動功能的熱點或影像地圖。 如果您有互動式影像、互動式視訊或轉盤橫幅，請使用互動式媒體元件。

互動式媒體元件是智慧型的——視您新增影像或視訊而定，您有各種選項。 此外，檢視器具有互動功能——螢幕大小會根據螢幕大小自動變更。 所有檢視器都是HTML5檢視器。

>[!NOTE]
>
>如果具有唯讀權限的使用者在網頁上存取動態媒體元件、互動式媒體元件或兩者，分頁和元件將無法正確呈現。 原因在於，重建頁面是為了確保元件的屬性良好，且可存取任何參考的資產和組態。 然後再次呈現頁面，導致元件中斷；由於使用者的唯讀存取權，無法重新轉譯頁面上的個別元件代碼。
> 
>若要避免此問題，請確定AEM Sites使用者擁有必要的存取資產權限。

![chlimage_1-541](assets/chlimage_1-541.png)

按一下元件中的&#x200B;**[!UICONTROL Edit]**&#x200B;可以編輯以下&#x200B;**[!UICONTROL General]**&#x200B;設定。

* **[!UICONTROL 檢視]**
器預設從下拉式選單中選取現有的檢視器預設。如果您所尋找的檢視器預設集不可見，您可能需要將它顯示。 檢視器預設集必須先發佈，才能使用。 請參閱管理檢視器預設集。

* **[!UICONTROL 標]**
題變更影片標題。

* **[!UICONTROL Width]** Height如果您 ****
希望視訊大小固定，請輸入像素值。將這些值留空可讓其適應性。

您可以按一下元件中的&#x200B;**[!UICONTROL 編輯]**，編輯下列「新增至購物車」**[!UICONTROL 設定。]**

* **[!UICONTROL 顯示產]**
品資產依預設，此值會選取。產品資產會依「商務」模組中的定義，顯示產品的影像。 清除核取標籤，不會顯示產品資產。

* **[!UICONTROL 顯示產]**
品價格依預設，此值會選取。產品價格顯示「商務」模組中定義的項目價格。 清除勾號以不顯示產品價格。

* **[!UICONTROL 顯示產]**
品表單依預設，此值未選取。「產品表單」包含任何產品變體，例如尺寸和顏色。 清除勾號，不顯示產品變數。

### 全景媒體元件{#panoramic-media-component}

全景媒體元件適用於球形全景影像的資產。 此類影像可提供360°的房間、房產、位置或風景觀賞體驗。 若要符合球形全景的影像，它必須具備下列其中一個或兩個：

* 寬高比為2:1。
* 使用關鍵字&quot;equirectangual&quot;或(&quot;spherical&quot; + &quot;panorama&quot;)或(&quot;spherical&quot; + &quot;panoramic&quot;)加上標籤。 請參閱[使用標籤](/help/sites-authoring/tags.md)。

外觀比例和關鍵字准則都適用於資產詳細資料頁面和「全景媒體」WCM元件的全景資產。

![panoramic-media-viewer-preset](assets/panoramic-media-viewer-preset.png)

您可以在元件中點選&#x200B;**[!UICONTROL Configure]**&#x200B;來編輯下列設定。

* **[!UICONTROL 檢視]**
器預設集從檢視器預設集下拉式選單中選取現有的檢視器。

如果您所尋找的檢視器預設集不可見，請勾選以確保已發佈。 您必須先發佈檢視器預設集，才能使用。 請參閱[管理檢視器預設集](managing-viewer-presets.md)。

### 使用HTTP/2傳送動態媒體資產{#using-http-to-delivery-dynamic-media-assets}

HTTP/2是全新、更新的Web通訊協定，可改善瀏覽器和伺服器的通訊方式。 它提供更快速的資訊傳輸，並降低所需的處理能力。 動態媒體資產的傳送現在可透過HTTP/2，提供更佳的回應和載入時間。

如需開始使用HTTP/2與動態媒體帳戶的完整詳細資訊，請參閱[HTTP2內容傳送](http2.md)。

>[!MORELIKETHIS]
>
>* [瞭解使用AEM Dynamic Media進行色彩管理](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-color-management-technical-video-setup.html)
>* [搭配AEM Dynamic Media使用自訂視訊縮圖](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-thumbnails-feature-video-use.html)
>* [使用AEM Dynamic Media瞭解資產檢視器](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-viewer-feature-video-understand.html)
>* [搭配AEM Dynamic Media使用互動式視訊](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-interactive-video-feature-video-use.html)
>* [在AEM Dynamic Media中使用視訊播放器](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-player-feature-video-use.html)
>* [搭配AEM Dynamic Media使用影像銳利化](https://helpx.adobe.com/experience-manager/6-4/assets/using/best-practices-for-optimizing-the-quality-of-your-images.html)


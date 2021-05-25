---
title: 將Dynamic Media Assets新增至頁面
seo-title: 將Dynamic Media Assets新增至頁面
description: 如何將Dynamic Media元件新增至AEM中的頁面
seo-description: 如何將Dynamic Media元件新增至AEM中的頁面
uuid: 77abcb87-2df7-449b-be52-540d749890b6
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d1f45751-1761-4d6b-b17d-110b2f1117ea
exl-id: bb97b649-a50d-49c8-97aa-18c32f18d527
feature: 元件
role: Business Practitioner
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '2826'
ht-degree: 4%

---

# 將 Dynamic Media 資產新增至頁面 {#adding-dynamic-media-assets-to-pages}

若要將動態媒體功能新增至您在網站上使用的資產，您可以直接在頁面上新增&#x200B;**Dynamic Media**&#x200B;或&#x200B;**Interactive Media**&#x200B;元件。 若要這麼做，請進入「版面」模式並啟用動態媒體元件。 然後，您可以將這些元件新增至頁面，並新增資產至元件。動態媒體和互動式媒體元件是智慧型的，他們知道您是新增影像還是視訊，而可用的選項會隨之變更。

如果您使用AEM做為WCM，請直接將動態媒體資產新增至頁面。 如果您使用協力廠商來處理WCM，請連結 [或](linking-urls-to-yourwebapplication.md)[內嵌資](embed-code.md) 產。如需多方互動網站，請參閱將最佳化 [的影像傳送至多方互動網站](responsive-site.md)。

>[!NOTE]
>
>您必須先發佈資產，才能將其新增至AEM中的頁面。 請參閱[發佈Dynamic Media資產](publishing-dynamicmedia-assets.md)。

## 將Dynamic Media元件新增至頁面{#adding-a-dynamic-media-component-to-a-page}

將Dynamic Media元件新增至頁面，與將元件新增至任何頁面相同。 以下章節將詳細說明Dynamic Media元件。

>[!NOTE]
>
>如果網頁上有Dynamic Media元件由具有唯讀權限的使用者存取，則會中斷頁面，且元件無法正確呈現。 原因在於重建頁面，以確保元件的屬性良好，且可存取任何參考的資產和設定。 然後頁面會再次呈現，導致元件中斷；由於使用者的唯讀存取權，無法重新轉譯頁面上的個別元件代碼。
>  
>若要避免此問題，請確定AEM Sites使用者擁有存取資產的必要權限。

1. 在AEM中，開啟您要新增Dynamic Media元件的頁面。
1. 在頁面左側的面板中（您可能需要切換側面板的顯示），按一下&#x200B;**[!UICONTROL 元件]**&#x200B;圖示。
1. 在&#x200B;**[!UICONTROL 元件]**&#x200B;標題下，在下拉式清單中，選取&#x200B;**[!UICONTROL Dynamic Media]**。 如果沒有Dynamic Media元件清單可用，您可能需要啟用您要使用的Dynamic Media元件。 請參閱[啟用Dynamic Media元件](#enabling-dynamic-media-components)。

   ![chlimage_1-537](assets/chlimage_1-537.png)

1. 將您要使用的Dynamic Media元件拖曳至所需位置的頁面。
1. 將滑鼠指標直接暫留在元件上。 當元件被藍色框包圍時，點選一次以顯示元件的工具列。 點選「**[!UICONTROL Configuration]**（扳手）」圖示。
1. [視需要](#dynamic-media-components) 編輯元件，然後按一下核取記號以儲存變更。

### 啟用Dynamic Media元件{#enabling-dynamic-media-components}

如果沒有可新增至頁面的Dynamic Media元件，可能表示您必須先啟用您要使用的元件。

1. 在AEM中，開啟您要新增Dynamic Media元件的頁面。
1. 在工具列的靠近頁面頂端的左側，點選「頁面資訊」圖示，然後從下拉式清單中點選「 **[!UICONTROL 編輯範本]** 」。

   ![編輯範本](/help/assets/assets-dm/edit-template.png)

1. 在工具列的靠近頁面頂端的右側，從下拉式清單中，點選&#x200B;**[!UICONTROL Structure]**。

   ![政策](/help/assets/assets-dm/structure-mode.png)

1. 在頁面底部附近，點選「 **[!UICONTROL Layout Container]** 」以開啟其工具列，然後點選「 Policy 」圖示。
1. 在「**[!UICONTROL 佈局容器]**」頁的「**[!UICONTROL 屬性]**」標題下，確保選中「**[!UICONTROL 允許的元件]**」頁簽。

   ![允許的元件](/help/assets/assets-dm/allowed-components.png)

1. 捲動直到您看見&#x200B;**[!UICONTROL Dynamic Media]**。
1. 點選&#x200B;**[!UICONTROL Dynamic Media]**&#x200B;左側的>圖示以展開清單，選取您要啟用的Dynamic Media元件。

   ![Dynamic Media元件清單](/help/assets/assets-dm/dm-components-select.png)

1. 在「**[!UICONTROL 版面容器]**」頁面的右上角附近，點選「完成」（勾選記號）圖示。

1. 在工具列的靠近頁面頂端的右側，從下拉式清單中，點選&#x200B;**[!UICONTROL 初始內容]**，然後照常[將Dynamic Media元件新增至頁面](#adding-a-dynamic-media-component-to-a-page)。

## 將Dynamic Media元件當地語系化{#localizing-dynamic-media-components}

您可以透過下列兩種方式之一，將Dynamic Media元件當地化：

* 在「網站」的網頁中，開啟「屬 **[!UICONTROL 性]** 」並選 **[!UICONTROL 取「進階]** 」標籤。選擇所要的本地化語言。

   ![chlimage_1-538](assets/chlimage_1-538.png)

* 從網站選擇器中，選取所需的頁面或頁面群組。 點選&#x200B;**[!UICONTROL 屬性]**&#x200B;並選取&#x200B;**[!UICONTROL 進階]**&#x200B;標籤。 選擇所要的本地化語言。

   >[!NOTE]
   >
   >請注意，並非所有&#x200B;**[!UICONTROL Language]**&#x200B;功能表中可用的語言當前都已分配令牌。

## Dynamic Media元件{#dynamic-media-components}

Dynamic Media和互動式媒體位於[!UICONTROL Components]的[!UICONTROL Dynamic Media]標籤下。 您可以對任何互動式資產（例如互動式視訊、互動式影像或轉盤集）使用[!UICONTROL 互動式媒體]元件。 對於所有其他動態媒體元件，請使用Dynamic Media元件。

>[!NOTE]
>
>這些元件預設不可用，在使用前必須透過範本編輯器提供。 [範本編輯器](/help/sites-authoring/templates.md#editing-templates-template-authors) 中提供元件後，您就可以像新增其他AEM元件一樣，將元件新增至頁面。

![chlimage_1-539](assets/chlimage_1-539.png)

### Dynamic Media元件{#dynamic-media-component}

Dynamic Media元件是智慧型的，視您新增影像或影片而定，您有各種選項。 元件支援影像預設集、以影像為基礎的檢視器，例如影像集、回轉集、混合媒體集和視訊。 此外，檢視器回應速度快。 也就是說，螢幕的大小會根據螢幕大小自動變更。 所有檢視器都是HTML5檢視器。

>[!NOTE]
>
>如果具有唯讀權限的使用者存取的網頁上有Dynamic Media元件、互動式媒體元件或兩者，則會中斷頁面，且元件無法正確呈現。 原因在於重建頁面，以確保元件的屬性良好，且可存取任何參考的資產和設定。 然後頁面會再次呈現，導致元件中斷；由於使用者的唯讀存取權，無法重新轉譯頁面上的個別元件代碼。
>  
>若要避免此問題，請確定AEM Sites使用者擁有存取資產的必要權限。

>[!NOTE]
>
>新增Dynamic Media元件且&#x200B;**[!UICONTROL Dynamic Media設定]**&#x200B;空白或無法正確新增資產時，請檢查下列項目：
>
>* 您已啟用[Dynamic Media](config-dynamic.md)。 Dynamic Media預設為停用。
>* 影像具有金字塔Tiff檔案。 在啟用動態媒體之前匯入的影像沒有金字塔Tiff檔案。

>



#### 使用影像{#when-working-with-images}時

Dynamic Media元件可讓您新增動態影像，包括影像集、回轉集和混合媒體集。 您可以放大、縮小，如果適用，可以在回轉集內開啟影像，或從另一類型的集合中選取影像。

您也可以直接在元件中設定檢視器預設集、影像預設集或影像格式。 若要讓影像具有回應性，您可以設定分界點或套用回應式影像預設集。

您必須按一下元件中的&#x200B;**[!UICONTROL Edit]**&#x200B;圖示，然後按一下&#x200B;**[!UICONTROL Dynamic Media設定]**，以編輯下列Dynamic Media設定。

![dm-settings-image-preset](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>依預設，動態媒體影像元件是可調式的。如果要將其設定為固定大小，請在&#x200B;**[!UICONTROL Advanced]**&#x200B;頁簽的元件中，使用&#x200B;**[!UICONTROL Width]**&#x200B;和&#x200B;**[!UICONTROL Height]**&#x200B;設定進行設定。

* **[!UICONTROL 檢視]**
器預設從下拉式選單中選取現有的檢視器預設集。如果您要尋找的檢視器預設集未顯示，您可能需要將其顯示。 請參閱管理檢視器預設集。 如果您使用影像預設集，則無法選取檢視器預設集，反之亦然。
如果您檢視影像集、回轉集或混合媒體集，此選項是唯一可用的選項。 顯示的檢視器預設集也是智慧型的 — 僅顯示相關的檢視器預設集。

* **[!UICONTROL 檢視]**
器修飾元檢視器修飾元會以名稱=值配對和分隔字元的形式，並可讓您依照檢視器參考指南中的概述來變更檢視器。查看器修飾符的示例是後驗影像=img.jpg&amp;caption=text.vtt,1，它為視頻縮略圖設定不同的影像，並將隱藏式字幕/字幕檔案與視頻關聯。

* **[!UICONTROL 影像]**
預設從下拉式選單中選取現有的影像預設集。如果您要尋找的影像預設集未顯示，則您可能需要使其可見。 請參閱管理影像預設集。 如果您使用影像預設集，則無法選取檢視器預設集，反之亦然。
如果您正在檢視影像集、回轉集或混合媒體集，則無法使用此選項。

* **[!UICONTROL 影像修]**
飾符您可以通過提供其他影像命令來應用影像效果。這些在「影像預設集」和「影像伺服命令」參考中有說明。
如果您正在檢視影像集、回轉集或混合媒體集，則無法使用此選項。

* ****
中斷點如果您在回應式網站上使用此資產，則需要新增影像中斷點。影像斷點必須用逗號(,)分隔。 當影像預設集中未定義高度或寬度時，此選項即可運作。
如果您正在檢視影像集、回轉集或混合媒體集，則無法使用此選項。
您可以按一下元件中的**[!UICONTROL Edit]**&#x200B;編輯下列進階設定。

* ****
標題變更影像的標題。

* **[!UICONTROL 替]**
代文本為那些關閉圖形的用戶添加影像標題。如果您正在檢視影像集、回轉集或混合媒體集，則無法使用此選項。

* **[!UICONTROL URL，在中]**
開啟您可以設定資產以開啟連結。設定URL，然後在「開啟」中（在中）指出您要在相同視窗還是新視窗中開啟它。
如果您正在檢視影像集、回轉集或混合媒體集，則無法使用此選項。

* **** Widthand  ****
HeightEnter值（以像素為單位），如果希望影像大小固定。將這些值保留為空白，可讓資產具有適用性。

#### 使用視訊{#when-working-with-video}時

使用Dynamic Media元件將動態視訊新增至網頁。 編輯元件時，您可以選擇使用預先定義的視訊檢視器預設集來在頁面上播放視訊。

![chlimage_1-541](assets/chlimage_1-540.png)

您必須按一下元件中的&#x200B;**[!UICONTROL Edit]**&#x200B;編輯下列Dynamic Media設定。

>[!NOTE]
>
>依預設，Dynamic Media視訊元件是最適化的。 如果要將其設定為固定大小，請在元件中以[!UICONTROL Advanced]標籤中的&#x200B;**[!UICONTROL Width]**&#x200B;和&#x200B;**[!UICONTROL Height]**&#x200B;設定它。

* **[!UICONTROL 檢視]**
器預設從下拉式選單中選取現有的視訊檢視器預設集。如果您要尋找的檢視器預設集未顯示，您可能需要將其顯示。 請參閱管理檢視器預設集。

* **[!UICONTROL 檢視]**
器修飾元檢視器修飾元會以名稱=值配對和分隔字元的形式，並可讓您依照Adobe檢視器參考指南中的概述來變更檢視器。檢視器修飾詞的範例為後驗影像=img.jpg&amp;caption=text.vtt,1

   例如，使用檢視器修飾元，您可以執行下列操作：

   * 將字幕檔案與視頻[字幕關聯。](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html)
   * 將導航檔案與視頻[導航關聯。](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html)

您可以按一下元件中的&#x200B;**[!UICONTROL Edit]**&#x200B;編輯以下[!UICONTROL 進階設定]。

* ****
標題變更視訊的標題。

* **** 如果您 ****
希望視訊大小固定，請以像素為單位輸入值。將這些值保留為空白，可使其變得最適化。

#### 使用智慧型裁切{#when-working-with-smart-crop}時

使用Dynamic Media元件將智慧型裁切影像資產新增至網頁。 編輯元件時，您可以選擇使用預先定義的視訊檢視器預設集來在頁面上播放視訊。

另請參閱[影像設定檔](image-profiles.md)。

![dm-settings-smart-crop](assets/dm-settings-smart-crop.png)

您可以按一下元件中的&#x200B;**[!UICONTROL Edit]**&#x200B;編輯以下[!UICONTROL Dynamic Media設定]。

>[!NOTE]
>
>依預設，動態媒體影像元件是可調式的。如果要使其成為固定大小，請在「高級」( [!UICONTROL Advanced] )頁籤的元件中使用「寬度」( **[!UICONTROL Width)和「高度」(Height]** )設定它 ****。

* **[!UICONTROL 影像修]**
飾符您可以通過提供其他影像命令來應用影像效果。這些在「影像預設集」和「影像伺服命令」參考中有說明。
如果您正在檢視影像集、回轉集或混合媒體集，則無法使用此選項。

您可以按一下元件中的&#x200B;**[!UICONTROL Edit]**&#x200B;編輯以下&#x200B;**[!UICONTROL Advanced]**&#x200B;設定。

* ****
標題變更智慧型裁切影像的標題。

* **[!UICONTROL 替]**
代文本為關閉圖形的用戶在智慧裁切影像中添加標題。如果您正在檢視影像集、回轉集或混合媒體集，則無法使用此選項。

* **[!UICONTROL URL，在中]**
開啟您可以設定資產以開啟連結。設定URL，然後在「開啟」中（在中）指出您要在相同視窗還是新視窗中開啟它。
如果您正在檢視影像集、回轉集或混合媒體集，則無法使用此選項。

* **** 如果您 ****
希望智慧型裁切影像大小固定，請高度和寬度輸入值（以像素為單位）。將這些值保留為空白，可使其變得最適化。

### 互動式媒體元件{#interactive-media-component}

互動式媒體元件適用於在這些資產上具有互動的熱點或影像地圖。 如果您有互動式影像、互動式視訊或輪播橫幅，請使用互動式媒體元件。

互動式媒體元件是智慧型的 — 根據您添加的影像還是視頻，您有各種選項。 此外，檢視器回應速度快 — 螢幕大小會根據螢幕大小自動變更。 所有檢視器都是HTML5檢視器。

>[!NOTE]
>
>如果具有唯讀權限的使用者存取的網頁上有Dynamic Media元件、互動式媒體元件或兩者，則會中斷頁面，且元件無法正確呈現。 原因在於重建頁面，以確保元件的屬性良好，且可存取任何參考的資產和設定。 然後頁面會再次呈現，導致元件中斷；由於使用者的唯讀存取權，無法重新轉譯頁面上的個別元件代碼。
> 
>若要避免此問題，請確定AEM Sites使用者擁有存取資產的必要權限。

![chlimage_1-541](assets/chlimage_1-541.png)

您可以按一下元件中的&#x200B;**[!UICONTROL Edit]**&#x200B;編輯以下&#x200B;**[!UICONTROL 一般]**&#x200B;設定。

* **[!UICONTROL 檢視]**
器預設從下拉式選單中選取現有的檢視器預設集。如果您要尋找的檢視器預設集未顯示，您可能需要將其顯示。 必須先發佈檢視器預設集，才能使用。 請參閱管理檢視器預設集。

* ****
標題變更視訊的標題。

* **** 如果您 ****
希望視訊大小固定，請以像素為單位輸入值。將這些值保留為空白，可使其變得最適化。

您可以按一下元件中的&#x200B;**[!UICONTROL Edit]**&#x200B;編輯下列&#x200B;**[!UICONTROL 新增至購物車]**&#x200B;設定。

* **[!UICONTROL 顯示產]**
品資產預設為選取此值。產品資產會依照商務模組中的定義顯示產品的影像。 清除勾號以不顯示產品資產。

* **[!UICONTROL 顯示產]**
品價格預設情況下，此值為選定值。產品價格顯示商務模組中定義的項目價格。 清除勾號以不顯示產品價格。

* **[!UICONTROL 顯示產]**
品表單預設情況下，此值未選中。產品表單包含任何產品變體，例如大小和顏色。 清除勾號以不顯示產品變體。

### 全景媒體元件{#panoramic-media-component}

全景媒體元件用於那些為球形全景影像的資產。 這些影像提供360°的房間、屬性、位置或景觀的觀看體驗。 要使影像符合球形全景，它必須具有以下一個或兩個：

* 長寬比為2:1。
* 以關鍵字&quot;equirectangual&quot;或(&quot;spherical&quot; + &quot;panorama&quot;)或(&quot;spherical&quot; + &quot;panoramic&quot;)加上標籤。 請參閱[使用標籤](/help/sites-authoring/tags.md)。

外觀比例和關鍵字條件都適用於資產詳細資訊頁面和「全景媒體」WCM元件的全景資產。

![panoramic-media-viewer-preset](assets/panoramic-media-viewer-preset.png)

您可以點選元件中的&#x200B;**[!UICONTROL Configure]**&#x200B;以編輯下列設定。

* **[!UICONTROL 檢視]**
器預設從檢視器預設集下拉式選單中選取現有的檢視器。

如果您要尋找的檢視器預設集未顯示，請核取以確認其已發佈。 您必須先發佈檢視器預設集，才能使用它們。 請參閱[管理檢視器預設集](managing-viewer-presets.md)。

### 使用HTTP/2來傳送Dynamic Media資產{#using-http-to-delivery-dynamic-media-assets}

HTTP/2是全新、更新的Web通訊協定，可改善瀏覽器和伺服器的通訊方式。 它提供了更快的資訊傳輸，並降低了所需的處理能力。 Dynamic Media資產的傳送現在可透過HTTP/2，提供更理想的回應和載入時間。

如需開始使用Dynamic Media帳戶的HTTP/2的完整詳細資訊，請參閱[HTTP2內容傳送](http2.md)。

>[!MORELIKETHIS]
>
>* [了解AEM Dynamic Media的色彩管理](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-color-management-technical-video-setup.html)
>* [搭配AEM Dynamic Media使用自訂視訊縮圖](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-thumbnails-feature-video-use.html)
>* [透過AEM Dynamic Media了解Asset Viewer](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-viewer-feature-video-understand.html)
>* [搭配AEM Dynamic Media使用互動式視訊](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-interactive-video-feature-video-use.html)
>* [在AEM Dynamic Media中使用視訊播放器](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-player-feature-video-use.html)
>* [搭配AEM Dynamic Media使用影像銳利化](https://helpx.adobe.com/experience-manager/6-4/assets/using/best-practices-for-optimizing-the-quality-of-your-images.html)


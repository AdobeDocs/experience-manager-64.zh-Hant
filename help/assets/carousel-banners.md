---
title: 輪播橫幅
seo-title: Carousel Banners
description: 了解如何在動態媒體中使用輪播橫幅
seo-description: Learn how to work with carousel banners in dynamic media
uuid: 6d6de9ac-a6e1-4f07-a610-cc84e26bf76b
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 4b532cd3-1561-4b5c-8b4b-420c278926f0
exl-id: d2fdad3f-513b-4147-a7c6-a3c1b64dd6e3
feature: Carousel Banners
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4771'
ht-degree: 4%

---

# 輪播橫幅 {#carousel-banners}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

轉盤橫幅可讓行銷人員輕鬆建立互動式旋轉促銷內容，並將其傳遞至任何畫面，借此促進轉換。

建立和修改促銷橫幅中特有的內容可能非常耗時，限制您快速發佈新內容或使其更具針對性的能力。 輪播橫幅可讓您快速建立或修改旋轉橫幅、新增連結至產品詳細資料或相關資源的熱點等互動功能，並將它們傳送至任何畫面，讓您更快將新促銷內容投放市場。

輪播橫幅是由具有單字的橫幅指定 **卡魯塞**:

![chlimage_1-438](assets/chlimage_1-438.png)

在您的網站上，輪播橫幅可以如下所示：

![chlimage_1-439](assets/chlimage_1-439.png)

您可以在此導覽影像（按一下數字）。 此外，幻燈片會根據您可以自定義的時間間隔自動旋轉。 您在轉盤橫幅中新增的影像支援熱點和影像地圖，使用者可以點選或前往超連結或存取快速檢視視窗。

在此示例中，用戶已點選或按一下影像映射，並訪問手套的「快速視圖」窗口：

![chlimage_1-440](assets/chlimage_1-440.png)

## 觀看輪播橫幅的建立方式 {#watch-how-carousel-banners-are-created}

觀看10分鐘33秒的逐步說明 [輪播橫幅的建立方式](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner). 您也將學習如何預覽、編輯和傳送輪播橫幅。

>[!NOTE]
>
>必須將非管理使用者新增至 **dam-users** 群組，以便能夠建立或編輯輪播橫幅。 如果您在建立或編輯時遇到問題，請咨詢系統管理員，該管理員可將您添加到 **dam-users** 群組。

## 快速入門：輪播橫幅 {#quick-start-carousel-banners}

快速啟動並運行：

1. [識別熱點和影像映射變數](#identifying-hotspot-and-image-map-variables) (僅限使用AEM Assets + Dynamic Media的客戶)

   首先，找出現有Quickview實作所使用的動態變數，以便在AEM Assets中的輪播橫幅建立程式期間，正確輸入熱點和影像地圖資料。

   >[!NOTE]
   >
   >如果您是AEM Sites或電子商務客戶，可以使用內建功能來導覽至產品頁面，並查詢產品目錄中的現有SKU。 您不需要手動輸入熱點或影像地圖變數。 請參閱 [設定電子商務](/help/sites-administering/generic.md).
   >
   >如果您是AEM Assets和Dynamic Media客戶，您將手動輸入熱點和影像地圖的資料，然後將發佈的URL或內嵌程式碼與您的協力廠商內容管理系統整合。

1. 可選：視需 [要建立轉盤集檢視器預設](managing-viewer-presets.md)。

   如果您是管理員，則可建立自己的轉盤檢視器預設集，以自訂轉盤的行為和外觀。 主要優點是，您可以針對多個輪播重複使用此自訂檢視器預設集。 不過，使用者也可以選擇在編寫轉盤時直接自訂轉盤的行為和外觀。 當您想要指定輪播的特定設計時，這是偏好的方法。

1. [上傳影像橫幅](#uploading-image-banners).

   上傳您要製作互動式的影像橫幅。

1. [建立轉盤集](#creating-carousel-sets).

   在輪播集中，使用者會瀏覽橫幅影像，並點選熱點或影像地圖以存取相關內容。

   若要在資產中建立轉盤集，請點選「 **[!UICONTROL 建立]**」，然後選 **[!UICONTROL 取轉盤集]**。將資產新增至投影片並點選「 **[!UICONTROL 儲存]**」。您也可以直接在編輯器中編輯轉盤的外觀和行為。

1. [將熱點或影像映射添加到影像橫幅。](#adding-hotspots-or-image-maps-to-an-image-banner)

   新增一或多個熱點或影像地圖至影像橫幅，並將每個熱點或影像地圖與連結、快速檢視或體驗片段等動作建立關聯。 添加熱點或影像映射後，通過發佈輪播集來完成此任務。 發佈會建立內嵌程式碼，供您複製並套用至網站登陸頁面。

   請參閱 [（選用）預覽轉盤橫幅](#optional-previewing-carousel-banners)  — 選用。 如有需要，您可以檢視輪播集的呈現，並測試其互動性。

1. [發佈輪播橫幅。](#publishing-carousel-banners)

   您發佈轉盤集的方式與發佈任何資產的方式相同。 在「資產」中，導覽至「轉盤集」，然後選取它，然後點選或點選 **[!UICONTROL 發佈]**. 「發佈轉盤集」會啟用URL和內嵌字串。

1. 執行下列任一項作業：

   * [將輪播橫幅新增至您的網站頁面](#adding-a-carousel-banner-to-your-website-page) 您可以新增已複製到網站頁面的轉盤橫幅URL或內嵌程式碼。

      * [將轉盤橫幅與現有的Quickview整合](#integrating-the-carousel-banner-with-an-existing-quickview). 如果您使用協力廠商網頁內容管理系統，則需要將新的轉盤橫幅與網站上現有的Quickview實作整合。
   * [在AEM中將轉盤橫幅新增至您的網站](adding-dynamic-media-assets-to-pages.md) 如果您是AEM Sites客戶，可使用互動式媒體元件，將輪播集直接新增至AEM中的頁面。


如果您需要編輯轉盤集，請參閱 [編輯轉盤集](#editing-carousel-sets). 此外，您也可以檢視及編輯 [轉盤集屬性](/help/assets/managing-assets-touch-ui.md#editing-properties).

## 識別熱點和影像映射變數 {#identifying-hotspot-and-image-map-variables}

首先，找出現有Quickview實作所使用的動態變數，以便在AEM Assets中轉盤集建立程式期間，正確輸入熱點或影像地圖資料。

在AEM Assets中將熱點或影像地圖新增至橫幅影像時，您需要指派SKU和選用的其他變數至每個熱點或影像地圖。 這些變數稍後用於匹配熱點或影像映射與Quickview內容。

>[!NOTE]
>
>如果您是AEM Sites和/或AEM Ecommerce客戶，請略過此步驟。 您不需要手動識別熱點或影像地圖變數；您可以將與Ecommerce的整合用於產品整合。 請參閱 [設定電子商務](/help/sites-administering/generic.md). 此外，您也可以使用互動式元件，並將其新增至您的網頁。
>
>如果您是AEM Assets或Media客戶，請發佈URL或內嵌程式碼，然後與您的協力廠商內容管理系統整合，並手動識別熱點和影像地圖。

請務必正確識別要與熱點或影像地圖資料建立關聯的變數數目和類型。 新增至橫幅影像的每個熱點或影像地圖都必須包含足夠的資訊，以明確識別現有後端系統中的產品。 同時，每個熱點或影像地圖不應包含超過必要的資料。 原因在於，這會使資料輸入程式過於複雜，且持續的熱點或影像地圖管理更容易出錯。

有不同的方式可識別要用於熱點或影像地圖資料的一組變數。

有時，與負責現有Quickview實施的IT專家協商可能已足夠，因為他們可能知道在系統中標識Quickview所需的最少一組資料。 不過，在大多數情況下，您也可以簡單分析前端程式碼的現有行為。

大多數Quickview實施都使用以下範例：

* 使用者在網站上啟動使用者介面元素。例如，按一下 **[!UICONTROL 快速檢視]** 按鈕。
* 網站會視需要傳送Ajax要求至後端，以載入Quickview資料或內容。
* 快速檢視資料會轉譯為內容，以準備在網頁上轉譯。
* 最後，前端代碼在螢幕上直觀地呈現這樣的內容。

接著，方法是造訪實作「快速檢視」功能的現有網站的不同區域、觸發快速檢視並擷取網頁所傳送的Ajax URL，以載入快速檢視資料或內容。

通常您不需要使用任何專用的除錯工具。 現代網頁瀏覽器的功能是能夠勝任工作的網頁檢查員。 以下是一些Web瀏覽器的示例，其中包括Web檢查員：

* 若要在Google Chrome中查看所有傳出的HTTP要求，請按F12(Windows)或Command-Option-I(Mac)以開啟「開發人員工具」面板，然後點選 **[!UICONTROL 網路]** 標籤。
* 在Firefox中，您可以按F12(Windows)或Command-Option-I(Mac)並使用其Net標籤來啟動Firebug外掛程式，或使用內建的偵測器工具及其網路標籤。

在瀏覽器中開啟網路監視時，觸發頁面上的快速檢視。

現在，在網路記錄中找到Quickview Ajax URL，並複製記錄的URL以供日後分析之用。 在大多數情況下，當您觸發Quickview時，會有許多請求傳送至伺服器。 Quickview Ajax URL通常是清單中第一個的URL。 它有複雜的查詢字串部分或路徑，其響應MIME類型為 `text/html`, `text/xml`，或 `text/javascript`.

在此程式中，請務必瀏覽網站的不同區域，包含不同的產品類別和類型。 原因是Quickview URL可能有指定網站類別中常見的部分，但只有當您造訪網站的其他區域時才會變更。

在最簡單的情況下，Quickview URL中唯一的變數部分是產品SKU。 在此情況下，SKU值是您唯一需要將熱點或影像映射添加到橫幅影像的資料段。

但是，在複雜的情況下，Quickview URL除了SKU以外，還有不同的元素，例如類別ID、顏色代碼、大小代碼等。 在這種情況下，每個元素都是熱點中的個別變數，或輪播橫幅功能中的影像地圖資料定義。

請考量下列Quickview URL範例及其產生的熱點或影像地圖變數：

<table> 
 <tbody> 
  <tr> 
   <td>在查詢字串中找到的單一SKU。</td> 
   <td><p>錄制的Quickview URL包括：</p> 
    <ul> 
     <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li> 
     <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li> 
     <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li> 
     <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li> 
    </ul> <p>URL中唯一的變數部分是 <code>productId=</code> 查詢字串參數，且顯然是SKU值。 因此，我們的熱點或影像映射僅需要填入如下值的SKU欄位 <code>866558,</code> <code>1196184,</code> <code>1081492,</code> <code>1898294.</code></p> </td> 
  </tr> 
  <tr> 
   <td>單一SKU，可在URL路徑中找到。</td> 
   <td><p>錄制的Quickview URL包括：</p> 
    <ul> 
     <li><p><code>https://server/product/6422350843</code></p> </li> 
     <li><p><code>https://server/product/1607745002</code></p> </li> 
     <li><p><code>https://server/product/0086724882</code></p> </li> 
    </ul> <p>變數部分位於路徑的最後一部分，它將成為熱點/影像映射的SKU值：<strong><code>6422350843</code>, <code>1607745002,</code> </strong><code>0086724882.</code></p> </td> 
  </tr> 
  <tr> 
   <td>查詢字串中的SKU和類別ID。</td> 
   <td><p>錄制的Quickview URL包括：</p> 
    <ul> 
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li> 
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li> 
     <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li> 
    </ul> <p>在此情況下，URL中會有兩個不同的部分。 SKU儲存在 <code>prodId</code> 參數和類別ID儲存在 <code>category=</code>參數。</p> <p>因此，熱點/影像地圖定義是配對。 即SKU值，以及名為 <code>categoryId</code>. 產生的配對如下：</p> 
    <ul> 
     <li><p>SKU是 <strong><code>305466</code></strong> 和 <code>categoryId</code> is <code>1100004</code>.</p> </li> 
     <li><p>SKU是 <strong><code>310181</code></strong> 和 <code>categoryId</code> is <strong><code>1100004</code></strong>.</p> </li> 
     <li><p>SKU是 <strong><code>308706</code></strong> 和 <code>categoryId</code> is <strong><code>1740148</code></strong>.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## 上傳影像橫幅 {#uploading-image-banners}

如果您已上傳要使用的影像，請前往下一個步驟， [建立轉盤集](#creating-carousel-sets). 請注意，在啟用Dynamic Media後，必須上傳輪播中使用的影像。

若要上傳影像橫幅，請參閱 [上傳資產](managing-assets-touch-ui.md).

## 建立轉盤集 {#creating-carousel-sets}

>[!NOTE]
>
>必須將非管理使用者新增至 **[!UICONTROL dam-users]** 群組，以建立或編輯輪播橫幅。 如果您在建立或編輯時遇到問題，請咨詢系統管理員，該管理員可將您添加到 **dam-users** 群組。

**建立轉盤集的方式**:

1. 在「資產」中，導覽至您要建立轉盤集的資料夾，然後點選 **[!UICONTROL 建立>轉盤集]**.
1. 在 **[!UICONTROL 轉盤橫幅編輯器]** 頁面，點選 **[!UICONTROL 點選以開啟資產選擇器]** 來選擇第一張幻燈片的影像。

   在 **[!UICONTROL 轉盤橫幅編輯器]** 頁面，執行下列其中一項操作：

   * 在頁面的左上角附近，點選 **[!UICONTROL 添加幻燈片]** 表徵圖。
   * 在頁面中間附近，點選 **[!UICONTROL 點選以開啟資產選擇器]**.

   點選以選取您要納入轉盤集的資產。選取的資產上面有核取標籤圖示。完成後，在頁面右上角附近點選 **[!UICONTROL 選擇]**.

   使用「資產選擇器」，您可以輸入關鍵字並點選「回報」來搜尋 **[!UICONTROL 資產]**。您也可以套用篩選條件來調整搜尋結果。您可以依路徑、系列、檔案類型和標籤來篩選。選取篩選，然後點選工具 **[!UICONTROL 列上的]** 「篩選」圖示。點選 **[!UICONTROL 檢視]** 圖示並選取 **[!UICONTROL 欄檢視]**, **[!UICONTROL 卡片檢視]**，或 **[!UICONTROL 清單檢視]**.

   請參閱 [使用選取器](working-with-selectors.md) 以取得更多資訊。

1. 繼續新增投影片，直到新增您要在轉盤集中旋轉的所有影像為止。
1. （選用）執行下列任一操作：

   * 如有必要，請拖曳幻燈片以重新排序設定清單中的影像。
   * 若要刪除影像，請選取影像，然後點選 **[!UICONTROL 刪除幻燈片]** 的上界。
   * 若要套用預設集，在頁面右上角附近，點選預設集下拉式清單，然後選取要一次套用至該集的預設集。

   要刪除幻燈片，請點選幻燈片，然後點選 **[!UICONTROL 刪除幻燈片]** 的下一頁。 要移動幻燈片，請點選訂單表徵圖並按住並移動到所需位置。

1. 在幻燈片中添加影像後，可以將熱點、影像映射或兩者添加到影像中。 請參閱 [添加熱點或影像映射](#adding-hotspots-or-image-maps-to-an-image-banner).
1. 您可以點選或按一下「行為」和「外觀」標籤，並對轉盤橫幅的外觀或特定元件的行為進行調整，以變更轉盤集的視覺設計和行為。 請參閱 [管理檢視器預設集](viewer-presets.md) 以取得如何使用檢視器編輯器的詳細資訊。

   >[!NOTE]
   >
   >對於輪播橫幅，下列項目可能是您要調整的項目：
   >* 影像顯示的持續時間。 依預設，每個影像會顯示9秒。
   >* 動畫. 依預設，每個投影片轉變都會淡出。 您可以將其變更為滑動轉變。
   >* 按鈕的樣式。 使用者可以點選每個點或數字來旋轉橫幅。 您可以更改設定指示符按鈕的顯示位置（以及它們是數字或點狀樣式）及其大小。
   >* 更改影像映射的突出顯示樣式或用於熱點的表徵圖。
   >* 編輯檢視器預設集之前，請選取要作為預設集基礎的樣式。 如果您不這麼做，當您開始編輯檢視器預設集時，如果您決定變更不同的預設集，將會失去所有變更。


   您也可以預覽轉盤橫幅的外觀。 請參閱 [（選用）預覽轉盤橫幅](#optional-previewing-carousel-banners).

1. 點選 **[!UICONTROL 儲存]** 完成時。

## 向影像橫幅添加熱點或影像映射 {#adding-hotspots-or-image-maps-to-an-image-banner}

您可以使用轉盤集編輯器將熱點或影像地圖新增至橫幅。

添加熱點或影像映射時，可以將其定義為快速視圖彈出式顯示、超連結或體驗片段。

請參閱 [體驗片段](/help/sites-authoring/experience-fragments.md).

>[!NOTE]
>
>請注意，當您將檢視器嵌入體驗片段時，「輪播橫幅」中的社交媒體分享工具不受支援。 若要解決此問題，您可以使用或建立沒有社交媒體共用工具的檢視器預設集。 這類檢視器預設集可讓您成功將其內嵌在體驗片段中。

將熱點或影像映射添加到影像時，請記住保存您的工作。 **[!UICONTROL 還原]** 和 **[!UICONTROL 取消復原]** 目前建立/編輯工作階段期間，會支援位於頁面右上角附近的選項。

完成轉盤橫幅的建立後，您可以選擇使用 **[!UICONTROL 預覽]** 來查看轉盤橫幅對客戶的呈現方式。

請參閱 [（選用）預覽轉盤橫幅](#optional-previewing-carousel-banners).

>[!NOTE]
>
>將熱點添加到 [互動式影像](interactive-images.md) 或輪播橫幅，熱點資訊會儲存在相對於影像位置的相同中繼資料位置，而不論是互動式影像或輪播橫幅。 此功能表示您可以在任一檢視器中輕鬆重複使用相同的影像，及其定義的熱點資料。
>
>但請注意，轉盤橫幅支援影像上的影像地圖，這些影像中也可能包含熱點；互動式影像則否。 如果您要建立使用相同影像的互動式影像或輪播橫幅，請記住這一點。 您可能想要使用相同影像的個別副本，建立互動式影像和輪播橫幅。

>[!NOTE]
>
>如果您正在使用熱點編輯互動式影像並裁切影像，則會刪除熱點。

**向影像橫幅添加熱點**:

1. 從「資產」，導覽至您要進行互動式的轉盤集。
1. 選取轉盤集並點選 **[!UICONTROL 編輯]**.
1. 在轉盤檢視器編輯器中，選取您要建立互動式的投影片。
1. 在頁面的左上角附近，點選「熱點 **[!UICONTROL 」]****[!UICONTROL 或「影像地圖」]**。
1. 執行下列任一操作：

   * 對於熱點：在影像上，點選您要熱點出現的位置。
   * 對於影像映射：在影像上，點選，然後從左上角拖曳至右下角，以建立影像地圖區域。 通過拖動角，可以調整影像映射的大小。

   如有必要，請將熱點或影像映射拖動到新位置。 根據需要添加其他熱點或影像映射。

   若要刪除熱點或影像地圖，請點選「動 **[!UICONTROL 作]** 」標籤。在「地 **[!UICONTROL 圖與熱點]** 」標題下，從「選定類型 **** 」下拉菜單中，選擇要刪除的熱點或影像映射的名稱。點選功 **[!UICONTROL 能表旁的]** 「垃圾筒」圖示，然後點選「 **[!UICONTROL 刪除」]**。

1. 在「名稱」文本欄位中，鍵入熱點或影像映射的名稱。 此名稱也會顯示在 **[!UICONTROL 地圖與熱點]** 下拉式清單。 如果您決定在未來進行變更，提供名稱可讓您輕鬆識別熱點或影像地圖。
1. 在 **[!UICONTROL 動作]** 標籤：

   * 點選 **[!UICONTROL 快速檢視]**.

      * 如果您是AEM Sites和電子商務客戶，請點選 **[!UICONTROL 產品選擇器]** 圖示（放大鏡）以開啟 **[!UICONTROL 選擇產品]** 頁面。 點選您要使用的產品，然後點選頁面右上角的核取記號以返回 **[!UICONTROL 轉盤橫幅編輯器]**.
      * 如果您不是AEM Sites或電子商務客戶

         * 請參閱 [識別熱點變數](#identifying-hotspot-and-image-map-variables) ，因為您可能想要定義這些變數。
         * 然後，手動輸入SKU值。 在 **[!UICONTROL SKU值]** 文字欄位中，輸入產品的SKU（庫存保存單位），這是您提供之每個不同產品或服務的唯一識別碼。 輸入的SKU值會自動填入Quickview模板的變數部分，以便系統知道將點選熱點與特定SKU的Quickview關聯。
         * （可選）如果「快速檢視」中有其他變數需要用來進一步識別產品，請點選 **[!UICONTROL 新增一般變數]**. 在文字欄位中，指定其他變數。 例如， `category=Mens` 是新增的變數。
         * 請參閱 [使用選取器](working-with-selectors.md) 以取得更多資訊。
   * 點選 **[!UICONTROL 超連結]**.

      * 如果您是AEM Sites客戶，請點選 **[!UICONTROL 網站選取器]** 圖示（資料夾）導覽至URL。

         >[!NOTE]
         >如果您的互動式內容有連結與相對URL(尤其是連結至AEM Sites頁面)，則無法使用以URL為基礎的連結方法。

      * 若您是獨立客戶，請在 **[!UICONTROL HREF]** 文字欄位，指定連結網頁的完整URL路徑。

         請務必指定要在新的瀏覽器標籤（建議的預設值）或相同的標籤中開啟連結。

         請參閱 [使用選取器](working-with-selectors.md) 以取得更多資訊。
   * 點選 **[!UICONTROL 體驗片段]**.

      * 如果您是AEM Sites客戶，請點選 **[!UICONTROL 搜尋]** 圖示（放大鏡）以開啟「體驗片段」頁面。 點選您要使用的體驗片段，然後點選 **[!UICONTROL 選擇]** 位於頁面的右上角，以返回「熱點」管理頁面。

         請參閱 [體驗片段](/help/sites-authoring/experience-fragments.md).

         **附註**:請注意，當您將檢視器嵌入體驗片段時，「輪播橫幅」中的社交媒體分享工具不受支援。 若要解決此問題，您可以使用或建立沒有社交媒體共用工具的檢視器預設集。 這類檢視器預設集可讓您成功將其內嵌在體驗片段中。

      * 指定體驗片段在橫幅上顯示的寬度和高度。

   ![experience_fragment-carouselbanner](assets/experience_fragment-carouselbanner.png)

   您也可以預覽轉盤橫幅的外觀。 請參閱 [（選用）預覽轉盤橫幅](#optional-previewing-carousel-banners).

1. 點選 **[!UICONTROL 儲存]**.
1. 發佈轉盤集。 發佈會建立您可在網站頁面上使用的內嵌程式碼或URL。 如果您是AEM Sites客戶，可以直接將轉盤集新增至網頁。

   請參閱 [發佈資產](publishing-dynamicmedia-assets.md).

   請參閱 [新增轉盤集至您的網站登陸頁面](#adding-a-carousel-banner-to-your-website-page)

## 編輯轉盤集 {#editing-carousel-sets}

>[!NOTE]
>
>必須將非管理使用者新增至 **[!UICONTROL dam-users]** 群組，以便能夠建立或編輯輪播橫幅。 如果您在建立或編輯時遇到問題，請咨詢系統管理員，該管理員可將您添加到 **[!UICONTROL dam-users]** 群組。

您可以對轉盤集執行各種編輯工作，例如：

* 將投影片新增至轉盤集。 另請參閱 [使用選取器](working-with-selectors.md).
* 在轉盤集中重新排序投影片。
* 刪除轉盤集中的資產。
* 套用檢視器預設集。
* 刪除轉盤集。
* 添加或編輯熱點和影像映射。 另請參閱 [使用選取器](working-with-selectors.md).

請注意，如果您正在編輯具有熱點的互動式影像並裁剪影像，則會刪除熱點。

**若要編輯轉盤集**:

1. 執行下列任一操作：

   * 將滑鼠指標暫留在轉盤集資產上，然後點選 **[!UICONTROL 編輯]** （鉛筆圖示）。
   * 將游標暫留在轉盤集資產上，點選 **[!UICONTROL 選擇]** （勾選圖示），然後點選 **[!UICONTROL 編輯]** 的上界。
   * 點選「轉盤集」資產，然後在頁麵點選的左上角 **[!UICONTROL 編輯]** （鉛筆圖示）。

1. 若要編輯轉盤集，請執行下列任一操作：

   * 若要新增投影片，請點選 **[!UICONTROL 添加幻燈片]** 圖示，然後導覽至您要新增至該投影片的資產，然後點選核取標籤。
   * 要重新排序幻燈片，請將幻燈片拖到新位置（選擇重新排序表徵圖以移動項目）。
   * 若要新增熱點或影像地圖，請點選熱點或影像地圖圖示，然後參閱 [添加熱點和影像映射](#adding-hotspots-or-image-maps-to-an-image-banner).
   * 若要編輯轉盤集的外觀或行為，請點選 **[!UICONTROL 外觀]** 標籤或 **[!UICONTROL 行為]** ，然後設定所需的選項。
   * 要編輯熱點或影像映射，請在相應的幻燈片上選擇熱點或影像映射，並根據需要在 **[!UICONTROL 動作]** 標籤。
   * 要刪除幻燈片，請選擇它，然後點選 **[!UICONTROL 刪除幻燈片]** 的上界。
   * 若要套用預設集，在頁面右上角附近，點選預設集下拉式清單，然後選取檢視器預設集。
   * 若要刪除整個轉盤集，請導覽至轉盤集，選取它，然後點選 **[!UICONTROL 刪除]**.

## （選用）預覽轉盤橫幅 {#optional-previewing-carousel-banners}

您可以使用 **[!UICONTROL 預覽]** 查看您的轉盤橫幅對客戶的看法，並測試轉盤橫幅熱點和影像地圖，以確保他們的行為符合預期。

當您對輪播橫幅感到滿意時，即可發佈它。

* 請參閱 [將視訊或影像檢視器內嵌在網頁上](embed-code.md).
* 請參閱 [將URL連結至您的Web應用程式](linking-urls-to-yourwebapplication.md). 請注意，如果您的互動式內容具有具有相對URL的連結，尤其是連結至AEM Sites頁面的連結，則無法使用以URL為基礎的連結方法。
* 請參閱 [將Dynamic Media Assets新增至頁面。](adding-dynamic-media-assets-to-pages.md)

您可以從轉盤編輯器（偏好的方法）或 **[!UICONTROL 檢視器]** 清單。

**若要預覽輪播橫幅**:

1. 在 **[!UICONTROL 資產]**，導覽至您已建立的現有輪播橫幅，然後點選以開啟它。
1. 點選 **[!UICONTROL 編輯]**.
1. 在工具列右角的檢視器預設集清單中，選取檢視器以預覽轉盤橫幅。

   ![experience_fragment-carouselbanner-viewerdown](assets/experience_fragment-carouselbanner-viewerdropdown.png)

1. 點選 **[!UICONTROL 預覽]**.
1. 點選影像上的熱點或影像地圖，以測試其相關聯的動作。

**從檢視器清單預覽輪播橫幅**:

1. 在 **[!UICONTROL 資產]**，導覽至您已建立的現有輪播橫幅，然後點選以開啟它。
1. 在 **[!UICONTROL 預覽]** 頁面，點選 **[!UICONTROL 內容]** 表徵圖。
1. 在 **[!UICONTROL 檢視器]** 清單（在頁面左側的面板中），點選您要使用的轉盤橫幅檢視器預設集的名稱。
1. 點選影像上的熱點或影像地圖，以測試其相關聯的動作。

## 發佈輪播橫幅 {#publishing-carousel-banners}

您必須發佈輪播才能使用。 發佈轉盤集會啟用URL和內嵌程式碼。 它也會將轉盤發佈至Dynamic Media雲端，與CDN整合以提供可擴充且效能優異的傳送。

如果您使用浮動切換橫幅的現有互動式影像與熱點，在您發佈浮動切換橫幅後，必須個別發佈互動式影像。

此外，如果您修改轉盤橫幅中使用的已發佈互動式影像，則必須先發佈互動式影像，這些變更才會反映在轉盤橫幅中。

請參閱 [發佈Dynamic Media Assets](publishing-dynamicmedia-assets.md) 以取得如何發佈輪播橫幅的資訊。

## 新增轉盤橫幅至您的網站頁面 {#adding-a-carousel-banner-to-your-website-page}

上傳橫幅影像以建立輪播、新增熱點和/或影像對應至橫幅並發佈輪播集後，您現在可以將其新增至現有的網站頁面。

如果您是AEM Sites客戶，您可以將互動式媒體元件拖曳至頁面，直接將輪播橫幅新增至頁面。 請參閱 [將Dynamic Media Assets新增至頁面。](adding-dynamic-media-assets-to-pages.md)

不過，如果您是獨立的AEM資產客戶，您可以依照本節所述，手動將轉盤橫幅新增至您的網站登陸頁面。

1. 複製已發佈的轉盤集的內嵌程式碼。

   請參閱 [將視訊或影像檢視器內嵌在網頁上](embed-code.md).

1. 將您從AEM Assets複製的內嵌程式碼新增至網頁。

   複製的內嵌程式碼會回應，因此應會自動符合頁面的內嵌區域。

## 將轉盤橫幅與現有的快速檢視整合 {#integrating-the-carousel-banner-with-an-existing-quickview}

只有當您是獨立AEM Assets客戶時，才適用此工作。

此程式的最後一個步驟是將轉盤橫幅與網站上現有的Quickview實作整合。 每個Quickview實施都是獨一無二的，需要一種最可能需要前端IT人員協助的特定方法。

現有的Quickview實施通常會依下列順序呈現網頁上發生的一系列相關動作：

1. 使用者會在您網站的使用者介面中觸發元素。
1. 前端程式碼會根據步驟1中觸發的使用者介面元素來取得快速檢視URL。
1. 前端程式碼會使用步驟2取得的URL來傳送Ajax要求。
1. 後端邏輯會將對應的Quickview資料或內容傳回前端程式碼。
1. 前端程式碼會載入Quickview資料或內容。
1. （可選）前端代碼將載入的Quickview資料轉換為HTML表示。
1. 前端程式碼會顯示強制回應對話方塊或面板，並在畫面上為一般使用者轉譯HTML內容。

這些呼叫可能不代表獨立的公用API呼叫，而網頁邏輯可從任意步驟呼叫。 相反地，它是連結呼叫，其中每個後續步驟都會隱藏在前一個步驟的最後一個階段（回撥）中。

在輪播橫幅正在取代步驟1和部分步驟2的同時，當使用者按一下輪播橫幅內的熱點或影像地圖時，檢視器會處理這類使用者互動。 檢視器會將事件傳回至網頁，其中包含先前新增的所有熱點或影像地圖資料。

在這種事件處理常式中，前端程式碼會執行下列動作：

* 監聽轉盤橫幅發出的事件。
* 根據熱點或影像地圖資料建構Quickview URL。
* 觸發從後端載入Quickview並在畫面上呈現以供顯示的程式。

AEM Assets傳回的內嵌程式碼已有可供使用的事件處理常式，且已註解。

因此，只需取消對代碼的註解，並將虛擬處理程式主體替換為特定網頁特有的代碼。

構建Quickview URL的過程與識別先前涵蓋的熱點和影像地圖變數的過程基本相反。

請參閱 [識別熱點和影像映射變數](#identifying-hotspot-and-image-map-variables).

觸發Quickview URL並啟動Quickview面板的最後一個步驟很可能需要IT部門的前端IT人員協助。 他們具備最佳知識，了解如何從正確的步驟準確觸發Quickview實施，並擁有可供使用的Quickview URL。

## 使用「快速檢視」建立自訂快顯視窗 {#using-quickviews-to-create-custom-pop-ups}

請參閱 [使用快速檢視建立自訂快顯視窗](custom-pop-ups.md).

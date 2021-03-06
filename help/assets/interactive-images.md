---
title: 互動影像
seo-title: 互動影像
description: 了解如何在動態媒體中使用互動式影像
seo-description: 了解如何在動態媒體中使用互動式影像
uuid: e8f79bc1-fccb-48d0-aca1-7f319c595fe9
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d630499d-740d-4979-8a34-9e3fcc3b5a23
exl-id: 4d3299e2-269b-4a41-a979-c884c707666d
feature: 互動影像
role: User
source-git-commit: cdee53ea75faa2e6d1a1ec6ca7aa8bf8b8840e46
workflow-type: tm+mt
source-wordcount: '4261'
ht-degree: 0%

---

# 互動影像 {#interactive-images}

將「可購買」熱點拖放到影像上，即可輕鬆讓靜態影像豐富、吸引客戶的體驗。 可購買熱點將有關產品或服務的附加資訊與直接、銷售點的「添加到購物車」或「購買」功能相結合。 客戶可以點選這些熱點並直接連結到產品或服務、將其添加到購物車或連結到網頁。 這類直接體驗可增加客戶參與和您網站上的轉換。

以下是帶有Quickview彈出窗口的可購買橫幅。 用戶通過點選模型上的圓或「熱點」來激活「快速視圖」。

![chlimage_1-368](assets/chlimage_1-368.png)

前往下列頁面，查看上述網頁上的互動式影像執行中功能：

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html)

## 觀看互動式影像橫幅的建立方式 {#watch-how-interactive-image-banners-are-created}

觀看[如何建立互動式影像橫幅的10分鐘33秒逐步說明](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner)。 您也將學習如何預覽、編輯和傳送互動式影像橫幅。

## 快速入門：互動式影像 {#quick-start-interactive-images}

下列逐步工作流程說明旨在協助您在AEM Assets中使用互動式影像快速上手並執行。

查看某些快速入門任務中的&#x200B;**Example**&#x200B;標題。 其中包含以下網頁範例為基礎的簡短教學課程，目前尚未新增互動式影像：

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html)

本教學課程可協助您說明如何將互動式影像整合到您自己的網站上。

**互動式影像工作流程**:

1. **（可選）識別熱點變數**  — 如果您使用AEM Assets和Dynamic Media獨立，請先識別現有Quickview實作中使用的動態變數，以便在建立互動式影像時輸入熱點資料。請參閱[（可選）識別熱點變數](#optional-identifying-hotspot-variables)。

   不過，如果您使用AEM Sites或AEM eCommerce或兩者，則不需要此步驟。

   請參閱AEM Assets中的[電子商務概念](/help/sites-administering/concepts.md)。

1. **（可選）建立互動式影像檢視器預設集**  — 自訂用來表示熱點的圖形影像。如果您想要使用名為`Shoppable_Banner`的現成可用互動式影像檢視器預設集，則不需要建立您自己的互動式影像檢視器預設集。

   請參閱[（選用）建立互動式影像檢視器預設集](managing-viewer-presets.md#creating-a-new-viewer-preset)。

1. **上傳影像橫幅**  — 上傳您要進行互動的影像橫幅。

   請參閱[上傳影像橫幅](#uploading-an-image-banner)。

1. **將熱點新增至影像橫幅**  — 新增一或多個熱點至影像橫幅，並將每個熱點與超連結、快速檢視或體驗片段等動作建立關聯。添加熱點後，將通過發佈交互影像來完成此任務。

   * 請參閱[向影像橫幅添加熱點](#adding-hotspots-to-an-image-banner)。
   * 請參閱[預覽互動式影像](#optional-previewing-interactive-images) — 選用。 如果需要，可以查看可購買橫幅的表示並測試其交互性。
   * 如需如何發佈互動式影像資產的詳細資訊，請參閱[發佈資產](publishing-dynamicmedia-assets.md)。

1. **在AEM中將互動式影像新增至您的網站或網站**

   * 如果您使用AEM Sites或AEM eCommerce，或兩者搭配，可將互動式媒體元件拖曳至頁面，直接將互動式影像新增至AEM的網頁。 請參閱[將Dynamic Media資產新增至頁面](adding-dynamic-media-assets-to-pages.md)。
   * 如果您使用獨立的AEM Assets和Dynamic Media，則必須複製網站上的內嵌程式碼，然後將其與現有的Quickview整合。 請參閱[整合互動式影像與您的網站](#integrating-an-interactive-image-with-your-website)。
   * 如果您使用第三方WCM（網頁內容管理員），則必須將新的互動式視訊與網站上使用的現有Quickview實作整合。 請參閱[將互動式影像與現有Quickview](#integrating-an-interactive-image-with-an-existing-quickview)整合。

## （可選）識別熱點變數 {#optional-identifying-hotspot-variables}

>[!NOTE]
>
>只有在以下情況為真時才需要此任務：
>
>* 您想要透過觸發Quickviews來為影像新增互動功能。
>* 您的AEM實作會&#x200B;*不*&#x200B;使用電子商務整合架構，從任何電子商務解決方案（例如IBM Websphere Commerce、Elastic Path、hybris或Intershop）將產品資料提取至AEM。 請參閱AEM Assets中的[電子商務概念](/help/sites-administering/concepts.md)。

>
>
如果您的AEM實作使用電子商務，您可以略過此工作，並繼續執行下一個工作。

首先，識別您現有Quickview實作所使用的動態變數，以便您可以輸入熱點資料來建立互動式影像。

在AEM Assets中為橫幅影像新增熱點時，您需要指派SKU(庫存保管單位；您提供的每個不重複產品或服務的唯一識別碼)，以及每個熱點的選用其他變數。 這些熱點變數稍後用於匹配熱點與Quickview內容。

請務必正確識別要與熱點資料關聯的變數數目和類型。 每個新增至橫幅影像的熱點都必須包含足夠的資訊，才能明確識別現有後端系統中的產品。

識別要用於熱點資料的一組變數有不同的方法。

有時，與負責現有Quickview實施的IT專家協商可能已足夠，因為他們可能知道在系統中標識Quickview所需的最少一組資料。 不過，在大多數情況下，您也可以簡單分析前端程式碼的現有行為。

大多數Quickview實施都使用以下範例：

* 使用者在網站上啟動使用者介面元素。例如，按一下&#x200B;**[!UICONTROL Quickview]**&#x200B;按鈕。
* 網站會視需要傳送Ajax要求至後端，以載入Quickview資料或內容。
* 快速檢視資料會轉譯為內容，以準備在網頁上轉譯。
* 最後，前端代碼在螢幕上直觀地呈現這樣的內容。

接著，方法是造訪實作「快速檢視」功能的現有網站的不同區域、觸發快速檢視並擷取網頁所傳送的Ajax URL，以載入快速檢視資料或內容。

通常您不需要使用任何專用的除錯工具。 現代網頁瀏覽器的功能是能夠勝任工作的網頁檢查員。 以下是一些Web瀏覽器的示例，其中包括Web檢查員：

* 若要在Google Chrome中查看所有傳出的HTTP請求，請按F12以開啟&#x200B;**[!UICONTROL 開發人員工具]**&#x200B;面板，然後按一下&#x200B;**[!UICONTROL 網路]**&#x200B;標籤。

   在Mac上，按&#x200B;**[!UICONTROL Command+Option+I]**&#x200B;以開啟&#x200B;**[!UICONTROL Developer Tools]**&#x200B;面板，然後按一下「Network（網路）」頁簽。

* 在Firefox中，您可以按F12並使用其Net標籤來啟動Firebug外掛程式，或使用內建的&#x200B;**[!UICONTROL Inspector]**&#x200B;工具及其&#x200B;**[!UICONTROL Network]**&#x200B;標籤。

   在Mac上，按&#x200B;**[!UICONTROL Command+Option+I]**&#x200B;以開啟&#x200B;**[!UICONTROL Developer Tools]**&#x200B;面板，然後按一下&#x200B;**[!UICONTROL Inspector]**&#x200B;標籤。

在瀏覽器中開啟網路監視時，觸發頁面上的快速檢視。

現在，在網路記錄中找到Quickview Ajax URL，並複製記錄的URL以供日後分析之用。 在大多數情況下，當您觸發Quickview時，會有許多請求傳送至伺服器。 Quickview Ajax URL通常是清單中第一個的URL。 它具有複雜的查詢字串部分或路徑，其響應MIME類型為`text/html`、`text/xml`或`text/javascript`。

在此程式中，請務必瀏覽網站的不同區域，包含不同的產品類別和類型。 原因是Quickview URL可能有指定網站類別中常見的部分，但只有當您造訪網站的其他區域時才會變更。

在最簡單的情況下，Quickview URL中唯一的變數部分是產品SKU。 在這種情況下，SKU值是您在橫幅影像中新增熱點所需的唯一資料片段。

但是，在複雜的情況下，Quickview URL除了SKU以外，還有不同的元素，例如類別ID、顏色代碼、大小代碼等。 在這種情況下，在AEM Assets的可購買互動式影像功能中，每個元素都是熱點資料定義中的個別變數。

請考量下列Quickview URL範例及其產生的熱點變數：

<table> 
     <tbody> 
      <tr> 
       <td><p>在查詢字串中找到的單一SKU。</p> </td> 
       <td><p>錄制的Quickview URL包括：</p> 
        <ul> 
         <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li> 
         <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li> 
         <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li> 
         <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li> 
        </ul> <p>URL中唯一的變數部分是productId=查詢字串參數的值，而這顯然是SKU值。 因此，我們的熱點只需要填入<strong><code>866558</code></strong>、<strong><code>1196184</code></strong>、<strong><code>1081492</code></strong>、<strong><code>1898294</code></strong>之類值的SKU欄位。</p> </td> 
      </tr> 
      <tr> 
       <td><p>單一SKU，可在URL路徑中找到。</p> </td> 
       <td><p>錄制的Quickview URL包括：</p> 
        <ul> 
         <li><p><code>https://server/product/6422350843</code></p> </li> 
         <li><p><code>https://server/product/1607745002</code></p> </li> 
         <li><p><code>https://server/product/0086724882</code></p> </li> 
        </ul> <p>變數部分位於路徑的最後一部分，它將成為熱點的SKU值：<strong><code>6422350843</code></strong>、<strong><code>1607745002</code></strong>、<strong><code>0086724882</code></strong>。</p> </td> 
      </tr> 
      <tr> 
       <td><p>查詢字串中的SKU和類別ID。</p> </td> 
       <td><p>錄制的Quickview URL包括：</p> 
        <ul> 
         <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li> 
         <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li> 
         <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li> 
        </ul> <p>在此情況下，URL中會有兩個不同的部分。 SKU儲存在<code>prodId</code>參數和類別ID中</p><p><code>categoryId</code></p><ul><li><p><code>305466</code><code>categoryId</code><code>1100004</code></p></li><li><p><code>310181</code><code>categoryId</code><code>1100004</code></p></li><li><p><code>308706</code><code>categoryId</code><code>1740148</code></p></li></ul><p></p></td></tr></tbody></table></td></tr><tr></tr></table>

**範例**

您可以將上述三個範例中使用的相同方法套用至示範網頁：

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html)

示範網頁有數個產品縮圖，每個縮圖都有標示為&#x200B;**[!UICONTROL 「查看更多內容」的「快速檢視」按鈕。]**&#x200B;在Web瀏覽器的偵錯工具仍處於啟用狀態時，按一下每個按鈕並記下記錄的Quickview URL。 啟用頁面上所有的四個產品快速檢視後，您就會有向後端提出的快速檢視請求清單：

* `/datafeed/Men-Windbreaker.json`
* `/datafeed/Men-SimpleHenley.json`
* `/datafeed/Men-CamoPullover.json`
* `/datafeed/Women-QuiltedDownJacket.json`

查看這些伺服器呼叫後，您會發現產品專屬資訊僅存在於請求路徑中。 您也注意到查詢字串完全未使用，且涉及兩種不同類型的資料片段：

* 第一種是「男」或「女」。 您可以將此稱為「產品類別」。
* 第二種類型是產品名稱，例如CamoPullover。 您可以假設這是產品SKU。

根據此資訊，整個Quickview URL的模式如下：

`/datafeed/$categoryId$-$SKU$.json`

根據這種分析，熱點應使用`categoryId`和`SKU`。

您現在可以使用AEM Assets中的可購買互動式影像功能，上傳影像橫幅並新增熱點。

## （可選）建立互動式影像檢視器預設集 {#optional-creating-an-interactive-image-viewer-preset}

您可以選擇使用隨AEM Assets提供的預設現成互動式影像檢視器預設集，稱為&#x200B;**[!UICONTROL Shopbable_Banner]**。 或者，您可以建立自己的自訂檢視器預設集以搭配互動式影像使用。

當您建立自訂互動式影像檢視器預設集時，可以決定影像橫幅上熱點的外觀。 在建立查看器預設集時，您可以選擇使用預定義影像庫中的熱點圖形。

儲存檢視器預設集後，系統會在AEM Assets的&#x200B;**[!UICONTROL 檢視器預設集]**&#x200B;清單頁面上自動啟動（開啟）該預設集。 此功能表示它會顯示在互動式媒體元件中，以及您每次檢視資產時。 不過，若要使用此檢視器預設集傳送&#x200B;*互動式橫幅，您也必須* publish *您的檢視器預設集（自訂或現成的檢視器預設集也是如此）。*

**若要建立互動式影像檢視器預設集**:

1. 在左側導軌中，點選「 **[!UICONTROL 工具>資產>檢視器預設集]**」。
1. 在頁面的右上角附近，點選&#x200B;**[!UICONTROL Create]**。
1. 在「**[!UICONTROL 新建查看器預設集]**」對話框中，鍵入一個名稱以說明互動式橫幅查看器預設集。

   這是儲存後會顯示在&#x200B;**[!UICONTROL 檢視器預設集]**&#x200B;清單頁面中的標題。
1. 在&#x200B;**[!UICONTROL 多媒體類型]**&#x200B;下拉式選單中，選取&#x200B;**[!UICONTROL 互動式影像]**。
1. 點選&#x200B;**建立**。
1. 在「**[!UICONTROL 編輯檢視器預設集]**」頁面上，點選「**[!UICONTROL Appearance]**」標籤。
1. 執行下列任一操作：

   * 若要上傳您要在影像上使用的自己熱點影像，請點選「資產選擇器&#x200B;]**」圖示。**[!UICONTROL &#x200B;在&#x200B;**[!UICONTROL 選取內容]**&#x200B;頁面中，導覽至您要使用的熱點影像，選取它，然後點選右上角的&#x200B;**[!UICONTROL 勾選標籤]**&#x200B;圖示。
   * 若要選取預先定義的熱點影像，請點選「熱點圖庫」]**圖示。**[!UICONTROL &#x200B;在熱點圖庫盤上，點選您要使用的熱點影像。

1. 在頁面的右上角附近，點選&#x200B;**[!UICONTROL Save]**。

   請務必發佈新的檢視器預設集。

   請參閱[發佈您已新增的檢視器預設集](managing-viewer-presets.md#publishing-viewer-presets)。

   您現在可以上傳影像橫幅了。

## 上傳影像橫幅 {#uploading-an-image-banner}

如果已上傳要使用的影像，請前進到下一步[向影像橫幅添加熱點](#adding-hotspots-to-an-image-banner)。

**上傳影像橫幅**:

1. 上傳您要製作互動式的影像橫幅。

   請參閱[上傳資產](managing-assets-touch-ui.md#uploading-assets)。

   您現在可以將熱點添加到影像橫幅中；請參閱下面的下一個任務。

## 向影像橫幅添加熱點 {#adding-hotspots-to-an-image-banner}

您可以使用&#x200B;**[!UICONTROL 熱點管理]**&#x200B;頁面上的編輯器將熱點添加到影像橫幅。

添加熱點時，可以將熱點定義為「快速視圖」彈出式顯示、超連結或體驗片段。

請參閱[體驗片段](/help/sites-authoring/experience-fragments.md)。

>[!NOTE]
>
>請注意，當您將檢視器內嵌在體驗片段時，互動式影像中的社交媒體共用工具不受支援。 若要解決此問題，您可以使用或建立沒有社交媒體共用工具的檢視器預設集。 這類檢視器預設集可讓您成功將其內嵌在體驗片段中。

**** 目前 **** 的建立/編輯工作階段期間，支援位於頁面右上角附近的「取消復原」選項。

建立完互動式影像後，您可以使用&#x200B;**[!UICONTROL 預覽]**&#x200B;來查看互動式影像在客戶面前的呈現方式。

請參閱[（選用）預覽互動式影像](#optional-previewing-interactive-images)。

>[!NOTE]
>
>在互動式影像或轉盤橫幅中將熱點新增至影像時，熱點資訊會儲存在相對於影像位置的相同中繼資料位置，而無論該位置是互動式影像還是轉盤橫幅。 這項功能意味著，您可以在任一查看器中輕鬆地重複使用同一影像及其定義的熱點資料。
>
>但請注意，轉盤橫幅支援影像上的影像地圖，這些影像中也可能包含熱點；互動式影像則否。 如果您要建立使用相同影像的互動式影像或輪播橫幅，請記住這一點。 您可能想要使用相同影像的個別副本，建立互動式影像和輪播橫幅。
>
>另請參閱[輪播橫幅](carousel-banners.md)。

>[!NOTE]
>
>如果您正在使用熱點編輯互動式影像並裁切影像，則會刪除熱點。

**要向影像橫幅添加熱點**:

1. 在「資產」檢視中，導覽至您要進行互動的影像橫幅。
1. 執行下列任一操作：

   * 暫留在影像上，然後點選&#x200B;**[!UICONTROL 選取]**（核取標籤圖示）。 在工具列上，點選&#x200B;**[!UICONTROL Edit]**。
   * 暫留在影像上，然後點選「**[!UICONTROL 更多動作]**（三個點圖示）> **[!UICONTROL 編輯]**」。
   * 點選影像以在&#x200B;**[!UICONTROL 詳細資料檢視]**&#x200B;頁面中開啟。 在工具列上，點選&#x200B;**[!UICONTROL Edit]**。

1. 在頁面的左上角附近，點選「**[!UICONTROL 新增熱點]**」（手指點選圖示）以開啟「**[!UICONTROL 熱點管理]**」頁面。
1. 在頁面的左上角附近，點選「**[!UICONTROL Hotspot]**」。
1. a.在「熱點管理」**頁面的左上角附近，點選「**[!UICONTROL &#x200B;熱點&#x200B;]**」。**b.在影像上，點選您要熱點出現的位置。 如有必要，請拖動熱點以調整其位置。c.通過重複步驟a和b，根據需要添加其他熱點。
d.（可選）要刪除熱點，請在影像上選擇熱點，然後點選**[!UICONTROL Delete]**（垃圾桶表徵圖）**[!UICONTROL Hotposts]**&#x200B;標題下。

1. 在&#x200B;**[!UICONTROL Name]**&#x200B;文本欄位中，鍵入熱點的名稱。 此名稱也出現在&#x200B;**[!UICONTROL 所選熱點]**&#x200B;下拉清單中。
1. 執行下列任一操作：

   * 點選&#x200B;**[!UICONTROL Quickview]**。

      * 如果您是AEM Sites或電子商務客戶，請點選&#x200B;**[!UICONTROL 產品選擇器]**&#x200B;圖示（放大鏡）以開啟&#x200B;**[!UICONTROL 選取產品]**&#x200B;頁面。 點選您要使用的產品，然後點選頁面右上角的「**[!UICONTROL 選取]** 」，以返回「**[!UICONTROL 熱點管理]**」頁面。
      * 如果您是&#x200B;*not* AEM Sites或eCommerce客戶

         * 請參閱[識別熱點變數](#optional-identifying-hotspot-variables);您需要定義這些變數。
         * 然後，手動輸入SKU值。 在「**[!UICONTROL SKU值]**」文字欄位中，輸入產品的SKU（庫存保存單位），這是您提供之每個不同產品或服務的唯一識別碼。 輸入的SKU值會自動填入Quickview模板的變數部分，以便系統知道將點選熱點與特定SKU的Quickview關聯。
         * （可選）如果「快速檢視」中有其他變數需要用來進一步識別產品，請點選「**[!UICONTROL 新增一般變數]**」。 在文字欄位中，指定其他變數。 例如， `category=Mens`是新增的變數。
   * 點選&#x200B;**超連結**。

      * 如果您是AEM Sites客戶，請點選&#x200B;**[!UICONTROL 網站選取器]**&#x200B;圖示（資料夾）以導覽至URL。 請注意，如果您的互動式內容具有具有相對URL的連結，尤其是連結至AEM Sites頁面的連結，則無法使用以URL為基礎的連結方法。
      * 如果您是獨立客戶，請在&#x200B;**[!UICONTROL HREF]**&#x200B;文字欄位中，指定連結網頁的完整URL路徑。

      請務必指定要在新的瀏覽器標籤（建議的預設值）或相同的標籤中開啟連結。

      如需詳細資訊，請參閱[使用選取器](working-with-selectors.md) 。

   * 點選&#x200B;**體驗片段**。

      * 如果您是AEM Sites客戶，請點選&#x200B;**[!UICONTROL 搜尋]**&#x200B;圖示（放大鏡）以開啟&#x200B;**[!UICONTROL 體驗片段]**&#x200B;頁面。 點選您要使用的體驗片段，然後點選頁面右上角的「**[!UICONTROL 選取]** 」以返回「熱點」管理頁面。

         請參閱[體驗片段](/help/sites-authoring/experience-fragments.md)。
         >[!NOTE]
         >請注意，當您將檢視器內嵌在體驗片段時，互動式影像中的社交媒體共用工具不受支援。 若要解決此問題，您可以使用或建立沒有社交媒體共用工具的檢視器預設集。 這類檢視器預設集可讓您成功將其內嵌在體驗片段中。

      * 指定體驗片段在橫幅上顯示的寬度和高度。



1. 點選&#x200B;**[!UICONTROL Save]**&#x200B;以保存您的工作並返回&#x200B;**[!UICONTROL Browse]**&#x200B;頁面。
1. 發佈互動式影像。 發佈可讓橫幅透過雲端傳送，也可在您需要與第三方網站整合時產生內嵌程式碼。

   請參閱[發佈資產](managing-assets-touch-ui.md#publishing-assets)。

   新增熱點並發佈互動式影像後，您現在可以將其新增至現有網站。

   請參閱[整合互動式影像與您的網站](#integrating-an-interactive-image-with-your-website)。

   >[!NOTE]
   >
   >如果您正在使用熱點編輯互動式影像並裁切影像，則會刪除熱點。

### （可選）預覽互動式影像 {#optional-previewing-interactive-images}

您可以使用預覽來查看您的互動式影像在客戶看來會是什麼樣子的表示，並測試影像的熱點，以確保它們如預期般運作。

對互動式影像感到滿意時，即可發佈影像。\
請參閱[將視訊或影像檢視器內嵌在網頁上](embed-code.md)。\
請參閱[將URL連結到您的Web應用程式](linking-urls-to-yourwebapplication.md)。 請注意，如果您的互動式內容具有具有相對URL的連結，尤其是連結至AEM Sites頁面的連結，則無法使用以URL為基礎的連結方法。\
請參閱[將Dynamic Media資產新增至頁面。](adding-dynamic-media-assets-to-pages.md)

**若要預覽互動式影像**:

1. 在「資產」檢視中，導覽至您已建立的現有互動式影像，然後點選以在「預覽」中開啟它。
1. 在「預覽」頁面的左上角附近，在&#x200B;**[!UICONTROL Content]**&#x200B;下拉式清單中，點選&#x200B;**[!UICONTROL Viewers]**。
1. 在「**[!UICONTROL 檢視器]**」清單中，點選「**[!UICONTROL Shopbable_Banner]**」或您建立的互動式影像檢視器預設集名稱。
1. 點選影像上的熱點以測試其相關聯的動作。

## 發佈互動式影像資產 {#publishing-interactive-image-assets}

如需如何發佈互動式影像資產的詳細資訊，請參閱[發佈資產](publishing-dynamicmedia-assets.md)。

## 將互動式影像與您的網站整合 {#integrating-an-interactive-image-with-your-website}

上傳橫幅影像、新增熱點至影像並發佈互動式影像後，您現在可以將其新增至網站頁面。

如果您是AEM Sites客戶，可將互動式媒體元件拖曳至頁面上，以新增互動式影像。 請參閱[將Dynamic Media資產新增至頁面。](adding-dynamic-media-assets-to-pages.md)

如果您是獨立的AEM Assets客戶，您可以依照本節所述手動將互動式影像新增至您的網站。

1. 複製已發佈的互動式影像的內嵌程式碼。

   請參閱[將視訊或影像檢視器內嵌在網頁上](embed-code.md)。

1. 將複製的內嵌程式碼新增至網頁內所需的位置。

   複製的內嵌程式碼會設定為回應式環境，因此應自動符合指派的區域。

**範例**

以示範網站為例：

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html)

請注意，這三個人的圖片是靜態`IMG`標籤：

```xml
<img class="img-responsive" width="100%" title="Hero Image 2" alt="Hero Image 2" src="images/shoppable-banner.jpg">
```

只要移除`IMG`標籤，並以AEM Assets中複製的內嵌程式碼取代，整合就很簡單。 您可以在以下URL中看到結果，該URL顯示頁面上具有三個圓形熱點的可購買互動影像：

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-1.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-1.html)

>[!NOTE]
>
>因此，演示網站的可購買交互影像上的熱點僅用於顯示；它們尚未與現有的Quickviews整合。

要為響應環境將裁切應用於可購買的交互影像，可以將交互影像配置屬性`ZoomView.iscommand`包含到路徑 — 其中`ZoomView`是要調用的元件，`iscommand`是要應用的裁切影像伺服命令。

請參閱[ZoomView.iscommand](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/command-reference-configuration-attributes-interactive-images/r-html5-aem-interactive-image-config-attrib-zoomview-iscommand.html)配置屬性。

請參閱[裁切](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-crop.html)影像伺服命令。

您現在可以將互動式影像與網站上現有的Quickview整合。

## 將互動式影像與現有的Quickview整合 {#integrating-an-interactive-image-with-an-existing-quickview}

>[!NOTE]
>
>只有當您是獨立AEM Assets客戶時，才適用此工作。

此程式的最後一個步驟是將互動式影像與網站上現有的Quickview實作整合。 整合沒有適用於所有情況的解決方案。 每個Quickview實施都是獨一無二的，需要一種最可能需要前端IT人員協助的特定方法。

現有的Quickview實施通常會依下列順序呈現網頁上發生的一系列相關動作：

1. 使用者會在您網站的使用者介面中觸發元素。
1. 前端程式碼會根據步驟1中觸發的使用者介面元素來取得快速檢視URL。
1. 前端程式碼會使用步驟2取得的URL來傳送Ajax要求。
1. 後端邏輯會將對應的Quickview資料或內容傳回前端程式碼。
1. 前端程式碼會載入Quickview資料或內容。
1. （可選）前端代碼將載入的Quickview資料轉換為HTML表示法。
1. 前端程式碼會顯示強制回應對話方塊或面板，並在畫面上為一般使用者轉譯HTML內容。

這些呼叫可能不代表獨立的公用API呼叫，而網頁邏輯可從任意步驟呼叫。 相反地，它是連結呼叫，其中每個後續步驟都會隱藏在前一個步驟的最後一個階段（回撥）中。

在可購買交互影像替換步驟1和部分步驟2的同時，當用戶按一下可購買影像內的熱點時，觀看者處理這種用戶交互。 檢視器會傳回事件至網頁，其中包含先前新增至AEM Assets的所有熱點資料。

在這種事件處理常式中，前端程式碼會執行下列動作：

* 偵聽可購買互動式影像所發出的事件。
* 根據熱點資料構建快速視圖URL。
* 觸發從後端載入Quickview並在畫面上呈現以供顯示的程式。

AEM Assets傳回的內嵌程式碼已有可供使用的事件處理常式，且已加以註解，如下列反白顯示的程式碼片段所示：

```xml
        var s7interactiveimageviewer = new s7viewers.InteractiveImage({
            "containerId" : "s7interactiveimage_div",
            "params" : { 
                "serverurl" : "https://aodmarketingna.assetsadobe.com/is/image",
                "contenturl" : "https://aodmarketingna.assetsadobe.com/", 
                "config" : "/etc/dam/presets/viewer/Shoppable_Media",
                "asset" : "/content/dam/mac/aodmarketingna/shoppable-banner/shoppable-banner.jpg" }
        })
        /* // Example of interactive image event for Quickview.
             s7interactiveimageviewer.setHandlers({ 
                "quickViewActivate": function(inData) {
                    var sku=inData.sku; //SKU for product ID
                    //To pass other parameter from the hotspot, you will need to add custom parameter during the hotspot setup as parameterName=value
                    loadQuickView(sku); //Replace this call with your Quickview plugin
                    //Please refer to your Quickviewer plugin for the Quickview call
                 }, 
             });
        */
        s7interactiveimageviewer.init();
```

因此，只需取消對代碼的註解，並將虛擬處理程式主體替換為特定網頁特有的代碼。

構建Quickview URL的過程與識別先前覆蓋的熱點變數的過程基本相反。

請參閱[識別熱點變數](#optional-identifying-hotspot-variables)。

使用先前的Quickview URL範例，您可以在下列範例中查看在每個案例中如何建構Quickview URL:

<table> 
 <tbody> 
  <tr> 
   <td><p>在查詢字串中找到的單一SKU</p> </td> 
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/json?productId=" + inData.sku + "&amp;amp;source=100";
      },
      });</code></td> 
  </tr> 
  <tr> 
   <td><p>在URL路徑中找到的單一SKU</p> </td> 
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/product/" + inData.sku;
      },
      });</code></td> 
  </tr> 
  <tr> 
   <td><p>查詢字串中的SKU和類別ID</p> </td> 
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/quickView/product/?category=" + inData.categoryId + "&amp;amp;prodId=" + inData.sku;
      },
      });</code></td> 
  </tr> 
 </tbody> 
</table>

觸發Quickview URL並啟動Quickview面板的最後一個步驟很可能需要IT部門的前端IT人員協助。 他們具備最佳知識，了解如何從正確的步驟準確觸發Quickview實作，並擁有可供使用的Quickview URL。

您可以了解這些步驟如何套用至示範網站，以將可購買的互動式影像與Quickview程式碼完全整合。 之前，Quickview URL的結構識別如下：

```xml
/datafeed/$categoryId$-$SKU$.json
```

若要在`quickViewActivate`處理常式內重新建構此URL，您可以使用`inData`物件中可用的`categoryId`和`SKU`欄位，該物件會由檢視器的程式碼傳遞至處理常式：

```xml
var sku=inData.sku;
var categoryId=inData.categoryId;
var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
```

示範網站正使用簡單的`loadQuickView()`函式呼叫觸發「快速檢視」對話方塊。 此函式只需使用一個引數，即Quickview資料URL。 因此，整合可購買互動式影像的最後一個步驟是將下列程式碼行新增至`quickViewActivate`處理常式：

```xml
loadQuickView(quickViewUrl);
```

以下是完整的原始碼：

```xml
 var s7interactiveimageviewer = new s7viewers.InteractiveImage({
  "containerId" : "s7interactiveimage_div",
  "params" : { 
   "serverurl" : "https://aodmarketingna.assetsadobe.com/is/image",
   "contenturl" : "https://aodmarketingna.assetsadobe.com/", 
   "config" : "/etc/dam/presets/viewer/Shoppable_Media",
   "asset" : "/content/dam/mac/aodmarketingna/shoppable-banner/shoppable-banner.jpg" }
 })
   s7interactiveimageviewer.setHandlers({ 
   "quickViewActivate": function(inData) {
     var sku=inData.sku;
     var categoryId=inData.categoryId;
    var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
    loadQuickView(quickViewUrl);
    }, 
   });
 s7interactiveimageviewer.init();
```

具有完全整合互動式影像的最終示範網站如下所示：

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-3.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-3.html)

## 使用「快速檢視」建立自訂快顯視窗 {#using-quickviews-to-create-custom-pop-ups}

請參閱使用Quickviews](custom-pop-ups.md)建立自訂快顯視窗。[

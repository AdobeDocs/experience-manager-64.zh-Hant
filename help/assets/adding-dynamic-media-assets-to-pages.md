---
title: 將Dynamic Media資產添加到頁面
description: 如何將Dynamic Media元件添加到Adobe Experience Manager的頁面
uuid: 77abcb87-2df7-449b-be52-540d749890b6
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: d1f45751-1761-4d6b-b17d-110b2f1117ea
exl-id: bb97b649-a50d-49c8-97aa-18c32f18d527
feature: Components
role: User
source-git-commit: 50b657456d2a0eaaaf681d3902eba38b15d00e12
workflow-type: tm+mt
source-wordcount: '2809'
ht-degree: 3%

---

# 將Dynamic Media資產添加到頁面 {#adding-dynamic-media-assets-to-pages}

要將動態媒體功能添加到您在網站上使用的資產中，您可以添加 **Dynamic Media** 或 **互動式媒體** 元件。 通過進入佈局模式並啟用動態媒體元件，可以執行此操作。 然後，您可以將這些元件新增至頁面，並新增資產至元件。動態媒體和互動式媒體元件是智慧的 — 它們知道您是添加影像還是添加視頻，可用選項也會相應更改。

如果將動態媒體資產用作WCM，則直接將AEM其添加到頁面。 如果您使用協力廠商來處理WCM，請連結 [或](linking-urls-to-yourwebapplication.md)[內嵌資](embed-code.md) 產。如需多方互動網站，請參閱將最佳化 [的影像傳送至多方互動網站](responsive-site.md)。

>[!NOTE]
>
>必須先發佈資產，然後才能將其添加到中的AEM頁面。 請參閱 [出版Dynamic Media資產](publishing-dynamicmedia-assets.md)。

## 將Dynamic Media元件添加到頁面 {#adding-a-dynamic-media-component-to-a-page}

將Dynamic Media元件添加到頁面與將元件添加到任何頁面相同。 以下各節詳細介紹了Dynamic Media的構成部分。

>[!NOTE]
>
>如果網頁上有一個具有只讀權限的用戶訪問的Dynamic Media元件，則分頁符和元件無法正確呈現。 原因是重構頁面，以確保元件的屬性良好，並且任何引用的資產和配置都可訪問。 然後再次呈現頁面，導致元件中斷；由於用戶的只讀訪問，無法重新呈現頁面上的相應元件代碼。
>  
>為避免此問題，請確保AEM Sites用戶擁有訪問資產的必要權限。

1. 在AEM中，開啟要添加Dynamic Media元件的頁面。
1. 在頁面左側的面板中（您可能需要切換側面板的顯示），按一下 **[!UICONTROL 元件]** 表徵圖
1. 在 **[!UICONTROL 元件]** 標題，在下拉清單中，選擇 **[!UICONTROL Dynamic Media]**。 如果沒有可用的Dynamic Media元件清單，則可能需要啟用要使用的Dynamic Media元件。 請參閱 [啟用Dynamic Media元件](#enabling-dynamic-media-components)。

   ![chlimage_1-537](assets/chlimage_1-537.png)

1. 將要使用的Dynamic Media元件拖到所需位置的頁面上。
1. 將滑鼠指針直接懸停在元件上。 當元件被藍色框包圍時，點擊一次以顯示元件的工具欄。 點擊 **[!UICONTROL 配置]** （扳手）表徵圖。
1. [編輯元件](#dynamic-media-components) 根據需要，按一下複選標籤以保存更改。

### 啟用Dynamic Media元件 {#enabling-dynamic-media-components}

如果沒有可添加到頁面的Dynamic Media元件，可能意味著您需要首先啟用要使用的元件。

1. 在AEM中，開啟要添加Dynamic Media元件的頁面。
1. 在工具欄左側靠近頁面頂部的位置，按一下「Page Information（頁面資訊）」表徵圖，然後按一下 **[!UICONTROL 編輯模板]** 從下拉清單中。

   ![編輯模板](/help/assets/assets-dm/edit-template.png)

1. 在靠近頁面頂部的工具欄右側，從下拉清單中按一下 **[!UICONTROL 結構]**。

   ![政策](/help/assets/assets-dm/structure-mode.png)

1. 在頁面底部附近，點擊 **[!UICONTROL 佈局容器]** 開啟其工具欄，然後按一下「策略」表徵圖。
1. 在 **[!UICONTROL 佈局容器]** 的子菜單。 **[!UICONTROL 屬性]** 航向，確保 **[!UICONTROL 允許的元件]** 的子菜單。

   ![允許的元件](/help/assets/assets-dm/allowed-components.png)

1. 滾動直到您看到 **[!UICONTROL Dynamic Media]**。
1. 按一下左側的>表徵圖 **[!UICONTROL Dynamic Media]** 要展開清單，請選擇要啟用的Dynamic Media元件。

   ![Dynamic Media元件清單](/help/assets/assets-dm/dm-components-select.png)

1. 靠近 **[!UICONTROL 佈局容器]** 的子菜單。

1. 在靠近頁面頂部的工具欄右側，從下拉清單中按一下 **[!UICONTROL 初始內容]**，則 [將Dynamic Media元件添加到頁面](#adding-a-dynamic-media-component-to-a-page) 像往常一樣。

## 本地化Dynamic Media元件 {#localizing-dynamic-media-components}

您可以通過以下兩種方式之一來本地化Dynamic Media元件：

* 在「網站」的網頁中，開啟「屬 **[!UICONTROL 性]** 」並選 **[!UICONTROL 取「進階]** 」標籤。選擇所要的本地化語言。

   ![chlimage_1-538](assets/chlimage_1-538.png)

* 從站點選擇器中，選擇所需的頁或頁組。 點擊 **[!UICONTROL 屬性]** 的 **[!UICONTROL 高級]** 頁籤。 選擇所要的本地化語言。

   >[!NOTE]
   >
   >請注意，並非所有語言都可在 **[!UICONTROL 語言]** 當前已分配令牌。

## Dynamic Media元件 {#dynamic-media-components}

Dynamic Media和互動媒體可在 [!UICONTROL Dynamic Media] 頁籤 [!UICONTROL 元件]。 使用 [!UICONTROL 互動式媒體] 用於任何互動式資產（如互動式視頻、互動式影像或旋轉盤集）的元件。 對於所有其它動態介質元件，使用Dynamic Media元件。

>[!NOTE]
>
>預設情況下，這些元件不可用，在使用之前需要通過模板編輯器使用。 [在它們可用後](/help/sites-authoring/templates.md#editing-templates-template-authors) 在模板編輯器中，可以像添加任何其他元件一樣將元件添加AEM到頁面。

![chlimage_1-539](assets/chlimage_1-539.png)

### Dynamic Media分量 {#dynamic-media-component}

Dynamic Media元件是智慧的 — 根據您是添加影像還是添加視頻，您有各種選項。 該元件支援影像預設、基於影像的查看器，如影像集、旋轉集、混合媒體集和視頻。 此外，觀看者是響應的。 即，螢幕大小根據螢幕大小自動更改。 所有觀眾都是HTML五觀眾。

>[!NOTE]
>
>如果在具有只讀權限的用戶訪問的網頁上存在Dynamic Media元件、交互媒體元件或兩者，則分頁符和元件將無法正確呈現。 原因是重構頁面，以確保元件的屬性良好，並且任何引用的資產和配置都可訪問。 然後再次呈現頁面，導致元件中斷；由於用戶的只讀訪問，無法重新呈現頁面上的相應元件代碼。
>  
>為避免此問題，請確保AEM Sites用戶擁有訪問資產的必要權限。

>[!NOTE]
>
>添加Dynamic Media元件時 **[!UICONTROL Dynamic Media設定]** 為空或無法正確添加資產，請檢查以下內容：
>
>* 您 [啟用Dynamic Media](config-dynamic.md)。 Dynamic Media預設為禁用。
>* 影像具有金字塔型tiff檔案。 在啟用動態媒體之前導入的影像沒有金字塔型tiff檔案。

>


#### 使用影像時 {#when-working-with-images}

Dynamic Media元件允許您添加動態映像，包括映像集、旋轉集和混合媒體集。 您可以放大、縮小，如果適用，可以在旋轉集內旋轉影像或從另一類型的集合中選擇影像。

您也可以直接在元件中配置查看器預設、影像預設或影像格式。 要使影像響應，可以設定斷點或應用響應影像預設。

必須通過按一下 **[!UICONTROL 編輯]** 表徵圖 **[!UICONTROL Dynamic Media設定]**。

![dm-settings-image預設](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>依預設，動態媒體影像元件是可調式的。如果要將其設定為固定大小，請在 **[!UICONTROL 高級]** 頁籤 **[!UICONTROL 寬度]** 和 **[!UICONTROL 高度]** 的子菜單。

* **[!UICONTROL 查看器預設]**
從下拉菜單中選擇現有查看器預設。 如果您要查找的查看器預設不可見，則可能需要使其可見。 請參閱管理查看器預設。 如果使用影像預設，則不能選擇查看器預設，反之亦然。
如果查看影像集、旋轉集或混合媒體集，則此選項是唯一可用的選項。 顯示的查看器預設也是智慧的 — 只顯示相關的查看器預設。

* **[!UICONTROL 查看器修飾符]**
查看器修飾符採用帶有&amp;分隔符的name=value對的形式，並允許您更改查看器，如查看器參考指南中所述。 查看器修飾符的示例是後驗影像=img.jpg&amp;caption=text.vtt,1，它為視頻縮略圖設定不同的影像並將隱藏的字幕/字幕檔案與視頻相關聯。

* **[!UICONTROL 影像預設]**
從下拉菜單中選擇現有影像預設。 如果您要查找的影像預設不可見，則可能需要使其可見。 請參閱管理影像預設。 如果使用影像預設，則不能選擇查看器預設，反之亦然。
如果您正在查看映像集、旋轉集或混合媒體集，則此選項不可用。

* **[!UICONTROL 影像修飾符]**
可以通過提供附加影像命令來應用影像效果。 這些內容在「影像預設」和「影像服務命令」參考中介紹。
如果您正在查看映像集、旋轉集或混合媒體集，則此選項不可用。

* **[!UICONTROL 斷點]**
如果在響應站點上使用此資產，則需要添加影像斷點。 影像斷點需要用逗號(,)分隔。 當影像預設中沒有定義高度或寬度時，此選項有效。
如果您正在查看映像集、旋轉集或混合媒體集，則此選項不可用。
通過按一下 **[!UICONTROL 編輯]** 的子菜單。

* **[!UICONTROL 標題]**
更改影像的標題。

* **[!UICONTROL 替代文字]**
為已關閉圖形的用戶添加影像標題。
如果您正在查看映像集、旋轉集或混合媒體集，則此選項不可用。

* **[!UICONTROL URL，在中開啟]**
您可以設定資產以開啟連結。 設定URL，在「開啟」(Open)中，指明希望在同一窗口或新窗口中開啟它。
如果您正在查看映像集、旋轉集或混合媒體集，則此選項不可用。

* **[!UICONTROL 寬度]** 和 **[!UICONTROL 高度]**
如果希望影像為固定大小，請以像素為單位輸入值。 將這些值留空可使資產具有自適應性。

#### 使用視頻時 {#when-working-with-video}

使用Dynamic Media元件將動態視頻添加到網頁。 編輯元件時，您可以選擇使用預定義的視頻查看器預設在頁面上播放視頻。

![chlimage_1-540](assets/chlimage_1-540.png)

必須通過按一下以下Dynamic Media設定來編輯 **[!UICONTROL 編輯]** 的子菜單。

>[!NOTE]
>
>預設情況下，Dynamic Media視頻元件是自適應的。 如果要將其設定為固定大小，請在元件中 **[!UICONTROL 寬度]** 和 **[!UICONTROL 高度]** 的 [!UICONTROL 高級] 頁籤。

* **[!UICONTROL 查看器預設]**
從下拉菜單中選擇現有視頻查看器預設。 如果您要查找的查看器預設不可見，則可能需要使其可見。 請參閱管理查看器預設。

* **[!UICONTROL 查看器修飾符]**
查看器修飾符採用帶有&amp;分隔符的name=value對的形式，並允許您更改查看器，如《Adobe查看器參考指南》中所述。 查看器修飾符的示例是後驗影像=img.jpg&amp;caption=text.vtt,1

   例如，使用查看器修飾符，可以執行以下操作：

   * 將字幕檔案與視頻關聯 [標題。](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html)
   * 將導航檔案與視頻關聯 [的下界。](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html)

可以編輯以下內容 [!UICONTROL 高級設定] 按一下 **[!UICONTROL 編輯]** 的子菜單。

* **[!UICONTROL 標題]**
更改視頻的標題。

* **[!UICONTROL 寬度]** 和 **[!UICONTROL 高度]**
如果希望視頻大小固定，請輸入以像素為單位的值。 將這些值留空可使其適應。

#### 使用Smart Crop時 {#when-working-with-smart-crop}

使用Dynamic Media元件將Smart Crop映像資產添加到網頁。 編輯元件時，您可以選擇使用預定義的視頻查看器預設在頁面上播放視頻。

另請參閱 [影像配置檔案](image-profiles.md)。

![dm-settings-smart-crop](assets/dm-settings-smart-crop.png)

可以編輯以下內容 [!UICONTROL Dynamic Media設定] 按一下 **[!UICONTROL 編輯]** 的子菜單。

>[!NOTE]
>
>依預設，動態媒體影像元件是可調式的。如果要使其成為固定大小，請在「高級」( [!UICONTROL Advanced] )頁籤的元件中使用「寬度」( **[!UICONTROL Width)和「高度」(Height]** )設定它 ****。

* **[!UICONTROL 影像修飾符]**
可以通過提供附加影像命令來應用影像效果。 這些內容在「影像預設」和「影像服務命令」參考中介紹。
如果您正在查看映像集、旋轉集或混合媒體集，則此選項不可用。

可以編輯以下內容 **[!UICONTROL 高級]** 按一下 **[!UICONTROL 編輯]** 的子菜單。

* **[!UICONTROL 標題]**
更改Smart Crop影像的標題。

* **[!UICONTROL 替代文字]**
為關閉圖形的用戶添加智慧裁剪影像的標題。
如果您正在查看映像集、旋轉集或混合媒體集，則此選項不可用。

* **[!UICONTROL URL，在中開啟]**
您可以設定資產以開啟連結。 設定URL，在「開啟」(Open)中，指明希望在同一窗口或新窗口中開啟它。
如果您正在查看映像集、旋轉集或混合媒體集，則此選項不可用。

* **[!UICONTROL 高度]** 和 **[!UICONTROL 寬度]**
如果希望智慧裁剪影像具有固定大小，請以像素為單位輸入值。 將這些值留空可使其適應。

### 互動式媒體元件 {#interactive-media-component}

互動式媒體元件用於那些具有交互性的資產，例如熱點或影像映射。 如果您有互動式影像、互動式視頻或旋轉播放橫幅，請使用互動式媒體元件。

互動式媒體元件是智慧的 — 根據您是添加影像還是添加視頻，您有各種選項。 此外，查看器會響應 — 螢幕大小會根據螢幕大小自動改變。 所有觀眾都是HTML五觀眾。

>[!NOTE]
>
>如果在具有只讀權限的用戶訪問的網頁上存在Dynamic Media元件、交互媒體元件或兩者，則分頁符和元件將無法正確呈現。 原因是重構頁面，以確保元件的屬性良好，並且任何引用的資產和配置都可訪問。 然後再次呈現頁面，導致元件中斷；由於用戶的只讀訪問，無法重新呈現頁面上的相應元件代碼。
> 
>為避免此問題，請確保AEM Sites用戶擁有訪問資產的必要權限。

![chlimage_1-541](assets/chlimage_1-541.png)

可以編輯以下內容 **[!UICONTROL 常規]** 按一下 **[!UICONTROL 編輯]** 的子菜單。

* **[!UICONTROL 查看器預設]**
從下拉菜單中選擇現有查看器預設。 如果您要查找的查看器預設不可見，則可能需要使其可見。 必須先發佈查看器預設，然後才能使用它們。 請參閱管理查看器預設。

* **[!UICONTROL 標題]**
更改視頻的標題。

* **[!UICONTROL 寬度]** 和 **[!UICONTROL 高度]**
如果希望視頻大小固定，請輸入以像素為單位的值。 將這些值留空可使其適應。

可以編輯以下內容 **[!UICONTROL 添加到購物車]** 按一下 **[!UICONTROL 編輯]** 的子菜單。

* **[!UICONTROL 顯示產品資產]**
預設情況下，此值處於選中狀態。 產品資產顯示在「商務」模組中定義的產品影像。 清除複選標籤以不顯示產品資產。

* **[!UICONTROL 顯示產品價格]**
預設情況下，此值處於選中狀態。 產品價格顯示在「商務」模組中定義的物料價格。 清除複選標籤以不顯示產品價格。

* **[!UICONTROL 顯示產品窗體]**
預設情況下，未選擇此值。 「產品表單」包括任何產品變型，如尺寸和顏色。 清除複選標籤以不顯示產品變型。

### 全景媒體元件 {#panoramic-media-component}

全景媒體元件用於那些球面全景影像的資產。 這些影像提供房間、房產、位置或景觀的360°觀看體驗。 要使影像符合為球形全景圖，它必須具有以下一個或兩個：

* 寬高比為2:1。
* 標籤有關鍵字「等長方形」或(「spherical」+「panorama」)或(「spherical」+「panoramic」)。 請參閱 [使用標籤](/help/sites-authoring/tags.md)。

縱橫比和關鍵字條件都適用於資產詳細資訊頁面和「全景媒體」 WCM元件的全景資產。

![全景媒體觀看器預設](assets/panoramic-media-viewer-preset.png)

可通過點擊來編輯以下設定 **[!UICONTROL 配置]** 的子菜單。

* **[!UICONTROL 查看器預設]**
從「查看器」預設下拉菜單中選擇現有查看器。

如果您要查找的查看器預設不可見，請檢查以確保已發佈。 必須先發佈查看器預設，然後才能使用它們。 請參閱 [管理查看器預設](managing-viewer-presets.md)。

### 使用HTTP/2交付Dynamic Media資產 {#using-http-to-delivery-dynamic-media-assets}

HTTP/2是新的、更新的Web協定，它改進了瀏覽器和伺服器的通信方式。 它提供了更快的資訊傳輸，並減少了所需的處理能力。 Dynamic Media資產的交付現在可以通過HTTP/2，從而提供更好的響應和載入時間。

請參閱 [HTTP2內容傳遞](http2.md) 有關使用HTTP/2和您的Dynamic Media帳戶入門的完整詳細資訊。

>[!MORELIKETHIS]
>
>* [理解色彩管AEM理Dynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-color-management-technical-video-setup.html)
>* [將自定義視頻縮略圖與AEMDynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-thumbnails-feature-video-use.html)
>* [瞭解資產查看器與AEMDynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-viewer-feature-video-understand.html)
>* [將互動式視頻與AEMDynamic Media](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-interactive-video-feature-video-use.html)
>* [在Dynamic Media使用視頻播AEM放器](https://helpx.adobe.com/experience-manager/kt/assets/using/dynamic-media-video-player-feature-video-use.html)
>* [使用影像銳化與AEMDynamic Media](https://helpx.adobe.com/experience-manager/6-4/assets/using/best-practices-for-optimizing-the-quality-of-your-images.html)


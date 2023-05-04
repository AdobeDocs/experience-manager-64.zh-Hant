---
title: 將Dynamic Media Classic元件新增至頁面
description: 如何將Dynamic Media Classic功能和元件新增至Adobe Experience Manager中的頁面。
contentOwner: Alva Ware-Bevacqui
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
topic-tags: managing-assets
exl-id: b11b19c1-712d-4698-aefc-930ff8cacbc1
feature: Dynamic Media Classic
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2860'
ht-degree: 1%

---

# 將Dynamic Media Classic元件新增至頁面 {#adding-scene-features-to-your-page}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Adobe Dynamic Media Classic是托管解決方案，可管理、增強、發佈和傳遞多媒體資產至網路、行動裝置、電子郵件及網際網路連線的顯示器及列印。

您可以在各種檢視器中檢視發佈於Dynamic Media Classic的AEM資產：

* 縮放
* 飛出
* 影片
* 影像範本
* 影像

您可以直接從AEM發佈數位資產至Dynamic Media Classic，也可以從Dynamic Media Classic發佈數位資產至AEM。

本檔案說明如何將數位資產從AEM發佈至Dynamic Media Classic，反之亦然。 檢視器也會詳細說明。 如需為Dynamic Media Classic設定AEM的詳細資訊，請參閱 [整合Dynamic Media Classic與AEM](/help/sites-administering/scene7.md).

另請參閱 [新增影像地圖](image-maps.md).

如需如何將視訊元件與AEM搭配使用的詳細資訊，請參閱 [影片](video.md).

>[!NOTE]
>
>如果Dynamic Media Classic資產未正確顯示，請確定Dynamic Media為 [停用](config-dynamic.md#disabling-dynamic-media) 然後重新整理頁面。

## 從資產手動發佈至Dynamic Media Classic {#manually-publishing-to-scene-from-assets}

您可以依照下列方式將數位資產發佈至Dynamic Media Classic:

* [在Assets控制台的傳統使用者介面中](/help/sites-classic-ui-authoring/manage-assets-classic-s7.md#publishing-from-the-assets-console)
* [在資產的傳統使用者介面中](/help/sites-classic-ui-authoring/manage-assets-classic-s7.md#publishing-from-an-asset)
* [在傳統使用者介面中，從CQ Target資料夾外部](/help/sites-classic-ui-authoring/manage-assets-classic-s7.md#publishing-assets-from-outside-the-cq-target-folder)

>[!NOTE]
>
>AEM會非同步發佈至Dynamic Media Classic。 按一下 **[!UICONTROL 發佈]**，您的資產可能需要數秒的時間才能發佈至Dynamic Media Classic。

## Dynamic Media Classic元件 {#scene-components}

AEM提供下列Dynamic Media Classic元件：

* 縮放
* 彈出（縮放）
* 影像範本
* 影像
* 影片

>[!NOTE]
>
>預設不提供這些元件，因此需在 **[!UICONTROL 設計]** 模式。

在 **[!UICONTROL 設計]** 模式中，您可以像其他AEM元件一樣將元件新增至頁面。 如果是在同步的資料夾、頁面或使用Dynamic Media Classic雲端設定，則尚未發佈至Dynamic Media Classic的資產會發佈至Dynamic Media Classic。

>[!NOTE]
>
>如果您要建立和開發自訂檢視器，以及使用「內容尋找器」，您需要明確新增 **[!UICONTROL 允許全螢幕]** 參數。

### Flash 檢視器生命週期結束注意事項 {#flash-viewers-end-of-life-notice}

自2017年1月31日起，Adobe Dynamic Media Classic停止支援Flash檢視器平台。

### 新增Dynamic Media Classic元件(Scene7)至頁面 {#adding-a-scene-component-to-a-page}

將Dynamic Media Classic(Scene7)元件新增至頁面，與將元件新增至任何頁面相同。 Dynamic Media Classic元件在以下章節中有詳細說明。

**新增Dynamic Media Classic(Scene7)元件至頁面的方式**:

1. 在AEM中，開啟您要新增Dynamic Media Classic(Scene7)元件的頁面。

1. 如果沒有可用的Dynamic Media Classic元件，請按一下 **[!UICONTROL 設計]** 模式，點選任何具有藍色邊框的元件，點選 **[!UICONTROL 父級]** 表徵圖，然後 **[!UICONTROL 設定]** 表徵圖。 在 **[!UICONTROL Parsys（設計）]**，請選取所有Dynamic Media Classic元件以讓它們可用，然後按一下 **[!UICONTROL 確定]**.

   ![chlimage_1-224](assets/chlimage_1-224.png)

1. 按一下 **[!UICONTROL 編輯]** 返回 **[!UICONTROL 編輯]** 模式。

1. 將sidekick中Dynamic Media Classic群組的元件拖曳至所需位置的頁面。

1. 按一下 **[!UICONTROL 設定]** 圖示以開啟元件。

1. 視需要編輯元件，然後按一下 **[!UICONTROL 確定]** 以儲存變更。
1. 從內容瀏覽器將您的影像或影片拖曳至您新增至頁面的Dynamic Media Classic元件。

   >[!NOTE]
   >
   >僅限觸控式UI中，您必須將影像或視訊拖放至您放置在頁面上的Dynamic Media Classic元件。 不支援選取及編輯Dynamic Media Classic元件，然後選取資產。

### 將互動式檢視體驗新增至回應式網站 {#adding-interactive-viewing-experiences-to-a-responsive-website}

針對資產進行回應式設計，表示資產會根據其顯示位置進行適應。 透過回應式設計，可在多部裝置上有效顯示相同的資產。

另請參閱 [網頁的回應式設計](/help/sites-developing/responsive.md).

**若要將互動式檢視體驗新增至回應式網站**:

1. 登入AEM，並確認您 [已設定Adobe Dynamic Media ClassicCloud Services](/help/sites-administering/scene7.md#configuring-scene-integration) 以及Dynamic Media Classic元件可供使用。

   >[!NOTE]
   >
   >如果Dynamic Media Classic元件無法使用，請確定 [以透過設計模式啟用](/help/sites-authoring/default-components-designmode.md).

1. 在具有 **[!UICONTROL Dynamic Media Classic]** 元件已啟用，請拖曳 **[!UICONTROL 影像]** 元件。
1. 選取元件，然後點選設定圖示。
1. 在 **[!UICONTROL Dynamic Media Classic設定]** 頁簽，調整斷點。

   ![chlimage_1-225](assets/chlimage_1-225.png)

1. 確認檢視器正在回應性地調整大小，且所有互動都已針對桌上型電腦、平板電腦和行動裝置最佳化。

### 所有Dynamic Media Classic元件的共同設定 {#settings-common-to-all-scene-components}

雖然設定選項不同，但以下是所有人的共同點 [!UICONTROL Dynamic Media Classic] 元件：

* **[!UICONTROL 檔案參考]**
瀏覽到要引用的檔案。 檔案參考會顯示資產URL，而非完整的Dynamic Media Classic URL，包括URL命令和參數。 您無法在此欄位中新增Dynamic Media Classic URL命令和參數。 必須透過元件中的對應功能來新增。
* **[!UICONTROL 寬度]**
可讓您設定寬度。
* **[!UICONTROL 高度]**
可讓您設定高度。

您可以開啟（按兩下）Dynamic Media Classic元件來設定這些設定選項，例如當您開啟 **[!UICONTROL 縮放]** 元件：

![chlimage_1-226](assets/chlimage_1-226.png)

### 縮放 {#zoom}

當您按下「HTML5縮放」元件時，「縮放」元件會顯示較大的影像 **[!UICONTROL +]** 按鈕。

資產底部有縮放工具。 點選 **[!UICONTROL +]** 放大。 點選 **[!UICONTROL -]** 減少。 點選 **[!UICONTROL x]** 或者，重置縮放箭頭將影像恢復為導入時的原始大小。 點選對角線箭頭，使其成為全螢幕。 點選 **[!UICONTROL 編輯]** 以設定元件。 使用此元件，您可以設定 [所有共用設定 [!UICONTROL Dynamic Media Classic] 元件](#settings-common-to-all-scene-components).

![chlimage_1-227](assets/chlimage_1-227.png)

### 飛出 {#flyout}

在HTML5 **[!UICONTROL 飛出]** 元件，資產會顯示為分割畫面；將資產保留在指定大小；顯示縮放部分的右側。 點選 **[!UICONTROL 編輯]** 以設定元件。 使用此元件，您可以設定 [所有Dynamic Media Classic元件的共同設定](#settings-common-to-all-scene-components).

>[!NOTE]
>
>若您的 **[!UICONTROL 飛出]** 元件會使用自訂大小，然後使用自訂大小，並停用元件的回應式設定。
>
>若您的 **[!UICONTROL 飛出]** 元件使用預設大小，如 **[!UICONTROL 設計檢視]**，則會使用預設大小，而元件會延伸以容納頁面配置大小，並啟用元件的回應式設定。 但請注意，元件的回應式設定有其限制。 若您使用 **[!UICONTROL 飛出]** 元件搭配回應式設定時，不應將其用於完整頁面延伸。 否則， **[!UICONTROL 飛出]** 可能超出頁面的右邊框。

![chlimage_1-228](assets/chlimage_1-228.png)

### 影像 {#image}

Dynamic Media Classic **[!UICONTROL 影像]** 元件可讓您將Dynamic Media Classic功能新增至影像，例如Dynamic Media Classic修飾元、影像或檢視器預設集，以及銳利化。 Dynamic Media Classic **[!UICONTROL 影像]** 元件類似於AEM中具有特殊Dynamic Media Classic功能的其他影像元件。 在此範例中，影像具有Dynamic Media Classic URL修飾元， **&amp;op_invert=1** 已套用。

![chlimage_1-229](assets/chlimage_1-229.png)

* **[!UICONTROL 標題、替代文字]**
在 **[!UICONTROL 進階]** 頁簽，為影像添加標題，並為那些已關閉圖形的用戶添加alt文本。

* **[!UICONTROL URL，在中開啟]**
您可以從設定資產以開啟連結。 設定 **[!UICONTROL URL]** 和 **[!UICONTROL 在中開啟]** 指定要在同一窗口中開啟還是在新窗口中開啟。

![chlimage_1-230](assets/chlimage_1-230.png)

* **[!UICONTROL 檢視器預設集]**
從下拉式選單中選取現有的檢視器預設集。 如果您要尋找的檢視器預設集未顯示，您可能需要將其顯示。 請參閱 [管理檢視器預設集](/help/assets/managing-viewer-presets.md). 如果您使用影像預設集，則無法選取檢視器預設集，反之亦然。

* **[!UICONTROL Dynamic Media Classic設定]**
選取您要用來從SPS擷取作用中影像預設集的Dynamic Media Classic設定。

* **[!UICONTROL 影像預設集]**
從下拉式選單中選取現有的影像預設集。 如果您要尋找的影像預設集未顯示，則您可能需要使其可見。 請參閱 [管理影像預設集](/help/assets/managing-image-presets.md). 如果您使用影像預設集，則無法選取檢視器預設集，反之亦然。

* **[!UICONTROL 輸出格式]**
選擇影像的輸出格式，例如jpeg。 視您選取的輸出格式而定，您可能有其他設定選項。 請參閱 [影像預設集最佳作法](/help/assets/managing-image-presets.md#image-preset-options).

* **[!UICONTROL 銳利化]**
選擇要如何銳化影像。 銳利化詳細說明於 [影像預設集最佳作法](/help/assets/managing-image-presets.md#image-preset-options) 和 [銳利化最佳實務](/help/assets/assets/sharpening_images.pdf).

* **[!UICONTROL URL修飾元]**
您可以提供其他Dynamic Media Classic影像命令來變更影像效果。 這些說明於 [影像預設集](/help/assets/managing-image-presets.md) 和 [命令參考](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html).

* **[!UICONTROL 斷點]**
如果網站回應式，您要調整斷點。 斷點必須以逗號(,)分隔。

### 影像範本 {#image-template}

[Dynamic Media Classic影像範本](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/template-basics/creating-template.html#creating-the-initial-template) 是已匯入至Dynamic Media Classic的分層Photoshop內容，其中內容和屬性已參數化，因而可變。 此 **[!UICONTROL 影像範本]** 元件可讓您在AEM中動態匯入影像和變更文字。 此外，您可以設定 **[!UICONTROL 影像範本]** 元件來使用用戶端內容的值，讓每個使用者以個人化的方式體驗影像。

點選 **[!UICONTROL 編輯]** 以設定元件。 您可以設定 [所有Dynamic Media Classic元件的共同設定](#settings-common-to-all-scene-components) 以及本節所述的其他設定。

![chlimage_1-231](assets/chlimage_1-231.png)

* **[!UICONTROL 檔案參考、寬度、高度]**
請參閱所有Dynamic Media Classic元件的共同設定。

   >[!NOTE]
   >
   >Dynamic Media Classic URL命令和參數無法直接新增至檔案參考URL。 它們只能在 **[!UICONTROL 參數]** 中。

* **[!UICONTROL 標題、替代文字]**
在「Dynamic Media Classic影像範本」索引標籤中，為影像新增標題，並為已關閉圖形的使用者新增替代文字。

* **[!UICONTROL URL，在中開啟]**
您可以從設定資產以開啟連結。 設定URL，然後在「開啟」中（在中）指出您要在相同視窗還是新視窗中開啟它。

![chlimage_1-232](assets/chlimage_1-232.png)

* **[!UICONTROL 參數面板]**
匯入影像時，參數會預先填入影像的資訊。 如果沒有可動態變更的內容，此視窗為空。

![chlimage_1-233](assets/chlimage_1-233.png)

#### 動態變更文字 {#changing-text-dynamically}

若要動態變更文字，請在欄位中輸入新文字，然後按一下 **[!UICONTROL 確定]**. 在此範例中， **[!UICONTROL 價格]** 現在是50美元，運費是99美分。

![chlimage_1-234](assets/chlimage_1-234.png)

影像中的文字會變更。 您可以點選，將文字重設回原始值 **[!UICONTROL 重設]** 欄位旁邊。

![chlimage_1-235](assets/chlimage_1-235.png)

#### 更改文本以反映客戶端上下文值的值 {#changing-text-to-reflect-the-value-of-a-client-context-value}

若要將欄位連結至用戶端內容值，請點選 **[!UICONTROL 選擇]** 若要開啟「用戶端內容」功能表，請選取「用戶端內容」，然後點選 **[!UICONTROL 確定]**. 在此示例中，名稱會根據將名稱與配置檔案中的格式化名稱連結而改變。

![chlimage_1-236](assets/chlimage_1-236.png)

文字會反映目前登入使用者的名稱。 您可以按一下「 」，將文字重設回原始值 **[!UICONTROL 重設]** 欄位旁邊。

![chlimage_1-237](assets/chlimage_1-237.png)

#### 讓Dynamic Media Classic影像範本成為連結 {#making-the-scene-image-template-a-link}

1. 在與Dynamic Media Classic **[!UICONTROL 影像範本]** 元件，點選 **[!UICONTROL 編輯]**.
1. 在 **[!UICONTROL URL]** 欄位中，輸入點選影像時使用者前往的URL。 在 **[!UICONTROL 在中開啟]** 欄位中，選擇是要開啟目標（新窗口還是同一窗口）。

   ![chlimage_1-238](assets/chlimage_1-238.png)

1. 點選 **[!UICONTROL 確定]**.

### 視訊元件 {#video-component}

Dynamic Media Classic **[!UICONTROL 影片]** 元件(可從sidekick的Dynamic Media Classic區段取得)使用裝置和頻寬偵測，將適當的視訊提供給每個畫面。 此元件為HTML5視訊播放器；是可跨頻道使用的單一檢視器。

它可用於最適化視訊集、單一MP4視訊或單一F4V視訊。

請參閱 [影片](s7-video.md) 以取得有關視訊如何與Dynamic Media Classic整合搭配運作的詳細資訊。 此外，請參閱 [Dynamic Media Classic視訊元件與Foundation視訊元件](s7-video.md).

![chlimage_1-239](assets/chlimage_1-239.png)

### 視訊元件的已知限制 {#known-limitations-for-the-video-component}

AdobeDAM和WCM會顯示主視訊是否已上傳。 它們不會顯示這些代理資產：

* Dynamic Media Classic編碼轉譯
* Dynamic Media Classic最適化視訊集

搭配Dynamic Media Classic視訊元件使用最適化視訊集時，您需要調整元件大小以符合視訊的尺寸。

## Dynamic Media Classic內容瀏覽器 {#scene-content-browser}

Dynamic Media Classic內容瀏覽器可讓您直接在AEM中檢視Dynamic Media Classic的內容。 若要存取內容瀏覽器，請在 **[!UICONTROL 內容尋找器]**，選取 **[!UICONTROL Dynamic Media Classic]** 在觸控最佳化的使用者介面或 **[!UICONTROL S7]** 圖示。 這兩個使用者介面的功能完全相同。

如果您有多個設定，依預設AEM會顯示 [預設配置](/help/sites-administering/scene7.md#configuring-a-default-configuration). 您可以直接在下拉式功能表的Dynamic Media Classic內容瀏覽器中選取不同的設定。

>[!NOTE]
>
>* 位於臨機資料夾中的資產不會顯示在Dynamic Media Classic內容瀏覽器中。
>* 當 [安全預覽已啟用](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene),Dynamic Media Classic上已發佈和未發佈的資產都會顯示在Dynamic Media Classic內容瀏覽器中。
>* 如果您沒有看到 **[!UICONTROL Dynamic Media Classic]** 或 **[!UICONTROL S7]** 圖示作為內容瀏覽器中的選項，您需要 [設定Dynamic Media Classic以搭配AEM使用](/help/sites-administering/scene7.md).
>* 若是影片，Dynamic Media Classic內容瀏覽器支援：
   >   * 最適化視訊集：容器，以便在多個畫面間順暢播放所需的所有視訊轉譯
   >   * 單MP4視頻
   >   * 單一F4V影片


### 在觸控最佳化UI中瀏覽內容 {#browsing-content-in-the-touch-optimized-ui}

您可以在觸控最佳化或傳統UI中存取內容瀏覽器。 目前觸控最佳化有下列限制：

* 不支援來自Dynamic Media Classic的FXG和Flash資產。

透過選取 **[!UICONTROL Dynamic Media Classic]** 從第三個下拉式功能表。 如果您尚未設定Dynamic Media Classic/AEM整合，則清單中不會顯示Dynamic Media Classic。

>[!NOTE]
>
>* Dynamic Media Classic內容瀏覽器會載入約100個資產，並依名稱排序。
>* 如果您已設定安全預覽伺服器，瀏覽器將使用該預覽伺服器來呈現縮圖和資產。
>


![chlimage_1-240](assets/chlimage_1-240.png)

此外，您可以將游標暫留在瀏覽器中的資產上，以瀏覽解析度資訊、大小、修改後間隔天數和檔案名稱。

![chlimage_1-241](assets/chlimage_1-241.png)

* 對於適用性視訊集和範本，不會產生縮圖的大小資訊。
* 針對適用性視訊集，不會產生縮圖的解析度。

### 使用內容瀏覽器搜尋Dynamic Media Classic資產 {#searching-for-scene-assets-with-the-content-browser}

搜尋Dynamic Media Classic資產與搜尋AEM資產類似，只是搜尋時，您實際上看到的是Dynamic Media Classic系統中資產的遠端檢視，而非直接匯入AEM。

您可以使用傳統UI或觸控最佳化UI來檢視和搜尋資產。 根據介面，您的搜尋方式會稍有不同。

在任一UI中搜尋時，您可以依下列條件進行篩選（如觸控最佳化UI中的此處所示）:

* **[!UICONTROL 輸入關鍵字]**
您可以依名稱搜尋資產。 搜尋所輸入的關鍵字時，檔案名稱的開頭為。 例如，輸入&quot;swimming&quot;會尋找任何以該順序字母開頭的資產檔案名稱。 輸入詞語以尋找資產後，請務必點選「enter」。

![chlimage_1-242](assets/chlimage_1-242.png)

* **[!UICONTROL 資料夾/路徑]**
顯示的資料夾名稱取決於您選取的配置。 您可以點選資料夾圖示並選取子資料夾，然後點選核取標籤以選取，以深入鑽研至較低層級。

如果您輸入關鍵字並選取資料夾，AEM會搜尋該資料夾和任何子資料夾。 不過，如果您在搜尋時未輸入任何關鍵字，選取資料夾只會顯示該資料夾中的資產，且不會包含任何子資料夾。

依預設，AEM會搜尋選取的資料夾和所有子資料夾。

![chlimage_1-243](assets/chlimage_1-243.png)

* **[!UICONTROL 資產類型]**
選擇 **[!UICONTROL Dynamic Media Classic]** 瀏覽Dynamic Media Classic內容。 只有已設定Dynamic Media Classic時，才可使用此選項。

![chlimage_1-244](assets/chlimage_1-244.png)

* **[!UICONTROL 設定]**
如果您在中定義了多個Dynamic Media Classic設定 [!UICONTROL Cloud Services]，您可以在此處選取。 因此，資料夾會根據您選擇的設定而變更。

![chlimage_1-245](assets/chlimage_1-245.png)

* **[!UICONTROL 資產類型]**
在Dynamic Media Classic瀏覽器中，您可以篩選結果以包含下列任一項目：影像、範本、影片和最適化影片集。 如果您未選取任何資產類型，依預設AEM會搜尋所有資產類型。

![chlimage_1-246](assets/chlimage_1-246.png)

>[!NOTE]
>
>* 在傳統UI中，您也可以搜尋 **Flash** 和 **FXG**. 目前不支援在觸控最佳化UI中篩選這些項目。
>
>* 搜尋視訊時，會搜尋單一轉譯。 結果返回原始格式副本（僅&amp;ast;.mp4）和編碼格式副本。
>* 搜尋最適化視訊集時，您會搜尋資料夾和所有子資料夾，但僅限於已新增關鍵字至搜尋時。 如果您尚未新增關鍵字，AEM不會搜尋子資料夾。
>


* **[!UICONTROL 發佈狀態]**
您可以根據發佈狀態篩選資產： **[!UICONTROL 未發佈]** 或 **[!UICONTROL 已發佈]**. 如果您未選取任何 **[!UICONTROL 發佈狀態]**, AEM依預設會搜尋所有發佈狀態。

![chlimage_1-247](assets/chlimage_1-247.png)

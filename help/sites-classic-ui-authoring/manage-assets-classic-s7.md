---
title: 將Dynamic Media Classic功能新增至您的頁面
seo-title: 將Dynamic Media Classic功能新增至您的頁面
description: AdobeDynamic Media Classic是托管解決方案，可管理、增強、發佈及將多媒體資產傳送至網路、行動裝置、電子郵件及與網際網路連線的顯示器及列印。
seo-description: AdobeDynamic Media Classic是托管解決方案，可管理、增強、發佈及將多媒體資產傳送至網路、行動裝置、電子郵件及與網際網路連線的顯示器及列印。
uuid: 66b9c150-c482-4a41-9772-fa39c135802c
contentOwner: Alva Ware-Bevacqui
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 9ba95dce-a801-4a36-8798-45d295371b1b
exl-id: 93921d23-a2bf-43b6-b002-58a7482b22b0
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '3381'
ht-degree: 0%

---

# 將Dynamic Media Classic功能新增至您的頁面{#adding-scene-features-to-your-page}

AdobeDynamic Media Classic是托管解決方案，可管理、增強、發佈及將多媒體資產傳送至網路、行動裝置、電子郵件及與網際網路連線的顯示器及列印。

您可以在各種檢視器中檢視在Dynamic Media Classic中發佈的AEM資產：

* 縮放
* 飛出
* 影片
* 影像範本
* 影像

您可以直接從AEM發佈數位資產至Dynamic Media Classic，也可以從Dynamic Media Classic發佈數位資產至AEM。

本節說明如何將數位資產從AEM發佈至Dynamic Media Classic，反之亦然。 檢視器也會詳細說明。 如需為Dynamic Media Classic設定AEM的詳細資訊，請參閱[整合Dynamic Media Classic與AEM](/help/sites-administering/scene7.md)。

另請參閱[新增影像圖](/help/assets/image-maps.md)。

如需搭配AEM使用視訊元件的詳細資訊，請參閱下列內容：

* [影片](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md)

>[!NOTE]
>
>如果Dynamic Media Classic資產未正確顯示，請確定Dynamic Media為[disabled](/help/assets/config-dynamic.md#disabling-dynamic-media)，然後重新整理頁面。

## 從Assets {#manually-publishing-to-scene-from-assets}手動發佈至Dynamic Media Classic

您可以從傳統UI的Assets控制台或直接從資產將數位資產發佈至Dynamic Media Classic。

>[!NOTE]
>
>AEM會以非同步方式發佈至Dynamic Media Classic。 按一下&#x200B;**[!UICONTROL Publish]**&#x200B;後，您的資產可能需要數秒的時間才會發佈至Dynamic Media Classic。


### 從Assets控制台發佈{#publishing-from-the-assets-console}

若要在資產位於Dynamic Media Classic目標資料夾中時，從Assets控制台發佈至Dynamic Media Classic:

1. 在AEM傳統UI中，按一下&#x200B;**[!UICONTROL 數位資產]**&#x200B;以存取數位資產管理器。

1. 從您要發佈至Dynamic Media Classic的目標資料夾中選取資產（或資產）或資料夾，然後按一下滑鼠右鍵，然後選取&#x200B;**[!UICONTROL 發佈至Dynamic Media Classic]**。 或者，您也可以從&#x200B;**[!UICONTROL 工具]**&#x200B;功能表選取&#x200B;**[!UICONTROL 發佈至Dynamic Media Classic]**。

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. 前往Dynamic Media Classic，確認資產可供使用。

   >[!NOTE]
   >
   >如果資產不在Dynamic Media Classic同步資料夾中，則兩個功能表中的&#x200B;**[!UICONTROL 發佈至Dynamic Media Classic]**&#x200B;都會顯示但停用。

### 從資產{#publishing-from-an-asset}發佈

只要資產位於同步的Dynamic Media Classic資料夾內，您就可以手動發佈資產。

>[!NOTE]
>
>如果資產未位於Dynamic Media Classic同步資料夾中，則無法使用&#x200B;**[!UICONTROL 發佈至Dynamic Media Classic]**&#x200B;的連結。

**若要直接從數位資產發佈至Dynamic Media Classic**:

1. 在AEM中，按一下&#x200B;**[!UICONTROL 數位資產]**&#x200B;以存取數位資產管理器。

1. 按兩下以開啟資產。

1. 在資產詳細資訊窗格中，選取&#x200B;**[!UICONTROL 發佈至Dynamic Media Classic]**。

   ![screen_shot_2012-02-22at34828pm](assets/screen_shot_2012-02-22at34828pm.png)

1. 連結變更為&#x200B;**[!UICONTROL 發佈……]**，然後&#x200B;**[!UICONTROL Published]**。 前往Dynamic Media Classic，確認資產可用。

   >[!NOTE]
   >
   >如果資產未正確發佈至Dynamic Media Classic，則連結會變更為&#x200B;**[!UICONTROL Publishing Failed]**。 如果資產已發佈至Dynamic Media Classic，此連結會顯示「**[!UICONTROL 重新發佈至Dynamic Media Classic]**」。 重新發佈可讓您在AEM中變更資產並重新發佈。

### 從CQ目標資料夾外部發佈資產{#publishing-assets-from-outside-the-cq-target-folder}

Adobe建議您只從Dynamic Media Classic目標資料夾中的資產發佈資產至Dynamic Media Classic。 不過，如果您需要從目標資料夾外部的資料夾上傳資產，您仍可將資產上傳至Dynamic Media Classic上的&#x200B;*ad-hoc*&#x200B;資料夾，以執行此操作。

若要這麼做，請為將顯示資產的頁面設定雲端設定。 然後將Dynamic Media Classic元件新增至頁面，並將資產拖放至元件上。 為該頁面設定頁面屬性後，當選取時觸發上傳至Dynamic Media Classic時，會出現&#x200B;**[!UICONTROL 發佈至Dynamic Media Classic]**&#x200B;連結。

>[!NOTE]
>
>臨機資料夾中的資產不會顯示在Dynamic Media Classic內容瀏覽器中。

**若要發佈位於CQ目標資料夾以外的資產**:

1. 在傳統UI的AEM中，按一下&#x200B;**[!UICONTROL 網站]**&#x200B;並導覽至您要新增尚未發佈至Dynamic Media Classic數位資產的網頁。 （套用一般頁面繼承規則）。

1. 在sidekick中，按一下&#x200B;**[!UICONTROL Page]**&#x200B;圖示，然後按一下&#x200B;**[!UICONTROL Page Properties]**。

1. 按一下&#x200B;**[!UICONTROL Cloud Services] > [!UICONTROL 新增服務] > [!UICONTROL Dynamic Media Classic(Scene7)]**。
1. 在「AdobeDynamic Media Classic」下拉式清單中，選取所需的設定，然後按一下&#x200B;**[!UICONTROL 確定]**。

   ![chlimage_1-77](assets/chlimage_1-77.png)

1. 在網頁上，將Dynamic Media Classic(Scene7)元件新增至頁面上的所需位置。
1. 從內容尋找器，將數位資產拖曳至元件。 您會看到「**[!UICONTROL 檢查Dynamic Media Classic發佈狀態]**」連結。

   >[!NOTE]
   >
   >如果數位資產位於CQ目標資料夾中，則沒有顯示「檢查Dynamic Media Classic發佈狀態&#x200B;]**」的連結。**[!UICONTROL &#x200B;資產只會放置在元件中。

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. 按一下「**[!UICONTROL 檢查Dynamic Media Classic發佈狀態]**」。 如果資產未發佈，AEM會將資產發佈至Dynamic Media Classic。 上傳資產後，資產會位於臨機資料夾中。 預設情況下，臨機資料夾位於`name_of_the_company/CQ5_adhoc`中。 如有需要，您可以[設定此項目](#configuringtheadhocfolder)。

   >[!NOTE]
   >
   >如果資產不在Dynamic Media Classic已同步資料夾中，且目前頁面沒有相關聯的Dynamic Media Classic雲端設定，上傳將會失敗。

## Dynamic Media Classic(Scene7)元件{#scene-components}

AEM提供下列Dynamic Media Classic元件：

* 縮放
* 彈出（縮放）
* 影像範本
* 影像
* 影片

>[!NOTE]
>
>預設不提供這些元件，在使用前需要在&#x200B;**[!UICONTROL Design]**&#x200B;模式中選取這些元件。

在&#x200B;**[!UICONTROL Design]**&#x200B;模式中使用元件後，您可以像其他任何AEM元件一樣將元件新增至頁面。 如果是在同步的資料夾、頁面上或使用Dynamic Media Classic雲端設定，則尚未發佈至Dynamic Media Classic的資產會發佈至Dynamic Media Classic。

### Flash檢視器生命週期結束注意事項{#flash-viewers-end-of-life-notice}

自2017年1月31日起，AdobeDynamic Media Classic已正式停止支援Flash檢視器平台。

### 將Dynamic Media Classic元件新增至頁面{#adding-a-scene-component-to-a-page}

將Dynamic Media Classic元件新增至頁面，與將元件新增至任何頁面相同。 Dynamic Media Classic元件在以下章節中詳細說明。

**若要將Dynamic Media Classic元件/檢視器新增至傳統UI中的頁面**:

1. 在AEM中，開啟您要新增Dynamic Media Classic元件的頁面。

1. 如果沒有可用的Dynamic Media Classic元件，請按一下sidekick中的尺標以進入&#x200B;**[!UICONTROL Design]**&#x200B;模式，按一下&#x200B;**[!UICONTROL Edit]** parsys，然後選取所有&#x200B;**[!UICONTROL Dynamic Media Classic]**&#x200B;元件以使它們可用。

1. 按一下sidekick中的鉛筆，返回&#x200B;**[!UICONTROL 編輯]**&#x200B;模式。

1. 將sidekick中&#x200B;**[!UICONTROL Dynamic Media Classic]**&#x200B;群組的元件拖曳至所需位置的頁面。

1. 按一下「**[!UICONTROL 編輯]**」以開啟元件。

1. 視需要編輯元件，然後按一下&#x200B;**[!UICONTROL OK]**&#x200B;以儲存變更。

### 將互動式檢視體驗新增至回應式網站{#adding-interactive-viewing-experiences-to-a-responsive-website}

針對資產進行回應式設計，表示資產會根據其顯示位置進行適應。 透過回應式設計，在多部裝置上有效顯示相同的資產。

**若要在傳統UI中將互動式檢視體驗新增至回應式網站**:

1. 登入AEM，並確認您已設定[AdobeDynamic Media ClassicCloud Services](/help/sites-administering/scene7.md#configuring-scene-integration)，且Dynamic Media Classic元件可用。

   >[!NOTE]
   >
   >如果Dynamic Media Classic WCM元件不可用，請務必透過**[!UICONTROL Design]模式啟用。

1. 在已啟用Dynamic Media Classic元件的網站中，將&#x200B;**[!UICONTROL Image]**&#x200B;檢視器拖曳至頁面。
1. 編輯元件並調整&#x200B;**[!UICONTROL Dynamic Media Classic Settings]**&#x200B;標籤中的斷點。

   ![chlimage_1-79](assets/chlimage_1-79.png)

1. 確認檢視器正在回應性地調整大小，且所有互動都已針對桌上型電腦、平板電腦和行動裝置最佳化。

### 所有Dynamic Media Classic元件的共同設定{#settings-common-to-all-scene-components}

雖然設定選項有所不同，但下列是所有Dynamic Media Classic元件的常見項目：

* **[!UICONTROL 檔案參考]**  — 瀏覽至您要參考的檔案。檔案參考會顯示資產URL，而非完整的Dynamic Media Classic URL，包括URL命令和參數。 您無法在此欄位中新增Dynamic Media Classic URL命令和參數。 必須透過元件中的對應功能來新增。
* **[!UICONTROL 寬度]**  — 可讓您設定寬度。
* **[!UICONTROL 高度]**  — 可讓您設定高度。

您可以連按兩下Dynamic Media Classic元件，例如開啟&#x200B;**[!UICONTROL Zoom]**&#x200B;元件時，設定這些設定選項：

![chlimage_1-80](assets/chlimage_1-80.png)

### 縮放 {#zoom}

按下+按鈕時，HTML5縮放元件會顯示較大的影像。

資產底部有縮放工具。 按一下&#x200B;**[!UICONTROL +]**&#x200B;放大。 按一下&#x200B;**[!UICONTROL -]**&#x200B;以減少。 按一下&#x200B;**[!UICONTROL x]**&#x200B;或重設縮放箭頭，可將影像重新調整為原來匯入的大小。 按一下對角線箭頭，使其成為全螢幕。 按一下&#x200B;**[!UICONTROL Edit]**&#x200B;以設定元件。 使用此元件，您可以配置所有Dynamic Media Classic元件(](#settings-common-to-all-scene-components))通用的[設定。

![](do-not-localize/chlimage_1-5.png)

### 飛出 {#flyout}

在HTML5彈出元件中，資產會顯示為分割畫面；將資產保留在指定大小；顯示縮放部分的右側。 按一下&#x200B;**[!UICONTROL Edit]**&#x200B;以設定元件。 使用此元件，您可以配置所有Dynamic Media Classic元件(](/help/sites-administering/scene7.md#settingscommontoalldynamicmediaclassiccomponents))通用的[設定。

>[!NOTE]
>
>如果您的彈出元件使用自訂大小，則會使用該自訂大小，並停用元件的回應式設定。
>
>如果您的彈出元件使用預設大小，如[!UICONTROL Design]檢視中所設定，則會使用預設大小，元件會延伸以容納頁面版面大小，並啟用元件的回應式設定。 但請注意，元件的回應式設定有其限制。 當您使用具有回應式設定的彈出元件時，不應將其用於完整頁面延伸。 否則，飛出可能會延伸到頁面的右邊。

![chlimage_1-81](assets/chlimage_1-81.png)

### 影像 {#image}

Dynamic Media Classic影像元件可讓您將Dynamic Media Classic功能新增至影像，例如Dynamic Media Classic修飾元、影像或檢視器預設集，以及銳利化。 Dynamic Media Classic影像元件與AEM中具有特殊Dynamic Media Classic功能的其他影像元件類似。 在此範例中，影像已套用Dynamic Media Classic URL修飾元`&op_invert=1`。

![](do-not-localize/chlimage_1-6.png)

**[!UICONTROL 標題、替代文字]**  — 在「進階」  標籤中，為影像新增標題，並為關閉圖形的使用者新增替代文字。

**[!UICONTROL URL，在]** 中開啟 — 您可以從設定資產以開啟連結。設定&#x200B;**[!UICONTROL URL]**&#x200B;和&#x200B;**[!UICONTROL 在]**&#x200B;中開啟，以指示您要在相同視窗還是在新視窗中開啟它。

![chlimage_1-82](assets/chlimage_1-82.png)

**[!UICONTROL 檢視器預設集]**  — 從下拉式選單中選取現有的檢視器預設集。如果您要尋找的檢視器預設集未顯示，您可能需要將其顯示。 請參閱[管理檢視器預設集](/help/assets/managing-viewer-presets.md)。 如果您使用影像預設集，則無法選取檢視器預設集，反之亦然。

**[!UICONTROL Dynamic Media Classic設定]**  — 選取您要用來從Scene7發佈系統擷取作用中影像預設集的Dynamic Media Classic設定。

**[!UICONTROL 影像預設]**  — 從下拉式選單中選取現有的影像預設集。如果您要尋找的影像預設集未顯示，則您可能需要使其可見。 請參閱[管理影像預設集](/help/assets/managing-image-presets.md)。 如果您使用影像預設集，則無法選取檢視器預設集，反之亦然。

**[!UICONTROL 輸出格式]**  — 選擇影像的輸出格式，例如jpeg。視您選取的輸出格式而定，您可能有其他設定選項。 請參閱[管理影像預設集](/help/assets/managing-image-presets.md)。

**[!UICONTROL 銳利化]**  — 選取您要如何銳利化影像。[*「AdobeDynamic Media Classic影像品質與銳利化最佳實務*](/help/assets/assets/sharpening_images.pdf)」中會詳細說明銳利化。

**[!UICONTROL URL修飾元]**  — 您可以提供其他Dynamic Media Classic影像命令，以變更影像效果。在[管理影像預設集](/help/assets/managing-image-presets.md)和[命令參考](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html)中對這些內容進行了說明。

**[!UICONTROL 中斷點]**  — 如果網站回應式，您要調整中斷點。斷點必須用逗號`,`分隔。

### 影像範本 {#image-template}

[Dynamic Media Classic影像](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/template-basics/quick-start-template-basics.html#template-basics) 範本是已匯入至Dynamic Media Classic的分層Photoshop內容，其中內容和屬性已參數化，因而可變性。**[!UICONTROL 影像範本]**&#x200B;元件可讓您匯入影像，並在AEM中動態變更文字。 此外，您可以設定&#x200B;**[!UICONTROL 影像範本]**&#x200B;元件，以使用用戶端內容的值，讓每位使用者都能以個人化的方式體驗影像。

按一下&#x200B;**[!UICONTROL Edit]**&#x200B;以設定元件。 您可以配置所有Dynamic Media Classic元件](/help/sites-administering/scene7.md#settingscommontoalldynamicmediaclassicscomponents)的共同設定，以及本節所述的其他設定。[

![chlimage_1-83](assets/chlimage_1-83.png)

**[!UICONTROL 檔案參考、寬度、高度]**  — 查看所有Dynamic Media Classic元件通用的設定。

>[!NOTE]
>
>Dynamic Media傳統URL命令和參數無法直接新增至檔案參考URL。 它們只能在&#x200B;**[!UICONTROL Parameter]**&#x200B;面板的元件UI中定義。

**[!UICONTROL 標題、替]** 代文字在Dynamic Media  [!UICONTROL Classic影像範本] 索引標籤中，為影像新增標題，並為關閉圖形的使用者新增替代文字。

**[!UICONTROL URL，在中]** 開啟您可以從設定資產以開啟連結。設定&#x200B;**[!UICONTROL URL]**，並在&#x200B;**[!UICONTROL 在]**&#x200B;中開啟指示您要在相同視窗還是在新視窗中開啟它。

![chlimage_1-84](assets/chlimage_1-84.png)

**[!UICONTROL 參]** 數面板匯入影像時，參數會預先填入影像的資訊。如果沒有可動態變更的內容，此視窗為空。

![chlimage_1-85](assets/chlimage_1-85.png)

#### 動態更改文本{#changing-text-dynamically}

要動態更改文本，請在欄位中輸入新文本，然後按一下&#x200B;**[!UICONTROL OK]**。 在此範例中，**[!UICONTROL Price]**&#x200B;現在為$50，而運費為99美分。

![chlimage_1-86](assets/chlimage_1-86.png)

影像中的文字會變更。 您可以按一下欄位旁的&#x200B;**[!UICONTROL 重設]**，將文字重設回原始值。

![chlimage_1-87](assets/chlimage_1-87.png)

#### 更改文本以反映客戶端上下文值{#changing-text-to-reflect-the-value-of-a-client-context-value}的值

要將欄位連結到客戶端上下文值，請按一下&#x200B;**[!UICONTROL 選擇]**&#x200B;以開啟客戶端上下文菜單，選擇客戶端上下文，然後按一下&#x200B;**[!UICONTROL 確定]**。 在此示例中，名稱會根據將名稱與配置檔案中的格式化名稱連結而改變。

![chlimage_1-88](assets/chlimage_1-88.png)

文字會反映目前登入使用者的名稱。 您可以按一下欄位旁的&#x200B;**[!UICONTROL 重設]**，將文字重設回原始值。

![chlimage_1-89](assets/chlimage_1-89.png)

#### 將Dynamic Media Classic影像範本設為連結{#making-the-scene-image-template-a-link}

**若要讓Dynamic Media Classic影像範本成為連結**:

1. 在具有Dynamic Media Classic影像範本元件的頁面上，按一下「**[!UICONTROL 編輯]**」。
1. 在&#x200B;**[!UICONTROL URL]**&#x200B;欄位中，輸入在點擊影像時使用者所前往的URL。 在&#x200B;**[!UICONTROL 在]**&#x200B;中開啟欄位中，選擇要開啟目標（新窗口還是同一窗口）。

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. 按一下&#x200B;**[!UICONTROL 「確定」]**。

### 視訊元件{#video-component}

Dynamic Media Classic **[!UICONTROL Video]**&#x200B;元件(可從sidekick的Dynamic Media Classic區段取得)使用裝置和頻寬偵測，將正確的視訊提供至每個畫面。 此元件為HTML5視訊播放器；是可跨頻道使用的單一檢視器。

它可用於最適化視訊集、單一MP4視訊或單一F4V視訊。

請參閱[Video](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md)以取得有關視訊如何搭配Dynamic Media Classic整合運作的詳細資訊。 此外，查看[Dynamic Media Classic視訊&#x200B;**元件與基礎** video **元件](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md)的比較結果。**

![chlimage_1-91](assets/chlimage_1-91.png)

### 視訊元件{#known-limitations-for-the-video-component}的已知限制

AdobeDAM和WCM會顯示主視訊是否已上傳。 它們不會顯示這些代理資產：

* Dynamic Media Classic編碼轉譯
* Dynamic Media Classic適用性視訊集

搭配Dynamic Media Classic視訊元件使用最適化視訊集時，您必須調整元件大小以符合視訊的尺寸。

## Dynamic Media Classic內容瀏覽器{#scene-content-browser}

Dynamic Media Classic內容瀏覽器可讓您直接在AEM中檢視Dynamic Media Classic的內容。 若要存取內容瀏覽器，請在「內容尋找器」中，選取觸控最佳化使用者介面中的&#x200B;**[!UICONTROL Dynamic Media Classic]**&#x200B;或傳統使用者介面中的&#x200B;**[!UICONTROL S7]**&#x200B;圖示。 這兩個使用者介面的功能完全相同。

如果您有多個設定，依預設AEM會顯示[預設設定](/help/sites-administering/scene7.md#configuring-a-default-configuration)。 您可以直接在Dynamic Media Classic內容瀏覽器的下拉式功能表中選取不同的設定。

>[!NOTE]
>
>* 位於臨機資料夾中的資產不會顯示在Dynamic Media Classic內容瀏覽器中。
>* 當[啟用](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene)安全預覽時，Dynamic Media Classic上已發佈和未發佈的資產都會顯示在Dynamic Media Classic內容瀏覽器中。
>* 如果您在內容瀏覽器中未看到&#x200B;**[!UICONTROL Dynamic Media Classic]**&#x200B;或&#x200B;**[!UICONTROL S7]**&#x200B;圖示做為選項，則需要[設定Dynamic Media Classic以搭配AEM](/help/sites-administering/scene7.md)使用。

   >
   >
* 若是影片，Dynamic Media Classic內容瀏覽器支援：
   >
   >
* 最適化視訊集：容器，以便在多個畫面間順暢播放所需的所有視訊轉譯
>* 單MP4視頻
>* 單一F4V影片


### 瀏覽傳統UI {#browsing-content-in-the-classic-ui}中的內容

按一下&#x200B;**[!UICONTROL S7]**&#x200B;標籤，瀏覽Dynamic Media Classic中的內容。

您可以選取設定，以變更要存取的設定。 資料夾會根據您選取的組態而改變。

![chlimage_1-92](assets/chlimage_1-92.png)

和資產的內容尋找器一樣，您可以搜尋資產並篩選結果。 不過，與「資產尋找器」不同，在&#x200B;**[!UICONTROL S7]**&#x200B;索引標籤中輸入關鍵字時，檔案名稱&#x200B;*以您輸入的字串*&#x200B;開頭，而不是以檔案名稱中包含&#x200B;*關鍵字的*&#x200B;開頭。

依預設，資產會依檔案名稱顯示。 您也可以依資產類型篩選結果。

>[!NOTE]
>
>若是影片，WCM的Dynamic Media Classic內容瀏覽器支援：
>
>* 最適化視訊集：容器，以便在多個畫面間順暢播放所需的所有視訊轉譯
>* 單MP4視頻
>* 單一F4V影片

>



### 使用內容瀏覽器{#searching-for-scene-assets-with-the-content-browser}搜尋Dynamic Media Classic資產

搜尋Dynamic Media Classic資產與搜尋AEM資產類似，只不過搜尋時，您實際上看到的是Dynamic Media Classic系統中資產的遠端檢視，而非直接匯入AEM。

您可以使用傳統UI或觸控最佳化UI來檢視和搜尋資產。 根據介面，您的搜尋方式會稍有不同。

在任一UI中搜尋時，您可以依下列條件進行篩選（如觸控最佳化UI的此處所示）:

**[!UICONTROL 輸入關鍵字]**  — 您可以依名稱搜尋資產。搜尋所輸入的關鍵字時，檔案名稱的開頭為。 例如，輸入&quot;swimming&quot;會尋找任何以該順序字母開頭的資產檔案名稱。 輸入詞語以尋找資產後，請務必按一下「輸入」。

![chlimage_1-93](assets/chlimage_1-93.png)

**[!UICONTROL 資料夾/路徑]**  — 顯示的資料夾名稱是根據您選取的設定。您可以按一下資料夾圖示並選取子資料夾，然後按一下核取記號以選取，以深入鑽研至較低層級。

如果您輸入關鍵字並選取資料夾，AEM會搜尋該資料夾和任何子資料夾。 不過，如果您在搜尋時未輸入任何關鍵字，選取資料夾只會顯示該資料夾中的資產，且不會包含任何子資料夾。

依預設，AEM會搜尋選取的資料夾和所有子資料夾。

![chlimage_1-94](assets/chlimage_1-94.png)

**[!UICONTROL 資產類]** 型選取Dynamic Media Classic以瀏覽Dynamic Media Classic內容。只有在您已設定Dynamic Media Classic時，才可使用此選項。

![chlimage_1-95](assets/chlimage_1-95.png)

**** 設定如果您在Cloud Services中定義了多個Dynamic Media Classic [!UICONTROL 設定]，可在此處選取。因此，資料夾會根據您選擇的設定而變更。

![chlimage_1-96](assets/chlimage_1-96.png)

**[!UICONTROL 資]** 產類型在Dynamic Media Classic瀏覽器中，您可以篩選結果以包含下列任一項目：影像、範本、影片和最適化影片集。如果您未選取任何資產類型，依預設AEM會搜尋所有資產類型。

![chlimage_1-97](assets/chlimage_1-97.png)

>[!NOTE]
>
>* 搜尋視訊時，會搜尋單一轉譯。 結果會傳回原始轉譯（僅限&amp;ast;.mp4）和編碼的轉譯。
>* 搜尋最適化視訊集時，您會搜尋資料夾和所有子資料夾，但僅限於已新增關鍵字至搜尋時。 如果您尚未新增關鍵字，AEM不會搜尋子資料夾。

>



**[!UICONTROL 發佈]** 狀態您可以根據發佈狀態篩選資產：  發佈或 [!UICONTROL 取消發佈]。如果您未選取任何[!UICONTROL 發佈狀態]，預設情況下AEM會搜尋所有發佈狀態。

![chlimage_1-98](assets/chlimage_1-98.png)

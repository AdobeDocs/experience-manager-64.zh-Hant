---
title: 將Dynamic Media Classic功能新增至頁面
seo-title: Adding Dynamic Media Classic features to your page
description: Adobe Dynamic Media Classic是托管解決方案，可管理、增強、發佈和傳遞多媒體資產至網路、行動裝置、電子郵件及網際網路連線的顯示器及列印。
seo-description: Adobe Dynamic Media Classic is a hosted solution for managing, enhancing, publishing, and delivering rich media assets to Web, mobile, email, and Internet-connected displays and print.
uuid: 66b9c150-c482-4a41-9772-fa39c135802c
contentOwner: Alva Ware-Bevacqui
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 9ba95dce-a801-4a36-8798-45d295371b1b
exl-id: 93921d23-a2bf-43b6-b002-58a7482b22b0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3383'
ht-degree: 1%

---

# 將Dynamic Media Classic功能新增至頁面{#adding-scene-features-to-your-page}

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

本節說明如何將數位資產從AEM發佈至Dynamic Media Classic，反之亦然。 檢視器也會詳細說明。 如需為Dynamic Media Classic設定AEM的詳細資訊，請參閱 [整合Dynamic Media Classic與AEM](/help/sites-administering/scene7.md).

另請參閱 [新增影像地圖](/help/assets/image-maps.md).

如需搭配AEM使用視訊元件的詳細資訊，請參閱下列內容：

* [影片](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md)

>[!NOTE]
>
>如果Dynamic Media Classic資產未正確顯示，請確定Dynamic Media為 [停用](/help/assets/config-dynamic.md#disabling-dynamic-media) 然後重新整理頁面。

## 從Assets手動發佈至Dynamic Media Classic {#manually-publishing-to-scene-from-assets}

您可以從傳統UI的Assets控制台或直接從資產將數位資產發佈至Dynamic Media Classic。

>[!NOTE]
>
>AEM會非同步發佈至Dynamic Media Classic。 按一下 **[!UICONTROL 發佈]**，您的資產可能需要數秒的時間才能發佈至Dynamic Media Classic。

### 從Assets主控台發佈 {#publishing-from-the-assets-console}

若要在資產位於Dynamic Media Classic目標資料夾中時，從Assets控制台發佈至Dynamic Media Classic :

1. 在AEM傳統UI中，按一下 **[!UICONTROL 數位資產]** 存取數位資產管理器。

1. 從您要發佈至Dynamic Media Classic的目標資料夾中選取資產（或資產）或資料夾，然後按一下滑鼠右鍵並選取 **[!UICONTROL 發佈至Dynamic Media Classic]**. 或者，您也可以選取 **[!UICONTROL 發佈至Dynamic Media Classic]** 從 **[!UICONTROL 工具]** 功能表。

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. 前往Dynamic Media Classic並確認資產可供使用。

   >[!NOTE]
   >
   >如果資產不在Dynamic Media Classic同步資料夾中， **[!UICONTROL 發佈至Dynamic Media Classic]** 會顯示，但會停用。

### 從資產發佈 {#publishing-from-an-asset}

只要資產位於同步的Dynamic Media Classic資料夾內，您就可以手動發佈資產。

>[!NOTE]
>
>如果資產未位於Dynamic Media Classic同步資料夾中，則會將連結連結至 **[!UICONTROL 發佈至Dynamic Media Classic]** 無法使用。

**直接從數位資產發佈至Dynamic Media Classic**:

1. 在AEM中，按一下 **[!UICONTROL 數位資產]** 存取數位資產管理器。

1. 按兩下以開啟資產。

1. 在資產詳細資訊窗格中，選取 **[!UICONTROL 發佈至Dynamic Media Classic]**.

   ![screen_shot_2012-02-22at34828pm](assets/screen_shot_2012-02-22at34828pm.png)

1. 連結變更為 **[!UICONTROL 正在發佈……]** 然後 **[!UICONTROL 已發佈]**. 前往Dynamic Media Classic並確認資產可用。

   >[!NOTE]
   >
   >如果資產未正確發佈至Dynamic Media Classic，連結會變更為 **[!UICONTROL 發佈失敗]**. 如果資產已發佈至Dynamic Media Classic，連結會顯示 **[!UICONTROL 重新發佈至Dynamic Media Classic]**. 重新發佈可讓您在AEM中變更資產並重新發佈。

### 從CQ目標資料夾外部發佈資產 {#publishing-assets-from-outside-the-cq-target-folder}

Adobe建議您只從Dynamic Media Classic Target資料夾內的資產發佈資產至Dynamic Media Classic。 不過，如果您需要從目標資料夾外部的資料夾上傳資產，您仍可將資產上傳至 *臨機* 資料夾。

若要這麼做，請為將顯示資產的頁面設定雲端設定。 然後，將Dynamic Media Classic元件新增至頁面，並將資產拖放至元件上。 為該頁面設定頁面屬性後， **[!UICONTROL 發佈至Dynamic Media Classic]** 連結顯示，當選取時，會觸發上傳至Dynamic Media Classic。

>[!NOTE]
>
>臨機資料夾中的資產不會顯示在Dynamic Media Classic內容瀏覽器中。

**發佈位於CQ目標資料夾以外的資產**:

1. 在傳統UI的AEM中，按一下 **[!UICONTROL 網站]** 並導覽至您要新增尚未發佈至Dynamic Media Classic之數位資產的網頁。 （套用一般頁面繼承規則）。

1. 在sidekick中，按一下 **[!UICONTROL 頁面]** 圖示，然後按一下 **[!UICONTROL 頁面屬性]**.

1. 按一下 **[!UICONTROL Cloud Services] > [!UICONTROL 新增服務] > [!UICONTROL Dynamic Media Classic(Scene7)]**.
1. 在Adobe Dynamic Media Classic下拉式清單中，選取所需的設定，然後按一下 **[!UICONTROL 確定]**.

   ![chlimage_1-77](assets/chlimage_1-77.png)

1. 在網頁上，將Dynamic Media Classic(Scene7)元件新增至頁面上的所需位置。
1. 從內容尋找器，將數位資產拖曳至元件。 您會看到連結 **[!UICONTROL 檢查Dynamic Media Classic發佈狀態]**.

   >[!NOTE]
   >
   >如果數位資產位於CQ目標資料夾中，則不會連結至 **[!UICONTROL 檢查Dynamic Media Classic發佈狀態]** 框。 資產只會放置在元件中。

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. 按一下 **[!UICONTROL 檢查Dynamic Media Classic發佈狀態]**. 如果資產未發佈，AEM會將資產發佈至Dynamic Media Classic。 上傳資產後，資產會位於臨機資料夾中。 依預設，臨機資料夾位於 `name_of_the_company/CQ5_adhoc`. 您可以 [視需要設定此項目](#configuringtheadhocfolder).

   >[!NOTE]
   >
   >如果資產不在Dynamic Media Classic同步資料夾中，且目前頁面沒有相關聯的Dynamic Media Classic雲端設定，上傳將會失敗。

## Dynamic Media Classic(Scene7)元件 {#scene-components}

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

### Flash檢視器生命週期結束通知 {#flash-viewers-end-of-life-notice}

自2017年1月31日起，Adobe Dynamic Media Classic正式停止支援Flash檢視器平台。

### 新增Dynamic Media Classic元件至頁面 {#adding-a-scene-component-to-a-page}

將Dynamic Media Classic元件新增至頁面，與將元件新增至任何頁面相同。 Dynamic Media Classic元件在以下章節中有詳細說明。

**若要將Dynamic Media Classic元件/檢視器新增至傳統UI中的頁面**:

1. 在AEM中，開啟您要新增Dynamic Media Classic元件的頁面。

1. 如果沒有可用的Dynamic Media Classic元件，請按一下sidekick中的尺標以輸入 **[!UICONTROL 設計]** 模式，按一下 **[!UICONTROL 編輯]** parsys，然後選取所有 **[!UICONTROL Dynamic Media Classic]** 元件以供使用。

1. 返回 **[!UICONTROL 編輯]** 模式，方法是按一下sidekick中的鉛筆。

1. 從 **[!UICONTROL Dynamic Media Classic]** 在sidekick中群組至所需位置中的頁面。

1. 按一下 **[!UICONTROL 編輯]** 以開啟元件。

1. 視需要編輯元件，然後按一下 **[!UICONTROL 確定]** 以儲存變更。

### 新增互動式檢視體驗至回應式網站 {#adding-interactive-viewing-experiences-to-a-responsive-website}

針對資產進行回應式設計，表示資產會根據其顯示位置進行適應。 透過回應式設計，在多部裝置上有效顯示相同的資產。

**若要在傳統UI中將互動式檢視體驗新增至回應式網站**:

1. 登入AEM，並確認您 [已設定Adobe Dynamic Media ClassicCloud Services](/help/sites-administering/scene7.md#configuring-scene-integration) 以及Dynamic Media Classic元件可供使用。

   >[!NOTE]
   >
   >如果Dynamic Media Classic WCM元件無法使用，請務必透過**啟用[!UICONTROL 設計] 模式。

1. 在已啟用Dynamic Media Classic元件的網站中，拖曳 **[!UICONTROL 影像]** 檢視器。
1. 編輯元件並調整 **[!UICONTROL Dynamic Media Classic設定]** 標籤。

   ![chlimage_1-79](assets/chlimage_1-79.png)

1. 確認檢視器正在回應性地調整大小，且所有互動都已針對桌上型電腦、平板電腦和行動裝置最佳化。

### 所有Dynamic Media Classic元件的共同設定 {#settings-common-to-all-scene-components}

雖然設定選項有所不同，但下列是所有Dynamic Media Classic元件的常見項目：

* **[!UICONTROL 檔案參考]**  — 瀏覽到要引用的檔案。 檔案參考會顯示資產URL，而非完整的Dynamic Media Classic URL，包括URL命令和參數。 您無法在此欄位中新增Dynamic Media Classic URL命令和參數。 必須透過元件中的對應功能來新增。
* **[!UICONTROL 寬度]**  — 可讓您設定寬度。
* **[!UICONTROL 高度]**  — 可讓您設定高度。

您可以連按兩下Dynamic Media Classic元件(例如開啟 **[!UICONTROL 縮放]** 元件：

![chlimage_1-80](assets/chlimage_1-80.png)

### 縮放 {#zoom}

當您按下+按鈕時，「HTML5縮放」元件會顯示較大的影像。

資產底部有縮放工具。 按一下 **[!UICONTROL +]** 放大。 按一下 **[!UICONTROL -]** 減少。 按一下 **[!UICONTROL x]** 或者，重置縮放箭頭將影像恢復為導入時的原始大小。 按一下對角線箭頭，使其成為全螢幕。 按一下 **[!UICONTROL 編輯]** 以設定元件。 使用此元件，您可以設定 [所有Dynamic Media Classic元件的共同設定](#settings-common-to-all-scene-components).

![](do-not-localize/chlimage_1-5.png)

### 飛出 {#flyout}

在「HTML5彈出」元件中，資產會顯示為分割畫面；將資產保留在指定大小；顯示縮放部分的右側。 按一下 **[!UICONTROL 編輯]** 以設定元件。 使用此元件，您可以設定 [所有Dynamic Media Classic元件的共同設定](/help/sites-administering/scene7.md#settingscommontoalldynamicmediaclassiccomponents).

>[!NOTE]
>
>如果您的彈出元件使用自訂大小，則會使用該自訂大小，並停用元件的回應式設定。
>
>如果您的彈出元件使用預設大小，如 [!UICONTROL 設計] 檢視，則會使用預設大小，元件會延伸以容納頁面配置大小，並啟用元件的回應式設定。 但請注意，元件的回應式設定有其限制。 當您使用具有回應式設定的彈出元件時，不應將其用於完整頁面延伸。 否則，飛出可能會延伸到頁面的右邊。

![chlimage_1-81](assets/chlimage_1-81.png)

### 影像 {#image}

Dynamic Media Classic影像元件可讓您將Dynamic Media Classic功能新增至影像，例如Dynamic Media Classic修飾元、影像或檢視器預設集，以及銳利化。 Dynamic Media Classic影像元件與AEM中具有特殊Dynamic Media Classic功能的其他影像元件類似。 在此範例中，影像具有Dynamic Media Classic URL修飾元， `&op_invert=1` 已套用。

![](do-not-localize/chlimage_1-6.png)

**[!UICONTROL 標題、替代文字]**  — 在 [!UICONTROL 進階] 頁簽，為影像添加標題，並為那些已關閉圖形的用戶添加alt文本。

**[!UICONTROL URL，在中開啟]**  — 您可以從設定資產，以開啟連結。 設定 **[!UICONTROL URL]** 和 **[!UICONTROL 在中開啟]** 以指定要在同一窗口還是新窗口中開啟它。

![chlimage_1-82](assets/chlimage_1-82.png)

**[!UICONTROL 檢視器預設集]**  — 從下拉式選單中選取現有的檢視器預設集。 如果您要尋找的檢視器預設集未顯示，您可能需要將其顯示。 請參閱 [管理檢視器預設集](/help/assets/managing-viewer-presets.md). 如果您使用影像預設集，則無法選取檢視器預設集，反之亦然。

**[!UICONTROL Dynamic Media Classic設定]**  — 選取您要用來從Dynamic Media Classic發佈系統擷取作用中影像預設集的Scene7設定。

**[!UICONTROL 影像預設集]**  — 從下拉式選單中選取現有的影像預設集。 如果您要尋找的影像預設集未顯示，則您可能需要使其可見。 請參閱 [管理影像預設集](/help/assets/managing-image-presets.md). 如果您使用影像預設集，則無法選取檢視器預設集，反之亦然。

**[!UICONTROL 輸出格式]**  — 選擇影像的輸出格式，例如jpeg。 視您選取的輸出格式而定，您可能有其他設定選項。 請參閱 [管理影像預設集](/help/assets/managing-image-presets.md).

**[!UICONTROL 銳利化]**  — 選擇要如何銳化影像。 銳利化詳細說明於 [*Adobe Dynamic Media Classic影像品質和銳利化最佳作法*](/help/assets/assets/sharpening_images.pdf).

**[!UICONTROL URL修飾元]**  — 您可以提供其他Dynamic Media Classic影像命令來更改影像效果。 這些說明於 [管理影像預設集](/help/assets/managing-image-presets.md) 和 [命令參考](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html).

**[!UICONTROL 斷點]**  — 如果網站回應式，您要調整中斷點。 斷點必須用逗號分隔 `,`.

### 影像範本 {#image-template}

[Dynamic Media Classic影像範本](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/template-basics/quick-start-template-basics.html#template-basics) 是已匯入至Dynamic Media Classic的分層Photoshop內容，其中內容和屬性已參數化，因而可變。 此 **[!UICONTROL 影像範本]** 元件；您可以在AEM中匯入影像並動態變更文字。 此外，您可以設定 **[!UICONTROL 影像範本]** 元件來使用用戶端內容的值，讓每個使用者以個人化的方式體驗影像。

按一下 **[!UICONTROL 編輯]** 以設定元件。 您可以設定 [所有Dynamic Media Classic元件的共同設定](/help/sites-administering/scene7.md#settingscommontoalldynamicmediaclassicscomponents) 以及本節所述的其他設定。

![chlimage_1-83](assets/chlimage_1-83.png)

**[!UICONTROL 檔案參考、寬度、高度]**  — 請參閱所有Dynamic Media Classic元件的共同設定。

>[!NOTE]
>
>Dynamic Media Classic URL命令和參數無法直接新增至檔案參考URL。 它們只能在 **[!UICONTROL 參數]** 中。

**[!UICONTROL 標題、替代文字]** 在 [!UICONTROL Dynamic Media Classic影像範本] 頁簽，為影像添加標題，並為那些已關閉圖形的用戶添加alt文本。

**[!UICONTROL URL，在中開啟]** 您可以從設定資產以開啟連結。 設定 **[!UICONTROL URL]** 和 **[!UICONTROL 在中開啟]** 指定要在同一窗口中開啟還是在新窗口中開啟。

![chlimage_1-84](assets/chlimage_1-84.png)

**[!UICONTROL 參數面板]** 匯入影像時，參數會預先填入影像的資訊。 如果沒有可動態變更的內容，此視窗為空。

![chlimage_1-85](assets/chlimage_1-85.png)

#### 動態變更文字 {#changing-text-dynamically}

若要動態變更文字，請在欄位中輸入新文字，然後按一下 **[!UICONTROL 確定]**. 在此範例中， **[!UICONTROL 價格]** 現在是50美元，運費是99美分。

![chlimage_1-86](assets/chlimage_1-86.png)

影像中的文字會變更。 您可以按一下「 」，將文字重設回原始值 **[!UICONTROL 重設]** 欄位旁邊。

![chlimage_1-87](assets/chlimage_1-87.png)

#### 更改文本以反映客戶端上下文值的值 {#changing-text-to-reflect-the-value-of-a-client-context-value}

若要將欄位連結至用戶端內容值，請按一下 **[!UICONTROL 選擇]** 要開啟「客戶端 — 上下文」菜單，請選擇「客戶端上下文」，然後按一下 **[!UICONTROL 確定]**. 在此示例中，名稱會根據將名稱與配置檔案中的格式化名稱連結而改變。

![chlimage_1-88](assets/chlimage_1-88.png)

文字會反映目前登入使用者的名稱。 您可以按一下「 」，將文字重設回原始值 **[!UICONTROL 重設]** 欄位旁邊。

![chlimage_1-89](assets/chlimage_1-89.png)

#### 讓Dynamic Media Classic影像範本成為連結 {#making-the-scene-image-template-a-link}

**讓Dynamic Media Classic影像範本成為連結的方式**:

1. 在含有Dynamic Media Classic影像範本元件的頁面上，按一下 **[!UICONTROL 編輯]**.
1. 在 **[!UICONTROL URL]** 欄位中，輸入使用者在點按影像時前往的URL。 在 **[!UICONTROL 在中開啟]** 欄位中，選擇是要開啟目標（新窗口還是同一窗口）。

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. 按一下&#x200B;**[!UICONTROL 「確定」]**。

### 視訊元件 {#video-component}

Dynamic Media Classic **[!UICONTROL 影片]** 元件(可從sidekick的Dynamic Media Classic區段取得)使用裝置和頻寬偵測，將適當的視訊提供給每個畫面。 此元件為HTML5視訊播放器；是可跨頻道使用的單一檢視器。

它可用於最適化視訊集、單一MP4視訊或單一F4V視訊。

請參閱 [影片](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md) 以取得有關視訊如何與Dynamic Media Classic整合搭配運作的詳細資訊。 此外，請參閱 [the **Dynamic Media Classic影片** 元件與基礎 **影片** 元件](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md).

![chlimage_1-91](assets/chlimage_1-91.png)

### 視訊元件的已知限制 {#known-limitations-for-the-video-component}

AdobeDAM和WCM會顯示主視訊是否已上傳。 它們不會顯示這些代理資產：

* Dynamic Media Classic編碼轉譯
* Dynamic Media Classic最適化視訊集

搭配Dynamic Media Classic視訊元件使用最適化視訊集時，您必須調整元件大小以符合視訊的尺寸。

## Dynamic Media Classic內容瀏覽器 {#scene-content-browser}

Dynamic Media Classic內容瀏覽器可讓您直接在AEM中檢視Dynamic Media Classic的內容。 若要存取內容瀏覽器，請在「內容尋找器」中，選取 **[!UICONTROL Dynamic Media Classic]** 在觸控最佳化的使用者介面或 **[!UICONTROL S7]** 圖示。 這兩個使用者介面的功能完全相同。

如果您有多個設定，依預設AEM會顯示 [預設配置](/help/sites-administering/scene7.md#configuring-a-default-configuration). 您可以直接在下拉式功能表的Dynamic Media Classic內容瀏覽器中選取不同的設定。

>[!NOTE]
>
>* 位於臨機資料夾中的資產不會顯示在Dynamic Media Classic內容瀏覽器中。
>* 當 [安全預覽已啟用](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene),Dynamic Media Classic上已發佈和未發佈的資產都會顯示在Dynamic Media Classic內容瀏覽器中。
>* 如果您沒有看到 **[!UICONTROL Dynamic Media Classic]** 或 **[!UICONTROL S7]** 圖示作為內容瀏覽器中的選項，您需要 [設定Dynamic Media Classic以搭配AEM使用](/help/sites-administering/scene7.md).
>
>* 若是影片，Dynamic Media Classic內容瀏覽器支援：
>
>* 最適化視訊集：容器，以便在多個畫面間順暢播放所需的所有視訊轉譯
>* 單MP4視頻
>* 單一F4V影片


### 瀏覽傳統UI中的內容 {#browsing-content-in-the-classic-ui}

按一下 **[!UICONTROL S7]** 標籤。

您可以選取設定，以變更要存取的設定。 資料夾會根據您選取的組態而改變。

![chlimage_1-92](assets/chlimage_1-92.png)

和資產的內容尋找器一樣，您可以搜尋資產並篩選結果。 不過，不同於「資產尋找器」，在 **[!UICONTROL S7]** 頁簽，檔案名 *開頭為* 您輸入的字串，而不是 *包含* 檔案名稱中的關鍵字。

依預設，資產會依檔案名稱顯示。 您也可以依資產類型篩選結果。

>[!NOTE]
>
>若是影片，WCM的Dynamic Media Classic內容瀏覽器支援：
>
>* 最適化視訊集：容器，以便在多個畫面間順暢播放所需的所有視訊轉譯
>* 單MP4視頻
>* 單一F4V影片
>


### 使用內容瀏覽器搜尋Dynamic Media Classic資產 {#searching-for-scene-assets-with-the-content-browser}

搜尋Dynamic Media Classic資產與搜尋AEM資產類似，只是搜尋時，您實際上看到的是Dynamic Media Classic系統中資產的遠端檢視，而非直接匯入AEM。

您可以使用傳統UI或觸控最佳化UI來檢視和搜尋資產。 根據介面，您的搜尋方式會稍有不同。

在任一UI中搜尋時，您可以依下列條件進行篩選（如觸控最佳化UI中的此處所示）:

**[!UICONTROL 輸入關鍵字]**  — 您可以依名稱搜尋資產。 搜尋所輸入的關鍵字時，檔案名稱的開頭為。 例如，輸入&quot;swimming&quot;會尋找任何以該順序字母開頭的資產檔案名稱。 輸入詞語以尋找資產後，請務必按一下「輸入」。

![chlimage_1-93](assets/chlimage_1-93.png)

**[!UICONTROL 資料夾/路徑]**  — 顯示的資料夾名稱取決於您選取的配置。 您可以按一下資料夾圖示並選取子資料夾，然後按一下核取記號以選取，以深入鑽研至較低層級。

如果您輸入關鍵字並選取資料夾，AEM會搜尋該資料夾和任何子資料夾。 不過，如果您在搜尋時未輸入任何關鍵字，選取資料夾只會顯示該資料夾中的資產，且不會包含任何子資料夾。

依預設，AEM會搜尋選取的資料夾和所有子資料夾。

![chlimage_1-94](assets/chlimage_1-94.png)

**[!UICONTROL 資產類型]** 選取Dynamic Media Classic以瀏覽Dynamic Media Classic內容。 只有在您已設定Dynamic Media Classic時，才可使用此選項。

![chlimage_1-95](assets/chlimage_1-95.png)

**[!UICONTROL 設定]** 如果您在中定義了多個Dynamic Media Classic設定 [!UICONTROL Cloud Services]，您可以在此處選取。 因此，資料夾會根據您選擇的設定而變更。

![chlimage_1-96](assets/chlimage_1-96.png)

**[!UICONTROL 資產類型]** 在Dynamic Media Classic瀏覽器中，您可以篩選結果以包含下列任一項目：影像、範本、影片和最適化影片集。 如果您未選取任何資產類型，依預設AEM會搜尋所有資產類型。

![chlimage_1-97](assets/chlimage_1-97.png)

>[!NOTE]
>
>* 搜尋視訊時，會搜尋單一轉譯。 結果返回原始格式副本（僅&amp;ast;.mp4）和編碼格式副本。
>* 搜尋最適化視訊集時，您會搜尋資料夾和所有子資料夾，但僅限於已新增關鍵字至搜尋時。 如果您尚未新增關鍵字，AEM不會搜尋子資料夾。
>


**[!UICONTROL 發佈狀態]** 您可以根據發佈狀態篩選資產： [!UICONTROL 已發佈] 或 [!UICONTROL 未發佈]. 如果您未選取任何 [!UICONTROL 發佈狀態], AEM依預設會搜尋所有發佈狀態。

![chlimage_1-98](assets/chlimage_1-98.png)

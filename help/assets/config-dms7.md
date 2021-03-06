---
title: 設定 Dynamic Media - Scene7 模式
description: 了解如何設定Dynamic Media - Scene7模式。
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: b0f0c6e4-77c8-40db-a9f4-699d1a633571
feature: Configuration,Scene7 Mode
role: Admin,User,Developer
source-git-commit: a750c5425e33c2a115aab581b71862c1d30cf166
workflow-type: tm+mt
source-wordcount: '5589'
ht-degree: 3%

---

# 設定 Dynamic Media - Scene7 模式 {#configuring-dynamic-media-scene-mode}

如果您使用針對不同環境（例如開發、測試和即時生產）設定的Adobe Experience Manager，則必須為每個環境設定Dynamic MediaCloud Services。

## Dynamic Media - Scene7模式的架構圖 {#architecture-diagram-of-dynamic-media-scene-mode}

以下架構圖表說明Dynamic Media - Scene7模式的運作方式。

透過新架構，Experience Manager負責主要資產，並與Dynamic Media同步處理及發佈資產：

1. 主資產上傳至Experience Manager時，會複製至Dynamic Media。 此時，Dynamic Media會處理所有資產處理和轉譯產生，例如影像的視訊編碼和動態變體。
1. 產生轉譯後，Experience Manager可以安全地存取和預覽遠端Dynamic Media轉譯(不會將任何二進位檔傳回至Experience Manager執行個體)。
1. 內容準備好發佈及核准後，就會觸發Dynamic Media服務將內容推送至傳遞伺服器，並在CDN快取內容。

![chlimage_1](assets/chlimage_1.png)

## 在Scene7模式中啟用Dynamic Media {#enabling-dynamic-media-in-scene-mode}

[動態](https://www.adobe.com/solutions/web-experience-management/dynamic-media.html) 媒體預設為停用。若要運用Dynamic Media功能，您必須啟用此功能。

>[!WARNING]
>
>Dynamic Media - Scene7模式僅適用於&#x200B;*Experience Manager製作例項*。 因此，請在「Experience Manager製作」例項上設定`runmode=dynamicmedia_scene7`，而不是&#x200B;*Experience Manager發佈例項。*

若要啟用Dynamic Media，您必須在終端視窗中輸入以下內容，從命令列使用`dynamicmedia_scene7`執行模式啟動Experience Manager（使用的範例埠為4502）:

```shell
java -Xms4096m -Xmx4096m -Doak.queryLimitInMemory=500000 -Doak.queryLimitReads=500000 -jar cq-quickstart-6.4.0.jar -gui -r author,dynamicmedia_scene7 -p 4502
```

## （選用）將Dynamic Media預設集和設定從6.3移轉至6.4零停機時間 {#optional-migrating-dynamic-media-presets-and-configurations-from-to-zero-downtime}

如果您將Experience ManagerDynamic Media從6.3升級至6.4（包括零停機部署功能），請執行下列curl命令，將CRXDE Lite中的所有預設集和設定從`/etc`移轉至`/conf`。

>[!NOTE]
>
>如果您以相容模式運行Experience Manager實例（即安裝了相容性包），則無需運行這些命令。

若要將自訂預設集和設定從`/etc`移轉至`/conf`，請執行下列Linux® curl命令：

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets.migratedmcontent.json`

對於所有升級，無論是否使用相容性包，都可以通過運行以下命令複製現成可用的查看器預設集：

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

## （選用）安裝Feature Pack 18912以移轉大量資產 {#installing-feature-pack}

Feature Pack 18912可讓您透過FTP大量內嵌資產，或在Experience Manager時從Dynamic Media — 混合模式或Dynamic Media Classic移轉至Dynamic Media - Scene7模式。 可從Adobe Professional Services取得。

如需詳細資訊，請參閱[安裝功能套件18912以移轉大量資產](bulk-ingest-migrate.md) 。

## 設定Dynamic MediaCloud Services {#configuring-dynamic-media-cloud-services}

先變更密碼，再設定Dynamic MediaCloud Services。 收到具有Dynamic Media憑證的布建電子郵件後，您必須[登入](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html#system-requirements-dmc-app)至Dynamic Media Classic案頭應用程式，才能變更密碼。 預配電子郵件中提供的密碼是系統生成的，並且僅用於臨時密碼。 請務必更新密碼，以便使用正確的憑證來設定Dynamic MediaCloud Service。

>[!NOTE]
>
>預設情況下，Cloud Services的配置路徑為`/content/dam`。 Dynamic Media - Scene7模式不支援任何其他設定路徑。

**若要設定Dynamic MediaCloud Services:**

1. 在您的「Experience Manager作者」例項中，點選Experience Manager標誌以存取全域導覽主控台，並點選「工具」圖示，然後點選「**[!UICONTROL Cloud Services]** > **[!UICONTROL Dynamic Media設定]**」。
1. 在「 Dynamic Media Configuration Browser」頁面的左窗格中，點選&#x200B;**[!UICONTROL global]**&#x200B;並點選&#x200B;**[!UICONTROL Create]**。 請勿點選或選取[!UICONTROL global]左側的資料夾圖示。
1. 在[!UICONTROL 建立Dynamic Media設定]頁面上，輸入標題、Dynamic Media帳戶電子郵件地址和密碼。 選取您的地區。 此資訊是透過布建電子郵件中的Adobe提供給您的。 如果您未收到電子郵件，請聯絡Adobe客戶支援。

   點選&#x200B;**[!UICONTROL 連線至Dynamic Media]**。

   >[!NOTE]
   >
   >收到包含Dynamic Media憑證的布建電子郵件後，請開啟[Dynamic Media Classic案頭應用程式](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)，然後登入您的公司帳戶以變更密碼。 預配電子郵件中提供的密碼是系統生成的，並且僅用於臨時密碼。 請務必更新密碼，以便使用正確的憑證設定Dynamic MediaCloud Service。

1. 如果連線成功，您也可以設定下列項目：

   * **[!UICONTROL 公司]**  -Dynamic Media帳戶的名稱。您可以為不同的子品牌、部門或不同的測試/生產環境擁有多個Dynamic Media帳戶。
   * **[!UICONTROL 公司根資料夾路徑]**
   * **[!UICONTROL 發佈資產]**  — 選項「立 **** 即」表示資產上傳時，系統會擷取資產並立即提供URL/內嵌。發佈資產不需要使用者干預。 選項&#x200B;**[!UICONTROL 啟用時]**&#x200B;表示您必須先明確發佈資產，才能提供URL/內嵌連結。
   * **[!UICONTROL 安全預覽伺服器]**  — 可讓您指定安全轉譯預覽伺服器的URL路徑。也就是說，產生轉譯後，Experience Manager可以安全地存取和預覽遠端Dynamic Media轉譯(不會將任何二進位檔傳回至Experience Manager執行個體)。

      除非您有使用自己公司的伺服器或特殊伺服器的特殊安排，否則Adobe建議您使用預設設定。
   >[!NOTE]
   >
   >DMS7不支援版本設定。 此外，延遲啟動僅適用於在「編輯動態媒體設定」頁面中的「發佈資產 ********」設定為「啟動時」，然後只適用於在首次啟動資產時。
   >
   >啟動資產後，任何更新都會立即上線發佈至S7傳送。

   ![dynamicmediaconfiguration_updated](assets/dynamicmediaconfiguration2updated.png)

1. 點選&#x200B;**[!UICONTROL 儲存]**。
1. 若要在發佈Dynamic Media內容之前安全地預覽，您必須「允許清單」Experience Manager製作例項，才能連線至Dynamic Media:

   * 開啟[Dynamic Media Classic案頭應用程式](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)，然後登入您的帳戶。 配置時，Adobe提供了您的憑據和登錄詳細資訊。 如果您沒有此資訊，請聯繫技術支援。
   * 在頁面右上角的導覽列中，點選「**[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL Publish Setup]** > **[!UICONTROL Image Server]**」。
   * 在「影像伺服器發佈」頁面的「發佈內容」下拉式清單中，選取「測試影像伺服」**[!UICONTROL 。]**
   * 對於「用戶端位址」篩選器，點選&#x200B;**[!UICONTROL Add]**。
   * 若要啟用（開啟）地址，請選取核取方塊。 輸入Experience Manager製作例項的IP位址（非Dispatcher IP）。
   * 點選&#x200B;**[!UICONTROL 儲存]**。

您現在已完成基本設定；您已準備好使用Dynamic Media - Scene7模式。

如果要進一步自訂配置，您可以選擇完成[（可選）在Dynamic Media - Scene7模式](#optional-configuring-advanced-settings-in-dynamic-media-scene-mode)中配置高級設定下的任何任務。

## （選用）在Dynamic Media - Scene7模式中設定進階設定 {#optional-configuring-advanced-settings-in-dynamic-media-scene-mode}

如果您想進一步自訂Dynamic Media - Scene7模式的設定和設定，或最佳化其效能，您可以完成下列一或多個選用工作：

* [（選用）Dynamic Media - Scene7模式設定的設定與設定](#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings-p)

* [（選用）調整Dynamic Media - Scene7模式的效能](#optional-tuning-the-performance-of-dynamic-media-scene-mode)
* [（選用）篩選復寫資產](#optional-filtering-assets-for-replication)

### （選用）Dynamic Media - Scene7模式設定的設定與設定</p> {#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings-p}

當您處於&#x200B;**dynamicmedia_scene7**&#x200B;執行模式時，請使用Dynamic Media Classic使用者介面來變更Dynamic Media設定。

上述部分工作需要您開啟[Dynamic Media Classic案頭應用程式](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)，然後登入您的帳戶。

設定和設定任務包括：

* [影像伺服器的發佈設定](#publishing-setup-for-image-server)
* [配置應用程式常規設定](#configuring-application-general-settings)
* [配置顏色管理](#configuring-color-management)
* [編輯支援格式的MIME類型](#editing-mime-types-for-supported-formats)
* [為不支援的格式添加MIME類型](#adding-mime-types-for-unsupported-formats)
* [建立批集預設集以自動生成影像集和回轉集](#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)

#### 影像伺服器的發佈設定 {#publishing-setup-for-image-server}

「發佈設定」設定決定預設如何從Dynamic Media傳送資產。 如果未指定任何設定，Dynamic Media會根據「發佈設定」中定義的預設設定來傳送資產。 例如，傳送不包含解析度屬性的影像請求，會產生具有預設物件解析度設定的影像。

若要設定發佈設定：在Dynamic Media Classic中，點選「**[!UICONTROL 設定]** > **[!UICONTROL 應用程式設定]** > **[!UICONTROL 發佈設定]** > **[!UICONTROL 影像伺服器]**」。

「影像伺服器」螢幕建立用於傳送影像的預設設定。 請參閱使用者介面以取得每個設定的說明。

* **[!UICONTROL 請求屬性]**  — 這些設定會限制可從伺服器傳送的影像。
* **[!UICONTROL 預設請求屬性]**  — 這些設定屬於影像的預設外觀。
* **[!UICONTROL 常見縮圖屬性]**  — 這些設定與縮圖影像的預設外觀相關。
* **[!UICONTROL 目錄欄位的預設值]**  — 這些設定與影像的解析度和預設縮圖類型相關。
* **[!UICONTROL 顏色管理屬性]**  — 這些設定將決定要使用的ICC顏色配置檔案。
* **[!UICONTROL 相容性屬性]**  — 此設定可讓文字層中的前導和尾隨段落，如同在3.6版中一樣處理，以提供回溯相容性。
* **[!UICONTROL 本地化支援]**  — 這些設定可讓您管理多個地區設定屬性。它也可讓您指定地區對應字串，以便定義要在檢視器中支援各種工具提示的語言。 有關設定本地化支援的詳細資訊，請參閱[實施本地化支援時的重要注意事項](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/publish-setup.html#image-server)。

#### 配置應用程式常規設定 {#configuring-application-general-settings}

若要開啟「[!UICONTROL 應用程式一般設定]」頁面，請在「Dynamic Media Classic全域導覽列」中，點選「**[!UICONTROL Setup]** > **[!UICONTROL 應用程式設定]** > **[!UICONTROL 一般設定]**」。

**[!UICONTROL 伺服器]**  — 在帳戶布建時，Dynamic Media會自動為您的公司提供指派的伺服器。這些伺服器可用來建構您網站和應用程式的URL字串。 這些URL呼叫是您的帳戶專屬的。 除非Experience Manager支援明確指示，否則請勿更改任何伺服器名稱。

**[!UICONTROL 覆寫影像]**  - Dynamic Media不允許兩個檔案具有相同的名稱。每個項目的URL ID（檔案名稱減去副檔名）必須是唯一的。 這些選項指定如何上傳取代資產：無論是取代原始檔案還是變成重複檔案。 重複資產會以「–1」重新命名（例如chair.tif已重新命名為chair-1.tif）。 這些選項會影響上傳至與原始資料夾不同的資料夾的資產，或副檔名與原始資料夾不同的資產(例如JPG、TIF或PNG)。

* **[!UICONTROL 在目前資料夾中覆寫，使用相同的基本影像名稱/擴充功能]**  — 此選項是最嚴格的取代規則。它要求您將取代影像上傳至與原始影像相同的資料夾，且取代影像的副檔名與原始影像相同。 如果這些需求未達成，則會建立重複項目。

>[!NOTE]
>
>若要與Experience Manager保持一致，請選擇「在當前資料夾中覆蓋」，使用相同的基本映像名稱/副檔名&#x200B;]**。**[!UICONTROL 

* **[!UICONTROL 在任何資料夾中覆寫相同的基本資產名稱/副檔名]**  — 需要取代影像的副檔名與原始影像相同(例如， `chair.jpg` 會 `chair.jpg` 取代而非 `chair.tif`)。不過，您可以將取代影像上傳至與原始影像不同的資料夾。 更新後的影像位於新資料夾中；在檔案的原始位置找不到該檔案。
* **[!UICONTROL 在任何資料夾中覆寫相同的基本資產名稱(不論副檔名為何]** ) — 此選項是包含最多的取代規則。您可以將取代影像上傳至與原始檔案不同的資料夾、以不同副檔名上傳檔案，然後取代原始檔案。 如果原始檔案位於不同的資料夾中，則替換影像位於上載到的新資料夾中。

**[!UICONTROL 預設色彩描述檔]**  — 如需詳細 [資訊，](#configuring-color-management) 請參閱設定色彩管理。

>[!NOTE]
>
>依預設，當您選取「轉譯」時，系統會顯示15個轉譯，當您在資產的詳細資料檢視中選取「檢視器 ******** 」時，系統會顯示15個檢視器預設集。您可以提高此限制。請參閱[增加顯示](managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display)或[的影像預設集數目增加顯示](managing-viewer-presets.md#increasing-the-number-of-viewer-presets-that-display)的檢視器預設集數目。

#### 配置顏色管理 {#configuring-color-management}

動態媒體色彩管理可讓您為資產加上色彩校正。 透過色彩校正，擷取的資產可保留其色彩空間(RGB、CMYK、灰色)和內嵌的色彩設定檔。 當您請求動態格式副本時，將使用CMYK、RGB或灰度輸出將影像顏色更正到目標顏色空間中。 請參閱[設定影像預設集](managing-image-presets.md)。

**要配置預設顏色屬性以在請求影像時啟用顏色校正，請執行以下操作：**

1. 開啟[Dynamic Media Classic案頭應用程式](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)，然後使用布建期間提供的憑證登入您的帳戶。 導覽至&#x200B;**[!UICONTROL Setup]** > **[!UICONTROL 應用程式設定]**。
1. 展開「發 **[!UICONTROL 布設定]** 」區域並選 **[!UICONTROL 取「影像伺服器」]**。設定發 **[!UICONTROL 布例項的預設值]** ，將「發佈內容」設 **** 定為「影像伺服」。
1. 捲動至您必須變更的屬性。 例如， **[!UICONTROL 色彩管理屬性]**&#x200B;區域中的屬性。

   您可以設定下列顏色校正屬性：

   * [!UICONTROL CMYK預設顏色空間]  — 預設CMYK顏色配置檔案的名稱
   * [!UICONTROL 灰階預設顏色空間]  — 預設灰階顏色配置檔案的名稱
   * [!UICONTROL RGB預設顏色空間]  — 預設RGB顏色配置檔案的名稱
   * [!UICONTROL 色彩轉換演算方式]  — 指定演算方式。可接受的值為`perceptual`、`relative` `colometric`、`saturation`和`absolute colometric`。 Adobe建議使用`relative`作為預設值。

1. 點選&#x200B;**[!UICONTROL 儲存]**。

例如，您可以將&#x200B;**[!UICONTROL RGB預設顏色空間]**&#x200B;設定為`sRGB`，將&#x200B;**[!UICONTROL CMYK預設顏色空間]**&#x200B;設定為`WebCoated`。

這麼做會執行下列動作：

* 啟用RGB和CMYK影像的顏色校正。
* 沒有顏色輪廓的RGB影像假定位於`sRGB`顏色空間中。
* 假定沒有顏色輪廓的CMYK影像位於`WebCoated`顏色空間中。
* 傳回RGB輸出的動態轉譯，會在`sRGB`色域中傳回。
* 傳回CMYK輸出的動態轉譯，會在`WebCoated`色域中傳回。

#### 編輯支援格式的MIME類型 {#editing-mime-types-for-supported-formats}

您可以定義由Dynamic Media處理的資產類型，並自訂進階資產處理參數。 例如，您可以指定資產處理參數以執行下列動作：

* 將Adobe PDF轉換為eCatalog資產。
* 將Adobe Photoshop檔案(.PSD)轉換為橫幅範本資產，以便個人化。
* 柵格化Adobe Illustrator檔案(.AI)或Adobe Photoshop封裝的PostScript®檔案(.EPS)。
* [視訊](/help/assets/video-profiles.md) 設定檔 [和](/help/assets/image-profiles.md) 影像設定檔可分別用來定義視訊和影像的處理。

請參閱[上傳資產](managing-assets-touch-ui.md#uploading-assets)。

**要編輯支援格式的mime類型：**

1. 在Experience Manager中，點選Experience Manager標誌以存取全域導覽主控台，然後點選&#x200B;**[!UICONTROL 工具]**（槌子）圖示並導覽至&#x200B;**[!UICONTROL 一般]** > **[!UICONTROL CRXDE Lite]**。
1. 在左側邊欄中，導覽至下列項目：

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

   ![mimetypes](assets/mimetypes.png)

1. 在`mimeTypes`資料夾下，選擇mime類型。
1. 在CRXDE Lite頁面的右側，下方：

   * 連按兩下&#x200B;**[!UICONTROL enabled]**&#x200B;欄位。 依預設，會啟用所有資產mime類型（設為&#x200B;**[!UICONTROL true]**），這表示資產會同步至Dynamic Media以進行處理。 如果您想要排除此資產mime類型，請將此設定變更為&#x200B;**[!UICONTROL false]**。
   * 按兩下&#x200B;**[!UICONTROL jobParam]**&#x200B;以開啟其相關的文字欄位。 如需可用於指定mime類型的允許處理參數值清單，請參閱[支援的Mime類型](assets-formats.md#supported-mime-types)。

1. 執行下列任一操作：

   * 重複步驟3-4以編輯更多mime類型。
   * 在CRXDE Lite頁面的菜單欄上，點選&#x200B;**[!UICONTROL Save All]**。

1. 在頁面的左上角，點選&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;以返回Experience Manager。

#### 為不支援的格式添加自定義MIME類型 {#adding-custom-mime-types-for-unsupported-formats}

您可以針對Experience Manager Assets中不支援的格式新增自訂MIME類型。 若要確保CRXDE Lite未刪除您在Experience Manager中新增的任何新節點，請將MIME類型移至&#x200B;**[!UICONTROL image_]**&#x200B;之前，並將其啟用值設為&#x200B;**[!UICONTROL false]**。

**若要針對不支援的格式新增自訂MIME類型：**

1. 從Experience Manager，按一下「**[!UICONTROL 工具]** > **[!UICONTROL 操作]** > **[!UICONTROL Web控制台]**」。

   ![Web 主控台](assets/2019-08-02_16-13-14.png)

1. 新的瀏覽器頁簽隨即開啟，顯示&#x200B;**[!UICONTROL Adobe Experience Manager Web Console Configuration]**&#x200B;頁面。

   ![Experience ManagerWeb控制台配置](assets/2019-08-02_16-17-29.png)

1. 在頁面上，向下捲動至名稱&#x200B;**[!UICONTROL Adobe CQ Scene7資產MIME類型Service]**。 在名稱的右側，點選「 **[!UICONTROL Edit configuration values]** (pencil icon)(編輯配置值 (鉛筆圖示) 」。

   ![編輯配置值](assets/2019-08-02_16-44-56.png)

1. 在&#x200B;**[!UICONTROL Adobe CQ Scene7資產MIME類型Service]**&#x200B;頁面上，按一下任何加號圖示`+`。 表格中按一下加號以新增mime類型的位置很瑣碎。

   ![加號表徵圖](assets/2019-08-02_16-27-27.png)

1. 在您剛新增的空白文字欄位中輸入`DWG=image/vnd.dwg`。

   範例`DWG=image/vnd.dwg`僅供示範之用。 您在此處新增的MIME類型可能是任何其他不支援的格式。

   ![新增mime類型範例](assets/2019-08-02_16-36-36.png)

1. 在頁面的右下角，按一下&#x200B;**[!UICONTROL Save]**。

   此時，您可以關閉開啟「Adobe Experience Manager Web Console設定」頁面的瀏覽器標籤。

1. 返回具有開啟的Experience Manager控制台的瀏覽器頁簽。

1. 從Experience Manager，按一下「**[!UICONTROL 工具]** > **[!UICONTROL 常規]** > **[!UICONTROL CRXDE Lite]**」。

   ![CRXDE Lite頁面](assets/2019-08-02_16-55-41.png)

1. 在左側邊欄中，導覽至下列項目：

   `conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

1. 拖曳mime類型`image_vnd.dwg`，並將其直接拖曳至樹狀結構中`image_`上方。

   ![拖動mime類型](assets/CRXDELite_CQDOC-14627.png)

1. 在樹中仍選擇MIME類型`image_vnd.dwg`時，從&#x200B;**[!UICONTROL Properties]**&#x200B;頁簽中，在&#x200B;**[!UICONTROL enabled]**&#x200B;行的&#x200B;**[!UICONTROL Value]**&#x200B;列標題下，按兩下值以開啟&#x200B;**[!UICONTROL Value]**&#x200B;下拉清單。

1. 在欄位中輸入`false`（或從下拉式清單中選取`false`）。

   ![False值](assets/2019-08-02_16_60_30.png)

1. 在CRXDE Lite頁面的左上角附近，按一下「**[!UICONTROL 全部保存]**」。

#### 建立批集預設集以自動生成影像集和回轉集 {#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets}

在資產上傳至Dynamic Media時，使用批次集預設集來自動建立影像集或回轉集。

首先，定義資產在集合中分組方式的命名慣例。 然後，您可以建立批集預設集，該預設集是一組唯一命名的、自包含的指令集，該指令集定義如何使用與預設配方中定義的命名慣例相匹配的影像構建該集。

上傳檔案時，Dynamic Media會自動建立一組檔案，其中包含所有符合使用中預設集中所定義命名慣例的檔案。

**配置預設命名**

建立用於任何批集預設配方的預設命名慣例。 批集預設集定義中選定的預設命名慣例可能是貴公司生成批集所需的全部。 系統會建立批集預設集，以使用您定義的預設命名慣例。 如果公司定義的預設命名有例外，您可以建立任意數量的批集預設集，其中包含特定內容集所需的替代自定義命名慣例。

雖然使用批集預設集功能不需要設定預設的命名慣例，但您可以使用它來定義要將命名慣例的多個元素組合在一個集合中。 這樣有助於簡化批集建立。

或者，您可以使用沒有可用表單欄位的&#x200B;**[!UICONTROL 檢視程式碼]**。 在此檢視中，您可以完全使用規則運算式建立命名慣例定義。

有兩個元素可供定義： **[!UICONTROL Match]**&#x200B;和&#x200B;**[!UICONTROL 基本名稱]**。 這些欄位可讓您定義命名約定的所有元素，並識別用於為包含這些元素的集命名的約定的一部分。 公司的個別命名慣例可針對每個元素使用一或多行定義。 使用唯一定義的任意行數，並將它們分組為不同的元素。 例如，「主影像」、「顏色」元素、「替代視圖」元素和「色票」元素。

**配置預設命名：**

1. 開啟[Dynamic Media Classic案頭應用程式](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)，然後登入您的帳戶。

   配置時，Adobe提供了您的憑據和登錄詳細資訊。 如果您沒有此資訊，請聯繫技術支援。

1. 在頁面頂端附近的導覽列中，點選「**[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL Batch Set Presets]** > **[!UICONTROL Default Naming]**」。
1. 選擇 **[!UICONTROL 「查看表單]** 」或「 **[!UICONTROL 查看代碼」]** ，以指定要查看的方式並輸入有關每個元素的資訊。

   您可以選取&#x200B;**[!UICONTROL 檢視程式碼]**&#x200B;核取方塊，檢視建立與表單選取項目一併的規則運算式值。 如果表單視圖因任何原因限制您，則可以輸入或更改這些值，以幫助定義命名約定的元素。 如果無法在表單檢視中剖析您的值，表單欄位就會變成非作用中。

   >[!NOTE]
   >
   >已停用的表單欄位不會執行規則運算式正確無誤的驗證。 您會看到在結果行後面為每個元素建立的規則運算式的結果。 頁面底部會顯示完整的規則運算式。

1. 視需要展開每個元素，並輸入您要使用的命名慣例。
1. 視需要執行下列任一操作：

   * 點選&#x200B;**[!UICONTROL 新增]**&#x200B;以新增元素的其他命名慣例。
   * 點選&#x200B;**[!UICONTROL 移除]**&#x200B;以刪除元素的命名慣例。

1. 執行下列任一操作：

   * 點選&#x200B;**[!UICONTROL 另存新檔]**&#x200B;並輸入預設集的名稱。
   * 如果您正在編輯現有的預設集，請點選「**[!UICONTROL 儲存]**」。

**建立批集預設集**

Dynamic Media使用批次集預設集，將資產組織成影像集（替代影像、顏色選項、360回轉），以便在檢視器中顯示。 批次集預設集會在Dynamic Media中與資產上傳程式一起自動執行。

您可以建立、編輯和管理批集預設集。 有兩種形式的批集預設集定義：一個是您設定的預設命名慣例，另一個是您即時建立的自訂命名慣例。

您可以使用表單欄位方法來定義批次集預設集，或使用程式碼方法來使用規則運算式。 如同在預設命名中，您可以在[!UICONTROL 表單檢視]中定義的同時選擇[!UICONTROL 檢視程式碼]，並使用規則運算式來建立您的定義。 或者，您也可以取消勾選任一個檢視，以專用使用其中一個檢視。

**要建立批集預設集，請執行以下操作：**

1. 開啟[Dynamic Media Classic案頭應用程式](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)，然後登入您的帳戶。

   配置時，Adobe提供了您的憑據和登錄詳細資訊。 如果您沒有此資訊，請聯繫技術支援。

1. 在頁面頂端附近的導航欄上，點選&#x200B;**[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL Batch Set Presets]** > **[!UICONTROL Batch Set Preset]**。

   [!UICONTROL 「檢視表單]」(如「詳細資訊」頁面的右上角所  設定)是預設檢視。

1. 在「預設清單」面板中，點選&#x200B;**[!UICONTROL Add]**&#x200B;以啟用螢幕右側&#x200B;**[!UICONTROL Details]**&#x200B;面板中的定義欄位。
1. 在&#x200B;**[!UICONTROL Details]**&#x200B;面板中，在&#x200B;**[!UICONTROL Preset Name]**&#x200B;欄位中，鍵入預設集的名稱。
1. 在&#x200B;**[!UICONTROL 批集類型]**&#x200B;下拉菜單中，選擇預設類型。
1. 執行下列任一操作：

   * 如果您使用先前在&#x200B;**[!UICONTROL Application Setup]** > **[!UICONTROL Batch Set Presets]** > **[!UICONTROL Default Naming]**&#x200B;下設定的預設命名慣例，請展開&#x200B;**[!UICONTROL Asset Naming Conventions]**，然後在&#x200B;**[!UICONTROL File Naming]**&#x200B;下拉式清單中，點選&#x200B;**[!UICONTROL Default A11/>。]**
   * 若要在設定預設集時定義新的命名慣例&#x200B;**[!UICONTROL 資產命名慣例]**，然後在&#x200B;**[!UICONTROL 檔案命名]**&#x200B;下拉式清單中，點選&#x200B;**[!UICONTROL 自訂]**。

1. 對於[!UICONTROL 序列順序]，定義在將影像集分組後，影像的顯示順序。

   依預設，您的資產依字母順序排列。 不過，您可以使用逗號分隔的規則運算式清單來定義順序。

1. 對於&#x200B;**[!UICONTROL 設定命名]**&#x200B;和&#x200B;**[!UICONTROL 建立約定]**，請在&#x200B;**[!UICONTROL 資產命名約定]**&#x200B;中定義的基礎名稱中指定尾碼或前置詞。 此外，定義在Dynamic Media資料夾結構內建立集的位置。

   如果您定義大量集，請將它們與包含資產本身的資料夾分開。 例如，建立「影像集」資料夾並將生成的集放在此處。

1. 在&#x200B;**[!UICONTROL Details]**&#x200B;面板中，點選&#x200B;**[!UICONTROL Save]**。
1. 點選新預設集名稱旁的&#x200B;**[!UICONTROL 作用中]**。

   啟動預設會確保當您將資產上傳至Dynamic Media時，會套用批次集預設集以產生該集。

**建立批集預設集以自動生成2D回轉集**

您可以使用批集類型&#x200B;**[!UICONTROL 多軸回轉集]**&#x200B;建立自動生成2D回轉集的方式。 影像分組使用「列」和「列」規則運算式，以便在多維度陣列中的對應位置正確對齊影像資產。 在多軸回轉集中，沒有必須具有的最小或最大行數或列數。

例如，假設您要建立名為`spin-2dspin`的多軸回轉集。 您有一組回轉集影像，包含三列，每列12個影像。 這些影像的名稱如下：

```
spin-01-01 
 spin-01-02 
 … 
 spin-01-12 
 spin-02-01 
 … 
 spin-03-12
```

使用此資訊，可以按如下方式建立[!UICONTROL 批集類型]配方：

![chlimage_1-1](assets/chlimage_1-1.png)

對回轉集的共用資產名稱部分進行分組會新增至「**[!UICONTROL 符合]**」欄位（如醒目提示）。 包含行和列的資產名稱的變數部分將分別添加到 **[!UICONTROL 行]** 和 **[!UICONTROL 列欄位中]** 。

上傳和發佈回轉集時，您會啟動&#x200B;**[!UICONTROL 上傳工作選項]**&#x200B;對話方塊中&#x200B;**[!UICONTROL 批次集預設集]**&#x200B;下方所列的2D回轉集方式名稱。

**要為自動生成2D回轉集建立批集預設集，請執行以下操作：**

1. 開啟[Dynamic Media Classic案頭應用程式](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)，然後登入您的帳戶。

   配置時，Adobe提供了您的憑據和登錄詳細資訊。 如果您沒有此資訊，請聯繫技術支援。

1. 在頁面頂端附近的導航欄上，點選&#x200B;**[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL Batch Set Presets]** > **[!UICONTROL Batch Set Preset]**。

   [!UICONTROL 「檢視表單]」(如「詳細資訊」頁面的右上角所  設定)是預設檢視。

1. 在&#x200B;**[!UICONTROL 預設清單]**&#x200B;面板中，點選&#x200B;**[!UICONTROL 新增]**&#x200B;以啟用螢幕右側&#x200B;**[!UICONTROL 詳細資訊]**&#x200B;面板中的定義欄位。
1. 在&#x200B;**[!UICONTROL Details]**&#x200B;面板中，在[!UICONTROL Preset Name]欄位中，鍵入預設集的名稱。
1. 在&#x200B;**[!UICONTROL 批集類型]**&#x200B;下拉菜單中，選擇&#x200B;**[!UICONTROL 資產集]**。
1. 在&#x200B;**[!UICONTROL 子類型]**&#x200B;下拉清單中，選擇&#x200B;**[!UICONTROL 多軸回轉集]**。
1. 展開&#x200B;**[!UICONTROL 資產命名慣例]**，然後在&#x200B;**[!UICONTROL 檔案命名]**&#x200B;下拉式清單中，點選&#x200B;**[!UICONTROL 自訂]**。
1. 使用「 **[!UICONTROL 比對]** 」(Match **[!UICONTROL )和 (可選) 「基本名稱]** 」(Base Name)屬性，定義組成群組之影像資產的命名規則運算式。

   例如，您的常值「比對」規則運算式可能如下所示：

   `(w+)-w+-w+`

1. 展開&#x200B;**[!UICONTROL 行列位置]**，然後定義2D回轉集陣列內影像資產位置的名稱格式。

   使用括弧在檔案名中包含行或列位置。

   例如，對於您的列規則運算式，它可能如下所示：

   `\w+-R([0-9]+)-\w+`

   或

   `\w+-(\d+)-\w+`

   對於欄規則運算式，可能如下所示：

   `\w+-\w+-C([0-9]+)`

   或

   `\w+-\w+-C(\d+)`

   請記住，這些運算式只是示範用途的範例。 您可以建立規則運算式，但需視需要而定。

   >[!NOTE]
   >
   >如果列和列規則運算式的組合無法判斷資產在多維度回轉集陣列內的位置，則不會將該資產新增至該集，且會記錄錯誤。

1. 對於&#x200B;**[!UICONTROL 設定命名]**&#x200B;和&#x200B;**[!UICONTROL 建立約定]**，請在&#x200B;**[!UICONTROL 資產命名約定]**&#x200B;中定義的基礎名稱中指定尾碼或前置詞。

   此外，定義回轉集在Dynamic Media Classic資料夾結構內建立的位置。

   如果您定義大量集，請將它們與包含資產本身的資料夾分開。 例如，建立「回轉集」資料夾，將產生的集放置在此處。

1. 在&#x200B;**[!UICONTROL Details]**&#x200B;面板中，點選&#x200B;**[!UICONTROL Save]**。
1. 點選新預設集名稱旁的&#x200B;**[!UICONTROL 作用中]**。

   啟動預設會確保當您將資產上傳至Dynamic Media時，會套用批次集預設集以產生該集。

### （選用）調整Dynamic Media - Scene7模式的效能 {#optional-tuning-the-performance-of-dynamic-media-scene-mode}

為了讓Dynamic Media - Scene7模式順利執行，Adobe建議使用下列同步效能/可擴充性微調提示：

* 更新預定義的作業參數，以處理不同的檔案格式。
* 更新預先定義的Granite工作流程（視訊資產）佇列背景工作執行緒。
* 更新預先定義的Granite暫時性工作流程（影像和非視訊資產）佇列背景工作執行緒。
* 更新最大上傳連線至Dynamic Media Classic伺服器。

#### 更新預定義的作業參數以處理不同的檔案格式

上傳檔案時，您可以調整工作參數以加快處理速度。 例如，如果您上傳PSD檔案，但不想以範本形式處理，則可將圖層擷取設為false(off)。 在這種情況下，調整的作業參數如下所示：`process=None&createTemplate=false`。

如果您確實要開啟範本建立，請使用下列參數：`process=MaintainLayers&layerNaming=AppendName&createTemplate=true`。

<!-- REMOVED BASED ON CQDOC-17657 You can tune job parameters for faster processing when you upload files. For example, if you are uploading PSD files, but do not want to process them as templates, you can set layer extraction to false (off). In such case, the tuned job parameter would appear as `process=None&createTemplate=false`. -->

Adobe建議對PDF、PostScript®和PSD檔案使用以下「調整」作業參數：

<!-- OLD PDF JOB PARAMETERS `pdfprocess=Rasterize&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` -->

<!-- OLD POSTSCRIPT JOB PARAMETERS `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Rasterize&airesolution=150&aicolorspace=Auto&aialpha=false` -->

| 檔案類型 | 建議的作業參數 |
| ---| ---|
| PDF | `pdfprocess=Thumbnail&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` |
| PostScript® | `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Thumbnail&airesolution=150&aicolorspace=Auto&aialpha=false` |
| PSD | `process=None&layerNaming=AppendName&anchor=Center&createTemplate=false&extractText=false&extendLayers=false` |

<!-- CQDOC-17657 for PSD entry in table above -->

若要更新任何這些參數，請依照[啟用MIME類型型資產/Dynamic Media Classic上傳工作參數support](/help/sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support)中的步驟操作。

#### 更新Granite暫時工作流程佇列 {#updating-the-granite-transient-workflow-queue}

「Granite傳輸工作流程」佇列用於&#x200B;**[!UICONTROL DAM更新資產]**&#x200B;工作流程。 在Dynamic Media中，它用於影像擷取和處理。

**若要更新Granite暫時工作流程佇列：**

1. 導航到[https://&lt;server>/system/console/configMgr](http://localhost:4502/system/console/configMgr)並搜索&#x200B;**[!UICONTROL 隊列：Granite暫時工作流隊列]**。

   >[!NOTE]
   >
   >由於OSGi PID是動態產生的，因此必須進行文字搜尋，而非直接URL。

1. 在&#x200B;**[!UICONTROL 最大並行作業]**&#x200B;欄位中，將數字更改為所需值。

   您可以增加&#x200B;**[!UICONTROL 最大並行作業數]**，以充分支援檔案的大量上傳至Dynamic Media。 確切值取決於硬體容量。 在某些情況下（例如初始移轉或一次性大量上傳），您可以使用大值。 但請注意，使用大值（如內核數的2倍）可能會對其他併發活動產生負面影響。 因此，請根據您的特定使用案例來測試和調整值。

<!--    By default, the maximum number of parallel jobs depends on the number of available CPU cores. For example, on a 4-core server, it assigns 2 worker threads. (A value between 0.0 and 1.0 is ratio based, or any numbers greater than 1 will assign the number of worker threads.)

   Adobe recommends that 32 **[!UICONTROL Maximum Parallel Jobs]** be configured to adequately support heavy upload of files to Dynamic Media Classic. -->

![chlimage_1](assets/chlimage_1.jpeg)

1. 點選&#x200B;**[!UICONTROL 儲存]**。

#### 更新Granite工作流程佇列 {#updating-the-granite-workflow-queue}

Granite工作流程佇列用於非暫時性的工作流程。 在Dynamic Media中，它用於透過&#x200B;**[!UICONTROL Dynamic Media編碼視訊]**&#x200B;工作流程處理視訊。

**若要更新Granite工作流程佇列：**

1. 導覽至`https://<server>/system/console/configMgr`並搜尋&#x200B;**[!UICONTROL 佇列：Granite工作流隊列]**。

   >[!NOTE]
   >
   >由於OSGi PID是動態產生的，因此必須進行文字搜尋，而非直接URL。

1. 在&#x200B;**[!UICONTROL 最大並行作業]**&#x200B;欄位中，將數字更改為所需值。

   預設情況下，並行作業的最大數量取決於可用的CPU核心數。 例如，在4核伺服器上，它分配兩個工作線程。 （介於0.0和1.0之間的值是基於比率的，或者任何大於1的數字都分配工作線程數。）

   對於大多數使用案例，0.5的預設設定已足夠。

   ![chlimage_1-1](assets/chlimage_1-1.jpeg)

1. 點選&#x200B;**[!UICONTROL 儲存]**。

#### 更新Scene7上傳連線 {#updating-the-scene-upload-connection}

Scene7上傳連線設定會將Experience Manager Assets同步至Dynamic Media Classic伺服器。

**若要更新Scene7上傳連線：**

1. 導航到 `https://<server>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl`
1. 在[!UICONTROL 連線數]欄位和/或[!UICONTROL 作用中作業逾時]欄位中，視需要變更數字。

   **[!UICONTROL 連線數]**&#x200B;設定會控制允許Experience Manager至Dynamic Media上傳的HTTP連線數量上限；通常，十個連線的預先定義值就足夠了。

   **[!UICONTROL 作用中工作逾時]**&#x200B;設定決定上傳之Dynamic Media資產在傳送伺服器中發佈的等待時間。 預設情況下，此值為2100秒或35分鐘。

   對於大多數使用案例，2100的設定已足夠。

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

1. 點選&#x200B;**[!UICONTROL 儲存]**。

### （選用）篩選復寫資產 {#optional-filtering-assets-for-replication}

在非Dynamic Media部署中，您會從Experience Manager製作環境復寫&#x200B;*所有*&#x200B;資產（包括影像和視訊）至Experience Manager發佈節點。 此工作流程是必要的，因為Experience Manager發佈伺服器也會傳送資產。

不過，在Dynamic Media部署中，由於資產是透過Cloud Service傳送，因此不需要將這些相同的資產複製到Experience Manager發佈節點。 這樣的「混合發佈」工作流程可避免額外的儲存成本和更長的複製資產處理時間。 其他內容（例如網站頁面）會繼續從「Experience Manager發佈」節點提供。

篩選器可讓您透過&#x200B;*排除*&#x200B;資產，避免複製到Experience Manager發佈節點。

#### 針對復寫使用預設資產篩選器 {#using-default-asset-filters-for-replication}

如果您是使用Dynamic Media進行影像處理、或影片，或兩者皆使用，則可使用Adobe依原樣提供的預設篩選器。 下列篩選器預設為作用中：

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td><strong>篩選</strong></td> 
   <td><strong>Mime 類型</strong></td> 
   <td><strong>轉譯</strong></td> 
  </tr> 
  <tr> 
   <td>Dynamic Media影像傳送</td> 
   <td><p>濾鏡影像</p> <p>篩選集</p> <p> </p> </td> 
   <td><p>開頭為<strong>image/</strong></p> <p>包含<strong>application/</strong>，並以<strong>set</strong>結尾。</p> </td> 
   <td>現成可用的「篩選影像」（套用至單一影像資產，包括互動式影像）和「篩選集」（套用至回轉集、影像集、混合媒體集和轉盤集）將： 
    <ul> 
     <li>從復寫中排除原始影像和靜態影像轉譯。</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Dynamic Media影片傳送</td> 
   <td>filter-video</td> 
   <td>開頭為<strong>video/</strong></td> 
   <td>現成可用的「filter-video」將： 
    <ul> 
     <li>從複製中排除原始視訊和靜態縮圖轉譯。<br /> <br /> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>篩選器會套用至MIME類型，且不能是路徑專屬的。

#### 自訂復寫的資產篩選器 {#customizing-asset-filters-for-replication}

1. 在Experience Manager中，點選Experience Manager標誌以存取全域導覽主控台，並點選&#x200B;**[!UICONTROL 工具]**&#x200B;圖示並導覽至&#x200B;**[!UICONTROL 一般]** > **[!UICONTROL CRXDE Lite]**。
1. 在左側資料夾樹中，導覽至`/etc/replication/agents.author/publish/jcr:content/damRenditionFilters`以檢閱篩選器。

   ![chlimage_1-2](assets/chlimage_1-2.png)

1. 若要定義篩選器的Mime類型，可以按如下方式找到Mime類型：

   在左側邊欄中，展開&#x200B;**[!UICONTROL content]** > **[!UICONTROL dam]** > **[!UICONTROL `locate_your_asset`>]** > **[!UICONTROL jcr:content]** > **[!UICONTROL metadata]**，然後在右側的表格中，找出&#x200B;**[!UICONTROL dc:format]**。

   下圖是資產dc:format路徑的範例。

   ![chlimage_1-3](assets/chlimage_1-3.png)

   請注意，資產`Fiji Red.jpg`的`dc:format`為`image/jpeg`。

   若要讓此篩選器套用至所有影像，而不論其格式為何，請將值設為`image/*`，其中`*`是套用至任何格式之所有影像的規則運算式。

   要讓篩選器僅應用於類型JPEG的影像，請輸入`image/jpeg`值。

1. 定義您要包含或排除在復寫中的轉譯。

   可用於篩選複製的字元包括：

   <table> 
    <tbody> 
    <tr> 
    <td><strong>要使用的字元</strong></td> 
    <td><strong>如何篩選資產以進行復寫</strong></td> 
    </tr> 
    <tr> 
    <td>*</td> 
    <td>通配符<br /> </td> 
    </tr> 
    <tr> 
    <td>+</td> 
    <td>包含復寫資產。</td> 
    </tr> 
    <tr> 
    <td>-</td> 
    <td>排除復寫中的資產。</td> 
    </tr> 
    </tbody> 
   </table>

   導覽至&#x200B;**content/dam/&lt;`locate your asset`>/jcr:content/renditions**。

   下圖是資產轉譯的範例。

   ![chlimage_1-4](assets/chlimage_1-4.png)

   如果只想複製原始檔案，則輸入`+original`。

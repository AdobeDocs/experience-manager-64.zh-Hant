---
title: 設定動態媒體- Scene7模式
seo-title: 設定動態媒體- Scene7模式
description: 有關如何設定動態媒體- Scene7模式的資訊。
seo-description: 有關如何設定動態媒體- Scene7模式的資訊。
uuid: 81cc208b-e95d-4a01-9817-2b6d50cfe8b8
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: cd3adbac-9868-4838-9d8a-37dde8973df4
translation-type: tm+mt
source-git-commit: df92346ca23161b8eaff293a6b9f2c8b7c72e2ec
workflow-type: tm+mt
source-wordcount: '5571'
ht-degree: 3%

---


# 設定動態媒體- Scene7模式{#configuring-dynamic-media-scene-mode}

如果您針對不同環境（例如開發環境、測試環境和即時生產環境）使用Adobe Experience Manager設定，您必須針對每個環境設定Dynamic Media Cloud Services。

## 動態媒體的架構圖- Scene7模式{#architecture-diagram-of-dynamic-media-scene-mode}

以下架構圖說明Dynamic Media - Scene7模式的運作方式。

有了新的架構，AEM負責主要資產並與Dynamic Media同步，以處理和發佈資產：

1. 當主資產上傳至AEM時，它會複製至Dynamic Media。 此時，Dynamic Media會處理所有資產處理和轉譯產生，例如影像的視訊編碼和動態變數。
1. 產生轉譯後，AEM可以安全地存取和預覽遠端的Dynamic Media轉譯（不會將二進位檔傳回至AEM例項）。
1. 內容準備好發佈及核准後，它會觸發Dynamic Media服務將內容推出至傳送伺服器，並在CDN快取內容。

![chlimage_1](assets/chlimage_1.png)

## 在Scene7模式中啟用動態媒體{#enabling-dynamic-media-in-scene-mode}

[動態](https://www.adobe.com/solutions/web-experience-management/dynamic-media.html) 媒體預設為停用。若要運用動態媒體功能，您必須啟用它。

>[!NOTE]
>
>動態媒體- Scene7模式僅適用於AEM Author例項。 因此，您必須在AEM Author例項上設定`runmode=dynamicmedia_scene7`，而非AEM Publish例項。

若要啟用動態媒體，您必須在終端視窗中輸入下列內容，從命令列使用`dynamicmedia_scene7`執行模式啟動AEM（使用的例如連接埠為4502）:

```shell
java -Xms4096m -Xmx4096m -Doak.queryLimitInMemory=500000 -Doak.queryLimitReads=500000 -jar cq-quickstart-6.4.0.jar -gui -r author,dynamicmedia_scene7 -p 4502
```

## （可選）將動態媒體預設集和組態從6.3移轉至6.4零停機時間{#optional-migrating-dynamic-media-presets-and-configurations-from-to-zero-downtime}

如果您要將AEM Dynamic Media從6.3升級至6.4（現在包含零停機部署的功能），您必須執行下列curl命令，才能將CRXDE Lite中的所有預設集和組態從`/etc`移轉至`/conf`。

>[!NOTE]
>
>如果您以相容模式執行AEM例項（即，您已安裝相容性封裝），就不需要執行這些命令。

要將自定義預設集和配置從`/etc`遷移到`/conf`，請運行以下Linux curl命令：

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets.migratedmcontent.json`

對於所有升級，不論是否使用相容性套件，您都可以執行下列命令來複製現成可用的檢視器預設集：

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

## （可選）安裝功能套件18912以進行大量資產移轉{#installing-feature-pack}

功能套件18912可讓您透過FTP大量收錄資產，或從Dynamic Media - Hybrid模式或Dynamic Media Classic移轉資產至AEM的Dynamic Media - Scene7模式。 您可從Adobe專業服務取得。

如需詳細資訊，請參閱[安裝功能套件18912以進行大量資產移轉](bulk-ingest-migrate.md)。

## 設定動態媒體雲端服務{#configuring-dynamic-media-cloud-services}

在您設定Dynamic Media Cloud服務之前，請變更密碼。 在您收到具有動態媒體憑證的布建電子郵件後，您必須[登入](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)至Dynamic Media Classic以變更密碼。 提供電子郵件中提供的密碼是系統生成的，並僅用於臨時密碼。 請務必更新密碼，以便使用正確的認證來設定Dynamic Media Cloud Service。

>[!NOTE]
>
>根據預設，雲端服務的設定路徑為`/content/dam`。 任何其他設定路徑都不受Dynamic Media - Scene7模式支援。

若要設定Dynamic Media Cloud服務：

1. 在AEM中，點選AEM標誌以存取全域導覽主控台，然後點選「工具」圖示，然後點選「**[!UICONTROL 雲端服務>動態媒體設定」]**。
1. 在「動態媒體設定瀏覽器」頁面的左窗格中，點選&#x200B;**[!UICONTROL global]**&#x200B;並點選&#x200B;**[!UICONTROL Create]**。 請勿點選或選取[!UICONTROL global]左側的資料夾圖示。
1. 在[!UICONTROL 建立動態媒體設定]頁面上，輸入標題、動態媒體帳戶電子郵件地址、密碼，然後選取您的地區。 Adobe會在布建電子郵件中提供給您。 如果您未收到此訊息，請聯絡支援。

   點選&#x200B;**[!UICONTROL 連線至動態媒體]**。

   >[!NOTE]
   >
   >在您收到具有動態媒體憑證的布建電子郵件後，請[登入](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) Dynamic Media Classic以變更密碼。 提供電子郵件中提供的密碼是系統生成的，並僅用於臨時密碼。 請務必更新密碼，以便使用正確的認證來設定Dynamic Media Cloud服務。

1. 如果連接成功，您還可以設定以下內容：

   * **[!UICONTROL 公司]** -動態媒體帳戶的名稱。您可能會針對不同子品牌、部門或不同的測試／生產環境擁有多個動態媒體帳戶。
   * **[!UICONTROL 公司根資料夾路徑]**
   * **[!UICONTROL 發佈資產]** -選項「立 **** 即」意指當資產上傳時，系統會收錄資產並立即提供URL/內嵌。發佈資產不需要使用者干預。 「啟動時」選項&#x200B;**[!UICONTROL 表示您必須先明確發佈資產，才能提供URL/內嵌連結。]**
   * **[!UICONTROL 安全預覽伺服器]** -可讓您指定安全轉譯預覽伺服器的URL路徑。也就是說，在產生轉譯後，AEM可以安全地存取和預覽遠端的「動態媒體」轉譯（不會將二進位檔傳回至AEM例項）。

      除非您有特殊安排可使用您公司的伺服器或特殊伺服器，否則Adobe建議您使用預設設定。
   >[!NOTE]
   >
   >DMS7中不支援版本修訂。 此外，延遲啟動僅適用於在「編輯動態媒體設定」頁面中的「發佈資產 ********」設定為「啟動時」，然後只適用於在首次啟動資產時。
   >
   >啟動資產後，任何更新都會立即即時發佈至S7傳送。

   ![dynamicmediaconfiguration2更新](assets/dynamicmediaconfiguration2updated.png)

1. 點選&#x200B;**[!UICONTROL Save]**。
1. 若要在動態媒體內容發佈之前安全地預覽，您必須「允許列出」AEM作者例項，才能連線至動態媒體：

   * 登入您的Dynamic Media Classic帳戶：[https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)。 您的認證和登入是在布建時由Adobe提供。 如果您沒有此資訊，請聯絡技術支援。
   * 在頁面右上角的導覽列上，點選「**[!UICONTROL 設定>應用程式設定>發佈設定>影像伺服器」]**。
   * 在「影像伺服器發佈」頁面的「發佈內容」下拉式清單中，選取「測試影像伺服」**[!UICONTROL 。]**
   * 對於「Client Address Filter」（客戶端地址過濾器），請按一下「Add **[!UICONTROL （添加]**）」。
   * 選取核取方塊以啟用（開啟）此位址，然後輸入AEM Author例項的IP位址（而非Dispatcher IP）。
   * 點選&#x200B;**[!UICONTROL Save]**。

您現在已完成基本配置；您已準備好使用Dynamic Media - Scene7模式。

如果您想進一步自訂配置，可以選擇性地完成[（選用）在動態媒體- Scene7模式中設定進階設定下的任何工作。](#optional-configuring-advanced-settings-in-dynamic-media-scene-mode)

## （可選）在動態媒體中設定進階設定- Scene7模式{#optional-configuring-advanced-settings-in-dynamic-media-scene-mode}

如果您想要進一步自訂動態媒體- Scene7模式的設定和設定，或最佳化其效能，則可以完成下列一或多項選用工作：

* [（選用）動態媒體的設定與設定- Scene7模式設定](#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings-p)

* [（可選）調整動態媒體- Scene7模式的效能](#optional-tuning-the-performance-of-dynamic-media-scene-mode)
* [（可選）篩選複製資產](#optional-filtering-assets-for-replication)

### （選用）動態媒體的設定與設定- Scene7模式設定</p> {#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings-p}

當您處於執行模式&#x200B;**dynamicmedia_scene7**&#x200B;時，您會使用Dynamic Media Classic(Scene7)使用者介面來變更動態媒體設定。

上述部分工作需要您在以下網址登入Dynamic Media Classic:[https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

設定和配置任務包括：

* [影像伺服器的發佈設定](#publishing-setup-for-image-server)
* [配置應用程式常規設定](#configuring-application-general-settings)
* [設定色彩管理](#configuring-color-management)
* [編輯支援格式的MIME類型](#editing-mime-types-for-supported-formats)
* [為不支援的格式添加MIME類型](#adding-mime-types-for-unsupported-formats)
* [建立批次集預設集以自動產生影像集和回轉集](#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)

#### 影像伺服器{#publishing-setup-for-image-server}的發佈設定

「發佈設定」設定會決定預設如何從動態媒體傳送資產。 如果未指定任何設定，動態媒體會根據發佈設定中定義的預設設定來傳送資產。 例如，傳送不含解析度屬性的影像請求，會產生具有「預設物件解析度」設定的影像。

若要設定發佈設定：在Dynamic Media Classic中，點選「**[!UICONTROL 設定>應用程式設定>發佈設定>影像伺服器」。]**

「影像伺服器」畫面會建立傳送影像的預設設定。 請參閱使用者介面以取得每個設定的說明。

* **[!UICONTROL 請求屬性]** -這些設定會限制從伺服器傳送的影像。
* **[!UICONTROL 預設請求屬性]** -這些設定屬於影像的預設外觀。
* **[!UICONTROL 常用縮圖屬性]** -這些設定屬於縮圖影像的預設外觀。
* **[!UICONTROL 目錄欄位的預設值]** -這些設定與影像的解析度和預設縮略圖類型相關。
* **[!UICONTROL 色彩管理屬性]** -這些設定會決定使用哪些ICC色彩描述檔。
* **[!UICONTROL 相容性屬性]** -此設定可讓文字圖層中的前導和尾隨段落視為3.6版中的段落，以提供回溯相容性。
* **[!UICONTROL 本地化支援]** -這些設定可讓您管理多個地區設定屬性。它也可讓您指定地區對應字串，以便定義您要在檢視器中支援哪些語言。 有關設定本地化支援的詳細資訊，請參閱[設定資產本地化時的注意事項](https://help.adobe.com/en_US/scene7/using/WS997f1dc4cb0179f034e07dc31412799d19a-8000.html)。

#### 配置應用程式常規設定{#configuring-application-general-settings}

若要開啟「[!UICONTROL 應用程式一般設定]」頁面，請在「動態媒體經典全域導覽列」中，點選「**[!UICONTROL 設定>應用程式設定>一般設定]**」。

**[!UICONTROL 伺服器]** -在帳戶布建時，動態媒體會自動為您的公司提供指派的伺服器。這些伺服器可用來建構網站和應用程式的URL字串。 這些URL呼叫是您帳戶專屬的。 除非AEM支援明確指示，否則請勿變更任何伺服器名稱。

**[!UICONTROL 覆寫影像]** -動態媒體不允許兩個檔案具有相同名稱。每個項目的URL ID（檔案名稱減去副檔名）必須是唯一的。 這些選項指定如何上傳取代資產：不論是替換原稿還是變成重複。 重複資產會以&quot;-1&quot;（例如chair.tif會更名為chair-1.tif）重新命名。 這些選項會影響上傳至原始檔案夾以外的資產，或是副檔名與原始檔案不同的資產（例如JPG、TIF或PNG）。

* **[!UICONTROL 在目前資料夾中覆寫相同的基本影像名稱／副檔名]** -此選項是最嚴格的取代規則。它要求您將取代影像上傳至與原始影像相同的檔案夾，而取代影像的副檔名與原始影像的副檔名相同。 如果這些需求未達成，則會建立復本。

>[!NOTE]
>
>若要與AEM保持一致，請選取「覆寫目前檔案夾中的基本影像名稱／副檔名&#x200B;**[!UICONTROL 」。]**

* **[!UICONTROL 在任何資料夾中覆寫相同的基本資產名稱／副檔名]** -要求取代影像的副檔名與原始影像相同(例如， `chair.jpg` 取代 `chair.jpg` 而非 `chair.tif`)。不過，您可以將取代影像上傳至原始檔案夾以外的其他檔案夾。 更新後的影像位於新資料夾中；在檔案的原始位置中無法再找到該檔案。
* **[!UICONTROL 在任何資料夾中覆寫相同的基本資產名稱(不論副檔名為何]** )-此選項是最包含的取代規則。您可以將取代影像上傳至原始檔案夾以外的其他檔案夾、以不同副檔名上傳檔案，並取代原始檔案。 如果原始檔案位於不同的檔案夾中，則取代影像會位於上傳檔案的新檔案夾中。

**[!UICONTROL 預設色彩描述檔]** -如需詳細 [資訊，](#configuring-color-management) 請參閱設定色彩管理。

>[!NOTE]
>
>依預設，當您選取「轉譯」時，系統會顯示15個轉譯，當您在資產的詳細資料檢視中選取「檢視器 ******** 」時，系統會顯示15個檢視器預設集。您可以提高此限制。請參閱[增加顯示](managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display)或[的影像預設集數目增加顯示](managing-viewer-presets.md#increasing-the-number-of-viewer-presets-that-display)的檢視器預設集數目。

#### 配置色彩管理{#configuring-color-management}

動態媒體色彩管理可讓您為正確的資產加上色彩。 透過色彩校正，收錄的資產會保留其色域（RGB、CMYK、灰色）和內嵌的色彩描述檔。 當您請求動態轉譯時，會使用CMYK、RGB或「灰色」輸出，將影像色彩校正為目標色域。 請參閱[設定影像預設集](managing-image-presets.md)。

若要設定預設顏色屬性，以在請求影像時啟用色彩校正：

1. [使用布建期間提供](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) 的憑證登入動態媒體類別。導覽至「**[!UICONTROL 設定>應用程式設定]**」。
1. 展開「發 **[!UICONTROL 布設定]** 」區域並選 **[!UICONTROL 取「影像伺服器」]**。設定發 **[!UICONTROL 布例項的預設值]** ，將「發佈內容」設 **** 定為「影像伺服」。
1. 捲動至您需要變更的屬性，例如&#x200B;**[!UICONTROL 色彩管理屬性]**&#x200B;區域中的屬性。

   您可以設定下列色彩校正屬性：

   * [!UICONTROL CMYK預設色域] -預設CMYK色彩描述檔的名稱
   * [!UICONTROL 灰階預設色域] -預設灰階色彩描述檔的名稱
   * [!UICONTROL RGB預設色域] -預設RGB色彩描述檔的名稱
   * [!UICONTROL 顏色轉換渲染方式] -指定渲染方式。可接受的值為`perceptual`、`relative`、`colometric`、`saturation`和`absolute colometric`。 Adobe建議預設值為`relative`。

1. 點選&#x200B;**[!UICONTROL Save]**。

例如，您可以將「**[!UICONTROL RGB預設色域]**」設為「`sRGB`」，並將「CMYK預設色域&#x200B;]**」設為「`WebCoated`」。**[!UICONTROL 

這麼做會執行下列動作：

* 啟用RGB和CMYK影像的色彩校正。
* 沒有色彩描述檔的RGB影像會假設在`sRGB`色域中。
* 沒有色彩描述檔的CMYK影像會假設在`WebCoated`色域中。
* 傳回RGB輸出的動態轉譯，會在`sRGB`色域中傳回。
* 傳回CMYK輸出的動態轉譯，會在`WebCoated`色域中傳回它。

#### 編輯支援格式{#editing-mime-types-for-supported-formats}的MIME類型

您可以定義Dynamic Media應處理哪些資產類型，並自訂進階資產處理參數。 例如，您可以指定資產處理參數以執行下列作業：

* 將Adobe PDF轉換為eCatalog資產。
* 將Adobe Photoshop檔案(.PSD)轉換為橫幅範本資產，以利個人化。
* 點陣化Adobe Illustrator檔案(.AI)或Adobe Photoshop封裝的Postscript檔案(.EPS)。
* [視訊](/help/assets/video-profiles.md) 描述檔 [和影](/help/assets/image-profiles.md) 像描述檔可分別用來定義視訊和影像的處理。

請參閱[上傳資產](managing-assets-touch-ui.md#uploading-assets)。

**若要編輯支援格式的MIME類型**

1. 在AEM中，點選AEM標誌以存取全域導覽主控台，然後點選「工具&#x200B;****（槌子）」圖示並導覽至「一般> CRXDE Lite ]**」。**[!UICONTROL 
1. 在左側導軌中，導覽至下列項目：

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

   ![mimetypes](assets/mimetypes.png)

1. 在`mimeTypes`資料夾下，選取MIME類型。
1. 在CRXDE Lite頁面的右側，位於下方：

   * 按兩下&#x200B;**[!UICONTROL enabled]**&#x200B;欄位。 依預設會啟用所有資產MIME類型（設為&#x200B;**[!UICONTROL true]**），這表示資產將同步至動態媒體以進行處理。 如果您不想處理此資產MIME類型，請將此設定變更為&#x200B;**[!UICONTROL false]**。
   * 連按兩下&#x200B;**[!UICONTROL jobParam]**&#x200B;以開啟其相關的文字欄位。 有關允許的處理參數值清單，請參見[支援的Mime類型](assets-formats.md#supported-mime-types) ，您可以用於給定的MIME類型。

1. 執行下列任一項作業：

   * 重複步驟3-4以編輯其他MIME類型。
   * 在「CRXDE Lite」頁面的菜單欄上，按一下&#x200B;**[!UICONTROL 全部保存]**。

1. 在頁面的左上角，點選&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;以返回AEM。

#### 為不支援的格式添加自定義MIME類型{#adding-custom-mime-types-for-unsupported-formats}

您可以針對AEM Assets中不支援的格式新增自訂MIME類型。為確保AEM不會刪除您在CRXDE Lite中新增的任何新節點，您必須確定您在&#x200B;**[!UICONTROL image_]**&#x200B;之前移動MIME類型，且其啟用值設定為&#x200B;**[!UICONTROL false]**。

**要為不支援的格式添加自定義MIME類型**

1. 在AEM中，按一下「工具>作業> Web Console ]**」。**[!UICONTROL 

   ![網路主控台](assets/2019-08-02_16-13-14.png)

1. 新的瀏覽器標籤會開啟至&#x200B;**[!UICONTROL Adobe Experience Manager Web Console Configuration]**&#x200B;頁面。

   ![網路主控台](assets/2019-08-02_16-17-29.png)

1. 在頁面上，向下捲動至名稱&#x200B;**[!UICONTROL Adobe CQ Scene7 Asset MIME類型Service]**。 在名稱的右側，點選「 **[!UICONTROL Edit configuration values]** (pencil icon)(編輯配置值 (鉛筆圖示) 」。

   ![編輯](assets/2019-08-02_16-44-56.png)

1. 在&#x200B;**[!UICONTROL Adobe CQ Scene7 Asset MIME類型服務]**&#x200B;頁面上，按一下任何加號圖示`+`。 在表格中，您按一下加號以新增MIME類型的位置微不足道。

   ![plussign](assets/2019-08-02_16-27-27.png)

1. 在您剛新增的空白文字欄位中鍵入`DWG=image/vnd.dwg`。

   請注意，範例`DWG=image/vnd.dwg`僅供圖例之用。 您在此處添加的MIME類型可以是任何其他不支援的格式。

   ![dwg](assets/2019-08-02_16-36-36.png)

1. 在頁面的右下角，按一下&#x200B;**[!UICONTROL 保存]**。

   此時，您可以關閉已開啟「Adobe Experience Manager Web Console設定」頁面的瀏覽器標籤。

1. 返回開啟AEM主控台的瀏覽器標籤。

1. 在AEM中，按一下「工具>一般> CRXDE Lite ]**」。**[!UICONTROL 

   ![crxdelite](assets/2019-08-02_16-55-41.png)

1. 在左側導軌中，導覽至下列項目：

   `conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

1. 拖曳MIME類型`image_vnd.dwg`，並將它直接放在樹狀結構中的`image_`上方。

   ![拖曳](assets/CRXDELite_CQDOC-14627.png)

1. 在樹中仍選擇MIME類型`image_vnd.dwg`的&#x200B;**[!UICONTROL 屬性]**&#x200B;標籤中，在&#x200B;**[!UICONTROL enabled]**&#x200B;行的&#x200B;**[!UICONTROL 值]**&#x200B;列標題下，按兩下該值以開啟&#x200B;**[!UICONTROL 值]**&#x200B;下拉清單。

1. 在欄位中鍵入`false`（或從下拉式清單中選取`false`）。

   ![虛值](assets/2019-08-02_16_60_30.png)

1. 在「CRXDE Lite」頁面的左上角附近，按一下「全部儲存」。]****[!UICONTROL 

#### 建立批次集預設集以自動產生影像集和回轉集{#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets}

使用批次集預設集，在資產上傳至動態媒體時，自動建立影像集或回轉集。

首先，定義資產在一組資產中如何分組的命名慣例。 然後，您可以建立批集預設集，該預設集是一組唯一命名的自含指令，定義如何使用符合預設配方中定義之命名慣例的影像來建構該預設集。

當您上傳檔案時，動態媒體會自動建立一組檔案，其中所有檔案都符合作用中預設集中定義的命名慣例。

**配置預設命名**

建立用於任何批集預設方式的預設命名慣例。 批集預設定義中選取的預設命名慣例可能是您公司需要的所有批次產生集。 系統會建立批集預設，以使用您定義的預設命名慣例。 在公司定義的預設命名有例外的情況下，您可以針對特定內容集建立任意數量的批集預設集，其中包含所需的替代自訂命名慣例。

雖然設定預設命名慣例並不需要使用批次集預設功能，但最佳實務建議您使用預設命名慣例來定義您想要在某個集合中分組的命名慣例元素數目，以便簡化批次集的建立。

另外，請注意，您可以使用沒有表格欄位的「檢視程式碼」。 ]****[!UICONTROL &#x200B;在此視圖中，您完全使用規則運算式建立命名約定定義。

定義時可使用兩個元素：**[!UICONTROL Match]**&#x200B;和&#x200B;**[!UICONTROL Base Name]**。 這些欄位可讓您定義命名約定的所有元素，並識別用於命名包含這些元素的集合的約定部分。 公司的個別命名慣例可能會針對每個元素使用一或多行定義。 您可以使用任意多行來定義獨特元素，並將它們分組為不同的元素，例如主影像、顏色元素、替代檢視元素和色票元素。

**要配置預設命名：**

1. 登入您的Dynamic Media Classic(Scene7)帳戶：[www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   您的認證和登入是在布建時由Adobe提供。 如果您沒有此資訊，請聯絡技術支援。

1. 在頁面頂部附近的導覽列上，點選「**[!UICONTROL 設定>應用程式設定>批次集預設集>預設命名]」。**
1. 選擇 **[!UICONTROL 「查看表單]** 」或「 **[!UICONTROL 查看代碼」]** ，以指定要查看的方式並輸入有關每個元素的資訊。

   您可以選取「檢視程式碼」核取方塊，檢視表格選擇旁邊建立的規則運算式值。 ****&#x200B;如果表單視圖因任何原因限制您，您可以輸入或更改這些值，以幫助定義命名約定的元素。 如果無法在表單檢視中解析您的值，表單欄位會變為非作用中。

   >[!NOTE]
   >
   >取消啟用的表單欄位不會驗證規則運算式是否正確。 在「結果」(Result)行後，您會看到每個元素所建立的規則運算式的結果。 完整的規則運算式會顯示在頁面底部。

1. 視需要展開每個元素，並輸入您要使用的命名慣例。
1. 視需要執行下列任一操作：

   * 點選「**[!UICONTROL 新增]**」，新增元素的其他命名慣例。
   * 點選&#x200B;**[!UICONTROL Remove]**&#x200B;可刪除元素的命名慣例。

1. 執行下列任一項作業：

   * 點選&#x200B;**[!UICONTROL 另存新檔]**&#x200B;並輸入預設集的名稱。
   * 如果您正在編輯現有預設集，請點選「**[!UICONTROL 儲存]**」。

**建立批集預設集**

動態媒體使用批次集預設集將資產組織成一組影像（替代影像、顏色選項、360回轉），以便在檢視器中顯示。 批次集預設集會自動在動態媒體中與資產上傳程式一起執行。

您可以建立、編輯和管理批次集預設集。 批集預設定義有兩種形式：一個代表您可能已設定的預設命名慣例，另一個代表您即時建立的自訂命名慣例。

您可以使用表單欄位方法來定義批次集預設集，或使用程式碼方法來使用規則運算式。 如同在預設命名中，您可以在[!UICONTROL 表單檢視]中定義的同時選擇[!UICONTROL 檢視程式碼]，並使用規則運算式來建立定義。 或者，您可以取消選中任一視圖以獨佔使用一個視圖或另一個視圖。

**要建立批集預設集，請執行以下操作：**

1. 登入您的Dynamic Media Classic(Scene7)帳戶：[www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   您的認證和登入是在布建時由Adobe提供。 如果您沒有此資訊，請聯絡技術支援。

1. 在頁面頂部附近的導覽列上，點選「**[!UICONTROL 設定>應用程式設定>批次集預設集>批次集預設集」。**]

   請注意，[!UICONTROL View Form]（如[!UICONTROL Details]頁面右上角所設定）是預設檢視。

1. 在「預設集清單」面板中，點選&#x200B;**[!UICONTROL Add]**&#x200B;以啟用畫面右側&#x200B;**[!UICONTROL Details]**&#x200B;面板中的定義欄位。
1. 在&#x200B;**[!UICONTROL Details]**&#x200B;面板中的&#x200B;**[!UICONTROL Preset Name]**&#x200B;欄位中，輸入預設的名稱。
1. 在&#x200B;**[!UICONTROL 批集類型]**&#x200B;下拉菜單中，選擇預設類型。
1. 執行下列任一項作業：

   * 如果您使用先前在&#x200B;**[!UICONTROL 應用程式設定>批次集預設集>預設命名]**&#x200B;下設定的預設命名慣例，請展開&#x200B;**[!UICONTROL 資產命名慣例]**，然後在&#x200B;**[!UICONTROL 檔案命名]**&#x200B;下拉式清單中，點選&#x200B;**[!UICONTROL 預設]**。
   * 若要在設定預設集&#x200B;**[!UICONTROL 資產命名慣例]**&#x200B;時定義新的命名慣例，然後在&#x200B;**[!UICONTROL 檔案命名]**&#x200B;下拉式清單中，點選&#x200B;**[!UICONTROL 自訂]**。

1. 對於[!UICONTROL 順序]，定義在動態媒體中將影像組合在一起後，影像顯示的順序。

   依預設，資產會以英數字元排序。 不過，您可以使用逗號分隔的規則運算式清單來定義順序。

1. 對於&#x200B;**[!UICONTROL 設定命名]**&#x200B;和&#x200B;**[!UICONTROL 建立慣例]**，請在&#x200B;**[!UICONTROL 資產命名慣例]**&#x200B;中定義的基本名稱中指定尾碼或前置詞。 此外，定義在「動態媒體」檔案夾結構中建立集合的位置。

   如果您定義大量集合，您可能偏好將這些集合與包含資產本身的資料夾分開。 例如，您可以建立「影像集」檔案夾，並將產生的集放在此處。

1. 在&#x200B;**[!UICONTROL Details]**&#x200B;面板中，點選&#x200B;**[!UICONTROL Save]**。
1. 點選新預設集名稱旁的&#x200B;**[!UICONTROL Active]**。

   啟動預設可確保在您上傳資產至動態媒體時，會套用批次集預設集以產生該預設集。

**為自動生成2D回轉集建立批集預設集**

您可以使用批集類型&#x200B;**[!UICONTROL 多軸回轉集]**&#x200B;建立自動生成2D回轉集的方式。 影像群組使用「列」和「欄」規則運算式，讓影像資產在多維度陣列的對應位置中正確對齊。 在多軸回轉集中，沒有必須具有的最小或最大行數或列數。

例如，假設您要建立名為`spin-2dspin`的多軸回轉集。 您有一組回轉集影像，包含三列，每列12個影像。 這些影像的命名如下：

```
spin-01-01 
 spin-01-02 
 … 
 spin-01-12 
 spin-02-01 
 … 
 spin-03-12
```

使用此資訊，可以建立[!UICONTROL 批集類型]配方，如下所示：

![chlimage_1-1](assets/chlimage_1-1.png)

對spinset的共用資產名稱部分進行分組將添加到「匹 **[!UICONTROL 配]** 」欄位 (如突出顯示)。包含行和列的資產名稱的變數部分將分別添加到 **[!UICONTROL 行]** 和 **[!UICONTROL 列欄位中]** 。

上傳和發佈回轉集時，您會啟用2D回轉集配方的名稱，該配方會列在&#x200B;**[!UICONTROL 上傳工作選項]**&#x200B;對話方塊的&#x200B;**[!UICONTROL 批次集預設集]**&#x200B;下。

**要為自動生成2D回轉集建立批集預設，請執行以下操作：**

1. 登入您的Dynamic Media Classic(Scene7)帳戶：[https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   您的認證和登入是在布建時由Adobe提供。 如果您沒有此資訊，請聯絡技術支援。

1. 在頁面頂部附近的導覽列上，點選「**[!UICONTROL 設定>應用程式設定>批次集預設集>批次集預設集]**」。

   請注意，[!UICONTROL View Form]（如[!UICONTROL Details]頁面右上角所設定）是預設檢視。

1. 在&#x200B;**[!UICONTROL 預設清單]**&#x200B;面板中，點選&#x200B;**[!UICONTROL 新增]**&#x200B;以啟用畫面右側&#x200B;**[!UICONTROL 詳細資料]**&#x200B;面板中的定義欄位。
1. 在&#x200B;**[!UICONTROL Details]**&#x200B;面板中的[!UICONTROL Preset Name]欄位中，輸入預設的名稱。
1. 在&#x200B;**[!UICONTROL 批集類型]**&#x200B;下拉菜單中，選擇&#x200B;**[!UICONTROL 資產集]**。
1. 在&#x200B;**[!UICONTROL 子類型]**&#x200B;下拉清單中，選擇&#x200B;**[!UICONTROL 多軸回轉集]**。
1. 展開&#x200B;**[!UICONTROL 資產命名慣例]**，然後在&#x200B;**[!UICONTROL 檔案命名]**&#x200B;下拉式清單中，點選&#x200B;**[!UICONTROL 自訂]**。
1. 使用「 **[!UICONTROL 比對]** 」(Match **[!UICONTROL )和 (可選) 「基本名稱]** 」(Base Name)屬性，定義組成群組之影像資產的命名規則運算式。

   例如，您的常值「符合」規則運算式可能如下所示：

   `(w+)-w+-w+`

1. 展開&#x200B;**[!UICONTROL 列位置]**，然後定義2D回轉集陣列中影像資產位置的名稱格式。

   使用括弧在檔案名中包住行或列位置。

   例如，對於行規則運算式，它可能如下所示：

   `\w+-R([0-9]+)-\w+`

   或

   `\w+-(\d+)-\w+`

   對於欄規則運算式，可能如下所示：

   `\w+-\w+-C([0-9]+)`

   或

   `\w+-\w+-C(\d+)`

   請記住，這些只是範例。 您可以建立您的規則運算式，但是您想要符合自己的需求。

   >[!NOTE]
   >
   >如果行和列規則表達式的組合無法確定資產在多維旋轉集陣列中的位置，則不會將該資產添加到該集，並記錄錯誤。

1. 對於&#x200B;**[!UICONTROL 設定命名]**&#x200B;和&#x200B;**[!UICONTROL 建立慣例]**，請在&#x200B;**[!UICONTROL 資產命名慣例]**&#x200B;中定義的基本名稱中指定尾碼或前置詞。

   此外，定義在Dynamic Media Classic檔案夾結構中建立回轉集的位置。

   如果您定義大量集合，您可能偏好將這些集合與包含資產本身的資料夾分開。 例如，建立「回轉集」資料夾，將生成的集放在此處。

1. 在&#x200B;**[!UICONTROL Details]**&#x200B;面板中，點選&#x200B;**[!UICONTROL Save]**。
1. 點選新預設集名稱旁的&#x200B;**[!UICONTROL Active]**。

   啟動預設可確保在您上傳資產至動態媒體時，會套用批次集預設集以產生該預設集。

### （可選）調整動態媒體- Scene7模式{#optional-tuning-the-performance-of-dynamic-media-scene-mode}的效能

為了讓Dynamic Media - Scene7模式順利執行，Adobe建議使用下列同步效能／延展性微調提示：

* 更新預定義的作業參數，以處理不同的檔案格式。
* 更新預先定義的Granite工作流程（視訊資產）佇列工作程式執行緒。
* 更新預先定義的Granite暫時工作流程（影像和非視訊資產）佇列工作線程。
* 更新到Dynamic Media Classic伺服器的上傳連線上限。

#### 更新預定義的作業參數，以處理不同的檔案格式

您可以在上傳檔案時調整工作參數，以加快處理速度。 例如，如果您上傳PSD檔案，但不想以範本的形式處理，則可將圖層擷取設為false(off)。 在這種情況下，已調整的作業參數將顯示為`process=None&createTemplate=false`。

Adobe建議對PDF、Postscript和PSD檔案使用下列「已調整」的工作參數：

<!-- OLD PDF JOB PARAMETERS `pdfprocess=Rasterize&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` -->

<!-- OLD POSTSCRIPT JOB PARAMETERS `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Rasterize&airesolution=150&aicolorspace=Auto&aialpha=false` -->

| 檔案類型 | 建議的作業參數 |
| ---| ---|
| PDF | `pdfprocess=Thumbnail&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` |
| Postscript | `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Thumbnail&airesolution=150&aicolorspace=Auto&aialpha=false` |
| PSD | `process=None&layerNaming=Layername&anchor=Center&createTemplate=false&extractText=false&extendLayers=false` |

若要更新這些參數，請遵循[啟用MIME類型型資產／動態媒體經典上傳工作參數support](#enabling-mime-type-based-assets-scene-upload-job-parameter-support)中的步驟。

#### 更新Granite Transient Workflow queue {#updating-the-granite-transient-workflow-queue}

「Granite傳輸工作流程」佇列用於&#x200B;**[!UICONTROL DAM更新資產]**&#x200B;工作流程。 在動態媒體中，它用於影像擷取和處理。

**要更新Granite瞬態工作流隊列，請執行以下操作：**

1. 導覽至[https://&lt;server>/system/console/configMgr](http://localhost:4502/system/console/configMgr)並搜尋&#x200B;**[!UICONTROL 佇列：Granite Transient Workflow Queue]**。

   >[!NOTE]
   >
   >由於OSGi PID是動態產生的，所以必須進行文字搜尋，而非直接URL。

1. 在&#x200B;**[!UICONTROL 最大並行作業數]**&#x200B;欄位中，將數字更改為所需值。

   您可以增加&#x200B;**[!UICONTROL 最大並行作業數]**，以充分支援將檔案大量上傳至動態媒體。 確切值取決於硬體容量。 在某些情況下（即初始移轉或一次性大量上傳），您可以使用大值。 但是，請注意，使用大值（如兩倍的內核數）可能會對其他併發活動產生負面影響。 因此，您應根據您的特定使用案例來測試和調整值。

<!--    By default, the maximum number of parallel jobs depends on the number of available CPU cores. For example, on a 4-core server, it assigns 2 worker threads. (A value between 0.0 and 1.0 is ratio based, or any numbers greater than 1 will assign the number of worker threads.)

   Adobe recommends that 32 **[!UICONTROL Maximum Parallel Jobs]** be configured to adequately support heavy upload of files to Dynamic Media Classic. -->

![chlimage_1](assets/chlimage_1.jpeg)

1. 點選&#x200B;**[!UICONTROL Save]**。

#### 更新Granite工作流隊列{#updating-the-granite-workflow-queue}

「Granite工作流程」佇列用於非暫時性工作流程。 在動態媒體中，它用來使用&#x200B;**[!UICONTROL 動態媒體編碼視訊工作流程來處理視訊。]**

**要更新Granite工作流隊列，請執行以下操作：**

1. 導覽至`https://<server>/system/console/configMgr`並搜尋&#x200B;**[!UICONTROL 佇列：Granite Workflow Queue]**。

   >[!NOTE]
   >
   >由於OSGi PID是動態產生的，所以必須進行文字搜尋，而非直接URL。

1. 在&#x200B;**[!UICONTROL 最大並行作業數]**&#x200B;欄位中，將數字更改為所需值。

   預設情況下，並行作業的最大數量取決於可用CPU內核的數量。 例如，在4核伺服器上，它分配2個工作線程。 （0.0到1.0之間的值是基於比率的，或者任何大於1的數字都將分配工作線程數。）

   對於大多數使用案例，0.5預設設定已足夠。

   ![chlimage_1-1](assets/chlimage_1-1.jpeg)

1. 點選&#x200B;**[!UICONTROL Save]**。

#### 更新Scene7上載連線{#updating-the-scene-upload-connection}

Scene7「上傳連線」設定會將AEM資產同步至Dynamic Media Classic伺服器。

**若要更新Scene7上傳連線：**

1. 導航到 `https://<server>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl`
1. 在[!UICONTROL 連接數]欄位和／或[!UICONTROL 活動作業超時]欄位中，根據需要更改數。

   **[!UICONTROL 連線數]**&#x200B;設定控制AEM上傳動態媒體所允許的HTTP連線數上限；通常，10個連接的預定義值就足夠了。

   **[!UICONTROL 作用中工作逾時]**&#x200B;設定會決定上傳之動態媒體資產在傳送伺服器中發佈的等待時間。 此值預設為2100秒或35分鐘。

   對於大多數使用情況，2100的設定就足夠了。

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

1. 點選&#x200B;**[!UICONTROL Save]**。

### （可選）篩選複製資產{#optional-filtering-assets-for-replication}

在非動態媒體部署中，您會將*所有*資產（包括影像和視訊）從AEM作者環境複製至AEM發佈節點。 此工作流程是必要的，因為AEM發佈伺服器也會傳送資產。

不過，在動態媒體部署中，由於資產是透過雲端服務傳送，因此不需要將這些相同的資產複製至AEM發佈節點。 這種「混合式發佈」工作流程可避免額外的儲存成本以及複製資產的較長處理時間。 其他內容（例如網站頁面）仍可從AEM發佈節點提供。

這些篩選條件可讓您以&#x200B;*exclude*&#x200B;資產的方式，避免複製至AEM發佈節點。

#### 使用複製{#using-default-asset-filters-for-replication}的預設資產篩選器

如果您使用動態媒體進行影像和／或視訊，則可使用我們依現狀提供的預設濾鏡。 下列篩選器預設為作用中：

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td><strong>篩選</strong></td> 
   <td><strong>Mime 類型</strong></td> 
   <td><strong>轉譯</strong></td> 
  </tr> 
  <tr> 
   <td>動態媒體影像傳送</td> 
   <td><p>濾鏡影像</p> <p>filter-sets</p> <p> </p> </td> 
   <td><p>開頭為<strong>image/</strong></p> <p>包含<strong>application/</strong>，結尾為<strong>set</strong>。</p> </td> 
   <td>現成可用的「濾鏡影像」（套用至單一影像資產，包括互動式影像）和「濾鏡集」（套用至旋轉集、影像集、混合媒體集和轉盤集）將： 
    <ul> 
     <li>不複製原始影像和靜態影像轉譯。</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>動態媒體視訊傳送</td> 
   <td>filter-video</td> 
   <td>開頭為<strong>video/</strong></td> 
   <td>現成可用的「filter-video」將： 
    <ul> 
     <li>不複製原始視訊和靜態縮圖轉譯。<br /> <br /> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>篩選器適用於MIME類型，不能是特定路徑。

#### 自定義複製{#customizing-asset-filters-for-replication}的資產篩選器

1. 在AEM中，點選AEM標誌以存取全域導覽主控台，並點選「工具&#x200B;****」圖示並導覽至「一般> CRXDE Lite ]**」。**[!UICONTROL 
1. 在左資料夾樹中，導航到`/etc/replication/agents.author/publish/jcr:content/damRenditionFilters`以查看篩選器。

   ![chlimage_1-2](assets/chlimage_1-2.png)

1. 要定義篩選器的Mime類型，可以按如下方式查找Mime類型：

   在左側導軌中，展開&#x200B;**[!UICONTROL 內容> dam > &lt;`locate_your_asset`> > jcr:content >中繼資料]**，然後在表格中找到&#x200B;**[!UICONTROL dc:format]**。

   下圖為資產dc:format路徑的範例。

   ![chlimage_1-3](assets/chlimage_1-3.png)

   請注意，資產`Fiji Red.jpg`的`dc:format`是`image/jpeg`。

   若要讓此篩選器套用至所有影像，而不論其格式為何，請將值設定為`image/*`，其中`*`是套用至任何格式之所有影像的規則運算式。

   要使濾鏡僅應用於JPEG類型的影像，請輸入`image/jpeg`值。

1. 定義要包含或排除在複製中的轉譯。

   可用於篩選複製的字元包括：

   <table> 
    <tbody> 
    <tr> 
    <td><strong>要使用的字元</strong></td> 
    <td><strong>如何篩選複製資產</strong></td> 
    </tr> 
    <tr> 
    <td>*</td> 
    <td>通配符<br /> </td> 
    </tr> 
    <tr> 
    <td>+</td> 
    <td>包括用於複製的資產。</td> 
    </tr> 
    <tr> 
    <td>-</td> 
    <td>排除複製中的資產。</td> 
    </tr> 
    </tbody> 
   </table>

   導覽至&#x200B;**content/dam/&lt;`locate your asset`>/jcr:content/renditions**。

   下圖為資產轉譯的範例。

   ![chlimage_1-4](assets/chlimage_1-4.png)

   如果您只想複製原稿，則輸入`+original`。


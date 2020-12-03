---
title: AEM 6.4 Cumulative Fix Pack發行說明
description: Adobe Experience Manager 6.4 Cumulative Fix Pack的發行說明。
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: f74e20c5264dc38dcbe20c8fc6b9beaaee7cc6da
workflow-type: tm+mt
source-wordcount: '4112'
ht-degree: 1%

---


# AEM 6.4 Cumulative Fix Pack發行說明{#aem-cumulative-fix-pack-release-notes}

## 發行資訊 {#release-information}

<!-- TBD: Update the SD URL. -->

| 產品 | **Adobe Experience Manager(AEM)6.4** |
|---|---|
| 版本 | 6.4.8.3 |
| 類型 | 累積修補程式套件 |
| 日期 | 2020年11月26日 |
| 先決條件 | [AEM 6.4 Service Pack 8(6.4.8.0)](sp-release-notes.md) |
| 下載URL | [軟體散發](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-3.0.zip)上的AEM 6.4.8.3 |

## AEM 6.4.8.3 {#what-s-included-in-aem}包含的功能

AEM Cumulative Fix Pack 6.4.8.3是重要的更新，自2020年3月AEM 6.4 Service Pack 8(6.4.8.0)全面推出以來，已包含數項內部和客戶修正。

AEM 6.4.8.3是依賴AEM 6.4 Service Pack 8的累積修補程式套件(CFP)。 在安裝AEM 6.4 Service Pack 8後安裝CFP。

在AEM 6.4.8.3中，內建儲存庫(Apache Jackrabbit Oak)已更新為1.8.23版。

如需CFP和其他發行類型的詳細資訊，請參閱[AEM Update Release Vehicle Definitions](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.3可修正下列問題。

### 網站 {#sites-6483}

* 當您更新內容片段變更的文字時，主內容片段的內容會更新，而非變更(NPR-35080)。

* 當您為元件的「字串類型」標籤屬性設定數值、刪除元件，並使用還原選項將其帶回時，標籤屬性的類型會自動從「字串」變更為「長」(NPR-34738)。

* 將「檔案上傳」元件添加到多欄位時，影像路徑儲存在元件節點中，而不是多欄位節點中(NPR-34423)。

* 在「移動頁面」精靈中，即使未選取目標，下一個按鈕仍會保持啟用(NPR-34460)。

* 當父元件包含`cq:isContainer`屬性時，繼承的元件不會自動包含該屬性(CQ-4308409)。

* 當您使用`calc()`函式使用CSS微型化時，`+`符號周圍的空格會被移除(NPR-34991)。

* 當您啟動AEM例項時，`com.adobe.granite.maintenance.impl.MaintenanceTaskManagerImpl`和`com.adobe.granite.maintenance.impl.TaskScheduler`元件不會顯示在`Active`狀態(NPR-34952)。

### [!DNL Assets] {#assets-6483}

* 當建立現有資產的版本時，如果中繼資料描述檔套用至資料夾，使用者不會持續更新中繼資料(NPR-34833)。
* 將[!DNL Adobe Asset Link]與[!DNL Adobe InDesign]搭配使用時，搜尋結果不包含資料夾和系列，但僅包含資產(NPR-34700)。
* 拖曳資料夾上的資產以移動資產時，使用者介面也會顯示[!UICONTROL 「放入燈箱」]和[!UICONTROL 「放入系列」]的選項。 即使取消移動操作，用戶介面仍繼續顯示後兩個選項(NPR-34525)。
* 當「管理出版物」介面開啟時，發佈選項不可用，選取取消發佈選項時，範圍頁面會空白(CQ-4302509)。

#### [!DNL Dynamic Media] {#dynamic-media}

* 在「影像預設集」設定中，當[!DNL Experience Manager]中取消選取「啟用JPG色彩縮減取樣」選項[!UICONTROL 時，變更不會與[!DNL Dynamic Media]同步(NPR-34284)。]
* 在[!UICONTROL 檢視器預設集編輯器]中，編輯[!UICONTROL PanoramicImage/PanoramicImage_VR]預設集時，在`PanoramicView`元件中，`PANORAMICVIEW_AUTOROTATE`修飾元標籤不可用(CQ-4302043)。
* 從[!DNL Experience Manager]取消發佈視訊時，不會解除發佈已設定Scene7上的最適化視訊集。 (CQ-4304405).

### 平台 {#platform-6483}

* `emitUseStrict`標幟會新增至Google Closure Compiler(GCC)處理器函式`com.adobe.granite.ui.clientlibs.impl.HtmlLibraryManagerImpl`。 該標籤抑制`use strict`指令的輸出(NPR-34830)。
* 在開始每日或每週維護任務時返回`NullPointerException`(NPR-34702)。
* [!DNL Apache Sling Health Check]工具已過時。 請改用[Pattern Detector](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/upgrading/pattern-detector.html)來偵測內容違規(NPR-33929)。

### 整合{#integrations-6483}

* 當從資料夾導覽至[!UICONTROL 觀眾]頁面時，[!UICONTROL 建立]按鈕會顯示在[!UICONTROL 觀眾]頁面上(NPR-35152)。

### 使用者介面{#ui-6483}

* [!UICONTROL Omnisearch]使用者介面上的[!UICONTROL Filters]搜尋面板也會傳回搜尋執行位置以外的位置結果(NPR-34877)。
* 在關閉[!UICONTROL Omnisearch]使用者介面上的[!UICONTROL Filters]面板時，左側導軌不會重設為[!UICONTROL Content]選擇，這會防止重新開啟[!UICONTROL Filters]面板(NPR-34483)。
* 訪問頁面屬性時返回`NullPointerException`(NPR-34509)。

### 社群 {#communities-6483}

<!-- Following fixes of 6483 are documented on Nov 11 20202 by Vishabh. 
-->

* 產品中所有不公平術語的例子都被接受的等價物(NPR-34506)所取代。

### 商務 {#commerce-6483}

* 當系列中有超過15種產品時，該系列只會顯示前15種產品(NPR-34494)。

### 表單 {#forms-6483}

>[!NOTE]
>
>[!DNL Experience Manager Forms] 在排程的Cumulative Fix Pack發行日期後一週發 [!DNL Experience Manager] 行附加套件。

**適用性表單**

* 套用[!DNL Experience Manager] Cumulative Fix Pack(NPR-35127)後，無法使用Classic UI編輯最適化表單。

* 由於快取失效，片段以最適化形式載入所花的時間較長(NPR-34655)。

* 協助功能：標籤導覽無法適合最適化表單的螢幕閱讀程式(NPR-34550)。

**信件管理**

* 從ES3移轉資產時，資產包含兩個不可編輯的預設條件(NPR-34971)。

**Foundation JEE**

* 將[!DNL AEM Forms]使用者從Flash移轉至HTML(CQ-4304075)。

如需安全性更新的詳細資訊，請參閱[Experience Manager安全性公告頁面](https://helpx.adobe.com/security/products/experience-manager.html)。

## 舊版累積修補程式套件包含的修補程式和功能套件{#hotfixes-and-feature-packs-included-in-previous-cumulative-fix-packs}

### Adobe Experience Manager 6.4.8.2 {#experience-manager-6482}

AEM Cumulative Fix Pack 6.4.8.2是重要的更新，自2020年3月AEM 6.4 Service Pack 8(6.4.8.0)全面推出以來，已包含數項內部和客戶修正。

AEM 6.4.8.2是依賴AEM 6.4 Service Pack 8的累積修補程式套件(CFP)。 在安裝AEM 6.4 Service Pack 8後安裝CFP。

在AEM 6.4.8.2中，內建儲存庫(Apache Jackrabbit Oak)已更新為1.8.22版。

如需CFP和其他發行類型的詳細資訊，請參閱[AEM Update Release Vehicle Definitions](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.2可修正下列問題。

#### 網站 {#sites-6482}

* 如果`RolloutConfigManagerFactoryImpl`無法載入轉出設定，則不會嘗試載入遺失的設定。 它會傳回快取的組態(NPR-34091)。
* 在Text核心元件中，使用來源HTML編輯選項後，`em`標籤中的類別會被移除(NPR-34080)。
* 從Experience Manager 6.2升級至Experience Manager 6.5時，靜態範本的Parsys元件無法正確顯示。 Parsys元件的高度設定為0，其內部元件不可見(NPR-34044)。
* 範本編輯器中允許的元件不會顯示標籤資訊(NPR-33908)。

   ![版面容器中遺失標籤](assets/33908_missing_labels.png)

* 在第4級嵌套元件之後，用戶無法向parsys添加或編輯元件(NPR-33873)。
* 如果可編輯範本的初始內容已變更，然後範本已發佈，則使用此範本建立的任何新頁面都會顯示範本的「已發佈」日期，即使頁面未發佈(NPR-33822)。
* 複製和貼上操作期間，複製中`cq:acLinks`和`cq:acUUID`的[!DNL Adobe Campaign]屬性將被刪除(NPR-33793)。
* 在[!UICONTROL 即時使用]標籤中，僅顯示49個結果。 它不顯示元件的全部用法(NPR-33710)。
* URL中具有`/`字元的網頁在撰寫時會停止回應。 在製作時新增元件時，CPU使用量會增加，瀏覽器會停止回應(NPR-33625)。
* 在[!DNL RTE]的內嵌編輯模式中，拖曳影像對文字元件無法運作(NPR-33579)。
* 您可以在藍圖頁面中建立與頁面名稱同名的元件。 在轉出期間，此類元件會以字尾`_msm_moved`重新命名。 但是，將該元件移至[!UICONTROL 段落系統]的末尾(NPR-33534)。
* 如果未勾選第一個內容根目錄上的[!UICONTROL include subpages]屬性，啟動促銷不會發佈頁面(NPR-33533)。
* 使用錨點重新導向至[!DNL Experience Manager]頁面在「作者」例項上無法運作，因為`PageRedirectServlets`會在URL片段或錨點後放置查詢字串(NPR-34287)。
* `PageRedirectServlet` 在Sling `.html` 對應後附加，導致連結失敗(NPR-34271)。
* 您可以暫停頁面的[!DNL Live Copy]，繼承會中斷，如編輯器模式所示。 但是，在「頁面」屬性中，表示繼承的表徵圖錯誤地表示繼承存在且未中斷(NPR-34096)。
* 在「編輯」範本頁面中顯示允許的元件時發生問題(CQ-4297295)。
* 升級Chrome和Firefox後，快顯功能表無法如預期般運作。 載入頁面屬性時，當面板中有資料時，它不會顯示面板(CQ-4292995)。

#### 資產 {#assets-6482}

* 已上傳PDF檔案的文字擷取無法運作，而PDF檔案中的某些字詞全文搜尋無法擷取該PDF檔案(NPR-34165)。

   >[!NOTE]
   >若要讓此修正有效，請在安裝Service Pack 6.4.8.2後重新啟動您的Adobe Experience Manager例項。

* 資產的搜尋建議會在特殊字元之前加入反斜線，其名稱中有特殊字元(NPR-33833)。

* 儲存為智慧型系列的自訂篩選器無法正確套用至資產，因此搜尋結果不正確   (NPR-33725)。

* 重新排序的資料夾中資產的時間軸顯示資產已移動(NPR-33580)。

* 從[!DNL Brand Portal]大量取消發佈資產會導致`Request-URI Too Long`錯誤(NPR-34158)。

* 在欄檢視中，如果使用者在選取一組資產（資產取消選取）後選取[!UICONTROL Filter]選項，然後選取另一組資產以移動，則先前選取的資產也會移至新位置(NPR-34018)。

* 即使頁面中有許多資產可容納，但清單檢視中仍無法顯示捲軸(NPR-34156)。

* 資產的[!UICONTROL 管理出版物]頁面已中斷，其中的選項無效(CQ-4302509)。

**Dynamic Media**

* 當將影像描述檔新增至具有多個（例如11）外觀比例的資料夾時，智慧型裁切功能會失敗並出現錯誤(NPR-34083)。

* 對[!UICONTROL Adobe Experience Manager]中影像預設集的變更不會同步至Scene7 Publishing System(NPR-34284、CQ-4299713)。

* 在[!UICONTROL 檢視器預設集編輯器]頁面的[!UICONTROL 行為]標籤中，[!UICONTROL PANORAMICVIEW_AUTOROTATE]修飾元標籤遺失(CQ-4302043)。

#### 平台 {#platform-6482}

* 未指定預設代理（發佈）配置的&#x200B;**[!UICONTROL 連接超時]**&#x200B;和&#x200B;**[!UICONTROL 套接字超時]**&#x200B;設定的預設值(NPR-33708)。
* 維護任務調度程式啟動和停止維護任務的頻率比配置的頻率高(NPR-33520)。
* 無法在升級的Experience Manager實例上使用診斷工具下載日誌(NPR-34419)。

#### 整合{#integrations-6482}

* 為從[!DNL Adobe Dynamic Tag Management]遷移的庫生成[!DNL Adobe Launch]庫URL時，不考慮`library_path`的值。 此外，遷移的庫使用與[!DNL Adobe Launch]庫不同的前置詞。 (NPR-34238)。
* 更新頁面屬性時，從雲端服務繼承的屬性不會持續存在(NPR-33865)。

#### 使用者介面{#ui-6482}

* 在搜尋頁面上顯示選取資產的計數不正確(NPR-33540)。

#### 社群 {#communities-6482}

* 透過管理控制台新增的社群群組現有使用者會從社群群組主控台中任何修改的使用者清單中移除(NPR-34312)。

#### 表單 {#forms-6482}

>[!NOTE]
>
>[!DNL Experience Manager] 累積修正套件不包含的修正 [!DNL Experience Manager Forms]。它們是使用單獨的[!DNL Forms]附加軟體包傳遞的。 此外，還發行了包含JEE上[!DNL Experience Manager Forms]修正的累積安裝程式。 如需詳細資訊，請參閱「安裝AEM Forms附加元件套件](#install-aem-forms-add-on-package)和[安裝AEM Forms JEE安裝程式](#install-aem-forms-jee-installer)」。[

**適用性表單**

* 當缺少自適應表單片段時，自適應表單無法轉換(NPR-34303)。

* 最適化表單欄位的說明內容說明會顯示段落HTML標籤(NPR-34117)。

* 當您在[!DNL Experience Manager Sites]頁面上新增Forms容器時，頁面會顯示下列錯誤訊息，且不允許您新增任何新元件(NPR-33858):

   `DevTools failed to load SourceMap: Could not load content for <Link>. HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE`

* 當您選擇&#x200B;**[!UICONTROL Revalidate on Server]**&#x200B;屬性並上傳多個附件時，自適應表單無法提交(NPR-33701)。

* 當您選擇&#x200B;**[!UICONTROL 使用頁面語言]**&#x200B;和&#x200B;**[!UICONTROL 表單時，頁面將涵蓋[!DNL Experience Manager Sites]頁面上[!DNL Experience Manager Forms]元件中的&lt;a4/>選項的整個寬度，頁面將無法翻譯(NPR-33641)。]**

* 當您提交內嵌於[!DNL Experience Manager Sites]頁面中啟用分析的最適化表單時，分析無法正常運作(NPR-31359)。

* 已刪除對[!DNL Lodash]和[!DNL backbone]庫的依賴性(NPR-33458)。

* **[!UICONTROL 提交到REST端點]**&#x200B;提交操作不適用於自適應表單(NPR-34513)。

* 協助功能：當您嘗試提交最適化表單而未上傳強制欄位的附件時，焦點不會自動移至附件欄位(NPR-34511)。

**工作流程**

* [!DNL Experience Manager] 「Workflow Purge（工作流清除）」操作失敗，並顯示以下錯誤消息(NPR-33576):

   `java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory`

* 當安裝[!DNL Experience Manager] 6.4.8.1時，[!UICONTROL To Do]項目清單不會顯示為連結。 [!UICONTROL To Do]項目的文字包含HTML標籤(NPR-34318)。

**後端整合**

* 無法在AWS托管的[!DNL Experience Manager Forms Linux]環境中配置表單資料模型(NPR-33617)。

**設計人員**

* 當[!DNL Acrobat DC]安裝在[!DNL Experience Manager] Forms伺服器上時，**[!UICONTROL Distribute Form]**&#x200B;選項在[!DNL Experience Manager Designer] 6.x版中不可用(NPR-34325)。

**Document Security**

* 在安裝[!DNL Experience Manager] 6.4.8.0(NPR-34309)後，無法在PDF檔案中使用HSM憑證執行簽署作業。

**升級**

* 在[!DNL Linux]環境中，將[!DNL JBoss]版本升級至[!DNL Experience Manager Forms]的&lt;a1/> 7.0.9，並使用Document Security，會產生錯誤(CQ-4300546)。

如需安全性更新的詳細資訊，請參閱[Experience Manager安全性公告頁面](https://helpx.adobe.com/security/products/experience-manager.html)。

### Adobe Experience Manager 6.4.8.1 {#experience-manager-6481}

AEM Cumulative Fix Pack 6.4.8.1是重要的更新，包含自2020年3月AEM 6.4 Service Pack 8(6.4.8.0)全面推出以來的數項內部和客戶修正。

AEM Cumulative Fix Pack 6.4.8.1需仰賴AEM 6.4 Service Pack 8。 因此，在安裝AEM 6.4 Service Pack 8後，您必須安裝AEM Cumulative Fix Pack 6.4.8.1套件。

AEM 6.4.8.1的一些主要亮點是：

* 不允許匿名存取CRXDE Lite以增強安全性。 而是將使用者導向登入畫面。 請參閱[使用CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md)開發。
* 已移除與Adobe Experience Manager的套件共用整合。
* 內建儲存庫(Apache Jackrabbit Oak)已更新至1.8.21版。

如需CFP和其他發行類型的詳細資訊，請參閱[AEM Update Release Vehicle Definitions](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.1可修正下列問題。

#### 網站 {#sites-6481}

* 匿名使用者可存取CRX DE Lite功能(NPR-33522)。
* 當LiveCopy中的本機元件名稱與Blueprint中的元件名稱相同，且元件從Blueprint中推出時，_msm_moved詞語不會新增至本機元件的名稱(NPR-33207)。
* 附加至原始請求的參數不會包含在重新導向URL中(NPR-33174)。
* 當Coral.Select選項設定emptyOption=true或包含值= &quot;&quot;的預設項目時，dropdownshowhide.js檔案會遇到錯誤：未捕獲的類型錯誤：component.getValue不是函式(NPR-33163)。
* 當元件包含另一個元件作為資料儲存資源時，父容器元件預留位置會以內部元件預留位置(NPR-33119)取代。
* 當內容片段以架構為基礎且包含強制文字區域或路徑欄位時，內容片段無法儲存(NPR-33007)
* 當您使用「現成可用的體驗」片段元件建立自訂元件並在AEM Sites頁面中使用時，AEM不會顯示自訂元件的參考（使用）(NPR-32852)。
* 當AEM Sites頁面是包含多個即時副本的大型內容集的一部分時，頁面版本歷史記錄預覽無法載入(NPR-32772)。
* 當您促銷啟動時，它會將&quot;cq:LiveRelations&quot;混合加入啟動中新增的每個元件。 它會影響所有啟動，而不論啟動是否已建立且未選取—  繼承來源頁面即時資料—  選項(NPR-32664)。
* 當分頁開始時，「體驗片段選擇器」不會載入所有項目(NPR-32605)。
* 無法建立AEM Sites頁面的啟動。 啟動建立會導致錯誤(NPR-32544)。
* 「管理出版物」在啟動工作流程的要求中不包含參考資產(NPR-32463)。
* Dispatcher Health check在日誌檔案中顯示`Invalid cookie header`警告消息(NPR-33630)。
* Salesforce整合易受SSRF(NPR-32671)的影響。
* PreferencesServlet中反映的XSS(NPR-33439)。

#### 資產 {#assets-6481}

* 資產計數不會因清單檢視中選取項目的變更而改變(NPR-33285)。

* 在選擇父節點（其中顯示單個子資料夾），然後選擇子資料夾(NPR-33284)時，未啟用「下一個」按鈕。

* 當啟用DMS7或混合模式時，對於沒有資料庫根目錄讀取存取權的使用者，Touch UI無法轉譯（有錯誤）(NPR-33175)。

* 資料夾和資產名稱中發生的GB18030字元在下載的zip檔案中會變更為空白(NPR-33150)。

* 在智慧型裁切資產時會建立額外的資料夾，該資產位於父資料夾內，名稱中包含點`.`字元(NPR-32755)。

* 不會觸發延遲載入，且選取來檢閱通知收件匣中的工作時，不會顯示超過100個資產(NPR-32749)。

* 共用系列的連結頁面因coral-info的變更而中斷(NPR-32510)。

* 大量上傳時的資產處理會卡住(CQ-4293916)。

* Experience Manager中的SSRF弱點(NPR-33437)。

#### 平台 {#platform-6481}

* 如果在`/etc/maps`下建立`sling:match`映射條目，則不調用[!DNL Sling]過濾器(NPR-33308)。
* 在停用頁面時觸發所有刷新代理(NPR-32941)。
* 當您使用`ScriptProcessor` API來精簡JavaScript程式庫時，記錄檔會顯示錯誤訊息，指出JavaScript程式碼不符合嚴格模式。 API不提供啟用或停用嚴格模式的選項。 (NPR-32746)。
* 當SQL查詢執行較長時間（例如7小時）時，AEM會停止回應(NPR-33043)。

#### 使用者介面{#ui-6481}

* 當您使用選擇對話框搜索或瀏覽路徑時，選擇對話框將顯示所選JCR節點的所有內容，而不只顯示影像(NPR-32712)。

#### 翻譯專案 {#tranlation-6481}

* 在運行翻譯作業的日誌中出現`NullPointerException`錯誤(NPR-32220)。

#### 整合{#integrations-6481}

* JSON的跨網站指令碼(NPR-32745)。

#### 社群 {#communities-6481}

* 建立新群組後，作者不會重新導向至[!DNL Internet Explorer] 11上的[!UICONTROL 社群群組]區段(NPR-33202)。
* 存取[!UICONTROL 活動串流]頁面時發生錯誤(NPR-33152)。
* 編輯[!DNL Communities]群組並變更縮圖影像並不會更新群組縮圖影像(NPR-32603)。
* 建立使用者產生的內容(UGC)的通知和訂閱版本時，會儲存來源頁面的錯誤ID(CQ-4289703)。
* 跨網站指令碼問題(NPR-33212)。

#### 工作流程 {#workflow-6481}

* 當使用者完成包含[!UICONTROL 對話參與者步驟](NPR-32989)的工作流程時，有些元件不會顯示在彈出的對話方塊中。

* 左側導軌中的[!UICONTROL 時間軸]選項的載入時間比預期要長(NPR-32850)。

#### 表單 {#forms-6481}

>[!NOTE]
>
>AEM Cumulative Fix Pack不包含AEM Forms的修正。 它們是使用個別的Forms附加套件傳送。 此外，還會發行包含JEE上AEM Forms修正的累積安裝程式。 如需詳細資訊，請參閱「安裝AEM Forms附加元件套件](#install-aem-forms-add-on-package)和[安裝AEM Forms JEE安裝程式](#install-aem-forms-jee-installer)」。[

* 通信管理：當使用者貼上[!DNL Word]檔案的內容時，文字檔案片段不會保留格式(NPR-33213)。
* 最適化表單：自適應表單字典中字串的新行將`&#xa;`字元添加到字典(NPR-33265)。
* 最適化表單：用戶無法保存具有多個附件的自適應表單(NPR-33214)。
* 最適化表單：例項管理器類的`AddInstance`和`RemoveInstance`方法不會在[!DNL Internet Explorer 11]上為延遲載入片段添加動態數目的實例(NPR-33201)。
* 最適化表單：在內嵌於[!DNL Sites]頁面的最適化表單上啟用的Analytics不會記錄提交和放棄事件的資料(NPR-31359)。
* 最適化表單：當使用者將[!DNL Word]檔案的內容貼入最適化表單並送出時，提交的最適化表單包含Unicode字元。 此外，PDF轉換為PDF/A失敗，因為Unicode字元(NPR-33348)。
* 後端整合：表單資料模型請求會因重新整理Token因非作用中狀態不正確而失敗(NPR-33168)。
* 檔案服務：由於[!DNL Linux]伺服器上[!DNL WebLogic]的Gibsonjar遺失，因此轉換PDF服務無法將PDF檔案轉換為PostScript(NPR-33515, CQ-4292239)。
* 檔案服務：當使用者將文字檔案轉換為PDF時，日文字元無法正確顯示(NPR-33239)。
* 將XSS與GuideSOMProviderServlet一起儲存(NPR-32701)。

## 安裝6.4.8.3 {#install}

### 安裝要求{#setup-requirements}

<!--

>[!NOTE]
>
>For successful installation of AEM 6.4.6.0 on the instance, it is strongly recommended to upgrade the version of com.adobe.granite.oak.s3connector to 1.8.4 for the customers who are on the older version of s3 connector.
>The process of upgrading the com.adobe.granite.oak.s3connector is available at [https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html](https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html).
>Download the latest version of com.adobe.granite.oak.s3connector from: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

-->

>[!CAUTION]
>
>適用於已安裝在AEM 6.4的功能套件客戶。Adobe提供的選購功能套件與發行版本和Service Pack有相依性。 如果您已安裝任何功能套件，請聯絡AEM客戶服務團隊，以驗證這些功能套件與AEM 6.4累積修補程式套件的相容性。

* AEM 6.4.8.3需要AEM 6.4.8.0。請造訪[升級檔案](../sites-deploying/upgrade.md)以取得詳細指示。
* 在使用MongoDB和多個執行個體的部署中，使用「套件管理員」將AEM 6.4.8.3安裝在其中一個「作者」執行個體上。
* 在安裝累積修補程式套件之前，請確定您有AEM例項的快照或最新備份。
* 在安裝之前重新啟動實例。 雖然只有在實例仍處於更新模式時才需要（這是剛從舊版更新實例時），但通常建議在實例運行較長時間時使用。

>[!NOTE]
>
>Adobe不建議移除或解除安裝AEM 6.4.8.3套件。

### 安裝Cumulative Fix Pack {#install-cumulative-fix-pack}

請執行下列步驟，在現有的AEM 6.4.8.0例項上安裝Cumulative Fix Pack:

1. 按一下[軟體分發](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-3.0.zip)連結下載軟體包。

1. 開啟[包管理器](http://localhost:4502/crx/packmgr/index.jsp) ，然後按一下&#x200B;**[!UICONTROL 上載包]**&#x200B;來上載包。

1. 選擇軟體包名稱，然後按一下&#x200B;**[!UICONTROL Install]**。

>[!NOTE]
>
>**在安裝6.4.8.3時，Package Manager UI的對話框有時會立即退出**
>
>因此，建議您先等待錯誤記錄穩定，再存取執行個體。 在確保安裝成功之前，用戶必須等待與卸載更新程式包相關的特定日誌。 通常在Safari上會發生，但在任何瀏覽器上都會偶爾發生。

### 自動安裝{#auto-installation}

有兩種方式可自動將AEM 6.4.8.3安裝至執行中的例項：

答：將套件放入……*/crx-quickstart/* installfolder（伺服器運行時）。軟體包會自動安裝。

B.使用Package Manager](https://docs.adobe.com/content/docs/en/crx/2-3/how_to/package_manager.html)的[HTTP API —— 請確定您使用`cmd=install&recursive=true` —— 以便安裝巢狀套件。

>[!NOTE]
>
>AEM 6.4.8.3不支援Bootstrap安裝。

### 驗證安裝{#validate-install}

1. 「產品資訊」頁面(*/system/console/productinfo*)現在應在「已安裝產品」下方顯示更新的版本字串「Adobe Experience Manager, Version 6.4.8.3」。
1. 所有OSGI組合在OSGI主控台中都是ACTIVE或FRAGMENT(使用Web主控台：/system/console/bundles)。
1. OSGI套件org.apache.jackrabbit.oak-core是1.8.17版或更新版本(使用Web Console:/system/console/bundles)。

若要決定此版AEM Sites和Assets的認證執行平台，請參閱[技術需求](../sites-deploying/technical-requirements.md)。

>[!NOTE]
>成功安裝套件時，會出現資訊性訊息，指出內容套件已成功安裝，例如&#x200B;**「Content Package AEM-6.4-Service-Pack-8已成功安裝。」**

### 更新動態媒體檢視器(5.10.1){#update-dynamic-media-viewers}

AEM 6.4.8.3包含新版動態媒體檢視器(5.10.1)，可讓您在「影像預設集」頁面上檢查重複名稱。 建議動態媒體客戶執行下列命令，將方塊檢視器預設集調整為最新狀態。

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

將新的檢視器預設集複製至/conf位置。

### 安裝AEM Forms附加元件套件{#install-aem-forms-add-on-package}

>[!NOTE]
>
>[!DNL Experience Manager Forms] 在排程的Cumulative Fix Pack發行日期後一週發 [!DNL Experience Manager] 行附加套件。

>[!NOTE]
>
>如果您不使用AEM Forms，請略過。 AEM Forms中的修正是透過個別的附加套件傳送。

1. 請確定您已安裝AEM Cumulative Fix Pack。
1. 針對您的作業系統，下載列在[AEM Forms releases](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html)的對應表格附加元件套件。
1. 如[安裝AEM Forms附加套件](https://docs.adobe.com/content/help/en/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package)中所述，安裝表單附加套件。

### 安裝AEM Forms JEE安裝程式{#install-aem-forms-jee-installer}

>[!NOTE]
>
>如果您未在JEE上使用AEM Forms，請略過。 AEM Forms JEE中的修正會透過個別安裝程式提供。

如需有關安裝AEM Forms JEE累積安裝程式和部署後設定的詳細資訊，請參閱[AEM Forms JEE修補程式安裝程式](jee-patch-installer-64.md)。

### Uber Jar {#uber-jar}

[Maven Central儲存庫](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.4.8.3/)中提供AEM 6.4.8.3版Uber Jar。

要在Maven項目中使用Uber Jar，請參閱[如何使用Uber jar](../sites-developing/ht-projects-maven.md)一文，並在項目POM中包括以下相關性：

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8.3</version>
      <scope>provided</scope>  
</dependency>
```

>[!NOTE]
>
>UberJar和其他相關對象可在Maven Central Repository中使用，而非Adobe Public Maven Repository(repo.adobe.com)。 主UberJar檔案更名為`uber-jar-<version>.jar`。 因此，`dependency`標籤沒有`classifier`,`apis`值。

## 已移除／已過時的功能{#removed-deprecated-features}

本節列出已從AEM 6.4移除或淘汰的功能和功能。

| 區域 | 功能 | 替代方案 | 版本 |
|---|---|---|---|
| 資產 | 管理子資產的標籤動作 | 無更換 | AEM 6.4.2.0 |
| 資產與Adobe Creative Cloud整合 | [AEM to Creative Cloud資料夾](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) 共用是在AEM 6.2中引進的，可讓創意使用者存取AEM的資產。Creative Cloud應用程式中發行的新功能Adobe Asset Link提供更佳的使用者體驗，並可直接從Photoshop、InDesign和Illustrator內部，以更強大的方式存取AEM中的資產。 Adobe不會進一步增強資料夾共用功能。 雖然AEM中包含此功能，但客戶會收到（我們強烈建議您使用此取代項目）。 | Adobe Asset Link或案頭應用程式。 如需詳細資訊，請參閱[AEM Creative Cloud整合](/help/assets/aem-cc-integration-best-practices.md)文章。 | AEM 6.4.4.0 |

## 已知問題 {#known-issues}

* 如果您從[!DNL Experience Manager] 6.4升級至[!DNL Experience Manager] 6.5，某些捆綁包可能不會將其狀態顯示為`Active`。 安裝最新的[!DNL Experience Manager] 6.5 Service Pack以解決問題。

如需AEM 6.4.8.0 Service Pack已知問題的詳細資訊，請參閱[ AEM 6.4.8.0 Service Pack發行說明](sp-release-notes.md)。

## 包含{#osgi-bundles-and-content-packages-included}的OSGi捆綁包和內容包

下列文字檔案列出AEM 6.4.8.3中包含的OSGi組合和內容封裝。

AEM 6.4.8.3隨附的OSGi搭售清單

[取得檔案](assets/6.4.8.3_osgi_bundles.txt)

AEM 6.4.8.3內容套件清單

[取得檔案](assets/6.4.8.3_content_packages.txt)

## 實用資源 {#helpful-resources}

* [AEM 6.4版本注意事項](../release-notes/release-notes.md)
* [AEM產品頁面](https://www.adobe.com/solutions/web-experience-management.html)
* [AEM 6.4 檔案](https://helpx.adobe.com/tw/support/experience-manager/6-4.html)
* 訂閱[Adobe優先產品更新](https://www.adobe.com/subscription/priority-product-update.html)

## 受限制的站點{#restricted-sites-new}

這些網站僅提供給客戶使用。 如果您是客戶，需要存取權，請聯絡您的Adobe客戶經理。

* [產品下載，請造訪licensing.adobe.com](https://licensing.adobe.com/)
* [聯絡客戶支援](https://docs.adobe.com/content/help/en/customer-one/using/home.html)

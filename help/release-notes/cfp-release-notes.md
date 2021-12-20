---
title: AEM 6.4 Cumulative Fix Pack 發行說明
description: Adobe Experience Manager 6.4 Cumulative Fix Pack專用的發行說明。
contentOwner: AK
mini-toc-levels: 1
exl-id: a63e77a3-da48-4072-bc75-c4c41a2f62a3
source-git-commit: 1d5d2ef3840a40df7c3b223c7b5835e41553e9f1
workflow-type: tm+mt
source-wordcount: '4693'
ht-degree: 10%

---

# AEM 6.4 Cumulative Fix Pack 發行說明 {#aem-cumulative-fix-pack-release-notes}

## 發行資訊 {#release-information}

<!-- TBD: Update the SD URL. -->

| 產品 | **Adobe Experience Manager(AEM)6.4** |
|---|---|
| 版本 | 6.4.8.4 |
| 類型 | Cumulative Fix Pack |
| 日期 | 2021 年 2 月 25 日 |
| 必備條件 | [AEM 6.4 Service Pack 8(6.4.8.0)](sp-release-notes.md) |
| 下載URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-4.0.zip) |

## AEM 6.4.8.4包含的項目 {#what-s-included-in-aem}

AEM Cumulative Fix Pack 6.4.8.4為重要更新，包含自2020年3月正式發行AEM 6.4 Service Pack 8(6.4.8.0)以來累積的多項內部及客戶修正。

AEM 6.4.8.4是依存於AEM 6.4 Service Pack 8的Cumulative Fix Pack(CFP)。 安裝AEM 6.4 Service Pack 8後，再安裝CFP。

中推出的主要功能和增強功能 [!DNL Adobe Experience Manager] 6.4.8.4包括：

* 啟用或停用 [!DNL Experience Manager Forms] 執行PDFG轉換時註冊表更改。

* X-509以憑證為基礎的驗證，適用於表單資料模型中以SOAP為基礎的Web服務。

* 內建存放庫 (Apache Jackrabbit Oak) 更新至 1.8.24 版。

如需CFP和其他發行版本的相關資訊，請參閱 [AEM更新發行工具定義](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.4修正下列問題。

### 網站 {#sites-6484}

* 安裝Experience ManagerService Pack 6.4.8.2後，使用者無法編輯內容片段模型，並遇到下列錯誤：

   `Uncaught TypeError: Cannot read property 'debounce' of undefined` (NPR-35312)
* 當用戶按一下註銷按鈕時，該用戶未登出包管理器。 (NPR-35161)
* 從Experience Manager6.4.x升級至Experience Manager6.4.8.3後，使用者無法透過管理出版物發佈頁面。 (CQ-4312511)
* 將Blueprint子頁面移回原始位置時，不會從Live Copy子頁面移除cq:liveSyncConfig設定。 (NPR-35900)
* 當您前後移動具有即時副本的藍圖時，只有第一次移動能運作，然後就會失敗，並且不會顯示錯誤訊息。 (NPR-35899)


### [!DNL Assets] {#assets-6484}

* `IndexWriter.merge` 原因 `OutOfMemoryError` 錯誤，因為智慧標籤功能會造成大 `/oak:index/lucene` 和 `/oak:index/ntBaseLucene` 索引(NPR-35650)。
* 在中編輯資產後，使用者無法登入資產 [!DNL Adobe InDesign] 並收到關於缺少權限的錯誤(NPR-35340)。
* 解決命名衝突後建立新版本的現有資產時，會覆寫原始資產的中繼資料(NPR-35939)。
* 刪除資料夾或使用更新資料夾時，不會維護和移除自動產生的私人資料夾群組 [!UICONTROL 移除私人資料夾限制] 選項設定(NPR-35625)。

#### [!DNL Dynamic Media] {#dynamic-media}

* 間歇性ImageServer錯誤導致403響應，並導致以下幾種功能的失敗： [!DNL Experience Manager]. (CQ-4308565)

### Integrations {#integrations-6484}

* 升級至Experience Manager6.4.8.3後開啟頁面的屬性時，主控台中會開始出現JavaScript錯誤(NPR-35649)。

### Forms {#forms-6484}

>[!NOTE]
>
>[!DNL Experience Manager Forms] 會在排程的[!DNL Experience Manager] Cumulative Fix Pack 發行日期一週後發行附加元件的套件。

**通信管理**

* 編輯信函時，含有條件的模組需要較長的載入時間(NPR-35326)。

* 編輯信函時，內容和資料系結不會顯示在使用者介面上(CQ-4312905)。

**文件服務**

* 升級後無法組合PDF [!DNL JAVA] to [!DNL JDK1.8.0_261] (NPR-35761、NPR-35848)。

**Foundation JEE**

* 在中編輯任務通知時 [!DNL Forms] 工作流程中，您無法儲存它(CQ-4315055)。

**AEMForms-6.4.0-0027中修正的問題**

* （僅限JEE）Apache Log4j2回報的重大安全性弱點(CVE-2021-44228和CVE-2021-45046)。

如需安全性更新的詳細資訊，請參閱 [Experience Manager安全性佈告欄頁面](https://helpx.adobe.com/security/products/experience-manager.html).

## 先前版本 Cumulative Fix Pack 中包含的 Hotfix 和 Feature Pack {#hotfixes-and-feature-packs-included-in-previous-cumulative-fix-packs}

### Adobe Experience Manager 6.4.8.3 {#experience-manager-6483}

AEM Cumulative Fix Pack 6.4.8.3為重要更新，包含自2020年3月正式發行AEM 6.4 Service Pack 8(6.4.8.0)以來累積的多項內部及客戶修正。

AEM 6.4.8.3是依存於AEM 6.4 Service Pack 8的Cumulative Fix Pack(CFP)。 安裝AEM 6.4 Service Pack 8後，再安裝CFP。

在AEM 6.4.8.3中，內建存放庫(Apache Jackrabbit Oak)更新至1.8.23版。

如需CFP和其他發行版本的相關資訊，請參閱 [AEM更新發行工具定義](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.3修正下列問題。

#### 網站 {#sites-6483}

* 當您更新內容片段變化的文字時，主內容片段的內容會更新，而非變化(NPR-35080)。

* 為元件的字串類型標籤屬性設定數值時，請刪除元件，並使用還原選項將其復原時，標籤屬性的類型會自動從字串變更為長(NPR-34738)。

* 將檔案上傳元件新增至多欄位時，影像路徑會儲存在元件節點中，而非多欄位節點(NPR-34423)。

* 在「移動頁面」精靈中，即使未選取任何目的地，下一個按鈕仍會維持啟用(NPR-34460)。

* 當父元件包含 `cq:isContainer` 屬性，繼承的元件不會自動包含屬性(CQ-4308409)。

* 當您使用CSS縮制時，使用 `calc()` 函式中，周圍的空格 `+` 移除符號(NPR-34991)。

* 當您啟動AEM例項時， `com.adobe.granite.maintenance.impl.MaintenanceTaskManagerImpl` 和 `com.adobe.granite.maintenance.impl.TaskScheduler` 元件未顯示於 `Active` state(NPR-34952)。

#### [!DNL Assets] {#assets-6483}

* 建立現有資產的版本時，如果將中繼資料設定檔套用至資料夾，使用者不會持續更新中繼資料(NPR-34833)。
* 使用時 [!DNL Adobe Asset Link] with [!DNL Adobe InDesign]，搜尋結果不包含資料夾和集合，但僅包含資產(NPR-34700)。
* 在資料夾上拖曳資產以移動資產時，使用者介面也會顯示 [!UICONTROL 放置燈箱] 和 [!UICONTROL 拖放集合]. 即使取消移動操作，使用者介面仍會繼續顯示後兩個選項(NPR-34525)。
* 開啟「管理出版物」介面時，無法使用發佈選項，且選取取消發佈選項時，範圍頁面會空白(CQ-4302509)。

##### [!DNL Dynamic Media] {#dynamic-media-6483}

* 在「影像預設集」設定中，當選項 [!UICONTROL 啟用JPG色度縮減取樣] 在中取消選取 [!DNL Experience Manager]，變更不會與同步 [!DNL Dynamic Media] (NPR-34284)。
* 在 [!UICONTROL 檢視器預設集編輯器]，編輯時 [!UICONTROL PanoramicImage/PanoramicImage_VR] 預設集，在 `PanoramicView` 元件， `PANORAMICVIEW_AUTOROTATE` 修飾符標籤不可用(CQ-4302043)。
* 取消發佈影片的來源 [!DNL Experience Manager] 不會取消發佈已設定之Dynamic Media Classic上的最適化視訊集。 (CQ-4304405).

#### 平台 {#platform-6483}

* 此 `emitUseStrict` 為Google關閉編譯器(GCC)處理器函式添加標籤 `com.adobe.granite.ui.clientlibs.impl.HtmlLibraryManagerImpl`. 此標幟會抑制 `use strict` 指示(NPR-34830)。
* A `NullPointerException` 在開始每日或每週維護任務時傳回(NPR-34702)。
* 此 [!DNL Apache Sling Health Check] 工具已過時。 請改用 [圖樣偵測器](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/upgrading/pattern-detector.html) 偵測內容違規(NPR-33929)。

#### 整合 {#integrations-6483}

* 此 [!UICONTROL 建立] 按鈕 [!UICONTROL 對象] 頁 [!UICONTROL 對象] 第(NPR-35152)頁。

#### 使用者介面 {#ui-6483}

* 此 [!UICONTROL 篩選器] 搜尋面板 [!UICONTROL Omnisearch] 使用者介面也會傳回執行搜尋所在位置以外的結果(NPR-34877)。
* 關閉 [!UICONTROL 篩選器] 面板 [!UICONTROL Omnisearch] 使用者介面時，左側邊欄不會重設為 [!UICONTROL 內容] 選項，這會阻止重新開啟 [!UICONTROL 篩選器] 面板(NPR-34483)。
* A `NullPointerException` 在存取頁面屬性時傳回(NPR-34509)。

#### 社群 {#communities-6483}

<!-- Following fixes of 6483 are documented on Nov 11 20202 by Vishabh. 
-->

* 產品中所有不公平術語的實例都被接受的等價物取代(NPR-34506)。

#### 商務 {#commerce-6483}

* 當集合中有超過15種產品時，集合只會顯示前15種產品(NPR-34494)。

#### Forms {#forms-6483}

>[!NOTE]
>
>[!DNL Experience Manager Forms] 會在排程的[!DNL Experience Manager] Cumulative Fix Pack 發行日期一週後發行附加元件的套件。

>[!NOTE]
>
>[!DNL Experience Manager] Cumulative Fix Pack不包含 [!DNL Experience Manager Forms]. 它們是使用 [!DNL Forms] 附加套件。 此外，已發行包含修正的累積安裝程式 [!DNL Experience Manager Forms] JEE版。 如需詳細資訊，請參閱 [安裝AEM Forms附加元件套件](#install-aem-forms-add-on-package) 和 [安裝AEM Forms JEE安裝程式](#install-aem-forms-jee-installer).

**調適型表單**

* 套用 [!DNL Experience Manager] Cumulative Fix Pack(NPR-35127)。

* 由於快取失效，片段以最適化形式載入所需的時間較長(NPR-34655)。

* 協助工具：針對最適化表單中的螢幕助讀程式，索引標籤導覽無法正常運作(NPR-34550)。

**通信管理**

* 從ES3移轉資產時，資產包含兩個不可編輯的預設條件(NPR-34971)。

**Foundation JEE**

* 移轉 [!DNL AEM Forms] 從Flash到HTML的使用者(CQ-4304075)。

### Adobe Experience Manager 6.4.8.2 {#experience-manager-6482}

AEM Cumulative Fix Pack 6.4.8.2為重要更新，包含自2020年3月正式發行AEM 6.4 Service Pack 8(6.4.8.0)以來累積的多項內部及客戶修正。

AEM 6.4.8.2是依存於AEM 6.4 Service Pack 8的Cumulative Fix Pack(CFP)。 安裝AEM 6.4 Service Pack 8後，再安裝CFP。

在AEM 6.4.8.2中，內建存放庫(Apache Jackrabbit Oak)更新至1.8.22版。

如需CFP和其他發行版本的相關資訊，請參閱 [AEM更新發行工具定義](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.2修正了下列問題。

#### 網站 {#sites-6482}

* 若 `RolloutConfigManagerFactoryImpl` 無法載入轉出設定，不會嘗試載入遺失的設定。 它會傳回快取設定(NPR-34091)。
* 在文本核心元件中，使用源HTML編輯選項後， `em` 標籤已移除(NPR-34080)。
* 從Experience Manager6.2升級至Experience Manager6.5時，靜態範本的Parsys元件無法正確顯示。 Parsys元件的高度設為0，且其中的元件不可見(NPR-34044)。
* 範本編輯器內未顯示允許的元件的標籤資訊(NPR-33908)。

   ![版面容器中缺少標籤](assets/33908_missing_labels.png)

* 使用者在第四層巢狀元件後，無法新增或編輯元件至parsys(NPR-33873)。
* 如果可編輯範本的初始內容已變更，然後範本已發佈，則使用此範本建立的任何新頁面都會顯示範本的「已發佈」日期，即使頁面未發佈(NPR-33822)。
* 此 `cq:acLinks` 和 `cq:acUUID` 屬性 [!DNL Adobe Campaign] 複製和貼上作業期間會移除復本上的(NPR-33793)。
* 在 [!UICONTROL 使用中] 頁簽，則只顯示49個結果。 它未顯示元件的所有用法(NPR-33710)。
* 網頁 `/` 編寫時，URL中的字元會停止回應。 製作時新增元件時，CPU使用量會增加，瀏覽器會停止回應(NPR-33625)。
* 在內嵌編輯模式中， [!DNL RTE]，拖曳影像對文字元件無法運作(NPR-33579)。
* 您可以在Blueprint頁面中建立與頁面名稱同名的元件。 轉出期間，會借由尾碼來重新命名此類元件 `_msm_moved`. 但元件會移至 [!UICONTROL 段落制度] (NPR-33534)。
* 若 [!UICONTROL 包含子頁面] 未在第一個內容根上檢查屬性(NPR-33533)。
* 重定向至 [!DNL Experience Manager] 具有錨點的頁面在作者例項上無法作為 `PageRedirectServlets` 會在URL片段或錨點後放置查詢字串(NPR-34287)。
* `PageRedirectServlet` 附加 `.html` 導致連結失敗的Sling對應之後(NPR-34271)。
* 您可以暫停 [!DNL Live Copy] 中的繼承會中斷，如編輯器模式所示。 不過，在頁面屬性中，代表繼承的圖示不正確地指出繼承存在且未中斷(NPR-34096)。
* 在「編輯範本」頁面中顯示允許的元件時發生問題(CQ-4297295)。
* 升級Chrome和Firefox後，快顯功能表無法如預期運作。 載入頁面屬性時，當面板中有資料時不會顯示該面板(CQ-4292995)。
* 中有多個跨網站指令碼執行個體 [!DNL Experience Manager Sites] 元件(NPR-33926)。
* 傳送資訊至用戶端時，使用者輸入內容未針對各種元件進行適當編碼(NPR-33696)。
* 結尾為 `childrenlist.html` 顯示HTML頁面，而非404回應。 這類URL容易遭受跨網站指令碼攻擊(NPR-33441)。

#### 資產 {#assets-6482}

* 上傳PDF檔案的文字擷取無法運作，且PDF檔案中某些字詞的全文搜尋無法擷取該PDF檔案(NPR-34165)。

   >[!NOTE]
   >若要讓此修正正常運作，請安裝Service Pack 6.4.8.2後，重新啟動您的Adobe Experience Manager執行個體。

* 在資產的搜尋建議中，會在特殊字元前面加上反斜線，這些資產的名稱中有特殊字元(NPR-33833)。

* 儲存為智慧型集合的自訂篩選器未正確套用至資產，因此搜尋結果不準確(NPR-33725)。

* 重新排序的資料夾內資產的時間軸表示資產已移動(NPR-33580)。

* 從大量取消發佈資產 [!DNL Brand Portal] 導向 `Request-URI Too Long` 錯誤(NPR-34158)。

* 在欄檢視中，如果使用者選取 [!UICONTROL 篩選] 選項：選取一組資產（取消選取資產），接著選取不同的一組資產以移動，之前選取的資產也會移至新位置(NPR-34018)。

* 即使頁面中有許多資產需要放入，清單檢視中仍無法顯示捲軸(NPR-34156)。

* 此 [!UICONTROL 管理出版物] 資產的頁面損毀，其中的選項無法運作(CQ-4302509)。

**Dynamic Media**

* 將影像描述檔新增至具有多個（例如11）外觀比例的資料夾時，智慧型裁切功能會因錯誤而失敗(NPR-34083)。

* 中影像預設集的變更 [!UICONTROL Adobe Experience Manager] 請勿同步至Dynamic Media Classic(NPR-34284、CQ-4299713)。

* 此 [!UICONTROL PANORAMICVIEW_AUTOOTATE] 修飾符標籤從中缺少 [!UICONTROL 行為] 標籤 [!UICONTROL 檢視器預設集編輯器] 第(CQ-4302043)頁。

#### 平台 {#platform-6482}

* 的預設值 **[!UICONTROL 連接超時]** 和 **[!UICONTROL 通訊端逾時]** 未指定預設代理（發佈）組態的設定(NPR-33708)。
* 維護任務調度程式啟動和停止維護任務的頻率比配置太高(NPR-33520)。
* 無法在升級的Experience Manager執行個體上使用診斷工具下載記錄檔(NPR-34419)。

#### 整合 {#integrations-6482}

* 的值 `library_path` 產生時不會考慮 [!DNL Adobe Launch] 從移轉的程式庫的程式庫URL [!DNL Adobe Dynamic Tag Management]. 此外，移轉的程式庫使用的前置詞與 [!DNL Adobe Launch] 程式庫。 (NPR-34238).
* 更新頁面屬性時，繼承自雲端服務的屬性不會持續存在(NPR-33865)。

#### 使用者介面 {#ui-6482}

* 在搜尋頁面上顯示選取資產的計數不正確(NPR-33540)。

#### 社群 {#communities-6482}

* 透過管理控制台新增的社群群組現有使用者，會在社群群組主控台中進行任何修改時從使用者清單中移除(NPR-34312)。

#### Forms {#forms-6482}

>[!NOTE]
>
>[!DNL Experience Manager] Cumulative Fix Pack不包含 [!DNL Experience Manager Forms]. 它們是使用 [!DNL Forms] 附加套件。 此外，已發行包含修正的累積安裝程式 [!DNL Experience Manager Forms] JEE版。 如需詳細資訊，請參閱 [安裝AEM Forms附加元件套件](#install-aem-forms-add-on-package) 和 [安裝AEM Forms JEE安裝程式](#install-aem-forms-jee-installer).

**調適型表單**

* 缺少最適化表單片段時，適用性表單無法轉譯(NPR-34303)。

* 適用性表單欄位的說明內容說明會顯示段落HTML標籤(NPR-34117)。

* 在 [!DNL Experience Manager Sites] 頁面上，該頁面顯示下列錯誤訊息，不允許您新增任何元件(NPR-33858):

   `DevTools failed to load SourceMap: Could not load content for <Link>. HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE`

* 選取 **[!UICONTROL 在伺服器上重新驗證]** 屬性和上傳多個附件，適用性表單無法提交(NPR-33701)。

* 選取 **[!UICONTROL 使用頁面語言]** 和 **[!UICONTROL 表單涵蓋頁面的整個寬度]** 選項 [!DNL Experience Manager Forms] 元件 [!DNL Experience Manager Sites] 頁面，頁面無法翻譯(NPR-33641)。

* 提交內嵌於 [!DNL Experience Manager Sites] 頁面中，analytics無法正常運作(NPR-31359)。

* 移除對 [!DNL Lodash] 和 [!DNL backbone] 資料庫(NPR-33458)。

* 此 **[!UICONTROL 提交到REST端點]** 提交動作在適用性表單中無法運作(NPR-34513)。

* 協助工具：當您嘗試提交適用性表單但未上傳必填欄位的附件時，焦點不會自動移至附件欄位(NPR-34511)。

* 未針對 [!DNL Forms] 元件傳送資訊給用戶端時(NPR-33611)。

**工作流程**

* [!DNL Experience Manager] 工作流程清除作業失敗並顯示下列錯誤訊息(NPR-33576):

   `java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory`

* 安裝時 [!DNL Experience Manager] 6.4.8.1 [!UICONTROL 待辦事項] 項目清單不會顯示為連結。 的文字 [!UICONTROL 待辦事項] 項目包含HTML標籤(NPR-34318)。

**後端整合**

* 無法在托管的AWS中設定表單資料模型 [!DNL Experience Manager Forms Linux] 環境(NPR-33617)。

**設計工具**

* 當 [!DNL Acrobat DC] 安裝在 [!DNL Experience Manager] Forms伺服器、 **[!UICONTROL 分發表單]** 選項在 [!DNL Experience Manager Designer] 6.x版(NPR-34325)。

**文件安全性**

* 安裝後，無法在PDF檔案中使用基於HSM的證書執行Sign操作 [!DNL Experience Manager] 6.4.8.0(NPR-34309)。

**升級**

* 升級 [!DNL JBoss] 7.0.9版 [!DNL Experience Manager Forms] 在 [!DNL Linux] 環境中，會導致錯誤(CQ-4300546)。

如需安全性更新的詳細資訊，請參閱 [Experience Manager安全性佈告欄頁面](https://helpx.adobe.com/security/products/experience-manager.html).

### Adobe Experience Manager 6.4.8.1 {#experience-manager-6481}

AEM Cumulative Fix Pack 6.4.8.1為重要更新，包含自2020年3月正式發行AEM 6.4 Service Pack 8(6.4.8.0)以來累積的多項內部及客戶修正。

AEM Cumulative Fix Pack 6.4.8.1 依存於 AEM 6.4 Service Pack 8。因此，您必須先安裝AEM 6.4 Service Pack 8，才能安裝AEM Cumulative Fix Pack 6.4.8.1套件。

AEM 6.4.8.1的部分關鍵重點為：

* 不允許匿名訪問CRXDE Lite以增強安全性。 而是將使用者導向登入畫面。 請參閱 [使用CRXDE Lite開發](/help/sites-developing/developing-with-crxde-lite.md).
* 移除與Adobe Experience Manager的套件共用整合。
* 內建存放庫 (Apache Jackrabbit Oak) 更新至 1.8.21 版。

如需CFP和其他發行版本的相關資訊，請參閱 [AEM更新發行工具定義](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.1修正下列問題。

#### 網站 {#sites-6481}

* 匿名使用者可存取CRX DE Lite功能(NPR-33522)。
* 當LiveCopy中的本機元件名稱與Blueprint中的元件名稱相同，且從Blueprint中推出元件時，_msm_moved一詞不會新增至本機元件的名稱(NPR-33207)。
* 重新導向URL中不包含附加至原始請求的參數(NPR-33174)。
* 當Coral.Select選項設定emptyOption=true或包含值= &quot;&quot;的預設項目時，dropdownshowhide.js檔案會發生錯誤：未捕獲的類型錯誤：component.getValue不是函式(NPR-33163)。
* 當元件包含其他元件作為data-sly-resource時，父容器元件預留位置會取代為內部元件預留位置(NPR-33119)。
* 將內容片段建立在架構上且其中包含強制文字區域或路徑欄位時，內容片段無法儲存(NPR-33007)
* 使用現成可用的體驗片段元件建立自訂元件並在AEM Sites頁面中使用時，AEM不會顯示自訂元件的參考（用法）(NPR-32852)。
* 當AEM Sites頁面屬於具有多個即時副本的大型內容集時，頁面版本歷史記錄預覽無法載入(NPR-32772)。
* 促銷啟動時，會將「cq:LiveRelationship」mixin新增至啟動中新增的每個元件。 無論啟動是否使用或未選取 — Inherit source page live data — 選項(NPR-32664)建立，它都會影響所有啟動。
* 分頁開始時，體驗片段選擇器不會載入所有項目(NPR-32605)。
* 無法為AEM Sites頁面建立啟動。 建立啟動會導致錯誤(NPR-32544)。
* 「管理出版物」未在啟動工作流程請求中納入參考的資產(NPR-32463)。
* Dispatcher健康狀況檢查顯示 `Invalid cookie header` 記錄檔中出現警告訊息(NPR-33630)。
* Salesforce整合容易受到SSRF攻擊(NPR-32671)。
* PreferencesServlet中反映的XSS(NPR-33439)。

#### 資產 {#assets-6481}

* 資產計數不會因清單檢視中選取項目的變更而變更(NPR-33285)。

* 選擇父節點（其中顯示單個子資料夾）然後選擇子資料夾時未啟用「下一步」按鈕(NPR-33284)。

* 啟用DMS7或混合模式時，無法針對沒有存放庫根目錄讀取存取權的使用者呈現觸控式UI（發生錯誤）(NPR-33175)。

* 資料夾和資產名稱中GB18030個字元在下載的zip檔案中會變更為空白(NPR-33150)。

* 系統會在智慧型裁切位於父資料夾內帶點的資產時，建立額外的資料夾 `.` 字元(NPR-32755)。

* 未觸發延遲載入，且選取以檢閱通知收件匣中的工作時不會顯示超過100個資產(NPR-32749)。

* 共用集合的連結頁面因coral-info中的變更而中斷(NPR-32510)。

* 大量上傳時的資產處理停滯(CQ-4293916)。

* SSRF在Experience Manager中的漏洞(NPR-33437)。

#### 平台 {#platform-6481}

* 此 [!DNL Sling] 若 `sling:match` 對應項目建立於 `/etc/maps` (NPR-33308)。
* 停用頁面時會觸發所有排清代理(NPR-32941)。
* 若您使用 `ScriptProcessor` 為縮小JavaScript程式庫，記錄檔會顯示錯誤訊息，指出JavaScript程式碼不符合嚴格模式。 API不提供啟用或停用嚴格模式的選項。 (NPR-32746).
* SQL查詢執行較長的時間（例如7小時）時，AEM停止回應(NPR-33043)。

#### 使用者介面 {#ui-6481}

* 使用選擇對話框搜索或瀏覽路徑時，選擇對話框顯示所選JCR節點的所有內容，而不只顯示影像(NPR-32712)。

#### 翻譯專案 {#tranlation-6481}

* A `NullPointerException` 執行翻譯工作時記錄中出現錯誤(NPR-32220)。

#### 整合 {#integrations-6481}

* 適用於JSON的跨網站指令碼(NPR-32745)。

#### 社群 {#communities-6481}

* 建立新群組後，作者不會重新導向至 [!UICONTROL 社群群組] 一節 [!DNL Internet Explorer] 11(NPR-33202)。
* 存取 [!UICONTROL 活動資料流] 第(NPR-33152)頁。
* 編輯 [!DNL Communities] 群組和變更縮圖影像不會更新群組縮圖影像(NPR-32603)。
* 建立使用者產生內容(UGC)的通知和訂閱版本時，儲存的來源頁面ID不正確(CQ-4289703)。
* 跨網站指令碼問題(NPR-33212)。

#### 工作流程 {#workflow-6481}

* 當使用者完成包含的工作流程時，某些元件不會顯示在彈出式對話方塊上 [!UICONTROL 對話參與者步驟] (NPR-32989)。

* 此 [!UICONTROL 時間表] 左側邊欄中的選項載入所需時間超過預期(NPR-32850)。

#### Forms {#forms-6481}

>[!NOTE]
>
>AEM Cumulative Fix Pack不包含AEM Forms的修正。 會使用個別的Forms附加套件來傳送。 此外，已發行包含JEE上AEM Forms修正的累積安裝程式。 如需詳細資訊，請參閱 [安裝AEM Forms附加元件套件](#install-aem-forms-add-on-package) 和 [安裝AEM Forms JEE安裝程式](#install-aem-forms-jee-installer).

* 通信管理：當使用者貼入 [!DNL Word] 文檔，文本文檔片段不保留格式(NPR-33213)。
* 適用性Forms:適用性表單字典中字串的新行會新增 `&#xa;` 字元加到字典(NPR-33265)。
* 適用性Forms:使用者無法儲存包含多個附件的最適化表單(NPR-33214)。
* 適用性Forms: `AddInstance` 和 `RemoveInstance` 例項管理器類別的方法不會在上新增延遲載入片段的例項動態數量 [!DNL Internet Explorer 11] (NPR-33201)。
* 適用性Forms:在內嵌於 [!DNL Sites] 頁面沒有記錄提交和放棄事件的資料(NPR-31359)。
* 適用性Forms:當使用者貼上 [!DNL Word] 將檔案記錄至最適化表單並提交，提交的最適化表單包含unicode字元。 此外，PDFPDF/A轉換因Unicode字元而失敗(NPR-33348)。
* 後端整合：由於重新整理代號因非作用中狀態不正確而過期，表單資料模型請求會失敗(NPR-33168)。
* 文檔服務：由於缺少Gibson jar，轉換PDF服務無法將PDF文檔轉換為PostScript [!DNL WebLogic] 在 [!DNL Linux] 伺服器(NPR-33515、CQ-4292239)。
* 文檔服務：當使用者將文字檔轉換為PDF時，日文字元無法正確轉譯(NPR-33239)。
* 使用GuideSOMProviderServlet儲存XSS(NPR-32701)。

## 安裝6.4.8.4 {#install}

### 設定需求 {#setup-requirements}

<!--

>[!NOTE]
>
>For successful installation of AEM 6.4.6.0 on the instance, it is strongly recommended to upgrade the version of com.adobe.granite.oak.s3connector to 1.8.4 for the customers who are on the older version of s3 connector.
>The process of upgrading the com.adobe.granite.oak.s3connector is available at [https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html](https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html).
>Download the latest version of com.adobe.granite.oak.s3connector from: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

-->

>[!CAUTION]
>
>若Adobe的AEM 6.4已安裝Feature Pack，則適用於此客戶。Feature Pack由客戶提供，且依賴於發行版本和Service Pack。 若您已安裝任何Feature Pack，請聯絡AEM客戶服務團隊，以驗證這些Feature Pack與此AEM 6.4適用的Cumulative Fix Pack之間的相容性。

* AEM 6.4.8.4需要AEM 6.4.8.0。請造訪 [升級檔案](../sites-deploying/upgrade.md) 以取得詳細指示。
* 在具有MongoDB和多個執行個體的部署上，使用套件管理器在其中一個製作執行個體上安裝AEM 6.4.8.4。
* 安裝Cumulative Fix Pack之前，請務必擁有AEM執行個體的快照或全新備份。
* 安裝前重新啟動執行個體。 雖然只有在執行個體仍處於更新模式時才需要這麼做（這是從舊版更新執行個體時的情況），但一般建議執行個體執行較長的時段。

>[!NOTE]
>
>Adobe不建議移除或解除安裝AEM 6.4.8.4套件。

### 安裝Cumulative Fix Pack {#install-cumulative-fix-pack}

執行以下步驟來在現有 AEM 6.4.8.0 執行個體上安裝 Cumulative Fix Pack：

1. 按一下 [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-4.0.zip) 連結即可下載套件。

1. 開啟[套件管理器](http://localhost:4502/crx/packmgr/index.jsp)，然後按一下&#x200B;**[!UICONTROL 「上傳套件」]**&#x200B;即可上傳套件。

1. 選取套件名稱並按一下&#x200B;**[!UICONTROL 「安裝」]**。

>[!NOTE]
>
>**在安裝6.4.8.4期間，Package Manager UI的對話方塊有時會過早退出**
>
>因此，建議在存取執行個體之前，等待錯誤記錄穩定下來。 在確保安裝成功之前，用戶必須等待與卸載更新程式捆綁相關的特定日誌。 這通常會在Safari上發生，但可能會在任何瀏覽器上間歇性發生。

### 自動安裝 {#auto-installation}

有兩種方式可自動將AEM 6.4.8.4安裝至執行中的執行個體：

A.將套件放入……*/crx-quickstart/install* 資料夾。 套件便會自動安裝。

B.使用 [來自套件管理器的HTTP API](https://docs.adobe.com/content/docs/en/crx/2-3/how_to/package_manager.html)  — 請務必使用 `cmd=install&recursive=true`  — 以安裝巢狀套件。

>[!NOTE]
>
>AEM 6.4.8.4不支援安裝Bootstrap。

### 驗證安裝 {#validate-install}

1. 產品資訊頁面(*/system/console/productinfo*)現在應在「已安裝產品」下顯示更新的版本字串「Adobe Experience Manager, 6.4.8.4版」。
1. 在 OSGI 控制台 (使用 Web 控制台：/system/console/bundles) 中，所有 OSGI 套件組合均為「作用中」或「片段」。
1. OSGI套件組合org.apache.jackrabbit.oak-core的版本為1.8.17或更新版本(使用Web主控台：/system/console/bundles)。

若要決定要透過此版本的AEM Sites和Assets執行，請參閱 [技術需求](../sites-deploying/technical-requirements.md).

>[!NOTE]
>成功安裝套件時，會顯示資訊性訊息，指出已成功安裝內容套件，例如 **&quot;已成功安裝AEM-6.4-Service-Pack-8內容包。&quot;**

### 更新Dynamic Media檢視器(5.10.1) {#update-dynamic-media-viewers}

AEM 6.4.8.4包含新版Dynamic Media檢視器(5.10.1)，可啟用在「影像預設集」頁面上檢查重複名稱。 建議Dynamic Media客戶執行下列命令，將方塊檢視器預設集開啟至最新狀態。

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

會將新的檢視器預設集複製到/conf位置。

### 安裝AEM Forms附加元件套件 {#install-aem-forms-add-on-package}

>[!NOTE]
>
>[!DNL Experience Manager Forms] 會在排程的[!DNL Experience Manager] Cumulative Fix Pack 發行日期一週後發行附加元件的套件。

>[!NOTE]
>
>如果您未使用AEM Forms，請略過。 AEM Forms中的修正是透過個別的附加套件提供。

1. 確認您已安裝AEM Cumulative Fix Pack。
1. 下載列於的對應表單附加套件 [AEM Forms版本](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#forms-updates) 作業系統。
1. 依照 [安裝AEM Forms附加元件套件](https://docs.adobe.com/content/help/en/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package).

### 安裝AEM Forms JEE安裝程式 {#install-aem-forms-jee-installer}

>[!NOTE]
>
>如果您沒有在JEE上使用AEM Forms，請略過。 AEM Forms JEE 中的修正是透過單獨的安裝程式提供。

如需安裝AEM Forms JEE的累積安裝程式和部署後設定的相關資訊，請參閱 [AEM Forms JEE修補程式安裝程式](jee-patch-installer-64.md).

>[!NOTE]
>
>在JEE上安裝Experience Manager Forms的Cumulative Installer後，請安裝最新的Forms附加元件套件，從 `crx-repository\install` ，然後重新啟動伺服器。

### Uber Jar {#uber-jar}

適用於AEM 6.4.8.4的Uber Jar可於 [Maven Central存放庫](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.4.8.4/).

若要在 Maven 專案中使用 Uber Jar，請參閱[如何使用 Uber jar](../sites-developing/ht-projects-maven.md) 一文，並在您的專案 POM 中加入以下相依性：

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8.4</version>
      <scope>provided</scope>  
</dependency>
```

>[!NOTE]
>
>Maven中央存放庫提供UberJar和其他相關成品，而非AdobePublic Maven存放庫(repo.adobe.com)。 主要UberJar檔案已重新命名為 `uber-jar-<version>.jar`. 因此，沒有 `classifier`，使用 `apis` 作為值，對於 `dependency` 標籤。

## 已移除/已棄用的功能 {#removed-deprecated-features}

本節列出 AEM 6.4 已移除或棄用的特色和功能。

| 區域 | 功能 | 替代方案 | 版本 |
|---|---|---|---|
| 資產 | 管理子資產的標籤動作 | 無替換 | AEM 6.4.2.0 |
| Assets 與 Adobe Creative Cloud 整合 | AEM 6.2 引入了 [AEM 對 Creative Cloud 資料夾共用](https://docs.adobe.com/content/help/zh-Hant/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html)功能，作為讓 Creative 使用者存取 AEM 資產的方式。Creative Cloud 應用程式推出的新功能 Adobe Asset Link 提供了更優異的使用者體驗，以及更強大的存取功能，可直接從 Photoshop、InDesign 和 Illustrator 中存取 AEM 的資產。 Adobe 將不會再對資料夾共用功能提供近一步的增強項目。雖然AEM中包含此功能，但強烈建議客戶使用取代。 | Adobe資產連結或案頭應用程式。 如需更多資訊，請參閱 [AEM Creative Cloud 整合](/help/assets/aem-cc-integration-best-practices.md)文章。 | AEM 6.4.4.0 |

## 已知問題 {#known-issues}

* 如果您從 [!DNL Experience Manager] 6.4至 [!DNL Experience Manager] 6.5，部分套件可能無法將其狀態顯示為 `Active`. 安裝最新 [!DNL Experience Manager] 6.5 Service Pack以解決問題。

如需AEM 6.4.8.0 Service Pack已知問題的相關資訊，請參閱 [AEM 6.4.8.0 Service Pack發行說明](sp-release-notes.md).

## 包含的 OSGi 套件組合和內容套件 {#osgi-bundles-and-content-packages-included}

下列文字檔案列出AEM 6.4.8.4中包含的OSGi套件組合和內容套件。

AEM 6.4.8.4 中包含的 OSGi 套件組合清單

[取得檔案](assets/6.4.8.4_osgi_bundles.txt)

AEM 6.4.8.4 中包含的內容套件清單

[取得檔案](assets/6.4.8.4_content_packages.txt)

## 實用資源 {#helpful-resources}

* [AEM 6.4 發行說明](../release-notes/release-notes.md)
* [AEM 產品頁面](https://www.adobe.com/solutions/web-experience-management.html)
* [AEM 6.4 檔案](https://helpx.adobe.com/tw/support/experience-manager/6-4.html)
* 訂閱 [Adobe 優先產品更新](https://www.adobe.com/tw/subscription/priority-product-update.html)

## 受限網站 {#restricted-sites-new}

這些網站僅供客戶使用。 如果您是Adobe，且需要存取權，請連絡您的客戶經理。

* [透過licensing.adobe.com下載產品](https://licensing.adobe.com/)
* [聯絡客戶支援](https://docs.adobe.com/content/help/en/customer-one/using/home.html)

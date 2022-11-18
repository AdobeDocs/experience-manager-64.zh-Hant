---
title: AEM 6.4 Service Pack發行說明
seo-title: AEM 6.4 Service Pack Release Notes
description: Adobe Experience Manager 6.4 Service Pack專屬的發行說明。
seo-description: Release notes specific to Adobe Experience Manager 6.4 Service Packs.
uuid: 49a710a8-7cd5-47de-9a96-7af7f3c00dfc
contentOwner: dekalra
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
discoiquuid: 93067308-e275-490f-8d78-ae79e046059c
exl-id: d0da9390-2167-47ee-82fd-8c81d8d68a3e
source-git-commit: 0f4f8c2640629f751337e8611a2c8f32f21bcb6d
workflow-type: tm+mt
source-wordcount: '21517'
ht-degree: 23%

---

# AEM 6.4 Service Pack發行說明 {#aem-service-pack-release-notes}

## 發行資訊 {#release-information}

| 產品 | **Adobe Experience Manager(AEM)6.4** |
|---|---|
| 版本 | 6.4.8.0 |
| 類型 | Service Pack發行 |
| 日期 | 2020 年 3 月 5 日 |
| 下載 URL | AEM 6.4.8.0開 [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/servicepack/aem-service-pkg-6.4.8.zip) |

## AEM 6.4.8.0包含的項目 {#what-s-included-in-aem}

AEM 6.4.8.0為重要更新，包含自AEM 6.4全面推出以來所推出的新功能、客戶要求的重要增強功能以及效能、穩定性、安全性等改善項目 **2018年4月。**

這也是累積的，也就是說6.4.8.0包含之前發行的所有AEM 6.4 Service Pack。

此Service Pack版本的部分關鍵重點為：

* 內建存放庫 (Apache Jackrabbit Oak) 更新至 1.8.20 版。

* WCM-RTE中的日文網站支援繞排文字功能。

* 日文網站支援分詞和分行處理。

* 已新增支援，可使用BUNSETSU方法在適當位置中斷日文句子和行。

* 用於通信管理的CCR UI現在支援德文地區設定的小數值。

* 使用SOAP Web服務的表單資料模型整合現在支援元素上的選擇群組或屬性。

* AEM Assets現在可透過Brand Portal設定 [!DNL Adobe I/O].

* 將ContextHub中隨附的jQuery版本更新至3.2.1。

## 變更清單 {#list-of-changes}

### Sites {#sites}

* 當AEM Sites頁面的URL包含冒號或百分比符號時，基礎瀏覽器停止回應，而CPU週期顯示尖峰(NPR-32368、NPR-31917)。
* 開啟AEM Sites頁面進行編輯並複製元件時，某些預留位置仍無法使用貼上動作(NPR-32328)。
* 啟動工作流程要求不包含參考的資產(NPR-32304)。
* 建立Blueprint時，如果記錄數超過80，則只會顯示前80個記錄。 Blueprint會為其餘的記錄顯示空白行(NPR-32058)。
* 使用者可以儲存內容片段，而不需在必要欄位中提供任何資訊(NPR-31988)。
* 核心體驗片段元件中設定的路徑無法自動導覽(NPR-31921)。
* 在RTF編輯器(RTE)中變更表格儲存格的類型時，會發生下列錯誤：
   `Error: No common ancestor found, cannot continue` (NPR-31916)。
* 在相同資料夾中移動內容時，停用頁面移動選項(NPR-31841)。
* 新增支援，可使用BUNSETSU方法分割日文句子，並在適當位置加上分行(NPR-31836)。
* 在RTF編輯器(RTE)中編輯超連結時，未儲存新選取的路徑(NPR-31659)。
* 刪除多欄位元件並還原刪除時，元件會還原，但資料不會還原(NPR-31617)。

### Assets {#assets}

* 使用Dynamic Media Classic設定將資產從一個資料夾移至另一個資料夾時，系統會在Dynamic Media Classic中建立沒有名稱的資料夾(NPR-32440)。

* PDF檔案的Experience Manager詳細資訊頁面在Dynamic Media Scene7模式上執行時，沒有顯示動作按鈕(NPR-32316)。

* 無法刪除資產和視訊轉譯(NPR-32213)。

* 針對已排程日期和時間稍後啟動的資產，已排程啟動的日曆圖示不會顯示在「狀態」欄（位於DAM資產清單的傳統UI中）(NPR-32198)。

* 使用「其他」將資產與多個資產相關時，資產關係會遭到覆寫(NPR-32196)。

* 使用者在Dynamic Media用戶端的設定編輯器中未進行任何變更時，儲存按鈕不會匯入遠端設定(NPR-32178)。

* PSD資產擷取造成CPU尖峰和Experience Manager製作執行個體停止回應(NPR-32165)。

* 在Experience ManagerDAM中上傳大型ZIP檔案時發現記憶體不足例外狀況(NPR-32155)。

* 版本記錄URL會顯示在資產屬性頁面的「參考者」欄位下(NPR-31889)。

* 從Brand Portal的「管理出版物」頁面取消發佈會無法顯示已發佈資料夾的子資料夾(NPR-31835)。

* Dynamic Media視訊會在Scene7雲端設定放入私人資料夾時無法上傳 `/conf` 而非 `/conf/global` (NPR-31779)。

* 新增註解後，在Dynamic Media Scene7執行模式上執行的Experience Manager上，時間軸上看不到影像(NPR-31754)。

* 無法使用WinZip開啟從DAM下載的ZIP檔案(NPR-31745)。

### Integrations {#integrations-6480}

* 此 **公司** 和 **報表** 套裝下拉式功能表會隱藏一次 **報表來源** 在Experience Manager雲端服務中設定Adobe Analytics時選取(NPR-31729)。

* 製作連結至Adobe Campaign的電子報語言副本時，Adobe Campaign屬性不會遭到清除，但連結至Adobe Campaign的電子報遭到複製或貼上時，就會發生清除(NPR-32540)。

* ReportSuitesServlet 容易遭受 SSRF 攻擊 (NPR-32161)。

### Sling {#sling-6480}

* 資源觀測的不確定性陰影無法運作(CQ-4286466)。

### 專案 {#projects-6480}

* 即使使用者有在子資料夾中建立專案的權限，使用者仍看不到「建立」按鈕(NPR-31831)。

* 在「專案」中選取「日曆檢視」後，在「卡片檢視」、「清單檢視」和「日曆檢視」之間切換的功能無法運作(NPR-31829)。

### 轉換 {#translation-6480}

* 針對多種語言建立翻譯專案時，只會針對某些語言產生專案，而非全部，且記錄中出現錯誤（資源解析器已關閉）(NPR-32212)。

### WCM-MSM {#wcm-msm-6480}

* 權限問題會導致在Blueprint內移動頁面時顯示錯誤(NPR-32610)。

### WCM頁面編輯器 {#wcm-page-editor-6480}

* 嘗試將元件新增至具有特定URL格式的頁面時，瀏覽器停止回應(NPR-32368、NPR-31917)。

### WCM — 管理員UI {#wcm-admin-ui-6480}

* 管理出版物在啟動工作流程請求中未包含參考的資產(NPR-32304)。

### 社群 {#communities}

* 無法更新組的組縮圖影像(NPR-32603)。

### Brand Portal {#brand-portal}

* AEM Assets中取消發佈中繼資料結構會填入錯誤訊息，不過結構會在後端移除(CQ-4286871)。

### Foundation UI {#foundations-ui-6480}

* 新增至Button元件的URL中顯示無效字元(NPR-32684)。

### Forms {#forms}

>[!NOTE]
>
>AEM Service Pack不包含AEM Forms的修正。 會使用個別的Forms附加套件來傳送。 此外，已發行包含JEE上AEM Forms修正的累積安裝程式。 如需詳細資訊，請參閱 [安裝AEM Forms附加元件套件](#install-aem-forms-add-on-package) 和 [安裝AEM Forms JEE安裝程式](#install-aem-forms-jee-installer).

* 設計器：如果啟用標籤選項，產生的PDF輸出中子表單邊框會消失(NPR-32546、NPR-32322)。

* Designer：如果表格中有合併的儲存格，協助工具測試就無法輸出透過輸出服務從 XDP 表單轉換而來的 PDF 檔案 (NPR-32079)。

* 檔案安全性：將DisableGlobalOfflineSynchronizationData選項設為True時，受保護的PDF檔案無法離線開啟(NPR-32080)。

* 檔案安全性：從ES4升級至AEM 6.3後開啟受保護的PDF檔案時發生問題(NPR-32170)。

* 文檔服務：嘗試使用toPDFA轉換方法將PDF檔案轉換為PDF/A檔案時，系統會顯示錯誤訊息(NPR-32663)。

* 文檔服務：在PDF檔案上套用Reader延伸模組服務時顯示例外狀況(NPR-32639)。

* 文檔服務：將XDP檔案組裝和轉換為PDF檔案時，系統會顯示錯誤訊息(NPR-31821)。

* 在網站頁面上提交或放棄表單時，Analytics沒有顯示適當的結果(NPR-31359)。

### 先前Service Pack包含的Hotfix和Feature Pack {#hotfixes-and-feature-packs-included-in-previous-service-packs}

#### AEM 6.4.7.0 {#experience-manager-6470}

AEM 6.4.7.0為重要更新，包含效能、穩定性、安全性和重要客戶修正，以及自AEM 6.4全面推出以來所發行的增強功能， **2018年4月。**

這也是累積的，也就是說6.4.7.0包含之前發行的所有AEM 6.4 Service Pack。

AEM 6.4.7.0的部分關鍵重點為：

* 內建存放庫 (Apache Jackrabbit Oak) 更新至 1.8.17 版。
* 新增在刪除Sites頁面時設定版本的支援。
* 已新增建立日期的欄（可排序），並已新增至 **DAM清單** 檢視資產搜尋結果 **清單** 檢視(NPR-31311)。
* 根據 **名稱** 欄允許於 **清單** 檢視。
* 重新處理和批次上傳的批次大小和工作流程步驟逾時現在可從Dynamic Media的UI設定。
* 此 `pdfBrochure` 已在Scene 7雲端設定中設為false，以在IPS儲存記憶體。

##### 資產 {#assets-6470}

**產品增強功能**

* API套件的匯出版本 `package com.day.cq.dam.handler.standard.msoffice` 支援 `dam-handler` 套件組合已升級至6.0.0(CQ-4279059)。
如果您使用套件 `com.day.cq.dam.handler.standard.msoffice` 在自訂實作中，建議您將 `dam-handler` 與最新的uber jar捆綁。

* 已在DAM清單檢視和清單檢視的資產搜尋結果中新增可排序的建立日期欄(NPR-31311)。

* 清單檢視中允許依名稱欄進行資產排序(NPR-31299)。

**修正**

* 某些PDF檔案的中繼資料沒有更新，且未在修改其標題時儲存至PDF(NPR-31575)。

* 無法刪除檔案名稱中帶有「+」符號的資產(NPR-30588)。

* DAM資料夾屬性沒有顯示封閉使用者群組中新增的使用者或群組（由LDAP同步建立）(NPR-30555)。

* 電子郵件範本主旨行中出現的特殊字元未正確顯示(NPR-30547)。

* 在Dynamic Media Scene 7執行模式中執行的AEM中，將資產從一個資料夾移至另一個資料夾時，資產名稱會變更為小寫(NPR-31631)。

* 在DAM中建立影像集（或mediaset）並以適當的命名慣例命名時，影像集的名稱在Scene 7中會變更為小寫(NPR-31576)。

* Dynamic Media 「編碼視訊」工作流程無法為從Scene 7移轉至Dynamic Media - Scene 7執行模式的視訊產生縮圖(NPR-31523)。

* 在Dynamic Media - Scene 7執行模式上執行的AEM中，使用篩選器來搜尋集時發現內部伺服器錯誤(NPR-31388)。

* 針對位於與Scene 7公司名稱相同之資料夾中的影像，在編輯遠端影像集時發現錯誤(NPR-31347)。

* 未發佈包含參考的資產(DM)(NPR-31179)。

* 針對 Dynamic Media 混合模式設定的到期 (用戶端快取的存留時間) 值沒有複製到 Dynamic Media 交付環境中 (NPR-31126)。

* 從AEM Dynamic Media上傳 — Scene 7執行模式上傳至Scene 7所花的時間太長，無法完成(NPR-30926)。

* 發佈相同元件時建立含有Dynamic Media元件的頁面後，從在Dynamic Media - Scene 7執行模式上執行的製作執行個體，系統會提示使用者發佈dmscene7設定(NPR-30880)。

* 在Dynamic Media - Scene 7上變更「移動後標題」和「移動後名稱」欄位中的值後，檢視器內嵌程式碼中「asset」參數的值維持不變(NPR-30745)。

* 觸控式UI搜尋（透過Omnisearch完成）結果頁面會自動向上捲動並遺失使用者的捲動位置(NPR-31306)。

* 「DAM事件清除」會刪除最新(maxSavedActivities)事件資料，並保留先前建立的資料(NPR-30870)。

* 將操作移至在選取資產時觸發無限捲動的目的地資料夾後，資產標題和名稱變更不會持續存在(NPR-30647)。

* 在從「Adobe資產連結」存取的AEM Assets中套用任何篩選器時，系列會從檢視中移除(CQ-4280534)。

* 重新處理和批次上傳的批次大小和工作流程步驟逾時無法從UI設定，且需在CRXDE中設定，且工作流程需要同步兩次(CQ-4281254)。

* 批次上傳的工作流程步驟名稱和簡單的上傳步驟在Scene 7中相同，因此造成混淆(CQ-4281176)。

* 如果資產遺失中繼資料節點，Scene7中的重新處理工作流程就會卡住(CQ-4281170)。

* 具有視訊資產的資料夾(CQ-4280630)無法使用重新處理工作流程中的BatchUpload步驟。

* 傳送至DM的PDF選項預設會將extractKeywords設為true(CQ-4280101)。

* 在包含非DM資產的資料夾上執行Scene 7重新處理工作流程時，發現Null點例外狀況(CQ-4279555)。

* 當場景7中已存在名稱重複的資產時，AEM中的資產重新命名無法同步至場景7(CQ-4276763)。

* 具有讀取權限的使用者嘗試開啟資產時，透過電子郵件傳送的Zip檔案無法解壓縮(CQ-4277925)。

* PPT轉譯工作流程無法產生上傳PPT檔案的轉譯，因為AEM 6.4無法更新至com.adobe.granite.poi 2.0.28版(CQ-4279059)。

* PDF檔案沒有編列索引，且內容無法搜尋(CQ-4278916)。

##### 網站 {#sites-6470}

* 當啟動以「僅促銷已修改的頁面」升級，並完成具有已修改頁面的「促銷」啟動時，只有已修改的頁面似乎會升級。 此外，當要升級的清單正確時，未修改的頁面仍顯示在清單底部(NPR-31314)。

* AEM Sites頁面移至不同位置時，其屬性不會因此更新以反映其新位置(NPR-31265)。

* 對於新的Blueprint，如果記錄數超過40，則只會顯示前40個記錄。 Blueprint會為其餘的記錄顯示空白行(NPR-31182)。

* 當LiveCopy數量很大時，LiveCopy概觀會花很長的時間來呈現預覽(NPR-30945)。

* 新增在刪除頁面時設定頁面版本的支援。 如果已刪除頁面的版本設定已停用，AEM Sites將無法還原這類頁面(NPR-30891)。

* 當使用者在功能表的description屬性中新增日文或韓文字元時，功能表會顯示日文和韓文文字的扭曲字元(NPR-31331)。

* 當使用者聚焦於左方邊欄的欄位，並使用鍵盤快速鍵貼上內容時，貼上了頁面編輯器剪貼簿的內容，而非左方邊欄的欄位內容 (NPR-31169)。

* 使用者編輯內容片段時，系統復原了已刪除的內容片段變化 (NPR-31178)。

* 內容片段模型查詢效率低下。 如果執行個體有許多頁面且導致錯誤，則速度會很慢(NPR-30666)。

* 儲存內容片段模型時，日期和時間欄位中的時間會設為00:00(NPR-30540)。

##### 整合 {#integrations-6470}

* 設定AdobeLaunch時，程式庫URL中會加上正斜線(/)(NPR-30700)。

* 發佈後ContextHub效能會下降(NPR-30884)。

##### Sling {#sling-6470}

* 將webconsole安全提供程式套件組合版本更新為1.2.4，以從webconsolesecurityprovider移除launchpad啟動器api的相依性(NPR-30885)。

##### 平台 {#platform-6470}

* 未儲存 Jetty 型 HTTP 服務的緩衝區大小設定更新 (NPR-30925)。

* QueryBuilder現在支援xpath查詢中的orderby fn:name()(NPR-31322)。

* 將Sling分散式事件管理員更新至1.1.4版，以改善叢集環境中記錄檔的品質(NPR-29256)。

##### Foundation UI {#foundation-6470}

* 捲動至結果頁面結尾處並含有大量搜尋結果，會導致瀏覽器當機(NPR-31332)。

* 從卡片檢視切換為搜尋結果頁面上的清單檢視時，可能會有延遲而無法捲動頁面(NPR-31280)。

##### Oak {#oak-6470}

* 副檔名包含JPEG影像的.docx和.xlsx的MS Office檔案無法使用Tika剖析器來剖析(NPR-31693)。

##### Livefyre {#livefyre-6470}

* 將DITA外掛程式用於合成資源時，與AEM 6.4升級的Livefyre整合會產生Null點例外狀況。 不過，當手動新增元件時，整合便可運作(FYR-11066)。

##### 轉換 {#translation-6470}

* 提升啟動頁面時沒有更新目標體驗片段的路徑(NPR-30830)。

##### 社群 {#communities-6470}

* 在某些情況下，即使在通知設定中啟用電子郵件訊息，系統仍在NotificationsActivityStreamProvider中擲回例外狀況(NPR-31521)。
* 無法建立新成員，在AEM製作執行個體的「建立成員」畫面上會顯示空白畫面(NPR-30951)。
* 使用者無法在Internet Explorer 11的部落格上張貼意見(NPR-30927)。
* 限制群組的管理員無法檢視群組卡片，無法在AEM製作執行個體中執行任何快速連結作業（編輯/發佈/刪除群組）(NPR-30810)。
* 在AEM製作例項中建立新網站時，看不到成員群組/群組資訊(NPR-28840)。

##### Forms {#forms-6470}

>[!NOTE]
>
>AEM Service Pack不包含AEM Forms的修正。 會使用個別的Forms附加套件來傳送。 此外，已發行包含JEE上AEM Forms修正的累積安裝程式。 如需詳細資訊，請參閱 [安裝AEM Forms附加元件套件](#install-aem-forms-add-on-package) 和 [安裝AEM Forms JEE安裝程式](#install-aem-forms-jee-installer).

**Forms 附加元件套件**

**調適型表單**

* 將最適化表單當地語系化時，字串會包含字典索引鍵(NPR-31109)。

* Forms中的核取方塊和下拉式清單會失敗協助工具檢查(NPR-31282)。

**HTML5 Forms**

* 新增子表單的例項時，產生 XDP 表單的 HTML5 預覽後出現閃爍畫面 (NPR-30907)。

**OSGi的檔案服務**

* 使用com.adobe.fd.assembler.service.AssemblerService.invoke()方法運行多個同時運行的線程來裝配表單，顯示一條錯誤消息(NPR-31164)。

* 組合器服務建立的臨時檔案不會自動刪除，需要AEM重新啟動(NPR-30846)。

* 將ReaderExtension權限套用至PDF會導致錯誤訊息(NPR-30930)。

**工作流程**

* OSGi工作流程因CPU使用率100%而失敗(NPR-31234)。

**Forms - JEE 安裝程式**

**文件服務**

* 轉換PDF服務無法將PDF檔案轉換為PostScript並顯示錯誤訊息(NPR-31267)。

* 套用修補程式以修正HTML至PDF失敗後，SOAP端點設定會重設(NPR-31309)。

**PDFG 服務**

* 無法上傳使用管理員UI下載的Adobe PDF設定檔案(NPR-31273)。

#### AEM 6.4.6.0 {#experience-manager-6460}

AEM 6.4.6.0為重要更新，包含效能、穩定性、安全性和重要客戶修正，以及自AEM 6.4全面推出以來所發行的增強功能， **2018年4月。**

這也是累積的，也就是說6.4.6.0包含之前發行的所有AEM 6.4 Service Pack。

AEM 6.4.6.0的部分關鍵重點為：

* 內建存放庫 (Apache Jackrabbit Oak) 更新至 1.8.15 版。
* 新增在基礎API中追蹤事件中追蹤動態UI狀態的支援。
* 新增轉譯支援至影像核心元件。

**Assets**

* 資料夾的資產共用連結，包含空格和 `&` 名稱中的字元會針對某些資產顯示空白灰色卡片。 NPR-29934：CQ-4270187 的 Hotfix
* 為AEM建立MP4資產時DAM工作流程當機。 NPR-30031：CQ-4271352 的 Hotfix
* Adobe 智慧標記透過 Datapower 連線的問題。NPR-30026：CQ-4269457 的 Hotfix
* 使用OmniSearch找不到PDF。 NPR-30046：GRANITE-26290 的 Hotfix
* ACP API產生的URL和資料夾中繼資料中的資產路徑未經URL編碼。  GRANITE-26198:CQ-4271814的Hotfix
* 由於未定義的裝載，「建立審核」任務功能無法運作。 NPR-30469:Hotfix CQ-4274263
* 在資產選擇器上執行OmniSearch後，可從卡片檢視切換至清單檢視（反之亦然）的功能會消失。 NPR-29852：CQ-4269369 的 Hotfix
* （觸控式UI）在管理發布精靈期間，新增頁面後，資產會新增至復寫佇列，因此會在幾秒後顯示部分資產。 NPR-29985：CQ-4270724 的 Hotfix
* 依關聯性排序搜尋查詢會傳回InDesign檔案以及InDesign範本。 CQ-4273864 的 Hotfix
* 如果使用者的電子郵件ID為大寫，使用者將無法登入先前已登出的資產。 CQ-4276575 的 Hotfix
* 在中設定Dynamic MediaCloud Services `DMHybrid` 模式會在AEM中建立多個空的報表套裝，且上未儲存任何報表套裝id，導致報表套裝重複。 CQ-4276855 的 Hotfix
* 在「受管理的標籤」頁面中促銷時，未顯示警告對話方塊。 CQ-4252851 的 Hotfix
* 使用輪播管理標籤時，導覽按鈕無法運作。 CQ-4275499 的 Hotfix
* 大量移動資產功能損毀，導致資產無法移動。 CQ-4272987 的 Hotfix

**Sites**

* `pageinfo.json` 請求極為緩慢，載入時間太長。 NPR-29709：CQ-4269560 的 Hotfix
* `onTime` 或 `offTime` 如果AEM伺服器重新啟動，系統不會重新叫用資產上儲存的中繼資料屬性。 NPR-30413：CQ-4272784 的 Hotfix
* 由於ConfigPostProcessor類的行為不正確，暫停的上層頁面會移除cq:來自子頁面的LiveRelationship混合類型。 NPR-30536、NPR-30510：CQ-4254113 的 Hotfix
* 在Campaign編輯頁面的「開始」工作流程對話方塊上，出現跨網站指令碼(XSS)。 NPR-29747：CQ-4271067 的 Hotfix
* （傳統UI）工作流程鎖定階段會停用工作流程標籤，直到解除鎖定為止。 NPR-30356：CQ-4237557 的 Hotfix
* (IE11)在RTF編輯器元件中貼上HTML內容時，若以defaultPasteMode = platext，則HTML會貼上格式，因此，defaultPasteMode沒有作用。 NPR-30045：GRANITE-26094 的 Hotfix
* （傳統UI）重新載入網站管理頁面時，「新增」功能表中的所有下拉式清單項目都會停用。 NPR-29980：CQ-4272044 的 Hotfix
* 無法將樣式新增至文字或編輯在內容上創作的任何現有樣式。 NPR-29712：CQ-4266249 的 Hotfix
* （傳統UI）無dc的資產：「路徑」欄位對話方塊瀏覽器中未列出標題值。 NPR-30166:CQ-88858的反向移植請求
* cq:即使新增parsys元件後，監聽器仍無法搭配巢狀元件運作。 NPR-30422：CQ-4274863 的 Hotfix
* AEM 和 Campaign 整合期間出現 ContextHub 錯誤。NPR-30625：CQ-4250790 的 Hotfix
* 系統將 resourceType 請求參數的值複製到 HTML 標記屬性 (以雙引號包圍) 的值中。NPR-29832：CQ-4255365 的 Hotfix
* 元件從一個頁面複製並貼至另一個頁面後，就需要重新整理頁面。 NPR-29982：CQ-4256019 的 Hotfix
* 不支援從頁面別名發佈/取消發佈，因此應移除。 NPR-30062：CQ-4271249 的 Hotfix
* ExperienceFragmentsReplicationListener中無結尾標籤的資源解析器警告，會導致一段時間內出現穩定性問題，強制重新啟動AEM例項。 NPR-30416：CQ-4257521 的 Hotfix
* 移動超過150個頁面中參照的體驗片段，不會修改參照頁面中的fragmentPath。 NPR-30556：CQ-4274900 的 Hotfix
* 開啟包含字元貨幣(`$`)和大括弧(`{`)一個接一個。 CQ-4270266 的 Hotfix
* 嘗試在時間軸中顯示體驗片段版本時， NullPointerException中的VersionPreviewServlet失敗。 NPR-30074：CQ-4271881 的 Hotfix
* 無法透過簽入功能鎖定內容片段。 NPR-29923：CQ-4258785 的 Hotfix
* SAML驗證處理常式中的簽名驗證失敗。 NPR-30379:GRANITE-26567的反向移植請求

**複寫**

* JCR工作階段/資源解析程式在OAuth實作期間，每次復寫至MAC / Brand Portal時都會遭到洩漏。 NPR-30000：Granite-26196 的 Hotfix

**Sling**

* 使用重疊和之前順序受影響的子代的順序導致IndexOutOfBoundException。 NPR-30408:Sling-8296和Sling-7375的Hotfix
* 保存InactiveBundlesHealthCheck配置後，InactiveBundlesHealthCheck將讀取MissingPackagesHealthCheck配置。 NPR-30084：CQ-4272644 的 Hotfix

**商務**

* 無法從Sites主控台執行目錄Blueprint。 NPR-29829：CQ-4271461 的 Hotfix
* 產品中使用的資產不會在資產的「參考」區段中顯示任何對產品的參考，而資產路徑在移動資產時不會更新。 NPR-30542：CQ-4270247 的 Hotfix

**平台**

* AEM預設郵件傳送者無法透過TLS v1.2傳送郵件至遠端SMTP伺服器。NPR-30476:GRANITE-26605的Hotfix

**社群**

* 在作者上刪除的群組未與所有發佈者同步。 NPR-29987：CQ-4268738 的 Hotfix
* 從「社區管理員」欄位刪除的用戶不與「成員」組同步。 NPR-30389：CQ-4274339 的 Hotfix
* 管理員群組的使用者沒有該群組的快速連結。 NPR-30546：CQ-4275579 的 Hotfix
* 更新任何新建立和現有的社群群組會覆寫jcr上的屬性：內容節點，並將其名稱變更為第一頁的標題。 NPR-30109：CQ-4273719 的 Hotfix
* 當社群設為與資料庫儲存資源提供者(DSRP)搭配使用時，透過位置和位址快速搜尋和搜尋無法運作。 NPR-26737：CQ-4258493 的 Hotfix

**轉換**

* 自動執行翻譯無法運作。 NPR-30499：CQ-4276288 的 Hotfix
* 使用者可以在限制為唯讀的內容路徑上建立語言副本。 NPR-29937：CQ-4270708 的 Hotfix
* 翻譯問題 - 使用機器翻譯時只翻譯了幾個元件。NPR-30079：CQ-4273764 的 Hotfix

**整合**

* 在重新啟動執行個體之前，自訂內容無法在發佈執行個體上正確顯示。 NPR-30421：CQ-4273706 的 Hotfix

**專案**

* dam:folderThumbnailPaths值即使刪除資料夾內的資產後，也不會重新整理並顯示舊的縮圖。 NPR-30424：CQ-4273667 的 Hotfix

**UI主控台**

* 縮圖索引標籤上的Sites頁面屬性上有跨網站指令碼(XSS)。 NPR-30048：Granite-26200 的 Hotfix

**UI-Foundation**

* 新增在基礎API中追蹤事件中追蹤動態UI狀態的支援。 NPR-30742、GRANITE-26322:GRANITE-26036的Hotfix

**Forms**

>[!NOTE]
>
>AEM Service Pack不包含AEM Forms的修正。 會使用個別的Forms附加套件來傳送。 此外，已發行包含JEE上AEM Forms修正的累積安裝程式。 如需詳細資訊，請參閱 [安裝AEM Forms附加元件套件](#install-aem-forms-add-on-package) 和 [安裝AEM Forms JEE安裝程式](#install-aem-forms-jee-installer).

**Forms 附加元件套件**

**調適型表單**

* 從發佈者擷取空白.css檔案所花的時間較長，造成效能問題。 NPR-30558：CQ-4274399 的 Hotfix
* 發佈網站時，發佈後修改的Forms不會再次發佈。 NPR-30411：CQ-4236566 的 Hotfix

**Forms - 後端整合**

* 使用Web服務定義語言(WSDL)建立表單資料模型時擲回錯誤。 NPR-30388：CQ-4272921 的 Hotfix

**Forms — 通信管理**

* 特殊字元(例如小於(&lt;)、大於(>)和&amp;)會在代理UI中進行編碼。 NPR-30410：CQ-4273887 的 Hotfix
* 觸發包含資料字典值的文字片段時，代理UI會停止回應。 NPR-30098、NPR-30083：CQ-4272204 的 Hotfix
* 建立通信UI(CCR UI)會因錯誤變數（物件物件）而間歇性失敗。 NPR-29983：CQ-4273874 的 Hotfix
* 當檔案片段的說明包含特殊字元，例如屬性中小於(&lt;)、大於(>)和&amp;符號時，信函草稿重新載入會失敗，但有例外。 NPR-29930：CQ-4252762 的 Hotfix

**HTML5Forms**

* 以瀏覽模式使用 NonVisual Desktop Access 來讀取 HTML5 Forms時，Chrome 瀏覽器在表單設計中的每個可縮放向量圖形 (SVG) 之前讀到「graphic」。NPR-30450：CQ-4274732 的 Hotfix

**Forms - JEE 安裝程式**

**Forms - Foundation JEE**

* 從AEM Forms Workbench叫用網站服務來新增或編輯網站服務連線時，系統擲回錯誤：ClassNotFoundException org.apache.axis.message.SOAPBodyElement。 NPR-30116：CQ-4273217 的 Hotfix

**Forms - 文件服務**

* PDF/Acrobat預檢中出現標籤遺失錯誤。 NPR-30594：CQ-4276032 的 Hotfix
* PDF中的單個字元資料綁定導致Reader擴展失敗，並出現錯誤「java.lang.StringIndexOutOfBoundsException:字串索引超出範圍：1」。 NPR-30128：CQ-4273878 的 Hotfix
* 對 HTML 轉 PDF 服務執行負載測試時，發生錯誤而失敗，且檔案類型設定從 AEM 表單伺服器中移除。NPR-30085：CQ-4272631 的 Hotfix
* 使用Adobe Acrobat 9.1（XFA 3.0版）拼合PDF時不會保留PDF表單狀態：窗體上的不可見元素將設回可見狀態。 NPR-29978：CQ-4270888 的 Hotfix

**Forms - 文件安全性**

* 套用具有時間戳記的簽名失敗，並出現錯誤：ALC-DSC-003-000:com.adobe.idp.dsc.DSCIndigationException:調用錯誤。 NPR-30696、NPR-30537：CQ-4273778 的 Hotfix
* Configuration Manager不會為本地化表格欄插入日文字串。 NPR-30496：CQ-4274868 的 Hotfix

**PDFG 服務**

* 嘗試在Windows Server 2016上將Word文檔轉換為PDF時出現連接錯誤。 NPR-30597：CQ-4275652 的 Hotfix
* 嘗試使用HTML透過「phantomjs」程式庫PDF後端服務時，權限遭拒例外狀況。 NPR-30456：CQ-4258077 的 Hotfix
* JBoss Management Console未顯示HTML對PDF服務的maxReuseCount。 NPR-30303、NPR-30135：CQ-4273763 的 Hotfix

#### AEM 6.4.5.0 {#experience-manager-6450}

AEM 6.4.5.0為重要更新，包含效能、穩定性、安全性和重要客戶修正，以及自AEM 6.4全面推出以來所發行的增強功能， **2018年4月。**

這也是累積的，也就是說6.4.5.0包含之前發行的所有AEM 6.4 Service Pack。

AEM 6.4.5.0的部分關鍵重點為：

* 內建存放庫 (Apache Jackrabbit Oak) 更新至 1.8.13 版。
* 在Brand Portal復寫代理中新增通訊端逾時和連線逾時。
* Omnisearch增強功能 — 將搜尋結果的分頁限制提高至100頁。
* 已停用 `AssetDownloadServlet` 依預設，AEM發佈執行個體上會有OSGi元件。 如需詳細資訊，請參閱 [從AEM下載資產](/help/assets/download-assets-from-aem.md).
* 啟用資產的多網站管理員支援。 如需詳細資訊，請參閱 [使用MSM對資產重複使用資產](/help/assets/reuse-assets-using-msm.md).

**資產**

* 檔案名稱中帶有縮寫符號的資產不會同步至Dynamic Media。 NPR-29538：CQ-4270592 的 Hotfix
* 更新 DAM DMGateway 介面以提供 S3 多部分支援。NPR-29740：CQ-4226303 的 Hotfix
* 在Dynamic Media中下載視訊的轉譯時，資產下載對話方塊顯示錯誤的檔案大小。 NPR-29642：CQ-4246202 的 Hotfix
* Day CQ DAM Mime Type Service為m3u8套用文字後，資產變得無法使用。 NPR-29276：CQ-4264052 的 Hotfix
* 如果任何已移動/重新命名的資產屬於Sling資源集合的一部分，資產參考調整將無法儲存工作階段。 NPR-29143:/CQ-4252605的Hotfix
* 無法透過搜尋中繼資料值來追蹤或尋找資產。 NPR-29141：CQ-4260215 的 Hotfix
* 使用搜尋篩選器來儲存智慧型集合時，面板上的點按動作不會維持焦點。 NPR-29000：CQ-4240323 的 Hotfix
* 移動資料夾可以建立大小寫混合或大寫名稱的資料夾。 NPR-28945：CQ-4265234 的 Hotfix
* 如果集合名稱有空格，則Omnisearch中會顯示空白結果。 NPR-29001：CQ-4236729 的 Hotfix
* 使用一些不支援的特殊字元（如&amp;）重新命名檔案，會建立無效的資料夾。 NPR-29196：CQ-4265037 的 Hotfix
* DAM解壓縮封存檔的zip檔案功能損毀。 NPR-29187：CQ-4254421 的 Hotfix
* 中繼資料匯入應允許匯入中繼資料，而不註冊命名空間。 NPR-29425、NPR-28132：CQ-4269445 的 Hotfix
* 名稱包含引號字元的資產無法儲存中繼資料變更。 NPR-29395：CQ-4254305 的 Hotfix
* 如果檔案名稱包含空白字元，則無法移動DAM資產。 NPR-29270：CQ-4266403 的 Hotfix
* 無法下載以Deflate64演算法壓縮的ZIP封存檔。 NPR-29225：CQ-4253995 的 Hotfix
* 開啟包含許多版本資產的資料夾時，資產縮圖顯示緩慢。 NPR-29833：CQ-4271629 的 Hotfix
* 如果在選取系列後按下Enter鍵，則無法反白輸入系列。 NPR-29723：CQ-4261607 的 Hotfix
* 跨網站指令碼(XSS)攻擊，通過受限的警報窗口。 NPR-29671：CQ-4270133 的 Hotfix
* 沒有刪除權限的使用者無法將關係新增至資產。 NPR-29640：CQ-4269196 的 Hotfix
* 在屬性頁面中新增資產標題後，當使用者嘗試關閉頁面時，AEM會再次開啟屬性頁面。 NPR-29628：CQ-4264929 的 Hotfix
* 在資產上建立大量關係會導致錯誤。 NPR-28779：CQ-4250708 的 Hotfix
* 在Scene7 Connect執行模式中，資產擷取速度緩慢。 NPR-28658：CQ-4263007 的 Hotfix
* 未捕獲的TypeError錯誤：嘗試查看搜索結果時，無法讀取未定義的屬性「split」。 NPR-28803：CQ-4248371 的 Hotfix
* 從AEM到Brand Portal的復寫會持續很長時間。 NPR-28914：CQ-4254932 的 Hotfix
* 在DAM中移動資產不會在Scene7上產生類似的移動。 NPR-28957：CQ-4264974 的 Hotfix
* 如果在AEM中更新中繼資料欄位，則中繼資料更新不會傳遞至IPS。 NPR-28961：CQ-4255393 的 Hotfix
* VersioningTimelineEventProvider應提供根版本和版本注釋。 GRANITE-26063的Hotfix
* 插入資料會導致在伺服器端執行程式碼。 CQ-4270246 的 Hotfix
* 啟用資產的多網站管理員支援。 CQ-4271453、CQ-4268621、CQ-4257491的Hotfix
* AEM介面應在時間軸歷史記錄中顯示資產目前版本的額外項目，並顯示「Adobe資產連結」的最新簽入備注。 CQ-4262864 的 Hotfix
* 建立或編輯MixedMediaSet時不會載入範例視訊。 CQ-4244889 的 Hotfix
* 停用AEM端刪除內容的權限，會導致使用者無法發佈至Brand Portal。 CQ-4270426 的 Hotfix
* 升級至AEM 6.4.3後，資產報表的查詢限制相關問題。NPR-28588:CQ-4262022、CQ-4260697的Hotfix
* 下載功能會透過 assetdownload servlet 運用 AEM Assets 讓匿名使用者下載所有資產。NPR-27315、CQ-4254732的Hotfix

**網站**

* JCR申訴標籤名稱應根據標籤標題自動填入。 NPR-28990：CQ-4199411 的 Hotfix
* 在頁面屬性中新增的某些欄位上看不到取消繼承按鈕。 NPR-29079：CQ-4265686 的 Hotfix
* 轉出預覽動作不應嘗試重新建立即時副本或在轉出頁面清單中顯示。 NPR-29151：CQ-4266213 的 Hotfix
* （範本編輯器）結構模式中的樣式原則回歸。 NPR-28981：CQ-4264400 的 Hotfix
* 巢狀即時副本在轉出期間會顯示重複的登入項目。 NPR-29300：CQ-4268664 的 Hotfix
* 發佈包含設計匯入工具元件之即時副本失敗，無法擷取所選頁面的參考。 NPR-28944：CQ-4265014 的 Hotfix
* 搭配多欄位使用時，CoralUI 在元件層級儲存 fileReferenceParameter 而非多欄位層級。NPR-29536：CQ-4266129 的 Hotfix
* 取消在設計匯入工具上的繼承後，不會在發佈時複製設計參考。 NPR-29648、NPR-29721：CQ-4269270、CQ-4271087 的 Hotfix
* RTF編輯器中的路徑欄位會在根路徑開啟，而不考慮要搜尋的路徑。 NPR-29483：CQ-4268997 的 Hotfix
* (IE11)使用defaultPasteMode = platext複製RTE元件中的貼上HTML內容時，不會將內容貼上為純文字。 NPR-29432、NPR-29171:GRANITE-24941的Hotfix
* RTF編輯器拼字檢查不再適用於其他語言。 NPR-29506：CQ-4264990 的 Hotfix
* Campaign頁面上有跨網站指令碼(XSS)。 NPR-29614：CQ-4269322 的 Hotfix
* 處於來源編輯模式時若從全螢幕最小化 RTF 編輯器，會導致內容遺失。NPR-29574：CQ-4260584 的 Hotfix
* （傳統UI）當有大量標籤時，不一定能導覽至最後一個標籤。 NPR-29544：CQ-4264548 的 Hotfix
* （傳統UI）Admin Console導覽功能表會消失，且頁面未完全載入。 NPR-29571：CQ-4264585 的 Hotfix
* 已在執行個體上啟用縮製的情況下，將元件新增至 WCM 頁面時會產生錯誤警報。NPR-29396：CQ-4266196 的 Hotfix
* 樣式系統節點從父節點繼承的問題。 NPR-29296：CQ-4266041 的 Hotfix
* 以「時間扭曲」還原的頁面，應參照版本設定時的正確圖片。  NPR-29431：CQ-4262638 的 Hotfix
* 安裝最新6.4.5快照版本後，編輯器上出現Javascript錯誤的空白頁面。 NPR-29475：CQ-4266196 的 Hotfix
* 將元件新增至parsys時，不會接受設計元件清單屬性，且會解析為具有類似parsys結構的不同範本節點名稱。 NPR-29509：CQ-4269044 的 Hotfix
* cq:dropTargets區域涵蓋整個元件而非影像大小，使得使用內嵌元件進行定位變得困難。 NPR-29738：CQ-4268912 的 Hotfix
* 使用影像就地編輯器後，影像元件不會呼叫「afteredit」接聽程式。 NPR-29616 CQ-4268065的Hotfix
* 設定社交貼文至Facebook的問題。 NPR-29212：CQ-4266630 的 Hotfix
* 升級已修改頁面的啟動時，會考量來源和啟動分支中的修改。 NPR-29308：CQ-4266746 的 Hotfix
* 內容片段上呈現的縮圖會顯示「日期」和「時間」欄位的內部日曆表示法。 NPR-29531：CQ-4269362 的 Hotfix
* 無法將標籤大量新增至具有現有不同標籤的頁面。 NPR-28729：CQ-4262922 的 Hotfix
* 網站管理員中未顯示排程啟動圖示。 NPR-28725：CQ-4263917 的 Hotfix

**複寫**

* 復寫代理元件中出現敏感資訊洩漏漏洞。 NPR-29612、NPR-24951:GRANITE-25070的Hotfix
* cq/replication/components/agent元件中，使用者提供的資料沒有在輸出上逸出，導致儲存型跨網站指令碼(XSS)漏洞。 CQ-4266263 的 Hotfix

**體驗片段**

* 使用智慧影像時，無法將體驗片段匯出至目標。CQ-4269606 的 Hotfix

**社交 — 報表**

* AEM社群報表沒有顯示在AEM製作例項中。 CQ-4266294 的 Hotfix

**平台**

* 安裝套件時，套件管理器中出現跨網站指令碼(XSS)。 NPR-29734、NPR-29713、NPR-29630:GRANITE-26161、GRANITE-
* 多個儲存且反映的跨網站指令碼(XSS)，呈CRXDE Lite。 NPR-29634：GRANITE-26049 的 Hotfix
* Package Share的登入功能使用GET要求，而非POST要求，導致密碼在網路標籤下可見。 NPR-29631：GRANITE-26048 的 Hotfix

**Felix**

* 在系統主控台中觀察到跨網站指令碼(XSS)。 將滑鼠置於文字欄位上方時，頁面會載入並彈出。 NPR-29853、NPR-29633:GRANITE-26188、GRANITE-26050的Hotfix

**Granite**

* Apache Sling Logging Logger Configuration不會篩選插入的指令碼。  NPR-29775：GRANITE-26051 的 Hotfix

**社群**

* 應從發佈例項中移除在作者上刪除的群組。 NPR-28933：CQ-4264645 的 Hotfix
* 應使用密碼欄位保護應用程式密碼，而不應以純文字顯示於社交連線工具。 NPR-29728：CQ-4270480 的 Hotfix
* 沒有版主權限的訪客和成員可以透過貼上URL來查看未核准/待審貼文。 NPR-29726：CQ-4271124、CQ-4271441 的 Hotfix
* 觀察到使用者登入 Community 時出現 40-50 秒的長回應時間。NPR-29678：CQ-4269444 的 Hotfix

**轉換**

* 導覽中沒有翻譯功能存取權的使用者應該無法存取其子頁面。 NPR-29644：CQ-4269979 的 Hotfix
* 嚮導允許在只讀位置建立翻譯副本，因此未支援用戶權限。 NPR-29375：CQ-4265877 的 Hotfix

**UI - Foundation**

* 將搜尋結果的分頁限制提高為卡片檢視的100頁，清單檢視的200頁。 NPR-29332：GRANITE-24644 的 Hotfix
* 由於標籤延遲載入，集合頁面上不會顯示任何內容。 NPR-29267：GRANITE-24902 的 Hotfix
* 將分頁限制變更為100（而非40）會觸發額外的延遲載入，而不需要分頁請求。 NPR-29246：GRANITE-25027 的 Hotfix
* 加密後不會填入AEM granite密碼欄位。 NPR-29245：GRANITE-24908 的 Hotfix

**整合**

* 嘗試編輯和儲存AEM啟動設定時，會顯示例外訊息。 NPR-29086：CQ-4266153 的 Hotfix
* BrightEdge憑證因連線錯誤而失敗。  NPR-29167：CQ-4265872 的 Hotfix
* 應移除「Cloud Service設定」中根層級顯示的繼承自核取方塊。 NPR-27856：CQ-4259676 的 Hotfix

**Sling**

* 未從設定讀取HTTP連線逾時。 NPR-29264：SLING-7902 的 Hotfix
* JCR安裝程式回寫導致OSGi配置使用無效格式並阻止重新部署。 NPR-29027：CQ-4264694 的 Hotfix

**專案**

* 使用者無法完成專案工作流程。 NPR-29621：CQ-4258791 的 Hotfix
* 專案工作流程清單會顯示40個工作流程以外的空白列。 NPR-28739：CQ-4264005 的 Hotfix
* 在Brand Portal中選擇「動態轉譯」選項會下載空白的.zip檔案。 NPR-29420：CQ-4268826 的 Hotfix
* 將資產從AEM作者/content/dam/mac資料夾發佈至Brand Portal無法運作。 NPR-29820：CQ-4271118 的 Hotfix
* 名稱中的標點符號會導致發佈按鈕發生問題。 NPR-29573：CQ-4269317 的 Hotfix
* 無法透過參考面板建立資產語言副本。 CQ-4269535 的 Hotfix

**工作流程**

* 從6.4.2升級到6.4.4會中斷對話參與者的日曆選擇欄位。 NPR-29727：CQ-4270423 的 Hotfix

**WCM — 管理UI**

* 在Coral2實作中開啟權限標籤時不會顯示按鈕。 CQ-4269419 的 Hotfix

**WCM - MSM**

* 刪除即時副本中的子節點應會分離liveRelationship。 CQ-4270395 的 Hotfix
* 升級至AEM 6.4.3讓多網站管理員需花很長時間才能推出。 CQ-4271410 的 Hotfix

**漏洞**

* CSRF 保護架構對 AEM Foundation 表單無效。NPR-28612：GRANITE-22231 的 Hotfix

**WCM - 頁面編輯器**

* 使用無效的選擇器時出現反射型跨網站指令碼 (XSS)。CQ-4270397 的 Hotfix

**Forms**

AEM 6.4.5.0表單的關鍵重點為：

**Forms 附加元件套件**

**調適型表單**

* （觸控式UI）啟動工作流程選項不會彈出用於設定的對話方塊。 NPR-29521：CQ-4269050 的 Hotfix

**Forms - 後端整合**

* 為Microsoft Dynamics內部部署整合啟用了對Active Directory聯合身份驗證服務(ADFS)v3.0的支援。 NPR-30003、NPR-29484：CQ-4270586 的 Hotfix
* 預填服務因AEM Forms資料整合模組的週轉時間延長而失敗。 NPR-28997：CQ-4265988 的 Hotfix
* AEM Forms中的SOAP Webservice請求格式不正確。 NPR-29013：CQ-4265443 的 Hotfix
* 測試SOAP服務時，如果日期值不正確，則不會顯示錯誤訊息。 CQ-4265445 的 Hotfix

**Forms — 互動式通訊與Forms — 通信管理**

* 建立通信UI(CCR UI)無法處理浮點數。  NPR-29210：CQ-4254201 的 Hotfix
* 「建立通信UI」(CCR UI)中看不到在變數上設定的工具提示。 NPR-29739：CQ-4250533 的 Hotfix
* 無法從信函中複製或貼上Omnisearch。 NPR-29808：CQ-4270783 的 Hotfix

**HTML5Forms**

* 在文字中新增空格時，文字欄位不允許填入到結尾。 NPR-28844：CQ-4260239 的 Hotfix

**Forms - JEE 安裝程式**

**Forms - Foundation JEE**

* AEM Forms Workbench中的Web服務元件無法叫用需要雙向SSL驗證的Web服務。 NPR-29485：CQ-4246794 的 Hotfix
* AEM Forms JEE配置管理器無法與多個NIC卡一起使用。 NPR-29236：CQ-4268598 的 Hotfix
* AEM啟動錯誤來自GemFire:java.lang.IllegalStateException:一次只能建立一個AdminDistributedSystem連接。 NPR-29524：CQ-4266295 的 Hotfix
* NoClassDefFoundError，因為jar版本不匹配。 NPR-28834：NPR-28834 的 Hotfix

**Forms - 文件服務**

* 無效PDF/檔案會以isPDFA作業的方式回報為有效PDF/A。 NPR-29076：CQ-4261541 的 Hotfix
* PDF無法轉換至「表單」欄位沒有外觀字典的PDF/A-1b。 NPR-29534：CQ-4269618 的 Hotfix
* PDF/透過輸出服務產生之PDF的轉換未通過Acrobat DC驗證。 NPR-29647：CQ-4270448 的 Hotfix
* Apache POI套件組合失敗，但出現例外狀況。 NPR-27861、NPR-28048：CQ-4245898、CQ-4244778 的 Hotfix

**Forms — 設計工具**

* 新增PDF/UA支援至使用Designer和Output Service產生的XML Forms架構(XFA)表單。 NPR-23022

**Forms - 工作流程**

* 從工作區提交時會以Umlaut字元失敗。 NPR-29087：CQ-4263172 的 Hotfix

**包含 Feature Pack**

**資產**

* 啟用資產的多網站管理員支援。 如需詳細資訊，請參閱 [使用MSM對資產重複使用資產](/help/assets/reuse-assets-using-msm.md). NPR-26450：CQ-4259922 的 Hotfix

**包含的 OSGI 套件組合和內容套件**

下列文字記錄 CFP 中包含的 OSGI 套件組合和內容套件清單。

AEM 6.4.5.0 中包含的 OSGi 套件組合清單

[取得檔案](assets/6.4.5.0_bundles.txt)

AEM 6.4.5.0 中包含的內容套件清單

[取得檔案](assets/6.4.5.0_OSGI.txt)

#### AEM 6.4.4.0 {#experience-manager-6440}

AEM 6.4.4.0為重要更新，包含效能、穩定性、安全性和重要客戶修正，以及自AEM 6.4全面推出以來所發行的增強功能， **2018年4月。**

這也是累積的，也就是說6.4.4.0包含之前發行的所有AEM 6.4 Service Pack。

AEM 6.4.4.0的部分關鍵重點為：

* 內建存放庫 (Apache Jackrabbit Oak) 更新至 1.8.11 版。
* 新增快取服務版本的支援，以避免經常出現服務版本HTTP要求。
* 新增刪除自動標籤的支援。
* 為目錄精靈實作無限捲動。
* 根據社群網站向後移植限制權限的功能。
* Sling Granite內容健康狀況檢查的效能修正（快取、非同步執行、排除清單）。
* 新增assetpicker按鈕至pagethumbnail對話方塊。
* 新增屬性，允許在欄位上進行工具提示定位。
* 改善多欄位內對ColorPicker的支援。
* 新增檢查，忽略內容片段clientlibs中數字輸入多欄位的空白值。
* 啟用對Microsoft Translator Text API v3的支援。

**資產**

* ACP和股票整合遷移至AEM 6.4.4.0 NPR-27632
* 稍後發佈含子資料夾的空白資產資料夾會使子資料夾消失。 NPR-27558：CQ-4254701 的 Hotfix
* 新增單一非命名空間的String\[\]屬性會導致XMP回寫不完整。 NPR-26805：CQ-4254142 的 Hotfix
* 將輸入pdf柵格化後，生成的輸出缺少影像。 NPR-27929：CTG-4150481 的 Hotfix
* 「移動資產精靈」顯示的「參考」頁面計數不正確。 NPR-27833：CQ-4258014 的 Hotfix
* 使用標籤篩選時，AssetPicker只會搜尋第一個標籤以篩選結果。 NPR-27778：CQ-4257705 的 Hotfix
* AEM OOTBPDF處理常式卡在含有外文字元的處理PDF上。 NPR-28778：CQ-4254234 的 Hotfix
* 若CSV檔案的值在單一欄中以逗號分隔，AEM CSV編輯器不會逸出逗號，並將其視為個別欄。 NPR-28801：CQ-4261694 的 Hotfix
* 使用路徑瀏覽器選取資料時，中繼資料結構編輯器出現問題。 NPR-28674：CQ-4263005 的 Hotfix
* 太多資產會被處理至智慧內容服務，導致完成定期標籤程式的時間過長。 NPR-28640：CQ-4262661、CQ-4262644、CQ-4263234 的 Hotfix
* 案頭動作無法用於Omnisearch結果，來自 `aem/start.html` 頁面。 NPR-27242：CQ-4248176 的 Hotfix
* 資產API不允許上傳檔案> 2 GB，造成上傳失敗。 NPR-27629：Granite-23590 的 Hotfix
* 執行個體上啟用Dynamic Media時，第一次嘗試下載的資產中不會儲存中繼資料。 NPR-28233：CQ-4260759 的 Hotfix
* 服務解析器未在SiteCatalyst配置中關閉。 NPR-28015：CQ-4259397 的 Hotfix
* 在DAM中移動資產不會在Scene7上造成類似移動（p2p設定）。 NPR-28313：CQ-4261091 的 Hotfix

**網站**

* （傳統UI）轉出清單中會顯示即時副本的一小部分。 NPR-28598、NPR-28574：CQ-4263410 的 Hotfix
* 當cq:master為空或無效時，LiveRelationshipManagerImpl會擲回例外。 NPR-28590：CQ-4263115 的 Hotfix
* 現成可用的「請求刪除」工作流程無法正確刪除頁面。 NPR-28668：CQ-4263195 的 Hotfix
* 「關係狀態」UI未顯示相關coral-datepicker欄位的正確年份或時間戳記值。 NPR-28666：CQ-4263661 的 Hotfix
* 適用於 6.4 的 SuggestionHandler 中出現跨網站指令碼 (XSS)。NPR-28693：CQ-4253821 的 Hotfix
* 從網站管理員移動資料夾會導致記憶體不足，進而導致AEM無法使用。 NPR-28346：CQ-4261398 的 Hotfix
* 更新後MSM LiveCopy轉出設定會遺失。 NPR-28311：CQ-4258705 的 Hotfix
* 無法捲動超過40個Blueprint設定。 NPR-27640：CQ-4239166 的 Hotfix
* 以SyntheticResource作為參考會擲回Null指標例外狀況，並封鎖頁面的移動。  NPR-27576：CQ-4258262 的 Hotfix
* 在6.1到6.4的升級執行個體上，PushOnModify無法用於刪除。 NPR-28108：CQ-4259833 的 Hotfix
* （傳統UI）遺失取消繼承按鈕，且即時副本頁面上的元件可編輯。 NPR-28256：CQ-4260161 的 Hotfix
* OakState0001:轉出時未解決的衝突。 NPR-27982：CQ-4259548 的 Hotfix
* 複製/貼上包含SyntheticResource引用的結構時，進程結束時出現錯誤500。 NPR-27709：CQ-4259179 的 Hotfix
* 激活負載時無法終止正在運行的工作流。 NPR-27672：CQ-4258520 的 Hotfix
* 轉出顯示從6.1升級至6.4後的重複轉出路徑。NPR-27845:CQ-4259487的Hotfix
* 將dam assetpicker強制回應至頁面縮圖元件。 NPR-28131：CQ-108042 的 Hotfix
* （傳統UI）無法開啟與標籤Widget的對話方塊。 NPR-28575：CQ-4262680 的 Hotfix
* 多欄位檔案上傳未顯示拖放區域。 NPR-28676：CQ-4263516 的 Hotfix
* 將元件從 AEM 6.0 移轉到 AEM 6.2 時，出現「無效的遞迴選擇器值」錯誤。NPR-28609：CQ-4241258 的 Hotfix
* 當外掛程式的彈出視窗高於文字區域時，對話方塊中的RTF編輯器會發生忽隱忽現的情形，因此會封鎖任何進一步的編寫作業。 NPR-27579：CQ-4257440 的 Hotfix
* （傳統UI）cq:action編輯器注釋無法運作。 NPR-28232：CQ-4257703 的 Hotfix
* 從頁面編輯器的標籤篩選資產搜尋面板中移除標籤無法正確重新整理清單。 NPR-27983：CQ-4245567 的 Hotfix
* 如果多欄位數字值為空，按一下「儲存」會導致無限載入提示，而實際上從未完成。  NPR-28400、NPR-28393：CQ-4244058、CQ-4244349 的 Hotfix
* 只有讀取權限，用戶/組無法選擇XF，並且沒有查看XF及其頁面屬性的選項。 NPR-28341：CQ-4260412 的 Hotfix
* 從Target收到的JSON資料有許多逸出字元，導致應用程式頁面中斷。 NPR-28318：CQ-4252043 的 Hotfix
* 安裝AEM 6.4.3後無法編輯任何元件。NPR-28125:CQ-4261216的Hotfix
* 對於結構化內容片段，刪除標籤欄位的所有標籤不會持續存在。 NPR-28133：CQ-4247241 的 Hotfix
* 編輯內容片段&quot;jcr:lastmodifiedby&quot;和&quot;jcr:lastmodified&quot;屬性時，值會更新，而使用者不會進行任何變更。 NPR-27847：CQ-4257138 的 Hotfix
* 內容片段版本設定比較AEM 6.4的差異改善。NPR-27764
* 如果/content/experience-fragments上未定義cq:allowedTemplates ，且Experience Fragement範本上使用allowedPaths ，則移動/複製體驗片段時會擲回錯誤。 NPR-27487：CQ-4257489 的 Hotfix
* 重新整理新使用者時，「建立」按鈕就會出現。 NPR-27335：CQ-4255360 的 Hotfix
* 嘗試移動已發佈頁面時，顯示在「移動頁面」精靈第一頁的「參考頁面」計數不正確。 NPR-28111：CQ-4259663 的 Hotfix
* （觸控式UI）參考邊欄不會顯示傳入的連結。 NPR-28529：CQ-4262306 的 Hotfix
* 安裝AEM 6.4.3後無法編輯任何元件和頁面屬性。NPR-27998:CQ-4261216、CQ-4260441的Hotfix
* 將 ContextHub 遷移至 jquery 3。NPR-28397：GRANITE-19902 的 Hotfix

**商務**

* 如果資料夾中有超過20個目錄，則無法選取目錄。 NPR-27649：CQ-4258119 的 Hotfix
* 由於缺少header.referer，商務精靈和屬性檢視中斷。 CQ-4261122 的 Hotfix

**Campaign - 目標定位**

* com.day.cq.personalization.impl.TeaserResourceEventHandler進入無限回圈，並導致發佈例項上的節點更新。 CQ-4263096 的 Hotfix

**複寫**

* 建立復寫內容com.day.cq.replication.AccessDeniedException時出錯。 NPR-28314：CQ-4261401 的 Hotfix
* 在復寫代理中將使用者代理id設為管理員時，會話洩漏。 NPR-28220：CQ-4255517 的 Hotfix

**DAM -Creative Cloud**

* 反向移植HTTP API以在AEM Assets內尋找類似的影像。 CQ-4254091 的 Hotfix
* 增強ACP API，允許將查詢結果限制為集合的成員。 CQ-4258708 的 Hotfix

**DAM — 格式**

* 觸發中繼資料匯出後，頁面會重新導向至404頁面。 CQ-4262447 的 Hotfix

**DAM - 一般**

* (Adobe Stock整合)伺服器錯誤強制回應會在error.log檔案中顯示，並出現Oauth錯誤。 CQ-4260406 的 Hotfix
* 如果6.4.4套用至6.4.3,Adobe Stock整合將無法運作。CQ-4266009的Hotfix
* 即使在應用SP3修補程式後，仍缺少CF模型的連結。 CQ-4259029 的 Hotfix

**平台**

* （傳統UI）升級至6.4.2後，基本報表元件中沒有編輯按鈕可用。NPR-28560:CQ-4262825的Hotfix
* 使用結合property.operation=like和property.depth的查詢時，結果為InvalidQueryException。 NPR-28570：CQ-4262652 的 Hotfix
* 從覆蓋的語言節點中刪除新添加的語言節點時出現內部伺服器錯誤。 NPR-28661：CQ-4239194 的 Hotfix
* 隨機啟動時sling-oak-1執行緒中stderr.log出現Null指標例外狀況。 NPR-28665：CQ-4237845 的 Hotfix

**Felix**

* webconsole.plugins.memoryusage在重新整理時造成鎖死。 NPR-27895：GRANITE-20715 的 Hotfix

**Granite**

* Sling內容存取狀況檢查會針對自訂資源解析器搜尋路徑執行過長的/libs驗證。 NPR-28113：GRANITE-23529 的 Hotfix

**內容片段管理**

* 內容片段資產的可用性改善和同等功能。 CQ-4253883 的 Hotfix

**社群**

* 將易受攻擊的引導程式升級為3.4，並將ckeditor程式庫升級為4.5.11。NPR-28490:CQ-4257511的Hotfix
* 取消編輯模式不會還原已刪除的附件。 NPR-27902：CQ-4255150 的 Hotfix
* 代表方塊撰寫的內容只應對有權限的成員可見。 NPR-27900：CQ-4251235 的 Hotfix
* 在發佈執行個體上，將rep:cache新增至AEM Communities使用者同步接聽程式的可忽略節點中。 NPR-27842：CQ-4247234 的 Hotfix
* 搜尋方塊在UI層級顯示逸出字元。 NPR-27838：CQ-4259757 的 Hotfix
* 搜尋特殊字元（如、+、？）時，會產生錯誤。 在快速搜索中。 NPR-28213：CQ-4260969 的 Hotfix
* 建立「社群特定管理員」群組，讓使用者能夠編輯和撰寫相關的社群網站。 NPR-27731
* 新增鍵盤事件邏輯以開啟視訊。 NPR-27726：CQ-4254026 的 Hotfix
* 在 Publish 上為 AEM Communities Enablement 元件啟用鍵盤導覽。NPR-27728：CQ-4254028 的 Hotfix
* 為清單和卡片檢視按鈕新增 Aria 標籤。NPR-27727：CQ-4254027 的 Hotfix
* 處理Social- Communities中開啟的資源解析器工作階段。 NPR-27721：CQ-4258714 的 Hotfix

**轉換**

* 支援Microsoft Translator Text API v3。 NPR-28366：CQ-4249755 的 Hotfix
* jcr:language和cq:language不會以翻譯的語言自動更新。 NPR-28338：CQ-4256046 的 Hotfix
* 循環引用在建立語言副本時導致StackOverflowError。 NPR-27596：CQ-4255621 的 Hotfix
* 在多語言翻譯專案中，按一下「儲存並關閉」會導致後續頁面新增至專案，而導致建立新專案，而非在現有專案中建立新的翻譯工作。 NPR-28219、NPR-28236：CQ-4261276、CQ-4260731 的 Hotfix
* 新增含有大量資料的內容片段時，由於允許的字元數目有限，錯誤字串太長。 NPR-28722：CQ-4262362 的 Hotfix

**Social**

* 每次發佈新評論時，發佈到下一頁的評論都會以黃色突出顯示。 CQ-4261359 的 Hotfix
* 無法使用 API 刪除使用者產生的內容中的評論。NPR-28075：CQ-4261135 的 Hotfix
* AbstractNotificationOperationService導致ClassCastException。 CQ-4260456 的 Hotfix
* 移除播放器中共享內容物件參考模型 (SCORM) 雲端的參考。CQ-4260779 的 Hotfix

**UI - Foundation**

* 整合在HTML客戶端庫管理器中的「檔案系統輸出快取」功能中斷了編譯指令碼（如LESS檔案）的「debugClientLibs」功能。 NPR-27249：Granite-23313 的 Hotfix
* 啟用除錯模式時顯示的資產數一律為1，且瀏覽器主控台中會擲回許多JS錯誤。  NPR-27575：GRANITE-23750 的 Hotfix
* 在使用Tomcat的AEM WAR中，儲存並關閉頁面屬性無法傳回正確頁面。 NPR-27566：GRANITE-23671 的 Hotfix

**整合**

* `com.day.cq.personalization.impl.TeaserResourceEventHandler` 進入無限迴圈，並造成發佈執行個體上的節點更新。NPR-28561：CQ-4263096 的 Hotfix
* 系統沒有針對目標元件考慮 cq:actions。NPR-27616：CQ-4257497 的 Hotfix
* LiveCopy 繼承取消無法在目標容器上正常運作。NPR-28129：CQ-4259813 的 Hotfix
* (雲端服務設定) 根層級顯示的「繼承自」核取方塊應移除。NPR-27856：CQ-4259676 的 Hotfix

**Sling**

* 更新至Sling模型API 1.3.8、Impl 1.4.10。NPR-27636:GRANITE-23537的Hotfix

**OAK — 區段持續性**

* 在OnRC後未刷新SegmentBufferWriter。 NPR-27464

**專案**

* 多語言翻譯專案不會為不屬於管理員群組的使用者建立多語言工作。 NPR-28508：CQ-4262023 的 Hotfix
* 每當在服務啟動期間調用getTaskRenders時， ProjectTaskListServlet就會洩漏ResourceResolver。 NPR-27590：CQ-4258011 的 Hotfix
* 如果目錄的子目錄比頁面大小多，而排序依日期或大小而定，則錯誤會阻止移出第一頁。 NPR-28867：CQ-4265039 的 Hotfix
* DAM檢視器中的反向移植跨網站指令碼(XSS)修正。 NPR-28106：CQ-4253215 的 Hotfix
* 無法由專案管理員將頁面新增至翻譯專案，因為無法顯示將頁面新增至翻譯專案的連結。 CQ-4266334 的 Hotfix

**工作流程**

* 在具有「標籤」(Tag)欄位的工作流通知中開啟完成的工作項對話框時，按一下交叉標籤將添加「標籤」(Tag)屬性。 NPR-28304：CQ-4261321 的 Hotfix
* 「重新分配任務」對話框中的「用戶選擇切換按鈕」無法正常工作。 NPR-28963：CQ-4264206 的 Hotfix

**Forms**

AEM 6.4.4.0表單的關鍵重點為：

* 新增支援，可記錄檔案安全API，以簽署和認證為交易。

**Forms 附加元件套件**

**Acrobat Sign整合**

* AEM 6.4 Forms用戶端SDK不包含adobesign-recipent套件。 NPR-27735：CQ-4259372 的 Hotfix

**調適型表單**

* 使用空白範本建立Wan適用性表單時，客戶無法將子面板置於表單的根面板。 NPR-28758：CQ-4264157 的 Hotfix
* 日期元件的year欄位值為9999時，驗證指令碼會失敗。 NPR-28580：CQ-4262620 的 Hotfix
* 使用空白範本建立最適化表單時，客戶無法將子面板傳送至表單的根面板。 NPR-28758：CQ-4264157 的 Hotfix
* 無法在適用性表單的延遲載入片段欄位之間設定值。 NPR-27758：CQ-4259703 的 Hotfix
* 適用性表單不使用RTF編輯器，但會載入其程式庫。  NPR-27759：CQ-4259193 的 Hotfix
* 內嵌於AEM Sites頁面的適用性表單無法重新導向至URL。 NPR-27620：CQ-4239287 的 Hotfix
* 無法在適用性表單的延遲載入片段欄位之間設定值。 NPR-28320：CQ-4262345 的 Hotfix
* 適用性表單不使用RTF編輯器，但會載入其程式庫。  NPR-28001：CQ-4259703、CQ-4259193 的 Hotfix
* 在Apple iOS 12.1上執行的AEM Forms應用程式無法使用手寫簽名。NPR-28497:CQ-4261765的Hotfix
* 在6.4中使用「Forms Workflow」傳統版編寫問題提交動作。CQ-4252740的Hotfix
* 處理塊和臨時儲存刪除時出錯。 NPR-28806：CQ-4264441 的 Hotfix

**Forms — 通信管理**

* 代理UI無法保留影像的原始大小。 NPR-28800：CQ-4259767 的 Hotfix
* CCR/代理UI:日期欄位的標籤在「資料」索引標籤中移位。 CQ-4255499 的 Hotfix

**Forms — 交易報告**

* 新增支援，可使用數位簽名或將檔案認證為計費交易。 NPR-28495：CQ-4260236 的 Hotfix
* 新增數位簽章和認證至計費API。 CQ-4260236 的 Hotfix

**Forms管理**

新增在Forms Manager的「開始檢閱精靈」和「移動資產精靈」中，以底線取代handlebars用戶端程式庫的使用。 NPR-27643：CQ-4246536 的 Hotfix.
在版本/640分支上安裝Forms管理套件後，一個套件組合會維持已安裝狀態。 已提交且其中附件的CQ-4265410 Forms的Hotfix不會顯示在提交動作「叫用AEM Forms工作流程」且已勾選啟用入口網站提交的工作流程中。 CQ-4263110 的 Hotfix

**Forms - 後端整合**

* 無法使用用戶端SDK、CQ-4238469的Hotfix來測試前置/後置處理程式和自訂提交

**Forms - JEE 安裝程式**

**Forms - 文件安全性**

* 使用更新策略服務時，將發生無法強制轉換對象錯誤。 NPR-28751：CQ-4252287 的 Hotfix
* 簽名生成失敗，而舊版commons-pkg。 CQ-4265535 的 Hotfix

**Forms - Foundation JEE**

* 在IBM WebSphere上安裝AEM Forms時，根據SOAP建立表單資料模型會失敗。 NPR-27923：CQ-4251134 的 Hotfix
* PDF產生器的SRT工具無法偵測已安裝的Adobe Acrobat版本。 NPR-27971

**Forms — 設計工具**

* XDP範本中的某些JPEG影像無法正確轉譯。  NPR-26702：LC-3917457 的 Hotfix

**Forms - 工作流程**

* HTML5Forms在a.lca中具有預設提交程式的JBoss 7無法運作。 NPR-28675：CQ-4243928 的 Hotfix
* 無法在HTML工作區中提交PDF forms。 NPR-28058：CQ-4260373 的 Hotfix
* 使用叫用FDM服務Forms Workflow在資訊日誌中打印客戶資料。 CQ-4260385 的 Hotfix

**包含 Feature Pack**

**網站**

* 內容片段版本設定比較AEM 6.4的差異改善。NPR-26760:CQ-4248839的FP
* AEM 6.4的內容片段變異差異改善。NPR-27866:CQ-4248839的FP
* OSGI設定中的啟用功能 **AEM工作流程撤回功能標幟**. 撤回動作應在設定標幟後終止工作流程例項。 NPR-26451：CQ-4259090 的 Hotfix

**平台**

* 增強的查詢產生器Facet擷取採用Oak API，適用於6.4。NPR-26674:CQ-4230337的FP

**包含的 OSGI 套件組合和內容套件**

下列文字記錄 CFP 中包含的 OSGI 套件組合和內容套件清單。

AEM 6.4.4.0 中包含的 OSGi 套件組合清單

[取得檔案](assets/bundles_6_4_4_0.txt)

AEM 6.4.4.0 中包含的內容套件清單

[取得檔案](assets/osgi_package_6_440.txt)

#### AEM 6.4.3.0 {#experience-manager-6430}

AEM 6.4.3.0為重要更新，包含2018年4月全面發行之AEM 6.4的效能、穩定性、安全性和重要客戶修正及增強功能。

這也是累積的，也就是說6.4.3.0包含之前發行的所有AEM 6.4 Service Pack。

AEM 6.4.3.0的部分關鍵重點為：

* 內建存放庫 (Apache Jackrabbit Oak) 更新至 1.8.9 版。
* 新增對適用性表單範本上allowedPaths屬性的支援。
* 增強AEM中以面板為基礎的資產搜尋功能
* 登入頁面中的跨網站指令碼(XSS)修正。
* 改善UI檢測。
* 改善FormData處理。
* 改善多欄位內項目命名的處理方式。
* 改善選取期間預留位置項目（卡片檢視和清單檢視）的處理方式。
* 新增Managed Services的Adobe IMS驗證和Admin Console支援。

**資產**

* 如果啟用「IDS分離」選項，「DAM更新資產」工作流程不會從INDD檔案中擷取參考。 NPR-26243;CQ-4250933的Hotfix
* 使用資產大量編輯器發佈資產時，不會顯示成功訊息。 NPR-26252;CQ-4251688的Hotfix。
* 從搜尋結果查看資產後，如果您按一下瀏覽器中的「上一步」按鈕，便會產生「錯誤請求」錯誤訊息，並顯示400錯誤代碼。 26578盧比；CQ-4253741的Hotfix
* 安裝Service Pack後，資產中繼資料顯示無效的命名空間錯誤。 NPR-22341;CQ-4237202的Quickfix
* 在清單檢視中重新排序資料夾和內容片段的選項不會針對適用的資料夾顯示。 NPR-27153;CQ-4255873的Hotfix
* 使用者無法將資產新增至新集合，因為這會導致錯誤彈出式對話方塊中出現影像損毀的錯誤訊息。 NPR-22431;CQ-4237086的Hotfix
* 動態下拉式清單不支援階層式下拉式清單。NPR-27043;CQ-4252564的Hotfix
* 如果使用者在DMS7雲端設定中為「公司根資料夾」設定非預設值，檢視器預設集就無法如預期運作。 NPR-26360;CQ-4249505的Hotfix
* 具有大量資產的例項的資產報表失敗。 NPR-27278;CQ-4256748的Hotfix
* 子資料夾不會繼承父資料夾的SmartCrop映像配置檔案。 NPR-27197;CQ-4256273的Hotfix
* 啟用Dynamic Media整合時，會修改Assets的某些中繼資料屬性。 不會顯示寬度、高度和位置屬性。 NPR-27203;CQ-4256258的Hotfix
* Dynamic Media不會對某些類型的資產使用已設定的Proxy。 NPR-25211;CQ-4244871的Hotfix
* 「元資料編輯器」頁包含無效項參數的Null指針異常。 NPR-26169;CQ-4241368的Hotfix。
* 如果下拉式清單有選擇規則，且套用了必要規則，則在中繼資料編輯器中無法滿足必要規則。 NPR-27479;CQ-4251428的Hotfix

**網站**

* 使用者可以使用內容原則，以內嵌全螢幕模式控制RTF編輯器功能，但無法使用內容原則控制「編輯對話方塊」RTF編輯器功能。 NPR-26750：CQ-4241130 的 Hotfix
* 從全螢幕切換至浮動式對話方塊時，RTF編輯器將無法使用。 浮動檢視包含兩個RTF編輯器。 NPR-25589：CQ-4206008 的 Hotfix
* 在文字欄位中按下傳回鍵（Enter鍵）時，RTF編輯器會切換為全螢幕模式。 NPR-26204：CQ-4245893 的 Hotfix
* RTF編輯器的清單外掛程式會自動停用，且不允許修改。 NPR-26507：CQ-4239387 的 Hotfix
* 將特殊字元新增至RTF編輯器視窗時，視窗會捲動至頂端。 NPR-26435：CQ-4249869 的 Hotfix
* 用戶端內容 segment.js 快取與非快取問題。NPR-26622：CQ-4253486 的 Hotfix
* 從製作例項啟動子規則至發佈例項時，發佈例項會停止運作。 NPR-26601：CQ-4253588 的 Hotfix
* RTF 編輯器與多個欄位結合時，出現「Uncaught TypeError: fieldAPI.getName 不是 foundation.js 的函數」錯誤。NPR-27146：CQ-4253155 的 Hotfix
* Salesforce整合無法使用Proxy設定。 NPR-27244：CQ-4245300 的 Hotfix
* 在以後使用「管理出版物」選項排程頁面進行啟用，並切換至清單檢視時，日曆圖示會消失。 NPR-26974：CQ-4239206 的 Hotfix
* 使用者無法編輯頁面屬性中封閉的使用者群組權限。 NPR-27138:CQ-4256089的Hotfix無法透過標籤編輯標籤。 NPR-26957：CQ-4254858 的 Hotfix
* 從結構化內容片段模型參考的標籤移動時，內容片段內對標籤的現有參考不會更新。 這會發生在內容片段模型的編輯畫面中。 NPR-26776：CQ-4251805 的 Hotfix
* 當您使用數個頁面建立和促銷啟動時，會為每個頁面建立多個版本。 NPR-26917：CQ-4254663 的 Hotfix
* AEM網站管理員不會處理在瀏覽器位址列中輸入的路徑。 NPR-26780：CQ-4254097 的 Hotfix
* 將頁面移至新位置而未重新命名時，頁面的版本記錄會遺失。 NPR-26706：CQ-4254025 的 Hotfix
* 體驗片段管理員編輯器中的URL不允許覆蓋。 NPR-26319：CQ-4252156 的 Hotfix
* 使用包含空白體驗片段的範本建立頁面並發佈時，頁面無法開啟，且會發生DefaultSlingScript錯誤。 NPR-26305：CQ-4252460 的 Hotfix
* 搭配名稱相同的類別使用data-sly-use時，會產生不相容的程式碼。 NPR-27282：Sling-7581 的 Hotfix
* 升級SP安裝後，網站的Blueprint轉出設定為空白。 NPR-27609：CQ-4257078 的 Hotfix

**DAM -Brand Portal**

* 中繼資料結構表單發佈至Brand Portal時，不會發佈標籤述詞。 CQ-4256218 的 Hotfix
* 從AEM發佈第三層資料夾至Brand Portal時，若未發佈父資料夾，資料夾名稱會變更。 CQ-4255423 的 Hotfix
* 路徑瀏覽器述詞會如預期般從AEM Assets發佈至Brand Portal。 不過，BP的已發佈路徑仍為/content/dam，必須更新。 CQ-4256240 的 Hotfix

**DAM -Creative Cloud**

* AEM主導覽中缺少「搜尋Adobe資產」圖示。 CQ-4254343 的 Hotfix

**DAM - DM 用戶端**

* 將視頻內嵌到與AVS視頻處理配置檔案關聯的資料夾後，瀏覽器窗口會反複刷新。 CQ-4253563 的 Hotfix
* YouTube使用包含大寫字元的臨機標籤時，發佈會失敗。 CQ-4252477 的 Hotfix
* 在PDF等資產中建立附註時，UI會啟動無限的頁面重新整理回圈。 NPR-27052：CQ-4255396 的 Hotfix

**DAM - DM服務**

* Dynamic Media不會對某些類型的資產使用已設定的Proxy。 NPR-10727;CQ-4244871的Hotfix

**平台**

* org.apache.sling.i18n的效能問題。 NPR-26812：SLING-7543 的 Hotfix
* 輸入XML的格式化和部署後，無法查看節點屬性。 NPR-26198：CQ-4250448 的 Hotfix
* ResourceProviderTracker中的IndexOutOfBoundsException。 NPR-26968：GRANITE-23310 的 Hotfix
* JMX主控台會累積許多管理工作階段，而每5分鐘會開啟一個新工作階段。 NPR-26958：CQ-4251090 的 Hotfix
* 從6.2升級至6.4後，記錄檔會顯示未結尾的資源解析器com.adobe.granite.repository.hc.impl.content.sling.SlingContentHealthCheck的堆疊追蹤。 NPR-26176：Granite-21734 的 Hotfix
* 將現成可用的調度程式刷新代理配置為更新別名時，操作會因StackOverflowError而失敗。 NPR-26373：CQ-4242928 的 Hotfix
* 復寫使用過期的OAuth代號，直到失敗為止。 NPR-25894
* 帶Sling的限制頁面（封閉使用者群組頁面）:別名不會將使用者重新導向至登入頁面。 NPR-25715:Granite=22263的Hotfix
* 發佈標籤時，UI上不會顯示任何活動。 CQ-4255961 的 Hotfix
* 無法在傳統UI中編輯標籤。 CQ-4258697 的 Hotfix
* 將org.apache.felix.http.bridge更新至4.0.4版。NPR-27038:Granite的反向移植 — 23334
* 套件管理器活動記錄應擷取至獨立的記錄檔中。NPR-27323：Granite-14866 的 Hotfix
* 套件驗證器不會報告CFP中的覆蓋。 NPR-27119：GRANITE-22825 的 Hotfix

**專案**

* ACP API只處理子目錄子目錄的分頁。 NPR-27617：CQ-4258639 的 Hotfix

**OAK**

* 安裝AEM 6.4 Service Pack 2後無法登入存放庫。 NPR-27171：Granite-23317 的 Hotfix

**複寫**

* 稽核記錄仍會開啟，而作用中工作階段會持續增加，每天約750次。 NPR-27062：CQ-4241350 的 Hotfix

**社群**

* 論壇貼文和回覆會新增到第二頁頂端，而重新整理後貼文就會移至第一頁頂端的正確位置。NPR-27342：CQ-4247338 的 Hotfix
* 所有資源的連結在捲動後拖放內容路徑(/aempublish)。 NPR-26982：CQ-4254345 的 Hotfix
* 編輯已發佈的網站時，社群管理員、社群協調者和特權成員下拉式清單中不會顯示新增的群組。 NPR-27190：CQ-4258574 的 Hotfix
* 啟用資源頁面中僅列出10個群組，即使群組清單已啟用分頁亦然。 NPR-26934：CQ-4252985 的 Hotfix
* 在ConfigMgr中提供了啟用/禁用搜索日誌元件中已排程貼文的選項，並且SearchScheduledPosts作業已優化。 NPR-26923：CQ-4250463 的 Hotfix
* 當AEM社群設為搭配DSRP運作時，依位址中的關鍵字搜尋在日曆元件頁面中無法運作。 NPR-26737：CQ-4258493 的 Hotfix
* 針對協調UI和啟用資源，實作與留言的直接連結，而非留言詳細資料中的主要貼文。 NPR-26704：CQ-4251381 的 Hotfix
* 在協調控制台上透過多重選取來協調的內容不會顯示在活動資料流上。 NPR-26695：CQ-4253244 的 Hotfix
* 在Communities Messaging的To欄位中使用名字和姓氏進行搜索不返回預期結果。 NPR-26385：CQ-4248673 的 Hotfix
* 在論壇中上傳影像以外的附件 (例如 .pdf) 時發現錯誤。NPR-27360：CQ-4257753 的 Hotfix
* 如果使用MySQL DSRP設定「作者發佈」，則取消固定或取消論壇貼文的功能將無法運作。 NPR-26125;CQ-4251520的Hotfix
* 集合元件（論壇、部落格、日曆、標識、QnA）現在在元件對話框中具有屬性，以啟用/禁用「在作者編輯模式下阻止UGC」，以在WCM編輯模式下允許/拒絕UGC載入。 NPR-26978：CQ-4248161 的 Hotfix
* 「標籤搜尋」無法用於本地化的搜尋詞。 NPR-26171：CQ-4249926 的 Hotfix
* 上一步按鈕會略過論壇搜尋中的頁面。 NPR-26950：CQ-4254804 的 Hotfix
* 在預設Http埠(80)上執行的AEM執行個體無法到達imsmanifest.xml。 NPR-27173：CQ-4252211 的 Hotfix
* 如果使用DSRP設定AEM Communities，取消將註解標示為QnA的答案則無法運作。 NPR-26247：CQ-4252232 的 Hotfix
* 無法調用Adobe儲存：414錯誤 — 使用者搜尋/content/community-components/en/search.html時觀察到的長GETURI，並選取作者欄位作為該搜尋詞的其中一個篩選器。 NPR-26643：CQ-4251303 的 Hotfix
* ASRP設定中DataCentreURL的下拉式清單值已從Dallas變更為Virginia(VA6)。 NPR-26936：CQ-4254434 的 Hotfix
* 論壇搜尋中的特殊字元會傳回錯誤或沒有結果。 NPR-26930：CQ-4247744 的 Hotfix
* 論壇搜尋中針對「結果數量」顯示的數字，對英文和德文地區設定使用錯誤的分隔字元。 NPR-27050：CQ-4248939 的 Hotfix
* 未讀通知數不會增加到21個以上。 NPR-26946、NPR-27480：CQ-4252829、CQ-4256939 的 Hotfix
* 透過分頁到達頁面時，任何元件的「註解」區段中的分頁都會讓使用者向上捲動以查看頁面內容。 NPR-27032：CQ-4251228 的 Hotfix
* 從AEM製作例項的管理控制台檢視時，無法在縮圖影像上點選社群網站資料夾。 NPR-26986：CQ-4254036 的 Hotfix
* 「全部標示為已讀取」選項只會將前10個通知標示為已讀取，而其他通知則會保持未讀，直到頁面重新整理為止。 NPR-27037：CQ-4254058 的 Hotfix
* 除非重新載入，否則不會針對「識別」觸發分頁，且主題清單（或回覆）會變長。 NPR-26193：CQ-4252104 的 Hotfix
* 使用版主憑證登入時，以及在版主的設定檔URL結尾新增「#social-activities」或「#tabs-2」時，會顯示其他使用者的活動和刪除的UGC。 CQ-4251355 的 Hotfix
* 無法從部落格文章中移除所有指派的標籤。 NPR-26851：CQ-4253359 的 Hotfix
* 刪除UGC時不會刪除與UGC的關係。 NPR-27630：CQ-4258706 的 Hotfix
* 回覆的連結在論壇回覆上無法用於列點按。 NPR-27623：CQ-4256138 的 Hotfix
* 使用者訂閱限制上限為 1000。NPR-27614：CQ-4254689 的 Hotfix
* 在角色設定中編輯網站和編輯角色時，會擲回Null指標例外狀況。 NPR-27377;CQ-4255909的Hotfix

**轉換**

* we.retail範例內容無法使用翻譯預覽。 NPR-26727：CQ-4241179 的 Hotfix

**UI - Foundation**

* 升級至AEM 6.4後，嘗試下載設定時傳回NullPointerException。NPR-27310:Granite-23573的Hotfix
* granite.platform.login修正的主動式反向移植。 NPR-26941
* 主動反向移植granite.ui.content修正。 NPR-26294
* 數字欄位元件不驗證Internet Explorer 11上的負數。 NPR-26701
* granite.ui.coralui3修正的主動式反向移植。 NPR-26662
* 針對granite.ui.coralui3-eon修正的主動式反向移植。 NPR-26666
* granite.ui.foundation.components修正的主動式反向移植。 NPR-27313
* granite.ui.commons修正的主動式反向移植。 NPR-26753
* 主動式 Foundation UI 反向移植。NPR-26248

**整合**

* 不會發佈透過定位引擎建立之AEM體驗中的修改。 NPR-24869：CQ-4247832 的 Hotfix
* 如果活動和體驗的名稱包含日文字元，則無法建立這些活動和體驗。 NPR-27271：CQ-4256857 的 Hotfix
* 更新Launch API端點。 NPR-26790：CQ-4254380 的 Hotfix
* （個人化）BrandsRetriever游走整個樹狀結構。 NPR-27060：CQ-4255790 的 Hotfix

**WCM — 管理UI**

* 新增HTTP測試，以發佈/取消發佈含有參考的頁面，以及Live Copy的UI測試。 CQ-4256894 的 Hotfix

**WCM - 頁面編輯器**

* 第一次編輯時，會停用元件的編輯工具列。 CQ-4253270 的 Hotfix

**Forms**

AEM 6.4.3.0表單的關鍵重點為：

* 啟用對具有動態實體替代的對象的陣列/清單的支援。
* 在數字簽名、Reader擴展、CryptoProvider和TrustStore中為Reader擴展工作流啟用FIPS合規性。
* 新增PDF/UA支援至使用Designer或Output Service產生的XFA表單。
* 啟用對適用性表單範本上allowedPaths屬性的支援。
* 新增AEM Forms 6.4的JBoss 7.1.4支援。

**Forms 附加元件套件**

**後端整合**

* 無法根據SOAP回應中的動態實體填入表單資料模型對應。 NPR-26428：CQ-4250639 的 Hotfix
* 使用測試UI輸入的表單資料模型中，_elementNamespace的值未正確反映在SOAP請求中。 CQ-4255373 的 Hotfix
* 可為null的屬性約束已用預設值初始化，無法與FDM同步。 CQ-4253873 的 Hotfix
* 對於OData資料源，nullable屬性的預設值未設定為True。 CQ-4253870 的 Hotfix

**調適型表單**

* 無法載入網站和表單編輯器。 NPR-26977;CQ-4249170的Hotfix
* 使用鍵盤將附件新增至最適化表單時發生問題。 NPR-25913;CQ-4249456的Hotfix

**Forms -互動式通訊**

* 無法在互動式通訊網頁頻道和最適化表單的內容樹中，使用「新增子面板」選項來移動已新增的面板。 CQ-4253915 的 Hotfix
* 在「列印」管道的「資料來源」區段中，會顯示表格名稱，而非FDM關聯的標題。 CQ-4253669 的 Hotfix
* isUseXFABullets()函式未在PrintChannelRenderOptions類中禁用，並且可在客戶端SDK中使用。 CQ-4246583、CQ-4252700

**通信管理**

* 6.4版Javadoc不包含com.adobe.dbforms。*包和相應的類。 CQ-4253200 的 Hotfix
* 如果測試資料XML沒有輸入，CCR UI會為日期欄位顯示預設的無用值。 CQ-4252041 的 Hotfix
* 如果信函包含清單模組，從信函產生PDF時，項目符號與文字之間的空格會遺失。 CQ-4250588 的 Hotfix

**Forms Manager**

* 啟用對適用性表單範本上allowedPaths屬性的支援。 NPR-26598：CQ-4255892 的 Hotfix

**Forms - 工作流程**

* 如果執行Forms工作流程時，任務名稱中包含大括弧，記錄中會顯示例外狀況。 CQ-4256626 的 Hotfix
* 無法在AEM Forms工作區中開啟「搜尋」範本。 CQ-4255651 的 Hotfix

**行動 Forms**

* 在AEM Forms中退出日期欄位時，退出通知不會顯示，該欄位在Internet Explorer或Chrome中呈現為HTML。 NPR-26483：CQ-4239352 的 Hotfix
* 處理開始時，XML中包含的日期會在使用者嘗試離開表單時導致表單出現驗證錯誤。 NPR-26787：CQ-4251211 的 Hotfix

**Forms - JEE 安裝程式**

**PDF產生器服務**

* 無法顯示PDF生成器的標準報告和合規性設定。 NPR-26715：CQ-4253384 的 Hotfix
* AIX Forms附加套件中缺少convertpdf二進位檔案，導致叫用PDFA服務時失敗。 CQ-4257873 的 Hotfix
* 處理TIFF檔案時紙張擷取服務當機。 NPR-28079：CQ-4240649 的 Hotfix

**文件服務**

* 在數字簽名、Reader擴展、CryptoProvider和TrustStore中為RE工作流添加FIPS合規性。 NPR-27495：CQ-4257572 的 Hotfix
* 在循環中運行AssemblerService.toPDFA服務時，轉換失敗。 NPR-26354：CQ-4248656 的 Hotfix
* 無法根據PDF/A-1b標準正確驗證PDF符合性。 NPR-26286：CQ-4227539 的 Hotfix
* 將AEM Forms從6.1 SP2 CFP5升級至CFP13時出現記憶體不足問題。 NPR-26285：CQ-4244379 的 Hotfix
* 無法根據PDF/A標準正確驗證PDF符合性。 NPR-26272：CQ-4248823 的 Hotfix

**Forms - Foundation JEE**

* 針對AEM Forms 6.4新增JBoss 7.1.4支援。NPR-27331;CQ-4255601的Hotfix

**包含 Feature Pack**

* 啟用對具有動態實體替代的對象的陣列/清單的支援。 NPR-26590：CQ-4254655 的 Hotfix

**包含的OSGI套件組合和內容套件**

AEM 6.4.3.0 中包含的 OSGi 套件組合清單

[取得檔案](assets/6.4.3.0_bundles.txt)

AEM 6.4.3.0 中包含的內容套件清單

[取得檔案](assets/6.4.3.0_OSGI.txt)

#### AEM 6.4.2.0 {#experience-manager-6420}

AEM 6.4.2.0為重要更新，包含效能、穩定性、安全性和重要客戶修正，以及自AEM 6.4全面推出以來所發行的增強功能， **2018年4月。**
這也是累積的，也就是說6.4.2.0包含之前發行的所有AEM 6.4 Service Pack。

AEM 6.4.2.0的部分關鍵重點為：

* 內建存放庫 (Apache Jackrabbit Oak) 更新至 1.8.7 版。
* 新增對HTML範本語言(HTL)規格1.4功能的支援
* 新增對MongoDB Enterprise 3.6的支援。
* Sites頁面編輯器新增了內容內編輯和合成的支援，其中包含在React或Angular中建置的用戶端元件，並搭配 <a href="../sites-developing/spa-walkthrough.md">AEM SPA Editor JS SDK</a>.
* 內容片段增強功能：新增可在文字欄位中加上注釋，並並排比較版本的功能。
* 新增 [整合Adobe Stock](/help/assets/aem-assets-adobe-stock.md) 讓使用者直接從AEM使用者介面搜尋、預覽、儲存及授權Adobe Stock資產。 如需詳細資訊，請參閱 [搭配Adobe Stock資產使用AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/creative-workflows/adobe-stock.html).
* 新增Assets支援動態條件式中繼資料結構，以及為資產資料夾設定中繼資料結構的功能。
* 在每個元件中新增設定，以啟用/停用資料夾縮圖建立/更新功能。
* 頁面編寫時的影像編輯器增強功能。
* 社群中的回歸修正，若刪除所選答案，計分事件無法正確處理。
* 將solr的搜尋結果上限修訂為MAX_INT-10000。
* 「事務刷新」作業僅在首次調用storeTransaction時啟動。
* 「卡片檢視」和「欄檢視」現在提供「全選」按鈕。
* 改善CoralUI的協助工具。
* 改善Coral.Keys處理方式。
* 將moment.js更新至2.22.2
* 將jquery更新至1.12.1
* 引入了基礎工作流程狀態元件。
* 將GCC更新至最新版本。
* 將SAML移至新的外部IDP同步。

**資產**

* pptx檔案的子資產產生不包含任何影像和縮圖。 NPR-24286：CQ-4217986 的 Hotfix
* migrateAllAssets — 新增批次處理支援，並改善將UUID新增至舊資產的AEM方法。 NPR-24861：CQ-4242863 和 CQ-4247874 的 Hotfix
* 產生縮圖時出現效能問題。 NPR-24693：CQ-4246960 的 Hotfix
* （觸控式UI）新增至「資產共用發佈者」頁面時，「選項述詞」元件會保留空白。 NPR-24643：CQ-4245295 的 Hotfix
* （工作流程）智慧標籤資產不會透過代理設定處理。 NPR-25840：CQ-4248202 的 Hotfix
* (Omnisearch)移除搜尋條件中的檔案類型：影像不會移除影像類型。 NPR-25232：CQ-4248280 的 Hotfix
* 嘗試將檔案移至其他資料夾時，不會顯示名稱帶有單引號的資料夾。 NPR-25125：CQ-4248660 的 Hotfix
* 當語言偏好設定為英文以外的其他值時，子資產頁面中的滑桿無法正常運作。 NPR-25274：CQ-4248489 的 Hotfix
* 在具有歐洲數字格式的電腦上開啟時，中繼資料匯出csv檔案的問題。 NPR-26009：CQ-4250677 的 Hotfix
* 沒有「刪除」權限的資產資料夾選取項目無法使用「建立」按鈕。 NPR-25788：CQ-4250140 的 Hotfix
* （反向移植）輔助功能增強：Duplicate-id:id屬性值必須唯一，標籤：表單元素必須有標籤和連結名稱：連結必須有可辨識的文字。 NPR-24252：CQ-4250905、CQ-4250906、CQ-4250907 的 Hotfix
* 上傳含有以「，」分隔欄位的csv時，歐洲國家/地區會失敗。 NPR-25549：CQ-4249931 的 Hotfix
* (Brand Portal)發佈資產時，多頁pdf檔案的子資產不會發佈。 NPR-25991：CQ-4245162 的 Hotfix
* 稍後發佈AEM到Brand Portal復寫的功能。 NPR-25911：CQ-109139 的 Hotfix
* 非管理員使用者發佈和取消發佈私人集合會產生NPE。 NPR-25906：CQ-4250594 的 Hotfix
* 停用將內容片段和表單結構發佈至Brand Portal。 NPR-24176、NPR-26004：CQ-4251592、CQ-4252026 的 Hotfix
* (Dynamic Media)將DM檢視器更新為5.10.1版，可啟用「影像預設集」頁面上重複名稱的檢查。 請參閱更新Dynamic Media檢視器(5.10.1)。 NPR-24403：CQ-4247554 的 Hotfix
* 選取資產或資料夾時，瀏覽器主控台中的欄檢視出現Javascript錯誤。 NPR-25939：CQ-4250228 的 Hotfix
* （欄檢視）無法識別工作，因為主要檔案顯示為空白項目。 NPR-25903：CQ-4246307 的 Hotfix

**網站**

* AEM 6.2上資料來源.jsp的查詢與AEM 6.4不同。NPR-24968:CQ-4244235的Hotfix
* （傳統UI）無法將標籤新增至頁面。 NPR-25255、NPR-25612：CQ-4249615 的 Hotfix
* HTML模板語言規範1.4功能向後移植到AEM 6.4.2.0 NPR-24585
* 複製即時副本頁面後，本機元件的繼承錯誤。 NPR-25920：CQ-4236737、CQ-4248957 的 Hotfix
* 開啟/關閉時間會儲存在crx/de中，但不會在頁面屬性UI主控台中擷取相同內容。 NPR-25154：CQ-4243431 的 Hotfix
* 樣式系統中斷對話框的初始屬性值。 NPR-25648：CQ-4250073 的 Hotfix
* 在cq:htmlTag節點中定義cq:tagName屬性時，如果透過JSP包含元件，則不會考慮標籤名稱。 NPR-24154：CQ-4244120 的 Hotfix
* 針對巢狀的 parsys 元件，一律從多個可用元件中套用滿足設計的第一個元件 (最短巢狀路徑)。如需詳細資訊，請參閱[設計路徑解析](https://experienceleague.adobe.com/docs/experience-manager-64/developing/platform/templates/page-templates-static.html)。NPR-24973：CQ-4246276 的 Hotfix
* 將文字貼入RTE元件時，會顯示快顯對話方塊，但無法正確轉譯。 NPR-24895：CQ-4245901 的 Hotfix
* (RTE)強制欄位指標的績效問題。 NPR-24894：CQ-4241895 的 Hotfix
* （頁面元件）新增元件至Parsys時，會從右側裁切，而出現裝置框架寬度。 NPR-25536：CQ-4238224 的 Hotfix
* 純文字編輯器會傳送未裁切的資料，並新增額外的空格。 NPR-25312：CQ-4249006 的 Hotfix
* 使用 inlide 模式開啟元件時，先前載入的外掛程式第二次會無法顯示。NPR-24610：CQ-4236850 的 Hotfix
* 透過複製/貼上在編輯器檢視中載入XF時，不會自動載入主變數。 NPR-24841：CQ-4248037 的 Hotfix
* 網站管理員/damadmin中的HTML結構錯誤，會中斷IE11。 NPR-24686：CQ-4246363、CQ-4248402 的 Hotfix
* （管理出版物精靈）「選項」步驟中的啟用日期日曆，在「範圍」步驟中執行某些動作後，無法開啟。 NPR-25681：CQ-4250205 的 Hotfix
* 由於功能遭淘汰，傳統 UI 無法用於編輯 CUG。NPR-25075：4241823 的 Hotfix
* 建立選項無法建立體驗片段。 NPR-26053：CQ-4249923 的 Hotfix
* XF變異因此啟動兩次，為相同項目產生重複ID。 NPR-24179：CQ-4245093 的 Hotfix
* Foundation 表格容易受到儲存型跨網站指令碼攻擊。NPR-25185：CQ-4240760 的 Hotfix
* 將元件從AEM 6.2.1.13移轉至AEM 6.4時，出現「無效的遞回選擇器值」錯誤。NPR-24146

**WCM - 頁面編輯器**

* 因為執行時間長的查詢 (超過 6 個) 出現多個堆疊，導致 AEM 變得緩慢。CQ-4240247 的 Hotfix
* 在cq:htmlTag節點中新增空cq:tagName時發生JS錯誤。 CQ-4251852 的 Hotfix
* 根據columnClassNames重定位更新EditableActions。 CQ-4250781 的 Hotfix
* 使用單一屬性和屬性公開資源和模型路徑。 CQ-4251255 的 Hotfix
* 還原export.json API中斷變更。 CQ-4251854 的 Hotfix
* (可編輯的SPA)1.0.0的候選版本。CQ-4251991的Hotfix
* 編輯任何元件時，編輯工具列會針對其他元件而停用。 CQ-4253270 的 Hotfix

**整合**

* 程式庫和下載URL欄位應可編輯。 NPR-24804：CQ-4246864 的 Hotfix
* 多個DTM設定發生問題。 NPR-24685：CQ-4247293 的 Hotfix
* 新增對托管用戶端程式庫非同步部署的支援。 NPR-25716：CQ-4245745 的 Hotfix
* 目標元件（缺少對應的選件）會呈現整個頁面，而非空的目標元件，則會新增頁面的另一個完整轉譯。 NPR-25273：CQ-4248003 的 Hotfix
* 目標引擎 (mbox.js、at.js) 沒有使用損害 URL 而使用包含冒號的 URL，這可能因為某些部署而失敗。NPR-25339：CQ-4237854 的 Hotfix
* （啟動）LibraryDownloadProcess儲存錯誤的libraryUri值。 NPR-25330：CQ-4250006 的 Hotfix

**平台**

* 重新索引環 |在從6.3就地升級至6.4期間執行BinaryTextExtraction時執行NPE。Granite的Hotfix - 21677
* 內部已標籤路徑的跨界覆寫/libs/cq/cloudserviceconfigs/templates/configpage/jcr:content — 執行模式偵測器時發生問題。 NPR-25036：CQ-4248597 的 Hotfix
* 由於LogEntryImpl中的NPE，未寫入日誌條目。 NPR-25627：Granite-22383 的 Hotfix
* 復寫刪除事件時不會檢查權限。 NPR-25679：CQ-4241234 的 Hotfix
* 在「Day CQ Mail Service」中新增STARTTLS支援。 NPR-25611：CQ-4249924 的 Hotfix
* granite.platform.login修正的主動式反向移植，可改善協助工具。 NPR-25176:Granite 21746和Granite-21309的Hotfix
* (AEM 6.4)重新建立套件並重新安裝時發生錯誤。 NPR-25173：CQ-4247939 的 Hotfix
* 移除預設的MERGE_PRESERVE aclHandling。 NPR-24593：Granite-21889 的 Hotfix
* 套用ContentDispositionFilter兩次後，回應中不會傳播Content-Type且遺失。 NPR-24175：Sling-7525 的 Hotfix
* 升級至AEM 6.4分支後，套件管理器狀態錯誤。 NPR-24551：Granite-21750 的 Hotfix
* AMS例項 — 錯誤記錄分析。 CQ-4249567 的 Hotfix

**安全性**

* SAML重新登入會重新導向，使用Okta IDP登出頁面。 NPR-25523：GRANITE-22364 的 Hotfix
* 透過OAK外部IDP OAuth提供者設定的IMS驗證會停用在AEM中建立的使用者。 NPR-25301：Granite-22363 的 Hotfix

**MAC - Test&amp;Target 整合**

* （定位）定位期間文字元件錯誤。 CQ-4233343 的 Hotfix

**社群**

* （檔案程式庫）從下載含空白字元的資產時，會造成格式問題。 NPR-24260：CQ-4245159 的 Hotfix
* 多個 Adobe Social 問題的修正。NPR-24247：CQ-4245054、CQ-4245120、CQ-4245296 的 Hotfix
* 如果作者發佈在不同內容路徑上執行，成員和群組控制台的無限捲動會失敗。 NPR-24437：CQ-4246013 的 Hotfix
* 即使從已應答狀態中刪除貼文，貼文也不會返回未應答狀態，且分數不會減少。 NPR-24419：CQ-4245797、CQ-4245932 的 Hotfix
* 在社群中使用日曆功能新增的事件會輸出錯誤的值。 NPR-24883：CQ-4244056 的 Hotfix
* （社群論壇）分頁點按和頁面載入行為問題。 NPR-24880：CQ-4246109 的 Hotfix
* (Chrome)社群事件的時區轉換會失敗。 NPR-24881：CQ-4247115 的 Hotfix
* 無法在電子郵件中呈現內嵌物件。 NPR-24999：CQ-4248022 的 Hotfix
* 除了建立UGC外，還應在UGC更新時執行自動協調序列。 NPR-25892：CQ-4251399 的 Hotfix
* 群組上的強制回應對話方塊。 NPR-25623：CQ-4248805 的 Hotfix
* 刪除內容時擲回解決器例外狀況。 NPR-25869：CQ-4248908 的 Hotfix
* 含有大量貼文之主題的已編頁連結在通知上無法運作。 NPR-25678：CQ-4243038 的 Hotfix
* 搜索結果中的時間值顯示伺服器時間，而不是客戶端的時區。 NPR-25594：CQ-4248986 的 Hotfix
* （論壇意見）瀏覽器返回按鈕未如預期運作。 NPR-25205：CQ-4248573 的 Hotfix
* （搜尋結果）瀏覽器返回按鈕未如預期運作。 NPR-25214：CQ-4248574 的 Hotfix
* 覆蓋communitygroupmemberlist元件時返回Null。 NPR-25228：CQ-4248523 的 Hotfix
* （社群日曆）使用新封面影像儲存事件時產生ClassCastException。 NPR-25167：CQ-4248662 的 Hotfix
* （社群）訊息遭截斷。 NPR-25326
* （AEM發佈）Scorm資源因內容路徑而失敗，且顯示空白畫面。 NPR-26155：CQ-4251942 的 Hotfix
* (MSRP)新建立的日曆會儲存到錯誤記錄中，部分擲回NPE。 NPR-26071：CQ-4250531 的 Hotfix
* 論壇/主題分頁只會在頁面重新整理時更新。 NPR-26070、NPR-25965：CQ-4249509 的 Hotfix
* （問答論壇）開啟評論的直接連結時無法導覽至上一頁。 NPR-26069：CQ-4251699 的 Hotfix
* 在「建立」群組中上傳影像在行動裝置上無法運作。 NPR-26172：CQ-4251703 的 Hotfix
* （傳訊）使用DSRP時，訊息接收器的名稱一律顯示為「未知」。 NPR-26056：CQ-4251397 的 Hotfix
* 啟用 Scorm 資源完成狀態在 UI 中顯示為空白。NPR-26034：CQ-4249994 的 Hotfix
* 建立新社群群組時，會在作用中/作用中的mongoMK叢集上建立重複的社群群組。 NPR-26032：CQ-4245884 的 Hotfix
* （製作）群組建立精靈在精靈中載入/建立群組所需的時間太長。 NPR-26031：CQ-4244966 的 Hotfix
* 在hbs指令碼中新增include陳述式時，Parsys會消失。 NPR-25908：CQ-4250489 的 Hotfix
* 啟用「允許有特殊權限者」時，有特殊權限的成員應只能為具有社群成員身分的使用者撰寫內容。NPR-25877：CQ-4248450 的 Hotfix
* 阻止深層連結以啟用。 NPR-25966：CQ-4251478 的 Hotfix
* 移除回覆時，不會動態更新論壇分頁。 NPR-25970：CQ-4248975、CQ-4252843 的 Hotfix
* 在巢狀註解的情況下，自動捲動和反白顯示在日曆和篩選事件上無法運作。 NPR-25958：CQ-4251471 的 Hotfix
* (DSRP)直接/深層連結效能因大量使用者產生的內容而降低。 NPR-25957：CQ-4251470 的 Hotfix
* 無法修改允許特權成員和特權成員的屬性。 NPR-26014：CQ-4244592 的 Hotfix
* 將全部標籤為已讀取會重設所有社群頁面的通知計數器。 NPR-25931：CQ-4248612 的 Hotfix
* 編輯IT因DSRP而失敗。 NPR-25929：CQ-4251382 的 Hotfix
* 建立電子郵件範本時，由於NPE，電子郵件IT失敗。 NPR-26039：CQ-4250962 的 Hotfix
* 內嵌解析度極高的影像時，會出現論壇執行緒問題。 NPR-26037：CQ-4244453、CQ-4253099 的 Hotfix
* 當伺服器時區與用戶時區不同時，時間顯示交換機。 NPR-26036：CQ-4248751 的 Hotfix
* 將相同名稱的檔案附加至論壇貼文兩次，會導致伺服器錯誤。 NPR-24172：CQ-4244367 的 Hotfix
* 反向移植效能修正 — 在作者和發佈上分組分頁、在作者上分組搜尋、避免日誌、日曆和構想的回覆序列化，以及在檢視群組清單頁面時為取得每個群組的群組成員資格（邀請/取消邀請）按鈕進行延遲載入。 NPR-24538：CQ-4246515 的 Hotfix
* 製作上看不到啟用資源。 CQ-4252618 的 Hotfix
* 不會從未知用戶生成線程通知。 CQ-4245132 的 Hotfix
* 群組搜尋不會顯示在左側邊欄上。 CQ-4252621 的 Hotfix
* （作者）群組主控台分頁無法運作。 CQ-4242786 的 Hotfix
* jQuery UI升級。 CQ-4248894 的 Hotfix
* 升級至最新SCORM 2017.1版。 NPR-25675：CQ-4240671 的 Hotfix
* 非社群使用者可看到「代表撰寫」欄位。 NPR-25331：CQ-4247858 的 Hotfix
* 即使刪除後，貼文仍會顯示在UI上，並在主控台上產生錯誤。 NPR-26290：CQ-4252803 的 Hotfix
* （網站設定）可儲存對角色所做的變更。 NPR-26274：CQ-4252187 的 Hotfix
* （安全漏洞）由於JSON Web令牌配置錯誤，帳戶遭接管。 NPR-26458：CQ-4253314 的 Hotfix
* 移除回覆時分頁不會重設。 NPR-26326：CQ-4252997 的 Hotfix
* 編輯時附件影像不會顯示在草稿中。 CQ-4253360 的 Hotfix
* 在關係資料庫(DSRP)中附加附件時頁面未重新整理。 CQ-4253084 的 Hotfix
* 群組無法在啟用網站資源內運作。 CQ-4252975 的 Hotfix
* 啟用中不會保留必要學習路徑。 CQ-4252948 的 Hotfix

**工作流程**

* 工作流程啟動器UI不會顯示過去41個啟動器設定，且會在主控台中觸發JavaScript錯誤。 NPR-25028：CQ-4247604 的 Hotfix
* 在不編輯啟動器的情況下編輯舊版工作流程，會導致在包含「啟動頁面/資產」步驟的任何工作流程上建立多個工作流程。 NPR-25870：CQ-4250896 的 Hotfix
* 如果頁面有中繼資料節點，則工作流程裝載中的連結不正確。 NPR-25916：CQ-4250733 的 Hotfix

**轉換**

* 修正匯入翻譯的專案會發出兩個同時進行的POST請求，因此會造成錯誤的問題。 NPR-24889：CQ-4247638 的 Hotfix
* 修正建立多語言翻譯專案時，相同語言的所有頁面都會新增至相同工作的問題。 NPR-25091：CQ-4246112 的 Hotfix
* 修正某些情況下，翻譯工作只會列出前40頁。 NPR-25974：CQ-4248661 的 Hotfix
* DataPicker元件(Coral2)不會變更年份。 NPR-24466：Granite-21893 的 Hotfix

**UI - Foundation**

* 主動式 Foundation UI 反向移植。NPR-24344、NPR-24345、NPR-25176、NPR-25095、NPR-24332、NPR-25653、NPR-25932、NPR-25935、NPR-25976
* （設計匯入工具）匯入頁面不會匯入js、css。 NPR-25203：Granite-22236 的 Hotfix
* 主動式Foundation UI反向移植，以提高產品的穩定性。 NPR-24334

**MAC - Test&amp;Target 整合**

* 個人化精靈的第二個頁面（由「開始鎖定目標」啟動）空白，且會擲回主控台錯誤。 CQ-4253277 的 Hotfix

**體驗片段**

* 將體驗片段/Target整合合併至AEM 6.4.2.0。CQ-4248653的Hotfix

**內容片段管理**

* 內容片段註解和內容片段版本的並排比較。 CQ-4247148 的 Hotfix

**DAM - 一般**

* 「簽出者」篩選器在搜索中無法正常工作。 CQ-4247070 的 Hotfix
* 執行資產更新工作流程時，資產語言副本及其縮圖會變成空白。 CQ-4250641 的 Hotfix
* Duplicate-id:id屬性值必須是唯一的。 CQ-4250905 的 Hotfix
* 標籤：表單元素必須有標籤。 CQ-4250906 的 Hotfix
* 連結名稱：連結必須有可辨識的文字。 CQ-4250907 的 Hotfix
* 埠資料夾元資料模板遷移JMX和ServiceUserMapping。 CQ-4252947 的 Hotfix
* WebdriverIO測試未在CQ/dam的發行版/640分支中運行。 CQ-4252749 的 Hotfix
* 如果已發佈連結，則移動資產的連結不會重構。 CQ-4245756 的 Hotfix

**DAM — 檢視器**

* 使用新檢視器載入視訊時發生間歇性錯誤5.10.1。CQ-4250562的Hotfix

**DAM-Brand Portal**

* 從Brand Portal取消發佈集合失敗，並顯示錯誤。 CQ-4245990 的 Hotfix
* 無法從Brand Portal取消發佈影像預設集。 CQ-4246140 的 Hotfix
* 發佈資產時，多頁pdf檔案的子資產不會發佈。 CQ-4245162 的 Hotfix

**DAM - DMClient**

* 將視訊資產發佈至YouTube時，產生YouTube的標籤會包含標籤的完整路徑。 CQ-4245549 的 Hotfix
* （選擇退出和選擇加入升級）檢視器CSS重新導向的問題。 CQ-4247854 的 Hotfix
* 無法建立/編輯非「管理員」組成員的查看器預設集。 CQ-4247618 的 Hotfix
* (6.4.1.0)在多個parsys中新增多個視訊會中斷視訊播放器。 CQ-4248517 的 Hotfix
* 重新命名和在影像集內移動資產導致無法編輯。 CQ-4248434 的 Hotfix
* 將大型影片發佈至YouTube會擲出逾時訊息。 CQ-4237831 的 Hotfix
* （清單檢視）資產選擇器/選擇器的使用者介面會變更為全部灰色，且使用者已停用。 CQ-4237817 的 Hotfix
* （垂直縮放）Css無法載入，出現404錯誤。 CQ-4236508 的 Hotfix
* 嘗試下載資產名稱中包含百分比(%)字元的資產時，會產生空的封存。 CQ-4250558 的 Hotfix
* （卡片檢視）在視訊資產上使用複製和貼上功能時，不會顯示處理指標。 CQ-4249037 的 Hotfix
* （從6.3.2升級至6.4）預先升級的影像預設集在轉譯頁面上會顯示為「未發佈」，但在選取時未產生URL按鈕。 CQ-4240406 的 Hotfix
* 技術負債/微幅增強。 CQ-4240648 的 Hotfix
* 資產選擇器（或資產選擇器）不會顯示可用資料夾中的所有資產。 CQ-4218414 的 Hotfix
* 沒有高度的影像預設集顯示大小不正確的影像。 CQ-4246546 的 Hotfix
* （多頁資產）按一下註解時UI會中斷。 CQ-4251434 的 Hotfix
* 從6.3升級至6.4及更新版本的Analytics預設集，會建立新的報表套裝和Analytics預設集，遺失使用者的舊報表資料。 CQ-4244529 的 Hotfix
* （管理出版物精靈）嘗試發佈或取消發佈時，資產清單似乎為空白。 CQ-4251881 的 Hotfix
* 在查看「設定成員」後選擇「查看器」時，AVS視頻無法播放。 CQ-4205308 的 Hotfix
* 預先升級視訊處理預設集無法新增視訊編碼預設集，也無法編輯現有的編碼預設集。 CQ-4240407 的 Hotfix
* 影像預設集不會套用至下載的動態轉譯。 CQ-4249862 的 Hotfix
* 「檢視器預設集」清單頁面上的「全部選取」按鈕無法正常運作。 CQ-4252462 的 Hotfix
* 視訊設定檔：選擇「全部」按鈕無法工作。 CQ-4253076、CQ-4251447
* SP2驗證通過 — 煙霧通過。 CQ-4251639 的 Hotfix

**DAM - DMServices**

* Dynamic Media無法為EPS檔案產生轉譯。 CQ-4243688 的 Hotfix

**Granite**

* 捆綁包SymbolicName中的類型會導致重複捆綁包。 Granite-22155 的 Hotfix
* CUGConfiguration不能提取CugExclude。 Granite-21109 的 Hotfix
* 重新啟動AdobeGranite工作流程核心會從中間重新執行工作流程步驟，以建立不必要的工作流程。 NPR-25057：Granite-22218 的 Hotfix
* JcrResourceBundle不正確支援多個基名。 NPR-25245：Granite-22317 的 Hotfix
* 安裝內容包時，ACL按主體分組，因此會破壞權限模型。 NPR-24583：Granite-21591 的 Hotfix
* 將Jetty更新為9.4.11以修正漏洞。 NPR-25030：Granite-22120 的 Hotfix

**Forms**

AEM 6.4.2.0表單的關鍵重點為：

* 已新增「佇列」的屬性，以便更新而不重新整理瀏覽器。
* 新增功能，讓使用者對多個服務使用相同的WSDL檔案。
* 從日期選擇器下拉式清單中移除不支援的時間戳記模式。
* 新增在OSGI中隱藏xfaf和pdf的支援。
* 新增支援以使用 [交易報告功能](https://experienceleague.adobe.com/docs/experience-manager-64/forms/transaction-reports/transaction-reports-overview.html) 內部部署。
* 新增程式碼，以在條件規則編輯器中不顯示子變數。

**Forms 附加元件套件**

**交易報告**

* 更新事務報告配置，使用在發佈伺服器上配置的反向複製的重要性。 NPR-26050：CQ-4246650 的 Hotfix
* 定期刷新作業的延遲初始化。 NPR-25968：CQ-4245024 的 Hotfix
* 事務記錄失敗，指針異常為Null。 CQ-4247302 的 Hotfix

**Forms - 工作流程**

* (HTML 工作區) 使用者認領任務時，系統會重新整理該特定使用者的佇列計數，但除非重新整理頁面，否則不會為其他使用者重新整理。此問題已由新屬性修正。 若要將此新屬性設定至您的AEM例項，請參閱其組態設定。 NPR-24536：CQ-4233665 的 Hotfix
* 無法在6.4的AEM Forms應用程式中載入大型表單。NPR-24463:CQ-4245091的Hotfix
* 嘗試檢視共用任務時，行動工作區應用程式發生問題。 NPR-25177：CQ-4248733 的 Hotfix
* Web和APK之間的驗證行為不一致。 NPR-25670：CQ-4248178 的 Hotfix
* 當呼叫Web服務時，在用戶端內開啟HTML5表單時，會失敗並傳回錯誤訊息。 NPR-26048：CQ-4244716 的 Hotfix
* 在AEM表單Windows應用程式6.3中呼叫服務時發生問題。NPR-26468:CQ-4252341的Hotfix

**行動 Forms**

* （表單集）預覽時發生SSN和行動欄位驗證問題。 NPR-24458：CQ-4244983 的 Hotfix
* 在HTML預覽中預填多行欄位時不會顯示資料。 NPR-24549：CQ-4244212 的 Hotfix
* 在多行欄位上評估指令碼時，資料會遺失。 NPR-25333、CQ-4249610的Hotfix

**Forms — 互動式通訊與通信管理**

* 在具有基本模板和參考IC打印模板的IC上同步失敗。 NPR-24912
* (CCR)欄位/變數的驗證器無法運作。 CQ-4245047 的 Hotfix
* 「文字編輯」工具列上的「資料模型物件」圖示會間歇性消失。 CQ-4245122 的 Hotfix
* 如果刪除原始IC，則複製的IC上會出現異常日誌。 CQ-4249378 的 Hotfix
* 在信函轉譯中，即使資料正確，條件也不會評估為true。 CQ-4245944 的 Hotfix
* 從內容樹中選取時，不會反白顯示自動產生的元件。 CQ-4246178 的 Hotfix
* 開啟「Web頻道範本」編輯器時發生問題。 CQ-4248182 的 Hotfix
* 無法變更新增資產的順序，因為向上/向下箭頭仍為停用狀態。 CQ-4252042 的 Hotfix
* 無法更新條件模組的屬性。 CQ-4247909 的 Hotfix
* 當使用者在Web通道中重新排列物件時，需要改善「取消繼承」對話方塊的UX。 CQ-4241076 的 Hotfix
* 與 XDP 中所定義繫結對應的信函中的資料，不會在使用直接信函 URL 時填入。CQ-4245833 的 Hotfix
* （快取問題）Web通道的同步不反映對版面片段、列印通道的文字片段所做的變更。 CQ-4251460 的 Hotfix
* 無法更新「佈局」段和DD屬性。 CQ-4247830 的 Hotfix
* (CCR)草稿重新載入因XML解析而失敗。 CQ-4250950 的 Hotfix
* （IC編輯器）「編輯片段」按鈕應該更容易找到。 CQ-4244694 的 Hotfix
* (XDP)在新建立的子表單中新增版面片段時，會顯示空白畫面。 CQ-4248810 的 Hotfix
* DocumentFragment-master-DeployWithServerSideTests測試失敗。 CQ-4245496 的 Hotfix
* 條件模組中重複的文字模組變數例項。 CQ-4252128 的 Hotfix
* PDF預覽URL在發佈時不會顯示交易報表。 CQ-4246158 的 Hotfix
* IC同步與打印通道到Web通道同步相關的問題。 CQ-4251505 的 Hotfix
* EXM代碼清理：刪除LocalFunctionMapper。 CQ-4243265 的 Hotfix
* 更正IC的webChannel表元件的TableHeader的資源類型。 CQ-4251821 的 Hotfix
* （IC編輯器）可用性問題。 CQ-4241081 的 Hotfix
* 列印管道子表單未顯示插入功能。 CQ-4252994 的 Hotfix
* 移除FDM節點或變數預留位置後，保留變更同步失敗。 CQ-4253178 的 Hotfix
* （範本編輯器）基本範本顯示頁首/頁尾的其他拖放區域，而開啟Web頻道時畫面會閃爍。 CQ-4253323 的 Hotfix
* 從內容樹中選取時，自動產生的元件不會醒目顯示。 CQ-4246178 的 Hotfix

**文件服務**

* （表單服務）OSGI不支援XFAF。 NPR-25181、CQ-4251313的Hotfix
* 組合PDF檔案標題中的字元將亂碼。 NPR-25113：CQ-4244682 的 Hotfix

**調適型表單**

* 以「傳送郵件」的形式提交動作會擲回例外狀況，而CC/BC欄位會空白。 NPR-25019：CQ-4243039 的 Hotfix
* 由於查詢效率低下，無法使用OOTB AEM表單元件。 NPR-25065：CQ-4247256 的 Hotfix
* 從guideImageChoiceComponent的對話方塊節點中移除sling:orderBefore。 CQ-4245013 的 Hotfix
* （日期選擇器）「編輯模式」不支援兩種類型的時間戳記模式。 CQ-4237982 的 Hotfix
* 使用「Forms Workflow」傳統版編寫問題提交動作。 CQ-4236981 的 Hotfix
* （Web通道）IC圖表應繼承AF圖表中的colspan屬性。 CQ-4252143 的 Hotfix

**後端整合**

* （SOAP請求）大小數（超過6位數）以指數表示法表示，導致驗證錯誤。 NPR-25283：CQ-4248100 的 Hotfix
* 對複雜類型中定義的可選參數進行錯誤驗證。 NPR-25070：CQ-4247107 的 Hotfix
* 新增功能，讓使用者對多個服務使用相同的WSDL檔案。 NPR-24604、CQ-4247756的Hotfix
* FDM會混亂其SOAP呼叫中的參數順序。 NPR-25069、CQ-4247180的Hotfix
* FDM合併SOAP請求中的實體（在清單/陣列中）。 NPR-25284：CQ-4248375 的 Hotfix

**Forms JEE 安裝程式**

**PDFG 服務**

* 安全設定的建立/修改功能無法運作。 NPR-24769：CQ-4246927 的 Hotfix
* Optimize PDF，透過單一API呼叫選擇性地取消內嵌字型。 NPR-23287

**文件服務**

* 輸出服務未為輔助工具Reader提供正確的標籤。 NPR-24438、NPR-24439、NPR-24440、NPR-24441:CQ-4243849、CQ-4243845、CQ-4243852、CQ-4243853的Hotfix

**文件安全性**

* 使用檔案安全性建立原則時發生問題。 NPR-25586、NPR-25547：CQ-4247086 的 Hotfix

**Forms - Foundation JEE**

* 間歇性地以系統上下文帳戶運行的進程。 NPR-25289、NPR-25313：CQ-4249331 的 Hotfix
* AEM Forms JEE受到Apache Struts和Jackson資料捆綁安全性警報的影響。 NPR-25628：CQ-4242891 的 Hotfix
* 電子郵件起始點程式無法運作。 NPR-25253：CQ-4248518 的 Hotfix

**包含 Feature Pack**

**資產**

* 新增 [整合Adobe Stock](/help/assets/aem-assets-adobe-stock.md) 讓使用者直接從AEM使用者介面搜尋、預覽、儲存及授權Adobe Stock資產。 如需詳細資訊，請參閱 [搭配AEM資產使用Adobe Stock資產](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/creative-workflows/adobe-stock.html). NPR-15779：CQ-30857 的 Hotfix
* 新增對動態條件式中繼架構的支援。 如需詳細資訊，請參閱 [階層式中繼資料](/help/assets/cascading-metadata.md). NPR-25189：CQ-4237413 的 Hotfix
* 在內容片段上啟用「資產下載」選項。 如需詳細資訊，請參閱 [資產報表](/help/assets/asset-reports.md). NPR-25186：CQ-4237410 的 Hotfix
* 可為資產資料夾設定中繼資料結構。 如需詳細資訊，請參閱 [資料夾中繼資料結構](/help/assets/folder-metadata-schema.md) 並參考其 [組態設定](#configuration-settings-required-for-npr) 安裝AEM 6.4.2.0後。 NPR-21268：CQ-4221574 的 Hotfix

**網站**

* 允許編輯內容片段而不具有刪除權限。 如需詳細資訊，請參閱 [自訂和擴充內容片段](https://experienceleague.adobe.com/docs/experience-manager-64/assets/fragments/content-fragments-delete.html). NPR-25793：CQ-4248750 的 Hotfix
* 新增為內容片段加上注釋的功能。 如需詳細資訊，請參閱 [變體製作片段](https://experienceleague.adobe.com/docs/experience-manager-64/assets/fragments/content-fragments-variations.html#annotating-a-content-fragment). NPR-25188：CQ-4235336 的 Hotfix
* 版本設定：並排比較內容片段。 如需詳細資訊，請參閱 [管理內容片段](https://experienceleague.adobe.com/docs/experience-manager-64/assets/fragments/content-fragments-managing.html#comparing-fragment-versions). NPR-25187：CQ-4237412 的 Hotfix
* 影像編輯器增強功能已支援至AEM 6.4.2.0。如需詳細資訊，請參閱 [影像編輯器](https://experienceleague.adobe.com/docs/experience-manager-64/developing/components/image-editor.html). NPR-24467

**包含的OSGI套件組合和內容套件**

AEM 6.4.2.0 中包含的 OSGi 套件組合清單

[取得檔案](assets/6.4.2.0_bundle-list.txt)

AEM 6.4.2.0 中包含的內容套件清單

[取得檔案](assets/6_4_2_0content-package-list.txt)

#### AEM 6.4.1.0 {#experience-manager-6410}

AEM 6.4.1.0為重要更新，包含2018年4月全面發行之AEM 6.4的效能、穩定性、安全性和重要客戶修正及增強功能。

AEM 6.4.1.0可安裝在AEM 6.4 GA上。 Service Pack的部分重點為：

* 內建存放庫 (Apache Jackrabbit Oak) 更新至 1.8.3 版。
* 推出增強智慧標籤。
* 設計選擇器、標籤選擇器中的修正（將源VM和目標VM更改為自動）
* 新增對 typeHint 的支援，可將值儲存為字串。
* 新增在郵件服務中支援SMTP over TLS。
* DMS7中HTTP轉寄站的Proxy處理修正。
* 更新至/etc/clientlibs/social/thirdparty/handlebars/source/handlebars.js 1.3版。
* DMHybrid選擇退出和選擇加入套件中的修正。
* 智慧型裁切的修正。
* 將OOTB配置值遷移到新位置（從/etc到/conf）。
* 新增色彩設定檔至傳送伺服器上的客戶設定。
* 從/etc遷移映像伺服器設定(&amp;gt);/conf.
* 新增要翻譯的來源內容片段。
* 為Print和PrintDialog新增ARIA支援。
* 新增電子郵件驗證ARIA支援。
* platform.clientlibs修正的主動式反向移植。
* 當沒有輸入至明確dataType時，防止自動執行指令碼（解析CVE-2015-9251）。

**資產**

* 重新開啟資產屬性頁面時，階層式下拉式清單值顯示空白。 NPR-23042：CQ-4238761 的 Hotfix
* 非管理員使用者無法使用mylinkshare頁面上的共用連結和頁面連結NPR-23044:CQ-4239004的Hotfix
* 為了防止6.4.0中的DAM資產更新工作流程出現Null指標例外狀況。NPR-24134:CQ-4244972的Hotfix
* 已發佈的WCM頁面顯示熱點的預留位置圖示，遺失OOTB檢視器有403錯誤的CSS檔案。 NPR-23041：CQ-4233716 的 Hotfix
* （詳細資訊檢視）「下一/上一頁導覽」功能會在「動態轉譯」預覽區域中保留DIV覆蓋，以封鎖檢視器的存取。 NPR-23043：CQ-4238499 的 Hotfix
* CMYK影像格式副本的飽和度不正確。 NPR-23048：CQ-4235470 的 Hotfix
* 由Scene7ListInfoProvider提取XMP中繼資料需要大量資源。 NPR-23754
* (dam-delivery)HTTP轉送器不遵守HTTP代理設定。 NPR-24002：CQ-4244140 的 Hotfix

**網站**

* 移動時重新命名頁面時，頁面移動成功，但重新命名功能無法運作。 NPR-22923：CQ-4235907 的 Hotfix
* 發佈指向 Adobe Campaigns 中匯入工具頁面的 Live Copy 頁面時發生錯誤。NPR-23053：CQ-4237164 的 Hotfix
* 傳統UI中的移動/重新命名失敗，錯誤為「移動頁面時發生錯誤」，且未重新命名。 NPR-23051：CQ-4235907 的 Hotfix
* 將內容從「欄」檢視切換為「清單」檢視時，會呈現空白頁面，並針對設定OffTime且OnTime為空白的頁面觸發「Null指標例外狀況」。 NPR-22968、NPR-23052：CQ-4238940 的 Hotfix

**商務**

* 修正失敗的核心霍布斯測試案例（CQ/商務模組）。 CQ-4253494 的 Hotfix

**漏洞**

* Salesforce 整合容易遭受伺服器端請求偽造 (SSRF) 攻擊。NPR-24289：CQ-4245277 的 Hotfix
* ReportingServicesProxyServlet中的伺服器端請求偽造(SSRF)和跨網站指令碼(XSS)。 NPR-24657：CQ-4246880 的 Hotfix
* 跨網站指令碼(XSS):反映在商務createcatalogwizard.html/content中。 NPR-24642：CQ-4237017 的 Hotfix
* 管理員 UI 專案連結中有跨網站指令碼 (XSS)。NPR-23272：CQ-4241795 的 Hotfix

**WCM - Foundation 元件**

* 開啟設計選擇器會導致Null指標異常。 NPR-23047：CQ-4238736 的 Hotfix

**使用者介面**

* (Coral3 Datepicker)新增對typeHint的支援，將值儲存為「String」。 NPR-23398：Granite-21194 的 Hotfix
* 國際化翻譯在語言層級無法運作。 NPR-22967、NPR-23046:Granite-21111的Hotfix
* granite.ui.commons修正的主動式反向移植。 NPR-23537
* 主動反向移植granite.ui.content修正。 NPR-23535
* 針對granite.ui.coralui修正的主動式反向移植。 NPR-23538
* 無法一次從組中刪除多個用戶。 NPR-23846
* (OMEGA)僅以英文報告「功能」。 NPR-23989：Granite-21231 的 Hotfix
* （設計匯入工具）匯入頁面不會匯入js、css。 NPR-25203：Granite-22236 的 Hotfix

**整合**

* com.day.cq.analytics.sitecatalyst 中無結尾標記的資源解析器。NPR-22340：CQ-4236515 的 Hotfix
* 長時間執行查詢期間 TargetContentImpl 導致 AEM 變得緩慢。NPR-22359：CQ-4236907 的 Hotfix
* 目標引擎 (mbox.js、at.js) 沒有使用損害 URL 而使用包含冒號的 URL，這可能因為某些部署而失敗。NPR-22434：CQ-4237854 的 Hotfix
* 在「目標」模式中，作者不需要取消繼承即可修改從 Blueprint 繼承的元件。NPR-22865：CQ-4237907 的 Hotfix
* （個人化）圖示在切換至「卡片」檢視時會變形。 NPR-23373、NPR-23374：CQ-4240018、CQ-4240019 的 Hotfix
* （個人化）對象控制台不顯示nt：資料夾類型。 NPR-23375：CQ-4242293 的 Hotfix
* 在發佈執行個體上將元件設為目標時，顯示目標元件之前的預設體驗時會出現閃爍畫面。NPR-23415：CQ-4242038 的 Hotfix
* （Adobe IMS主控台）刪除後， AccessTokenProvider OSGi服務設定會重新顯示。 NPR-23520：CQ-4208250 的 Hotfix
* 中繼資料夾結構出現設定參考複寫失敗。NPR-23485：CQ-4242751 的 Hotfix
* （個人化）由代理servlet封鎖的clientlib。 NPR-23521：CQ-4240995 的 Hotfix
* (Adobe IMS Console)在設定精靈中不會擷取已註冊的雲端解決方案。 NPR-23977：CQ-4244549 的 Hotfix
* 在沒有HTML擴充功能的頁面上載入目標內容時，會產生無限回圈。 NPR-23522：CQ-4223600 的 Hotfix
* 繼承的動態Tag Management組態參考頁面的啟動失敗。 NPR-23485：CQ-4242751 的 Hotfix

**平台**

* （傳統UI）（觸控式UI）嘗試透過資產搜尋結構中的標籤述詞來瀏覽標籤時，標籤選擇器未顯示，且擲回例外狀況。 NPR-23049：CQ-4239371 的 Hotfix
* （傳統UI）使用xtype=tags的元件會傳回null，且無法從標籤的eth清單中選取。 NPR-23050：CQ-4239937 的 Hotfix
* （品牌）選擇加入對話方塊提及Adobe Marketing Cloud而非Adobe Experience Cloud。 NPR-23210：CQ-4237799 的 Hotfix
* 從6.3升級至6.4後，篩選選項導致AEM變得緩慢。NPR-23260:CQ-4239847的Hotfix（待檢查）
* granite.omnisearch.core修正的主動式反向移植。 NPR-23536
* platform.clientlibs修正的主動式反向移植。 NPR-23569
* Cloud Service設定繼承在編輯其他頁面屬性時中斷。 NPR-23216：CQ-4239782 的 Hotfix
* 在Day CQ Mail Service中啟用STARTTLS支援。 NPR-23941：CQ-4240397 的 Hotfix

**專案**

* （內容片段）將英文資產新增至翻譯時，不會建立內嵌資產的語言副本。 CQ-4243477 的 Hotfix
* 在舊版模式中，msft設定下拉式清單顯示的是/libs（6.4設定）的設定，而非/etc（6.3設定）。 CQ-4243475 的 Hotfix
* 自動促銷和刪除翻譯專案中的翻譯啟動。 CQ-4243474 的 Hotfix
* 網站內的內容片段未翻譯。 CQ-4243482、CQ-4243483、CQ-4245687的Hotfix
* 開啟翻譯作業搜索篩選器時出現伺服器錯誤。 CQ-4236813 的 Hotfix
* 即使在/conf/we-retail內部存在tif後，憑證設定下拉式清單仍空白。 CQ-4236315 的 Hotfix
* 開啟項目KPI:建立更多專案時，效能會降低。 NPR-23840：CQ-4238392 的 Hotfix
* 工作流程啟動器無法接受 String 的 TypeHint 值。NPR-23863：CQ-4238356 的 Hotfix

**社群**

* Handlebars 1.0版中存在安全漏洞。 NPR-23636：CQ-4243055 的 Hotfix
* 標幟訊息的「大量允許」無法運作。 NPR-23867：CQ-4243962 的 Hotfix
* 論壇元件的排序按鈕上未顯示預設值。 NPR-23882：CQ-4243375 的 Hotfix
* 從社群網站傳送訊息至群組時發生問題。 NPR-23935

**工作流程**

* Day CQ 工作流程電子郵件通知服務會針對 WorkflowCompleted 和 WorkflowAborted 通知，對每個 Mongo 節點觸發一封電子郵件。NPR-22515：CQ-4238172 的 Hotfix
* 執行DAM更新資產工作流程時擲回NullPointerException。 NPR-23010：Granite-21096 的 Hotfix
* 「工作流進程」步驟不顯示/etc/workflow/scripts中的指令碼。 NPR-23263：Granite-20775 的 Hotfix
* 工作流動態參與者步驟不顯示/apps/workflow/scripts中的指令碼。 NPR-23464：Granite-21276 的 Hotfix
* 編輯一次後，無法編輯任何工作流程。 NPR-23742：CQ-4238526 的 Hotfix
* （傳統UI）編輯工作流程啟動器時，條件消失，導致工作流程無任何條件啟動。 NPR-23835：CQ-4239153 的 Hotfix
* 專案收件匣：切換至日曆檢視時，會顯示主要收件匣內容。 NPR-23947：CQ-4241236 的 Hotfix
* 需要公開套件中的裝載詳細資訊，讓HTL元件可在清單檢視中顯示值。 NPR-23948：CQ-4240953 的 Hotfix
* 無法在對話參與者步驟中儲存對話資料。 NPR-23965：CQ-4234123 的 Hotfix
* （觸控式UI）儲存工作流程模型時，「同步」按鈕會變更為「同步」，導致拼字錯誤。 CQ-4244843 的 Hotfix
* 專案收件匣：切換至日曆檢視時，會顯示主要收件匣內容。 CQ-4244436 的 Hotfix
* 無法在對話參與者步驟中選擇對話。 CQ-4244532 的 Hotfix
* granite.omnisearch.core修正的主動式反向移植。 NPR-23536
* 行動工作區應用程式6.4中，共用任務發生問題。 NPR-26383

**WCM — 翻譯**

* （參考面板）專案建立期間不會執行翻譯工作。 CQ-4245327 的 Hotfix

**WCM - MSM**

* (MSM)轉出效能改善。 CQ-4231488 的 Hotfix
* (MSM)事件接聽中實際發生的事件與事件處理之間的時間差。 CQ-4227766 的 Hotfix

**畫面**

* 螢幕頁面因screens-core-pkg:1.4.42的相依性遺失而失敗，並出現錯誤。CQ-4245918的Hotfix

**專案 — 翻譯**

* （內容片段）將英文資產新增至翻譯時，不會建立內嵌資產的語言副本。 CQ-4243477 的 Hotfix
* 在舊版模式中，msft設定下拉式清單顯示的是/libs（6.4設定）的設定，而非/etc（6.3設定）。 CQ-4243475 的 Hotfix
* 自動促銷和刪除翻譯專案中的翻譯啟動。 CQ-4243474 的 Hotfix
* 網站內的內容片段未翻譯。 CQ-4243482、CQ-4243483、CQ-4245687的Hotfix
* 開啟翻譯作業搜索篩選器時出現伺服器錯誤。 CQ-4236813 的 Hotfix
* 即使在/conf/we-retail內部存在tif後，憑證設定下拉式清單仍空白。 CQ-4236315 的 Hotfix

**內容片段管理**

* 刪除元件會填入包含堆疊追蹤的記錄。 CQ-4242315 的 Hotfix

**DAM - 一般**

* 關閉資產的詳細資訊檢視會傳回不正確的搜尋結果頁面。 CQ-4240960 的 Hotfix
* (Camera Raw)缺少影像調整選項。 CQ-4246121 的 Hotfix
* IndexOutOfBoundsException:OOTB資產修改報表。 CQ-4239744 的 Hotfix
* 從報表csv中移除信賴分數。 CQ-4241491 的 Hotfix
* 非「管理員」寄件者的連結共用電子郵件傳送中斷。 CQ-4240357 的 Hotfix
* 修復IT故障。 CQ-4249891 的 Hotfix

**DAM -Brand Portal**

* 資產屬性只會列出第一個索引標籤上的3個屬性，請讓所有索引標籤顯示為空白。 CQ-4242503 的 Hotfix
* 發佈的搜索表單中無法使用檔案類型和檔案大小謂詞。 CQ-4242026 的 Hotfix
* 目錄述詞中的搜尋應篩選掉/不應顯示在搜尋篩選器中。 CQ-4241386 的 Hotfix
* 取消發佈後，應存在來自的預設搜尋。 CQ-4241383、CQ-4241113
* 發佈至Brand Portal手勢無法用於影像預設集。 CQ-4241074 的 Hotfix
* 發佈至Brand Portal無法用於集合。 CQ-4241122、CQ-4246558

**DAM - DM 用戶端**

* 升級至6.4會移除先前建立的視訊編碼設定檔。 CQ-4244067 的 Hotfix
* Alt Text屬性在Dynamic Media元件中損毀。 CQ-4244081 的 Hotfix
* (DMS7)在AEM中編輯遠端集時不會在Scene7中覆寫。 CQ-4243430 的 Hotfix
* 6.4 SP1在DM混合型上的驗證。 CQ-4244623 的 Hotfix
* (DMS7-UA)按一下已發佈視訊資產的「內嵌」按鈕時，任何動作都不會發生。 「內嵌」對話方塊應會顯示為HTML代碼。 CQ-4245237 的 Hotfix
* （DM混合）已發佈視訊資產或混合媒體集的複製URL會獲得「`[object Object]`」。 CQ-4245236、CQ-4245451
* (DMHybrid)視訊的「詳細資料檢視」頁面不包含視訊資產顯示的預覽，並會將錯誤訊息輸出至主控台。 CQ-4244320 的 Hotfix
* we.retail內容的自動S7編碼。 CQ-4242253 的 Hotfix
* 預先升級視訊處理預設集無法新增視訊編碼預設集，也無法編輯現有的編碼預設集。 CQ-4240407 的 Hotfix
* 預先升級的影像預設集在轉譯頁面上會顯示為「取消發佈」，且不會產生URL。 CQ-4240406 的 Hotfix
* (CSS)會顯示資產，但使用的檢視器為預設檢視器，而非OOTB檢視器。 CQ-4239839 的 Hotfix
* 已停用清除步驟掛起手動執行和使用私有珊瑚類。 CQ-4239729 的 Hotfix
* 影像檢視器產生錯誤，且無法顯示正確的智慧型裁切。 CQ-4237564 的 Hotfix
* /etc下的舊預設集似乎損毀，且儲存時未移轉至/conf下的位置。 CQ-4237416 的 Hotfix
* OOB VideoViewer 5.8.x中的回歸 — 檢視器向右展開iframe，導致頁面版面中斷。 CQ-4235465 的 Hotfix
* (DMS7)智慧型裁切轉譯URL和內嵌按鈕對於尚未發佈的影像處於作用中狀態。 CQ-4233696 的 Hotfix
* (DMHybrid)還原先前的裁切/旋轉功能。 CQ-4239489 的 Hotfix
* 在卡片檢視中預覽視訊時，播放按鈕不會切換為暫停。 CQ-4238592 的 Hotfix
* 執行選擇加入升級時，YouTube設定不會從其舊位置移動/複製到新位置。 CQ-4238590 的 Hotfix
* DropTwo OOTB AVS視頻處理配置檔案列在「資料夾屬性」下，並且只有一個包含定義的編碼。 CQ-4238096 的 Hotfix
* (DMS7)智慧型裁切：詳細資訊視圖：URL按鈕標籤為Copy按鈕，以用於轉譯。 CQ-4237804 的 Hotfix
* 即使執行curl命令，檢視器預設集清單頁面仍保持空白。 CQ-4243246 的 Hotfix
* 已停用清除步驟掛起手動執行和使用私有珊瑚類。 CQ-4239729 的 Hotfix
* 視訊報表詳細資料頁面不會顯示視訊資產。 CQ-4246208 的 Hotfix

**DAM - DMServices**

* (DMS7)雲配置：更新至SP1後，無法與Scene7同步新內容。 CQ-4244437 的 Hotfix
* (DMHybrid)色彩設定檔和目錄設定未在debug_info=catalog呼叫中註冊。 CQ-4242346 的 Hotfix
* 將色彩設定檔新增至傳送伺服器上的客戶設定。 CQ-4241818、CQ-4241819
* (DMHybrid)在6.3和gt；之後6.4升級後，目錄設定會移至不正確的節點。 CQ-4239974、CQ-4239975
* (DMHybrid)pushviewerpresets指令碼不會建立修改目錄設定所需的節點。 CQ-4240076 的 Hotfix
* 使用「格式」下拉式選取項目並選取PNG或JPG格式時，下載的檔案會顯示為超飽和且較原始資產深。 CQ-4240073 的 Hotfix
* (DMS7)移除MIME類型對應：image_x-eps。 CQ-4240394 的 Hotfix
* (DMS7)挖空背景的上傳參數未傳遞ipsApiService.log，因此無法運作。 CQ-4240686 的 Hotfix
* 將6.3到6.4執行個體中建立的影像處理設定檔升級會中斷「裁切類型」屬性。 CQ-4237739 的 Hotfix
* (Dynamic Media)智慧型裁切資料夾外部的一般資產上傳失敗。 CQ-4237670 的 Hotfix
* 將「適用性視訊編碼」設定檔名稱的設定檔備援程式碼調整為「Adaptive_Video_Encoding」。 CQ-4237666 的 Hotfix
* EmbedXMP 資料一律對 Ptiff 產生程序設為「作用中」。CQ-4234498 的 Hotfix
* CMYK影像格式副本的飽和度不正確。 CQ-4235470 的 Hotfix
* 當復寫記錄將影像伺服器設定標示為成功時，不會將其複製到傳送。 CQ-4239480、CQ-4239046
* (DMS7)無法使用對雲端設定的舊/新參考來建立集合。 CQ-4238078 的 Hotfix
* Scene7工作流程步驟只會讀取名稱和說明中的Scene7，但不會釐清DAM更新工作流程中的工作流程步驟。 CQ-4237865 的 Hotfix

**DAM — 智慧標籤**

* 簡介 [增強智慧標籤](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/enhanced-smart-tags.html). NPR-21951

**Forms**

透過附加套件和發行版本隨附的其他修補安裝程式來提供 AEM Forms 修正。如需詳細資訊，請參閱 AEM Forms 發行版本。

AEM Forms 的關鍵重點為：

* AEM Forms簡介 [交易報告功能](https://experienceleague.adobe.com/docs/experience-manager-64/forms/transaction-reports/transaction-reports-overview.html) 追蹤並保留已提交的表單、已處理的檔案和已轉譯的檔案等交易記錄計數，以便在AEM Forms部署中執行。 它提供產品使用情況的深入分析，並協助商務使用者了解數位處理量。
* 啟用XML表單的PDF/UA支援。
* 為Clientlib新增allowProxy = true **aemfd.ccm.channel.contentpage**
* 更新程式碼，將進階標題搜尋設為包含而非等於。
* 更新至Continuous Integration Machine上的新版Node Package Manager(NPM)。

**Forms 附加元件套件**

**後端整合**

* 將null作為值提供給可選欄位時，會產生錯誤。 NPR-24397
* 元素的命名空間與全局命名空間不同時，WSDL調用失敗。 NPR-24281
* (FDM WSDL)獲取Dermis異常：屬性類型陣列中的例外清單資料。 NPR-24265
* (FDM WSDL)獲取Dermis異常：java.lang.exception:createSOAPParam:參數無效。 NPR-24264
* (FDM Client SDK)無法測試前置/後置處理程式和自訂提交動作。 CQ-4238469 的 Hotfix
* 修正Dermis中的Javadoc問題。 CQ-4244250 的 Hotfix
* 增強網站服務說明語言(WSDL)中的輸入。 CQ-4244133 的 Hotfix
* AEM 6.3和AEM 6.4中，WSDL的基本驗證測試會針對相同設定產生不同錯誤。CQ-4244132的Hotfix
* 請求在client-sdk和javadoc中包含ValueUtil。 CQ-4242803 的 Hotfix
* （FDM雲配置）無法從雲配置配置配置基於SOAP的身份驗證。 CQ-4238462 的 Hotfix
* Dermis — 在Javadoc中新增遺漏的套件。 CQ-4242815 的 Hotfix
* 要包含在Forms附加用戶端sdk中的WSDLInvokerParams。 NPR-23381：CQ-4240233 的 Hotfix

**調適型表單**

* 文檔(IC)格式副本應使用事務記錄服務記錄為事務。 CQ-4245333 的 Hotfix
* 執行UAT5時，驗證階段產生的pdf缺少項目。 CQ-4243184 的 Hotfix
* guideContext的深層復本測試案例。 CQ-4242924 的 Hotfix
* 在最新升級的伺服器上執行UAT3時缺少校樣類型欄位。 CQ-4243120 的 Hotfix
* 在升級的伺服器上，提交的表單缺少預升級伺服器上存在的「州/省/地區」和「國家/地區」值。 CQ-4241444 的 Hotfix
* （運算式編輯器）在表單提交期間導覽至驗證階段時發生錯誤。 CQ-4241384 的 Hotfix
* 在預升級和升級的伺服器上，已提交表單的驗證階段缺少值。 CQ-4241896 的 Hotfix
* 頁面底部的「結束並儲存」按鈕無法運作。 CQ-4240112 的 Hotfix
* 升級設定上缺少聯繫電話。 CQ-4239870 的 Hotfix
* 在 `ACTION TAKEN` 「爭議類型」頁簽中的「其他文檔」中有「保存」的其他欄位「證明類型」。 CQ-4239873 的 Hotfix
* verifyPdf階段發生「getDataAPI錯誤」錯誤。 CQ-4239865 的 Hotfix
* 製作和發佈例項的移轉記錄中發生錯誤。 CQ-4239365 的 Hotfix
* 製作和發佈例項的移轉記錄中發生錯誤。 CQ-4239635 的 Hotfix
* 還原序列化錯誤，例如「不允許對sun.util.calendar.ZoneInfo類別進行還原序列化」，錯誤記錄提交適用性表單後的錯誤。 CQ-4240419 的 Hotfix
* Mobile表單轉譯中未填入狀態欄位。 CQ-4240597 的 Hotfix
* 從反模式清單中移除範本中元件的參考用途。 CQ-4239217 的 Hotfix
* HTML5數值方塊設為「浮點數」或「小數」，可在不同的瀏覽器中提供不同的驗證結果。 NPR-23528：CQ-4244097 的 Hotfix
* （影像上傳）影像未在DOR預覽中顯示。 CQ-4243178 的 Hotfix
* 嘗試提交包含「電子郵件PDF」和「包含附件」的適用性表單時，JEE伺服器擲回錯誤。 CQ-4239894 的 Hotfix
* 在執行階段不會使用表格/面板繪製圖表。 CQ-4240010 的 Hotfix
* 適用性表單提交無法運作，且由於提交失敗，交易計數沒有變更。 CQ-4246125 的 Hotfix
* （影像選擇）記錄選項的文檔不可見。 CQ-4236976 的 Hotfix
* 範本編輯器UI不穩定。 CQ-4241497 的 Hotfix
* 使用側面板的「資產」索引標籤不會顯示AF，而使用AEM表單元件屬性對話方塊的「瀏覽」選項來顯示。 CQ-4236751 的 Hotfix
* 為表單轉換產生的工作流程ID應在產生的最適化表單中提供。 CQ-4240014 的 Hotfix
* 無法在直接升級時選擇模板以在站點中建立頁面：Livecycle至6.4伺服器。 CQ-4241300 的 Hotfix

**組合器服務**

* 組合器服務中的事務記錄。 CQ-4245018、CQ-4245017、CQ-4245016的Hotfix。
* 使用DDX完成PDF/轉換時，不會報告交易。 CQ-4246039 的 Hotfix

**Forms經理**

* FM CREATE按鈕清單按字母順序排序。 CQ-4242307 的 Hotfix

**表單入口網站**

* 儲存在升級前伺服器上的草稿在升級的伺服器上無法正確開啟。 CQ-4243303 的 Hotfix
* adobe-formsmanager-core-module的7.1版更新。 CQ-4245753 的 Hotfix
* 儲存在升級前伺服器上的草稿在升級的伺服器上無法正確開啟。 CQ-4243303 的 Hotfix
* 在草稿的新實例/同一實例中替換/添加/刪除附件時，附件方案將中斷。 CQ-4243165 的 Hotfix
* 從查詢資料庫中檢索的草稿的計數多於門戶中顯示的草稿的計數。 CQ-4241489 的 Hotfix
* 升級前伺服器上提交的Forms不存在於升級後伺服器上。 CQ-4241490 的 Hotfix
* 儘管提交訊息成功，但UI中呈現的表單在提交索引標籤中仍為未提交狀態。 CQ-4241487 的 Hotfix
* guideContext應透過深層複製欄位來形成，因為guideContext包含本身為物件的customPropertyMap。 CQ-4240126 的 Hotfix
* 嘗試保存表單時出錯。 CQ-4240763 的 Hotfix
* 儘管Forms入口網站草稿和提交設定中已提供資料庫設定，但已儲存和提交表單的項目仍會填入crx/de。 CQ-4240726 的 Hotfix
* (Search &amp; Lister)進階搜尋標題固定值應包含而非等於。 CQ-4245499 的 Hotfix

**行動 Forms**

* 日期欄位在行動Forms中重疊。 CQ-4242256 的 Hotfix
* Mobile Forms的表單提交應使用「交易記錄服務」記錄為交易。 CQ-4246166 的 Hotfix
* 表單提交應使用「交易記錄服務」記錄為交易記錄。 CQ-4246165 的 Hotfix

**AEM Forms 應用程式**

* （Windows應用程式）無法呈現表單。 CQ-4238005 的 Hotfix

**工作流程OSGI**

* 工作流分配任務中的事務記錄。 CQ-4244440 的 Hotfix
* （FDM步驟）在處理步驟和fdm步驟之間插入「分配任務」步驟時，無法使用工作流元資料的值。 CQ-4241472 的 Hotfix
* 在OSGI工作流程的Forms整合中，指派任務的委派無法運作。 NPR-23709：CQ-4243700 的 Hotfix
* （工作流模型編輯器）某些工作流模型無法透過傳統UI WF模型編輯器編輯。 CQ-4241151 的 Hotfix

**多通道文檔**

* 模板中的日期欄位與IC創作中的子表單重疊。 CQ-4240110 的 Hotfix
* 在IC Web頻道製作中，不得刪除標題或上下移動。 CQ-4243358 的 Hotfix
* （IC編輯器）表元件預設行設定為1。 CQ-4244848 的 Hotfix
* 目標區域即使被拖放或拖放內容後，仍可顯示。 CQ-4244534 的 Hotfix
* Web通道無法識別文本文檔片段中的頁簽空間。 CQ-4244481 的 Hotfix
* （打印通道）應使用事務記錄服務將文檔(IC)格式副本記錄為事務。 CQ-4245335 的 Hotfix
* （Web通道）應使用事務記錄服務將文檔(IC)格式副本記錄為事務。 CQ-4245334 的 Hotfix
* 「文檔容器搜索」或「資料模型樹」搜索必須與「資產」篩選器搜索統一。 CQ-4242305 的 Hotfix
* （檔案片段）縮排屬性會縮減文字中無法理解的單位數。 CQ-4241082、CQ-4240643
* （IC編輯器）列於「資產」標籤下之檔案片段表徵圖上的「編輯片段」圖示不易探索及理解。 CQ-4241047 的 Hotfix
* 允許匿名訪問IC匿名客戶端庫。 CQ-4245588 的 Hotfix
* （Web管道）在Web預覽中，資料不會解析於任何表格中，且會顯示為空白。 CQ-4244476 的 Hotfix
* 表格標題在自動產生時會在Web頻道中顯示為變數。 CQ-4244242 的 Hotfix
* （IC編輯器）IC中使用的文檔片段的內容應自動重新調整大小以適合目標區域的寬度。 CQ-4244094 的 Hotfix
* 中央頂部顯示的通道名稱必須與WEB/PRINT的IC標題一致。 CQ-4242498 的 Hotfix
* 文字編輯器資料物件面板應僅列出頂層實體，CQ-4244121的Hotfix
* 在編輯器中新增元件時，未指派預設名稱。 CQ-4244691 的 Hotfix
* 在所有Web通道元件中新增Colspan設定。 CQ-4244946 的 Hotfix
* 版面片段表格寬度屬性未在信函或客戶通訊列印管道中重設及遵循。 CQ-4241574 的 Hotfix

**通信管理**

* 編輯包含預留位置的文字資產後，字幕範本中移除了標題。 NPR-24196
* XDP檔案上傳後，若用作信函範本的版面，將無法預覽或編輯範本。 NPR-24143：CQ-4244407 的 Hotfix
* 預設情況下，在清單片段中選擇分配選擇。 CQ-4240097 的 Hotfix
* 條件編輯器 — 預設應啟用多個結果評估。 CQ-4240096 的 Hotfix
* 從「清單」中刪除時的影像仍會在預覽中顯示影像。 CQ-4239909 的 Hotfix
* 條件模組上的規則集會設為所有模組的「預設」。 CQ-4239878 的 Hotfix
* 資料字典建立失敗，出現「未知JCR例外狀況」錯誤。 CQ-4244122 的 Hotfix
* 6.3內容JavaDocs中的間隙。 CQ-4213586 的 Hotfix

**Forms - JEE 安裝程式**

**核心**

* (HTML工作區)名稱中帶有括弧之應用程式的追蹤詳細資料遺失。 NPR-23402

**PDFG 服務**

* PDFG服務中的事務記錄。 CQ-4244951、CQ-4244586
* 透過單一API呼叫選擇性地取消內嵌字型，以減少PDF。 NPR-23287
* AEM升級時出現PDFG設定更新問題。 CQ-4241176 的 Hotfix
* PDFUtility服務中的事務記錄。 CQ-4245014 的 Hotfix

**處理程序管理**

* (HTML 工作區) 程序起始點沒有依照字母順序排列。CQ-4239629 的 Hotfix
* (HTML工作區)首次開啟草稿時，準備提出兩次資料呼叫。 CQ-4243280 的 Hotfix
* (HTML工作區)關閉表單時會觸發準備資料處理。 CQ-4239456 的 Hotfix
* 在兩個任務之間遍歷時，工作空間將掛起。 CQ-4237125 的 Hotfix

**Workbench**

* 管理操作配置檔案當預設渲染進程配置設定為HTML時，準備資料進程失敗。 CQ-4244292 的 Hotfix

**Forms Designer**

* 為透過 Designer 和 Output Service 產生的 XML 表單新增 PDF/UA 支援。NPR-23022
* 從 Designer 另存為 PDF 時，在 Designer 中定義的內嵌超連結沒有受到標記，且沒有替代文字。NPR-23023

**包含 Feature Pack**

**資產**

* 新增「增強智慧標籤」的功能。 如需詳細資訊，請參閱 [增強智慧標籤](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/enhanced-smart-tags.html). NPR-21951：CQ-4234883 的 Hotfix
* 在InDesign中導入AEM Assets參考。 如需詳細資訊，請參閱 [AEM Assets參考InDesign](/help/assets/managing-linked-subassets.md). NPR-23386

**網站**

* （頁面編寫）影像編輯器增強功能。 如需詳細資訊，請參閱 [影像編輯器](https://experienceleague.adobe.com/docs/experience-manager-64/developing/components/image-editor.html). NPR-24267：CQ-4245502 的 Hotfix

**包含的 OSGI 套件組合和內容套件**

下列文字記錄 CFP 中包含的 OSGI 套件組合和內容套件清單。

AEM 6.4.1.0 中包含的 OSGi 套件組合清單

[取得檔案](assets/6_4_1_0_bundle-list.txt)

AEM 6.4.1.0 中包含的內容套件清單

[取得檔案](assets/6_4_1_0_content-package-list.txt)

### 安裝6.4.8.0 {#install}

#### 設定需求 {#setup-requirements}

<!--

>[!NOTE]
>
>For successful installation of AEM 6.4.6.0 on the instance, it is strongly recommended to upgrade the version of com.adobe.granite.oak.s3connector to 1.8.4 for the customers who are on the older version of s3 connector.
>The process of upgrading the com.adobe.granite.oak.s3connector is available at [https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html](https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html).
>Download the latest version of com.adobe.granite.oak.s3connector from: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

-->

>[!CAUTION]
>
>AEM 6.4安裝了Feature Pack的客戶。Adobe提供的選用Feature Pack依存於發行版本和Service Pack。 若您已安裝任何Feature Pack，請聯絡AEM客戶服務團隊，以驗證這些Feature Pack與此AEM 6.4適用的Service Pack的相容性。

* AEM 6.4.8.0需要AEM 6.4。如需詳細資訊，請參閱 [升級檔案](../sites-deploying/upgrade.md).
* Service Pack下載可在 [Software Distribution入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 下載。
* 在具有MongoDB和多個執行個體的部署上，使用套件管理器在其中一個製作執行個體上安裝AEM 6.4.8.0。
* 安裝Service Pack之前，請確定有AEM執行個體的快照或全新備份。
* 安裝前重新啟動執行個體。 雖然只有在執行個體仍處於更新模式時才需要這麼做（這是從舊版更新執行個體時的情況），但一般建議執行個體執行較長的時段。

>[!NOTE]
>
>Adobe不建議移除或解除安裝AEM 6.4.8.0套件。

### 透過封裝管理器安裝Service Pack {#install-the-service-pack-via-package-share}

執行下列步驟將Service Pack安裝在現有AEM 6.4執行個體上：

1. 從Software Distribution下載套件。

1. 在AEM中，登入套件管理器並新增下載的AEM 6.4.8.0套件。 選取上傳的套件，然後按一下 **[!UICONTROL 安裝]**.

>[!NOTE]
>
>**在安裝6.4.8.0期間，Package Manager UI的對話方塊有時會過早退出**
>
>因此，建議在存取執行個體之前，等待錯誤記錄穩定下來。 在確保安裝成功之前，用戶必須等待與卸載更新程式捆綁相關的特定日誌。 這通常會在Safari上發生，但可能會在任何瀏覽器上間歇性發生。

### 自動安裝 {#auto-installation}

有兩種方式可自動將AEM 6.4.8.0安裝至執行中的執行個體：

A.將套件放入……*/crx-quickstart/install* 資料夾。 套件便會自動安裝。

B.使用 [來自套件管理器的HTTP API](/help/sites-administering/package-manager.md)  — 請務必使用 `cmd=install&recursive=true`  — 以安裝巢狀套件。

>[!NOTE]
>
>AEM 6.4.8.0不支援安裝Bootstrap。

### 驗證安裝 {#validate-install}

1. 「產品資訊」頁面(*/system/console/ productinfo *)現在應在「已安裝產品」下顯示更新的版本字串「Adobe Experience Manager, 6.4.8.0版」。
1. 在 OSGI 控制台 (使用 Web 控制台：/system/console/bundles) 中，所有 OSGI 套件組合均為「作用中」或「片段」。
1. OSGI套件組合org.apache.jackrabbit.oak-core的版本為1.8.17或更新版本(使用Web主控台：/system/console/bundles)。

若要決定要透過此版本的AEM Sites和Assets執行，請參閱 [技術需求](../sites-deploying/technical-requirements.md).

>[!NOTE]
>成功安裝套件時，會顯示資訊性訊息，指出已成功安裝內容套件，例如 **&quot;已成功安裝AEM-6.4-Service-Pack-7內容包。&quot;**

### 更新Dynamic Media檢視器(5.10.1) {#update-dynamic-media-viewers}

<p id="Dynamic">AEM 6.4.8.0包含新版Dynamic Media檢視器(5.10.1)，可啟用在「影像預設集」頁面上檢查重複名稱。 建議Dynamic Media客戶執行下列命令，將方塊檢視器預設集開啟至最新狀態。

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

會將新的檢視器預設集複製到/conf位置。

### 安裝AEM Forms附加元件套件 {#install-aem-forms-add-on-package}

#### 安裝AEM Forms附加元件 {#installaemformsaddon}

>[!NOTE]
>
>如果您未使用AEM Forms，請略過。 AEM Forms中的修正是透過個別的附加套件提供。

>[!NOTE]
>
>AEM 6.4.8.0包含新版本 [AEM Forms相容性套件](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html). 如果您使用舊版AEM Forms相容性套件並更新至AEM 6.4.8.0，請在安裝Forms附加元件套件後安裝最新版AEM Forms相容性套件。

1. 確認您已安裝AEM Service Pack。
1. 下載列於的對應表單附加套件 [AEM Forms版本](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) 作業系統。
1. 依照 [安裝AEM Forms附加元件套件](https://experienceleague.adobe.com/docs/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package).

### 安裝AEM Forms JEE安裝程式 {#install-aem-forms-jee-installer}

>[!NOTE]
>
>如果您沒有在JEE上使用AEM Forms，請略過。 AEM Forms JEE 中的修正是透過單獨的安裝程式提供。

如需安裝AEM Forms JEE的累積安裝程式和部署後設定的相關資訊，請參閱 [AEM Forms JEE修補程式安裝程式0015](https://helpx.adobe.com/aem-forms/quick-fixes/6-4/jee-patch-0015.html).

#### NPR-21268 所需的配置設定 {#configuration-settings-required-for-npr}

如果您使用傳統（舊）UI並且已使用它建立元資料模板，請按照步驟運行JMX指令碼以保留它們 — 

1. 轉到/system/console/jmx。
1. 按一下「移轉中繼資料範本」。
1. 按一下「migrateMetadataTemplatesAtPath」，並提供要保留元資料模板的資料夾路徑。

#### NPR-24536 所需的配置設定 {#configuration-settings-required-for-npr-1}

預設情況下，使用者認領任務時，不會重新整理其他使用者的共用佇列計數。為此，我們引入了一項新屬性。請依照下列步驟操作，在您的 AEM 執行個體上設定此屬性：

1. 前往「管理員 UI -> 服務 -> 工作區 -> 全域管理」。
1. 匯出全域設定。
1. 在下載的XML檔案中，新增標籤 &lt;client_taskspollinginterval>10&lt;/client_taskspollinginterval> 其中，10是以秒為單位的範例值。 您可以視情況修改此值。
1. 儲存檔案。
1. 返回「管理員 UI -> 服務 -> 工作區 -> 全域管理」。
1. 在「匯入全域設定」區段中匯入該 xml 檔案。
1. 這時您可以登出系統並重新登入。
1. 系統會為工作區中的其他使用者開始重新整理共用佇列的計數。
1. 若要關閉輪詢，請將值變更為 0，然後再次匯入 XML 檔案。

### Uber Jar {#uber-jar}

適用於AEM 6.4.8.0的Uber Jar可於 [Adobe公用Maven存放庫](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.4.8/).

若要在 Maven 專案中使用 Uber Jar，請參閱[如何使用 Uber jar](../sites-developing/ht-projects-maven.md) 一文，並在您的專案 POM 中加入以下相依性：

```shell
<dependency>
      <code>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8</version>
      <classifier>apis</classifier>
      <scope>provided</scope>
</dependency>
```

### 已移除/已棄用的功能 {#removed-deprecated-features}

本節列出 AEM 6.4 已移除或棄用的特色和功能。

| 區域 | 功能 | 替代方案 | 版本 |
|---|---|---|---|
| 資產 | 管理子資產的標籤動作 | 無替換 | AEM 6.4.2.0 |
| Assets 與 Adobe Creative Cloud 整合 | AEM 6.2 引入了 [AEM 對 Creative Cloud 資料夾共用](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html)功能，作為讓 Creative 使用者存取 AEM 資產的方式。Creative Cloud 應用程式推出的新功能 Adobe Asset Link 提供了更優異的使用者體驗，以及更強大的存取功能，可直接從 Photoshop、InDesign 和 Illustrator 中存取 AEM 的資產。 Adobe 將不會再對資料夾共用功能提供近一步的增強項目。雖然AEM中包含此功能，但強烈建議客戶使用取代。 | Adobe資產連結或案頭應用程式。 如需更多資訊，請參閱 [AEM Creative Cloud 整合](/help/assets/aem-cc-integration-best-practices.md)文章。 | AEM 6.4.4.0 |

### 已知問題 {#known-issues}

* 安裝期間可能會顯示下列錯誤和警告：

   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` :等待登錄更改完成解除登錄的超時。
   * `com.adobe.granite.maintenance.impl.TaskScheduler` 在granite/operations/maintenance中未找到維護窗口
   * `com.adobe.cq.com.adobe.cq.ui.commons bundle com.adobe.cq.com.adobe.cq.ui.commons:1.2.28 (204)[com.adobe.cq.ui.wcm.commons.internal.servlets.rte.RTEFilterServletFactory(573)]`:unbindAndiment方法擲回例外狀況(java.lang.IllegalStateException:服務已註銷)。
這些錯誤不需要任何動作，因為它們不會影響您的AEM例項。

### 已解決的問題 {#resolved-issues}

**AEM 6.4.4.0**

* 在匯入/匯出中繼資料時未發現找到資源錯誤。 CQ-4253263
* 在6.4.2.0上方套用6.4.3.0後，無法編輯任何影像元件和頁面屬性。CQ-4260316和CQ-4260441要解決此問題：
   * 前往封裝管理員
   * 重新安裝套件「cq-ui-wcm-admin-content-1.0.1004.zip」
   * 重新編譯所有JSP `(http://<AEM HOST>:<AEM PORT/system/console/slingjsp)` 或重新啟動執行個體。

### 包含的 OSGi 套件組合和內容套件 {#osgi-bundles-and-content-packages-included}

下列文字檔案列出AEM 6.4.8.0中包含的OSGi套件組合和內容套件。

AEM 6.4.8.0 中包含的 OSGi 套件組合清單

[取得檔案](assets/6.4.8.0_osgi_bundles.txt)

AEM 6.4.8.0 中包含的內容套件清單

[取得檔案](assets/6.4.8.0_content_packages.txt)

### 實用資源 {#helpful-resources}

* [AEM 6.4 發行說明](../release-notes/release-notes.md)
* [AEM 產品頁面](https://www.adobe.com/solutions/web-experience-management.html)
* [AEM 6.4 檔案](https://helpx.adobe.com/tw/support/experience-manager/6-4.html)
* 訂閱 [Adobe 優先產品更新](https://www.adobe.com/tw/subscription/priority-product-update.html)

### 受限網站 {#restricted-sites-new}

這些網站僅供客戶使用。 如果您是Adobe，且需要存取權，請連絡您的客戶經理。

* [請前往licensing.adobe.com下載產品](https://licensing.adobe.com/).
* 產品更新、修補程式和包，以獲得 [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* [透過Admin Console提供客戶支援](https://adminconsole.adobe.com/). 如需詳細資訊，請參閱 [全新Adobe客戶支援體驗](https://experienceleague.adobe.com/docs/customer-one/using/home.html).

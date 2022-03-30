---
title: 《 AEM 6.4 Service Pack發行說明》
seo-title: AEM 6.4 Service Pack Release Notes
description: 特定於Adobe Experience Manager6.4 Service Pack的發行說明。
seo-description: Release notes specific to Adobe Experience Manager 6.4 Service Packs.
uuid: 49a710a8-7cd5-47de-9a96-7af7f3c00dfc
contentOwner: dekalra
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
discoiquuid: 93067308-e275-490f-8d78-ae79e046059c
exl-id: d0da9390-2167-47ee-82fd-8c81d8d68a3e
source-git-commit: 1537055fd88cbc3b01e4df7855a99f993f2052e4
workflow-type: tm+mt
source-wordcount: '21547'
ht-degree: 23%

---

# 《 AEM 6.4 Service Pack發行說明》 {#aem-service-pack-release-notes}

## 發行資訊 {#release-information}

| 產品 | **Adobe Experience Manager(AEM6.4)** |
|---|---|
| 版本 | 6.4.8.0 |
| 類型 | Service Pack版本 |
| 日期 | 2020 年 3 月 5 日 |
| 下載URL | AEM 6.4.8.0 [軟體分發](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/servicepack/aem-service-pkg-6.4.8.zip) |

## 包含在AEM6.4.8.0中 {#what-s-included-in-aem}

AEM  6.4.8.0是重要的更新，包括新功能、客戶要求的關鍵增強功能以及效能、穩定性、安全性改進，自AEM6.4中的正式發佈以來發佈 **2018年4月。**

它也是累積的，這意味6.4.8.0包括之前發AEM布的所有6.4個服務包。

此Service Pack版本的一些關鍵亮點是：

* 內建存放庫 (Apache Jackrabbit Oak) 更新至 1.8.20 版。

* WCM-RTE中的日文網站支援包文功能。

* 日語網站支援分詞和分詞處理。

* 增加了對使用BUNSETSU方法在適當位置中斷日語句和行的支援。

* 用於通信管理的CCR UI現在支援德語區域設定的小數值。

* 使用SOAP Web服務的表單資料模型整合現在支援元素上的選擇組或屬性。

* AEM Assets現在配置Brand Portal [!DNL Adobe I/O]。

* 已將ContextHub中捆綁的jQuery版本更新為3.2.1。

## 更改清單 {#list-of-changes}

### 網站 {#sites}

* 當AEM Sites頁面的URL包含冒號或百分比符號時，基礎瀏覽器停止響應，CPU週期顯示尖峰(NPR-32368、NPR-31917)。
* 當開啟AEM Sites頁面進行編輯並複製元件時，某些佔位符(NPR-32328)仍無法使用貼上操作。
* 激活工作流請求不包括引用的資產(NPR-32304)。
* 建立藍圖時，如果記錄數超過80，則只顯示前80條記錄。 藍圖顯示其餘記錄的空白行(NPR-32058)。
* 允許用戶保存內容片段而不在必填欄位中提供任何資訊(NPR-31988)。
* 自動導航不適用於在核心體驗片段元件(NPR-31921)中配置的路徑。
* 在RTE中更改表單元格的類型時，會出現以下錯誤：
   `Error: No common ancestor found, cannot continue` (NPR-31916)。
* 當內容在同一資料夾中移動時，頁面移動選項被禁用(NPR-31841)。
* 增加了對使用BUNSETSU方法劃分日文句子的支援，並在適當位置(NPR-31836)劃分了斷線。
* 在富格文本編輯器(RTE)中編輯超連結時，不會保存新選擇的路徑(NPR-31659)。
* 刪除多欄位元件並撤消刪除時，將恢復該元件，但不恢復資料(NPR-31617)。

### 資產 {#assets}

* 在與Dynamic Media Classic配置(NPR-32440)Experience Manager時，將資產從一個資料夾移動到另一個資料夾時，將在Dynamic Media Classic建立一個沒有名稱的資料夾。

* 在Dynamic MediaScene7模式(NPR-32316)上運行的Experience Manager中，PDF檔案的資產詳細資訊頁面不顯示操作按鈕。

* 無法刪除資產和視頻格式副本(NPR-32213)。

* 計畫激活的日曆表徵圖未顯示在「狀態」列（DAM資產清單的經典UI中）中，其資產的激活計畫在以後的日期和時間(NPR-32198)。

* 當資產與使用Other的多個資產相關時，資產關係被覆蓋(NPR-32196)。

* 當用戶在Dynamic Media客戶端(NPR-32178)中未對集編輯器進行任何更改時，「保存」按鈕不導入遠程集。

* PSD資產吞吐導致CPU激增和Experience Manager作者無響應實例(NPR-32165)。

* 在Experience ManagerDAM(NPR-32155)中上載大型ZIP檔案時出現記憶體不足異常。

* 版本歷史記錄URL顯示在「資產屬性」頁的「引用者」欄位下(NPR-31889)。

* 在「管理出版物」(Manage Publication)頁面上，從Brand Portal取消發佈已發佈資料夾的子資料夾失敗(NPR-31835)。

* Dynamic Media視頻編碼在Scene7雲配置放入私有資料夾時無法上載 `/conf` 而不是 `/conf/global` (NPR-31779)。

* 添加批注後，在Dynamic MediaScene7運行模式(NPR-31754)上運行的Experience Manager上，時間軸上看不到影像。

* 無法使用WinZip(NPR-31745)開啟從DAM下載的ZIP檔案。

### Integrations {#integrations-6480}

* 的 **公司** 和 **報告** 套件下拉菜單已隱藏一次 **報告源** 在Experience Manager雲服務中配置Adobe Analytics時選擇(NPR-31729)。

* 在製作與Adobe Campaign連結的通訊的語文副本時，不清理Adobe Campaign的財產，而當複製或貼上與Adobe Campaign連結的通訊時，則清理工作(NPR-32540)。

* ReportSuitesServlet 容易遭受 SSRF 攻擊 (NPR-32161)。

### Sling {#sling-6480}

* 資源觀測的非確定性跟蹤不工作(CQ-4286466)。

### 專案 {#projects-6480}

* 即使用戶有權在子資料夾中建立項目(NPR-31831)，用戶也看不到「建立」按鈕。

* 在「項目」(NPR-31829)中選擇「日曆」視圖後，在「卡視圖」、「清單視圖」和「日曆視圖」之間切換的功能不工作。

### 轉換 {#translation-6480}

* 為多語言建立翻譯項目只為某些語言而不是所有語言生成項目，並且日誌(NPR-32212)中出現錯誤（資源解析程式已關閉）。

### WCM-MSM {#wcm-msm-6480}

* 權限問題導致在藍圖中移動頁面時顯示錯誤(NPR-32610)。

### WCM頁面編輯器 {#wcm-page-editor-6480}

* 在嘗試將元件添加到具有特定URL格式的頁面(NPR-32368、NPR-31917)時，瀏覽器停止響應。

### WCM — 管理UI {#wcm-admin-ui-6480}

* 管理出版物在激活工作流請求(NPR-32304)中不包括引用的資產。

### 社群 {#communities}

* 無法更新組的組縮略圖影像(NPR-32603)。

### Brand Portal {#brand-portal}

* 雖然在後端刪除了AEM Assets中的取消發佈元資料架構(CQ-4286871)，但會填充錯誤消息。

### 基礎UI {#foundations-ui-6480}

* 添加到按鈕元件(NPR-32684)的URL中顯示的字元無效。

### Forms {#forms}

>[!NOTE]
>
>AEM Service Pack不包含針對AEM Forms的修復程式。 它們使用單獨的Forms附加包遞送。 此外，還會發佈一個累積安裝程式，其中包括對JEE上的AEM Forms的修復。 有關詳細資訊，請參見 [安裝AEM Forms載入項軟體包](#install-aem-forms-add-on-package) 和 [安裝AEM FormsJEE安裝程式](#install-aem-forms-jee-installer)。

* 設計器：如果啟用標籤選項，子格式邊框將消失在生成的PDF輸出(NPR-32546、NPR-32322)中。

* Designer：如果表格中有合併的儲存格，協助工具測試就無法輸出透過輸出服務從 XDP 表單轉換而來的 PDF 檔案 (NPR-32079)。

* 文檔安全性：受保護的PDF檔案無法離線開啟，DisableGlobalOfflineSynchronizationData選項設定為True(NPR-32080)。

* 文檔安全性：從ES4升級到6.3(NPR-32170)後開啟受保護的PDF檔案時出現的問題。

* 文檔服務：嘗試使用toPDFA轉換方法(NPR-32663)將PDF檔案轉換為PDF/A文檔時，將顯示錯誤消息。

* 文檔服務：對Reader檔案(NPR-32639)應用PDF擴展服務時顯示異常。

* 文檔服務：在將XDP檔案匯編和轉換為PDF檔案(NPR-31821)時顯示錯誤消息。

* 分析在「站點」頁面上提交或放棄表單時不顯示適當結果(NPR-31359)。

### 先前Service Pack中包含的修補程式和功能包 {#hotfixes-and-feature-packs-included-in-previous-service-packs}

#### AEM 6.4.7.0 {#experience-manager-6470}

AEM 6.4.7.0是重要的更新，包括效能、穩定性、安全性和關鍵客戶修復程式以及自AEM6.4 i的正式發佈以來發佈的增強功能 **2018年4月。**

它也是累積的，這意味著6.4.7.0包括之前AEM發佈的所有6.4 Service Pack。

6.4.7.0的一些關鍵亮點AEM是：

* 內建存放庫 (Apache Jackrabbit Oak) 更新至 1.8.17 版。
* 添加了對設定網站頁面版本的支援，同時刪除該頁面。
* 已在中為建立日期添加了可排序的新列 **DAM清單** 查看和查看資產搜索結果 **清單** (NPR-31311)。
* 基於 **名稱** 允許列在 **清單** 的子菜單。
* 重新處理和批處理上載的批處理大小和工作流步驟超時現在可以從Dynamic Media的UI中配置。
* 的 `pdfBrochure` 已在場景7雲配置中設定為false，以在IPS中保存記憶體。

##### 資產 {#assets-6470}

**產品增強**

* API包的導出版本 `package com.day.cq.dam.handler.standard.msoffice` 支援 `dam-handler` 捆綁包已升級到6.0.0(CQ-4279059)。
如果您正在使用包 `com.day.cq.dam.handler.standard.msoffice` 在自定義實施中，建議您 `dam-handler` 和最新的優步罐捆綁在一起。

* 已在DAM清單視圖中添加可排序的建立日期的新列，並在清單視圖中添加有關資產搜索結果的列(NPR-31311)。

* 在「清單」視圖(NPR-31299)中允許基於「名稱」列的資產排序。

**修復**

* 某些PDF文檔的元資料不會更新並保存到PDF修改其標題(NPR-31575)。

* 無法刪除檔案名中具有「+」符號的資產(NPR-30588)。

* DAM資料夾屬性不顯示已關閉用戶組(NPR-30555)中添加的用戶或組（由LDAP同步建立）。

* 未正確顯示電子郵件模板主題行中出現的特殊字元(NPR-30547)。

* 在Dynamic MediaScene 7運行模式(NPR-31631)中，將資產從一個資料夾移動到AEM另一個資料夾時，資產名稱將更改為小寫。

* 建立影像集（或媒體集）時，在場景7中將影像集的名稱更改為小寫(NPR-31576)，並使用DAM中的相應命名約定命名。

* Dynamic Media編碼視頻工作流無法為從場景7遷移到Dynamic Media — 場景7運行模式(NPR-31523)的視頻生成縮略圖。

* 在Dynamic Media — 場景7運行模式(NPR-31388)上運行時，使用篩選器搜索集時，會AEM發現內部伺服器錯誤。

* 編輯遠程影像集時，對於與Scene 7公司名稱(NPR-31347)相同的資料夾中的影像出現錯誤。

* 未發佈包含引用的資產(DM)(NPR-31179)。

* 針對 Dynamic Media 混合模式設定的到期 (用戶端快取的存留時間) 值沒有複製到 Dynamic Media 交付環境中 (NPR-31126)。

* 從Dynamic MediaAEM上傳 — Scene 7運行模式到Scene 7的上載時間太長，無法完成(NPR-30926)。

* 在發佈具有Dynamic Media元件的頁面時，從在Dynamic Media- Scene 7運行模式上運行的作者實例建立該元件後，將提示用戶發佈dmscene7配置(NPR-30880)。

* 在更改Dynamic Media- Scene 7(NPR-30745)的「移動後標題」和「移動後名稱」欄位中的值後，查看器嵌入代碼中「asset」參數的值保持不變。

* 觸摸UI搜索（通過Omnisearch完成）結果頁自動滾動並丟失用戶的滾動位置(NPR-31306)。

* DAM事件清除刪除最新(maxSavedActivities)事件資料並保存先前建立的資料(NPR-30870)。

* 在將操作移到目標資料夾後，資產標題和名稱更改不會永續，該資料夾在選擇時觸發無限滾動(NPR-30647)。

* 在應用從Adobe資產連結(CQ-4280534)訪問的AEM Assets的任何篩選器時，將從視圖中刪除集合。

* 無法從UI配置重新處理和批處理上載的批處理大小和工作流步驟超時，需要在CRXDE中設定，並且需要同步兩次工作流(CQ-4281254)。

* 批處理上載和簡單上載步驟的工作流步驟名稱在場景7中相同，這會導致混淆(CQ-4281176)。

* 如果資產缺少元資料節點(CQ-4281170)，則場景7中的重新處理工作流將停滯。

* BatchUpload步驟在重新處理工作流時對具有視頻資產的資料夾(CQ-4280630)不起作用。

* 發送到DM的PDF選項的extractKeywords在預設情況下設定為true(CQ-4280101)。

* 在包含非DM資產的資料夾(CQ-427955)上運行「場景7重新處理」工作流時，出現空點異常。

* 當場景7中AEM已存在具有重複名稱的資產時，中的資產更名無法與場景7同步(CQ-4276763)。

* 當具有「讀取」權限的用戶嘗試開啟該檔案時，通過電子郵件發送的用於資產下載的Zip檔案無法解壓縮(CQ-4277925)。

* PPT格式副本工作流無法生成上載的PPT檔案的格式副本，AEM因為6.4無法更新到com.adobe.granite.poi 2.0.28版(CQ-4279059)。

* PDF檔案不進行索引，內容不可搜索(CQ-4278916)。

##### 網站 {#sites-6470}

* 當使用「僅升級已修改的頁面」來升級啟動並完成「升級已修改的頁面」啟動時，僅顯示已修改的頁面被升級。 此外，當要升級的清單正確時，未修改的頁面仍顯示在清單的底部(NPR-31314)。

* 當AEM Sites頁面移到其他位置時，其屬性不會相應地更新以反映其新位置(NPR-31265)。

* 對於新藍圖，如果記錄數超過40，則只顯示前40條記錄。 藍圖顯示其餘記錄的空白行(NPR-31182)。

* 當LiveCopy數量較大時， LiveCopy概述需要很長時間才能呈現預覽(NPR-30945)。

* 已添加支援，以在刪除頁面時設定其版本。 如果已刪除頁面的版本控制被禁用，則AEM Sites無法恢復此類頁面(NPR-30891)。

* 當用戶在菜單的description屬性中添加日文或韓文字元時，菜單將顯示日文和韓文文本(NPR-31331)的扭曲字元。

* 當使用者聚焦於左方邊欄的欄位，並使用鍵盤快速鍵貼上內容時，貼上了頁面編輯器剪貼簿的內容，而非左方邊欄的欄位內容 (NPR-31169)。

* 使用者編輯內容片段時，系統復原了已刪除的內容片段變化 (NPR-31178)。

* 內容片段模型查詢效率低。 如果實例有大量頁面並導致錯誤(NPR-30666)，則速度很慢。

* 保存內容片段模型時，日期和時間欄位中的時間設定為00:00(NPR-30540)。

##### 整合 {#integrations-6470}

* 配置Adobe啟動時，庫URL(NPR-30700)中會預先包含正斜槓(/)。

* 發佈後ContextHub效能下降(NPR-30884)。

##### 吊帶 {#sling-6470}

* 將webconsole安全提供程式包版本更新為1.2.4，以從webconsolesecurityprovider(NPR-30885)中刪除launchpad啟動程式api的依賴項。

##### 平台 {#platform-6470}

* 未儲存 Jetty 型 HTTP 服務的緩衝區大小設定更新 (NPR-30925)。

* QueryBuilder現在支援xpath查詢(NPR-31322)中的orderby fn:name()。

* 已將Sling分佈式事件管理更新為1.1.4版，以改進群集環境中的日誌質量(NPR-29256)。

##### 基礎UI {#foundation-6470}

* 滾動到結果頁的末尾，並顯示大量搜索結果，導致瀏覽器崩潰(NPR-31332)。

* 當從搜索結果頁面的「卡」視圖切換到「清單」視圖時，在可滾動該頁面之前會出現延遲(NPR-31280)。

##### 橡樹 {#oak-6470}

* MS Office檔案(包含JPEG影像的.docx和.xlsx檔案副檔名)無法使用Tika分析器(NPR-31693)進行分析。

##### Livefyre {#livefyre-6470}

* 當使用DITA插件為合成AEM資源完成整合時，LiveFyre與6.4升級的整合會帶來空點異常。 但是，當手動添加元件(FYR-11066)時，整合會起作用。

##### 轉換 {#translation-6470}

* 升級啟動頁時，目標體驗片段的路徑未更新(NPR-30830)。

##### 社群 {#communities-6470}

* 在某些情況下，即使在通知設定中啟用了電子郵件消息傳遞，電子郵件功能也無法正常工作，系統在NotificationsActivityStreamProvider(NPR-31521)中引發異常。
* 無法建立新成員，空白螢幕將出現在作者實例中的「建立AEM成員」螢幕(NPR-30951)上。
* 用戶無法在Internet Explorer 11(NPR-30927)的部落格上發表評論。
* 受限組的管理員無法查看組卡，無法在作者實例(NPR-30810)中執行任何快速連結操作(編輯/發佈/刪AEM除組)。
* 在作者實例中建立新站點時，成員組/組AEM資訊不可見(NPR-28840)。

##### Forms {#forms-6470}

>[!NOTE]
>
>AEM Service Pack不包含針對AEM Forms的修復程式。 它們使用單獨的Forms附加包遞送。 此外，還會發佈一個累積安裝程式，其中包括對JEE上的AEM Forms的修復。 有關詳細資訊，請參見 [安裝AEM Forms載入項軟體包](#install-aem-forms-add-on-package) 和 [安裝AEM FormsJEE安裝程式](#install-aem-forms-jee-installer)。

**Forms 附加元件套件**

**調適型表單**

* 字串在本地化自適應表單時包含字典鍵(NPR-31109)。

* Forms中的複選框和下拉清單未通過輔助功能檢查(NPR-31282)。

**HTML5 Forms**

* 新增子表單的例項時，產生 XDP 表單的 HTML5 預覽後出現閃爍畫面 (NPR-30907)。

**OSGi的文檔服務**

* 運行多個同時線程以使用com.adobe.fd.assembler.service.AssemblerService.invoke()方法組裝表單，顯示錯誤消息(NPR-31164)。

* 匯編程式服務建立的臨時檔案不會自動刪除，AEM需要重新啟動(NPR-30846)。

* 將ReaderExtension Rights應用於PDF會導致錯誤消息(NPR-30930)。

**工作流程**

* OSGi工作流由於CPU利用率為100%(NPR-31234)而失敗。

**Forms - JEE 安裝程式**

**文件服務**

* 轉換PDF服務無法將PDF文檔轉換為PostScript並顯示錯誤消息(NPR-31267)。

* SOAP終結點配置在應用修補程式以將HTML修復到PDF故障後重置(NPR-31309)。

**PDFG 服務**

* 無法上載使用管理員UI下載的Adobe PDF設定檔案(NPR-31273)。

#### AEM 6.4.6.0 {#experience-manager-6460}

AEM 6.4.6.0是重要的更新，包括效能、穩定性、安全性和關鍵客戶修復程式以及自AEM6.4 i的正式發佈以來發佈的增強功能 **2018年4月。**

它也是累積的，這意味著6.4.6.0包括之前AEM發佈的所有6.4 Service Pack。

6.4.6.0的一些關鍵亮點AEM是：

* 內建存放庫 (Apache Jackrabbit Oak) 更新至 1.8.15 版。
* 在基礎API中添加了對跟蹤事件中動態UI狀態的跟蹤支援。
* 為影像核心元件添加了格式副本支援。

**資產**

* 具有空間和 `&` 名稱中的字元顯示某些資產的空白灰色卡。 NPR-29934：CQ-4270187 的 Hotfix
* 為建立MP4資產時，DAM工作流崩潰AEM。 NPR-30031：CQ-4271352 的 Hotfix
* Adobe 智慧標記透過 Datapower 連線的問題。NPR-30026：CQ-4269457 的 Hotfix
* 使用OmniSearch找不到PDF。 NPR-30046：GRANITE-26290 的 Hotfix
* ACP API生成的URL和資料夾元資料中的資產路徑不是URL編碼。  GRANITE-26198:CQ-4271814修補程式
* 由於未定義負載，「建立審閱」任務功能無效。 NPR-30469:修補程式CQ-4274263
* 在資產選取器上執行OmniSearch後，將視圖從卡視圖切換到清單視圖（反之亦然）的功能消失。 NPR-29852：CQ-4269369 的 Hotfix
* （觸摸UI）在管理發布嚮導期間，在添加頁面後，資產會添加到複製隊列，因此，某些資產會在幾秒鐘後出現。 NPR-29985：CQ-4270724 的 Hotfix
* 按相關性排序搜索查詢將返回InDesign文檔和InDesign模板。 CQ-4273864 的 Hotfix
* 如果用戶具有大寫電子郵件ID，則用戶無法簽入以前已簽出的資產。 CQ-4276575 的 Hotfix
* 配置Dynamic MediaCloud Services `DMHybrid` 模式導致在Analytics中建立的多個空報表套件中沒有儲存報告套件ID,AEM從而導致報告套件重複。 CQ-4276855 的 Hotfix
* 在「托管標籤」頁中升級時不顯示警告對話框。 CQ-4252851 的 Hotfix
* 使用旋轉傳送器管理標籤時，導航按鈕不起作用。 CQ-4275499 的 Hotfix
* 批量移動資產功能被中斷，導致資產不會移動。 CQ-4272987 的 Hotfix

**網站**

* `pageinfo.json` 請求速度極慢，載入時間過長。 NPR-29709：CQ-4269560 的 Hotfix
* `onTime` 或 `offTime` 如果伺服器重新啟動，則不會重新調用保存在AEM資產上的元資料屬性。 NPR-30413：CQ-4272784 的 Hotfix
* 由於ConfigPostProcessor類的行為不正確，掛起父頁會刪除cq:子頁中的LiveRelationship混合類型。 NPR-30536、NPR-30510：CQ-4254113 的 Hotfix
* 在「市場活動編輯」頁面的「啟動」工作流對話框上的跨站點指令碼(XSS)。 NPR-29747：CQ-4271067 的 Hotfix
* （經典UI）「工作流鎖定」階段將禁用工作流頁籤，直到解除鎖定。 NPR-30356：CQ-4237557 的 Hotfix
* (IE11)在Rich Text Editor元件中貼上HTML內容時，如果預設的PasteMode =純文字檔案，則HTML將貼上格式，因此，defaultPasteMode無效。 NPR-30045：GRANITE-26094 的 Hotfix
* （經典UI）重新載入站點管理頁後，「新建」菜單中的所有下拉項都被禁用。 NPR-29980：CQ-4272044 的 Hotfix
* 無法將樣式添加到文本或編輯內容上創作的任何現有樣式。 NPR-29712：CQ-4266249 的 Hotfix
* （經典UI）沒有dc的資產：在路徑欄位對話框瀏覽器中列出標題值，但沒有標題。 NPR-30166:CQ-88858的備份請求
* cq :即使添加parsys元件後，偵聽器也不能使用嵌套元件。 NPR-30422：CQ-4274863 的 Hotfix
* AEM 和 Campaign 整合期間出現 ContextHub 錯誤。NPR-30625：CQ-4250790 的 Hotfix
* 系統將 resourceType 請求參數的值複製到 HTML 標記屬性 (以雙引號包圍) 的值中。NPR-29832：CQ-4255365 的 Hotfix
* 將元件從一個頁面複製並貼上到另一個頁面後，需要刷新頁面。 NPR-29982：CQ-4256019 的 Hotfix
* 不支援從頁面別名中發佈/取消發佈，因此應刪除。 NPR-30062：CQ-4271249 的 Hotfix
* ExperienceFragmentsReplicationListener中未關閉的ResourceResolver警告導致隨時間推移的穩定性問題，強制重新啟AEM動實例。 NPR-30416：CQ-4257521 的 Hotfix
* 移動在150多頁中引用的體驗片段不會在引用它們的頁中修改fragmentPath。 NPR-30556：CQ-4274900 的 Hotfix
* 開啟包含字元元的內容片段時出現分析錯誤(`$`)和左大括弧(`{`)一個接一個。 CQ-4270266 的 Hotfix
* 嘗試在時間軸中顯示體驗片段的版本時，VersionPreviewServlet在NullPointerException中失敗。 NPR-30074：CQ-4271881 的 Hotfix
* 無法通過簽入功能鎖定內容片段。 NPR-29923：CQ-4258785 的 Hotfix
* SAML驗證處理程式中的簽名驗證失敗。 NPR-30379:GRANITE-26567的後台請求

**複寫**

* JCR會話/資源解析器在OAuth實施期間在每次複製到MAC/Brand Portal時都被洩漏。 NPR-30000：Granite-26196 的 Hotfix

**Sling**

* 使用重疊和之前順序受影響的子級順序導致IndexOutOfBoundException。 NPR-30408:Sling-8296和Sling-7375的修補程式
* 保存InactiveBundlesHealthCheck配置後，InactiveBundlesHealthCheck正在讀取MissingPackagesHealthCheck配置。 NPR-30084：CQ-4272644 的 Hotfix

**商務**

* 無法從站點控制台運行目錄藍圖。 NPR-29829：CQ-4271461 的 Hotfix
* 產品中使用的資產不會在資產的「引用」部分顯示對產品的任何引用，如果資產被移動，則資產路徑將不會更新。 NPR-30542：CQ-4270247 的 Hotfix

**平台**

* 默AEM認郵件發送者無法通過TLS v1.2將郵件發送到遠程SMTP伺服器。NPR-30476:GRANITE-26605修補程式

**社群**

* 在作者上刪除的組與所有發佈者不同步。 NPR-29987：CQ-4268738 的 Hotfix
* 從「社區管理員」欄位中刪除的用戶與「成員資格」組不同步。 NPR-30389：CQ-4274339 的 Hotfix
* 管理員組的用戶部分沒有組的快速連結。 NPR-30546：CQ-4275579 的 Hotfix
* 更新任何新建立和現有的社區組將覆蓋jcr上的屬性：內容節點，並將其名稱更改為首頁的標題。 NPR-30109：CQ-4273719 的 Hotfix
* 當社區設定為與資料庫儲存資源提供程式(DSRP)協作時，通過位置和地址快速搜索和搜索將無法工作。 NPR-26737：CQ-4258493 的 Hotfix

**轉換**

* 自動執行翻譯無效。 NPR-30499：CQ-4276288 的 Hotfix
* 用戶能夠在限制為只讀的內容路徑上建立語言副本。 NPR-29937：CQ-4270708 的 Hotfix
* 翻譯問題 - 使用機器翻譯時只翻譯了幾個元件。NPR-30079：CQ-4273764 的 Hotfix

**整合**

* 在發佈實例重新啟動之前，無法正確顯示自定義內容。 NPR-30421：CQ-4273706 的 Hotfix

**專案**

* 大壩：folderThumbnailPaths值即使在刪除資料夾中的資產後也不會刷新並顯示舊的縮略圖。 NPR-30424：CQ-4273667 的 Hotfix

**UI控制台**

* 「站點」頁屬性的「縮略圖」頁籤上的跨站點指令碼(XSS)。 NPR-30048：Granite-26200 的 Hotfix

**UI-Foundation**

* 在基礎API中添加了對跟蹤事件中動態UI狀態的跟蹤支援。 NPR-30742、GRANITE-26322:GRANITE-26036修補程式

**Forms**

>[!NOTE]
>
>AEM Service Pack不包含針對AEM Forms的修復程式。 它們使用單獨的Forms附加包遞送。 此外，還會發佈一個累積安裝程式，其中包括對JEE上的AEM Forms的修復。 有關詳細資訊，請參見 [安裝AEM Forms載入項軟體包](#install-aem-forms-add-on-package) 和 [安裝AEM FormsJEE安裝程式](#install-aem-forms-jee-installer)。

**Forms 附加元件套件**

**調適型表單**

* 從發佈伺服器讀取空.css檔案需要更長的時間，從而導致效能問題。 NPR-30558：CQ-4274399 的 Hotfix
* 發佈後修改的Forms在發佈網站時不會再次發佈。 NPR-30411：CQ-4236566 的 Hotfix

**Forms - 後端整合**

* 使用Web服務定義語言(WSDL)建立表單資料模型時引發錯誤。 NPR-30388：CQ-4272921 的 Hotfix

**Forms — 通信管理**

* 在代理UI中編碼小於(&lt;)、大於(>)和和符(&amp;)等特殊字元。 NPR-30410：CQ-4273887 的 Hotfix
* 觸發包含資料字典值的文本片段時，代理UI將無響應。 NPR-30098、NPR-30083：CQ-4272204 的 Hotfix
* 建立對應UI(CCR UI)時斷時續失敗，錯誤變數（對象對象）。 NPR-29983：CQ-4273874 的 Hotfix
* 當文檔片段的說明包含屬性中的小於(&lt;)、大於(>)和和符(&amp;)等特殊字元時，字母草稿重新載入將失敗，但例外。 NPR-29930：CQ-4252762 的 Hotfix

**HTML5Forms**

* 以瀏覽模式使用 NonVisual Desktop Access 來讀取 HTML5 Forms時，Chrome 瀏覽器在表單設計中的每個可縮放向量圖形 (SVG) 之前讀到「graphic」。NPR-30450：CQ-4274732 的 Hotfix

**Forms - JEE 安裝程式**

**Forms — 基金會**

* 通過從表單工作台調用Web服務來添加或編AEM輯Web服務連接會引發錯誤：ClassNotFoundException org.apache.axis.message.SOAPBodyElement。 NPR-30116：CQ-4273217 的 Hotfix

**Forms - 文件服務**

* PDF/Acrobat印前檢查中缺少標籤錯誤。 NPR-30594：CQ-4276032 的 Hotfix
* PDF中的單字元資料綁定導致Reader擴展失敗，並出現錯誤&quot;java.lang.StringIndexOutOfBoundsException:字串索引超出範圍：1」。 NPR-30128：CQ-4273878 的 Hotfix
* 對 HTML 轉 PDF 服務執行負載測試時，發生錯誤而失敗，且檔案類型設定從 AEM 表單伺服器中移除。NPR-30085：CQ-4272631 的 Hotfix
* 使用Adobe Acrobat9.1（XFA 3.0版）拼合PDF不會保留PDF形式狀態：窗體上的不可見元素將重新設定為可見狀態。 NPR-29978：CQ-4270888 的 Hotfix

**Forms - 文件安全性**

* 應用帶時間戳的簽名失敗，出現錯誤：ALC-DSC-003-000:com.adobe.idp.dsc.DSCInvisiationException:調用錯誤。 NPR-30696、NPR-30537：CQ-4273778 的 Hotfix
* Configuration Manager不為本地化表列插入日文字串。 NPR-30496：CQ-4274868 的 Hotfix

**PDFG 服務**

* 嘗試在Windows Server 2016上將Word文檔轉換為PDF時出現連接錯誤。 NPR-30597：CQ-4275652 的 Hotfix
* 嘗試使用HTML通過「phantomjs」庫PDF後端服務時，權限被拒絕異常。 NPR-30456：CQ-4258077 的 Hotfix
* JBoss Management Console未顯示HTML到PDF服務的maxReuseCount。 NPR-30303、NPR-30135：CQ-4273763 的 Hotfix

#### AEM 6.4.5.0 {#experience-manager-6450}

AEM 6.4.5.0是重要的更新，包括效能、穩定性、安全性和關鍵客戶修復程式以及自AEM6.4 i的正式發佈以來發佈的增強功能 **2018年4月。**

它也是累積的，這意味著6.4.5.0包括之前AEM發佈的所有6.4 Service Pack。

6.4.5.0的一些關鍵亮點AEM是：

* 內建存放庫 (Apache Jackrabbit Oak) 更新至 1.8.13 版。
* 在Brand Portal複製代理中添加套接字超時和連接超時。
* Omnisearch增強功能 — 將搜索結果的分頁限制提高到100頁。
* 已禁用 `AssetDownloadServlet` 預設情況下，在發佈實例AEM上OSGi元件。 有關詳細資訊，請參見 [從下載資AEM產](/help/assets/download-assets-from-aem.md)。
* 已為資產啟用多站點管理器支援。 有關詳細資訊，請參見 [使用MSM重新使用資產](/help/assets/reuse-assets-using-msm.md)。

**資產**

* 檔案名中帶有撇號的資產不同步到Dynamic Media。 NPR-29538：CQ-4270592 的 Hotfix
* 更新 DAM DMGateway 介面以提供 S3 多部分支援。NPR-29740：CQ-4226303 的 Hotfix
* 在Dynamic Media下載視頻的格式副本時，資產下載對話框顯示的檔案大小不正確。 NPR-29642：CQ-4246202 的 Hotfix
* Day CQ DAM Mime Type Service將文本應用於m3u8後，資產將變得不可用。 NPR-29276：CQ-4264052 的 Hotfix
* 如果移動/更名的任何資產是Sling資源集合的一部分，則資產引用調整無法保存會話。 NPR-29143:/CQ-4252605的修補程式
* 無法通過搜索元資料值來跟蹤或查找資產。 NPR-29141：CQ-4260215 的 Hotfix
* 使用搜索過濾器保存智慧收藏時，面板上的按一下操作不會保持焦點。 NPR-29000：CQ-4240323 的 Hotfix
* 移動資料夾可以建立包含混合大小寫或大寫名稱的資料夾。 NPR-28945：CQ-4265234 的 Hotfix
* 如果集合名稱具有空格，則在Omnisearch中顯示空結果。 NPR-29001：CQ-4236729 的 Hotfix
* 使用一些不受支援的特殊字元（如&amp;）更名檔案會建立無效資料夾。 NPR-29196：CQ-4265037 的 Hotfix
* DAM Extract Archive for zip檔案功能已斷開。 NPR-29187：CQ-4254421 的 Hotfix
* 元資料導入應允許在不註冊命名空間的情況下導入元資料。 NPR-29425、NPR-28132：CQ-4269445 的 Hotfix
* 保存元資料更改對於名稱包含引號字元的資產無效。 NPR-29395：CQ-4254305 的 Hotfix
* 如果檔案名包含空格，則無法移動DAM資產。 NPR-29270：CQ-4266403 的 Hotfix
* 無法下載使用Deflate64算法壓縮的ZIP檔案。 NPR-29225：CQ-4253995 的 Hotfix
* 開啟包含具有多個版本的資產的資料夾時，資產縮略圖顯示緩慢。 NPR-29833：CQ-4271629 的 Hotfix
* 如果在選擇集合後按了Enter鍵，則無法輸入突出顯示的集合。 NPR-29723：CQ-4261607 的 Hotfix
* 跨站點指令碼(XSS)攻擊通過受限警報窗口。 NPR-29671：CQ-4270133 的 Hotfix
* 對於沒有刪除權限的用戶，向資產添加關係失敗。 NPR-29640：CQ-4269196 的 Hotfix
* 在屬性頁中添加資產標題後，當用戶嘗試關閉該頁時，AEM將再次開啟屬性頁。 NPR-29628：CQ-4264929 的 Hotfix
* 在資產上建立大量關係會導致錯誤。 NPR-28779：CQ-4250708 的 Hotfix
* 在「Scene7連接」運行模式下，資產接收速度較慢。 NPR-28658：CQ-4263007 的 Hotfix
* 未捕獲的TypeError錯誤：無法讀取未定義的屬性「split」，當嘗試查看搜索結果時顯示。 NPR-28803：CQ-4248371 的 Hotfix
* 從Brand Portal到AEM的複製長期停滯。 NPR-28914：CQ-4254932 的 Hotfix
* 在DAM轉移資產，不會導致Scene7採取類似舉措。 NPR-28957：CQ-4264974 的 Hotfix
* 如果在中更新元資料欄位，則元資料更新不會傳遞給IPSAEM。 NPR-28961：CQ-4255393 的 Hotfix
* VersioningTimelineEventProvider應提供根版本和版本注釋。 GRANITE-26063修補程式
* 注入資料會導致在伺服器端執行代碼。 CQ-4270246 的 Hotfix
* 已為資產啟用多站點管理器支援。 CQ-4271453、CQ-4268621、CQ-4257491的修補程式
* 接AEM口應在時間線歷史記錄中顯示資產當前版本的附加條目，並顯示Adobe資產連結中的最新簽入注釋。 CQ-4262864 的 Hotfix
* 建立或編輯MixedMediaSet時不載入示例視頻。 CQ-4244889 的 Hotfix
* 禁用刪除一側內容的權AEM限會阻止用戶發佈到Brand Portal。 CQ-4270426 的 Hotfix
* 在升級到AEM6.4.3後，查詢限制與資產報表相關的問題。NPR-28588:CQ-4262022、CQ-4260697的修補程式
* 下載功能會透過 assetdownload servlet 運用 AEM Assets 讓匿名使用者下載所有資產。NPR-27315, CQ-4254732修補程式

**網站**

* JCR投訴標籤名稱應基於標籤標題自動填充。 NPR-28990：CQ-4199411 的 Hotfix
* 取消繼承按鈕在頁面屬性中添加的某些欄位上不可見。 NPR-29079：CQ-4265686 的 Hotfix
* 推廣預覽操作不應嘗試重新建立即時副本或在推廣頁面清單中顯示它。 NPR-29151：CQ-4266213 的 Hotfix
* （模板編輯器）結構模式下的樣式策略回歸。 NPR-28981：CQ-4264400 的 Hotfix
* 嵌套的即時副本在部署期間顯示重複的條目。 NPR-29300：CQ-4268664 的 Hotfix
* 發佈包含設計導入程式元件的即時副本失敗，無法檢索所選頁面的引用。 NPR-28944：CQ-4265014 的 Hotfix
* 搭配多欄位使用時，CoralUI 在元件層級儲存 fileReferenceParameter 而非多欄位層級。NPR-29536：CQ-4266129 的 Hotfix
* 取消設計導入程式上的繼承後，在發佈時不會複製設計引用。 NPR-29648、NPR-29721：CQ-4269270、CQ-4271087 的 Hotfix
* 富格文本編輯器中的路徑欄位將在根路徑中開啟，而與要搜索的指定路徑無關。 NPR-29483：CQ-4268997 的 Hotfix
* (IE11)複製RTE元件中的貼上HTML內容(defaultPasteMode = plaintext)，不將內容貼上為純文字檔案。 NPR-29432、NPR-29171:GRANITE-24941修補程式
* 富格文本編輯器拼寫檢查不再在其他語言中工作。 NPR-29506：CQ-4264990 的 Hotfix
* 「市場活動」頁面上的跨站點指令碼(XSS)。 NPR-29614：CQ-4269322 的 Hotfix
* 處於來源編輯模式時若從全螢幕最小化 RTF 編輯器，會導致內容遺失。NPR-29574：CQ-4260584 的 Hotfix
* （經典UI）當存在大量標籤時，不總能導航到最後一個頁籤。 NPR-29544：CQ-4264548 的 Hotfix
* （經典UI）Admin Console導航菜單消失，頁面未完全載入。 NPR-29571：CQ-4264585 的 Hotfix
* 已在執行個體上啟用縮製的情況下，將元件新增至 WCM 頁面時會產生錯誤警報。NPR-29396：CQ-4266196 的 Hotfix
* 父級中「樣式系統」節點的繼承問題。 NPR-29296：CQ-4266041 的 Hotfix
* 使用Timewarp還原的頁面應參考版本控制時的正確圖片。  NPR-29431：CQ-4262638 的 Hotfix
* 安裝最新的6.4.5快照版本後，編輯器上出現Javascript錯誤的空白頁。 NPR-29475：CQ-4266196 的 Hotfix
* 將元件添加到parsys時，設計元件清單屬性不受尊重，並會解析為具有相似parsys結構的不同模板節點名稱。 NPR-29509：CQ-4269044 的 Hotfix
* cq:dropTargets區域覆蓋整個元件，而不是影像大小，這使嵌入的元件難以進行目標定位。 NPR-29738：CQ-4268912 的 Hotfix
* 在使用映像就地編輯器後，映像元件不會調用&quot;afteredit&quot;偵聽器。 NPR-29616 CQ-4268065修補程式
* 設定向Facebook發送的社交帖子的問題。 NPR-29212：CQ-4266630 的 Hotfix
* 在為已修改的頁面升級啟動時，將考慮源分支和啟動分支中的修改。 NPR-29308：CQ-4266746 的 Hotfix
* 「內容片段」上呈現的縮略圖顯示「日期」和「時間」欄位的內部日曆表示法。 NPR-29531：CQ-4269362 的 Hotfix
* 無法將標籤批量添加到具有現有不同標籤的頁面。 NPR-28729：CQ-4262922 的 Hotfix
* 站點管理員中未顯示「計畫激活」表徵圖。 NPR-28725：CQ-4263917 的 Hotfix

**複寫**

* 複製代理元件中的敏感資訊洩漏漏洞。 NPR-29612、NPR-24951:GRANITE-25070修補程式
* 在cq/replication/components/agent元件的輸出中，不會轉義用戶提供的資料，從而導致儲存的跨站點指令碼(XSS)漏洞。 CQ-4266263 的 Hotfix

**體驗片段**

* 使用智慧影像時，無法將體驗片段匯出至目標。CQ-4269606 的 Hotfix

**社交 — 報告**

* 在AEM作者實例中不顯AEM示社區報告。 CQ-4266294 的 Hotfix

**平台**

* 安裝軟體包時在軟體包管理器中執行跨站點指令碼(XSS)。 NPR-29734、NPR-29713、NPR-29630:GRANITE-26161、GRANITE — 的修補程式
* 在CRXDE Lite中儲存和反映多個跨站點指令碼(XSS)。 NPR-29634：GRANITE-26049 的 Hotfix
* 包共用的登錄功能使用GET請求，而不是POST請求，導致密碼在網路頁籤下可見。 NPR-29631：GRANITE-26048 的 Hotfix

**Felix**

* 在系統控制台中觀察到跨站點指令碼(XSS)。 當滑鼠懸停在文本欄位上時，頁面將被載入並彈出。 NPR-29853、NPR-29633:GRANITE-26188、GRANITE-26050修補程式

**Granite**

* Apache Sling日誌記錄記錄器配置不篩選注入的指令碼。  NPR-29775：GRANITE-26051 的 Hotfix

**社群**

* 應從發佈實例中刪除在作者上刪除的組。 NPR-28933：CQ-4264645 的 Hotfix
* 應用密碼欄位應受到保護，而不應以純文字檔案顯示，以用於社交連接工具。 NPR-29728：CQ-4270480 的 Hotfix
* 訪問者和成員沒有版主權限，可以通過貼上URL來查看未批准/待定帖子。 NPR-29726：CQ-4271124、CQ-4271441 的 Hotfix
* 觀察到使用者登入 Community 時出現 40-50 秒的長回應時間。NPR-29678：CQ-4269444 的 Hotfix

**轉換**

* 在導航中沒有翻譯功能訪問權限的用戶不應能夠訪問其子頁。 NPR-29644：CQ-4269979 的 Hotfix
* 未支援用戶權限，因為嚮導允許在只讀位置建立翻譯副本。 NPR-29375：CQ-4265877 的 Hotfix

**UI - Foundation**

* 將搜索結果的分頁限制增加到卡視圖的100頁和清單視圖的200頁。 NPR-29332：GRANITE-24644 的 Hotfix
* 由於拖放標籤，收集頁上不顯示任何內容。 NPR-29267：GRANITE-24902 的 Hotfix
* 將分頁限制更改為100而不是40會觸發額外的延遲負載，而不需要分頁請求。 NPR-29246：GRANITE-25027 的 Hotfix
* 加密AEM後未填充花崗岩密碼欄位。 NPR-29245：GRANITE-24908 的 Hotfix

**整合**

* 嘗試編輯和保存啟動配置時顯示AEM異常消息。 NPR-29086：CQ-4266153 的 Hotfix
* BrightEdge憑據失敗，出現連接錯誤。  NPR-29167：CQ-4265872 的 Hotfix
* 應刪除Cloud Service配置中根級別中的「繼承自」複選框。 NPR-27856：CQ-4259676 的 Hotfix

**吊帶**

* 未從配置中讀取HTTP連接超時。 NPR-29264：SLING-7902 的 Hotfix
* JCR安裝程式寫回導致OSGi配置使用無效格式並阻止重新部署。 NPR-29027：CQ-4264694 的 Hotfix

**專案**

* 用戶無法完成項目工作流。 NPR-29621：CQ-4258791 的 Hotfix
* 「項目工作流」清單顯示40個工作流以外的空行。 NPR-28739：CQ-4264005 的 Hotfix
* 在Brand Portal中選擇「動態格式副本」選項可下載一個空的.zip檔案。 NPR-29420：CQ-4268826 的 Hotfix
* 將AEM Author /content/dam/mac資料夾中的資產發佈到Brand Portal無效。 NPR-29820：CQ-4271118 的 Hotfix
* 名稱中的標點會導致發佈按鈕出現問題。 NPR-29573：CQ-4269317 的 Hotfix
* 無法通過引用面板建立資產語言副本。 CQ-4269535 的 Hotfix

**工作流程**

* 從6.4.2升級到6.4.4會中斷對話參與者的日曆選取器欄位。 NPR-29727：CQ-4270423 的 Hotfix

**WCM — 管理員UI**

* 在Coral2實現中開啟權限頁籤不顯示按鈕。 CQ-4269419 的 Hotfix

**WCM - MSM**

* 刪除即時副本中的子節點應分離liveRelationship。 CQ-4270395 的 Hotfix
* 升級到AEM6.4.3後，Multi-Site Manager需要很長時間才能推出。 CQ-4271410 的 Hotfix

**漏洞**

* CSRF 保護架構對 AEM Foundation 表單無效。NPR-28612：GRANITE-22231 的 Hotfix

**WCM - 頁面編輯器**

* 使用無效的選擇器時出現反射型跨網站指令碼 (XSS)。CQ-4270397 的 Hotfix

**Forms**

表單AEM6.4.5.0的主要亮點是：

**Forms 附加元件套件**

**調適型表單**

* （觸摸UI）啟動工作流選項不會彈出用於配置的對話框。 NPR-29521：CQ-4269050 的 Hotfix

**Forms - 後端整合**

* 為MicrosoftDynamics內部整合支援Active Directory聯合身份驗證服務(ADFS)v3.0。 NPR-30003、NPR-29484：CQ-4270586 的 Hotfix
* 預填充服務因AEM Forms資料整合模組的週轉時間延長而失敗。 NPR-28997：CQ-4265988 的 Hotfix
* SOAP Webservice請求在AEM Forms內格式不正確。 NPR-29013：CQ-4265443 的 Hotfix
* 測試SOAP服務時，如果日期值不正確，則不顯示錯誤消息。 CQ-4265445 的 Hotfix

**Forms — 互動式通信和Forms — 通信管理**

* 建立對應UI(CCR UI)無法處理浮點數。  NPR-29210：CQ-4254201 的 Hotfix
* 在「建立對應UI(CCR UI)」上不可見在變數上設定的工具提示。 NPR-29739：CQ-4250533 的 Hotfix
* 無法從字母內的Omnisearch複製或貼上。 NPR-29808：CQ-4270783 的 Hotfix

**HTML5Forms**

* 在文本中添加空格時，文本欄位不允許填充到結尾。 NPR-28844：CQ-4260239 的 Hotfix

**Forms - JEE 安裝程式**

**Forms — 基金會**

* AEM FormsWorkbench中的Web服務元件無法調用Web服務，這需要雙向SSL驗證。 NPR-29485：CQ-4246794 的 Hotfix
* AEM FormsJEE配置管理器不能使用多個NIC卡。 NPR-29236：CQ-4268598 的 Hotfix
* 從AEMGemFire發生啟動錯誤：java.lang.IllegalStateException:一次只能建立一個AdminDistributedSystem連接。 NPR-29524：CQ-4266295 的 Hotfix
* NoClassDefFoundError，因為jar版本不匹配。 NPR-28834：NPR-28834 的 Hotfix

**Forms - 文件服務**

* 無效的PDF/A檔案報告為使用isPDFA操作的有效PDF/A。 NPR-29076：CQ-4261541 的 Hotfix
* PDF無法轉換為「表單」欄位的PDF/A-1b，但沒有外觀指令。 NPR-29534：CQ-4269618 的 Hotfix
* PDF/A從輸出服務生成的PDF轉換未通過Acrobat DC驗證。 NPR-29647：CQ-4270448 的 Hotfix
* Apache POI捆綁包失敗，但出現異常。 NPR-27861、NPR-28048：CQ-4245898、CQ-4244778 的 Hotfix

**Forms — 設計師**

* 已向使用設計器和輸出服務生成的XMLForms體系結構(XFA)表單添加PDF/UA支援。 NPR-23022

**Forms - 工作流程**

* 從工作區提交失敗，但帶有Umlaut字元。 NPR-29087：CQ-4263172 的 Hotfix

**包含 Feature Pack**

**資產**

* 已為資產啟用多站點管理器支援。 有關詳細資訊，請參見 [使用MSM重新使用資產](/help/assets/reuse-assets-using-msm.md)。 NPR-26450：CQ-4259922 的 Hotfix

**包含的 OSGI 套件組合和內容套件**

下列文字記錄 CFP 中包含的 OSGI 套件組合和內容套件清單。

AEM 6.4.5.0 中包含的 OSGi 套件組合清單

[取得檔案](assets/6.4.5.0_bundles.txt)

AEM 6.4.5.0 中包含的內容套件清單

[取得檔案](assets/6.4.5.0_OSGI.txt)

#### AEM 6.4.4.0 {#experience-manager-6440}

AEM 6.4.4.0是重要的更新，包括效能、穩定性、安全性和關鍵客戶修復程式以及自AEM6.4 i的正式發佈以來發佈的增強功能 **2018年4月。**

它也是累積的，這意味著6.4.4.0包括之前AEM發佈的所有6.4 Service Pack。

6.4.4.0的一些關鍵亮點AEM是：

* 內建存放庫 (Apache Jackrabbit Oak) 更新至 1.8.11 版。
* 增加了對快取服務版本的支援，以避免頻繁的服務版本HTTP請求。
* 添加了對刪除自動標籤的支援。
* 為目錄嚮導實現了無休止滾動。
* 支援根據社區站點限制權限的能力。
* Sling Granite內容運行狀況檢查的效能修復（快取、非同步執行、排除清單）。
* 已將元件選取器按鈕添加到「頁號」對話框。
* 添加了新屬性，以允許在欄位上進行工具提示定位。
* 多欄位內對ColorPicker的支援得到改進。
* 已添加一個複選框，以忽略內容片段客戶端清單中數字輸入多欄位的空值。
* 已啟用對Microsoft翻譯器文本API v3的支援。

**資產**

* ACP遷移和庫存整合AEM到6.4.4.0 NPR-27632
* 稍後發佈帶有子資料夾的空資產資料夾會使子資料夾消失。 NPR-27558：CQ-4254701 的 Hotfix
* 添加單個無命名空間的String\[\]屬性會導致寫回XMP不完整。 NPR-26805：CQ-4254142 的 Hotfix
* 柵格化輸入pdf後，生成的輸出缺少影像。 NPR-27929：CTG-4150481 的 Hotfix
* 「移動資產嚮導」顯示的已發佈頁面的引用頁數不正確。 NPR-27833：CQ-4258014 的 Hotfix
* AssetPicker僅搜索第一個標籤，以在篩選帶標籤的結果時篩選結果。 NPR-27778：CQ-4257705 的 Hotfix
* OOTBAEMPDF處理程式卡在具有外來字元的處理PDF上。 NPR-28778：CQ-4254234 的 Hotfix
* 當CSV檔案具有在單個列中用逗號分隔的值時，AEM CSV編輯器不會轉義逗號，並將其視為單獨的列。 NPR-28801：CQ-4261694 的 Hotfix
* 使用路徑瀏覽器選擇資料時，元資料架構編輯器出現問題。 NPR-28674：CQ-4263005 的 Hotfix
* 太多資產被處理到智慧內容服務，導致需要大量時間來完成定期標籤過程。 NPR-28640：CQ-4262661、CQ-4262644、CQ-4263234 的 Hotfix
* 案頭操作對來自的Omnisearch結果無效 `aem/start.html` 的子菜單。 NPR-27242：CQ-4248176 的 Hotfix
* 資產API不允許上載檔案> 2 GB，導致上載失敗。 NPR-27629：Granite-23590 的 Hotfix
* 元資料在第一次嘗試時不會保存在下載的資產中，以防實例上啟用Dynamic Media。 NPR-28233：CQ-4260759 的 Hotfix
* 服務解析程式未在SiteCatalyst配置中關閉。 NPR-28015：CQ-4259397 的 Hotfix
* 在DAM中移動資產不會導致在Scene7（p2p配置）上出現類似的移動。 NPR-28313：CQ-4261091 的 Hotfix

**網站**

* （經典UI）展示清單中顯示的即時拷貝只佔一小部分。 NPR-28598、NPR-28574：CQ-4263410 的 Hotfix
* 當cq:master為空或無效時，LiveRelationshipManagerImpl會引發異常。 NPR-28590：CQ-4263115 的 Hotfix
* 「請求刪除」工作流不能正確刪除頁面。 NPR-28668：CQ-4263195 的 Hotfix
* 關係狀態UI不顯示相關coral-datepicker欄位的正確年或時間戳值。 NPR-28666：CQ-4263661 的 Hotfix
* 適用於 6.4 的 SuggestionHandler 中出現跨網站指令碼 (XSS)。NPR-28693：CQ-4253821 的 Hotfix
* 從siteadmin中移動資料夾會導致記憶體不足，並AEM導致不可用。 NPR-28346：CQ-4261398 的 Hotfix
* MSM LiveCopy部署配置在更新後丟失。 NPR-28311：CQ-4258705 的 Hotfix
* 無法滾動到40個藍圖配置之外。 NPR-27640：CQ-4239166 的 Hotfix
* 使用SyntheticResource作為引用會引發空指針異常並阻止頁面移動。  NPR-27576：CQ-4258262 的 Hotfix
* PushOnModify在6.1到6.4升級實例的刪除上不起作用。 NPR-28108：CQ-4259833 的 Hotfix
* （經典UI）「取消繼承」按鈕缺失，元件可在即時複製頁上編輯。 NPR-28256：CQ-4260161 的 Hotfix
* OakState0001:部署上未解決的衝突。 NPR-27982：CQ-4259548 的 Hotfix
* 複製/貼上包含SyntheticResource引用的結構時，進程以錯誤500結束。 NPR-27709：CQ-4259179 的 Hotfix
* 激活負載時無法終止正在運行的工作流。 NPR-27672：CQ-4258520 的 Hotfix
* 展出顯示從6.1升級到6.4後的重複展出路徑。NPR-27845:CQ-4259487修補程式
* 在頁面縮略圖元件中整合dam assetpicker模式。 NPR-28131：CQ-108042 的 Hotfix
* （經典UI）無法開啟與標籤小部件的對話框。 NPR-28575：CQ-4262680 的 Hotfix
* 多欄位檔案上載不顯示放置區域。 NPR-28676：CQ-4263516 的 Hotfix
* 將元件從 AEM 6.0 移轉到 AEM 6.2 時，出現「無效的遞迴選擇器值」錯誤。NPR-28609：CQ-4241258 的 Hotfix
* 當插件的跨距高於文本區域時，對話框中的富格文本編輯器會閃爍，因此會阻止任何進一步的創作。 NPR-27579：CQ-4257440 的 Hotfix
* （經典UI）cq:action editantate不起作用。 NPR-28232：CQ-4257703 的 Hotfix
* 從頁面編輯器的標籤篩選器資產搜索面板中刪除標籤無法正確刷新清單。 NPR-27983：CQ-4245567 的 Hotfix
* 如果多欄位數值為空，按一下「保存」將導致無限的載入提示，而實際上不會完成。  NPR-28400、NPR-28393：CQ-4244058、CQ-4244349 的 Hotfix
* 僅具有讀取權限，用戶/組無法選擇XF，並且沒有查看XF及其頁屬性的選項。 NPR-28341：CQ-4260412 的 Hotfix
* 從目標接收的JSON資料包含許多轉義字元，導致應用程式頁中斷。 NPR-28318：CQ-4252043 的 Hotfix
* 安裝AEM6.4.3後無法編輯任何元件。NPR-28125:CQ-4261216修補程式
* 對於結構化內容片段，不會保留刪除標籤欄位的所有標籤。 NPR-28133：CQ-4247241 的 Hotfix
* 編輯內容片段「jcr:lastmodifiedby」和「jcr:lastmodified」屬性時，將更新值，而用戶不進行任何更改。 NPR-27847：CQ-4257138 的 Hotfix
* 內容片段版本化比較6.AEM4的差異改進。NPR-27764
* 如果在/content/experience-fragments上未定義cq:allowedTemplates，並且在「體驗碎片」模板上使用allowedPaths，則移動/複製「體驗碎片」時會引發錯誤。 NPR-27487：CQ-4257489 的 Hotfix
* 新用戶的刷新時將顯示「建立」按鈕。 NPR-27335：CQ-4255360 的 Hotfix
* 嘗試移動已發佈頁面時，「移動頁面」嚮導第一頁上顯示的「引用頁面」計數不正確。 NPR-28111：CQ-4259663 的 Hotfix
* （觸摸UI）參考導軌不顯示傳入連結。 NPR-28529：CQ-4262306 的 Hotfix
* 安裝6.4.3後無法編輯任何元件和頁面AEM屬性。NPR-27998:CQ-4261216、CQ-4260441的修補程式
* 將 ContextHub 遷移至 jquery 3。NPR-28397：GRANITE-19902 的 Hotfix

**商務**

* 如果資料夾中有20個以上的目錄，則無法選擇目錄。 NPR-27649：CQ-4258119 的 Hotfix
* 由於缺少header.referer，商業嚮導和屬性視圖已斷開。 CQ-4261122 的 Hotfix

**Campaign - 目標定位**

* com.day.cq.personalization.impl.TeaserResourceEventHandler進入無限循環並導致對發佈實例上的節點進行更新。 CQ-4263096 的 Hotfix

**複寫**

* 生成複製內容com.day.cq.replication.AccessDeniedException時出錯。 NPR-28314：CQ-4261401 的 Hotfix
* 在複製代理中將用戶代理ID設定為admin時會發生會話洩漏。 NPR-28220：CQ-4255517 的 Hotfix

**大壩 — Creative Cloud**

* 備份HTTP API以從AEM Assets內查找類似映像。 CQ-4254091 的 Hotfix
* 增強ACP API以允許將查詢結果限制到集合的成員。 CQ-4258708 的 Hotfix

**DAM — 格式**

* 觸發元資料導出後，該頁被重定向到404頁。 CQ-4262447 的 Hotfix

**DAM - 一般**

* (Adobe Stock整合)伺服器錯誤模式顯示在error.log檔案中，並出現Oauth錯誤。 CQ-4260406 的 Hotfix
* 如果將Adobe Stock整合應用6.4.4於，則該集6.4.3無效。CQ-4266009修補程式
* 即使在應用SP3修補程式後，也缺少到CF模型的連結。 CQ-4259029 的 Hotfix

**平台**

* （經典UI）升級到6.4.2後，「基本報表」元件中不提供編輯按鈕。NPR-28560:CQ-4262825修補程式
* 使用組合property.operation=like和property.depth的查詢時，它最終會出現InvalidQueryException。 NPR-28570：CQ-4262652 的 Hotfix
* 從重疊語言節點中刪除新添加的語言節點時出現內部伺服器錯誤。 NPR-28661：CQ-4239194 的 Hotfix
* 隨機啟動時sling-oak-1線程中stderr.log中的Null指針異常。 NPR-28665：CQ-4237845 的 Hotfix

**費利克斯**

* webconsole.plugins.memoryusage在刷新時導致死鎖。 NPR-27895：GRANITE-20715 的 Hotfix

**花崗岩**

* Sling Content Access Health Check對自定義資源解析器搜索路徑執行過長的/libs驗證。 NPR-28113：GRANITE-23529 的 Hotfix

**內容片段管理**

* 可用性改進和與內容片段的資產的功能奇偶校驗。 CQ-4253883 的 Hotfix

**社群**

* 將易受攻擊的引導程式升級到3.4，將ckeditor庫升級到4.5.11。NPR-28490:CQ-4257511修補程式
* 取消編輯模式不會恢復已刪除的附件。 NPR-27902：CQ-4255150 的 Hotfix
* 代表框撰寫只應對特權成員可見。 NPR-27900：CQ-4251235 的 Hotfix
* 在發佈實例上將rep:cache添加到AEM Communities用戶同步監聽器上的可忽略節點中。 NPR-27842：CQ-4247234 的 Hotfix
* 搜索框在UI級別顯示轉義字元。 NPR-27838：CQ-4259757 的 Hotfix
* 搜索特殊字元(, +,?)時生成錯誤 的子菜單。 NPR-28213：CQ-4260969 的 Hotfix
* 建立「社區特定管理員」組，讓用戶能夠編輯和創作相關社區站點。 NPR-27731
* 已添加鍵盤事件邏輯以開啟視頻。 NPR-27726：CQ-4254026 的 Hotfix
* 在 Publish 上為 AEM Communities Enablement 元件啟用鍵盤導覽。NPR-27728：CQ-4254028 的 Hotfix
* 為清單和卡片檢視按鈕新增 Aria 標籤。NPR-27727：CQ-4254027 的 Hotfix
* 在社區中處理開啟的資源解析程式會話。 NPR-27721：CQ-4258714 的 Hotfix

**轉換**

* 支援Microsoft翻譯器文本API v3。 NPR-28366：CQ-4249755 的 Hotfix
* jcr:language &amp; cq:language不會在翻譯後的語言中自動更新。 NPR-28338：CQ-4256046 的 Hotfix
* 循環引用在建立語言副本時導致StackOverflowError。 NPR-27596：CQ-4255621 的 Hotfix
* 在多語言翻譯項目中，按一下保存並關閉添加到項目的後續頁中的結果將導致建立新項目，而不是在現有項目中建立新的翻譯作業。 NPR-28219、NPR-28236：CQ-4261276、CQ-4260731 的 Hotfix
* 由於允許的字元數有限，因此在添加包含批量資料的內容片段時錯誤字串太長。 NPR-28722：CQ-4262362 的 Hotfix

**Social**

* 每次發佈新評論時，發佈到下一頁的評論都會以黃色突出顯示。 CQ-4261359 的 Hotfix
* 無法使用 API 刪除使用者產生的內容中的評論。NPR-28075：CQ-4261135 的 Hotfix
* AbstractNotificationOperationService導致ClassCastException。 CQ-4260456 的 Hotfix
* 移除播放器中共享內容物件參考模型 (SCORM) 雲端的參考。CQ-4260779 的 Hotfix

**UI — 基礎**

* 整合在HTML客戶端庫管理器中的「檔案系統輸出快取」功能會中斷編譯指令碼（如LESS檔案）的「debugClientLibs」功能。 NPR-27249：Granite-23313 的 Hotfix
* 激活調試模式時顯示的資產數始終為1，並且瀏覽器的控制台中會拋出許多JS錯誤。  NPR-27575：GRANITE-23750 的 Hotfix
* 使用Tomcat在WAR中保存和關閉頁面屬AEM性不會返回正確頁面。 NPR-27566：GRANITE-23671 的 Hotfix

**整合**

* `com.day.cq.personalization.impl.TeaserResourceEventHandler` 進入無限迴圈，並造成發佈執行個體上的節點更新。NPR-28561：CQ-4263096 的 Hotfix
* 系統沒有針對目標元件考慮 cq:actions。NPR-27616：CQ-4257497 的 Hotfix
* LiveCopy 繼承取消無法在目標容器上正常運作。NPR-28129：CQ-4259813 的 Hotfix
* (雲端服務設定) 根層級顯示的「繼承自」核取方塊應移除。NPR-27856：CQ-4259676 的 Hotfix

**吊帶**

* 更新到Sling Models API 1.3.8，實施1.4.10。NPR-27636:GRANITE-23537修補程式

**OAK — 段持久性**

* SegmentBufferWriter未在OnRC後刷新。 NPR-27464

**專案**

* 多語言翻譯項目沒有為不屬於管理員組的用戶建立多語言作業。 NPR-28508：CQ-4262023 的 Hotfix
* 只要在服務啟動期間調用getTaskRenderers,ProjectTaskListServlet就會洩漏ResourceResolver。 NPR-27590：CQ-4258011 的 Hotfix
* 如果目錄的子目錄數多於頁面大小，並且按日期或大小排序，則錯誤將阻止移動到第一頁之外。 NPR-28867：CQ-4265039 的 Hotfix
* DAM查看器中的備份跨站點指令碼(XSS)修復。 NPR-28106：CQ-4253215 的 Hotfix
* 無法由項目管理員向翻譯項目添加頁面，因為向翻譯項目添加新頁面的連結不可見。 CQ-4266334 的 Hotfix

**工作流程**

* 在工作流通知中開啟「標籤」(Tag)欄位的「完成工作項」(complete work item)對話框時，按一下交叉標籤會向其添加「標籤」(Tag)屬性。 NPR-28304：CQ-4261321 的 Hotfix
* 重新分配任務對話框中的用戶選擇切換按鈕無效。 NPR-28963：CQ-4264206 的 Hotfix

**Forms**

表單AEM6.4.4.0的主要亮點是：

* 添加了對記錄文檔安全API的支援，以便將其簽名和驗證為事務。

**Forms 附加元件套件**

**Adobe Sign整合**

* AEM 6.4Forms客戶端SDK不包含adobesign-recipent包。 NPR-27735：CQ-4259372 的 Hotfix

**調適型表單**

* 使用空模板建立Wan自適應表單時，客戶無法將面板子級到表單的根面板。 NPR-28758：CQ-4264157 的 Hotfix
* 當日期元件的年欄位的值為9999時，驗證指令碼將失敗。 NPR-28580：CQ-4262620 的 Hotfix
* 使用空模板建立自適應表單時，客戶無法將面板子級到表單的根面板。 NPR-28758：CQ-4264157 的 Hotfix
* 無法在自適應表單的延遲載入片段的欄位之間設定值。 NPR-27758：CQ-4259703 的 Hotfix
* 自適應表單不使用RT編輯器，而是載入其庫。  NPR-27759：CQ-4259193 的 Hotfix
* 重定向至「URL不適用於嵌入在AEM Sites頁中的自適應表單」診斷樹。 NPR-27620：CQ-4239287 的 Hotfix
* 無法在自適應表單的延遲載入片段的欄位之間設定值。 NPR-28320：CQ-4262345 的 Hotfix
* 自適應表單不使用RT編輯器，而是載入其庫。  NPR-28001：CQ-4259703、CQ-4259193 的 Hotfix
* Scribble簽名在AppleiOS12.1上運行的AEM Forms應用不起作用。NPR-28497:CQ-4261765修補程式
* 在6.4中使用「Forms Workflow」經典創作問題提交操作。CQ-4252740修補程式
* 處理塊和臨時儲存刪除時出錯。 NPR-28806：CQ-4264441 的 Hotfix

**Forms — 通信管理**

* 代理UI無法保留映像的原始大小。 NPR-28800：CQ-4259767 的 Hotfix
* CCR/代理UI:日期欄位的標籤在「資料」頁籤中移動。 CQ-4255499 的 Hotfix

**Forms — 交易報告**

* 添加了對使用數字簽名或將文檔證明為可開單交易記錄的計數的支援。 NPR-28495：CQ-4260236 的 Hotfix
* 已將數字簽名和認證添加到可計費API。 CQ-4260236 的 Hotfix

**Forms管理**

在「Forms管理器」的「開始審閱」嚮導和「移動資產」嚮導中，添加了對使用下划線替換把手客戶端庫的支援。 NPR-27643：CQ-4246536 的 Hotfix.
在發行版/640分支上安裝Forms管理軟體包後，一個軟體包仍處於已安裝狀態。 CQ-4265410Forms提交的熱修復程式及其附件未在工作流中出現，提交操作「調用AEM Forms工作流」並選中啟用門戶提交。 CQ-4263110 的 Hotfix

**Forms - 後端整合**

* 無法使用Client SDK、Hotfix for CQ-4238469測試前/後預處理器和自定義提交

**Forms - JEE 安裝程式**

**Forms - 文件安全性**

* 使用updatepolicy服務時，將發生無法強制對象錯誤。 NPR-28751：CQ-4252287 的 Hotfix
* Signature Build失敗，而版本較舊的commons-pkg。 CQ-4265535 的 Hotfix

**Forms — 基金會**

* 當AEM Forms在IBMWebSphere上被導入時，基於SOAP建立表單資料模型失敗。 NPR-27923：CQ-4251134 的 Hotfix
* PDF生成器的SRT工具無法檢測已安裝的Adobe Acrobat版本。 NPR-27971

**Forms — 設計師**

* XDP模板中的某些JPEG影像無法正確呈現。  NPR-26702：LC-3917457 的 Hotfix

**Forms - 工作流程**

* HTML5在an.lca中具有預設提交過程的Forms在JBoss 7上不工作。 NPR-28675：CQ-4243928 的 Hotfix
* 無法在HTML工作區中提交PDF forms。 NPR-28058：CQ-4260373 的 Hotfix
* 使用「調用FDM服務」Forms Workflow在資訊日誌中打印客戶資料。 CQ-4260385 的 Hotfix

**包含 Feature Pack**

**網站**

* 內容片段版本化比較6.AEM4的差別改進。NPR-26760:FP用於CQ-4248839
* 6.4的內容片段變AEM化差異改進。NPR-27866:FP用於CQ-4248839
* OSGI配置中啟用的功能 **工AEM作流撤消功能標誌**。 撤消操作應在設定標誌後終止工作流實例。 NPR-26451：CQ-4259090 的 Hotfix

**平台**

* 增強的查詢生成器方面提取利用Oak API實現6.4。NPR-26674:FP用於CQ-4230337

**包含的 OSGI 套件組合和內容套件**

下列文字記錄 CFP 中包含的 OSGI 套件組合和內容套件清單。

AEM 6.4.4.0 中包含的 OSGi 套件組合清單

[取得檔案](assets/bundles_6_4_4_0.txt)

AEM 6.4.4.0 中包含的內容套件清單

[取得檔案](assets/osgi_package_6_440.txt)

#### AEM 6.4.3.0 {#experience-manager-6430}

AEM  6.4.3.0是一項重要更新，包括自2018年4月6.4正式發佈以來發佈的效能、穩定性、安全性和關鍵客戶修復AEM和增強功能。

它也是累積的，這意味著6.4.3.0包括之前AEM發佈的所有6.4 Service Pack。

6.4.3.0的一些關鍵亮點AEM是：

* 內建存放庫 (Apache Jackrabbit Oak) 更新至 1.8.9 版。
* 添加了對Adaptive表單模板上allowedPaths屬性的支援。
* 增強的基於面板的對中資產的搜AEM索
* 跨站點指令碼(XSS)在「登錄」頁中修復。
* 改進的UI檢測。
* FormData處理方面的改進。
* 改進了對多欄位內項命名的處理。
* 在選擇期間改進對佔位符項（卡視圖和清單視圖）的處理。
* 已添加針對Managed Services的Adobe IMS身份驗證和Admin Console支援。

**資產**

* 如果啟用了「IDS解耦」選項，則「DAM更新資產」工作流不會從INDD檔案中提取引用。 NPR-26243;CQ-4250933修補程式
* 使用資產批量編輯器發佈資產時，不顯示成功消息。 NPR-26252;CQ-4251688修補程式。
* 在從搜索結果中查看資產後，如果按一下瀏覽器中的「後退」按鈕，則會導致出現「錯誤請求」錯誤消息，錯誤代碼為400。 26578盧比；CQ-4253741修補程式
* 資產元資料在安裝Service Pack後顯示無效的命名空間錯誤。 NPR-22341;CQ-4237202的快速修復
* 對於適用的資料夾，不顯示在清單視圖中重新排序資料夾和內容片段的選項。 NPR-27153;CQ-4255873修補程式
* 用戶無法將資產添加到新集合中，因為它會在錯誤彈出對話框中生成一條錯誤消息，其中顯示一個損壞的影像。 NPR-22431;CQ-4237086修補程式
* 動態下拉式清單不支援階層式下拉式清單。NPR-27043;CQ-4252564修補程式
* 如果用戶在DMS7雲配置中為「公司根資料夾」設定了非預設值，則查看器預設不按預期工作。 NPR-26360;CQ-4249505修補程式
* 資產數量非常多的實例的資產報告失敗。 NPR-27278;CQ-4256748修補程式
* 子資料夾不繼承父資料夾的SmartCrop映像配置檔案。 NPR-27197;CQ-4256273修補程式
* 啟用Dynamic Media整合後，將修改Assets的某些元資料屬性。 不顯示寬度、高度和位置屬性。 NPR-27203;CQ-4256258修補程式
* Dynamic Media不將配置的代理用於某些類型的資產。 NPR-25211;CQ-4244871修補程式
* 「元資料編輯器」頁包含無效項參數的空指針異常。 NPR-26169;CQ-4241368修補程式。
* 如果下拉清單具有選擇規則並應用了必需規則，則元資料編輯器中無法滿足所需規則。 NPR-27479;CQ-4251428的修補程式

**網站**

* 用戶可以使用內容策略在串聯式全屏模式下控制富格文本編輯器功能，但無法使用內容策略控制「編輯對話框富格文本編輯器」功能。 NPR-26750：CQ-4241130 的 Hotfix
* 當從全屏切換到浮動對話框時，富格文本編輯器將不可用。 浮動視圖包含兩個富格文本編輯器。 NPR-25589：CQ-4206008 的 Hotfix
* 在文本欄位中按回車鍵（Enter鍵）時，富格文本編輯器將切換到全屏模式。 NPR-26204：CQ-4245893 的 Hotfix
* 富格文本編輯器的清單插件已自動禁用，不允許修改。 NPR-26507：CQ-4239387 的 Hotfix
* 在富格文本編輯器窗口中添加特殊字元時，窗口將滾動到頂部。 NPR-26435：CQ-4249869 的 Hotfix
* 用戶端內容 segment.js 快取與非快取問題。NPR-26622：CQ-4253486 的 Hotfix
* 當從作者實例到發佈實例激活子規則時，發佈實例將停止工作。 NPR-26601：CQ-4253588 的 Hotfix
* RTF 編輯器與多個欄位結合時，出現「Uncaught TypeError: fieldAPI.getName 不是 foundation.js 的函數」錯誤。NPR-27146：CQ-4253155 的 Hotfix
* Salesforce整合無法使用代理配置。 NPR-27244：CQ-4245300 的 Hotfix
* 使用「管理發布」選項為以後的日期安排激活頁面並切換到清單視圖時，日曆表徵圖將丟失。 NPR-26974：CQ-4239206 的 Hotfix
* 用戶無法編輯頁面屬性中關閉的用戶組權限。 NPR-27138:CQ-4256089修補程式無法通過標籤編輯標籤。 NPR-26957：CQ-4254858 的 Hotfix
* 當移動從結構化內容片段模型引用的標籤時，不更新內容片段內對標籤的現有引用。 這種情況在內容片段模型的編輯螢幕中發生。 NPR-26776：CQ-4251805 的 Hotfix
* 在建立和升級具有多個頁面的啟動時，將為每個頁面建立多個版本。 NPR-26917：CQ-4254663 的 Hotfix
* siteadminAEM不處理在瀏覽器地址欄中鍵入的路徑。 NPR-26780：CQ-4254097 的 Hotfix
* 如果將頁面移動到新位置而不更名它，則頁面的版本歷史記錄將丟失。 NPR-26706：CQ-4254025 的 Hotfix
* 體驗片段管理員編輯器中的URL不允許重疊。 NPR-26319：CQ-4252156 的 Hotfix
* 當使用包含空體驗片段的模板建立頁面並發佈時，該頁面將無法開啟，並會出現DefaultSlingScript錯誤。 NPR-26305：CQ-4252460 的 Hotfix
* 當與具有相同名稱的類一起使用資料漏洞時，將產生不可編譯的代碼。 NPR-27282：Sling-7581 的 Hotfix
* 升級SP安裝後，這些站點的藍圖部署配置為空。 NPR-27609：CQ-4257078 的 Hotfix

**大壩 — Brand Portal**

* 在元資料架構表單發佈到Brand Portal時，不會發佈標籤謂詞。 CQ-4256218 的 Hotfix
* 當第三級資料夾從發佈到AEMBrand Portal時，如果不發佈父資料夾，則資料夾名稱會更改。 CQ-4255423 的 Hotfix
* 路徑瀏覽器謂語按預期從AEM Assets發佈到Brand Portal。 但是，BP的已發佈路徑仍然是/content/dam，必須更新。 CQ-4256240 的 Hotfix

**大壩 — Creative Cloud**

* 主導航中缺少「搜索Adobe資AEM產」表徵圖。 CQ-4254343 的 Hotfix

**DAM - DM 用戶端**

* 在將視頻插入與AVS視頻處理配置檔案關聯的資料夾後，瀏覽器窗口會反複刷新。 CQ-4253563 的 Hotfix
* YouTube發佈在使用包含大寫字元的即席標籤時失敗。 CQ-4252477 的 Hotfix
* 在類似PDF的資產中建立批注時，UI將啟動無限頁刷新循環。 NPR-27052：CQ-4255396 的 Hotfix

**DAM - DM服務**

* Dynamic Media不將配置的代理用於某些類型的資產。 NPR-10727;CQ-4244871修補程式

**平台**

* org.apache.sling.i18n的效能問題。 NPR-26812：SLING-7543 的 Hotfix
* 當輸入XML的格式化和部署時，無法查看節點屬性。 NPR-26198：CQ-4250448 的 Hotfix
* ResourceProviderTracker中的IndexOutOfBoundsException。 NPR-26968：GRANITE-23310 的 Hotfix
* JMX控制台累積大量管理會話，每5分鐘開啟一個新會話。 NPR-26958：CQ-4251090 的 Hotfix
* 從6.2升級到6.4後，日誌檔案將顯示未關閉資源解析程式com.adobe.granite.repository.hc.impl.content.sling.SlingContentHealthCheck的堆棧跟蹤。 NPR-26176：Granite-21734 的 Hotfix
* 如果將現成的調度程式刷新代理配置為更新別名，則操作將失敗，並出現StackOverflowError。 NPR-26373：CQ-4242928 的 Hotfix
* 複製使用過期的OAuth令牌，直到其失敗。 NPR-25894
* 限制頁（「關閉的用戶組」頁），帶吊帶：別名不會將用戶重定向到登錄頁。 NPR-25715:花崗石熱修補程式=22263
* 在發佈標籤時，UI上不顯示任何活動。 CQ-4255961 的 Hotfix
* 無法編輯傳統UI中的標籤。 CQ-4258697 的 Hotfix
* 已將org.apache.felix.http.bridge更新為4.0.4版。NPR-27038:花崗岩的後台 — 23334
* 套件管理器活動記錄應擷取至獨立的記錄檔中。NPR-27323：Granite-14866 的 Hotfix
* 包驗證程式不報告CFP中的重疊。 NPR-27119：GRANITE-22825 的 Hotfix

**專案**

* ACP API僅處理子目錄子目錄的分頁錯誤。 NPR-27617：CQ-4258639 的 Hotfix

**橡樹**

* 安裝6.4 Service Pack 2後無AEM法登錄儲存庫。 NPR-27171：Granite-23317 的 Hotfix

**複寫**

* 「審核日誌」保持開啟狀態，活動會話每天約750次，持續不斷增加。 NPR-27062：CQ-4241350 的 Hotfix

**社群**

* 論壇貼文和回覆會新增到第二頁頂端，而重新整理後貼文就會移至第一頁頂端的正確位置。NPR-27342：CQ-4247338 的 Hotfix
* 滾動後，指向所有資源的連結將刪除上下文路徑(/aempublish)。 NPR-26982：CQ-4254345 的 Hotfix
* 編輯已發佈站點時，在「社區管理者」、「社區管理者」和「特權成員」下拉清單中看不到添加的組。 NPR-27190：CQ-4258574 的 Hotfix
* 即使為組清單啟用分頁，啟用資源頁中也只列出10個組。 NPR-26934：CQ-4252985 的 Hotfix
* 在ConfigMgr中提供了啟用/禁用日誌元件中計畫帖子搜索的選項，並優化了SearchScheduledPosts作業。 NPR-26923：CQ-4250463 的 Hotfix
* 當社區設定為使用DSRP時，按地址中的關鍵字AEM搜索在日曆元件頁中不起作用。 NPR-26737：CQ-4258493 的 Hotfix
* 已實現指向注釋的直接連結，而不是注釋詳細資訊中的主帖子，以適當化UI和啟用資源。 NPR-26704：CQ-4251381 的 Hotfix
* 在審核控制台上通過多選擇進行審核的內容不會顯示在活動流上。 NPR-26695：CQ-4253244 的 Hotfix
* 在「社區消息傳遞」的「收件人」欄位中使用名和姓氏進行搜索不會返回預期結果。 NPR-26385：CQ-4248673 的 Hotfix
* 在論壇中上傳影像以外的附件 (例如 .pdf) 時發現錯誤。NPR-27360：CQ-4257753 的 Hotfix
* 如果使用MySQL DSRP設定了「作者發佈」，則取消固定或取消功能論壇帖子將不起作用。 NPR-26125;CQ-4251520修補程式
* 集合元件（論壇、部落格、日曆、建立、QnA）現在在元件對話框中具有一個屬性，以啟用/禁用「在作者編輯模式下阻止UGC」，以允許/拒絕在WCM編輯模式下載入UGC。 NPR-26978：CQ-4248161 的 Hotfix
* 「標籤搜索」不適用於本地化搜索詞。 NPR-26171：CQ-4249926 的 Hotfix
* 「後退」按鈕在論壇搜索中跳過頁面。 NPR-26950：CQ-4254804 的 Hotfix
* 在默AEM認Http埠(80)上運行的實例無法到達imsmanifest.xml。 NPR-27173：CQ-4252211 的 Hotfix
* 如果AEM Communities設定為DSRP，則取消標籤注釋作為QnA的答案無效。 NPR-26247：CQ-4252232 的 Hotfix
* 無法調用Adobe儲存：414錯誤 — 當用戶搜索/content/community-components/en/search.html並選擇「作者」欄位作為該搜索項的篩選器之一時，觀察到長GETURI。 NPR-26643：CQ-4251303 的 Hotfix
* ASRP配置中DataCentreURL的下拉值從Dallas更改為Virginia（對於VA6）。 NPR-26936：CQ-4254434 的 Hotfix
* 論壇搜索中的特殊字元返回錯誤或沒有結果。 NPR-26930：CQ-4247744 的 Hotfix
* 論壇搜索中顯示的「結果數」的數字對英語和德語區域設定使用不正確的分隔符。 NPR-27050：CQ-4248939 的 Hotfix
* 未讀通知不會超過21。 NPR-26946、NPR-27480：CQ-4252829、CQ-4256939 的 Hotfix
* 任何元件的注釋部分中的分頁使用戶在通過分頁到達頁面時向上滾動以查看頁面內容。 NPR-27032：CQ-4251228 的 Hotfix
* 從AEM Author實例的管理控制台查看縮略圖時，無法在縮略圖上按一下社區站點資料夾。 NPR-26986：CQ-4254036 的 Hotfix
* 「標籤所有已讀」選項僅將前10個通知標籤為已讀，其他通知在頁面刷新前仍未讀。 NPR-27037：CQ-4254058 的 Hotfix
* 不會為「標識」觸發分頁，除非重新載入主題（或回復）清單，否則它將變長。 NPR-26193：CQ-4252104 的 Hotfix
* 其他用戶的活動和刪除了在使用版主憑據登錄時可見的UGC，並在版主配置檔案URL的末尾添加「#social-activities」或「#tabs-2」。 CQ-4251355 的 Hotfix
* 無法從部落格中刪除所有分配的標籤。 NPR-26851：CQ-4253359 的 Hotfix
* 在UGC刪除時不會刪除與UGC的關係。 NPR-27630：CQ-4258706 的 Hotfix
* 回復連結在行上不工作，按一下論壇回復。 NPR-27623：CQ-4256138 的 Hotfix
* 使用者訂閱限制上限為 1000。NPR-27614：CQ-4254689 的 Hotfix
* 在角色設定中編輯站點和編輯角色會引發空指針異常。 NPR-27377;CQ-4255909修補程式

**轉換**

* 翻譯預覽與we.retail示例內容不相容。 NPR-26727：CQ-4241179 的 Hotfix

**UI — 基礎**

* 在升級到6.4後嘗試下載配置時，返AEM回NullPointerException。NPR-27310:花崗石熱修補程式–23573
* 用於granite.platform.login修復的主動備份。 NPR-26941
* granite.ui.content修復的主動備份。 NPR-26294
* 數字欄位元件不驗證Internet Explorer 11上的負數。 NPR-26701
* granite.ui.coralui3的主動備份修復。 NPR-26662
* granite.ui.coralui3-eon的主動備份修復。 NPR-26666
* granite.ui.foundation.components的主動備份修復。 NPR-27313
* granite.ui.commons的主動備份修復。 NPR-26753
* 主動式 Foundation UI 反向移植。NPR-26248

**整合**

* 不會發AEM布通過目標引擎建立的經驗的修改。 NPR-24869：CQ-4247832 的 Hotfix
* 如果活動和體驗的名稱包含日文字元，則無法建立這些活動和體驗。 NPR-27271：CQ-4256857 的 Hotfix
* 更新啟動API終結點。 NPR-26790：CQ-4254380 的 Hotfix
* (Personalization)BrandsRetriever在整棵樹上行走。 NPR-27060：CQ-4255790 的 Hotfix

**WCM — 管理員UI**

* 已添加HTTPtest，用於發佈/取消發佈包含引用的頁面和Live Copy的UItest。 CQ-4256894 的 Hotfix

**WCM - 頁面編輯器**

* 對於第一次編輯時的元件，將禁用編輯工具欄。 CQ-4253270 的 Hotfix

**Forms**

表單AEM6.4.3.0的主要亮點是：

* 已啟用對具有動態實體替代的對象的陣列/清單的支援。
* 為數字簽名、Reader擴展、加密提供程式和信任儲存中的Reader擴展工作流啟用了FIPS符合性。
* 已向使用設計器或輸出服務生成的XFA表單添加PDF/UA支援。
* 已啟用對Adaptive表單模板上allowedPaths屬性的支援。
* 增加了對AEM Forms6.4的JBoss 7.1.4支援。

**Forms 附加元件套件**

**後端整合**

* 無法基於SOAP響應中的動態實體填充表單資料模型映射。 NPR-26428：CQ-4250639 的 Hotfix
* 表單資料模型中使用TestUI輸入的_elementNamespace的值在SOAP請求中未正確反映。 CQ-4255373 的 Hotfix
* 可為null的屬性約束已初始化為預設值，無法與FDM同步。 CQ-4253873 的 Hotfix
* 對於OData資料源，可為null的屬性的預設值未設定為True。 CQ-4253870 的 Hotfix

**調適型表單**

* 無法載入站點和表單編輯器。 NPR-26977;CQ-4249170修補程式
* 使用鍵盤將附件添加到自適應表單時出現問題。 NPR-25913;CQ-4249456修補程式

**Forms -互動式通訊**

* 無法移動已使用Interactive Communication的Web通道和自適應表單的內容樹中的「添加子面板」選項添加的面板。 CQ-4253915 的 Hotfix
* 在打印通道的「資料源」部分中顯示表名，而不是FDM關聯的標題。 CQ-4253669 的 Hotfix
* isUseXFABullets()函式未在PrintChannelRenderOptions類中禁用，並且在客戶端SDK中可用。 CQ-4246583、CQ-4252700

**通信管理**

* 6.4的Javadoc不包含com.adobe.dbforms。*包和相應的類。 CQ-4253200 的 Hotfix
* CCR UI顯示日期欄位的預設垃圾值，以防test資料XML沒有輸入。 CQ-4252041 的 Hotfix
* 如果字母包含清單模組，則在從字母生成PDF時，項目符號和文本之間的空間將丟失。 CQ-4250588 的 Hotfix

**Forms Manager**

* 已啟用對Adaptive表單模板上allowedPaths屬性的支援。 NPR-26598：CQ-4255892 的 Hotfix

**Forms - 工作流程**

* 如果在執行Forms工作流時大括弧包含在任務名稱中，則日誌中將顯示異常。 CQ-4256626 的 Hotfix
* 無法在AEM Forms工作區中開啟搜索模板。 CQ-4255651 的 Hotfix

**行動 Forms**

* 退出AEM Forms中的日期欄位時，退出通知不顯示，該欄位在Internet Explorer或Chrome中呈現為HTML。 NPR-26483：CQ-4239352 的 Hotfix
* 處理開始時XML中包含的日期會導致用戶嘗試離開表單時表單引發驗證錯誤。 NPR-26787：CQ-4251211 的 Hotfix

**Forms - JEE 安裝程式**

**PDF生成器服務**

* 無法顯示PDF生成器的標準報告和符合性設定。 NPR-26715：CQ-4253384 的 Hotfix
* convertpdf二進位檔案在AIXForms附加軟體包中丟失，這在調用PDFA服務時導致失敗。 CQ-4257873 的 Hotfix
* 紙面捕獲服務在處理TIFF檔案時崩潰。 NPR-28079：CQ-4240649 的 Hotfix

**文件服務**

* 在數字簽名、Reader擴展、CryptoProvider和TrustStore中為RE工作流添加FIPS符合性。 NPR-27495：CQ-4257572 的 Hotfix
* 在循環中運行AssemblerService.toPDFA服務時，轉換失敗。 NPR-26354：CQ-4248656 的 Hotfix
* 無法根據PDF/A-1b標準正確驗證PDF合規性。 NPR-26286：CQ-4227539 的 Hotfix
* 將AEM Forms從6.1 SP2 CFP5升級到CFP13時記憶體不足問題。 NPR-26285：CQ-4244379 的 Hotfix
* 無法根據PDF/A標準正確驗證PDF合規性。 NPR-26272：CQ-4248823 的 Hotfix

**Forms — 基金會**

* 增加了對AEM Forms6.4的JBoss 7.1.4支援。NPR-27331;CQ-4255601修補程式

**包含 Feature Pack**

* 已啟用對具有動態實體替代的對象的陣列/清單的支援。 NPR-26590：CQ-4254655 的 Hotfix

**包括OSGI捆綁包和內容包**

AEM 6.4.3.0 中包含的 OSGi 套件組合清單

[取得檔案](assets/6.4.3.0_bundles.txt)

AEM 6.4.3.0 中包含的內容套件清單

[取得檔案](assets/6.4.3.0_OSGI.txt)

#### AEM 6.4.2.0 {#experience-manager-6420}

AEM 6.4.2.0是重要的更新，包括效能、穩定性、安全性和關鍵客戶修復程式以及自AEM6.4 i的正式發佈以來發佈的增強功能 **2018年4月。**
它也是累積的，這意味著6.4.2.0包括之前AEM發佈的所有6.4 Service Pack。

6.4.2.0的一些關鍵亮點AEM是：

* 內建存放庫 (Apache Jackrabbit Oak) 更新至 1.8.7 版。
* 增加了對HTML模板語言(HTL)規範1.4功能的支援
* 增加了對MongoDB Enterprise 3.6的支援。
* 「站點」頁面編輯器添加了對上下文內編輯和合成的支援，客戶端元件在React或Angular中與 <a href="../sites-developing/spa-walkthrough.md">AEM編SPA輯器JS SDK</a>。
* 內容片段增強：添加了在文本欄位中添加註釋的功能，並逐個比較了版本。
* 已添加 [與Adobe Stock](/help/assets/aem-assets-adobe-stock.md) 使用戶可以直接從用戶介面搜索、預覽、保存和許可Adobe StockAEM資產。 有關詳細資訊，請參見 [將Adobe Stock資產與AEM Assets](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/creative-workflows/adobe-stock.html)。
* Assets添加了對動態條件元資料模式的支援以及為資產資料夾設定元資料模式的能力。
* 在每個元件中添加配置以啟用/禁用資料夾縮略圖建立/更新功能。
* 頁面創作上的影像編輯器增強功能。
* 社區中的回歸修復，用於在刪除所選答案時未正確處理評分事件。
* 已將solr的搜索結果最大限制修改為MAX_INT-10000。
* 僅在對storeTransaction的首次調用中啟動事務刷新作業。
* 「全選」按鈕現在可在「卡視圖」和「列視圖」中使用。
* CoralUI中的輔助功能改進。
* 改進了Coral.Keys處理。
* 將moment.js更新為2.22.2
* 已將jquery更新為1.12.1
* 介紹了基礎工作流狀態元件。
* 已將GCC更新為最新版本。
* 將SAML移動到新的外部IDP同步。

**資產**

* pptx檔案的子組生成不包含任何影像和縮略圖。 NPR-24286：CQ-4217986 的 Hotfix
* migrateAllAssets — 添加對批處理的支援，AEM並改進將UUID添加到舊資產的方法。 NPR-24861：CQ-4242863 和 CQ-4247874 的 Hotfix
* 縮略圖生成時的效能問題。 NPR-24693：CQ-4246960 的 Hotfix
* （觸摸UI）「選項謂詞」元件添加到「資產共用發佈器」頁面時仍為空。 NPR-24643：CQ-4245295 的 Hotfix
* （工作流）智慧標籤資產不會通過代理配置進行處理。 NPR-25840：CQ-4248202 的 Hotfix
* (Omnisearch)從搜索條件中刪除檔案類型：image不會刪除影像類型。 NPR-25232：CQ-4248280 的 Hotfix
* 嘗試將檔案移動到其他資料夾時，不顯示名稱中帶有撇號的資料夾。 NPR-25125：CQ-4248660 的 Hotfix
* 當語言首選項設定為「英語」以外的值時，「子組」頁中的滑塊無法正常工作。 NPR-25274：CQ-4248489 的 Hotfix
* 在具有歐洲數字格式的電腦上開啟元資料導出csv檔案時出現問題。 NPR-26009：CQ-4250677 的 Hotfix
* 在沒有「刪除」權限的資產資料夾選擇中，「建立」按鈕不可用。 NPR-25788：CQ-4250140 的 Hotfix
* （備份）輔助功能增強：重複ID:id屬性值必須唯一，標籤：表單元素必須具有標籤和連結名稱：連結必須具有可識別的文本。 NPR-24252：CQ-4250905、CQ-4250906、CQ-4250907 的 Hotfix
* 對於歐洲國家，上載帶「，」分隔欄位的csv失敗。 NPR-25549：CQ-4249931 的 Hotfix
* (Brand Portal)發佈資產時，多頁pdf檔案的子組不發佈。 NPR-25991：CQ-4245162 的 Hotfix
* 發佈以後用於AEMBrand Portal複製的功能。 NPR-25911：CQ-109139 的 Hotfix
* 由非管理員用戶發佈和取消發佈私有集合將導致NPE。 NPR-25906：CQ-4250594 的 Hotfix
* 禁用將內容片段和表單架構發佈到Brand Portal。 NPR-24176、NPR-26004：CQ-4251592、CQ-4252026 的 Hotfix
* (Dynamic Media)將DM查看器更新為5.10.1版，以便在「影像預設」頁面上檢查重複名稱。 請參閱更新Dynamic Media查看器(5.10.1)。 NPR-24403：CQ-4247554 的 Hotfix
* 在選擇資產或資料夾時，在列視圖中的瀏覽器控制台中出現Javascript錯誤。 NPR-25939：CQ-4250228 的 Hotfix
* （列視圖）無法識別任務，因為關鍵檔案顯示為空白條目。 NPR-25903：CQ-4246307 的 Hotfix

**網站**

* 6.2上的datasource.jspAEM查詢與6.AEM4不同。NPR-24968:CQ-4244235修補程式
* （經典UI）無法向頁面添加標籤。 NPR-25255、NPR-25612：CQ-4249615 的 Hotfix
* HTML模板語言規範1.4支援AEM6.4.2.0 NPR-24585
* 複製即時複製頁後，本地元件上的繼承錯誤。 NPR-25920：CQ-4236737、CQ-4248957 的 Hotfix
* ON/OFF時間儲存在crx/de中，但在頁面屬性UI控制台中讀取的時間不相同。 NPR-25154：CQ-4243431 的 Hotfix
* 「樣式系統」會中斷對話框的初始屬性值。 NPR-25648：CQ-4250073 的 Hotfix
* 在cq:htmlTag節點中定義cq:tagName屬性時，如果通過JSP包含元件，則不考慮標籤名稱。 NPR-24154：CQ-4244120 的 Hotfix
* 針對巢狀的 parsys 元件，一律從多個可用元件中套用滿足設計的第一個元件 (最短巢狀路徑)。如需詳細資訊，請參閱[設計路徑解析](https://docs.adobe.com/content/help/zh-Hant/experience-manager-64/developing/platform/templates/page-templates-static.html)。NPR-24973：CQ-4246276 的 Hotfix
* 將文本貼上到RTE元件時，將顯示一個彈出對話框，但無法正確呈現。 NPR-24895：CQ-4245901 的 Hotfix
* (RTE)具有強制性外地指標的業績問題。 NPR-24894：CQ-4241895 的 Hotfix
* （頁面元件）將元件添加到Parsys會從右側裁切，並顯示設備幀寬度。 NPR-25536：CQ-4238224 的 Hotfix
* 純文字檔案編輯器發送未裁剪的資料並添加額外空格。 NPR-25312：CQ-4249006 的 Hotfix
* 使用 inlide 模式開啟元件時，先前載入的外掛程式第二次會無法顯示。NPR-24610：CQ-4236850 的 Hotfix
* 通過複製/貼上在編輯器視圖中載入XF不會自動載入主變體。 NPR-24841：CQ-4248037 的 Hotfix
* siteadmin / damadmin中HTML結構錯誤，導致IE11中斷。 NPR-24686：CQ-4246363、CQ-4248402 的 Hotfix
* （管理發布嚮導）在「選項」步驟中執行某些操作後，激活日期的日曆不會開啟。 NPR-25681：CQ-4250205 的 Hotfix
* 由於功能遭淘汰，傳統 UI 無法用於編輯 CUG。NPR-25075：4241823 的 Hotfix
* 建立選項不可用於建立體驗片段。 NPR-26053：CQ-4249923 的 Hotfix
* XF變體因此被激活兩次，為同一項生成重複ID。 NPR-24179：CQ-4245093 的 Hotfix
* Foundation 表格容易受到儲存型跨網站指令碼攻擊。NPR-25185：CQ-4240760 的 Hotfix
* 將元件從6.2.1.13遷移到AEM6.4時出現「Invalid recursion selector value」錯誤。NPR-24146

**WCM - 頁面編輯器**

* 因為執行時間長的查詢 (超過 6 個) 出現多個堆疊，導致 AEM 變得緩慢。CQ-4240247 的 Hotfix
* 在cq:htmlTag節點中添加空cq:tagName時，JS出錯。 CQ-4251852 的 Hotfix
* 根據columnClassNames重新定位更新EditableActions。 CQ-4250781 的 Hotfix
* 使用單個屬性和屬性公開資源和模型路徑。 CQ-4251255 的 Hotfix
* 還原export.json API中斷更改。 CQ-4251854 的 Hotfix
* (可編SPA輯)1.0.0的候選版本。CQ-4251991修補程式
* 編輯任何一個元件時，編輯工具欄將被禁用。 CQ-4253270 的 Hotfix

**整合**

* 庫和下載URL欄位應可編輯。 NPR-24804：CQ-4246864 的 Hotfix
* 多個DTM配置出現問題。 NPR-24685：CQ-4247293 的 Hotfix
* 已添加對托管客戶端庫非同步部署的支援。 NPR-25716：CQ-4245745 的 Hotfix
* 缺少相應優惠的目標元件呈現整個頁面，而不是空的目標元件，則添加該頁面的另一個完整格式副本。 NPR-25273：CQ-4248003 的 Hotfix
* 目標引擎 (mbox.js、at.js) 沒有使用損害 URL 而使用包含冒號的 URL，這可能因為某些部署而失敗。NPR-25339：CQ-4237854 的 Hotfix
* （啟動）LibraryDownloadProcess儲存錯誤的libraryUri值。 NPR-25330：CQ-4250006 的 Hotfix

**平台**

* 重新索引循環 |在從6.3到6.4的就地升級期間執行BinaryTextExtraction時執行NPE。花崗岩熱修補程式 — 21677
* 內部標籤路徑的跨邊界覆蓋/libs/cq/cloudserviceconfigs/templates/configpage/jcr:content — 運行模式檢測器時出現問題。 NPR-25036：CQ-4248597 的 Hotfix
* 由於LogEntryImpl中的NPE而未寫入日誌項。 NPR-25627：Granite-22383 的 Hotfix
* 複製刪除事件不檢查權限。 NPR-25679：CQ-4241234 的 Hotfix
* 在「第CQ天郵件服務」中添加了STARTTLS支援。 NPR-25611：CQ-4249924 的 Hotfix
* 對granite.platform.login進行主動備份修復，以提高可訪問性。 NPR-25176:花崗岩21746和花崗岩21309熱固劑
* (AEM6.4)重新構建和重新安裝軟體包時出錯。 NPR-25173：CQ-4247939 的 Hotfix
* 已刪除預設MERGE_PRESERVE aclHandling。 NPR-24593：Granite-21889 的 Hotfix
* 在兩次應用ContentDispositionFilter後，響應中不會傳播和丟失Content-Type。 NPR-24175：Sling-7525 的 Hotfix
* 升級到6.4分支後，包管AEM理器狀態錯誤。 NPR-24551：Granite-21750 的 Hotfix
* AMS實例 — 錯誤日誌分析。 CQ-4249567 的 Hotfix

**安全性**

* SAML重新登錄使用Okta IDP重定向到註銷頁。 NPR-25523：GRANITE-22364 的 Hotfix
* 通過OAK外部IDP OAuth提供程式配置進行IMS身份驗證會禁用在中建立的AEM用戶。 NPR-25301：Granite-22363 的 Hotfix

**MAC - Test&amp;Target 整合**

* （目標）在目標過程中出現文本元件錯誤。 CQ-4233343 的 Hotfix

**社群**

* （檔案庫）下載帶空格的資源時，會導致格式問題。 NPR-24260：CQ-4245159 的 Hotfix
* 多個 Adobe Social 問題的修正。NPR-24247：CQ-4245054、CQ-4245120、CQ-4245296 的 Hotfix
* 成員和組控制台的無限滾動失敗，以防作者在不同的上下文路徑上發佈運行。 NPR-24437：CQ-4246013 的 Hotfix
* 即使從已應答狀態中刪除後，帖子也不會返回未應答狀態，並且分數不會減少。 NPR-24419：CQ-4245797、CQ-4245932 的 Hotfix
* 使用社區中的日曆功能添加的事件輸出錯誤的值。 NPR-24883：CQ-4244056 的 Hotfix
* （社區論壇）「分頁」按一下問題和「頁面載入」行為。 NPR-24880：CQ-4246109 的 Hotfix
* (Chrome)社區事件時區轉換失敗。 NPR-24881：CQ-4247115 的 Hotfix
* 無法在電子郵件中呈現嵌入對象。 NPR-24999：CQ-4248022 的 Hotfix
* 除了建立UGC外，還應在UGC更新上執行自動對代序列。 NPR-25892：CQ-4251399 的 Hotfix
* 組上的模式對話響應。 NPR-25623：CQ-4248805 的 Hotfix
* 刪除內容時引發Solr異常。 NPR-25869：CQ-4248908 的 Hotfix
* 具有大量帖子的指向線程的分頁連結在通知上不起作用。 NPR-25678：CQ-4243038 的 Hotfix
* 搜索結果中的時間值顯示伺服器時間，而不顯示客戶端的時區。 NPR-25594：CQ-4248986 的 Hotfix
* （論壇評論）「瀏覽器後退」按鈕未按預期工作。 NPR-25205：CQ-4248573 的 Hotfix
* （搜索結果）瀏覽器後退按鈕未按預期工作。 NPR-25214：CQ-4248574 的 Hotfix
* 覆蓋社區組成員清單元件時返回Null。 NPR-25228：CQ-4248523 的 Hotfix
* （社區日曆）在使用新封面映像保存事件時生成ClassCastException。 NPR-25167：CQ-4248662 的 Hotfix
* （社區）消息被截斷。 NPR-25326
* （AEM發佈）Scorm資源在上下文路徑下失敗並顯示空白螢幕。 NPR-26155：CQ-4251942 的 Hotfix
* (MSRP)新建立的日曆被部分保存到錯誤日誌中。 NPR-26071：CQ-4250531 的 Hotfix
* 只有刷新頁面時才會更新論壇/主題分頁。 NPR-26070、NPR-25965：CQ-4249509 的 Hotfix
* （問答論壇）在開啟指向注釋的直接連結時無法導航到上一頁。 NPR-26069：CQ-4251699 的 Hotfix
* 在「建立」組中上載映像在移動上不起作用。 NPR-26172：CQ-4251703 的 Hotfix
* （消息）使用DSRP時，消息接收方的名稱始終顯示為「未知」。 NPR-26056：CQ-4251397 的 Hotfix
* 啟用 Scorm 資源完成狀態在 UI 中顯示為空白。NPR-26034：CQ-4249994 的 Hotfix
* 在建立新社區組時，會在活動/活動mongoMK群集上建立重複的社區組。 NPR-26032：CQ-4245884 的 Hotfix
* （作者）組建立嚮導在嚮導中載入/建立組需要太長時間。 NPR-26031：CQ-4244966 的 Hotfix
* 在hbs指令碼中添加include語句時，Parsys將消失。 NPR-25908：CQ-4250489 的 Hotfix
* 啟用「允許有特殊權限者」時，有特殊權限的成員應只能為具有社群成員身分的使用者撰寫內容。NPR-25877：CQ-4248450 的 Hotfix
* 阻止釋放連結。 NPR-25966：CQ-4251478 的 Hotfix
* 在刪除答復時，論壇分頁不會動態更新。 NPR-25970：CQ-4248975、CQ-4252843 的 Hotfix
* 在出現嵌套注釋時，自動滾動和突出顯示在日曆和檔案欄事件上不起作用。 NPR-25958：CQ-4251471 的 Hotfix
* (DSRP)直接/深度連結效能隨大量用戶生成內容而降低。 NPR-25957：CQ-4251470 的 Hotfix
* 無法修改允許特權成員和特權成員的屬性。 NPR-26014：CQ-4244592 的 Hotfix
* 將全部標籤為已讀會重置所有社區頁的通知計數器。 NPR-25931：CQ-4248612 的 Hotfix
* 編輯DSRP的IT失敗。 NPR-25929：CQ-4251382 的 Hotfix
* 生成電子郵件模板時，由於NPE,IT電子郵件失敗。 NPR-26039：CQ-4250962 的 Hotfix
* 當以非常高的解析度嵌入影像時，論壇主題問題。 NPR-26037：CQ-4244453、CQ-4253099 的 Hotfix
* 當伺服器時區與用戶時區不同時，時間顯示交換機。 NPR-26036：CQ-4248751 的 Hotfix
* 將具有相同名稱的檔案兩次附加到論壇帖子會導致伺服器錯誤。 NPR-24172：CQ-4244367 的 Hotfix
* 備份效能修復 — 在作者和發佈上進行分組分頁、在作者上進行分組搜索、避免對日誌、日曆和想像進行答復的序列化以及在查看組清單頁時為每個組獲取組成員資格（邀請/取消邀請）按鈕的延遲載入。 NPR-24538：CQ-4246515 的 Hotfix
* 在作者上不可見啟用資源。 CQ-4252618 的 Hotfix
* 未知用戶不會為線程生成通知。 CQ-4245132 的 Hotfix
* 組搜索未顯示在左滑軌上。 CQ-4252621 的 Hotfix
* （作者）分頁操作不適用於組控制台。 CQ-4242786 的 Hotfix
* j查詢UI升級。 CQ-4248894 的 Hotfix
* 升級到最新的SCORM 2017.1版。 NPR-25675：CQ-4240671 的 Hotfix
* 「代表撰寫」欄位對非社區用戶可見。 NPR-25331：CQ-4247858 的 Hotfix
* 即使在刪除後，UI上仍可看到開機自檢，並在控制台上出現錯誤。 NPR-26290：CQ-4252803 的 Hotfix
* （站點設定）無法保存對角色所做的更改。 NPR-26274：CQ-4252187 的 Hotfix
* （安全漏洞）由於JSON Web令牌配置錯誤而導致的帳戶接管。 NPR-26458：CQ-4253314 的 Hotfix
* 刪除回復後不重置分頁。 NPR-26326：CQ-4252997 的 Hotfix
* 編輯時，附件影像不顯示在「草稿」中。 CQ-4253360 的 Hotfix
* 在關係資料庫(DSRP)中附加附件時，頁面未刷新。 CQ-4253084 的 Hotfix
* 組未在啟用站點資源內工作。 CQ-4252975 的 Hotfix
* 先決條件學習路徑未保留在啟用中。 CQ-4252948 的 Hotfix

**工作流程**

* 工作流啟動程式UI不顯示過去41個啟動程式配置，並在控制台中觸發javascript錯誤。 NPR-25028：CQ-4247604 的 Hotfix
* 在不編輯舊式工作流啟動程式的情況下編輯舊式工作流將導致在包含「激活頁面/資產」步驟的任何工作流上建立多個工作流。 NPR-25870：CQ-4250896 的 Hotfix
* 如果頁面具有元資料節點，則工作流負載中的連結不正確。 NPR-25916：CQ-4250733 的 Hotfix

**轉換**

* 已修復導入已轉換的項目會發出兩個併發POST請求，因此會導致錯誤。 NPR-24889：CQ-4247638 的 Hotfix
* 修復了在為多語言建立翻譯項目時，同一語言的所有頁面都會添加到同一作業。 NPR-25091：CQ-4246112 的 Hotfix
* 在某些情況下，翻譯作業只列出前40頁。 NPR-25974：CQ-4248661 的 Hotfix
* DataPicker元件(Coral2)不更改年份。 NPR-24466：Granite-21893 的 Hotfix

**UI — 基礎**

* 主動式 Foundation UI 反向移植。NPR-24344、NPR-24345、NPR-25176、NPR-25095、NPR-24332、NPR-25653、NPR-25932、NPR-2593225935、NPR-25976
* （設計導入程式）導入頁面不會導入js,css。 NPR-25203：Granite-22236 的 Hotfix
* 主動式Foundation UI Backports（主動式Foundation UI備份），可提高產品的穩定性。 NPR-24334

**MAC - Test&amp;Target 整合**

* PersonalizationWizard（由「開始目標」啟動）的第二頁為空，並拋出控制台錯誤。 CQ-4253277 的 Hotfix

**體驗片段**

* 將經驗片段/目標整合合併AEM到6.4.2.0。CQ-4248653修補程式

**內容片段管理**

* 內容片段注釋和內容片段版本的並排比較。 CQ-4247148 的 Hotfix

**DAM - 一般**

* 「簽出者」篩選器在搜索中無法正常工作。 CQ-4247070 的 Hotfix
* 在執行資產更新工作流時，資產語言副本及其縮略圖將變為空白。 CQ-4250641 的 Hotfix
* 重複ID:id屬性值必須唯一。 CQ-4250905 的 Hotfix
* 標籤：窗體元素必須具有標籤。 CQ-4250906 的 Hotfix
* 連結名稱：連結必須具有可識別的文本。 CQ-4250907 的 Hotfix
* 埠資料夾元資料模板遷移JMX和ServiceUserMapping。 CQ-4252947 的 Hotfix
* WebdriverIOTest未在CQ/dam的發行版/640分支中運行。 CQ-4252749 的 Hotfix
* 如果連結已發佈，則不會重新計算到已移動資產的連結。 CQ-4245756 的 Hotfix

**DAM — 查看器**

* 載入新查看器時出現間歇性錯5.10.1。CQ-4250562修補程式

**丹 — Brand Portal**

* 從Brand Portal取消發佈集合失敗，出現錯誤。 CQ-4245990 的 Hotfix
* 無法取消發佈來自Brand Portal的影像預設。 CQ-4246140 的 Hotfix
* 發佈資產時，不會發佈多頁pdf檔案的子組。 CQ-4245162 的 Hotfix

**DAM - DMClient**

* 向YouTube發佈視頻資產時，導致YouTube的標籤包括該標籤的完整路徑。 CQ-4245549 的 Hotfix
* （選擇退出和選擇加入升級）查看器CSS重定向問題。 CQ-4247854 的 Hotfix
* 無法建立/編輯作為「administrators」組非成員的查看器預設。 CQ-4247618 的 Hotfix
* (6.4.1.0)在多個parsys中添加多個視頻會斷開視頻播放器。 CQ-4248517 的 Hotfix
* 在影像集中更名和移動資產將導致無法編輯。 CQ-4248434 的 Hotfix
* 將大型視頻發佈到YouTube，會超時留言。 CQ-4237831 的 Hotfix
* （清單視圖）資產選取器/選擇器的用戶介面將變為所有灰色，並且對用戶禁用。 CQ-4237817 的 Hotfix
* （垂直縮放）Css載入失敗，出現404錯誤。 CQ-4236508 的 Hotfix
* 嘗試下載資產名稱中具有百分比(%)字元的資產將導致空存檔。 CQ-4250558 的 Hotfix
* （卡視圖）在視頻資產上使用「複製並貼上」時不顯示任何處理指示燈。 CQ-4249037 的 Hotfix
* (從6.3.2升級到6.4)升級前影像預設在「格式副本」頁面上顯示為「未發佈」，但選中後不會生成URL按鈕。 CQ-4240406 的 Hotfix
* 技術負債/次要增強。 CQ-4240648 的 Hotfix
* 資產選擇器（或資產選取器）不顯示可用資料夾中的所有資產。 CQ-4218414 的 Hotfix
* 沒有高度的影像預設顯示大小不正確的影像。 CQ-4246546 的 Hotfix
* （多頁資產）按一下注釋時UI會斷開。 CQ-4251434 的 Hotfix
* 從6.3升級到6.4及更高版本的「分析」預設，將建立新的報告套件和分析預設，以丟失用戶較舊的報告資料。 CQ-4244529 的 Hotfix
* （管理發布嚮導）當嘗試發佈或取消發佈時，資產清單似乎為空。 CQ-4251881 的 Hotfix
* 在查看「設定成員」後選擇「查看者」時，AVS視頻無法播放。 CQ-4205308 的 Hotfix
* 預升級視頻處理預設不能添加新的視頻編碼預設，也不能編輯現有的編碼預設。 CQ-4240407 的 Hotfix
* 影像預設不應用於下載的動態格式副本。 CQ-4249862 的 Hotfix
* 「全選」按鈕在「查看器預設」清單頁上無法正確工作。 CQ-4252462 的 Hotfix
* 視頻配置檔案：「全選」按鈕無效。 CQ-4253076、CQ-4251447
* SP2驗證通過 — 煙霧通過。 CQ-4251639 的 Hotfix

**DAM - DMServices**

* Dynamic Media格式副本無法為EPS檔案生成。 CQ-4243688 的 Hotfix

**花崗岩**

* 捆綁包SymbolicName中的Typo會導致重複的捆綁包。 Granite-22155 的 Hotfix
* CUGConfiguration無法拾取CugExclude。 Granite-21109 的 Hotfix
* 重新啟動Adobe花崗岩工作流核心從中間重新運行建立不必要工作流的工作流步驟。 NPR-25057：Granite-22218 的 Hotfix
* JcrResourceBundle不正確支援多個基名。 NPR-25245：Granite-22317 的 Hotfix
* 在安裝內容包時，ACL按主體分組，因此會破壞權限模型。 NPR-24583：Granite-21591 的 Hotfix
* 將Jetty更新為9.4.11以修復漏洞。 NPR-25030：Granite-22120 的 Hotfix

**Forms**

表單AEM6.4.2.0的主要亮點是：

* 已添加新屬性，以便更新隊列而不刷新瀏覽器。
* 為用戶添加了對多個服務使用相同WSDL檔案的功能。
* 已從datepicker下拉清單中刪除不支援的時間戳模式。
* 在OSGI中增加了對xfaf和pdf的底層支援。
* 添加支援以使用 [事務處理報告功能](https://docs.adobe.com/content/help/en/experience-manager-64/forms/transaction-reports/transaction-reports-overview.html) 部署。
* 添加的代碼在條件規則編輯器中不顯示子變數。

**Forms 附加元件套件**

**事務報告**

* 使用在發佈伺服器上配置的反向複製的重要性更新Transaction Reporting配置。 NPR-26050：CQ-4246650 的 Hotfix
* 週期刷新作業的延遲初始化。 NPR-25968：CQ-4245024 的 Hotfix
* 事務記錄失敗，指針異常為Null。 CQ-4247302 的 Hotfix

**Forms - 工作流程**

* (HTML 工作區) 使用者認領任務時，系統會重新整理該特定使用者的佇列計數，但除非重新整理頁面，否則不會為其他使用者重新整理。此問題已由新屬性解決。 要將此新屬性配置AEM到實例，請參閱其配置設定。 NPR-24536：CQ-4233665 的 Hotfix
* 無法在6.4上的AEM Forms應用程式中載入大窗體。NPR-24463:CQ-4245091修補程式
* 嘗試查看共用任務時在MobileWorkspace App中出現問題。 NPR-25177：CQ-4248733 的 Hotfix
* Web和APK之間的驗證行為不一致。 NPR-25670：CQ-4248178 的 Hotfix
* 當對Web服務的調用在客戶端內開啟HTML5窗體時，它將失敗並返回錯誤消息。 NPR-26048：CQ-4244716 的 Hotfix
* 在窗體Windows應用6.3AEM中調用服務時出現問題。NPR-26468:CQ-4252341修補程式

**行動 Forms**

* （格式集）SSN和Mobile現場驗證問題。 NPR-24458：CQ-4244983 的 Hotfix
* 在HTML預覽中，不會使用多行欄位的預填充來顯示資料。 NPR-24549：CQ-4244212 的 Hotfix
* 在多行欄位上計算指令碼時，資料將丟失。 NPR-25333, CQ-4249610修補程式

**Forms — 互動式通信和通信管理**

* 使用基本模板和參考IC打印模板在IC上同步失敗。 NPR-24912
* (CCR)驗證器不適用於欄位/變數。 CQ-4245047 的 Hotfix
* 「資料模型對象」表徵圖在「文本編輯」工具欄上間歇性地消失。 CQ-4245122 的 Hotfix
* 如果刪除原始IC，則複製的IC上會出現異常日誌。 CQ-4249378 的 Hotfix
* 在字母格式副本中，即使資料正確，條件也不會計算為true。 CQ-4245944 的 Hotfix
* 在從內容樹中進行選擇時，不會突出顯示自動生成的元件。 CQ-4246178 的 Hotfix
* 開啟Web渠道模板編輯器時出現問題。 CQ-4248182 的 Hotfix
* 無法更改添加的資產順序，因為上/下箭頭仍處於禁用狀態。 CQ-4252042 的 Hotfix
* 無法更新條件模組的屬性。 CQ-4247909 的 Hotfix
* 當用戶在Web通道中重新排列對象時，需要改進「取消繼承」對話框的UX。 CQ-4241076 的 Hotfix
* 與 XDP 中所定義繫結對應的信函中的資料，不會在使用直接信函 URL 時填入。CQ-4245833 的 Hotfix
* （快取問題）Web通道的同步不反映對佈局片段、打印通道的文本片段所做的更改。 CQ-4251460 的 Hotfix
* 無法更新佈局段和DD屬性。 CQ-4247830 的 Hotfix
* (CCR)由於XML分析，草稿重裝失敗。 CQ-4250950 的 Hotfix
* （IC編輯器）「編輯片段」按鈕應更可發現。 CQ-4244694 的 Hotfix
* (XDP)在新建立的子窗體中添加佈局片段時，將顯示一個空白螢幕。 CQ-4248810 的 Hotfix
* DocumentFragment-master-DeployWithServerSideTeststest失敗。 CQ-4245496 的 Hotfix
* Condition模組中複製的文本模組變數Instance。 CQ-4252128 的 Hotfix
* PDF預覽URL不顯示發佈時的事務報告。 CQ-4246158 的 Hotfix
* IC同步與打印通道到Web通道同步相關的問題。 CQ-4251505 的 Hotfix
* EXM代碼清除：刪除LocalFunctionMapper。 CQ-4243265 的 Hotfix
* 更正IC webChannel表元件的TableHeader的資源類型。 CQ-4251821 的 Hotfix
* （IC編輯器）可用性問題。 CQ-4241081 的 Hotfix
* 打印通道子窗體不顯示插入功能。 CQ-4252994 的 Hotfix
* 刪除FDM節點或變數佔位符後，保持更改同步失敗。 CQ-4253178 的 Hotfix
* （模板編輯器）基本模板顯示頁眉/頁腳附加的拖放區域，以及開啟Web通道時螢幕閃爍。 CQ-4253323 的 Hotfix
* 在從內容樹中進行選擇時，不會突出顯示自動生成的元件。 CQ-4246178 的 Hotfix

**文件服務**

* （表格服務）OSGI缺乏對XFAF的支援。 NPR-25181, CQ-4251313修補程式
* 已裝配的PDF檔案標題中的字元將變亂。 NPR-25113：CQ-4244682 的 Hotfix

**調適型表單**

* 「發送郵件時提交操作」引發異常，CC/BC欄位為空。 NPR-25019：CQ-4243039 的 Hotfix
* 由於查詢效率低AEM下，無法使用OOTB表單元件。 NPR-25065：CQ-4247256 的 Hotfix
* 從guideImageChoiceComponent的對話框節點中刪除sling:orderBefore。 CQ-4245013 的 Hotfix
* （日期選取器）編輯模式不支援兩種類型的時間戳模式。 CQ-4237982 的 Hotfix
* 使用「Forms Workflow」經典創作問題提交操作。 CQ-4236981 的 Hotfix
* （Web通道）IC圖應從AF圖繼承colspan屬性。 CQ-4252143 的 Hotfix

**後端整合**

* （SOAP請求）大小數（超過6位數）以指數表示法表示，導致驗證錯誤。 NPR-25283：CQ-4248100 的 Hotfix
* 在複雜類型中定義的可選參數驗證不正確。 NPR-25070：CQ-4247107 的 Hotfix
* 為用戶添加了對多個服務使用相同WSDL檔案的功能。 NPR-24604, CQ-4247756修補程式
* FDM在其SOAP調用中混亂參數的順序。 NPR-25069, CQ-4247180修補程式
* FDM合併SOAP請求中的實體（在清單/陣列中）。 NPR-25284：CQ-4248375 的 Hotfix

**Forms JEE 安裝程式**

**PDFG 服務**

* 安全設定的建立/修改功能不起作用。 NPR-24769：CQ-4246927 的 Hotfix
* Optimize PDF通過通過單個API調用有選擇地解嵌字型。 NPR-23287

**文件服務**

* 輸出服務未為輔助功能Reader提供正確的標籤。 NPR-24438、NPR-24439、NPR-24440、NPR-24441:CQ-4243849、CQ-4243845、CQ-4243852、CQ-4243853的修補程式

**文件安全性**

* 使用文檔安全性建立策略時出現問題。 NPR-25586、NPR-25547：CQ-4247086 的 Hotfix

**Forms — 基金會**

* 間歇性作為系統上下文帳戶運行的進程。 NPR-25289、NPR-25313：CQ-4249331 的 Hotfix
* AEM FormsJEE受Apache Struts和Jackson資料綁定安全警報的影響。 NPR-25628：CQ-4242891 的 Hotfix
* 電子郵件起始點進程無效。 NPR-25253：CQ-4248518 的 Hotfix

**包含 Feature Pack**

**資產**

* 已添加 [與Adobe Stock](/help/assets/aem-assets-adobe-stock.md) 使用戶可以直接從用戶介面搜索、預覽、保存和許可Adobe StockAEM資產。 有關詳細資訊，請參見 [將Adobe Stock資產與AEM資產](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/creative-workflows/adobe-stock.html)。 NPR-15779：CQ-30857 的 Hotfix
* 已添加對動態條件元架構的支援。 有關詳細資訊，請參見 [級聯元資料](/help/assets/cascading-metadata.md)。 NPR-25189：CQ-4237413 的 Hotfix
* 已在內容片段上啟用「資產下載」選項。 有關詳細資訊，請參見 [資產報表](/help/assets/asset-reports.md)。 NPR-25186：CQ-4237410 的 Hotfix
* 能夠為資產資料夾設定元資料架構。 有關詳細資訊，請參見 [資料夾元資料架構](/help/assets/folder-metadata-schema.md) 並引用 [配置設定](#configuration-settings-required-for-npr) 6.4.2.0安裝AEM後。 NPR-21268：CQ-4221574 的 Hotfix

**網站**

* 允許編輯內容片段，但不具有刪除權限。 有關詳細資訊，請參見 [自定義和擴展內容片段](https://docs.adobe.com/content/help/en/experience-manager-64/assets/fragments/content-fragments-delete.html)。 NPR-25793：CQ-4248750 的 Hotfix
* 已添加為內容片段添加批注的功能。 有關詳細資訊，請參見 [變體創作片段](https://docs.adobe.com/content/help/en/experience-manager-64/assets/fragments/content-fragments-variations.html#annotating-a-content-fragment)。 NPR-25188：CQ-4235336 的 Hotfix
* 版本控制：並排比較內容片段。 有關詳細資訊，請參見 [管理內容片段](https://docs.adobe.com/content/help/en/experience-manager-64/assets/fragments/content-fragments-managing.html#comparing-fragment-versions)。 NPR-25187：CQ-4237412 的 Hotfix
* 支援到AEM6.4.2.0的映像編輯器增強。有關詳細資訊，請參見 [影像編輯器](https://docs.adobe.com/content/help/en/experience-manager-64/developing/components/image-editor.html)。 NPR-24467

**包括OSGI捆綁包和內容包**

AEM 6.4.2.0 中包含的 OSGi 套件組合清單

[取得檔案](assets/6.4.2.0_bundle-list.txt)

AEM 6.4.2.0 中包含的內容套件清單

[取得檔案](assets/6_4_2_0content-package-list.txt)

#### AEM 6.4.1.0 {#experience-manager-6410}

AEM  6.4.1.0是一項重要更新，包括自2018年4月6.4正式發佈以來發佈的效能、穩定性、安全性和關鍵客戶修復AEM和增強功能。

AEM 6.4.1.0可安裝在AEM6.4 GA上。 Service Pack的一些關鍵亮點是：

* 內建存放庫 (Apache Jackrabbit Oak) 更新至 1.8.3 版。
* 已引入增強智慧標籤。
* 在設計選取器、標籤選取器中修復（將源VM和目標VM更改為自動。）
* 新增對 typeHint 的支援，可將值儲存為字串。
* 已在郵件服務中添加對SMTP over TLS的支援。
* DMS7中HTTP轉發器的代理處理修復。
* 更新到/etc/clientlibs/social/thirdparty/handlebars/source/handlebars.js 1.3版。
* 在DMHybrid Opt-OUT和Opt-IN包中修復。
* 在Smart Crop中修復。
* 已將OOTB配置值遷移到新位置（從/etc到/conf）。
* 已將顏色配置檔案添加到交付伺服器上的客戶設定中。
* 從/etc遷移映像伺服器設定 — &amp;gt;/conf。
* 已添加源內容片段以供翻譯。
* 已將ARIA支援添加到「打印」和「打印」對話框。
* 已添加電子郵件驗證ARIA支援。
* 用於platform.clientlibs的主動備份修復。
* 在沒有輸入顯式dataType時防止指令碼自動執行（解析CVE-2015-9251）。

**資產**

* 在重新開啟資產屬性頁時，級聯下拉清單值顯示為空。 NPR-23042：CQ-4238761 的 Hotfix
* mylinkshare頁面上的共用連結和指向該頁面的連結對於非管理員用戶NPR-23044不可用：CQ-4239004修補程式
* 要防止6.4.0中的DAM資產更新工作流中出現空指針異常。NPR-24134:CQ-4244972修補程式
* 已發佈的WCM頁顯示熱點的佔位符表徵圖，OOTB查看器缺少CSS檔案，錯誤為403。 NPR-23041：CQ-4233716 的 Hotfix
* （詳細資訊視圖）「下一/後導航」功能將在「動態格式副本預覽」區域中保留一個DIV覆蓋，阻止查看者訪問。 NPR-23043：CQ-4238499 的 Hotfix
* CMYK影像格式副本的飽和度不正確。 NPR-23048：CQ-4235470 的 Hotfix
* 由XMPScene7ListInfoProvider提取的元資料佔用大量資源。 NPR-23754
* (dam-delivery)Http轉發器不尊重HTTP代理設定。 NPR-24002：CQ-4244140 的 Hotfix

**網站**

* 當我們在移動時更名頁面時，頁面移動是成功的，但更名功能不起作用。 NPR-22923：CQ-4235907 的 Hotfix
* 發佈指向 Adobe Campaigns 中匯入工具頁面的 Live Copy 頁面時發生錯誤。NPR-23053：CQ-4237164 的 Hotfix
* 在傳統UI中移動/更名失敗，錯誤為「移動頁面時出錯」，但未更名。 NPR-23051：CQ-4235907 的 Hotfix
* 將內容從列視圖切換到清單視圖將呈現一個空白頁，並為設定了OffTime且OnTime為空的頁觸發空指針異常。 NPR-22968、NPR-23052：CQ-4238940 的 Hotfix

**商務**

* 修復故障核心Hobbes測試用例（CQ/Commerce模組）。 CQ-4253494 的 Hotfix

**漏洞**

* Salesforce 整合容易遭受伺服器端請求偽造 (SSRF) 攻擊。NPR-24289：CQ-4245277 的 Hotfix
* ReportingServicesProxyServlet中的伺服器端請求偽造(SSRF)和跨站點指令碼(XSS)。 NPR-24657：CQ-4246880 的 Hotfix
* 跨站點指令碼(XSS):反映在商業目錄wizard.html/content中。 NPR-24642：CQ-4237017 的 Hotfix
* 管理員 UI 專案連結中有跨網站指令碼 (XSS)。NPR-23272：CQ-4241795 的 Hotfix

**WCM - Foundation 元件**

* 開啟「設計」選取器將導致指針出現空異常。 NPR-23047：CQ-4238736 的 Hotfix

**使用者介面**

* (Coral3 Datepicker)添加對typeHint的支援，將值另存為「String」。 NPR-23398：Granite-21194 的 Hotfix
* 國際化翻譯在語言級別不起作用。 NPR-22967、NPR-23046:花崗石–21111修補程式
* granite.ui.commons的主動備份修復。 NPR-23537
* granite.ui.content修復的主動備份。 NPR-23535
* granite.ui.coralui的主動備份修復。 NPR-23538
* 無法同時從組中刪除多個用戶。 NPR-23846
* (OMEGA)僅用英文報告&quot;功能&quot;。 NPR-23989：Granite-21231 的 Hotfix
* （設計導入程式）導入頁面不會導入js、css。 NPR-25203：Granite-22236 的 Hotfix

**整合**

* com.day.cq.analytics.sitecatalyst 中無結尾標記的資源解析器。NPR-22340：CQ-4236515 的 Hotfix
* 長時間執行查詢期間 TargetContentImpl 導致 AEM 變得緩慢。NPR-22359：CQ-4236907 的 Hotfix
* 目標引擎 (mbox.js、at.js) 沒有使用損害 URL 而使用包含冒號的 URL，這可能因為某些部署而失敗。NPR-22434：CQ-4237854 的 Hotfix
* 在「目標」模式中，作者不需要取消繼承即可修改從 Blueprint 繼承的元件。NPR-22865：CQ-4237907 的 Hotfix
* (Personalization)切換到「卡」視圖時表徵圖變形。 NPR-23373、NPR-23374：CQ-4240018、CQ-4240019 的 Hotfix
* (Personalization)觀眾控制台不顯示nt:folder類型。 NPR-23375：CQ-4242293 的 Hotfix
* 在發佈執行個體上將元件設為目標時，顯示目標元件之前的預設體驗時會出現閃爍畫面。NPR-23415：CQ-4242038 的 Hotfix
* （Adobe IMS控制台）刪除後，AccessTokenProvider OSGi服務配置將重新顯示。 NPR-23520：CQ-4208250 的 Hotfix
* 中繼資料夾結構出現設定參考複寫失敗。NPR-23485：CQ-4242751 的 Hotfix
* (Personalization)客戶端庫被代理servlet阻止。 NPR-23521：CQ-4240995 的 Hotfix
* （Adobe IMS控制台）在配置嚮導中未獲取已註冊的雲解決方案。 NPR-23977：CQ-4244549 的 Hotfix
* 在沒有HTML副檔名的頁面上載入目標內容時出現無限循環。 NPR-23522：CQ-4223600 的 Hotfix
* 對具有繼承的動態Tag Management配置引用的頁進行激活失敗。 NPR-23485：CQ-4242751 的 Hotfix

**平台**

* （經典UI）（觸摸UI）當嘗試通過資產搜索架構中的標籤謂詞瀏覽標籤時，標籤選取器不顯示並引發異常。 NPR-23049：CQ-4239371 的 Hotfix
* （經典UI）使用xtype=tags的元件返回Null，無法從eth標籤清單中選擇。 NPR-23050：CQ-4239937 的 Hotfix
* （品牌推廣）選擇性對話提到Adobe Marketing Cloud，而不是Adobe Experience Cloud。 NPR-23210：CQ-4237799 的 Hotfix
* Filter選項AEM在從6.3升級到6.4後會變得遲緩。NPR-23260:CQ-4239847修補程式（要檢查）
* 用於granite.omnisearch.core的主動備份修復。 NPR-23536
* 用於platform.clientlibs的主動備份修復。 NPR-23569
* Cloud Service編輯其他頁屬性時，配置繼承斷開。 NPR-23216：CQ-4239782 的 Hotfix
* 已在第CQ郵件服務中啟用STARTTLS支援。 NPR-23941：CQ-4240397 的 Hotfix

**專案**

* （內容片段）在將英文資產添加到翻譯時，不會為嵌入資產建立語言副本。 CQ-4243477 的 Hotfix
* msft config下拉清單顯示的配置來自/libs(6.4 configs)，而不是來自/etc(6.3 configs)（在舊模式下）。 CQ-4243475 的 Hotfix
* 自動提升和刪除翻譯項目中的翻譯啟動。 CQ-4243474 的 Hotfix
* 未翻譯站點內的內容片段。 CQ-4243482、CQ-4243483、CQ-4245687的修補程式
* 開啟翻譯作業搜索篩選器時出現伺服器錯誤。 CQ-4236813 的 Hotfix
* 即使在/conf/we-retail內部存在tif後，憑據配置下拉清單也為空。 CQ-4236315 的 Hotfix
* 開啟項目KPI:建立更多項目時效能下降。 NPR-23840：CQ-4238392 的 Hotfix
* 工作流程啟動器無法接受 String 的 TypeHint 值。NPR-23863：CQ-4238356 的 Hotfix

**社群**

* Handlebar 1.0版中的安全漏洞。 NPR-23636：CQ-4243055 的 Hotfix
* 批量允許已標籤郵件無效。 NPR-23867：CQ-4243962 的 Hotfix
* 論壇元件中的排序按鈕上未顯示預設值。 NPR-23882：CQ-4243375 的 Hotfix
* 從社區站點向組傳遞郵件的問題。 NPR-23935

**工作流程**

* Day CQ 工作流程電子郵件通知服務會針對 WorkflowCompleted 和 WorkflowAborted 通知，對每個 Mongo 節點觸發一封電子郵件。NPR-22515：CQ-4238172 的 Hotfix
* 運行DAM更新資產工作流會引發NullPointerException。 NPR-23010：Granite-21096 的 Hotfix
* 工作流進程步驟不顯示/etc/workflow/scripts中的指令碼。 NPR-23263：Granite-20775 的 Hotfix
* 工作流動態參與者步驟不顯示/apps/workflow/scripts中的指令碼。 NPR-23464：Granite-21276 的 Hotfix
* 編輯一次後無法編輯任何工作流。 NPR-23742：CQ-4238526 的 Hotfix
* （經典UI）編輯工作流啟動器後，這些條件消失，導致工作流在沒有任何條件的情況下啟動。 NPR-23835：CQ-4239153 的 Hotfix
* 項目收件箱：切換到日曆視圖顯示主收件箱內容。 NPR-23947：CQ-4241236 的 Hotfix
* 需要在捆綁包中公開負載詳細資訊，以便HTL元件可以在清單視圖中顯示值。 NPR-23948：CQ-4240953 的 Hotfix
* 無法在「對話參與者」步驟中儲存對話資料。 NPR-23965：CQ-4234123 的 Hotfix
* （觸摸UI）保存工作流模型時，「同步」按鈕將更改為「同步」，導致拼寫錯誤。 CQ-4244843 的 Hotfix
* 項目收件箱：切換到日曆視圖顯示主收件箱內容。 CQ-4244436 的 Hotfix
* 無法在「對話參與者」(Dialog Participant)步驟中選擇「對話」(Dialogs)。 CQ-4244532 的 Hotfix
* 用於granite.omnisearch.core的主動備份修復。 NPR-23536
* MobileWorkspace App 6.4中的共用任務問題。 NPR-26383

**WCM — 翻譯**

* （參考面板）在項目建立期間未執行翻譯作業。 CQ-4245327 的 Hotfix

**WCM - MSM**

* (MSM)推廣效能改進。 CQ-4231488 的 Hotfix
* (MSM)事件偵聽中實際發生的事件和事件處理之間的時間差。 CQ-4227766 的 Hotfix

**畫面**

* 由於screens-core-pkg:1.4.42缺少依賴項，螢幕頁失敗，並出現錯誤。CQ-4245918修補程式

**項目 — 翻譯**

* （內容片段）在將英文資產添加到翻譯時，不會為嵌入資產建立語言副本。 CQ-4243477 的 Hotfix
* msft config下拉清單顯示的配置來自/libs(6.4 configs)，而不是來自/etc(6.3 configs)（在舊模式下）。 CQ-4243475 的 Hotfix
* 自動提升和刪除翻譯項目中的翻譯啟動。 CQ-4243474 的 Hotfix
* 未翻譯站點內的內容片段。 CQ-4243482、CQ-4243483、CQ-4245687的修補程式
* 開啟翻譯作業搜索篩選器時出現伺服器錯誤。 CQ-4236813 的 Hotfix
* 即使在/conf/we-retail內部存在tif後，憑據配置下拉清單也為空。 CQ-4236315 的 Hotfix

**內容片段管理**

* 刪除元件將填充具有堆棧跟蹤的日誌。 CQ-4242315 的 Hotfix

**DAM - 一般**

* 關閉資產的詳細資訊視圖將返回不正確的搜索結果頁。 CQ-4240960 的 Hotfix
* (Camera Raw)缺少影像調整選項。 CQ-4246121 的 Hotfix
* IndexOutOfBoundsException:OOTB資產修改報表。 CQ-4239744 的 Hotfix
* 從報告csv中刪除信任分數。 CQ-4241491 的 Hotfix
* 連結共用電子郵件傳遞中斷，無「管理員」發件人。 CQ-4240357 的 Hotfix
* 修復IT故障。 CQ-4249891 的 Hotfix

**大壩 — Brand Portal**

* 資產屬性僅列出第一個頁籤上的3個屬性，其餘所有頁籤都顯示為空。 CQ-4242503 的 Hotfix
* 檔案類型和檔案大小謂詞在已發佈的搜索表單中不可用。 CQ-4242026 的 Hotfix
* 在目錄謂語中搜索應過濾出/未在搜索篩選器中顯示。 CQ-4241386 的 Hotfix
* 取消發佈後，應存在預設搜索。 CQ-4241383、CQ-4241113
* 發佈到品牌門戶的手勢對影像預設不起作用。 CQ-4241074 的 Hotfix
* 發佈到Brand Portal不為收藏工作。 CQ-4241122、CQ-4246558

**DAM - DM 用戶端**

* 升級到6.4會刪除以前建立的視頻編碼配置檔案。 CQ-4244067 的 Hotfix
* Alt Text屬性在Dynamic Media元件中斷開。 CQ-4244081 的 Hotfix
* (DMS7)在中編輯遠AEM程集在Scene7不被覆蓋。 CQ-4243430 的 Hotfix
* 6.4 SP1的驗證基於DM Hybrid。 CQ-4244623 的 Hotfix
* (DMS7-UA)按一下已發佈視頻資產的「嵌入」按鈕時，似乎不會發生任何情況。 「嵌入」對話框應顯示HTML代碼。 CQ-4245237 的 Hotfix
* (DM Hybrid)已發佈視頻資產或混合媒體集的複製URL獲取&quot;`[object Object]`的子菜單。 CQ-4245236、CQ-4245451
* (DMHybrid)視頻的「詳細資訊視圖」頁不包含視頻資產顯示的預覽，並向控制台輸出錯誤消息。 CQ-4244320 的 Hotfix
* 對we.retail內容進行自動S7編碼。 CQ-4242253 的 Hotfix
* 預升級視頻處理預設不能添加新的視頻編碼預設，也不能編輯現有的編碼預設。 CQ-4240407 的 Hotfix
* 「升級前影像預設」在「格式副本」頁面上顯示為「未發佈」，不會生成URL。 CQ-4240406 的 Hotfix
* (CSS)顯示資產 — 但使用的查看器是預設的，而不是OOTB查看器。 CQ-4239839 的 Hotfix
* 已禁用清除步驟掛起手動執行和使用私有珊瑚類。 CQ-4239729 的 Hotfix
* 影像查看器正在生成錯誤，無法顯示正確的智慧裁剪。 CQ-4237564 的 Hotfix
* /etc下的舊預設似乎已斷開，並且在保存時未遷移到/conf下的位置。 CQ-4237416 的 Hotfix
* OOB VideoViewer 5.8.x中的回歸 — 查看器向右展開iframe，從而中斷頁面佈局。 CQ-4235465 的 Hotfix
* (DMS7)對於尚未發佈的影像，智慧裁剪格式副本URL和嵌入按鈕處於活動狀態。 CQ-4233696 的 Hotfix
* (DMHybrid)恢復以前的裁剪/旋轉特徵。 CQ-4239489 的 Hotfix
* 在卡視圖中預覽視頻時，播放按鈕不會切換為暫停。 CQ-4238592 的 Hotfix
* 執行「選擇加入」升級時，不會將YouTube配置從其舊位置移動/複製到新位置。 CQ-4238590 的 Hotfix
* 「DropTwo OOTB AVS視頻處理配置檔案」列在「資料夾」屬性下，只有一個包含已定義的編碼。 CQ-4238096 的 Hotfix
* (DMS7)智慧裁剪：詳細資訊視圖：「URL」按鈕標籤為「複製」按鈕以用於重新編輯。 CQ-4237804 的 Hotfix
* 即使執行curl命令後，查看器預設清單頁仍為空。 CQ-4243246 的 Hotfix
* 已禁用清除步驟掛起手動執行和使用私有珊瑚類。 CQ-4239729 的 Hotfix
* 「視頻報告詳細資訊」頁面不顯示視頻資產。 CQ-4246208 的 Hotfix

**DAM - DMS服務**

* (DMS7)雲配置：更新到SP1後，無法將新內容與Scene7同步。 CQ-4244437 的 Hotfix
* (DMHybrid)顏色配置檔案和目錄設定未在debug_info=catalog調用中註冊。 CQ-4242346 的 Hotfix
* 將顏色配置檔案添加到交付伺服器上的客戶設定。 CQ-4241818、CQ-4241819
* (DMHybrid)6.3後(&amp;gt)6.4升級，目錄設定被移動到不正確的節點。 CQ-4239974、CQ-4239975
* (DMHybrid)圖示視圖預設指令碼不建立修改目錄設定所需的節點。 CQ-4240076 的 Hotfix
* 當使用「格式」下拉選擇並選擇PNG或JPG格式時，下載的檔案將顯示為比原始資產過飽和且較深。 CQ-4240073 的 Hotfix
* (DMS7)刪除MIME類型映射：image_x-eps。 CQ-4240394 的 Hotfix
* (DMS7)挖空後台的上載參數不會傳遞ipsApiService.log，因此，不能工作。 CQ-4240686 的 Hotfix
* 升級在6.3到6.4實例中建立的影像處理配置檔案會中斷「裁剪類型」屬性。 CQ-4237739 的 Hotfix
* (Dynamic Media)在smartcrop資料夾外上傳常規資產失敗。 CQ-4237670 的 Hotfix
* 將「自適應視頻編碼」配置檔案名稱的配置檔案回退代碼調整為「Adaptive_Video_Encoding」。 CQ-4237666 的 Hotfix
* EmbedXMP 資料一律對 Ptiff 產生程序設為「作用中」。CQ-4234498 的 Hotfix
* CMYK影像格式副本的飽和度不正確。 CQ-4235470 的 Hotfix
* 映像伺服器設定在複製日誌標籤成功時不會複製到交付中。 CQ-4239480、CQ-4239046
* (DMS7)無法使用對雲配置的舊/新引用建立集。 CQ-4238078 的 Hotfix
* Scene7工作流步驟只讀取名稱和說明中的Scene7，但不明確DAM更新工作流中的工作流步驟。 CQ-4237865 的 Hotfix

**DAM — 智慧標籤**

* 已介紹 [增強的智慧標籤](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/enhanced-smart-tags.html)。 NPR-21951

**Forms**

透過附加套件和發行版本隨附的其他修補安裝程式來提供 AEM Forms 修正。如需詳細資訊，請參閱 AEM Forms 發行版本。

AEM Forms 的關鍵重點為：

* AEM Forms介紹 [事務處理報告功能](https://docs.adobe.com/content/help/en/experience-manager-64/forms/transaction-reports/transaction-reports-overview.html) 跟蹤並保持已提交表單、已處理文檔和您的AEM Forms部署中已呈現文檔等事務的計數。 它提供了產品使用情況的洞察力，並幫助業務用戶瞭解數字處理量。
* 已啟用對XML表單的PDF/UA支援。
* 已為Clientlib添加allowProxy = true **aemfd.ccm.channel.contentpage**
* 更新代碼，使高級標題搜索為包含而不是相等。
* 更新到Continuous Integration Machine上的新版本的Node Package Manager(NPM)。

**Forms 附加元件套件**

**後端整合**

* 當為可選欄位提供空值時，將生成錯誤。 NPR-24397
* 當元素具有全局命名空間以外的其他命名空間時，WSDL調用失敗。 NPR-24281
* (FDM WSDL)獲取DermisException:屬性類型陣列的情況下，清單資料除外。 NPR-24265
* (FDM WSDL)獲取DermisException:java.lang.exception:createSOAPParam:無效參數。 NPR-24264
* （FDM客戶端SDK）無法測試前/後預處理器和自定義提交操作。 CQ-4238469 的 Hotfix
* 修復Dermis中的Javadoc問題。 CQ-4244250 的 Hotfix
* Web服務描述語言(WSDL)中的增強輸入。 CQ-4244133 的 Hotfix
* 對WSDL進行基本身份驗證測試時，在6.3和AEM6.4中對於相同配置會產AEM生不同錯誤。CQ-4244132修補程式
* 請求在client-sdk和javadocs中包括ValueUtil。 CQ-4242803 的 Hotfix
* （FDM雲配置）無法從雲配置配置基於SOAP的身份驗證。 CQ-4238462 的 Hotfix
* Dermis — 在Javadoc中添加缺少的包。 CQ-4242815 的 Hotfix
* WSDLInvokerParams，將包含在Forms附加客戶端sdk中。 NPR-23381：CQ-4240233 的 Hotfix

**調適型表單**

* 文檔(IC)格式副本應使用「事務記錄服務」作為事務記錄。 CQ-4245333 的 Hotfix
* 執行UAT5時，驗證階段生成的pdf缺少條目。 CQ-4243184 的 Hotfix
* TestguideContext的深度副本大小寫。 CQ-4242924 的 Hotfix
* 在最新升級的伺服器上執行UAT3時缺少校樣類型欄位。 CQ-4243120 的 Hotfix
* 在已升級的伺服器上，提交的表單缺少升級前伺服器上存在的「省/市/區」和「國家/地區」值。 CQ-4241444 的 Hotfix
* (ExpressionEditor)在提交表單期間導航到「驗證」階段時出錯。 CQ-4241384 的 Hotfix
* 已提交表單的預升級和升級伺服器的驗證階段中缺少值。 CQ-4241896 的 Hotfix
* 退出並保存頁面底部的按鈕無效。 CQ-4240112 的 Hotfix
* 升級後的設定缺少聯繫人號碼。 CQ-4239870 的 Hotfix
* 下 `ACTION TAKEN` 「爭議類型」頁籤中的「支援我的索賠的附加文檔」中包含「已保存」的其他欄位證明類型。 CQ-4239873 的 Hotfix
* 在verifyPdf階段遇到「getDataAPI中出錯」錯誤。 CQ-4239865 的 Hotfix
* 作者和發佈實例的遷移日誌中出錯。 CQ-4239365 的 Hotfix
* 作者和發佈實例的遷移日誌中出錯。 CQ-4239635 的 Hotfix
* 錯誤日誌中的反序列化錯誤，如「不允許對sun.util.calendar.ZoneInfo類進行反序列化」，在提交自適應表單後記錄。 CQ-4240419 的 Hotfix
* 未在Mobile格式副本中填充狀態欄位。 CQ-4240597 的 Hotfix
* 從反陣列清單中刪除模板中元件的引用用法。 CQ-4239217 的 Hotfix
* HTML5數值框設定為浮動或十進位，在不同瀏覽器中提供不同的驗證結果。 NPR-23528：CQ-4244097 的 Hotfix
* （影像上載）影像未在DOR預覽中顯示。 CQ-4243178 的 Hotfix
* JEE伺服器在嘗試提交帶有「電子郵件PDF」和「包括附件」的Adaptive Form時出錯。 CQ-4239894 的 Hotfix
* 運行時不使用表/面板繪製圖表。 CQ-4240010 的 Hotfix
* 自適應表單提交不工作，並且由於提交失敗而更改事務計數。 CQ-4246125 的 Hotfix
* （影像選擇）記錄選項的文檔不可見。 CQ-4236976 的 Hotfix
* 模板編輯器UI不穩定。 CQ-4241497 的 Hotfix
* AF不使用側面板的assets頁籤顯示，而使用窗體元件屬性對話框的瀏覽選項AEM顯示。 CQ-4236751 的 Hotfix
* 為表單轉換生成的工作流ID應在生成的自適應表單中可用。 CQ-4240014 的 Hotfix
* 無法選擇模板以在Direct Upgrade上的站點中建立頁：生命週期到6.4伺服器。 CQ-4241300 的 Hotfix

**組合器服務**

* 在匯編程式服務中記錄事務。 CQ-4245018、CQ-4245017、CQ-4245016的修補程式。
* 使用DDX完成PDF/A轉換時，不報告事務。 CQ-4246039 的 Hotfix

**Forms經理**

* FM CREATE按鈕清單，按字母順序排序。 CQ-4242307 的 Hotfix

**表單入口網站**

* 在升級前伺服器上保存的草稿在升級後伺服器上未正確開啟。 CQ-4243303 的 Hotfix
* 對於adobe-formsmanager-core-module，版本更新為7.1。 CQ-4245753 的 Hotfix
* 在升級前伺服器上保存的草稿在升級後伺服器上未正確開啟。 CQ-4243303 的 Hotfix
* 附件方案在替換/添加/刪除新實例/草稿相同實例中的附件時會中斷。 CQ-4243165 的 Hotfix
* 從資料庫查詢中檢索的草稿計數大於門戶中存在的草稿計數。 CQ-4241489 的 Hotfix
* 升級前伺服器上的Forms未提交。 CQ-4241490 的 Hotfix
* 儘管提交消息成功，但在提交頁籤中UI中顯示的表單仍處於未提交狀態。 CQ-4241487 的 Hotfix
* guideContext應通過深度複製欄位來形成，因為guideContext包含其本身是對象的customPropertyMap。 CQ-4240126 的 Hotfix
* 嘗試保存表單時出錯。 CQ-4240763 的 Hotfix
* 保存和提交的表單的條目正在以crx/de填充，儘管我們在Forms門戶草稿和提交配置中提供了資料庫配置。 CQ-4240726 的 Hotfix
* (Search &amp; Lister)高級搜索標題固定值應包含而非相等。 CQ-4245499 的 Hotfix

**行動 Forms**

* 日期欄位在MobileForms重疊。 CQ-4242256 的 Hotfix
* MobileForms的表單提交應使用事務記錄服務記錄為事務。 CQ-4246166 的 Hotfix
* 應使用事務記錄服務將表單提交記錄為事務處理。 CQ-4246165 的 Hotfix

**AEM Forms 應用程式**

* (Windows App)無法呈現表單。 CQ-4238005 的 Hotfix

**工作流OSGI**

* 工作流分配任務中的事務記錄。 CQ-4244440 的 Hotfix
* （FDM步驟）當在流程步驟和fdm步驟之間插入「分配任務」步驟時，無法使用工作流元資料中的值。 CQ-4241472 的 Hotfix
* 指派任務在OSGI工作流中的Forms整合中不起作用。 NPR-23709：CQ-4243700 的 Hotfix
* （工作流模型編輯器）某些工作流模型無法通過ClassicUI WF模型編輯器進行編輯。 CQ-4241151 的 Hotfix

**多渠道文檔**

* 模板中的日期欄位與IC創作中的子表單重疊。 CQ-4240110 的 Hotfix
* 在IC Web頻道創作中，不應允許刪除或上下移動標題。 CQ-4243358 的 Hotfix
* （IC編輯器）表元件的預設行設定為1。 CQ-4244848 的 Hotfix
* 目標區域即使在內容被拖放到其上後仍然可見。 CQ-4244534 的 Hotfix
* Web通道無法識別文本文檔片段中的制表符空間。 CQ-4244481 的 Hotfix
* （打印通道）文檔(IC)格式副本應使用事務記錄服務記錄為事務。 CQ-4245335 的 Hotfix
* （Web通道）文檔(IC)格式副本應使用事務記錄服務記錄為事務。 CQ-4245334 的 Hotfix
* 文檔容器搜索或資料模型樹搜索必須與資產篩選器搜索統一。 CQ-4242305 的 Hotfix
* （文檔片段）縮進屬性按無法理解的單位數縮進文本。 CQ-4241082、CQ-4240643
* （IC編輯器）在「資產」頁籤下列出的文檔片段磁貼上的「編輯片段」表徵圖不容易發現和理解。 CQ-4241047 的 Hotfix
* 允許匿名訪問IC匿名無法訪問的客戶端庫。 CQ-4245588 的 Hotfix
* （Web通道）資料在Web預覽中的任何表中都未解析，顯示為空。 CQ-4244476 的 Hotfix
* 表頭在自動生成時在Web通道中顯示為變數。 CQ-4244242 的 Hotfix
* （IC編輯器）IC中使用的文檔片段的內容應自動重新調整大小以適合目標區域的寬度。 CQ-4244094 的 Hotfix
* 中心頂部顯示的頻道名稱必須與WEB/PRINT的IC標題一致。 CQ-4242498 的 Hotfix
* 文本編輯器資料對象面板應僅列出頂級實體，CQ-4244121修補程式
* 在編輯器中添加新元件時未指定預設名稱。 CQ-4244691 的 Hotfix
* 在所有Web通道元件中添加Colspan配置。 CQ-4244946 的 Hotfix
* 佈局片段表寬度屬性未在信函或客戶通信打印通道中重置和處理。 CQ-4241574 的 Hotfix

**通信管理**

* 編輯包含佔位符的文本資產後從字母模板中刪除的標題。 NPR-24196
* XDP檔案在上載和用作字母模板的佈局時無法預覽或編輯模板。 NPR-24143：CQ-4244407 的 Hotfix
* 預設情況下，在清單片段中選擇分配選擇。 CQ-4240097 的 Hotfix
* 條件編輯器 — 預設情況下應啟用多個結果評估。 CQ-4240096 的 Hotfix
* 從「清單」中刪除的影像仍顯示預覽中的影像。 CQ-4239909 的 Hotfix
* 條件模組上的規則集被設定為所有模組的「預設」。 CQ-4239878 的 Hotfix
* 資料字典建立失敗，出現「未知JCR異常」錯誤。 CQ-4244122 的 Hotfix
* 6.3內容JavaDocs中的差距。 CQ-4213586 的 Hotfix

**Forms - JEE 安裝程式**

**核心**

* (HTML工作區)名稱中帶括弧符號的應用程式缺少跟蹤詳細資訊。 NPR-23402

**PDFG 服務**

* PDFG服務中的事務記錄。 CQ-4244951、CQ-4244586
* 通過通過單個API調用有選擇地解嵌入字型來減少PDF。 NPR-23287
* 升級時PDFG配置更新AEM問題。 CQ-4241176 的 Hotfix
* PDFUtility服務中的事務記錄。 CQ-4245014 的 Hotfix

**處理程序管理**

* (HTML 工作區) 程序起始點沒有依照字母順序排列。CQ-4239629 的 Hotfix
* (HTML工作區)在首次開啟草稿時準備兩次資料調用。 CQ-4243280 的 Hotfix
* (HTML工作區)關閉窗體時觸發準備資料進程。 CQ-4239456 的 Hotfix
* 在兩個任務之間遍歷時，工作空間掛起。 CQ-4237125 的 Hotfix

**Workbench**

* 管理操作配置檔案當預設呈現過程配置設定為HTML時，準備資料過程失敗。 CQ-4244292 的 Hotfix

**Forms設計師**

* 為透過 Designer 和 Output Service 產生的 XML 表單新增 PDF/UA 支援。NPR-23022
* 從 Designer 另存為 PDF 時，在 Designer 中定義的內嵌超連結沒有受到標記，且沒有替代文字。NPR-23023

**包含 Feature Pack**

**資產**

* 已添加增強智慧標籤的功能。 有關詳細資訊，請參見 [增強的智慧標籤](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/enhanced-smart-tags.html)。 NPR-21951：CQ-4234883 的 Hotfix
* 介紹了AEM Assets的InDesign。 有關詳細資訊，請參見 [AEM Assets在InDesign中的參考](/help/assets/managing-linked-subassets.md)。 NPR-23386

**網站**

* （頁面創作）影像編輯器增強。 有關詳細資訊，請參見 [影像編輯器](https://docs.adobe.com/content/help/en/experience-manager-64/developing/components/image-editor.html)。 NPR-24267：CQ-4245502 的 Hotfix

**包含的 OSGI 套件組合和內容套件**

下列文字記錄 CFP 中包含的 OSGI 套件組合和內容套件清單。

AEM 6.4.1.0 中包含的 OSGi 套件組合清單

[取得檔案](assets/6_4_1_0_bundle-list.txt)

AEM 6.4.1.0 中包含的內容套件清單

[取得檔案](assets/6_4_1_0_content-package-list.txt)

### 安裝6.4.8.0 {#install}

#### 設定要求 {#setup-requirements}

<!--

>[!NOTE]
>
>For successful installation of AEM 6.4.6.0 on the instance, it is strongly recommended to upgrade the version of com.adobe.granite.oak.s3connector to 1.8.4 for the customers who are on the older version of s3 connector.
>The process of upgrading the com.adobe.granite.oak.s3connector is available at [https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html](https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html).
>Download the latest version of com.adobe.granite.oak.s3connector from: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

-->

>[!CAUTION]
>
>對於在6.4上安裝功能包AEM的客戶。Adobe提供的可選功能包與發行版和Service Pack有依賴關係。 如果您安裝了任何功能包，請與客戶AEM保護團隊聯繫，以驗證這些功能包與此Service Pack AEM 6.4的相容性。

* AEM  AEM6.4.8.0要求6.4。有關詳細資訊，請參閱 [升級文檔](../sites-deploying/upgrade.md)。
* Service Pack下載可在 [軟體分發門戶](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 下載。
* 在具有MongoDB和多個實例的部署中，使用包管理AEM器將6.4.8.0安裝到其中一個「作者」實例上。
* 在安裝Service Pack之前，請確保對實例執行快照或新AEM備份。
* 在安裝前重新啟動實例。 雖然只有在實例仍處於更新模式時才需要這樣做（這是從早期版本更新實例時需要這樣做），但通常建議如果實例運行較長時間。

>[!NOTE]
>
>Adobe不建議刪除或卸載AEM6.4.8.0軟體包。

### 通過包管理器安裝Service Pack {#install-the-service-pack-via-package-share}

執行以下步驟在現有6.4實例上安AEM裝Service Pack:

1. 從軟體分發下載包。

1. 在AEM中，登錄到包管理器並添加下載的AEM6.4.8.0包。 選擇上載的包，然後按一下 **[!UICONTROL 安裝]**。

>[!NOTE]
>
>**在安裝6.4.8.0時，有時會在Package Manager UI上出現不成熟的對話框**
>
>因此，建議在訪問實例之前等待錯誤日誌穩定。 在確保安裝成功之前，用戶必須等待與卸載更新程式包相關的特定日誌。 通常在Safari上發生，但在任何瀏覽器上都可能偶爾發生。

### 自動安裝 {#auto-installation}

有兩種方法可自動將AEM6.4.8.0安裝到正在運行的實例中：

答：將包放入……*/crx-quickstart/install* 資料夾。 套件便會自動安裝。

B使用 [包管理器中的HTTP API](/help/sites-administering/package-manager.md)  — 確保使用 `cmd=install&recursive=true`  — 因此已安裝嵌套的軟體包。

>[!NOTE]
>
>AEM 6.4.8.0不支援Bootstrap安裝。

### 驗證安裝 {#validate-install}

1. 「產品資訊」頁(*/system/console/ productinfo *)現在應在「已安裝產品」下顯示更新的版本字串「Adobe Experience Manager，版本6.4.8.0」。
1. 在 OSGI 控制台 (使用 Web 控制台：/system/console/bundles) 中，所有 OSGI 套件組合均為「作用中」或「片段」。
1. OSGI捆綁包org.apache.jackrabbit.oak-core版本1.8.17或更高版本(使用Web控制台：/system/console/bundles)。

要確定與此版本的AEM Sites和資產一起運行的經認證的平台，請參見 [技術要求](../sites-deploying/technical-requirements.md)。

>[!NOTE]
>成功安裝軟體包時，會出現一條>資訊性消息，指示內容>軟體包已成功安裝，如 **&quot;Content Package AEM-6.4-Service-Pack-7已成功安裝。&quot;**

### 更新Dynamic Media查看器(5.10.1) {#update-dynamic-media-viewers}

<p id="Dynamic">AEM 6.4.8.0包含新版本的Dynamic Media查看器(5.10.1)，它允許在「影像預設」頁面上檢查重複名稱。 建議Dynamic Media客戶運行以下命令，以將框查看器預設定調出為最新狀態。

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

將新查看器預設複製到/conf位置。

### 安AEM裝窗體載入項包 {#install-aem-forms-add-on-package}

#### 安AEM裝窗體載入項 {#installaemformsaddon}

>[!NOTE]
>
>如果你不用AEM Forms，跳過。 AEM Forms的修復通過單獨的附加軟體包提供。

>[!NOTE]
>
>AEM 6.4.8.0包括的 [AEM Forms相容性包](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)。 如果您使用的是舊版的AEM Forms相容性軟體包並更新到AEM6.4.8.0 ，請在安裝Forms附加軟體包後安裝最新版本的AEM Forms相容性軟體包。

1. 確保已安裝AEMService Pack。
1. 下載列於的相應表單載入項包 [AEM Forms釋放](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) 作業系統。
1. 按中所述安裝窗體載入項包 [安AEM裝窗體載入項包](https://docs.adobe.com/content/help/en/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package)。

### 安裝AEM FormsJEE安裝程式 {#install-aem-forms-jee-installer}

>[!NOTE]
>
>如果JEE上沒有使用AEM Forms，則跳過。 AEM Forms JEE 中的修正是透過單獨的安裝程式提供。

有關為AEM FormsJEE和部署後配置安裝累積安裝程式的資訊，請參見 [AEM FormsJEE修補程式安裝程式0015](https://helpx.adobe.com/aem-forms/quick-fixes/6-4/jee-patch-0015.html)。

#### NPR-21268 所需的配置設定 {#configuration-settings-required-for-npr}

如果您使用的是Classic(old)UI並且已使用它建立了元資料模板，請按照步驟運行JMX指令碼以保留它們 — 

1. 轉到/system/console/jmx。
1. 按一下「遷移元資料模板」。
1. 按一下「migrateMetadataTemplatesAtPath」，並提供要保留元資料模板的資料夾路徑。

#### NPR-24536 所需的配置設定 {#configuration-settings-required-for-npr-1}

預設情況下，使用者認領任務時，不會重新整理其他使用者的共用佇列計數。為此，我們引入了一項新屬性。請依照下列步驟操作，在您的 AEM 執行個體上設定此屬性：

1. 前往「管理員 UI -> 服務 -> 工作區 -> 全域管理」。
1. 匯出全域設定。
1. 在下載的XML檔案中，添加標籤 &lt;client_taskspollinginterval>10&lt;/client_taskspollinginterval> 這裡，10是示例值（秒）。 您可以視情況修改此值。
1. 儲存檔案。
1. 返回「管理員 UI -> 服務 -> 工作區 -> 全域管理」。
1. 在「匯入全域設定」區段中匯入該 xml 檔案。
1. 這時您可以登出系統並重新登入。
1. 系統會為工作區中的其他使用者開始重新整理共用佇列的計數。
1. 若要關閉輪詢，請將值變更為 0，然後再次匯入 XML 檔案。

### Uber Jar {#uber-jar}

Uber AEM Jar for  6.4.8.0在 [Adobe公共Maven儲存庫](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.4.8/)。

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
| 資產 | 管理子元件的標籤操作 | 無替換 | AEM6.4.2.0 |
| Assets 與 Adobe Creative Cloud 整合 | AEM 6.2 引入了 [AEM 對 Creative Cloud 資料夾共用](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html)功能，作為讓 Creative 使用者存取 AEM 資產的方式。Creative Cloud 應用程式推出的新功能 Adobe Asset Link 提供了更優異的使用者體驗，以及更強大的存取功能，可直接從 Photoshop、InDesign 和 Illustrator 中存取 AEM 的資產。 Adobe 將不會再對資料夾共用功能提供近一步的增強項目。儘管該功能已包括AEM在內，但強烈建議客戶使用更換。 | Adobe資產連結或案頭應用。 如需更多資訊，請參閱 [AEM Creative Cloud 整合](/help/assets/aem-cc-integration-best-practices.md)文章。 | AEM6.4.4.0 |

### 已知問題 {#known-issues}

* 安裝過程中可能顯示以下錯誤和警告：

   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` :等待註冊表更改完成註銷時超時。
   * `com.adobe.granite.maintenance.impl.TaskScheduler` 未在花崗岩/操作/維護中找到維護窗口
   * `com.adobe.cq.com.adobe.cq.ui.commons bundle com.adobe.cq.com.adobe.cq.ui.commons:1.2.28 (204)[com.adobe.cq.ui.wcm.commons.internal.servlets.rte.RTEFilterServletFactory(573)]`:unbindAmpendment方法引發了異常(java.lang.IllegalStateException:服務已註銷)。
這些錯誤不需要任何操作，因為它們不影響您的實AEM例。

### 已解決的問題 {#resolved-issues}

**AEM6.4.4.0**

* 在導入/導出元資料時未發現找到資源錯誤。 CQ-4253263
* 在頂部應用後，無法編輯任6.4.3.0影像元件和6.4.2.0。CQ-4260316和CQ-4260441要解決此問題：
   * 轉到包管理器
   * 重新安裝包&quot;cq-ui-wcm-admin-content-1.0.1004.zip&quot;
   * 重新編譯所有JSP `(http://<AEM HOST>:<AEM PORT/system/console/slingjsp)` 或重新啟動實例。

### 包含的 OSGi 套件組合和內容套件 {#osgi-bundles-and-content-packages-included}

以下文本文檔列出了6.4.8.0中包括的OSGi捆綁包和內容AEM包。

AEM 6.4.8.0 中包含的 OSGi 套件組合清單

[取得檔案](assets/6.4.8.0_osgi_bundles.txt)

AEM 6.4.8.0 中包含的內容套件清單

[取得檔案](assets/6.4.8.0_content_packages.txt)

### 實用資源 {#helpful-resources}

* [AEM 6.4 發行說明](../release-notes/release-notes.md)
* [AEM 產品頁面](https://www.adobe.com/solutions/web-experience-management.html)
* [AEM 6.4 檔案](https://helpx.adobe.com/tw/support/experience-manager/6-4.html)
* 訂閱 [Adobe 優先產品更新](https://www.adobe.com/tw/subscription/priority-product-update.html)

### 受限站點 {#restricted-sites-new}

這些站點僅可供客戶使用。 如果您是客戶，需要訪問，請與Adobe客戶經理聯繫。

* [產品下載，網址為licensing.adobe.com](https://licensing.adobe.com/)。
* 產品更新、修補程式和包，以獲得 [軟體分發](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)。
* [客戶支援(通過Admin Console)](https://adminconsole.adobe.com/)。 有關詳細資訊，請參見 [新Adobe客戶支援體驗](https://docs.adobe.com/content/help/en/customer-one/using/home.html)。

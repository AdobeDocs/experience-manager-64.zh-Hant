---
title: AEM Sites發行說明
seo-title: AEM Sites
description: Adobe Experience Manager 6.4 Sites的發行說明。
seo-description: Adobe Experience Manager 6.4 Sites的發行說明。
uuid: 593928ec-5d1a-4a88-bd73-897421c5984a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 40225441-7cfe-4395-ac71-60504b42e764
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 0%

---


# AEM Sites發行說明{#aem-sites-release-notes}

## 網站 {#sites}

如需AEM Sites 6.4增強功能的詳細資訊，請參閱下列內容：

### 站點管理{#site-administration}

* 新的內容樹狀結構可快速導覽網站階層。 結合清單檢視，可還原Classic UI互動模型以瀏覽網站。
* 已改善卡片中的捲動和大型檔案夾的清單檢視。
* 改善與搜尋結果的互動——返回按鈕可還原先前的搜尋結果。
* 其他鍵盤快速鍵，用於大多數常見動作，例如開啟特定邊欄、編輯、移動和刪除頁面，或開啟屬性。
* 可停用鍵盤快速鍵（在「偏好設定」中啟用／停用）。
* 在7天後停止顯示所有UI相對時間戳記（在「偏好設定」中設定預設值）。

### 頁面編輯器{#page-editor}

* 更新裝置清單以進行回應式網站預覽，現在包括Apple iPhone 8、8 Plus和X以及Samsung S7
* 將範本設計資訊的預設位置從/etc/design移開，以支援/conf中的網站特定設定。 從舊版AEM升級的客戶可繼續使用/etc/design。

### 元件與範本開發{#component-amp-template-development}

* Project Archetype 13+，請參閱[Github，以取得發行說明](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/releases)。
* HTL 1.3.1版，請參閱[Github以取得發行說明](https://github.com/Adobe-Marketing-Cloud/htl-spec/releases/tag/1.3.1)。
* 核心元件2.0.4+，請參閱[Github，以取得發行說明](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/releases)。
* 樣式系統

   * 新增全新概念，以指派CSS類別至元件，並允許頁面編輯器中的使用者透過UI從樣式子集中選取
   * 新增定義在元件周圍呈現的HTML元素名稱的功能，例如&lt;main>, &lt;ased>

* 版面容器的格線系統，請參閱[Github](https://github.com/Adobe-Marketing-Cloud/aem-responsivegrid)。
* 範本編輯器與原則

   * 原則現在支援每個元件、每個容器、每個範本的樣式系統組態。
   * 改善可編輯元件上範本中定義版面的支援

* 參考網站We.Retail 3.0，請參閱[Github，以取得發行說明](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases)。

>[!CAUTION]
>
>AEM包含jQuery程式庫的1.12.4版，可提供與現有自訂程式碼的最大相容性。 Adobe已針對已知的安全性問題進行修改。

### 內容片段與編輯器{#content-fragments-amp-editor}

* 引入結構化內容模型作為內容片段的基礎

   * 模型編輯器UI
   * 內容片段模型的預先設定資料元素（單行文字、多行文字、數字、布林值、日期與時間、列舉、內容參考、標籤）

* 已改善AEM內容片段編輯器的可用性

   * 檢視所有元素概觀
   * 針對單一元素進行全螢幕編輯
   * 增強的豐富式文字編輯功能（項目清單、編號清單、縮排、超連結、表格、尋找與取代、拼字檢查）

* 新增AEM內容片段的增強輸出選項

   * 新的內容片段元件，做為核心元件的一部分。 [請參閱GitHub上的程式碼。](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/tree/master/extension/contentfragment/content/src/content/jcr_root/apps/core/wcm/extension/components/contentfragment/v1/contentfragment)
   * 透過Sling Model Exporter輸出JSON的Content Services支援

### 體驗片段 {#experience-fragments}

* 引入體驗片段建立區塊，透過將元件分組並允許變數中的簡單參考，以方便在體驗片段變數之間重複使用內容。
* 新增透過參考邊欄將體驗片段新增至翻譯專案的功能
* 新增透過時間軸邊欄使用Experience片段啟動工作流程的功能
* 參考邊欄現在會顯示AEM中使用體驗片段的位置
* 範本位置的設定現在允許作者在全域或資料夾層級定義允許使用的體驗片段範本
* 多面搜尋現在支援進階篩選，例如已發佈／未發佈、匯出至社交媒體和Adobe Target
* 新增將體驗片段匯出至Pinterest或Facebook時的單一社交媒體登入
* 將AEM體驗片段與Adobe Target整合。 將體驗片段同步至Target將在Adobe Target中建立選件，並可與Target的Visual Experience Composer搭配使用，以將其嵌入任何啟用Target的體驗。

### 轉換 {#translation}

* 已增強AEM Translation專案的可用性：

   * 在單一專案中支援多種目標語言
   * 自動提升和刪除翻譯啟動的選項
   * 排程翻譯專案（每日、每週、每月、每年）週期性執行的選項
   * 增強的翻譯項目表徵圖，提供更詳細的狀態資訊

* 引入「反向翻譯記憶庫更新」，在AEM中編輯本機內容後更新第三方翻譯管理系統中的翻譯記憶庫
* 翻譯工作流程現在支援分組語言根目錄
* 新增可指派任意名稱至語言根目錄，並使用JCR屬性來對應至ISO程式碼的功能
* 智慧型翻譯更新現在可識別新增至語言主要分支的頁面
* 在「站點管理員」清單視圖中引入翻譯狀態報告

### 多站點管理(MSM){#multi-site-management-msm}

* 使用Oak索引與記憶體內建索引(LiveCopyIndex)來改善MSM的可擴充性

### 啟動 {#launches}

* 已改善包含大型網站樹狀結構，且有許多啟動作用中的啟動效能
* 已改善具有多個根頁面的啟動自動促銷和發佈功能。
* 修正回應式裝置預覽無法處理在啟動內容中編輯之頁面的問題。

### 內容定位與模擬{#content-targeting-simulation}

* 支援資料夾，以根據網站／內容來組織區段(CQ-94620)
* 將區段的預設位置移至/conf，以便擁有網站／內容特定的區段清單。

### AEM與Adobe Target  {#aem-amp-adobe-target-nbsp}

* 將AEM體驗片段與Adobe Target整合。 將體驗片段同步至Target將在Adobe Target中建立選件，並可與Target的Visual Experience Composer搭配使用，以將其嵌入任何啟用Target的體驗。
* Adobe Target mbox.js 63版現已隨附。 Adobe建議將實作切換為at.js。
* 現已隨附at.js 1.2.2版。 Adobe建議使用動態標籤管理(DTM)或[Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html)，將at.js布建至網站。

### AEM &amp; Adobe Analytics {#aem-amp-adobe-analytics}

* s_code.js H.27.5現已包含在內。 Adobe建議將實作切換為AppMeasurement.js
* AppMeasurement.js 1.8.0現已隨附。 Adobe建議使用動態標籤管理(DTM)或[Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html)，將AppMeasurement.js布建至網站。

## 社群附加元件{#communities-add-on}

請參閱[社群發行說明頁面](/help/release-notes/communities-release-notes.md)

## 畫面附加元件{#screens-add-on}

* 新增支援「畫面播放器」以連線至AEM發佈伺服器，以進行命令與控制和頻道下載（而非直接連線至AEM作者）。
* 新增在「排程」中群組渠道指派的能力
* 頻道指派現在有開始和結束日期
* 「裝置儀表板」現在會顯示播放器外殼和韌體版本
* 「裝置控制面板」清單顯示播放器的連線狀態
* 新增AEM Screens Player的Google Chrome OS支援
* 已新增Microsoft Windows 10 for AEM Screens Player

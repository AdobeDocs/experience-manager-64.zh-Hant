---
title: AEM Sites發行說明
seo-title: AEM Sites
description: Adobe Experience Manager 6.4 Sites專用發行說明。
seo-description: Release notes specific to Adobe Experience Manager 6.4 Sites.
uuid: 593928ec-5d1a-4a88-bd73-897421c5984a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 40225441-7cfe-4395-ac71-60504b42e764
exl-id: 19ec5c00-eae5-4e7f-9dc5-c7a88b06fd2a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1046'
ht-degree: 1%

---

# AEM Sites發行說明 {#aem-sites-release-notes}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## Sites {#sites}

請詳細參閱下列AEM Sites 6.4增強功能：

### 網站管理 {#site-administration}

* 新增內容樹狀結構邊欄，以快速導覽網站階層。 這可結合清單檢視，還原傳統UI互動模型以瀏覽網站。
* 改善大型資料夾的卡片和清單檢視中的捲動功能。
* 改善與搜尋結果的互動 — 返回按鈕可還原先前的搜尋結果。
* 其他鍵盤快速鍵，用於最常見的動作，例如開啟特定邊欄、編輯、移動和刪除頁面，或開啟屬性。
* 可禁用鍵盤快捷方式（在「首選項」中啟用/禁用）。
* 在7天後停止顯示所有UI相對的時間戳記（在「偏好設定」中設定預設值）。

### 頁面編輯器 {#page-editor}

* 更新回應式網站預覽的裝置清單，現在包括Apple iPhone 8、8 Plus和X，以及Samsung S7
* 將範本設計資訊的預設位置從/etc/design移開，以支援/conf中的網站特定設定。 從舊版AEM升級的客戶可以繼續使用/etc/design。

### 元件和範本開發 {#component-amp-template-development}

* 專案原型13+，請參閱 [Github以取得發行說明](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/releases).
* HTL 1.3.1版，請參閱 [Github以取得發行說明](https://github.com/Adobe-Marketing-Cloud/htl-spec/releases/tag/1.3.1).
* 核心元件2.0.4+，請參閱 [Github以取得發行說明](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/releases).
* 樣式系統

   * 新增全新概念，將CSS類別指派給元件，並允許頁面編輯器中的使用者透過UI從樣式子集中選取
   * 新增定義以元件周圍呈現的HTML元素名稱的功能，例如 &lt;main>, &lt;aside>

* 佈局容器的網格系統，請參閱 [Github](https://github.com/Adobe-Marketing-Cloud/aem-responsivegrid).
* 範本編輯器和原則

   * 原則現在支援每個元件、每個容器、每個範本的樣式系統設定。
   * 改善在可編輯元件上的範本中定義版面的支援

* 參考網站We.Retail 3.0，請參閱 [Github以取得發行說明](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases).

>[!CAUTION]
>
>AEM包含jQuery程式庫1.12.4版，可提供與現有自訂程式碼的最大相容性。 Adobe已修改以解決已知的安全問題。

### 內容片段與編輯器 {#content-fragments-amp-editor}

* 導入結構化內容模型作為內容片段的基礎

   * 模型編輯器UI
   * 內容片段模型的預先設定資料元素（單行文字、多行文字、數字、布林值、日期與時間、分項清單、內容參考、標籤）

* 改善AEM內容片段編輯器的可用性

   * 檢視全部元素概觀
   * 單一元素的全螢幕編輯
   * 增強的RTF編輯功能（項目符號清單、編號清單、縮進、超連結、表格、尋找和取代、拼字檢查）

* 新增AEM內容片段的增強輸出選項

   * 新內容片段元件，屬於核心元件的一部分。 [請參閱GitHub上的程式碼。](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/tree/master/extension/contentfragment/content/src/content/jcr_root/apps/core/wcm/extension/components/contentfragment/v1/contentfragment)
   * 透過Sling模型匯出工具支援JSON輸出的內容服務

### 體驗片段 {#experience-fragments}

* 推出體驗片段建置區塊，借由將元件分組，以及允許在變數內輕鬆參考，來促進在體驗片段變異之間重複使用內容。
* 新增透過參考邊欄將體驗片段新增至翻譯專案的功能
* 新增透過時間軸邊欄，使用體驗片段開始工作流程的功能
* 參考邊欄現在會顯示體驗片段在AEM中的使用位置
* 範本位置的設定現在可讓作者在全域或資料夾層級定義允許使用的體驗片段範本
* 多面搜尋現在支援進階篩選，例如已發佈/未發佈、已匯出至社交媒體和Adobe Target
* 新增將體驗片段匯出至Pinterest或Facebook時的單一社交媒體登入
* 將AEM體驗片段與Adobe Target整合。 將體驗片段同步至Target會在Adobe Target中建立選件，可與Target的可視化體驗撰寫器搭配使用，以將其內嵌於任何已啟用Target的體驗中。

### 轉換 {#translation}

* 增強AEM翻譯專案的可用性：

   * 在一個專案中支援多種目標語言
   * 自動促銷和刪除翻譯啟動的選項
   * 排程翻譯專案週期性執行的選項（每日、每週、每月、每年）
   * 增強的翻譯專案圖磚，並提供更詳細的狀態資訊

* 引入了「反向翻譯記憶體更新」，以在AEM中編輯本地內容後更新第三方翻譯管理系統中的翻譯記憶體
* 翻譯工作流程現在支援分組語言根
* 新增將任意名稱指派給語言根，以及使用JCR屬性來對應至ISO程式碼的功能
* 智慧翻譯更新現在可識別新增至語言主分支的頁面
* 在網站管理員清單檢視中導入翻譯狀態報表

### 多站點管理(MSM) {#multi-site-management-msm}

* 使用Oak型索引與記憶體內索引(LiveCopyIndex)，改善MSM可擴充性

### Launch {#launches}

* 已改善包含大型網站樹狀結構以及有許多啟動作用中的啟動的效能
* 改善具有多個根頁面的啟動自動促銷和發佈功能。
* 修正回應式裝置預覽無法搭配在啟動內容中編輯之頁面運作的問題。

### 內容鎖定與模擬 {#content-targeting-simulation}

* 支援資料夾以根據網站/內容組織區段(CQ-94620)
* 將區段的預設位置移至/conf ，以便有網站/內容專用的區段清單。

### AEM與Adobe Target  {#aem-amp-adobe-target-nbsp}

* 將AEM體驗片段與Adobe Target整合。 將體驗片段同步至Target會在Adobe Target中建立選件，可與Target的可視化體驗撰寫器搭配使用，以將其內嵌於任何已啟用Target的體驗中。
* Adobe Target mbox.js版本63現已包含。 Adobe建議將實作切換為at.js。
* 現已納入at.js版本1.2.2。 Adobe建議使用動態Tag Management(DTM)或 [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) 將at.js布建至網站。

### AEM與Adobe Analytics {#aem-amp-adobe-analytics}

* 現已包含s_code.js H.27.5。 Adobe建議將實作切換為AppMeasurement.js
* 現已納入AppMeasurement.js 1.8.0。 Adobe建議使用動態Tag Management(DTM)或 [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) 將AppMeasurement.js布建至網站。

## Communities附加元件 {#communities-add-on}

請參閱 [Communities發行說明頁面](/help/release-notes/communities-release-notes.md)

## Screens附加元件 {#screens-add-on}

* 新增支援Screens播放器以連線至AEM發佈伺服器以執行命令與控制及頻道下載(而非直接連線至AEM作者)。
* 新增在排程中分組管道指派的功能
* 管道指派現在有開始和結束日期
* 「設備儀表板」現在顯示播放器外殼和韌體版本
* 「設備儀表板」清單顯示播放器的連接狀態
* 新增Google Chrome OS對AEM Screens Player的支援
* 新增Microsoft Windows 10 for AEM Screens Player

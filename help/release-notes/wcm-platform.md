---
title: AEM Foundation與存放庫
seo-title: AEM Foundation & Repository
description: Adobe Experience Manager 6.3 AEM平台和存放庫專屬發行說明。
seo-description: Release notes specific to Adobe Experience Manager 6.3 AEM Platform and Repository.
uuid: 147b38d0-cf87-467c-a52d-3399d4af7e6e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: e5dd9d0d-6d67-4430-aeb3-2be91356f624
exl-id: 6f131247-d35e-4298-958f-35b94ff08c58
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 3%

---

# AEM Foundation與存放庫 {#aem-foundation-repository}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 變更清單 {#list-of-changes}

### 存放庫 {#repository}

* Oak Segment Tar MicroKernel

   * 線上修訂清除的快速壓縮模式（尾部壓縮）
   * 提高寫入率
   * 透過JMXBean公開的區段作業統計資料
   * 離線修訂清除的持續時間估計

* Oak Mongo微內核

   * MongoMK的持續修訂清除取代了排程的清除維護

* 改善檔案記錄檔的修訂清除效率
* 請參閱 [Apache Jackrabbit Oak Jira v1.8.0](https://archive.apache.org/dist/jackrabbit/oak/1.8.0/RELEASE-NOTES.txt), [Apache Jackrabbit Oak Jira v. 1.8.1](https://archive.apache.org/dist/jackrabbit/oak/1.8.1/RELEASE-NOTES.txt) 和 [阿帕奇·傑克拉布特·奧克·吉拉訴1.8.2](https://archive.apache.org/dist/jackrabbit/oak/1.8.2/RELEASE-NOTES.txt) 以取得已修正問題的完整概述。

>[!CAUTION]
>
>* 自AEM 6.3以來出現的新版Oak Segment Tar需要移轉存放庫。 如果您從舊版TarMK升級，或想從其他類型的永續性切換新的區段Tar，此步驟為必要步驟。 如需新區段Tar的優點的詳細資訊，請參閱 [移轉至Oak Segment Tar常見問題集](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar).
>


### 搜尋與索引 {#search-amp-indexing}

* 透過oak-run(CLI)增強對建立作業索引的支援：

   * 索引一致性檢查
   * 索引統計
   * 索引配置Im/Export
   * 重新索引

* 降低Lucene相關儲存庫的增長，以全面提高系統效能
* 同步Lucene屬性索引 [（更多資訊）](https://wiki.apache.org/jackrabbit/Synchronous%20Lucene%20Property%20Indexes)
* Index Manager中的「說明查詢」現在支援AEM QueryBuilder語法
* 「索引管理器」現在公開索引度量：大小、上次更新和一致性檢查

### 使用者介面 {#user-interface}

* UI已經過多種增強功能，讓生產力更高，使用更輕鬆。
* 新增內容樹狀結構邊欄，以快速導覽階層。 這會與清單檢視結合，還原傳統UI互動模型。
* 改善大型資料夾的卡片和清單檢視中的捲動功能。
* 改善與搜尋結果的互動 — 返回按鈕可還原先前的搜尋結果。
* 其他鍵盤快速鍵，用於最常見的動作，例如開啟特定邊欄、編輯、移動和刪除項目，或開啟屬性。
* 可禁用鍵盤快捷方式（在「首選項」中啟用/禁用）。
* 在7天後停止顯示所有UI相對的時間戳記（在「偏好設定」中設定預設值）。

>[!CAUTION]
>
>* Adobe不打算對傳統UI進行進一步的增強。 AEM 6.4已包含傳統UI，而從舊版升級的客戶可繼續依原樣使用。 請注意，舊版UI在淘汰時仍完全支援 [了解詳情](/help/sites-deploying/ui-recommendations.md).
>


### 內容發佈 {#content-distribution}

* 改善複製效能以支援發佈大容量資產
* 在發佈傳輸中支援OAuth 2.0驗證
* 改善VLT包的效能

### 監控 {#monitoring}

* 新的「系統概述」提供了與效能相關的所有系統狀態和活動的快照視圖
* 新健康檢查：

   * 檢測大Lucene索引
   * 非同步索引運行狀況
   * 大型 Lucene 索引
   * 查詢效能
   * 查詢周遊限制
   * 已同步時鐘
   * 系統維護 — 修訂清除
   * 系統維護 — DataStore GC
   * 系統維護 — 連續修訂GC

* 使用者現在可以定義status.zip下載的範圍

### 維護 {#maintenance}

* 使用維護任務主動刪除Lucene二進位檔案
* MongoDB的RevisionGC維護任務現在已禁用，以支援「連續修訂清除」，請參閱上面的儲存庫一節。
* 版本清除配置允許保留最低版本數
* 版本清除在維護窗口的末尾停止。 也可以手動啟動和停止，且會隨著下次啟動而逐步繼續。

### 升級 {#upgrade}

* 向後相容性：6.4版中回溯相容的功能，可協助您的自訂程式碼在大多數情況下保持相容，並降低升級工作量。
* 升級複雜性評估：全新模式偵測器工具，可評估升級的複雜度。
* 可持續升級：導入API介面和內容分類，協助您在整個開發週期中，輕鬆遵循最佳實務，以有效率且順暢地升級至下一個版本。
* 存放庫重新調整：大幅重組（主要是/等）以促進更輕鬆的升級並促進實施最佳實務。 [了解詳情。](/help/sites-deploying/repository-restructuring.md)
* 請參閱 [升級檔案](/help/sites-deploying/upgrade.md) 以取得這些功能的詳細資訊。

### 雲端服務 {#cloud-services}

* 許多Cloud Services現在可透過觸控式UI設定；其餘的可在「舊版Cloud Services」卡下設定。
* 網站和資產資料夾可以設定以內容感知方式載入的Cloud Services。

### 安全性 {#security}

* 增強並簡化使用者建立UI，支援多個使用者設定檔。
* 改善使用者大型群組成員資格的效能。

### 專案和工作流程 {#projects-and-workflows}

* 觸控式UI工作流程編輯器，以更簡化的方式管理工作流程模型。
* 支援在維護任務中清除項目任務。

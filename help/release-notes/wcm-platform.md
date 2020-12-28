---
title: AEM Foundation & Repository
seo-title: AEM Foundation & Repository
description: Adobe Experience Manager 6.3 AEM Platform和Repository的發行說明。
seo-description: Adobe Experience Manager 6.3 AEM Platform和Repository的發行說明。
uuid: 147b38d0-cf87-467c-a52d-3399d4af7e6e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: e5dd9d0d-6d67-4430-aeb3-2be91356f624
translation-type: tm+mt
source-git-commit: 966263cc94f44bcad76e7e9ba5c6ecdc93574348
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 2%

---


# AEM Foundation &amp; Repository {#aem-foundation-repository}

## 變更清單{#list-of-changes}

### 存放庫 {#repository}

* Oak Segment Tar MicroKernel

   * 線上修訂清除的快速壓縮模式（尾部壓縮）
   * 改善的寫入率
   * 透過JMXBean公開的區段作業統計資料
   * 離線修訂清除的持續時間估計

* Oak Mongo Microkernel

   * MongoMK的「連續修訂清除」取代計畫的清除維護

* 改善檔案記錄檔的修訂清除效率
* 請參閱[Apache Jackrabbit Oak Jira v. 1.8.0](https://archive.apache.org/dist/jackrabbit/oak/1.8.0/RELEASE-NOTES.txt)、[Apache Jackrabbit Oak Jira v. 1.8.1](https://archive.apache.org/dist/jackrabbit/oak/1.8.1/RELEASE-NOTES.txt)和[Apache Jackrabbit Oak Jira v. 1.8.2](https://archive.apache.org/dist/jackrabbit/oak/1.8.2/RELEASE-NOTES.txt)，以取得修正問題的完整概觀。

>[!CAUTION]
>
>* 自AEM 6.3以來，Oak Segment Tar的新版本需要儲存庫移轉。 如果您要從舊版TarMK升級，或想要從其他永續性類型切換新的區段Tar，此步驟為必要步驟。 如需新區段Tar的優點的詳細資訊，請參閱[移轉至Oak區段Tar常見問答集](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar)。

>



### 搜索和索引{#search-amp-indexing}

* 通過oak-run(CLI)增強對索引操作的支援：

   * 索引一致性檢查
   * 索引統計資料
   * 索引配置Im/Export
   * 重新索引

* 降低與Lucene相關的儲存庫增長，以提高整體系統效能
* 同步Lucene屬性索引[（更多資訊）](https://wiki.apache.org/jackrabbit/Synchronous%20Lucene%20Property%20Indexes)
* Index Manager中的Explain Query現在支援AEM QueryBuilder語法
* Index Manager現在公開索引度量：大小、上次更新和一致性檢查

### 使用者介面{#user-interface}

* UI已做了各種增強功能，讓它更有生產力，也更容易使用。
* 新的內容樹狀結構可快速導覽階層。 這會與清單檢視結合，還原Classic UI互動模型。
* 已改善卡片中的捲動和大型檔案夾的清單檢視。
* 改善與搜尋結果的互動——返回按鈕可還原先前的搜尋結果。
* 其他鍵盤快速鍵，用於大多數常見動作，例如開啟特定邊欄、編輯、移動和刪除項目，或開啟屬性。
* 可停用鍵盤快速鍵（在「偏好設定」中啟用／停用）。
* 在7天後停止顯示所有UI相對時間戳記（在「偏好設定」中設定預設值）。

>[!CAUTION]
>
>* Adobe不打算對Classic UI做進一步的增強。 AEM 6.4包含Classic UI，而從舊版升級的客戶可依現狀繼續使用。 請注意，Classic UI仍完全受支援，但不再提倡[閱讀更多內容](/help/sites-deploying/ui-recommendations.md)。

>



### 內容發佈 {#content-distribution}

* 改進複製效能以支援大容量資產發佈
* 在散發傳輸中支援OAuth 2.0驗證
* VLT包的效能改進

### 監控 {#monitoring}

* 新的「系統概述」提供了所有與效能相關的系統狀態和活動的快照視圖
* New Health Checks:

   * 檢測大Lucene索引
   * 非同步索引健康狀況
   * 大型 Lucene 索引
   * 查詢效能
   * 查詢周遊限制
   * 已同步時鐘
   * 系統維護——修訂清除
   * 系統維護- DataStore GC
   * 系統維護——連續修訂GC

* 使用者現在可以定義status.zip下載的範圍

### 維護 {#maintenance}

* 使用維護任務主動刪除Lucene二進位檔案
* MongoDB的RevisionGC維護任務現在禁用，以利於「連續修訂清除」，請參見上面的「儲存庫」部分。
* 版本清除配置允許保留最低版本數
* 版本清除在維護窗口結束時停止。 它也可以手動啟動和停止，並且會隨著下次啟動而遞增。

### 升級{#upgrade}

* 向後相容性：6.4版中向後相容的功能可協助您的自訂程式碼在大多數情況下仍能相容，並降低升級工作量。
* 升級複雜性評估：全新的圖樣偵測器工具，可評估升級的複雜性。
* 可持續升級：引入API介面和內容分類，協助您在整個開發週期中，輕鬆遵循最佳實務，以有效率且順暢地升級至下一版。
* 儲存庫重組：大幅重組（主要是／等）以促進更輕鬆的升級並促進實施最佳做法。 [閱讀更多資訊。](/help/sites-deploying/repository-restructuring.md)
* 有關這些功能的詳細資訊，請參閱[升級文檔](/help/sites-deploying/upgrade.md)。

### 雲端服務 {#cloud-services}

* 許多雲端服務現在都可透過Touch UI進行設定；其餘則可在舊版雲端服務卡下設定。
* 網站和資產資料夾可以設定Cloud Services，這些服務會以內容感知方式載入。

### 安全性 {#security}

* 增強並簡化使用者建立UI，並支援多個使用者設定檔。
* 已改善使用者大型群組會籍的效能。

### 專案和工作流程{#projects-and-workflows}

* 以Touch UI為基礎的工作流程編輯器，以更簡化的方式管理工作流程模型。
* 支援在維護任務中清除項目任務。


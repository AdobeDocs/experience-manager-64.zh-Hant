---
title: 透過Oak-run Jar建立索引
seo-title: Indexing via the Oak-run Jar
description: 了解如何透過Oak-run Jar執行索引。
seo-description: Learn how to perform indexing via the Oak-run Jar.
uuid: 09a83ab9-92ec-4b55-8d24-2302f28fc2e4
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: c8a505ab-a075-47da-8007-43645a8c3ce5
exl-id: b85fc608-9653-4491-8557-f66a0a7da5ea
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '906'
ht-degree: 1%

---

# 透過Oak-run Jar建立索引{#indexing-via-the-oak-run-jar}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Oak-run支援命令列上的所有索引使用案例，不需從JMX層級操作。 oak-run方法的優點包括：

1. 這是適用於AEM 6.4的新索引工具集
1. 它減少了重新索引的時間，這有益地影響了大型儲存庫的重新索引時間
1. 它正在減少AEM中重新索引期間的資源耗用量，為其他AEM活動帶來更佳的系統效能
1. Oak-run提供帶外支援：如果生產條件不允許在生產實例上運行重新索引，則可以使用克隆的環境進行重新索引，以避免對效能造成嚴重影響。

在下方，您會找到一份使用案例清單，當透過 `oak-run` 工具。

## 索引一致性檢查 {#indexconsistencychecks}

>[!NOTE]
>
>如需此案例的詳細資訊，請參閱 [使用案例1 — 索引一致性檢查](/help/sites-deploying/oak-run-indexing-usecases.md#usercase1indexconsistencycheck).

* `oak-run.jar`快速判斷lucene oak索引是否損毀。
* 在使用中的AEM例項上執行以進行一致性檢查層級1和2是安全的。

![screen_shot_2017-12-14at135758](assets/screen_shot_2017-12-14at135758.png)

## 索引統計資訊 {#indexstatistics}

>[!NOTE]
>
>如需此案例的詳細資訊，請參閱 [使用案例2 — 索引統計資訊](/help/sites-deploying/oak-run-indexing-usecases.md#usecase2indexstatistics)

* `oak-run.jar` 轉儲離線分析的所有索引定義、重要索引統計資訊和索引內容。

* 可在使用中的AEM例項上執行。

![image2017-12-19_9-47-40](assets/image2017-12-19_9-47-40.png)

## 重新索引方法決策樹 {#reindexingapproachdecisiontree}

此圖表是決定何時應使用各種重新索引方法的決策樹。

![oak_-_riendingwithoak run](assets/oak_-_reindexingwithoak-run.png)

## 重新索引MongoMK / RDMBMK {#reindexingmongomk}

>[!NOTE]
>
>如需此案例的詳細資訊，請參閱 [使用案例3 — 重新索引](/help/sites-deploying/oak-run-indexing-usecases.md#usecase3reindexing).

### SegmentNodeStore和DocumentNodeStore的文字預先擷取 {#textpre-extraction}

[文字預先擷取](/help/sites-deploying/best-practices-for-queries-and-indexing.md#how-to-perform-text-pre-extraction) (AEM 6.3已存在的功能)可用來縮短重新索引的時間。 文本預取可與所有重新索引方法結合使用。

視 `oak-run.jar` 索引方法在下圖的「執行重新索引」步驟的兩側會有各種步驟。

![4](assets/4.png)

>[!NOTE]
>
>橘色表示AEM必須位於維護視窗中的活動。

### 使用oak-run.jar為MongoMK或RDBMK線上重新索引 {#onlinere-indexingformongomk}

>[!NOTE]
>
>如需此案例的詳細資訊，請參閱 [重新索引 — DocumentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#reindexdocumentnodestore).

這是重新索引MongoMK（和RDBMK）AEM安裝的建議方法。 不應使用其他方法。

此程式只需對叢集中的單一AEM執行個體執行。

![5](assets/5.png)

## 重新索引TarMK {#re-indexingtarmk}

>[!NOTE]
>
>如需此案例的詳細資訊，請參閱 [重新索引 — SegmentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#reindexsegmentnodestore).

* **冷備考量事項(TarMK)**

   * 冷備無特殊考慮；冷待機實例將照常同步更改。

* **AEM發佈伺服器陣列（AE發佈伺服器陣列應一律為TarMK）**

   * 對於發佈伺服器陣列，必須針對所有OR執行單一發佈上的步驟，然後複製其他伺服器的設定(複製AEM例項時，請採取所有通常的操作);sling.id — 應連結至此處的項目)

### TarMK的線上重新索引 {#onlinere-indexingfortarmk}

>[!NOTE]
>
>如需此案例的詳細資訊，請參閱 [聯機重新索引 — SegmentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestore).

這是導入oak-run.jar新索引功能前所使用的方法。 若要這麼做，請設定 `reindex=true` 屬性。

如果索引的時間和效能影響是客戶可接受的，則可以使用此方法。 中小型AEM安裝通常會採用此方式。

![6](assets/6.png)

### 使用oak-run.jar線上重新索引TarMK {#onlinere-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>如需此案例的詳細資訊，請參閱 [線上重新索引 — SegmentNodeStore -AEM執行個體正在執行](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestoretheaeminstanceisrunning).

使用oak-run.jar線上重新索引TarMK的速度比 [TarMK的線上重新索引](#onlinere-indexingfortarmk) 如上所述。 但是，在維護窗口期間也需要執行；提到窗口將更短，需要執行更多步驟來重新索引。

>[!NOTE]
>
>橙色表示必須在維護期間執行AEM的操作。

![7](assets/7.png)

### 使用oak-run.jar離線重新索引TarMK {#offlinere-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>如需此案例的詳細資訊，請參閱 [線上重新索引 — SegmentNodeStore — 關閉AEM例項](/help/sites-deploying/oak-run-indexing-usecases.md#onlinereindexsegmentnodestoreaeminstanceisdown).

離線重新索引TarMK是最簡單的 `oak-run.jar` 基於重新索引的TarMK方法，因為它需要單一 `oak-run.jar` 註解。 但是，它需要關閉AEM例項。

>[!NOTE]
>
>紅色表示必須關閉AEM的操作。

![8](assets/8.png)

### 使用oak-run.jar進行帶外重新索引TarMK  {#out-of-bandre-indexingtarmkusingoak-run-jar}

>[!NOTE]
>
>如需此案例的詳細資訊，請參閱 [帶外重新索引 — SegmentNodeStore](/help/sites-deploying/oak-run-indexing-usecases.md#outofbandreindexsegmentnodestore).

帶外重新索引可將重新索引對使用中AEM例項的影響降至最低。

>[!NOTE]
>
>紅色表示可能關閉AEM的操作。

![9](assets/9.png)

## 更新索引定義 {#updatingindexingdefinitions}

>[!NOTE]
>
>如需此案例的詳細資訊，請參閱 [使用案例4 — 更新索引定義](/help/sites-deploying/oak-run-indexing-usecases.md#usecase4updatingindexdefinitions).

### 使用ACS在TarMK上建立和更新索引定義確保索引 {#creatingandupdatingindexdefinitionsontarmkusingacsensureindex}

>[!NOTE]
>
>ACS Ensure Index是社區支援的項目，不受Adobe支援。

這可讓您透過內容套件來傳送索引定義，之後內容套件會將重新索引標幟設為 `true`. 這適用於較小的設定，其中重新索引不需要很長時間。

如需詳細資訊，請參閱 [ACS確保索引文檔](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) 以取得詳細資訊。

### 使用oak-run.jar在TarMK上建立和更新索引定義 {#creatingandupdatingindexdefinitionsontarmkusingoak-run-jar}

如果使用非索引重新索引對時間或效能的影響 `oak-run.jar` 方法太高，以下 `oak-run.jar` 基於的方法可用於在基於TarMK的AEM安裝中導入和重新索引Lucene索引定義。

![10](assets/10.png)

### 使用oak-run.jar在MonogMK上建立和更新索引定義 {#creatingandupdatingindexdefinitionsonmonogmkusingoak-run-jar}

如果使用非索引重新索引對時間或效能的影響 `oak-run.jar` 方法太高，以下 `oak-run.jar` 基於的方法可用於在基於MongoMK的AEM安裝中導入和重新索引Lucene索引定義。

![11](assets/11.png)

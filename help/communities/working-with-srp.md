---
title: SRP —— 社群內容儲存
seo-title: SRP —— 社群內容儲存
description: 自AEM Communities 6.1起，使用者產生的內容(UGC)會儲存在儲存資源提供者(SRP)提供的單一共用商店中
seo-description: 自AEM Communities 6.1起，使用者產生的內容(UGC)會儲存在儲存資源提供者(SRP)提供的單一共用商店中
uuid: 651af1d7-70e8-4b56-8c01-871cb397678e
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e975e026-e815-4445-be3e-b1237ed3f6b2
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465
workflow-type: tm+mt
source-wordcount: '922'
ht-degree: 0%

---


# SRP —— 社群內容儲存 {#srp-community-content-storage}

## 簡介 {#introduction}

自AEM Communities 6.1起，使用者產生的內容(UGC)會儲存在儲存資源提供者(SRP)提供的單一共用儲存區中。 有幾種SRP選項可供選擇，例如ASRP、MSRP和JSRP。

與舊版不同，AEM例項中不會反向／正向複製UGC。 SRP可讓UGC直接存取，以便從所有作者和發佈例項建立、讀取、更新和刪除(CRUD)作業，但JSRP除外。

以下是每 [個SRP選項的特性](#characteristics-of-srp-options)，在選擇適當的SRP和基礎部署時，這是決策過程的關 [鍵資訊](topologies.md)。

有關使用UGC的SRP的詳細資訊，請參 [閱儲存資源提供商概述](srp.md)。

>[!NOTE]
>
>SRP僅適用於社群內容。 它不會影響網站內容的儲存位置(節點儲存[)，也不會影響AEM例項之間使用者註冊、使用者設定檔和使用者群組的安全處理(另請參閱](../../help/sites-deploying/data-store-config.md)管理使用者資料 [](#managing-user-data))。

>[!CAUTION]
>
>自AEM 6.1起， [UGC將不複製](#ugc-never-replicated)。
>
>當部署不包含公用商店(例如預設 [JSRP](topologies.md#jsrp) 拓撲)時，UGC只會顯示在輸入AEM發佈或作者例項上。 只有當拓撲包含發佈群集時，UGC才會顯示在任何發佈實例上。

## SRP選項的特點 {#characteristics-of-srp-options}

[ASRP - Adobe儲存資源供應商](asrp.md)\
使用這個選項，UGC會在Adobe代管和管理的雲端服務中遠端保存。 它需要額外的授權，並與帳戶代表合作為該特定授權提供帳戶。

* 需要Adobe提供並支援的相關雲端服務，才能儲存社群內容
* 需要在特定地理位置（美國、歐洲、中東和非洲、亞太地區）選擇資料中心
* 需要透過SRP API以程式化方式存取UGC
* 適用於TarMK發佈農場
* 當沒有投資本地儲存的意圖時適用

>[!NOTE]
>
>ASRP中的貼文（或留言）上傳附件的限制為50 MB。

[MSRP - MongoDB儲存資源提供程式](msrp.md)\
使用此選項，UGC會直接保存在本地MongoDB實例中。

* 需要本機授權安裝MongoDB以儲存社群內容
* 需要本機安裝Apache Solr
* 需要透過SRP API以程式化方式存取UGC
* 適用於現有的TarMK發佈農場
* 適用於MongoMK或RdbMK群集
* 適合期待大量社群內容時

[DSRP —— 關係資料庫儲存資源提供程式](dsrp.md)\
使用此選項，UGC將直接保存在本地MySQL資料庫實例中。

* 需要本地安裝MySQL以儲存社區內容
* 需要本機安裝Apache Solr
* 需要透過SRP API以程式化方式存取UGC
* 適用於現有的TarMK發佈農場
* 適用於MongoMK或RdbMK群集
* 適合期待大量社群內容時

[JSRP - JCR儲存資源提供商](jsrp.md)\
使用預設選項時，沒有共用商店。 UGC僅會與輸入AEM例項的相同JCR儲存庫中持續存在。

* 將社群內容儲存在AEM作者的JCR儲存庫或發佈執行個體的JCR儲存庫中
* 需要透過SRP API以程式化方式存取UGC
* 如果部署了多個發佈實例，則需要發佈群集（TarMK場中的發佈實例之間沒有複製機制）
* 協調僅在發佈環境中執行（作者和發佈之間沒有反向／正向複製機制）
* 通常最適合開發、展示和培訓

## 配置SRP {#configuring-srp}

根據基礎部署指定預設儲存選項是通過儲存配置控制 [台進行的](srp-config.md)。

如需每個選項的設定詳細資訊，請參閱：

* [ASRP - Adobe儲存資源供應商](asrp.md)
* [MSRP - MongoDB儲存資源提供程式](msrp.md)
* [DSRP —— 關係資料庫儲存資源提供程式](dsrp.md)
* [JSRP - JCR儲存資源提供商](jsrp.md)

如果未主動選擇儲存選項，則預設啟用JSRP。

## 其他資訊 {#additional-information}

### 從未複製UGC {#ugc-never-replicated}

在作者環境中，作者會建立頁面內容並將它複製至發佈環境。 當頁面包含互動式AEM社群功能（例如註解、評論、論壇、部落格或QnA）時，會員對發佈例項的互動（在網站訪客中登入）會導致使用者產生的內容(UGC)進入發佈環境。

以前，此社群內容會反向複製至作者例項，以及從作者複製至發佈例項。 使用反向和正向複製來維持AEM例項間的一致性是有問題的。

從AEM Communities 6.1開始，使用UGC的共用儲存空間，已免除複製UGC的需求，如上所述。

在複製網站內容時，不會複製UGC。

### 管理使用者資料 {#managing-user-data}

此外，社群也感興趣的 [*是使用者&#x200B;*、*&#x200B;使用者群組&#x200B;**&#x200B;和使用者個人檔案&#x200B;*](users.md)。 當拓撲為發佈場時，在發佈環境中建立和更新此用戶相關資料時，需要將其提供給其他發佈實例[使用](../../help/sites-deploying/recommended-deploys.md#tarmk-farm)。

自AEM Communities 6.1起，使用Sling散發而非複製來同步使用者相關資料。 有關詳細資訊，請 [訪問用戶同步](sync.md)。

### 升級至AEM Communities 6.2 {#upgrading-to-aem-communities}

在升級至AEM Communities 6.3時，如果需要保留預先存在的UGC，則應根據AEM 5.6.1或AEM 6.0社群是否使用Adobe隨選儲存空間或UGC的內部部署儲存空間來採取步驟。

如需詳細資訊，請 [造訪「升級至AEM Communities 6.3」](upgrade.md)。

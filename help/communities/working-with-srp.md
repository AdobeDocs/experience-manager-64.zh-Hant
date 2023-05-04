---
title: SRP — 社群內容儲存
seo-title: SRP - Community Content Storage
description: 自AEM Communities 6.1起，用戶生成的內容(UGC)儲存在由儲存資源提供商(SRP)提供的單個公共儲存中
seo-description: As of AEM Communities 6.1, user generated content (UGC) is stored in a single, common store provided by a storage resource provider (SRP)
uuid: 651af1d7-70e8-4b56-8c01-871cb397678e
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e975e026-e815-4445-be3e-b1237ed3f6b2
role: Admin
exl-id: 4ff530ae-c676-4259-86f2-a3881843b642
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 0%

---

# SRP — 社群內容儲存 {#srp-community-content-storage}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 簡介 {#introduction}

自AEM Communities 6.1起，使用者產生的內容(UGC)儲存在由儲存資源提供者(SRP)提供的單一通用儲存中。 SRP、MSRP和JSRP等SRP選項可供選擇。

與舊版不同，UGC不會跨AEM執行個體進行反向/正向復寫。 相反地，SRP可讓UGC直接存取，以便從所有製作和發佈執行個體建立、讀取、更新和刪除(CRUD)作業，JSRP則例外。

以下是 [每個SRP選項的特性](#characteristics-of-srp-options)，此為選擇適當的SRP和 [基礎部署](topologies.md).

如需UGC使用SRP的詳細資訊，請參閱 [儲存資源提供程式概述](srp.md).

>[!NOTE]
>
>SRP僅適用於社群內容。 它不會影響儲存網站內容的位置([節點存放區](../../help/sites-deploying/data-store-config.md))，且不會影響在AEM例項之間安全處理使用者註冊、使用者設定檔和使用者群組(另請參閱 [管理使用者資料](#managing-user-data))。

>[!CAUTION]
>
>自AEM 6.1起， [UGC從未複製](#ugc-never-replicated).
>
>當部署不包含公用儲存時，例如預設 [JSRP](topologies.md#jsrp) 拓撲中，UGC只會顯示在輸入UGC的AEM發佈或製作執行個體上。 只有當拓撲中包含發佈群集時，UGC才會顯示在任何發佈實例上。

## SRP選項的特點 {#characteristics-of-srp-options}

[ASRP -Adobe儲存資源提供程式](asrp.md)\
透過此選項，UGC可以遠端保存在由Adobe托管及管理的雲端服務中。 它需要額外的授權，並與客戶代表合作，為該特定授權規定帳戶。

* 需要Adobe提供並支援的相關雲端服務，才能儲存社群內容
* 需要在特定地理位置（美國、歐洲、中東和非洲、亞太地區）選擇資料中心
* 需要透過SRP API以程式化方式存取UGC
* 適用於TarMK發佈伺服器陣列
* 當沒有投資本地儲存的意圖時是合適的

>[!NOTE]
>
>在ASRP(50 MB)中上傳附件至貼文（或留言）的限制。

[MSRP - MongoDB儲存資源提供程式](msrp.md)\
透過此選項，UGC會直接保存在本機MongoDB例項中。

* 需要本地授權安裝MongoDB來儲存社區內容
* 需要本機安裝Apache Solr
* 需要透過SRP API以程式化方式存取UGC
* 適用於現有的TarMK發佈伺服器陣列
* 適用於MongoMK或RdbMK叢集
* 當預期大量社群內容時適用

[DSRP — 關係資料庫儲存資源提供程式](dsrp.md)\
使用此選項，UGC會直接保存在本機MySQL資料庫例項中。

* 需要本地安裝MySQL來儲存社區內容
* 需要本機安裝Apache Solr
* 需要透過SRP API以程式化方式存取UGC
* 適用於現有的TarMK發佈伺服器陣列
* 適用於MongoMK或RdbMK叢集
* 當預期大量社群內容時適用

[JSRP - JCR儲存資源提供商](jsrp.md)\
使用預設選項時，沒有共用商店。 UGC僅與輸入UGC的AEM例項保存在相同的JCR存放庫中。

* 在AEM作者的JCR存放庫或發佈例項的發佈例項中儲存社群內容
* 需要透過SRP API以程式化方式存取UGC
* 若部署了多個發佈執行個體，則需要發佈叢集（TarMK伺服器陣列中的發佈執行個體之間沒有復寫機制）
* 協調僅在發佈環境中執行（製作與發佈之間沒有反向/正向復寫機制）
* 通常最適合開發、演示和培訓

## 配置SRP {#configuring-srp}

根據基礎部署指定預設儲存選項，會透過 [儲存配置控制台](srp-config.md).

如需每個選項的設定詳細資訊，請參閱：

* [ASRP -Adobe儲存資源提供程式](asrp.md)
* [MSRP - MongoDB儲存資源提供程式](msrp.md)
* [DSRP — 關係資料庫儲存資源提供程式](dsrp.md)
* [JSRP - JCR儲存資源提供商](jsrp.md)

如果未主動選取儲存選項，則JSRP預設為啟用。

## 其他資訊 {#additional-information}

### UGC從未複製 {#ugc-never-replicated}

在製作環境中，製作者會建立頁面內容並複製到發佈環境。 當頁面包含互動式AEM Communities功能時（例如留言、評論、論壇、部落格或QnA），成員（在網站訪客中籤名）在發佈實例上的交互會導致用戶在發佈環境中生成內容(UGC)。

以前，此社群內容會反向複製至製作例項，或從複製至發佈例項的製作。 使用反向和正向復寫來維持AEM例項之間的一致性會有問題。

從AEM Communities 6.1開始，如上所述，對UGC使用共用儲存已消除了復寫UGC的需求。

複製網站內容時，不會複製UGC。

### 管理使用者資料 {#managing-user-data}

社區也感興趣 [*使用者*, *使用者群組*，和 *使用者設定檔*](users.md). 當此用戶相關資料在發佈環境中建立和更新時，拓撲為 [發佈農場](../../help/sites-deploying/recommended-deploys.md#tarmk-farm).

自AEM Communities 6.1起，使用者相關資料會使用Sling分送同步，而非復寫。 如需詳細資訊，請造訪 [使用者同步](sync.md).

### 升級至AEM Communities 6.2 {#upgrading-to-aem-communities}

升級至AEM Communities 6.3時，如果需要保留原有的UGC，則應根據AEM 5.6.1或AEM 6.0社群是否使用Adobe隨選儲存或UGC的內部部署儲存，採取步驟。

如需詳細資訊，請造訪 [升級至AEM Communities 6.3](upgrade.md).

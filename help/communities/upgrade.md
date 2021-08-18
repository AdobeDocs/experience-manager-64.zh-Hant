---
title: 升級至AEM 6.4 Communities
seo-title: 升級至AEM 6.4 Communities
description: 如何從舊版升級至AEM 6.4 Communities
seo-description: 如何從舊版升級至AEM 6.4 Communities
uuid: c6c2846e-38d4-4e99-9038-bfb486afd8b9
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: 7aa28e36-6b31-4447-b800-cab2dc78c93c
exl-id: ef622ac3-d96d-48bf-bfb2-61516d9deb5c
source-git-commit: a70f874ad7fcae59ee4c6ec20e23ffb2e339590b
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 0%

---

# 升級至AEM 6.4 Communities {#upgrading-to-aem-communities}

視每個網站的拓撲和功能而定，升級至AEM Communities 6.4或安裝最新的Feature Pack時，可能需要執行下列動作。

本節針對Communities，並補充[升級至AEM 6.4](../../help/sites-deploying/upgrade.md)（平台）中提供的資訊。

## 從AEM 6.1或更新版本升級 {#upgrading-from-aem-or-later}

### 重新索引Solr {#reindex-solr}

在使用MSRP設定的部署上安裝新的Communities功能套件時，必須：

1. 安裝[最新的Feature Pack](deploy-communities.md#latestfeaturepack)
2. 安裝[最新Solr配置檔案](msrp.md#upgrading)
3. 重新索引MSRP

   請參閱[MSRP重新索引工具](msrp.md#msrp-reindex-tool)節

### 啟用2.0 {#enablement}

自AEM 6.3起，啟用功能不再將報表資訊儲存在MySQL中。 MySQL相依性僅用於追蹤SCORM內容。

請聯絡[客戶服務](https://helpx.adobe.com/tw/marketing-cloud/contact-support.html)以取得從啟用1.0移轉內容的協助。

## 從AEM 6.0升級 {#upgrading-from-aem}

如果需要保留預先存在的UGC，則執行此操作的方法取決於儲存的部署UGC [內部部署](#on-premise-storage)還是[Adobe雲](#adobe-cloud-storage)中。

### Adobe雲端儲存空間 {#adobe-cloud-storage}

如果升級的網站設定為使用Adobe雲端儲存空間，則可能會顯示（不正確），好像所有UGC都已遺失，因為SRP方法將無法在舊位置找到原先現有的UGC。

因此，能夠指示ASRP使用`AEM 6.0 compatability-mode`訪問UGC。

適用於所有AEM 6.3製作和發佈例項

1. 以管理員權限登入
2. 配置[ASRP](asrp.md)
3. 請依照下列步驟，使預先存在的UGC可見：
我。例如，瀏覽至Web主控台
   [https://&lt;host>:&lt;port>/system/console/](http://localhost:4502/system/console/configMgr)
configMgrii。找到**[!UICONTROL AEM Communities實用程式]**配置
三。 選取以展開設定面板
   * *取消選中* **`Cloud Storage`**
   * 選擇&#x200B;**[!UICONTROL 保存]**

![chlimage_1-126](assets/chlimage_1-126.png)

### 內部部署儲存 {#on-premise-storage}

如果升級的網站未使用雲端儲存空間，則必須轉換任何原先現有的UGC，以符合AEM 6.1 Communities中推出的新結構，以支援通用儲存空間。

為此，GitHub提供開放原始碼移轉工具：\
[AEM Communities UGC移轉工具](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

### Java API {#java-apis}

從AEM 6.0社交社群升級至AEM 6.3社群時，請注意，許多API已重新組織為不同的套件。 使用IDE定制Communities功能時，應輕鬆解決大多數問題。

如需已棄用SocialUtils套件的詳細資訊，請造訪[SocialUtils重構](socialutils.md)。

另請參閱[使用Maven for Communities](maven.md)。

### 無JSP元件模板 {#no-jsp-component-templates}

[社交元件架構](scf.md)(SCF)使用[HandlebarsJS](https://handlebarsjs.com/)(HBS)範本語言，取代AEM 6.0之前使用的Java伺服器頁面(JSP)。

在AEM 6.0中，JSP元件會保留在相同位置的新HBS架構元件旁，而HBS元件通常位於名為「hbs」的子資料夾中。

自AEM 6.1起，JSP元件已完全移除。 對於Communities，建議用SCF元件取代JSP元件的所有使用。

## AEM Communities UGC移轉工具 {#aem-communities-ugc-migration-tool}

[AEM Communities UGC移轉工具](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)是開放原始碼移轉工具，可在GitHub上使用，可自訂以從舊版AEM社群匯出UGC，並匯入至AEM Communities 6.1或更新版本。

除了從舊版移動UGC外，還可使用工具將UGC從一個[SRP](working-with-srp.md)移至另一個，例如從MSRP移至DSRP。

## 從AEM 5.6.1或更舊版本升級 {#upgrading-from-aem-or-earlier}

從概念上講，有三代社區組成：

**第1代**:大約CQ 5.4到AEM 5.6.0 — 這些是 **** collabcomponents，將UGC儲存在本機存放庫中，使用復寫作為跨平台同步UGC的工具。其他差異包括使用Java Server Pages(JSP)來實作，以及僅在製作環境中製作部落格的功能。

**第2代**:從AEM 5.6.1到AEM 6.1 — 這是collaband socialcomponents的 **** 組 **** 合。AEM 6.0推出了新的[social元件框架](scf.md)(SCF),AEM 6.2引入了[通用UGC儲存](working-with-srp.md)，其中UGC是使用[儲存資源提供者](srp.md)(SRP)來存取的。

**第3代**:從AEM 6.2開始，在SCF中實 **** 作為Handlebars(HBS)元件時，只有socialcomponents需要為UGC選擇SRP。

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
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 0%

---


# 升級至AEM 6.4 Communities {#upgrading-to-aem-communities}

視每個網站的拓撲和功能而定，在升級至AEM Communities 6.4或安裝最新功能套件時，可能需要執行下列動作。

本節針對社群，並補充[升級至AEM 6.4](../../help/sites-deploying/upgrade.md)（平台）中提供的資訊。

## 從AEM 6.1或更新版本{#upgrading-from-aem-or-later}升級

### 重新索引Solr {#reindex-solr}

在配置有MSRP的部署上安裝新的Communities功能包時，必須：

1. 安裝[最新功能套件](deploy-communities.md#latestfeaturepack)
2. 安裝[最新的Solr配置檔案](msrp.md#upgrading)
3. 重新索引MSRP

   請參閱[節MSRP重新索引工具](msrp.md#msrp-reindex-tool)

### 啟用2.0 {#enablement}

自AEM 6.3起，啟用功能將不再將報告資訊儲存在MySQL中。 MySQL相依性僅用於跟蹤SCORM內容。

請聯絡[客戶服務](https://helpx.adobe.com/tw/marketing-cloud/contact-support.html)，以取得從Enablement 1.0移轉內容的協助。

## 從AEM 6.0 {#upgrading-from-aem}升級

如果需要保留預先存在的UGC，則執行此動作的方式取決於部署儲存在[on-premise](#on-premise-storage)或[Adobe雲端](#adobe-cloud-storage)中。

### Adobe雲端儲存空間{#adobe-cloud-storage}

如果已升級的網站設定為使用Adobe雲端儲存空間，則可能會（不正確）顯示，好像所有UGC都已遺失，因為SRP方法將無法在舊位置找到預先存在的UGC。

因此，能夠指示ASRP使用`AEM 6.0 compatability-mode`訪問UGC。

針對所有AEM 6.3作者和發佈例項

1. 以管理員權限登入
2. 配置[ASRP](asrp.md)
3. 請依照下列步驟，讓預先存在的UGC可見：
i.例如，瀏覽至Web主控台
   [https://&lt;host>:&lt;port>/system/console/](http://localhost:4502/system/console/configMgr)
configMgrii。找到**[!UICONTROL AEM Communities Utilities]**組態
iii. 選擇以展開配置面板
   * *取消選中* **`Cloud Storage`**
   * 選擇&#x200B;**[!UICONTROL 保存]**

![chlimage_1-126](assets/chlimage_1-126.png)

### 內部部署儲存{#on-premise-storage}

如果升級的網站未使用雲端儲存空間，則必須轉換任何預先存在的UGC，以符合AEM 6.1 Communities中引進的新結構，以支援共用儲存空間。

為此，GitHub上提供開放原始碼移轉工具：\
[AEM Communities UGC移轉工具](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

### Java API {#java-apis}

從AEM 6.0社交社群升級至AEM 6.3社群時，請注意，許多API已重新組織為不同的套件。 在使用IDE自訂社群功能時，大多數問題都應輕鬆解決。

如需已過時SocialUtils套件的詳細資訊，請造訪[SocialUtils Reforcation](socialutils.md)。

另請參見[使用Maven for Communities](maven.md)。

### 無JSP元件模板{#no-jsp-component-templates}

[social元件架構](scf.md)(SCF)使用[HandlebarsJS](https://www.handlebarsjs.com/)(HBS)範本語言來取代AEM 6.0之前使用的Java Server Pages(JSP)。

在AEM 6.0中，JSP元件會保留在新HBS架構元件旁邊的相同位置，而HBS元件通常位於名為&quot;hbs&quot;的子檔案夾中。

自AEM 6.1起，JSP元件已完全移除。 對於Communities，建議使用SCF元件替換所有JSP元件的使用。

## AEM Communities UGC移轉工具{#aem-communities-ugc-migration-tool}

[AEM Communities UGC Migration Tool](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)是開放原始碼移轉工具，可在GitHub上使用，可自訂以從舊版AEM Social社群匯出UGC，並匯入AEM Communities 6.1或更新版本。

除了從舊版移動UGC外，還可使用該工具將UGC從一個[SRP](working-with-srp.md)移至另一個，如從MSRP移至DSRP。

## 從AEM 5.6.1或舊版{#upgrading-from-aem-or-earlier}升級

從概念上講，有三代社群組成：

**第1代**:大約CQ 5.4到AEM 5.6.0 —— 這些是 **** collabcomponents，將UGC儲存在本機儲存庫中，將復製作為跨平台同步UGC的方式。其他差異包括使用Java Server Pages(JSP)的實作，以及部落格功能，其中僅包含在作者環境中編寫。

**第2代**:從AEM 5.6.1到AEM 6.1 —— 這是collaband  **** socialcomponents的 **** 混合。AEM 6.0推出新的[社交元件架構](scf.md)(SCF),AEM 6.2推出了[通用UGC商店](working-with-srp.md)，其中UGC是使用[儲存資源提供者](srp.md)(SRP)存取。

**第3代**:從AEM 6.2轉發，只有 **** socialcomponents，在SCF中實作為Handlebars(HBS)元件，需要針對UGC選擇SRP。

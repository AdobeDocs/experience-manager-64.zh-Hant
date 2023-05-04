---
title: ASRP -Adobe儲存資源提供程式
seo-title: ASRP - Adobe Storage Resource Provider
description: 設定AEM Communities以使用關係資料庫作為其公用儲存
seo-description: Set up AEM Communities to use a relational database as its common store
uuid: 29826b44-633d-4586-8553-cd87ebe269a2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 86349e4d-29ff-4baa-9fcd-c0ab1f0753e9
role: Admin
exl-id: 136c0913-c8b8-451d-bb28-3c3285c172a1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 2%

---

# ASRP -Adobe儲存資源提供程式 {#asrp-adobe-storage-resource-provider}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 關於ASRP {#about-asrp}

當AEM Communities設定為使用ASRP作為其公用存放區時，使用者產生的內容(UGC)可從所有製作和發佈執行個體存取，而無須同步或復寫。

另請參閱 [SRP選項的特點](working-with-srp.md#characteristics-of-srp-options) 和 [建議的拓撲](topologies.md).

## 要求 {#requirements}

使用ASRP需要額外的許可。

若要設定您的AEM Communities網站以使用ASRP進行UGC，請連絡您的客戶代表，以取得：

* 資料中心URL（ASRP端點的地址）
* 消費者金鑰
* 機密金鑰
* 報表套裝ID

消費者金鑰和機密金鑰會在公司的所有報表套裝間共用。 每個租用戶有一個報表套裝。

## 設定 {#configuration}

### 選擇ASRP {#select-asrp}

此 [儲存配置控制台](srp-config.md) 允許選擇預設儲存配置，以確定要使用的SRP實施。

**論作者**:

* 從全局導航： **[!UICONTROL 工具>社區>儲存配置]**

![chlimage_1-310](assets/chlimage_1-310.png)

* 選擇 **[!UICONTROL Adobe儲存資源提供程式(ASRP)]**
* 以下資訊來自設定過程

   * **[!UICONTROL 資料中心 URL]**

      從下拉式清單中選取由您的帳戶代表所識別的生產資料中心

   * **[!UICONTROL 預設報表套裝]**

      輸入預設報表套裝的名稱

   * **[!UICONTROL 消費者金鑰]**

      輸入使用者金鑰

   * **[!UICONTROL 機密]**

      輸入密鑰

* 選擇 **[!UICONTROL 提交]**

準備發佈例項：

* [複製加密密鑰](#replicate-the-crypto-key)
* [複製配置](#publishing-the-configuration)

提交配置後，測試連接：

* 選擇 **[!UICONTROL 測試設定]**
對於每個製作和發佈實例，從儲存配置控制台測試與資料中心的連接

* 最後，請確定設定檔資料的網站URL可從資料中心路由，方法為 [外部連結](#externalize-links).

### 複製加密密鑰 {#replicate-the-crypto-key}

使用者金鑰和密鑰已加密。 為了正確加密/解密金鑰，所有AEM例項上的主要Granite Crypto金鑰必須相同。

請依照 [複製加密密鑰](deploy-communities.md#replicate-the-crypto-key).

### 將連結外部化 {#externalize-links}

若要取得正確的設定檔和設定檔影像連結，請務必正確 [配置Link Externalizer](../../help/sites-developing/externalizer.md).

請務必將網域設定為可從資料中心URL（ASRP端點）路由的URL。

### 時間同步 {#time-synchronization}

為了成功與ASRP端點進行驗證，執行托管AEM Communities的電腦必須同步時間，例如與 [網路時間協定(NTP)](https://www.ntp.org/).

### 發佈設定 {#publishing-the-configuration}

ASRP必須識別為所有製作和發佈執行個體上的通用存放區。

若要讓相同的設定可在發佈環境中使用：

* **論作者**:

   * 從主功能表導覽至 **[!UICONTROL 工具>操作>複製]**
   * 選擇 **[!UICONTROL 激活樹]**
   * **[!UICONTROL 開始路徑]**:

      * 瀏覽至 `/etc/socialconfig/srpc/`
   * 取消選中 **[!UICONTROL 僅已修改]**
   * 選擇 **[!UICONTROL 啟動]**


## 從AEM 6.0升級 {#upgrading-from-aem}

>[!CAUTION]
>
>如果您在已發佈的社群網站上啟用ASRP，則任何已儲存在 [JCR](jsrp.md) 將不再顯示，因為內部部署儲存與雲端儲存之間沒有資料同步。

**`AEM Communities Extension`** 先前於AEM 6.0 social communities as a cloud service中推出。 自AEM 6.1 Communities起，不需要雲端設定，只需從 [儲存配置控制台](srp-config.md).

由於新的儲存結構，因此必須遵循 [升級](upgrade.md#adobe-cloud-storage) 從社交社群升級至社群的指示。

## 管理使用者資料 {#managing-user-data}

如需 *使用者*, *使用者設定檔* 和 *使用者群組*，通常會在發佈環境中輸入，請造訪

* [使用者同步](sync.md)
* [管理使用者和使用者群組](users.md)

## 疑難排解 {#troubleshooting}

### 升級後UGC消失 {#ugc-disappears-after-upgrade}

如果從現有的AEM 6.0社交社群網站升級，請務必遵循 [升級指示](upgrade.md#adobe-cloud-storage)，否則UGC將 *出現* 被迷路了。

### 驗證錯誤 {#authentication-errors}

如果收到資料中心URL的驗證錯誤，且AEM error.log包含有關過時時間戳的訊息，請確認正在進行時間同步。

建議使用工具，例如 [網路時間協定(NTP)](https://www.ntp.org/) 來同步所有AEM製作和發佈伺服器。

### 搜尋中未出現新內容 {#new-content-does-not-appear-in-searches}

Adobe雲儲存基礎架構使用 *最終一致性* 幫助實現其擴展和效能目標。 因此，新內容無法立即使用，而且可能需要幾秒鐘時間才會出現在搜尋結果中。

在監控影響最終一致性的間隔期間，如果新內容出現在搜尋中所花的時間超過幾秒，請連絡您的帳戶代表。

### UGC在ASRP中不可見 {#ugc-not-visible-in-asrp}

檢查儲存選項的配置，確保ASRP已配置為預設提供程式。 預設情況下，儲存資源提供者為JSRP，而非ASRP。

在所有製作和發佈AEM例項上，重新造訪儲存設定主控台或檢查AEM存放庫：

* 在JCR中，如果 [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * 不包含 [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) 節點，表示儲存提供者為JSRP
   * 如果srpc節點存在且包含節點 [defaultconfiguration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration),defaultconfiguration的屬性應將ASRP定義為預設提供程式

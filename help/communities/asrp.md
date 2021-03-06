---
title: ASRP -Adobe儲存資源提供程式
seo-title: ASRP -Adobe儲存資源提供程式
description: 設定AEM Communities以使用關係資料庫作為其公用儲存
seo-description: 設定AEM Communities以使用關係資料庫作為其公用儲存
uuid: 29826b44-633d-4586-8553-cd87ebe269a2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 86349e4d-29ff-4baa-9fcd-c0ab1f0753e9
role: Admin
exl-id: 136c0913-c8b8-451d-bb28-3c3285c172a1
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 2%

---

# ASRP -Adobe儲存資源提供程式 {#asrp-adobe-storage-resource-provider}

## 關於ASRP {#about-asrp}

當AEM Communities設定為使用ASRP作為其公用存放區時，使用者產生的內容(UGC)可從所有製作和發佈執行個體存取，而無須同步或復寫。

另請參閱[SRP選項的特性](working-with-srp.md#characteristics-of-srp-options)和[建議拓撲](topologies.md)。

## 需求 {#requirements}

使用ASRP需要額外的許可。

若要設定您的AEM Communities網站以使用ASRP進行UGC，請連絡您的客戶代表，以取得：

* 資料中心URL（ASRP端點的地址）
* 消費者金鑰
* 機密金鑰
* 報表套裝ID

消費者金鑰和機密金鑰會在公司的所有報表套裝間共用。 每個租用戶有一個報表套裝。

## 設定 {#configuration}

### 選擇ASRP {#select-asrp}

[儲存配置控制台](srp-config.md)允許選擇預設儲存配置，以確定要使用的SRP實施。

**在作者上**:

* 從全局導航：**[!UICONTROL 工具>社區>儲存配置]**

![chlimage_1-310](assets/chlimage_1-310.png)

* 選擇&#x200B;**[!UICONTROL Adobe儲存資源提供程式(ASRP)]**
* 以下資訊來自設定過程

   * **[!UICONTROL 資料中心 URL]**

      從下拉式清單中選取由您的帳戶代表所識別的生產資料中心

   * **[!UICONTROL 預設報表套裝]**

      輸入預設報表套裝的名稱

   * **[!UICONTROL 消費者金鑰]**

      輸入使用者金鑰

   * **[!UICONTROL 機密]**

      輸入密鑰

* 選擇&#x200B;**[!UICONTROL 提交]**

準備發佈例項：

* [複製加密密鑰](#replicate-the-crypto-key)
* [複製配置](#publishing-the-configuration)

提交配置後，測試連接：

* 選擇&#x200B;**[!UICONTROL 測試配置]**
對於每個製作和發佈實例，從儲存配置控制台測試與資料中心的連接

* 最後，請確定設定檔資料的網站URL可透過[將連結外部化](#externalize-links)從資料中心路由。

### 複製加密密鑰 {#replicate-the-crypto-key}

使用者金鑰和密鑰已加密。 為了正確加密/解密金鑰，所有AEM例項上的主要Granite Crypto金鑰必須相同。

按照[複製加密密鑰](deploy-communities.md#replicate-the-crypto-key)中的說明操作。

### 將連結外部化 {#externalize-links}

要獲得正確的配置檔案和配置檔案影像連結，請確保正確[配置連結外部化程式](../../help/sites-developing/externalizer.md)。

請務必將網域設定為可從資料中心URL（ASRP端點）路由的URL。

### 時間同步 {#time-synchronization}

為了成功與ASRP端點進行身份驗證，運行托管AEM Communities的電腦必須進行時間同步，例如與[網路時間協定(NTP)](https://www.ntp.org/)同步。

### 發佈設定 {#publishing-the-configuration}

ASRP必須識別為所有製作和發佈執行個體上的通用存放區。

若要讓相同的設定可在發佈環境中使用：

* **在作者上**:

   * 從主菜單導航到&#x200B;**[!UICONTROL 工具>操作>複製]**
   * 選擇&#x200B;**[!UICONTROL 激活樹]**
   * **[!UICONTROL 開始路徑]**:

      * 瀏覽至`/etc/socialconfig/srpc/`
   * 取消選中&#x200B;**[!UICONTROL 僅已修改]**
   * 選擇&#x200B;**[!UICONTROL 激活]**


## 從AEM 6.0升級 {#upgrading-from-aem}

>[!CAUTION]
>
>如果您在已發佈的社群網站上啟用ASRP，則已儲存在[JCR](jsrp.md)中的任何UGC將不再可見，因為內部部署儲存與雲端儲存之間沒有資料同步。

**`AEM Communities Extension`** 先前於AEM 6.0 social communities as a cloud service中推出。自AEM 6.1 Communities起，無需雲配置，只需從[儲存配置控制台](srp-config.md)中選擇ASRP即可。

由於新的儲存結構，從社交社群升級為社群時，必須遵循[upgrade](upgrade.md#adobe-cloud-storage)指示。

## 管理使用者資料 {#managing-user-data}

如需&#x200B;*users*、*user profiles*&#x200B;和&#x200B;*user groups*&#x200B;的相關資訊，通常在發佈環境中輸入，請瀏覽

* [使用者同步](sync.md)
* [管理使用者和使用者群組](users.md)

## 疑難排解 {#troubleshooting}

### 升級後UGC消失 {#ugc-disappears-after-upgrade}

如果從現有AEM 6.0社交社群網站升級，請務必遵循[升級指示](upgrade.md#adobe-cloud-storage)，否則UGC將會&#x200B;*出現*&#x200B;而遺失。

### 驗證錯誤 {#authentication-errors}

如果收到資料中心URL的驗證錯誤，且AEM error.log包含有關過時時間戳的訊息，請驗證是否發生時間同步。

建議使用[網路時間協定(NTP)](https://www.ntp.org/)等工具來將所有AEM作者和發佈伺服器進行時間同步。

### 搜尋中未出現新內容 {#new-content-does-not-appear-in-searches}

Adobe雲儲存基礎架構使用&#x200B;*最終一致性*&#x200B;來幫助實現其擴展和效能目標。 因此，新內容無法立即使用，而且可能需要幾秒鐘時間才會出現在搜尋結果中。

在監控影響最終一致性的間隔期間，如果新內容出現在搜尋中所花的時間超過幾秒，請連絡您的帳戶代表。

### UGC在ASRP中不可見 {#ugc-not-visible-in-asrp}

檢查儲存選項的配置，確保ASRP已配置為預設提供程式。 預設情況下，儲存資源提供者為JSRP，而非ASRP。

在所有製作和發佈AEM例項上，重新造訪儲存設定主控台或檢查AEM存放庫：

* 在JCR中，如果[/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * 不包含[srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc)節點，表示儲存提供者為JSRP
   * 如果srpc節點存在且包含節點[defaultconfiguration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration)，則defaultconfiguration的屬性應將ASRP定義為預設提供程式

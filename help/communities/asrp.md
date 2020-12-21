---
title: ASRP - Adobe儲存資源供應商
seo-title: ASRP - Adobe儲存資源供應商
description: 設定AEM Communities，以使用關聯式資料庫做為其公用儲存
seo-description: 設定AEM Communities，以使用關聯式資料庫做為其公用儲存
uuid: 29826b44-633d-4586-8553-cd87ebe269a2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 86349e4d-29ff-4baa-9fcd-c0ab1f0753e9
translation-type: tm+mt
source-git-commit: 09f8adac1d5fc4edeca03d6955faddf5ea045405
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 2%

---


# ASRP - Adobe儲存資源供應商{#asrp-adobe-storage-resource-provider}

## 關於ASRP {#about-asrp}

當AEM Communities設定為使用ASRP做為其公用儲存時，使用者產生的內容(UGC)可從所有作者和發佈例項存取，而不需同步或複製。

另請參見[SRP選項的特性](working-with-srp.md#characteristics-of-srp-options)和[建議拓撲](topologies.md)。

## 要求{#requirements}

使用ASRP需要額外的授權。

若要設定您的AEM Communities網站以使用UGC的ASRP，請連絡您的帳戶代表，以取得：

* 資料中心URL（ASRP端點的位址）
* 消費者金鑰
* 機密金鑰
* 報表套裝ID

消費者和機密金鑰會在公司的所有報表套裝中共用。 每個租用戶有一個報表套裝。

## 設定 {#configuration}

### 選擇ASRP {#select-asrp}

[儲存配置控制台](srp-config.md)允許選擇預設儲存配置，該配置標識要使用的SRP實施。

**作者**:

* 從全域導覽：**[!UICONTROL 工具>社區>儲存配置]**

![chlimage_1-311](assets/chlimage_1-310.png)

* 選擇&#x200B;**[!UICONTROL Adobe儲存資源提供商(ASRP)]**
* 以下資訊來自設定過程

   * **[!UICONTROL 資料中心 URL]**

      下拉式清單，以選擇由您的帳戶代表所識別的生產資料中心

   * **[!UICONTROL 預設報表套裝]**

      輸入預設報表套裝的名稱

   * **[!UICONTROL 消費者金鑰]**

      輸入消費者金鑰

   * **[!UICONTROL 機密]**

      輸入密鑰

* 選擇&#x200B;**[!UICONTROL 提交]**

準備發佈例項：

* [複製加密密鑰](#replicate-the-crypto-key)
* [複製配置](#publishing-the-configuration)

提交配置後，測試連接：

* 選擇&#x200B;**[!UICONTROL 測試配置]**
對於每個作者和發佈實例，請測試從「儲存配置」控制台到資料中心的連接

* 最後，請確定描述檔資料的網站URL可透過[外部化連結](#externalize-links)從資料中心路由。

### 複製加密密鑰{#replicate-the-crypto-key}

消費者金鑰和機密金鑰會加密。 為了正確加密／解密密鑰，所有AEM實例上的主Granite Crypto密鑰必須相同。

按照[複製加密密鑰](deploy-communities.md#replicate-the-crypto-key)中的說明操作。

### 將連結外部化{#externalize-links}

如需正確的描述檔和描述檔影像連結，請務必正確[設定連結外部化器](../../help/sites-developing/externalizer.md)。

請務必將網域設定為可從資料中心URL（ASRP端點）路由的URL。

### 時間同步{#time-synchronization}

為了成功與ASRP端點進行驗證，您所代管的AEM Communities的執行機器必須進行時間同步，例如與[網路時間通訊協定(NTP)](https://www.ntp.org/)同步。

### 發佈配置{#publishing-the-configuration}

ASRP必須被識別為所有作者和發佈實例上的公用商店。

要使相同的配置在發佈環境中可用，請執行以下操作：

* **作者**:

   * 從主菜單導航到&#x200B;**[!UICONTROL 工具>操作>複製]**
   * 選擇&#x200B;**[!UICONTROL 激活樹]**
   * **[!UICONTROL 開始路徑]**:

      * 瀏覽至`/etc/socialconfig/srpc/`
   * 取消選中&#x200B;**[!UICONTROL 僅已修改]**
   * 選擇&#x200B;**[!UICONTROL 激活]**


## 從AEM 6.0 {#upgrading-from-aem}升級

>[!CAUTION]
>
>如果您在發佈的社群網站上啟用ASRP，則已儲存在[JCR](jsrp.md)中的任何UGC將不再顯示，因為內部部署儲存空間和雲端儲存空間之間不會同步資料。

**`AEM Communities Extension`** 之前在AEM 6.0社交社群中以雲端服務的形式推出。自AEM 6.1 Communities起，您不需要雲端設定，只需從[儲存組態控制台](srp-config.md)中選取ASRP。

由於新的儲存結構，從社交社區升級到社區時，必須遵循[upgrade](upgrade.md#adobe-cloud-storage)說明。

## 管理用戶資料{#managing-user-data}

有關通常在發佈環境中輸入的&#x200B;*用戶*、*用戶配置檔案*&#x200B;和&#x200B;*用戶組*&#x200B;的資訊，請訪問

* [用戶同步](sync.md)
* [管理使用者和使用者群組](users.md)

## 疑難排解 {#troubleshooting}

### 升級{#ugc-disappears-after-upgrade}後UGC消失

如果從現有的AEM 6.0社交社群網站升級，請務必遵循[升級指示](upgrade.md#adobe-cloud-storage)，否則UGC將會遺失&#x200B;*appear*。

### 驗證錯誤{#authentication-errors}

如果收到Data Center URL的驗證錯誤，而AEM error.log包含有關過時時間戳記的訊息，請確認時間同步正在進行。

建議使用[網路時間通訊協定(NTP)](https://www.ntp.org/)等工具，來時間同步所有AEM作者和發佈伺服器。

### 搜尋{#new-content-does-not-appear-in-searches}中未顯示新內容

Adobe雲端儲存基礎架構使用&#x200B;*最終的一致性*&#x200B;來協助實現其擴充和效能目標。 因此，新內容無法立即使用，而且可能需要幾秒鐘的時間才會顯示在搜尋結果中。

雖然會監控影響最終一致性的間隔，但若搜尋中出現新內容所花的時間超過幾秒，請連絡您的帳戶代表。

### ASRP {#ugc-not-visible-in-asrp}中不顯示UGC

通過檢查儲存選項的配置，確保ASRP已配置為預設提供程式。 預設情況下，儲存資源提供方是JSRP，而不是ASRP。

在所有作者和發佈AEM例項上，請重新造訪「儲存組態控制台」或檢查AEM存放庫：

* 在JCR中，如果[/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * 不包含[srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc)節點，這表示儲存提供程式是JSRP
   * 如果srpc節點存在並包含節點[defaultconfiguration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration)，則defaultconfiguration的屬性應將ASRP定義為預設提供程式


---
title: 使AEM能夠搜索受安全保護的文檔PDF文檔
seo-title: Enable AEM to search document security protected PDF documents
description: 了解如何啟用原生AEM搜尋，以對受DRM保護的PDF檔案執行全文搜尋。
seo-description: Learn how to enable native AEM search to perform full-text search on DRM protected PDF documents.
uuid: c743cda3-252f-4c1f-8d94-e6d26d91dcd8
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
geptopics: SG_AEMFORMS/categories/working_with_document_security
discoiquuid: 759068fa-dc1b-4cf5-bc7b-62b8c5464831
feature: Document Security
exl-id: c405c69b-3588-4701-8f36-1ea0680e056d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 1%

---

# 使AEM能夠搜索受安全保護的文檔PDF文檔 {#enable-aem-to-search-document-security-protected-pdf-documents}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

AEM搜尋能夠搜尋及找到AEM資產，並對各種常用的檔案格式(例如純文字檔案、Microsoft Office檔案和PDF檔案)執行文字搜尋。 您也可以擴充原生搜尋，以執行全文搜尋 [PDF受AEM檔案安全性保護的檔案](/help/forms/using/admin-help/document-security.md). 要啟用AEM對此類文檔執行全文搜索，請執行以下步驟：

1. 建立安全連接
1. 索引受策略保護的示例PDF文檔

## 必備條件 {#prerequisites}

* 如果您在OSGi上使用AEM Forms:

   * 安裝 [AEM Forms Document Security Indexer套件](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) 在AEM Forms伺服器上。
   * 確認JEE伺服器上的AEM Forms正常運作，且JEE伺服器上對應的AEM Forms上已安裝檔案安全性。 JEE伺服器上的AEM表單必須為受保護的檔案建立索引。

* 如果您只在JEE伺服器上使用AEM Forms，則已安裝索引器套件。
* 請確定所有套件組合皆已啟動並執行。 如果所有套件組合都未啟用，請等待所有套件組合都啟動並運行。

   * 若為OSGi上的AEM Forms，套件組合列於 `https://[server]:[port]/system/console/bundles`.
   * 若為JEE版的AEM Forms，套件組合列於 `https://[server]:[port]/[context-path]/system/console/bundles`. 例如 `http://localhost:8080/lc/system/console/bundles`。

* 新增 *sun.util.calendar* 封裝至允許清單。 要將包添加到允許清單，請執行以下步驟：

   1. 開啟AEM Web Console。 URL為 `https://[server]:[port]/system/console/configMgr`.
   1. 尋找並開啟 **反序列化防火牆配置**.
   1. 將sun.util.calendar包添加到白名單類或包前置詞欄位，然後按一下 **儲存**.

## 在AEM Forms JEE和OSGi堆疊之間建立安全連線 {#establish-a-secure-connection-between-aem-forms-jee-and-osgi-stacks}

您可以使用下列其中一種方法來建立安全連線：

* 在JEE上使用AEM Forms管理憑證設定AdobeLiveCycle用戶端SDK套件
* 使用相互驗證來設定AdobeLiveCycle用戶端SDK套件組合

### 在JEE上使用AEM Forms管理憑證設定AdobeLiveCycle用戶端SDK套件 {#configure-adobe-livecycle-client-sdk-bundle-with-aem-forms-on-jee-admin-credentials}

1. 開啟AEM Web Console。 URL為 `https://[server]:[port]/system/console/configMgr`.
1. 找出並開啟 **AdobeLiveCycle用戶端SDK套件**. 指定下列欄位的值：

   * **伺服器URL:** 指定JEE伺服器上AEM Forms的HTTPS URL。 要啟用通過https的通信，請使用-Djavax.net.ssl.trustStore=重新啟動伺服器&lt;path of=&quot;&quot; aem=&quot;&quot; forms=&quot;&quot; on=&quot;&quot; jee=&quot;&quot; keystore=&quot;&quot; file=&quot;&quot;> 參數。
   * **服務名稱**:將RightsManagementService添加到指定服務的清單中。
   * **用戶名：** 指定JEE帳戶上用來起始來自AEM伺服器呼叫的AEM Forms使用者名稱。 指定的帳戶必須擁有在JEE伺服器上的AEM Forms上啟動檔案服務的權限。
   * **密碼**:在使用者名稱欄位中提及的JEE帳戶上指定AEM Forms的密碼。

   按一下「**儲存**」。AEM可用於搜索受文檔安全保護的PDF文檔。

### 使用相互驗證來設定AdobeLiveCycle用戶端SDK套件組合 {#configure-adobe-livecycle-client-sdk-bundle-using-mutual-authentication}

1. 啟用JEE上AEM Forms的相互驗證。 如需詳細資訊，請參閱 [CAC與相互驗證](https://helpx.adobe.com/livecycle/kb/cac-mutual-authentication.html).
1. 開啟AEM Web Console。 URL為 `https://[server]:[port]/system/console/configMgr`.
1. 找出並開啟 **AdobeLiveCycle用戶端SDK** 捆綁。 指定下列屬性的值：

   * **伺服器URL**:指定JEE伺服器上AEM Forms的HTTPS URL。 若要啟用透過https的通訊，請使用-Djavax.net.ssl.trustStore=重新啟動AEM伺服器&lt;path of=&quot;&quot; aem=&quot;&quot; forms=&quot;&quot; on=&quot;&quot; jee=&quot;&quot; keystore=&quot;&quot; file=&quot;&quot;> 參數。
   * **啟用雙向SSL**:啟用「啟用2向SSL」選項。
   * **KeyStore檔案URL**:指定金鑰存放區檔案的URL。
   * **TrustStore FIle URL**:指定信任儲存檔案的URL。
   * **KeyStore密碼**:指定金鑰存放區檔案的密碼。
   * **TrustStorePassword**:指定信任儲存檔案的密碼。
   * **服務名稱**:將RightsManagementService添加到指定服務的清單中。

   按一下「**儲存**」。AEM可搜尋受檔案安全保護的PDF檔案

## 索引受策略保護的示例PDF文檔 {#index-a-sample-policy-protected-pdf-document}

1. 以管理員身分登入AEM Assets。
1. 在AEM Digital Asset Manager中建立資料夾，並將受原則保護的PDF檔案上傳至新建立的資料夾。

   現在，您可以使用AEM搜索來搜索受策略保護的文檔。

---
title: SAML 2.0 驗證處理常式
seo-title: SAML 2.0 Authentication Handler
description: 了解 AEM 中的 SAML 2.0 驗證處理常式。
seo-description: Learn about the SAML 2.0 Authentication Handler in AEM.
uuid: 51f97315-350a-42a4-af2c-2de87307c6ad
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 6ed09b5d-5089-43d2-b9d5-e7db57be5c02
exl-id: 4868daad-0f3e-48cb-9b20-08dee270e74e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 90%

---

# SAML 2.0 驗證處理常式{#saml-authentication-handler}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

AEM 隨附 [SAML](http://saml.xml.org/saml-specifications) 驗證處理常式。此處理常式使用 `HTTP POST` 繫結，提供對 [SAML](http://saml.xml.org/saml-specifications) 2.0 驗證請求通訊協定 (Web-SSO 設定檔) 的支援。

它支援：

* 訊息的簽署和加密
* 使用者的自動建立
* 將群組同步至 AEM 中的現有群組
* 服務提供者和身分提供者啟動的驗證

此處理常式會將加密的 SAML 回應訊息儲存在使用者節點 (`usernode/samlResponse`) 中，以促進與協力廠商服務提供者的通訊。

>[!NOTE]
>
>請參閱 [AEM 與 SAML 整合的示範](https://helpx.adobe.com/experience-manager/kb/simple-saml-demo.html)。
>
>若要閱讀端對端社群文章，請按一下： [整合SAML與Adobe Experience Manager](https://helpx.adobe.com/experience-manager/using/aem63_saml.html).

## 設定 SAML 2.0 驗證處理常式 {#configuring-the-saml-authentication-handler}

[網頁主控台](/help/sites-deploying/configuring-osgi.md)提供了對 [SAML](http://saml.xml.org/saml-specifications) 2.0 驗證處理常式設定 (稱為 **Adobe Granite SAML 2.0 驗證處理常式**) 的存取權。您可設定下列屬性。

>[!NOTE]
>
>SAML 2.0 驗證處理常式會依預設停用。您必須至少設定下列其中一個屬性，才能啟用此處理常式：
>
>* 身分提供者POSTURL。
>* 服務提供者實體 ID。
>


>[!NOTE]
>
>SAML 聲明已經過簽署，並可選擇進行加密。為了使其運作，您必須至少在 TrustStore 中提供身分提供者的公開憑證。如需詳細資訊，請參閱[將 IdP 憑證新增至 TrustStore](/help/sites-administering/saml-2-0-authenticationhandler.md#add-the-idp-certificate-to-the-aem-truststore) 一節。

**路徑**：Sling 應使用此驗證處理常式的存放庫路徑。如果此為空白，則會停用驗證處理常式。

**服務排名**：OSGi 框架服務排名值，可指示呼叫此服務的順序。此為整數值，其中較高的值代表較高的優先順序。

**IDP 憑證別名**：全域 TrustStore 中 IdP 憑證的別名。如果此屬性為空白，則會停用驗證處理常式。若要了解如何設定，請參閱下方的「將 IdP 憑證新增至 AEM TrustStore」一章。

**身分提供者URL** IDP的URL，應將SAML驗證要求傳送至此處。 如果此屬性為空白，則會停用驗證處理常式。

>[!CAUTION]
>
>身分提供者主機名稱必須新增至 **Apache Sling 反向連結篩選器** OSGi 設定。如需詳細資訊，請參閱[網頁主控台](/help/sites-deploying/configuring-osgi.md)一節。

**服務提供者實體 ID**：此 ID 可透過身分提供者唯一地辨識此服務提供者。如果此屬性為空白，則會停用驗證處理常式。

**預設重新導向**：在成功驗證後，重新導向到的預設位置。

>[!NOTE]
>
>此位置僅在未設定 `request-path` Cookie 時使用。如果您在沒有有效登入權杖的情況下，請求已設定路徑下方的任何頁面，則請求的路徑會儲存在 Cookie 中，\
>而且在成功驗證後，瀏覽器會重新導向到此位置。

**使用者 ID 屬性**：屬性的名稱，其中包含在 CRX 存放庫中用於驗證和建立使用者的使用者 ID。

>[!NOTE]
>
>系統不會從 SAML 聲明的 `saml:Subject` 節點取得使用者 ID，而是從此 `saml:Attribute` 取得。

**使用加密**：此驗證處理常式是否需要加密的 SAML 聲明。

**自動建立 CRX 使用者**：在成功驗證後，是否自動建立存放庫中的非現有使用者。

>[!CAUTION]
>
>如果停用 CRX 使用者的自動建立，則必須手動建立使用者。

**新增至群組**：在成功驗證後，是否應自動將使用者新增至 CRX 群組。

**群組成員資格**：saml:Attribute 的名稱，其中包含此使用者應新增至的 CRX 群組清單。

## 將 IdP 憑證新增至 AEM TrustStore {#add-the-idp-certificate-to-the-aem-truststore}

SAML 聲明已經過簽署，並可選擇進行加密。為了使其運作，您必須至少在存放庫中提供 IdP 的公開憑證。若要進行這項作業，您必須：

1. 前往 *http:/serveraddress:serverport/libs/granite/security/content/truststore.html*
1. 按下「**[!UICONTROL 建立 TrustStore 連結]**」
1. 輸入 TrustStore 的密碼，然後按「**[!UICONTROL 儲存]**」。
1. 按一下「**[!UICONTROL 管理 TrustStore]**」。
1. 上傳 IdP 憑證。
1. 記下憑證別名。在下方的範例中，別名為 **[!UICONTROL admin#1436172864930]**。

   ![chlimage_1-372](assets/chlimage_1-372.png)

## 將服務提供者金鑰和憑證鏈新增至 AEM KeyStore {#add-the-service-provider-key-and-certificate-chain-to-the-aem-keystore}

>[!NOTE]
>
>下方的步驟為必要步驟，否則將擲回下列例外狀況：`com.adobe.granite.keystore.KeyStoreNotInitialisedException: Uninitialised system trust store`

1. 前往：[http://localhost:4502/libs/granite/security/content/useradmin.html](http://localhost:4502/libs/granite/security/content/useradmin.html)
1. 編輯 `authentication-service` 使用者。
1. 按一下「**帳戶設定**」下的「**建立 KeyStore**」，以建立 KeyStore。

>[!NOTE]
>
>只有在處理常式應該能簽署或解密訊息時，才需要執行下方的步驟。

1. 按一下「**選取私密金鑰檔案**」，上傳私密金鑰檔案。金鑰必須採用 PKCS#8 格式與 DER 編碼。
1. 按一下「**選擇證書鏈檔案**」，上傳憑證檔案。
1. 指派別名，如下所示：

   ![chlimage_1-373](assets/chlimage_1-373.png)

## 為 SAML 設定記錄器 {#configure-a-logger-for-saml}

您可以設定記錄器，以偵錯任何可能因錯誤設定 SAML 而產生的問題。您可以透過以下方式進行：

1. 前往網頁主控台：*http://localhost:4502/system/console/configMgr*
1. 搜尋並按一下稱為「**Apache Sling 記錄記錄器設定**」的項目
1. 使用下列設定來建立記錄器：

   * **記錄層級：** Debug
   * **記錄檔：** logs/saml.log
   * **記錄器：** com.adobe.granite.auth.saml

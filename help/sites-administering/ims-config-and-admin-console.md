---
title: 適用於AEM Managed Services的Adobe IMS驗證和Admin Console支援
seo-title: Adobe IMS Authentication and Admin Console Support for AEM Managed Services
description: 了解如何在AEM中使用Admin Console。
seo-description: Learn how to use the Admin Console in AEM.
uuid: 3f5b32c7-cf62-41a4-be34-3f71bbf224eb
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: f6112dea-a1eb-4fd6-84fb-f098476deab7
exl-id: 38bbad03-aead-43d3-a28c-cc716955ddfb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1785'
ht-degree: 14%

---

# 適用於AEM Managed Services的Adobe IMS驗證和Admin Console支援 {#adobe-ims-authentication-and-admin-console-support-for-aem-managed-services}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>請注意，此功能僅供Adobe Managed Services客戶使用。

## 簡介 {#introduction}

AEM 6.4.3.0推出AEM例項和Adobe IMS(Identity Management系統)驗證的Admin Console支援 **AEM Managed Services** 客戶。

AEM上線至Admin Console可讓AEM Managed Services客戶在一個主控台中管理所有Experience Cloud使用者。 可將使用者和群組指派給與AEM例項相關聯的產品設定檔，讓他們登入特定例項。

## 重要焦點 {#key-highlights}

* AEM IMS驗證支援僅適用於AEM作者、管理員或開發人員，不適用於客戶網站的外部使用者，例如網站訪客
* 此Admin Console會將AEM Managed Services客戶顯示為IMS組織，並將其例項顯示為產品內容。 客戶系統和產品管理員將能管理例項的存取權
* AEM Managed Services會同步客戶拓撲與Admin Console。 在Admin Console中，每個例項都有一個AEM Managed Services產品內容例項。
* Admin Console中的產品設定檔將決定使用者可存取的例項
* 支援使用客戶自己符合SAML 2的身分提供者進行同盟驗證
* 僅支援Enterprise ID或Federated ID（適用於客戶單一登入），不支援個人AdobeID。
* 客戶管理員將繼續擁有使用者管理(在Adobe Admin Console中)。

## 架構 {#architecture}

IMS驗證的運作方式是在AEM和Adobe IMS端點之間使用OAuth通訊協定。 使用者新增至IMS且擁有Adobe身分識別後，就可以使用IMS憑證登入AEM Managed Services執行個體。

使用者登入流程如下所示，系統會將使用者重新導向至IMS，並選擇性地導向至客戶IDP以進行SSO驗證，然後重新導向回AEM。

![image2018-9-23_23-55-8](assets/image2018-9-23_23-55-8.png)

## 如何設定 {#how-to-set-up}

### 在 Admin Console 中佈建組織 {#onboarding-organizations-to-admin-console}

客戶必須上線Admin Console才能使用Adobe IMS進行AEM驗證。

第一步，客戶應該有已布建於Adobe IMS中的組織。 Adobe企業客戶在 [Adobe Admin Console](https://helpx.adobe.com/tw/enterprise/using/admin-console.html).

AEM Managed Services客戶應已布建組織，且在IMS布建過程中，將可在Admin Console中提供客戶例項，以管理使用者權益和存取權。

移至IMS進行使用者驗證是AMS與客戶之間的共同努力，每個客戶都有自己的工作流程要完成。

客戶成為IMS組織且AMS完成為IMS布建客戶後，以下為所需設定工作流程的摘要：

![image2018-9-23_23-33-25](assets/image2018-9-23_23-33-25.png)

1. 指定的系統管理員會收到登入Admin Console的邀請
1. 系統管理員聲明網域以確認網域的所有權（在此範例中為acme.com）
1. 系統管理員設定使用者目錄
1. 系統管理員會在Admin Console中設定身分提供者(IDP)以進行SSO設定。
1. AEM管理員可照常管理本機群組、權限。 請參閱使用者和群組同步

>[!NOTE]
>
>如需AdobeIdentity Management基本知識的詳細資訊，包括IDP設定，請參閱文章 [此頁面。](https://helpx.adobe.com/tw/enterprise/using/set-up-identity.html)
>
>有關企業管理和Admin Console的詳細資訊，請參閱文章 [本頁](https://helpx.adobe.com/tw/enterprise/managing/user-guide.html).

### 將使用者加入Admin Console {#onboarding-users-to-the-admin-console}

根據客戶的規模和偏好設定，建立使用者的方式有三種：

1. 在Admin Console中手動建立使用者和群組
1. 上傳含有使用者的CSV檔案
1. 從客戶的企業Active Directory同步用戶和組。

#### 透過 Admin Console UI 手動新增 {#manual-addition-through-admin-console-ui}

客戶可在 Admin Console UI 中手動建立使用者和群組。如果沒有大量使用者可管理，則可使用此方法。 例如，少於50個AEM使用者。

如果客戶已使用此方法管理其他Adobe產品(例如Analytics、Target或Creative Cloud應用程式)，也可以手動建立使用者。

![image2018-9-23_20-39-9](assets/image2018-9-23_20-39-9.png)

#### 在Admin ConsoleUI中上傳檔案 {#file-upload-in-the-admin-console-ui}

為方便建立使用者，可上傳CSV檔案以大量新增使用者：

![image2018-9-23_18-59-57](assets/image2018-9-23_18-59-57.png)

#### 使用者同步工具 {#user-sync-tool}

用戶同步工具（簡稱UST）使企業客戶能夠利用Active Directory或其他經測試的OpenLDAP目錄服務建立或管理Adobe用戶。 目標使用者是IT身分管理員（企業目錄和系統管理員），他們將能夠安裝和配置此工具。 可自訂開放原始碼工具，讓客戶可讓開發人員修改它，以符合自己的特定需求。

當「用戶同步」運行時，它會從組織的Active Directory（或任何其他相容的資料源）中提取用戶清單，並與Admin Console內的用戶清單進行比較。 接著，系統會呼叫 Adobe User Management API，將 Admin Console 與組織的目錄同步。變更流程完全是單向的；在Admin Console中所做的任何編輯都不會推送至目錄。

此工具允許系統管理員將客戶目錄中的使用者群組與Admin Console中的產品設定和使用者群組對應，新的UST版本也允許在Admin Console中動態建立使用者群組。

若要設定「使用者同步」，組織需先透過與 [User Management API](https://www.adobe.io/apis/cloudplatform/usermanagement/docs/setup.html) 相同的使用方式，建立一組憑證。

![image2018-9-23_13-36-56](assets/image2018-9-23_13-36-56.png)

使用者同步是透過AdobeGithub存放庫分送，位置如下：

[https://github.com/adobe-apiplatform/user-sync.py/releases/latest](https://github.com/adobe-apiplatform/user-sync.py/releases/latest)

請注意，搶鮮版2.4RC1提供建立動態群組的支援，可在此處找到： [https://github.com/adobe-apiplatform/user-sync.py/releases/tag/v2.4rc1](https://github.com/adobe-apiplatform/user-sync.py/releases/tag/v2.4rc1)

此版本的主要功能是能在 Admin Console 中動態對應新 LDAP 群組，以取得使用者成員資格，並且建立動態使用者群組。

如需新群組功能的詳細資訊，請參閱：

[https://github.com/adobe-apiplatform/user-sync.py/blob/v2/docs/en/user-manual/advanced_configuration](https://github.com/adobe-apiplatform/user-sync.py/blob/v2/docs/en/user-manual/advanced_configuration.md#additional-group-options)

>[!NOTE]
>
>有關「用戶同步工具」的詳細資訊，請參閱 [檔案頁面](https://adobe-apiplatform.github.io/user-sync.py/en/).
>
>
>使用者同步工具必須依照所述程式，註冊為Adobe I/O用戶端UMAPI [此處](https://adobe-apiplatform.github.io/umapi-documentation/en/UM_Authentication.html).
>
>您可以找到Adobe I/O主控台檔案 [此處](https://www.adobe.io/apis/cloudplatform/console.html).
>
>
>本檔案將說明使用者同步工具所使用的使用者管理API [位置](https://www.adobe.io/apis/cloudplatform/umapi-new.html).

>[!NOTE]
>
>AEM IMS設定將由Adobe Managed Services團隊處理。 但是，客戶管理員可根據其需求（例如「自動群組成員資格」或「群組對應」）對其進行修改。 您的Managed Services團隊也會註冊IMS用戶端。

## 使用方式 {#how-to-use}

### 在 Admin Console 中管理產品和使用者存取權限 {#managing-products-and-user-access-in-admin-console}

客戶產品管理員登入Admin Console時，會看到AEM Managed Services產品內容的多個例項，如下所示：

![screen_shot_2018-09-17at105804pm](assets/screen_shot_2018-09-17at105804pm.png)

在此範例中，組織 *AEM-MS-Onboard* 有32個執行個體，橫跨不同的拓撲和環境，如Stage、Prod等。

![screen_shot_2018-09-17at105517pm](assets/screen_shot_2018-09-17at105517pm.png)

您可以檢查執行個體詳細資訊，以識別執行個體：

![screen_shot_2018-09-17at105601pm](assets/screen_shot_2018-09-17at105601pm.png)

在每個「產品內容」例項下，都會有相關聯的「產品設定檔」。 此產品設定檔用於指派存取權給使用者和群組。

![image2018-9-18_7-48-50](assets/image2018-9-18_7-48-50.png)

在此產品設定檔中新增的任何使用者和群組都可以登入該執行個體，如下列範例所示：

![screen_shot_2018-09-17at105623pm](assets/screen_shot_2018-09-17at105623pm.png)

### 登入AEM {#logging-into-aem}

#### 本機管理員登入 {#local-admin-login}

AEM可繼續支援管理員使用者的本機登入，因為登入畫面可以選取本機登入：

![screen_shot_2018-09-18at121056am](assets/screen_shot_2018-09-18at121056am.png)

#### IMS 登入 {#ims-based-login}

若是其他使用者，在執行個體上設定 IMS 後，即可使用 IMS 登入。使用者會先按一下 **使用Adobe登入** 按鈕，如下所示：

![image2018-9-18_0-10-32](assets/image2018-9-18_0-10-32.png)

接著，系統會將使用者重新導向至IMS登入畫面，並輸入其認證：

![screen_shot_2018-09-17at115629pm](assets/screen_shot_2018-09-17at115629pm.png)

如果在初始Admin Console設定期間設定了同盟IDP，系統會將使用者重新導向至客戶IDP，以執行SSO。

以下範例中為Okta:

![screen_shot_2018-09-17at115734pm](assets/screen_shot_2018-09-17at115734pm.png)

驗證完成後，系統會將使用者重新導向回 AEM 並登入：

![screen_shot_2018-09-18at120124am](assets/screen_shot_2018-09-18at120124am.png)

### 移轉現有使用者 {#migrating-existing-users}

若現有AEM例項使用其他驗證方法，且現在正移轉至IMS，則需要進行移轉步驟。

AEM存放庫中的現有使用者（來源為本機、透過LDAP或SAML）可移轉至使用者移轉公用程式，將IMS視為IDP。

此公用程式將由您的AMS團隊執行，作為IMS布建的一部分。

### 在AEM中管理權限和ACL {#managing-permissions-and-acls-in-aem}

AEM將繼續管理存取控制和權限，這可透過分離來自IMS的使用者群組(例如下列範例中的AEM-GRP-008)和定義權限和存取控制的本機群組來達成。 可將從IMS同步的使用者群組指派給本機群組，並繼承權限。

以下範例中，我們會示範將同步的群組新增至本機 *Dam_Users* 群組。

在此，也將使用者指派給Admin Console中的幾個群組。 (請注意，可使用使用者同步工具從LDAP同步使用者和群組，或在本機建立，請參閱區段 **將使用者加入Admin Console** 以上)。

>[!NOTE]
>
>使用者登入執行個體時，才會同步使用者群組。

![screen_shot_2018-09-17at94207pm](assets/screen_shot_2018-09-17at94207pm.png)

使用者屬於 IMS 中的下列群組：

![screen_shot_2018-09-17at94237pm](assets/screen_shot_2018-09-17at94237pm.png)

使用者登入後，系統會同步其群組成員資格，如下所示：

![screen_shot_2018-09-17at94033pm](assets/screen_shot_2018-09-17at94033pm.png)

在AEM中，從IMS同步的使用者群組可以新增為現有本機群組（例如DAM使用者）的成員。

![screen_shot_2018-09-17at95804pm](assets/screen_shot_2018-09-17at95804pm.png)

如下所示， *AEM-GRP_008* 會繼承DAM使用者的權限。 這是管理同步群組權限的有效方式，也常用於LDAP型驗證方法。

![screen_shot_2018-09-17at110505pm](assets/screen_shot_2018-09-17at110505pm.png)

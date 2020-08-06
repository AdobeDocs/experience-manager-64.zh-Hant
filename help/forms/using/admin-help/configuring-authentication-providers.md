---
title: 設定驗證提供者
seo-title: 設定驗證提供者
description: 新增、編輯或刪除驗證提供者、變更驗證設定，以及閱讀使用者的即時布建。
seo-description: 新增、編輯或刪除驗證提供者、變更驗證設定，以及閱讀使用者的即時布建。
uuid: 90e7690b-1ce0-4604-b58f-6dca4f2372cf
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 31dd8db3-ddac-429e-82f8-8c5dc4ffc186
translation-type: tm+mt
source-git-commit: d04e08e105bba2e6c92d93bcb58839f1b5307bd8
workflow-type: tm+mt
source-wordcount: '1595'
ht-degree: 0%

---


# 設定驗證提供者 {#configuring-authentication-providers}

混合網域需要至少一個驗證提供者，而企業網域則需要至少一個驗證提供者或目錄提供者。

如果使用SPNEGO啟用SSO，請添加啟用SPNEGO的Kerberos驗證提供程式和LDAP提供程式作為備份。 如果SPNEGO不工作，此配置將啟用用戶ID和口令的用戶驗證。 (請參 [閱使用SPNEGO啟用SSO](/help/forms/using/admin-help/enabling-single-sign-on-aem.md#enable-sso-using-spnego))。

## 新增驗證提供者 {#add-an-authentication-provider}

1. 在管理控制台中，按一下「設定>使用者管理>網域管理」。
1. 按一下清單中的現有域。 如果要為新域添加驗證，請參 [閱添加企業域](/help/forms/using/admin-help/adding-domains.md#add-an-enterprise-domain)[或添加混合域](/help/forms/using/admin-help/adding-domains.md#add-a-hybrid-domain)。
1. 按一下「新增驗證」，然後在「驗證提供者」清單中，根據貴組織使用的驗證機制，選取提供者。
1. 提供頁面所需的其他資訊。 (請參閱 [驗證設定](configuring-authentication-providers.md#authentication-settings)。)
1. （可選）按一下「測試」以測試設定。
1. Click OK and then click OK again.

## 編輯現有的驗證提供者 {#edit-an-existing-authentication-provider}

1. 在管理控制台中，按一下「設定>使用者管理>網域管理」。
1. 在清單中按一下適當的網域。
1. 在顯示的頁面上，從清單中選擇適當的驗證提供方，並根據需要進行更改。 (請參閱 [驗證設定](configuring-authentication-providers.md#authentication-settings)。)
1. 按一下「確定」。

## 刪除驗證提供者 {#delete-an-authentication-provider}

1. 在管理控制台中，按一下「設定>使用者管理>網域管理」。
1. 在清單中按一下適當的網域。
1. 選擇要刪除的驗證提供者的複選框，然後按一下刪除。
1. 在顯示的確認頁面上按一下「確定」，然後再按一下「確定」。

## Authentication settings {#authentication-settings}

下列設定可供使用，視您選擇的網域類型和驗證類型而定。

### LDAP設定 {#ldap-settings}

如果要為企業或混合域配置身份驗證並選擇LDAP身份驗證，您可以選擇使用目錄配置中指定的LDAP伺服器，也可以選擇其他LDAP伺服器進行身份驗證。 如果您選擇不同的伺服器，則用戶必須同時存在於兩個LDAP伺服器上。

要使用在目錄配置中指定的LDAP伺服器，請選擇LDAP作為驗證提供程式，然後按一下確定。

要使用不同的LDAP伺服器來執行驗證，請選擇LDAP作為驗證提供程式，然後選擇「自定義LDAP驗證」複選框。 將顯示以下配置設定。

**伺服器：** （強制）目錄伺服器的完全限定域名(FQDN)。 例如，對於corp.example.com網路上名為x的電腦，FQDN為x.corp.example.com。 IP地址可用來代替FQDN伺服器名。

**埠：** （必要）目錄伺服器使用的埠。 通常為389或636(如果安全通訊端層(SSL)通訊協定用於透過網路傳送驗證資訊)。

**SSL:** （必要）指定目錄伺服器在通過網路發送資料時是否使用SSL。 預設值為「否」。 當設定為「是」時，應用程式伺服器的Java™運行時環境(JRE)必須信任相應的LDAP伺服器證書。

**綁定** （強制）指定如何訪問目錄。

**匿名：** 不需要用戶名或密碼。

**使用者：** 需要驗證。 在「名稱」框中，指定可以訪問目錄的用戶記錄的名稱。 最好輸入用戶帳戶的完整唯一判別名(DN)，如cn=Jane Doe、ou=user、dc=can、dc=com。 在「密碼」方塊中，指定相關的密碼。 當您選取「使用者」作為「系結」選項時，就需要這些設定。

**檢索基本DN:** （非必要）擷取基本DN並在下拉式清單中顯示。 當您有多個基本DN且需要選擇值時，此設定非常有用。

**基本DN:** （必要）用作從LDAP階層同步使用者和群組的起點。 最好在層次結構的最低級別指定基本DN，該DN包括所有需要同步服務的用戶和組。 請勿在此設定中包含使用者的DN。 若要同步特定使用者，請使用「搜尋篩選」設定。

**填入頁面的方式為：** （非強制性）選取此選項時，使用對應的預設LDAP值填入「使用者」和「群組」設定頁面上的屬性。

**Search Filter:** (Mandatory) The search filter to use to find the record that is associated with the user. See Search Filter Syntax.

### Kerberos settings {#kerberos-settings}

If you are configuring authentication for an enterprise or hybrid domain and select Kerberos authentication, the following settings are available.

**DNS IP:** 執行AEM表單之伺服器的DNS IP位址。 On Windows, you can determine this IP address by running ipconfig /all at the command line.

**KDC主機：** 用於驗證的Active Directory伺服器的完全限定主機名或IP地址。

**Service User:** If you are using Active Directory 2003, this value is the mapping created for the service principal in the form `HTTP/<server name>`. If you are using Active Directory 2008, this value is the login ID of the service principal. 例如，假設服務承擔者名為um spnego，用戶ID為spnegodemo，映射為HTTP/example.corp.yourcompany.com。 With Active Directory 2003, you set Service User to HTTP/example.corp.yourcompany.com. With Active Directory 2008, you set Service User to spnegodemo. （請參閱使用SPNEGO啟用SSO）。

**服務領域：** Active Directory的域名

**Service Password:** Service user’s password

**Enable SPNEGO:** Enables the use of SPNEGO for single sign-on (SSO). （請參閱使用SPNEGO啟用SSO）。

### SAML設定 {#saml-settings}

If you are configuring authentication for an enterprise or hybrid domain and select SAML authentication, the following settings are available. 如需其他SAML設定的詳細資訊，請參 [閱設定SAML服務提供者設定](/help/forms/using/admin-help/configure-saml-service-provider-settings.md#configure-saml-service-provider-settings)。

**請選取要匯入的SAML身分提供者中繼資料檔案：** 按一下「瀏覽」以選取從IDP產生的SAML身分提供者中繼資料檔案，然後按一下「匯入」。 將顯示來自IDP的詳細資訊。

**標題：** EntityID所表示之URL的別名。 標題也會顯示在企業與本機使用者的登入頁面上。

**身分提供者支援用戶端基本驗證：** 當IDP使用SAML Artifact Resolution描述檔時，會使用用戶端基本驗證。 在此設定檔中，使用者管理會連線回IDP上執行的Web服務，以擷取實際的SAML斷言。 IDP可能需要驗證。 如果IDP需要驗證，請選取此選項，並在提供的方塊中指定使用者名稱和密碼。

**自訂屬性：** 可讓您指定其他屬性。 其他屬性是由新行分隔的name=value對。

The following custom properties are required if artifact binding is used.

* 新增下列自訂屬性，以指定代表AEM表單服務提供者的使用者名稱，此使用者名稱將用來驗證IDP Artifact Resolution服務。
   `saml.idp.resolve.username=<username>`

* Add the following custom property to specify the password for the user specified in `saml.idp.resolve.username`.
   `saml.idp.resolve.password=<password>`

* Add the following custom property to allow the service provider to ignore the certificate validation while establishing the connection with the Artifact Resolution service over SSL.
   `saml.idp.resolve.ignorecert=true`

### Custom settings {#custom-settings}

If you are configuring authentication for an enterprise or hybrid domain and select Custom authentication, select the name of the custom authentication provider.

## Just-in-time provisioning of users {#just-in-time-provisioning-of-users}

Just-in-time provisioning creates a user in the User Management database automatically after the user is successfully authenticated via an authentication provider. Relevant roles and groups are also assigned dynamically to the new user. You can enable just-in-time provisioning for enterprise and hybrid domains.

This procedure describes the way traditional authentication works in AEM forms:

1. When a user tries to log in to AEM forms, User Management passes their credentials sequentially to all available authentication providers. (Login credentials include username/password combination, Kerberos ticket, PKCS7 signature, and so on.)
1. The authentication provider validates the credentials.
1. The authentication provider then checks whether the user exists in the User Management database. The following statuses are possible:

   **Exists** If the user is current and unlocked, User Management returns authentication success. However, if the user is not current or is locked, User Management returns authentication failure.

   **Does not exist** User Management returns authentication failure.

   **Invalid** User Management returns authentication failure.

1. The result returned by the authentication provider is evaluated. 如果驗證提供者傳回驗證成功，則允許使用者登入。 否則，使用者管理會檢查下一個驗證提供者（步驟2-3）。
1. Authentication failure is returned if no available authentication provider validates the user credentials.

When just-in-time provisioning is enabled, new users are created dynamically in User Management if one of the authentication providers validates their credentials. (After step 3 in the procedure above.)

Without just-in-time provisioning, when a user is successfully authenticated but is not found in the User Management database, the authentication fails. Just-in-time provisioning adds a step in the authentication procedure to create the user and assign roles and groups to the user.

### Enable just-in-time provisioning for a domain {#enable-just-in-time-provisioning-for-a-domain}

1. Write a service container that implements the IdentityCreator and AssignmentProvider interfaces. (See [Programming with AEM forms](https://www.adobe.com/go/learn_aemforms_programming_63).)
1. 將服務容器部署到表單伺服器。
1. 在管理控制台中，按一下「設定>使用者管理>網域管理」。

   Select an existing domain or click New Enterprise Domain.

1. To create a domain, click New Enterprise Domain or New Hybrid Domain. To edit an existing domain, click the name of the domain.
1. Select Enable Just In Time Provisioning.

   ***note **: If the Enable Just In Time Provisioning checkbox is missing, click Home > Settings > User Management> Configuration > Advanced System Attributes and then click Reload.*

1. 新增驗證提供者。 新增驗證提供者時，在「新增驗證」畫面上，選取已註冊的Identity Creator和Assignment Provider。 (See [Configuring authentication providers](configuring-authentication-providers.md#configuring-authentication-providers).)
1. Save the domain.


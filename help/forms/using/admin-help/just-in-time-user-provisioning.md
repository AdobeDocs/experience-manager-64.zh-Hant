---
title: 即時用戶布建
seo-title: 即時用戶布建
description: 使用即時布建功能，在成功驗證後將使用者新增至「使用者管理」，並動態將相關角色和群組指派給新使用者。
seo-description: 使用即時布建功能，在成功驗證後將使用者新增至「使用者管理」，並動態將相關角色和群組指派給新使用者。
uuid: a5ad4698-70bb-487b-a069-7133e2f420c2
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_organizing_users
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e80c3f98-baa1-45bc-b713-51a2eb5ec165
exl-id: 8c205d1d-d17e-4810-8ef9-a8bdcd9aa1c2
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 0%

---

# 即時用戶預配{#just-in-time-user-provisioning}

AEM forms支援對「使用者管理」中尚未存在的使用者進行即時布建。 利用即時布建，當使用者的憑證成功驗證後，系統會自動將使用者新增至「使用者管理」。 此外，相關角色和群組會動態指派給新使用者。

## 需要及時設定用戶{#need-for-just-in-time-user-provisioning}

傳統驗證的運作方式如下：

1. 當使用者嘗試登入AEM表單時，「使用者管理」會依序將使用者的憑證傳遞至所有可用的驗證提供者。 （登錄憑據包括用戶名/密碼組合、Kerberos票證、PKCS7簽名等。）
1. 驗證提供程式驗證憑據。
1. 然後，驗證提供程式將檢查用戶是否存在於用戶管理資料庫中。 可能的結果如下：

   **存在：** 如果使用者為最新且已解除鎖定，則使用者管理會傳回驗證成功。但是，如果用戶不是當前用戶或已鎖定用戶，則User Management將返回身份驗證失敗。

   **不存在：** 使用者管理傳回驗證失敗。

   **無效：** 使用者管理傳回驗證失敗。

1. 評估驗證提供程式返回的結果。 如果驗證提供程式返回驗證成功，則允許用戶登錄。 否則，「使用者管理」會與下一個驗證提供者檢查（步驟2-3）。
1. 如果沒有可用的驗證提供程式驗證用戶憑據，則返回驗證失敗。

當實施即時布建時，如果驗證提供者之一驗證該使用者的憑證，則會在「使用者管理」中動態建立新使用者。 （在傳統驗證程式的步驟3之後，於上方說明。）

## 實施及時用戶預配{#implement-just-in-time-user-provisioning}

### 適用於準時布建{#apis-for-just-in-time-provisioning}的API

AEM forms提供下列API以供即時布建：

```as3
package com.adobe.idp.um.spi.authentication  ; 
publ ic interface IdentityCreator { 
/** 
* Tries  to create a user with the  in formation  provided in the <code>UserProvisioningBO</code> object. 
* If the user is successfully created, a valid AuthResponse is returned along with the information using which the user was created. 
* It is the responsibility of the IdentityCreator to set the User obje ct  in the cre dential map with th e  ke y  <code>UMA u thenticationUtil.authenticatedUserKey</code> 
* The credentials are available in the <code>UserProvisioningBO</code> object in the 'credentials' property. 
* If the IdentityCreator is unable to create a user due to any reason, it returns <code>null</code> 
* @param userBO An object of <code>com.adobe. i dp.um . spi.authenti c ationUserProvisioningBO</code> 
* @return */public AuthResponse create(UserProvisioningBO userBO); 
/** 
* Returns the name of the IdentityCreator which will be registered in preferences. 
* This name is used to associate the IdentityProvider with the Auth Provider Configuration in the domain. 
* @return The name of the Identity Creator which is recognized in Configuration. 
*/ 
public String getName(); 
} 
package com.adobe.idp.um.spi.authentication; 
import com.adobe.idp.um.api.infomodel.User; 
public interface AssignmentProvider { 
/** 
* Tries to assign roles or permissions or group memberships to users created via Just-in-time provisioning. 
* @param user The User created via the Just-in-time provisioning process. 
* @return a Boolean flag indicating whether the assignment was successful or not. 
*/ 
public Boolean assign(User user); 
/** 
* Returns the name of the AssignmentProvider through which it is registered under preferences. 
* This name is used to associate the AssignmentProvider with the Auth Provider Configuration in the domain. 
* @return The name of the AssignmentProvider which is recognized in Configuration. 
*/public String getName(); 
}
```

### 建立及時啟用的域{#considerations-while-creating-a-just-in-time-enabled-domain}時的考量事項

* 為混合域建立自定義`IdentityCreator`時，請確保為本地用戶指定了虛擬密碼。 請勿將此密碼欄位留空。
* 建議：使用`DomainSpecificAuthentication`驗證特定域的用戶憑據。

### 建立啟用時間的域{#create-a-just-in-time-enabled-domain}

1. 在「適時布建的API」一節中撰寫實作API的DSC。
1. 將DSC部署至表單伺服器。
1. 建立及時啟用的域：

   * 在管理控制台中，按一下「設定>使用者管理>網域管理>新企業網域」。
   * 配置域，然後選擇「啟用準時置備」。<!--Fix broken link (See Setting up and managing domains).-->
   * 添加身份驗證提供程式。 添加身份驗證提供程式時，在「新建身份驗證」螢幕上，選擇註冊的身份建立者和分配提供程式。

1. 儲存新網域。

## 幕後{#behind-the-scenes}

假設使用者嘗試登入AEM表單，且驗證提供者接受其使用者憑證。 如果用戶尚未在用戶管理資料庫中，則用戶的身份檢查將失敗。 AEM Forms現在會執行下列動作：

1. 使用驗證資料建立`UserProvisioningBO`對象，並將其放入憑據映射中。
1. 根據`UserProvisioningBO`返回的域資訊，為域提取並調用已註冊的`IdentityCreator`和`AssignmentProvider`。
1. 調用`IdentityCreator`。 如果它返回成功的`AuthResponse`，請從憑據映射中提取`UserInfo`。 將其傳遞至`AssignmentProvider`，以進行群組/角色指派，以及在建立使用者後執行任何其他後續處理。
1. 如果成功建立了用戶，則返回用戶嘗試的登錄成功。
1. 對於混合域，從提供給驗證提供者的驗證資料中提取使用者資訊。 如果成功擷取此資訊，請即時建立使用者。

>[!NOTE]
>
>即時布建功能隨附預設實施`IdentityCreator`，您可使用該實施動態建立用戶。 建立用戶時會使用與域中目錄關聯的資訊。

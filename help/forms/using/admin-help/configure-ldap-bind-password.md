---
title: 配置LDAP綁定密碼
seo-title: Configure the LDAP bind password
description: 了解如何先配置綁定密碼欄位，然後再將配置檔案導入其他系統。
seo-description: Learn how to configure the bind password field before you import the configuration file into another system.
uuid: 1ab1907c-8b55-4b6f-bd5b-49f22d78b8a8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 165b3950-b03f-4848-8361-ffb0a26d2658
exl-id: eaa2c889-d116-4209-9063-0c0b32dd8849
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 2%

---

# 配置LDAP綁定密碼{#configure-the-ldap-bind-password}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

為避免安全風險，未配置導出的配置檔案(config.xml)中的綁定密碼欄位。 將配置檔案導入其他系統之前，請確保配置此密碼。 此密碼將覆蓋儲存在資料庫中的現有密碼。 空密碼不會覆蓋現有的非空密碼值。

1. 在管理控制台中，按一下「設定>使用者管理>設定>匯入和匯出設定檔」。
1. 要將當前配置設定導出到檔案，請按一下「導出」並將配置檔案保存到其他位置。
1. 在檔案中，找出 `Domains` > *[您的網域名稱]* > `DirectoryConfigs` > `LDAPGroupConfig` 節點。 以下是範例：

   ```as3
    <node name="LDAPGroupConfig"> 
        <map> 
            <entry key="bindanonymously" value="false" />  
            <entry key="basedn" value="dc=corp,dc=adobe,dc=com" />  
            <entry key="batchSize" value="200" />  
            <entry key="binduser" value="cn=Directory Manager" />  
            <entry key="bindpassword" value="" /> 
        </map>
   ```

   輸入 `bindpassword` 並儲存您的變更。

1. 在檔案中，找出 `Domains` > *[您的網域名稱]* > `DirectoryConfigs` > `LDAPGroupConfig` > `LDAPUserConfig` 節點。 以下是範例：

   ```as3
    <node name="LDAPUserConfig"> 
        <map> 
            <entry key="bindanonymously" value="false" />  
            <entry key="batchSize" value="200" />  
            <entry key="basedn" value="dc=corp,dc=adobe,dc=com" />  
            <entry key="bindpassword" value="" /> 
            <entry key="binduser" value="cn=Directory Manager" />  
        </map>
   ```

   輸入 `bindpassword` 並儲存您的變更。

1. 若要匯入更新的檔案，請在「使用者管理」中按一下「設定>匯入和匯出設定檔」。
1. 按一下「瀏覽」以查找檔案，按一下「導入」，然後按一下「確定」。

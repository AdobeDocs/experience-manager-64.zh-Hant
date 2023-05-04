---
title: 為啟用SSL的LDAP伺服器配置用戶管理
seo-title: Configure User Management for an SSL-enabled LDAP server
description: 了解如何為啟用SSL的LDAP伺服器配置用戶管理，以使同步能夠在LDAPS上正常工作。
seo-description: Learn how  to configure User Management for an SSL-enabled LDAP server to enable synchronization to work properly over LDAPS.
uuid: 4b3f8ac7-fa38-4adf-a851-82d55fe431fe
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e6e7e2fa-579d-4b36-8598-6ced469a94b1
exl-id: 9ed22c75-bce7-4d26-a4cd-a58e41e5068e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 1%

---

# 為啟用SSL的LDAP伺服器配置用戶管理 {#configure-user-management-for-an-ssl-enabled-ldap-server}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

為了在LDAPS上正常工作，頒發證書頒發機構(CA)的LDAP證書必須存在於應用程式伺服器的Java運行時環境(JRE)中。 將證書導入應用程式伺服器的JRE快取檔案中，該檔案通常位於 *[JAVA_HOME]*/jre/lib/security/cacerts目錄。

1. 在目錄伺服器上啟用SSL。 有關詳細資訊，請參閱目錄供應商提供的文檔。
1. 從目錄伺服器導出客戶端證書。
1. 使用keytool程式將客戶端證書檔案導入AEM表單應用程式伺服器的預設Java虛擬機(JVM™)證書儲存中。 此任務的過程會因JVM和客戶端安裝路徑而異。 例如，如果您使用帶有JDK 1.5的BEA WebLogic伺服器，請在命令提示符下鍵入以下文本：

   `keytool -import -alias`*別名* `-file certificatename -keystore C:\bea\jdk15_04\jre\lib\security\cacerts`

1. 出現提示時，鍵入密碼。 (若為Java，預設密碼為 `changeit`.) 系統會顯示訊息，指出憑證匯入成功。
1. 出現提示時，鍵入 `Yes` 來信任憑證。
1. 在「用戶管理」中啟用SSL，並在配置目錄設定時，為SSL選項選擇「是」，並相應地更改埠設定。 預設埠號為636。

>[!NOTE]
>
>如果使用SSL時遇到任何問題，請使用LDAP瀏覽器檢查它在使用SSL時是否可以訪問LDAP系統。 如果LDAP瀏覽器無法訪問，則您的證書或應用程式伺服器配置不正確。 如果LDAP瀏覽器正常工作，而您仍然遇到問題，則用戶管理配置不正確。

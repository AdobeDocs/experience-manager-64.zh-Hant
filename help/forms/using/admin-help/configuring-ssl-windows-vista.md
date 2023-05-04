---
title: 在Windows Vista上配置SSL
seo-title: Configuring SSL on Windows Vista
description: 了解如何在Windows Vista上設定SSL。
seo-description: Learn how to configure SSL on Windows Vista.
uuid: 20bfcefb-ec84-4c55-bceb-6af106d883d7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 667645a0-53d0-4f9b-a0ba-cc7e366a23a1
exl-id: 8eee2ed2-8263-47f2-b928-214fd9ab5f6e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 2%

---

# 在Windows Vista上配置SSL {#configuring-ssl-on-windows-vista}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

若要在Windows Vista™上配置SSL，您需要一個帶有RSA密鑰的SSL證書以進行身份驗證。 您可以使用Java鍵工具來建立憑證。

>[!NOTE]
>
>Windows Vista無法搭配DSA金鑰運作。

您可以使用包含建立憑證和金鑰存放區所需所有資訊的單一命令，來執行keytool。

**建立SSL憑證**

1. 在命令提示字元中，導覽至 *[JAVA首頁]*/bin ，然後鍵入以下命令以建立證書和密鑰庫：

   `keytool -genkey -keyalg RSA -dname "CN=`*主機名稱* `, OU=`*群組名稱* `, O=`*公司名稱* `,L=`*城市******名稱* `, S=`*狀態* `, C=`*國家/地區代碼* `" -alias`*&quot;LC證書&quot;* `-keypass` `*key*`*_**密碼* `-keystore`*keystorename* `.keystore`

   >[!NOTE]
   >
   >取代 *[JAVA_HOME] 使用安裝JDK的目錄，並將斜體文字取代為與您的環境相對應的值。*

1. 類型 `changeit` 作為密碼。 此密碼是Java安裝的預設密碼，系統管理員可能已更改它。

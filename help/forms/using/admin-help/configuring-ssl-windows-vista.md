---
title: 在Windows Vista上配置SSL
seo-title: 在Windows Vista上配置SSL
description: 了解如何在Windows Vista上設定SSL。
seo-description: 了解如何在Windows Vista上設定SSL。
uuid: 20bfcefb-ec84-4c55-bceb-6af106d883d7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 667645a0-53d0-4f9b-a0ba-cc7e366a23a1
exl-id: 8eee2ed2-8263-47f2-b928-214fd9ab5f6e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# 在Windows Vista {#configuring-ssl-on-windows-vista}上配置SSL

若要在Windows Vista™上配置SSL，您需要一個帶有RSA密鑰的SSL證書以進行身份驗證。 您可以使用Java鍵工具來建立憑證。

>[!NOTE]
>
>Windows Vista無法搭配DSA金鑰運作。

您可以使用包含建立憑證和金鑰存放區所需所有資訊的單一命令，來執行keytool。

**建立SSL憑證**

1. 在命令提示字元中，導覽至&#x200B;*[JAVA HOME]*/bin ，然後輸入下列命令以建立憑證和金鑰存放區：

   `keytool -genkey -keyalg RSA -dname "CN=`*主* `, OU=`*機名* `, O=`*稱組名* `,L=`*稱公司名稱城市******名稱*  `, S=`** `, C=`*StateCountry代碼* `" -alias`*&quot;LC Cert&quot;* `-keypass` `*key*`*_*** `-keystore`*passwordkeystorerename* `.keystore`

   >[!NOTE]
   >
   >將&#x200B;*[JAVA_HOME]替換為安裝JDK的目錄，並將斜體文本替換為與您的環境相對應的值。*

1. 鍵入`changeit`作為密碼。 此密碼是Java安裝的預設密碼，系統管理員可能已更改它。

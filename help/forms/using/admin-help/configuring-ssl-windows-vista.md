---
title: 在Windows Vista上配置SSL
seo-title: 在Windows Vista上配置SSL
description: 瞭解如何在Windows Vista上設定SSL。
seo-description: 瞭解如何在Windows Vista上設定SSL。
uuid: 20bfcefb-ec84-4c55-bceb-6af106d883d7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 667645a0-53d0-4f9b-a0ba-cc7e366a23a1
translation-type: tm+mt
source-git-commit: d04e08e105bba2e6c92d93bcb58839f1b5307bd8
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---


# 在Windows Vista上配置SSL {#configuring-ssl-on-windows-vista}

要在Windows Vista™上配置SSL，您需要一個帶有RSA密鑰的SSL證書進行身份驗證。 您可以使用Java鍵工具來建立憑證。

>[!NOTE]
>
>Windows Vista無法與DSA金鑰搭配使用。

您可以使用單一命令來執行keytool，該命令包含建立憑證和金鑰庫所需的所有資訊。

**建立SSL憑證**

1. 在命令提示符下，導航至&#x200B;*[JAVA HOME]*/bin ，然後鍵入以下命令以建立證書和密鑰庫：

   `keytool -genkey -keyalg RSA -dname "CN=`*主* `, OU=`*機名* `, O=`*稱組名* `,L=`*稱公司名稱城市******Name*  `, S=`** `, C=`*StateCountry Code* `" -alias`*&quot;LC Cert&quot;* `-keypass` `*key*`** `-keystore`**_*keystorename* `.keystore`

   >[!NOTE]
   >
   >將&#x200B;*[JAVA_HOME]替換為安裝JDK的目錄，並將斜體文本替換為與您的環境相對應的值。*

1. 鍵入`changeit`作為口令。 此密碼是Java安裝的預設密碼，系統管理員可能已對其進行更改。


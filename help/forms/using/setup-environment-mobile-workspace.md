---
title: 設定AEM Forms應用程式的環境
seo-title: Set up environment for AEM Forms app
description: 建置和部署AEM Forms應用程式的硬體、軟體和授權。
seo-description: Hardware, software, and licenses to build and deploy the AEM Forms app.
uuid: 0c8f5259-8e9f-45ce-ade4-e14f1a41c0de
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 72c3a451-fa57-4b12-8d25-fc2e6fa98adb
exl-id: 5c60d1a6-a4a2-4131-81e6-e39a5ab07dcf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 2%

---

# 設定AEM Forms應用程式的環境 {#set-up-environment-for-aem-forms-app}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

您需要下列硬體、軟體和授權才能建置和部署AEM Forms應用程式：

## Windows裝置 {#for-windows-devices}

* Microsoft Windows 8.1或Windows 10
* Microsoft Visual Studio 2015
* Microsoft Visual Studio Tools for Apache Cordova

## 適用於iOS裝置 {#for-ios-devices}

* 運行Mac OS X 10.9.5或更高版本的基於英特爾的Apple Mac
* iOS SDK 8.4或更新版本
* Xcode版本：適用於OS X或更新版本的Xcode 6.4
* iOS開發人員企業計畫成員
* 用於發佈內部iOS應用程式的企業憑證
* Apple iPad搭配iOS 8.4或更新版本

## Android裝置 {#for-android-devices}

* Android開發工具套件（ADT套件組合），可從 [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html)
* 如果環境是在MAC系統上設定，ADT應安裝在Applications資料夾中。
* 如果ADT安裝在MAC上的任何其他位置，或環境是在Windows系統上設定，則ADT SDK路徑必須在 `local.properties` 檔案 `src\android` 資料夾（在已提取的源存檔中） `mobileworkspace-src.zip`. 在此檔案中，指向 `sdk.dir` 變數至案頭上的ADT SDK位置。

>[!NOTE]
>
>adobe-lc-mobileworkspace-src.zip包含PhoneGap SDK 5.0。請確定未預先安裝PhoneGap SDK。

---
title: 設定AEM Forms應用程式的環境
seo-title: 設定AEM Forms應用程式的環境
description: 建置和部署AEM Forms應用程式的硬體、軟體和授權。
seo-description: 建置和部署AEM Forms應用程式的硬體、軟體和授權。
uuid: 0c8f5259-8e9f-45ce-ade4-e14f1a41c0de
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 72c3a451-fa57-4b12-8d25-fc2e6fa98adb
exl-id: 5c60d1a6-a4a2-4131-81e6-e39a5ab07dcf
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---

# 設定AEM Forms應用程式的環境{#set-up-environment-for-aem-forms-app}

您需要下列硬體、軟體和授權才能建置和部署AEM Forms應用程式：

## 對於Windows設備{#for-windows-devices}

* Microsoft Windows 8.1或Windows 10
* Microsoft Visual Studio 2015
* 適用於Apache Cordova的Microsoft Visual Studio Tools

## 對於iOS設備{#for-ios-devices}

* 運行Mac OS X 10.9.5或更高版本的基於Intel的Apple Mac
* iOS SDK 8.4或更新版本
* Xcode版本：適用於OS X或更新版本的Xcode 6.4
* iOS開發人員企業計畫會員資格
* 用於發佈內部iOS應用程式的企業憑證
* 使用iOS 8.4或更新版本的Apple iPad

## 針對Android裝置{#for-android-devices}

* 可從[https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html)下載的Android開發工具套件（ADT套件組合）
* 如果環境是在MAC系統上設定的，則應將ADT安裝在Applications資料夾中。
* 如果ADT安裝在MAC上的任何其他位置，或者環境是在Windows系統上設定的，則ADT SDK路徑需要在`local.properties`檔案中更新，該檔案位於已提取的源歸檔檔案`mobileworkspace-src.zip`的`src\android`資料夾中。 在此檔案中，將`sdk.dir`變數指向案頭上的ADT SDK位置。

>[!NOTE]
>
>adobe-lc-mobileworkspace-src.zip包含PhoneGap SDK 5.0。請確定未預先安裝PhoneGap SDK。

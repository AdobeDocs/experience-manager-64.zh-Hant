---
title: 設定啟用功能
seo-title: 設定啟用功能
description: 在社群中設定啟用功能
seo-description: 在社群中設定啟用功能
uuid: 27be3128-1a7d-412e-99a9-6e3b3b0aec1c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 765a3d9b-4552-403e-872c-fdf684ac271d
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---


# 設定啟用功能{#configuring-enablement-features}

## 概覽 {#overview}

啟用功能提供建立[啟用社群](overview.md#enablement-community)的能力。

* 此功能需要額外的授權才能用於生產環境。

使用啟用功能需要：

安裝：

* **SCORMS**
可分享內容物件參考模型(SCORM)是數位學習的標準與規格集合。SCORM也定義如何將內容封裝在可轉讓的ZIP檔案中。

* **MySQLMySQL是關**
系型資料庫，主要用於SCORM追蹤和報告資料以用於「啟用」，以及用於追蹤視訊進度的表格。用於啟用功能包的SCORM需要MySQL JDBC驅動程式。

* **FFmpegFFmpeg是**
轉換和串流音訊和視訊的解決方案，安裝時會用來正確轉碼視訊 [資產](../../help/sites-authoring/default-components-foundation.md#video)。對於啟用社群，它會用於作者環境，以取得已上傳資源的中繼資料，並產生縮圖以在列出資源時顯示。

設定：

* **社群管**
理員對於啟用社群，僅限 
`Community Enablement Managers` 用戶組可被指派角色，其權限可 `*Community Site* Enablement Manager`能包括內容建立、分配和發佈環境中的成員管理。

可選配置：

* **Adobe**
Analytics與Adobe Analytics的整合新增了完整的報告功能，並支援Analytics的視訊心率新增功能。

* **Dispatcher**

## 配置步驟{#configuration-steps}

以下是啟用社群的必要步驟。

每個步驟都會連結至提供必要詳細資訊的檔案。

**在所有作者／發佈例項上：**

1. **[為](deploy-communities.md#jdbc-driver-for-mysql)**
MySQLUse Web Console(bundles)安裝JDBC驅動程式：安裝 *http://localhost:4502/system/console/*
bundles安 ** 裝SCORM套件之前

1. **[安裝SCORM套](deploy-communities.md#scorm-package)**
件使用套件管理員： 
*http://localhost:4502/crx/packmgr/*

**在任何伺服器上：**

1. **[安裝MySQL、MySQL Workbench](mysql.md)**

1. **[安裝MySQL數](mysql.md#database-setup)**
據庫執行從作者實例下載的SQL指令碼
\
   使用MySQL工作台

**在裝載作者例項的相同伺服器上：**

1. **[安裝FFmpeg](ffmpeg.md)**

**在所有作者／發佈例項上：**

1. **[配置JDBC連接](mysql.md#configure-jdbc-connections)**
池使用Web控制台(configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[配置SCORM引擎服](mysql.md#aem-communities-scormengine-service)**
務使用Web控制台(configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[配置CSRF篩](mysql.md#adobe-granite-csrf-filter)**
選器使用Web控制台(configMgr): 
*http://localhost:4502/system/console/configMgr*

**在作者實例上：**

1. （*可選*）**[設定Analytics服務](analytics.md)**
使用工具、部署、Cloud Services控制台： 
*http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[配置](ffmpeg.md#configure-ffmpeg-transcoding-service)**
Fmpeg使用工作流／型號控制台

1. **[啟用通道](deploy-communities.md#tunnel-service-on-author)**
服務使用Web控制台(configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[建立社區管](users.md#creating-community-members)** 理員對於作者環境，請使用傳統UI安全控制台： *http://localhost:4502/*
useradmincreate用戶，路徑= /home/users/community

   * 將成員添加到以下組：

      * 社群支援經理
      * 社群管理員

## Dispatcher {#dispatcher}

當部署包含[AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html)時，為了使啟用功能正常運作，`clientheader`和`filter`區段需要修改。 請參閱[配置Dispatcher for Communities](dispatcher.md#enablement)。

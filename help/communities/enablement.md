---
title: 配置啟用功能
seo-title: 配置啟用功能
description: 在Communities中設定啟用功能
seo-description: 在Communities中設定啟用功能
uuid: 27be3128-1a7d-412e-99a9-6e3b3b0aec1c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 765a3d9b-4552-403e-872c-fdf684ac271d
role: Admin
exl-id: 01cfc774-8ae1-48c0-a7e3-5836c4b39bff
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# 配置啟用功能 {#configuring-enablement-features}

## 概覽 {#overview}

啟用功能提供建立[啟用社群](overview.md#enablement-community)的功能。

* 若要在生產環境中使用，此功能需要額外的授權。

使用啟用功能需要下列項目：

安裝：

* ****
SCORMSharable Content Object Reference Model(SCORM)是數位學習的標準和規格集合。SCORM也定義了如何將內容封裝成可傳輸的ZIP檔案。

* ****
MySQLMySQL是關係資料庫，主要用於SCORM追蹤和報告啟用資料，以及用於追蹤視訊進度的表。啟用功能包的SCORM需要MySQL JDBC驅動程式。

* ****
FFmpegFFmpeg是轉換和串流音訊和視訊的解決方案，安裝後可用來正確轉碼視訊 [資產](../../help/sites-authoring/default-components-foundation.md#video)。針對啟用社群，製作環境會使用它來取得上傳資源的中繼資料，以及產生縮圖以在列出資源時顯示。

設定：

* **社**
群管理員針對啟用社群，僅限 
`Community Enablement Managers` 可將使用者群組指派給的角 `*Community Site* Enablement Manager`色，其權限可能包括發佈環境中的內容建立、指派及成員管理。

可選配置：

* **Adobe**
Analytics與Adobe Analytics的整合新增了完整的報表功能，並支援Analytics的視訊心率新增。

* **Dispatcher**

## 配置步驟 {#configuration-steps}

以下是啟用社群的必要步驟。

每個步驟都會連結至提供必要詳細資料的檔案。

**在所有製作/發佈例項上：**

1. **[為MySQLUse Web](deploy-communities.md#jdbc-driver-for-mysql)**
控制台（套件）安裝JDBC驅動程式：安裝 *http://localhost:4502/system/console/*
套件組合安裝 ** 之前，請安裝SCORM套件

1. **[安裝SCORM包](deploy-communities.md#scorm-package)**
使用包管理器： 
*http://localhost:4502/crx/packmgr/*

**在任何伺服器上：**

1. **[安裝MySQL、MySQL Workbench](mysql.md)**

1. **[安裝MySQL資](mysql.md#database-setup)**
料庫執行從製作實例下載的SQL指令碼
\
   使用MySQL Workbench

**在托管作者例項的相同伺服器上：**

1. **[安裝FFmpeg](ffmpeg.md)**

**在所有製作/發佈例項上：**

1. **[配置JDBC連接](mysql.md#configure-jdbc-connections)**
池使用Web控制台(configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[配置SCORM引擎](mysql.md#aem-communities-scormengine-service)**
服務使用Web控制台(configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[配置CSRF篩](mysql.md#adobe-granite-csrf-filter)**
選器使用Web控制台(configMgr): 
*http://localhost:4502/system/console/configMgr*

**在製作例項上：**

1. （*可選*）**[配置Analytics服務](analytics.md)**
使用工具、部署、Cloud Services控制台： 
*http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[配置](ffmpeg.md#configure-ffmpeg-transcoding-service)**
FFmpeg使用工作流/模型控制台

1. **[啟用通道](deploy-communities.md#tunnel-service-on-author)**
服務使用Web控制台(configMgr): 
*http://localhost:4502/system/console/configMgr*

1. **[建立社群](users.md#creating-community-members)** 管理員針對製作環境，請使用傳統UI安全性主控台： *http://localhost:4502/*
useradmincreate使用者，其路徑= /home/users/community

   * 將成員添加到以下組：

      * 社群培訓經理
      * Communities管理員

## Dispatcher {#dispatcher}

當部署包含[AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html)時，為了讓啟用功能正常運作，`clientheader`和`filter`區段需要修改。 請參閱[為Communities設定Dispatcher](dispatcher.md#enablement)。

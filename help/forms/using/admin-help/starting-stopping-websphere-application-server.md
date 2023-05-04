---
title: 啟動和停止WebSphere應用程式伺服器
seo-title: Starting and stopping WebSphere Application Server
description: 若要部署AEM表單產品，有數個程式需要您停止或啟動WebSphere執行個體。 本文檔介紹如何啟動和停止WebSphere應用程式伺服器。
seo-description: Several procedures require you to stop or start the instance of WebSphere where you want to deploy AEM forms products. This document describes how to start and stop the WebSphere Application Server.
uuid: e0373197-aa57-4087-933d-92a86840a11a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: bcd16691-67ab-4694-9e6b-c9d3e0c7bf0b
exl-id: 8e3bb77f-b187-42c8-a90e-fe0fee50dc34
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 2%

---

# 啟動和停止WebSphere應用程式伺服器 {#starting-and-stopping-websphere-application-server}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

若要部署AEM表單產品，有數個程式需要您停止或啟動WebSphere執行個體。 如果您不確定應用程式伺服器是否已啟動，則可以首先查看WebSphere應用程式伺服器的狀態。

## 查看WebSphere應用程式伺服器的狀態 {#view-the-status-of-websphere-application-server}

1. 從命令提示字元，前往 *[appserver根]*/bin目錄。
1. 輸入以下命令，替換 *server_name* 名稱為WebSphere應用程式伺服器：

   * (Windows) `serverStatus.bat`*server_name*
   * (Linux、UNIX)。/ `serverStatus.sh`*server_name*

## 啟動WebSphere應用程式伺服器 {#start-websphere-application-server}

1. 從命令提示字元，前往 *[appserver根]*/bin目錄。
1. 輸入以下命令，替換 *server_name* 名稱為WebSphere應用程式伺服器：

   * (Windows) `startServer.bat`*server_name*
   * (Linux、UNIX)。/ `startServer.sh`*server_name*

## 停止WebSphere應用程式伺服器 {#stop-websphere-application-server}

1. 從命令提示字元，前往 *[appserver根]*/bin目錄。
1. 輸入以下命令，替換 *server_name* 名稱為WebSphere應用程式伺服器：

   * (Windows) `stopServer.bat`*server_name*
   * (Linux、UNIX)。/ `stopServer.sh`*server_name*

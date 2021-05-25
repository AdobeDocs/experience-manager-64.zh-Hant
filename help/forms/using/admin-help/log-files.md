---
title: 記錄檔
seo-title: 記錄檔
description: 運行時或啟動錯誤等事件將記錄到應用程式伺服器日誌檔案中，可以使用任何文本編輯器開啟這些日誌檔案。
seo-description: 運行時或啟動錯誤等事件將記錄到應用程式伺服器日誌檔案中，可以使用任何文本編輯器開啟這些日誌檔案。
uuid: 6ed9fdcd-ff02-4b35-893f-09261a6a557a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: cf140483-470f-4bff-8870-304207508aab
exl-id: acce13aa-864c-4999-be5c-6d49b99d5459
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# 日誌檔案{#log-files}

運行時或啟動錯誤等事件將記錄到應用程式伺服器日誌檔案中。 如果部署到應用程式伺服器時遇到任何問題，可以使用日誌檔案幫助您找到問題。 您可以使用任何文字編輯器開啟記錄檔。

(JBoss)以下日誌檔案位於`*[appserver root]*/server/*[server]*/log`目錄中：

* boot.log
* server.log.*[yyyy-mm-dd]*
* server.log

(WebLogic)網域記錄檔位於&#x200B;*[appserverdomain]*&#x200B;目錄中，而伺服器記錄檔位於*[appserverdomain]/servers/[appservername]/logs *目錄中：

* access.log
* *[appserver name]*.log
* *[appserver name]*.out。*[增量數]*

(WebSphere)以下日誌檔案位於&#x200B;*[appserver root]*/profiles/default/logs/*[appserver name]*&#x200B;目錄中：

* SystemErr.log
* SystemOut.log
* StartServer.log

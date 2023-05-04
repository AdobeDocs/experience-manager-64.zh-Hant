---
title: 記錄檔
seo-title: Log files
description: 運行時或啟動錯誤等事件將記錄到應用程式伺服器日誌檔案中，可以使用任何文本編輯器開啟這些日誌檔案。
seo-description: Events such as run-time or startup errors are recorded to the application server log files, which can be  opened using any text editor.
uuid: 6ed9fdcd-ff02-4b35-893f-09261a6a557a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: cf140483-470f-4bff-8870-304207508aab
exl-id: acce13aa-864c-4999-be5c-6d49b99d5459
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 2%

---

# 記錄檔 {#log-files}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

運行時或啟動錯誤等事件將記錄到應用程式伺服器日誌檔案中。 如果部署到應用程式伺服器時遇到任何問題，可以使用日誌檔案幫助您找到問題。 您可以使用任何文字編輯器開啟記錄檔。

(JBoss)下列記錄檔位於 `*[appserver root]*/server/*[server]*/log` 目錄：

* boot.log
* server.log.*[yyyy-mm-dd]*
* server.log

(WebLogic)網域記錄檔位於 *[appserverdomain]* 目錄和伺服器日誌檔案位於*[appserverdomain]/servers/[appserver名稱]/logs *目錄：

* access.log
* *[appserver名稱]*.log
* *[appserver名稱]*.out。*[增量數]*

(WebSphere)下列記錄檔位於 *[appserver根]*/profiles/default/logs/*[appserver名稱]* 目錄：

* SystemErr.log
* SystemOut.log
* StartServer.log

---
title: 疑難排解AEM
seo-title: 疑難排解AEM
description: 了解疑難排解AEM的問題。
seo-description: 了解疑難排解AEM的問題。
uuid: d68e9ead-8aa6-4108-9f1e-85d7cd7a370f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 1bc19f9a-fa3f-43e3-813e-23ab0b708d43
exl-id: 34b509d5-4e80-4229-b155-40004856e87e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---

# 疑難排解AEM{#troubleshooting-aem}

以下章節說明使用AEM時可能會遇到的一些問題，以及如何疑難排解的建議。

>[!NOTE]
>
>如果您要疑難排解AEM中的編寫問題，請參閱[作者疑難排解。](/help/sites-authoring/troubleshooting.md)

>[!NOTE]
>
>遇到問題時，也值得檢查您執行個體（發行版和服務套件）的[已知問題](/help/release-notes/known-issues.md)清單。

## 管理員{#troubleshooting-scenarios-for-administrators}的故障排除方案

下表概述管理員可能需要進行疑難排解的問題：

<table> 
 <tbody> 
  <tr> 
   <td><strong>角色</strong></td> 
   <td><strong>問題 </strong></td> 
  </tr> 
  <tr> 
   <td>系統管理員</td> 
   <td><p>按兩下Quickstart Jar不會產生任何效果，或使用其他程式（例如，歸檔管理器）開啟jar檔案</p> </td> 
  </tr> 
  <tr> 
   <td><p>系統管理員</p> </td> 
   <td><p>我在CRX上執行的應用程式擲回記憶體不足錯誤</p> </td> 
  </tr> 
  <tr> 
   <td><p>系統管理員</p> </td> 
   <td><p>按兩下「AEM CM快速入門」後，瀏覽器中不會顯示「AEM歡迎」畫面</p> </td> 
  </tr> 
  <tr> 
   <td><p>系統管理員</p> <p>管理員使用者</p> </td> 
   <td><p>建立線程轉儲</p> </td> 
  </tr> 
  <tr> 
   <td><p>系統管理員</p> <p>管理員使用者</p> </td> 
   <td><p>檢查未關閉的JCR會話</p> </td> 
  </tr> 
 </tbody> 
</table>

## 安裝問題{#installation-issues}

有關以下故障排除方案的資訊，請參閱[常見安裝問題](/help/sites-deploying/troubleshooting.md#common-installation-issues):

* 按兩下Quickstart Jar不起作用，或JAR檔案與其他程式（如歸檔管理器）一起無效。
* 在CRX上運行的應用程式會擲出記憶體不足錯誤。
* 按兩下「AEM快速入門」後，瀏覽器中不會顯示「AEM歡迎」畫面。

## 分析的故障排除方法{#methods-for-troubleshooting-analysis}

### 建立線程轉儲{#making-a-thread-dump}

線程轉儲是當前活動的所有Java線程的清單。 如果AEM未正確響應，線程轉儲可幫助您識別死鎖或其他問題。

### 使用Sling線程轉儲程式{#using-sling-thread-dumper}

1. 開啟&#x200B;**AEM Web Console**;例如，在`http://localhost:4502/system/console/`。

1. 在&#x200B;**狀態**&#x200B;標籤下選擇&#x200B;**線程**。

![screen_shot_2012-02-13at43925pm](assets/screen_shot_2012-02-13at43925pm.png)

### 使用jstack（命令行）{#using-jstack-command-line}

1. 尋找AEM Java例項的PID（程式ID）。

   例如，您可以使用`ps -ef`或`jps`。

1. 執行:

   `jstack <pid>`

1. 這將顯示線程轉儲。

>[!NOTE]
>
>您可以使用`>>`輸出重定向將線程轉儲附加到日誌檔案：
>
>`jstack <pid> >> /path/to/logfile.log`

有關詳細資訊，請參閱[如何從JVM](https://helpx.adobe.com/cq/kb/TakeThreadDump.html)獲取線程轉儲文檔

### 檢查未關閉的JCR會話{#checking-for-unclosed-jcr-sessions}

為AEM WCM開發功能時，可以開啟JCR工作階段（與開啟資料庫連線類似）。 如果開啟的工作階段從未關閉，您的系統可能會出現下列症狀：

* 系統變慢了。
* 您可以看到許多CacheManager:resize日誌檔案中的所有條目；以下數字(size=&lt;x>)顯示快取的數量，每個會話開啟多個快取。
* 系統有時記憶體不足（幾小時、幾天或幾週後，具體取決於嚴重性）。

要分析未關閉的會話並找出未關閉會話的代碼，請參閱知識庫文章[分析未關閉會話](https://helpx.adobe.com/crx/kb/AnalyzeUnclosedSessions.html)。

### 使用Adobe Experience Manager Web控制台{#using-the-adobe-experience-manager-web-console}

OSGi套件組合的狀態也可提供可能問題的初步指示。

1. 開啟&#x200B;**AEM Web Console**;例如，在`http://localhost:4502/system/console/`。

1. 在&#x200B;**OSGI**&#x200B;標籤下選擇&#x200B;**套件組合**。

1. 檢查:

   * 包的狀態。 如果有非活動或未滿足，請嘗試停止並重新啟動套件組合。 如果問題持續存在，則您可能需要使用其他方法進一步調查。
   * 是否有任何包缺少依賴項。 按一下個別套件名稱即為連結（下列範例不含任何問題）即可查看此類詳細資料：

![screen_shot_2012-02-13at44706pm](assets/screen_shot_2012-02-13at44706pm.png)

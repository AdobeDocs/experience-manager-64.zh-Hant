---
title: 流程報告簡介
seo-title: Introduction to Process Reporting
description: AEM Forms on JEE Process Reporting的簡介和主要功能
seo-description: Introduction and key capabilities of AEM Forms on JEE Process Reporting
uuid: a33ea729-7e1f-4093-bdb6-b8dc3afd59a7
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 0cfe62b8-839e-414b-95e5-1bfce6a9d16a
exl-id: 279b2f89-5b91-4b8f-ab0f-8ade9b9f3932
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 2%

---

# 流程報告簡介 {#introduction-to-process-reporting}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

![process-reporting](assets/process-reporting.png)

「程式報表」是以瀏覽器為基礎的工具，可用來建立及檢視AEM Forms程式和工作的報表。

「流程報告」提供一組現成的報告，允許您篩選、查看有關長期運行的流程、流程持續時間和工作流卷的資訊。

另外，「Process Reporting」還提供一個介面，用於運行臨機查詢，並將自定義報告視圖整合到「Process Reporting」用戶介面中。

如需支援的瀏覽器清單，請參閱 [AEM Forms支援平台](/help/forms/using/aem-forms-jee-supported-platforms.md).

Process Reporting構建在以下模組上：

* 從AEM Forms資料庫讀取處理資料
* 將進程資料發佈到嵌入的進程報告儲存庫
* 提供以瀏覽器為基礎的使用者介面，以檢視報表

## 關鍵功能 {#key-capabilities}

### 隨時報告 {#always-on-reporting}

![網站管理](assets/site-management.png)

查看長運行進程的清單、進程持續時間圖表，以及使用篩選器運行自定義查詢。

「處理報表」也提供將報表和查詢資料匯出為CSV格式的選項。

### 臨機報表 {#adhoc-reports}

![打印和顏色](assets/print-&-colour.png)

使用篩選器來取得資料的特定檢視。

您可以按ID、持續時間、開始和結束日期、進程啟動器等來搜索進程或任務。

您可以結合多個篩選器以建立特定報表。

然後，您可以儲存報表篩選器，以便在之後的日期或時間執行。

### 進程/任務歷史記錄 {#process-task-history}

![檔案管理](assets/file-management.png)

AEM Forms伺服器會同時執行許多程式。 這些程式會持續從一個狀態轉換為另一個狀態。 通過定期將Forms資料發佈到Process Reporting儲存庫，Process Reporting將保留有關在AEM Forms中運行的流程的轉換資訊。

### 存取控制 {#access-control-br}

![無標題](assets/untitled.png)

「流程報告」提供基於權限的用戶介面訪問。

這表示只有具有報告權限的使用者才能存取「處理報告」使用者介面。

---
title: Request Analysis Script
seo-title: Request Analysis Script
description: 製作請求分析指令碼以便於分析access.log檔案，生成可讀報表以供後續處理
seo-description: The request analysis script is made to ease the analysis of the access.log files producing a readable report for later processing
uuid: 24eff3c6-5748-46f3-a30c-4a3a6427ce1d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 1b5e0ccf-4157-45e3-8caf-1d6739d7d9d2
exl-id: 8582bbca-c11a-4880-88ba-da22e0301dba
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 4%

---

# Request Analysis Script{#request-analysis-script}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 下載 {#download}

製作此指令碼是為了方便分析 `access.log` 產生可讀報表以供後續處理的檔案。

[取得檔案](assets/analyse-access.sh)

## 說明 {#description}

製作此指令碼是為了方便分析 `access.log` 產生可讀報表以供後續處理的檔案。

它會產生總體請求數、GET與POST、隨時間等變化的請求分配。

輸出採用Markdown語法，因此透過pandoc等工具，或透過Markdown檢視器等外掛程式在瀏覽器中顯示，將其轉換為PDF會較為容易。

它可以分析命令行上提供的自定義路徑。

從檔案內的註解中擷取，該註解會告訴您如何執行：

分析CQ `access.log` 外推各種資訊，並產生Markdown輸出， `stdout`.

## 使用狀況 {#usage}

`./analyse-access.sh access.log.2013-&ast;`

您可以提供其他自訂路徑，以便在命令列上進行分析

`/analyse-access.sh access.log.2013-&ast; /my/custom/path/1 /my/custom/path/2`

可通過簡單管道保存輸出

`./analyse-access.sh access.log.2013-&ast; | tee yr2013.md`

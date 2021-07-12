---
title: 報表主控台
seo-title: 報表主控台
description: 了解如何存取報表
seo-description: 了解如何存取報表
uuid: 580f5eb8-24b2-4404-90d4-81f7108d1ee6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 0042893e-3d2c-469e-8759-404be16e7436
role: Admin
exl-id: 766711ea-f3d3-49ab-8346-4e4477c261bd
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 5%

---

# 報表主控台 {#reports-console}

## 概覽 {#overview}

針對AEM Communities，有多種報表可從製作環境以數種方式存取。

一般而言，各種報告包括：

* [工作總攬報](#assignments-report) 表 — 啟用社 [群](overview.md#enablement-community)，提供學習者工作總攬進度的概觀，包括實施SCORM標準時的相關分數
* [檢視報表](#views-report)  — 提供任何社群網站之社群成員和網站訪客的內容檢視圖表
* [貼文報表](#posts-report)  — 提供依社群成員到任何社群網站的各種貼文類型圖表

當[Adobe Analytics啟用](sites-console.md#analytics)時，報表將包含各啟用資源在一段時間內的檢視次數、播放次數、留言數和評等數

表格報表可匯出為.csv格式，以供後續處理。

## 報表主控台 {#reporting-consoles}

### 社群網站報表 {#reports-for-community-sites}

* 從全局導航：**[!UICONTROL 導覽>社群>報表]**
* 選擇
   * **[!UICONTROL 指定任務報表]**
      * 為所選社區站點、用戶或組和分配生成報告
   * **[!UICONTROL 貼文報表]**
      * 為所選社區站點、內容類型和時段生成報告
   * **[!UICONTROL 檢視報表]**
      * 為所選社區站點、內容類型和時段生成報告
         ![chlimage_1-156](assets/chlimage_1-156.png)

### 啟用資源和學習路徑報表 {#reports-for-enablement-resources-and-learning-paths}

* 從全局導航：**[!UICONTROL 導覽>社群>資源]**
* 選擇現有啟用社區站點
   * 選擇&#x200B;**[!UICONTROL Report]**&#x200B;表徵圖以生成涵蓋所有啟用資源的報表
   * 選擇啟用學習路徑
   * 選擇&#x200B;**[!UICONTROL Report]**&#x200B;表徵圖以生成
      * 隨附的啟用資源
      * 分配給學習路徑的學習者
* 這些報表提供：
   * 表格資料，可下載為CSV
      * 識別學習者
      * 他們的狀態
      * 是否通過目錄分配或訪問
      * 評論數
      * 給定星級

如需詳細資訊，請參閱資源控制台的[報表區段](resources.md#report)。

## 指定任務報表 {#assignments-report}

「工作總攬」控制台允許按啟用社區站點、用戶或組以及工作分配篩選報表。

報告提供了有關其進展的資訊以及所提供的任何評論或評級。

![chlimage_1-157](assets/chlimage_1-157.png)

選取報表的條件：

* ****
網站選取啟用社群網站
* **[!UICONTROL 使用者或群組]**
   * 選擇用戶為一個學習者生成報告
   * 選擇「組」為一組學習者生成報告
通道服務將從發佈環境訪問成員和成員組
* ****
工作分配從分配給所選學習者的啟用資源中選擇

選擇&#x200B;**[!UICONTROL Generate]**&#x200B;以建立報表：

![chlimage_1-158](assets/chlimage_1-158.png)

## 檢視報表 {#views-report}

「檢視」主控台可讓您在指定時段內，依社群功能在頁面檢視時產生報表。

![chlimage_1-159](assets/chlimage_1-159.png)

選取報表的條件：

* ****
網站選擇社群網站
* **[!UICONTROL 內]**
容類型可以選擇全部內容或選擇站點上存在的功能之一
* 時間範圍
選擇以下選項之一：
   * 過去 7 天
   * 過去 30 天
   * 過去 90 天
   * 去年

選擇&#x200B;**[!UICONTROL Generate]**&#x200B;以建立報表：

![chlimage_1-160](assets/chlimage_1-160.png)

## 貼文報表 {#posts-report}

「貼文」主控台可針對特定時段內社群功能的貼文數產生報表。

![chlimage_1-161](assets/chlimage_1-161.png)

選取報表的條件：

* ****
網站選擇社群網站
* **[!UICONTROL 內]**
容類型可以選擇全部內容或選擇站點上存在的功能之一
* 時間範圍
選擇以下選項之一：
   * 過去 7 天
   * 過去 30 天
   * 過去 90 天
   * 去年

選擇&#x200B;**[!UICONTROL Generate]**&#x200B;以建立報表：

![chlimage_1-162](assets/chlimage_1-162.png)

## 疑難排解 {#troubleshooting}

### 未列出社區站點 {#no-community-sites-listed}

如果未列出社群網站，請確定已為網站啟用Adobe Analytics。 如果選擇分配的報表，請確保分配函式位於社區站點的結構中。

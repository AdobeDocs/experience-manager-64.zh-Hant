---
title: 報表主控台
seo-title: Reports Console
description: 了解如何存取報表
seo-description: Learn how to access reports
uuid: 580f5eb8-24b2-4404-90d4-81f7108d1ee6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 0042893e-3d2c-469e-8759-404be16e7436
role: Admin
exl-id: 766711ea-f3d3-49ab-8346-4e4477c261bd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 7%

---

# 報表主控台 {#reports-console}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 概觀 {#overview}

針對AEM Communities，有多種報表可從製作環境以數種方式存取。

一般而言，各種報告包括：

* [分配報告](#assignments-report) - [啟用社群](overview.md#enablement-community)，提供學習者指派工作的進度概覽，包括若實作SCORM標準時的相關分數
* [檢視報表](#views-report)  — 提供任何社區站點的社區成員和站點訪客的內容視圖圖表
* [貼文報表](#posts-report)  — 按社區成員向任何社區站點提供各種類型的帖子圖表

當 [Adobe Analytics已啟用](sites-console.md#analytics)，報表將包含每個啟用資源隨著時間的檢視次數、播放次數、留言數和評等

表格報表可匯出為.csv格式，以供後續處理。

## 報表主控台 {#reporting-consoles}

### 社群網站報表 {#reports-for-community-sites}

* 從全局導航： **[!UICONTROL 導覽>社群>報表]**
* 選擇
   * **[!UICONTROL 指定任務報表]**
      * 為所選社區站點、用戶或組和分配生成報告
   * **[!UICONTROL 貼文報表]**
      * 為所選社區站點、內容類型和時段生成報告
   * **[!UICONTROL 檢視報表]**
      * 為所選社區站點、內容類型和時段生成報告
         ![chlimage_1-156](assets/chlimage_1-156.png)

### 啟用資源和學習路徑報表 {#reports-for-enablement-resources-and-learning-paths}

* 從全局導航： **[!UICONTROL 導覽>社群>資源]**
* 選擇現有啟用社區站點
   * 選擇 **[!UICONTROL 報表]** 表徵圖，生成涵蓋所有啟用資源的報表
   * 選擇啟用學習路徑
   * 選擇 **[!UICONTROL 報表]** 表徵圖
      * 隨附的啟用資源
      * 分配給學習路徑的學習者
* 這些報表提供：
   * 表格資料，可下載為CSV
      * 識別學習者
      * 他們的狀態
      * 是否通過目錄分配或訪問
      * 評論數
      * 給定星級

如需詳細資訊，請參閱 [報表區段](resources.md#report) （在資源控制台中）。

## 指定任務報表 {#assignments-report}

「工作總攬」控制台允許按啟用社區站點、用戶或組以及工作分配篩選報表。

報告提供了有關其進展的資訊以及所提供的任何評論或評級。

![chlimage_1-157](assets/chlimage_1-157.png)

選取報表的條件：

* **[!UICONTROL 網站]**
選取啟用社群網站
* **[!UICONTROL 使用者或群組]**
   * 選擇用戶為一個學習者生成報告
   * 選擇組為一組學習者生成報告通道服務將訪問發佈環境中的成員和成員組
* **[!UICONTROL 分配]**
從指派給所選學員的培訓資源中進行選擇

選擇 **[!UICONTROL 產生]** 若要建立報表：

![chlimage_1-158](assets/chlimage_1-158.png)

## 檢視報表 {#views-report}

「檢視」主控台可讓您在指定時段內，依社群功能在頁面檢視時產生報表。

![chlimage_1-159](assets/chlimage_1-159.png)

選取報表的條件：

* **[!UICONTROL 網站]**
選擇社區站點
* **[!UICONTROL 內容類型]**
可以選擇「全部內容」或選擇站點上存在的功能之一
* 時間範圍選擇以下選項之一：
   * 過去 7 天
   * 過去 30 天
   * 過去 90 天
   * 去年

選擇 **[!UICONTROL 產生]** 若要建立報表：

![chlimage_1-160](assets/chlimage_1-160.png)

## 貼文報表 {#posts-report}

「貼文」主控台可針對特定時段內社群功能的貼文數產生報表。

![chlimage_1-161](assets/chlimage_1-161.png)

選取報表的條件：

* **[!UICONTROL 網站]**
選擇社區站點
* **[!UICONTROL 內容類型]**
可以選擇「全部內容」或選擇站點上存在的功能之一
* 時間範圍選擇以下選項之一：
   * 過去 7 天
   * 過去 30 天
   * 過去 90 天
   * 去年

選擇 **[!UICONTROL 產生]** 若要建立報表：

![chlimage_1-162](assets/chlimage_1-162.png)

## 疑難排解 {#troubleshooting}

### 未列出社區站點 {#no-community-sites-listed}

如果未列出社群網站，請確定已為網站啟用Adobe Analytics。 如果選擇分配的報表，請確保分配函式位於社區站點的結構中。

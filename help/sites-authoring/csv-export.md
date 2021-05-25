---
title: 匯出為 CSV
seo-title: 匯出為 CSV
description: 將您頁面的相關資訊匯出至本機系統上的CSV檔案
seo-description: 將您頁面的相關資訊匯出至本機系統上的CSV檔案
uuid: aa03adac-bbfb-4566-a153-25fe6f6843dd
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: d4473758-674a-42d6-923a-b536f7f9c1f7
exl-id: 52eb9c2f-ce29-4622-8726-802ac40246d4
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 27%

---

# 匯出為 CSV{#export-to-csv}

**建立CSV** 可匯出至您本機系統上的CSV檔案，以匯出頁面的相關資訊。

* 下載的檔案名為`export.csv`
* 內容取決於您選擇的屬性。
* 可以定義路徑與導出深度。

>[!NOTE]
>
>會使用瀏覽器的下載功能和預設目的地。

「建 立CSV匯出 」精靈可讓您選擇：

* 要匯出的屬性

   * 中繼資料

      * 修改時間
      * 已發佈
   * 分析

      * 頁面檢視
      * 不重複訪客
      * 頁面逗留時間


* 深度

   * 父路徑
   * 僅導向子項
   * 其他層級的子項
   * 層級

產生的`export.csv`檔案可在Excel或任何其他相容的應用程式中開啟。

![chlimage_1-58](assets/chlimage_1-58.png)

瀏覽&#x200B;**Sites**&#x200B;主控台時（在「清單」檢視中），可使用建立&#x200B;**CSV匯出**&#x200B;選項：它是&#x200B;**建立**&#x200B;下拉式功能表的選項：

![screen_shot_2018-03-21at154719](assets/screen_shot_2018-03-21at154719.png)

若要建立CSV匯出：

1. 開啟 **Sites** Console，視需要導覽至所需位置。
1. 從工具列中，依序選擇&#x200B;**Create**&#x200B;和&#x200B;**CSV Export**&#x200B;以開啟精靈：

   ![screen_shot_2018-03-21at154758](assets/screen_shot_2018-03-21at154758.png)

1. 選擇要導出的必需屬性。
1. 選擇 **建立**。

---
title: 匯出為 CSV
seo-title: Export to CSV
description: 將您頁面的相關資訊匯出至本機系統上的CSV檔案
seo-description: Export information about your pages to a CSV file on your local system
uuid: aa03adac-bbfb-4566-a153-25fe6f6843dd
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: d4473758-674a-42d6-923a-b536f7f9c1f7
exl-id: 52eb9c2f-ce29-4622-8726-802ac40246d4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 26%

---

# 匯出為 CSV{#export-to-csv}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

**建立CSV匯出** 可讓您將頁面的相關資訊匯出至本機系統上的CSV檔案。

* 下載的檔案稱為 `export.csv`
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

產生的 `export.csv` 檔案可在Excel或任何其他相容的應用程式中開啟。

![chlimage_1-58](assets/chlimage_1-58.png)

建立 **CSV匯出** 選項在瀏覽時可用 **網站** 控制台（在清單視圖中）:這是 **建立** 下拉式功能表：

![screen_shot_2018-03-21at154719](assets/screen_shot_2018-03-21at154719.png)

若要建立CSV匯出：

1. 開啟 **Sites** Console，視需要導覽至所需位置。
1. 從工具列中選取 **建立** then **CSV匯出** 要開啟嚮導：

   ![screen_shot_2018-03-21at154758](assets/screen_shot_2018-03-21at154758.png)

1. 選擇要導出的必需屬性。
1. 選擇 **建立**。

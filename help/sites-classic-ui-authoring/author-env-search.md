---
title: 搜尋
seo-title: Search
description: AEM的製作環境提供多種搜尋內容的機制，視資源類型而定。
seo-description: The author environment of AEM provides various mechanisms for searching for content, dependent on the resource type.
uuid: b50c8144-1993-441d-8303-fcb6b0f24376
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: b20e0f78-9ae4-47ba-8e9a-452a0a78b663
exl-id: 9c1d8969-6aa6-41b9-a797-3e6431475fc6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 2%

---

# 搜尋{#search-features}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

AEM的製作環境提供多種搜尋內容的機制，視資源類型而定。

>[!NOTE]
>
>在製作環境之外，也可使用其他機制進行搜尋，例如 [查詢產生器](/help/sites-developing/querybuilder-api.md) 和 [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

## 搜尋基本知識 {#search-basics}

若要存取搜尋面板，請按一下 **搜尋** 標籤。

![chlimage_1-140](assets/chlimage_1-140.png)

「搜尋」面板可讓您在所有網站頁面上進行搜尋。 它包含下列項目的欄位和小工具：

* **全文**:搜索指定的文本
* **在之後/之前修改**:僅搜尋在特定日期之間變更的頁面
* **範本**:僅根據指定的範本搜尋那些頁面
* **標籤**:僅搜尋具有指定標籤的頁面

>[!NOTE]
>
>當您的執行個體設定為 [Lucene搜索](/help/sites-deploying/queries-and-indexing.md) 您可以在 **全文**:
>
>* [萬用字元](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Wildcard_Searches)
>* [布林運算子](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Boolean_operators)
>
>* [規則運算式](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Regexp_Searches)
>* [欄位分組](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Field_Grouping)
>* [Boosting](https://lucene.apache.org/core/5_3_1/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#Boosting_a_Term)
>


按一下 **搜尋** 在窗格底部。 按一下 **重設** 來清除搜尋條件。

## 篩選 {#filter}

在各種位置，可設定（並清除）篩選器，以深入鑽研並調整檢視：

![chlimage_1-141](assets/chlimage_1-141.png)

## 查找和替換 {#find-and-replace}

在 **網站** 主控台 **查找和替換** 功能表選項，可讓您在網站的區段內搜尋和取代字串的多個例項。

1. 選擇根頁面或資料夾，以在其中執行查找和替換操作。
1. 選擇 **工具** then **查找和替換**:

   ![screen_shot_2012-02-15at120346pm](assets/screen_shot_2012-02-15at120346pm.png)

1. 此 **查找和替換** 對話框執行下列操作：

   * 確認尋找動作應從哪個根路徑開始
   * 定義要找到的詞
   * 定義應替代該詞的術語
   * 指出搜尋是否應區分大小寫
   * 指示是否只應找到整字（否則也找到子字串）

   按一下 **預覽** 列出找到詞語的位置。 您可以選取/清除要取代的特定例項：

   ![screen_shot_2012-02-15at120719pm](assets/screen_shot_2012-02-15at120719pm.png)

1. 按一下 **取代** 來實際取代所有例項。 系統會要求您確認動作。

查找和替換servlet的預設範圍涵蓋以下屬性：

* `jcr:title`
* `jcr:description`
* `jcr:text`
* `text`

範圍可使用Apache Felix Web Management Console進行變更(例如， `http://localhost:4502/system/console/configMgr`)。 選擇 `CQ WCM Find Replace Servlet (com.day.cq.wcm.core.impl.servlets.FindReplaceServlet)` 並視需要設定範圍。

>[!NOTE]
>
>在標準AEM安裝中，「尋找和取代」會使用Lucene來執行搜尋功能。
>
>Lucene索引長度多達16k的字串屬性。 系統不會搜尋超出此範圍的字串。

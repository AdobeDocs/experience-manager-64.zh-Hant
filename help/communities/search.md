---
title: 搜尋功能
seo-title: Search Feature
description: 向Communities站點添加和配置搜索
seo-description: Adding and configuring Search to a Communities site
uuid: ca633456-911f-447f-881e-653533125d5f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 3acac082-efbe-4995-b374-851cb9aaf62d
exl-id: 15d8bd59-397e-4bd3-b0a2-b6893c015798
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 3%

---

# 搜尋功能 {#search-feature}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

搜尋功能可與論壇等各種其他功能搭配使用，以提供搜尋內容的功能。

新增搜尋社群成員所輸入貼文的能力時(也稱為使用者產生的內容(UGC))，有兩個元件： [ `Search`](#search-features) 和 [ `Search Results`](#search-results).

包含 `Search Results` 元件支援搜索和顯示結果。

包含 `Search`元件提供啟動搜尋的位置，結果會顯示在 `Search Results` 頁面。

搜尋功能可與任何其他允許網站訪客和成員檢視內容的功能搭配使用。

## 搜尋 {#search-features}

### 新增搜尋至頁面 {#add-search-to-a-page}

新增 `Search` 在製作模式中，使用元件瀏覽器來尋找 `Communities / Search` 並將其拖曳到頁面上。 使用 `Search` 需要 `Search Results.`

如需必要資訊，請造訪 [Communities元件基本知識](basics.md).

當需要的用戶端程式庫時， `cq.social.hbs.search`，此為方法 `Search` 元件隨即顯示。

![chlimage_1-373](assets/chlimage_1-373.png)

### 配置添加的搜索 {#configure-the-added-search}

選取已放置的 `Search` 要存取的元件並選取 `Configure` 表徵圖，開啟「編輯」對話框。

![chlimage_1-374](assets/chlimage_1-374.png)

在 **[!UICONTROL 搜尋設定]** 索引標籤，指定當訪客輸入查詢時，要如何搜尋路徑。

![chlimage_1-375](assets/chlimage_1-375.png)

* **[!UICONTROL 搜尋路徑]**
使用「新增項目」按鈕新增搜尋路徑，將限制內容搜尋。 例如，若要將搜尋限制在特定論壇，請選取放在頁面中的論壇元件：

   * `/content/community-components/en/forum/jcr:content/content/forum`

* **[!UICONTROL 結果頁]**
結果會顯示在使用瀏覽器選取包含的頁面所指定的個別頁面上 
`Search Results` 元件.

## 搜尋結果 {#search-results}

### 將搜尋結果新增至頁面 {#add-search-results-to-a-page}

新增 `Search Results` 在製作模式中，使用元件瀏覽器來尋找

* `Communities / Search Results`

並將其拖曳到頁面上。 與搜尋元件不同，不需要第二個頁面，因為結果會顯示在相同的頁面上。

若在網站的其他地方使用「搜尋」，則此頁面具有 `Search Results` 可設定為 `Result Page` 適用於任何或所有例項 `Search`.

如需必要資訊，請造訪 [Communities元件基本知識](basics.md).

當需要的用戶端程式庫時， `cq.social.hbs.search`，此為方法 `Search Result` 元件隨即出現：

![chlimage_1-376](assets/chlimage_1-376.png)

### 配置添加的搜索結果 {#configure-the-added-search-result}

選取已放置的 `Search Results` 要存取的元件並選取 `Configure` 表徵圖，開啟「編輯」對話框。

![chlimage_1-377](assets/chlimage_1-377.png)

在 **[!UICONTROL 搜尋結果設定]** 索引標籤，則可指定當訪客輸入查詢時，要納入搜尋的路徑。

![chlimage_1-378](assets/chlimage_1-378.png)

* **[!UICONTROL 每頁搜索結果]**
定義每頁顯示的主題/貼文數。 預設為10。

* **[!UICONTROL 搜尋路徑]**
使用「新增項目」按鈕新增搜尋路徑，將限制內容搜尋。

## 其他資訊 {#additional-information}

如需詳細資訊，請參閱 [搜尋要點](search-implementation.md) 頁面。

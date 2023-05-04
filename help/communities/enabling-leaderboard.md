---
title: 排行榜功能
seo-title: Leaderboard Feature
description: 將排行榜元件新增至頁面
seo-description: Adding a Leaderboard component to a page
uuid: 2a766b63-3ab4-44cd-8a26-629a71b837ea
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 1e96d388-8517-4a84-bb0a-d49567eb4bdf
exl-id: 1ebe0cbb-33be-4101-92e3-64253a7f7f31
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 8%

---

# 排行榜功能 {#leaderboard-feature}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 簡介 {#introduction}

此 `Leaderboard` 元件可讓您根據獲得的分數（基本分數）或其專業知識（進階分數）對成員進行排名，以了解成員在社群中的互動方式。

在頁面上加入排行榜元件之前，必須先設定 [社群計分和徽章](implementing-scoring.md).

本檔案的本節說明

* 新增 `Leaderboard` 元件 [社群網站](overview.md#community-sites)

* 的組態設定 `Leaderboard` 元件

## 向頁面新增排行榜 {#adding-a-leaderboard-to-a-page}

新增 `Leaderboard` 在製作模式中，找到元件至頁面

* `Communities / Leaderboard`

並將其拖曳到頁面上。

如需必要資訊，請造訪 [Communities元件基本知識](basics.md).

首次放置在社群網站的頁面時，元件的顯示方式如下：

![chlimage_1-8](assets/chlimage_1-8.png)

## 配置排行榜 {#configuring-leaderboard}

選取已放置的 `Leaderboard` 要存取的元件並選取 `Configure` 表徵圖，開啟「編輯」對話框。

![chlimage_1-9](assets/chlimage_1-9.png) ![chlimage_1-10](assets/chlimage_1-10.png)

### 設定標籤 {#settings-tab}

在 **[!UICONTROL 設定]** 頁簽，指定與成員相關的資訊：

* **[!UICONTROL 顯示名稱]**
要為展示板顯示的描述性名稱，反映為顯示徽章和分數而選取的規則。

   預設為 `Leaderboard`，如果未輸入任何內容。

* **[!UICONTROL 徽章]**
如果勾選此選項，排行榜中會包含徽章圖示的欄。

   預設為未勾選。

* **[!UICONTROL 徽章名稱]**
如果選中，則排行榜中將包含徽章名稱的列。

   預設為未勾選。

* **[!UICONTROL 使用頭像]**
如果選中，成員的頭像影像將包含在排行榜中，位於其成員配置檔案的名稱連結旁。

   預設為未勾選。

### 規則標籤 {#rules-tab}

在 **[!UICONTROL 規則]** 頁簽、社區站點及其評分和標籤規則

* **[!UICONTROL 規則位置]**
（必要）設定計分/徽章規則的位置。

* **[!UICONTROL 計分規則]**
（必要）產生要顯示的分數的特定規則。

* **[!UICONTROL 徽章規則]**
（必要）產生徽章以顯示的特定規則。

* **[!UICONTROL 顯示限制]**
每頁要顯示的成員數。

   預設為10。

## 範例：參加者領導委員會 {#example-participants-leaderboard}

此排行榜會報告應用基本評分規則的結果。

排行榜元件配置：

* **[!UICONTROL 設定]** 標籤：

   * 顯示名稱 = `Participation Board`
   * `checked`:

      * 徽章
      * 徽章名稱
      * 使用頭像

* **[!UICONTROL 規則]** 標籤：

   * 規則位置 = `/content/sites/communities/jcr:content`
   * 得分規則 = `/etc/community/scoring/rules/forums-scoring`
   * 徽章規則 = `/etc/community/badging/rules/reference-badging`
   * 顯示限制 = `10`

![chlimage_1-11](assets/chlimage_1-11.png)

## 範例：專家領導委員會 {#example-experts-leaderboard}

此排行榜會報告應用高級評分規則的結果。

排行榜元件配置：

* **[!UICONTROL 設定]** 標籤：

   * 顯示名稱 = `Expertise Board`
   * `checked`:

      * 徽章
      * 使用頭像

* **[!UICONTROL 規則]** 標籤：

   * 規則位置 = `/content/sites/communities/jcr:content`
   * 得分規則 = `/etc/community/scoring/rules/adv-forums-scoring`
   * 徽章規則 = `/etc/community/badging/rules/adv-forums-badging`
   * 顯示限制 = `10`

![chlimage_1-12](assets/chlimage_1-12.png)

## 其他資訊 {#additional-information}

如需詳細資訊，請參閱 [排行榜要點](leaderboard.md) 頁面。

有關建立規則的指示，請參閱 [社群計分和徽章](implementing-scoring.md) 頁面。

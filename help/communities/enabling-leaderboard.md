---
title: 排行榜功能
seo-title: 排行榜功能
description: 將Leaderboard元件添加到頁面
seo-description: 將Leaderboard元件添加到頁面
uuid: 2a766b63-3ab4-44cd-8a26-629a71b837ea
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 1e96d388-8517-4a84-bb0a-d49567eb4bdf
translation-type: tm+mt
source-git-commit: 1bbd917ef20c4a618e93af66ffe8a6cfc8448e78
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 6%

---


# 排行榜功能 {#leaderboard-feature}

## 簡介 {#introduction}

該 `Leaderboard` 元件通過根據獲得的點數（基本分數）或其專業知識（高級分數）對成員進行排名，從而獲得成員在社區內如何交互的感知。

在將排行榜元件包括在頁面之前，必須配置社 [區評分和標章](implementing-scoring.md)。

本節說明

* 將元件 `Leaderboard` 新增至社 [群網站](overview.md#community-sites)

* 元件的配置設 `Leaderboard` 置

## 新增排行榜至頁面 {#adding-a-leaderboard-to-a-page}

若要在作 `Leaderboard` 者模式下將元件新增至頁面，請找出元件

* `Communities / Leaderboard`

並將它拖曳至頁面上的位置。

如需必要資訊，請造 [訪Communities Components Basics](basics.md)。

首次放置在社群網站頁面時，元件的顯示方式如下：

![chlimage_1-8](assets/chlimage_1-8.png)

## 配置排行榜 {#configuring-leaderboard}

選擇要訪問 `Leaderboard` 的已放置元件，並選 `Configure` 擇開啟編輯對話框的表徵圖。

![chlimage_1-9](assets/chlimage_1-9.png) ![chlimage_1-10](assets/chlimage_1-10.png)

### 「設定」頁籤 {#settings-tab}

在「設 **[!UICONTROL 置]** 」頁籤下，指定將顯示與成員相關的資訊：

* **[!UICONTROL 顯示名]**&#x200B;稱要顯示展示板的描述性名稱，反映為顯示標章和分數所選取的規則。

   如果未輸 `Leaderboard`入任何內容，則預設為。

* **[!UICONTROL 徽章]**&#x200B;如果勾選，則排行榜中會包含徽章圖示的欄。

   預設為未勾選。

* **[!UICONTROL 徽章名稱]**&#x200B;如果選中此選項，則會在排行榜中包含徽章名稱的列。

   預設為未勾選。

* **[!UICONTROL 使用頭像]**：如果勾選此選項，成員的頭像影像將包含在排行榜中，位於其成員配置檔案的名稱連結旁邊。

   預設為未勾選。

### 規則標籤 {#rules-tab}

在「規 **[!UICONTROL 則]** 」索引標籤下，社群網站及其計分和標籤規則

* **[!UICONTROL 規則位置]**（必要）設定計分／簽章規則的位置。

* **[!UICONTROL 計分規則]**（必要）產生要顯示的分數的特定規則。

* **[!UICONTROL 標籤規則]**（必要）產生要顯示的標籤的特定規則。

* **[!UICONTROL 顯示限]**&#x200B;制每頁要顯示的成員數。

   預設值為10。

## 範例： 參與者領導委員會 {#example-participants-leaderboard}

此排行榜會報告套用基本計分規則的結果。

Leaderboard元件配置：

* **[!UICONTROL 「設定]** 」頁籤：

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

## 範例： 專家排行榜 {#example-experts-leaderboard}

此排行榜會報告套用進階計分規則的結果。

Leaderboard元件配置：

* **[!UICONTROL 「設定]** 」頁籤：

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

如需詳細資訊，請參閱開發人 [員的Leaderboard](leaderboard.md) Essentials頁面。

管理員的「社群計分與標章」頁面 [中提供建立規則的指示](implementing-scoring.md) 。

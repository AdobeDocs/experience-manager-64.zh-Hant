---
title: 排行榜功能
seo-title: 排行榜功能
description: 將排行榜元件新增至頁面
seo-description: 將排行榜元件新增至頁面
uuid: 2a766b63-3ab4-44cd-8a26-629a71b837ea
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 1e96d388-8517-4a84-bb0a-d49567eb4bdf
exl-id: 1ebe0cbb-33be-4101-92e3-64253a7f7f31
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 6%

---

# 排行榜功能{#leaderboard-feature}

## 簡介 {#introduction}

`Leaderboard`元件提供了通過根據獲得的分數（基本分數）或其專業知識（高級分數）對成員進行排名來了解成員在社區中如何交互的能力。

在頁面上加入排行榜元件之前，必須配置[Communities Scoring和Badges](implementing-scoring.md)。

本檔案的本節說明

* 將`Leaderboard`元件新增至[社群網站](overview.md#community-sites)

* `Leaderboard`元件的組態設定

## 向頁面{#adding-a-leaderboard-to-a-page}添加排行榜

若要在製作模式中將`Leaderboard`元件新增至頁面，請找出元件

* `Communities / Leaderboard`

並將其拖曳到頁面上。

如需必要資訊，請造訪[Communities Components Basics](basics.md)。

首次放置在社群網站的頁面時，元件的顯示方式如下：

![chlimage_1-8](assets/chlimage_1-8.png)

## 配置排行榜{#configuring-leaderboard}

選取要存取的放置`Leaderboard`元件，並選取開啟編輯對話方塊的`Configure`圖示。

![chlimage_1-9](assets/chlimage_1-9.png) ![chlimage_1-10](assets/chlimage_1-10.png)

### 設定頁簽{#settings-tab}

在&#x200B;**[!UICONTROL 設定]**&#x200B;頁簽下，指定顯示與成員相關的資訊：

* **[!UICONTROL 顯示]**
名稱要為展示板顯示的描述性名稱，反映為顯示徽章和分數而選擇的規則。

   如果未輸入任何內容，則預設為`Leaderboard`。

* ****
徽章如果勾選此選項，排行榜中會包含徽章圖示的欄。

   預設為未勾選。

* **[!UICONTROL 徽章]**
名稱如果選中此選項，則該徽章名稱的列將包含在排行榜中。

   預設為未勾選。

* **[!UICONTROL 使]**
用頭像如果選中，成員的頭像影像將包含在排行榜中，位於其成員配置檔案的名稱連結旁。

   預設為未勾選。

### 規則頁簽{#rules-tab}

在&#x200B;**[!UICONTROL Rules]**&#x200B;標籤下，社區站點及其分數和標籤規則

* **[!UICONTROL 規則位置]**
（必要）設定計分/徽章規則的位置。

* **[!UICONTROL 計分規則]**
（必要）產生要顯示之分數的特定規則。

* **[!UICONTROL 徽章規則]**
（必要）產生要顯示之徽章的特定規則。

* **[!UICONTROL 顯示]**
LimitNumber要顯示的每頁成員數。

   預設為10。

## 範例：參與者領導板{#example-participants-leaderboard}

此排行榜會報告應用基本評分規則的結果。

排行榜元件配置：

* **** 設定標籤：

   * 顯示名稱 = `Participation Board`
   * `checked`:

      * 徽章
      * 徽章名稱
      * 使用頭像

* **** 規則標籤：

   * 規則位置 = `/content/sites/communities/jcr:content`
   * 得分規則 = `/etc/community/scoring/rules/forums-scoring`
   * 徽章規則 = `/etc/community/badging/rules/reference-badging`
   * 顯示限制 = `10`

![chlimage_1-11](assets/chlimage_1-11.png)

## 範例：專家領導板{#example-experts-leaderboard}

此排行榜會報告應用高級評分規則的結果。

排行榜元件配置：

* **** 設定標籤：

   * 顯示名稱 = `Expertise Board`
   * `checked`:

      * 徽章
      * 使用頭像

* **** 規則標籤：

   * 規則位置 = `/content/sites/communities/jcr:content`
   * 得分規則 = `/etc/community/scoring/rules/adv-forums-scoring`
   * 徽章規則 = `/etc/community/badging/rules/adv-forums-badging`
   * 顯示限制 = `10`

![chlimage_1-12](assets/chlimage_1-12.png)

## 其他資訊 {#additional-information}

如需詳細資訊，請參閱開發人員的[ Leaderboard Essentials](leaderboard.md)頁面。

管理員的[Communities計分和徽章](implementing-scoring.md)頁面上提供建立規則的說明。

---
title: 徽章主控台
seo-title: 徽章主控台
description: 「社群徽章」控制台可讓您新增自訂徽章，這些徽章可在獲得（授予）或成員在社群中承擔特定角色（已指派）時顯示給成員
seo-description: 「社群徽章」控制台可讓您新增自訂徽章，這些徽章可在獲得（授予）或成員在社群中承擔特定角色（已指派）時顯示給成員
uuid: 9eeba240-f0d4-4937-baba-8bac0e0b2a36
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 4194278f-5127-4105-b181-60961c7a1def
role: Admin
exl-id: b6aa9d73-4e20-446a-a1fc-78f8968d6844
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 4%

---

# 徽章主控台 {#badges-console}

## 關於徽章 {#about-badges}

「社區徽章」控制台提供添加自定義徽章的功能，這些徽章可以在獲得（授予）成員或成員在社區中承擔特定角色（已分配）時顯示。

### 徽章可見性 {#badge-visibility}

目前，社群成員所掙得或獲指派的徽章，將與其名稱和頭像一起顯示在下列位置：

* 設定檔
* [論壇](forum.md)
* [QnA](working-with-qna.md)
* [排行榜](enabling-leaderboard.md)
* [創意力](ideation-feature.md)

在製作環境中，若要觸及「徽章」主控台

* 從全局導航：**[!UICONTROL 工具>社區>徽章]**

此主控台會顯示目前可用的徽章，以及可從中新增徽章。

![chlimage_1-242](assets/chlimage_1-242.png)

## 建立預算 {#create-badge}

通過上傳合適的小影像（72dpi，高度在26-32像素之間）並提供名稱來建立徽章。 徽章影像儲存在`/etc/community/badging/images`的存放庫中，並自動複製到發佈環境。

如果發佈環境是發佈者的伺服器陣列，則必須配置[用戶同步](sync.md)。

![chlimage_1-243](assets/chlimage_1-243.png)

* **[!UICONTROL 上傳影像]**

   （*必要*）JPEG或PNG格式中，建議大小為32 x 32像素、72dpi的徽章影像。

* **[!UICONTROL 名稱]**

   （*必要*）徽章名稱。 它是預設的`Display Name`以及儲存庫節點名稱。 如果`Name`不是有效的儲存庫節點名稱，則會修改該名稱。

* **[!UICONTROL 顯示名稱]**

   （*選用*）要在UI中顯示徽章的名稱。 預設值為`Name`輸入的未更改文本。

* **[!UICONTROL 說明]**

   （*選用*）徽章的說明。

## 其他資訊 {#additional-information}

有關設定評分和徽章規則的詳細資訊，請參閱[評分和徽章](implementing-scoring.md)。

有關管理成員的徽章，請參閱[成員控制台](members.md)。

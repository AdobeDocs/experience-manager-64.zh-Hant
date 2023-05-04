---
title: 排行榜要點
seo-title: Leaderboard Essentials
description: 排行榜功能概述
seo-description: Leaderboard feature overview
uuid: 815a6928-b147-496d-9751-13159ad1304d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7449f99e-77d7-4c0f-96d5-b67d5e1f124a
exl-id: 20c16e96-2ba8-4f2d-8cfa-8cd804e3441f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 7%

---

# 排行榜要點 {#leaderboard-essentials}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

本頁提供使用排行榜功能的基本資訊。

在頁面上加入排行榜元件之前，必須先設定 [社群計分和徽章](implementing-scoring.md). 另請參閱 [計分和徽章要點](configure-scoring.md).

## 用戶端的要點 {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>社交/遊戲化/元件/hbs/排行榜</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>包括</strong></a></td> 
   <td>否</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.gamification.hbs.leaderboard</td> 
  </tr>
  <tr>
   <td> <strong>範本</strong></td> 
   <td> /libs/social/gamification/components/hbs/leaderboard/leaderboard.hbs<br /> </td> 
  </tr>
  <tr>
   <td> <strong>cs</strong></td> 
   <td> /libs/social/gamification/components/hbs/leaderboard/clientlibs/leaderboard.css</td> 
  </tr>
  <tr>
   <td><strong> 屬性</strong></td> 
   <td>請參閱 <a href="enabling-leaderboard.md">排行榜功能</a></td> 
  </tr>
 </tbody>
</table>

* [用戶端自訂](client-customize.md)

### 檔案庫功能 {#file-library-function}

包含 [排行榜功能](functions.md#leaderboard-function)，包含已設定的 `leaderboard` 元件。

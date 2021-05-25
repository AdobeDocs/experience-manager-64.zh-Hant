---
title: 活動資料流要點
seo-title: 活動資料流要點
description: 由成員執行的最近活動的清單或單個內容線程上最近活動的清單
seo-description: 由成員執行的最近活動的清單或單個內容線程上最近活動的清單
uuid: 6e4734bb-52a8-4670-b665-e640108b036e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 8cc04993-4021-4cb7-b973-5afc4da1ed11
exl-id: 74dcbefa-e670-419b-af9b-b3d3c593ebaa
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 1%

---

# 活動流要點{#activity-stream-essentials}

在社區成員中籤名的活動，例如張貼到論壇或部落格，被收集到流中，該流可以通過活動流元件的配置以各種方式被過濾和顯示。

當社群成員關注感興趣的帖子或其他社區成員時，跟隨能力將添加另一組活動。

所有[社區站點](overview.md#communitiessites)都包含登錄成員的用戶配置檔案頁，該用戶配置檔案頁將以相同方式顯示成員活動。

## 概念 {#concepts}

*活動流*&#x200B;是成員執行的最近活動的清單，或單個內容線程（如論壇主題或部落格）上最近活動的清單。

成員可以跟隨另一個個人或內容，跟隨活動流。

*新聞摘要*&#x200B;是活動流的合併，隨後是成員到單個流。

[社交圖表](essentials-socialgraph.md)擷取一個成員與另一個成員的下列關係。

## 客戶端{#essentials-for-client-side}的要點

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>社交/活動資料流/元件/hbs/活動資料流</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>包括</strong></a></td> 
   <td>否</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.hbs.activitystreams</td> 
  </tr>
  <tr>
   <td> <strong>範本</strong></td> 
   <td> /libs/social/activitystreams/components/hbs/activitystreams/activitystreams.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity-title.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity.hbs</td> 
  </tr>
  <tr>
   <td> <strong>cs</strong></td> 
   <td> /libs/social/activitystreams/components/hbs/activitystreams/clientlibs/activitystreams.css</td> 
  </tr>
  <tr>
   <td><strong> 屬性</strong></td> 
   <td>請參閱<a href="activities.md">活動資料流功能</a></td> 
  </tr>
 </tbody>
</table>

* [用戶端自訂](client-customize.md)

## 伺服器端{#essentials-for-server-side}的要點

* [活動資料流API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/api/package-frame.html)

* [活動資料流接聽程式API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/listener/api/package-frame.html)

* [伺服器端自訂](server-customize.md)

### 活動資料流功能 {#activity-stream-function}

包含[活動流函式](functions.md#activity-stream-function)的社區站點結構包括配置的`activity streams`元件。

---
title: QnA要點
seo-title: QnA Essentials
description: 問題與解答論壇功能
seo-description: Questions and answers forum feature
uuid: c718a8e3-b3bd-4db9-8c0f-6dd973d40583
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ceace3aa-78a5-485e-b519-630479e087d8
exl-id: 99f8afda-1771-471b-bd0c-99960a453bc9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 3%

---

# QnA要點 {#qna-essentials}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

本頁提供使用問題和答案(QnA)論壇功能的基本資訊。

## 用戶端的要點 {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> resourceType</td> 
   <td>social/qna/components/hbs/qnaforum</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component">包括</a></td> 
   <td>否</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md">clientllibs</a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.voting<br /> cq.social.hbs.qna</td> 
  </tr>
  <tr>
   <td> 範本</td> 
   <td> /libs/social/qna/components/hbs/qnaforum/qnaforum.hbs<br /> /libs/social/qna/components/hbs/qnaforum/activity-title.hbs</td> 
  </tr>
  <tr>
   <td> cs</td> 
   <td> /libs/social/qna/components/hbs/qnaforum/clientlibs/qnaforum.css</td> 
  </tr>
  <tr>
   <td> 屬性</td> 
   <td>請參閱 <a href="working-with-qna.md">QnA論壇功能</a></td> 
  </tr>
 </tbody>
</table>

* [用戶端自訂](client-customize.md)

## 伺服器端的Essentials {#essentials-for-server-side}

* [QnA API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/qna/client/api/package-summary.html)

* [QnA端點](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/qna/client/endpoints/package-summary.html)

* [伺服器端自訂](server-customize.md)

### QnA 功能 {#qna-function}

包含 [QnA函式](functions.md#qna-function) 將配置 `QnA` 元件，以及影響協調和標籤的設定。 QnA函式支援標識 [特權成員用戶組](users.md#privileged-members-group).

### 訪問QnA論壇帖子(UGC) {#accessing-qna-forum-posts-ugc}

UGC應使用其中一種標準的協調方法來協調。\
請參閱 [協調使用者產生的內容](moderate-ugc.md).

自AEM 6.1社群起，請使用 [公用商店](working-with-srp.md) 針對UGC包括可程式化地存取UGC，而無論選擇的儲存選項（例如ASRP、MSRP或JSRP）。

**UGC在存放庫中的位置和格式可能會變更，恕不另行警告**.

請參閱：

* [儲存資源提供程式概述](srp.md)  — 簡介和存放庫使用概觀
* [SRP和UGC要點](srp-and-ugc.md) - SRP實用程式方法和示例
* [使用SRP存取UGC](accessing-ugc-with-srp.md)  — 編碼准則
* [SocialUtils重構](socialutils.md)  — 將已棄用的實用程式方法映射到當前SRP實用程式方法

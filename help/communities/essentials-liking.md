---
title: 按贊要點
seo-title: 按贊要點
description: 按贊元件概觀
seo-description: 按贊元件概觀
uuid: 89f16859-c901-4090-8e16-363b95c508de
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: f176c42b-b16b-42c9-af22-4b6421de5a90
pagetitle: Liking Essentials
exl-id: 509d1fb4-a88d-4438-a618-ba063adb6fb9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 1%

---

# 按贊要點{#liking-essentials}

按贊元件（[tally](tally.md)子類）是一個有用的工具，它允許成員通過僅選擇心臟表徵圖來表達對特定內容的正面意見。

允許將贊元件的多個例項放在相同頁面上；每個實例都必須配置唯一的`tally name`屬性。

不支援匿名張貼贊。 網站訪客必須註冊並登入才能參與按贊。 已登入的訪客（成員）可隨時切換為開啟或關閉。

## 客戶端{#essentials-for-client-side}的要點

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td>social/tally/components/hbs/like</td> 
  </tr> 
  <tr> 
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>包括</strong></a></td> 
   <td>是 — 可在<i>design </i>模式中編輯屬性</td> 
  </tr> 
  <tr> 
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td> 
   <td> cq.social.hbs.liking</td> 
  </tr> 
  <tr> 
   <td> <strong>範本</strong></td> 
   <td><p> /libs/social/tally/components/hbs/liking/liking.hbs<br /> /libs/social/tally/components/hbs/liking/activity-icon.hbs<br /> /libs/social/tally/components/hbs/liking/activity-title.hbs</p> </td> 
  </tr> 
  <tr> 
   <td><strong>CSS</strong></td> 
   <td> /libs/social/tally/components/hbs/liking/clientlibs/likingcomponent.css</td> 
  </tr> 
  <tr> 
   <td><strong>屬性</strong></td> 
   <td><p>請參閱<a href="liking.md">使用贊</a></p> </td> 
  </tr> 
 </tbody> 
</table>

* [用戶端自訂](client-customize.md)

## 伺服器端{#essentials-for-server-side}的要點

* [Tally API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [計數端點](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [伺服器端自訂](server-customize.md)

### 訪問已發佈的投票(UGC){#accessing-posted-voting-ugc}

UGC應使用其中一種標準的協調方法來協調。\
請參閱[協調使用者產生的內容](moderate-ugc.md)。

自AEM 6.1社群起，UGC使用[公用商店](working-with-srp.md)包括程式化存取UGC，而不論選擇的儲存選項（例如ASRP、MSRP或JSRP）。

**UGC在存放庫中的位置和格式可能會變更，恕不另行警告**。

請參閱：

* [儲存資源提供程式概述](srp.md)  — 簡介和儲存庫使用概述
* [SRP和UGC Essentials](srp-and-ugc.md)  - SRP公用程式方法與範例
* [使用SRP存取UGC](accessing-ugc-with-srp.md)  — 編碼准則
* [SocialUtils重構](socialutils.md)  — 將棄用的公用程式方法對應至目前的SRP公用程式方法

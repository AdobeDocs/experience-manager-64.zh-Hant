---
title: 部落格要點
seo-title: Blog Essentials
description: 部落格概述
seo-description: Blog overview
uuid: ce0885de-6276-47a2-8f6c-358f0beb2b89
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: de8d0e6d-827b-45fe-a538-d3fe1dec8427
exl-id: 8cff0b7b-c120-462f-8fce-13822073eabb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 2%

---

# 部落格要點 {#blog-essentials}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

自AEM 6.1社群起，部落格是社群活動。 部落格文章現在會從發佈環境發佈，之前，部落格文章只能在作者環境中建立並發佈。

部落格文章現在可由任何社群成員建立，除非僅限於有權限的成員。

本頁面提供使用部落格功能的基本資訊。

>[!NOTE]
>
>部落格功能的基礎結構是日誌功能。

## 用戶端的要點 {#essentials-for-client-side}

部落格功能由兩個主要元件組成，可借由新增 [部落格功能](functions.md#blog-function) 或在製作編輯模式中將元件新增至頁面。

### 部落格 {#blog}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/journal/components/hbs/journal</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>包括</strong></a></td> 
   <td>否</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.voting<br /> cq.social.hbs.journal</td> 
  </tr>
  <tr>
   <td> <strong>範本</strong></td> 
   <td> /libs/social/journal/components/hbs/journal/journal.hbs<br /> /libs/social/journal/components/hbs/entry_topic/list-item.hbs</td> 
  </tr>
  <tr>
   <td> <strong>cs</strong></td> 
   <td> /libs/social/journal/components/hbs/journal/clientlibs/journal.css</td> 
  </tr>
  <tr>
   <td><strong> 屬性</strong></td> 
   <td>請參閱 <a href="blog-feature.md">部落格功能</a></td> 
  </tr>
 </tbody>
</table>

### 部落格則欄 {#blog-sidebar}

| **resourceType** | social/journal/components/hbs/sidebar |
|---|---|
| [**包括**](scf.md#add-or-include-a-communities-component) | 否 |
| [**clientllibs**](clientlibs.md) | cq.social.hbs.journal_sidebar |
| **範本** | /libs/social/journal/components/hbs/sidebar/sidebar.hbs |
| **cs** | /libs/social/journal/components/hbs/sidebar/clientlibs/sidebar.css |
| **屬性** | 請參閱 [部落格功能](blog-feature.md) |

* [用戶端自訂](client-customize.md)

## 伺服器端的Essentials {#essentials-for-server-side}

* [部落格API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/api/package-summary.html)

* [部落格端點](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/endpoints/package-summary.html)

* [伺服器端自訂](server-customize.md)

### 部落格功能 {#blog-function}

包含 [Bog函式](functions.md#blog-function) 將配置 `Blog` 和 `Blog Sidebar` 元件。 部落格功能支援識別 [特權成員用戶組](users.md#privileged-members-group).

### 訪問部落格條目(UGC) {#accessing-blog-entries-ugc}

UGC應使用其中一種標準的協調方法來協調。\
請參閱 [協調使用者產生的內容](moderate-ugc.md).

自AEM 6.1社群起，請使用 [公用商店](working-with-srp.md) 針對UGC包括可程式化地存取UGC，而無論選擇的儲存選項（例如ASRP、MSRP或JSRP）。

**UGC在存放庫中的位置和格式可能會變更，恕不另行警告**.

請參閱：

* [儲存資源提供程式概述](srp.md)  — 簡介和存放庫使用概觀
* [SRP和UGC要點](srp-and-ugc.md) - SRP實用程式方法和示例
* [使用SRP存取UGC](accessing-ugc-with-srp.md)  — 編碼准則
* [SocialUtils重構](socialutils.md)  — 將已棄用的實用程式方法映射到當前SRP實用程式方法

## 主要發行者 {#primary-publisher}

當部署為發佈伺服器陣列時，必須識別要輪詢已排程發佈之文章的主要發佈者。

請參閱 [主要發行者](deploy-communities.md#primary-publisher) 以取得更多詳細資訊。

## 允許多媒體 {#allowing-rich-media}

AEM平台會封鎖其他網站的連結，以防止XSS攻擊，如

* [Protect反對跨網站指令碼(XSS)](../../help/sites-developing/security.md#protect-against-cross-site-scripting-xss)

自AEM 6.2起，先前手動進行的必要修改將包含在預設AntiSamy設定檔案中。

透過選取 `Embed Media from External Sites` 圖示：  ![chlimage_1-471](assets/chlimage_1-471.png)

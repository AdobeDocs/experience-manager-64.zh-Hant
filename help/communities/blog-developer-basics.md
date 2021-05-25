---
title: 部落格要點
seo-title: 部落格要點
description: 部落格概述
seo-description: 部落格概述
uuid: ce0885de-6276-47a2-8f6c-358f0beb2b89
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: de8d0e6d-827b-45fe-a538-d3fe1dec8427
exl-id: 8cff0b7b-c120-462f-8fce-13822073eabb
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 2%

---

# 部落格要點{#blog-essentials}

自AEM 6.1社群起，部落格是社群活動。 部落格文章現在會從發佈環境發佈，之前，部落格文章只能在作者環境中建立並發佈。

部落格文章現在可由任何社群成員建立，除非僅限於有權限的成員。

本頁面提供使用部落格功能的基本資訊。

>[!NOTE]
>
>部落格功能的基礎結構是日誌功能。

## 客戶端{#essentials-for-client-side}的要點

部落格功能由兩個主要元件組成，可透過新增[Blog函式](functions.md#blog-function)或在作者編輯模式中將元件新增至頁面來使用。

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
   <td>請參閱<a href="blog-feature.md">部落格功能</a></td> 
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
| **屬性** | 請參閱[部落格功能](blog-feature.md) |

* [用戶端自訂](client-customize.md)

## 伺服器端{#essentials-for-server-side}的要點

* [部落格API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/api/package-summary.html)

* [部落格端點](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/endpoints/package-summary.html)

* [伺服器端自訂](server-customize.md)

### 部落格功能 {#blog-function}

包含[Bog函式](functions.md#blog-function)的社區站點結構將配置`Blog`和`Blog Sidebar`元件。 Blog函式支援標識[特權成員用戶組](users.md#privileged-members-group)。

### 訪問部落格條目(UGC){#accessing-blog-entries-ugc}

UGC應使用其中一種標準的協調方法來協調。\
請參閱[協調使用者產生的內容](moderate-ugc.md)。

自AEM 6.1社群起，UGC使用[公用商店](working-with-srp.md)包括程式化存取UGC，而不論選擇的儲存選項（例如ASRP、MSRP或JSRP）。

**UGC在存放庫中的位置和格式可能會變更，恕不另行警告**。

請參閱：

* [儲存資源提供程式概述](srp.md)  — 簡介和儲存庫使用概述
* [SRP和UGC Essentials](srp-and-ugc.md)  - SRP公用程式方法與範例
* [使用SRP存取UGC](accessing-ugc-with-srp.md)  — 編碼准則
* [SocialUtils重構](socialutils.md)  — 將棄用的公用程式方法對應至目前的SRP公用程式方法

## 主發佈者{#primary-publisher}

當部署為發佈伺服器陣列時，必須識別要輪詢已排程發佈之文章的主要發佈者。

如需詳細資訊，請參閱[主要發佈者](deploy-communities.md#primary-publisher) 。

## 允許富媒體{#allowing-rich-media}

AEM平台會封鎖其他網站的連結，以防止XSS攻擊，如

* [Protect反對跨網站指令碼(XSS)](../../help/sites-developing/security.md#protect-against-cross-site-scripting-xss)

自AEM 6.2起，先前手動進行的必要修改將包含在預設AntiSamy設定檔案中。

選取`Embed Media from External Sites`圖示，即可將多媒體內嵌在部落格文章中： ![chlimage_1-471](assets/chlimage_1-471.png)

---
title: Blog Essentials
seo-title: Blog Essentials
description: 部落格概觀
seo-description: 部落格概觀
uuid: ce0885de-6276-47a2-8f6c-358f0beb2b89
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: de8d0e6d-827b-45fe-a538-d3fe1dec8427
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 2%

---


# Blog Essentials {#blog-essentials}

自AEM 6.1 Communities起，部落格就是社群活動。 現在，部落格文章會從發佈環境張貼，以前，部落格文章只能在作者環境中建立並發佈。

部落格文章現在可由任何社群成員建立，除非僅限於特權成員。

本頁提供使用部落格功能的基本資訊。

>[!NOTE]
>
>部落格功能的基礎結構是日誌功能。

## 用戶端基本功能 {#essentials-for-client-side}

部落格功能由兩個主要元件組成，這些元件可透過新增 [Blog函式](functions.md#blog-function) ，或在作者編輯模式中將元件新增至頁面來使用。

### 部落格 {#blog}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/journal/components/hbs/journal</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>included</strong></a></td> 
   <td>否</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.porting<br /> cq.social.hbs.journal</td> 
  </tr>
  <tr>
   <td> <strong>模板</strong></td> 
   <td> /libs/social/journal/components/hbs/journal/journal.hbs<br /> /libs/social/journal/components/hbs/entry_topic/list-item.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
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
| [**included **](scf.md#add-or-include-a-communities-component) | 否 |
| [**clientlibs **](clientlibs.md) | cq.social.hbs.journal_sidebar |
| **模板** | /libs/social/journal/components/hbs/sidebar/sidebar.hbs |
| **css** | /libs/social/journal/components/hbs/sidebar/clientlibs/sidebar.css |
| **屬性** | 請參閱 [部落格功能](blog-feature.md) |

* [用戶端自訂](client-customize.md)

## 伺服器端的基本功能 {#essentials-for-server-side}

* [部落格API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/api/package-summary.html)

* [部落格端點](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/endpoints/package-summary.html)

* [伺服器端自訂](server-customize.md)

### 部落格功能 {#blog-function}

包含 [Bog函式的社群網站結構](functions.md#blog-function) ，將具有 `Blog` 設定和元 `Blog Sidebar` 件。 Blog函式支援標識特權 [成員用戶組](users.md#privileged-members-group)。

### 訪問部落格條目(UGC) {#accessing-blog-entries-ugc}

UGC應使用其中一種標準的協調方法來協調。\
請參 [閱協調使用者產生的內容](moderate-ugc.md)。

自AEM 6.1 Communities起，使用UGC的 [公用商店](working-with-srp.md) ，包括程式化存取UGC，不論選擇的儲存選項（例如ASRP、MSRP或JSRP）。

**UGC在儲存庫中的位置和格式可能會變更，但不會發出警告**。

請參閱：

* [儲存資源提供方概述](srp.md) -簡介和儲存庫使用概述
* [SRP和UGC Essentials](srp-and-ugc.md) - SRP實用程式方法和示例
* [使用SRP存取UGC](accessing-ugc-with-srp.md) —— 編碼准則
* [SocialUtils重構](socialutils.md) -將不建議使用的公用程式方法對應至目前的SRP公用程式方法

## 主要發行者 {#primary-publisher}

當部署為發佈群組時，必須識別將針對排程發佈的文章進行民調問答的主要發佈者。

如需詳 [細資訊，請參閱](deploy-communities.md#primary-publisher) 「主要發行者」。

## 允許豐富式媒體 {#allowing-rich-media}

AEM平台會封鎖其他網站的連結，以防止XSS攻擊，如

* [防止跨網站指令碼(XSS)](../../help/sites-developing/security.md#protect-against-cross-site-scripting-xss)

自AEM 6.2起，先前需要手動進行的修改會包含在預設的AntiSamy設定檔案中。

透過選取圖示，豐富式媒體內嵌在部落格 `Embed Media from External Sites` 文章中：  ![chlimage_1-471](assets/chlimage_1-471.png)


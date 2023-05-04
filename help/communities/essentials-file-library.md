---
title: 檔案庫要點
seo-title: File Library Essentials
description: 使用檔案庫功能
seo-description: Working with the file library feature
uuid: 0630f13e-97b4-4f93-9dce-07f559287c29
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 9019b967-fff8-4dda-bc5a-fd4a3e14a4ef
exl-id: 0e9d508e-d7dc-478a-99c0-c6885bcdcb81
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 3%

---

# 檔案庫要點 {#file-library-essentials}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

本頁面提供使用檔案程式庫功能的基本資訊。

## 用戶端的要點 {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/filelibrary/components/hbs/filelibrary</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>包括</strong></a></td> 
   <td>否</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.voting<br /> cq.social.hbs.filelibrary</td> 
  </tr>
  <tr>
   <td> <strong>範本</strong></td> 
   <td> /libs/social/filelibrary/components/hbs/filelibrary/filelibrary.hbs<br /> /libs/social/filelibrary/components/hbs/folder/folder.hbs<br /> /libs/social/filelibrary/components/hbs/folder/item.hbs<br /> /libs/social/filelibrary/components/hbs/document/document.hbs<br /> /libs/social/filelibrary/components/hbs/document/item.hbs<br /> </td> 
  </tr>
  <tr>
   <td> <strong>cs</strong></td> 
   <td> /libs/social/filelibrary/components/hbs/filelibrary/clientlibs/filelibrary.css</td> 
  </tr>
  <tr>
   <td><strong> 屬性</strong></td> 
   <td>請參閱 <a href="file-library.md">檔案庫功能</a></td> 
  </tr>
 </tbody>
</table>

* [用戶端自訂](client-customize.md)

## 伺服器端的Essentials {#essentials-for-server-side}

* [檔案庫API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/filelibrary/client/api/package-summary.html)

* [檔案庫端點](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/filelibrary/client/endpoints/package-summary.html)

* [伺服器端自訂](server-customize.md)

### 檔案庫功能 {#file-library-function}

包含 [檔案庫函式](functions.md#file-library-function)，包含已設定的 `file library` 元件。

### 訪問為檔案庫(UGC)發佈的注釋 {#accessing-comments-posted-for-file-libraries-ugc}

UGC應使用其中一種標準的協調方法來協調。\
請參閱 [協調使用者產生的內容](moderate-ugc.md).

自AEM 6.1社群起，請使用 [公用商店](working-with-srp.md) 針對UGC包括可程式化地存取UGC，而無論選擇的儲存選項（例如ASRP、MSRP或JSRP）。

**UGC在存放庫中的位置和格式可能會變更，恕不另行警告**.

請參閱：

* [儲存資源提供程式概述](srp.md)  — 簡介和存放庫使用概觀
* [SRP和UGC要點](srp-and-ugc.md) - SRP實用程式方法和示例
* [使用SRP存取UGC](accessing-ugc-with-srp.md)  — 編碼准則
* [SocialUtils重構](socialutils.md)  — 將已棄用的實用程式方法映射到當前SRP實用程式方法

---
title: 將建立通信UI與您的自訂入口網站整合
seo-title: Integrating Create Correspondence UI with your custom portal
description: 了解如何將建立通信UI與您的自訂入口網站整合
seo-description: Learn how to integrate create correspondence UI with your custom portal
uuid: 4ae9c5fb-bb9d-46d8-be84-455f386ab443
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: cb232931-60b7-4956-bc77-10636c19325e
feature: Correspondence Management
exl-id: 8b1bbd85-66ba-4e96-917a-d768d84a417f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 4%

---

# 將建立通信UI與您的自訂入口網站整合 {#integrating-create-correspondence-ui-with-your-custom-portal}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 概觀 {#overview}

本文詳細說明如何將建立通信解決方案與您的環境整合。

## 基於URL的調用 {#url-based-invocation}

若要從自訂入口網站呼叫「建立通信」應用程式，一種方式是使用下列要求參數準備URL:

* 字母模板的標識符（使用cmLetterId參數），或字母模板的名稱（使用cmLetterName參數）

* 從所需資料源（使用cmDataUrl參數）中提取的XML資料的URL。

例如，自訂入口網站會將URL準備為\
`https://[server]:[port]/[contextPath]/aem/forms/createcorrespondence.html?random=[timestamp]&cmLetterId=[letter identifier]&cmDataUrl=[data URL]`，可以是入口網站連結的href。\
如果入口網站的Letter範本名稱為，則URL可能為\
`https://[server]:[port]/content/cm/createcorrespondence.html?cmLetterName=[letter name]&cmDataUrl=[data URL]`。

>[!NOTE]
>
>以這種方式呼叫不安全，因為必要的參數會以GET要求的形式傳遞，方法是在URL中顯示相同的（清楚顯示）。

>[!NOTE]
>
>呼叫「建立通信」應用程式前，請儲存並上傳資料，以在指定dataURL呼叫「建立通信」UI。 這可以從自訂入口網站本身，或透過其他後端程式來完成。

## 內嵌資料型叫用 {#inline-data-based-invocation}

呼叫「建立通信」應用程式的另一種（且更安全）方式，可能只是點擊URL: `https://[server]:[port]/[contextPath]/aem/forms/createcorrespondence.html`時，以POST請求的形式傳送參數和資料以呼叫建立通信應用程式（隱藏給一般使用者）。 這也表示您現在可以內嵌傳遞建立通信應用程式的XML資料（作為相同請求的一部分，使用cmData參數），這在先前的方法中不可能/不理想。

### 用於指定字母的參數 {#parameters-for-specifying-letter}

<table> 
 <tbody>
  <tr>
   <td><strong>名稱</strong></td> 
   <td><strong>類型</strong></td> 
   <td><strong>說明</strong></td> 
  </tr>
  <tr>
   <td>cmLetterInstanceId</td> 
   <td>字串</td> 
   <td>信函例項的識別碼。</td> 
  </tr>
  <tr>
   <td>cmLetterName</td> 
   <td>字串</td> 
   <td><p>信函範本的識別碼。 </p> <p>如果伺服器上有多個同名的CM字母，則在URL中使用cmLetterName參數會擲回錯誤「有多個字母與名稱存在」。 在這種情況下，請在URL中使用cmLetterId參數，而非cmLetterName。</p> </td> 
  </tr>
  <tr>
   <td>cmLetterId</td> 
   <td>字串</td> 
   <td>字母模板的名稱。</td> 
  </tr>
 </tbody>
</table>

表中的參數順序指定用於載入字母的參數的首選項。

### 指定XML資料源的參數 {#parameters-for-specifying-the-xml-data-source}

<table> 
 <tbody>
  <tr>
   <td><strong>名稱</strong></td> 
   <td><strong>類型</strong></td> 
   <td><strong>說明</strong></td> 
  </tr>
  <tr>
   <td>cmDataUrl<br /> </td> 
   <td>URL</td> 
   <td>使用基本通訊協定（例如cq、ftp、http或檔案）從來源檔案取得XML資料。<br /> </td> 
  </tr>
  <tr>
   <td>cmLetterInstanceId</td> 
   <td>字串</td> 
   <td>使用信函例項中可用的xml資料。</td> 
  </tr>
  <tr>
   <td>cmUseTestData</td> 
   <td>布林值</td> 
   <td>重複使用資料字典中附加的測試資料。</td> 
  </tr>
 </tbody>
</table>

表中的參數順序指定用於載入XML資料的參數的首選項。

### 其他參數 {#other-parameters}

<table> 
 <tbody>
  <tr>
   <td><strong>名稱</strong></td> 
   <td><strong>類型</strong></td> 
   <td><strong>說明</strong></td> 
  </tr>
  <tr>
   <td>cmPreview<br /> </td> 
   <td>布林值</td> 
   <td>在預覽模式中開啟信函的值為true<br /> </td> 
  </tr>
  <tr>
   <td>隨機</td> 
   <td>時間戳記</td> 
   <td>解決瀏覽器快取問題。</td> 
  </tr>
 </tbody>
</table>

如果您對cmDataURL使用http或cq通訊協定，http/cq的URL應可匿名存取。

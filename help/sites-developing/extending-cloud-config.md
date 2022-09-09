---
title: 雲端服務設定
description: 您可以擴充現有例項，以建立您自己的設定。
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
exl-id: d2b8503e-8ac1-4617-ad76-b05d1e80a6b6
source-git-commit: bbc13d64a33d9033e04fb4f37d60bcfe223be337
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 3%

---

# 雲端服務設定{#cloud-service-configurations}

配置旨在提供用於儲存服務配置的邏輯和結構。

您可以擴充現有例項，以建立您自己的設定。

## 概念 {#concepts}

在開發配置時使用的原則基於以下概念：

* 服務/適配器用於檢索配置。
* 設定（例如屬性/段落）繼承自父項。
* 依路徑從分析節點參考。
* 可輕鬆擴充。
* 具有彈性，可應付更複雜的配置，例如 [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics).
* 支援相依性(例如 [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics) 外掛程式需要 [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics) 設定)。

## 結構 {#structure}

配置的基本路徑是：

`/etc/cloudservices`。

對於每種類型的配置，將提供模板和元件。這樣，配置模板就可以滿足自定義後的大多數需求。

要為新服務提供配置，您需要：

* 在中建立服務頁面

   `/etc/cloudservices`

* 下方：

   * 配置模板
   * 配置元件

範本和元件必須繼承 `sling:resourceSuperType` 從基礎模板：

`cq/cloudserviceconfigs/templates/configpage`

或基元

`cq/cloudserviceconfigs/components/configpage`

服務提供商還應提供服務頁：

`/etc/cloudservices/<service-name>`

### 範本 {#template}

您的範本將擴充基礎範本：

`cq/cloudserviceconfigs/templates/configpage`

並定義 `resourceType` 指向自訂元件。

```xml
/libs/cq/analytics/templates/sitecatalyst
sling:resourceSuperType = cq/cloudserviceconfigs/templates/configpage
allowedChildren = /libs/cq/analytics/templates/sitecatalyst
allowedPaths = /etc/cloudservices/analytics/*, /etc/cloudservices/analytics/.*
componentReference = cq/analytics/components/sitecatalyst
jcr:content/
cq:designPath = /etc/designs/cloudservices
sling:resourceType = cq/analytics/components/sitecatalystpage

/libs/cq/analytics/templates/generictracker
sling:resourceSuperType = cq/cloudservices/templates/configpage
allowedChildren = /libs/cq/analytics/templates/generictracker
allowedPaths = /etc/cloudservices/analytics/*, /etc/cloudservices/analytics/.*
jcr:content/
cq:designPath = /etc/designs/cloudservices
sling:resourceType = cq/analytics/components/generictrackerpage
```

### 元件 {#components}

元件應擴充基礎元件：

`cq/cloudserviceconfigs/templates/configpage`

```xml
/libs/cq/analytics/components/sitecatalystpage

/libs/cq/analytics/components/generictrackerpage
```

設定範本和元件後，您可以在下方新增子頁面，以新增設定：

`/etc/cloudservices/<service-name>`

### 內容模型 {#content-model}

內容模型儲存為 `cq:Page` 在下：

`/etc/cloudservices/<service-name>(/*)`

```xml
/etc/cloudservices
/etc/cloudservices/service-name
/etc/cloudservices/service-name/config
/etc/cloudservices/service-name/config/inherited-config
```

配置儲存在子節點下 `jcr:content`.

* 修正在對話方塊中定義的屬性應儲存在 `jcr:node` 直接。
* 動態元素(使用 `parsys` 或 `iparsys`)使用子節點來儲存元件資料。

```xml
/etc/cloudservices/service/config/jcr:content as nt:unstructured
propertyname
*
par/component/ as cq:Component
propertyname
*
```

### API {#api}

如需API的參考檔案，請參閱 [com.day.cq.wcm.webservicesupport](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/webservicesupport/package-summary.html).

### AEM整合 {#aem-integration}

可用服務列於 **Cloud Services** 的 **頁面屬性** 對話框（從繼承的任何頁） `foundation/components/page` 或 `wcm/mobile/components/page`)。

索引標籤也提供：

* 可啟用服務的位置連結
* 從路徑欄位中選擇配置（服務的子節點）

#### 密碼加密 {#password-encryption}

儲存服務的使用者憑證時，應加密所有密碼。

您可以新增隱藏的表單欄位來達成此目標。 此欄位應具有註解 `@Encrypted` 在屬性名稱中；即為 `password` 欄位名稱將寫入為：

`password@Encrypted`

然後會自動加密屬性(使用 `CryptoSupport` 服務) `EncryptionPostProcessor`.

>[!NOTE]
>
>這類似於標準 ` [SlingPostServlet](https://sling.apache.org/site/manipulating-content-the-slingpostservlet-servletspost.html)` 註解。

>[!NOTE]
>
>依預設， `EcryptionPostProcessor` 僅加密 `POST` 向 `/etc/cloudservices`.

#### 服務頁jcr:content節點的其他屬性 {#additional-properties-for-service-page-jcr-content-nodes}

<table> 
 <tbody> 
  <tr> 
   <td><strong>屬性</strong></td> 
   <td><strong>說明</strong></td> 
  </tr> 
  <tr> 
   <td>componentReference</td> 
   <td>要自動包含在頁面中的元件的參考路徑。<br /> 這可用於其他功能和JS包含。<br /> 這包括頁面上的元件，其中<br /> <code> cq/cloudserviceconfigs/components/servicecomponents</code><br /> 包含在內(通常是在 <code>body</code> 標籤)。<br /> 在Analytics和Target中，我們會使用此功能來包含其他功能，例如追蹤訪客行為的JavaScript呼叫。</td> 
  </tr> 
  <tr> 
   <td>說明</td> 
   <td>服務的簡短說明。<br /> </td> 
  </tr> 
  <tr> 
   <td>descriptionExtended</td> 
   <td>服務的延伸說明。</td> 
  </tr> 
  <tr> 
   <td>排名</td> 
   <td>用於清單的服務排名。</td> 
  </tr> 
  <tr> 
   <td>selectableChildren</td> 
   <td>在頁面屬性對話方塊中顯示設定的篩選。</td> 
  </tr> 
  <tr> 
   <td>serviceUrl</td> 
   <td>網站服務URL。</td> 
  </tr> 
  <tr> 
   <td>serviceUrlLabel</td> 
   <td>服務URL的標籤。</td> 
  </tr> 
  <tr> 
   <td>thumbnailPath</td> 
   <td>服務的縮圖路徑。</td> 
  </tr> 
  <tr> 
   <td>可見</td> 
   <td>頁面屬性對話方塊中的可見性；預設顯示（可選）</td> 
  </tr> 
 </tbody> 
</table>

### 使用案例 {#use-cases}

預設會提供下列服務：

* [追蹤器片段](/help/sites-administering/external-providers.md) (Google、WebTrends等)
* [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics)
* [Test&amp;Target](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-target)
* [Dynamic Media](/help/sites-administering/marketing-cloud.md#integrating-with-scene)

>[!NOTE]
>
>另請參閱 [建立自訂Cloud Service](/help/sites-developing/extending-cloud-config-custom-cloud.md).

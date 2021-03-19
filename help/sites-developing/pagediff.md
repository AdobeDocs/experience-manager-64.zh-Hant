---
title: 開發與頁面比較
seo-title: 開發與頁面比較
description: 開發與頁面比較
seo-description: 'null'
uuid: 48bbeca3-fe16-48ef-bb4d-ac605fe0ca76
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 13e8cbef-698f-4e69-9f8c-f9bee82e9fd1
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---


# 開發和頁面差異{#developing-and-page-diff}

## 功能概觀{#feature-overview}

內容建立是一個反覆的過程。 製作具效率的內容需要能夠查看從一個迭代到另一個迭代的變化。 檢視一個頁面版本，然後檢視另一個頁面版本則無效率且容易出錯。 作者想要能夠並排比較目前頁面與先前版本的差異。

頁面差異可讓使用者比較目前頁面與啟動、舊版等。 有關此用戶功能的詳細資訊，請參見[頁面差異](/help/sites-authoring/page-diff.md)。

## 操作詳細資訊{#operation-details}

比較頁面版本時，使用者想要比較的舊版會在背景重新建AEM立，以利比較。 這需要能夠呈現內容[以便並排比較](/help/sites-authoring/page-diff.md#presentation-of-differences)。

此娛樂作業由內部AEM進行，對使用者透明，不需干預。 但是，在CRX DE Lite中查看儲存庫的管理員在內容結構中可以看到這些重新建立的版本。

根據修補程AEM序級別，行為不同，可能需要某些權限才能正常工作。

### 6.AEM4.3 {#prior-to-aem}之前版本

比較內容時，會在下列位置重新建立整個要比較頁面的樹狀結構：

`/content/versionhistory/<userId>/<site structure>`

因為使用頁面比較機制時，AEM會重新建立頁面的舊版本，所以使用者必須具有特定的JCR權限才能使用此功能。

>[!CAUTION]
>
>為了使用頁面比較功能，用戶需要對節點`/content/versionhistory`具有&#x200B;**修改／建立／刪除**&#x200B;權限。

### 截至AEM6.4.3 {#as-of-aem}

比較內容時，會在下列位置重新建立整個要比較頁面的樹狀結構：

`/tmp/versionhistory/`

此內容是由具有權限限制目前使用者可見性的服務使用者建立。 因此，不需要特殊權限。

自動執行清除任務以清除此臨時內容。

## 開發人員限制{#developer-limitations}

以前，在Classic UI中，必須特別考慮開發，以利AEM進行差異化（例如使用`cq:text`標籤庫，或自訂將`DiffService` OSGi服務整合至元件）。 新的比較功能不再需要這個功能，因為比較是通過DOM比較在客戶端進行。

不過，開發人員需要考慮許多限制。

* 此功能使用名稱未與「產品」間隔開的CSSAEM類別。 如果頁面上包含其他具有相同名稱的自訂CSS類別或第三方CSS類別，則會影響比較的顯示。

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* 由於比較是客戶端，並在頁面載入時執行，因此在客戶端比較服務運行後對DOM的任何調整都不會計算在內。 這可能會影響

   * 用於包含內AJAX容的元件
   * 單頁應用程式
   * 在使用者互動時控制DOM的Javascript型元件。


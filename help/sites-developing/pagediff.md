---
title: 開發與頁面比較
seo-title: 開發與頁面比較
description: 'null'
seo-description: 'null'
uuid: 48bbeca3-fe16-48ef-bb4d-ac605fe0ca76
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 13e8cbef-698f-4e69-9f8c-f9bee82e9fd1
translation-type: tm+mt
source-git-commit: 6de5e6f12f123ca2ec45358a138becc410c89e4e
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---


# 開發與頁面比較{#developing-and-page-diff}

## 功能概觀 {#feature-overview}

內容建立是一個反覆的過程。 製作具效率的內容需要能夠查看從一個迭代到另一個迭代的變化。 檢視一個頁面版本，然後檢視另一個頁面版本則無效率且容易出錯。 作者想要能夠並排比較目前頁面與先前版本的差異。

頁面差異可讓使用者比較目前頁面與啟動、舊版等。 有關此用戶功能的詳細資訊，請參 [閱頁面差異](/help/sites-authoring/page-diff.md)。

## 操作詳細資訊 {#operation-details}

比較頁面版本時，使用者想要比較的舊版會由AEM在背景重新建立，以利比較。 這需要能夠演算內容以 [進行並排比較](/help/sites-authoring/page-diff.md#presentation-of-differences)。

此娛樂作業由AEM在內部完成，而且對使用者透明，不需要干預。 但是，在CRX DE Lite中查看儲存庫的管理員在內容結構中可以看到這些重新建立的版本。

視AEM修補程式層級而定，行為不同，可能需要特定權限才能正常運作。

### AEM 6.4.3之前版本 {#prior-to-aem}

比較內容時，會在下列位置重新建立整個要比較頁面的樹狀結構：

`/content/versionhistory/<userId>/<site structure>`

因為當使用頁面比較機制時，AEM會重新建立頁面的舊版，以使用使用者必須具有特定JCR權限的功能。

>[!CAUTION]
>
>為了使用頁面比較功能，用戶需要對節點具有 **修改／建立／刪除** 權限 `/content/versionhistory`。

### 自AEM 6.4.3起 {#as-of-aem}

比較內容時，會在下列位置重新建立整個要比較頁面的樹狀結構：

`/tmp/versionhistory/`

此內容由權限限制目前使用者可見度的服務使用者建立。 因此，不需要特殊權限。

自動執行清除任務以清除此臨時內容。

## 開發人員限制 {#developer-limitations}

以前，在Classic UI中，必須特別考慮開發以利AEM差異化(例如使用 `cq:text` tag lib，或自訂將 `DiffService` OSGi服務整合至元件)。 新的比較功能不再需要這個功能，因為比較是通過DOM比較在客戶端進行。

不過，開發人員需要考慮許多限制。

* 此功能使用的CSS類別名稱與AEM產品間隔不開。 如果頁面上包含其他具有相同名稱的自訂CSS類別或第三方CSS類別，則會影響比較的顯示。

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* 由於比較是客戶端，並在頁面載入時執行，因此在客戶端比較服務運行後對DOM的任何調整都不會計算在內。 這可能會影響

   * 使用AJAX來包含內容的元件
   * 單頁應用程式
   * 在使用者互動時控制DOM的Javascript型元件。


---
title: 開發與頁面差異
seo-title: Developing and Page Diff
description: 開發與頁面差異
seo-description: null
uuid: 48bbeca3-fe16-48ef-bb4d-ac605fe0ca76
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 13e8cbef-698f-4e69-9f8c-f9bee82e9fd1
exl-id: 365e944d-d8a3-4f4e-8925-88629845232f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 1%

---

# 開發與頁面差異{#developing-and-page-diff}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 功能概述 {#feature-overview}

內容建立是一個迭代過程。 以效率製作需要能夠查看從一個迭代到另一個迭代的更改。 檢視一個頁面版本，而另一個頁面版本則效率低下且容易出錯。 作者想要能夠並排比較目前的頁面與上一個版本，並反白顯示差異。

頁面差異可讓使用者比較目前的頁面與啟動、舊版等。 如需此使用者功能的詳細資訊，請參閱 [頁面差異](/help/sites-authoring/page-diff.md).

## 操作詳細資訊 {#operation-details}

比較頁面版本時，使用者想要比較的舊版本會由AEM在背景重新建立，以利比較。 這必須能夠呈現內容 [並排比較](/help/sites-authoring/page-diff.md#presentation-of-differences).

此休閒作業由AEM內部完成，且對使用者而言是透明的，不需要干預。 但是，如果管理員檢視儲存庫（例如在CRX DE Lite中），會在內容結構中看到這些重新建立的版本。

視AEM修補程式層級而定，行為會有所不同，為了正常運作，可能需要特定權限。

### AEM 6.4.3之前 {#prior-to-aem}

比較內容時，會在下列位置重新建立要比較的頁面前整個樹狀結構：

`/content/versionhistory/<userId>/<site structure>`

因為使用頁面比較機制時，AEM會重新建立舊版頁面，為了使用功能，使用者必須具有特定JCR權限。

>[!CAUTION]
>
>若要使用頁面差異功能，使用者必須具備 **修改/建立/刪除** 節點的權限 `/content/versionhistory`.

### 自AEM 6.4.3起 {#as-of-aem}

比較內容時，會在下列位置重新建立要比較的頁面前整個樹狀結構：

`/tmp/versionhistory/`

此內容由服務使用者建立，其權限會限制目前使用者的可見性。 因此，不需要特殊權限。

清除任務會自動運行以清除此臨時內容。

## 開發人員限制 {#developer-limitations}

之前，在傳統UI中，必須進行特殊開發考量，以便利AEM差異(例如使用 `cq:text` 標籤庫，或自訂整合 `DiffService` OSGi服務至元件)。 新差異功能不再需要此功能，因為差異會透過DOM比較在用戶端發生。

但開發人員需要考慮許多限制。

* 此功能使用的CSS類別名稱與AEM Product不同。 如果頁面上包含其他具有相同名稱的自訂CSS類或第三方CSS類，則差異的顯示可能會受到影響。

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* 由於差異是用戶端並會在頁面載入時執行，因此在用戶端差異服務執行後對DOM所做的任何調整都不會計入。 這可能會影響

   * 使用AJAX包含內容的元件
   * 單頁應用程式
   * 在使用者互動時操控DOM的Javascript型元件。

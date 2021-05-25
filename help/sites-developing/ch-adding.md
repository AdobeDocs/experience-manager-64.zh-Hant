---
title: 新增ContextHub至頁面及存取商店
seo-title: 新增ContextHub至頁面及存取商店
description: 將ContextHub新增至您的頁面以啟用ContextHub功能並連結至ContextHub Javascript資料庫
seo-description: 將ContextHub新增至您的頁面以啟用ContextHub功能並連結至ContextHub Javascript資料庫
uuid: ade37960-21c4-4d64-a525-68f0d199f955
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: ac8f44df-39fb-44ea-ae17-ead0dbd1f6c0
exl-id: 99efe308-bf8a-41ad-8203-b57fce20820c
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1033'
ht-degree: 0%

---

# 將ContextHub新增至頁面並存取儲存{#adding-contexthub-to-pages-and-accessing-stores}

將ContextHub新增至您的頁面以啟用ContextHub功能並連結至ContextHub Javascript資料庫

ContextHub Javascript API可讓您存取ContextHub管理的內容資料。 本頁簡要說明API用於存取及處理內容資料的主要功能。 請依照API參考檔案的連結，查看詳細資訊和程式碼範例。

## 將ContextHub新增至頁面元件{#adding-contexthub-to-a-page-component}

若要啟用ContextHub功能並連結至ContextHub Javascript程式庫，請在頁面的`head`區段中包含Contexthub元件。 頁面元件的JSP程式碼類似下列範例：

```xml
<head>
   <sling:include path="contexthub" resourceType="granite/contexthub/components/contexthub" />
</head>
```

請注意，您也需要設定ContextHub工具列是否顯示在「預覽」模式中。 請參閱[顯示和隱藏ContextHub UI](/help/sites-administering/contexthub-config.md#showing-and-hiding-the-contexthub-ui)。

## 關於ContextHub儲存{#about-contexthub-stores}

使用ContextHub存放區來保留內容資料。 ContextHub提供下列儲存類型，這些儲存類型構成所有儲存類型的基礎：

* [PerisentStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)
* [SessionStore](/help/sites-developing/contexthub-api.md#contexthub-store-sessionstore)
* [JSONPStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore)
* [PerisentJSONPStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)

所有儲存類型都是[`ContextHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core)類的副檔名。 有關建立新商店類型的資訊，請參閱[建立自定義商店](/help/sites-developing/ch-extend.md#creating-custom-store-candidates)。 如需範例存放區類型的相關資訊，請參閱[範例ContextHub存放區候選項](/help/sites-developing/ch-samplestores.md)。

### 持久性模式{#persistence-modes}

Context Hub存放區使用下列其中一種持續性模式：

* **本機：** 使用HTML5 localStorage來保存資料。本機儲存會跨工作階段保存在瀏覽器上。
* **工作階段：** 使用HTML5 sessionStorage來保存資料。工作階段儲存在瀏覽器工作階段期間持續存在，且可供所有瀏覽器視窗使用。
* **Cookie:** 使用瀏覽器對資料儲存Cookie的原生支援。Cookie資料會在HTTP要求中傳送至伺服器，或從伺服器傳送。
* **Window.name:** 使用window.name屬性來保存資料。
* **記憶體：** 使用Javascript物件來保存資料。

預設情況下，Context Hub使用本地持久性模式。 如果瀏覽器不支援或允許HTML5 localStorage，則會使用工作階段持續性。 如果瀏覽器不支援或允許HTML5 sessionStorage，則會使用Window.name持續性。

### 存放資料 {#store-data}

在內部，將資料儲存為樹結構，以便將值添加為主要類型或複雜對象。 添加要儲存的複雜對象時，對象屬性在資料樹中形成分支。 例如，下列複雜物件會新增至名為位置的空白存放區：

```xml
Object {
   number: 321,
   data: {
      city: "Basel",
      country: "Switzerland",
      details: {
         population: 173330,
         elevation: 260
      }
   }
}
```

儲存資料的樹狀結構可概念化如下：

```xml
/
|- number
|- data
      |- city
      |- country
      |- details
            |- population
            |- elevation
```

樹結構將儲存中的資料項目定義為索引鍵/值組。 在上例中，鍵`/number`與值`321`對應，鍵`/data/country`與值`Switzerland`對應。

### 操作對象{#manipulating-objects}

ContextHub提供[`ContextHub.Utils.JSON.tree`](/help/sites-developing/contexthub-api.md#contexthub-utils-json-tree)類別，用於操作Javascript對象。 在將Javascript對象添加到儲存區之前，或在從儲存區獲取Javascript對象之後，使用此類的函式。

此外，[`ContextHub.Utils.JSON`](/help/sites-developing/contexthub-api.md#contexthub-utils-json)類還提供了將對象序列化為字串，並將字串反序列化為對象的函式。 使用此類別處理JSON資料，以支援原生不包含`JSON.parse`和`JSON.stringify`函式的瀏覽器。

## 與ContextHub商店互動{#interacting-with-contexthub-stores}

使用[`ContextHub`](/help/sites-developing/contexthub-api.md#ui-event-constants) Javascript物件來取得儲存作為Javascript物件。 取得儲存物件後，您就可以控制其包含的資料。 使用[`getAllStores`](/help/sites-developing/contexthub-api.md#getallstores)或[`getStore`](/help/sites-developing/contexthub-api.md#getstore-name)函式來取得存放區。

### 訪問儲存資料{#accessing-store-data}

[`ContexHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core) Javascript類定義了與儲存資料交互的多個函式。 以下函式儲存和檢索對象中包含的多個資料項：

* [addAllItems](/help/sites-developing/contexthub-api.md#addallitems-tree-options)
* [getTree](/help/sites-developing/contexthub-api.md#gettree-includeinternals)

個別資料項目會儲存為一組索引鍵/值組。 要儲存和檢索值，請指定相應的鍵：

* [getItem](/help/sites-developing/contexthub-api.md#getitem-key)
* [setItem](/help/sites-developing/contexthub-api.md#setitem-key-value-options)

請注意，自訂存放區候選項可定義其他功能，以提供存取儲存資料的權限。

>[!NOTE]
>
>ContextHub預設不會知道目前在發佈伺服器上使用的登入，且ContextHub會將這類使用者視為「匿名」。
>
>您可以依照[We.Retail參考網站](/help/sites-developing/we-retail.md)中的實作，載入設定檔存放區，讓ContextHub得知已登入的使用者。 請在此處](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/blob/master/ui.apps/src/main/content/jcr_root/apps/weretail/components/structure/header/clientlib/js/utilities.js)參閱GitHub上的[相關程式碼。

### ContextHub事件{#contexthub-eventing}

ContextHub包含事件架構，可讓您自動回應以儲存事件。 每個儲存對象都包含一個[`ContextHub.Utils.Eventing`](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing)對象，該對象可用作儲存的[`eventing`](/help/sites-developing/contexthub-api.md#eventing)屬性。 使用[`on`](/help/sites-developing/contexthub-api.md#on-name-handler-selector-triggerforpastevents)或[`once`](/help/sites-developing/contexthub-api.md#once-name-handler-selector-triggerforpastevents)函式將Javascript函式系結至儲存事件。

## 使用內容中樞來操控Cookie {#using-context-hub-to-manipulate-cookies}

Context Hub Javascript API提供跨瀏覽器支援，可處理瀏覽器Cookie。 [`ContextHub.Utils.Cookie`](/help/sites-developing/contexthub-api.md#contexthub-utils-cookie)命名空間定義了用於建立、操作和刪除Cookie的多個函式。

## 確定解析的ContextHub區段{#determining-resolved-contexthub-segments}

ContextHub區段引擎可讓您判斷目前內容中要解析的已註冊區段。 使用[`ContextHub.SegmentEngine.SegmentManager`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segmentmanager)類的getResolvedSegments函式來檢索已解析的段。 然後，使用[`ContextHub.SegmentEngine.Segment`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segment)類的`getName`或`getPath`函式來測試段。

### 已安裝的區段{#installed-segments}

ContextHub區段會安裝在`/conf/we-retail/settings/wcm/segments`節點下。

* 女性
* 30歲以上女性
* 30歲以下女性
* 男性
* 男30歲以上
* 男30歲以下
* order-value-75-to-100
* order-value-over-100
* 30歲以上
* 夏季
* 夏女
* 30歲以上夏季女性
* 30歲以下夏季女性
* 夏男
* 30歲以上夏季男性
* 30歲以下的夏季男性
* 30歲以下
* 冬季
* 冬女
* 冬季 — 女30歲以上
* 冬季 — 女性–30歲以下
* 冬男
* 冬季男30歲以上
* 20歲以下的冬季男性

用以解決這些區段的規則摘要如下：

* 從[配置檔案](/help/sites-developing/ch-samplestores.md#granite-profile-sample-store-candidate)儲存的`gender`資料項確定女性或男性。

* 年齡由設定檔存放區的年齡資料項目決定。
* 季數由[geolocation](/help/sites-developing/ch-samplestores.md#contexthub-geolocation-sample-store-candidate)商店的緯度資料項和surferinfo商店的月資料項決定。

>[!WARNING]
>
>安裝的區段會作為參考設定提供，協助您為專案建立專屬的設定，因此不應直接使用。

## 記錄ContextHub {#logging-debug-messages-for-contexthub}的除錯訊息

設定AdobeGranite ContextHub OSGi服務(PID = `com.adobe.granite.contexthub.impl.ContextHubImpl`)，以記錄開發時很實用的詳細除錯訊息。

要配置服務，可以使用[Web控制台](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console)或在儲存庫](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository)中使用[JCR節點：

* Web控制台：若要記錄除錯訊息，請選取除錯屬性。
* JCR節點：若要記錄除錯訊息，請將布林值`com.adobe.granite.contexthub.debug`屬性設為`true`。

## 請參閱ContextHub架構概述{#see-an-overview-of-the-contexthub-framework}

ContextHub提供[診斷頁面](/help/sites-developing/ch-diagnostics.md) ，您可在其中看到ContextHub架構的概觀。

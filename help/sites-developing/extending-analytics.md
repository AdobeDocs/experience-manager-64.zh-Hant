---
title: 擴充事件追蹤
seo-title: Extending Event Tracking
description: AEM Analytics可讓您追蹤使用者在您網站上的互動
seo-description: AEM Analytics allows you to track user interaction on your website
uuid: 722798ac-4043-4918-a6df-9eda2c85020b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: e0372f4a-fe7b-4526-8391-5bb345b51d70
exl-id: 8df6b48f-b1a8-4294-a52e-dc17ab65606c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# 擴充事件追蹤{#extending-event-tracking}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

AEM Analytics可讓您追蹤使用者在您網站上的互動。 身為開發人員，您可能需要：

* 追蹤訪客與元件的互動方式。 您可以透過 [自訂事件。](#custom-events)
* [存取ContextHub中的值](/help/sites-developing/extending-analytics.md#accessing-values-in-the-contexthub).
* [添加記錄回調](#adding-record-callbacks).

>[!NOTE]
>
>這些資訊基本上是通用的，但它使用 [Adobe Analytics](/help/sites-administering/adobeanalytics.md) 以取得特定範例。
>
>有關開發元件和對話框的一般資訊，請參見 [開發元件](/help/sites-developing/components.md).

## 自訂事件 {#custom-events}

自訂事件會追蹤任何與頁面上特定元件的可用性相關的項目。 這也包括範本專屬的事件，因為頁面元件會視為另一個元件。

### 在頁面載入時追蹤自訂事件 {#tracking-custom-events-on-page-load}

您可以使用偽屬性來完成此操作 `data-tracking` （舊記錄屬性仍支援回溯相容性）。 您可以將其新增至任何HTML標籤。

的語法 `data-tracking` is

* `data-tracking="{'event': ['eventName'], 'values': {'key': 'value', 'nextKey': 'nextValue'}, componentPath: 'myapp/component/mycomponent'}"`

您可以將任何數量的機碼值組作為第二個參數（稱為有效負載）傳遞。

範例看起來可能如下：

```xml
<span data-tracking="{event:'blogEntryView', 
                                values:{
                                   'blogEntryContentType': 'blog', 
                                   'blogEntryUniqueID': '<%= xssAPI.encodeForJSString(entry.getId()) %>',
                                   'blogEntryTitle': '<%= xssAPI.encodeForJSString(entry.getTitle()) %>',
                                   'blogEntryAuthor':'<%= xssAPI.encodeForJSString(entry.getAuthor()) %>',
                                   'blogEntryPageLanguage':'<%= currentPage.getLanguage(true) %>'
                                },
                                componentPath:'myapp/component/mycomponent'}">
</span>
```

在頁面載入時，全部 `data-tracking` 屬性將會收集並新增至ContextHub的事件存放區，以便對應至Adobe Analytics事件。 未對應的事件將不會由Adobe Analytics追蹤。 請參閱 [連線至Adobe Analytics](/help/sites-administering/adobeanalytics.md) 以取得關於對應事件的詳細資訊。

### 在頁面載入後追蹤自訂事件 {#tracking-custom-events-after-page-load}

若要追蹤頁面載入後發生的事件（例如使用者互動），請使用 `CQ_Analytics.record` JavaScript函式：

* `CQ_Analytics.record({event: 'eventName', values: { valueName: 'VALUE' }, collect: false, options: { obj: this, defaultLinkType: 'X' }, componentPath: '<%=resource.getResourceType()%>'})`

其中

* `events` 是字串或字串陣列（適用於多個事件）。

* `values` 包含所有要追蹤的值
* `collect` 為選用項目，將傳回包含事件和資料物件的陣列。
* `options` 為選用項目，且包含連結追蹤選項，例如HTML元素 `obj` 和 ` [defaultLinkType](https://microsite.omniture.com/t2/help/en_US/sc/implement/index.html#linkType)`.

* `componentPath` 是必要的屬性，建議將其設為 `<%=resource.getResourceType()%>`

例如，使用下列定義，使用者按一下 **跳到頂** 連結會造成兩個事件， `jumptop` 和 `headlineclick`，將引發：

```xml
<h1 data-tracking="{event: 'headline', values: {level:'1'}, componentPath: '<%=resource.getResourceType()%>'}">
  My Headline <a href="#" onclick="CQ_Analytics.record({event: ['jumptop','headlineclick'],  values: {level:'1'}, componentPath: '<%=resource.getResourceType()%>'})">Jump to top</a>
</h1>
```

## 存取ContextHub中的值 {#accessing-values-in-the-contexthub}

ContextHub JavaScript API具有 `getStore(name)` 函式（如果可用），傳回指定的存放區。 商店有 `getItem(key)` 函式（如果可用），傳回指定金鑰的值。 使用 `getKeys()` 函式可擷取特定存放區之已定義索引鍵的陣列。

您可以透過使用 `ContextHub.getStore(name).eventing.on(ContextHub.Constants.EVENT_STORE_UPDATED, handler, selector, triggerForPastEvents)` 函式。

ContextHub初次可用時收到通知的最佳方式是使用 `ContextHub.eventing.on(ContextHub.Constants.EVENT_ALL_STORES_READY, handler, selector, triggerForPastEvents);` 函式。

**ContextHub的其他事件：**

所有商店都準備就緒：

`ContextHub.eventing.on(ContextHub.Constants.EVENT_ALL_STORES_READY, handler, selector, triggerForPastEvents);`

特定儲存：

`ContextHub.getStore(store).eventing.on(ContextHub.Constants.EVENT_STORE_READY, handler, selector, triggerForPastEvents)`

>[!NOTE]
>
>另請參閱完成 [ContextHub API參考](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/contexthub-api.html#ContextHubJavascriptAPIReference)

## 添加記錄回撥 {#adding-record-callbacks}

使用函式註冊回呼之前和之後 `CQ_Analytics.registerBeforeCallback(callback,rank)` 和 `CQ_Analytics.registerAfterCallback(callback,rank)`.

這兩個函式都將函式當作第一個引數，並將排名當作第二個引數，而此引數會指定回呼的執行順序。

如果回呼傳回false，則執行鏈中後續的回呼將不會執行。

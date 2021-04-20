---
title: 擴充資產搜尋
description: 將AEM Assets的搜尋功能擴展至現成可用的字串搜尋以外。
contentOwner: AG
feature: Search
role: Developer
translation-type: tm+mt
source-git-commit: 4acf159ae1b9923a9c93fa15faa38c7f4bc9f759
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 14%

---


# 擴充資產搜尋{#extending-assets-search}

您可以擴充Adobe Experience Manager(AEM)資產搜尋功能。 AEM Assets開箱即用，按字串搜尋資產。

搜尋是透過QueryBuilder介面完成，因此可使用數個謂語自訂搜尋。 您可以覆蓋下列目錄中的預設謂詞集：`/apps/dam/content/search/searchpanel/facets`。

您也可以新增其他標籤至AEM Assets管理面板。

>[!CAUTION]
>
>自6.AEM4起，Classic UI已過時。 如需公告，請參閱[已過時和已移除的功能](../release-notes/deprecated-removed-features.md)。 我們建議您使用可觸控的UI。 如需自訂資訊，請參閱[搜尋Facets](search-facets.md)。

## 覆蓋{#overlaying}

若要覆蓋預先設定的謂語，請將`facets`節點從`/libs/dam/content/search/searchpanel`複製至`/apps/dam/content/search/searchpanel/`，或在搜尋面板設定中指定另一個`facetURL`屬性（預設為`/libs/dam/content/search/searchpanel/facets.overlay.infinity.json`）。

![screen_shot_2012-06-05at113619am](assets/screen_shot_2012-06-05at113619am.png)

>[!NOTE]
>
>預設情況下，/ `apps`下的目錄結構不存在，需要建立。 確保節點類型與/ `libs`下的節點類型匹配。


## 添加頁籤{#adding-tabs}

您可以在「AEM Assets管理員」中設定其他「搜尋」標籤，以新增這些標籤。 要建立其他頁籤：

1. 如果資料夾結構`/apps/wcm/core/content/damadmin/tabs,`尚不存在，則建立該資料夾結構，並從`/libs/wcm/core/content/damadmin`複製`tabs`節點並貼上它。
1. 視需要建立並設定第二個標籤。

   >[!NOTE]
   >
   >當您建立第二個siteadminsearchpanel時，請務必設定`id`屬性，以避免表單衝突。

## 建立自定義謂語{#creating-custom-predicates}

AEM Assets提供一組預先定義的謂詞，可用於自訂「資產共用」頁面。 以此方式自訂資產共用，請參閱[建立和設定資產共用頁面](assets-finder-editor.md#creating-and-configuring-an-asset-share-page)。

除了使用預先存在的謂語外，開AEM發人員也可使用[Query Builder API](/help/sites-developing/querybuilder-api.md)建立自己的謂語。

建立自訂謂語需要[Widgets架構](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/widgets-api/index.html)的基本知識。

最佳做法是複製現有謂詞並調整它。 範例謂語位於`/libs/cq/search/components/predicates`中。

### 範例：建立簡單屬性謂詞{#example-build-a-simple-property-predicate}

要構建屬性謂語：

1. 在項目目錄中建立元件資料夾，例如`/apps/geometrixx/components/titlepredicate`。
1. 新增 `content.xml`:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0"
    xmlns:cq="https://www.day.com/jcr/cq/1.0"
    xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Title Predicate"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. 新增 `titlepredicate.jsp`.

   ```xml
   <%--
     Sample title predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Title</div>
   
       <%-- The wrapper for the form elements. All items will be append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:title";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // createId adds a counter to the predicate name - useful in case this predicate
           // is inserted multiple times on the same page.
           var id = qb.createId(predicateName);
   
           // Hidden field that defines the property to search for; in our case this
           // is the "dc:title" metadata. The name "property" (or "1_property", "2_property" etc.)
           // indicates the server to use the property predicate
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id,
               "value": propertyName
           });
   
           // The visible text field. The name has to be like the one of the hidden field above
           // plus the ".value" suffix.
           qb.addField({
               "xtype": "textfield",
               "renderTo": elemId,
               "name": id + ".value"
           });
   
           // Depending on the predicate additional parameters allow to configure the
           // predicate. Here we add an operation parameter to create a "like" query.
           // Again note the name set to the id and a suffix.
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id + ".operation",
               "value": "like"
           });
   
       });
   
   </script>
   ```

1. 若要讓元件可用，您必須能夠加以編輯。要使元件可編輯，請在CRXDE中添加主類型`cq:EditConfig`的節點`cq:editConfig`。 為了能夠移除段落，請新增多值屬性 `cq:actions` ，其中單一值 **為DELETE**。
1. 導覽至您的瀏覽器，並在範例頁面（例如`press.html`）切換至設計模式，並啟用謂詞段落系統的新元件（例如&#x200B;**left**）。

1. 在&#x200B;**Edit**&#x200B;模式中，新元件現在可在sidekick中使用（位於&#x200B;**Search**&#x200B;群組中）。 在&#x200B;**謂語**&#x200B;欄中插入元件，並輸入搜尋字詞，例如&#x200B;**Diamond**，然後按一下放大鏡開始搜尋。

   >[!NOTE]
   >
   >搜尋時，請務必準確輸入詞語，包括正確的大小寫。

### 範例：建立簡單群組述詞{#example-build-a-simple-group-predicate}

若要建立群組述詞：

1. 在項目目錄中建立元件資料夾，例如`/apps/geometrixx/components/picspredicate`。
1. 新增 `content.xml`:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0"
    xmlns:cq="https://www.day.com/jcr/cq/1.0"
    xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Image Formats"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. 新增 `titlepredicate.jsp`:

   ```java
   <%--
   
     Sample group predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page.
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Image Formats</div>
   
       <%-- The wrapper for the form elements. All items will be append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:format";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // Create a unique group ID; will return e.g. "1_group".
           var groupId = qb.createGroupId();
   
           // Hidden field that defines the property to search for  - in our case "dc:format" -
           // and declares the group of predicates. "property" in the name ("1_group.property")
           // indicates to the server to use the "property predicate"
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": "<%= elemId %>",
               "name": groupId + "." + predicateName, // 1_group.property
               "value": propertyName
           });
   
           // Declare to combine the multiple values using OR.
           qb.add(new CQ.Ext.form.Hidden({
               "name": groupId + ".p.or",  // 1_group.p.or
               "value": "true"
           }));
   
           // The options
           var options = [
               { "label":"JPEG", "value":"image/jpeg"},
               { "label":"PNG",  "value":"image/png" },
               { "label":"GIF",  "value":"image/gif" }
           ];
   
           // Build a checkbox for each option.
           for (var i = 0; i < options.length; i++) {
               qb.addField({
                   "xtype": "checkbox",
                   "renderTo": "<%= elemId %>",
                   // 1_group.property.0_value, 1_group.property.1_value etc.
                   "name": groupId + "." +  predicateName + "." + i + "_value",
                   "inputValue": options[i].value,
                   "boxLabel": options[i].label,
                   "listeners": {
                       "check": function() {
                           // Submit the search form when checking/unchecking a checkbox.
                           qb.submit();
                       }
                   }
               });
           }
   
       });
   ```

1. 若要讓元件可用，您必須能夠加以編輯。要使元件可編輯，請在CRXDE中添加主類型`cq:EditConfig`的節點`cq:editConfig`。 為了能夠移除段落，請新增多值屬性 `cq:actions` ，其中單一值 `DELETE`為。
1. 導覽至您的瀏覽器，並在範例頁面（例如`press.html`）切換至設計模式，並啟用謂詞段落系統的新元件（例如&#x200B;**left**）。
1. 在&#x200B;**Edit**&#x200B;模式中，新元件現在可在sidekick中使用（位於&#x200B;**Search**&#x200B;群組中）。 將元件插入&#x200B;**謂語**&#x200B;列中。

### 已安裝的謂詞Widget {#installed-predicate-widgets}

以下謂語是預先設定的ExtJS Widget。

### FulltextPredicate {#fulltextpredicate}

| 屬性 | 類型 | 說明 |
|---|---|---|
| predicateName | 字串 | 謂詞的名稱。 預設為 `fulltext` |
| searchCallback | 函數 | 回呼以觸發事件`keyup`上的搜尋。 預設為 `CQ.wcm.SiteAdmin.doSearch` |

### PropertyPredicate {#propertypredicate}

| 屬性 | 類型 | 說明 |
|---|---|---|
| predicateName | 字串 | 謂詞的名稱。 預設為 `property` |
| propertyName | 字串 | JCR屬性的名稱。 預設為 `jcr:title` |
| defaultValue | 字串 | 預先填入的預設值。 |

### PathPredicate {#pathpredicate}

| 屬性 | 類型 | 說明 |
|---|---|---|
| predicateName | 字串 | 謂詞的名稱。 預設為 `path` |
| rootPath | 字串 | 謂詞的根路徑。 預設為 `/content/dam` |
| pathFieldPredicateName | 字串 | 預設為 `folder` |
| showFlatOption | 布林值 (Boolean) | 顯示複選框`search in subfolders`的標籤。 預設為true。 |

### DatePredicate {#datepredicate}

| 屬性 | 類型 | 說明 |
|---|---|---|
| predicateName | 字串 | 謂詞的名稱。 預設為 `daterange` |
| 屬性名 | 字串 | JCR屬性的名稱。 預設為 `jcr:content/jcr:lastModified` |
| defaultValue | 字串 | 預先填入的預設值 |

### OptionsPredicate {#optionspredicate}

| 屬性 | 類型 | 說明 |
|---|---|---|
| 標題 | 字串 | 新增其他標題 |
| predicateName | 字串 | 謂詞的名稱。 預設為 `daterange` |
| 屬性名 | 字串 | JCR屬性的名稱。 預設為 `jcr:content/metadata/cq:tags` |
| 崩潰 | 字串 | 收合層級。 預設為 `level1` |
| triggerSearch | 布林值 (Boolean) | 用於在檢查時觸發搜索的標籤。 預設為false |
| searchCallback | 函數 | 觸發搜尋的回呼。 預設為 `CQ.wcm.SiteAdmin.doSearch` |
| searchTimeoutTime | 數量 | 觸發searchCallback之前的逾時。 預設為800毫秒 |

## 自訂搜尋結果{#customizing-search-results}

「資產分享」頁面上的搜尋結果呈現方式由選取的鏡頭控制。 AEM Assets提供一組預先定義的鏡頭，可用來自訂「資產共用」頁面。 以此方式自訂資產共用，請參閱[建立和設定資產共用頁面](assets-finder-editor.md#creating-and-configuring-an-asset-share-page)。

除了使用現有的鏡頭外，開發人員AEM也可以自行建立鏡頭。

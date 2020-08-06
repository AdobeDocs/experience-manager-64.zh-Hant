---
title: 變更介面上的字型
seo-title: 變更介面上的字型
description: 如何選擇性地變更使用者介面上的字型。
seo-description: 如何選擇性地變更使用者介面上的字型。
uuid: d079f656-76f8-4908-9989-dde79e215eb2
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 487e3966-443a-408e-b5af-899fcba6fca6
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# 變更介面上的字型 {#changing-the-font-on-the-interface}

您可以變更AEM Forms工作區中顯示的字型。 用戶介面的特定部分中使用的字型在樣式表的相應部分中定義。 您可以選擇性地變更使用者介面上的字型。

依照 [AEM Forms工作區自訂的一般步驟](/help/forms/using/generic-steps-html-workspace-customization.md) ，並視您的需求，依循自訂CSS、HTML或兩者的步驟。

1. 以現有樣式變更或新增字型系列。
1. 變更或新增HTML元素的字型系列內嵌。
1. 新增樣式並用於HTML元素。

例如，若要將頂端導覽列錨點文字的字型變更為Courier New，請依照下列步驟進行：

1. 存取以登入CRXDE Lite `https://[server]:[port]/lc/crx/de/index.jsp`。
1. 執行下列任一項作業：

   1. 若要以現有樣式變更font-family，請在newStyle.css檔案中新增下列項目： /apps/ws/css。

      ```css
      #topnav a {
         font-family: "Courier New";
      }
      ```

   1. 要為HTML元素添加font-family行內，請將檔案復 `/libs/ws/js/runtime/templates/appnavigation.html` 制到 `/apps/ws/js/runtime/templates/appnavigation.html`。

      按如下方式更新/apps/ws/js/runtime/templates/appnavigation.html檔案：

      ```
      <li class="process"><a href="#" title="<%= $.t('index.header.topnav.startprocess.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.startprocess.name')%></a></li>
      <li class="todo"><a href="#/todo" title="<%= $.t('index.header.topnav.todo.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.todo.name')%></a></li>
      <li class="track"><a href="#/tracking" title="<%= $.t('index.header.topnav.tracking.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.tracking.name')%></a></li>
      <li class="preference"><a href="#/preferences" title="<%= $.t('index.header.topnav.preferences.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.preferences.name')%></a></li>
      ```

      開啟/apps/ws/js/registry.js檔案以進行編輯，並取代 `text!/lc/libs/ws/js/runtime/templates/appnavigation.html` 為 `text!/lc/apps/ws/js/runtime/templates/appnavigation.html`。

   1. 若要新增定義font-family的樣式，請在新的Style.css檔案中新增下列項目：/apps/ws/css。

      ```css
      .myNewFontStyle a {
         font-family: "Courier New";
      }
      ```

      若要新增HTML元素的font-family內嵌，請在appnavigation.html檔案中新增下列項目：/apps/ws/js/runtime/templates。

      ```css
      <div id="topnav" class="myNewFontStyle">
          <ul>
              <li class="process"><a href="#" title="<%= $.t('index.header.topnav.startprocess.detail')%>" ><%= $.t('index.header.topnav.startprocess.name')%></a></li>
              <li class="todo"><a href="#/todo" title="<%= $.t('index.header.topnav.todo.detail')%>"><%= $.t('index.header.topnav.todo.name')%></a></li>
              <li class="track"><a href="#/tracking" title="<%= $.t('index.header.topnav.tracking.detail')%>" ><%= $.t('index.header.topnav.tracking.name')%></a></li>
              <li class="preference"><a href="#/preferences" title="<%= $.t('index.header.topnav.preferences.detail')%>" ><%= $.t('index.header.topnav.preferences.name')%></a></li>
          </ul>
      </div>
      ```

1. 重新啟動工作區並清除瀏覽器快取，以便顯示變更。

![change_font_before圖](assets/change_font_before.png)**中：** *字型自訂前的頂端導覽列*

![change_font_after圖](assets/change_font_after.png)**中：** *自訂第一個標籤的字型後的頂端導覽列*

---
title: 更改介面上的字型
seo-title: Changing the font on the interface
description: 如何有選擇地更改用戶介面上的字型。
seo-description: How to change the fonts on the user interface selectively.
uuid: d079f656-76f8-4908-9989-dde79e215eb2
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 487e3966-443a-408e-b5af-899fcba6fca6
exl-id: bd7ec9d6-b1d2-4f01-8cef-05e5e1eceda1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 3%

---

# 更改介面上的字型 {#changing-the-font-on-the-interface}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

您可以變更AEM Forms工作區中顯示的字型。 在用戶介面的特定部分中使用的字型在樣式表的相應部分中定義。 您可以選擇性地更改用戶介面上的字型。

關注 [AEM Forms工作區自訂的一般步驟](/help/forms/using/generic-steps-html-workspace-customization.md) 並根據您的需求，請依照自訂CSS、HTML或兩者的步驟進行。

1. 以現有樣式更改或添加字型系列。
1. 更改或添加HTML元素的字型系列內嵌。
1. 新增樣式並將其用於HTML元素。

例如，要將頂部導航欄錨點文本的字型更改為「Courier New」，請執行以下步驟：

1. 透過存取 `https://[server]:[port]/lc/crx/de/index.jsp`.
1. 執行下列任一項作業：

   1. 若要以現有樣式變更字型系列，請在位於/apps/ws/css的newStyle.css檔案中新增下列內容。

      ```css
      #topnav a {
         font-family: "Courier New";
      }
      ```

   1. 若要為HTML元素內嵌新增字型系列，請複製 `/libs/ws/js/runtime/templates/appnavigation.html` 檔案 `/apps/ws/js/runtime/templates/appnavigation.html`.

      按如下方式更新/apps/ws/js/runtime/templates/appnavigation.html檔案：

      ```
      <li class="process"><a href="#" title="<%= $.t('index.header.topnav.startprocess.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.startprocess.name')%></a></li>
      <li class="todo"><a href="#/todo" title="<%= $.t('index.header.topnav.todo.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.todo.name')%></a></li>
      <li class="track"><a href="#/tracking" title="<%= $.t('index.header.topnav.tracking.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.tracking.name')%></a></li>
      <li class="preference"><a href="#/preferences" title="<%= $.t('index.header.topnav.preferences.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.preferences.name')%></a></li>
      ```

      開啟/apps/ws/js/registry.js檔案以進行編輯和取代 `text!/lc/libs/ws/js/runtime/templates/appnavigation.html` with `text!/lc/apps/ws/js/runtime/templates/appnavigation.html`.

   1. 要添加定義font-family的樣式，請在位於/apps/ws/css的newStyle.css檔案中添加以下內容。

      ```css
      .myNewFontStyle a {
         font-family: "Courier New";
      }
      ```

      若要為HTML元素新增字型系列內嵌，請在位於/apps/ws/js/runtime/templates的appnavigation.html檔案中新增下列內容。

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

1. 重新啟動工作區，並清除瀏覽器快取，讓變更可見。

![change_font_before](assets/change_font_before.png)
**圖：** *字型自訂前的頂端導覽列*

![change_font_after](assets/change_font_after.png)
**圖：** *第一個索引標籤的字型自訂後的頂端導覽列*

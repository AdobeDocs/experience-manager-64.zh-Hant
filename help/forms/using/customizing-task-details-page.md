---
title: 自定義任務詳細資訊頁
seo-title: Customizing the task details page
description: 如何自訂AEM Forms工作區中的任務詳細資訊頁面，以修改顯示的任務預設資訊。
seo-description: How-to customize the task details page in AEM Forms workspace to modify the default information displayed about a task.
uuid: d85fae55-8e66-4595-8560-5485622b6841
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 16e57cf6-aaa1-406d-a6ad-71ec60b15386
exl-id: de97e6f7-25bf-462b-b67d-0d3fbd86a321
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 2%

---

# 自定義任務詳細資訊頁 {#customizing-the-task-details-page}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

任務詳細資訊頁包含有關任務及其進程的資訊。 但是，您可以自定義任務詳細資訊頁以添加或刪除資訊。

您可以將下列資訊添加到任務詳細資訊頁中：

* 任務的JSON物件中可用的資訊(位於 [AEM Forms工作區JSON物件說明](/help/forms/using/html-workspace-json-object-description.md))
* 處理例項的JSON物件中可用的資訊(位於 [AEM Forms工作區JSON物件說明](/help/forms/using/html-workspace-json-object-description.md))

要自定義任務詳細資訊頁，請執行以下操作：

1. 追隨 [AEM Forms工作區自訂的一般步驟。](/help/forms/using/generic-steps-html-workspace-customization.md)
1. 若要顯示任何其他資訊，請將對應的索引鍵值配對新增至 `translation.json` 檔案位置 `todo`區塊> `details`區塊> `app`區塊> [ `required`塊].

   此 [ `required`塊] 指可用塊，如任務資訊的任務塊、進程資訊的進程塊和待定任務資訊的當前待定任務塊。

   例如，要在任務詳細資訊頁中添加有關「所需工藝路線選擇」的資訊，可以在任務塊中添加以下鍵值對：

   ```
   "todo" : {
       .
       .
       .
       "details" : {
           .
           .
           "task" : {
               .
               .
               "RouteSelectionRequired" : "Route Selection Required"
           }
       }
   }
   ```

   >[!NOTE]
   >
   >為所有支援的語言新增對應的索引鍵值配對。

1. 複製 `/libs/ws/js/runtime/templates/taskdetails.html` to `/apps/ws/js/runtime/templates/taskdetails.html`.

   新增資訊至 `/apps/ws/js/runtime/templates/taskdetails.html`. 例如：

   ```css
   <div class="detailsContainer">
       .
       .
       <ul>
           .
           .
           <li>
               <label for="routeSelectionRequired" title="<%= $.t('todo.details.task.RouteSelectionRequired')%>"><%= $.t('todo.details.task.RouteSelectionRequired')%></label>
               <div>
                   <span id="routeSelectionRequired"><%= isRouteSelectionRequired != null ? isRouteSelectionRequired : ''%></span>
               </div>
           </li>
           .
           .
       </ul>
   </div>
   ```

1. 開啟/apps/ws/js/registry.js進行編輯。

   搜尋和取代 `text!/lc/libs/ws/js/runtime/templates/taskdetails.html` with `text!/lc/apps/ws/js/runtime/templates/taskdetails.html`.

>[!NOTE]
>
>要使用在AEM Forms工作區的**Start Process **頁簽中建立的任務自定義任務詳細資訊頁，請將新資訊添加到 `/apps/ws/js/runtime/templates/startprocess.html`.
>
>若要為詳細資訊頁面中新增的資訊新增樣式，請使用 *使用者介面變更* 區段 [工作區自訂](/help/forms/using/changing-locale-user-interface.md).

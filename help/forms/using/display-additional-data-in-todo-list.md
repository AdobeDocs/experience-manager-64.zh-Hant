---
title: 在ToDo清單中顯示其他資料
seo-title: Displaying additional data in ToDo list
description: 自訂LiveCycleAEM Forms工作區待辦事項清單的顯示方式，以顯示預設值以外的詳細資訊。
seo-description: How-to customize the display of the To-do list of LiveCycle AEM Forms workspace to show more information besides the default.
uuid: 4c678d9c-7794-4b62-8705-d62c7780c13f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: b74a0933-2b96-4a88-9995-6fb21df141aa
exl-id: 42d8472d-0eab-4cf9-a7c3-bf2775ee6bec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 2%

---

# 在ToDo清單中顯示其他資料 {#displaying-additional-data-in-todo-list}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

依預設，AEM Forms工作區待辦事項清單會顯示任務顯示名稱和說明。 不過，您可以新增其他資訊，例如建立日期、截止日期。 您也可以新增圖示並變更顯示的樣式。

![查看顯示預設配置的「HTML工作區待辦事項」標籤](assets/html-todo-list.png)

本文詳細說明了為「待辦事項」清單中的每個任務添加顯示資訊的步驟。

## 可新增內容 {#what-can-be-added}

您可以新增 `task.json` 由伺服器傳送。 資訊可以以純文字檔案形式添加，也可以使用樣式來格式化資訊。

如需JSON物件說明的詳細資訊，請參閱 [此](/help/forms/using/html-workspace-json-object-description.md) 文章。

## 顯示任務的資訊 {#displaying-information-on-a-task}

1. 關注 [AEM Forms工作區自訂的一般步驟](/help/forms/using/generic-steps-html-workspace-customization.md).
1. 若要顯示任務的其他資訊，必須在的任務區塊中新增對應的索引鍵值組 `translation.json`.

   例如變更 `/apps/ws/locales/en-US/translation.json` 英語：

   ```
   "task" : {
           "reminder" : {
               "value" : "Reminder",
               "tooltip" : "This is reminder __reminderCount__, for this task."
           },
           "deadlined" : {
               "value" : "Deadlined",
               "tooltip" : "This task has deadlined"
           },
           "save" : {
               "message" : "Task has been saved successfully"
           },
           "status" : {
               "deadlined" : "Deadlined",
               "created" : "Created",
               "assignedsaved" : "Draft from assigned task",
               "terminated" : "Terminated",
               "assigned" : "Assigned",
               "unknown" : "Unknown",
               "createdsaved" : "Draft from created task",
               "completed" : "Completed"
           },
           "draft" : {
               "value" : "Saved",
               "tooltip" : "This task is marked as a draft"
           },
           "escalated" : {
               "value" : "Escalated",
               "tooltip" : "This task has been escalated"
           },
           "forward" : {
               "value" : "Forwarded",
               "tooltip" : "This task was forwarded"
           },
           "priority" : {
               "highest" : "Highest priority",
               "normal" : "Normal priority",
               "high" : "High priority",
               "low" : "Low priority",
               "lowest" : "Lowest priority"
           },
           "claimed" : {
               "value" : "Claimed",
               "tooltip" : "This task has been claimed"
           },
           "locked" : {
               "value" : "Locked",
               "tooltip" : "This task is locked"
           },
           "consulted" : {
               "value" : "Consulted",
               "tooltip" : "This task has been consulted"
           },
           "returned" : {
               "value" : "Returned",
               "tooltip" : "This task was returned back"
           },
           "multiplesubmitbuttons" : {
               "message" : "The form associated with this task has multiple submit buttons so the Workspace Complete button will be disabled. Click the appropriate button on the form to submit it."
           },
           "nosubmitbutton" : {
               "message" : "The form associated with this task does not appear to have submit buttons. You may need to upgrade your Adobe Reader version to 9.1 or greater and enable the Reader Submit option in your process."
           },
           "icon" : {
               "tooltip" : "open the task __taskName__"
           }
       }
   ```

   >[!NOTE]
   >
   >為所有支援的語言新增對應的索引鍵值配對。

1. 例如，在任務塊內添加資訊：

   ```
   "stepname" : {
               "value" : "Step Name",
               "tooltip" : "This task belongs to __stepName__ step"
   }
   ```

## 定義新屬性的CSS {#defining-css-for-the-new-property}

1. 您可以將樣式套用至新增至任務的資訊（屬性）。 若要這麼做，您必須為新增至的新屬性新增樣式資訊 `/apps/ws/css/newStyle.css`.

   例如，新增：

   ```css
   .task .taskProperties .stepname{
       width: 25px;
       background: url(../images/stepname.png) no-repeat; /*-------- Or just reuse background image / image-sprite defined .task .taskProperties span of style.css---------------------*/
       background-position: 0px 0px; /*-------- Dummy values, need to be configured as per user background image / image-sprite ---------------------*/
   }
   ```

## 在HTML範本中新增項目 {#adding-entry-in-the-html-template}

最後，您需要在開發套件中加入要新增至任務之每個屬性的項目。 若要建立，請參閱建立AEM Forms工作區程式碼。

1. 複製 `task.html`:

   * 從: `/libs/ws/js/runtime/templates/`
   * 至: `/apps/ws/js/runtime/templates/`

1. 新增資訊至 `/apps/ws/js/runtime/templates/task.html`.

   例如，在下方新增 `div class="taskProperties"`:

   ```
   <span class="stepname" alt="<%= $.t('task.stepname.value')%>" title = '<%= $.t("task.stepname.tooltip",{stepName:stepName})%>'/>
   ```

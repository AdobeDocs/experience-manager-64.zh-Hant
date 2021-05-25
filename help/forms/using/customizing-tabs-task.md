---
title: 自定義任務的頁簽
seo-title: 自定義任務的頁簽
description: 在LiveCycleAEM Forms工作區中，自訂工作之索引標籤的名稱。
seo-description: 在LiveCycleAEM Forms工作區中，自訂工作之索引標籤的名稱。
uuid: 77eabb63-f8ea-4ec0-8a41-b51c65cdecc0
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: ac0a281f-f589-4a70-9bc7-1a23e054b02f
exl-id: 42671435-e0f0-41db-af83-182b01742954
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---

# 為任務{#customizing-tabs-for-a-task}自定義頁簽

您可以在`Start Process` Uber檢視中自訂`Start Process`元件的索引標籤名稱，以及在`ToDo` Uber檢視中自訂`Task Details`元件的索引標籤名稱。

1. 請依照[AEM Forms工作區自訂的一般步驟](/help/forms/using/generic-steps-html-workspace-customization.md)操作。
1. 更改`translation.json`檔案中`tabname`的值。

   例如，將英文的`/apps/ws/locales/en-US/translation.json`變更為下列內容。

   * 對於啟動過程中啟動的任務，請使用`"startprocess" : {}`塊中的以下代碼段。

   ```
   "tabname" : {
               "form" : "Application",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Helper Notes"
           }
   ```

   * 對於待辦事項中的任務，請使用`"todo" : {}`塊中的以下代碼段。

   ```
   "tabname" : {
               "summary" : "Bird's-eye view",
               "history" : "Past",
               "form" : "Form",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Notes"
   }
   ```

   >[!NOTE]
   >
   >為所有支援的語言新增對應的索引鍵值組。

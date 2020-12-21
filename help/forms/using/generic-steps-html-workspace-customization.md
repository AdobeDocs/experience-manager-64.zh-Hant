---
title: AEM Forms工作區自訂的一般步驟
seo-title: AEM Forms工作區自訂的一般步驟
description: 如何開始自訂AEM Forms工作區使用者介面。
seo-description: 如何開始自訂AEM Forms工作區使用者介面。
uuid: 555b5039-cd68-4090-8a8f-30b654474f55
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 54326a05-3fb0-4111-a6ec-230b6473052e
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# AEM Forms工作區自訂的一般步驟{#generic-steps-for-aem-forms-workspace-customization}

執行任何自訂的一般步驟包括：

1. 通過訪問`https://[server]:[port]/lc/crx/de/index.jsp`登錄到CRXDE Lite。
1. 在`/apps`處建立名為`ws`的資料夾（如果資料夾不存在）。 按一下&#x200B;**[!UICONTROL 保存全部]**。
1. 瀏覽至`/apps/ws`，然後瀏覽至&#x200B;**[!UICONTROL 存取控制]**&#x200B;標籤。
1. 在&#x200B;**[!UICONTROL 訪問控制]**&#x200B;清單中，按一下&#x200B;**[!UICONTROL +]**&#x200B;以添加新條目。 再次按一下&#x200B;**[!UICONTROL +]**。
1. 搜索並選擇&#x200B;**[!UICONTROL PERM_WORKSPACE_USER]**&#x200B;承擔者。

   ![選擇「PERM_WORKSPACE_USER承擔者」作為定制HTML工作區的一般步驟的一部分](assets/perm_workspace_user.png)

1. 為承擔者授予`jcr:read`權限。
1. 按一下&#x200B;**[!UICONTROL 保存全部]**。
1. 將`GET.jsp`和`html.jsp`檔案從`/libs/ws`檔案夾複製至`/apps/ws`檔案夾。
1. 複製`/apps/ws`資料夾中的`/libs/ws/locales`資料夾。 按一下&#x200B;**[!UICONTROL 保存全部]**。
1. 更新`GET.jsp`檔案中的參考和相對路徑，如下所示，然後按一下「全部儲存」。****

   ```
   <meta http-equiv="refresh" content="0;URL='/lc/apps/ws/index.html'" />
   ```

1. 請針對CSS自訂執行下列動作：

   1. 導覽至`/apps/ws`資料夾並建立名為`css`的新資料夾。
   1. 在`css`資料夾中，建立名為`newStyle.css`的新檔案。
   1. 開啟`/apps/ws/html`.jsp並變更

   ```css
   <link lang="en" rel="stylesheet" type="text/css" href="css/style.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="css/jquery-ui.css"/>
   ```

   至

   ```css
   <link lang="en" rel="stylesheet" type="text/css" href="../../libs/ws/css/style.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="css/newStyle.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="../../libs/ws/css/jquery-ui.css"/>
   ```

   >[!NOTE]
   >
   >將使用者定義的CSS檔案項目置於newStyle.css項目之後，如上所示。

1. 在/apps/ws/html.jsp檔案中，從

   ```css
   <script data-main="js/main" src="js/libs/require/require.js"></script>
   ```

   至

   ```css
   <script data-main="js/main" src="../../libs/ws/js/libs/require/require.js"></script>
   ```

1. 執行下列動作：

   1. 在`/apps/ws`建立名為`js`的資料夾。 按一下&#x200B;**[!UICONTROL 保存全部]**。
   1. 在`/apps/ws/js`建立名為`libs`的資料夾。 按一下&#x200B;**[!UICONTROL 保存全部]**。
   1. 在`/apps/ws/js/libs`建立名為`jqueryui`的資料夾。 按一下&#x200B;**[!UICONTROL 保存全部]**。
   1. 將`/libs/ws/js/libs/jqueryui/jquery.ui.datepicker-ja.js`複製到`/apps/ws/js/libs/jqueryui`。 按一下&#x200B;**[!UICONTROL 保存全部]**。

1. 請針對HTML自訂執行下列動作：

   1. 在`/apps/ws/js`下，建立名為`runtime`的資料夾。 按一下&#x200B;**[!UICONTROL 保存全部]**。
   1. 在`/apps/ws/js/runtime`下，建立名為`templates`的資料夾。 按一下&#x200B;**[!UICONTROL 保存全部]**。
   1. 將`/libs/ws/js/main.js`複製到`/apps/ws/js/main.js`。
   1. 將/libs/ws/js/registry.js複製至`/apps/ws/js/registry.js`。

1. 按一下「全部儲存」、清除快取並重新整理AEM Forms工作區。****

   存取URL `https://[server]:[port]/lc/ws`並使用管理員／密碼憑證登入。 瀏覽器會重新導向至`https://[server]:[port]/lc/apps/ws/index.html`。


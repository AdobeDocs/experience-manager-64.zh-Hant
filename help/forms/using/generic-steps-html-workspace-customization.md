---
title: AEM Forms工作區自訂的一般步驟
seo-title: Generic steps for AEM Forms workspace customization
description: 如何開始自訂AEM Forms工作區使用者介面。
seo-description: How to get started customizing AEM Forms workspace user interface.
uuid: 555b5039-cd68-4090-8a8f-30b654474f55
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 54326a05-3fb0-4111-a6ec-230b6473052e
exl-id: 2c0dab68-d77e-46fb-832d-90edea510750
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 3%

---

# AEM Forms工作區自訂的一般步驟 {#generic-steps-for-aem-forms-workspace-customization}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

執行任何自訂的一般步驟為：

1. 透過存取 `https://[server]:[port]/lc/crx/de/index.jsp`.
1. 建立名為 `ws`at `/apps`，如果不存在。 按一下 **[!UICONTROL 全部儲存]**.
1. 瀏覽至 `/apps/ws`，並導覽至 **[!UICONTROL 存取控制]** 標籤。
1. 在 **[!UICONTROL 存取控制]** 清單，按一下 **[!UICONTROL +]** 來添加新條目。 按一下 **[!UICONTROL +]** 。
1. 搜尋並選取 **[!UICONTROL PERM_WORKSPACE_USER]** 校長。

   ![選取PERM_WORKSPACE_USER主體，作為自訂HTML工作區的一般步驟的一部分](assets/perm_workspace_user.png)

1. 提供 `jcr:read` 特權給承擔者。
1. 按一下 **[!UICONTROL 全部儲存]**.
1. 複製 `GET.jsp` 和 `html.jsp`檔案 `/libs/ws`檔案夾 `/apps/ws` 檔案夾。
1. 複製 `/libs/ws/locales` 檔案夾 `/apps/ws` 檔案夾。 按一下 **[!UICONTROL 全部儲存]**.
1. 更新 `GET.jsp` 檔案，如下所示，然後按一下 **[!UICONTROL 全部儲存]**.

   ```
   <meta http-equiv="refresh" content="0;URL='/lc/apps/ws/index.html'" />
   ```

1. 請針對CSS自訂執行下列動作：

   1. 導覽至 `/apps/ws` 資料夾和建立名為 `css`.
   1. 在 `css`資料夾，建立名為的新檔案 `newStyle.css`.
   1. 開啟 `/apps/ws/html`.jsp和更改

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
   >將使用者定義的CSS檔案的項目置於newStyle.css的項目之後，如上所示。

1. 在/apps/ws/html.jsp檔案中，從

   ```css
   <script data-main="js/main" src="js/libs/require/require.js"></script>
   ```

   至

   ```css
   <script data-main="js/main" src="../../libs/ws/js/libs/require/require.js"></script>
   ```

1. 請執行下列動作：

   1. 建立名為 `js`at `/apps/ws`. 按一下 **[!UICONTROL 全部儲存]**.
   1. 建立名為 `libs`at `/apps/ws/js`. 按一下 **[!UICONTROL 全部儲存]**.
   1. 建立名為 `jqueryui`at `/apps/ws/js/libs`. 按一下 **[!UICONTROL 全部儲存]**.
   1. 複製 `/libs/ws/js/libs/jqueryui/jquery.ui.datepicker-ja.js` to `/apps/ws/js/libs/jqueryui`. 按一下 **[!UICONTROL 全部儲存]**.

1. 請針對HTML自訂執行下列動作：

   1. 在 `/apps/ws/js`，建立名為 `runtime`. 按一下 **[!UICONTROL 全部儲存]**.
   1. 在 `/apps/ws/js/runtime`，建立名為 `templates`. 按一下 **[!UICONTROL 全部儲存]**.
   1. 複製 `/libs/ws/js/main.js` to `/apps/ws/js/main.js`.
   1. 將/libs/ws/js/registry.js複製到 `/apps/ws/js/registry.js`.

1. 按一下 **[!UICONTROL 全部儲存]**、清除快取，以及重新整理AEM Forms工作區。

   存取URL `https://[server]:[port]/lc/ws` 並使用管理員/密碼憑據登錄。 瀏覽器重新導向至 `https://[server]:[port]/lc/apps/ws/index.html`.

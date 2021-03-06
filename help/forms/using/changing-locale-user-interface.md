---
title: 變更AEM Forms工作區使用者介面的地區設定
seo-title: 變更AEM Forms工作區使用者介面的地區設定
description: 如何修改AEM Forms工作區，將介面上的文字、折疊的類別、佇列和程式，以及日期選取器當地化。
seo-description: 如何修改AEM Forms工作區，將介面上的文字、折疊的類別、佇列和程式，以及日期選取器當地化。
uuid: f8e7d399-98d9-4655-b51f-0346a5713f06
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: e4ca8188-fb9a-44bf-8437-a98abaa7521a
exl-id: 9968f399-454b-4cb2-b6af-2c16428ca7b4
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---

# 變更AEM Forms工作區使用者介面的地區設定{#changing-the-locale-of-aem-forms-workspace-user-interface}

AEM Forms工作區提供英文、法文、德文和日文語言的立即可用支援。 此外，還提供將AEM Forms工作區使用者介面當地化為任何其他語言的功能。

若要將AEM Forms工作區使用者介面當地化為您所選擇的語言：

* 將AEM Forms工作區的文字本地化。
* 將折疊的類別、佇列和程式本地化。
* 本地化日期選擇器

執行上述步驟之前，請務必遵循[AEM Forms工作區自訂的一般步驟](/help/forms/using/generic-steps-html-workspace-customization.md)中所列的步驟。

>[!NOTE]
>
>若要變更AEM Forms工作區登入畫面的語言，請參閱[建立新登入畫面](/help/forms/using/creating-new-login-screen.md)。

## 將文本{#localizing-text}本地化

執行下列步驟以新增對語言&#x200B;*New*&#x200B;和瀏覽器地區設定代碼&#x200B;*nw*&#x200B;的支援。

1. 登入CRXDE Lite。

   CRXDE Lite的預設URL為`https://[server]:[port]/lc/crx/de/index.jsp`。

1. 導覽至位置`apps/ws/locales`並建立新資料夾`nw.`
1. 將檔案`translation.json`從位置`/apps/ws/locales/en-US`複製到位置`/apps/ws/locales/nw`。
1. 導覽至`/apps/ws/locales/nw`並開啟`translation.json`以進行編輯。 對translation.json檔案進行地區特定變更。

   下列範例包含AEM Forms工作區的英文和法文地區設定的translation.json檔案。

   ![translation_json_in_](assets/translation_json_in_en.png) ![entranslation_json_in_fr](assets/translation_json_in_fr.png)

## 將折疊的類別、隊列和進程本地化{#localizing-collapsed-categories-queues-and-processes}

AEM Forms工作區使用影像來顯示類別、佇列和程式的標題。 您需要開發套件才能將這些標題當地化。 如需建立開發套件的詳細資訊，請參閱建立AEM Forms工作區程式碼。](introduction-customizing-html-workspace.md#building-html-workspace-code)[

在下列步驟中，假設新的本地化影像檔案為&#x200B;*Categories_nw.png*、*Queue_nw.png*&#x200B;和&#x200B;*Processes_nw.png*。 建議的影像寬度為19px。

>[!NOTE]
>
>查找瀏覽器語言區域代碼。 開啟 `https://[server]:[port]/lc/libs/ws/Locale.html`.

![collapping_panels_image](assets/collapsing_panels_image.png)

執行下列步驟將影像本地化：

1. 使用WebDAV客戶端，將影像檔案置於&#x200B;*/apps/ws/images*&#x200B;資料夾中。
1. 導覽至&#x200B;*/apps/ws/css*。 開啟&#x200B;*newStyle.css*&#x200B;以進行編輯，並新增下列項目：

   ```
   #categoryListBar .content.nw {
        background: #3e3e3e url(../images/Categories_nw.png) no-repeat 10px 10px;
    }
   
   #filterListBar .content.nw {
       background: #3e3e3e url(../images/Queues_nw.png) no-repeat 10px 10px;
   }
   
   #processNameListBar .content.nw {
       background: #3e3e3e url(../images/Processes_nw.png) no-repeat 10px 10px;
   }
   ```

1. 執行[Workspace Customization](/help/forms/using/introduction-customizing-html-workspace.md)文章中列出的所有語義更改。
1. 導覽至&#x200B;*js/runtime/utility*&#x200B;資料夾，並開啟* usersession.js*檔案以進行編輯。
1. 找到原始代碼塊中列出的代碼，並添加條件&#x200B;*lang !== &#39;nw&#39;*&#x200B;到if語句：

   ```
   // Orignal code
   setLocale = function () {
           var lang = $.trim(i18n.lng());
           if (lang === null || lang === '' || (lang !== 'fr-FR' && lang !== 'de-DE' && lang !== 'ja-JP')) {
               window.lcWorkspace.locale = 'en-US';
           } else {
               window.lcWorkspace.locale = lang;
           }
       }
   ```

   ```
   //new code
    setLocale = function () {
           var lang = $.trim(i18n.lng());
           if (lang === null || lang === '' || (lang !== 'fr-FR' && lang !== 'de-DE' && lang !== 'ja-JP' && lang !== 'nw')) {
               window.lcWorkspace.locale = 'en-US';
           } else {
               window.lcWorkspace.locale = lang;
           }
       }
   ```

## 本地化日期選擇器{#localizing-date-picker}

您需要開發套件，才能將*datepicker *API本地化。 如需建立開發套件的詳細資訊，請參閱[建立AEM Forms工作區程式碼](introduction-customizing-html-workspace.md#building-html-workspace-code)。

1. 下載並解壓縮[jQuery UI套件](https://jqueryui.com/download/all/)，導覽至&#x200B;*&lt;extracted jquery UI套件>*\jquery-ui-1.10.2.zip\jquery-ui-1.10.2\ui\i18n。
1. 將區域設定代碼的jquery.ui.datepicker-nw.js檔案複製到apps/ws/js/libs/jqueryui，並對檔案進行區域設定特定的變更。
1. 導覽至`apps/ws/js`並開啟`jquery.ui.datepicker-nw.js`檔案以進行編輯。
1. 在main.js檔案中為`jquery.ui.datepicker-nw.js.`建立別名的代碼為：`jquery.ui.datepicker-nw.js`

   ```
   jqueryuidatepickernw : pathprefix + 'libs/jqueryui/jquery.ui.datepicker-nw'
   ```

1. 使用別名`jqueryuidatepickernw`將`jquery.ui.datepicker-nw.js`檔案包含在使用日期選擇器的所有檔案中。 日期選擇器用於下列檔案：

   * `js/runtime/views/outofoffice.js`
   * `js/runtime/views/searchtemplatedetails.js`

   下列范常式式碼顯示如何新增jquery.ui.datepicker-nw.js項目：

   ```
   //Original Code
   define([
       'jquery',
       'underscore',
       'backbone',
       'jqueryui',
       'jqueryuidatepickerja',
       'jqueryuidatepickerde',
       'jqueryuidatepickerfr',
       'slimscroll',
       'usersearchview',
       'logmanagerutil',
       'loggerutil'
   ], function ($, _, Backbone, jQueryUI, jQueryUIDatePickerJA, jQueryUIDatePickerDE, jQueryUIDatePickerFR, slimScroll, UserSearch, LogManager, Logger) {
   ```

   ```
   // Code with Date Picker alias for new language
   define([
       'jquery',
       'underscore',
       'backbone',
       'jqueryui',
       'jqueryuidatepickerja',
       'jqueryuidatepickerde',
       'jqueryuidatepickerfr',
       'jqueryuidatepickernw', // Date Picker alias
       'slimscroll',
       'usersearchview',
       'logmanagerutil',
       'loggerutil'
   ], function ($, _, Backbone, jQueryUI, jQueryUIDatePickerJA, jQueryUIDatePickerDE, jQueryUIDatePickerFR, jQueryUIDatePickerNW, slimScroll, UserSearch, LogManager, Logger) {
   ```

1. 在使用日期挑選器API的所有檔案中，變更預設的日期挑選器API設定。 日期挑選器API用於下列檔案：

   * apps\ws\js\runtime\views\searchtemplatedetails.js
   * apps\ws\js\runtime\views\outofoffice.js

   更改以下代碼以添加新區域設定：

   ```
   if (locale === 'ja-JP') {
      $.datepicker.setDefaults($.datepicker.regional.ja);
   } else if (locale === 'de-DE') {
      $.datepicker.setDefaults($.datepicker.regional.de);
   } else if (locale === 'fr-FR') {
      $.datepicker.setDefaults($.datepicker.regional.fr);
   } else {
      $.datepicker.setDefaults($.datepicker.regional['']);
   }
   ```

至

```
if (locale === 'ja-JP') {
    $.datepicker.setDefaults($.datepicker.regional.ja);
} else if (locale === 'de-DE') {
    $.datepicker.setDefaults($.datepicker.regional.de);
} else if (locale === 'fr-FR') {
    $.datepicker.setDefaults($.datepicker.regional.fr);
} else if (locale === 'nw') {
    $.datepicker.setDefaults($.datepicker.regional.nw);
} else {
    $.datepicker.setDefaults($.datepicker.regional['']);
}
```

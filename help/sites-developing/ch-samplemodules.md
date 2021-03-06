---
title: 範例ContextHub UI模組類型
seo-title: 範例ContextHub UI模組類型
description: ContextHub提供數個範例UI模組，您可在解決方案中使用
seo-description: ContextHub提供數個範例UI模組，您可在解決方案中使用
uuid: af1a8fa1-8f8b-49c8-b2ca-ba92c955871e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: fa68c786-5102-4cc3-b61c-2565ee919768
exl-id: 637ec80e-320f-4cf7-b09a-9f3cbf47bb63
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1194'
ht-degree: 0%

---

# 範例ContextHub UI模組類型{#sample-contexthub-ui-module-types}

ContextHub提供數個範例UI模組，您可在解決方案中使用。 提供下列資訊：

* UI模組的主要功能。
* 在何處查找原始碼，以便您可以開啟它以學習。
* 如何設定UI模組。

有關將UI模組添加到ContextHub的資訊，請參閱[添加UI模組](/help/sites-administering/contexthub-config.md#adding-a-ui-module)。 有關開發UI模組的資訊，請參閱[建立ContextHub UI模組類型](/help/sites-developing/ch-extend.md#creating-contexthub-ui-module-types)。

## contexthub.base UI模組類型{#contexthub-base-ui-module-type}

contexthub.base UI模組類型是所有其他UI模組類型的基本類型。 因此，它提供轉譯儲存資料的通用功能。

提供下列功能：

* **標題和圖示：** 指定UI模組的標題和圖示。您可以使用URL或Coral UI圖示庫來參照圖示。
* **儲存資料：** 識別要從中擷取資料的一或多個儲存。
* **內容：** 指定UI模組中顯示的內容，與ContextHub工具列中顯示的內容相同。
* **彈出式內容：** 指定在按一下或點選UI模組時，出現在彈出式視窗中的內容。
* **全螢幕模式：** 控制是否允許全螢幕模式。

原始碼位於/libs/granite/contexthub/code/ui/container/js/ContextHub.UI.BaseModuleRenderer.js。

### 設定 {#configuration}

使用JSON格式的Javascript物件來設定contexthub.base UI模組。 納入下列任一屬性以設定UI模組功能：

* **影像：** 要顯示為圖示之影像的URL。
* **圖示：** Coral UI圖 [示類](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html) 別的名稱。如果您同時為圖示和影像屬性指定值，則會使用影像。

* **title:** UI模組的標題。當指標暫停在UI模組圖示上時，標題就會顯示。
* **fullscreen:** 指出UI模組是否支援全螢幕模式的布林值。使用`true`支援全螢幕，使用`false`防止全螢幕模式。

* **範本：** Handlebarstemplate，指 [](https://handlebarsjs.com/) 定要在ContextHub工具列中呈現的內容。最多使用兩個`<p>`標籤。

* **storeMapping:** 索引鍵/存放區對應。使用Handlebar範本中的索引鍵存取相關聯的ContextHub存放區資料。
* **list:** 按一下UI模組時，在彈出式視窗中顯示為清單的項目陣列。如果包含此項目，請勿包含popoverTemplate。 值是物件的陣列，具有下列鍵值：

   * 標題：要針對此項目顯示的文本
   * 影像：（選用）應顯示在左側的影像URL
   * 圖示：（可選）左側應顯示的CUI表徵圖類；如果指定影像，則忽略
   * 已選取：（可選）一個布林值，它指定是否應將此項顯示為選定項(true=selected)。 依預設，選取的項目會以粗體字型顯示。 使用`listType`屬性來配置其他外觀（請參見下面）。

* **listType:** 用於彈出式清單項目的樣式。使用下列其中一個值：

   * 勾號
   * 核取方塊
   * 廣播

* **popoverTemplate:** Handlebars範本，指定當按一下UI模組時，要在彈出視窗中呈現的內容。如果包括此項目，則不要包括`list`項目。

### 範例 {#example}

下列範例會設定contexthub.base UI模組，以顯示[contexthub.emulators](/help/sites-developing/ch-samplestores.md#granite-emulators-sample-store-candidate)存放區的資訊。 `template`項目示範如何使用`storeMapping`項目建立的索引鍵，從存放區取得資料。

```xml
{
   "icon": "coral-Icon--move",
    "title": "Screen Resolution",
    "storeMapping": {
      "emulator": "emulators"
    },
    "template": "<p>{{{ i18n \"Resolution\"}}}</p><p>{{{emulator.currentDevice.width}}} x {{{emulator.currentDevice.height}}}</p>"
}
```

![chlimage_1-76](assets/chlimage_1-76.png)

## contexthub.browserinfo UI模組類型{#contexthub-browserinfo-ui-module-type}

contexthub.browserinfo UI模組會顯示用戶端網頁瀏覽器和作業系統的相關資訊。 根據[contexthub.surferinfo](/help/sites-developing/ch-samplestores.md#contexthub-surferinfo-sample-store-candidate)儲存候選項，從surferinfo儲存中獲得資訊。

![chlimage_1-77](assets/chlimage_1-77.png)

UI模組的原始碼位於/libs/granite/contexthub/components/modules/browserinfo。 雖然contexthub.browserinfo擴充了contexthub.base UI模組，但不會覆寫或提供其他功能。 實施提供轉譯瀏覽器資訊的預設設定。

### 設定 {#configuration-1}

contexthub.browserinfo UI模組的例項不需要「詳細設定」的值。 下列JSON文字代表模組的預設設定。

```xml
{
   "icon":"coral-Icon--globe",
   "title":"Browser/OS Information",
   "storeMapping":{"surferinfo":"surferinfo"},
   "template":"<p>{{surferinfo.browser.family}} {{surferinfo.browser.version}}</p><p>{{surferinfo.os.name}} {{surferinfo.os.version}}</p>"
}
```

## contexthub.datetime UI模組類型{#contexthub-datetime-ui-module-type}

contexthub.datetime UI模組顯示儲存在名為datetime的儲存中的日期和時間，該儲存基於[contexthub.datetime](/help/sites-developing/ch-samplestores.md#contexthub-datetime-sample-store-candidate)儲存候選。

![chlimage_1-78](assets/chlimage_1-78.png)

模組提供彈出式表單，可讓您變更商店中的日期和時間。

contexthub.datetime UI模組的源位於/libs/granite/contexthub/components/modules/datetime。

### 設定 {#configuration-2}

contexthub.datetime UI模組的實例不需要「詳細配置」的值。 下列JSON文字代表模組的預設設定。

```xml
{
   "icon":"coral-Icon--clock",
   "title":"DATE&TIME",
   "clickable":true,
   "storeMapping":{"d":"datetime"},
   "template":"<p class=\"contexthub-module-line1\">{{i18n \"Date&Time\"}}</p><p class=\"contexthub-module-line2\">{{d.formatted.locale.date}} {{d.formatted.locale.time}}</p>",
   "popoverTemplate":"<div class=\"datetime center\"><div class=\"coral-DatePicker-calendar\" data-init=\"datepicker\"><input class=\"coral-Textfield\" type=\"datetime\" value=\"{{d.formatted.iso}}\"><button class=\"coral-Button coral-Button--secondary coral-Button--square\" title=\"{{i18n \"Datetime picker\"}}\"><i class=\"coral-Icon coral-Icon--calendar coral-Icon--sizeS\"></i></button></div></div>"
}
```

## contexthub.location UI模組類型{#contexthub-location-ui-module-type}

contexthub.location UI模組會顯示用戶端的經度和緯度。 模組會提供彈出視窗，顯示Google地圖，您可以按一下該地圖來變更目前位置。 模組從名為geolocation的ContextHub儲存區獲取資訊，該儲存區基於[contexthub.geolocation](/help/sites-developing/ch-samplestores.md#contexthub-geolocation-sample-store-candidate)儲存候選。

![chlimage_1-80](assets/chlimage_1-80.png)

UI模組的來源位於/etc/cloudsettings/default/contexthub/geolocation。

### 設定 {#configuration-4}

contexthub.location UI模組的例項不需要「詳細設定」的值。 下列JSON文字代表模組的預設設定。

```xml
{
 "icon":"coral-Icon--compass",
 "title":"Location",
 "clickable":true,
 "editable":{"key":"/geolocation","disabled":[],"hidden":["/geolocation/generatedThumbnail","/geolocation/city","/geolocation/country"]},
 "fullscreen":true,
 "storeMapping":{"g":"geolocation"},
 "template":"<p>{{i18n \"Location\"}}</p><p>{{g.address.postalCode}} {{g.address.city}}{{#if g.address.city}}{{#if g.address.region}},{{/if}}{{/if}} {{g.address.region}}</p>",
 "list":[
  {"title":"Basel, Switzerland",
  "data":{"longitude":7.58929,"latitude":47.554746,"city":"Basel","country":"Switzerland"}},
  {"title":"Melbourne, Australia",
  "data":{"longitude":144.96328,"latitude":-37.814107,"city":"Melbourne","country":"Australia"}},
  {"title":"Beijing, China",
  "data":{"longitude":116.407526,"latitude":39.90403,"city":"Beijing","country":"China"}},
  {"title":"New York, NY, USA",
  "data":{"longitude":-74.005973,"latitude":40.714353,"city":"New York","country":"United States"}},
  {"title":"Paris, France",
  "data":{"longitude":2.352222,"latitude":48.856614,"city":"Paris","country":"France"}},
  {"title":"Rio de Janeiro, Brazil",
  "data":{"longitude":-43.20071,"latitude":-22.913395,"city":"Rio","country":"Brazil"}},
  {"title":"San Jose, CA, USA",
  "data":{"longitude":-121.894955,"latitude":37.339386,"city":"San Jose","country":"United States"}},
  {"title":"Tokyo, Japan",
  "data":{"longitude":139.691706,"latitude":35.689487,"city":"Shinjuku","country":"Japan"}}
 ],
 "listType":"checkmark"
}
```

## contexthub.screen-orientation UI模組類型{#contexthub-screen-orientation-ui-module-type}

contexthub.screen-orientation UI模組會顯示用戶端的目前螢幕方向。 雖然預設為停用，但模組會提供彈出視窗，讓您選取方向。 該模組從ContextHub儲存區獲取資訊，該儲存區命名模擬器基於[granite.emulators](/help/sites-developing/ch-samplestores.md#granite-emulators-sample-store-candidate)儲存候選。

![chlimage_1-81](assets/chlimage_1-81.png)

UI模組的來源位於/libs/granite/contexthub/components/modules/screen-orientation。

### 設定 {#configuration-5}

Contexthub.screen-orientation UI模組的例項不需要「詳細設定」的值。 下列JSON文字代表模組的預設設定。 請注意，預設情況下，`clickable`屬性為`false`。 如果覆蓋將`clickable`設定為`true`的預設配置，按一下模組將顯示彈出窗口，您可以在其中選擇方向。

```xml
{
   "icon":"coral-Icon--rotateRight",
   "title":"Screen Orientation",
   "clickable":false,
   "storeMapping":{"emulator":"emulators"},
   "template":"<p>{{{ i18n \"Screen Orientation\" }}}</p><p>{{{ emulator.currentDevice.orientation }}}",
   "listReference":"/emulators/orientations",
   "listType":"checkmark"
}
```

## contexthub.tagcloud UI模組類型{#contexthub-tagcloud-ui-module-type}

contexthub.tagcloud UI模組會顯示標籤的相關資訊。 在工具列上，UI模組會顯示標籤數。 彈出式功能表會顯示新增標籤的標籤雲和文字方塊。 UI模組從名為tagcloud的ContextHub存放區取得資訊，該存放區是以[contexthub.tagcloud](/help/sites-developing/ch-samplestores.md#contexthub-tagcloud-sample-data-store)存放區候選項為基礎。

![chlimage_1-82](assets/chlimage_1-82.png)

UI模組的來源位於/libs/granite/contexthub/components/modules/tagcloud。

### 設定 {#configuration-6}

Contexthub.tagcloud UI模組的例項不需要「詳細設定」的值。 下列JSON文字代表模組的預設設定。

```xml
{
   "icon":"coral-Icon--tag",
   "title":"TagCloud",
   "clickable":true,
   "storeMapping":{"t":"tagcloud"},
   "maxTags":20,
   "template":"<p class=\"contexthub-module-line1\">{{i18n \"TagCloud\"}}</p><p class=\"contexthub-module-line2\">{{stats.total}} {{i18n \"Tags\"}}</p>",
   "popoverTemplate":"<div class=\"contexthub-popover-content center\"><p class=\"stats\">{{stats.total}} {{i18n \"Tags\"}} | {{stats.hits}} {{i18n \"Hits\"}} | {{i18n \"Last tag\"}}: {{#if stats.recent}}{{stats.recent}}{{else}}{{i18n \"Unknown\"}}{{/if}}</p><p class=\"tagcloud\">{{#each tags}}<span class=\"tag{{this.weight}}\">{{this.name}}</span> {{/each}}</p><div class=\"coral-InputGroup\"><input type=\"text\" class=\"coral-InputGroup-input coral-Textfield tag-name\" placeholder=\"{{i18n \"Add a namespace:my/tag\"}}\" pattern=\"^[A-Za-z0-9_\\-]+(:[A-Za-z0-9_\\-\\/]+)?$\" title=\"{{i18n \"namespace:my/tag\"}}\"><span class=\"coral-InputGroup-button\"><button class=\"coral-Button coral-Button--secondary coral-Button--square contexthub-new-tag\" type=\"button\" title=\"{{i18n \"increment\"}}\"><i class=\"coral-Icon coral-Icon--sizeS coral-Icon--add\"></i></button></span></div></div>"
}
```

## granite.profile UI模組類型{#granite-profile-ui-module-type}

granite.profile ContextHub UI模組會顯示目前使用者的顯示名稱。 彈出式功能會顯示使用者的登入名稱，並讓您變更顯示名稱的值。 UI模組從名為profile的ContextHub存放區取得資訊，該存放區是以[granite.profile](/help/sites-developing/ch-samplestores.md#granite-profile-sample-store-candidate)存放候選項為基礎。

![chlimage_1-83](assets/chlimage_1-83.png)

UI模組的來源為/libs/granite/contexthub/components/modules/profile。

### 設定 {#configuration-7}

grantie.profile UI模組的例項不需要「詳細設定」的值。 下列JSON文字代表模組的預設設定。

```xml
{
   "icon":"coral-Icon--user",
   "title":"Profile",
   "clickable":true,
   "editable":{
      "key":"/profile",
      "disabled":["/profile/authorizableId"],
      "hidden":["/profile/avatar","/profile/path"]},
   "storeMapping":{"p":"profile"},
   "template":"<p class=\"contexthub-module-line1\">{{i18n \"Persona\"}}</p><p class=\"contexthub-module-line2\">{{p.displayName}}</p>",
   "listType":"checkmark"
}
```

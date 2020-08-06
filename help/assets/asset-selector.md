---
title: 資產選擇器
description: 瞭解如何使用資產選擇器來搜尋、篩選、瀏覽及擷取Adobe Experience Manager(AEM)Assets中資產的中繼資料。 此外，也瞭解如何自訂資產選擇器介面。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---


# Asset Selector {#asset-selector}

>[!NOTE]
>
>在舊版AEM中，「資 [產選擇器](https://helpx.adobe.com/experience-manager/6-2/assets/using/asset-picker.html) 」已命名為「資產選擇器」。

資產選擇器可讓您在Adobe Experience Manager(AEM)資產內搜尋、篩選及瀏覽資產。 您也可以使用資產選擇器擷取您選取之資產的中繼資料。 若要自訂資產選擇器介面，您可以使用支援的請求參數來啟動它。 這些參數會針對特定藍本設定資產選擇器的上下文。

目前，您可以將請求參數 `Asset Type` (*影像／視訊／文字*)和 `Selection mode` (單一／多重&#x200B;**)作為資產選擇器的上下文資訊，在整個選取範圍內仍保持不變。

資產選擇器使用HTML5 **Window.postMessage** (HTML5 Window.postMessage)訊息，將所選資產的資料傳送給收件者。

資產選擇器是以Granite的基礎選擇器辭彙為基礎。 依預設，資產選擇器會在「瀏覽」模式中運作。 不過，您可以使用Omnisearch體驗套用篩選器，以調整您對特定資產的搜尋。

您可以將任何網頁（不論其是否屬於CQ容器）與資產選擇器(`https://[AEM_server]:[port]/aem/assetpicker.html`)整合。

## 上下文參數 {#contextual-parameters}

您可以在URL中傳遞下列請求參數，以在特定內容中啟動資產選擇器：

| 名稱 | 值 | 範例 | 目的 |
|---|---|---|---|
| 資源尾碼(B) | 資料夾路徑作為URL中的資源尾碼：`http://localhost:4502/aem/`<br>`assetpicker.html/<folder_path>` | 若要啟動已選取特定檔案夾的資產選擇器，例如已選取 `/content/dam/we-retail/en/activities` 檔案夾，URL應為： `http://localhost:4502/aem/assetpicker.html`<br>`/content/dam/we-retail/en/activities?assettype=images` | 如果在啟動資產選擇器時需要選取特定資料夾，請將其作為資源尾碼傳遞。 |
| 模式 | 單一，多重 | `http://localhost:4502/aem/assetpicker.html`<br>`?mode=multiple` <br> `http://localhost:4502/aem/assetpicker.html`<br>`?mode=single` | 在多個模式中，您可以使用資產選擇器同時選取多個資產。 |
| mimetype | 資產的mimetype(s`/jcr:content/metadata/dc:format`)（也支援萬用字元） | <ul><li>`http://localhost:4502/aem/assetpicker.html`<br>`?mimetype=image/png`</li>  <li>`http://localhost:4502/aem/assetpicker.html`<br>`?mimetype=*png`</li>  <li>`http://localhost:4502/aem/assetpicker.html`<br>`?mimetype=*presentation`</li>  <li>`http://localhost:4502/aem/assetpicker.html`<br>`?mimetype=*presentation&mimetype=*png`</li></ul> | 使用它以MIME類型篩選資產 |
| 對話方塊 | true, false | `http://localhost:4502/aem/assetpicker.html`<br>`?dialog=true` | 使用這些參數將資產選擇器開啟為「花崗岩」對話方塊。 只有當您透過Granite路徑欄位啟動資產選擇器，並將其設定為pickerSrc URL時，此選項才適用。 |
| assettype(S) | 影像、檔案、多媒體、封存 | <ul><li>`http://localhost:4502/aem/assetpicker.html`<br>`?assettype=images`</li> <li>`http://localhost:4502/aem/assetpicker.html?assettype=documents`</li> <li>`http://localhost:4502/aem/assetpicker.html?assettype=multimedia`</li> <li>`http://localhost:4502/aem/assetpicker.html?assettype=archives`</li> | 使用這個選項可根據傳遞的值來篩選資產類型。 |
| 根 | `<folder_path>` | `http://localhost:4502/aem/`<br>`assetpicker.html?assettype=images`<br>`&root=/content/dam/we-retail/en/activities` | 使用此選項可指定資產選擇器的根資料夾。 在這種情況下，資產選擇器可讓您只選取根資料夾下的子資產（直接／間接）。 |

## 使用資產選擇器 {#using-the-asset-selector}

1. 若要存取資產選擇器介面，請前往 `https://[AEM_server]:[port]/aem/assetpicker`。
1. 導覽至所要的檔案夾，並選取一或多個資產。

   ![chlimage_1-441](assets/chlimage_1-441.png)

   或者，您可以從OmniSearch方塊中搜尋所需資產，然後選取它。

   ![chlimage_1-442](assets/chlimage_1-442.png)

   如果您使用OmniSearch方塊搜尋資產，則可從「篩選器」窗格選取各種篩選器 **** ，以調整搜尋。

   ![chlimage_1-443](assets/chlimage_1-443.png)

1. 點選／按一 **[!UICONTROL 下工具列]** 中的「選取」。

---
title: 在HTML5表單中建立自訂外觀
seo-title: 在HTML5表單中建立自訂外觀
description: 您可以將自訂Widget外掛至行動Forms。 您可以擴展現有的jQuery Widget，或開發您自己的自訂Widget。
seo-description: 您可以將自訂Widget外掛至行動Forms。 您可以擴展現有的jQuery Widget，或開發您自己的自訂Widget。
uuid: afb16f42-e404-478b-82dd-4b5b59c4f184
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 5d860f05-3257-4cf7-93dd-77d226d59b39
feature: 行動表單
exl-id: e9e53b6d-6403-4d37-bac1-efaff0317f34
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 0%

---

# 在HTML5表單中建立自定義外觀{#create-custom-appearances-in-html-forms}

您可以將自訂Widget外掛至行動Forms。 您可以擴展現有的jQuery Widget，或使用外觀框架開發自己的自定義Widget。 XFA引擎使用各種小工具，有關詳細資訊，請參閱適用性和HTML5表單](/help/forms/using/introduction-widgets.md)的[外觀架構。

![預設和自訂介面工具集](assets/custom-widgets.jpg)
**的範例：** *預設和自訂介面工具集的範例*

## 將自訂Widget與HTML5表單整合{#integrating-custom-widgets-with-html-forms}

### 建立設定檔  {#create-a-profile-nbsp}

您可以建立設定檔或選擇現有設定檔以新增自訂介面工具集。 有關建立配置式的詳細資訊，請參閱[建立自定義配置式](/help/forms/using/custom-profile.md)。

### 建立Widget {#create-a-widget}

HTML5表單提供介面工具集架構的實作，可延伸以建立新介面工具集。 實作是jQuery Widget *abstractWidget*，可延伸以編寫新Widget。 只有延伸/覆寫下列功能，新介面工具集才能運作。

<table> 
 <tbody> 
  <tr> 
   <td>函式/類</td> 
   <td>說明</td> 
  </tr> 
  <tr> 
   <td>轉譯</td> 
   <td>呈現函式返回構件的預設HTML元素的jQuery對象。 預設的HTML元素應為可聚焦類型。 例如， &lt;a&gt;、&lt;input&gt;和&lt;li&gt;。 傳回的元素會作為$userControl使用。 如果$userControl指定了上述約束，則AbstractWidget類的函式將如預期工作，否則某些常見API（焦點、按一下）需要更改。 </td> 
  </tr> 
  <tr> 
   <td>getEventMap</td> 
   <td>傳回映射以將HTML事件轉換為XFA事件。 <br /> {<br /> blur:XFA_EXIT_EVENT,<br /> }<br /> 此範例顯示模糊是HTML事件，而XFA_EXIT_EVENT是對應的XFA事件。 </td> 
  </tr> 
  <tr> 
   <td>getOptionsMap</td> 
   <td>傳回地圖，詳細說明在變更選項時要執行的動作。 鍵是提供給介面工具集的選項，值是每當檢測到該選項中的更改時調用的函式。 介面工具集為所有公共選項（value和displayValue除外）提供處理程式</td> 
  </tr> 
  <tr> 
   <td>getCommitValue</td> 
   <td>每當Widget的值儲存在XFAModel中時（例如，在textField的退出事件上）,Widget架構就會載入函式。 實施應傳回儲存在介面工具集中的值。 處理常式會隨選項的新值提供。</td> 
  </tr> 
  <tr> 
   <td>showValue</td> 
   <td>依預設，在輸入事件時的XFA中，會顯示欄位的rawValue。 呼叫此函式是為了向使用者顯示rawValue。 </td> 
  </tr> 
  <tr> 
   <td>showDisplayValue</td> 
   <td>依預設，在退出事件時的XFA中，會顯示欄位的formattedValue 。 調用此函式是為了向用戶顯示formattedValue。 </td> 
  </tr> 
 </tbody> 
</table>

若要建立您自己的介面工具集，請在上述建立的設定檔中，納入JavaScript檔案的參考，該檔案包含覆寫的函式和新新增的函式。 例如， *sliderNumericFieldWidget*&#x200B;是數值欄位的介面工具集。 若要在您的設定檔中於標題區段使用介面工具集，請加入下列行：

```
window.formBridge.registerConfig("widgetConfig" , widgetConfigObject);
```

### 使用XFA指令碼引擎註冊自訂Widget  {#register-custom-widget-with-xfa-scripting-engine-nbsp}

當自訂介面工具集程式碼準備就緒時，請使用`registerConfig`[表單橋接器](/help/forms/using/form-bridge-apis.md)的API，向指令碼引擎註冊介面工具集。 此參數會以widgetConfigObject為輸入。

```
window.formBridge.registerConfig("widgetConfig",
        {
        ".<field-identifier>":"<name-of-the-widget>"
        }
    );
```

#### widgetConfigObject {#widgetconfigobject}

介面工具集設定會以JSON物件（索引鍵值配對的集合）提供，其中索引鍵可識別欄位，值代表要與這些欄位搭配使用的介面工具集。 範例設定如下：

```
*{*

*“identifier1” : “customwidgetname”,  
“identifier2” : “customwidgetname2”,  
..  
}*
```

其中，「identifier」是jQuery CSS選取器，代表特定欄位、特定類型的一組欄位或所有欄位。 下列列出不同情況下的識別碼值：

| 識別碼類型 | 識別碼 | 說明 |
|---|---|---|
| 具有名稱欄位名稱的特定欄位 | 識別碼：&quot;div.fieldname&quot; | 所有名為&#39;fieldname&#39;的欄位都會使用介面工具集呈現。 |
| 所有類型為&#39;type&#39;的欄位（其中type為NumericField、DateField等）。: | 識別碼：&quot;div.type&quot; | 對於Timefield和DateTimeField，類型為文本欄位，因為不支援這些欄位。 |
| 所有欄位 | 識別碼：&quot;div.field&quot; |  |

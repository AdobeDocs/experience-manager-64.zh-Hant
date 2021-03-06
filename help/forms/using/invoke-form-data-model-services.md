---
title: 從適用性表單叫用表單資料模型服務的API
seo-title: 從適用性表單叫用表單資料模型服務的API
description: '說明可用來從適用性表單欄位中叫用在WSDL中寫入的Web服務的invokeWebServices API。 '
seo-description: '說明可用來從適用性表單欄位中叫用在WSDL中寫入的Web服務的invokeWebServices API。 '
uuid: 40561086-e69d-4e6a-9543-1eb2f54cd836
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: aa3e50f1-8f5a-489d-a42e-a928e437ab79
feature: 適用性表單
exl-id: 0653b0e4-a697-472a-8093-5ed48ede3c75
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 1%

---

# 從適用性表單叫用表單資料模型服務的API {#api-to-invoke-form-data-model-service-from-adaptive-forms}

## 概覽 {#overview}

AEM Forms可讓表單作者從最適化表單欄位中叫用在表單資料模型中設定的服務，進一步簡化並增強表單填寫體驗。 若要叫用資料模型服務，您可以在可視化編輯器中建立規則，或使用[規則編輯器](/help/forms/using/rule-editor.md)的代碼編輯器中的`guidelib.dataIntegrationUtils.executeOperation` API指定JavaScript。

本檔案著重於使用`guidelib.dataIntegrationUtils.executeOperation` API來叫用服務來編寫JavaScript。

## 使用API {#using-the-api}

`guidelib.dataIntegrationUtils.executeOperation` API從適用性表單欄位內叫用服務。 API語法如下：

```
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs)
```

API需要下列參數。

| 參數 | 說明 |
|---|---|
| `operationInfo` | 用於指定表單資料模型標識符、操作標題和操作名稱的結構 |
| `inputs` | 用於指定其值輸入到服務操作的表單對象的結構 |
| `outputs` | 用於指定將填充服務操作返回值的表單對象的結構 |

`guidelib.dataIntegrationUtils.executeOperation` API的結構指定了有關服務操作的詳細資訊。 結構的語法如下。

```
var operationInfo = {
formDataModelId,
operationTitle,
operationName
};
var inputs = {
inputField1,
inputFieldN
};
var outputs = {
outputField1,
outputFieldN
}
```

API結構會指定服務操作的下列詳細資訊。

<table> 
 <tbody> 
  <tr> 
   <th>參數</th> 
   <th>說明</th> 
  </tr> 
  <tr> 
   <td><code>forDataModelId</code></td> 
   <td>指定表單資料模型的存放庫路徑，包括其名稱</td> 
  </tr> 
  <tr> 
   <td><code>operationName</code></td> 
   <td>指定要執行的服務操作的名稱</td> 
  </tr> 
  <tr> 
   <td><code>input</code></td> 
   <td>將一個或多個表單對象映射到服務操作的輸入參數</td> 
  </tr> 
  <tr> 
   <td>輸出</td> 
   <td>映射一個或多個表單對象以從服務操作輸出值以填充表單欄位<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 調用服務{#sample-script-to-invoke-a-service}的示例指令碼

以下示例指令碼使用`guidelib.dataIntegrationUtils.executeOperation` API調用`employeeAccount`表單資料模型中配置的`getAccountById`服務操作。

`getAccountById`操作將`employeeID`表單欄位中的值作為`empId`參數的輸入，並返回相應員工的員工名稱、帳號和帳戶餘額。 輸出值會填入指定的表單欄位中。 例如， `name`引數中的值會填入`fullName`表單元素中，以及`account`表單元素中`accountNumber`引數的值。

```
var operationInfo = {
"formDataModelId": "/content/dam/formsanddocuments-fdm/employeeAccount",
"operationName": "getAccountDetails"
};
var inputs = {
"empid" : employeeID
};
var outputs = {
"name" : fullName,
"accountNumber" : account,
"balance" : balance
};
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs);
```

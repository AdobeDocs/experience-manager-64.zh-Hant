---
title: 從適用性表單叫用表單資料模型服務的API
seo-title: API to invoke form data model service from adaptive forms
description: 說明可用來從適用性表單欄位中叫用在WSDL中寫入的Web服務的invokeWebServices API。
seo-description: Explains the invokeWebServices API that you can use to invoke web services written in WSDL from within an adaptive form field.
uuid: 40561086-e69d-4e6a-9543-1eb2f54cd836
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: aa3e50f1-8f5a-489d-a42e-a928e437ab79
feature: Adaptive Forms
exl-id: 0653b0e4-a697-472a-8093-5ed48ede3c75
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 2%

---

# 從適用性表單叫用表單資料模型服務的API {#api-to-invoke-form-data-model-service-from-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 概觀 {#overview}

AEM Forms可讓表單作者從最適化表單欄位中叫用在表單資料模型中設定的服務，進一步簡化並增強表單填寫體驗。 若要叫用資料模型服務，您可以在視覺編輯器中建立規則，或使用 `guidelib.dataIntegrationUtils.executeOperation` API(位於 [規則編輯器](/help/forms/using/rule-editor.md).

本檔案著重於使用 `guidelib.dataIntegrationUtils.executeOperation` 叫用服務的API。

## 使用API {#using-the-api}

此 `guidelib.dataIntegrationUtils.executeOperation` API從適用性表單欄位中叫用服務。 API語法如下：

```
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs)
```

API需要下列參數。

| 參數 | 說明 |
|---|---|
| `operationInfo` | 用於指定表單資料模型標識符、操作標題和操作名稱的結構 |
| `inputs` | 用於指定其值輸入到服務操作的表單對象的結構 |
| `outputs` | 用於指定將填充服務操作返回值的表單對象的結構 |

的結構 `guidelib.dataIntegrationUtils.executeOperation` API指定服務操作的詳細資訊。 結構的語法如下。

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

## 叫用服務的範例指令碼 {#sample-script-to-invoke-a-service}

下列範例指令碼使用 `guidelib.dataIntegrationUtils.executeOperation` 叫用 `getAccountById` 在中配置的服務操作 `employeeAccount` 表單資料模型。

此 `getAccountById` 操作會採用 `employeeID` 表單欄位作為輸入 `empId` 參數和返回相應員工的員工名稱、帳號和帳戶餘額。 輸出值會填入指定的表單欄位中。 例如， `name` 引數會填入 `fullName` 表單元素和值 `accountNumber` 引數 `account` 表單元素。

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

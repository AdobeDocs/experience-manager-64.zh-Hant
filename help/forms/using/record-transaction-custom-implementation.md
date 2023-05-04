---
title: 記錄自訂實施的交易
seo-title: Record a transaction for custom implementations
description: 使用TransactionRecorder API可自動記錄未作為事務處理的操作
seo-description: Use the TransactionRecorder API to record actions which are not accounted as transactions automatically
uuid: a22b1a0b-7553-4a17-8fb4-a3bee97b4a98
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: 0d961630-573b-4c8e-902f-996f1d1265b6
exl-id: e97ecb77-96a0-44cf-8da9-1e85cc122011
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 2%

---

# 記錄自訂實施的交易 {#record-a-transaction-for-custom-implementations}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

使用TransactionRecorder API可自動記錄未作為事務處理的操作

您可以使用自訂程式碼來提交PDF表單、傳送代理UI預覽URL給使用者以預覽互動式通訊，或使用自訂方法提交表單，而非使用AEM Forms隨附的提交方法。 AEM Forms API的所有先前提及動作和自訂實作不會計為交易。 AEM Forms提供API, [TransactionRecorder](https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/aem/transaction/core/ITransactionRecorder.html)，以記錄交易等動作。

要記錄事務，請寫入 [標準sling servlet](https://helpx.adobe.com/experience-manager/using/custom-sling-servlets.html) 並從客戶端調用servlet以記錄事務。 您可以使用AJAX或任何其他標準方法呼叫servlet。

## 伺服器端程式碼範例 {#sample-server-sided-code}

您可以使用以下示例代碼，使用自定義OSGi包從JAVA類運行TransactionRecorder API。

```java
import com.adobe.aem.transaction.core.ITransactionRecorder;
import com.adobe.aem.transaction.core.model.TransactionRecord;
import com.adobe.aem.transaction.core.exception.TransactionException;
import com.adobe.aem.transaction.core.FormsTransactionConstants;

@Reference
private ITransactionRecorder transactionRecorder;
 
doPost (SlingHttpServletRequest request, SlingHttpServletResponse response) {
    transactionRecorder.startContext();
    TransactionRecord txRecord = extractTxRecordFromRequest(request); //extract transaction relevant data from request
    try {
        bool success = doBillableWork();
        if (success) {
            transactionRecorder.recordTransaction(txRecord);
        }
    } catch (Exception e) {
        //exception handling
    } finally {
        transactionRecorder.endContext();
    }
}

//Here, it is assumed that txInfo is passed in Stringified json form in the ajax call (in data parameter). You can pass txInfo from client in any way that you find suitable.
private TransactionRecord extractTxRecordFromRequest(SlingHttpServletRequest request) {
    BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(request.getInputStream()));
    Map<String, Object> txDataMap = new HashMap<String, Object>();
    String txData = bufferedReader.readLine();
    JSONObject txInfo= new JSONObject(txData );
    try {
        String resourceType= txInfo.getString("resourceType");
        String transactionType = txInfo.getString("transactionType");
        Integer transactionCount = (Integer)txInfo.get("transactionCount");
        //Extract all the relevant tx record attributes similarly and pass them in Transaction Record constructor as per the java doc}
        return new TransactionRecord(transactionCount, transactionType, resourceType, ..);
    } catch (JSONException e) {
        //exception handling
    } finally {
        bufferedReader.close();
    }
}
```

## 用戶端代碼範例 {#sample-client-side-code}

您可以使用下列范常式式碼來呼叫具有 `TransactionRecorder`API。

```
$.ajax({
   type: 'POST',
   url: url, //servlet url
   contentType: 'application/json; UTF-8',
   data: JSON.stringify({transactionCount : 1, 
                        transactionType: "SUBMIT",
                        resourceType: "FORM",
                        resourceSubType: "ADAPTIVE-FORM"}),
   success: successHandler,
   error: faultHandler
})
```

## 相關文章 {#related-articles}

* [交易報表概述](/help/forms/using/transaction-reports-overview.md)
* [查看和了解交易報表](/help/forms/using/viewing-and-understanding-transaction-reports.md)
* [交易報表計費API](/help/forms/using/transaction-reports-billable-apis.md)

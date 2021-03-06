---
title: 使用條碼式表單
seo-title: 使用條碼式表單
description: 使用Java API和Web服務API將PDF表單或包含條碼的影像中的資料解碼。
seo-description: 使用Java API和Web服務API將PDF表單或包含條碼的影像中的資料解碼。
uuid: e56c3c94-384d-401f-b418-dd34cdc57eda
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: eb28ac30-265c-4611-8247-1f4bc826f254
role: Developer
exl-id: 9d459939-a311-4770-84db-f2a4b7869072
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1931'
ht-degree: 0%

---

# 使用條碼式表單{#working-with-barcoded-forms}

## 關於條碼式表單服務{#about-the-barcoded-forms-service}

條碼式表單服務可自動從填寫和打印表單中擷取資料，並將擷取的資訊整合到組織的核心IT系統中。

使用條碼式表單服務，您可以將一維和二維條碼新增至互動式PDF forms。 然後，您可以將條碼式表單發佈至網站，或透過電子郵件或光碟分發。 當使用者使用Adobe Reader、Acrobat Professional或Acrobat Standard填入條碼式表單時，條碼會自動更新，以編碼使用者提供的表單資料。 用戶可以以電子方式提交表單，或將表單打印成紙張，然後通過郵件、傳真或手提提交。 您稍後可以在自動化工作流程中擷取使用者提供的資料，並將資料路由至核准流程和業務系統之間。

如需條碼式表單服務的詳細資訊，請參閱[AEM Forms的服務參考](https://www.adobe.com/go/learn_aemforms_services_63)。

## 解碼條碼式表單資料{#decoding-barcoded-form-data}

您可以使用條碼式表單服務API來解碼PDF表單或包含條碼之影像的資料。 解碼表單資料意味著提取位於條形碼中的資料。 在從PDF表單（或影像）解碼資料之前，使用者必須先將資料填入表單中。

>[!NOTE]
>
>如需條碼式表單服務的詳細資訊，請參閱[AEM Forms的服務參考](https://www.adobe.com/go/learn_aemforms_services_63)。

### 步驟{#summary-of-steps}的摘要

要解碼PDF表單中的資料，請執行以下步驟：

1. 包含專案檔案。
1. 建立條碼式formsClient API物件。
1. 取得包含條碼式資料的PDF表單。
1. 將資料從PDF表單解碼。
1. 將資料轉換為XML資料源。
1. 處理已解碼的資料。

**包含項目檔案**

在您的開發專案中加入必要的檔案。 如果您使用Java建立客戶端應用程式，請包括必要的JAR檔案。 如果您使用Web服務，請確定您包含Proxy檔案。

必須將以下JAR檔案添加到項目的類路徑中：

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-barcodedforms-client.jar
* adobe-utilities.jar(若AEM Forms部署在JBoss上則為必要)
* jbossall-client.jar(若AEM Forms部署在JBoss上則為必要)
* xercesImpl.jar(位於&lt;install directory>/Adobe/Adobe_Experience_Manager_forms/sdk/client-libs\thirdparty)

如果AEM Forms部署在非JBOSS的受支援J2EE應用程式伺服器上，則您需要將adobe-utilities.jar和jbossall-client.jar取代為部署AEM Forms的J2EE應用程式伺服器專屬的JAR檔案。 有關所有AEM Forms JAR檔案的位置資訊，請參閱[包含AEM Forms Java庫檔案](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)。

**建立條碼式表單用戶端API物件**

在以程式設計方式執行條碼式表單服務操作之前，您必須建立Barcoded Forms服務用戶端。 如果您使用Java API，請建立`BarcodedFormsServiceClient`物件。 如果您使用條碼式表單網站服務API，請建立`BarcodedFormsServiceService`物件。

**取得包含條碼式資料的PDF表單**

您必須取得包含已填入使用者資料條碼的PDF表單。

**將資料從PDF表單解碼**

取得包含條碼的PDF表單（或影像）後，您就可以將資料解碼。 條碼式Forms服務支援下列條碼類型：

* PDF417條形碼。
* 資料矩陣條形碼。
* QR碼條碼。
* 科達巴條形碼。
* 128碼。
* 代碼39。
* EAN-13條形碼。
* EAN-8條形碼。

在解碼API中以十六進位輸入的字元集表示條碼的內容已編碼為十六進位字串。 例如，如果以格式將UTF-8指定為字元編碼，並在解碼操作中指定了十六進位，則條形碼的內容在解碼輸出的&lt;`xb:content`>元素中被編碼為十六進位字串。 您可以在用戶端應用程式中建立應用程式邏輯，借此轉換此十六進位值以取得原始內容。

**將資料轉換為XML資料源**

將表單資料解碼後，可將其轉換為XDP或XFDF資料。 例如，假設您要將資料匯入其他表單。 若要將資料匯入XFA表單，則必須將資料轉換為XDP資料。 如需詳細資訊，請參閱[匯入表單資料](/help/forms/developing/importing-exporting-data.md#importing-form-data)。

**處理解碼的資料**

您可以處理轉換後的資料，以符合您的業務需求。 例如，將資料解碼並轉換後，可將其保存到檔案、將其儲存在企業資料庫中、填入其他表單等。 本節將討論如何將轉換後的資料另存為XML檔案。

>[!NOTE]
>
>當行分隔符和欄位分隔符參數具有相同值時，條碼式表單服務無法解碼條碼資料

**另請參閱**

[使用Java API將條碼式表單資料解碼](barcoded-forms.md#decode-barcoded-form-data-using-the-java-api)

[使用網站服務API將條碼式表單資料解碼](barcoded-forms.md#decode-barcoded-form-data-using-the-web-service-api)

[包含AEM Forms Java程式庫檔案](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[設定連接屬性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### 使用Java API {#decode-barcoded-form-data-using-the-java-api}將條碼式表單資料解碼

使用條碼式表單API(Java)將表單資料解碼：

1. 包含項目檔案

   在Java項目的類路徑中包含客戶端JAR檔案。

1. 建立條碼式表單用戶端API物件

   使用其建構子並傳遞包含連線屬性的`ServiceClientFactory`物件，以建立`BarcodedFormsServiceClient`物件。

1. 取得包含條碼式資料的PDF表單

   * 建立`java.io.FileInputStream`對象，該對象使用其建構子並傳遞指定PDF文檔位置的字串值，來表示包含條碼資料的PDF表單。
   * 使用其建構子並傳遞`java.io.FileInputStream`物件，以建立`com.adobe.idp.Document`物件。

1. 將資料從PDF表單解碼

   調用`BarcodedFormsServiceClient`對象的`decode`方法並傳遞以下值，將表單資料解碼：

   * 包含PDF表單的`com.adobe.idp.Document`物件。
   * `java.lang.Boolean`物件，指定是否解碼PDF417條碼。
   * `java.lang.Boolean`對象，指定是否解碼資料矩陣條形碼。
   * `java.lang.Boolean`對象，指定是否解碼QR碼條形碼。
   * `java.lang.Boolean`對象，指定是否解碼codabar條形碼。
   * `java.lang.Boolean`對象，指定是否解碼代碼128條形碼。
   * `java.lang.Boolean`對象，指定是否解碼代碼39條形碼。
   * `java.lang.Boolean`對象，指定是否解碼EAN-13條形碼。
   * `java.lang.Boolean`對象，指定是否解碼EAN-8條形碼。
   * `com.adobe.livecycle.barcodedforms.CharSet`枚舉值，它指定條碼中使用的字元集編碼值。

   `decode`方法返回包含已解碼表單資料的`org.w3c.dom.Document`對象。

1. 將資料轉換為XML資料源

   調用`BarcodedFormsServiceClient`對象的`extractToXML`方法並傳遞以下值，將解碼的資料轉換為XDP或XFDF資料：

   * 包含已解碼資料的`org.w3c.dom.Document`物件（請務必使用`decode`方法的傳回值）。
   * 指定行分隔符的`com.adobe.livecycle.barcodedforms.Delimiter`枚舉值。 建議您指定`Delimiter.Carriage_Return`。
   * 指定欄位分隔字元的`com.adobe.livecycle.barcodedforms.Delimiter`枚舉值。 例如，指定`Delimiter.Tab`。
   * `com.adobe.livecycle.barcodedforms.XMLFormat`枚舉值，指定是將條形碼資料轉換為XDP還是XFDF XML資料。 例如，指定`XMLFormat.XDP`將資料轉換為XDP資料。

   >[!NOTE]
   >
   >請勿為行分隔字元和欄位分隔字元參數指定相同的值。

   `extractToXML`方法返回`java.util.List`對象，其中每個元素都是`org.w3c.dom.Document`對象。 表單上的每個條碼都有獨立的元素。 也就是說，如果表單上有四個條形碼，則返回的`java.util.List`對象中有四個元素。

1. 處理解碼的資料

   * 逐一查看`java.util.List`物件，以取得清單中的每個`org.w3c.dom.Document`物件。
   * 對於清單中的每個元素，將`org.w3c.dom.Document`對象轉換為`com.adobe.idp.Document`對象。 （將`org.w3c.dom.Document`物件轉換為`com.adobe.idp.Document`物件的應用程式邏輯，如使用Java API範例解碼條碼式表單資料中所示。）
   * 調用`com.adobe.idp.Document`對象的`copyToFile`，並傳遞表示XML檔案的檔案對象，將XML資料另存為XML檔案。

**另請參閱**

[快速入門（SOAP模式）:使用Java API解碼條碼式表單資料](/help/forms/developing/barcoded-forms-service-java-api.md#quick-start-soap-mode-decoding-barcoded-form-data-using-the-java-api)

[包含AEM Forms Java程式庫檔案](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[設定連接屬性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### 使用Web服務API {#decode-barcoded-form-data-using-the-web-service-api}對條碼式表單資料進行解碼

使用條碼式表單API（網站服務）將表單資料解碼：

1. 包含項目檔案

   * 建立一個Microsoft .NET客戶端程式集，該程式集將使用條碼式表單服務WSDL。 如需詳細資訊，請參閱[使用Base64編碼叫用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)。
   * 參考Microsoft .NET客戶端程式集。 如需詳細資訊，請參閱[使用Base64編碼](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)叫用AEM Forms中的「參考.NET用戶端程式集」。

1. 建立條碼式表單用戶端API物件

   使用佔用條碼式表單服務WSDL的Microsoft .NET客戶端程式集，通過調用其預設建構子來建立`BarcodedFormsServiceService`對象。

1. 取得包含條碼式資料的PDF表單

   * 使用其建構子建立`BLOB`物件。 `BLOB`對象用於儲存包含條形碼的PDF文檔。
   * 通過調用其建構子並傳遞一個字串值來建立`System.IO.FileStream`對象，該字串值表示PDF文檔的檔案位置以及開啟檔案的模式。
   * 建立儲存`System.IO.FileStream`對象內容的位元組陣列。 通過獲取`System.IO.FileStream`對象的`Length`屬性，可以確定位元組陣列的大小。
   * 調用`System.IO.FileStream`對象的`Read`方法並傳遞要讀取的位元組陣列、啟動位置和流長度，以流資料填充位元組陣列。
   * 為`binaryData`物件指派包含位元組陣列內容的屬性，以填入`BLOB`物件。

1. 將資料從PDF表單解碼

   調用`BarcodedFormsServiceService`對象的`decode`方法並傳遞以下值，將表單資料解碼：

   * 包含PDF表單的`BLOB`物件。
   * `Boolean`物件，指定是否解碼PDF417條碼。
   * `Boolean`對象，指定是否解碼資料矩陣條形碼。
   * `Boolean`對象，指定是否解碼QR碼條形碼。
   * `Boolean`對象，指定是否解碼codabar條形碼。
   * `Boolean`對象，指定是否解碼代碼128條形碼。
   * `Bolean`對象，指定是否解碼代碼39條形碼。
   * `Boolean`對象，指定是否解碼EAN-13條形碼。
   * `Boolean`對象，指定是否解碼EAN-8條形碼。
   * `CharSet`枚舉值，它指定條碼中使用的字元集編碼值。

   `decode`方法返回包含已解碼表單資料的字串值。

1. 將資料轉換為XML資料源

   調用`BarcodedFormsServiceService`對象的`extractToXML`方法並傳遞以下值，將解碼的資料轉換為XDP或XFDF資料：

   * 包含已解碼資料的字串值（請務必使用`decode`方法的傳回值）。
   * 指定行分隔符的`Delimiter`枚舉值。 建議您指定`Delimiter.Carriage_Return`。
   * 指定欄位分隔字元的`Delimiter`枚舉值。 例如，指定`Delimiter.Tab`。
   * `XMLFormat`枚舉值，指定是將條形碼資料轉換為XDP還是XFDF XML資料。 例如，指定`XMLFormat.XDP`將資料轉換為XDP資料。

   >[!NOTE]
   >
   >請勿為行分隔字元和欄位分隔字元參數指定相同的值。

   `extractToXML`方法會傳回`Object`陣列，其中每個元素都是`BLOB`例項。 表單上的每個條碼都有獨立的元素。 也就是說，如果表單上有四個條形碼，則返回的`Object`陣列中有四個元素。

1. 處理解碼的資料

   * 調用`System.IO.FileStream`對象的建構子並傳遞一個字串值，該字串值表示安全PDF文檔的檔案位置。
   * 建立位元組陣列，用於儲存`encryptPDFUsingPassword`方法返回的`BLOB`對象的資料內容。 獲取`BLOB`對象的`binaryData`資料成員的值，以填充位元組陣列。
   * 通過調用其建構子並傳遞`System.IO.FileStream`對象來建立`System.IO.BinaryWriter`對象。
   * 調用`System.IO.BinaryWriter`對象的`Write`方法並傳遞位元組陣列，將位元組陣列的內容寫入PDF檔案。

**另請參閱**

[使用Base64編碼叫用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

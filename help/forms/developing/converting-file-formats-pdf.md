---
title: 在檔案格式和PDF之間轉換
seo-title: Converting Between File Formatsand PDF
description: 使用「生成PDF」服務將原生檔案格式轉換為PDF。 產生PDF服務也可將PDF轉換為其他檔案格式，並最佳化PDF檔案的大小。
seo-description: Use the Generate PDF service to convert native file formats to PDF. Generate PDF service also converts PDF to other file formats and optimizes the size of PDF documents.
uuid: f72ad603-c996-4d48-9bfc-bed7bf776af6
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 180cac3f-6378-42bc-9a47-60f9f08a7103
role: Developer
exl-id: 79091a75-2669-453f-9560-e58bfffa3487
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '7872'
ht-degree: 0%

---

# 在檔案格式和PDF之間轉換 {#converting-between-file-formatsand-pdf}

**關於產生PDF服務**

「生成PDF」服務將原生檔案格式轉換為PDF。 它還能將PDF轉換為其他檔案格式，並最佳化PDF檔案的大小。

「產生PDF」服務使用原生應用程式將下列檔案格式轉換為PDF。 除非另有說明，否則僅支援這些應用程式的德文、法文、英文和日文版本。 *Windows僅* 表示僅支援Windows Server® 2003和Windows Server 2008。

* 轉換DOC、DOCX、RTF、TXT、XLS、XLSX、PPT、PPTX、VSD、MPP、MPP、MPPX、XPS和PUB的Microsoft Office 2003和2007（僅限Windows）

   >[!NOTE]
   >
   >Acrobat® 9.2或更新版本才能將Microsoft XPS格式轉換為PDF。

* Autodesk AutoCAD 2005、2006、2007、2008和2009，以轉換DWF、DWG和DXW（僅英語）
* Corel WordPerfect 12和X4轉換WPD、QPW、SHW（僅英語）
* OpenOffice 2.0、2.4、3.0.1和3.1，以轉換ODT、ODS、ODP、ODF、SXW、SXI、SXC、SXD、DOC、DOCX、RTF、TXT、XLS、XLSX、PPT、PTX、VSD、MP、MPX和PUB

   >[!NOTE]
   >
   >「產生PDF」服務不支援64位元版本的OpenOffice。

* Adobe Photoshop® CS2轉換PSD（僅限Windows）

   >[!NOTE]
   >
   >Photoshop CS3和CS4不受支援，因為它們不支援Windows Server 2003或Windows Server 2008。

* Adobe FrameMaker® 7.2和8以轉換FM（僅限Windows）
* AdobePageMaker® 7.0以轉換PMD、PM6、P65和PM（僅限Windows）
* 協力廠商應用程式支援的原生格式（需要開發應用程式專用的設定檔案）（僅限Windows）

「生成PDF」服務將以下基於標準的檔案格式轉換為PDF。

* 視頻格式：SWF、FLV（僅Windows）
* 影像格式：JPEG、JPG、JP2、J2Kí、JPC、J2C、GIF、BMP、TIFF、TIF、PNG、JPF
* HTML(Windows、Sun™ Solaris™和Linux®)

「生成PDF」服務將PDF轉換為以下檔案格式（僅限Windows）:

* 封裝的PostScript(EPS)
* HTML3.2
* HTML 4.01搭配CSS 1.0
* DOC（Microsoft Word格式）
* RTF
* 文本（可訪問和純文字檔案）
* XML
* 僅使用DeviceRGB色域的PDF/A-1a
* 僅使用DeviceRGB色域的PDF/A-1b

「產生PDF」服務需要您執行下列管理工作：

* 在托管AEM Forms的電腦上安裝所需的原生應用程式
* 在托管AEM Forms的電腦上安裝Adobe Acrobat Professional或Acrobat Pro Extended 9.2
* 執行安裝後安裝任務

使用JBoss Tunklying安裝和部署AEM表單中介紹了這些任務。

您可以使用「產生PDF」服務來完成下列工作：

* 從原生檔案格式轉換為PDF。
* 將HTML文檔轉換為PDF文檔。
* 將PDF文檔轉換為檔案格式。

>[!NOTE]
>
>如需產生PDF服務的詳細資訊，請參閱[AEM Forms的服務參考](https://www.adobe.com/go/learn_aemforms_services_63)。

## 將Word文檔轉換為PDF文檔 {#converting-word-documents-to-pdf-documents}

本節說明如何使用「產生PDF API」，以程式設計方式將Microsoft Word檔案轉換為PDF檔案。

>[!NOTE]
>
>有關其他檔案格式的詳細資訊，請參閱[添加對其他本機檔案格式的支援](converting-file-formats-pdf.md#adding-support-for-additional-native-file-formats)。

>[!NOTE]
>
>如需產生PDF服務的詳細資訊，請參閱[AEM Forms的服務參考](https://www.adobe.com/go/learn_aemforms_services_63)。

### 步驟摘要 {#summary-of-steps}

要將Microsoft Word文檔轉換為PDF文檔，請執行以下任務：

1. 包含專案檔案。
1. 建立產生PDF用戶端。
1. 檢索要轉換為PDF文檔的檔案。
1. 將檔案轉換為PDF文檔。
1. 檢索結果。

**包含項目檔案**

在您的開發專案中加入必要的檔案。 如果要使用Java建立客戶端應用程式，請包括必要的JAR檔案。 如果您使用Web服務，請確定您包含Proxy檔案。

**建立產生PDF用戶端**

在以程式設計方式執行「生成PDF」操作之前，請建立「生成PDF」服務客戶端。 如果您使用Java API，請建立`GeneratePdfServiceClient`物件。 如果您使用Web服務API，請建立`GeneratePDFServiceService`物件。

**檢索要轉換為PDF文檔的檔案**

檢索要轉換為PDF文檔的Microsoft Word文檔。

**將檔案轉換為PDF檔案**

建立「生成PDF」服務客戶端後，可以調用`createPDF2`方法。 此方法需要有關要轉換的文檔的資訊，包括副檔名。

**擷取結果**

將檔案轉換為PDF文檔後，可以檢索結果。 例如，將Word檔案轉換為PDF文檔後，可以檢索和保存PDF文檔。

**另請參閱**

[使用Java API將Word文檔轉換為PDF文檔](converting-file-formats-pdf.md#convert-word-documents-to-pdf-documents-using-the-java-api)

[使用Web服務API將Word文檔轉換為PDF文檔](converting-file-formats-pdf.md#convert-word-documents-to-pdf-documents-using-the-web-service-api)

[包含AEM Forms Java程式庫檔案](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[設定連接屬性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[產生PDF服務API快速入門](/help/forms/developing/generate-pdf-service-java-api.md#generate-pdf-service-java-api-quick-start-soap)

### 使用Java API將Word文檔轉換為PDF文檔 {#convert-word-documents-to-pdf-documents-using-the-java-api}

使用「生成PDF API(Java)」將Microsoft Word文檔轉換為PDF文檔：

1. 包含專案檔案。

   在Java專案的類別路徑中包含用戶端JAR檔案，例如adobe-generatepdf-client.jar。

1. 建立產生PDF用戶端。

   * 建立包含連接屬性的`ServiceClientFactory`對象。
   * 使用其建構子並傳遞`ServiceClientFactory`物件，以建立`GeneratePdfServiceClient`物件。

1. 檢索要轉換為PDF文檔的檔案。

   * 建立`java.io.FileInputStream`對象，該對象表示要使用其建構子轉換的Word檔案。 傳遞指定檔案位置的字串值。
   * 使用其建構子並傳遞`java.io.FileInputStream`物件，以建立`com.adobe.idp.Document`物件。

1. 將檔案轉換為PDF文檔。

   調用`GeneratePdfServiceClient`對象的`createPDF2`方法並傳遞以下值，將檔案轉換為PDF文檔：

   * 代表要轉換的檔案的`com.adobe.idp.Document`物件。
   * 包含副檔名的`java.lang.String`物件。
   * `java.lang.String`物件，包含要用於轉換的檔案類型設定。 檔案類型設定為不同的檔案類型(如.doc或.xls)提供轉換設定。
   * `java.lang.String`物件，包含要使用的PDF設定名稱。 例如，您可以指定`Standard`。
   * `java.lang.String`物件，包含要使用的安全設定名稱。
   * 選用的`com.adobe.idp.Document`物件，包含產生PDF檔案時要套用的設定。
   * 可選`com.adobe.idp.Document`對象，包含要應用於PDF文檔的元資料資訊。

   `createPDF2`方法返回包含新PDF文檔和日誌資訊的`CreatePDFResult`對象。 記錄檔通常包含轉換請求產生的錯誤或警告訊息。

1. 檢索結果。

   要獲取PDF文檔，請執行以下操作：

   * 調用`CreatePDFResult`對象的`getCreatedDocument`方法，該方法返回`com.adobe.idp.Document`對象。
   * 調用`com.adobe.idp.Document`對象的`copyToFile`方法，從上一步建立的對象中提取PDF文檔。

   如果您使用`createPDF2`方法來取得記錄檔（不適用於HTML轉換），請執行下列動作：

   * 調用`CreatePDFResult`對象的`getLogDocument`方法。 這會傳回`com.adobe.idp.Document`物件。
   * 調用`com.adobe.idp.Document`對象的`copyToFile`方法以提取日誌文檔。


**另請參閱**

[步驟摘要](converting-file-formats-pdf.md#summary-of-steps)

[快速入門（SOAP模式）:使用Java API將Microsoft Word文檔轉換為PDF文檔](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-a-microsoft-word-document-to-a-pdf-document-using-the-java-api)

[包含AEM Forms Java程式庫檔案](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[設定連接屬性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### 使用Web服務API將Word文檔轉換為PDF文檔 {#convert-word-documents-to-pdf-documents-using-the-web-service-api}

使用「生成PDF API（Web服務）」將Microsoft Word文檔轉換為PDF文檔：

1. 包含專案檔案。

   建立使用MTOM的Microsoft .NET項目。 確保使用以下WSDL定義：`http://localhost:8080/soap/services/GeneratePDFService?WSDL&lc_version=9.0.1`。

   >[!NOTE]
   >
   >將`localhost`取代為托管AEM Forms之伺服器的IP位址。

1. 建立產生PDF用戶端。

   * 使用其預設建構子建立`GeneratePDFServiceClient`物件。
   * 使用`System.ServiceModel.EndpointAddress`建構子建立`GeneratePDFServiceClient.Endpoint.Address`物件。 將指定WSDL的字串值傳遞到AEM Forms服務（例如`http://localhost:8080/soap/services/GeneratePDFService?blob=mtom`）。 您不需要使用`lc_version`屬性。 但請指定`?blob=mtom`。
   * 獲取`GeneratePDFServiceClient.Endpoint.Binding`欄位的值，建立`System.ServiceModel.BasicHttpBinding`對象。 將傳回值轉換為`BasicHttpBinding`。
   * 將`System.ServiceModel.BasicHttpBinding`物件的`MessageEncoding`欄位設為`WSMessageEncoding.Mtom`。 此值可確保使用MTOM。
   * 通過執行以下任務來啟用基本HTTP身份驗證：

      * 將AEM表單使用者名稱指派給欄位`GeneratePDFServiceClient.ClientCredentials.UserName.UserName`。
      * 將相應的密碼值分配給欄位`GeneratePDFServiceClient.ClientCredentials.UserName.Password`。
      * 將常數值`HttpClientCredentialType.Basic`指派給欄位`BasicHttpBindingSecurity.Transport.ClientCredentialType`。
      * 將常數值`BasicHttpSecurityMode.TransportCredentialOnly`指派給欄位`BasicHttpBindingSecurity.Security.Mode`。

1. 檢索要轉換為PDF文檔的檔案。

   * 使用其建構子建立`BLOB`物件。 `BLOB`對象用於儲存要轉換為PDF文檔的檔案。
   * 調用`System.IO.FileStream`對象的建構子以建立對象。 傳遞一個字串值，該字串值表示要轉換的檔案的檔案位置以及開啟檔案的模式。
   * 建立儲存`System.IO.FileStream`對象內容的位元組陣列。 通過獲取`System.IO.FileStream`對象的`Length`屬性，可以確定位元組陣列的大小。
   * 調用`System.IO.FileStream`對象的`Read`方法並傳遞要讀取的位元組陣列、啟動位置和流長度，以流資料填充位元組陣列。
   * 將位元組陣列的內容指派給其`MTOM`屬性，以填入`BLOB`物件。

1. 將檔案轉換為PDF文檔。

   調用`GeneratePDFServiceService`對象的`CreatePDF2`方法並傳遞以下值，將檔案轉換為PDF文檔：

   * 代表要轉換的檔案的`BLOB`物件。
   * 包含副檔名的字串。
   * `java.lang.String`物件，包含要用於轉換的檔案類型設定。 檔案類型設定為不同的檔案類型(如.doc或.xls)提供轉換設定。
   * 包含要使用的PDF設定的字串物件。 您可以指定`Standard`。
   * 包含要使用的安全設定的字串對象。 您可以指定`No Security`。
   * 選用的`BLOB`物件，包含產生PDF檔案時要套用的設定。
   * 可選`BLOB`對象，包含要應用於PDF文檔的元資料資訊。
   * 由`CreatePDF2`方法填入的`BLOB`類型的輸出參數。 `CreatePDF2`方法會以轉換的檔案填入此物件。 （此參數值僅對於Web服務調用是必需的）。
   * 由`CreatePDF2`方法填入的`BLOB`類型的輸出參數。 `CreatePDF2`方法會以記錄檔填入此物件。 （此參數值僅對於Web服務調用是必需的）。

1. 檢索結果。

   * 通過將`BLOB`對象的`MTOM`欄位指派給位元組陣列來檢索已轉換的PDF文檔。 位元組陣清單示轉換的PDF文檔。 請確定您使用`BLOB`物件作為`createPDF2`方法的輸出參數。
   * 調用`System.IO.FileStream`對象的建構子並傳遞一個字串值，該字串值表示已轉換PDF文檔的檔案位置。
   * 通過調用其建構子並傳遞`System.IO.FileStream`對象來建立`System.IO.BinaryWriter`對象。
   * 調用`System.IO.BinaryWriter`對象的`Write`方法並傳遞位元組陣列，將位元組陣列的內容寫入PDF檔案。

**另請參閱**

[步驟摘要](converting-file-formats-pdf.md#summary-of-steps)

[使用MTOM叫用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[使用SwaRef叫用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## 將HTML文檔轉換為PDF文檔 {#converting-html-documents-to-pdf-documents}

本節說明如何使用「產生PDF API」，以程式設計方式將HTML檔案轉換為PDF檔案。

>[!NOTE]
>
>如需產生PDF服務的詳細資訊，請參閱[AEM Forms的服務參考](https://www.adobe.com/go/learn_aemforms_services_63)。

### 步驟摘要 {#summary_of_steps-1}

要將HTML文檔轉換為PDF文檔，請執行以下任務：

1. 包含專案檔案。
1. 建立產生PDF用戶端。
1. 檢索要轉換為PDF文檔的HTML內容。
1. 將HTML內容轉換為PDF檔案。
1. 檢索結果。

**包含項目檔案**

在您的開發專案中加入必要的檔案。 如果要使用Java建立客戶端應用程式，請包括必要的JAR檔案。 如果您使用Web服務，請確定您包含Proxy檔案。

**建立產生PDF用戶端**

必須先建立「生成PDF」服務客戶端，才能以寫程式方式執行「生成PDF」操作。 如果您使用Java API，請建立`GeneratePdfServiceClient`物件。 如果您使用Web服務API，請建立`GeneratePDFServiceService`。

**檢索要轉換為PDF文檔的HTML內容**

參考要轉換為PDF文檔的HTML內容。 您可以參考HTML內容，例如HTML檔案或可使用URL存取的HTML內容。

**將HTML內容轉換為PDF檔案**

建立服務客戶端後，可以調用相應的PDF建立操作。 此操作需要有關要轉換的文檔的資訊，包括目標文檔的路徑。

**擷取結果**

將HTML內容轉換為PDF文檔後，您可以檢索結果並保存PDF文檔。

**另請參閱**

[使用Java API將HTML內容轉換為PDF檔案](converting-file-formats-pdf.md#convert-html-content-to-a-pdf-document-using-the-java-api)

[使用Web服務API將HTML內容轉換為PDF檔案](converting-file-formats-pdf.md#convert-html-content-to-a-pdf-document-using-the-web-service-api)

[包含AEM Forms Java程式庫檔案](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[設定連接屬性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[產生PDF服務API快速入門](/help/forms/developing/generate-pdf-service-java-api.md#generate-pdf-service-java-api-quick-start-soap)

### 使用Java API將HTML內容轉換為PDF檔案 {#convert-html-content-to-a-pdf-document-using-the-java-api}

使用「生成PDF API(Java)」將HTML文檔轉換為PDF文檔：

1. 包含專案檔案。

   在Java專案的類別路徑中包含用戶端JAR檔案，例如adobe-generatepdf-client.jar。

1. 建立產生PDF用戶端。

   使用其建構子並傳遞包含連線屬性的`ServiceClientFactory`物件，以建立`GeneratePdfServiceClient`物件。

1. 檢索要轉換為PDF文檔的HTML內容。

   建立字串變數並指派指向HTML內容的URL，以擷取HTML內容。

1. 將HTML內容轉換為PDF檔案。

   調用`GeneratePdfServiceClient`對象的`htmlToPDF2`方法並傳遞以下值：

   * `java.lang.String`物件，包含要轉換的HTML檔案的URL。
   * `java.lang.String`物件，包含要用於轉換的檔案類型設定。 檔案類型設定可以包含尖峰層級。
   * `java.lang.String`物件，包含要使用的安全設定名稱。
   * 選用的`com.adobe.idp.Document`物件，包含產生PDF檔案時要套用的設定。 如果未提供此資訊，則會根據前三個參數自動選擇設定。
   * 可選`com.adobe.idp.Document`對象，包含要應用於PDF文檔的元資料資訊。

1. 檢索結果。

   `htmlToPDF2`方法返回一個`HtmlToPdfResult`對象，該對象包含生成的新PDF文檔。 要獲取新建立的PDF文檔，請執行以下操作：

   * 調用`HtmlToPdfResult`對象的`getCreatedDocument`方法。 這會傳回`com.adobe.idp.Document`物件。
   * 調用`com.adobe.idp.Document`對象的`copyToFile`方法，從上一步建立的對象中提取PDF文檔。

**另請參閱**

[將HTML文檔轉換為PDF文檔](converting-file-formats-pdf.md#converting-html-documents-to-pdf-documents)

[快速入門（SOAP模式）:使用Java API將HTML內容轉換為PDF檔案](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-html-content-to-a-pdf-document-using-the-java-api)

[快速入門（SOAP模式）:使用Java API將HTML內容轉換為PDF檔案](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-html-content-to-a-pdf-document-using-the-java-api)

[包含AEM Forms Java程式庫檔案](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[設定連接屬性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### 使用Web服務API將HTML內容轉換為PDF檔案 {#convert-html-content-to-a-pdf-document-using-the-web-service-api}

使用「生成PDF API（Web服務）」將HTML內容轉換為PDF文檔：

1. 包含專案檔案。

   建立使用MTOM的Microsoft .NET項目。 確保使用以下WSDL定義：`http://localhost:8080/soap/services/GeneratePDFService?WSDL&lc_version=9.0.1`。

   >[!NOTE]
   >
   >將`localhost`取代為托管AEM Forms之伺服器的IP位址。

1. 建立產生PDF用戶端。

   * 使用其預設建構子建立`GeneratePDFServiceClient`物件。
   * 使用`System.ServiceModel.EndpointAddress`建構子建立`GeneratePDFServiceClient.Endpoint.Address`物件。 將指定WSDL的字串值傳遞到AEM Forms服務（例如`http://localhost:8080/soap/services/GeneratePDFService?blob=mtom`）。 您不需要使用`lc_version`屬性。 但請指定`?blob=mtom`。
   * 獲取`GeneratePDFServiceClient.Endpoint.Binding`欄位的值，建立`System.ServiceModel.BasicHttpBinding`對象。 將傳回值轉換為`BasicHttpBinding`。
   * 將`System.ServiceModel.BasicHttpBinding`物件的`MessageEncoding`欄位設為`WSMessageEncoding.Mtom`。 此值可確保使用MTOM。
   * 通過執行以下任務來啟用基本HTTP身份驗證：

      * 將AEM表單使用者名稱指派給欄位`GeneratePDFServiceClient.ClientCredentials.UserName.UserName`。
      * 將相應的密碼值分配給欄位`GeneratePDFServiceClient.ClientCredentials.UserName.Password`。
      * 將常數值`HttpClientCredentialType.Basic`指派給欄位`BasicHttpBindingSecurity.Transport.ClientCredentialType`。
      * 將常數值`BasicHttpSecurityMode.TransportCredentialOnly`指派給欄位`BasicHttpBindingSecurity.Security.Mode`。

1. 檢索要轉換為PDF文檔的HTML內容。

   建立字串變數並指派指向HTML內容的URL，以擷取HTML內容。

1. 將HTML內容轉換為PDF檔案。

   叫用`GeneratePDFServiceService`物件的`HtmlToPDF2`方法，將HTML內容轉換為PDF檔案，並傳遞下列值：

   * 包含要轉換之HTML內容的字串。
   * `java.lang.String`物件，包含要用於轉換的檔案類型設定。
   * 包含要使用的安全設定的字串對象。
   * 選用的`BLOB`物件，包含產生PDF檔案時要套用的設定。
   * 可選`BLOB`對象，包含要應用於PDF文檔的元資料資訊。
   * 由`CreatePDF2`方法填入的`BLOB`類型的輸出參數。 `CreatePDF2`方法會以轉換的檔案填入此物件。 （此參數值僅對於Web服務調用是必需的）。

1. 檢索結果。

   * 通過將`BLOB`對象的`MTOM`欄位指派給位元組陣列來檢索已轉換的PDF文檔。 位元組陣清單示轉換的PDF文檔。 請確定您使用`BLOB`物件作為`HtmlToPDF2`方法的輸出參數。
   * 調用`System.IO.FileStream`對象的建構子並傳遞一個字串值，該字串值表示已轉換PDF文檔的檔案位置。
   * 通過調用其建構子並傳遞`System.IO.FileStream`對象來建立`System.IO.BinaryWriter`對象。
   * 調用`System.IO.BinaryWriter`對象的`Write`方法並傳遞位元組陣列，將位元組陣列的內容寫入PDF檔案。

**另請參閱**

[將HTML文檔轉換為PDF文檔](converting-file-formats-pdf.md#converting-html-documents-to-pdf-documents)

[使用MTOM叫用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[使用SwaRef叫用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## 將PDF檔案轉換為非影像格式 {#converting-pdf-documents-to-non-image-formats}

本節介紹如何使用生成PDF Java API和Web服務API，以寫程式方式將PDF文檔轉換為RTF檔案，這是非影像格式的示例。 其他非影像格式包括HTML、文字、DOC和EPS。 將PDF文檔轉換為RTF時，請確保PDF文檔不包含表單元素，如提交按鈕。 表單元素不會轉換。

>[!NOTE]
>
>如需產生PDF服務的詳細資訊，請參閱[AEM Forms的服務參考](https://www.adobe.com/go/learn_aemforms_services_63)。

### 步驟摘要 {#summary_of_steps-2}

要將PDF文檔轉換為任何支援的類型，請執行以下步驟：

1. 包含專案檔案。
1. 建立產生PDF用戶端。
1. 檢索要轉換的PDF文檔。
1. 轉換PDF文檔。
1. 儲存轉換的檔案。

**包含項目檔案**

在您的開發專案中加入必要的檔案。 如果要使用Java建立客戶端應用程式，請包括必要的JAR檔案。 如果您使用Web服務，請確定您包含Proxy檔案。

**建立產生PDF用戶端**

必須先建立「生成PDF」服務客戶端，才能以寫程式方式執行「生成PDF」操作。 如果您使用Java API，請建立`GeneratePdfServiceClient`物件。 如果您使用Web服務API，請建立`GeneratePDFServiceService`物件。

**檢索要轉換的PDF文檔**

檢索要轉換為非影像格式的PDF文檔。

**轉換PDF檔案**

建立服務客戶端後，可以調用PDF導出操作。 此操作需要有關要轉換的文檔的資訊，包括目標文檔的路徑。

**儲存轉換的檔案**

儲存轉換的檔案。 例如，如果將PDF文檔轉換為RTF檔案，請將轉換的文檔保存為RTF檔案。

**另請參閱**

[使用Java API將PDF文檔轉換為RTF檔案](converting-file-formats-pdf.md#convert-a-pdf-document-to-a-rtf-file-using-the-java-api)

[使用Web服務API將PDF文檔轉換為RTF檔案](converting-file-formats-pdf.md#convert-a-pdf-document-to-a-rtf-file-using-the-web-service-api)

[包含AEM Forms Java程式庫檔案](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[設定連接屬性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[產生PDF服務API快速入門](/help/forms/developing/generate-pdf-service-java-api.md#generate-pdf-service-java-api-quick-start-soap)

### 使用Java API將PDF文檔轉換為RTF檔案 {#convert-a-pdf-document-to-a-rtf-file-using-the-java-api}

使用生成PDF API(Java)將PDF文檔轉換為RTF檔案：

1. 包含專案檔案。

   在Java專案的類別路徑中包含用戶端JAR檔案，例如adobe-generatepdf-client.jar。

1. 建立產生PDF用戶端。

   使用其建構子並傳遞包含連線屬性的`ServiceClientFactory`物件，以建立`GeneratePdfServiceClient`物件。

1. 檢索要轉換的PDF文檔。

   * 建立`java.io.FileInputStream`對象，該對象使用其建構子表示要轉換的PDF文檔。 傳遞指定PDF文檔位置的字串值。
   * 使用其建構子並傳遞`java.io.FileInputStream`物件，以建立`com.adobe.idp.Document`物件。

1. 轉換PDF文檔。

   調用`GeneratePdfServiceClient`對象的`exportPDF2`方法並傳遞以下值：

   * 代表要轉換的PDF檔案的`com.adobe.idp.Document`物件。
   * `java.lang.String`物件，包含要轉換的檔案名稱。
   * `java.lang.String`物件，包含Adobe PDF設定的名稱。
   * `ConvertPDFFormatType`物件，用於指定轉換的目標檔案類型。
   * 選用的`com.adobe.idp.Document`物件，包含產生PDF檔案時要套用的設定。

   `exportPDF2`方法返回包含轉換檔案的`ExportPDFResult`對象。

1. 轉換PDF文檔。

   要獲取新建立的檔案，請執行以下步驟：

   * 調用`ExportPDFResult`對象的`getConvertedDocument`方法。 這會傳回`com.adobe.idp.Document`物件。
   * 調用`com.adobe.idp.Document`對象的`copyToFile`方法以提取新文檔。

**另請參閱**

[步驟摘要](converting-file-formats-pdf.md#summary-of-steps)

[快速入門（SOAP模式）:使用Java API將HTML內容轉換為PDF檔案](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-html-content-to-a-pdf-document-using-the-java-api)

[包含AEM Forms Java程式庫檔案](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[設定連接屬性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### 使用Web服務API將PDF文檔轉換為RTF檔案 {#convert-a-pdf-document-to-a-rtf-file-using-the-web-service-api}

使用生成PDF API（Web服務）將PDF文檔轉換為RTF檔案：

1. 包含專案檔案。

   建立使用MTOM的Microsoft .NET項目。 確保使用以下WSDL定義：`http://localhost:8080/soap/services/GeneratePDFService?WSDL&lc_version=9.0.1`。

   >[!NOTE]
   >
   >將`localhost`取代為托管AEM Forms之伺服器的IP位址。

1. 建立生成PDf客戶端。

   * 使用其預設建構子建立`GeneratePDFServiceClient`物件。
   * 使用`System.ServiceModel.EndpointAddress`建構子建立`GeneratePDFServiceClient.Endpoint.Address`物件。 將指定WSDL的字串值傳遞到AEM Forms服務（例如`http://localhost:8080/soap/services/GeneratePDFService?blob=mtom`）。 您不需要使用`lc_version`屬性。 但請指定`?blob=mtom`。
   * 獲取`GeneratePDFServiceClient.Endpoint.Binding`欄位的值，建立`System.ServiceModel.BasicHttpBinding`對象。 將傳回值轉換為`BasicHttpBinding`。
   * 將`System.ServiceModel.BasicHttpBinding`物件的`MessageEncoding`欄位設為`WSMessageEncoding.Mtom`。 此值可確保使用MTOM。
   * 通過執行以下任務來啟用基本HTTP身份驗證：

      * 將AEM表單使用者名稱指派給欄位`GeneratePDFServiceClient.ClientCredentials.UserName.UserName`。
      * 將相應的密碼值分配給欄位`GeneratePDFServiceClient.ClientCredentials.UserName.Password`。
      * 將常數值`HttpClientCredentialType.Basic`指派給欄位`BasicHttpBindingSecurity.Transport.ClientCredentialType`。
      * 將常數值`BasicHttpSecurityMode.TransportCredentialOnly`指派給欄位`BasicHttpBindingSecurity.Security.Mode`。

1. 檢索要轉換的PDF文檔。

   * 使用其建構子建立`BLOB`物件。 `BLOB`對象用於儲存轉換的PDF文檔。
   * 通過調用其建構子並傳遞一個字串值來建立`System.IO.FileStream`對象，該字串值表示PDF文檔的檔案位置以及開啟檔案的模式。
   * 建立儲存`System.IO.FileStream`對象內容的位元組陣列。 通過獲取`System.IO.FileStream`對象的`Length`屬性，可以確定位元組陣列的大小。
   * 調用`System.IO.FileStream`對象的`Read`方法並傳遞要讀取的位元組陣列、啟動位置和流長度，以流資料填充位元組陣列。
   * 將位元組陣列的內容指派給其`MTOM`屬性，以填入`BLOB`物件。

1. 轉換PDF文檔。

   調用`GeneratePDFServiceServiceWse`對象的`ExportPDF2`方法並傳遞以下值：

   * 代表要轉換的PDF檔案的`BLOB`物件。
   * 包含要轉換的檔案路徑名的字串。
   * 指定檔案位置的`java.lang.String`對象。
   * 指定轉換目標檔案類型的字串對象。 指定`RTF`。
   * 選用的`BLOB`物件，包含產生PDF檔案時要套用的設定。
   * 由`ExportPDF2`方法填入的`BLOB`類型的輸出參數。 `ExportPDF2`方法會以轉換的檔案填入此物件。 （此參數值僅對於Web服務調用是必需的）。

1. 儲存轉換的檔案。

   * 通過將`BLOB`對象的`MTOM`欄位分配給位元組陣列來檢索已轉換的RTF文檔。 位元組陣清單示轉換的RTF文檔。 請確定您使用`BLOB`物件作為`ExportPDF2`方法的輸出參數。
   * 調用`System.IO.FileStream`對象的建構子以建立對象。 傳遞表示RTF檔案位置的字串值。
   * 通過調用其建構子並傳遞`System.IO.FileStream`對象來建立`System.IO.BinaryWriter`對象。
   * 調用`System.IO.BinaryWriter`對象的`Write`方法並傳遞位元組陣列，將位元組陣列的內容寫入RTF檔案。

**另請參閱**

[步驟摘要](converting-file-formats-pdf.md#summary-of-steps)

[使用MTOM叫用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[使用SwaRef叫用AEM Forms](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## 新增對其他原生檔案格式的支援 {#adding-support-for-additional-native-file-formats}

本節說明如何新增對其他原生檔案格式的支援。 它概述了「產生PDF」服務與本服務用於將原生檔案格式轉換為PDF的原生應用程式之間的互動。

本節也說明下列內容：

* 如何修改「生成PDF」服務對本機應用程式的響應，該產品已用於將本機檔案格式轉換為PDF
* 「生成PDF」服務、「生成PDF服務應用程式監視器(AppMon)」元件和本機應用程式（如Microsoft Word）之間的交互
* XML語法在這些交互中所扮演的角色

### 元件互動 {#component-interactions}

「生成PDF」服務通過調用與檔案格式關聯的應用程式，然後與應用程式交互以使用預設打印機打印文檔來轉換本機檔案格式。 預設打印機必須設定為Adobe PDF打印機。

此圖顯示了與本機應用程式支援相關的元件和驅動程式。 它還提到影響交互的XML文法。

原生檔案轉換的元件互動

本文檔使用&#x200B;*本機應用程式*&#x200B;一詞來指示用於生成本機檔案格式（如Microsoft Word）的應用程式。

** AppMonis是企業元件，與原生應用程式互動的方式與使用者瀏覽該應用程式所顯示對話方塊的方式相同。AppMon用於指示應用程式（如Microsoft Word）開啟和打印涉及以下順序任務的檔案的XML語法：

1. 選取「檔案」>「開啟」以開啟檔案
1. 確保顯示「開啟」對話框；否則，處理錯誤
1. 在「檔案名」欄位中提供檔案名，然後按一下「開啟」按鈕
1. 確保檔案實際開啟
1. 通過選擇「檔案」>「打印」開啟「打印」對話框
1. 確保顯示「打印」對話框

AppMon使用標準的Win32 API與第三方應用程式交互，以傳輸UI事件，如按鍵和滑鼠點擊，這對控制這些應用程式以從它們生成PDF檔案非常有用。

由於這些Win32 API的限制，AppMon無法將這些UI事件發送到某些特定類型的窗口，如浮動菜單欄（在TextPad等應用程式中找到），以及某些類型的對話框，其內容無法使用Win32 API檢索。

直觀地識別浮動菜單條很容易；但是，可能無法僅通過視覺檢查來確定特殊類型的對話。 您需要第三方應用程式(如Microsoft Spy++(Microsoft Visual C++開發環境的一部分)或其等效的WinID(可從[https://www.dennisbabkin.com/php/download.php?what=WinID](https://www.dennisbabkin.com/php/download.php?what=WinID)免費下載)來檢查對話框，以確定AppMon是否能夠使用標準Win32 API與它進行交互。

如果WinID能夠提取對話框內容，如文本、子窗口、窗口類ID等，則AppMon也能夠提取這些內容。

此表列出了打印本機檔案格式時使用的資訊類型。

<table> 
 <thead> 
  <tr> 
   <th><p>資訊類型</p></th> 
   <th><p>說明</p></th> 
   <th><p>修改/建立與本機檔案相關的條目 </p></th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td><p>管理設定 </p></td> 
   <td><p>包括PDF設定、安全設定和檔案類型設定。 </p><p>檔案類型設定將檔案名副檔名與相應的本機應用程式關聯。 檔案類型設定還指定用於打印本機檔案的本機應用程式設定。 </p></td> 
   <td><p>要更改已支援的本機應用程式的設定，系統管理員在管理控制台中設定「檔案類型設定」。 </p><p>若要新增對新原生檔案格式的支援，您必須手動編輯檔案。 （請參閱<a href="converting-file-formats-pdf.md#adding-or-modifying-support-for-a-native-file-format">添加或修改對本機檔案格式的支援</a>。） </p></td> 
  </tr> 
  <tr> 
   <td><p>指令碼 </p></td> 
   <td><p>指定「生成PDF」服務與本機應用程式之間的交互。 這類交互通常指導應用程式將檔案打印到Adobe PDF驅動程式。 </p><p>該指令碼包含指導本機應用程式開啟特定對話框的說明，以及對這些對話框中的欄位和按鈕提供特定響應的說明。 </p></td> 
   <td><p>「產生PDF」服務包含所有支援原生應用程式的指令碼檔案。 您可以使用XML編輯應用程式修改這些檔案。</p><p>要添加對新本機應用程式的支援，必須建立新的指令碼檔案。 （請參閱<a href="converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application">為本機應用程式建立或修改附加對話框XML檔案</a>。） </p></td> 
  </tr> 
  <tr> 
   <td><p>一般對話方塊指示 </p></td> 
   <td><p>指定如何響應多個應用程式共用的對話框。 這些對話框由作業系統、輔助應用程式（如PDFMaker）和驅動程式生成。 </p><p>包含此資訊的檔案為appmon.global.en_US.xml。</p></td> 
   <td><p>請勿修改此檔案。 </p></td> 
  </tr> 
  <tr> 
   <td><p>特定於應用程式的對話框說明</p></td> 
   <td><p>指定如何響應特定於應用程式的對話框。 </p><p>包含此資訊的檔案為appmon。<i>[appname]</i>.dialog。<i>[locale]</i>.xml（例如appmon.word.en_US.xml）。</p></td> 
   <td><p>請勿修改此檔案。 </p><p>要為新的本機應用程式添加對話框說明，請參閱<a href="converting-file-formats-pdf.md#creating_or_modifying_an_additional_dialog_xml_file_for_a_native_application">為本機應用程式建立或修改附加的對話框XML檔案</a>。</p></td> 
  </tr> 
  <tr> 
   <td><p>其他特定於應用程式的對話框說明 </p></td> 
   <td><p>指定應用程式特定對話框指令的覆蓋和添加。 本節提供此類資訊的示例。 </p><p>包含此資訊的檔案為appmon。<i>[appname]</i>.addition。<i>[locale]</i>.xml。例如appmon.addition.en_US.xml。</p></td> 
   <td><p>可使用XML編輯應用程式建立和修改此類型的檔案。 （請參閱<a href="converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application">為本機應用程式建立或修改附加對話框XML檔案</a>。） </p><p><strong>重要</strong>:您必須為伺服器將支援的每個本機應用程式建立其他特定於應用程式的對話方塊指示。 </p></td> 
  </tr> 
 </tbody> 
</table>

### 關於指令碼和對話框XML檔案 {#about-the-script-and-dialog-xml-files}

指令碼XML檔案指示「生成PDF」服務導航應用程式對話框，與用戶導航應用程式對話框的方式相同。 指令碼XML檔案還指示「生成PDF」服務通過執行按鈕、選擇或取消選擇複選框或選擇菜單項等操作來響應對話框。

相反地，對話框XML檔案只是以指令碼XML檔案中使用的相同類型的操作響應對話框。

#### 對話框和窗口元素術語 {#dialog-box-and-window-element-terminology}

本節和下一節將根據所描述的透視，對對話框及其包含的元件使用不同的術語。 對話框元件是按鈕、欄位和組合框等項。

當本節和下節從用戶的角度描述對話框及其元件時，使用了諸如&#x200B;*dialog box*、*button*、*field*&#x200B;和&#x200B;*combox*&#x200B;等術語。

當本節和下一節從內部表示的角度描述對話框及其元件時，將使用&#x200B;*窗口元素*&#x200B;一詞。 窗口元素的內部表示是層次，其中每個窗口元素實例由標籤標識。 窗口元素實例還描述了其物理特性和行為。

從用戶的角度來看，對話框及其元件顯示不同的行為，其中某些對話框元素在激活之前處於隱藏狀態。 從內部代表的角度看，不存在此類行為問題。 例如，對話框的內部表示與包含的元件相似，但該元件在對話框內嵌套除外。

本節介紹為AppMon提供說明的XML元素。 這些元素的名稱如`dialog`元素和`window`元素。 本文檔使用單行字型來區分XML元素。 `*dialog*`元素標識XML指令碼檔案可能導致顯示的對話框，有意或無意。 `*window*`元素標識窗口元素（對話框或對話框的元件）。

#### 階層 {#hierarchy}

此圖表顯示指令碼和對話框XML的層次結構。 指令碼XML檔案符合script.xsd架構，該架構包括（在XML意義中）window.xsd架構。 同樣地，對話框XML檔案符合dialogs.xsd架構，其中也包含window.xsd架構。

![as_as_xml_hierarchy](assets/as_as_xml_hierarchy.png)

指令碼和對話框XML的層次

#### 指令碼XML檔案 {#script-xml-files}

*指令碼XML檔案*&#x200B;指定了一系列步驟，這些步驟引導本地應用程式導航到某些窗口元素，然後為這些元素提供響應。 大多數響應是文本或擊鍵，它們與用戶在相應對話框中提供的欄位、組合框或按鈕的輸入相對應。

「生成PDF」服務對指令碼XML檔案的支援目的是引導本機應用程式打印本機檔案。 但是，指令碼XML檔案可用於完成用戶在與本機應用程式的對話框交互時可以執行的任何任務。

指令碼XML檔案中的步驟會依序執行，不會有任何分支的機會。 唯一支援的條件式測試是超時/重試，如果某個步驟在特定時間段內和特定重試次數之後未成功完成，則會導致指令碼終止。

除了循序步驟之外，步驟內的指令也依序執行。 您必須確保步驟和指示反映使用者執行這些步驟的順序。

指令碼XML檔案中的每個步驟都標識了如果成功執行了步驟的指令，則預期會出現的窗口元素。 如果執行指令碼步驟時出現意外的對話框，則生成PDF服務將按下一節中所述搜索對話框XML檔案。

#### 對話框XML檔案 {#dialog-xml-files}

運行本地應用程式會顯示不同的對話框，無論本地應用程式處於可見模式還是不可見模式，都會顯示這些對話框。 對話框可由作業系統或應用程式本身生成。 當本機應用程式在「生成PDF」服務的控制下運行時，系統和本機應用程式對話框將顯示在不可見的窗口中。

*對話框XML檔案*&#x200B;指定生成PDF服務如何響應系統或本機應用程式對話框。 對話框XML檔案允許生成PDF服務響應未提示的對話框，以便於轉換過程。

當系統或本機應用程式顯示一個當前執行的指令碼XML檔案未處理的對話框時，生成PDF服務會按此順序搜索對話框XML檔案，當它找到匹配項時停止：

* appmon。*[appname]*.additional。*[locale]*.xml
* appmon。*[appname]。[locale]*.xml（請勿修改此檔案）。
* appmon.global.*[locale]*.xml（請勿修改此檔案）。

如果「生成PDF」服務找到對話框的匹配項，則通過發送為對話框指定的按鍵或其他操作將其關閉。 如果對話框的說明指定了中止消息，則生成PDF服務將終止當前正在執行的作業並生成錯誤消息。 此類中止消息將在指令碼XML文法的`abortMessage`元素中指定。

如果「生成PDF」服務遇到的對話框未在先前列出的任何檔案中描述，則生成PDF服務會將對話框的標題併入日誌檔案條目中。 當前執行的作業最終超時。 然後，您可以使用日誌檔案中的資訊，在本機應用程式的其他對話框XML檔案中合成新指令。

### 添加或修改對本機檔案格式的支援 {#adding-or-modifying-support-for-a-native-file-format}

本節介紹為支援其他本機檔案格式或修改對已支援本機檔案格式的支援而必須執行的任務。

您必須先完成下列工作，才能新增或修改支援。

#### 選擇用於標識窗口元素的工具 {#choosing-a-tool-for-identifying-window-elements}

對話框和指令碼XML檔案要求您標識對話框或指令碼元素要響應的窗口元素（對話框、欄位或其他對話框元件）。 例如，在指令碼調用本地應用程式的菜單後，指令碼必須標識該菜單上要應用擊鍵或操作的窗口元素。

通過標題欄中顯示的標題，可以輕鬆識別對話框。 但是，必須使用Microsoft Spy++等工具來標識較低級別的窗口元素。 可以通過各種屬性來識別較低級別的窗口元素，這些屬性並不明顯。 此外，每個本機應用程式可以不同地識別其窗口元素。 因此，有多種方式可識別視窗元素。 以下是考慮窗口元素標識的建議順序：

1. 註解本身（如果它是唯一的）
1. 控制ID，它對於指定對話框可能唯一，也可能不唯一
1. 類名，可能唯一，也可能不唯一

這三個屬性的任何一個或組合都可以用來識別視窗。

如果屬性無法識別標題，則可以改為使用相對於其父項的索引來識別窗口元素。 *index*&#x200B;指定窗口元素相對於其同級窗口元素的位置。 索引通常是標識組合框的唯一方法。

請注意下列問題：

* Microsoft Spy++使用&amp;符號來標識字幕的熱鍵，從而顯示字幕。 例如，Spy++將一個「打印」對話框的標題顯示為`Pri&nt`，表示熱鍵為&#x200B;*n*。 指令碼和對話框XML檔案中的標題必須忽略&amp;符號。
* 有些字幕包括分行。 產生PDF服務無法識別分行。 如果標題包括分行符，則包括足夠的標題以將其與其他菜單項區分，然後對省略的部分使用規則表達式。 例如(`^Long caption title$`)。 （請參閱[在字幕屬性中使用規則運算式](converting-file-formats-pdf.md#using-regular-expressions-in-caption-attributes)。）
* 對保留的XML字元使用字元實體（也稱為轉義序列）。 例如，對於&amp;符號，`&`和`>`對於小於和大於符號，`&apos;`對於單引號，`&quot;`對於雙引號。`<`

如果您打算使用對話框或指令碼XML檔案，則應安裝應用程式Microsoft Spy++。

#### 取消對對話框和指令碼檔案的打包 {#unpackaging-the-dialog-and-script-files}

對話方塊和指令碼檔案位於appmondata.jar檔案中。 在可以修改其中任何檔案或添加新指令碼或對話框檔案之前，必須取消包裝此JAR檔案。 例如，假設您要添加對EditPlus應用程式的支援。 建立兩個XML檔案，名為appmon.editplus.script.en_US.xml和appmon.editplus.script.addition.en_US.xml。 必須將這些XML指令碼新增至adobe-appmondata.jar檔案中的兩個位置，如下所指定：

* adobe-livecycle-native-jboss-x86_win32.ear > adobe-Native2PDFSvc.war\WEB-INF\lib > adobe-native.jar > Native2PDFSvc-native.jar\bin > adobe-appmondata.jar\com\adobe\appmon。 adobe-livecycle-native-jboss-x86_win32.ear檔案位於*[AEM forms install directory]\*configurationManager的匯出資料夾中。 (如果AEM Forms部署在其他J2EE應用程式伺服器上，請以與您的J2EE應用程式伺服器對應的EAR檔案取代adobe-livecycle-native-jboss-x86_win32.ear檔案。)
* adobe-generatepdf-dsc.jar > adobe-appmondata.jar\com\adobe\appmon （adobe-appmondata.jar檔案位於adobe-generatepdf-dsc.jar檔案內）。 adobe-generatepdf-dsc.jar檔案位於&#x200B;*[AEM forms安裝目錄]*\deploy資料夾中。

將這些XML檔案新增至adobe-appmondata.jar檔案後，您必須重新部署GeneratePDF元件。 若要將對話方塊和指令碼XML檔案新增至adobe-appmondata.jar檔案，請執行下列工作：

1. 使用WinZip或WinRAR等工具，開啟adobe-livecycle-native-jboss-x86_win32.earfile > adobe-Native2PDFSvc.war\WEB-INF\lib > adobe-native.jar > Native2PDFSvc-vc-native.jar\bin > adobe-appmondata.jar檔案。
1. 將對話框和指令碼XML檔案添加到appmondata.jar檔案中，或修改此檔案中的現有XML檔案。 （請參閱[為本機應用程式](converting-file-formats-pdf.md#creating-or-modifying-a-script-xml-file-for-a-native-application)建立或修改指令碼XML檔案和[為本機應用程式](converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application)建立或修改附加的對話框XML檔案。）
1. 使用WinZip或WinRAR等工具，開啟adobe-generatepdf-dsc.jar > adobe-appmondata.jar。
1. 將對話框和指令碼XML檔案添加到appmondata.jar檔案中，或修改此檔案中的現有XML檔案。 （請參閱[為本機應用程式](converting-file-formats-pdf.md#creating-or-modifying-a-script-xml-file-for-a-native-application)建立或修改指令碼XML檔案和[為本機應用程式](converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application)建立或修改附加的對話框XML檔案。） 將XML檔案新增至adobe-appmondata.jar檔案後，請將新的adobe-appmondata.jar檔案放入adobe-generatepdf-dsc.jar檔案中。
1. 如果添加了對其他本機檔案格式的支援，請建立提供應用程式路徑的系統環境變數（請參閱[建立環境變數以查找本機應用程式](converting-file-formats-pdf.md#creating-an-environment-variable-to-locate-the-native-application)）。

**重新部署GeneratePDF元件**

1. 登入Workbench。
1. 選擇&#x200B;**Window** > **顯示視圖** > **元件**。 此動作會將「元件」檢視新增至Workbench。
1. 按一下右鍵GeneratePDF元件，然後選擇&#x200B;**Stop Component**。
1. 元件停止後，按一下右鍵並選擇「卸載元件」將其刪除。
1. 按一下右鍵&#x200B;**元件**&#x200B;表徵圖，然後選擇&#x200B;**安裝元件**。
1. 瀏覽並選取修改的adobe-generatepdf-dsc.jar檔案，然後按一下「開啟」。 請注意， GeneratePDF元件旁會出現一個紅方。
1. 展開GeneratePDF元件，選擇服務描述符，然後按一下右鍵GeneratePDFService並選擇激活服務。
1. 在顯示的設定對話方塊中，輸入適用的設定值。 若將這些值保留為空白，則會使用預設設定值。
1. 按一下右鍵「生成PDF」，然後選擇「啟動元件」。
1. 展開「活動服務」。 服務名稱（如果正在運行）旁會出現綠色箭頭。 否則，服務處於停止狀態。
1. 如果服務處於停止狀態，請按一下右鍵服務名稱，然後選擇啟動服務。

### 為本機應用程式建立或修改指令碼XML檔案 {#creating-or-modifying-a-script-xml-file-for-a-native-application}

如果要將檔案導向到新的本機應用程式，必須為該應用程式建立指令碼XML檔案。 如果要修改生成PDF服務與已支援的本機應用程式交互的方式，則必須修改該應用程式的指令碼。

指令碼包含在本機應用程式的窗口元素中導航的指令，並為這些元素提供特定響應。 包含此資訊的檔案為appmon。*[appname]*.script。*[locale]*.xml。例如appmon.notepad.script.en_US.xml。

#### 識別指令碼必須執行的步驟 {#identifying-steps-the-script-must-execute}

使用本機應用程式確定必須導航的窗口元素以及必須執行的打印文檔的每個響應。 請注意任何回應產生的對話方塊。 步驟將類似於以下步驟：

1. 選擇「檔案」>「開啟」。
1. 指定路徑，然後按一下「開啟」。
1. 在菜單欄上選擇檔案>打印。
1. 指定打印機所需的屬性。
1. 選擇「打印」並等待「另存為」對話框出現。 「生成PDF」服務需要「另存新檔」對話框來指定PDF檔案的目標。

#### 標識在字幕屬性中指定的對話框 {#identifying-the-dialogs-specified-in-caption-attributes}

使用Microsoft Spy++獲取本地應用程式中窗口元素屬性的標識。 您必須有這些身分才能編寫指令碼。

#### 在註解屬性中使用規則運算式 {#using-regular-expressions-in-caption-attributes}

您可以在註解規格中使用規則運算式。 「產生PDF」服務使用`java.util.regex.Matcher`類別來支援規則運算式。 該實用程式支援`java.util.regex.Pattern`中描述的規則運算式。

**在記事本橫幅中，可容納在記事本前面的檔案名的規則運算式**

```as3
 <!-- The regular expression ".*Notepad" means any number of non-terminating characters followed by Notepad. --> 
 <step> 
     <expectedWindow> 
         <window caption=".*Notepad"/> 
     </expectedWindow> 
 </step>
```

**規則運算式區分打印和打印設定**

```as3
 <!-- This regular expression differentiates the Print dialog box from the Print Setup dialog box. The "^" specifies the beginning of the line, and the "$" specifies the end of the line. --> 
 <windowList> 
     <window controlID="0x01" caption="^Print$" action="press"/> 
 </windowList>
```

#### 對窗口和windowList元素排序 {#ordering-the-window-and-windowlist-elements}

您必須依下列方式排序`window`和`windowList`元素：

* 當多個`window`元素在`windowList`或`dialog`元素中顯示為子元素時，請以降序排序這些`window`元素，並以`caption`名稱的長度指示該順序中的位置。
* 當`window`元素中出現多個`windowList`元素時，請以降序排序這些`windowList`元素，第一個`indexes/`元素的`caption`屬性長度指示該順序中的位置。

**對對話框檔案中的窗口元素進行排序**

```as3
 <!-- The caption attribute in the following window element is 40 characters long. It is the longest caption in this example, so its parent window element appears before the others. --> 
 <window caption="Unexpected Failure in DebugActiveProcess"> 
     <…> 
 </window> 
  
 <!-- Caption length is 33 characters. --> 
 <window caption="Adobe Acrobat - License Agreement"> 
     <…> 
 </window> 
  
 <!-- Caption length is 33 characters. --> 
 <window caption="Microsoft Visual.*Runtime Library"> 
     <…> 
 </window> 
  
 <!-- The caption attribute in the following window element is 28 characters long. It is the shortest caption in this example, so its parent window element appears after the others. --> 
 <window caption="Adobe Acrobat - Registration"> 
     <…> 
 </window>
```

**在windowList元素內排序窗口元素**

```as3
 <!-- The caption attribute in the following indexes element is 56 characters long. It is the longest caption in this example, so its parent window element appears before the others. --> 
 <windowList> 
     <window caption="Can&apos;t exit design mode because.* cannot be created"/> 
     <window className="Button" caption="OK" action="press"/> 
 </windowList> 
 <windowList> 
     <window caption="Do you want to continue loading the project?"/> 
     <window className="Button" caption="No" action="press"/> 
 </windowList> 
 <windowList> 
     <window caption="The macros in this project are disabled"/> 
     <window className="Button" caption="OK" action="press"/> 
 </windowList>
```

### 為本機應用程式建立或修改其他對話框XML檔案 {#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application}

如果為以前不支援的本機應用程式建立指令碼，則還必須為該應用程式建立一個附加的對話框XML檔案。 AppMon使用的每個本機應用程式都只能有一個額外的對話XML檔案。 即使沒有未請求的對話框，也需要附加的對話框XML檔案。 即使該`window`元素僅是佔位符，該附加對話框必須至少包含一個`window`元素。

>[!NOTE]
>
>在此情境中，「額外」一詞表示應用程式的內容。[applicationname].addition。[locale].xml檔案。此類檔案指定對話XML檔案的覆蓋和添加。

您還可以為以下目的修改本機應用程式的其他對話框XML檔案：

* 用不同的響應覆蓋應用程式的對話框XML檔案
* 向該應用程式的對話框XML檔案中未定址的對話框添加響應

標識其他dialogXML檔案的檔案名為appmon。*[appname]*.addition。*[locale]*.xml。例如appmon.excel.addition.en_US.xml。

其他對話框XML檔案的名稱必須使用appmon格式。*[applicationname]*.addition。*[locale]*.xml，其中 ** applicationname必須與XML配置檔案和指令碼中使用的應用程式名稱完全匹配。

>[!NOTE]
>
>native2pdfconfig.xml配置檔案中指定的所有通用應用程式都沒有主對話框XML檔案。 [添加或修改對本機檔案格式](converting-file-formats-pdf.md#adding-or-modifying-support-for-a-native-file-format)的支援部分描述了此類規範。

您必須排序`windowList`元素，這些元素在`window`元素中顯示為子項。 （請參閱[排序窗口和windowList元素](converting-file-formats-pdf.md#ordering-the-window-and-windowlist-elements)。）

### 修改常規對話框XML檔案 {#modifying-the-general-dialog-xml-file}

可以修改常規對話框XML檔案以響應系統生成的對話框或響應多個應用程式共同的對話框。

#### 在XML配置檔案中添加檔案類型條目 {#adding-a-filetype-entry-in-the-xml-configuration-file}

此過程說明如何更新生成PDF服務配置檔案，以將檔案類型與本機應用程式關聯。 要更新此配置檔案，必須使用管理控制台將配置資料導出到檔案。 配置資料的預設檔案名為native2pdfconfig.xml。

**更新產生PDF服務設定檔**

1. 選擇&#x200B;**首頁** > **服務** > **Adobe PDF生成器** > **配置檔案**，然後選擇&#x200B;**導出配置**。
1. 視需要修改native2pdfconfig.xml檔案中的`filetype-settings`元素。
1. 選擇&#x200B;**首頁** > **服務** > **Adobe PDF生成器** > **配置檔案**，然後選擇&#x200B;**導入配置**。 配置資料會匯入「產生PDF」服務，取代先前的設定。

>[!NOTE]
>
>應用程式的名稱被指定為`GenericApp`元素的`name`屬性的值。 此值必須與您在為該應用程式開發的指令碼中指定的對應名稱完全相符。 同樣，`GenericApp`元素的`displayName`屬性應完全符合對應指令碼的`expectedWindow`視窗標題。 解析出`displayName`或`caption`屬性中出現的任何規則運算式後，即會評估此類對應。

在此示例中，已修改「生成PDF」服務提供的預設配置資料，以指定應使用記事本（而非Microsoft Word）來處理副檔名為.txt的檔案。 在進行此修改之前，已將Microsoft Word指定為應處理此類檔案的本機應用程式。

**將文本檔案導向到記事本(native2pdfconfig.xml)的修改**

```as3
 <filetype-settings> 
  
 <!-- Some native app file types were omitted for brevity. --> 
 <!-- The following GenericApp element specifies Notepad as the native application that should be used to process files that have a txt file name extension. --> 
             <GenericApp 
                 extensions="txt" 
                 name="Notepad" displayName=".*Notepad"/> 
             <GenericApp  
                 extensions="wpd"  
                 name="WordPerfect" displayName="Corel WordPerfect"/> 
             <GenericApp extensions="pmd,pm6,p65,pm"  
                 name="PageMaker" displayName="Adobe PageMaker"/> 
             <GenericApp extensions="fm"  
                 name="FrameMaker" displayName="Adobe FrameMaker"/> 
             <GenericApp extensions="psd"  
                 name="Photoshop" displayName="Adobe Photoshop"/> 
         </settings> 
     </filetype-settings>
```

#### 建立環境變數以找出原生應用程式 {#creating-an-environment-variable-to-locate-the-native-application}

建立環境變數，指定本機應用程式執行檔的位置。 變數必須使用&#x200B;*[applicationname]*_PATH格式，其中&#x200B;*applicationname*&#x200B;必須與XML配置檔案和指令碼中使用的應用程式名稱完全匹配，且路徑包含雙引號中執行檔的路徑。 此類環境變數的範例為`Photoshop_PATH`。

建立新環境變數後，您必須重新啟動部署「產生PDF」服務的伺服器。

**在Windows XP環境中建立系統變數**

1. 選擇&#x200B;**控制面板>系統**。
1. 在「系統屬性」對話框中，按一下「**高級**」頁簽，然後按一下「**環境變數**」。
1. 在「環境變數」對話框的「系統變數」下，按一下「**新建**」。
1. 在「新建系統變數」對話框的「變數名稱&#x200B;**」框中，鍵入使用&#x200B;*[applicationname]*_PATH格式的名稱。**
1. 在&#x200B;**變數值**&#x200B;框中，鍵入應用程式執行檔的完整路徑和檔案名，然後按一下&#x200B;**確定**。 例如，輸入：`c:\windows\Notepad.exe`
1. 在「環境變數」對話框中，按一下「**確定**」。

**從命令列建立系統變數**

1. 在命令列視窗中，使用以下格式輸入變數定義：

   ```as3
            [applicationname]_PATH=[Full path name]
   ```

   例如，輸入：`NotePad_PATH=C:\WINDOWS\NOTEPAD.EXE`

1. 啟動新的命令行提示，使系統變數生效。

#### XML檔案 {#xml-files}

AEM Forms包含範例XML檔案，這些檔案會導致「產生PDF」服務使用記事本處理任何副檔名為.txt的檔案。 本節包含此程式碼。 此外，您必須進行本節所述的其他修改。

#### 其他對話框XML檔案 {#additional-dialog-xml-file}

此示例包含記事本應用程式的其他對話框。 除了「生成PDF」服務指定的對話框之外，還可以使用這些對話框。

**記事對話框(appmon.notepad.addition.en_US.xml)**

```as3
 <dialogs app="Notepad" locale="en_US" version="7.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="dialogs.xsd"> 
     <window caption="Caption Title"> 
         <windowList> 
             <window className="Button" caption="OK" action="press"/> 
         </windowList> 
     </window> 
 </dialogs>
```

#### 指令碼XML檔案 {#script-xml-file}

此示例指定「生成PDF」服務如何與記事本交互，以使用Adobe PDF打印機打印檔案。

**記事本指令碼XML檔案(appmon.notepad.script.en_US.xml)**

```as3
<?xml version="1.0" encoding="UTF-8" standalone="yes"?> 
<!-- 
* 
* ADOBE CONFIDENTIAL 
* ___________________ 
* Copyright 2004 - 2005 Adobe Systems Incorporated 
* All Rights Reserved. 
* 
* NOTICE:  All information contained herein is, and remains 
* the property of Adobe Systems Incorporated and its suppliers, 
* if any.  The intellectual and technical concepts contained 
* herein are proprietary to Adobe Systems Incorporated and its 
* suppliers and may be covered by U.S. and Foreign Patents, 
* patents in process, and are protected by trade secret or copyright law. 
* Dissemination of this information or reproduction of this material 
* is strictly forbidden unless prior written permission is obtained 
* from Adobe Systems Incorporated. 
*--> 
 
<!-- This file automates printing of text files via notepad to Adobe PDF printer. In order to see the complete hierarchy we recommend using the Microsoft Spy++ which details the properties of windows necessary to write scripts. In this sample there are total of eight steps--> 
 
<application name="Notepad" version="9.0" locale="en_US" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="scripts.xsd"> 
 
    <!-- In this step we wait for the application window to appear --> 
    <step> 
        <expectedWindow> 
            <window caption=".*Notepad"/> 
        </expectedWindow> 
    </step> 
     
    <!-- In this step, we acquire the application window and send File->Open menu bar, menu item commands and the expectation is the windows Open dialog-->         
    <step> 
        <acquiredWindow> 
            <window caption=".*Notepad"> 
                <virtualInput> 
                    <menuBar> 
                        <selection> 
                            <name>File</name> 
                        </selection> 
                        <selection> 
                            <name>Open...</name> 
                        </selection> 
                    </menuBar> 
                </virtualInput> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Open"/> 
        </expectedWindow> 
    </step> 
     
    <!-- In this step, we acquire the Open window and then select the 'Edit' widget and input the source path followed by clicking on the 'Open' button . The expectation of this 'action' is that the Open dialog will disappear --> 
    <step> 
        <acquiredWindow> 
            <window caption="Open"> 
                <windowList> 
                    <window className="ComboBoxEx32"> 
                        <windowList> 
                            <window className="ComboBox"> 
                                <windowList> 
                                <window className="Edit" action="inputSourcePath"/> 
                                </windowList> 
                            </window> 
                        </windowList> 
                    </window> 
                </windowList> 
                <windowList> 
                    <window className="Button" caption="Open" action="press"/> 
                </windowList> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Open" action="disappear"/> 
        </expectedWindow> 
        <pause value="30"/> 
    </step> 
     
    <!-- In this step, we acquire the application window and send File->Print menu bar, menu item commands and the expectation is the windows Print dialog--> 
    <step> 
        <acquiredWindow> 
            <window caption=".*Notepad"> 
                <virtualInput> 
                    <menuBar> 
                        <selection> 
                            <name>File</name> 
                        </selection> 
                        <selection> 
                            <name>Print...</name> 
                        </selection> 
                    </menuBar> 
                </virtualInput> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Print"> 
        </window> 
        </expectedWindow> 
    </step> 
     
    <!-- In this step, we acquire the Print dialog and click on the 'Preferences' button and the expected window in this case is the dialog with the caption '"Printing Preferences' --> 
    <step> 
        <acquiredWindow> 
            <window caption="Print"> 
                <windowList> 
                    <window caption="General"> 
                        <windowList> 
                            <window className="Button" caption="Preferences" action="press"/> 
                        </windowList> 
                    </window> 
                </windowList> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Printing Preferences"/> 
        </expectedWindow> 
    </step> 
     
    <!-- In this step, we acquire the dialog "Printing Preferences' and select the combo box which is the 10th child of window with caption '"Adobe PDF Settings' and select the first index. (Note: All indeces start with 0.) Besides this we uncheck the box which  has the caption '"View Adobe PDF results' and we click on the button OK. The expectation is that 'Printing Preferences' dialog disappears. --> 
    <step> 
        <acquiredWindow> 
            <window caption="Printing Preferences"> 
                <windowList> 
                    <window caption="Adobe PDF Settings"> 
                        <windowList> 
                            <window className="Button" caption="View Adobe PDF results" action="uncheck"/> 
                        </windowList> 
                        <windowList> 
                            <window className="Button" caption="Ask to Replace existing PDF file" action="uncheck"/> 
                        </windowList> 
                    </window> 
                </windowList> 
                <windowList> 
                    <window className="Button" caption="OK" action="press"/> 
                </windowList> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Printing Preferences" action="disappear"/> 
        </expectedWindow> 
    </step> 
     
    <!-- In this step, we acquire the 'Print' dialog and click on the Print button. The expectation is that the dialog with caption 'Print' disappears. In this case we use the regular expression '^Print$' for specifying the caption given there could be multiple dialogs with caption that includes the word Print. --> 
    <step> 
        <acquiredWindow> 
            <window caption="Print"> 
                <windowList> 
                    <window caption="General"/> 
                    <window className="Button" caption="^Print$" action="press"/> 
                </windowList> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Print" action="disappear"/> 
        </expectedWindow> 
    </step> 
    <step> 
        <expectedWindow> 
            <window caption="Save PDF File As"/> 
        </expectedWindow> 
    </step> 
    <!-- Finally in this step, we acquire the dialog with caption "Save PDF File As" and in the Edit widget type the destination path for the output PDF file and click on the Save button. The expectation is that the dialog disappears--> 
    <step> 
        <acquiredWindow> 
            <window caption="Save PDF File As"> 
                <windowList> 
                    <window className="Edit" action="inputDestinationPath"/> 
                </windowList> 
                <windowList> 
                    <window className="Button" caption="Save" action="press"/> 
                </windowList> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Save PDF File As" action="disappear"/> 
        </expectedWindow> 
    </step> 
     
    <!-- We can always set a retry count or a maximum time for a step. In case we surpass these limitations, PDF Generator generates this abort message and terminates processing. --> 
    <abortMessage msg="15078"/> 
</application>
```

---
title: 生成PDF服務Java API快速入門(SOAP)
seo-title: Generate PDF Service Java API QuickStart(SOAP)
description: 使用「生成PDF」服務將Microsoft Word文檔轉換為PDF文檔，將HTML內容轉換為PDF文檔，使用Java API將PDF文檔轉換為RTF檔案。
seo-description: Use the Generate PDF service to convert a Microsoft Word document to a PDF document, convert HTML content to a PDF document, convert a PDF document to an RTF file using the Java API.
uuid: f8c4a476-de5e-440a-b419-0bd1d7fde5ca
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: a7c0c4cf-7476-41e7-8d4e-564e6a21458d
role: Developer
exl-id: 897be9a1-a2e7-469f-8c60-2ede787cef29
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 1%

---

# 產生PDF服務Java API快速入門(SOAP) {#generate-pdf-service-java-api-quickstart-soap}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Java API快速入門(SOAP)適用於產生PDF服務。

[快速入門（SOAP模式）:使用Java API將Microsoft Word檔案轉換為PDF檔案](generate-pdf-service-java-api.md#quick-start-soap-mode-converting-a-microsoft-word-document-to-a-pdf-document-using-the-java-api)

[快速入門（SOAP模式）:使用Java API將HTML內容轉換為PDF檔案](generate-pdf-service-java-api.md#quick-start-soap-mode-converting-html-content-to-a-pdf-document-using-the-java-api)

[快速入門（SOAP模式）:使用Java API（SOAP模式）將PDF文檔轉換為RTF檔案](generate-pdf-service-java-api.md#quick-start-soap-mode-converting-a-pdf-document-to-an-rtf-file-using-the-java-api-soap-mode)

AEM Forms操作可使用AEM Forms強制類型API來執行，且連線模式應設為SOAP。

>[!NOTE]
>
>使用AEM Forms進行程式設計中的快速入門是以部署在JBoss Application Server和Microsoft Windows作業系統上的Forms Server為基礎。 但是，如果您使用其他作業系統（如UNIX），請用適用作業系統支援的路徑取代Windows專用路徑。 同樣，如果您正在使用其他J2EE應用程式伺服器，請確保指定有效的連接屬性。 請參閱 [設定連接屬性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## 快速入門（SOAP模式）:使用Java API將Microsoft Word檔案轉換為PDF檔案 {#quick-start-soap-mode-converting-a-microsoft-word-document-to-a-pdf-document-using-the-java-api}

以下代碼示例轉換名為 *Loan.doc* 到已命名的PDF文檔 *Loan.pdf*. (請參閱 [將Word文檔轉換為PDF文檔](/help/forms/developing/converting-file-formats-pdf.md#converting-word-documents-to-pdf-documents).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-generatepdf-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. activation.jar (required for SOAP mode) 
     * 7. axis.jar (required for SOAP mode) 
     * 8. commons-codec-1.3.jar (required for SOAP mode) 
     * 9.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 10. commons-discovery.jar (required for SOAP mode) 
     * 11. commons-logging.jar (required for SOAP mode) 
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 14. jaxrpc.jar (required for SOAP mode) 
     * 15. log4j.jar (required for SOAP mode) 
     * 16. mail.jar (required for SOAP mode) 
     * 17. saaj.jar (required for SOAP mode) 
     * 18. wsdl4j.jar (required for SOAP mode) 
     * 19. xalan.jar (required for SOAP mode) 
     * 20. xbean.jar (required for SOAP mode) 
     * 21. xercesImpl.jar (required for SOAP mode) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * The adobe-utilities.jar file is located in the following path: 
     * <install directory>/sdk/client-libs/jboss 
     * 
     * The jboss-client.jar file is located in the following path: 
     * <install directory>/jboss/bin/client 
     * 
     * SOAP required JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include these additional JAR files 
     * 
     * For information about the SOAP  
     * mode, see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
 import java.io.File; 
 import java.io.FileInputStream; 
 import java.util.Properties; 
  
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.generatepdf.client.CreatePDFResult; 
 import com.adobe.livecycle.generatepdf.client.GeneratePdfServiceClient; 
  
 public class ConvertWordDocumentSOAP { 
  
     public static void main(String[] args) 
     { 
         try{ 
         //Set connection properties required to invoke AEM Forms using SOAP mode                                 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
          
         //Create a ServiceClientFactory instance 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
                  
         //Create a GeneratePdfServiceClient object 
         GeneratePdfServiceClient pdfGenClient = new GeneratePdfServiceClient(myFactory); 
          
         //Get a Microsoft Word file document to convert to a PDF document 
         String inputFileName = "C:\\Adobe\\Loan.doc"; 
         FileInputStream fileInputStream = new FileInputStream(inputFileName); 
         Document inDoc = new Document(fileInputStream); 
          
         //Set createPDF2 parameter values 
         String adobePDFSettings = "Smallest_File_Size"; 
          String securitySettings = "No Security"; 
          String fileTypeSettings = "Filetype Settings"; 
           
          //Convert the Word document to a PDF document 
          CreatePDFResult result = pdfGenClient.createPDF2( 
             inDoc, 
             inputFileName, 
             fileTypeSettings, 
             adobePDFSettings, 
             securitySettings, 
             null, 
             null); 
               
          //Get the newly created document 
          Document createdDocument = result.getCreatedDocument(); 
               
          //Save the converted PDF document as a PDF file 
         createdDocument.copyToFile(new File("C:\\Adobe\\Loan.pdf")); 
     } 
     catch (Exception e) { 
         System.out.println("Error OCCURRED: " + e.getMessage()); 
         } 
     } 
 }
```

## 快速入門（SOAP模式）:使用Java API將HTML內容轉換為PDF檔案 {#quick-start-soap-mode-converting-html-content-to-a-pdf-document-using-the-java-api}

以下Java代碼示例將位於https://www.adobe.com的HTML內容轉換為名為的PDF文檔 *AdobeHTML.pdf*. (請參閱 [將HTML文檔轉換為PDF文檔](/help/forms/developing/converting-file-formats-pdf.md#converting-html-documents-to-pdf-documents).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-generatepdf-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. activation.jar (required for SOAP mode) 
     * 7. axis.jar (required for SOAP mode) 
     * 8. commons-codec-1.3.jar (required for SOAP mode) 
     * 9.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 10. commons-discovery.jar (required for SOAP mode) 
     * 11. commons-logging.jar (required for SOAP mode) 
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 14. jaxrpc.jar (required for SOAP mode) 
     * 15. log4j.jar (required for SOAP mode) 
     * 16. mail.jar (required for SOAP mode) 
     * 17. saaj.jar (required for SOAP mode) 
     * 18. wsdl4j.jar (required for SOAP mode) 
     * 19. xalan.jar (required for SOAP mode) 
     * 20. xbean.jar (required for SOAP mode) 
     * 21. xercesImpl.jar (required for SOAP mode) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * The adobe-utilities.jar file is located in the following path: 
     * <install directory>/sdk/client-libs/jboss 
     * 
     * The jboss-client.jar file is located in the following path: 
     * <install directory>/jboss/bin/client 
     * 
     * SOAP required JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include these additional JAR files 
     * 
     * For information about the SOAP  
     * mode, see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
 import java.io.File; 
 import java.util.Properties; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.generatepdf.client.GeneratePdfServiceClient; 
 import com.adobe.livecycle.generatepdf.client.HtmlToPdfResult; 
  
 public class ConvertHTMLSOAP { 
  
     public static void main(String[] args) 
     { 
         try{ 
         //Set connection properties required to invoke AEM Forms using SOAP mode                                 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
         //Create a ServiceClientFactory instance 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
          
         //Create a GeneratePdfServiceClient object 
         GeneratePdfServiceClient pdfGenClient = new GeneratePdfServiceClient(myFactory); 
          
         //Get an HTML document to convert to a PDF document a 
         String inputFileName = "https://www.adobe.com"; 
          
          String securitySettings = "No Security"; 
         String fileTypeSettings = "Standard"; 
           
          //Convert HTML content to a PDF document 
          HtmlToPdfResult result = pdfGenClient.htmlToPDF2( 
                  inputFileName, 
                  fileTypeSettings, 
                  securitySettings, 
                  null, 
                 null); 
               
          //Get the newly created document 
          Document createdDocument = result.getCreatedDocument(); 
           
          //Save the PDF document as a PDF file 
         createdDocument.copyToFile(new File("C:\\AdobeHTML.pdf")); 
     } 
     catch (Exception e) { 
         System.out.println("Error OCCURRED: " + e.getMessage()); 
     } 
     } 
 }
```

## 快速入門（SOAP模式）:使用Java API（SOAP模式）將PDF文檔轉換為RTF檔案 {#quick-start-soap-mode-converting-a-pdf-document-to-an-rtf-file-using-the-java-api-soap-mode}

以下代碼示例轉換名為的PDF文檔 *Loan.pdf* RTF文檔名稱 *Loan.rtf*. (請參閱 [將PDF文檔轉換為非影像格式](/help/forms/developing/converting-file-formats-pdf.md#converting-pdf-documents-to-non-image-formats).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-generatepdf-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. adobe-utilities.jar 
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed 
     * on JBoss) 
     * 6. activation.jar (required for SOAP mode) 
     * 7. axis.jar (required for SOAP mode) 
     * 8. commons-codec-1.3.jar (required for SOAP mode) 
     * 9.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 10. commons-discovery.jar (required for SOAP mode) 
     * 11. commons-logging.jar (required for SOAP mode) 
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 14. jaxrpc.jar (required for SOAP mode) 
     * 15. log4j.jar (required for SOAP mode) 
     * 16. mail.jar (required for SOAP mode) 
     * 17. saaj.jar (required for SOAP mode) 
     * 18. wsdl4j.jar (required for SOAP mode) 
     * 19. xalan.jar (required for SOAP mode) 
     * 20. xbean.jar (required for SOAP mode) 
     * 21. xercesImpl.jar (required for SOAP mode) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * The adobe-utilities.jar file is located in the following path: 
     * <install directory>/sdk/client-libs/jboss 
     * 
     * The jboss-client.jar file is located in the following path: 
     * <install directory>/jboss/bin/client 
     * 
     * SOAP required JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include these additional JAR files 
     * 
     * For information about the SOAP  
     * mode, see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
 import java.io.File; 
 import java.io.FileInputStream; 
 import java.util.Properties; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.generatepdf.client.ConvertPDFFormatType; 
 import com.adobe.livecycle.generatepdf.client.ExportPDFResult; 
 import com.adobe.livecycle.generatepdf.client.GeneratePdfServiceClient; 
  
  
 public class GeneratePdf_ExportPDFSOAP { 
  
     public static void main(String[] args) 
     { 
         try{ 
             //Set connection properties required to invoke AEM Forms using SOAP mode                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                  
             //Create a ServiceClientFactory instance 
             ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps); 
          
             //Create a GeneratePdfServiceClient object 
             GeneratePdfServiceClient pdfGenClient = new GeneratePdfServiceClient(factory); 
           
             //Get a PDF document to convert to an RTF document 
             String inputFileName = "C:\\Adobe\\Loan.pdf.pdf"; 
             FileInputStream fileInputStream = new FileInputStream(inputFileName); 
             Document inDoc = new Document(fileInputStream); 
              
             //Convert a PDF document to a RTF document 
             ExportPDFResult result = pdfGenClient.exportPDF2( 
                 inDoc, 
                 inputFileName, 
                 ConvertPDFFormatType.RTF, 
                 null); 
               
          //Get the newly created RTF document 
          Document createdDocument = result.getConvertedDocument(); 
               
          //Save the RTF file 
         createdDocument.copyToFile(new File("C:\\Adobe\\Loan.pdf.rtf")); 
         } 
         catch (Exception e) { 
             System.out.println("Error OCCURRED: " + e.getMessage()); 
         } 
     } 
 }
```

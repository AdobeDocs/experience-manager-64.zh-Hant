---
title: 簽名服務Java API快速入門(SOAP)
seo-title: Signature Service Java API QuickStart(SOAP)
description: 使用簽名服務向PDF文檔添加簽名欄位、檢索簽名欄位名稱、修改簽名欄位、對PDF文檔進行數字簽名、對基於XFA的表單進行數字簽名、對PDF文檔進行認證、驗證數字簽名、驗證多個數字簽名以及刪除數字簽名。
seo-description: Use the Signature service to add a signature field to a PDF document, retrieve signature field names, modify a signature field, digitally sign a PDF document, digitally sign an XFA-based form, certify a PDF document, verify a digital signature, verify multiple digital signatures, and remove a digital signature.
uuid: ae6adf23-b119-45f6-bd57-73d8d9ca8ecb
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 07fffbd5-5430-4abc-b532-0840ecc7b1b0
role: Developer
exl-id: 72726c83-e0e4-40ae-ad1d-8ac9589d9e8f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 0%

---

# 簽名服務Java API快速入門(SOAP) {#signature-service-java-api-quickstart-soap}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Java API快速入門(SOAP)適用於簽名服務：

[快速入門（SOAP模式）:使用Java API將簽名欄位新增至PDF檔案](signature-service-java-api-quick.md#quick-start-soap-mode-adding-a-signature-field-to-a-pdf-document-using-the-java-api)

[快速入門（SOAP模式）:使用Java API檢索簽名欄位名稱](signature-service-java-api-quick.md#quick-start-soap-mode-retrieving-signature-field-names-using-the-java-api)

[快速入門（SOAP模式）:使用Java API修改簽名欄位](signature-service-java-api-quick.md#quick-start-soap-mode-modifying-a-signature-field-using-the-java-api)

[快速入門（SOAP模式）:使用Java API數位簽署PDF檔案](signature-service-java-api-quick.md#quick-start-soap-mode-digitally-signing-a-pdf-document-using-the-java-api)

[快速入門（SOAP模式）:使用Java API以數位方式簽署XFA型表單](signature-service-java-api-quick.md#quick-start-soap-mode-digitally-signing-a-xfa-based-form-using-the-java-api)

[快速入門（SOAP模式）:使用Java API驗證PDF檔案](signature-service-java-api-quick.md#quick-start-soap-mode-certifying-a-pdf-document-using-the-java-api)

[快速入門（SOAP模式）:使用Java API驗證數位簽名](signature-service-java-api-quick.md#quick-start-soap-mode-verifying-a-digital-signature-using-the-java-api)

[快速入門（SOAP模式）:使用Java API驗證多個數位簽名](signature-service-java-api-quick.md#quick-start-soap-mode-verifying-multiple-digital-signatures-using-the-java-api)

[快速入門（SOAP模式）:使用Java API移除數位簽名](signature-service-java-api-quick.md#quick-start-soap-mode-removing-a-digital-signature-using-the-java-api)

AEM Forms操作可使用AEM Forms強制類型API來執行，且連線模式應設為SOAP。

>[!NOTE]
>
>「使用AEM Forms進行程式設計」中的「快速入門」以部署在JBoss Application Server和Microsoft Windows作業系統上的Forms伺服器為基礎。 但是，如果您使用其他作業系統（如UNIX），請用適用作業系統支援的路徑取代Windows專用路徑。 同樣，如果您正在使用其他J2EE應用程式伺服器，請確保指定有效的連接屬性。 請參閱 [設定連接屬性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## 快速入門（SOAP模式）:使用Java API將簽名欄位新增至PDF檔案 {#quick-start-soap-mode-adding-a-signature-field-to-a-pdf-document-using-the-java-api}

以下Java代碼示例添加一個名為 *簽名欄位1* PDF文檔，該文檔基於名為的PDF檔案&#x200B;*Loan.pdf*. 包含新簽名欄位的PDF文檔將另存為名為的PDF檔案 *LoanSig.pdf*. (請參閱 [添加簽名欄位](/help/forms/developing/digitally-signing-certifying-documents.md#adding-signature-fields).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-signatures-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
    * 4. activation.jar (required for SOAP mode) 
     * 5. axis.jar (required for SOAP mode) 
     * 6. commons-codec-1.3.jar (required for SOAP mode) 
     * 7.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 8. commons-discovery.jar (required for SOAP mode) 
     * 9. commons-logging.jar (required for SOAP mode) 
     * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 12. jaxrpc.jar (required for SOAP mode) 
     * 13. log4j.jar (required for SOAP mode) 
     * 14. mail.jar (required for SOAP mode) 
     * 15. saaj.jar (required for SOAP mode) 
     * 16. wsdl4j.jar (required for SOAP mode) 
     * 17. xalan.jar (required for SOAP mode) 
     * 18. xbean.jar (required for SOAP mode) 
     * 19. xercesImpl.jar (required for SOAP mode) 
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
 import java.util.*; 
 import java.io.File; 
 import java.io.FileInputStream; 
 import com.adobe.livecycle.signatures.client.*; 
 import com.adobe.livecycle.signatures.client.types.*; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class AddSignatureFieldSOAP { 
  
     public static void main(String[] args) { 
          
         try 
         { 
          //Set connection properties required to invoke AEM Forms using SOAP mode                                 
          Properties connectionProps = new Properties(); 
          connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
          connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
          connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
          connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
          connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
          
           //Create a ServiceClientFactory instance 
           ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
           //Create a SignatureServiceClient object 
           SignatureServiceClient signClient = new SignatureServiceClient(myFactory); 
          
           //Specify a PDF document to which a signature field is added 
           FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\Loan.pdf");     
           Document inDoc = new Document (fileInputStream);  
  
           //Specify the name of the signature field 
           String fieldName = "SignatureField1"; 
  
           //Create a  PositionRectangle object that specifies 
           //the signature fields location 
           PositionRectangle post = new  PositionRectangle(193,47,133,12); 
  
           //Specify the page number that will contain the signature field 
           java.lang.Integer pageNum = new java.lang.Integer(1); 
  
           //Add a signature field to the PDF document 
           Document sigFieldPDF = signClient.addSignatureField( 
              inDoc, 
              fieldName, 
              pageNum, 
              post, 
              null, 
              null); 
          
           //Save the PDF document that contains the signature field                     
           File outFile = new File("C:\\Adobe\LoanSig.pdf"); 
           sigFieldPDF.copyToFile(outFile); 
             } 
          
         catch (Exception ee) 
             { 
                 ee.printStackTrace(); 
             } 
     } 
 } 
  
 
```

## 快速入門（SOAP模式）:使用Java API檢索簽名欄位名稱 {#quick-start-soap-mode-retrieving-signature-field-names-using-the-java-api}

以下Java代碼示例檢索位於PDF文檔中的簽名欄位的名稱，該文檔名為 *LoanSig.pdf*. (請參閱 [檢索簽名欄位名稱](/help/forms/developing/digitally-signing-certifying-documents.md#retrieving-signature-field-names).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-signatures-client.jar 
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
 import java.util.*; 
 import java.io.FileInputStream; 
 import com.adobe.livecycle.signatures.client.*; 
 import com.adobe.livecycle.signatures.client.types.*; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class GetSignatureFieldsSOAP { 
  
 public static void main(String[] args) { 
     try 
     { 
         //Set connection properties required to invoke AEM Forms using SOAP mode                                 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
          
         //Create a ServiceClientFactory instance 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
         //Create a SignatureServiceClient object 
         SignatureServiceClient signClient = new SignatureServiceClient(myFactory); 
          
         //Specify a PDF document that contains signature fields 
         FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\LoanSig.pdf");     
         Document inDoc = new Document (fileInputStream); 
              
         //Retrieve the name of the document’s signature fields 
         List fieldNames = signClient.getSignatureFieldList(inDoc); 
  
         //Obtain the name of each signature field by iterating through the  
         //List object 
         Iterator iter = fieldNames.iterator();  
         int i = 0 ;  
         String fieldName=""; 
         while (iter.hasNext()) {  
             PDFSignatureField signatureField = (PDFSignatureField)iter.next();  
             fieldName = signatureField.getName(); 
             System.out.println("The name of the signature field is " +fieldName);  
             i++; 
              } 
         } 
         catch (Exception ee) 
         { 
             ee.printStackTrace(); 
         } 
     } 
 }
```

## 快速入門（SOAP模式）:使用Java API修改簽名欄位 {#quick-start-soap-mode-modifying-a-signature-field-using-the-java-api}

以下Java代碼示例通過在將簽名應用到簽名欄位時鎖定窗體中的所有欄位來修改名為SignatureField1的簽名欄位，並確保不允許更改。 簽名服務返回包含已修改簽名欄位的PDF文檔後，PDF文檔將另存為名為LoanSig.pdf的PDF檔案。 (此範例會覆寫傳遞至簽名服務的PDF檔案。) (請參閱 [修改簽名欄位](/help/forms/developing/digitally-signing-certifying-documents.md#modifying-signature-fields).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-signatures-client.jar 
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
  
 import java.util.*; 
 import java.io.File; 
 import java.io.FileInputStream; 
 import com.adobe.livecycle.signatures.client.*; 
 import com.adobe.livecycle.signatures.client.types.*; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class ModifySignatureFieldSOAP { 
      
     public static void main(String[] args) { 
          
     try 
     { 
         //Set connection properties required to invoke AEM Forms using SOAP mode                                 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
          
         //Create a ServiceClientFactory instance 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
         //Create a SignatureServiceClient object 
         SignatureServiceClient signClient = new SignatureServiceClient(myFactory); 
          
         //Specify a PDF document that contains a signature field to modify 
         FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\LoanSig.pdf");     
         Document inDoc = new Document (fileInputStream); 
          
         //Specify the name of the signature field 
         String fieldName = "SignatureField1"; 
          
         //Create a PDFSignatureFieldProperties 
         PDFSignatureFieldProperties fieldProperties = new PDFSignatureFieldProperties(); 
          
          //Create a PDFSeedValueOptionSpec object that stores  
          //seed value dictionary information. 
          PDFSeedValueOptionSpec seedOptionsSpec = new PDFSeedValueOptionSpec(); 
          
          //Disallow changes to the PDF document. Any change to the document invalidates  
          //the signature 
          seedOptionsSpec.setMdpValue(MDPPermissions.NoChanges); 
          
          //Create a FieldMDPOptionSpec object that stores  
          //signature field lock dictionary information. 
          FieldMDPOptionSpec fieldMDPOptionsSpec = new FieldMDPOptionSpec();     
          
          //Lock all fields in the PDF document 
          fieldMDPOptionsSpec.setAction(FieldMDPAction.ALL); 
          
          //Set dictionary information 
          fieldProperties.setSeedValue(seedOptionsSpec); 
          fieldProperties.setFieldMDP(fieldMDPOptionsSpec); 
                  
          //Modify the signature field 
          Document modSignatureField =  signClient.modifySignatureField(inDoc,fieldName,fieldProperties); 
                   
          //Save the PDF document that contains modified signature field 
          File file = new File("C:\\Adobe\LoanSig.pdf"); 
          modSignatureField.copyToFile(file); 
                   
     } 
     catch (Exception ee) 
       { 
         ee.printStackTrace(); 
       } 
     } 
 } 
 
```

## 快速入門（SOAP模式）:使用Java API數位簽署PDF檔案 {#quick-start-soap-mode-digitally-signing-a-pdf-document-using-the-java-api}

以下Java代碼示例以數字方式簽署基於以下PDF檔案的PDF文檔： *LoanSig.pdf*. 為安全憑據指定的別名是安全的，並執行吊銷檢查。 由於沒有指定CRL或OCSP伺服器資訊，因此從用於對PDF文檔進行數字簽名的證書中獲取伺服器資訊。 已簽名的文檔將另存為名為的PDF檔案 *LoanSigned.pdf*. (請參閱 [數位簽署PDF檔案](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-signatures-client.jar 
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
 import java.util.*; 
 import java.io.File; 
 import java.io.FileInputStream; 
 import com.adobe.livecycle.signatures.client.*; 
 import com.adobe.livecycle.signatures.client.types.*; 
 import com.adobe.livecycle.signatures.pki.client.types.common.HashAlgorithm; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class SignDocumentSOAP { 
  
 public static void main(String[] args) { 
          
     try 
     { 
       //Set connection properties required to invoke AEM Forms using SOAP mode                                 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
      
       //Create a ServiceClientFactory instance 
       ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
       //Create a SignatureServiceClient object 
       SignatureServiceClient signClient = new SignatureServiceClient(myFactory); 
          
       //Specify a PDF document to sign 
       FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\LoanSig.pdf");     
       Document credDoc = new Document (fileInputStream); 
      
       //Specify the name of the signature field 
       String fieldName = "SignatureField1"; 
  
       //Create a Credential object 
       Credential myCred = Credential.getInstance("secure"); 
  
       //Specify the reason to sign the document 
       String reason = "The document was reviewed"; 
  
       //Specify the location of the signer 
       String location  = "New York HQ";  
  
       //Specify contact information 
       String contactInfo = "Tony Blue"; 
  
       //Create a PDFSignatureAppearanceOptions object  
       //and show date information 
       PDFSignatureAppearanceOptionSpec appear = new  PDFSignatureAppearanceOptionSpec();  
       appear.setShowDate(true); 
       appear.setShowReason(true); 
      
       //Set revocation checking to false 
       java.lang.Boolean revCheck = new Boolean(true); 
      
       //Create an OCSPOptionSpec object to pass to the sign method 
            OCSPOptionSpec ocspSpec = new OCSPOptionSpec(); 
           
            //Create a CRLOptionSpec object to pass to the sign method 
            CRLOptionSpec crlSpec = new CRLOptionSpec(); 
           
            //Create a TSPOptionSpec object to pass to the sign method 
            TSPOptionSpec tspSpec = new TSPOptionSpec(); 
  
       //Sign the PDF document 
       Document signedDoc = signClient.sign( 
          credDoc, 
          fieldName, 
          myCred, 
          HashAlgorithm.SHA1, 
          reason, 
          location, 
          contactInfo, 
          appear, 
          revCheck, 
         ocspSpec, 
              crlSpec, 
              tspSpec); 
  
       //Save the signed PDF document                         
       File outFile = new File("C:\\Adobe\LoanSigned.pdf"); 
       signedDoc.copyToFile (outFile); 
       } 
      
     catch (Exception ee) 
       { 
         ee.printStackTrace(); 
       } 
       } 
 } 
  
 
```

## 快速入門（SOAP模式）:使用Java API以數位方式簽署XFA型表單 {#quick-start-soap-mode-digitally-signing-a-xfa-based-form-using-the-java-api}

下列Java程式碼範例會簽署由Forms服務轉譯的互動式表單。 此 `com.adobe.idp.Document` 由Forms服務傳回的例項會傳遞至簽名服務。 已簽名的互動式表單將另存為名為的PDF檔案 *LoanXFASided.pdf*.

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-signatures-client.jar 
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
 import java.util.*; 
 import java.io.File; 
 import java.io.FileInputStream; 
  
 import com.adobe.livecycle.formsservice.client.FormsResult; 
 import com.adobe.livecycle.formsservice.client.FormsServiceClient; 
 import com.adobe.livecycle.formsservice.client.PDFFormRenderSpec; 
 import com.adobe.livecycle.signatures.client.*; 
 import com.adobe.livecycle.signatures.client.types.*; 
 import com.adobe.livecycle.signatures.pki.client.types.common.HashAlgorithm; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class SignXFAFormsSOAP { 
  
 public static void main(String[] args) { 
          
     try 
     { 
      
      //Set connection properties required to invoke AEM Forms using SOAP mode                                 
      Properties connectionProps = new Properties(); 
      connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
      connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
      connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
      connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
      connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
          
      //Create a ServiceClientFactory instance 
      ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
      //Get the XFA form to sign 
      Document myForm = GetForm(myFactory); 
      
     //Sign the XFA form 
     SignXFA(myForm,myFactory);  
     } 
      
     catch (Exception ee) 
       { 
         ee.printStackTrace(); 
       } 
       } 
  
  
 //Creates an interactive PDF form based on a XFA form 
 private static Document GetForm(ServiceClientFactory myFactory) 
 { 
      
     try 
     { 
     //Create a FormsServiceClient object 
     FormsServiceClient formsClient = new FormsServiceClient(myFactory);  
  
     //Specify a PDF document to sign 
     FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\LoanSigXFA.pdf");     
     Document xfaForm = new Document (fileInputStream); 
              
     //Retrieve form data 
     FileInputStream cData = new FileInputStream("C:\\Adobe\Loan.xml"); 
     Document oInputData = new Document(cData); 
                              
     //Cache the PDF form 
     PDFFormRenderSpec pdfFormRenderSpec = new PDFFormRenderSpec(); 
     pdfFormRenderSpec.setGenerateServerAppearance(true); 
              
     //Invoke the renderPDFForm2 method  
     FormsResult formOut = formsClient.renderPDFForm2( 
             xfaForm,               //formQuery 
             oInputData,             //inDataDoc 
             pdfFormRenderSpec,      //PDFFormRenderSpec 
             null,                //urlSpec 
             null            //attachments 
             ); 
  
     //Create a Document object that stores form data 
     Document myForm = formOut.getOutputContent(); 
     return myForm;  
 } 
      
     catch (Exception ee) 
       { 
         ee.printStackTrace(); 
       } 
     return null;  
      
 } 
  
 //Sign the PDF document 
 private static void SignXFA(Document doc, ServiceClientFactory myFactory) 
 { 
     try 
     { 
      
     //Create a SignatureServiceClient object 
      SignatureServiceClient signClient = new SignatureServiceClient(myFactory); 
          
      //Specify the name of the signature field 
      String fieldName = "SignatureField1"; 
  
      //Create a Credential object 
      Credential myCred = Credential.getInstance("secure"); 
  
      //Specify the reason to sign the document 
      String reason = "The document was reviewed"; 
  
      //Specify the location of the signer 
      String location  = "New York HQ";  
  
      //Specify contact information 
      String contactInfo = "Tony Blue"; 
  
      //Create a PDFSignatureAppearanceOptions object  
      //and show date information 
      PDFSignatureAppearanceOptionSpec appear = new  PDFSignatureAppearanceOptionSpec();  
      appear.setShowDate(true); 
      appear.setShowReason(true); 
          
      //Set revocation checking to false 
      java.lang.Boolean revCheck = new Boolean(true); 
      
      //Create an OCSPOptionSpec object to pass to the sign method 
      OCSPOptionSpec ocspSpec = new OCSPOptionSpec(); 
      
      //Create a CRLOptionSpec object to pass to the sign method 
      CRLOptionSpec crlSpec = new CRLOptionSpec(); 
      
      //Create a TSPOptionSpec object to pass to the sign method 
      TSPOptionSpec tspSpec = new TSPOptionSpec(); 
  
      //Sign the PDF document 
       Document signedDoc = signClient.sign( 
          doc, 
          fieldName, 
          myCred, 
          HashAlgorithm.SHA1, 
          reason, 
          location, 
          contactInfo, 
          appear, 
          revCheck, 
         ocspSpec, 
         crlSpec, 
         tspSpec); 
  
       //Save the signed PDF document                         
       File outFile = new File("C:\\Adobe\LoanXFASigned.pdf"); 
       signedDoc.copyToFile (outFile); 
 } 
      
     catch (Exception ee) 
       { 
         ee.printStackTrace(); 
       } 
      } 
 } 
 
```

## 快速入門（SOAP模式）:使用Java API驗證PDF檔案 {#quick-start-soap-mode-certifying-a-pdf-document-using-the-java-api}

以下Java代碼示例驗證基於名為的PDF檔案的PDF文檔 *LoanSig.pdf*. 為安全憑據指定的別名是安全的，並且不執行吊銷檢查。 認證的文檔將另存為名為的PDF檔案 *LoanCertified.pdf*. (請參閱 [認證PDF檔案](/help/forms/developing/digitally-signing-certifying-documents.md#certifying-pdf-documents).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-signatures-client.jar 
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
 import java.util.*; 
 import java.io.File; 
 import java.io.FileInputStream; 
 import com.adobe.livecycle.signatures.client.*; 
 import com.adobe.livecycle.signatures.client.types.*; 
 import com.adobe.livecycle.signatures.pki.client.types.common.HashAlgorithm; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class CertifyDocumentSOAP { 
  
     public static void main(String[] args) { 
     try 
     { 
         //Set connection properties required to invoke AEM Forms using SOAP mode                                 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
           
       //Create a ServiceClientFactory instance 
       ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
       //Create a SignatureServiceClient object 
       SignatureServiceClient signClient = new SignatureServiceClient(myFactory); 
          
       //Specify a PDF document to certify 
       FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\LoanSig.pdf");     
       Document credDoc = new Document (fileInputStream);  
  
       //Specify the name of the signature field 
       String fieldName = "SignatureField1"; 
  
       //Create a Credential object 
       Credential myCred = Credential.getInstance("secure"); 
      
       //Specify the reason to sign the document 
       String reason = "The document was reviewed"; 
  
       //Specify the location of the signer 
       String location  = "My company";  
      
       //Specify contact information 
           String contactInfo = "New York, New York"; 
  
       //Create a PDFSignatureAppearanceOptions object and show date information 
       PDFSignatureAppearanceOptionSpec appear = new  PDFSignatureAppearanceOptionSpec();  
       appear.setShowDate(true); 
  
       //Set revocation checking to false 
            java.lang.Boolean revCheck = new Boolean(false); 
      
            //Set locking to false 
            java.lang.Boolean lockField = new Boolean(false); 
      
            //Specify a legalAttestation value 
            String msg = "Any change to this document will invalidate the certificate";     
      
            //Create objects to pass to the certify method 
            OCSPOptionSpec ocspSpec = new OCSPOptionSpec(); 
            CRLOptionSpec crlSpec = new CRLOptionSpec(); 
            TSPOptionSpec tspSpec = new TSPOptionSpec(); 
           
            //Certify the PDF document 
            Document signedDoc = signClient.certify( 
               credDoc, 
               fieldName, 
               myCred, 
               HashAlgorithm.SHA1, 
               reason, 
               location, 
               contactInfo, 
               MDPPermissions.NoChanges, 
               msg, 
               appear, 
               revCheck, 
               lockField, 
              ocspSpec, 
              crlSpec, 
              tspSpec); 
          
         //Save the signed PDF document                         
              File outFile = new File("C:\\Adobe\LoanCertified.pdf"); 
              signedDoc.copyToFile (outFile); 
         } 
      
     catch (Exception ee) 
         { 
         ee.printStackTrace(); 
         } 
     } 
 }
```

## 快速入門（SOAP模式）:使用Java API驗證數位簽名 {#quick-start-soap-mode-verifying-a-digital-signature-using-the-java-api}

以下Java代碼示例驗證位於基於名為LoanSigned.pdf的PDF檔案的已簽名PDF文檔中的數字簽名。 將驗證時間設定為當前時間，並將吊銷檢查選項設定為最佳努力。 (請參閱 [驗證數字簽名](#unresolvedlink-lc-si).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-signatures-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
    * 4. activation.jar (required for SOAP mode) 
     * 5. axis.jar (required for SOAP mode) 
     * 6. commons-codec-1.3.jar (required for SOAP mode) 
     * 7.  commons-collections-3.1.jar  (required for SOAP mode) 
     * 8. commons-discovery.jar (required for SOAP mode) 
     * 9. commons-logging.jar (required for SOAP mode) 
     * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 11. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 12. jaxrpc.jar (required for SOAP mode) 
     * 13. log4j.jar (required for SOAP mode) 
     * 14. mail.jar (required for SOAP mode) 
     * 15. saaj.jar (required for SOAP mode) 
     * 16. wsdl4j.jar (required for SOAP mode) 
     * 17. xalan.jar (required for SOAP mode) 
     * 18. xbean.jar (required for SOAP mode) 
     * 19. xercesImpl.jar (required for SOAP mode) 
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
 import java.util.*; 
 import java.io.FileInputStream; 
 import com.adobe.livecycle.signatures.client.*; 
 import com.adobe.livecycle.signatures.client.types.*; 
 import com.adobe.livecycle.signatures.pki.client.types.common.RevocationCheckStyle; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class VerifySignatureSOAP{ 
  
     public static void main(String[] args) { 
          
     try 
     { 
       //Set connection properties required to invoke AEM Forms using SOAP mode                                 
       Properties connectionProps = new Properties(); 
       connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
      connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
       connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
       connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
       connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
          
       //Create a ServiceClientFactory instance 
       ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
       //Create a SignatureServiceClient object 
       SignatureServiceClient signClient = new SignatureServiceClient(myFactory); 
      
       //Specify a PDF document that contains a digital signature 
       FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\LoanSigned.pdf");     
       Document inDoc = new Document (fileInputStream);  
  
       //Specify the name of the signature field 
       String fieldName = "SignatureField1"; 
      
       //Create a PKIOptions object that contains PKI run-time options 
       PKIOptions pkiOptions = new PKIOptions();  
       pkiOptions.setVerificationTime(VerificationTime.CURRENT_TIME); 
       pkiOptions.setRevocationCheckStyle(RevocationCheckStyle.BestEffort); 
      
       //Verify the digital signature 
       PDFSignatureVerificationInfo  signInfo = signClient.verify2( 
          inDoc, 
          fieldName, 
          pkiOptions, 
          null); 
  
       //Get the Signature Status 
       SignatureStatus sigStatus = signInfo.getStatus(); 
       String myStatus="";  
      
       //Determine the status of the signature 
       if (sigStatus == SignatureStatus.DynamicFormSignatureUnknown) 
              myStatus = "The signatures located in the dynamic PDF form are unknown"; 
          else if (sigStatus == SignatureStatus.DocumentSignatureUnknown) 
              myStatus = "The signatures located in the PDF document are unknown"; 
          else if (sigStatus == SignatureStatus.CertifiedDynamicFormSignatureTamper) 
              myStatus = "The signatures located in a certified PDF form are valid"; 
          else if (sigStatus == SignatureStatus.SignedDynamicFormSignatureTamper) 
              myStatus = "The signatures located in a signed dynamic PDF form are valid"; 
          else if (sigStatus == SignatureStatus.CertifiedDocumentSignatureTamper) 
              myStatus = "The signatures located in a certified PDF document are valid"; 
          else if (sigStatus == SignatureStatus.SignedDocumentSignatureTamper) 
              myStatus = "The signatures located in a signed PDF document are valid"; 
          else if (sigStatus == SignatureStatus.SignatureFormatError) 
              myStatus = "The format of a signature in a signed document is invalid"; 
          else if (sigStatus == SignatureStatus.DynamicFormSigNoChanges) 
              myStatus = "No changes were made to the signed dynamic PDF form"; 
          else if (sigStatus == SignatureStatus.DocumentSigNoChanges) 
              myStatus = "No changes were made to the signed PDF document"; 
          else if (sigStatus == SignatureStatus.DynamicFormCertificationSigNoChanges) 
              myStatus = "No changes were made to the certified dynamic PDF form"; 
          else if (sigStatus == SignatureStatus.DocumentCertificationSigNoChanges) 
              myStatus = "No changes were made to the certified PDF document"; 
          else if (sigStatus == SignatureStatus.DocSigWithChanges) 
              myStatus = "There were changes to a signed PDF document"; 
         else if (sigStatus == SignatureStatus.CertificationSigWithChanges) 
              myStatus = "There were changes made to the PDF document."; 
                
       //Get the signature type 
       SignatureType sigType = signInfo.getSignatureType(); 
       String myType = ""; 
          
       if (sigType.getType() == PDFSignatureType.AUTHORSIG) 
              myType="Certification"; 
       else if(sigType.getType() == PDFSignatureType.RECIPIENTSIG) 
              myType="Recipient"; 
      
       //Get the identity of the signer 
       IdentityInformation signerId = signInfo.getSigner(); 
       String signerMsg = ""; 
      
      if (signerId.getStatus() == IdentityStatus.UNKNOWN) 
          signerMsg = "Identity Unknown"; 
      else if (signerId.getStatus() == IdentityStatus.TRUSTED) 
          signerMsg = "Identity Trusted"; 
      else if (signerId.getStatus() == IdentityStatus.NOTTRUSTED) 
          signerMsg = "Identity Not Trusted"; 
               
      //Get the Signature properties returned by the Signature service 
      SignatureProperties sigProps = signInfo.getSignatureProps(); 
      String signerName =  sigProps.getSignerName(); 
      
     System.out.println("The status of the signature is: "+myStatus +". The signer identity is "+signerMsg +". The signature type is "+myType +". The name of the signer is "+signerName+"."); 
     } 
     catch (Exception ee) 
     { 
         ee.printStackTrace(); 
     } 
      } 
 } 
  
 
```

## 快速入門（SOAP模式）:使用Java API驗證多個數位簽名 {#quick-start-soap-mode-verifying-multiple-digital-signatures-using-the-java-api}

以下Java代碼示例驗證位於基於名為LoanAllSigs.pdf的PDF檔案的已簽名PDF文檔中的多個數字簽名。 將驗證時間設定為當前時間，並將吊銷檢查選項設定為最佳努力。 (請參閱 [驗證多個數字簽名](#unresolvedlink-lc-si).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-signatures-client.jar 
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
 import java.util.*; 
 import java.io.FileInputStream; 
 import com.adobe.livecycle.signatures.client.*; 
 import com.adobe.livecycle.signatures.client.types.*; 
 import com.adobe.livecycle.signatures.pki.client.types.common.RevocationCheckStyle; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class VerifyAllSignaturesSOAP{ 
  
     public static void main(String[] args) { 
          
     try 
     { 
       //Set connection properties required to invoke AEM Forms using SOAP mode                                 
       Properties connectionProps = new Properties(); 
       connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
      connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
       connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
       connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
       connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
          
       //Create a ServiceClientFactory instance 
       ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
       //Create a SignatureServiceClient object 
       SignatureServiceClient signClient = new SignatureServiceClient(myFactory); 
      
       //Specify a PDF document that contains multiple digital signatures 
       FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\LoanAllSigs.pdf");     
       Document inDoc = new Document (fileInputStream);  
      
       //Create a PKIOptions object that contains PKI run-time options 
       PKIOptions pkiOptions = new PKIOptions();  
       pkiOptions.setVerificationTime(VerificationTime.CURRENT_TIME); 
       pkiOptions.setRevocationCheckStyle(RevocationCheckStyle.BestEffort); 
      
       //Verify all digital signatures that are located in a PDF document 
       PDFDocumentVerificationInfo  allSig = signClient.verifyPDFDocument( 
          inDoc, 
          pkiOptions, 
          null); 
  
       //Get a list of all signatures that are located in the PDF document 
       List allSignatures = allSig.getVerificationInfos(); 
      
     //Create an Iterator object and iterate through  
     //the List object 
     Iterator<PDFSignatureVerificationInfo> iter = allSignatures.iterator();  
      
     while (iter.hasNext()) {  
            PDFSignatureVerificationInfo signInfo = (PDFSignatureVerificationInfo)iter.next();  
              
            //Get the Signature Status 
               SignatureStatus sigStatus = signInfo.getStatus(); 
               String myStatus="";  
              
             //Determine the status of the signature 
               if (sigStatus == SignatureStatus.DynamicFormSignatureUnknown) 
                   myStatus = "The signatures located in the dynamic PDF form are unknown"; 
               else if (sigStatus == SignatureStatus.DocumentSignatureUnknown) 
                   myStatus = "The signatures located in the PDF document are unknown"; 
               else if (sigStatus == SignatureStatus.CertifiedDynamicFormSignatureTamper) 
                   myStatus = "The signatures located in a certified PDF form are valid"; 
               else if (sigStatus == SignatureStatus.SignedDynamicFormSignatureTamper) 
                   myStatus = "The signatures located in a signed dynamic PDF form are valid"; 
               else if (sigStatus == SignatureStatus.CertifiedDocumentSignatureTamper) 
                   myStatus = "The signatures located in a certified PDF document are valid"; 
               else if (sigStatus == SignatureStatus.SignedDocumentSignatureTamper) 
                   myStatus = "The signatures located in a signed PDF document are valid"; 
               else if (sigStatus == SignatureStatus.SignatureFormatError) 
                   myStatus = "The format of a signature in a signed document is invalid"; 
               else if (sigStatus == SignatureStatus.DynamicFormSigNoChanges) 
                   myStatus = "No changes were made to the signed dynamic PDF form"; 
               else if (sigStatus == SignatureStatus.DocumentSigNoChanges) 
                   myStatus = "No changes were made to the signed PDF document"; 
               else if (sigStatus == SignatureStatus.DynamicFormCertificationSigNoChanges) 
                   myStatus = "No changes were made to the certified dynamic PDF form"; 
               else if (sigStatus == SignatureStatus.DocumentCertificationSigNoChanges) 
                   myStatus = "No changes were made to the certified PDF document"; 
               else if (sigStatus == SignatureStatus.DocSigWithChanges) 
                   myStatus = "There were changes to a signed PDF document"; 
              else if (sigStatus == SignatureStatus.CertificationSigWithChanges) 
                   myStatus = "There were changes made to the PDF document."; 
                   
               //Get the signature type 
              SignatureType sigType = signInfo.getSignatureType(); 
              String myType = ""; 
              
              if (sigType.getType() == PDFSignatureType.AUTHORSIG) 
                  myType="Certification"; 
              else if(sigType.getType() == PDFSignatureType.RECIPIENTSIG) 
                  myType="Recipient"; 
                           
              //Get the Signature properties returned by the Signature service 
              SignatureProperties sigProps = signInfo.getSignatureProps(); 
              String signerName =  sigProps.getSignerName(); 
              
             System.out.println("The status of the signature is: "+myStatus +". The signature type is "+myType +". The name of the signer is "+signerName+"."); 
         } 
     } 
     catch (Exception ee) 
     { 
         ee.printStackTrace(); 
     } 
      } 
 }
```

## 快速入門（SOAP模式）:使用Java API移除數位簽名 {#quick-start-soap-mode-removing-a-digital-signature-using-the-java-api}

以下Java代碼示例從名為的簽名欄位中刪除了數字簽名 *簽名欄位1*. 包含簽名欄位的PDF檔案的名稱為 *LoanSigned.pdf*. (請參閱 [移除數位簽名](/help/forms/developing/digitally-signing-certifying-documents.md#removing-digital-signatures).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-signatures-client.jar 
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
  
 import java.util.*; 
 import java.io.File; 
 import java.io.FileInputStream; 
 import com.adobe.livecycle.signatures.client.*; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
      
 public class ClearSignatureFieldSOAP { 
  
     public static void main(String[] args) { 
          
     try 
     { 
         //Set connection properties required to invoke AEM Forms using SOAP mode                                 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
          
         //Create a ServiceClientFactory instance 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
         //Create a SignatureServiceClient object 
         SignatureServiceClient signClient = new SignatureServiceClient(myFactory); 
          
         //Specify a PDF document that contains the signature to remove  
         FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\LoanSigned.pdf");     
         Document inDoc = new Document (fileInputStream); 
      
         //Specify the name of the signature field 
         String fieldName = "SignatureField1"; 
  
         //Clear the signature field 
         Document outPDF = signClient.clearSignatureField(inDoc,fieldName); 
  
         //Save the PDF document                     
         File outFile = new File("C:\\Adobe\Loan.pdf"); 
         outPDF.copyToFile(outFile); 
         } 
  
     catch (Exception ee) 
         { 
         ee.printStackTrace(); 
         } 
     } 
 } 
  
  
 
```

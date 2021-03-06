---
title: 條碼式Forms服務Java APIQ快速入門(SOAP)
seo-title: 條碼式Forms服務Java APIQ快速入門(SOAP)
description: 使用條碼式Forms服務，使用Java API快速入門將條碼式表單資料解碼。
seo-description: 使用條碼式Forms服務，使用Java API快速入門將條碼式表單資料解碼。
uuid: a6739695-ee0b-4480-8cef-0f91a72deaad
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 245b9cc4-5837-4a22-b5f4-a1d4c5d66918
role: Developer
exl-id: fbeefa4e-966d-43b5-ae59-9548fe520cc2
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# 條碼式Forms服務Java API快速入門(SOAP){#barcoded-forms-service-java-apiquick-start-soap}

Java API快速入門(SOAP)適用於條碼式Forms服務：

[快速入門（SOAP模式）:使用Java API解碼條碼式表單資料](barcoded-forms-service-java-api.md#quick-start-soap-mode-decoding-barcoded-form-data-using-the-java-api)

AEM Forms操作可使用AEM Forms強制類型API來執行，且連線模式應設為SOAP。

>[!NOTE]
>
>使用AEM Forms進行程式設計中的快速入門是以部署在JBoss Application Server和Microsoft Windows作業系統上的Forms Server為基礎。 但是，如果您使用其他作業系統（如UNIX），請用適用作業系統支援的路徑取代Windows專用路徑。 同樣，如果您正在使用其他J2EE應用程式伺服器，請確保指定有效的連接屬性。 請參閱[設定連線屬性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)。

## 快速入門（SOAP模式）:使用Java API {#quick-start-soap-mode-decoding-barcoded-form-data-using-the-java-api}解碼條碼式表單資料

以下Java代碼會解碼儲存為Loan.pdf的PDF表單中的表單資料。 解碼的資料被保存為名為extractedData.xml的XML檔案。 此代碼示例將`org.w3c.dom.Document`對象轉換為`com.adobe.idp.Document`對象。 （請參閱[解碼條碼表單資料](/help/forms/developing/barcoded-forms.md#decoding-barcoded-form-data)。）

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-barcodedforms-client.jar 
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
 import java.io.*; 
 import java.util.Iterator; 
 import java.util.List; 
 import java.util.Properties; 
 import javax.xml.transform.*; 
 import javax.xml.transform.dom.DOMSource; 
 import javax.xml.transform.stream.StreamResult; 
 import com.adobe.livecycle.barcodedforms.CharSet; 
 import com.adobe.livecycle.barcodedforms.Delimiter ; 
 import com.adobe.livecycle.barcodedforms.XMLFormat ;  
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.barcodedforms.client.*; 
  
 public class DecodeFormDataSOAP { 
  
     public static void main(String[] args) { 
          
     try 
         { 
         //Set connection properties required to invoke AEM Forms                                 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
         //Create a ServiceClientFactory object 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
         BarcodedFormsServiceClient barClient = new BarcodedFormsServiceClient(myFactory); 
                          
         //Specify a PDF document to convert to a XDP file 
         FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\LoanBarForms.pdf");     
         Document inDoc = new Document (fileInputStream); 
          
         java.lang.Boolean myFalse = new java.lang.Boolean(false); 
         java.lang.Boolean myTrue = new java.lang.Boolean(true); 
          
         //Decode barcoded form data 
         org.w3c.dom.Document decodeXML = barClient.decode( 
             inDoc, 
             myTrue, 
             myFalse, 
             myFalse, 
             myFalse, 
             myFalse, 
             myFalse, 
             myFalse, 
             myFalse, 
             CharSet.UTF_8); 
                                                  
         //Convert the decoded data to XDP data 
         List extractedData = barClient.extractToXML( 
             decodeXML,  
             Delimiter.Carriage_Return, 
             Delimiter.Tab, 
             XMLFormat.XDP); 
                  
         //Create an Iterator object and iterate through  
         //the List object 
         Iterator iter = extractedData.iterator();  
         int i = 0 ;  
              
         while (iter.hasNext()) {  
              
             //Get the org.w3c.dom.Document object in each element 
             org.w3c.dom.Document myDom = (org.w3c.dom.Document)iter.next();  
                  
             //Convert the org.w3c.dom.Document object to a  
             //com.adobe.idp.Document object 
             com.adobe.idp.Document myDocument = convertDOM(decodeXML); 
              
             //Save the XML data to extractedData.xml 
             File myFile = new File("C:\\Adobe\extractedData"+i+".xml"); 
              
             myDocument.copyToFile(myFile); 
             i++;  
             }     
         } 
     catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
  
  
     //This user-defined method converts an org.w3c.dom.Document to a  
     //com.adobe.idp.Document object 
     public static com.adobe.idp.Document convertDOM(org.w3c.dom.Document doc) 
         { 
              
             byte[] mybytes = null ; 
         com.adobe.idp.Document myDocument = null;  
         try 
             { 
  
             //Create a Java Transformer object 
          TransformerFactory transFact = TransformerFactory.newInstance(); 
          Transformer transForm = transFact.newTransformer(); 
      
          //Create a Java ByteArrayOutputStream object 
          ByteArrayOutputStream myOutStream = new ByteArrayOutputStream(); 
  
         //Create a Java Source object 
          Source myInput = new DOMSource(doc); 
  
         //Create a Java Result object 
          Result myOutput = new StreamResult(myOutStream); 
      
         //Populate the Java ByteArrayOutputStream object 
          transForm.transform(myInput,myOutput); 
  
         //Get the size of the ByteArrayOutputStream buffer 
          int myByteSize = myOutStream.size(); 
  
         //Allocate myByteSize to the byte array 
         mybytes = new byte[myByteSize]; 
  
         //Copy the content to the byte array 
         mybytes = myOutStream.toByteArray();  
         com.adobe.idp.Document myDoc = new com.adobe.idp.Document(mybytes); 
      
          myDocument = myDoc ;  
          } 
              
         catch(Exception ee) 
         { 
             ee.printStackTrace(); 
         } 
              
     return myDocument;     
       } 
 }
```

>[!NOTE]
>
>在相同的應用程式邏輯中同時使用`org.w3c.dom.Document`對象和`com.adobe.idp.Document`對象時，完全限定這兩個對象是一種好做法。

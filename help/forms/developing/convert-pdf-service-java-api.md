---
title: 轉換PDF服務Java API快速入門(SOAP)
seo-title: Convert PDF Service Java API QuickStart(SOAP)
description: 使用「轉換PDF服務Java API」將PDF檔案轉換為PostScript和JPEG檔案。
seo-description: Use the Convert PDF service Java API to convert a PDF document to PostScript and JPEG files.
uuid: 97253ac7-f0c1-4766-a7bd-c19af52adf51
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: bdd9bb56-14f6-448b-be4a-7c11f670e901
role: Developer
exl-id: af0cb623-c29c-4b9e-9ffd-736047a45b8d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 1%

---

# 轉換PDF服務Java API快速入門(SOAP) {#convert-pdf-service-java-api-quickstart-soap}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

轉換PDF服務API提供下列快速入門。

[快速入門（SOAP模式）:使用Java API將PDF檔案轉換為PostScript](convert-pdf-service-java-api.md#quick-start-soap-mode-converting-a-pdf-document-to-postscript-using-the-java-api)

[快速入門（SOAP模式）:使用Java API將PDF檔案轉換為JPEG檔案](convert-pdf-service-java-api.md#quick-start-soap-mode-converting-a-pdf-document-to-jpeg-files-using-the-java-api)

AEM Forms操作可使用AEM Forms強制類型API來執行，且連線模式應設為SOAP。

>[!NOTE]
>
>使用AEM表單進行程式設計中的快速入門是以部署在JBoss Application Server和Microsoft Windows作業系統上的Forms Server為基礎。 但是，如果您使用其他作業系統（如UNIX），請用適用作業系統支援的路徑取代Windows專用路徑。 同樣，如果您正在使用其他J2EE應用程式伺服器，請確保指定有效的連接屬性。 請參閱 [設定連接屬性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## 快速入門（SOAP模式）:使用Java API將PDF檔案轉換為PostScript {#quick-start-soap-mode-converting-a-pdf-document-to-postscript-using-the-java-api}

以下代碼示例轉換了名為的PDF文檔 *Loan.pdf* 填入名為 *Loan.ps*. (請參閱 [將PDF文檔轉換為PostScript](/help/forms/developing/converting-pdf-postscript-image-files.md#converting-pdf-documents-to-postscript).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-convertpdf-client.jar 
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
 import java.io.File; 
 import java.io.FileInputStream; 
 import java.util.Properties; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.convertpdfservice.client.ConvertPdfServiceClient; 
 import com.adobe.livecycle.convertpdfservice.client.ToPSOptionsSpec; 
 import com.adobe.livecycle.convertpdfservice.client.enumeration.Color; 
 import com.adobe.livecycle.convertpdfservice.client.enumeration.LineWeight; 
 import com.adobe.livecycle.convertpdfservice.client.enumeration.PSLevel; 
 import com.adobe.livecycle.convertpdfservice.client.enumeration.PageSize; 
 import com.adobe.livecycle.convertpdfservice.client.enumeration.Color; 
  
 public class JavaAPIConvertPDFtoPSSOAP 
 { 
     public static void main(String[] args) 
     { 
     try 
         { 
         //Set connection properties required to invoke AEM Forms using SOAP mode                                 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
         //Create a ServiceClientFactory object 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
          
         //Create a ConvertPdfServiceClient object 
         ConvertPdfServiceClient convertPDFClient= new ConvertPdfServiceClient(myFactory); 
  
         //Get a PDF file document to convert to a PS document  
         //and populate a com.adobe.idp.Document object 
         String inputFileName = "C:\\Adobe\Loan.pdf"; 
         FileInputStream fileInputStream = new FileInputStream(inputFileName); 
         Document inDoc = new Document(fileInputStream); 
          
         //Create a ToPSOptionsSpec object that defines run-time options 
         ToPSOptionsSpec psSpec = new ToPSOptionsSpec();  
         psSpec.setPsLevel(PSLevel.LEVEL_3); 
         psSpec.setShrinkToFit(true); 
         psSpec.setPageSize(PageSize.A4); 
         psSpec.setRotateAndCenter(true); 
         psSpec.setColor(Color.compositeGray); 
         psSpec.setLineWeight(LineWeight.point25); 
          
         //Convert the PDF document to a PostScript file 
         Document createdDocument =convertPDFClient.toPS2( 
             inDoc, 
             psSpec 
             ); 
  
         //Save the PostScript file 
         createdDocument.copyToFile(new File("C:\\Adobe\Loan.ps")); 
         } 
     catch (Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 }
```

## 快速入門（SOAP模式）:使用Java API將PDF檔案轉換為JPEG檔案 {#quick-start-soap-mode-converting-a-pdf-document-to-jpeg-files-using-the-java-api}

以下Java代碼示例將轉換名為的PDF文檔 *Loan.pdf* 儲存到一組JPEG檔案，並將其儲存在C:\Adobe directory中。 每個檔案的名稱都是 *tempFile[索引].jpg*，其中會命名第一個影像檔案 *tempFile0.jpg*. (請參閱 [將PDF文檔轉換為影像格式](/help/forms/developing/converting-pdf-postscript-image-files.md#converting-pdf-documents-to-image-formats).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-convertpdf-client.jar 
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
 import java.io.File; 
 import java.io.FileInputStream; 
 import java.util.Iterator; 
 import java.util.List; 
 import java.util.Properties; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.convertpdfservice.client.ConvertPdfServiceClient; 
 import com.adobe.livecycle.convertpdfservice.client.ToImageOptionsSpec; 
 import com.adobe.livecycle.convertpdfservice.client.enumeration.CMYKPolicy; 
 import com.adobe.livecycle.convertpdfservice.client.enumeration.ColorCompression; 
 import com.adobe.livecycle.convertpdfservice.client.enumeration.ColorSpace; 
 import com.adobe.livecycle.convertpdfservice.client.enumeration.GrayScaleCompression; 
 import com.adobe.livecycle.convertpdfservice.client.enumeration.GrayScalePolicy; 
 import com.adobe.livecycle.convertpdfservice.client.enumeration.ImageConvertFormat; 
 import com.adobe.livecycle.convertpdfservice.client.enumeration.Interlace; 
 import com.adobe.livecycle.convertpdfservice.client.enumeration.JPEGFormat; 
 import com.adobe.livecycle.convertpdfservice.client.enumeration.MonochromeCompression; 
 import com.adobe.livecycle.convertpdfservice.client.enumeration.PNGFilter; 
 import com.adobe.livecycle.convertpdfservice.client.enumeration.RGBPolicy; 
  
 public class JavaAPIConvertPDFtoImageSOAP { 
  
     public static void main(String[] args) 
     { 
     try 
     { 
         //Set connection properties required to invoke AEM Forms using SOAP mode                                 
         Properties connectionProps = new Properties(); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
         //Create a ServiceClientFactory object 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
         //Create the ConvertPDF service client 
         ConvertPdfServiceClient serviceClient = new ConvertPdfServiceClient(myFactory); 
          
         //Get a PDF file document to convert to a JPEG document and populate a com.adobe.idp.Document object 
         String inputFileName = "C:\\Adobe\Loan.pdf"; 
         FileInputStream fileInputStream = new FileInputStream(inputFileName); 
         Document inDoc = new Document(fileInputStream); 
  
         // Set up the runtime options for the new JPEG file to be created 
         ToImageOptionsSpec spec = new ToImageOptionsSpec(); 
         spec.setImageConvertFormat(ImageConvertFormat.JPEG); 
         spec.setGrayScaleCompression(GrayScaleCompression.Low); 
         spec.setColorCompression(ColorCompression.Low); 
         spec.setFormat(JPEGFormat.BaselineOptimized); 
         spec.setRgbPolicy(RGBPolicy.Off); 
         spec.setCmykPolicy(CMYKPolicy.Off); 
         spec.setColorSpace(ColorSpace.RGB); 
         spec.setResolution("72"); 
         spec.setMonochrome(MonochromeCompression.None); 
         spec.setFilter(PNGFilter.Sub); 
         spec.setInterlace(Interlace.Adam7); 
         spec.setTileSize(180); 
         spec.setGrayScalePolicy(GrayScalePolicy.Off); 
          
         //Perform the conversion and get the containing the newly created JPEG files 
         List allImages = serviceClient.toImage2( 
             inDoc, 
             spec 
         ); 
          
         //Create an Iterator object and iterate through  
         //the List object to get all images 
         Iterator iter = allImages.iterator();  
         int i = 0 ;  
         while (iter.hasNext()) {  
             Document file = (Document)iter.next();  
             file.copyToFile(new File("C:\\Adobe\tempFile"+i+".jpg")); 
             i++;  
         } 
     } 
     catch (Exception e) { 
         e.printStackTrace(); 
         } 
     } 
 }
```

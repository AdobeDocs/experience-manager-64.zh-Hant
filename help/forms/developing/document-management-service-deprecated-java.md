---
title: 文檔管理服務（已過時）Java API快速入門(SOAP)
seo-title: Document Management Service (Deprecated)Java API Quick Start(SOAP)
description: 使用Document Management Service Java API建立Content Services空間、刪除Content Services空間、向Content Services添加內容、從Content Services中檢索內容、移動Content Services內容、列出Content Services內容、搜索Content Services內容，以及設定Content Services權限。
seo-description: Use the Document Management Service Java API to create Content Services spaces, delete Content Services spaces, Add content to Content Services, retrieve content from Content Services, move Content Services content, list Content Services content, search Content Services content, and set Content Services permissions.
uuid: 967c282a-ccde-4489-a4d5-53c6a1a0cac0
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 9cffdb77-c8a4-4a15-b64f-1d3aadaa60c7
role: Developer
exl-id: 5ffd9600-03ec-4fd5-abb1-a8d9adefe6f3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---

# 檔案管理服務（已過時）Java API快速入門(SOAP) {#document-management-service-deprecated-java-api-quick-start-soap}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

文檔管理服務（已過時）提供以下快速入門。

>[!NOTE]
>
>自2011年8月5日起，Adobe將內容服務ES客戶移轉至Adobe Digital Enterprise Platform Experience Services。 使用內容服務的客戶的產品藍圖是改用新的ADEP Experience Services - Core，其中包括以現代化模組化CRX架構為基礎的原生內容存放庫，此架構是在Adobe收購Day Software時購買的。

[快速入門（SOAP模式）:使用Java API建立內容服務空間](document-management-service-deprecated-java.md#quick-start-soap-mode-create-content-services-spaces-using-the-java-api-deprecated)

[快速入門（SOAP模式）:使用Java API刪除內容服務內容](document-management-service-deprecated-java.md#quick-start-soap-mode-delete-content-services-content-using-the-java-api-deprecated)

[快速入門（SOAP模式）:使用Java API將內容新增至內容服務](document-management-service-deprecated-java.md#quick-start-soap-mode-add-content-to-content-services-using-the-java-api-deprecated)

[快速入門（SOAP模式）:使用Java API從「內容服務」擷取內容](document-management-service-deprecated-java.md#quick-start-soap-mode-retrieve-content-from-content-services-using-the-java-api-deprecated)

[快速入門（SOAP模式）:使用Java API移動內容服務內容](document-management-service-deprecated-java.md#quick-start-soap-mode-move-content-services-content-using-the-java-api-deprecated)

[快速入門（SOAP模式）:使用Java API列出內容服務內容](document-management-service-deprecated-java.md#quick-start-soap-mode-list-content-services-content-using-the-java-api-deprecated)

[快速入門（SOAP模式）:使用Java API搜尋內容服務內容](document-management-service-deprecated-java.md#quick-start-soap-mode-search-content-services-content-using-the-java-api-deprecated)

[快速入門（SOAP模式）:使用Java API設定內容服務權限](document-management-service-deprecated-java.md#quick-start-soap-mode-setting-content-services-permissions-using-the-java-api-deprecated)

AEM Forms操作可使用AEM Forms強制類型API來執行，且連線模式應設為SOAP。

>[!NOTE]
>
>使用AEM表單進行程式設計中的快速入門是以部署在JBoss和Windows作業系統上的Forms伺服器為基礎。 但是，如果您使用其他作業系統（如UNIX），則用適用作業系統支援的路徑替換特定於windows的路徑。 同樣，如果您正在使用其他J2EE應用程式伺服器，請確保指定有效的連接屬性。 請參閱 [設定連接屬性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## 快速入門（SOAP模式）:使用Java API建立內容服務空間（已過時） {#quick-start-soap-mode-create-content-services-spaces-using-the-java-api-deprecated}

以下Java代碼示例在公司首頁中建立名為*測試目錄*的新空間。 新空間的標識值寫入控制台。

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-contentservices-client.jar 
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
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl; 
  
 public class CreateNewSpaceSoap { 
  
     public static void main(String[] args) { 
          
         try{ 
          
             //Set connection properties required to invoke AEM Forms using SOAP mode                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             //Create a DocumentManagementServiceClientImpl object 
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory);  
              
             //Specify the name of the store and node 
             String storeName ="SpacesStore";  
             String nodeName = "/Company Home/Test Directory" ; 
                                  
             //Create a new space 
             String spaceId = docManager.createSpace(storeName,nodeName); 
             System.out.println("The identifier value of the new space is " +spaceId); 
         } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
 
```

## 快速入門（SOAP模式）:使用Java API刪除內容服務內容（已過時） {#quick-start-soap-mode-delete-content-services-content-using-the-java-api-deprecated}

以下Java代碼示例刪除名為/Company Home/Test Directory的空格。

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-contentservices-client.jar 
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
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl; 
  
 public class DeleteContentSoap { 
  
     public static void main(String[] args) { 
          
         try{ 
          
             //Set connection properties required to invoke AEM Forms using SOAP mode                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             //Create a DocumentManagementServiceClientImpl object 
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory);  
              
             //Specify the name of the store and node 
             String storeName ="SpacesStore";  
             String nodeName = "/Company Home/Test Directory" ; 
              
             //Delete the content from /Company Home/Test Directory 
             Boolean ans = docManager.deleteContent(storeName, nodeName); 
              
             if (ans == true) 
                 System.out.println("The content was successfully deleted"); 
             else 
                 System.out.println("The content was not deleted"); 
             } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
 
```

## 快速入門（SOAP模式）:使用Java API將內容新增至內容服務（已過時） {#quick-start-soap-mode-add-content-to-content-services-using-the-java-api-deprecated}

下列Java程式碼範例會新增一個名為 *MortgageForm.pdf* 到名為/Company Home/Test Directory的資料夾。 已設定建立者和說明屬性。 將新內容的標識值寫入控制台。

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-contentservices-client.jar 
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
 import java.util.*; 
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.contentservices.client.CRCResult; 
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl; 
 import com.adobe.livecycle.contentservices.client.impl.UpdateVersionType; 
  
 public class AddContentSoap { 
  
     public static void main(String[] args) { 
          
         try{ 
          
             //Set connection properties required to invoke AEM Forms using SOAP mode                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             //Create a DocumentManagementServiceClientImpl object 
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory); 
              
             //Specify the store and node name 
             String storeName ="SpacesStore";  
             String nodeName = "/Company Home/Test Directory" ; 
              
             //Retrieve the document to store in /Company Home/Test Directory 
             Document content =  new Document(new File("C:\\Adobe\MortgageForm.pdf"), false); 
              
             //Create a MAP instance to store attributes 
             Map<String,Object> inputs = new HashMap<String,Object>(); 
              
             //Specify attributes that belong to the new content 
             String creator = "{https://www.alfresco.org/model/content/1.0}creator"; 
             String description = "{https://www.alfresco.org/model/content/1.0}description";  
              
             inputs.put(creator,"Tony Blue"); 
             inputs.put(description,"A mortgage application form"); 
                                  
             //Store MortgageForm.pdf in /Company Home/Test Directory 
             CRCResult result = docManager.storeContent(storeName,  
                      nodeName, 
                     "MortgageForm.pdf", 
                     "{https://www.alfresco.org/model/content/1.0}content",  
                     content, 
                     "UTF-8", 
                     UpdateVersionType.INCREMENT_MAJOR_VERSION, 
                     null, 
                     inputs);  
              
             //Get the identifier value of the new content 
             String id = result.getNodeUuid(); 
             System.out.println("The identifier value of the new content is "+id); 
     } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
 
```

## 快速入門（SOAP模式）:使用Java API從內容服務擷取內容（已過時） {#quick-start-soap-mode-retrieve-content-from-content-services-using-the-java-api-deprecated}

下列Java程式碼範例會擷取一個名為 *MortgageForm.pdf* 從/公司首頁。 PDF檔案將保存到本地檔案系統，並命名為 *更新的MortgageForm.pdf*.

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-contentservices-client.jar 
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
 import java.util.*; 
  
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.contentservices.client.CRCResult; 
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl; 
  
 public class RetrieveContentSoap { 
  
     public static void main(String[] args) { 
          
         try{ 
             //Set connection properties required to invoke AEM Forms using SOAP mode                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             //Create a DocumentManagementServiceClientImpl object 
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory);  
              
             //Specify the name of the store and the content to retrieve 
                String storeName = "SpacesStore"; 
                String nodeName  = "/Company Home/MortgageForm.pdf"; 
  
                //Retrieve /Company Home/MortgageForm.pdf 
                CRCResult content = docManager.retrieveContent( 
                      storeName, 
                      nodeName, 
                      ""); 
      
                //Write the PDF file to the local file system 
                File myFile = new File("C:\\Adobe\UpdatedMortgageForm.pdf"); 
                Document doc =content.getDocument();  
                doc.copyToFile(myFile); 
          } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
  
 
```

## 快速入門（SOAP模式）:使用Java API移動內容服務內容（已過時） {#quick-start-soap-mode-move-content-services-content-using-the-java-api-deprecated}

下列Java程式碼範例會移動名為 *MortgageForm.pdf* 從/Company Home/Test Directory到/Company Home。 移動內容的標識值被寫入控制台。

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-contentservices-client.jar 
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
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl; 
  
 public class MoveContentSoap { 
  
     public static void main(String[] args) { 
          
         try{ 
          
             //Set connection properties required to invoke AEM Forms using SOAP mode                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
  
             //Create a DocumentManagementServiceClientImpl object 
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory);  
              
             //Specify the name of the store and the content to move 
                String storeName = "SpacesStore"; 
                String nodeName = "/Company Home/Test Directory/MortgageForm.pdf"; 
                String newSpace = "/Company Home"; 
  
                //Move the content from /Company Home/Test Directory 
                //to /Company Home and display the identifier value of the  
                //moved content 
                String contentID = docManager.moveContent(storeName, nodeName, newSpace); 
                System.out.println("The identifier value of the moved content is "+contentID); 
         } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
  
 
```

## 快速入門（SOAP模式）:使用Java API列出內容服務內容（已過時） {#quick-start-soap-mode-list-content-services-content-using-the-java-api-deprecated}

下面的Java代碼示例列出了位於/Company Home中的內容。 將顯示每個節點類型和節點名稱。

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-contentservices-client.jar 
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
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.contentservices.client.CRCResult; 
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl; 
  
 public class ListingContentSoap { 
  
     public static void main(String[] args) { 
          
         try{ 
          
             //Set connection properties required to invoke AEM Forms using SOAP mode                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             //Create a DocumentManagementServiceClientImpl object 
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory);  
              
             //Specify the name of the store and the space 
                String storeName = "SpacesStore"; 
                String nodeName  = "/Company Home"; 
  
               //List the contents of /Company Home 
               List<CRCResult> allImages = docManager.getSpaceContents( 
                      storeName, 
                      nodeName, 
                      false); 
               
              //Create an Iterator object and iterate through  
              //the List object 
              Iterator iter = allImages.iterator();  
              int i = 0 ;  
              while (iter.hasNext()) {  
                                
                  //Get the node content type and name  
                  CRCResult sinContent = (CRCResult)iter.next();  
                  String nodeType =  sinContent.getNodeType(); 
                  String name = sinContent.getNodeName(); 
                  System.out.println("The node type is "+nodeType  +". The node name is "+name);   
              } 
         } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
  
 
```

## 快速入門（SOAP模式）:使用Java API搜尋內容服務內容（已過時） {#quick-start-soap-mode-search-content-services-content-using-the-java-api-deprecated}

以下Java代碼將搜索/公司首頁，以查找包含MortgageForm文本的文檔。 也會搜尋子資料夾。

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-contentservices-client.jar 
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
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.contentservices.client.ResultSet; 
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl; 
 import com.adobe.livecycle.contentservices.client.impl.QueryImpl; 
 import com.adobe.livecycle.contentservices.client.impl.StatementImpl; 
  
 public class SearchSpaceSoap { 
  
     public static void main(String[] args) { 
          
         try{ 
             //Set connection properties required to invoke AEM Forms using SOAP mode                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             //Create a DocumentManagementServiceClientImpl object 
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory);  
              
             //Specify the name of the store and node 
             String path ="/Company Home";  
              String storeName = "SpacesStore"; 
              
             //Create a Query expression 
             QueryImpl qImpl = new QueryImpl(); 
             String myName = "{https://www.alfresco.org/model/content/1.0}name"; 
             StatementImpl statement = new StatementImpl(myName, StatementImpl.OPERATOR_CONTAINS, "MortgageForm" ); 
             qImpl.addStatement(statement);  
          
             //Perform the search for a document that contains the text MortgageForm 
             ResultSet rs = docManager.searchRepository(storeName, path, true, qImpl, 200); 
             long resultSize = rs.getResultSize();  
              
             //Determine if the document is located in Content space 
             if (resultSize > 0) 
             { 
                 System.out.println("MortgageForm is located in the Repository"); 
             } 
         } 
     catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
  
 
```

## 快速入門（SOAP模式）:使用Java API設定內容服務權限（已過時） {#quick-start-soap-mode-setting-content-services-permissions-using-the-java-api-deprecated}

以下Java代碼示例設定名為tony blue的用戶的權限。 指定的域是預設域。 已指定Consumer權限，且節點為 `/Company Home/Test Directory`.

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-contentservices-client.jar 
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
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl; 
 import com.adobe.livecycle.contentservices.client.impl.ContentAccessPermission; 
  
 public class SetPermissionsSoap { 
  
     public static void main(String[] args) { 
          
         try{ 
          
             //Set connection properties required to invoke AEM Forms using SOAP mode     
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             //Create a DocumentManagementServiceClientImpl object 
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory); 
              
             //Specify the store and node name 
             String storeName ="SpacesStore";  
             String nodeName = "/Company Home/Test Directory/"; 
              
              //Create a new permission 
             ContentAccessPermission permission = new ContentAccessPermission(); 
             permission.setAuthority("tblue/DefaultDom");  
             permission.setIsAllowed(false); 
             permission.setPermission("Consumer"); 
              
             //Create a collection to hold the values 
             List<ContentAccessPermission> permissionList = new ArrayList<ContentAccessPermission>(); 
             permissionList.add(0,permission); 
                          
             //Set the permission 
             docManager.writePermissions(storeName,  
                      nodeName, 
                      permissionList, 
                     false);  
     } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
 
```

## 快速入門（SOAP模式）:使用Java API建立關聯（已廢止） {#quick-start-soap-mode-creating-associations-using-the-java-api-deprecated}

以下Java代碼將建立XML資料檔案和PDF表單的關聯。 此類型的關聯名為LinkedBy。PDF文檔必須應用可連結的方面。

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-contentservices-client.jar 
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
  
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl; 
  
 public class CreateAssociationsSoap { 
  
     public static void main(String[] args) { 
          
         try{ 
          
             //Set connection properties required to invoke AEM Forms using SOAP mode                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                          
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             //Create a DocumentManagementServiceClientImpl object 
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory); 
              
             //Specify the input values  
             String storeName ="SpacesStore"; 
             String associationType = "{https://www.adobe.com/lc/datacapture/1.0}linkedBy"; 
             String aspect = "{https://www.adobe.com/lc/datacapture/1.0}linkable"; 
             String parentPath= "/Company Home/MortgageForm.pdf"; 
             String childPath= "/Company Home/Loan.xml"; 
                      
             //Set the linkable aspect to MortgageForm.pdf 
             List<String> aspectList = new ArrayList(); 
             aspectList.add(aspect); 
              
             //Create an attribute map 
             Map<String,Object> inputs = new HashMap<String,Object>(); 
              
             //Specify attributes that belong to the new content 
             String creator = "{https://www.alfresco.org/model/content/1.0}creator"; 
             String description = "{https://www.alfresco.org/model/content/1.0}description";  
              
             inputs.put(creator,"Tony Blue"); 
             inputs.put(description,"Link the PDF document to loan data"); 
              
             //Set the aspects 
             docManager.setContentAttributes(storeName,parentPath,aspectList,inputs); 
  
             //Create an association between MortgageForm.pdf and Loan.xml  
             docManager.createAssociation(storeName,  
                     associationType, 
                     parentPath, 
                     childPath);  
         } 
              
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 
```

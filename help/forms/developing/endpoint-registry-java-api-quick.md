---
title: 端點註冊表Java API快速入門(SOAP)
seo-title: Endpoint Registry Java API QuickStart(SOAP)
description: 使用Endpoint Registry Java API添加EJB端點、添加SOAP端點、添加Watched資料夾端點、添加Email端點、添加遠程端點、添加TaskManager端點、修改端點、刪除端點以及檢索端點連接器資訊。
seo-description: Use the Endpoint Registry Java API to add an EJB endpoint, add a SOAP endpoint, add a Watched folder endpoint, add an Email endpoint, add a remoting endpoint, add a TaskManager endpoint, modify an endpoint, remove an endpoint, and retrieve endpoint connector information.
uuid: 986c55d0-e199-46f8-a3cc-a6baf5cce316
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: e5989859-e58d-4049-9e0d-c4c848d597af
role: Developer
exl-id: 70816a79-a200-4afa-8602-bf3c414665ea
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# 端點註冊表Java API快速入門(SOAP) {#endpoint-registry-java-api-quickstart-soap}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Endpoint Registry可使用Java API快速入門(SOAP)。

[快速入門：使用Java API添加EJB端點](endpoint-registry-java-api-quick.md#quickstart-adding-an-ejb-endpoint-using-the-java-api)

[快速入門：使用Java API添加SOAP端點](endpoint-registry-java-api-quick.md#quickstart-adding-a-soap-endpoint-using-the-java-api)

[快速入門：使用Java API新增「監看資料夾」端點](endpoint-registry-java-api-quick.md#quickstart-adding-a-watched-folder-endpoint-using-the-java-api)

[快速入門：使用Java API新增電子郵件端點](endpoint-registry-java-api-quick.md#quickstart-adding-an-email-endpoint-using-the-java-api)

[快速入門：使用Java API新增遠端端點](endpoint-registry-java-api-quick.md#quickstart-adding-a-remoting-endpoint-using-the-java-api)

[快速入門：使用Java API添加TaskManager終結點](endpoint-registry-java-api-quick.md#quickstart-adding-a-taskmanager-endpoint-using-the-java-api)

[快速入門：使用Java API修改端點](endpoint-registry-java-api-quick.md#quickstart-modifying-an-endpoint-using-the-java-api)

[快速入門：使用Java API移除端點](endpoint-registry-java-api-quick.md#quickstart-removing-an-endpoint-using-the-java-api)

[快速入門：使用Java API擷取端點連接器資訊](endpoint-registry-java-api-quick.md#quickstart-retrieving-endpoint-connector-information-using-the-java-api)

AEM Forms操作可使用AEM Forms強制類型API來執行，且連線模式應設為SOAP。

>[!NOTE]
>
>使用AEM表單進行程式設計中的快速入門是以Forms為基礎（如果您使用其他作業系統，例如Unix），請以適用作業系統支援的路徑取代windows特定路徑。 同樣，如果您正在使用其他J2EE應用程式伺服器，請確保指定有效的連接屬性。 請參閱 [設定連接屬性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

>[!NOTE]
>
>無法使用Web服務來使用端點。

## 快速入門：使用Java API添加EJB端點 {#quickstart-adding-an-ejb-endpoint-using-the-java-api}

以下Java代碼示例將EJB端點添加到名為的服務 *MyApplication/EncryptDocument*. (請參閱 [添加EJB終結點](/help/forms/developing/programmatically-endpoints.md#adding-ejb-endpoints).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-livecycle-client.jar 
     * 2. adobe-usermanager-client.jar 
     * 3. activation.jar (required for SOAP mode) 
     * 4. axis.jar (required for SOAP mode) 
     * 5. commons-codec-1.3.jar (required for SOAP mode) 
     * 6. commons-collections-3.2.jar  (required for SOAP mode) 
     * 7. commons-discovery.jar (required for SOAP mode) 
     * 8. commons-logging.jar (required for SOAP mode) 
     * 9. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 10. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 11. jaxrpc.jar (required for SOAP mode) 
     * 12. log4j.jar (required for SOAP mode) 
     * 13. mail.jar (required for SOAP mode) 
     * 14. saaj.jar (required for SOAP mode) 
     * 15. wsdl4j.jar (required for SOAP mode) 
     * 16. xalan.jar (required for SOAP mode) 
     * 17. xbean.jar (required for SOAP mode) 
     * 18. xercesImpl.jar (required for SOAP mode) 
     * 
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     * 
     * For complete details about the location of the AEM Forms JAR files,  
     * see "Including AEM Forms Java library files" in Programming  
     * with AEM Forms 
     */ 
 import java.util.Properties; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.idp.dsc.registry.endpoint.CreateEndpointInfo; 
 import com.adobe.idp.dsc.registry.endpoint.client.EndpointRegistryClient; 
 import com.adobe.idp.dsc.registry.infomodel.Endpoint; 
  
 public class AddEJBEndPoint { 
      
     public static void main(String[] args) { 
          
     try{ 
         //Set connection properties    required to invoke AEM Forms 
         Properties ConnectionProps = new Properties(); 
          
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                      
         //Create a ServiceClientFactory object 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(ConnectionProps); 
  
         //Create an EndpointRegistryClient object 
         EndpointRegistryClient endPointClient = new EndpointRegistryClient(myFactory); 
          
         //Create an SOAP endpoint for the MyApplication/EncryptDocument process 
         CreateEndpointInfo e = new CreateEndpointInfo(); 
         e.setConnectorId("EJB"); 
         e.setDescription("EJB endpoint for the MyApplication/EncryptDocument proces"); 
         e.setName("MyApplication/EncryptDocument"); 
         e.setServiceId("MyApplication/EncryptDocument"); 
         e.setOperationName("*"); 
         Endpoint endPoint = endPointClient.createEndpoint(e); 
          
         //Enable the SOAP Endpoint     
         endPointClient.enable(endPoint); 
          
     }catch (Exception e) { 
          e.printStackTrace(); 
         }     
  
     } 
 } 
 
```

## 快速入門：使用Java API添加SOAP端點 {#quickstart-adding-a-soap-endpoint-using-the-java-api}

以下Java代碼示例將SOAP端點添加到名為 *MyApplication/EncryptDocument*. (請參閱 [添加SOAP端點](/help/forms/developing/programmatically-endpoints.md#adding-soap-endpoints).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-livecycle-client.jar 
     * 2. adobe-usermanager-client.jar 
     * 3. activation.jar (required for SOAP mode) 
     * 4. axis.jar (required for SOAP mode) 
     * 5. commons-codec-1.3.jar (required for SOAP mode) 
     * 6. commons-collections-3.2.jar  (required for SOAP mode) 
     * 7. commons-discovery.jar (required for SOAP mode) 
     * 8. commons-logging.jar (required for SOAP mode) 
     * 9. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 10. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 11. jaxrpc.jar (required for SOAP mode) 
     * 12. log4j.jar (required for SOAP mode) 
     * 13. mail.jar (required for SOAP mode) 
     * 14. saaj.jar (required for SOAP mode) 
     * 15. wsdl4j.jar (required for SOAP mode) 
     * 16. xalan.jar (required for SOAP mode) 
     * 17. xbean.jar (required for SOAP mode) 
     * 18. xercesImpl.jar (required for SOAP mode) 
     * 
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     * 
     * For complete details about the location of the AEM Forms JAR files,  
     * see "Including AEM Forms Java library files" in Programming  
     * with AEM Forms 
     */ 
 import java.util.Properties; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.idp.dsc.registry.endpoint.CreateEndpointInfo; 
 import com.adobe.idp.dsc.registry.endpoint.client.EndpointRegistryClient; 
 import com.adobe.idp.dsc.registry.infomodel.Endpoint; 
  
  
 public class AddSoapEndPoint { 
      
     public static void main(String[] args) { 
          
     try{ 
         //Set connection properties    required to invoke AEM Forms 
         Properties ConnectionProps = new Properties(); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
          
         //Create a ServiceClientFactory object 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(ConnectionProps); 
  
         //Create an EndpointRegistryClient object 
         EndpointRegistryClient endPointClient = new EndpointRegistryClient(myFactory); 
          
         //Create a SOAP Endpoint for the MortgageLoan - Prebuilt process 
         CreateEndpointInfo e = new CreateEndpointInfo(); 
         e.setConnectorId("SOAP"); 
         e.setDescription("SOAP endpoint for the MyApplication/EncryptDocument proces"); 
         e.setName("MyApplication/EncryptDocument"); 
         e.setServiceId("MyApplication/EncryptDocument"); 
         e.setOperationName("*"); 
         Endpoint endPoint = endPointClient.createEndpoint(e); 
          
         //Enable the SOAP Endpoint     
         endPointClient.enable(endPoint); 
          
          
     }catch (Exception e) { 
          e.printStackTrace(); 
         }     
  
     } 
 } 
 
```

## 快速入門：使用Java API新增「監看資料夾」端點 {#quickstart-adding-a-watched-folder-endpoint-using-the-java-api}

以下Java代碼示例將「監看資料夾」端點添加到名為 *MyApplication/EncryptDocument*. (請參閱 [添加監視的資料夾端點](/help/forms/developing/programmatically-endpoints.md#adding-watched-folder-endpoints).)

>[!NOTE]
>
>您必須在專案中包含WatchedFolderEndpointConfigConstants.java檔案，才能編譯並執行下列快速入門。 (請參閱 [監看的資料夾配置值常數檔案](/help/forms/developing/programmatically-endpoints.md#watched-folder-configuration-values-constant-file).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-livecycle-client.jar 
     * 2. adobe-usermanager-client.jar 
     * 3. activation.jar (required for SOAP mode) 
     * 4. axis.jar (required for SOAP mode) 
     * 5. commons-codec-1.3.jar (required for SOAP mode) 
     * 6. commons-collections-3.2.jar  (required for SOAP mode) 
     * 7. commons-discovery.jar (required for SOAP mode) 
     * 8. commons-logging.jar (required for SOAP mode) 
     * 9. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 10. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 11. jaxrpc.jar (required for SOAP mode) 
     * 12. log4j.jar (required for SOAP mode) 
     * 13. mail.jar (required for SOAP mode) 
     * 14. saaj.jar (required for SOAP mode) 
     * 15. wsdl4j.jar (required for SOAP mode) 
     * 16. xalan.jar (required for SOAP mode) 
     * 17. xbean.jar (required for SOAP mode) 
     * 18. xercesImpl.jar (required for SOAP mode) 
     * 
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     * 
     * For complete details about the location of the AEM Forms JAR files,  
     * see "Including AEM Forms Java library files" in Programming  
     * with AEM Forms 
     */ 
 import java.util.Properties; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.idp.dsc.registry.endpoint.CreateEndpointInfo; 
 import com.adobe.idp.dsc.registry.endpoint.client.EndpointRegistryClient; 
 import com.adobe.idp.dsc.registry.infomodel.Endpoint; 
  
 public class AddWatchFolderEndPoint { 
      
     public static void main(String[] args) { 
          
     try{ 
         //Set connection properties    required to invoke AEM Forms 
         Properties ConnectionProps = new Properties(); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
         //Create a ServiceClientFactory object 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(ConnectionProps); 
  
         //Create an EndpointRegistryClient object 
         EndpointRegistryClient endPointClient = new EndpointRegistryClient(myFactory); 
          
         //Create a Watched Folder endpoint for the MyApplication/EncryptDocument process 
         CreateEndpointInfo e = new CreateEndpointInfo(); 
         e.setConnectorId("WatchedFolder"); 
         e.setDescription("WatchedFolder endpoint for the EncryptDocument process"); 
         e.setName("MyApplication/EncryptDocument"); 
         e.setServiceId("MyApplication/EncryptDocument"); 
         e.setOperationName("invoke"); 
          
         //Set configuration values for a Watched Folder EndPoint 
         e.setConfigParameterAsText(WatchedFolderEndpointConfigConstants.PROPERTY_FILEPROVIDER_URL,"C:\\EncryptFolder"); 
         e.setConfigParameterAsText(WatchedFolderEndpointConfigConstants.PROPERTY_PROPERTY_ASYNCHRONOUS,"true"); 
         e.setConfigParameterAsText(WatchedFolderEndpointConfigConstants.PROPERTY_PURGE_DURATION,"-1"); 
         e.setConfigParameterAsText(WatchedFolderEndpointConfigConstants.PROPERTY_REPEAT_INTERVAL,"5"); 
         e.setConfigParameterAsText(WatchedFolderEndpointConfigConstants.PROPERTY_REPEAT_COUNT,"-1"); 
         e.setConfigParameterAsText(WatchedFolderEndpointConfigConstants.PROPERTY_THROTTLE,"false"); 
         e.setConfigParameterAsText(WatchedFolderEndpointConfigConstants.PROPERTY_USERNAMER,"SuperAdmin"); 
         e.setConfigParameterAsText(WatchedFolderEndpointConfigConstants.PROPERTY_DOMAINNAME,"DefaultDom"); 
         e.setConfigParameterAsText(WatchedFolderEndpointConfigConstants.PROPERTY_FILEPROVIDER_BATCH_SIZE,"2"); 
         e.setConfigParameterAsText(WatchedFolderEndpointConfigConstants.PROPERTY_FILEPROVIDER_WAIT_TIME,"0"); 
         e.setConfigParameterAsText(WatchedFolderEndpointConfigConstants.PROPERTY_EXCLUDE_FILE_PATTERN,".txt"); 
         e.setConfigParameterAsText(WatchedFolderEndpointConfigConstants.PROPERTY_INCLUDE_FILE_PATTERN,"*"); 
         e.setConfigParameterAsText(WatchedFolderEndpointConfigConstants.PROPERTY_FILEPROVIDER_RESULT_FOLDER_NAME,"result/%Y/%M/%D/"); 
         e.setConfigParameterAsText(WatchedFolderEndpointConfigConstants.PROPERTY_FILEPROVIDER_PRESERVE_FOLDER_NAME,"preserve/%Y/%M/%D/"); 
         e.setConfigParameterAsText(WatchedFolderEndpointConfigConstants.PROPERTY_FILEPROVIDER_FAILURE_FOLDER_NAME,"failure/%Y/%M/%D/"); 
         e.setConfigParameterAsText(WatchedFolderEndpointConfigConstants.PROPERTY_FILEPROVIDER_PRESERVE_ON_FAILURE,"true"); 
         e.setConfigParameterAsText(WatchedFolderEndpointConfigConstants.PROPERTY_FILEPROVIDER_OVERWRITE_DUPLICATE_FILENAME,"false"); 
                  
         //Define input parameter values 
         e.setInputParameterMapping("inDoc", 
                 "com.adobe.idp.Document", 
                 "variable", 
                 "*.pdf"); 
          
         //Define the output parameter values 
         e.setOutputParameterMapping("outDoc",  
                 "com.adobe.idp.Document", 
                 "%F.pdf"); 
          
         //Create the Watched Folder Endpoint 
         Endpoint endPoint = endPointClient.createEndpoint(e); 
          
         //Enable the Endpoint     
         endPointClient.enable(endPoint); 
              
          
     }catch (Exception e) { 
          e.printStackTrace(); 
         }     
  
     } 
 } 
 
```

## 快速入門：使用Java API新增電子郵件端點 {#quickstart-adding-an-email-endpoint-using-the-java-api}

以下Java代碼示例將Email端點添加到名為 *MyApplication/EncryptDocument* t.(請參閱 [新增電子郵件端點](/help/forms/developing/programmatically-endpoints.md#adding-email-endpoints).)

>[!NOTE]
>
>您必須在專案中包含EmailEndpointConfigConstants.java檔案，才能編譯並執行下列快速入門。 (請參閱 [電子郵件配置值常數檔案](/help/forms/developing/programmatically-endpoints.md#email-configuration-values-constant-file).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-livecycle-client.jar 
     * 2. adobe-usermanager-client.jar 
     * 3. activation.jar (required for SOAP mode) 
     * 4. axis.jar (required for SOAP mode) 
     * 5. commons-codec-1.3.jar (required for SOAP mode) 
     * 6. commons-collections-3.2.jar  (required for SOAP mode) 
     * 7. commons-discovery.jar (required for SOAP mode) 
     * 8. commons-logging.jar (required for SOAP mode) 
     * 9. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 10. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 11. jaxrpc.jar (required for SOAP mode) 
     * 12. log4j.jar (required for SOAP mode) 
     * 13. mail.jar (required for SOAP mode) 
     * 14. saaj.jar (required for SOAP mode) 
     * 15. wsdl4j.jar (required for SOAP mode) 
     * 16. xalan.jar (required for SOAP mode) 
     * 17. xbean.jar (required for SOAP mode) 
     * 18. xercesImpl.jar (required for SOAP mode) 
     * 
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     * 
     * For complete details about the location of the AEM Forms JAR files,  
     * see "Including AEM Forms Java library files" in Programming  
     * with AEM Forms 
     */ 
 import java.util.Properties; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.idp.dsc.registry.endpoint.CreateEndpointInfo; 
 import com.adobe.idp.dsc.registry.endpoint.client.EndpointRegistryClient; 
 import com.adobe.idp.dsc.registry.infomodel.Endpoint; 
  
 public class AddEmailEndPoint { 
      
     public static void main(String[] args) { 
          
     try{ 
         //Set connection properties    required to invoke AEM Forms 
         Properties ConnectionProps = new Properties(); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
         //Create a ServiceClientFactory object 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(ConnectionProps); 
  
         //Create an EndpointRegistryClient object 
         EndpointRegistryClient endPointClient = new EndpointRegistryClient(myFactory); 
          
         //Create a new Email endpoint for the MyApplication/EncryptDocument process 
         CreateEndpointInfo e = new CreateEndpointInfo(); 
         e.setConnectorId("Email"); 
         e.setDescription("Email endpoint for the MyApplication/EncryptDocument proces"); 
         e.setName("MyApplication/EncryptDocument"); 
         e.setServiceId("MyApplication/EncryptDocument"); 
         e.setOperationName("invoke"); 
          
         //Set Configuration values for the Email endPoint 
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_CRON_EXPRESSION,""); 
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_REPREAT_COUNT,"-1"); 
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_REPREAT_INTERVAL,"10"); 
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_START_DELAY,"0"); 
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_BATCH_SIZE,"2"); 
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_USERNAME,"SuperAdmin"); 
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_DOMAINNAME,"DefaultDom"); 
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_DOMAINPATTERN,"*"); 
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_FILEPATTERN,"*"); 
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_RECIPIENT_SUCCESSFUL_JOB,"sender"); 
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_RECIPIENT_FAILED_JOB,"sender"); 
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_INBOX_HOST,"sj-lost"); 
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_INBOX_PORT,"0"); 
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_PROTOCOL,"pop3");  
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_INBOX_TIMEOUT,"60");      
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_INBOX_USER,"scott"); 
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_INBOX_PASSWORD,"password"); 
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_INBOX_SSL,"false"); 
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_SMTP_HOST,"sj-lost"); 
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_SMTP_PORT,"25"); 
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_SMTP_USER,"scott"); 
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_SMTP_PASSWORD,"password"); 
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_CHARSET,"password"); 
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_SMTP_SSL,"false"); 
         e.setConfigParameterAsText(EmailEndpointConfigConstants.PROPERTY_EMAILPROVIDER_FAILED_FOLDER,"failedJobFolder"); 
                      
         //Define input parameter values 
         e.setInputParameterMapping("InDoc", 
                 "com.adobe.idp.Document", 
                 "variable", 
                 "*.pdf"); 
          
         //Define the output parameter values 
         e.setOutputParameterMapping("SecuredDoc",  
                 "com.adobe.idp.Document", 
                 "%F.pdf"); 
          
         //Create the Email Endpoint 
         Endpoint endPoint = endPointClient.createEndpoint(e); 
          
         //Enable the Email Endpoint     
         endPointClient.enable(endPoint); 
  
     }catch (Exception e) { 
          e.printStackTrace(); 
         }     
  
     } 
 } 
  
 
```

## 快速入門：使用Java API新增遠端端點 {#quickstart-adding-a-remoting-endpoint-using-the-java-api}

以下Java代碼示例將Remoteing端點添加到名為 *MyApplication/EncryptDocument*. (請參閱 [新增遠端端點](/help/forms/developing/programmatically-endpoints.md#adding-remoting-endpoints).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-livecycle-client.jar 
     * 2. adobe-usermanager-client.jar 
     * 3. activation.jar (required for SOAP mode) 
     * 4. axis.jar (required for SOAP mode) 
     * 5. commons-codec-1.3.jar (required for SOAP mode) 
     * 6. commons-collections-3.2.jar  (required for SOAP mode) 
     * 7. commons-discovery.jar (required for SOAP mode) 
     * 8. commons-logging.jar (required for SOAP mode) 
     * 9. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 10. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 11. jaxrpc.jar (required for SOAP mode) 
     * 12. log4j.jar (required for SOAP mode) 
     * 13. mail.jar (required for SOAP mode) 
     * 14. saaj.jar (required for SOAP mode) 
     * 15. wsdl4j.jar (required for SOAP mode) 
     * 16. xalan.jar (required for SOAP mode) 
     * 17. xbean.jar (required for SOAP mode) 
     * 18. xercesImpl.jar (required for SOAP mode) 
     * 
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     * 
     * For complete details about the location of the AEM Forms JAR files,  
     * see "Including AEM Forms Java library files" in Programming  
     * with AEM Forms 
     */ 
  
 import java.util.Properties; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.idp.dsc.registry.endpoint.CreateEndpointInfo; 
 import com.adobe.idp.dsc.registry.endpoint.client.EndpointRegistryClient; 
 import com.adobe.idp.dsc.registry.infomodel.Endpoint; 
  
 /** 
     * This Java Quick Start adds a Remoting endpoint to a service named MyApplication/EncryptDocument 
     */ 
 public class AddRemotingEndPoint { 
      
     public static void main(String[] args) { 
          
     try{ 
         //Set connection properties    required to invoke AEM Forms 
         Properties ConnectionProps = new Properties(); 
          
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                      
         //Create a ServiceClientFactory object 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(ConnectionProps); 
  
         //Create a ConnectorRegistryClient object 
         EndpointRegistryClient endPointClient = new EndpointRegistryClient(myFactory); 
          
         //Create an Remoting Endpoint for the MyApplication/EncryptDocument process 
         CreateEndpointInfo e = new CreateEndpointInfo(); 
         e.setConnectorId("Remoting"); 
         e.setDescription("Remoting endpoint for the MyApplication/EncryptDocument proces"); 
         e.setName("EncryptDocumentRemoting"); 
         e.setServiceId("MyApplication/EncryptDocument"); 
         e.setOperationName("*"); 
          
         //Create the EndPoint 
         Endpoint endPoint = endPointClient.createEndpoint(e); 
          
         //Enable the Endpoint     
         endPointClient.enable(endPoint); 
          
     }catch (Exception e) { 
          e.printStackTrace(); 
         }     
  
     } 
 } 
 
```

## 快速入門：使用Java API添加TaskManager終結點 {#quickstart-adding-a-taskmanager-endpoint-using-the-java-api}

以下Java代碼示例將TaskManager端點添加到名為 *MyApplication/EncryptDocument*. 請注意，類別的名稱為 *EncryptProcess*. (請參閱 [添加TaskManager端點](/help/forms/developing/programmatically-endpoints.md#adding-taskmanager-endpoints).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-livecycle-client.jar 
     * 2. adobe-usermanager-client.jar 
     * 3. activation.jar (required for SOAP mode) 
     * 4. axis.jar (required for SOAP mode) 
     * 5. commons-codec-1.3.jar (required for SOAP mode) 
     * 6. commons-collections-3.2.jar  (required for SOAP mode) 
     * 7. commons-discovery.jar (required for SOAP mode) 
     * 8. commons-logging.jar (required for SOAP mode) 
     * 9. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 10. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 11. jaxrpc.jar (required for SOAP mode) 
     * 12. log4j.jar (required for SOAP mode) 
     * 13. mail.jar (required for SOAP mode) 
     * 14. saaj.jar (required for SOAP mode) 
     * 15. wsdl4j.jar (required for SOAP mode) 
     * 16. xalan.jar (required for SOAP mode) 
     * 17. xbean.jar (required for SOAP mode) 
     * 18. xercesImpl.jar (required for SOAP mode) 
     * 
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     * 
     * For complete details about the location of the AEM Forms JAR files,  
     * see "Including AEM Forms Java library files" in Programming  
     * with AEM Forms 
     */ 
 import java.util.Properties; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.idp.dsc.registry.endpoint.CreateEndpointCategoryInfo; 
 import com.adobe.idp.dsc.registry.endpoint.CreateEndpointInfo; 
 import com.adobe.idp.dsc.registry.endpoint.client.EndpointRegistryClient; 
 import com.adobe.idp.dsc.registry.infomodel.Endpoint; 
 import com.adobe.idp.dsc.registry.infomodel.EndpointCategory; 
  
 public class AddTaskManagerEndPoint { 
      
     public static void main(String[] args) { 
          
     try{ 
         //Set connection properties    required to invoke AEM Forms 
         Properties ConnectionProps = new Properties(); 
          
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
                      
         //Create a ServiceClientFactory object 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(ConnectionProps); 
  
         //Create a ConnectorRegistryClient object 
         EndpointRegistryClient endPointClient = new EndpointRegistryClient(myFactory); 
                  
         //Create the category associated with this TaskManager endpoint 
         CreateEndpointCategoryInfo catInfo = new CreateEndpointCategoryInfo("EncryptProcess", "Enables this process to be invoked from within Workspace");  
         EndpointCategory cat = endPointClient.createEndpointCategory(catInfo); 
                  
         //Set TaskManager endpoint attributes 
         CreateEndpointInfo e = new CreateEndpointInfo(); 
         e.setConnectorId("TaskManagerConnector"); 
         e.setDescription("TaskManagerConnector endpoint for the MyApplication/EncryptDocument process"); 
         e.setName("MyApplication/EncryptDocument"); 
         e.setServiceId("MyApplication2/EncryptDocument"); 
         e.setCategoryId(cat.getId()); 
         e.setOperationName("invoke"); 
                  
         //Create the TaskManagerConnector endpoint 
         Endpoint endPoint = endPointClient.createEndpoint(e); 
          
         //Enable the endpoint     
         endPointClient.enable(endPoint); 
          
     }catch (Exception e) { 
          e.printStackTrace(); 
         }     
  
     } 
 } 
  
 
```

## 快速入門：使用Java API修改端點 {#quickstart-modifying-an-endpoint-using-the-java-api}

以下Java代碼示例修改了「監看資料夾」端點。端點為 *MyApplication/EncryptDocument* 程式。 已監看的資料夾變更為 `C:\NewWatchedFolder`. (請參閱 [修改端點](/help/forms/developing/programmatically-endpoints.md#modifying-endpoints).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-livecycle-client.jar 
     * 2. adobe-usermanager-client.jar 
     * 3. activation.jar (required for SOAP mode) 
     * 4. axis.jar (required for SOAP mode) 
     * 5. commons-codec-1.3.jar (required for SOAP mode) 
     * 6. commons-collections-3.2.jar  (required for SOAP mode) 
     * 7. commons-discovery.jar (required for SOAP mode) 
     * 8. commons-logging.jar (required for SOAP mode) 
     * 9. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 10. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 11. jaxrpc.jar (required for SOAP mode) 
     * 12. log4j.jar (required for SOAP mode) 
     * 13. mail.jar (required for SOAP mode) 
     * 14. saaj.jar (required for SOAP mode) 
     * 15. wsdl4j.jar (required for SOAP mode) 
     * 16. xalan.jar (required for SOAP mode) 
     * 17. xbean.jar (required for SOAP mode) 
     * 18. xercesImpl.jar (required for SOAP mode) 
     * 
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     * 
     * For complete details about the location of the AEM Forms JAR files,  
     * see "Including AEM Forms Java library files" in Programming  
     * with AEM Forms 
     */ 
 import java.util.Iterator; 
 import java.util.List; 
 import java.util.Properties; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.idp.dsc.filter.PagingFilter; 
 import com.adobe.idp.dsc.registry.endpoint.ModifyEndpointInfo; 
 import com.adobe.idp.dsc.registry.endpoint.client.EndpointRegistryClient; 
 import com.adobe.idp.dsc.registry.infomodel.Endpoint; 
  
 public class ModifyEndPoint { 
      
     public static void main(String[] args) { 
          
     try{ 
         Endpoint _endpoint = null;  
          
         //Set connection properties    required to invoke AEM Forms 
         Properties ConnectionProps = new Properties(); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
      
         //Create a ServiceClientFactory object 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(ConnectionProps); 
  
         //Create an EndpointRegistryClient object 
         EndpointRegistryClient endPointClient = new EndpointRegistryClient(myFactory); 
                  
         //Retrieve all endpoints 
         List allEndpoints = endPointClient.getEndpoints((PagingFilter)null); 
          
         //Iterate through the returned list of endpoints 
         Iterator iter = allEndpoints.iterator();     
         int i =0; 
         while (iter.hasNext()) { 
             _endpoint = (Endpoint) iter.next(); 
              
             //Look for an endpoint that belongs to the  
             //EncryptDocument service 
             String serviceID = _endpoint.getServiceId(); 
              
             if (serviceID.matches("MyApplication/EncryptDocument")) 
             { 
                 //Get the WatchedFolder endpoint 
                 String connId = _endpoint.getConnectorId(); 
                 if (connId.matches("WatchedFolder")) 
                 { 
                      
                     //Create a ModifyEndpointInfo object 
                     ModifyEndpointInfo endpointInfo =new ModifyEndpointInfo(); 
                      
                     //Modify configuration values 
                     endpointInfo.setId(_endpoint.getId()); 
                     endpointInfo.setConfigParameterAsText("url", "C:\\NewWatchedFolder"); 
                     endpointInfo.setConfigParameterAsText("asynchronous","true"); 
                     endpointInfo.setConfigParameterAsText("repeatInterval","5"); 
                     endpointInfo.setConfigParameterAsText("repeatCount","-1"); 
                     endpointInfo.setConfigParameterAsText("throttleOn","false"); 
                     endpointInfo.setConfigParameterAsText("userName","SuperAdmin"); 
                     endpointInfo.setConfigParameterAsText("domainName","DefaultDom"); 
                     endpointInfo.setConfigParameterAsText("batchSize","2"); 
                     endpointInfo.setConfigParameterAsText("waitTime","0"); 
                     endpointInfo.setConfigParameterAsText("excludeFilePattern",".txt"); 
                     endpointInfo.setConfigParameterAsText("includeFilePattern","*"); 
                     endpointInfo.setConfigParameterAsText("resultFolderName","result/%Y/%M/%D/"); 
                     endpointInfo.setConfigParameterAsText("preserveFolderName","preserve/%Y/%M/%D/"); 
                     endpointInfo.setConfigParameterAsText("failureFolderName","failure/%Y/%M/%D/"); 
                     endpointInfo.setConfigParameterAsText("preserveOnFailure","true"); 
                     endpointInfo.setConfigParameterAsText("overwriteDuplicateFilename","false"); 
                      
                     //Define input parameter values 
                     endpointInfo.setInputParameterMapping("inDoc", 
                             "com.adobe.idp.Document", 
                             "variable", 
                             "*.pdf"); 
                      
                     //Define the output parameter values 
                     endpointInfo.setOutputParameterMapping("outDoc",  
                             "com.adobe.idp.Document", 
                             "%F.pdf"); 
                      
                     //Modify the endpoint for this service 
                     endPointClient.modifyEndpoint(endpointInfo); 
                     System.out.println("The EJB endpoint for the EncryptDocument service was modified");  
                 } 
             i++;      
             } 
         } 
     }catch (Exception e) { 
          e.printStackTrace(); 
         }     
     } 
 } 
 
```

## 快速入門：使用Java API移除端點 {#quickstart-removing-an-endpoint-using-the-java-api}

以下Java代碼從名為的服務中刪除EJB終結點 *MyApplication/EncryptDocument*. (請參閱 [移除端點](/help/forms/developing/programmatically-endpoints.md#removing-endpoints).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-livecycle-client.jar 
     * 2. adobe-usermanager-client.jar 
     * 3. activation.jar (required for SOAP mode) 
     * 4. axis.jar (required for SOAP mode) 
     * 5. commons-codec-1.3.jar (required for SOAP mode) 
     * 6. commons-collections-3.2.jar  (required for SOAP mode) 
     * 7. commons-discovery.jar (required for SOAP mode) 
     * 8. commons-logging.jar (required for SOAP mode) 
     * 9. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 10. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 11. jaxrpc.jar (required for SOAP mode) 
     * 12. log4j.jar (required for SOAP mode) 
     * 13. mail.jar (required for SOAP mode) 
     * 14. saaj.jar (required for SOAP mode) 
     * 15. wsdl4j.jar (required for SOAP mode) 
     * 16. xalan.jar (required for SOAP mode) 
     * 17. xbean.jar (required for SOAP mode) 
     * 18. xercesImpl.jar (required for SOAP mode) 
     * 
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     * 
     * For complete details about the location of the AEM Forms JAR files,  
     * see "Including AEM Forms Java library files" in Programming  
     * with AEM Forms 
     */ 
 import java.util.Iterator; 
 import java.util.List; 
 import java.util.Properties; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.idp.dsc.filter.PagingFilter; 
 import com.adobe.idp.dsc.registry.endpoint.client.EndpointRegistryClient; 
 import com.adobe.idp.dsc.registry.infomodel.Endpoint; 
  
 /** 
     * This Java Quick Start removes an EJB endpoint from a service named MyApplication/EncryptDocument 
     */ 
 public class RemoveEndPoints { 
      
     public static void main(String[] args) { 
          
     try{ 
         Endpoint _endpoint = null;  
          
         //Set connection properties    required to invoke AEM Forms 
         Properties ConnectionProps = new Properties(); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
      
         //Create a ServiceClientFactory object 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(ConnectionProps); 
  
         //Create an EndpointRegistryClient object 
         EndpointRegistryClient endPointClient = new EndpointRegistryClient(myFactory); 
                  
         //Get all endpoints 
         List allEndpoints = endPointClient.getEndpoints((PagingFilter)null); 
          
         //Iterate through the returned list of endpoints 
         Iterator iter = allEndpoints.iterator();     
         int i =0; 
         while (iter.hasNext()) { 
             _endpoint = (Endpoint) iter.next(); 
              
             //Look for an endpoint that belongs to the  
             //EncryptDocument service 
             String serviceID = _endpoint.getServiceId(); 
              
             if (serviceID.matches("MyApplication/EncryptDocument")) 
             { 
                 //Get the EJB endpoint that belongs to  
                 //this service 
                 String connId = _endpoint.getConnectorId(); 
                 if (connId.matches("EJB")) 
                 { 
                     //Remove the EJB endpoint for this service 
                     endPointClient.remove(_endpoint); 
                     System.out.println("The EJB endpoint for the EncryptDocument service was removed");  
                 } 
             i++;      
             } 
         } 
     }catch (Exception e) { 
          e.printStackTrace(); 
         }     
     } 
 } 
 
```

## 快速入門：使用Java API擷取端點連接器資訊 {#quickstart-retrieving-endpoint-connector-information-using-the-java-api}

以下Java代碼將檢索有關「監看資料夾」端點的資訊。 會擷取並顯示每個設定值的相關資訊。 此程式碼清單會指定每個設定值為必要或選用。 此外，還會顯示每個設定值的名稱和值。 (請參閱 [檢索端點連接器資訊](/help/forms/developing/programmatically-endpoints.md#retrieving-endpoint-connector-information).)

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-livecycle-client.jar 
     * 2. adobe-usermanager-client.jar 
     * 3. activation.jar (required for SOAP mode) 
     * 4. axis.jar (required for SOAP mode) 
     * 5. commons-codec-1.3.jar (required for SOAP mode) 
     * 6. commons-collections-3.2.jar  (required for SOAP mode) 
     * 7. commons-discovery.jar (required for SOAP mode) 
     * 8. commons-logging.jar (required for SOAP mode) 
     * 9. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
     * 10. jaxen-1.1-beta-9.jar (required for SOAP mode) 
     * 11. jaxrpc.jar (required for SOAP mode) 
     * 12. log4j.jar (required for SOAP mode) 
     * 13. mail.jar (required for SOAP mode) 
     * 14. saaj.jar (required for SOAP mode) 
     * 15. wsdl4j.jar (required for SOAP mode) 
     * 16. xalan.jar (required for SOAP mode) 
     * 17. xbean.jar (required for SOAP mode) 
     * 18. xercesImpl.jar (required for SOAP mode) 
     * 
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     * 
     * For complete details about the location of the AEM Forms JAR files,  
     * see "Including AEM Forms Java library files" in Programming  
     * with AEM Forms 
     */ 
 import java.util.Properties; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import com.adobe.idp.dsc.registry.connector.client.ConnectorRegistryClient; 
 import com.adobe.idp.dsc.registry.infomodel.ConfigParameter; 
 import com.adobe.idp.dsc.registry.infomodel.Endpoint; 
  
 public class RetrieveConnectorInfo { 
      
     public static void main(String[] args) { 
          
     try{ 
         Endpoint _endpoint = null;  
          
         //Set connection properties    required to invoke AEM Forms 
         Properties ConnectionProps = new Properties(); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
         ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
      
         //Create a ServiceClientFactory object 
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(ConnectionProps); 
  
         //Create a ConnectorRegistry Client object  
         ConnectorRegistryClient conClient = new ConnectorRegistryClient(myFactory); 
          
         //Specify WatchedFolder as the connector type 
         Endpoint endpoint = conClient.getEndpointDefinition("WatchedFolder"); 
          
         //Get all the configuration values associated with this connector type 
         ConfigParameter[] allConfigParams = endpoint.getConfigParameters(); 
         int len = allConfigParams.length; 
          
         //Get the value of the individual configuration parameter values 
         //and which ones are required and which ones are optional 
         for (int i=0; i<len; i++) 
         { 
             //Get an individual ConfigParameter object  
             ConfigParameter cp = (ConfigParameter)allConfigParams[i]; 
              
             //Determine if this configuration value is required 
             if (cp.isRequired() == true) 
                 System.out.println("This required configuration value name is "+cp.getName() + ". Its value is "+cp.getTextValue()); 
             else 
                 System.out.println("This optional configuration value name is "+cp.getName() + ". Its value is "+cp.getTextValue()); 
         } 
     }catch (Exception e) { 
          e.printStackTrace(); 
         }     
     } 
 } 
 
```

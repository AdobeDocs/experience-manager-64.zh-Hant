---
title: Application Manager客戶端JavaAPI快速入門(SOAP)
seo-title: Application Manager客戶端JavaAPI快速入門(SOAP)
description: 使用Application Manager Client來建立應用程式版本、導出應用程式、導入應用程式、獲取AEM Forms應用程式、獲取應用程式狀態、預覽AEM Forms和更新的應用程式存檔，以及刪除AEM Forms應用程式存檔。
seo-description: 使用Application Manager Client來建立應用程式版本、導出應用程式、導入應用程式、獲取AEM Forms應用程式、獲取應用程式狀態、預覽AEM Forms和更新的應用程式存檔，以及刪除AEM Forms應用程式存檔。
uuid: 043f1c08-c7de-4e2d-88ca-b46428b1b551
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 2ec2a75e-4191-4660-a6f2-26cc667720b3
role: Developer
exl-id: 8369beeb-4628-40ea-9167-717f112768da
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%

---

# Application Manager客戶端JavaAPI快速入門(SOAP){#application-manager-client-javaapi-quick-start-soap}

以下Java API快速入門(SOAP)適用於Application Manager客戶端。

[快速入門（SOAP模式）:使用Java API建立應用程式版本](#quick-start-soap-mode-creating-application-version-using-the-java-api)

[快速入門（SOAP模式）:使用Java API匯出應用程式](#quick-start-soap-mode-exporting-applications-using-the-java-api)

[快速入門（SOAP模式）:使用Java API匯入應用程式](#quick-start-soap-mode-importing-applications-using-the-java-api)

[快速入門（SOAP模式）:使用Java API取得AEM Forms應用程式](application-manager-client-java-api.md#quick-start-soap-mode-getting-a-application-using-the-java-api)

[快速入門（SOAP模式）:使用Java API取得應用程式](application-manager-client-java-api.md#quick-start-soap-mode-getting-the-applications-using-the-java-api)

[快速入門（SOAP模式）:使用Java API取得應用程式的狀態](application-manager-client-java-api.md#quick-start-soap-mode-getting-status-of-applications-using-java-api)

[快速入門（SOAP模式）：使用Java API預覽AEM Forms和更新的應用程式封存](application-manager-client-java-api.md#quick-start-soap-mode-previewing-the-livecycle-es2-and-later-application-archive-using-the-java-api)

[快速入門（SOAP模式）：使用Java API刪除AEM Forms應用程式封存](application-manager-client-java-api.md#quick-start-soap-mode-deleting-the-application-archive-using-the-java-api)

AEM Forms操作可使用AEM Forms強制類型API來執行，且連線模式應設為SOAP。

>[!NOTE]
>
>使用AEM Forms進行程式設計中的快速入門是以部署在JBoss和Windows作業系統上的Forms伺服器為基礎。 但是，如果您使用其他作業系統（如Unix），則用適用作業系統支援的路徑替換特定於windows的路徑。 同樣，如果您正在使用其他J2EE應用程式伺服器，請確保指定有效的連接屬性。 請參閱[設定連線屬性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)。

## 快速入門（SOAP模式）:使用Java API {#quick-start-soap-mode-creating-application-version-using-the-java-api}建立應用程式版本

以下Java程式碼範例會使用JAVA API建立應用程式。

```as3
/* 
 * This Java Quick Start uses the SOAP mode and contains the following JAR files 
 * in the class path: 
 * 1. adobe-livecycle-client.jar 
 * 2. adobe-usermanager-client.jar 
 * 3. adobe-application-remote-client.jar 
 * 4. adobe-repository-client.jar 
 * 5. activation.jar (required for SOAP mode) 
 * 6. axis.jar (required for SOAP mode) 
 * 7. commons-codec-1.3.jar (required for SOAP mode) 
 * 8. commons-collections-3.1.jar  (required for SOAP mode) 
 * 9. commons-discovery.jar (required for SOAP mode) 
 * 10. commons-logging.jar (required for SOAP mode) 
 * 11. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
 * 12. jaxen-1.1-beta-9.jar (required for SOAP mode) 
 * 13. jaxrpc.jar (required for SOAP mode) 
 * 14. log4j.jar (required for SOAP mode) 
 * 15. mail.jar (required for SOAP mode) 
 * 16. saaj.jar (required for SOAP mode) 
 * 17. wsdl4j.jar (required for SOAP mode) 
 * 18. xalan.jar (required for SOAP mode) 
 * 19. xbean.jar (required for SOAP mode) 
 * 20. xercesImpl.jar (required for SOAP mode) 
 * 
 * These JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/common 
 * 
 * 
 * SOAP required JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/thirdparty 
 * 
 * 
 */ 
package com.adobe.idp.dsc.applicationmanager; 
import java.util.Properties; 
import java.util.Random; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClient; 
import com.adobe.repository.bindings.ResourceRepositoryDelegate; 
import com.adobe.repository.bindings.dsc.client.ResourceRepositoryClient; 
public class CreateApplicationVersion_SOAP { 
    private static String applicationFolder = "Applications"; 
    private static String defaultAppVersion = "1.0"; 
    public static void main(String[] args) { 
        // Set connection properties required to invoke AEM Forms 
        Properties connectionProps = new Properties(); 
        connectionProps.setProperty("DSC_DEFAULT_SOAP_ENDPOINT", 
                "https://[server]:[port]"); 
        connectionProps.setProperty("DSC_TRANSPORT_PROTOCOL", 
                ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL); 
        connectionProps.setProperty("DSC_SERVER_TYPE", 
                ServiceClientFactoryProperties.DSC_JBOSS_SERVER_TYPE); 
        connectionProps.setProperty("DSC_CREDENTIAL_USERNAME", "administrator"); 
        connectionProps.setProperty("DSC_CREDENTIAL_PASSWORD", "password"); 
        // Create ServiceClientFactory object 
        ServiceClientFactory myFactory = ServiceClientFactory 
                .createInstance(connectionProps); 
        // Create ApplicationManagerClient object 
        ApplicationManagerClient appClient = new ApplicationManagerClient( 
                myFactory); 
        // Create ResourceRepositoryDelegate object 
        ResourceRepositoryDelegate repositoryClient = new ResourceRepositoryClient( 
                myFactory); 
        final Random num = new Random(); 
        String appName = "App" + num.nextInt(); 
        String newAppName = null; 
        try { 
            // Create application with default application version 
            newAppName = appClient.createApplication(appName); 
            if (repositoryClient.resourceExists("/" + applicationFolder + "/" 
                    + appName.toString() + "/" + defaultAppVersion)) { 
                System.out.println("Application with name: " + appName + "/" 
                        + defaultAppVersion + " is created succesfully!"); 
            } 
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
        try { 
            // Create version of the new application 
            appName = appClient.createApplicationVersion(newAppName, 
                    defaultAppVersion, "2.0", "version increment"); 
            if (repositoryClient.resourceExists("/" + applicationFolder + "/" 
                    + appName.toString() + "/" + "2.0")) { 
                System.out.println("Application version 2.0 created : " 
                        + appName + "/" + "2.0"); 
            } 
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
    } 
}
```

## 快速入門（SOAP模式）:使用Java API {#quick-start-soap-mode-exporting-applications-using-the-java-api}導出應用程式

下列Java程式碼範例會使用JAVA API匯出應用程式。

```as3
/* 
 * This Java Quick Start uses the SOAP mode and contains the following JAR files 
 * in the class path: 
 * 1. adobe-livecycle-client.jar 
 * 2. adobe-usermanager-client.jar 
 * 3. adobe-application-remote-client.jar 
 * 4. activation.jar (required for SOAP mode) 
 * 5. axis.jar (required for SOAP mode) 
 * 6. commons-codec-1.3.jar (required for SOAP mode) 
 * 7. commons-collections-3.1.jar  (required for SOAP mode) 
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
 * 
 * SOAP required JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/thirdparty 
 * 
 * 
 */ 
package com.adobe.idp.dsc.applicationmanager; 
import java.io.File; 
import java.io.FileInputStream; 
import java.util.ArrayList; 
import java.util.List; 
import java.util.Properties; 
import com.adobe.idp.Document; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClient; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClientException; 
public class ExportLCA_SOAP { 
    public static void main(String[] args) { 
        // Set connection properties required to invoke AEM Forms 
        Properties connectionProps = new Properties(); 
        connectionProps.setProperty("DSC_DEFAULT_SOAP_ENDPOINT", 
                "https://[server]:[port]"); 
        connectionProps.setProperty("DSC_TRANSPORT_PROTOCOL", 
                ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL); 
        connectionProps.setProperty("DSC_SERVER_TYPE", 
                ServiceClientFactoryProperties.DSC_JBOSS_SERVER_TYPE); 
        connectionProps.setProperty("DSC_CREDENTIAL_USERNAME", "administrator"); 
        connectionProps.setProperty("DSC_CREDENTIAL_PASSWORD", "password"); 
        // Create ServiceClientFactory object 
        ServiceClientFactory myFactory = ServiceClientFactory 
                .createInstance(connectionProps); 
        // Create ApplicationManagerClient object 
        ApplicationManagerClient appClient = new ApplicationManagerClient( 
                myFactory); 
        Document doc = null; 
        try { 
            final FileInputStream fileApp = new FileInputStream( 
                    "C:\\ImportSampleApp2.lca"); 
            doc = new Document(fileApp); 
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
        String resourceID = null; 
        try { 
            // Import the application into the LC server 
            resourceID = appClient.importApplication(doc); 
            System.out.println("Import application with resource ID:" 
                    + resourceID + " is completed successfully!"); 
        } catch (ApplicationManagerClientException e) { 
            e.printStackTrace(); 
        } 
        final String sampleAppName = "ExportSampleApp2"; 
        try { 
            final List<String> eReqList = new ArrayList<String>(); 
            eReqList.add(resourceID); 
            // Export the application imported above 
            doc = appClient.export(eReqList, "lcaDescription"); 
            // Save into local LCA file 
            final String archiveName = "C:/" + sampleAppName + "-" + "1.0" 
                    + ".lca"; 
            final File fTemp = new File(archiveName); 
            doc.copyToFile(fTemp); 
            System.out.println("Export application completed with name: " 
                    + archiveName); 
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
    } 
}
```

## 快速入門（SOAP模式）:使用Java API {#quick-start-soap-mode-importing-applications-using-the-java-api}導入應用程式

以下Java程式碼範例使用JAVA API匯入應用程式。

>[!NOTE]
>
>Java API importApplication()會以較新的應用程式取代相同名稱的現有應用程式。 若要更新現有應用程式，請使用API importApplication()來取代API updateApplication()。

```as3
/* 
 * This Java Quick Start uses the SOAP mode and contains the following JAR files 
 * in the class path: 
 * 1. adobe-livecycle-client.jar 
 * 2. adobe-usermanager-client.jar 
 * 3. adobe-application-remote-client.jar 
 * 4. activation.jar (required for SOAP mode) 
 * 5. axis.jar (required for SOAP mode) 
 * 6. commons-codec-1.3.jar (required for SOAP mode) 
 * 7. commons-collections-3.1.jar  (required for SOAP mode) 
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
 * 
 * SOAP required JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/thirdparty 
 * 
 * 
 */ 
package com.adobe.idp.dsc.applicationmanager; 
import java.io.FileInputStream; 
import java.util.Properties; 
import com.adobe.idp.Document; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClient; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClientException; 
public class ImportLCA_SOAP { 
    public static void main(String[] args) { 
        // Set connection properties required to invoke AEM FOrms 
        Properties connectionProps = new Properties(); 
        connectionProps.setProperty("DSC_DEFAULT_SOAP_ENDPOINT", 
                "https://[server]:[port]"); 
        connectionProps.setProperty("DSC_TRANSPORT_PROTOCOL", 
                ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL); 
        connectionProps.setProperty("DSC_SERVER_TYPE", 
                ServiceClientFactoryProperties.DSC_JBOSS_SERVER_TYPE); 
        connectionProps.setProperty("DSC_CREDENTIAL_USERNAME", "administrator"); 
        connectionProps.setProperty("DSC_CREDENTIAL_PASSWORD", "password"); 
        // Create ServiceClientFactory object 
        ServiceClientFactory myFactory = ServiceClientFactory 
                .createInstance(connectionProps); 
        // Create ApplicationManagerClient object 
        ApplicationManagerClient appClient = new ApplicationManagerClient( 
                myFactory); 
        Document doc = null; 
        try { 
            final FileInputStream fileApp = new FileInputStream( 
                    "C:\\ImportSampleApp2.lca"); 
            doc = new Document(fileApp); 
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
        try { 
            // Import the application into the LC server 
            final String resourceID = appClient.importApplication(doc); 
            System.out.println("Import application with resource ID:" 
                    + resourceID + " is completed successfully!"); 
        } catch (ApplicationManagerClientException e) { 
            e.printStackTrace(); 
        } 
    } 
}
```

## 快速入門（SOAP模式）:使用Java API {#quick-start-soap-mode-getting-a-application-using-the-java-api}獲取應用程式

下列Java程式碼範例會使用Java API取得應用程式。

```as3
/* 
 * This Java Quick Start uses the SOAP mode and contains the following JAR files 
 * in the class path: 
 * 1. adobe-livecycle-client.jar 
 * 2. adobe-usermanager-client.jar 
 * 3. adobe-application-remote-client.jar 
 * 4. activation.jar (required for SOAP mode) 
 * 5. axis.jar (required for SOAP mode) 
 * 6. commons-codec-1.3.jar (required for SOAP mode) 
 * 7. commons-collections-3.1.jar  (required for SOAP mode) 
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
 * 
 * SOAP required JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/thirdparty 
 * 
 * 
 */ 
package com.adobe.idp.dsc.applicationmanager; 
 
import java.io.FileInputStream; 
import java.util.Properties; 
 
import com.adobe.idp.Document; 
import com.adobe.idp.applicationmanager.application.Application; 
import com.adobe.idp.applicationmanager.application.ApplicationId; 
import com.adobe.idp.applicationmanager.application.impl.ApplicationIdImpl; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClient; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClientException; 
 
public class GetApplication_SOAP { 
 
    public static void main(String[] args) { 
        //Set connection properties required to invoke AEM Forms 
        Properties connectionProps = new Properties(); 
        connectionProps.setProperty("DSC_DEFAULT_SOAP_ENDPOINT", "https://[server]:[port]"); 
        connectionProps.setProperty("DSC_TRANSPORT_PROTOCOL", ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);          
        connectionProps.setProperty("DSC_SERVER_TYPE", "JBoss"); 
        connectionProps.setProperty("DSC_CREDENTIAL_USERNAME", "administrator"); 
        connectionProps.setProperty("DSC_CREDENTIAL_PASSWORD", "password"); 
 
        //Create ServiceClientFactory object 
        ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
        //Create ApplicationManagerClient object 
        ApplicationManagerClient appClient = new ApplicationManagerClient(myFactory); 
         
        Document doc = null; 
        try { 
             
            final FileInputStream fileApp = new FileInputStream("C:\\appraisal.lca"); 
            doc = new Document(fileApp); 
             
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
        final String sampleAppName = "Samples - Performance Appraisal"; 
        try { 
         
            //Import the application into the LC server 
            final String resourceID = appClient.importApplication(doc); 
            System.out.println("Import application with resource ID: " + resourceID + " is completed successfully!"); 
            //Deploy the application 
            boolean result = appClient.deployApplication(sampleAppName); 
            if (result) { 
                System.out.println("Imported application is deployed."); 
            } 
        } catch (ApplicationManagerClientException e) { 
            e.printStackTrace();     
        } 
         
        //Initialize the ApplicationId instance 
        ApplicationId appId = new ApplicationIdImpl(); 
        appId.setApplicationName(sampleAppName); 
 
        try { 
                //Get the application by application id 
                Application app = appClient.getApplication(appId); 
                System.out.println("Get application with name: " + app.getApplicationId().getApplicationName()); 
                 
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
    } 
}
```

## 快速入門（SOAP模式）:使用Java API {#quick-start-soap-mode-getting-the-applications-using-the-java-api}獲取應用程式

以下Java代碼示例使用Java API獲取應用程式。

***注意**:取得AEM Forms應用程式API、getApplications()，只會傳回已部署的應用程式。*

```as3
/* 
 * This Java Quick Start uses the SOAP mode and contains the following JAR files 
 * in the class path: 
 * 1. adobe-livecycle-client.jar 
 * 2. adobe-usermanager-client.jar 
 * 3. adobe-application-remote-client.jar 
 * 4. activation.jar (required for SOAP mode) 
 * 5. axis.jar (required for SOAP mode) 
 * 6. commons-codec-1.3.jar (required for SOAP mode) 
 * 7. commons-collections-3.1.jar  (required for SOAP mode) 
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
 * 
 * SOAP required JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/thirdparty 
 * 
 * 
 */ 

package com.adobe.idp.dsc.applicationmanager; 
 
import java.io.FileInputStream; 
import java.util.List; 
import java.util.Properties; 
 
import com.adobe.idp.Document; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClient; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClientException; 
 
public class GetApplications_SOAP { 
 
    public static void main(String[] args) { 
        //Set connection properties required to invoke AEM Forms 
        Properties connectionProps = new Properties(); 
        connectionProps.setProperty("DSC_DEFAULT_SOAP_ENDPOINT", "https://[server]:[port]"); 
        connectionProps.setProperty("DSC_TRANSPORT_PROTOCOL", ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);          
        connectionProps.setProperty("DSC_SERVER_TYPE", "JBoss"); 
        connectionProps.setProperty("DSC_CREDENTIAL_USERNAME", "administrator"); 
        connectionProps.setProperty("DSC_CREDENTIAL_PASSWORD", "password"); 
 
        //Create ServiceClientFactory object 
        ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
        //Create ApplicationManagerClient object 
        ApplicationManagerClient appClient = new ApplicationManagerClient(myFactory); 
         
        Document doc = null; 
        try { 
             
            final FileInputStream fileApp = new FileInputStream("C:\\appraisal.lca"); 
            doc = new Document(fileApp); 
             
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
         
        try { 
         
            //Import the application into the LC server 
            final String resourceID = appClient.importApplication(doc); 
            System.out.println("Import application with resource ID: " + resourceID + " is completed successfully!"); 
         
        } catch (ApplicationManagerClientException e) { 
            e.printStackTrace();     
        } 
 
        try { 
                //Get applications from LC server 
                List appList = appClient.getApplications(); 
                System.out.println("Get applications from LC Server: " + appList.size()); 
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
    } 
}
```

## 快速入門（SOAP模式）:使用Java API {#quick-start-soap-mode-getting-status-of-applications-using-java-api}獲取應用程式的狀態

```as3
/* 
 * This Java Quick Start uses the SOAP mode and contains the following JAR files 
 * in the class path: 
 * 1. adobe-livecycle-client.jar 
 * 2. adobe-usermanager-client.jar 
 * 3. adobe-application-remote-client.jar 
 * 4. activation.jar (required for SOAP mode) 
 * 5. axis.jar (required for SOAP mode) 
 * 6. commons-codec-1.3.jar (required for SOAP mode) 
 * 7. commons-collections-3.1.jar  (required for SOAP mode) 
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
 * 
 * SOAP required JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/thirdparty 
 * 
 * 
 */ 
package com.adobe.idp.dsc.applicationmanager; 
 
import java.io.FileInputStream; 
import java.util.Properties; 
 
import com.adobe.idp.Document; 
import com.adobe.idp.applicationmanager.application.ApplicationId; 
import com.adobe.idp.applicationmanager.application.ApplicationStatus; 
import com.adobe.idp.applicationmanager.application.impl.ApplicationIdImpl; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClient; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClientException; 
 
public class GetApplicationStatus_SOAP { 
 
    public static void main(String[] args) { 
        //Set connection properties required to invoke AEM Forms 
        Properties connectionProps = new Properties(); 
        connectionProps.setProperty("DSC_DEFAULT_SOAP_ENDPOINT", "https://[server]:[port]"); 
        connectionProps.setProperty("DSC_TRANSPORT_PROTOCOL", ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);          
        connectionProps.setProperty("DSC_SERVER_TYPE", "JBoss"); 
        connectionProps.setProperty("DSC_CREDENTIAL_USERNAME", "administrator"); 
        connectionProps.setProperty("DSC_CREDENTIAL_PASSWORD", "password"); 
 
        //Create ServiceClientFactory object 
        ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
        //Create ApplicationManagerClient object 
        ApplicationManagerClient appClient = new ApplicationManagerClient(myFactory); 
         
        Document doc = null; 
        try { 
             
            final FileInputStream fileApp = new FileInputStream("C:\\appraisal.lca"); 
            doc = new Document(fileApp); 
             
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
        final String sampleAppName = "Samples - Performance Appraisal"; 
        try { 
         
            //Import the application into the LC server 
            final String resourceID = appClient.importApplication(doc); 
            System.out.println("Import application with resource ID: " + resourceID + " is completed successfully!"); 
            //Deploy the application 
            boolean result = appClient.deployApplication(sampleAppName); 
            if (result) { 
                System.out.println("Imported application is deployed."); 
            } 
        } catch (ApplicationManagerClientException e) { 
            e.printStackTrace();     
        } 
         
        //Initialize the ApplicationId instance 
        ApplicationId appId = new ApplicationIdImpl(); 
        appId.setApplicationName(sampleAppName); 
 
        try { 
                //Get the application by application id 
                ApplicationStatus status = appClient.getApplicationStatus(appId); 
                System.out.println("Get application status with code: " + status.getStatusCode()); 
                 
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
    } 
}
```

## 快速啟動（SOAP模式）：使用Java API {#quick-start-soap-mode-previewing-the-livecycle-es2-and-later-application-archive-using-the-java-api}預覽LiveCycleES2和更新的應用程式歸檔檔案

下列Java程式碼範例用於使用Java API預先檢視AEM Forms和更新的應用程式封存。

```as3
/* 
 * This Java Quick Start uses the SOAP mode and contains the following JAR files 
 * in the class path: 
 * 1. adobe-livecycle-client.jar 
 * 2. adobe-usermanager-client.jar 
 * 3. adobe-application-remote-client.jar 
 * 4. activation.jar (required for SOAP mode) 
 * 5. axis.jar (required for SOAP mode) 
 * 6. commons-codec-1.3.jar (required for SOAP mode) 
 * 7. commons-collections-3.1.jar  (required for SOAP mode) 
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
 * 
 * SOAP required JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/thirdparty 
 */ 
package com.adobe.idp.dsc.applicationmanager; 
import java.io.FileInputStream; 
import java.util.Properties; 
import com.adobe.idp.Document; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClient; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClientException; 
public class PreviewLCA_SOAP { 
    public static void main(String[] args) { 
        //Set connection properties required to invoke AEM Forms 
        Properties connectionProps = new Properties(); 
        connectionProps.setProperty("DSC_DEFAULT_SOAP_ENDPOINT", "https://[server]:[port]"); 
        connectionProps.setProperty("DSC_TRANSPORT_PROTOCOL", ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);          
        connectionProps.setProperty("DSC_SERVER_TYPE", "JBoss"); 
        connectionProps.setProperty("DSC_CREDENTIAL_USERNAME", "administrator"); 
        connectionProps.setProperty("DSC_CREDENTIAL_PASSWORD", "password"); 
        //Create ServiceClientFactory object 
        ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
        //Create ApplicationManagerClient object 
        ApplicationManagerClient appClient = new ApplicationManagerClient(myFactory); 
         
        Document doc = null; 
        try { 
             
            final FileInputStream fileApp = new FileInputStream("C:\\appraisal.lca"); 
            doc = new Document(fileApp); 
             
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
         
        try { 
         
            //Preview the LCA 
            final Document newDoc = appClient.previewLCA(doc); 
                     
        } catch (ApplicationManagerClientException e) { 
            e.printStackTrace();     
        } 
    } 
}
```

## 快速入門（SOAP模式）：使用Java API {#quick-start-soap-mode-deleting-the-application-archive-using-the-java-api}刪除應用程式歸檔檔案

以下Java代碼示例用於刪除應用程式存檔。

```as3
/* 
 * This Java Quick Start uses the SOAP mode and contains the following JAR files 
 * in the class path: 
 * 1. adobe-livecycle-client.jar 
 * 2. adobe-usermanager-client.jar 
 * 3. adobe-application-remote-client.jar 
 * 4. activation.jar (required for SOAP mode) 
 * 5. axis.jar (required for SOAP mode) 
 * 6. commons-codec-1.3.jar (required for SOAP mode) 
 * 7. commons-collections-3.1.jar  (required for SOAP mode) 
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
 * 
 * SOAP required JAR files are located in the following path: 
 * <install directory>/sdk/client-libs/thirdparty 
 * 
 * 
 */ 
package com.adobe.idp.dsc.applicationmanager; 
 
import java.io.FileInputStream; 
import java.util.Properties; 
 
import com.adobe.idp.Document; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClient; 
import com.adobe.livecycle.applicationmanager.client.ApplicationManagerClientException; 
 
public class DeleteApplication_SOAP { 
 
    public static void main(String[] args) { 
        //Set connection properties required to invoke AEM Forms 
        Properties connectionProps = new Properties(); 
        connectionProps.setProperty("DSC_DEFAULT_SOAP_ENDPOINT", "https://[server]:[port]"); 
        connectionProps.setProperty("DSC_TRANSPORT_PROTOCOL", ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);          
        connectionProps.setProperty("DSC_SERVER_TYPE", "JBoss"); 
        connectionProps.setProperty("DSC_CREDENTIAL_USERNAME", "administrator"); 
        connectionProps.setProperty("DSC_CREDENTIAL_PASSWORD", "password"); 
 
        //Create ServiceClientFactory object 
        ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
        //Create ApplicationManagerClient object 
        ApplicationManagerClient appClient = new ApplicationManagerClient(myFactory); 
         
        Document doc = null; 
        try { 
             
            final FileInputStream fileApp = new FileInputStream("C:\\appraisal.lca"); 
            doc = new Document(fileApp); 
             
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
         
        try { 
         
            //Import the application into the LC server 
            final String resourceID = appClient.importApplication(doc); 
            System.out.println("Import application with resource ID: " + resourceID + " is completed successfully!"); 
         
        } catch (ApplicationManagerClientException e) { 
            e.printStackTrace();     
        } 
        final String sampleAppName = "Samples - Performance Appraisal"; 
        try { 
                //Delete the application imported above 
                appClient.deleteApplication(sampleAppName, "1.0"); 
                System.out.println("Delete application completed with name: " + sampleAppName); 
                 
        } catch (Exception e) { 
            e.printStackTrace(); 
        } 
    } 
}
```

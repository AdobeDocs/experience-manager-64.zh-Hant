---
title: 備份和還原服務APIQ快速啟動
seo-title: Backup and Restore Service APIQuick Starts
description: 使用「備份和還原服務API」，使用「Java API快速入門」進入和離開備份模式。
seo-description: Use the Backup and Restore Service API to enter and leave backup mode using the Java API Quick Start.
uuid: c3992be2-ceb4-480d-9c8f-71eb0ea66dde
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 813162be-dbf5-4dc1-80ff-e37dbc25ef60
role: Developer
exl-id: b4fa018f-48a6-4991-9f80-d2d6e0b30555
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 1%

---

# 備份和恢復服務API快速啟動 {#backup-and-restore-service-apiquick-starts}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Java API快速入門(SOAP)適用於備份和還原服務API。

[快速入門：使用Java API(SOAP)進入備份模式](backup-restore-service-api-quick.md#quick-start-soap-mode-entering-backup-mode-using-the-java-api)

[快速入門：使用Java API(SOAP)離開備份模式](backup-restore-service-api-quick.md#quick-start-soap-mode-leaving-backup-mode-using-the-java-api)

AEM Forms操作可使用AEM Forms強制類型API來執行，且連線模式應設為SOAP。

>[!NOTE]
>
>AEM Forms程式設計中的快速入門是以Forms作業系統為基礎。 但是，如果您使用其他作業系統（如UNIX），請用適用作業系統支援的路徑取代Windows專用路徑。 同樣，如果您正在使用其他J2EE應用程式伺服器，請確保指定有效的連接屬性。 請參閱 [設定連接屬性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## 快速入門（SOAP模式）:使用Java API進入備份模式 {#quick-start-soap-mode-entering-backup-mode-using-the-java-api}

以下Java代碼示例進入備份模式，並且標籤唯一，時間為兩小時。 備份時間過期後，或者如果備份模式被顯式退出，表單伺服器將返回從全局文檔儲存中清除檔案。 (請參閱 [在表單伺服器上進入備份模式](/help/forms/developing/preparing-aem-forms-backup.md#entering-backup-mode-on-the-forms-server).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-backup-restore-client-sdk.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. activation.jar (required for SOAP mode) 
     * 5. axis.jar (required for SOAP mode) 
     * 6. commons-codec-1.3.jar (required for SOAP mode) 
     * 7. commons-collections-3.2.jar  (required for SOAP mode) 
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
  
 import com.adobe.idp.backup.dsc.client.BackupServiceClient; 
 import com.adobe.idp.backup.dsc.service.BackupModeEntryResult; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class BackupRestoreEnter 
 { 
     public static void main(String[] args)  
     { 
         try 
         { 
             // Set connection properties required to invoke AEM Forms 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL, ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, ServiceClientFactoryProperties.DSC_JBOSS_SERVER_TYPE); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME,"administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
  
             // Create a ServiceClientFactory instance 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             // Create a BackupService client object 
             BackupServiceClient backup = new BackupServiceClient(myFactory); 
              
             // Specify a generic label, 120 minutes to perform the backup,  
             // and not to provide continous backup mode coverage (used for snapshot backups) 
             String backUpLabel = new String("Snapshot2008July01"); 
             int minsInBackupMode = 120; 
             boolean continousCoverage = false; 
              
              
             // Enter backup mode on the forms server server 
             BackupModeEntryResult backupResult = backup.enterBackupMode(backUpLabel,minsInBackupMode, continousCoverage); 
              

             // Get information from entering backup mode on the forms server. 
             if (backupResult != null) 
             {     
                 System.out.println("Start time is: " + backupResult.getStartTime()); 
                 System.out.println("Backup Current ID is: " + backupResult.getId()); 
                 System.out.println("Backup Previous ID is: " + backupResult.getPreviousReservationId()); 
                 System.out.println("Backup Label is: " + backupResult.getLabel()); 
                 System.out.println("Backup Time to complete is: " + backupResult.getReservationTimeout()); 
             } 
             else 
             { 
                 System.out.println("Could not enter backup mode."); 
             } 
                              
         } 
         catch (Exception e)  
         { 
             e.printStackTrace(); 
         } 
         return; 
     }  
 } 
 
```

## 快速入門（SOAP模式）:使用Java API離開備份模式 {#quick-start-soap-mode-leaving-backup-mode-using-the-java-api}

以下Java代碼示例明確導致Forms伺服器退出備份模式並返回從全局文檔儲存中清除檔案。 (請參閱 [在表單伺服器上保留備份模式](/help/forms/developing/preparing-aem-forms-backup.md#leaving-backup-mode-on-the-forms-server).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-backup-restore-client-sdk.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 4. activation.jar (required for SOAP mode) 
     * 5. axis.jar (required for SOAP mode) 
     * 6. commons-codec-1.3.jar (required for SOAP mode) 
     * 7. commons-collections-3.2.jar  (required for SOAP mode) 
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
  
 import com.adobe.idp.backup.dsc.client.BackupServiceClient; 
 import com.adobe.idp.backup.dsc.service.BackupModeResult; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class BackupRestoreLeave  
 { 
      
     public static void main(String[] args) 
     { 
         try 
         { 
             //Set connection properties required to invoke AEM Forms 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[host]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL, ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, ServiceClientFactoryProperties.DSC_JBOSS_SERVER_TYPE); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME,"administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
  
             // Create a ServiceClientFactory instance 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             // Create a BackupService object 
             BackupServiceClient backup = new BackupServiceClient(myFactory); 
                      
             // Leave backup mode on the forms server 
             BackupModeResult leaveBackupResult = backup.leaveBackupMode(); 
              
             //Get result information from leaving backup mode 
             if (leaveBackupResult != null) 
             { 
                 System.out.println("Backup Mode ID is : " + leaveBackupResult.getId()); 
             } 
             else 
             { 
                 System.out.println("Forms server is not in backup mode."); 
             }         
      
         } 
         catch (Exception e)  
         { 
             e.printStackTrace(); 
         } 
         return; 
     } 
 } 
 
```

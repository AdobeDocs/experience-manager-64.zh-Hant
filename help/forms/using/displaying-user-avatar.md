---
title: 顯示使用者頭像
seo-title: 顯示使用者頭像
description: 如何自訂AEM Forms工作區以顯示登入使用者的影像。
seo-description: 如何自訂AEM Forms工作區以顯示登入使用者的影像。
uuid: 2961dc93-f0d0-4842-80f1-3c239a20e348
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: aec03ea5-17a6-4775-92cb-2ad361895fdf
exl-id: 2bc70cd6-1ea6-4594-9b42-ab3d3000a0c5
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# 顯示用戶頭像{#displaying-the-user-avatar}

登入使用者的頭像會顯示在AEM Forms工作區的右上角。 此外，組織階層中直接報表的變數會顯示在「管理員檢視」中。 您可以配置AEM Forms工作區，從資料庫（如LDAP伺服器）中挑選用戶映像。

>[!NOTE]
>
>支援的使用者影像長寬比為1:1。

1. 使用下一步驟提及的詳細資訊建立DSC。 如需詳細資訊，請參閱[使用AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63)寫程式指南中的「開發AEM Forms的元件」主題。
1. 在DSC中，定義新的SPI，此SPI會公開getCurrentUserImageUrl和getUserImageUrl方法，以取得AEM Forms使用者的影像URL。 以下是範例Java™程式碼片段：

   ```as3
   public class DemoUserImageURLProviderService { 
     public String getCurrentUserImageUrl() 
     { 
        // return the URL for profile Image of logged in user 
     } 
     public String getUserImageUrl(String principalOid) 
     { 
         // return the URL for profile Image for user represented by this principal Oid 
      } 
   }
   ```

1. 建立元件.xml檔案。 請確定規格ID如下列程式碼片段所示。

   下列程式碼片段為範例。 自訂以符合您的特定需求。

   ```as3
   <component xmlns="https://adobe.com/idp/dsc/component/document"> 
       <component-id>com.adobe.sample.DemoUsersComponent</component-id> 
       <version>1.1</version> 
       <supports-export>false</supports-export> 
       <descriptor-class>com.adobe.idp.dsc.component.impl.DefaultPOJODescriptorImpl</descriptor-class> 
       <services> 
           <service name="DemoUserImageURLProviderService" title="Demo User ImageURL provider service" orchestrateable="false"> 
           <auto-deploy service-id="DemoUserImageURLProviderService" category-id="Demo Users Component DSC" major-version="1" minor-version="0" /> 
           <description>Service for resolving user image url.</description> 
            <specifications> 
            <specification spec-id="com.adobe.idp.taskmanager.dsc.enterprise.UserImageUrlProvider"/> 
            </specifications> 
           <specification-version>1.0</specification-version> 
           <implementation-class>com.adobe.sample.demousers.DemoUserImageURLProviderService</implementation-class> 
           <request-processing-strategy>single_instance</request-processing-strategy> 
           <supported-connectors>default</supported-connectors> 
           <operation-config> 
               <operation-name>*</operation-name> 
               <transaction-type>Container</transaction-type> 
               <transaction-propagation>supports</transaction-propagation> 
               <!--transaction-timeout>3000</transaction-timeout--> 
           </operation-config> 
           <operations> 
               <operation anonymous-access="false" name="getCurrentUserImageUrl" method="getCurrentUserImageUrl"> 
                   <output-parameter name="result" type="java.lang.String"/> 
               </operation> 
               <operation anonymous-access="false" name="getUserImageUrl" 
   method="getUserImageUrl"> 
               <input-parameter name="principalOid" type="java.lang.String"/> 
               <output-parameter name="result" type="java.lang.String"/> 
               </operation> 
           </operations> 
           </service> 
       </services>
   </component>
   ```

1. 透過Workbench部署DSC。 重新啟動`ProcessManagementClientSessionService`服務。
1. 您可能需要重新整理瀏覽器，或重新登出/登入使用者。

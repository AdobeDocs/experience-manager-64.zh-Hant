---
title: 建立可呈現Forms的Web應用程式
seo-title: 建立可呈現Forms的Web應用程式
description: 建立使用Java servlet來叫用Forms服務及轉譯表單的網頁型應用程式。 Java servlet可作為傳回表單的Forms服務與用戶端網頁瀏覽器之間的連結。
seo-description: 建立使用Java servlet來叫用Forms服務及轉譯表單的網頁型應用程式。 Java servlet可作為傳回表單的Forms服務與用戶端網頁瀏覽器之間的連結。
uuid: 00de10c5-79bd-4d8a-ae18-32f1fd2623bf
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: f29b089e-8902-4744-81c5-15ee41ba8069
role: Developer
exl-id: f77796ff-f5c9-455f-8616-fa590db7fdbe
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1912'
ht-degree: 0%

---

# 建立可呈現Forms {#creating-web-applications-thatrenders-forms}的Web應用程式

## 建立可呈現Forms {#creating-web-applications-that-renders-forms}的Web應用程式

您可以建立使用Java servlet來叫用Forms服務及轉譯表單的網頁型應用程式。 使用Java™ servlet的一個好處是可以將進程的返回值寫入客戶端Web瀏覽器。 也就是說，Java servlet可作為傳回表單的Forms服務與用戶端網頁瀏覽器之間的連結。

>[!NOTE]
>
>本節說明如何建立使用Java servlet的網頁型應用程式，此Java servlet會叫用Forms服務並轉譯以片段為基礎的表單。 (請參閱[根據片段呈現Forms](/help/forms/developing/rendering-forms-based-fragments.md)。)

使用Java servlet，您可以將表單寫入客戶端Web瀏覽器，以便客戶查看表單並在表單中輸入資料。 使用資料填入表單後，Web使用者按一下表單上的提交按鈕，將資訊傳回Java Servlet，以便擷取和處理資料。 例如，資料可傳送至其他程式。

本節探討如何建立基於Web的應用程式，以便用戶選擇基於美國的表單資料或基於加拿大的表單資料，如下圖所示。

![cw_cw_fragmentwebclient](assets/cw_cw_fragmentwebclient.png)

呈現的表單是以片段為基礎的表單。 也就是說，如果使用者選取美國資料，則傳回的表單會根據美國資料使用片段。 例如，表單的頁尾包含美國地址，如下圖所示。

![cw_cw_framementfooter](assets/cw_cw_fragementformfooter.png)

同樣，如果用戶選擇加拿大資料，則返回的表單包含加拿大地址，如下圖所示。

![cw_cw_framementformfootercnd](assets/cw_cw_fragementformfootercnd.png)

>[!NOTE]
>
>如需根據片段建立表單設計的相關資訊，請參閱[Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63)。

**範例檔案**

本節使用的範例檔案可位於下列位置：

&lt;>Forms Designer安裝目錄&#x200B;*>/範例/Forms/採購訂單/表單片段*

其中&lt;*install directory*>是安裝路徑。 為了客戶端應用程式的目的，從此安裝位置複製了Purchase Order Dynamic.xdp檔案，並部署到名為&#x200B;*Applications/FormsApplication*&#x200B;的Forms應用程式。 採購訂單Dynamic.xdp檔案被放在名為FormsFolder的資料夾中。 同樣地，片段會放置在名為「片段」的資料夾中，如下圖所示。

![cw_cw_fragments儲存庫](assets/cw_cw_fragmentsrepository.png)

要訪問Purchase Order Dynamic.xdp表單設計，請指定`Applications/FormsApplication/1.0/FormsFolder/Purchase Order Dynamic.xdp`作為表單名稱（傳遞到`renderPDFForm`方法的第一個參數），指定`repository:///`作為內容根URI值。

Web應用程式使用的XML資料檔案已從Data資料夾移至`C:\Adobe`(屬於托管AEM Forms的J2EE應用程式伺服器的檔案系統)。 檔案名為採購訂單&#x200B;*Canada.xml*&#x200B;和採購訂單&#x200B;*US.xml*。

>[!NOTE]
>
>如需使用Workbench建立Forms應用程式的相關資訊，請參閱[Workbench說明](https://www.adobe.com/go/learn_aemforms_workbench_63)。

### 步驟{#summary-of-steps}的摘要

要建立基於Web的應用程式，以根據片段來呈現表單，請執行以下步驟：

1. 建立新的Web專案。
1. 建立代表Java servlet的Java應用程式邏輯。
1. 為Web應用程式建立網頁。
1. 將Web應用程式打包為WAR檔案。
1. 將WAR檔案部署到J2EE應用伺服器。
1. 測試您的Web應用程式。

>[!NOTE]
>
>其中有些步驟取決於部署了AEM Forms的J2EE應用程式。 例如，您用來部署WAR檔案的方法取決於您使用的J2EE應用程式伺服器。 本節假設已在JBoss®上部署AEM Forms。

### 建立Web項目{#creating-a-web-project}

要建立包含可叫用Forms服務的Java Servlet的Web應用程式，第一步是建立新的Web項目。 本文檔所基於的Java IDE是Eclipse 3.3。使用Eclipse IDE，建立Web項目，並將所需的JAR檔案添加到項目中。 最後，將名為&#x200B;*index.html*&#x200B;的HTML頁面和Java servlet新增至您的專案。

以下清單指定必須添加到Web項目的JAR檔案：

* adobe-forms-client.jar
* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar

有關這些JAR檔案的位置，請參閱[包括AEM Forms Java庫檔案](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)。

**要建立Web項目，請執行以下操作：**

1. 啟動Eclipse，然後按一下&#x200B;**File** > **New Project**。
1. 在&#x200B;**新建項目**&#x200B;對話框中，選擇&#x200B;**Web** > **動態Web項目**。
1. 鍵入`FragmentsWebApplication`作為項目名稱，然後按一下&#x200B;**完成**。

**要向項目添加所需的JAR檔案，請執行以下操作：**

1. 在「項目資源管理器」窗口中，按一下右鍵`FragmentsWebApplication`項目並選擇&#x200B;**屬性**。
1. 按一下&#x200B;**Java組建路徑**，然後按一下&#x200B;**Libraries**&#x200B;標籤。
1. 按一下&#x200B;**添加外部JAR**&#x200B;按鈕，然後瀏覽到要包含的JAR檔案。

**若要將Java servlet新增至專案：**

1. 在「項目資源管理器」窗口中，按一下右鍵`FragmentsWebApplication`項目，然後選擇&#x200B;**New** > **Other**。
1. 展開&#x200B;**Web**&#x200B;資料夾，選擇&#x200B;**Servlet**，然後按一下&#x200B;**Next**。
1. 在「建立Servlet」對話框中，鍵入`RenderFormFragment`作為servlet的名稱，然後按一下&#x200B;**完成**。

**若要新增HTML頁面至您的專案：**

1. 在「項目資源管理器」窗口中，按一下右鍵`FragmentsWebApplication`項目，然後選擇&#x200B;**New** > **Other**。
1. 展開&#x200B;**Web**&#x200B;資料夾，選擇&#x200B;**HTML**，然後按一下&#x200B;**Next**。
1. 在「新建HTML」對話框中，鍵入檔案名`index.html`，然後按一下&#x200B;**完成**。

>[!NOTE]
>
>有關建立調用`RenderFormFragment` Java servlet的HTML頁的資訊，請參閱[建立網頁](/help/forms/developing/rendering-forms.md#creating-the-web-page)。

### 為servlet {#creating-java-application-logic-for-the-servlet}建立Java應用程式邏輯

您可以建立Java應用程式邏輯，從Java servlet內叫用Forms服務。 以下代碼顯示`RenderFormFragment` Java Servlet的語法：

```as3
     public class RenderFormFragment extends HttpServlet implements Servlet { 
         public void doGet(HttpServletRequest req, HttpServletResponse resp 
         throws ServletException, IOException { 
         doPost(req,resp); 
          
         } 
         public void doPost(HttpServletRequest req, HttpServletResponse resp 
         throws ServletException, IOException { 
             //Add code here to invoke the Forms service 
             }
```

通常，您不會將用戶端代碼放在Java servlet的`doGet`或`doPost`方法中。 更好的寫程式做法是將此代碼放置在單獨的類中，從`doPost`方法（或`doGet`方法）中實例化類，並調用相應的方法。 不過，為了簡化程式碼，本區段中的程式碼範例會維持在最小值，且程式碼範例會放置在`doPost`方法中。

若要使用Forms服務API根據片段轉譯表單，請執行下列工作：

1. 在Java專案的類別路徑中加入用戶端JAR檔案，例如adobe-forms-client.jar。 有關這些檔案的位置資訊，請參閱[包含AEM Forms Java庫檔案](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)。
1. 擷取從HTML表單提交之選項按鈕的值，並指定使用美國或加拿大資料。 如果提交了American，請建立`com.adobe.idp.Document`以儲存位於&#x200B;*採購訂單US.xml*&#x200B;中的資料。 同樣，如果是加拿大，則建立一個`com.adobe.idp.Document`，該&#x200B;*儲存位於 Purchase Order Canada.xml*&#x200B;檔案中的資料。
1. 建立包含連接屬性的`ServiceClientFactory`對象。 （請參閱[設定連接屬性](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)。）
1. 使用其建構子並傳遞`ServiceClientFactory`物件，以建立`FormsServiceClient`物件。
1. 建立`URLSpec`對象，該對象使用其建構子儲存URI值。
1. 叫用`URLSpec`物件的`setApplicationWebRoot`方法，並傳遞代表應用程式Web根的字串值。
1. 調用`URLSpec`對象的`setContentRootURI`方法並傳遞指定內容根URI值的字串值。 請確定表單設計和片段位於內容根URI中。 否則，Forms服務會擲回例外狀況。 若要參考AEM Forms存放庫，請指定`repository://`。
1. 叫用`URLSpec`物件的`setTargetURL`方法，並傳遞字串值，指定將表單資料張貼到的目標URL值。 如果您在表單設計中定義目標URL，則可以傳遞空字串。 您也可以指定表單要傳送到哪個URL，以執行計算。
1. 調用`FormsServiceClient`對象的`renderPDFForm`方法並傳遞以下值：

   * 指定表單設計名稱的字串值，包括檔案名副檔名。
   * `com.adobe.idp.Document`物件，包含要與表單合併的資料（在步驟2中建立）。
   * 儲存運行時選項的`PDFFormRenderSpec`對象。 如需詳細資訊，請參閱[AEM Forms API參考](https://www.adobe.com/go/learn_aemforms_javadocs_63_en)。
   * `URLSpec`物件，包含Forms服務根據片段轉譯表單所需的URI值。
   * 儲存檔案附件的`java.util.HashMap`對象。 這是可選參數，如果不想將檔案附加到表單，可以指定`null`。

   `renderPDFForm`方法返回一個`FormsResult`對象，該對象包含必須寫入客戶端Web瀏覽器的表單資料流。

1. 調用`FormsResult`對象s `getOutputContent`方法，建立`com.adobe.idp.Document`對象。
1. 調用`getContentType`方法，獲取`com.adobe.idp.Document`對象的內容類型。
1. 通過調用`setContentType`方法並傳遞`com.adobe.idp.Document`對象的內容類型來設定`javax.servlet.http.HttpServletResponse`對象的內容類型。
1. 通過調用`javax.servlet.http.HttpServletResponse`對象的`getOutputStream`方法，建立用於將表單資料流寫入客戶端Web瀏覽器的`javax.servlet.ServletOutputStream`對象。
1. 調用`com.adobe.idp.Document`對象的`getInputStream`方法，建立`java.io.InputStream`對象。
1. 叫用`InputStream`物件的`read`方法並將位元組陣列傳遞為引數，以填入表單資料流的位元組陣列。
1. 調用`javax.servlet.ServletOutputStream`對象的`write`方法，將表單資料流發送到客戶端Web瀏覽器。 將位元組陣列傳遞至`write`方法。

下列程式碼範例代表叫用Forms服務並根據片段轉譯表單的Java servlet。

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-forms-client.jar 
     * 2. adobe-livecycle-client.jar 
     * 3. adobe-usermanager-client.jar 
     * 
     * (Because Forms quick starts are implemented as Java servlets, it is  
     * not necessary to include J2EE specific JAR files - the Java project 
     * that contains this quick start is exported as a WAR file which 
     * is deployed to the J2EE application server) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs 
     * 
     * For complete details about the location of these JAR files,  
     * see "Including AEM Forms library files" in Programming with AEM forms 
     */ 
 import java.io.File; 
 import java.io.FileInputStream; 
 import java.io.IOException; 
 import java.io.PrintWriter; 
  
 import javax.servlet.Servlet; 
 import javax.servlet.ServletException; 
 import javax.servlet.ServletOutputStream; 
 import javax.servlet.http.HttpServlet; 
 import javax.servlet.http.HttpServletRequest; 
 import javax.servlet.http.HttpServletResponse; 
 import com.adobe.livecycle.formsservice.client.*; 
 import java.util.*; 
 import java.io.InputStream; 
 import java.net.URL; 
  
 import com.adobe.idp.Document; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class RenderFormFragment extends HttpServlet implements Servlet { 
      
     public void doGet(HttpServletRequest req, HttpServletResponse resp) 
         throws ServletException, IOException { 
             doPost(req,resp);  
  
     } 
     public void doPost(HttpServletRequest req, HttpServletResponse resp) 
     throws ServletException, IOException { 
          
          
              
         try{ 
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             //Get the value of selected radio button 
             String radioValue = req.getParameter("radio"); 
              
             //Create an Document object to store form data 
             Document oInputData = null;  
              
             //The value of the radio button determines the form data to use 
             //which determines which fragments used in the form 
             if (radioValue.compareTo("AMERICAN") == 0)            { 
                 FileInputStream myData = new FileInputStream("C:\\Adobe\Purchase Order US.xml"); 
                 oInputData = new Document(myData);  
             } 
             else if (radioValue.compareTo("CANADIAN") == 0)            { 
                 FileInputStream myData = new FileInputStream("C:\\Adobe\Purchase Order Canada.xml"); 
                 oInputData = new Document(myData);  
             } 
                      
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
                  
             //Create a FormsServiceClient object 
             FormsServiceClient formsClient = new FormsServiceClient(myFactory);  
          
             //Set the parameter values for the renderPDFForm method 
             String formName = "Applications/FormsApplication/1.0/FormsFolder/Purchase Order Dynamic.xdp";   
                                      
             //Cache the PDF form 
             PDFFormRenderSpec pdfFormRenderSpec = new PDFFormRenderSpec(); 
             pdfFormRenderSpec.setCacheEnabled(new Boolean(true)); 
          
             //Specify URI values that are required to render a form 
             //design based on fragments 
             URLSpec uriValues = new URLSpec();  
             uriValues.setApplicationWebRoot("https://[server]:[port]/RenderFormFragment"); 
             uriValues.setContentRootURI("repository:///"); 
             uriValues.setTargetURL("https://[server]:[port]/FormsServiceClientApp/HandleData"); 
                      
             //Invoke the renderPDFForm method and write the  
             //results to a client web browser 
             FormsResult formOut = formsClient.renderPDFForm( 
                         formName,               //formQuery 
                         oInputData,             //inDataDoc 
                         pdfFormRenderSpec,      //PDFFormRenderSpec 
                         uriValues,                //urlSpec 
                         null                    //attachments 
                         ); 
          
             //Create a Document object that stores form data 
             Document myData = formOut.getOutputContent(); 
          
             //Get the content type of the response and 
             //set the HttpServletResponse object’s content type 
             String contentType = myData.getContentType();  
             resp.setContentType(contentType); 
          
             //Create a ServletOutputStream object 
             ServletOutputStream oOutput = resp.getOutputStream(); 
          
             //Create an InputStream object 
             InputStream inputStream = myData.getInputStream(); 
          
             //Write the data stream to the web browser 
             byte[] data = new byte[4096]; 
             int bytesRead = 0; 
             while ((bytesRead = inputStream.read(data)) > 0) 
             { 
                 oOutput.write(data, 0, bytesRead); 
             } 
      
         }catch (Exception e) { 
              System.out.println("The following exception occurred: "+e.getMessage()); 
       } 
     } 
 }
```

### 建立網頁{#creating-the-web-page}

index.html網頁提供Java servlet的入口點，並叫用Forms服務。 此網頁是基本HTML表單，包含兩個選項按鈕和一個提交按鈕。 選項按鈕的名稱為選項。 當用戶按一下提交按鈕時，表單資料將發佈到`RenderFormFragment` Java servlet。

Java servlet會使用下列Java代碼從HTML頁面擷取發佈的資料：

```as3
             Document oInputData = null;  
              
             //Get the value of selected radio button 
             String radioValue = req.getParameter("radio"); 
                          
             //The value of the radio button determines the form data to use 
             //which determines which fragments used in the form 
             if (radioValue.compareTo("AMERICAN") == 0)            { 
                 FileInputStream myData = new FileInputStream("C:\\Adobe\Purchase Order US.xml"); 
                 oInputData = new Document(myData);  
             } 
             else if (radioValue.compareTo("CANADIAN") == 0)            { 
                 FileInputStream myData = new FileInputStream("C:\\Adobe\Purchase Order Canada.xml"); 
                 oInputData = new Document(myData);  
             }
```

下列HTML程式碼位於設定開發環境期間建立的index.html檔案中。 （請參閱[建立Web項目](/help/forms/developing/rendering-forms.md#creating-a-web-project)。）

```as3
 <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "https://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 
 <html xmlns="https://www.w3.org/1999/xhtml"> 
 <head> 
 <meta http-equiv="Content-Type" content="text/html; charset=utf-8" /> 
 <title>Untitled Document</title> 
 </head> 
  
 <body> 
 <form name="myform" action="https://[server]:[port]/FragmentsWebApplication/RenderFormFragment" method="post"> 
      <table> 
      <tr> 
        <th>Forms Fragment Web Client</th> 
      </tr> 
      <tr> 
        <td> 
          <label> 
          <input type="radio" name="radio" id="radio_Data" value="CANADIAN" /> 
          Canadian data<br /> 
          </label> 
          <p> 
            <label> 
            <input type="radio" name="radio" id="radio_Data" value="AMERICAN" checked/> 
            American data</label> 
          </p> 
        </td> 
      </tr> 
      <tr> 
      <td> 
        <label> 
          <input type="submit" name="button_Submit" id="button_Submit" value="Submit" /> 
            </label> 
            </td> 
         </tr> 
        </table> 
      </form>     
 </body> 
 </html>
```

### 打包Web應用程式{#packaging-the-web-application}

要部署調用Forms服務的Java servlet，請將Web應用程式打包到WAR檔案。 請確定元件商業邏輯所依賴的外部JAR檔案，例如adobe-livecycle-client.jar和adobe-forms-client.jar，也包含在WAR檔案中。

**要將Web應用程式打包為WAR檔案，請執行以下操作：**

1. 在&#x200B;**Project Explorer**&#x200B;窗口中，按一下右鍵`FragmentsWebApplication`項目並選擇&#x200B;**Export** > **WAR檔案**。
1. 在&#x200B;**Web模組**&#x200B;文本框中，鍵入`FragmentsWebApplication`作為Java項目的名稱。
1. 在&#x200B;**目標**&#x200B;文本框中，鍵入&#x200B;`FragmentsWebApplication.war`**作為**&#x200B;檔案名，指定WAR檔案的位置，然後按一下完成。

### 將WAR檔案部署到J2EE應用程式伺服器{#deploying-the-war-file-to-the-j2ee-application-server}

您可以將WAR檔案部署到部署了AEM Forms的J2EE應用程式伺服器。 部署WAR檔案後，可使用Web瀏覽器訪問HTML網頁。

**要將WAR檔案部署到J2EE應用伺服器，請執行以下操作：**

* 將WAR檔案從導出路徑複製到&#x200B;*[Forms Install]*\Adobe\Adobe Experience Manager Forms\jboss\server\all\deploy。

### 測試Web應用程式{#testing-your-web-application}

部署Web應用程式後，可以使用Web瀏覽器進行測試。 假設您使用的電腦與托管AEM Forms的電腦相同，您可以指定下列URL:

* http://localhost:8080/FragmentsWebApplication/index.html

   選擇單選按鈕，然後按一下「提交」按鈕。 網頁瀏覽器中將會顯示以片段為基礎的表單。 如果出現問題，請參閱J2EE應用程式伺服器的日誌檔案。

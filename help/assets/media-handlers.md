---
title: 使用媒體處理常式和工作流程處理資產
description: 瞭解各種媒體處理常式，以及如何在工作流程中使用它們來執行資產上的工作。
contentOwner: AG
translation-type: tm+mt
source-git-commit: b6342b79e964daf1a05bb9ccfad06d8edaca4312
workflow-type: tm+mt
source-wordcount: '2228'
ht-degree: 3%

---


# 處理資產使用媒體處理常式和工作流程{#processing-assets-using-media-handlers-and-workflows}

Adobe Experience Manager資產提供一組預設工作流程和媒體處理常式，以處理資產。 工作流程會定義典型的資產管理和處理工作，然後將特定工作委派給媒體處理常式，例如縮圖產生或中繼資料擷取。

可以定義工作流，當特定類型或格式的資產上傳至伺服器時自動執行。 這些處理步驟被定義為一系列Experience ManagerAssets媒體處理常式。 Adobe Experience Manager提供一些內建的[處理常式、](#default-media-handlers)等，可以是[自訂開發的](#creating-a-new-media-handler)，或將程式委託給[命令列工具](#command-line-based-media-handler)來定義。

媒體處理常式是Experience Manager資產內的服務，可對資產執行特定動作。 例如，當MP3音訊檔案上傳至Experience Manager時，工作流程會觸發MP3處理常式，以擷取中繼資料並產生縮圖。 媒體處理常式與工作流程搭配使用。 Experience Manager中支援最常見的MIME類型。 您可以執行下列任一項作業，對資產執行特定工作

* 擴充或建立工作流程。
* 擴充或建立媒體處理常式。
* 禁用或啟用媒體處理程式。

>[!NOTE]
>
>請參閱[Assets supported formats](assets-formats.md)頁面，以取得說明Experience Manager資產支援的所有格式以及每種格式支援的功能。

## 預設媒體處理程式{#default-media-handlers}

下列媒體處理常式可用於Experience Manager資產並處理最常見的MIME類型：

| 處理常式名稱 | 服務名（在系統控制台中） | 支援的MIME類型 |
|---|---|---|
| [!UICONTROL TextHandler] | com.day.cq.dam.core.impl.handler.TextHandler | text/plain |
| [!UICONTROL PdfHandler] | com.day.cq.dam.handler.standard.pdf.PdfHandler | <ul><li>application/pdf</li><li>application/illustrator</li></ul> |
| [!UICONTROL JpegHandler] | com.day.cq.dam.core.impl.handler.JpegHandler | image/jpeg |
| [!UICONTROL Mp3Handler] | com.day.cq.dam.handler.standard.mp3.Mp3Handler | audio/mpeg<br><b>Importent</b> —— 當您上傳MP3檔案時，會使用協力廠商程式庫](http://www.zxdr.it/programmi/SistEvolBDD/LibJava/doc/de/vdheide/mp3/MP3File.html)加以處理。 [如果MP3具有可變位元速率(VBR)，程式庫會計算非精確的近似長度。 |
| [!UICONTROL ZipHandler] | com.day.cq.dam.handler.standard.zip.ZipHandler | <ul><li>application/java-archive </li><li> application/zip</li></ul> |
| [!UICONTROL PictHandler] | com.day.cq.dam.handler.standard.pict.PictHandler | image/pict |
| [!UICONTROL StandardImageHandler] | com.day.cq.dam.core.impl.handler.StandardImageHandler | <ul><li>image/gif </li><li> image/png </li> <li>application/photoshop </li> <li>image/jpeg </li><li> image/tiff </li> <li>image/x-ms-bmp </li><li> image/bmp</li></ul> |
| [!UICONTROL MSOfficeHandler] | com.day.cq.dam.handler.standard.msoffice.MSOfficeHandler | application/msword |
| [!UICONTROL MSPowerPointHandler] | com.day.cq.dam.handler.standard.msoffice.MSPowerPointHandler | application/vnd.ms-powerpoint |
| [!UICONTROL OpenOfficeHandler] | com.day.cq.dam.handler.standard.ooxml.OpenOfficeHandler | <ul><li>application/vnd.openxmlformats-officedocument.wordprocessingml.document</li><li> application/vnd.openxmlformats-officedocument.spreadsheetml.sheet</li><li> application/vnd.openxmlformats-officedocument.presentationml.presentation</li></ul> |
| [!UICONTROL EPubHandler] | com.day.cq.dam.handler.standard.epub.EPubHandler | application/epub+zip |
| [!UICONTROL GenericAssetHandler] | com.day.cq.dam.core.impl.handler.GenericAssetHandler | 回退，以備找不到其他處理常式來擷取資產的資料 |

所有處理程式都執行下列任務：

* 從資產擷取所有可用的中繼資料。
* 從資產建立縮圖影像。

可以查看活動媒體處理程式：

1. 在瀏覽器中，導覽至`http://localhost:4502/system/console/components`。
1. 按一下連結`com.day.cq.dam.core.impl.store.AssetStoreImpl`。
1. 將顯示包含所有活動媒體處理程式的清單。 例如：

![chlimage_1-437](assets/chlimage_1-437.png)

## 在工作流程中使用媒體處理常式，對資產{#using-media-handlers-in-workflows-to-perform-tasks-on-assets}執行工作

媒體處理常式是與工作流程搭配使用的服務。

Experience Manager有一些處理資產的預設工作流程。 要查看它們，請開啟「工作流控制台」，然後按一下&#x200B;**[!UICONTROL Models]**&#x200B;頁籤：以「Experience Manager資產」開頭的工作流程標題是資產特定標題。

可擴充現有的工作流程，並建立新的工作流程，以根據特定需求處理資產。

下列範例說明如何增強&#x200B;**[!UICONTROL AEM Assets同步]**&#x200B;工作流程，以便為除PDF檔案外的所有資產產生子資產。

### 禁用／啟用媒體處理程式{#disabling-enabling-a-media-handler}

媒體處理常式可以透過Apache Felix Web Management Console停用或啟用。 停用媒體處理常式時，不會對資產執行其工作。

要啟用／禁用媒體處理程式：

1. 在瀏覽器中，導覽至`https://<host>:<port>/system/console/components`。
1. 按一下媒體處理程式名稱旁的&#x200B;**[!UICONTROL 禁用]**。 例如：`com.day.cq.dam.handler.standard.mp3.Mp3Handler`。
1. 重新整理頁面：媒體處理常式旁會顯示圖示，指出其已停用。
1. 要啟用媒體處理程式，請按一下媒體處理程式名稱旁的「啟用」。****

### 建立媒體處理程式{#creating-a-new-media-handler}

要支援新介質類型或對資產執行特定任務，必須建立介質處理程式。 本節說明如何繼續。

#### 重要類和介面{#important-classes-and-interfaces}

開始實施的最佳方式是繼承所提供的抽象實施，以處理大部分事物並提供合理的預設行為：`com.day.cq.dam.core.AbstractAssetHandler`類別。

此類已提供抽象服務描述符。 因此，如果您繼承此類別並使用maven-sling-plugin，請務必將inherit標幟設為`true`。

實施下列方法：

* `extractMetadata()`:擷取所有可用的中繼資料。
* `getThumbnailImage()`:在傳遞的資產中建立縮圖影像。
* `getMimeTypes()`:傳回資產MIME類型。

以下是範例範本：

`package my.own.stuff; /** * @scr.component inherit="true" * @scr.service */ public class MyMediaHandler extends com.day.cq.dam.core.AbstractAssetHandler { // implement the relevant parts } `

介面和類包括：

* `com.day.cq.dam.api.handler.AssetHandler` 介面：此介面說明新增支援特定MIME類型的服務。添加MIME類型需要實施此介面。 介麵包含匯入和匯出特定檔案、建立縮圖和擷取中繼資料的方法。
* `com.day.cq.dam.core.AbstractAssetHandler` 類別：此類別可做為所有其他資產處理常式實作的基礎，並提供常用的功能。
* `com.day.cq.dam.core.AbstractSubAssetHandler` 類別：
   * 此類別可做為所有其他資產處理常式實作的基礎，並提供常用功能以及子資產擷取的常用功能。
   * 開始實施的最佳方式是繼承所提供的抽象實施，以處理大部分事物並提供合理的預設行為：com.day.cq.dam.core.AbstractAssetHandler類別。
   * 此類已提供抽象服務描述符。 因此，如果您繼承此類別並使用maven-sling-plugin，請確定您將inherit標幟設為true。

必須實作下列方法：

* `extractMetadata()`:此方法會擷取所有可用的中繼資料。
* `getThumbnailImage()`:此方法會從傳遞的資產中建立縮圖影像。
* `getMimeTypes()`:此方法會傳回資產MIME類型。

以下是範例範本：

封裝my.own.stuff;/&amp;ast;&amp;ast;&amp;ast;@scr.component inherit=&quot;true&quot; &amp;ast;@scr.service &amp;ast;/ public class MyMediaHandler extends com.day.cq.dam.core.AbstractAssetHandler { // implement relevant parts }

介面和類包括：

* `com.day.cq.dam.api.handler.AssetHandler` 介面：此介面說明為特定MIME類型添加支援的服務。添加MIME類型需要實施此介面。 介麵包含匯入和匯出特定檔案、建立縮圖和擷取中繼資料的方法。
* `com.day.cq.dam.core.AbstractAssetHandler` 類別：此類別可做為所有其他資產處理常式實作的基礎，並提供常用的功能。
* `com.day.cq.dam.core.AbstractSubAssetHandler` 類別：此類別可做為所有其他資產處理常式實作的基礎，並提供常用功能以及子資產擷取的常用功能。

#### 範例：建立特定的文本處理程式{#example-create-a-specific-text-handler}

在本節中，您將建立特定的文字處理常式，以產生含浮水印的縮圖。

按如下步驟進行：

請參閱[開發工具](../sites-developing/dev-tools.md)以安裝並設定Eclipse與Maven外掛程式，以及設定Maven專案所需的相依性。

執行下列步驟後，將txt檔案上載到Experience Manager時，將提取檔案的元資料並生成兩個帶有水印的縮略圖。

1. 在Eclipse中，建立`myBundle` Maven專案：

   1. 在菜單欄中，按一下&#x200B;**[!UICONTROL 檔案>新建>其他]**。
   1. 在對話框中，展開Maven資料夾，選擇Maven Project，然後按一下&#x200B;**[!UICONTROL Next]**。
   1. 選中「建立簡單項目&#x200B;]**」框和「使用預設工作區位置]**」框，然後按一下「下一步」。**[!UICONTROL **[!UICONTROL ****
   1. 使用下列值定義Maven項目：

      * 群組ID:com.day.cq5.myhandler
      * 對象ID:myBundle
      * 名稱：我的Experience Manager包
      * 說明：這是我的Experience Manager包
   1. 按一下&#x200B;**[!UICONTROL 完成]**。


1. 將「Java™編譯器」設定為1.5版：

   1. 按一下右鍵`myBundle`項目，選擇「屬性」。
   1. 選擇「Java™編譯器」，並將下列屬性設定為1.5:

      * 編譯器合規性級別
      * 生成的。class檔案相容性
      * 原始碼相容性
   1. 按一下&#x200B;**[!UICONTROL 「確定」]**。在對話框窗口中，按一下「是」。


1. 將pom.xml檔案中的程式碼取代為下列程式碼：

   ```xml
   <project xmlns="https://maven.apache.org/POM/4.0.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion> 
    <!-- ====================================================================== --> 
    <!-- P A R E N T P R O J E C T D E S C R I P T I O N --> 
    <!-- ====================================================================== -->
    <parent>
     <groupId>com.day.cq.dam</groupId>
     <artifactId>dam</artifactId>
     <version>5.2.14</version>
     <relativePath>../parent</relativePath>
    </parent> 
    <!-- ====================================================================== --> 
    <!-- P R O J E C T D E S C R I P T I O N --> 
    <!-- ====================================================================== -->
    <groupId>com.day.cq5.myhandler</groupId>
    <artifactId>myBundle</artifactId>
    <name>My CQ5 bundle</name>
    <version>0.0.1-SNAPSHOT</version>
    <description>This is my CQ5 bundle</description>
    <packaging>bundle</packaging> 
    <!-- ====================================================================== --> 
    <!-- B U I L D D E F I N I T I O N --> 
    <!-- ====================================================================== -->
    <build>
     <plugins>
      <plugin>
       <groupId>org.apache.felix</groupId>
       <artifactId>maven-scr-plugin</artifactId>
      </plugin>
      <plugin>
       <groupId>org.apache.sling</groupId>
       <artifactId>maven-sling-plugin</artifactId>
       <configuration>
        <slingUrlSuffix>/libs/dam/install/</slingUrlSuffix>
       </configuration>
      </plugin>
      <plugin>
       <groupId>org.apache.felix</groupId>
       <artifactId>maven-bundle-plugin</artifactId>
       <extensions>true</extensions>
       <configuration>
        <instructions>
         <Bundle-Category>cq5</Bundle-Category>
         <Export-Package> com.day.cq5.myhandler </Export-Package>
        </instructions>
       </configuration>
      </plugin>
     </plugins>
    </build> 
    <!-- ====================================================================== --> 
    <!-- D E P E N D E N C I E S --> 
    <!-- ====================================================================== -->
    <dependencies>
     <dependency>
      <groupId>com.day.cq.dam</groupId>
      <artifactId>cq-dam-api</artifactId>
      <version>5.2.10</version>
      <scope>provided</scope>
     </dependency>
     <dependency>
      <groupId>com.day.cq.dam</groupId>
      <artifactId>cq-dam-core</artifactId>
      <version>5.2.10</version>
      <scope>provided</scope>
     </dependency>
     <dependency>
      <groupId>com.day.cq</groupId>
      <artifactId>cq-commons</artifactId>
     </dependency>
     <dependency>
      <groupId>javax.jcr</groupId>
      <artifactId>jcr</artifactId>
     </dependency>
     <dependency>
      <groupId>org.apache.felix</groupId>
      <artifactId>org.osgi.compendium</artifactId>
     </dependency>
     <dependency>
      <groupId>org.slf4j</groupId>
      <artifactId>slf4j-api</artifactId>
     </dependency>
     <dependency>
      <groupId>commons-lang</groupId>
      <artifactId>commons-lang</artifactId>
     </dependency>
     <dependency>
      <groupId>commons-collections</groupId>
      <artifactId>commons-collections</artifactId>
     </dependency>
     <dependency>
      <groupId>commons-io</groupId>
      <artifactId>commons-io</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.commons</groupId>
      <artifactId>day-commons-gfx</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.commons</groupId>
      <artifactId>day-commons-text</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.cq.workflow</groupId>
      <artifactId>cq-workflow-api</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.cq.wcm</groupId>
      <artifactId>cq-wcm-foundation</artifactId>
      <version>5.2.22</version>
     </dependency>
    </dependencies>
   ```

1. 建立包`com.day.cq5.myhandler`，該包包含`myBundle/src/main/java`下的Java™類：

   1. 在myBundle下，按一下右鍵`src/main/java` ，選擇新建，然後選擇包。
   1. 將其命名為`com.day.cq5.myhandler` ，然後按一下「完成」。

1. 建立Java™類`MyHandler` :

   1. 在Eclipse的`myBundle/src/main/java`下，按一下右鍵`com.day.cq5.myhandler`包，選擇新建，然後選擇類。
   1. 在對話框窗口中，為Java™類命名MyHandler，然後按一下「完成」。 Eclipse會建立並開啟檔案MyHandler.java。
   1. 在`MyHandler.java`中，將現有代碼替換為以下代碼，然後保存更改：

   ```java
   package com.day.cq5.myhandler; 
   import java.awt.Color; 
   import java.awt.Rectangle; 
   import java.awt.image.BufferedImage; 
   import java.io.IOException; 
   import java.io.InputStream; 
   import java.io.InputStreamReader; 
   import javax.jcr.Node; 
   import javax.jcr.RepositoryException; 
   import javax.jcr.Session; 
   import org.apache.commons.io.IOUtils; 
   import org.slf4j.Logger; 
   import org.slf4j.LoggerFactory; 
   import com.day.cq.dam.api.metadata.ExtractedMetadata; 
   import com.day.cq.dam.core.AbstractAssetHandler; 
   import com.day.image.Font; 
   import com.day.image.Layer; 
   import com.day.cq.wcm.foundation.ImageHelper; 
   
   /** 
    * The <code>MyHandler</code> can extract text files 
    * @scr.component inherit="true" immediate="true" metatype="false" 
    * @scr.service 
    * 
    **/ 
   
   public class MyHandler extends AbstractAssetHandler { 
    /** * Logger instance for this class. */ 
    private static final Logger log = LoggerFactory.getLogger(MyHandler.class); 
    /** * Music icon margin */ 
    private static final int MARGIN = 10; 
    /** * @see com.day.cq.dam.api.handler.AssetHandler#getMimeTypes() */ 
    public String[] getMimeTypes() {
     return new String[] {"text/plain"}; 
    }
   
    public ExtractedMetadata extractMetadata(Node asset) { 
     ExtractedMetadata extractedMetadata = new ExtractedMetadata(); 
     InputStream data = getInputStream(asset); 
     try { 
      // read text data 
      InputStreamReader reader = new InputStreamReader(data); 
      char[] buffer = new char[4096]; 
      String text = ""; 
      while (reader.read(buffer) != -1) { 
       text += new String(buffer); 
      } 
      reader.close(); 
      long wordCount = this.wordCount(text); 
      extractedMetadata.setProperty("text", text); 
      extractedMetadata.setMetaDataProperty("Word Count",wordCount); 
      setMimetype(extractedMetadata, asset); 
     } catch (Throwable t) { 
      log.error("handling error: " + t.toString(), t); 
     } finally { 
      IOUtils.closeQuietly(data); 
     } 
     return extractedMetadata; } 
    // ----------------------< helpers >---------------------------------------- 
    protected BufferedImage getThumbnailImage(Node node) { 
     ExtractedMetadata metadata = extractMetadata(node); 
     final String text = (String) metadata.getProperty("text"); 
     // create text layer 
     final Layer layer = new Layer(500, 600, Color.WHITE); 
     layer.setPaint(Color.black); 
     Font font = new Font("Arial", 12); 
     String displayText = this.getDisplayText(text, 600, 12); 
     if(displayText!=null && displayText.length() > 0) {
      // commons-gfx Font class would throw IllegalArgumentException on empty or null text 
      layer.drawText(10, 10, 500, 600, displayText, font, Font.ALIGN_LEFT, 0, 0); 
     } 
     // create watermark and merge with text layer 
     Layer watermarkLayer; 
     try { 
      final Session session = node.getSession(); 
      watermarkLayer = ImageHelper.createLayer(session, "/content/dam/geometrixx/icons/certificate.png"); 
      watermarkLayer.setX(MARGIN); 
      watermarkLayer.setY(MARGIN); 
      layer.merge(watermarkLayer); 
     } catch (RepositoryException e) { 
      // TODO Auto-generated catch block 
      e.printStackTrace(); 
     } catch (IOException e) { 
      // TODO Auto-generated catch block 
      e.printStackTrace(); } 
     layer.crop(new Rectangle(510, 600)); 
     return layer.getImage(); } 
    // ---------------< private >----------------------------------------------- 
    /** 
     * This method cuts lines if the text file is too long..
     * * @param text
     * * text to check
     * * @param height
     * * text box height (px)
     * * @param fontheight
     * * font height (px) 
     * * @return the text which will fit into the box 
     */ 
    private String getDisplayText(String text, int height, int fontheight) { 
     String trimmedText = text.trim(); 
     int numOfLines = height / fontheight; 
     String lines[] = trimmedText.split("\n"); 
     if (lines.length <= numOfLines) { 
      return trimmedText; 
     } else { 
      String cuttetText = ""; 
      for (int i = 0; i < numOfLines; i++) { 
       cuttetText += lines[i] + "\n"; 
      } 
      return cuttetText; 
     } 
    } 
    /**
     * * This method counts the number of words in a string 
     * * @param text the String whose words would like to be counted
     * * @return the number of words in the string
     * */ 
    private long wordCount(String text) { 
     // We need to keep track of the last character, if we have two whitespace in a row we don't want to double count.
     // The starting of the document is always a whitespace.
     boolean prevWhiteSpace = true; 
     boolean currentWhiteSpace = true; 
     char c; long numwords = 0; 
     int j = text.length(); 
     int i = 0; 
     while (i < j) { 
      c = text.charAt(i++); 
      if (c == 0) { break; } 
      currentWhiteSpace = Character.isWhitespace(c); 
      if (currentWhiteSpace && !prevWhiteSpace) { numwords++; } 
      prevWhiteSpace = currentWhiteSpace; 
     } 
     // If we do not end with a whitespace then we need to add one extra word.
     if (!currentWhiteSpace) { numwords++; } 
     return numwords; 
    } 
   }
   ```

1. 編譯Java™類並建立包：

   1. 按一下右鍵myBundle項目，選擇&#x200B;**[!UICONTROL 以]**&#x200B;運行，然後選擇&#x200B;**[!UICONTROL Maven Install]**。
   1. 在`myBundle/target`下建立包`myBundle-0.0.1-SNAPSHOT.jar`（包含編譯的類）。

1. 在CRX Explorer中，在`/apps/myApp`下建立節點。 名稱= `install`，類型= `nt:folder`。
1. 複製包`myBundle-0.0.1-SNAPSHOT.jar`並將其儲存在`/apps/myApp/install`下（例如，與WebDAV一起）。 新的文字處理常式現在在Experience Manager中處於作用中。
1. 在您的瀏覽器中，開啟Apache Felix Web Management Console。 選擇「元件」頁籤並禁用預設文本處理程式`com.day.cq.dam.core.impl.handler.TextHandler`。

## 基於命令行的媒體處理程式{#command-line-based-media-handler}

Experience Manager功能可讓您在工作流程中執行任何命令列工具，以轉換資產（例如ImageMagick），並將新的轉譯新增至資產。 在托管Experience Manager伺服器的磁碟上安裝命令行工具，並為工作流添加和配置流程步驟。 調用的進程（稱為`CommandLineProcess`）根據特定MIME類型進行篩選，並基於新的轉譯建立多個縮略圖。

下列轉換可自動執行並儲存在Experience Manager資產中：

* 使用[ImageMagick](https://www.imagemagick.org/script/index.php)和[Ghostscript](https://www.ghostscript.com/)進行EPS和AI轉換
* 使用[FFmpeg](https://ffmpeg.org/)進行FLV視訊轉碼
* 使用[LAME](http://lame.sourceforge.net/)進行MP3編碼
* 使用[SOX](http://sox.sourceforge.net/)進行音訊處理

>[!NOTE]
>
>在非Windows系統上，FFMpeg工具會傳回錯誤，因為視訊資產的檔案名稱中有單引號(&#39;)，所以會產生轉譯。 如果視訊檔案的名稱包含單引號，請先將其移除，再上傳至Experience Manager。

`CommandLineProcess`進程會按列出順序執行以下操作：

* 根據特定MIME類型（如果已指定）篩選檔案。
* 在托管Experience Manager伺服器的磁碟上建立臨時目錄。
* 將原始檔案流到臨時目錄。
* 執行由步驟的參數定義的命令。 該命令在臨時目錄內執行，具有運行Experience Manager的用戶權限。
* 將結果串流回Experience Manager伺服器的轉譯資料夾。
* 刪除臨時目錄。
* 根據這些轉譯（如果已指定）建立縮圖。 縮圖的編號和尺寸由步驟的參數定義。

### 使用ImageMagick {#an-example-using-imagemagick}的範例

以下示例說明如何設定命令行處理步驟。 每次在Experience Manager伺服器的`/content/dam`中新增具有MIME類型gif或tiff的資產時，就會建立原始影像的翻轉影像，以及另外三個縮圖（140x100、48x48和10x250）。

若要執行此程式步驟，請使用ImageMagick。 在托管Experience Manager伺服器的磁碟上安裝ImageMagick:

1. 安裝ImageMagick。 如需詳細資訊，請參閱[ImageMagick檔案](https://www.imagemagick.org/script/download.php)。
1. 設定工具，以便在命令行上運行`convert`。
1. 要查看工具是否已正確安裝，請在命令行上運行以下命令`convert -h`。

   它會顯示「說明」畫面，其中包含轉換工具的所有可能選項。

   >[!NOTE]
   >
   >在某些Windows®版本（例如Windows® SE）中，convert命令無法運行，因為它與Windows®安裝中的本機轉換實用程式衝突。 在這種情況下，請提及將影像檔案轉換為縮圖的ImageMagick公用程式的完整路徑。 例如，`"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`。

1. 要查看工具是否運行正常，請將JPG影像添加到工作目錄並在命令行中運行命令`convert <image-name>.jpg -flip <image-name>-flipped.jpg`。

   翻轉的影像會新增至目錄。

然後，將命令列處理步驟新增至 **[!UICONTROL DAM更新資產工作流程]** :

1. 轉至&#x200B;**[!UICONTROL Workflow]**&#x200B;控制台。
1. 在&#x200B;**[!UICONTROL Models]**&#x200B;標籤中，編輯&#x200B;**[!UICONTROL DAM Update Asset]**&#x200B;模型。
1. 按如下方式更改&#x200B;**[!UICONTROL 啟用Web的轉譯]**&#x200B;步驟的設定：

   `mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

1. 儲存工作流程。

若要測試修改的工作流程，請新增資產至`/content/dam`。

1. 在檔案系統中，取得您選擇的TIFF影像。 將其重新命名為`myImage.tiff`並複製到`/content/dam`，例如使用WebDAV。
1. 前往&#x200B;**[!UICONTROL CQ5 DAM]**&#x200B;主控台，例如`http://localhost:4502/libs/wcm/core/content/damadmin.html`。
1. 開啟資產`myImage.tiff`並確認已建立翻轉的影像和三個縮圖。

#### 配置CommandLineProcess進程步驟{#configuring-the-commandlineprocess-process-step}

本節介紹如何設定 **[!UICONTROL 的Process]**`CommandLineProcess`參數。使用逗號分隔[!UICONTROL 處理參數]的值，不要以空格開頭值。

| 參數格式 | 說明 |
|---|---|
| mime:&lt;mime-type> | 可選引數。 如果資產與其中一個引數具有相同的MIME類型，則會套用此程式。 <br>可定義數種MIME類型。 |
| tn:&lt;width>:&lt;height> | 可選引數。 該過程建立具有在參數中定義的尺寸的縮略圖。 <br>可定義數個縮圖。 |
| cmd:&lt;command> | 定義要運行的命令。 語法取決於命令行工具。 只能定義一個命令。 <br>以下變數可用來建立命令：<br>`${filename}`:輸入檔案的名稱，例如original.jpg  <br> `${file}`:輸入檔案的完整路徑名稱，例如/tmp/cqdam0816.tmp/original.jpg  <br> `${directory}`:的目錄，例如/tmp/cqdam0816.tmp  <br>`${basename}`:輸入檔案的名稱（不帶副檔名），例如原始檔案 <br>`${extension}`:輸入檔案的副檔名，例如jpg |

例如，如果ImageMagick安裝在Experience Manager伺服器所在的磁碟上，並且使用&#x200B;**CommandLineProcess**&#x200B;作為實施，並使用以下值作為&#x200B;**Process Arguments**&#x200B;建立處理步驟：

`mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

然後，當工作流程執行時，此步驟僅適用於具有`image/gif`或`mime:image/tiff`作為mime類型的資產。 它會建立原稿的翻轉影像，並將它轉換為。jpg，並建立三個尺寸縮圖：140x100、48x48和10x250。

使用以下[!UICONTROL 處理參數]使用ImageMagick建立三個標準縮圖：

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=319x319 -thumbnail "319x319>" -background transparent -gravity center -extent 319x319 -write png:cq5dam.thumbnail.319.319.png -thumbnail "140x100>" -background transparent -gravity center -extent 140x100 -write cq5dam.thumbnail.140.100.png -thumbnail "48x48>" -background transparent -gravity center -extent 48x48 cq5dam.thumbnail.48.48.png`

使用以下[!UICONTROL 處理參數]使用ImageMagick建立啟用Web的轉譯：

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=1280x1280 -thumbnail "1280x1280>" cq5dam.web.1280.1280.jpeg`

>[!NOTE]
>
>`CommandLineProcess`步驟僅適用於資產（類型`dam:Asset`的節點）或資產的後代。

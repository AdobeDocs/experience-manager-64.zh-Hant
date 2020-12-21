---
title: JEE上AEM Forms的支援平台
seo-title: JEE上AEM Forms的支援平台
description: 在JEE上安裝AEM Forms所需和支援的基礎架構元件清單
seo-description: 在JEE上安裝AEM Forms所需和支援的基礎架構元件清單
uuid: 22f05fd4-f9fc-423e-8a86-1e75df4b2b44
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 1b9f8d98-e7e8-4b9b-a0df-52ccba324da3
translation-type: tm+mt
source-git-commit: ee38d0ebde12a70e3af04254b0c0b4995c45519b
workflow-type: tm+mt
source-wordcount: '3327'
ht-degree: 0%

---


# JEE上AEM Forms的支援平台{#supported-platforms-for-aem-forms-on-jee}

## 支援的平台{#supported-platforms}

### 支援級別{#support-levels}

JEE伺服器上的AEM Forms可使用支援的作業系統、應用程式伺服器、資料庫、資料庫驅動程式、JDK、LDAP伺服器和電子郵件伺服器的任何組合來設定。

本檔案列出JEE上AEM Forms支援的用戶端和伺服器平台。 Adobe針對我們建議的組態和其他組態提供數種支援等級。 本文檔還列出了其他支援的軟體及其版本、例外、補丁程式定義和第三方軟體補丁程式支援策略。

>[!NOTE]
>
>* 有關受支援伺服器平台的例外的完整清單，請參見[受支援伺服器平台的例外](#exceptions-to-supported-server-platforms)。
>* AEM Forms on JEE僅支援支援英文、法文、德文和日文版的支援作業系統和應用程式。

>



### 建議的配置{#recommendedconfigurations}

Adobe建議您進行這些組態，並在標準軟體維護合約中提供完整或受限制的支援：

<table> 
 <tbody> 
  <tr> 
   <th>支援等級</th> 
   <th>說明</th> 
  </tr> 
  <tr> 
   <td>答：支援<br /> </td> 
   <td>Adobe提供此組態的完整支援與維護。 Adobe的品質保證程式涵蓋此設定。</td> 
  </tr> 
  <tr> 
   <td>R:受限制的支援</td> 
   <td>在符合特定先決條件後，Adobe會提供此設定的完整支援。 請聯絡Adobe企業支援以瞭解必要條件並提出支援要求。</td> 
  </tr> 
  <tr> 
   <td>L:有限支援</td> 
   <td>在符合特定先決條件後，Adobe會提供此組態的完整支援與維護。 並非所有功能都可用於配置。 請聯絡Adobe企業支援以瞭解必要條件並提出支援要求。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 不支援的配置{#unsupported-configurations}

| 支援等級 | 說明 |
|---|---|
| E:預期可運作 | 預計此設定會運作，而且沒有相反的報告。 |
| Z:不支援 | 不支援配置。 Adobe不會就設定是否有效發表任何陳述，也不支援。 |

### Java虛擬機(JVM){#java-virtual-machines-jvm}

Adobe Experience Manager Forms需要Java Virtual Machine才能執行，此程式由Java開發套件(JDK)散發提供。 Adobe Experience Manager可與下列Java虛擬機版本搭配運作：

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>平台</strong></p> </th> 
   <th><p><strong>支援等級</strong></p> </th> 
   <th><p><strong>支援的修補程式定義</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Oracle Java™ SE 8（64位）</p> </td> 
   <td><p>答：支援</p> </td> 
   <td><p>次要版本和更新</p> </td> 
  </tr> 
  <tr> 
   <td>IBM® J9 Virtual Machine(build 2.8,JRE 1.8.0)</td> 
   <td>答：支援</td> 
   <td>次要版本和更新</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* JEE上的AEM Forms僅支援生產環境上的64位元JVM。
>* 建議您追蹤Java廠商的安全性公告，以確保生產環境的安全性，並安裝最新的Java更新。

>



### 資料庫和CRX持久性{#databases-and-crx-persistence}

#### AEM永續性支援{#aem-persistence-support}

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>平台</strong></p> </td> 
   <td><p><strong> 說明</strong></p> </td> 
   <td><p><strong>支援等級</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>檔案系統</p> </td> 
   <td><p>儲存庫微內核（TAR MK檔案）</p> </td> 
   <td><p>支援</p> </td> 
  </tr> 
  <tr> 
   <td><p>MongoDB Enterprise 3.4</p> </td> 
   <td><p>儲存庫微內核</p> </td> 
   <td><p>支援</p> </td> 
  </tr> 
  <tr> 
   <td>IBM DB2 11.1</td> 
   <td>儲存庫微內核</td> 
   <td>支援</td> 
  </tr> 
  <tr> 
   <td><p>Oracle Database 12c發行版1</p> </td> 
   <td><p>儲存庫微內核</p> </td> 
   <td><p>支援</p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft SQL Server 2016</p> </td> 
   <td><p>儲存庫微內核</p> </td> 
   <td><p>支援</p> </td> 
  </tr> 
 </tbody> 
</table>

* MongoDB是協力廠商軟體，不包含在AEM授權套件中。 如需詳細資訊，請參閱[MongoDB授權政策](https://www.mongodb.org/about/licensing/)頁面。

* 為了充份運用您的AEM部署，Adobe建議您授權MongoDB企業版，以便從專業支援中獲益。
* Adobe客戶服務將協助您針對搭配AEM使用MongoDB的相關資格問題。 如需詳細資訊，請參閱[MongoDB for Adobe Experience Manager頁面](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager)。
* 「檔案系統」包括符合POSIX的塊儲存。 其中包括網路儲存技術。 請注意，檔案系統效能可能會有所不同，並影響整體效能。 建議您將測試AEM與網路／遠端檔案系統結合載入。
* 僅支援MongoDB儲存引擎WiredTiger。
* AEM不支援MongoDB Sharding。
* JEE上的AEM Forms不支援MySQL的RDBMK永續性。
* Document Security模組不使用Content Repository。 這表示，如果您只使用Document Security，而不打算使用HTML Workspace、HTML5表單或最適化表單，則不要安裝內容儲存庫。
* AEM Forms on JEE支援Oracle Multitenant架構。

#### 資料庫支援{#database-support}

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>平台</strong></p> </td> 
   <td><p><strong> 說明</strong></p> </td> 
   <td><p><strong>支援層級AEM 6.4</strong></p> </td> 
   <td><p><strong>JEE的支援層級AEM Forms 6.4</strong></p> </td> 
  </tr> 
  <tr> 
   <td>IBM DB2 11.1</td> 
   <td>儲存庫微內核</td> 
   <td>支援</td> 
   <td>支援</td> 
  </tr> 
  <tr> 
   <td><p>Oracle Database 12c發行版1</p> </td> 
   <td><p>儲存庫微內核</p> </td> 
   <td><p>支援</p> </td> 
   <td><p>支援</p> </td> 
  </tr> 
  <tr> 
   <td><p>MySQL 5.7.19<br /> </p> </td> 
   <td><p>儲存庫微內核</p> </td> 
   <td><p>預期可運作</p> </td> 
   <td><p>支援</p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft SQL Server 2016</p> </td> 
   <td><p>儲存庫微內核</p> </td> 
   <td><p>預期可運作</p> </td> 
   <td><p>支援</p> </td> 
  </tr> 
 </tbody> 
</table>

### 資料庫驅動程式{#database-drivers}

<table> 
 <tbody> 
  <tr> 
   <th>資料庫 </th> 
   <th><p><strong>平台</strong></p> </th> 
   <th><p><strong>支援的修補程式定義</strong></p> </th> 
  </tr> 
  <tr> 
   <td>MySQL</td> 
   <td><p>MySQL Connector/J 5.7</p> <p>mysql-connector-java-5.1.30-bin.jar（5.1.30版）</p> </td> 
   <td><p>隨附於JEE安裝的AEM Forms</p> </td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server<br /> </td> 
   <td><p>Microsoft® SQL Server JDBC驅動程式6.2.1.0<br /> </p> <p>sqljdbc6.jar</p> </td> 
   <td><p>隨附於JEE安裝的AEM Forms。</p> </td> 
  </tr> 
  <tr> 
   <td>Oracle</td> 
   <td><p>Oracle Database 12.1.0.2.0 JDBC驅動程式</p> <p>ojdbc7.jar（12.1.0.2.0版）<br /> </p> </td> 
   <td><p>隨附於JEE安裝的AEM Forms。</p> </td> 
  </tr> 
  <tr> 
   <td>IBM DB2</td> 
   <td><p>IBM® DB2 Universal JDBC驅動程式4.16.53(db2jcc4.jar)</p> </td> 
   <td><p>從<a href="https://www-01.ibm.com/support/docview.wss?uid=swg21363866" target="_blank">IBM Website</a>下載驅動程式</p> </td> 
  </tr> 
 </tbody> 
</table>

### 應用程式伺服器{#application-servers}

<table> 
 <tbody> 
  <tr> 
   <td><p><strong> 平台</strong></p> </td> 
   <td><p><strong>支援等級</strong></p> </td> 
   <td><p><strong>支援的修補程式定義</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Oracle WebLogic Server 12.2.1(12c R2)<sup>[1] [2] [4] [8]</sup></p> </td> 
   <td><p>答：支援</p> </td> 
   <td><p>Service Pack和重要更新</p> </td> 
  </tr> 
  <tr> 
   <td>IBM® WebSphere® Application Server 9.0 <sup>[2] [6]</sup><br /> </td> 
   <td>答：支援</td> 
   <td>Service Pack和重要更新</td> 
  </tr> 
  <tr> 
   <td><p>JBoss®企業應用平台(EAP)7.0.6 <sup>[1] [4] [5] [7] [8][11]</sup></p> </td> 
   <td><p>答：支援</p> </td> 
   <td><p>支援的EAP版本<br />的修補程式和累積修補程式 </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>IBM® WebSphere®叢集僅支援網路部署版本。

### 伺服器作業系統{#server-operating-systems}

#### 生產環境{#production-environments}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong> 平台</strong></p> </th> 
   <th><p><strong>支援等級</strong></p> </th> 
   <th><p><strong>支援的修補程式定義</strong></p> </th> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2016</td> 
   <td>答：支援</td> 
   <td>服務包和重要更新</td> 
  </tr> 
  <tr> 
   <td><p>Microsoft Windows Server 2012 R2 V6.3</p> </td> 
   <td><p>答：支援</p> </td> 
   <td><p>服務包和重要更新</p> </td> 
  </tr> 
  <tr> 
   <td><p>Oracle Solaris™ 11 - V5.11<sup> [3] [10]</sup></p> </td> 
   <td><p>L:有限</p> </td> 
   <td><p>更新和修補程式</p> </td> 
  </tr> 
  <tr> 
   <td><p>Red Hat Enterprise Linux 7（內核3.x）</br><b>注意：</b> <a href="https://access.redhat.com/articles/4665701">Red Hat Enterprise Linux 6</a>進入維護結束階段，並於2020年11月30日過渡到延長生命週期支援階段。 Adobe建議使用Red Hat Enterprise Linux 7進行升級和新安裝。 現有安裝可在延長生命週期支援階段使用Red Hat Enterprise Linux 6。</p> </td> 
   <td><p>答：支援</p> </td> 
   <td><p>次要版本、累計更新和重要更新</p> </td> 
  </tr> 
  <tr> 
   <td><p>SUSE® Linux® Enterprise Server 12</p> </td> 
   <td><p>答：支援</p> </td> 
   <td><p>服務包、累積修補程式和關鍵安全更新</p> </td> 
  </tr> 
  <tr> 
   <td>Oracle Linux® 7更新3</td> 
   <td>答：支援</td> 
   <td>服務包、累積修補程式和關鍵安全更新</td> 
  </tr> 
  <tr> 
   <td>CentOS 7<sup> [9]</sup></td> 
   <td>答：支援</td> 
   <td>服務包、累積修補程式和關鍵安全更新</td> 
  </tr> 
  <tr> 
   <td>IBM AIX 7.2 [10]</td> 
   <td>答：有限支援</td> 
   <td>服務包、累積修補程式和關鍵安全更新</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>AEM Forms on JEE僅支援64位元作業系統。

#### 虛擬化環境{#virtualized-environment}

您可以在實體機器或虛擬環境上在JEE上執行AEM Forms。 不過，如果您在虛擬環境中遇到AEM Forms的任何問題，請嘗試在實體機器上複製問題。 如果問題在實體機器上仍然存在，請聯絡Adobe支援以取得解決方案。 有關不在物理電腦上複製的問題，請與虛擬環境供應商聯繫。

#### 開發環境{#development-environments}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>平台（基本版本）</strong></p> </th> 
   <th>支援等級</th> 
   <th><p><strong>支援的修補程式定義</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Microsoft® Windows® 10</p> </td> 
   <td>E:預期可運作</td> 
   <td><p>Service Pack和重要更新</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* AEM Forms on JEE僅支援64位元作業系統。
>* Windows 10不支援PDF Generator服務。

>



### 受支援伺服器平台的例外{#exceptions-to-supported-server-platforms}

在選擇平台以在JEE伺服器上設定AEM Forms時，請考慮下列例外情況。

1. JEE上的AEM Forms不支援IBM® AIX®上的Oracle WebLogic和JBoss®。
1. JEE上的AEM Forms不支援Oracle WebLogic和IBM® WebSphere®搭配MySQL。
1. JEE上的AEM Forms不支援採用Intel®架構的Oracle Solaris™（僅支援SPARC®）。
1. JEE上的AEM Forms不支援SUSE Linux Enterprise Server 12上的Oracle WebLogic和JBoss。 SUSE Linux Enterprise Server 12僅支援IBM WebSphere。
1. JEE上的AEM Forms不支援任何JDK搭配JBoss®（Oracle Java™ SE除外）。
1. AEM Forms on JEE不支援IBM® WebSphere®的任何JDK（IBM® JDK除外）。
1. AEM Forms on JEE不支援IBM® DB2 with JBoss®。
1. CRX-repository支援TarMK、MongoDB和關係資料庫(RDBMK)類型的持久性。 應用程式伺服器和CRX-repository之間不能有兩個不同的資料庫系統。 不過，在JEE環境的AEM Forms上，您可以搭配CRX-repository使用MongoMK，並搭配應用程式伺服器使用支援的關係資料庫。
1. JEE上的AEM Forms不支援CentOS上的WebSphere應用程式伺服器。
1. AIX和Solaris作業系統僅適用於升級客戶。
1. JEE上的AEM Forms不支援JBoss角色型存取控制(RBAC)。

此外，在選擇JEE部署上的Adobe AEM Forms軟體時，請考量下列幾點：

* AEM Forms on JEE支援在支援軟體的指定主要和次要版本上更新、修補程式和修正套件。 但是，除非指定，否則不支援更新至下一個主要或次要版本。
* 基於群集的安裝不支援TarMK持久性。 如需支援永續性的詳細資訊，請參閱[選擇AEM Forms安裝的永續性類型](/help/forms/using/choosing-persistence-type-for-aem-forms.md)。
* AEM Forms on JEE依據我們的[協力廠商軟體支援政策](#third-party-patch-support-policy)支援各種協力廠商軟體。
* AEM Forms on JEE根據協力廠商提供的支援支援支援平台。 某些組合可能無法由第三方廠商允許。 例如，許多供應商尚未通過IBM® DB2的應用程式伺服器認證。 因此，JEE上的AEM Forms也不支援這些組合。 為確保您選擇支援的軟體版本，請檢查協力廠商的支援清單。
* JEE上的AEM Forms不支援TarMK Cold Standby。
* JEE上的AEM Forms不支援垂直叢集。
* JEE上的AEM Forms不支援叢集環境中的MySQL資料庫。
* 當在Weblogic上配置包JDBC模組時，RDBMK無法與DB2、MYSQL、MS SQL和Oracle資料庫一起使用。

### LDAP伺服器（可選）{#ldap-servers-optional}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>產品（基本版本）</strong></p> </th> 
   <th><p><strong>支援的修補程式定義</strong></p> </th> 
  </tr> 
  <tr> 
   <td>Oracle Unified Directory(OUD)11g版本2</td> 
   <td>Service Pack</td> 
  </tr> 
  <tr> 
   <td>Microsoft Active Directory 2016</td> 
   <td>維護髮行和修正套件</td> 
  </tr> 
  <tr> 
   <td><p>Microsoft® Active Directory 2012</p> </td> 
   <td><p>作業系統提供的更新</p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft Active Directory輕量型目錄服務2012</p> </td> 
   <td><p>作業系統提供的更新</p> </td> 
  </tr> 
  <tr> 
   <td><p>IBM® Tivoli Directory Server 6.4</p> </td> 
   <td><p>功能套件和過渡修正</p> </td> 
  </tr> 
  <tr> 
   <td>IBM Lotus Domino 8.5.0</td> 
   <td>維護髮行和修正套件</td> 
  </tr> 
  <tr> 
   <td>Novell eDirectory 8.8.7</td> 
   <td>產品更新</td> 
  </tr> 
 </tbody> 
</table>

### 電子郵件伺服器（可選）{#email-servers-optional}

* IBM Lotus Domino 9.0
* Microsoft Exchange 2013
* Microsoft Office 365

### 內容管理器和對應的連接器{#content-managers-and-corresponding-connectors}

<table> 
 <tbody> 
  <tr> 
   <td><strong>產品<br /> </strong></td> 
   <td><strong>版本</strong></td> 
  </tr> 
  <tr> 
   <td>IBM Content Manager Server</td> 
   <td>8.5修補程式套件2<br /> </td> 
  </tr> 
  <tr> 
   <td>IBM Content Manager Client</td> 
   <td><p>支援版本8.5<strong> </strong></p> </td> 
  </tr> 
  <tr> 
   <td>EMC Documentum</td> 
   <td>7.0和7.3</td> 
  </tr> 
  <tr> 
   <td>IBM Filenet</td> 
   <td>5.2</td> 
  </tr> 
  <tr> 
   <td>Microsoft Sharepoint</td> 
   <td>2013年及2016年<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 支援Cordova {#support-for-cordova}

AEM Forms App現在支援Apache Cordova。 以下是支援的Cordova平台特定版本：

* Apache Cordova 6.4.0
* Cordova iOS 4.3.0
* Cordova Android 6.0.0
* Cordova Windows 4.4.3

### PDF產生器{#software-support-for-pdf-generator}的軟體支援

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>產品</strong></p> </th> 
   <th><p><strong>支援的格式，可轉換為PDF</strong></p> </th> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html">Acrobat 2017經典曲目</a></td> 
   <td>XPS，影像格式(BMP、GIF、JPEG、JPG、TIF、TIFF、PNG、JPF、JPX、JP2、J2K、J2C、JPC)、HTML、HTM、DWG、DXF和DWF</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office 2016</td> 
   <td>DOC、DOCX、XLS、XLSX、PPT、PPTX、RTF和TXT</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office 2013</td> 
   <td>DOC、DOCX、XLS、XLSX、PPT、PPTX、RTF和TXT</td> 
  </tr> 
  <tr> 
   <td>WordPerfect X7</td> 
   <td>WP, WPD</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office Visio 2013</td> 
   <td>VSD、VSDX</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office Visio 2016</td> 
   <td>VSD、VSDX</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Publisher 2013</td> 
   <td>PUB</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Publisher 2016</td> 
   <td>PUB</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Project 2013</td> 
   <td>MPP</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Project 2016</td> 
   <td>MPP</td> 
  </tr> 
  <tr> 
   <td>OpenOffice 4.1.2</td> 
   <td>ODT、ODP、ODS、ODG、ODF、SXW、SXI、SXC、SXD、XLS、DOC、DOCX、PPT、PPTX、影像格式(BMP、GIF、JPEG、JPG、TIF、PFF、 PNG)、JPF、JPX、JP2、J2K、J2C、JPC)、HTML、HTM、RTF和TXT</td> 
  </tr> 
  <tr> 
   <td>OpenOffice 3.4</td> 
   <td>ODT、ODP、ODS、ODG、ODF、SXW、SXI、SXC、SXD、XLS、DOC、DOCX、PPT、PPTX、影像格式(BMP、GIF、JPEG、JPG、TIF、PFF、 PNG)、JPF、JPX、JP2、J2K、J2C、JPC)、HTML、HTM、RTF和TXT</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>PDF產生器僅支援英文、法文、德文和日文版支援的作業系統和應用程式。
>
>此外：
>
>* PDF Generator需要32位元版本的[Acrobat 2017傳統音軌17.011.30078或更新版本](https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html)才能執行轉換。
>* PDF Generator僅支援32位元零售版Microsoft Office Professional Plus和轉換所需的其他軟體。
>* PDF產生器不支援Microsoft Office 365。
>* OpenOffice專用的PDF產生器轉換僅在Windows、Linux和Solaris上受支援。
>* AIX上已停用HTML2PDF服務。
>* OCR PDF、最佳化PDF和匯出PDF功能僅在Windows上受支援。
>* AEM Forms隨附Acrobat版本，以啟用PDF Generator功能。 在AEM Forms授權期間，僅能透過AEM Forms以程式設計方式存取搭售版本，以便與AEM Forms PDF Generator搭配使用。 如需詳細資訊，請參閱AEM Forms產品說明（依您的部署而定）（[On-Premise](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html)或[Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html)）&quot;

>



### 協助工具支援的例外{#exceptions-to-accessibility-support}

下列AEM Forms子系統不符合[508](https://www.section508.gov/)規範：

* 最適化表單製作UI
* Forms Manager編寫UI
* Commense Management編寫UI
* 管理員UI（管理控制台UI）

## JEE上AEM Forms的系統需求{#system-requirements-for-aem-forms-on-jee}

### 最低硬體需求{#minimum-hardware-requirements}

<table> 
 <tbody> 
  <tr> 
   <td>平台</td> 
   <td>最低硬體需求</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server</td> 
   <td>Intel® Xeon® E5-2680、2.4 GHz處理器或相當等級的<br /> VMWare ESX 5.1或更新版本<br /> RAM:6 GB（64位元作業系統，含64位元JVM）<br />可用磁碟空間：JEE上的AEM Forms需要15GB的臨時空間加上22GB<br /></td> 
  </tr> 
  <tr> 
   <td>Sun Solaris</td> 
   <td>UltraSPARC® IIIi, 1.5 GHz處理器<br /> Solaris Containers(Zones)Partitioning<br /> RAM:6 GB（64位元作業系統，含64位元JVM）<br />可用磁碟空間：JEE上的AEM Forms需要6 GB的臨時空間加上22 GB<br /></td> 
  </tr> 
  <tr> 
   <td>IBM AIX</td> 
   <td>P6 pSeries 520（型號52A）9131-52A,1.8 GHz處理器<br /> LPAR分區<br /> RAM:6 GB（64位元作業系統，含64位元JVM）<br />可用磁碟空間：JEE上的AEM Forms需要6 GB的臨時空間加上22 GB<br /></td> 
  </tr> 
  <tr> 
   <td>SUSE Linux Enterprise Server</td> 
   <td>Intel Xeon E5-2670v2,1 vCPU,2.5 GHz處理器<br /> AWS m3.medium（3個ECU）<br /> RAM:6 GB（64位元作業系統，含64位元JVM）<br />可用磁碟空間：JEE上的AEM Forms需要6 GB的臨時空間加上22 GB<br /></td> 
  </tr> 
  <tr> 
   <td>Red Hat Enterprise Linux</td> 
   <td>Intel Xeon E5-2670v2,1 vCPU,2.5 GHz處理器<br /> AWS m3.medium（3個ECU）<br /> RAM:6 GB（64位元作業系統，含64位元JVM）<br />可用磁碟空間：JEE上的AEM Forms需要6 GB的臨時空間加上22 GB<br /><br /> </td> 
  </tr> 
  <tr> 
   <td>小型生產環境的硬體需求</td> 
   <td> 
    <ul> 
     <li><strong>英特爾驅動的環境</strong>:英特爾®至強® E5-2680、2.4 GHz或更高版本。使用雙核處理器將進一步提高效能</li> 
     <li><strong>支援Sun SPARC的環境：</strong> UltraSPARC V或更高版本</li> 
     <li><strong>IBM AIX支援的環境：</strong> Power6或更高版本<br /> </li> 
     <li><strong>記憶體： </strong>4 GB  <br /> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

如需其他需求，請參閱：

* [JEE部署上的單一伺服器AEM表單的系統需求](https://www.adobe.com/go/learn_aemforms_sysreq_single_64)
* [JEE部署上的叢集AEM Forms的系統需求](https://www.adobe.com/go/learn_aemforms_sysreq_cluster_64)

## JEE上AEM Forms的支援用戶端{#supported-clients-for-aem-forms-on-jee}

### 工作台{#workbench}

>[!NOTE]
>
>支援32位元和64位元作業系統。

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>平台</strong></p> </th> 
   <th><p><strong>支援的修補程式定義</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Microsoft® Windows® 10</p> <p>（企業版、專業版、基本版）</p> </td> 
   <td>服務包和重要更新</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Windows® 2012 Server R2</td> 
   <td>服務包和重要更新</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Windows® 2016 Server</td> 
   <td>服務包和重要更新</td> 
  </tr> 
 </tbody> 
</table>

* 安裝的磁碟空間：僅適用於Workbench 1.7 GB，在單一磁碟機上2.7 GB可完整安裝Workbench、Designer和範例元件400 MB（適用於臨時安裝目錄）- 200 MB（適用於用戶臨時目錄）和200 MB（適用於Windows臨時目錄）

>[!NOTE]
>
>如果所有這些位置都駐留在單個驅動器上，則安裝期間必須有1.5 GB的可用空間。 安裝完成後，將刪除複製到臨時目錄的檔案。

* 運行Workbench的記憶體：2GB的記憶體
* 硬體需求：Intel® Pentium® 4或AMD等級，1 GHz處理器
* 最低1024 X 768像素或更高的螢幕解析度（含16位元色彩或更高）
* TCP/IPv4或TCP/IPv6網路連線至JEE伺服器上的AEM Forms

>[!NOTE]
>
>您必須擁有管理權限，才能在Windows上安裝Workbench。 如果您使用非管理員帳戶進行安裝，安裝程式會提示您輸入適當帳戶的認證。

### 設計人員{#designer}

**注意：若要** 在Windows上安裝Designer，請以管理權限執行安裝程式。

* Microsoft® Windows® 2012 Server R2、Microsoft® Windows® 2016 Server、Microsoft Windows 10

   * 支援PAE、NX和SSE2的1 GHz或速度更快的處理器。
   * 64位元作業系統需1 GB的記憶體（32位元或2 GB的記憶體）
   * 64位元作業系統需要16 GB的磁碟空間（32位元或20 GB的磁碟空間）

* 圖形記憶體- 128 MB的GPU（建議使用256 MB）
* 2.35 GB的可用硬碟空間
* DVD-ROM光碟機
* Internet Explorer 10或11;Firefox 45.x
* 1024 X 768像素或更高的螢幕解析度
* 視訊硬體加速（選用）
* Acrobat Pro DC、Acrobat Standard DC或Adobe Acrobat Reader DC。

### Adobe Acrobat和Adobe Reader {#adobe-acrobat-and-adobe-reader}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Acrobat和Adobe Reader（基本）</strong></p> </th> 
   <th><p><strong>支援的修補程式定義</strong></p> </th> 
  </tr> 
  <tr> 
   <td>Acrobat 2017(Classic track)</td> 
   <td>17.011.30078或更高版本<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Acrobat DC產品系列為Acrobat和Reader提供兩種本質上不同的產品：「經典」和「連續」。 如需詳細資訊和兩個音軌的比較，請參閱[https://www.adobe.com/go/acrobatdctracks。](https://www.adobe.com/go/acrobatdctracks)

### 瀏覽器{#browsers}

#### 台式機{#desktops}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>瀏覽器（基本）</strong></p> </th> 
   <th><p><strong>支援等級</strong></p> </th> 
   <th><p><strong>支援的修補程式定義</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Microsoft Edge</p> </td> 
   <td><p>答：支援</p> </td> 
   <td><p>服務包和更新</p> </td> 
  </tr> 
  <tr> 
   <td><p>Mozilla Firefox 45.x</p> </td> 
   <td><p>答：支援</p> </td> 
   <td><p>所有更新</p> </td> 
  </tr> 
  <tr> 
   <td><p>Google Chrome 46+</p> </td> 
   <td><p>答：支援</p> </td> 
   <td><p>所有更新</p> </td> 
  </tr> 
  <tr> 
   <td>Apple Safari 11.x</td> 
   <td>答：支援</td> 
   <td>所有更新</td> 
  </tr> 
  <tr> 
   <td><p>MAC OS X上的Google Chrome和Firefox</p> </td> 
   <td><p>答：支援</p> </td> 
   <td><p>所有更新</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>桌上型電腦的部分瀏覽器相關例外如下：
>
>* 大部份的現代瀏覽器不再支援NPAPI增效模組。 如需有關它如何影響AEM Forms應用程式和工作流程的詳細資訊，請參閱[中止NPAPI瀏覽器外掛程式及其影響](https://helpx.adobe.com/aem-forms/kb/discontinuation-of-npapi-plugins-impact-on-aem-forms.html)。
>* Safari僅在Macintosh OS X上受支援。


#### 行動用戶端{#mobile-clients}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>瀏覽器（基本）</strong></p> </th> 
   <th><p><strong>支援的修補程式定義</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Android™ 4.1.2及更新版本上的Chrome</p> </td> 
   <td><p>所有更新</p> </td> 
  </tr> 
  <tr> 
   <td>iOS 11.0及更新版本上的Safari</td> 
   <td>所有更新</td> 
  </tr> 
  <tr> 
   <td>Windows 10上的Internet Explorer</td> 
   <td>所有更新</td> 
  </tr> 
  <tr> 
   <td>Microsoft Edge<br /> </td> 
   <td>所有更新<br /> </td> 
  </tr> 
  <tr> 
   <td>Android™ 4.4和更新版本上的原生Andriod瀏覽器</td> 
   <td>所有更新</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* Safari僅在iPad上支援表單入口網站。

>



### AEM Forms應用程式{#aem-forms-workspace-app}

#### 行動裝置支援{#mobile-device-support}

AEM Forms應用程式可在下列平台上使用：

| **平台** | **支援的裝置** |
|---|---|
| Apple iOS | 執行iOS 11及以上版本的Apple iPhone、iPad、iPad Air和iPad mini。 |
| Google Android | Android 4.4(Androird Kit Kat)和&#x200B;*[API Level 19及以上版本]*。 AEM Forms應用程式已通過7寸和10寸Samsung Galaxy平板電腦、7寸Google Nexus平板電腦和熱門智慧型手機的認證。 |
| Microsoft Windows | 運行Microsoft Windows 10作業系統的Microsoft Surface設備、平板電腦、筆記型電腦和台式機。 |

### Adobe Flash Player {#adobe-flash-player}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Flash Player（基本）</strong></p> </th> 
   <th><p><strong>支援的修補程式定義</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Flash Player最新版</p> </td> 
   <td><p>次要版本和更新</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Adobe將於2020年底[停止更新和散發Flash Player。](https://theblog.adobe.com/adobe-flash-update/)

### Adobe Document Security Extension for Microsoft Office {#adobe-rights-management-extension-for-microsoft-office}

按一下[這裡](https://www.adobe.com/products/livecycle/rightsmanagement/extension/downloads.html)以檢視Adobe Document Security Extension for Microsoft® Office的系統需求。

### 客戶端支援的例外{#exceptions-to-client-support}

除Reader和Acrobat外，並非所有指定用戶端軟體都支援Microsoft® Windows® 2012。

此外，AEM Forms on JEE支援在支援軟體的指定主要和次要版本上的更新、修補程式和修正套件。 但是，除非指定，否則不支援更新至下一個主要或次要版本。

## 協力廠商修補程式支援政策{#third-party-patch-support-policy}

AEM Forms on JEE的協力廠商軟體需求記錄在其各自產品檔案的「系統需求」一節。 您可從[https://adobe.com/go/learn_aemforms_documentation_64](https://adobe.com/go/learn_aemforms_documentation_64)存取所有檔案。

JEE協力廠商參考平台上的AEM Forms會說明在JEE上開發和發行AEM Forms時，第三方基礎架構的特定修補程式層級，以及JEE上該AEM Forms版本支援的基礎架構的最低修補程式／服務套件層級。

Adobe支援協力廠商在發行時發出的緊急或建議的修補程式，前提是協力廠商保證向後相容於JEE上的AEM Forms支援的版本。 Adobe僅支援在AEM Forms on JEE檔案中規定的最低修補程式層級之後發行的修補程式。

在某些情況下，Adobe不支援變更主要功能的協力廠商更新，因此不支援完全回溯相容性。 有關支援的更新的詳細資訊，請參見[ Supported patch definitions](https://helpx.adobe.com/aem-forms/aem-forms-third-party-software-patch.html) ，以瞭解特定供應商產品和Adobe支援的修補程式類型。

在Adobe無法控制的情況下，宣稱回溯相容性的協力廠商修補程式可能會對Adobe產品或客戶環境造成負面影響。 在這種情況下，Adobe建議客戶先評估第三方的任何緊急修補程式，再將它們套用至關鍵系統。 Adobe將與第三方合作，以合理的商業努力來解決此類問題，不論是透過一般的Adobe支援計畫，還是透過協力廠商在修補程式中修正問題。 這並不保證Adobe支援的新發行協力廠商修補程式會如廠商所記錄，或與JEE上的AEM Forms一起運作。

Adobe保留在任何指定點變更AEM Forms on JEE版本所支援之協力廠商參考平台及其支援修補程式定義的權利。

如需協力廠商修補程式的詳細資訊，請搜尋Adobe企業支援網站，以取得與您產品相關的知識庫文章。

[**聯絡支援**](https://www.adobe.com/account/sign-in.supportportal.html)

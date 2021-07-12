---
title: AEM Forms on JEE的支援平台
seo-title: AEM Forms on JEE的支援平台
description: 在JEE上安裝AEM Forms所需和支援的基礎架構元件清單
seo-description: 在JEE上安裝AEM Forms所需和支援的基礎架構元件清單
uuid: 22f05fd4-f9fc-423e-8a86-1e75df4b2b44
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 1b9f8d98-e7e8-4b9b-a0df-52ccba324da3
role: Admin
exl-id: 6609c625-0591-42fd-910b-c7c65d52c5f1
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '3316'
ht-degree: 1%

---

# AEM Forms on JEE的支援平台 {#supported-platforms-for-aem-forms-on-jee}

## 支援平台 {#supported-platforms}

### 支援層級 {#support-levels}

JEE伺服器上的AEM Forms可使用支援的作業系統、應用程式伺服器、資料庫、資料庫驅動程式、 JDK、LDAP伺服器和電子郵件伺服器的任意組合來設定。

本檔案列出JEE版AEM Forms支援的用戶端和伺服器平台。 Adobe提供數種支援級別，包括我們建議的配置和其他配置。 該文檔還列出了其他受支援的軟體及其版本、例外、補丁程式定義和第三方軟體補丁程式支援策略。

>[!NOTE]
>
>* 有關受支援伺服器平台的例外狀況的完整清單，請參閱[受支援伺服器平台的例外狀況](#exceptions-to-supported-server-platforms)。
>* AEM Forms on JEE僅支援英文、法文、德文和日文版本的支援作業系統和應用程式。

>



### 建議的設定 {#recommendedconfigurations}

Adobe建議這些配置，並在標準軟體維護協定中提供完整或受限的支援：

<table> 
 <tbody> 
  <tr> 
   <th>支援層級</th> 
   <th>說明</th> 
  </tr> 
  <tr> 
   <td>答：支援<br /> </td> 
   <td>Adobe對此配置提供完全支援和維護。 此設定由Adobe的品質保證程式涵蓋。</td> 
  </tr> 
  <tr> 
   <td>R:受限支援</td> 
   <td>Adobe在符合特定必要條件後，即可完全支援此設定。 聯絡Adobe企業支援，了解必要條件並提出支援要求。</td> 
  </tr> 
  <tr> 
   <td>L:有限支援</td> 
   <td>Adobe在符合特定必要條件後，即可提供此設定的完整支援和維護。 並非所有功能都可在設定中使用。 請聯繫Adobe企業支援，了解先決條件並提出支援請求。<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 不支援的配置 {#unsupported-configurations}

| 支援層級 | 說明 |
|---|---|
| E:預期可運作 | 預期該配置會正常運作，而且沒有相反的報告。 |
| Z:不支援 | 不支援配置。 Adobe不會針對設定是否有效發表任何陳述，也不支援。 |

### Java虛擬機(JVM) {#java-virtual-machines-jvm}

Adobe Experience Manager Forms需要Java虛擬機才能運行，該虛擬機由Java開發套件(JDK)分發提供。 Adobe Experience Manager可搭配下列版本的Java虛擬機運作：

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>平台</strong></p> </th> 
   <th><p><strong>支援層級</strong></p> </th> 
   <th><p><strong>支援的修補程式定義</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>OracleJava™ SE 8（64位）</p> </td> 
   <td><p>答：支援</p> </td> 
   <td><p>次要版本和更新</p> </td> 
  </tr> 
  <tr> 
   <td>IBM® J9 Virtual Machine（版本編號2.8、JRE 1.8.0）</td> 
   <td>答：支援</td> 
   <td>次要版本和更新</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* JEE版AEM Forms僅支援生產環境上的64位元JVM。
>* 建議您追蹤來自Java廠商的安全性佈告欄，以確保生產環境的安全性，並安裝最新的Java更新。

>



### 資料庫和CRX持久性 {#databases-and-crx-persistence}

#### AEM永續性支援 {#aem-persistence-support}

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>平台</strong></p> </td> 
   <td><p><strong> 說明</strong></p> </td> 
   <td><p><strong>支援層級</strong></p> </td> 
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
   <td><p>Oracle資料庫12c版本1</p> </td> 
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

* MongoDB是協力廠商軟體，不包含在AEM授權套件中。 有關詳細資訊，請參閱[MongoDB許可策略](https://www.mongodb.org/about/licensing/)頁。

* 為了充分利用您的AEM部署，Adobe建議您授權MongoDB企業版本，以便從專業支援中受益。
* Adobe客戶服務將協助確認與搭配AEM使用MongoDB的相關問題。 如需詳細資訊，請參閱[Adobe Experience Manager適用的MongoDB頁面](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager)。
* 「檔案系統」包括符合POSIX的塊儲存。 這包括網路儲存技術。 請注意，檔案系統效能可能會有所不同，並影響整體效能。 建議結合網路/遠端檔案系統載入測試AEM。
* 僅支援MongoDB儲存引擎WiredTiger。
* AEM不支援MongoDB共用。
* JEE上的AEM Forms不支援MySQL用於RDBMK持續性。
* 檔案安全性模組不使用內容存放庫。 這表示，如果您只使用檔案安全性，且不打算使用HTML工作區、HTML5表單或最適化表單，則請勿安裝內容存放庫。
* AEM Forms on JEE支援Oracle多租用戶架構。

#### 資料庫支援 {#database-support}

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>平台</strong></p> </td> 
   <td><p><strong> 說明</strong></p> </td> 
   <td><p><strong>支援級別AEM 6.4</strong></p> </td> 
   <td><p><strong>JEE上的支援層級AEM Forms 6.4</strong></p> </td> 
  </tr> 
  <tr> 
   <td>IBM DB2 11.1</td> 
   <td>儲存庫微內核</td> 
   <td>支援</td> 
   <td>支援</td> 
  </tr> 
  <tr> 
   <td><p>Oracle資料庫12c版本1</p> </td> 
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

### 資料庫驅動程式 {#database-drivers}

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
   <td><p>在JEE安裝上隨AEM Forms提供</p> </td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server<br /> </td> 
   <td><p>Microsoft® SQL Server JDBC驅動程式6.2.1.0<br /> </p> <p>sqljdbc6.jar</p> </td> 
   <td><p>在JEE安裝上隨AEM Forms提供。</p> </td> 
  </tr> 
  <tr> 
   <td>Oracle</td> 
   <td><p>Oracle資料庫12.1.0.2.0 JDBC驅動程式</p> <p>ojdbc7.jar（12.1.0.2.0版）<br /> </p> </td> 
   <td><p>在JEE安裝上隨AEM Forms提供。</p> </td> 
  </tr> 
  <tr> 
   <td>IBM DB2</td> 
   <td><p>IBM® DB2通用JDBC驅動程式4.16.53(db2jcc4.jar)</p> </td> 
   <td><p>從<a href="https://www-01.ibm.com/support/docview.wss?uid=swg21363866" target="_blank">IBM網站</a>下載驅動程式</p> </td> 
  </tr> 
 </tbody> 
</table>

### 應用程式伺服器 {#application-servers}

<table> 
 <tbody> 
  <tr> 
   <td><p><strong> 平台</strong></p> </td> 
   <td><p><strong>支援層級</strong></p> </td> 
   <td><p><strong>支援的修補程式定義</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>OracleWebLogic Server 12.2.1(12c R2)<sup>[1] [2] [4] [8]</sup></p> </td> 
   <td><p>答：支援</p> </td> 
   <td><p>Service Pack和重要更新</p> </td> 
  </tr> 
  <tr> 
   <td>IBM® WebSphere® Application Server 9.0 <sup>[2] [6]</sup><br /> </td> 
   <td>答：支援</td> 
   <td>Service Pack和重要更新</td> 
  </tr> 
  <tr> 
   <td><p>JBoss®企業應用程式平台(EAP)7.0.6 <sup>[1] [4] [5] [7] [8][11]</sup></p> </td> 
   <td><p>答：支援</p> </td> 
   <td><p>支援的EAP版本<br />的修補程式和累積修補程式 </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>IBM® WebSphere®群集僅在網路部署版中受支援。

### 伺服器作業系統 {#server-operating-systems}

#### 生產環境 {#production-environments}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong> 平台</strong></p> </th> 
   <th><p><strong>支援層級</strong></p> </th> 
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
   <td><p>OracleSolaris™ 11 - V5.11<sup> [3] [10]</sup></p> </td> 
   <td><p>L:有限</p> </td> 
   <td><p>更新和修補程式</p> </td> 
  </tr> 
  <tr> 
   <td><p>Red Hat Enterprise Linux 7（內核3.x）</br><b>注意：</b> <a href="https://access.redhat.com/articles/4665701">Red Hat Enterprise Linux 6</a>到達維護階段的結束，並於2020年11月30日過渡到「延長生命週期支援」階段。 Adobe建議使用Red Hat Enterprise Linux 7進行升級和新安裝。 在「延長生命週期支援」階段，現有安裝可以使用Red Hat Enterprise Linux 6。</p> </td> 
   <td><p>答：支援</p> </td> 
   <td><p>次要版本、累積更新和重要更新</p> </td> 
  </tr> 
  <tr> 
   <td><p>SUSE® Linux® Enterprise Server 12</p> </td> 
   <td><p>答：支援</p> </td> 
   <td><p>服務包、累積修補程式和關鍵安全更新</p> </td> 
  </tr> 
  <tr> 
   <td>OracleLinux® 7更新3</td> 
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

#### 虛擬化環境 {#virtualized-environment}

您可以在物理機器或虛擬環境上於JEE上執行AEM Forms。 不過，如果您在虛擬環境中遇到AEM Forms的任何問題，請嘗試在物理電腦上複製問題。 如果問題在物理電腦上持續存在，請與Adobe支援聯繫以獲得解決。 如果問題未在物理電腦上複製，請聯繫您的虛擬環境供應商。

#### 開發環境 {#development-environments}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>平台（基本版本）</strong></p> </th> 
   <th>支援層級</th> 
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
>* Windows 10不支援PDF產生器服務。

>



### 受支援伺服器平台的例外情況 {#exceptions-to-supported-server-platforms}

選擇平台以在JEE伺服器上設定AEM Forms時，請考量下列例外情況。

1. JEE版AEM Forms不支援IBM® AIX®上的WebLogic和JBoss®。
1. AEM Forms on JEE不支援使用MySQL的OracleWebLogic和IBM® WebSphere®。
1. JEE版AEM Forms不支援採用英特爾®架構的OracleSolaris™(僅支援SPARC®)。
1. JEE版AEM Forms不支援SUSE Linux Enterprise Server 12上的OracleWebLogic和JBoss。 SUSE Linux Enterprise Server 12僅支援IBM WebSphere。
1. AEM Forms on JEE不支援使用JBoss®的任何JDK，但OracleJava™ SE除外。
1. JEE上的AEM Forms不支援使用IBM® WebSphere®(IBM® JDK除外)的任何JDK。
1. JEE上的AEM Forms不支援IBM® DB2搭配JBoss®。
1. CRX-repository支援TarMK、MongoDB類型和關係資料庫(RDBMK)的持久性。 應用程式伺服器和CRX-repository之間不能有兩個不同的資料庫系統。 不過，在JEE環境上的AEM Forms上，您可以搭配CRX存放庫使用MongoMK，以及搭配應用程式伺服器使用支援的關係資料庫。
1. JEE上的AEM Forms不支援CentOS上的WebSphere應用程式伺服器。
1. AIX和Solaris作業系統僅適用於升級客戶。
1. AEM Forms on JEE不支援JBoss角色型存取控制(RBAC)。

此外，在選擇軟體以AdobeJEE部署上的AEM Forms時，請考量下列幾點：

* AEM Forms on JEE支援在指定的主要和次要支援軟體版本之上更新、修補程式和修正套件。 但是，除非另有指定，否則不支援更新至下一個主要或次要版本。
* 基於群集的安裝不支援TarMK持久性。 有關支援的持久性的資訊，請參閱[為AEM Forms安裝選擇持久性類型](/help/forms/using/choosing-persistence-type-for-aem-forms.md)。
* AEM Forms on JEE根據我們的[第三方軟體支援政策](#third-party-patch-support-policy)支援各種第三方軟體。
* AEM Forms on JEE根據協力廠商提供的支援支援支援平台。 協力廠商可能不允許某些組合。 例如，許多供應商尚未通過IBM® DB2認證其應用程式伺服器。 因此，JEE上的AEM Forms也不支援這些組合。 為確保您選擇支援的軟體版本，請檢查第三方供應商的支援清單。
* JEE上的AEM Forms不支援TarMK冷備。
* AEM Forms on JEE不支援垂直叢集。
* JEE上的AEM Forms不支援群集環境上的MySQL資料庫。
* 在Weblogic上配置包JDBC模組時，RDBMK不能用於DB2、MYSQL、MS SQL和Oracle資料庫。

### LDAP伺服器（可選） {#ldap-servers-optional}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>產品（基本版本）</strong></p> </th> 
   <th><p><strong>支援的修補程式定義</strong></p> </th> 
  </tr> 
  <tr> 
   <td>Oracle統一目錄(OUD)11g第2版</td> 
   <td>Service Pack</td> 
  </tr> 
  <tr> 
   <td>Microsoft Active Directory 2016</td> 
   <td>維護髮行和修正套件</td> 
  </tr> 
  <tr> 
   <td><p>Microsoft® Active Directory 2012</p> </td> 
   <td><p>作業系統隨附的更新</p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft Active Directory輕型目錄服務2012</p> </td> 
   <td><p>作業系統隨附的更新</p> </td> 
  </tr> 
  <tr> 
   <td><p>IBM® Tivoli Directory Server 6.4</p> </td> 
   <td><p>功能套件和臨時修正</p> </td> 
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

### 電子郵件伺服器（可選） {#email-servers-optional}

* IBM Lotus Domino 9.0
* Microsoft Exchange 2013
* Microsoft Office 365

### 內容管理器和相應的連接器 {#content-managers-and-corresponding-connectors}

<table> 
 <tbody> 
  <tr> 
   <td><strong>產品<br /> </strong></td> 
   <td><strong>版本</strong></td> 
  </tr> 
  <tr> 
   <td>IBM Content Manager Server</td> 
   <td>8.5 Fix Pack 2<br /> </td> 
  </tr> 
  <tr> 
   <td>IBM Content Manager客戶端</td> 
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
   <td>2013年和2016年<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 支援Cordova {#support-for-cordova}

AEM Forms應用程式現在支援Apache Cordova。 以下是支援的平台特定版本Cordova:

* Apache Cordova 6.4.0
* Cordova iOS 4.3.0
* Cordova Android 6.0.0
* Cordova Windows 4.4.3

### PDF產生器的軟體支援 {#software-support-for-pdf-generator}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>產品</strong></p> </th> 
   <th><p><strong>支援的PDF轉換格式</strong></p> </th> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html">Acrobat 2017傳統賽道</a></td> 
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
   <td>ODT、ODP、ODS、ODG、ODF、SXW、SXI、SXC、XLS、XLSX、DOC、DOCX、PPT、PPTX、影像格式(BMP、GIF、JPEG、JPG、TIF、TIFF、PNG、JP2、J2C、JPXT、JPC)、HTML、HTF、HTF、HTF</td> 
  </tr> 
  <tr> 
   <td>OpenOffice 3.4</td> 
   <td>ODT、ODP、ODS、ODG、ODF、SXW、SXI、SXC、XLS、XLSX、DOC、DOCX、PPT、PPTX、影像格式(BMP、GIF、JPEG、JPG、TIF、TIFF、PNG、JP2、J2C、JPXT、JPC)、HTML、HTF、HTF、HTF</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>PDF產生器僅支援支援的作業系統和應用程式的英文、法文、德文和日文版本。
>
>此外：
>
>* PDF產生器需要32位元版本的[Acrobat 2017傳統追蹤17.011.30078版或更新版本](https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html)才能執行轉換。
>* PDF Generator僅支援32位Retail版的Microsoft Office Professional Plus和轉換所需的其他軟體。
>* PDF產生器不支援Microsoft Office 365。
>* 只有Windows、Linux和Solaris支援OpenOffice的PDF生成器轉換。
>* AIX上已棄用HTML2PDF服務。
>* OCR PDF、Optimize PDF和Export PDF功能僅在Windows上受支援。
>* Acrobat版本與AEM Forms搭配，以啟用PDF產生器功能。 套件版本僅能在AEM Forms授權期限內以程式設計方式存取，以便與AEM Forms PDF Generator搭配使用。 如需詳細資訊，請參閱根據您的部署([On-Premise](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html)或[Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html))&quot;的AEM Forms產品說明

>



### 協助工具支援的例外情況 {#exceptions-to-accessibility-support}

AEM Forms的下列子系統不符合[508](https://www.section508.gov/):

* 適用性Forms編寫UI
* Forms Manager編寫UI
* 通信管理編寫UI
* 管理UI（管理控制台UI）

## JEE版AEM Forms的系統需求 {#system-requirements-for-aem-forms-on-jee}

### 最低硬體需求 {#minimum-hardware-requirements}

<table> 
 <tbody> 
  <tr> 
   <td>平台</td> 
   <td>最低硬體需求</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server</td> 
   <td>英特爾®至強® E5-2680、2.4 GHz處理器或等效的<br /> VMWare ESX 5.1或更高版本<br /> RAM:6 GB（64位OS，帶64位JVM）<br />可用磁碟空間：15GB的暫存空間，加上22GB<br />(適用於JEE上的AEM Forms)</td> 
  </tr> 
  <tr> 
   <td>Sun Solaris</td> 
   <td>UltraSPARC® III, 1.5 GHz處理器<br /> Solaris容器（區域）分區<br /> RAM:6 GB（64位OS，帶64位JVM）<br />可用磁碟空間：JEE版AEM Forms的6 GB臨時空間加22 GB<br /></td> 
  </tr> 
  <tr> 
   <td>IBM AIX</td> 
   <td>P6 pSeries 520（型號52A）9131-52A,1.8 GHz處理器<br /> LPAR分區<br /> RAM:6 GB（64位OS，帶64位JVM）<br />可用磁碟空間：JEE版AEM Forms的6 GB臨時空間加22 GB<br /></td> 
  </tr> 
  <tr> 
   <td>SUSE Linux Enterprise Server</td> 
   <td>英特爾至強E5-2670v2,1 vCPU,2.5 GHz處理器<br /> AWS m3.medium(3 ECU)<br /> RAM:6 GB（64位OS，帶64位JVM）<br />可用磁碟空間：JEE版AEM Forms的6 GB臨時空間加22 GB<br /></td> 
  </tr> 
  <tr> 
   <td>Red Hat Enterprise Linux</td> 
   <td>英特爾至強E5-2670v2,1 vCPU,2.5 GHz處理器<br /> AWS m3.medium(3 ECU)<br /> RAM:6 GB（64位OS，帶64位JVM）<br />可用磁碟空間：JEE上的AEM Forms 6 GB臨時空間加22GB<br /><br /> </td> 
  </tr> 
  <tr> 
   <td>小型生產環境的硬體需求</td> 
   <td> 
    <ul> 
     <li><strong>英特爾供電環境</strong>:英特爾®至強® E5-2680,2.4 GHz或更高。使用雙核處理器將進一步提高效能</li> 
     <li><strong>Sun SPARC支援的環境： </strong> UltraSPARC V或更高版本</li> 
     <li><strong>IBM AIX支援的環境： </strong> Power6或更高版本<br /> </li> 
     <li><strong>記憶體： </strong>4 GB  <br /> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

如需其他需求，請參閱：

* [JEE部署上單伺服器AEM Forms的系統需求](https://www.adobe.com/go/learn_aemforms_sysreq_single_64)
* [JEE部署上的叢集AEM Forms的系統需求](https://www.adobe.com/go/learn_aemforms_sysreq_cluster_64)

## JEE版AEM Forms的支援用戶端 {#supported-clients-for-aem-forms-on-jee}

### Workbench {#workbench}

>[!NOTE]
>
>支援32位和64位作業系統。

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

* 要安裝的磁碟空間：僅適用於Workbench 1.7 GB，在單一驅動器上為2.7 GB，以完整安裝Workbench、Designer和示常式式集400 MB用於臨時安裝目錄 — 在用戶臨時目錄中為200 MB，在Windows臨時目錄中為200 MB

>[!NOTE]
>
>如果所有這些位置都駐留在單個驅動器上，則安裝期間必須有1.5 GB的可用空間。 安裝完成後，將刪除複製到臨時目錄的檔案。

* 運行Workbench的記憶體：2 GB記憶體
* 硬體需求：英特爾®奔騰® 4或AMD等效處理器，1 GHz處理器
* 至少1024 X 768像素或更高的監視器解析度，使用16位元顏色或更高
* TCP/IPv4或TCP/IPv6網路連線至JEE伺服器上的AEM Forms

>[!NOTE]
>
>您必須擁有管理權限，才能在Windows上安裝Workbench。 如果您使用非管理員帳戶進行安裝，安裝程式會提示您輸入適當帳戶的憑證。

### 設計工具 {#designer}

* Microsoft® Windows® 2012 Server R2、Microsoft® Windows® 2016 Server、Microsoft® Windows® 2019 Server、Microsoft® Windows® 10
* 支援PAE、NX和SSE2的1 GHz或更快的處理器。
* 1 GB的RAM（32位）或2 GB的RAM（64位作業系統）
* 32位或20 GB磁碟空間（64位作業系統）為16 GB磁碟空間
* 圖形記憶體 — 128 MB的GPU（建議256 MB）
* 2.35 GB可用硬碟空間
* 1024 X 768像素或更高的監視器解析度
* 視頻硬體加速（可選）
* Acrobat Pro DC、Acrobat Standard DC或Adobe Acrobat Reader DC
* 安裝Designer的管理權限

### Adobe Acrobat和Adobe Reader {#adobe-acrobat-and-adobe-reader}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Acrobat和Adobe Reader（基地）</strong></p> </th> 
   <th><p><strong>支援的修補程式定義</strong></p> </th> 
  </tr> 
  <tr> 
   <td>Acrobat 2017（傳統曲目）</td> 
   <td>17.011.30078或更新版本<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Acrobat DC產品系列針對Acrobat和Reader推出兩種基本上不同的產品：「Classic」和「Continuous」。 如需這兩個追蹤的詳細資訊和比較，請參閱[https://www.adobe.com/go/acrobatdctracks。](https://www.adobe.com/go/acrobatdctracks)

### 瀏覽器 {#browsers}

#### 台式機 {#desktops}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>瀏覽器（基礎）</strong></p> </th> 
   <th><p><strong>支援層級</strong></p> </th> 
   <th><p><strong>支援的修補程式定義</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Microsoft Edge</p> </td> 
   <td><p>答：支援</p> </td> 
   <td><p>Service Pack和更新</p> </td> 
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
>案頭的某些瀏覽器相關例外如下：
>
>* 大部分的現代瀏覽器不再支援NPAPI型外掛程式。 如需其如何影響AEM Forms應用程式和工作流程的詳細資訊，請參閱[中止NPAPI瀏覽器外掛程式及其影響](https://helpx.adobe.com/aem-forms/kb/discontinuation-of-npapi-plugins-impact-on-aem-forms.html)。
>* Safari僅在Macintosh OS X上受支援。


#### 行動用戶端 {#mobile-clients}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>瀏覽器（基礎）</strong></p> </th> 
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
   <td>Android™ 4.4及更新版本上的原生Android瀏覽器</td> 
   <td>所有更新</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* Forms Portal僅支援iPad上的Safari。

>



### AEM Forms應用程式 {#aem-forms-workspace-app}

#### 行動裝置支援 {#mobile-device-support}

AEM Forms應用程式適用於下列平台：

| **平台** | **支援的裝置** |
|---|---|
| Apple iOS | 運行iOS 11及更高版本的iPhone、iPad、iPad Air和iPad mini。 |
| Google Android | Android 4.4(Androird Kit Kat)和高於&#x200B;*[API Level 19和]*。 AEM Forms應用在7英吋和10英吋的三星Galaxy平板電腦、7英吋的Google Nexus平板電腦和流行的智慧手機上獲得認證。 |
| Microsoft Windows | 運行Microsoft Windows 10作業系統的Microsoft Surface設備、平板電腦、筆記型電腦和台式機。 |

### AdobeFlash Player {#adobe-flash-player}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Flash Player（基礎）</strong></p> </th> 
   <th><p><strong>支援的修補程式定義</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p>Flash Player最新版本</p> </td> 
   <td><p>次要版本和更新</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Adobe將於2020年底[停止更新和分發Flash Player。](https://theblog.adobe.com/adobe-flash-update/)

### AdobeDocument Security Extension for Microsoft Office {#adobe-rights-management-extension-for-microsoft-office}

按一下[這裡](https://www.adobe.com/products/livecycle/rightsmanagement/extension/downloads.html)查看AdobeDocument Security Extension for Microsoft® Office的系統要求。

### 客戶支援例外 {#exceptions-to-client-support}

除Reader和Acrobat外，所有指定的客戶端軟體均不支援Microsoft® Windows® 2012。

此外，JEE版AEM Forms在指定的主要和次要支援軟體版本上，也支援更新、修補程式和修正套件。 但是，除非另有指定，否則不支援更新至下一個主要或次要版本。

## 第三方修補程式支援策略 {#third-party-patch-support-policy}

JEE版AEM Forms的協力廠商軟體需求記錄在其各自產品檔案的「系統需求」一節中。 所有檔案皆可從[https://adobe.com/go/learn_aemforms_documentation_64](https://adobe.com/go/learn_aemforms_documentation_64)存取。

JEE第三方參考平台上的AEM Forms會說明在JEE上開發和發行AEM Forms期間，以及該版本JEE上的AEM Forms所支援基礎架構的最低修補程式/服務套件層級，所使用的協力廠商基礎架構的特定修補程式層級。

Adobe在第三方廠商發佈時，支援其發佈的緊急或建議修補程式，假設第三方廠商保證與AEM Forms on JEE支援的版本回溯相容。 Adobe僅支援在JEE檔案中AEM Forms所述的最低修補程式級別之後發行的修補程式。

在某些情況下，Adobe不支援會變更主要功能的協力廠商更新，因此不支援完全回溯相容性。 有關支援的更新的詳細資訊，請參閱[支援的補丁程式定義](https://helpx.adobe.com/aem-forms/aem-forms-third-party-software-patch.html)以了解特定供應商產品以及Adobe支援的補丁程式類型。

在Adobe無法控制的情況下，聲稱向後相容性的第三方補丁程式可能會對Adobe產品或客戶環境產生負面影響。 在這種情況下，Adobe建議客戶在將任何緊急補丁程式應用到關鍵系統之前，先評估這些補丁程式對第三方的影響。 Adobe將與第三方合作，通過正常的Adobe支援計畫或第三方在其補丁程式中糾正該問題，通過合理的業務努力解決此類問題。 這無法保證新發行且受Adobe支援的協力廠商修補程式，能如廠商所記錄或JEE上的AEM Forms所運作。

Adobe保留在任何指定時間點變更AEM Forms JEE版本支援的第三方參考平台及其支援的修補程式定義的權利。

有關第三方修補程式的其他資訊，也可通過搜索Adobe企業支援站點中與產品相關的知識庫文章來找到。

[**聯絡支援**](https://www.adobe.com/tw/account/sign-in.supportportal.html)

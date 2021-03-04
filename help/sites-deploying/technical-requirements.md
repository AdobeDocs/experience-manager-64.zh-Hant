---
title: 技術需求
seo-title: 技術需求
description: 支援的客戶端和伺服器平台清單AEM。
seo-description: 支援的客戶端和伺服器平台清單AEM。
uuid: d5bdcd41-3585-41f7-860d-8068a2931a72
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: platform
discoiquuid: 4d3c4650-3e2a-43b1-ad2d-8d0ae2254ca9
translation-type: tm+mt
source-git-commit: 53154f9ada1062dae4bdccc5eac3d3113cd730a2
workflow-type: tm+mt
source-wordcount: '3273'
ht-degree: 0%

---


# 技術要求{#technical-requirements}

Adobe支援Adobe Experience Manager(AEM)在平台上運行，如本文檔中的以下資訊所詳述。

如果有任何與平台本身特別相關的問題，請直接與平台廠商聯絡。

>[!NOTE]
>
>視您所安裝的平台而定，AEM使用者管理的需求可能會有不同。

## 必備條件 {#prerequisites}

安裝Adobe Experience Manager的最低要求：

* 已安裝Java平台、標準版JDK或其他支援的[Java虛擬機](#java-virtual-machines)
* Experience Manager快速入門檔案（獨立JAR或Web應用程式部署WAR）

### 最小尺寸要求{#minimum-sizing-requirements}

運行Adobe Experience Manager的最低要求：

* 安裝目錄中有5 GB的可用磁碟空間
* 2 GB記憶體

>[!NOTE]
>
>* 數位資產使用案例需要更多的基本記憶體。 如需詳細資訊，請參閱[部署與維護](/help/sites-deploying/deploy.md#default-local-install)。
>* [AEM Forms附加](/help/forms/using/installing-configuring-aem-forms-osgi.md) 封裝需要15 GB的暫存空間。

>



有關詳細資訊，請參閱[硬體尺寸指南](/help/managing/hardware-sizing-guidelines.md)。

### 支援級別{#support-levels}

本檔案列出了Adobe Experience Manager支援的客戶端和伺服器平台。 Adobe提供多種支援級別，包括建議的配置和其他配置。

### 支援的配置{#supported-configurations}

Adobe建議這些配置，並作為標準軟體維護協定的一部分提供完整支援。

<table> 
 <tbody> 
  <tr> 
   <td>支援等級</td> 
   <td>說明<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>答：支援</strong></td> 
   <td>Adobe為此配置提供完整支援和維護。 此配置由Adobe的質量保證流程涵蓋。</td> 
  </tr> 
  <tr> 
   <td><strong>R:受限制的支援</strong></td> 
   <td>為確保客戶專案成功，Adobe在受限制的支援計畫中提供完整支援，這需要符合特定條件。 R級支援需要正式的客戶要求及Adobe確認。 如需詳細資訊，請聯絡Adobe客戶服務。</td> 
  </tr> 
 </tbody> 
</table>

### 不支援的配置{#unsupported-configurations}

| 支援等級 | 說明 |
|---|---|
| **Z:不支援** | 不支援配置。 Adobe不會就配置是否有效發表任何聲明，也不支援它。 |

## 支援的平台{#supported-platforms}

### Java虛擬機{#java-virtual-machines}

應用程式需要Java虛擬機器來執行，此程式由Java開發套件(JDK)散發提供。

Adobe Experience Manager運行下列版本的Java虛擬機：

>[!CAUTION]
>
>建議您追蹤Java廠商的安全性公告，以確保生產環境的安全性，並安裝最新的Java更新。

<table> 
 <tbody> 
  <tr> 
   <td>平台</td> 
   <td>支援級別<br /> </td> 
  </tr> 
  <tr> 
   <td>OracleJava SE 11 JDK [1]</td> 
   <td>Z:不支援 </td> 
  </tr> 
  <tr> 
   <td>OracleJava SE 10 JDK [1]</td> 
   <td>Z:不支援 </td> 
  </tr> 
  <tr> 
   <td>OracleJava SE 9 JDK [1]</td> 
   <td>Z:不支援</td> 
  </tr> 
  <tr> 
   <td><strong>OracleJava SE 8 JDK - 64位元</strong></td> 
   <td>答：支援的[3]<br /> </td> 
  </tr> 
  <tr> 
   <td>IBM J9 VM —— 內部版本2.9、JRE 1.8.0 [2]</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>IBM J9 VM —— 內部版本2.8、JRE 1.8.0 [2]</td> 
   <td>答：支援</td> 
  </tr> 
 </tbody> 
</table>

1. Oracle已改為OracleJava SE產品的「長期支援」(LTS)模型。 Java 9和10是非LTS版本，依Oracle區分(請參閱OracleJava SE支援路線圖](https://www.oracle.com/technetwork/java/eol-135779.html))。 [Adobe將僅提供LTS版Java的支援，以在生產AEM中執行。

1. IBM JRE僅與WebSphere Application Server結合使用。
1. 對OracleJava SE JDK的支援和分發，包括公開更新結束後LTS版本的所有維護更新，將直接由使用OracleJava SE技術的所有客AEM戶Adobe支援。 如需詳細資訊，請參閱[Adobe Experience ManagerQ&amp;A](assets/adobe-oracle-java-license-agreement.pdf)的OracleJava支援。

### 儲存和持久性{#storage-persistence}

有各種選項可部署Adobe Experience Manager的儲存庫。 有關支援的技術和儲存選項，請參見以下清單。

<table> 
 <tbody> 
  <tr> 
   <td><strong>平台</strong></td> 
   <td><strong>說明</strong></td> 
   <td><strong>支援等級</strong></td> 
  </tr> 
  <tr> 
   <td><strong>具有TAR檔案[1]的檔案系統</strong></td> 
   <td>存放庫</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td><strong>具有資料儲存[1]的檔案系統</strong></td> 
   <td>二進位檔</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>將二進位檔案儲存在檔案系統[1]上的TAR檔案中</td> 
   <td>二進位檔</td> 
   <td>Z:不支援生產</td> 
  </tr> 
  <tr> 
   <td>AmazonS3</td> 
   <td>二進位檔</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>Microsoft Azure Blob儲存空間</td> 
   <td>二進位檔</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.6 [5, 6]</td> 
   <td>存放庫</td> 
   <td>答：受限制支援</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.4 [2, 3, 6]</td> 
   <td>存放庫</td> 
   <td>答：受限制支援</td> 
  </tr> 
  <tr> 
   <td>MySQL 5.7</td> 
   <td>Forms資料庫</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>IBM DB2 11.1<br /> </td> 
   <td>Forms資料庫</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>IBM DB2 10.5</td> 
   <td>儲存庫和Forms資料庫</td> 
   <td>R:受限制的支援(4)</td> 
  </tr> 
  <tr> 
   <td>Oracle資料庫12c(12.1.x)</td> 
   <td>儲存庫和Forms資料庫</td> 
   <td>R:受限制的支援</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2017</td> 
   <td>Forms資料庫</td> 
   <td>Z:不支援(4)</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2016</td> 
   <td>Forms資料庫</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2014</td> 
   <td>Forms資料庫</td> 
   <td>R:受限制的支援(4)</td> 
  </tr> 
  <tr> 
   <td><strong>Apache Lucene（Quickstart內置）</strong></td> 
   <td>搜尋服務</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>Apache Solr</td> 
   <td>搜尋服務</td> 
   <td>答：支援</td> 
  </tr> 
 </tbody> 
</table>

1. 「檔案系統」包括符合POSIX的塊儲存。 其中包括網路儲存技術。 請注意，檔案系統效能可能會有所不同，並影響整體效能。 建議將測試與網AEM絡／遠程檔案系統結合使用。
1. 中不支援MongoDB共用AEM。
1. 僅支援MongoDB儲存引擎WiredTiger。
1. 不支援AEM Forms。
1. AEM 6.4.2.0 版開始支援 MongoDB Enterprise 3.6。
1. 對MongoDB 3.4的支援已到期(EOL)，而MongoDB 3.6預計將於2021年4月30日到期。 請注意，Adobe將僅提供未來產品相AEM關問題的支援。

>[!NOTE]
>
>有關AEM Communities功能的其他資訊，請參見[部署社區](/help/communities/deploy-communities.md)。

>[!NOTE]
>
>MongoDB是協力廠商軟體，不包含在授權套件AEM中。 如需詳細資訊，請參閱[MongoDB授權政策](https://www.mongodb.org/about/licensing/)頁面。
>
>為了充份運用MongoDB的部AEM署，Adobe建議授權MongoDB企業版，以從專業支援中獲益。 如需詳細資訊，請參閱[建議部署](/help/sites-deploying/recommended-deploys.md#prerequisites-and-recommendations-when-deploying-aem-with-mongomk)。
>
>該許可證包括一個標準副本集，該副本集由一個主實例和兩個輔助實例組成，可用於作者或發佈部署。
>
>如果您想要在MongoDB上執行作者和發佈，則需要購買兩個不同的授權。
>
>Adobe客戶服務將協助與MongoDB搭配使用相關的資格確認問AEM題。
>
>如需詳細資訊，請參閱[MongoDB forAdobe Experience Manager頁面](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager)。

>[!NOTE]
>
>上述支援的關聯式資料庫是協力廠商軟體，不包含在授權套件AEM中。
>
>為了使用支AEM持的關係資料庫運行6.4，需要與資料庫供應商簽訂單獨的支援合同。 Adobe客戶服務將協助您針對6.4版使用關聯式資料庫的相關AEM資格問題。
>
>**請注意，大多數關係型資料庫目前都受到Level-R(6.4AEM)的支援，Level-R隨附支援標準和支援計畫，如上述Level-R說明所述。**

### Servlet引擎／應用程式伺服器{#servlet-engines-application-servers}

Adobe Experience Manager可以作為獨立伺服器（快速入門JAR檔案）或作為第三方應用程式伺服器（WAR檔案）中的Web應用程式運行。

所需的Servlet API最低版本為Servlet 3.1，但低於Servlet 4.0。

| 平台 | 支援等級 |
|---|---|
| **快速入門內建Servlet引擎(Jetty 9.3)** | 答：支援 |
| OracleWebLogic Server 12.2(12cR2) | 答：支援 |
| IBM WebSphere Application Server Continuous Delivery(LibertyProfile)與Web Profile 7.0和IBM JRE 1.8 | 答：支援 |
| IBM WebSphere Application Server 9.0 | 答：支援 |
| Apache Tomcat 8.5.x | 答：支援 |
| JBoss EAP 7.1.0與JBoss應用程式伺服器 | 答：支援(1) |
| JBoss EAP 7.0.0與JBoss應用程式伺服器 | 答：支援 |

1. 不支援AEM Forms。

### 伺服器作業系統{#server-operating-systems}

Adobe Experience Manager與下列伺服器平台搭配使用：

<table> 
 <tbody> 
  <tr> 
   <td><strong>平台</strong></td> 
   <td><strong>支援等級</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Linux，基於Red Hat分發</strong></td> 
   <td>答：支援(1)</td> 
  </tr> 
  <tr> 
   <td>Linux，基於Debian分發，包括 烏邦圖</td> 
   <td>答：支援(4)</td> 
  </tr> 
  <tr> 
   <td>Linux，基於SUSE分發</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2016</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2012 R2</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>OracleSolaris 11</td> 
   <td>答：受限制(3,5,7)<br /> R:新合約的限制支援</td> 
  </tr> 
  <tr> 
   <td>IBM AIX 7.2</td> 
   <td>答：受限制(2,5,7)<br /> R:新合約的限制支援</td> 
  </tr> 
 </tbody> 
</table>

1. Linux內核2.6、3.x和4.x包括Red Hat發佈的衍生產品，包括Red Hat Enterprise Linux、CentOS、OracleLinux和AmazonLinux。 AEM Forms附加功能僅在CentOS 7和Red Hat Enterprise Linux 7上受支援。
1. AEM Assets:請參閱[支援中繼資料XMP回寫](#requirements-for-aem-assets-xmp-metadata-write-back)一節
1. AEM Assets:不支援Dynamic Media影像。 Dynamic Media視訊受支援。
1. AEM Forms僅在Ubuntu 16.04 LTS上受支援。
1. AEM Assets:不支援[原始檔案轉換](/help/assets/camera-raw.md)
1. AEM Forms:不支援生產環境
1. AEM Assets:不支援[增強的PDF點陣化器](/help/assets/aem-pdf-rasterizer.md)
1. AEM Forms:不支援

### 虛擬和雲計算環境{#virtual-cloud-computing-environments}

Adobe Experience Manager在雲計算環境(如Microsoft Azure和AmazonWeb Services(AWS))上的虛擬機中運行時，受支援，符合本頁所列的技術要求，並且符合Adobe的標準支援條款。

Adobe建議使用Adobe Managed Services部署AEM在Azure或AWS上。 Adobe Managed Services為專家提供在這些雲計算環境中部署和AEM運作的經驗和技能。 請參閱我們有關Adobe Managed Services](https://www.adobe.com/marketing-cloud/enterprise-content-management/managed-services-cloud-platform.html?aemClk=t)的其他檔案。[

在部署在Azure或AEMAWS或任何其他雲計算環境上的所有其他情況下，將根據本頁所列的技術規格，對虛擬計算環境提供Adobe支援。 與在任何這些雲環境中AEM運行相關的任何已報告問題，都必須獨立於特定於雲計算環境的任何雲服務進行重制，除非雲服務作為本頁所列技術要求（例如Azure Blob儲存或AWS S3）的一部分特別受支援。

如需有關如何在Adobe Managed Services以外部署AEMAzure或AWS的建議，我們強烈建議直接與雲端供應商或Adobe合作夥伴合作，以支援在您選擇的雲端環境AEM中部署。 所選雲端供應商或合作夥伴將負責架構的規模規格、設計和實作，以符合您的特定效能、負載、延展性及安全性需求。

### Dispatcher Platforms(Web Servers){#dispatcher-platforms-web-servers}

Dispatcher是快取和負載平衡元件。 [下載最新的Dispatcher版本](https://helpx.adobe.com/experience-manager/dispatcher/release-notes.html)。Experience Manager6.4需要Dispatcher 4.3.1版或更高版本。

支援將下列Web伺服器與Dispatcher 4.3.1版一起使用：

| 平台 | 支援等級 |
|---|---|
| **Apache httpd 2.4.x** （另請參見下面的1,2） | 答：支援 |
| Microsoft IIS 10(Internet Information Server) | 答：支援 |
| Microsoft IIS 8.5(Internet Information Server) | 答：支援 |

1. 以Apache httpd原始碼為基礎的Web伺服器，其支援等級將與其所依據的httpd版本相同。 如有疑問，請向Adobe洽詢有關各伺服器產品的支援等級確認。 以下情況：

   1. HTTP伺服器僅使用官方的Apache來源散發，或
   1. HTTP伺服器是以其執行作業系統的方式傳送。 範例：IBM HTTP Server,OracleHTTP Server

1. Dispatcher不適用於Windows作業系統的Apache 2.4.x。

## 支援的客戶端平台{#supported-client-platforms}

### 製作使用者介面{#supported-browsers-for-authoring-user-interface}支援的瀏覽器

Adobe Experience Manager用戶介面適用於以下客戶端平台。 所有瀏覽器都會使用預設的增效模組和附加元件集進行測試。

使用者AEM介面已針對較大螢幕（通常是筆記型電腦和桌上型電腦）和平板電腦外形規格（例如Apple iPad或Microsoft Surface）進行最佳化。 不支援電話外形。

>[!NOTE]
>
>**支援具快速發行週期的瀏覽器：**
>
>Mozilla Firefox、Google Chrome和Microsoft Edge發行版本每隔幾個月更新一次。 Adobe承諾為Adobe Experience Manager提供更新，以維持下列即將推出的這些瀏覽器版本的支援等級。

<table> 
 <tbody> 
  <tr> 
   <td><strong>瀏覽器</strong></td> 
   <td><strong>支援UI<br /> </strong></td> 
   <td><strong>支援Classic UI</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Google Chrome(Evergreen)</strong></td> 
   <td>答：支援</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>Microsoft Edge(Evergreen)</td> 
   <td>答：支援</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>Microsoft Internet Explorer 11</td> 
   <td>答：支援</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>Mozilla Firefox(Evergreen)</td> 
   <td>答：支援</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>Mozilla Firefox最後一個ESR [1]</td> 
   <td>答：支援</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>macOS版Apple Safari 12.x</td> 
   <td>答：支援</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>macOS版Apple Safari 11.x</td> 
   <td>答：支援</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>macOS版Apple Safari 10.x</td> 
   <td>答：支援</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>iOS 12.x版的Apple Safari</td> 
   <td>答：支援[2]</td> 
   <td>Z:不支援</td> 
  </tr> 
  <tr> 
   <td>iOS 11.x版的Apple Safari</td> 
   <td>答：支援[2]</td> 
   <td>Z:不支援</td> 
  </tr> 
  <tr> 
   <td>iOS 10.3版的Apple Safari</td> 
   <td>答：支援[2]</td> 
   <td>Z:不支援</td> 
  </tr> 
 </tbody> 
</table>

1. Firefox的延伸支援版本[在mozilla.org](https://www.mozilla.org/en-US/firefox/organizations/faq/)上進一步瞭解此資訊
1. 支援Apple iPad

### 支援的網站瀏覽器{#supported-browsers-for-websites}

一般而言，AEM Sites網站的瀏覽器支援取決於頁面範本AEM的實作、設計和元件輸出，因此由執行這些部分的一方控制。

### WebDAV客戶端{#webdav-clients}

**Microsoft Windows 7+**

要成功與Microsoft Windows 7+連接到未使用AEMSSL保護的實例，必須在Windows中啟用基於不安全網路的基本身份驗證。 這要求在WebClient的Windows註冊表中進行更改：

1. 找到註冊表子項：

   * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WebClient\Parameters

1. 使用值2或更多的值，將BasicAuthLevel註冊表項添加到此子鍵。

請參閱[Microsoft支援KB 841215](https://support.microsoft.com/default.aspx/kb/841215)。

要提高Windows下WebDav客戶端的響應性——請參見[ Microsoft支援KB 2445570](https://support.microsoft.com/kb/2445570)

## 其他平台說明{#additional-platform-notes}

本節提供有關運行Adobe Experience Manager及其附加元件的特殊說明和更詳細的資訊。

### IPv4和IPv6 {#ipv-and-ipv}

Adobe Experience Manager的所有元素（實例、Dispatcher）都可以安裝在IPv4和IPv6網路中。

操作是無縫的，因為無需特殊配置。 如有需要，您只需使用適合您網路類型的格式來指定IP位址。

這表示當需要指定IP位址時，您可以（視需要）從以下位置選擇：

* IPv6地址

   例如`https://[ab12::34c5:6d7:8e90:1234]:4502`

* IPv4地址

   例如`https://123.1.1.4:4502`

* 伺服器名稱

   例如，`https://www.yourserver.com:4502`

* `localhost`的預設情況將解釋為IPv4和IPv6網路安裝

   例如，`http://localhost:4502`

### Dynamic MediaAEM附加元件{#requirements-for-aem-dynamic-media-add-on}的要求

預設AEM禁用Dynamic Media。 請參閱[啟用Dynamic Media](/help/assets/config-dynamic.md#enabling-dynamic-media)。

啟用Dynamic Media後，將適用下列額外系統需求：
>[!NOTE]
>
>如果您使用Dynamic Media-混合模式，則以下系統要求僅適用&#x200B;**__**;Dynamic Media-混合模式具有嵌入式映像伺服器，僅在某些作業系統上通過認證。
>
>對於運行Dynamic Media-Scene7模式（即&#x200B;**dynamicmedia_scene7**&#x200B;運行模式）的Dynamic Media客戶，沒有其他系統要求；系統要求與相同AEM。 Dynamic Media-Scene7模式架構使用雲端影像服務，而非內嵌於中的服務AEM。

#### 硬體{#hardware}

下列硬體需求適用於Linux和Windows作業系統：

* 至少具有4個內核的Intel Xeon或AMD Opteron CPU
* 最低16GB的記憶體

#### Linux {#linux}

在Linux上使用Dynamic Media需要下列先決條件：

* RedHat Enterprise 7或CentOS 7及更新版本及最新的修補程式
* 64位元作業系統
* 已停用交換（建議）
* SELinux已停用（請參閱以下附註）

>[!NOTE]
>
>如果地區設定為LC_CTYPE不等於en_US.UTF-8，則會使動態媒體無法運作。 要查看其值是什麼，請在命令提示符下鍵入&quot;locale&quot;。 如果未設定為該值，則在運行前鍵入&quot;export LC_CTYPE=&quot;，將LC_CTYPE環境變數設定為空字串AEM。

>[!NOTE]
>
>**啟用SELinux時，** 禁用SELinux：影像服務無法工作。預設會啟用此選項。 要解決此問題，請編輯&#x200B;**/etc/selinux/config**&#x200B;檔案，並將SELinux值從：
>
>`SELINUX=enforcing` 至  `SELINUX=disabled`

>[!NOTE]
>
>**NUMA體系結構：具有AMD64和英特爾EM64T處理器的系統通常配置為非統一記憶體體系結構(NUMA)平台，這意味著內核在啟動時構建多個記憶體節點，而不是構建單個記憶體節點。** 
>
>該多節點結構可導致在其它節點耗盡之前在一個或多個節點上耗盡儲存器。 當記憶體耗盡時，內核可以決定中止進程（例如，映像伺服器或平台伺服器），即使有可用記憶體。
>
>因此，Adobe建議，如果您運行這樣的系統，使用&#x200B;**numa=off**&#x200B;引導選項關閉NUMA，以避免內核導致這些進程中斷。

>[!NOTE]
>
>**伺服器的主機名必須可** 以解析：確保伺服器的主機名可解析為IP地址。如果不能，請將完全限定的主機名和IP地址添加到&#x200B;**/etc/hosts**:
>
>`<ip address> <fully qualified hostname>`

#### Windows {#windows}

* Microsoft Windows Server 2016
* 交換空間至少等於物理記憶體(RAM)的兩倍

若要在Windows上使用Dynamic Media，必須安裝Microsoft Visual Studio 2010、2013和2015 x64和x86可轉散發套件。

x64

* 您可在[https://www.microsoft.com/en-us/download/details.aspx?id=13523](https://www.microsoft.com/en-us/download/details.aspx?id=13523)找到Microsoft Visual Studio 2010的可再散發版本
* Microsoft Visual Studio 2013可在[https://www.microsoft.com/en-us/download/details.aspx?id=40784](https://www.microsoft.com/en-us/download/details.aspx?id=40784)上重新分發
* 您可在[https://www.microsoft.com/en-us/download/details.aspx?id=48145](https://www.microsoft.com/en-us/download/details.aspx?id=48145)找到Microsoft Visual Studio 2015的可再散發版本

x86

* 您可在[https://www.microsoft.com/en-in/download/details.aspx?id=5555](https://www.microsoft.com/en-in/download/details.aspx?id=5555)找到Microsoft Visual Studio 2010的可再散發版本
* Microsoft Visual Studio 2013可在[https://www.microsoft.com/en-in/download/details.aspx?id=40769](https://www.microsoft.com/en-in/download/details.aspx?id=40769)上重新分發
* 您可在[https://www.microsoft.com/en-us/download/details.aspx?id=52685](https://www.microsoft.com/en-us/download/details.aspx?id=52685)找到Microsoft Visual Studio 2015的可再散發版本

#### MacOS {#macos}

* 10.9.x及更新版本
* 僅支援試用與示範用途

### AEM FormsPDF產生器的需求{#requirements-for-aem-forms-pdf-generator}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>產品</strong></p> </th> 
   <th><p><strong>支援的格式，可轉換為PDF</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html">Acrobat2017年古典田徑</a></p> </td> 
   <td><p>XPS，影像格式(BMP、GIF、JPEG、JPG、TIF、TIFF、PNG、JPF、JPX、JP2、J2K、J2C、JPC)、HTML、HTM、DWG、DXF和DWF</p> </td> 
  </tr> 
  <tr> 
   <td>Microsoft® Project 2016</td> 
   <td>MPP</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Publisher 2016</td> 
   <td>PUB</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office Visio 2016</td> 
   <td>VSD</td> 
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
   <td>Corel WordPerfect X7</td> 
   <td>WP、WPD<br /> </td> 
  </tr> 
  <tr> 
   <td>OpenOffice 4.1.2</td> 
   <td>ODT、ODP、ODS、ODG、ODF、SXW、SXI、SXC、SXD、XLS、DOC、DOCX、PPT、PPTX、影像格式(BMP、GIF、JPEG、JPG、TIF、TIF、 PF、 PNG、 PNG)、JPF、JPX、JP2、J2K、J2C、JPC)、HTML、HTM、RTF和TXT</td> 
  </tr> 
  <tr> 
   <td><p>OpenOffice 3.4</p> </td> 
   <td><p>ODT、ODP、ODS、ODG、ODF、SXW、SXI、SXC、SXD、XLS、DOC、DOCX、PPT、PPTX、影像格式(BMP、GIF、JPEG、JPG、TIF、TIF、 PF、 PNG、 PNG)、JPF、JPX、JP2、J2K、J2C、JPC)、HTML、HTM、RTF和TXT</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>PDF產生器僅支援英文、法文、德文和日文版支援的作業系統和應用程式。
>
>此外：
>
>* PDF產生器需要[Acrobat2017傳統音軌版本17.011.30078或更新版本](https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html)才能執行轉換。
>* AEM Forms僅支援32位元版本的支援軟體。
>* OCR PDF（可搜尋的PDF）、Optimize PDF和Export PDF功能僅在Microsoft Windows上受支援。
>* AIX上已停用HTML2PDF服務。
>* OpenOffice專用的PDF產生器轉換僅在Windows、Linux和Solaris上受支援。
>* OCR PDF、Optimize PDF和Export PDF功能僅在Windows上受支援。
>* Acrobat的版本隨附於AEM Forms，以啟用PDF產生器功能。 套裝版本僅能在AEM Forms授權期間以程式設計方式存取，以搭配AEM FormsPDF產生器使用。 如需詳細資訊，請參閱AEM Forms產品說明（依部署而定）([On-Premise](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html)或[Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html))&quot;

>



### AEM Forms設計人員{#requirements-for-aem-forms-designer}的需求

* Microsoft® Windows® 2012 Server R2、Microsoft® Windows® 2016 Server、Microsoft® Windows® 2019 Server、Microsoft® Windows® 10
* 支援PAE、NX和SSE2的1 GHz或速度更快的處理器。
* 64位元作業系統需1 GB的記憶體（32位元或2 GB的記憶體）
* 64位元作業系統需要16 GB的磁碟空間（32位元或20 GB的磁碟空間）
* 圖形記憶體- 128 MB的GPU（建議使用256 MB）
* 2.35 GB的可用硬碟空間
* DVD-ROM光碟機
* 1024 X 768像素或更高的螢幕解析度
* 視訊硬體加速（選用）
* Acrobat Pro DC、Acrobat Standard DC或Adobe Acrobat Reader DC
* 安裝Designer的管理權限

### AEM Assets元XMP資料回寫{#requirements-for-aem-assets-xmp-metadata-write-back}的要求

支XMP持並啟用以下平台和檔案格式的回寫：

**作業系統**

* Linux（32位元，需要64位元系統上的32位元應用程式支援）。 如需安裝32位元用戶端程式庫的步驟，請參閱[如何啟XMP用64位元RedHat Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html)上的擷取和回寫。

* Windows Server
* OracleSolaris
* Mac OS X（64位元）

**檔案格式**

* JPEG
* PNG
* TIFF
* PDF
* INDD
* AI
* EPS

### AEM Screens播放器{#requirements-for-aem-screens-player}的需求

AEM Screens播放器3.3.x版支援下列作業系統：

* Microsoft Windows 10 Enterprise LTSB
* Google Chome OS 62+
* Google Android 5.1.1（含更新的Android系統WebView 52+版）
* Apple iOS 10.3+
* Apple macOS 10.12+

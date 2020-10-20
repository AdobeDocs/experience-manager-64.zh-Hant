---
title: 技術需求
seo-title: 技術需求
description: AEM支援的用戶端和伺服器平台清單。
seo-description: AEM支援的用戶端和伺服器平台清單。
uuid: d5bdcd41-3585-41f7-860d-8068a2931a72
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: platform
discoiquuid: 4d3c4650-3e2a-43b1-ad2d-8d0ae2254ca9
translation-type: tm+mt
source-git-commit: d09956e5e7fb42e9c4b145e027778f209876239a
workflow-type: tm+mt
source-wordcount: '3142'
ht-degree: 0%

---


# 技術需求{#technical-requirements}

Adobe支援平台上的Adobe Experience Manager(AEM)，如本檔案下列資訊所詳述。

如果有任何與平台本身特別相關的問題，請直接與平台廠商聯絡。

>[!NOTE]
>
>視您安裝AEM的平台而定，可能會有不同的使用者管理需求集。

## 必備條件 {#prerequisites}

安裝Adobe Experience Manager的最低要求：

* 已安裝Java Platform、Standard Edition JDK或其他支援的 [Java虛擬機](#java-virtual-machines)
* Experience Manager Quickstart檔案（獨立JAR或Web應用程式部署WAR）

### 最小尺寸要求 {#minimum-sizing-requirements}

執行Adobe Experience Manager的最低需求：

* 安裝目錄中有5 GB的可用磁碟空間
* 2 GB記憶體

>[!NOTE]
>
>* 數位資產使用案例需要更多的基本記憶體。 如需詳 [細資訊，請參閱部署](/help/sites-deploying/deploy.md#default-local-install) 與維護。
>* [AEM Forms附加元件套件](/help/forms/using/installing-configuring-aem-forms-osgi.md) ，需要15 GB的暫存空間。

>



請參閱硬體 [調整規模指引](/help/managing/hardware-sizing-guidelines.md) ，以取得詳細資訊。

### 支援等級 {#support-levels}

本檔案列出Adobe Experience Manager支援的用戶端和伺服器平台。 Adobe針對建議的組態和其他組態提供數種支援等級。

### 支援的組態 {#supported-configurations}

Adobe建議您進行這些組態，並在標準軟體維護合約中提供完整支援。

<table> 
 <tbody> 
  <tr> 
   <td>支援等級</td> 
   <td>說明<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>答：支援</strong></td> 
   <td>Adobe提供此組態的完整支援與維護。 Adobe的品質保證程式涵蓋此設定。</td> 
  </tr> 
  <tr> 
   <td><strong>R:受限制的支援</strong></td> 
   <td>為確保客戶專案成功，Adobe在受限制的支援計畫中提供完整支援，這需要符合特定條件。 R級支援需要Adobe正式向客戶提出要求及確認。 如需詳細資訊，請聯絡Adobe客戶服務。</td> 
  </tr> 
 </tbody> 
</table>

### 不支援的組態 {#unsupported-configurations}

| 支援等級 | 說明 |
|---|---|
| **Z:不支援** | 不支援配置。 Adobe不會就設定是否有效發表任何陳述，也不支援。 |

## 支援的平台 {#supported-platforms}

### Java虛擬機 {#java-virtual-machines}

應用程式需要Java虛擬機器來執行，此程式由Java開發套件(JDK)散發提供。

Adobe Experience Manager可與下列Java虛擬機版本搭配運作：

>[!CAUTION]
>
>建議您追蹤Java廠商的安全性公告，以確保生產環境的安全性，並安裝最新的Java更新。

<table> 
 <tbody> 
  <tr> 
   <td>平台</td> 
   <td>支援等級<br /> </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 11 JDK [1]</td> 
   <td>Z:不支援 </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 10 JDK [1]</td> 
   <td>Z:不支援 </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 9 JDK [1]</td> 
   <td>Z:不支援</td> 
  </tr> 
  <tr> 
   <td><strong>Oracle Java SE 8 JDK - 64位</strong></td> 
   <td>答：支援[3]<br /> </td> 
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

1. Oracle已改為Oracle Java SE產品的「長期支援」(LTS)模型。 Java 9和10是Oracle發行的非LTS版本(請參 [閱Oracle Java SE支援路線圖](https://www.oracle.com/technetwork/java/eol-135779.html))。 Adobe僅提供LTS版Java的支援，以在生產中執行AEM。

1. IBM JRE僅與WebSphere Application Server結合使用。
1. Adobe將直接支援所有使用Oracle Java SE技術的AEM客戶，支援和散發Oracle Java SE JDK，包括公開更新結束後所有LTS版本的維護更新。 如需詳 [細資訊，請參閱Adobe Experience Manager Q&amp;A的Oracle Java](assets/adobe-oracle-java-license-agreement.pdf) 支援。

### 儲存空間與永續性 {#storage-persistence}

Adobe Experience Manager的儲存庫有多種部署選項。 有關支援的技術和儲存選項，請參見以下清單。

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
   <td>Amazon S3</td> 
   <td>二進位檔</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>Microsoft Azure Blob儲存空間</td> 
   <td>二進位檔</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.6 [5]</td> 
   <td>存放庫</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.4 [2, 3]</td> 
   <td>存放庫</td> 
   <td>答：支援</td> 
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
   <td>儲存庫和表單資料庫</td> 
   <td>R:受限制的支援(4)</td> 
  </tr> 
  <tr> 
   <td>Oracle Database 12c(12.1.x)</td> 
   <td>儲存庫和表單資料庫</td> 
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

1. 「檔案系統」包括符合POSIX的塊儲存。 其中包括網路儲存技術。 請注意，檔案系統效能可能會有所不同，並影響整體效能。 建議您將測試AEM與網路／遠端檔案系統結合載入。
1. AEM不支援MongoDB Sharding。
1. 僅支援MongoDB儲存引擎WiredTiger。
1. AEM Forms不支援。
1. 從AEM 6.4.2.0版開始，支援MongoDB Enterprise 3.6。

>[!NOTE]
>
>如需 [AEM Communities功能的其他相關資訊，請參閱部署社群](/help/communities/deploy-communities.md) 。

>[!NOTE]
>
>MongoDB是協力廠商軟體，不包含在AEM授權套件中。 如需詳細資訊，請參 [閱MongoDB授權政策頁](https://www.mongodb.org/about/licensing/) 。
>
>為了充份運用MongoDB的AEM部署，Adobe建議您授權MongoDB企業版，以便從專業支援中獲益。 如需詳 [細資訊](/help/sites-deploying/recommended-deploys.md#prerequisites-and-recommendations-when-deploying-aem-with-mongomk) ，請參閱建議的部署。
>
>該許可證包括一個標準副本集，該副本集由一個主實例和兩個輔助實例組成，可用於作者或發佈部署。
>
>如果您想要在MongoDB上執行作者和發佈，則需要購買兩個不同的授權。
>
>Adobe客戶服務將協助您針對搭配AEM使用MongoDB的相關資格問題。
>
>如需詳細資訊，請參 [閱Adobe Experience Manager專用的MongoDB頁面](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager)。

>[!NOTE]
>
>上述支援的關聯式資料庫是協力廠商軟體，不包含在AEM授權套件中。
>
>若要使用支援的關係式資料庫執行AEM 6.4，必須與資料庫廠商簽訂個別的支援合約。 Adobe客戶服務將協助您針對AEM 6.4使用關係式資料庫的相關資格問題。
>
>**請注意，AEM 6.4的Level-R目前支援大部分的關聯式資料庫，此Level-R隨附支援標準和支援方案，如上述Level-R說明所述。**

### Servlet引擎／應用程式伺服器 {#servlet-engines-application-servers}

Adobe Experience Manager可以作為獨立伺服器（快速入門JAR檔案）或作為第三方應用程式伺服器（WAR檔案）中的Web應用程式運行。

所需的Servlet API最低版本為Servlet 3.1，但低於Servlet 4.0。

| 平台 | 支援等級 |
|---|---|
| **快速入門內建Servlet引擎(Jetty 9.3)** | 答：支援 |
| Oracle WebLogic Server 12.2(12cR2) | 答：支援 |
| IBM WebSphere Application Server Continuous Delivery(LibertyProfile)與Web Profile 7.0和IBM JRE 1.8 | 答：支援 |
| IBM WebSphere Application Server 9.0 | 答：支援 |
| Apache Tomcat 8.5.x | 答：支援 |
| JBoss EAP 7.1.0與JBoss應用程式伺服器 | 答：支援(1) |
| JBoss EAP 7.0.0與JBoss應用程式伺服器 | 答：支援 |

1. AEM Forms不支援。

### 伺服器作業系統 {#server-operating-systems}

Adobe Experience Manager可與下列伺服器平台搭配使用：

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
   <td>Oracle Solaris 11</td> 
   <td>答：受限制(3,5,7)<br /> R:新合約的限制支援</td> 
  </tr> 
  <tr> 
   <td>IBM AIX 7.2</td> 
   <td>答：受限制(2,5,7)<br /> R:新合約的限制支援</td> 
  </tr> 
 </tbody> 
</table>

1. Linux內核2.6、3.x和4.x包括Red Hat分發的衍生產品，包括Red Hat Enterprise Linux、CentOS、Oracle Linux和Amazon Linux。 AEM Forms附加元件功能僅在CentOS 7和Red Hat Enterprise Linux 7上受支援。
1. AEM Assets:請參閱「 [XMP中繼資料回寫支援」一節](#requirements-for-aem-assets-xmp-metadata-write-back)
1. AEM Assets:不支援動態媒體影像。 支援動態媒體視訊。
1. AEM Forms僅在Ubuntu 16.04 LTS上受支援。
1. AEM Assets:不支援原始 [檔案轉換](/help/assets/camera-raw.md)
1. AEM Forms:不支援生產環境
1. AEM Assets:不支援增強的 [PDF點陣化器](/help/assets/aem-pdf-rasterizer.md)
1. AEM Forms:不支援

### 虛擬和雲計算環境 {#virtual-cloud-computing-environments}

Adobe Experience Manager在雲計算環境(例如Microsoft Azure和Amazon Web Services(AWS))的虛擬機器中執行時受到支援，符合本頁所列的技術要求，並符合Adobe的標準支援條款。

Adobe建議使用Adobe Managed Services在Azure或AWS上部署AEM。 Adobe Managed Services為專家提供在這些雲端運算環境中部署和操作AEM的經驗和技能。 請參閱我們有關 [Adobe Managed Services的其他檔案](https://www.adobe.com/marketing-cloud/enterprise-content-management/managed-services-cloud-platform.html?aemClk=t)。

在部署AEM至Azure或AWS或任何其他雲端運算環境的所有其他情況下，Adobe將依照本頁所列技術規格，對虛擬計算環境提供支援。 與在任何這些雲端環境中執行的AEM相關的任何已報告問題，都必須獨立於雲端計算環境專用的任何雲端服務來重制，除非雲端服務是本頁所列技術需求中特別支援的一部分，例如Azure Blob儲存空間或AWS S3。

如需有關如何在Adobe Managed Services以外的Azure或AWS上部署AEM的建議，我們強烈建議直接與雲端供應商或支援在您選擇的雲端環境中部署AEM的Adobe合作夥伴合作。 所選雲端供應商或合作夥伴將負責架構的規模規格、設計和實作，以符合您的特定效能、負載、延展性及安全性需求。

### Dispatcher Platforms(Web Servers) {#dispatcher-platforms-web-servers}

Dispatcher是快取和負載平衡元件。 [下載最新的Dispatcher版本](https://helpx.adobe.com/experience-manager/dispatcher/release-notes.html)。 Experience Manager 6.4需要Dispatcher 4.3.1版或更新版本。

支援將下列Web伺服器與Dispatcher 4.3.1版一起使用：

| 平台 | 支援等級 |
|---|---|
| **Apache httpd 2.4.x** （另請參見下面的1,2） | 答：支援 |
| Microsoft IIS 10(Internet Information Server) | 答：支援 |
| Microsoft IIS 8.5(Internet Information Server) | 答：支援 |

1. 以Apache httpd原始碼為基礎的Web伺服器，其支援等級將與其所依據的httpd版本相同。 如有疑問，請向Adobe洽詢有關個別伺服器產品的支援等級。 以下情況：

   1. HTTP伺服器僅使用官方的Apache來源散發，或
   1. HTTP伺服器是以其執行作業系統的方式傳送。 範例：IBM HTTP Server、Oracle HTTP Server

1. Dispatcher不適用於Windows作業系統的Apache 2.4.x。

## 支援的用戶端平台 {#supported-client-platforms}

### 製作使用者介面的支援瀏覽器 {#supported-browsers-for-authoring-user-interface}

Adobe Experience Manager使用者介面適用於下列用戶端平台。 所有瀏覽器都會使用預設的增效模組和附加元件集進行測試。

AEM使用者介面已針對較大螢幕（通常是筆記型電腦和桌上型電腦）和平板電腦外形規格（例如Apple iPad或Microsoft Surface）進行最佳化。 不支援電話外形。

>[!NOTE]
>
>**支援具快速發行週期的瀏覽器：**
>
>Mozilla Firefox、Google Chrome和Microsoft Edge發行版本每隔幾個月更新一次。 Adobe致力於提供Adobe Experience Manager更新，以維持下列對這些瀏覽器即將推出的版本的支援等級。

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

1. Firefox延伸支援版本在mozilla.org [上進一步瞭解此資訊](https://www.mozilla.org/en-US/firefox/organizations/faq/)
1. 支援Apple iPad

### 網站支援的瀏覽器 {#supported-browsers-for-websites}

一般而言，AEM Sites提供的網站瀏覽器支援取決於AEM頁面範本的實作、設計和元件輸出，因此可由實作這些部分的一方控制。

### WebDAV客戶端 {#webdav-clients}

**Microsoft Windows 7+**

若要成功連線至未使用SSL保護的AEM例項，Windows中必須啟用透過不安全網路的基本驗證。 這要求在WebClient的Windows註冊表中進行更改：

1. 找到註冊表子項：

   * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WebClient\Parameters

1. 使用值2或更多的值，將BasicAuthLevel註冊表項添加到此子鍵。

請參 [閱Microsoft支援KB 841215](https://support.microsoft.com/default.aspx/kb/841215)。

要提高Windows下WebDav客戶端的響應性——請參 [閱Microsoft支援KB 2445570](https://support.microsoft.com/kb/2445570)

## 其他平台說明 {#additional-platform-notes}

本節提供有關執行Adobe Experience Manager及其附加元件的特殊注意事項和詳細資訊。

### IPv4和IPv6 {#ipv-and-ipv}

Adobe Experience Manager(Instance, Dispatcher)的所有元素都可安裝在IPv4和IPv6網路中。

操作是無縫的，因為無需特殊配置。 如有需要，您只需使用適合您網路類型的格式來指定IP位址。

這表示當需要指定IP位址時，您可以（視需要）從以下位置選擇：

* IPv6地址

   for example `https://[ab12::34c5:6d7:8e90:1234]:4502`

* IPv4地址

   for example `https://123.1.1.4:4502`

* 伺服器名稱

   for example, `https://www.yourserver.com:4502`

* 對於IPv4和 `localhost` IPv6網路安裝，將解釋預設情況

   for example, `http://localhost:4502`

### AEM Dynamic Media附加元件的需求 {#requirements-for-aem-dynamic-media-add-on}

AEM Dynamic Media預設為停用。 請參閱 [啟用動態媒體](/help/assets/config-dynamic.md#enabling-dynamic-media)。

啟用動態媒體後，將適用下列其他系統需求：
>[!NOTE]
>
>下列系統需求僅 **_適用於_** 「動態媒體——混合」模式；動態媒體——混合模式具有內嵌的影像伺服器，僅在特定作業系統上取得認證。
>
>對於執行Dynamic Media - Scene7模式(即 **dynamicmedia_scene7** runmode)的Dynamic Media客戶，並無其他系統需求；只有與AEM相同的系統需求。 動態媒體- Scene7模式架構使用雲端影像服務，而非內嵌於AEM中的服務。

#### 硬體 {#hardware}

下列硬體需求適用於Linux和Windows作業系統：

* 至少具有4個內核的Intel Xeon或AMD Opteron CPU
* 最低16GB的記憶體

#### Linux {#linux}

在Linux上使用動態媒體需要下列必要條件：

* RedHat Enterprise 7或CentOS 7及更新版本及最新的修補程式
* 64位元作業系統
* 已停用交換（建議）
* SELinux已停用（請參閱以下附註）

>[!NOTE]
>
>如果地區設定為LC_CTYPE不等於en_US.UTF-8，則會使動態媒體無法運作。 要查看其值是什麼，請在命令提示符下鍵入&quot;locale&quot;。 如果未設定為該值，則在運行AEM之前，通過鍵入&quot;export LC_CTYPE=&quot;將LC_CTYPE環境變數設定為空字串。

>[!NOTE]
>
>**禁用SELinux:** 開啟SELinux時，影像伺服無法運作。 預設會啟用此選項。 要解決此問題，請編輯 **/etc/selinux/config** 檔案，並將SELinux值從：
>
>`SELINUX=enforcing` 至  `SELINUX=disabled`

>[!NOTE]
>
>**NUMA架構：** 具有AMD64和英特爾EM64T處理器的系統通常配置為非統一記憶體體系結構(NUMA)平台，這意味著內核在啟動時構建多個記憶體節點，而不是構建單個記憶體節點。
>
>該多節點結構可導致在其它節點耗盡之前在一個或多個節點上耗盡儲存器。 當記憶體耗盡時，內核可以決定中止進程（例如，映像伺服器或平台伺服器），即使有可用記憶體。
>
>因此，Adobe建議您，如果您運行的系統使用 **numa=off** boot選項關閉NUMA，以避免內核將這些進程終止。

>[!NOTE]
>
>**伺服器的主機名必須可解析：** 請確定伺服器的主機名可解析為IP地址。 如果不能，請將完全限定的主機名和IP地址添加到 **/etc/hosts**:
>
>`<ip address> <fully qualified hostname>`

#### Windows {#windows}

* Microsoft Windows Server 2016
* 交換空間至少等於物理記憶體(RAM)的兩倍

若要在Windows上使用動態媒體，必須安裝Microsoft Visual Studio 2010、2013和2015 x64和x86可轉散發套件。

x64

* Microsoft Visual Studio 2010的可再次分發版位於 [https://www.microsoft.com/en-us/download/details.aspx?id=13523](https://www.microsoft.com/en-us/download/details.aspx?id=13523)
* Microsoft Visual Studio 2013可重新分發，網址為 [https://www.microsoft.com/en-us/download/details.aspx?id=40784](https://www.microsoft.com/en-us/download/details.aspx?id=40784)
* Microsoft Visual Studio 2015可重新分發，網址為 [https://www.microsoft.com/en-us/download/details.aspx?id=48145](https://www.microsoft.com/en-us/download/details.aspx?id=48145)

x86

* Microsoft Visual Studio 2010的可再次分發版位於 [https://www.microsoft.com/en-in/download/details.aspx?id=5555](https://www.microsoft.com/en-in/download/details.aspx?id=5555)
* Microsoft Visual Studio 2013可重新分發，網址為 [https://www.microsoft.com/en-in/download/details.aspx?id=40769](https://www.microsoft.com/en-in/download/details.aspx?id=40769)
* Microsoft Visual Studio 2015可重新分發，網址為 [https://www.microsoft.com/en-us/download/details.aspx?id=52685](https://www.microsoft.com/en-us/download/details.aspx?id=52685)

#### MacOS {#macos}

* 10.9.x及更新版本
* 僅支援試用與示範用途

### AEM Forms PDF Generator的需求 {#requirements-for-aem-forms-pdf-generator}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>產品</strong></p> </th> 
   <th><p><strong>支援的格式，可轉換為PDF</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html">Acrobat 2017經典曲目</a></p> </td> 
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
   <td>WP, WPD<br /> </td> 
  </tr> 
  <tr> 
   <td>OpenOffice 4.1.2</td> 
   <td>ODT、ODP、ODS、ODG、ODF、SXW、SXI、SXC、SXD、XLS、DOC、DOCX、PPT、PPTX、影像格式(BMP、GIF、JPEG、JPG、TIF、TIF、 PNG、 PNG)、JPF、JPX、JP2、J2K、J2C、JPC)、HTML、HTM、RTF和TXT</td> 
  </tr> 
  <tr> 
   <td><p>OpenOffice 3.4</p> </td> 
   <td><p>ODT、ODP、ODS、ODG、ODF、SXW、SXI、SXC、SXD、XLS、DOC、DOCX、PPT、PPTX、影像格式(BMP、GIF、JPEG、JPG、TIF、TIF、 PNG、 PNG)、JPF、JPX、JP2、J2K、J2C、JPC)、HTML、HTM、RTF和TXT</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>PDF產生器僅支援英文、法文、德文和日文版支援的作業系統和應用程式。
>
>此外：
>
>* PDF Generator需要 [Acrobat 2017傳統音軌17.011.30078版或更新版本](https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html) ，才能執行轉換。
>* AEM Forms僅支援32位元版本的支援軟體。
>* OCR PDF（可搜尋的PDF）、最佳化PDF和匯出PDF功能僅在Microsoft Windows上受支援。
>* AIX上已停用HTML2PDF服務。
>* OpenOffice專用的PDF產生器轉換僅在Windows、Linux和Solaris上受支援。
>* OCR PDF、最佳化PDF和匯出PDF功能僅在Windows上受支援。
>* AEM Forms隨附Acrobat版本，以啟用PDF Generator功能。 在AEM Forms授權期間，僅能透過AEM Forms以程式設計方式存取搭售版本，以便與AEM Forms PDF Generator搭配使用。 如需詳細資訊，請參閱AEM Forms產品說明，如您的部署([On-Premise](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html) 或 [Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html))」

>



### AEM Assets XMP中繼資料回寫的需求 {#requirements-for-aem-assets-xmp-metadata-write-back}

支援XMP回寫功能，並啟用下列平台和檔案格式：

**作業系統**

* Linux（32位元，需要64位元系統上的32位元應用程式支援）。 如需安裝32位元用戶端程式庫的步驟，請參 [閱如何在64位元RedHat Linux上啟用XMP擷取和回寫](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html)。

* Windows Server
* Oracle Solaris
* Mac OS X（64位元）

**檔案格式**

* JPEG
* PNG
* TIFF
* PDF
* INDD
* AI
* EPS

### AEM Screens Player的需求 {#requirements-for-aem-screens-player}

AEM Screens Player 3.3.x版支援下列作業系統：

* Microsoft Windows 10 Enterprise LTSB
* Google Chome OS 62+
* Google Android 5.1.1（含更新的Android系統WebView 52+版）
* Apple iOS 10.3+
* Apple macOS 10.12+

---
title: 技術需求
seo-title: Technical Requirements
description: AEM支援的用戶端和伺服器平台清單。
seo-description: A list of the supported client and server platforms for AEM.
uuid: d5bdcd41-3585-41f7-860d-8068a2931a72
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: platform
discoiquuid: 4d3c4650-3e2a-43b1-ad2d-8d0ae2254ca9
exl-id: 21c10b39-ca37-4085-86f8-063c30a180ed
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3294'
ht-degree: 1%

---

# 技術需求{#technical-requirements}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Adobe支援平台上的Adobe Experience Manager(AEM)，如本檔案的下列資訊所詳述。

若有任何與平台本身特別相關的問題，請直接聯絡平台廠商。

>[!NOTE]
>
>視您安裝AEM的平台而定，使用者管理的需求可能會有不同的集合。

## 必備條件 {#prerequisites}

安裝Adobe Experience Manager的最低需求：

* 已安裝Java平台、標準版JDK或其他支援的 [Java虛擬機](#java-virtual-machines)
* Experience Manager快速入門檔案（獨立JAR或Web應用程式部署WAR）

### 最低規模要求 {#minimum-sizing-requirements}

執行Adobe Experience Manager的最低需求：

* 安裝目錄中有5 GB可用磁碟空間
* 2 GB記憶體

>[!NOTE]
>
>* 數位資產使用案例需要更多基本記憶體。 請參閱 [部署和維護](/help/sites-deploying/deploy.md#default-local-install) 以取得詳細資訊。
>* [AEM Forms附加元件套件](/help/forms/using/installing-configuring-aem-forms-osgi.md) 需要15 GB的臨時空間。
>


請參閱 [硬體調整指南](/help/managing/hardware-sizing-guidelines.md) 以取得更多資訊。

### 支援層級 {#support-levels}

本檔案列出Adobe Experience Manager支援的用戶端和伺服器平台。 Adobe提供數種支援級別，包括建議的配置和其他配置。

### 支援的配置 {#supported-configurations}

Adobe建議進行這些配置，並在標準軟體維護協定中提供完整支援。

<table> 
 <tbody> 
  <tr> 
   <td>支援程度</td> 
   <td>說明<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>答：支援</strong></td> 
   <td>Adobe對此配置提供完全支援和維護。 此設定由Adobe的品質保證程式涵蓋。</td> 
  </tr> 
  <tr> 
   <td><strong>R:受限支援</strong></td> 
   <td>為確保客戶項目成功，Adobe在受限支援計畫中提供全面支援，這要求滿足特定條件。 R級支援需要正式的客戶請求和按Adobe確認。 如需詳細資訊，請連絡Adobe客戶服務。</td> 
  </tr> 
 </tbody> 
</table>

### 不支援的配置 {#unsupported-configurations}

| 支援程度 | 說明 |
|---|---|
| **Z:不支援** | 不支援配置。 Adobe不會針對設定是否有效發表任何陳述，也不支援。 |

## 支援平台 {#supported-platforms}

### Java虛擬機 {#java-virtual-machines}

應用程式需要Java虛擬機才能運行，該虛擬機由Java開發套件(JDK)分發提供。

Adobe Experience Manager可搭配下列版本的Java虛擬機運作：

>[!CAUTION]
>
>建議您追蹤來自Java廠商的安全性佈告欄，以確保生產環境的安全性，並安裝最新的Java更新。

<table> 
 <tbody> 
  <tr> 
   <td>Platform</td> 
   <td>支援程度<br /> </td> 
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
   <td><strong>OracleJava SE 8 JDK - 64位</strong></td> 
   <td>答：支援[3]<br /> </td> 
  </tr> 
  <tr> 
   <td>IBM J9 VM — 版本編號2.9、JRE 1.8.0 [2]</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>IBM J9 VM — 版本編號2.8、JRE 1.8.0 [2]</td> 
   <td>答：支援</td> 
  </tr> 
 </tbody> 
</table>

1. Oracle已改用OracleJava SE產品的「長期支援」(LTS)模型。 Java 9和10是依Oracle的非LTS版本(請參閱 [OracleJava SE支援藍圖](https://www.oracle.com/technetwork/java/eol-135779.html))。 Adobe僅支援LTS版的Java，以在生產環境中執行AEM。

1. 只有WebSphere Application Server才支援IBM JRE。
1. 所有使用OracleJava SE技術的AEM客戶，將直接透過Adobe支援OracleJava SE JDK的支援和發佈，包括公開更新結尾以外的所有LTS版本的維護更新。 請參閱 [OracleJava支援Adobe Experience Manager問答](assets/adobe-oracle-java-license-agreement.pdf) 以取得更多資訊。

### 儲存和持久性 {#storage-persistence}

部署Adobe Experience Manager存放庫有各種選項。 請參閱下列清單，了解支援的技術和儲存選項。

<table> 
 <tbody> 
  <tr> 
   <td><strong>Platform</strong></td> 
   <td><strong>說明</strong></td> 
   <td><strong>支援程度</strong></td> 
  </tr> 
  <tr> 
   <td><strong>具有TAR檔案的檔案系統[1]</strong></td> 
   <td>存放庫</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td><strong>具有資料儲存的檔案系統[1]</strong></td> 
   <td>二進位檔</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>將二進位檔儲存在檔案系統[1]上的TAR檔案中</td> 
   <td>二進位檔</td> 
   <td>Z:不支援生產</td> 
  </tr> 
  <tr> 
   <td>Amazon S3</td> 
   <td>二進位檔</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>Microsoft Azure Blob儲存</td> 
   <td>二進位檔</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.6 [5, 6]</td> 
   <td>存放庫</td> 
   <td>答：受支援且有限制</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.4 [2, 3, 6]</td> 
   <td>存放庫</td> 
   <td>答：受支援且有限制</td> 
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
   <td>存放庫與Forms資料庫</td> 
   <td>R:限制支援(4)</td> 
  </tr> 
  <tr> 
   <td>Oracle資料庫12c(12.1.x)</td> 
   <td>存放庫與Forms資料庫</td> 
   <td>R:受限支援</td> 
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
   <td>R:限制支援(4)</td> 
  </tr> 
  <tr> 
   <td><strong>Apache Lucene（Quickstart內建）</strong></td> 
   <td>搜尋服務</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>阿帕奇索爾</td> 
   <td>搜尋服務</td> 
   <td>答：支援</td> 
  </tr> 
 </tbody> 
</table>

1. 「檔案系統」包括符合POSIX的塊儲存。 這包括網路儲存技術。 請注意，檔案系統效能可能會有所不同，並影響整體效能。 建議結合網路/遠端檔案系統載入測試AEM。
1. AEM不支援MongoDB共用。
1. 僅支援MongoDB儲存引擎WiredTiger。
1. 不支援AEM Forms。
1. AEM 6.4.2.0 版開始支援 MongoDB Enterprise 3.6。
1. 對MongoDB 3.4的支援已結束(EOL)，而MongoDB 3.6預計於2021年4月30日終止。 請注意，Adobe將僅針對日後AEM產品相關問題提供支援。

>[!NOTE]
>
>請參閱 [部署社群](/help/communities/deploy-communities.md) 以取得AEM Communities功能的其他資訊。

>[!NOTE]
>
>MongoDB是協力廠商軟體，不包含在AEM授權套件中。 如需詳細資訊，請參閱 [MongoDB許可策略](https://www.mongodb.org/about/licensing/) 頁面。
>
>為了使用MongoDB充分利用您的AEM部署，Adobe建議授予MongoDB企業版本許可，以便從專業支援中受益。 請參閱 [建議的部署](/help/sites-deploying/recommended-deploys.md#prerequisites-and-recommendations-when-deploying-aem-with-mongomk) 以取得更多資訊。
>
>該許可證包括一個標準副本集，該集由一個主實例和兩個輔助實例組成，可用於製作或發佈部署。
>
>如果您想要在MongoDB上同時執行製作和發佈，則需要購買兩個不同的授權。
>
>Adobe客戶服務將協助確認與搭配AEM使用MongoDB的相關問題。
>
>如需詳細資訊，請參閱 [適用於Adobe Experience Manager的MongoDB頁](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).

>[!NOTE]
>
>如上所列的支援關係資料庫是第三方軟體，不包含在AEM授權套件中。
>
>為了使用支援的關係資料庫運行AEM 6.4，需要與資料庫供應商單獨簽訂支援合同。 Adobe客戶服務將協助您了解與AEM 6.4使用關係資料庫相關的資格認定問題。
>
>**請注意，AEM 6.4的Level-R中當前支援大多數關係資料庫，這附帶了上面Level-R說明中所述的支援標準和支援計畫。**

### Servlet引擎/應用程式伺服器 {#servlet-engines-application-servers}

Adobe Experience Manager可以作為獨立伺服器（quickstart JAR檔案）運行，也可以作為第三方應用程式伺服器（WAR檔案）中的Web應用程式運行。

所需的Servlet API最低版本為Servlet 3.1，但低於Servlet 4.0。

| Platform | 支援程度 |
|---|---|
| **快速入門內置Servlet引擎(Jetty 9.3)** | 答：支援 |
| OracleWebLogic Server 12.2(12cR2) | 答：支援 |
| IBM WebSphere應用程式伺服器連續交付(LibertyProfile)，帶Web配置檔案7.0和IBM JRE 1.8 | 答：支援 |
| IBM WebSphere Application Server 9.0 | 答：支援 |
| Apache Tomcat 8.5.x | 答：支援 |
| JBoss EAP 7.1.0與JBoss應用程式伺服器 | 答：支援(1) |
| JBoss EAP 7.0.0與JBoss應用程式伺服器 | 答：支援 |

1. 不支援AEM Forms。

### 伺服器作業系統 {#server-operating-systems}

Adobe Experience Manager可與下列伺服器平台搭配使用：

<table> 
 <tbody> 
  <tr> 
   <td><strong>Platform</strong></td> 
   <td><strong>支援程度</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Linux，基於Red Hat分發</strong></td> 
   <td>答：支援(1)</td> 
  </tr> 
  <tr> 
   <td>Linux，以Debian發佈(包括 烏邦圖</td> 
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
   <td>答：支援限制(3,5,7)<br /> R:對新合同的限制支援</td> 
  </tr> 
  <tr> 
   <td>IBM AIX 7.2</td> 
   <td>答：支援限制(2、5、7)<br /> R:對新合同的限制支援</td> 
  </tr> 
 </tbody> 
</table>

1. Linux內核2.6、3.x和4.x包含來自Red Hat發佈的衍生產品，包括Red Hat Enterprise Linux、CentOS、OracleLinux和Amazon Linux。 AEM Forms附加元件功能僅在CentOS 7和Red Hat Enterprise Linux 7上受支援。
1. AEM Assets:請參閱 [支援XMP中繼資料回寫](#requirements-for-aem-assets-xmp-metadata-write-back)
1. AEM Assets:不支援Dynamic Media影像。 Dynamic Media影片受支援。
1. AEM Forms僅在Ubuntu 16.04 LTS上受支援。
1. AEM Assets:不支援 [原始檔案轉換](/help/assets/camera-raw.md)
1. AEM Forms:不支援生產環境
1. AEM Assets:不支援 [增強PDF模擬轉譯器](/help/assets/aem-pdf-rasterizer.md)
1. AEM Forms:不支援

### 虛擬和雲計算環境 {#virtual-cloud-computing-environments}

支援Adobe Experience Manager在雲端運算環境(例如Microsoft Azure和Amazon Web Services(AWS))上的虛擬機中執行，且符合本頁所列的技術需求，且符合Adobe的標準支援條款。

Adobe建議使用Adobe Managed Services在Azure或AWS上部署AEM。 Adobe Managed Services為專家提供在這些雲端運算環境中部署和操作AEM的經驗和技能。 請查看我們的 [Adobe Managed Services的其他檔案](https://www.adobe.com/marketing-cloud/enterprise-content-management/managed-services-cloud-platform.html?aemClk=t).

在將AEM部署在Azure或AWS或任何其他雲計算環境的所有其他情況下，將根據本頁所列的技術規範，從Adobe支援包含到虛擬計算環境。 與在任何這些雲端環境中執行的AEM相關的任何回報問題，都必須可獨立於雲端運算環境專用的任何雲端服務重複，除非本頁所列技術需求(例如Azure Blob儲存或AWS S3)特別支援雲端服務。

如需有關如何在Azure或AWS上部署AEM（在Adobe Managed Services外）的建議，強烈建議您直接與雲端提供者或Adobe合作夥伴合作，支援在您選擇的雲端環境中部署AEM。 選定的雲提供商或合作夥伴將負責架構的規模規格、設計和實施，以滿足您的特定效能、負載、可擴充性和安全性要求。

### Dispatcher平台（Web伺服器） {#dispatcher-platforms-web-servers}

Dispatcher是快取和負載平衡元件。 [下載最新的Dispatcher版本](https://helpx.adobe.com/experience-manager/dispatcher/release-notes.html). Experience Manager6.4需使用Dispatcher 4.3.1版或更新版本。

下列Web伺服器支援與Dispatcher 4.3.1版搭配使用：

| Platform | 支援程度 |
|---|---|
| **Apache httpd 2.4.x** （另請參閱下方的1、2） | 答：支援 |
| Microsoft IIS 10（Internet資訊伺服器） | 答：支援 |
| Microsoft IIS 8.5（Internet資訊伺服器） | 答：支援 |

1. 以Apache httpd原始碼為基礎建置的Web伺服器，其支援級別與其所基於的httpd版本相同。 如果有疑問，請向Adobe要求確認與相應伺服器產品相關的支援級別。 下列案例：

   1. HTTP伺服器是僅使用官方的Apache來源分配建立，或
   1. HTTP伺服器是作為運行該伺服器的作業系統的一部分進行傳送的。 範例：IBM HTTP伺服器，OracleHTTP伺服器

1. Windows作業系統無法使用Apache 2.4.x。

## 支援的客戶端平台 {#supported-client-platforms}

### 製作使用者介面支援的瀏覽器 {#supported-browsers-for-authoring-user-interface}

Adobe Experience Manager使用者介面適用於下列用戶端平台。 所有瀏覽器都會使用預設的外掛程式和附加元件集進行測試。

AEM使用者介面已針對較大螢幕（通常是筆記型電腦和桌上型電腦）和平板電腦外形規格(例如Apple iPad或Microsoft Surface)而最佳化。 不支援電話外形。

>[!NOTE]
>
>**支援發行週期快的瀏覽器：**
>
>Mozilla Firefox、Google Chrome和Microsoft Edge版本每幾個月更新一次。 Adobe承諾為Adobe Experience Manager提供更新，以維持下列這些瀏覽器即將推出的版本所提供的支援層級。

<table> 
 <tbody> 
  <tr> 
   <td><strong>瀏覽器</strong></td> 
   <td><strong>支援UI<br /> </strong></td> 
   <td><strong>支援傳統UI</strong></td> 
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
   <td>Apple Safari 12.x on macOS</td> 
   <td>答：支援</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>Apple Safari 11.x on macOS</td> 
   <td>答：支援</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>Apple Safari 10.x on macOS</td> 
   <td>答：支援</td> 
   <td>答：支援</td> 
  </tr> 
  <tr> 
   <td>Apple Safari on iOS 12.x</td> 
   <td>答：支援[2]</td> 
   <td>Z:不支援</td> 
  </tr> 
  <tr> 
   <td>Apple Safari on iOS 11.x</td> 
   <td>答：支援[2]</td> 
   <td>Z:不支援</td> 
  </tr> 
  <tr> 
   <td>Apple Safari on iOS 10.3</td> 
   <td>答：支援[2]</td> 
   <td>Z:不支援</td> 
  </tr> 
 </tbody> 
</table>

1. Firefox延伸支援版本 [在mozilla.org上了解更多相關資訊](https://www.mozilla.org/en-US/firefox/organizations/faq/)
1. 支援Apple iPad

### 支援的網站瀏覽器 {#supported-browsers-for-websites}

一般而言，AEM Sites轉譯之網站的瀏覽器支援取決於AEM頁面範本、設計和元件輸出的實作，因此可由實作這些部分的一方控制。

### WebDAV客戶端 {#webdav-clients}

**Microsoft Windows 7+**

若要成功將Microsoft Windows 7+連線至未透過SSL保護的AEM執行個體，必須在Windows中啟用不安全網路上的基本驗證。 這要求在WebClient的Windows註冊表中進行更改：

1. 找到註冊表子項：

   * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WebClient\Parameters

1. 使用值2或更多將BasicAuthLevel註冊表項添加到此子項。

請參閱 [Microsoft支援KB 841215](https://support.microsoft.com/default.aspx/kb/841215).

要在Windows下提高WebDav客戶端的響應性，請參閱 [Microsoft支援KB 2445570](https://support.microsoft.com/kb/2445570)

## 其他平台說明 {#additional-platform-notes}

本節提供有關執行Adobe Experience Manager及其附加元件的特殊附註和詳細資訊。

### IPv4和IPv6 {#ipv-and-ipv}

Adobe Experience Manager的所有元素（例項、Dispatcher）都可安裝在IPv4和IPv6網路中。

操作無縫，因為不需要特殊配置。 如有必要，您只需使用適合您網路類型的格式來指定IP位址。

這表示當需要指定IP位址時，您可以（視需要）從下列項目中選取：

* IPv6地址

   例如 `https://[ab12::34c5:6d7:8e90:1234]:4502`

* IPv4地址

   例如 `https://123.1.1.4:4502`

* 伺服器名稱

   例如， `https://www.yourserver.com:4502`

* 預設大小寫為 `localhost` 將解釋為IPv4和IPv6網路安裝

   例如， `http://localhost:4502`

### AEM Dynamic Media附加元件需求 {#requirements-for-aem-dynamic-media-add-on}

AEM Dynamic Media預設為停用。 請參閱 [啟用Dynamic Media](/help/assets/config-dynamic.md#enabling-dynamic-media).

啟用Dynamic Media後，將適用下列額外系統需求：
>[!NOTE]
>
>適用以下系統要求 **_僅限_** 如果您使用Dynamic Media — 混合模式；Dynamic Media — 混合模式具有嵌入式映像伺服器，該伺服器僅在某些作業系統上通過認證。
>
>執行Dynamic Media - Scene7模式的Dynamic Media客戶(即 **dynamicmedia_scene7** runmode)，則無其他系統需求；只有與AEM相同的系統需求。 Dynamic Media - Scene7模式架構使用雲端型影像服務，而非AEM中內嵌的服務。

#### 硬體 {#hardware}

以下硬體要求適用於Linux和Windows作業系統：

* 至少4個內核的英特爾至強或AMD皓龍CPU
* 最少16GB記憶體

#### Linux {#linux}

在Linux上使用Dynamic Media需要下列必要條件：

* RedHat Enterprise 7或CentOS 7及更新版本，以及最新的修補程式
* 64位作業系統
* 禁用交換（建議）
* SELinux已禁用（請參閱以下備注）

>[!NOTE]
>
>如果設定地區設定為LC_CTYPE不等於en_US.UTF-8，則會阻止動態媒體運作。 在命令提示符下查看其值是什麼。 如果未將其設定為該值，請在運行AEM之前鍵入&quot;export LC_CTYPE=&quot;，將LC_CTYPE環境變數設定為空字串。

>[!NOTE]
>
>**禁用SELinux:** 開啟SELinux時影像伺服無法運作。 預設會啟用此選項。 若要解決此問題，請編輯 **/etc/selinux/config** 檔案，並將SELinux值從：
>
>`SELINUX=enforcing` 至  `SELINUX=disabled`

>[!NOTE]
>
>**NUMA架構：** 具有AMD64和英特爾EM64T處理器的系統通常配置為非統一記憶體架構(NUMA)平台，這意味著內核在啟動時構建多個記憶體節點，而不是構建單個記憶體節點。
>
>該多節點結構可導致在一個或多個節點耗盡之前對其它節點耗盡記憶體。 當記憶體耗盡時，內核可以決定終止進程（例如，映像伺服器或平台伺服器），即使記憶體可用。
>
>因此，Adobe建議，如果您運行的系統使用 **numa=off** 引導選項，以避免內核導致這些進程死亡。

>[!NOTE]
>
>**伺服器的主機名必須可解析：** 請確定伺服器的主機名稱可解析為IP位址。 如果無法，請將完全限定的主機名和IP地址添加到 **/etc/hosts**:
>
>`<ip address> <fully qualified hostname>`

#### Windows {#windows}

* Microsoft Windows Server 2016
* 交換空間至少等於物理記憶體(RAM)量的兩倍

若要在Windows上使用Dynamic Media，必須安裝適用於x64和x86的Microsoft Visual Studio 2010、2013和2015可轉散發套件。

x64

* Microsoft Visual Studio 2010可重新分發，位於 [https://www.microsoft.com/en-us/download/details.aspx?id=13523](https://www.microsoft.com/en-us/download/details.aspx?id=13523)
* Microsoft Visual Studio 2013可重新分發，位於 [https://www.microsoft.com/en-us/download/details.aspx?id=40784](https://www.microsoft.com/en-us/download/details.aspx?id=40784)
* Microsoft Visual Studio 2015可重新分發，位於 [https://www.microsoft.com/en-us/download/details.aspx?id=48145](https://www.microsoft.com/en-us/download/details.aspx?id=48145)

x86

* Microsoft Visual Studio 2010可重新分發，位於 [https://www.microsoft.com/en-in/download/details.aspx?id=5555](https://www.microsoft.com/en-in/download/details.aspx?id=5555)
* Microsoft Visual Studio 2013可重新分發，位於 [https://www.microsoft.com/en-in/download/details.aspx?id=40769](https://www.microsoft.com/en-in/download/details.aspx?id=40769)
* Microsoft Visual Studio 2015可重新分發，位於 [https://www.microsoft.com/en-us/download/details.aspx?id=52685](https://www.microsoft.com/en-us/download/details.aspx?id=52685)

#### macOS {#macos}

* 10.9.x及更新版本
* 僅支援試用和示範用途

### AEM FormsPDF產生器需求 {#requirements-for-aem-forms-pdf-generator}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>產品</strong></p> </th> 
   <th><p><strong>支援的格式，可轉換為PDF</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html">Acrobat 2017傳統賽道</a></p> </td> 
   <td><p>XPS，影像格式(BMP,GIF,JPEG,JPG, TIF,TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC),HTML, HTM, DWG, DXF，和DWF</p> </td> 
  </tr> 
  <tr> 
   <td>Microsoft® 2016工程</td> 
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
   <td>ODT、ODP、ODS、ODG、ODF、SXW、SXI、SXC、XLS、XLSX、DOC、DOCX、PPT、PPTX、影像格式(BMP、GIF、JPEG、JPG、TIF、TIFF、PNG、JPF、JP2、J2K、J2C、JPC、HTM、TF和RTF)</td> 
  </tr> 
  <tr> 
   <td><p>OpenOffice 3.4</p> </td> 
   <td><p>ODT、ODP、ODS、ODG、ODF、SXW、SXI、SXC、XLS、XLSX、DOC、DOCX、PPT、PPTX、影像格式(BMP、GIF、JPEG、JPG、TIF、TIFF、PNG、JPF、JP2、J2K、J2C、JPC、HTM、TF和RTF)</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>PDF產生器僅支援支援的作業系統和應用程式的英文、法文、德文和日文版本。
>
>此外：
>
>* PDF產生器需要 [Acrobat 2017 classic track 17.011.30078或更新版本](https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html) 來執行轉換。
>* AEM Forms僅支援32位元版本的支援軟體。
>* OCRPDF(可搜尋PDF)、Optimize PDF和Export PDF功能僅在Microsoft Windows上受支援。
>* AIX上不建議使用HTML2PDF服務。
>* 只有Windows、Linux和Solaris支援OpenOffice的PDF生成器轉換。
>* OCRPDF、Optimize PDF和Export PDF功能僅在Windows上受支援。
>* Acrobat版本與AEM Forms搭配，以啟用PDF產生器功能。 套件版本在AEM Forms授權期間，僅能透過AEM Forms以程式設計方式存取，以便與AEM FormsPDF產生器搭配使用。 如需詳細資訊，請參閱根據您的部署的AEM Forms產品說明([內部部署](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html) 或 [Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html))&quot;
>


### AEM Forms Designer的需求 {#requirements-for-aem-forms-designer}

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

### AEM Assets XMP中繼資料回寫的需求 {#requirements-for-aem-assets-xmp-metadata-write-back}

下列平台和檔案格式支援並啟用XMP回寫：

**作業系統**

* Linux（32位，需要64位系統上的32位應用程式支援）。 有關安裝32位客戶端庫的步驟，請參見 [如何在64位元RedHat Linux上啟用XMP擷取和回寫](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).

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

### AEM Screens Player需求 {#requirements-for-aem-screens-player}

AEM Screens Player 3.3.x版支援下列作業系統：

* Microsoft Windows 10企業版LTSB
* Google Chome OS 62+
* Google Android 5.1.1，含更新的Android系統WebView 52+版
* Apple iOS 10.3+
* Apple macOS 10.12+

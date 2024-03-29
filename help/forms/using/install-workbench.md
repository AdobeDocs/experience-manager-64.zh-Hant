---
title: 安裝工作台
seo-title: Install workbench
description: 安裝工作台。
uuid: null
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: null
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2779'
ht-degree: 0%

---


# 安裝工作台 {#install-workbench}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

本檔案提供安裝和設定工作台的說明。 安裝程式還安裝Designer。

## 關於 {#about}

本檔案適用於負責安裝、設定、管理或部署Workbench的管理員或開發人員。
此外，還包含配置系統以支援升級Adobe® AEM forms® Enterprise Suite(ES)更新1(8.2.x)和Adobe® AEM forms® Enterprise Suite 2(ES2)流程所需的資訊。
提供的資訊基於以下假設：閱讀本文檔的任何人都熟悉Microsoft® Windows®作業系統。

## 其他資訊 {#additional-information}

此表格中的資源可協助您進一步了解及開始使用AEM Forms。
<table> 
 <tbody> 
  <tr> 
   <td><p><strong>關於後述資訊：</strong></p> </td> 
   <td><p><strong>請參閱</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Workbench的程式資訊</p> </td> 
   <td><p><a href="http://www.adobe.com/go/learn_aemforms_workbench_61">Workbench說明</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>關於AEM Forms及其如何與其他Adobe產品整合的一般資訊</p> </td> 
   <td><p><a href="http://adobe.com/go/learn_aemforms_introduction_65">AEM Forms概述</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>建立AEM Forms應用程式並在工作區中測試的教學課程</p> </td> 
   <td><p><a href="http://adobe.com/go/learn_aemforms_firstapp_ds_65">建立您的第一個AEM Forms應用程式</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>AEM Forms提供的所有檔案</p> </td> 
   <td><p><a href="http://adobe.com/go/learn_aemforms_introduction_65">AEM Forms檔案</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>其他與AEM Forms整合的服務和產品</p> </td> 
   <td><p><a href="http://www.adobe.com/tw/">www.adobe.com</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>有關此產品版本的補丁程式更新、技術說明和其他資訊</p> </td> 
   <td><p><a href="https://www.adobe.com/tw/account/sign-in.supportportal.html">聯絡Adobe企業支援</a><br /> <br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>AEM Forms不再使用Flex Workspace。 此功能適用於AEM Forms版本。

## 安裝之前 {#before-you-install}

### Workbench安裝概觀 {#workbench-installation-overview}

Workbench是整合式開發環境(IDE)，開發人員和表單作者可使用此環境建立自動化的業務流程和表單。 它還用於管理流程和表單使用的資源和服務。

下圖說明Workbench安裝，包括：
* 使用Workbench進行流程設計
* 使用設計工具進行表單設計

>[!NOTE]
>
>AEM Forms伺服器需要個別的安裝程式。 如需詳細資訊，請參閱JEE上的AEM Forms安裝檔案。

## 系統先決條件 {#system-prerequisites}

本節概述硬體和軟體需求以及支援的平台。

### 最低硬體和軟體需求 {#minimum-hardware-software-requirements}

**Workbench**
建議最低要求如下：要安裝的磁碟空間：
* 僅適用於Workbench的680 MB。
* 在單個驅動器上安裝2.15 GB，以完整安裝Workbench、Designer和示例元件。
* 400 MB用於臨時安裝目錄 — 用戶\temp目錄為200 MB,Windows臨時目錄為200 MB。

>[!NOTE]
>
>如果所有這些位置都駐留在單個驅動器上，則安裝期間必須有1.5 GB的可用空間。 安裝完成後，將刪除複製到臨時目錄的檔案。

* 硬體需求：英特爾®奔騰® 4或AMD等效處理器，1 GHz。
* 下載並安裝最新版Adobe AIR(從 <a href="http://www.adobe.com/tw/">www.adobe.com</a>)與Workbench整合之社群說明用戶端所需。
* Java™ Runtime Environment(JRE)6.0更新22或更新至6.0 *10版新增*.
* 16位顏色或更高，最低1024 X 768像素或更高的監視器解析度。
* TCP/IPv4或TCP/IPv6與AEM Forms伺服器的網路連接。
* 安裝Visual C++ Redistributable運行時包2012 32位。
* 安裝Visual C++ Redistributable運行時包2013 32位。

>[!NOTE]
>
>如果您的電腦上已安裝Adobe® Acrobat® X，請務必先解除安裝，再安裝Workbench。 安裝Workbench後，您可以重新安裝Acrobat。

>[!NOTE]
>
>您必須擁有管理權限才能安裝Workbench。 如果您使用非管理員帳戶進行安裝，安裝程式會提示您輸入適當帳戶的憑證。

### 支援平台 {#supported-platforms}

請參閱Workbench支援平台的完整清單，網址為 [AEM Forms支援平台](http://adobe.com/go/learn_aemforms_supportedplatforms_65).

## 設計工具安裝考量事項 {#designer-installation-considerations}

依預設，Workbench安裝包含對應的僅限英文版Designer。 如果Workbench安裝應用程式在您的電腦上檢測到現有版本的Designer，則安裝可能會終止，並且您必須先刪除當前版本的Designer，然後才能繼續。
下表列出了安裝Workbench時您可能遇到的可能Designer安裝方案以及您必須執行的任何操作的完整清單。

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>當前安裝的Designer版本</strong></p> </td> 
   <td><p><strong>必要動作</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Acrobat Pro或Acrobat Pro Extended（包括Designer）</p> </td> 
   <td><p>無. Workbench安裝會在您電腦上偵測隨Acrobat Pro或Acrobat Pro Extended安裝的Designer例項。
不同版本的Designer可以共存於同一系統，例如Designer 8.2.x和9.0.x。不需要卸載隨Acrobat 10 Pro或Acrobat 10 Pro Extended一起安裝的Designer版本。
<br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>設計人員（獨立）</p> </td> 
   <td><p>無. Workbench隨附的Designer版本僅提供英文版。 Workbench安裝程式不會重新安裝新版本的Designer。 將會修補隨Workbench安裝程式提供的更新版本。 這也可讓您在Workbench中使用本地化版本的Designer。<br /> <br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

### 卸載Designer（獨立） {#uninstall-designer-standalone}

1. 前往 **「控制面板」 > 「程式」 > 「程式和功能」**
1. 在當前安裝的程式清單中，選擇 **Adobe設計工具**.
1. 按一下 **解除安裝** 然後按一下 **是**.

### 在Windows 10上卸載Designer（獨立） {#uninstall-designer-standalone-windows10}

1. 前往 **「控制面板」 > 「程式」 > 「程式和功能」**
1. 在當前安裝的程式清單中，選擇 **Adobe設計工具**.
1. 按一下 **解除安裝** 然後按一下 **是**.

### 若要解除安裝Acrobat Pro或Acrobat Pro Extended隨附的Designer {#uninstall-designer-included-with-acrobatpro-or-acrobatextended}

1. 前往 **「控制面板」 > 「程式」 > 「程式和功能」**
1. 在當前安裝的程式清單中，選擇 **Adobe Acrobat Pro** 或 **Adobe Acrobat Pro Extended**.
1. 按一下 **變更** 然後按一下 **下一個**.
1. 選擇 **修改** 然後按一下 **下一個**.
1. 選擇 **Adobe設計工具**，選取 **此功能將無法使用**，然後按一下 **下一個**
1. 按一下 **更新** 然後按一下 **完成**

### 若要在Windows 10上解除安裝Acrobat Pro或Acrobat Pro Extended隨附的Designer {#uninstall-designer-included-with-acrobatpro-or-acrobatextended-windows10}

1. 前往 **「控制面板」 > 「程式」 > 「程式和功能」**
1. 在當前安裝的程式清單中，選擇 **Adobe Acrobat Pro** 或 **Adobe Acrobat Pro Extended**.
1. 按一下 **變更** 然後按一下 **下一個**.
1. 選擇 **修改** 然後按一下 **下一個**.
1. 選擇 **Adobe設計工具**，選取 **此功能將無法使用**，然後按一下 **下一個**
1. 按一下 **更新** 然後按一下 **完成**

## 安裝Workbench {#installing-workbench}

本章說明如何安裝Workbench。

### 安裝和執行Workbench {#installing-and-running-workbench}

安裝Workbench之前，您必須確定您的環境包含執行Workbench所需的軟體和硬體(請參閱區段： **安裝之前**)。

**要安裝並運行Workbench，請執行以下操作：**

1. 執行下列任務之一：
   * 導覽至安裝媒體上的\workbench目錄，然後按兩下run_windows_installer.bat檔案。
   * 將Workbench下載並解壓縮至您的檔案系統。 下載後，導航到\workbench目錄，然後按兩下run_windows_installer.bat檔案。

   >[!IMPORTANT]
   >
   >Workbench安裝程式僅從DVD或本機磁碟執行。 無法從遠程站點運行。

   >[!NOTE]
   >
   >如果遇到「無法建立Java虛擬機」錯誤，請建立名為_JAVA_OPTIONS的環境變數（值為 — Xmx512M），然後運行安裝程式。

1. 在「簡介」畫面上，按一下「下一步」 。
1. 閱讀產品許可協定，選擇「我接受許可協定的條款」，然後按一下「下一步」。
1. （可選）如果需要此工具來建立和修改表單，請選擇「安裝Adobe設計器」。

   >[!NOTE]
   >
   >若要繼續使用與Acrobat 10一起安裝的Designer，請將此選項保留為取消選取。

1. 接受列出的預設目錄，或按一下「選擇」，導覽至您要安裝Workbench的目錄，然後按一下「下一步」。

   >[!NOTE]
   >
   >安裝目錄路徑不應包含#（井號）和$（井號）字元。

1. 查看預安裝摘要，然後按一下「安裝」。 安裝程式顯示安裝進度。
1. 查看安裝摘要。 選取「啟動AEM Forms Workbench」以啟動Workbench，然後按一下「下一步」。
1. 檢閱發行說明，然後按一下完成。
1. 您的電腦現在安裝了下列項目：
   * **Workbench**:若要從「開始」功能表執行Workbench，請選取「所有程式> AEM Forms > Workbench」（如果您選擇將快捷方式資料夾儲存在此處）。 如需詳細資訊，請參閱使用Workbench檔案。
   * **設計工具**:您可以從Workbench記憶體取「設計工具」。 如需詳細資訊，請參閱設計工具說明中的快速入門主題。
   * **Workbench外掛程式**:請依照第6頁「3.3安裝Workbench Eclipse功能」中的指示操作。
   * **AEM Forms SDK**:如需使用SDK的詳細資訊，請參閱 <a href="http://www.adobe.com/go/learn_lc_programming_10">使用AEM Forms進行程式設計</a>.

## 升級程式 {#upgrading-processes}

AEM Forms更新1和LiveCycleES2程式可透過升級精靈升級至AEM Forms應用程式。 如需詳細資訊，請參閱Workbench說明中的升級舊成品檔案。

### 安裝Workbench Eclipse功能 {#installing-workbench-eclipse-feature}

您可以選擇將Workbench功能新增至Eclipse。 在安裝Workbench後，即可新增Workbench。 例如，對於JBoss，下列位置包含檔案：

* Workbench_DVD/additional/eclipse從以下位置下載及安裝Eclipse 3.6: <a href="https://www.eclipse.org/downloads/">www.eclipse.org/downloads</a>.

### 為Workbench設定Eclipse更新功能 {#configuring-eclipse-update-feature-for-workbench}

Workbench支援更新功能，以確保您使用的是最新的Eclipse版本。 不過，您必須確保每次下載都包含某些其他模組：

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Eclipse版本</strong></p> </td> 
   <td><p><strong>Workbench必要模組</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Eclipse 3.6.x</p> </td> 
   <td><p>

* 圖形編輯框架GEF [org.eclipse.gef.feature.group]:「圖形建模框架SDK」中包含此項 [org.eclipse.gmf.sdk.feature.group]

* WST XML核心 [org.eclipse.wst.xml_core.feature.feature.group]:這包含在「Eclipse XML編輯器和工具」中 [org.eclipse.wst.xml_ui.feature.feature.group]

* 外掛程式&#39;org.apache.commons.lang_2.3.0&#39; [n/a]:這包含在「Mylyn任務清單（必要）」中 [org.eclipse.mylyn_feature.feature.group]

   </p> </td> 
  </tbody>
  </table>

**若要安裝Workbench功能並部署至Eclipse**:
1. 啟動Eclipse。
1. 選擇「幫助」>「安裝新軟體」，按一下「添加」以開啟「添加儲存庫」對話框。
1. 在「新增存放庫」對話方塊中，按一下「本機」，並瀏覽至Workbench安裝程式儲存外掛程式ZIP檔案的目錄，選取workbench-updatesite.zip，然後按一下「開啟」。
1. 請依照後續畫面上的指示，將Workbench功能部署至Eclipse。

   >[!NOTE]
   >
   >忽略「警告：您即將安裝未簽名的功能，」然後按一下「安裝」繼續。

   >[!NOTE]
   >
   >適用於Flash Builder的AdobeAEM Forms Discovery外掛程式可讓您快速建立AdobeFlex和AIR應用程式，這些應用程式會透過其遠端端點叫用屬於AEM Forms的服務。 有關如何安裝和更新外掛程式的資訊，請訪問Adobe網站： **需要連結**.

### 配置並記錄到伺服器 {#configuring-and-logging-server}

若要使用Workbench，您必須有執行中的AEM Forms例項，通常是在個別電腦上。 您必須有使用者名稱和密碼才能登入AEM Forms，以及伺服器位置的詳細資訊。

>[!NOTE]
>
>如果您將AEM Forms配置為使用EMC Documentum或IBM FileNet儲存庫提供程式，並且要登錄到儲存庫，而不是在AEM Forms管理控制台中配置為預設的儲存庫，請提供用戶名為username@Repository。

### 配置超時設定 {#configuring-timeout-settings}

依預設，無論活動或閒置，Workbench都會在兩小時後逾時。 要編輯超時設定，請參閱管理控制台幫助中的「配置用戶管理>配置高級系統屬性」。

### 設定Workbench以透過HTTPS連線 {#configuring-workbench-to-connect-over-HTTPS}

若要透過HTTPS將Workbench連線至AEM Forms伺服器，您必須確定核發公開金鑰的憑證授權單位(CA)會被Workbench認可。 如果未將憑證辨識為來自信任的來源，您必須更新位於 [Workbench_HOME]/workbench/jre/lib/security目錄。

>[!NOTE]
>
>[Workbench_HOME] 代表您安裝Workbench的目錄。 預設位置為C:\Program Files (x86)\Adobe Experience Manager forms Workbench。

請使用憑證中指定的名稱來連線至HTTPS。 此名稱通常是完全限定的主機名稱。

**更新快取檔案**:
1. 確保您有安全套接字層(SSL)證書的副本。 請聯絡設定SSL伺服器的管理員，或使用網頁瀏覽器匯出憑證。

   >[!NOTE]
   >
   >若要匯出憑證，請開啟Web瀏覽器並登入管理主控台，在瀏覽器中安裝憑證，然後將憑證從瀏覽器匯出至暫時儲存位置(或直接匯出至 [Workbench_HOME]/workbench/jre/lib/security directory)。

1. 將憑證複製到 [Workbench_HOME]/workbench/jre/lib/security目錄。

1. 開啟命令提示窗口，導航到 [Workbench_HOME]/workbench/jre/bin，然後鍵入以下命令：
   `keytool -import -storepass changeit -file [Workbench_HOME]\workbench\jre\lib\security\ssl_cert_for_certname.cer -keystore [Workbench_HOME]\workbench\jre\lib\security\cacerts -alias example`
其中：
   * changeit是cacerts密鑰庫的預設密碼。
   * certname是您在步驟1中選取的憑證。
   * 您為憑證選擇的別名就是範例。 此值可以變更

1. 提示您信任證書時，鍵入Yes並按一下Enter鍵。 鍵工具會繼續將快取檔案匯入至 [Workbench_HOME]/workbench/jre/lib/security目錄。

1. 關閉並重新啟動Workbench以套用變更。

### 配置動態生成模板的快取設定 {#configuring-cache-settings-for-dynamically-generated-templates}

如果您的應用程式透過自動更新XFA內容而即時產生唯一範本，則應考慮快取操作的下列方面。 實際上，每個交易都使用新的唯一範本。

當表單產生器或輸出器針對特定表單範本搜尋或更新快取中的項目時，會使用數個索引鍵值來找出要存取的特定快取項目。

* **範本檔案名稱**:用作快取表單主要唯一標識符的模板的位置和檔案名。
* **時間戳記**:範本檔案包含用於決定表單上次更新時間的時間戳記。
* **範本UUID**:設計工具會在每個範本中插入表單及其版本的唯一識別碼(UUID)。 每次更新表單時，內嵌的UUID都會更新。 例如，XDP範本可能會顯示下列內容：

   `<?xml version="1.0" encoding="UTF-8"?>`
   `<?xfa generator="AdobeAEM formsDesignerES_V8.2" APIVersion="2.6.7185.0"?><xdp:xdp xmlns:xdp=http://ns.adobe.com/xdp/ timeStamp="2008-07-29T21:22:12Z" uuid="823e538f-ff6c-4961-b759-f7626978a223"><template xmlns="http://www.xfa.org/schema/xfa-template/2.6/">`

* **呈現選項**:在呈現的表單快取中，對於每組唯一呈現選項分別儲存快取內容。


Forms服務會參考檔案名稱或存放庫位置，或參考記憶體中XML物件的值，接收範本。
* **參考傳遞的範本**:使用內容根和表單名稱。 如果使用此方法在每個請求中傳遞了檔案名不同的唯一模板，則磁碟快取將不斷增長，並且永遠不會重複使用。 為避免發生此情況，應以相同檔案名稱傳遞唯一範本，以確保所有要求都更新相同的快取。
* **按值傳遞的模板**:使用使用theinDataDoc參數傳遞的模板位元組以及資料。 如果使用此方法傳遞了具有不同UUID的唯一模板，則磁碟快取將不斷增長，並且永遠不會重複使用。 為避免此情況，應從所有範本中移除UUID屬性，以確保不會為範本建立快取。 或者，傳遞相同的非空UUID可以建立快取物件，但可確保每個請求都更新相同的快取。

為避免快取無休止地成長，請使用新AEM Forms API來轉譯動態產生的範本（即renderHTMLForm2和renderPDFForm2），請考量下列因素。

使用新API時，範本會以檔案物件的形式傳遞，這會根據是否鈍化在Forms服務中處理。

對於以UUID和內容根作為快取鍵的鈍化文檔，請考慮以下方面：
* 沒有UUID的鈍化輸入範本不會建立快取。
* 如果傳遞了多個具有相同UUID和內容根的鈍化輸入模板，則覆蓋相同的快取。

對於檔案名和內容根作為快取鍵的未鈍化文檔，請考慮以下方面：
* 對於未鈍化的輸入模板，快取取決於生成文檔的內容根和檔案名。
只有具有相同內容根和範本檔案名稱的請求，才會使用相同的快取。
下列最佳實務可確保在動態產生的範本傳遞至Forms服務時，快取不會無休止地成長：
   * 移除UUID，或在所有動態產生的範本中傳遞相同的UUID。
   * 從模板位元組或從磁碟上的相同檔案名生成文檔。

### 解除安裝Workbench {#uninstalling-workbench}

使用「控制面板」中的「添加或刪除程式」功能啟動「卸載程式」。 Workbench和Designer應用程式有個別的解除安裝程式。

## 設定AEM Forms XDC編輯器 {#configuring-aem-forms-xdc-editor}

使用XDC編輯器，網路打印機管理員可以建立和修改XML Forms體系結構設備配置(XDC)檔案。 XDC檔案描述了打印機的功能，如打印機語言或紙張大小與紙盒位置之間的關聯。

在網路打印機管理員使用XDC編輯器之前，請重新定位示例XDC檔案，並參閱使用XDC編輯器建立設備配置檔案。

**若要取得範例XDC檔案**:
1. 在AEM Forms伺服器上，在 [AEM Forms根]\sdk\samples\Output\IVS。
1. 將此資料夾的內容複製至可從Workbench或Eclipse系統存取的目錄。

**取得XDC編輯器說明**:
1. 前往AEM Forms檔案網站。
1. 按一下開發標籤，並導覽至使用XDC編輯器建立裝置設定檔。 下載xdc_editor_help_web.zip檔案，並按照自述檔案中提供的說明安裝幫助檔案。


---
title: 新功能摘要 | AEM 6.4 Forms
seo-title: New features summary | AEM 6.4 Forms
description: AEM 6.4 Forms的新功能和增強功能摘要。
seo-description: Summary of new features and enhancements in AEM 6.4 Forms.
uuid: 152068ec-47a8-43f4-b9c8-3a17d1f085fe
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 436aa424-d05e-4f3d-90ac-5ff3b05ddba8
exl-id: 21b8ed83-9c0c-41ee-9fbb-56ccebaee132
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2038'
ht-degree: 0%

---

# 新功能摘要 | AEM 6.4 Forms {#new-features-summary-aem-forms}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

AEM 6.4 Forms的新功能和增強功能摘要。

AEM Forms包含數項新功能和增強功能，可透過最適化表單和互動式通訊進一步簡化建立、管理和使用者體驗。

閱讀以快速了解新功能和增強功能。 請造訪資源說明檔案，以取得產品詳細資訊。 另請參閱AEM 6.4 Forms [發行說明](/help/release-notes/forms.md). 如需完整的AEM 6.4 Forms檔案，請造訪 [AEM 6.4 Forms指南](/help/forms/home.md).

## 互動式通訊 {#interactive-communications}

![通信管理](assets/correspondence-management.png)

「互動式通訊」可集中處理及管理安全、個人化與互動式通信的建立、集合與傳遞，例如商業信函、信函、檔案、對帳單、利益通知、財富管理說明書、行銷郵件、帳單和歡迎套件。

互動式通訊使用與最適化表單相同的基礎技術、程式和元件，建立回應式多通道通訊，就像回應式最適化表單一樣。

互動式通訊具有下列顯著優點：

* 提供與表單資料模型的OOTB整合，以便輕鬆、簡化地訪問後端資料庫和其他CRM系統（如MS Dynamics）
* 為打印和Web通道提供整合的創作介面
* 針對列印和網頁頻道提供拖放式製作介面，類似於適用性Forms製作。

互動式通訊是建立客戶通訊的預設且建議方法。 若要繼續使用AEM 6.3 Forms和AEM 6.2 Forms中的字母，您需要安裝相容性套件。

### 多通道互動式通信製作 {#multi-channel-interactive-communication-authoring}

使用互動式通信，您可以從單個文檔編輯器中編寫和編輯打印文檔和Web文檔。 利用相同的檔案片段來建立兩個管道的轉譯，即可消除重複工作。
![printweb_2](assets/printweb_2.png)

如需詳細資訊，請參閱 [互動式通訊概述](/help/forms/using/interactive-communications-overview.md).

### WYSIWYG文檔編輯器 {#wysiwyg-document-editor}

WYSIWYG拖放檔案編輯器適合商業使用。 資產的直覺式介面、拖放功能、標準元件、資料模型和整合式存放庫，有助於快速輕鬆地編寫互動式通訊。

若要建立互動式通訊或編輯現有通訊，商務使用者可使用下列建置組塊：管道、內容、屬性、資產、元件和資料來源。

![拖放 — n-lf](assets/drag-n-drop-lf.png)

如需詳細資訊，請參閱 [製作互動式通訊簡介](/help/forms/using/introduction-interactive-communication-authoring.md).

### 在交互通信中從打印內容自動生成Web版本 {#auto-generate-web-version-from-print-content-in-interactive-communication}

作者可以在同一編輯器中自動從打印文檔生成Web文檔內容，以製作、預覽和編輯打印文檔和Web文檔。 互動式通訊作者只需建立一次，即可發佈至所有管道。 互動式通訊作者可在列印和網頁通道中使用相同的檔案片段，以避免工作重複。

如需詳細資訊，請參閱 [打印通道和Web通道](/help/forms/using/web-channel-print-channel.md).

### 使用主題來設定互動式通信的網路通道 {#use-themes-to-style-web-channel-of-interactive-communication}

互動式通訊支援主題。 您可以建立主題，並將其套用至您的互動式通訊。 主題包含元件和面板的樣式詳細資料。 您可以重複使用不同互動式通訊上的主題，讓主題具有共同且一致的外觀和品牌。

AEM Forms包含互動式通訊的現成可用主題。 使用主題，您也可以自訂互動式通訊在裝置上的外觀。

如需詳細資訊，請參閱 [AEM Forms主題](/help/forms/using/themes.md).

### 增強的代理介面 {#enhanced-agent-interface}

代理用戶介面現在支援互動式通信的打印和Web預覽。 在同一Agent用戶介面中，您可以選擇編輯打印通道並預覽多通道交互通信的Web通道。 打印通道中的欄位、變數、FDM元素和文檔片段可以配置為由代理用戶介面中的代理修改。 表單資料模型支援可讓您使用預填的範例資料產生預覽。

如需詳細資訊，請參閱 [使用Agent UI準備和發送互動式通信](/help/forms/using/prepare-send-interactive-communication.md).

### 在圖表中顯示資訊 {#present-information-in-charts}

互動式通訊支援網頁中的圖表和列印通道，以提供更豐富的通訊。 使用餅圖、環圈圖、橫條圖和直條圖，您可以濃縮並直觀地呈現大量資訊，以便於解釋和分析。

![圖表–2](assets/chart-2.png) ![圖表](assets/chart.png)

如需詳細資訊，請參閱 [在互動式通信中使用圖表](/help/forms/using/chart-component-interactive-communications.md).

### 預填檔案的現成可用資料連接器 {#out-of-the-box-data-connectors-to-prefill-documents}

互動式通訊提供與商業工具的資料整合，以與多個商業系統（包括CRM系統）連線，並將資料個人化為檔案。

![fdm_ad](assets/fdm_ad.png)

如需詳細資訊，請參閱 [使用表單資料模型](/help/forms/using/using-form-data-model.md).

### 增強的檔案片段編輯器 {#enhanced-document-fragment-editor}

您現在可以在互動式通訊的檔案片段中使用FDM元素和規則。

* 支援表單資料模型元素
* 使用規則顯示或隱藏資產/文字片段
* 驗證元素/變數的值
* 執行函式以計算數學表達式的值

如需詳細資訊，請參閱：

* [互動式通信中的文本](/help/forms/using/texts-interactive-communications.md)
* [互動式通訊中的條件](/help/forms/using/conditions-interactive-communications.md)

### 現有資產的相容性套件 {#compatibility-package-for-existing-assets}

依預設，此版本不支援舊版AEM Forms的信函資產。 如果您要繼續使用AEM 6.3 Forms和AEM 6.2 Forms的信函，則需要安裝相容性套件。

## 資料整合 {#data-integration}

![](do-not-localize/data-integeration-1.png)

[AEM Forms資料整合](/help/forms/using/data-integration.md) 可讓您設定不同的資料來源；例如資料庫、基於RESTful或SOAP的Web服務和OData服務；要建立表單資料模型，可以使用該模型來綁定資料、預填和調用最適化表單和文檔中的服務。

此版本的資料整合中有數項新功能和增強功能。

### 不使用資料來源建立表單資料模型 {#create-form-data-model-without-data-source}

商務使用者和表單作者現在可以建立表單資料模型，包括其實體和屬性，而不需設定資料來源，且可用來製作最適化表單和檔案。 您稍後可以將表單資料模型系結至資料來源。 它消除了使用表單資料模型製作表單和檔案時對資料來源的依賴。

同樣地，您可以在現有表單資料模型中建立實體和子屬性，並稍後將其綁定到資料源中的相應實體和屬性。

如需詳細資訊，請參閱 [建立表單資料模型](/help/forms/using/create-form-data-models.md).

### 建立計算屬性 {#create-computed-properties}

Forms作者和開發人員可以在表單資料模型中建立計算屬性。 它們可讓您針對設定的資料來源中可用的資料建立規則或邏輯，以便計算屬性的值。 規則是當資料在表單資料模型中載入或表達式中屬性的值更改時所評估的表達式。 例如，名為Phatials的計算屬性根據資料源中指定的利率以及用戶在窗體中指定的貸款金額和期限計算貸款的月支付額。

計算屬性駐留在表單資料模型中的本地位置，且不存在於資料源中。 您可以在最適化表單和互動式通訊中使用運算屬性。

如需詳細資訊，請參閱 [使用表單資料模型](/help/forms/using/work-with-form-data-model.md).

### 使用範例資料預覽表單和檔案 {#preview-forms-and-documents-with-sample-data}

表單資料模型可讓您為表單資料模型中所有實體的屬性產生範例資料。 生成的資料對應於為屬性配置的資料類型。 預覽與表單資料模型相關聯的最適化表單或檔案時，會呈現預填的範例資料。

範例資料是一組隨機值，每次您產生它時都會變更。 不過，您可以編輯並儲存即使重新產生仍持續存在的範例資料。 例如，如果編輯和保存名字和姓氏屬性的示例資料，並稍後在表單資料模型中添加其他屬性或實體並重新生成示例資料，則名字和姓氏屬性將在重新生成其他屬性的值時顯示保存的值。

如需詳細資訊，請參閱 [使用表單資料模型](/help/forms/using/using-form-data-model.md).

### 重新整理資料來源定義 {#refresh-data-source-definitions}

資料來源實體或屬性中的任何更新不會自動反映在相關聯的表單資料模型中。 表單資料模型編輯器現在提供功能 ![refresh_forms_di](assets/refresh_forms_di.png) （重新整理資料來源定義）會讓伺服器快取失效，並從資料來源擷取更新的架構，以立即反映在表單資料模型中。

### 使用觸控式使用者介面設定資料來源 {#configure-data-sources-using-touch-user-interface}

透過此版本，資料來源的雲端服務設定可在觸控式使用者介面中使用。 此外，設定雲端服務的位置已變更為 **[!UICONTROL 工具>Cloud Services>資料來源]**. 請參閱 [設定資料來源](/help/forms/using/configure-data-sources.md).

## 最適化表單 {#adaptive-forms}

![authoring的簡化 — forms-and-documents_hero-image_2](assets/simplification-of-authoring-forms-and-documents_hero-image_2.png)

### 透過增強延遲載入改善最適化表單的效能 {#improve-performance-of-adaptive-forms-with-enhanced-lazy-loading}

適用性表單中的延遲載入功能會預先初始化表單片段，直到需要為止。 它將轉譯表單所需的時間減到最少，進而改善大型表單的效能，進而提供更理想的使用者體驗。

此發行中，延遲載入功能有幾項增強功能：

* 啟用延遲載入的表單片段支援檔案附件和條款與條件元件。
* 可重複面板支援已啟用延遲載入的適用性表單片段。
* AEM Forms應用程式支援具有延遲載入啟用片段的適用性表單。

## Forms導向的AEM工作流程 {#forms-centric-aem-workflows}

![aem-forms-workflow-on-osgi-](assets/aem-forms-workflow-on-osgi-.png)

透過以Forms為中心的AEM工作流程功能，您可以快速建立並部署OSGi堆疊上各種工作的工作流程。 您不再需要安裝JEE堆棧上提供的流程管理功能，從而簡化了部署並消除了應用程式伺服器和基礎架構成本。 如需詳細資訊，請參閱 [Forms OSGi工作流程](/help/forms/using/aem-forms-workflow.md).

以下是以Forms為中心的AEM工作流程增強功能：·

* 工作流程模型編輯器可在觸控式使用者介面中使用。 它可協助您縮短建立表單導向AEM工作流程所需的時間。
* 傳送電子郵件的工作流程步驟。 例如，您可以使用電子郵件步驟，在完成工作流程時傳送記錄檔案。
* 在工作流模型中使用表單資料模型服務的工作流程步驟。 此步驟可讓您叫用資料整合服務，而不需編寫任何自訂程式碼。 例如，您可以調用GET服務，從資料庫存檔中獲取員工詳細資訊，而無需編寫任何自定義代碼。

## AEM Forms 應用程式 {#aem-forms-app}

![aem-forms-app](assets/aem-forms-app.png)

AEM Forms應用程式可讓現場工作人員將行動裝置與AEM Forms伺服器同步，並處理其表單。 當設備離線時，應用程式無縫工作，方法是將資料本地保存在設備上，並在設備重新聯機時與伺服器同步資料。 如需詳細資訊，請參閱 [AEM Forms應用程式](/help/forms/using/aem-forms-app.md).

以下是AEM Forms應用程式中的改善項目：

* AEM Forms應用程式支援具有延遲載入啟用片段的適用性表單。
* AEM Forms應用程式支援具有表單資料模型的適用性表單。

## 文件安全性 {#document-security}

![aem-forms-document-security-](assets/aem-forms-document-security-.png)

使用文檔安全性，您可以安全地分發以支援格式保存的任何資訊。 檔案安全性可確保只有授權的使用者才能使用您的檔案。 以下是文檔安全性的重大更改：

* 檔案安全性提供 [可移植保護庫(PPL)](/help/forms/using/document-security-offerings.md) 在本機保護檔案，而不需將檔案傳送至AEM Forms伺服器。 只有安全憑證和原則詳細資訊會透過網路傳送至AEM Forms伺服器。 AEM 6.4 Forms已導入OSGi套件格式的可攜式保護程式庫(PPL)。 現在，您可以直接在AEM Forms伺服器上安裝PPL程式庫，並搭配使用AEM和PPL的功能。
* 檔案安全性C++ SDK和C++ PPL程式庫可透過Microsoft Visual Studio 2013編譯。 先前支援的版本為Microsoft Visual Studio 2010。

## 支援平台 {#supported-platforms}

可使用支援的作業系統、應用程式伺服器、資料庫、資料庫驅動程式、 JDK、LDAP伺服器和電子郵件伺服器的任意組合來設定AEM Forms。 以下是支援平台的重大變更：

<table> 
 <tbody> 
  <tr> 
   <td>Component</td> 
   <td>新增支援</td> 
   <td>已移除支援</td> 
  </tr> 
  <tr> 
   <td>作業系統</td> 
   <td> 
    <ul> 
     <li>Microsoft Windows Server 2016</li> 
     <li>OracleLinux 7更新3</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>IBM AIX 7.2 <sup>[1]</sup><br /> </li> 
     <li>Solaris 11 <sup>[1]</sup></li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>應用程式伺服器<br /> </td> 
   <td> 
    <ul> 
     <li>Red Hat JBoss EAP 7</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>IBM Weblogic 12.1.3</li> 
     <li>IBM WebSphere 8.5.5</li> 
     <li>Red Hat JBoss EAP 6</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>資料庫</td> 
   <td> 
    <ul> 
     <li>Microsoft SQL Server 2016</li> 
     <li>MySQL 5.7.19和更新版本</li> 
     <li>IBM DB2 11.1</li> 
     <li>Oracle多租用戶架構</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Microsoft SQL Server 2012<br /> </li> 
     <li>Microsoft SQL Server 2014</li> 
     <li>MySQL 5.5</li> 
     <li>IBM DB2 10.5<br /> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>LDAP伺服器</td> 
   <td> 
    <ul> 
     <li>Microsoft Active Directory 2016</li> 
     <li>IBM Tivoli Directory Server 6.4</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Microsoft Active Directory 2008</li> 
     <li>IBM Tivoli Directory Server 6.3</li> 
     <li>Oracle目錄伺服器企業版7.0</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>電子郵件伺服器</td> 
   <td> 
    <ul> 
     <li>Microsoft Office 365</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Novell Groupwise 7</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>連接器</td> 
   <td> 
    <ul> 
     <li>Microsoft Sharepoint 2016的連接器</li> 
     <li>EMC Documentum 7.3的連接器</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Microsoft Sharepoint 2007的連接器</li> 
     <li>Microsoft Sharepoint 2010的連接器</li> 
     <li>IBM Filenet 5.0的連接器</li> 
     <li>EMC Documentum 6.7的連接器</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>瀏覽器</td> 
   <td> 
    <ul> 
     <li>Apple Safari 11.x on macOS</li> 
     <li>Apple Safari 11.x on iOS</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>適用於Blackberry Z30和Q10設備的Blackberry瀏覽器</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>AEM Forms應用程式<br /> </td> 
   <td> 
    <ul> 
     <li>Android 4.4或更新版本</li> 
     <li>Apple iOS 10或更新版本</li> 
    </ul> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

1. AIX和Solaris作業系統僅適用於升級客戶。

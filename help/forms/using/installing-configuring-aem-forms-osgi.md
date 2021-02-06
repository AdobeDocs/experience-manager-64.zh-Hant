---
title: 安裝和配置資料捕獲功能
seo-title: 安裝和配置資料捕獲功能
description: 安裝和設定最適化表單、PDF表單和HTML5表單。 設定Adobe Analytics和Adobe Target以調整表單，以根據使用者的個人檔案分析表單的使用情況並鎖定使用者。
seo-description: 安裝和設定最適化表單、PDF表單和HTML5表單。 設定Adobe Analytics和Adobe Target以調整表單，以根據使用者的個人檔案分析表單的使用情況並鎖定使用者。
uuid: ce253b5a-eeb2-47d2-a6c9-e6f59384159a
contentOwner: khsingh
topic-tags: installing
discoiquuid: 1bb8360c-5543-484e-9712-590822211298
translation-type: tm+mt
source-git-commit: 6a8fa45ec61014acebe09048066972ecb1284641
workflow-type: tm+mt
source-wordcount: '1836'
ht-degree: 4%

---


# 安裝和配置資料捕獲功能{#install-and-configure-data-capture-capabilities}

安裝和設定最適化表單、PDF表單和HTML5表單。 設定Adobe Analytics和Adobe Target以調整表單，以根據使用者的個人檔案分析表單的使用情況並鎖定使用者。

## 簡介 {#introduction}

AEM Forms提供一組表單，以從使用者取得資料：最適化表單、HTML5表單和PDF表單。 它還提供工具來列出網頁上所有可用的表單、分析表單的使用情況，並根據用戶的個人檔案來定位用戶。 這些功能已包含在AEM Forms附加套件中。 附加元件套件已部署在AEM的「作者」或「發佈」例項上。

**最適化表** 單：這些表單會根據裝置的螢幕大小改變外觀，而且具有吸引力，而且具互動性。Adaptive Forms也可以與Adobe Analytics、Adobe Sign和Adobe Target整合。 它可讓您根據使用者的人口結構和其他功能，為使用者提供個人化表單和流程導向的體驗。 您也可以將最適化表單與Adobe Sign整合。

**PDF表** 格適合在PDF檔案中列印精確像素及擷取數位資訊。在數位頭像中，您可以使用Adobe Acrobat或Acrobat Reader填寫這些表格。 您可以將這些表單托管在您的網站上，或使用表單入口網站，在AEM網站上列出這些表單。 您也可以將這些表格以電子郵件附件形式寄送給其他人。 這些表格最適合案頭環境。

**HTML5表** 格是PDF表格的瀏覽器友好版本。HTML5 Forms適用於不支援PDF外掛程式的環境。 HTML5 Forms可讓您在不支援XFA PDF的行動裝置和案頭瀏覽器上轉換以XFA為基礎的表格。 這些表格最適合平板電腦和案頭環境。

AEM Forms是功能強大的企業級平台，資料擷取（最適化表單、PDF表單和HTML5表單）只是AEM Forms的功能之一。 如需完整的功能清單，請參閱[AEM Forms簡介](/help/forms/using/introduction-aem-forms.md)。

## 部署拓撲{#deployment-topology}

AEM Forms附加元件套件是部署在AEM上的應用程式。 您至少只需要一個AEM Author和AEM Publish執行個體，即可執行AEM Forms資料擷取功能。 建議使用下列拓撲來執行AEM Forms AEM Forms資料擷取功能。 有關拓撲的詳細資訊，請參見[ Architecture and deployment topologies for AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md)。

![推薦拓撲](assets/recommended-topology.png)

## 系統要求{#system-requirements}

在您開始安裝和設定資料擷取功能AEM Forms之前，請確定：

* 硬體和軟體基礎架構已就緒。 有關支援的硬體和軟體的詳細清單，請參見[技術要求](/help/sites-deploying/technical-requirements.md)。

* AEM例項的安裝路徑不包含空格。
* AEM例項已啟動並執行。 在AEM術語中，「例項」是在作者或發佈模式下伺服器上執行的AEM復本。 您至少需要兩個[AEM例項（一個作者和一個發佈）](/help/sites-deploying/deploy.md)才能執行AEM Forms資料擷取功能：

   * **作者**:用於建立、上傳和編輯內容以及管理網站的AEM例項。內容一旦準備好上線，就會複製到發佈實例。
   * **發佈**:透過網際網路或內部網路為大眾提供已發佈內容的AEM例項。

* 符合記憶體需求。 AEM Forms附加元件套件需要：

   * 15 GB的臨時空間，用於基於Microsoft Windows的安裝。
   * 6 GB的臨時空間，用於基於UNIX的安裝。

* 為作者和發佈實例設定複製和反向複製。 有關詳細資訊，請參見[Replication](/help/sites-deploying/replication.md)。
* 基於UNIX的系統的額外要求：如果您使用基於UNIX的作業系統，請從相應作業系統的安裝介質安裝以下軟體包。

<table> 
 <tbody> 
  <tr> 
   <td>expat</td> 
   <td>libxcb</td> 
   <td>freetype</td> 
   <td>libXau</td> 
  </tr> 
  <tr> 
   <td>libSM</td> 
   <td>zlib</td> 
   <td>libICE</td> 
   <td>libuuid</td> 
  </tr> 
  <tr> 
   <td>glibc</td> 
   <td>libXext</td> 
   <td><p>nss-softokn-freebl</p> </td> 
   <td>fontconfig</td> 
  </tr> 
  <tr> 
   <td>libX11</td> 
   <td>libXrender</td> 
   <td>libXrandr</td> 
   <td>libXinerama</td> 
  </tr> 
 </tbody> 
</table>

## 安裝AEM Forms附加元件套件{#install-aem-forms-add-on-package}

AEM Forms附加元件套件是部署在AEM上的應用程式。 套件包含AEM Forms資料擷取和其他功能。 執行下列步驟以安裝附加元件套件：

1. 開啟 [Software Distribution](https://experience.adobe.com/downloads)。您需要 Adobe ID 才能登入 Software Distribution。
1. 點一下頁首功能表中的 **[!UICONTROL Adobe Experience Manager]**。
1. 在&#x200B;**[!UICONTROL Filters]**&#x200B;區段中：
   1. 從&#x200B;**[!UICONTROL Solution]**&#x200B;下拉式清單中選擇&#x200B;**[!UICONTROL Forms]**。
   2. 選擇包的版本和類型。 您也可以使用&#x200B;**[!UICONTROL 搜尋下載]**&#x200B;選項來篩選結果。
1. 點選適用於您作業系統的套件名稱，選取「**[!UICONTROL 接受EULA條款]**」，然後點選「**[!UICONTROL 下載]**」。
1. 開啟[套件管理器](https://docs.adobe.com/content/help/zh-Hant/experience-manager-65/administering/contentmanagement/package-manager.html)，然後按一下&#x200B;**[!UICONTROL 「上傳套件」]**&#x200B;即可上傳套件。
1. 選擇軟體包並按一下&#x200B;**[!UICONTROL Install]**。

   您也可以透過[AEM Forms releases](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html)文章中所列的直接連結下載套件。

1. 安裝套件後，系統會提示您重新啟動AEM例項。 **不要立即重新啟動伺服器。** 在停止AEM Forms伺服器之前，請等到ServiceEvent REGISTERED和ServiceEvent UNREGISTERED訊息停止出現在 [AEM-Installation-Directory] /crx-quickstart/logs/error.log檔案中，且記錄檔是穩定的。
1. 對所有「作者」和「發佈」例項重複步驟1-7。

## 安裝後配置{#post-installation-configurations}

AEM Forms有一些必備和選用的設定。 必備配置包括配置BuncyCastle庫和序列化代理。 選用的組態包括設定Dispatcher、Forms入口網站、Adobe Sign、Adobe Analytics和Adobe Target。

### 強制安裝後配置{#mandatory-post-installation-configurations}

#### 配置RSA和BuncyCastle庫{#configure-rsa-and-bouncycastle-libraries}

對所有「作者」(Author)和「發佈」(Publish)實例執行以下步驟以引導委派庫：

1. 停止基礎AEM例項。
1. 開啟[AEM安裝目錄]\crx-quickstart\conf\sling.properties檔案以進行編輯。

   如果您使用[AEM安裝目錄]\crx-quickstart\bin\start.bat來啟動AEM，請編輯位於[AEM_root]\crx-quickstart\的sling.properties。

1. 將下列屬性新增至sling.properties檔案：

   ```
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*
   sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*
   ```

1. （僅限AIX）將下列屬性新增至sling.properties檔案：

   ```
   sling.bootdelegation.xerces=org.apache.xerces.*
   ```

1. 儲存並關閉檔案，然後啟動AEM例項。
1. 對所有「作者」和「發佈」例項重複步驟1-4。

#### 配置序列化代理{#configure-the-serialization-agent}

對所有「作者」(Author)和「發佈」(Publish)實例執行以下步驟，將包添加到allowlist:

1. 在瀏覽器視窗中開啟AEM Configuration Manager。 預設URL為`https://[server]:[port]/system/console/configMgr`。
1. 搜索並開啟&#x200B;**[!UICONTROL 還原序列化防火牆配置]**。
1. 將&#x200B;**[!UICONTROL sun.util.calendar]**&#x200B;軟體包添加到&#x200B;**[!UICONTROL allowlist]**&#x200B;欄位。 按一下&#x200B;**[!UICONTROL 「儲存」]**。
1. 對所有「作者」和「發佈」例項重複步驟1-3。

### 可選安裝後配置{#optional-post-installation-configurations}

#### 配置Dispatcher {#configure-dispatcher}

Dispatcher是AEM的快取和負載平衡工具。 AEM Dispatcher也可協助保護AEM伺服器不受攻擊。 您可搭配使用Dispatcher與企業級Web伺服器，以提高AEM例項的安全性。 如果您使用[Dispatcher](https://helpx.adobe.com/tw/experience-manager/dispatcher/using/dispatcher-configuration.html)，請針對AEM Forms執行下列設定：

1. 設定AEM Forms的存取權：

   開啟dispatcher.any檔案以進行編輯。 導覽至篩選區段，並將下列篩選新增至篩選區段：

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   儲存並關閉檔案。 有關篩選器的詳細資訊，請參見[Dispatcher documentation](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html)。

1. 設定反向連結篩選服務：

   以管理員身分登入Apache Felix組態管理員。 配置管理器的預設URL為`https://[server]:[port_number]/system/console/configMgr`。 在&#x200B;**[!UICONTROL Configurations]**&#x200B;選單中，選取&#x200B;**[!UICONTROL Apache Sling Referrer Filter]**&#x200B;選項。 在「允許主機」欄位中，輸入調度程式的主機名以允許它作為反向連接，然後按一下「保存」。 ****&#x200B;條目的格式為`https://[server]:[port]`。

#### 配置快取{#configure-cache}

快取是一種機制，可縮短資料存取時間、減少延遲，並改善輸入／輸出(I/O)速度。 最適化表單快取只儲存最適化表單的HTML內容和JSON結構，而不儲存任何預先填入的資料。 它有助於縮短轉換最適化表單所需的時間。

* 在使用最適化表單快取時，請使用[AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html)快取最適化表單的用戶端程式庫（CSS和JavaScript）。
* 在開發自訂元件時，請在用於開發的伺服器上停用最適化表單快取。

執行以下步驟以配置自適應表單快取：

1. 前往`https://[server]:[port]/system/console/configMgr`的AEM網頁主控台組態管理器。
1. 按一下&#x200B;**[!UICONTROL 自適應表單和互動式通信Web通道配置]**&#x200B;以編輯其配置值。 在編輯設定值對話方塊中，在&#x200B;**[!UICONTROL Number of Adaptive Forms]**&#x200B;欄位中指定AEM Forms伺服器執行個體可快取的表單或檔案數上限。 預設值為 100。按一下&#x200B;**[!UICONTROL 「儲存」]**。

   >[!NOTE]
   >
   >要禁用快取，請將「最適化表單數」欄位中的值設定為&#x200B;**0**。 當禁用或更改快取配置時，將重置快取，並從快取中刪除所有表單和文檔。

#### 為表單資料模型{#configure-ssl-communcation-for-form-data-model}配置SSL通信

您可以為表單資料模型啟用SSL通訊。 若要啟用表單資料模型的SSL通訊，請在啟動任何AEM Forms例項之前，將憑證新增至所有例項的Java信任存放區。 您可以執行以下命令來添加證書：&quot;

`keytool -import -alias <alias-name> -file <pathTo .cer certificate file> -keystore <<pathToJRE>\lib\security\cacerts>`

#### 設定Adobe Sign {#configure-adobe-sign}

Adobe Sign可針對最適化表單啟用電子簽名工作流程。 電子簽名可改善處理法律、銷售、薪資、人力資源管理等領域檔案的工作流程。

在典型的Adobe Sign和最適化表單案例中，使用者會填寫最適化表單以申請服務。 例如，信用卡申請和公民福利表。 當使用者填寫、提交及簽署申請表格時，表格會傳送給服務提供者，以做進一步的動作。 服務供應商會審核應用程式，並使用Adobe Sign來標示已核准的應用程式。 若要啟用類似的電子簽名工作流程，您可以將Adobe Sign與AEM Forms整合。

若要搭配AEM Forms使用Adobe Sign，請[將Adobe Sign與AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md)整合。

#### 設定Adobe Analytics {#configure-adobe-analytics}

AEM Forms與Adobe Analytics整合，可讓您擷取並追蹤已發佈表單和檔案的效能量度。 分析這些量度的目的，是根據使表單或檔案更有用所需變更的資料，做出明智的決策。

若要搭配AEM Forms使用Adobe Analytics，請參閱「設定分析和報表」](/help/forms/using/configure-analytics-forms-documents.md)。[

#### 整合Adobe Target {#integrate-adobe-target}

如果您的客戶提供的體驗並不吸引人，他們可能會放棄表單。 雖然這令客戶感到挫折，但也可以提升組織的支援數量和成本。 識別並提供合適的客戶體驗以提高轉化率，既重要，也極具挑戰性。 AEM表格是此問題的關鍵。

AEM表單與Adobe Marketing Cloud解決方案Adobe Target整合，跨多個數位通道提供個人化且吸引人的客戶體驗。 若要使用Adobe Target來A/B測試最適化表單，請[將Adobe Target與AEM Forms](/help/forms/using/ab-testing-adaptive-forms.md#setupandintegratetargetinaemforms)整合。

## 後續步驟{#next-steps}

您已設定環境以使用AEM Forms資料擷取功能。 現在，使用此功能的後續步驟是：

* [建立您的第一個最適化表單](/help/forms/using/create-your-first-adaptive-form.md)
* [建立您的第一個PDF表格](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/pdf/designer-quickstart.pdf)
* [HTML5 Forms簡介](/help/forms/using/introduction.md)


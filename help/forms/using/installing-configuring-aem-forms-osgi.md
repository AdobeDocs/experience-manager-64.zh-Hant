---
title: 安裝和配置資料捕獲功能
seo-title: Install and configure data capture capabilities
description: 安裝及設定最適化表單、PDF forms和HTML5 Forms。 設定Adobe Analytics和Adobe Target以使用最適化表單，以根據使用者的設定檔分析表單的使用情形，並鎖定使用者。
seo-description: Install and configure adaptive forms, PDF Forms, and HTML5 Forms. Configure Adobe Analytics and Adobe Target for adaptive forms to analyze usage of forms and target users based on their profile.
uuid: ce253b5a-eeb2-47d2-a6c9-e6f59384159a
contentOwner: khsingh
topic-tags: installing
discoiquuid: 1bb8360c-5543-484e-9712-590822211298
role: Admin
exl-id: 45b0fb99-9f7f-47e6-a4de-4db321867f8f
source-git-commit: 0f4f8c2640629f751337e8611a2c8f32f21bcb6d
workflow-type: tm+mt
source-wordcount: '1797'
ht-degree: 6%

---

# 安裝和配置資料捕獲功能 {#install-and-configure-data-capture-capabilities}

安裝及設定最適化表單、PDF forms和HTML5 Forms。 設定Adobe Analytics和Adobe Target以使用最適化表單，以根據使用者的設定檔分析表單的使用情形，並鎖定使用者。

## 簡介 {#introduction}

AEM Forms提供一套表單，可從使用者取得資料：適用性表單、HTML5 Forms和PDF forms。 它還提供了一些工具，用於列出網頁上所有可用的表單、分析表單的使用情況，以及根據用戶的配置檔案定位用戶。 這些功能包含在AEM Forms附加元件套件中。 附加套件部署在AEM的製作或發佈例項上。

**適用性表單：** 這些表單會根據裝置的螢幕大小而改變外觀、吸引人且互動性強。 適用性Forms也可與Adobe Analytics、Acrobat Sign和Adobe Target整合。 它可讓您根據使用者的人口統計和其他功能，為使用者提供個人化表單和以程式為導向的體驗。 您也可以整合最適化表單與Acrobat Sign。

**PDF forms** 適用於PDF文檔中的像素完美打印和數字資訊捕獲。 在數位頭像中，您可以使用Adobe Acrobat或Acrobat Reader填寫這些表單。 您可以在網站上托管這些表單，或使用表單入口網站在AEM網站上列出這些表單。 您也可以將這些表單以附件形式傳送給其他人。 這些表單最適合案頭環境。

**HTML5Forms** 是適用於瀏覽器的PDF forms。 HTML5 Forms適用於不支援PDF外掛程式的環境。 HTML5 Forms可讓您在不支援XFA型PDF的行動裝置和案頭瀏覽器上，轉譯XFA型表單。 這些表單最適合平板電腦和案頭環境。

AEM Forms是功能強大的企業級平台，資料擷取(最適化表單、PDF forms和HTML5 Forms)只是AEM Forms的其中一項功能。 如需功能的完整清單，請參閱 [AEM Forms簡介](/help/forms/using/introduction-aem-forms.md).

## 部署拓撲 {#deployment-topology}

AEM Forms附加元件套件是部署至AEM的應用程式。 您至少需要一個AEM製作和AEM發佈執行個體，才能執行AEM Forms資料擷取功能。 建議使用以下拓撲來運行AEM Forms AEM Forms資料捕獲功能。 有關拓撲的詳細資訊，請參見 [適用於AEM Forms的架構和部署拓撲](/help/forms/using/aem-forms-architecture-deployment.md).

![推薦拓撲](assets/recommended-topology.png)

## 系統需求 {#system-requirements}

開始安裝和配置資料捕獲功能AEM Forms之前，請確保：

* 硬體和軟體基礎架構已就緒。 有關支援的硬體和軟體的詳細清單，請參見 [技術要求](/help/sites-deploying/technical-requirements.md).

* AEM例項的安裝路徑不包含空格。
* AEM例項已啟動並執行。 在AEM術語中，「例項」是在製作或發佈模式中，於伺服器上執行的AEM復本。 您至少需要兩個 [AEM例項（一個作者和一個發佈）](/help/sites-deploying/deploy.md) 若要執行AEM Forms資料擷取功能：

   * **作者**:用於建立、上傳和編輯內容及管理網站的AEM例項。 內容準備好上線後，就會複製到發佈執行個體。
   * **發佈**:透過網際網路或內部網路向公眾提供已發佈內容的AEM例項。

* 滿足記憶體要求。 AEM Forms附加元件套件需要：

   * 15 GB的暫存空間，適用於Microsoft Windows安裝。
   * 6 GB的臨時空間，用於基於UNIX的安裝。

* 已設定製作和發佈執行個體的復寫和反向復寫。 如需詳細資訊，請參閱 [復寫](/help/sites-deploying/replication.md).
* 基於UNIX的系統的額外要求：如果使用基於UNIX的作業系統，請從相應作業系統的安裝介質安裝以下軟體包。

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

## 安裝AEM Forms附加元件套件 {#install-aem-forms-add-on-package}

AEM Forms附加元件套件是部署至AEM的應用程式。 套件包含AEM Forms資料擷取和其他功能。 執行下列步驟以安裝附加元件套件：

1. 開啟 [Software Distribution](https://experience.adobe.com/downloads)。您需要 Adobe ID 才能登入 Software Distribution。
1. 點一下頁首功能表中的 **[!UICONTROL Adobe Experience Manager]**。
1. 在 **[!UICONTROL 篩選器]** 小節：
   1. 選擇 **[!UICONTROL Forms]** 從 **[!UICONTROL 解決方案]** 下拉式清單。
   2. 選取套件的版本和類型。 您也可以使用 **[!UICONTROL 搜尋下載]** 選項來篩選結果。
1. 點選適用於您作業系統的套件名稱，然後選取 **[!UICONTROL 接受EULA條款]**，然後點選 **[!UICONTROL 下載]**.
1. 開啟[套件管理器](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html)，然後按一下&#x200B;**[!UICONTROL 「上傳套件」]**&#x200B;即可上傳套件。
1. 選取套件，然後按一下 **[!UICONTROL 安裝]**.

   您也可以透過 [AEM Forms版本](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) 文章。

1. 安裝套件後，系統會提示您重新啟動AEM執行個體。 **不要立即重新啟動伺服器。** 停止AEM Forms伺服器之前，請等到ServiceEvent REGISTERED和ServiceEvent UNECROVERD訊息停止出現在 [AEM-Installation-Directory]/crx-quickstart/logs/error.log檔案和日誌穩定。
1. 在所有「製作」和「發佈」例項上重複步驟1至7。

## 安裝後配置 {#post-installation-configurations}

AEM Forms提供一些強制和選用設定。 強制設定包括設定BouncyCastle程式庫和序列化代理。 選用的設定包括設定Dispatcher、Forms入口網站、Acrobat Sign、Adobe Analytics和Adobe Target。

### 強制安裝後配置 {#mandatory-post-installation-configurations}

#### 配置RSA和BouncyCastle庫  {#configure-rsa-and-bouncycastle-libraries}

對所有製作和發佈執行個體執行下列步驟以引導委派程式庫：

1. 停止基礎AEM例項。
1. 開啟 [AEM安裝目錄]\crx-quickstart\conf\sling.properties檔案進行編輯。

   若您使用 [AEM安裝目錄]\crx-quickstart\bin\start.bat以啟動AEM，然後編輯位於的sling.properties [AEM_root]\crx-quickstart\。

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
1. 在所有「製作」和「發佈」例項上重複步驟1至4。

#### 配置序列化代理 {#configure-the-serialization-agent}

對所有製作和發佈執行個體執行下列步驟，將套件新增至允許清單：

1. 在瀏覽器視窗中開啟AEM Configuration Manager。 預設URL為 `https://[server]:[port]/system/console/configMgr`.
1. 搜尋並開啟 **[!UICONTROL 反序列化防火牆配置]**.
1. 新增 **[!UICONTROL sun.util.calendar]** 封裝至 **[!UICONTROL 允許清單]** 欄位。 按一下「**[!UICONTROL 儲存]**」。
1. 在所有「製作」和「發佈」例項上重複步驟1至3。

### 可選安裝後配置 {#optional-post-installation-configurations}

#### 設定 Dispatcher {#configure-dispatcher}

Dispatcher是AEM的快取和負載平衡工具。 AEM Dispatcher也有助於保護AEM伺服器免受攻擊。 您可以搭配使用Dispatcher與企業級Web伺服器，以提高AEM例項的安全性。 如果您使用 [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html)，然後對AEM Forms執行下列設定：

1. 設定AEM Forms的存取權：

   開啟dispatcher.any檔案以進行編輯。 導覽至篩選區段，並將下列篩選新增至篩選區段：

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   儲存並關閉檔案。 如需篩選器的詳細資訊，請參閱 [Dispatcher檔案](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html).

1. 設定反向連結篩選服務：

   以管理員身分登入Apache Felix設定管理器。 配置管理器的預設URL為 `https://[server]:[port_number]/system/console/configMgr`. 在 **[!UICONTROL 配置]** ，選擇 **[!UICONTROL Apache Sling反向連結篩選器]** 選項。 在「允許主機」欄位中，輸入Dispatcher的主機名稱，以允許它作為反向連結，然後按一下 **[!UICONTROL 儲存]**. 輸入的格式為 `https://[server]:[port]`.

#### 配置快取 {#configure-cache}

快取是一種縮短資料存取時間、減少延遲並改善輸入/輸出(I/O)速度的機制。 適用性表單快取僅儲存適用性表單的HTML內容和JSON結構，而不儲存任何預先填入的資料。 有助於縮短演算最適化表單所需的時間。

* 使用最適化表單快取時，請使用 [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html) 快取最適化表單的用戶端程式庫（CSS和JavaScript）。
* 開發自訂元件時，請在用於開發的伺服器上停用最適化表單快取。

執行下列步驟以設定最適化表單快取：

1. 前往AEM Web主控台組態管理器，網址為 `https://[server]:[port]/system/console/configMgr`.
1. 按一下 **[!UICONTROL 最適化表單與互動式通訊Web通道設定]** 來編輯其配置值。 在「編輯設定值」對話方塊中，指定AEM Forms伺服器執行個體可在 **[!UICONTROL 適用性Forms數]** 欄位。 預設值為 100。按一下「**[!UICONTROL 儲存]**」。

   >[!NOTE]
   >
   >若要停用快取，請將「適用性Forms數」欄位中的值設為 **0**. 當禁用或更改快取配置時，將重置快取，並從快取中刪除所有表單和文檔。

#### 為表單資料模型配置SSL通訊 {#configure-ssl-communcation-for-form-data-model}

您可以為表單資料模型啟用SSL通訊。 若要為表單資料模型啟用SSL通訊，請在啟動任何AEM Forms例項前，將憑證新增至所有例項的Java信任存放區。 您可以執行以下命令來新增憑證：&quot;

`keytool -import -alias <alias-name> -file <pathTo .cer certificate file> -keystore <<pathToJRE>\lib\security\cacerts>`

#### 設定Acrobat Sign {#configure-adobe-sign}

Acrobat Sign可啟用最適化表單的電子簽名工作流程。 電子簽名有助於改善處理法律、銷售、薪資、人力資源管理及許多領域文件的工作流程。

在典型的Acrobat Sign和最適化表單案例中，使用者會填入最適化表單以申請服務。 例如，信用卡申請表和市民福利表單。用戶申請、提交和簽署申請表單時，此表單會被傳送給服務提供者，以進一步動作。服務提供商審核應用程式，並使用Acrobat Sign來標籤已批准的應用程式。 若要啟用類似的電子簽名工作流程，您可以整合Acrobat Sign與AEM Forms。

若要搭配使用Acrobat Sign和AEM Forms, [整合Acrobat Sign與AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

#### 設定Adobe Analytics {#configure-adobe-analytics}

AEM Forms與Adobe Analytics整合，可讓您擷取及追蹤已發佈表單和檔案的效能量度。 分析這些量度的目的，是根據讓表單或檔案更實用所需的變更資料，做出明智的決策。

若要搭配AEM Forms使用Adobe Analytics，請參閱 [設定分析和報表](/help/forms/using/configure-analytics-forms-documents.md).

#### 整合Adobe Target {#integrate-adobe-target}

如果您的客戶提供的體驗不吸引人，他們可能會放棄表單。 雖然讓客戶感到沮喪，但它還可以提高貴組織的支援量和成本。 識別並提供適當的客戶體驗以提高轉換率既重要又具挑戰性。 AEM表單是此問題的關鍵。

AEM forms與Adobe Marketing Cloud解決方案Adobe Target整合，可跨多個數位頻道提供個人化且吸引人的客戶體驗。 若要使用Adobe Target測試適用性表單， [整合Adobe Target與AEM Forms](/help/forms/using/ab-testing-adaptive-forms.md#setupandintegratetargetinaemforms).

## 後續步驟 {#next-steps}

您已設定環境以使用AEM Forms資料擷取功能。 現在，使用此功能的後續步驟為：

* [建立第一個最適化表單](/help/forms/using/create-your-first-adaptive-form.md)
* [建立您的第一個PDF表單](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/pdf/designer-quickstart.pdf)
* [HTML5 Forms簡介](/help/forms/using/introduction.md)

---
title: 設定AEM Forms參考網站
seo-title: Set up and configure AEM Forms reference sites
description: AEM Forms參考網站示範如何使用AEM Forms在組織中實作端對端工作流程。
seo-description: AEM Forms reference sites showcase how you can use AEM Forms to implement end-to-end workflow in an organization.
uuid: 087d58a1-d84e-49ac-a82d-4e7fc708f00f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 2feb4a9c-57ad-4c6b-a572-0047bc409bbb
exl-id: 9c5d956c-06bc-4428-afcd-02b4f81b802f
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '2911'
ht-degree: 2%

---

# 設定AEM Forms參考網站 {#set-up-and-configure-aem-forms-reference-sites}

AEM Forms提供參考網站實作，以示範AEM Forms如何協助金融服務行業和政府組織，隨時隨地在任何裝置上將其複雜的交易轉換為簡單而吸引人的數位體驗。

We.Finance和We.Gov參考網站會繪製真實的使用案例，以便與現有和潛在客戶互動，從首次接觸開始，以個人化且符合成本效益的方式管理通信和交易。

參考網站可讓您探索並展示下列AEM Forms的主要功能。

* 簡化吸引人且回應式最適化表單和互動式通訊的製作體驗。
* 互動式通訊，建立可適應裝置設定和配置的互動式、個人化和回應式客戶通訊。
* 資料整合，連線至不同的資料來源，透過表單資料模型預先填寫及提交表單資料。
* Forms工作流程，將業務流程和工作流程自動化。
* 進階的使用者資料管理與處理功能。
* 與Adobe Sign整合，以安全方式簽署及提交最適化表單。
* 與Adobe Target整合，提供目標式建議並執行A/B測試，從表單中最大化ROI。
* 與Adobe Analytics整合，以評估表單或行銷活動的績效並做出明智的決策。
* 增強表單填寫體驗。

參考網站提供可重複使用的資產，您可將這些資產當作範本，以建立您自己的資產。

* 與Adobe Sign整合，以安全方式簽署及提交最適化表單。

* 與Adobe Sign整合，以安全方式簽署及提交最適化表單。

## 設定參考網站的必要條件和步驟 {#prerequisites-and-steps-to-set-up-reference-sites}

設定參考網站之前，請確定您有下列項目：

* **AEM essentials**

   AEM QuickStart、AEM Forms附加套件和參考網站套件。 請參閱[AEM Forms版本](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) ，了解附加元件和參考網站套件的詳細資訊。

* **SMTP服務**
您可以使用任何SMTP服務。

* **Adobe Sign開發人員帳戶和Adobe Sign API應用程式**

   若要使用數位簽署功能，需要Adobe Sign開發人員帳戶。 請參閱[Adobe Sign](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html)。

* 要與AEM Forms整合的Microsoft Dynamics 365執行個體。 要運行引用站點，可將示例資料導入Microsoft Dynamics實例，以預填引用站點中使用的交互通信。
* 具有Forms附加元件套件的AEM 6.4執行個體。 如需詳細資訊，請參閱[安裝和設定AEM Forms](installing-configuring-aem-forms-osgi.md)。

按建議順序執行以下步驟以設定和配置參考站點。

<table> 
 <tbody> 
  <tr> 
   <th><strong>步驟</strong></th> 
   <th><strong>設定</strong></th> 
   <th><strong>附註</strong></th> 
  </tr> 
  <tr> 
   <td><a href="#installaemforms">安裝及設定AEM Forms</a></td> 
   <td>製作和發佈</td> 
   <td>安裝及設定AEM Forms製作和發佈執行個體。</td> 
  </tr> 
  <tr> 
   <td><a href="#ssl">配置SSL</a></td> 
   <td>製作和發佈<br /> </td> 
   <td>啟用HTTP over SSL以安全與Adobe Sign通訊。</td> 
  </tr> 
  <tr> 
   <td><p><a href="#externalizer">配置Day CQ Link Externalizer configuration</a></p> </td> 
   <td>製作和發佈<br /> </td> 
   <td><p>參考網站使用案例會針對不同的交易傳送電子郵件。 透過電子郵件傳送電子報時，須使用此設定。 它可確保URL和影像指向發佈例項。 </p> </td> 
  </tr> 
  <tr> 
   <td><a href="#cqmail">設定Day CQ Mail Service</a></td> 
   <td>製作和發佈</td> 
   <td>電子郵件通訊所需。</td> 
  </tr> 
  <tr> 
   <td><a href="#xss">覆寫預設XSS設定</a></td> 
   <td>發佈</td> 
   <td>用於覆蓋被xss安全性阻止的$、{和}字元。</td> 
  </tr> 
  <tr> 
   <td><a href="#aemds">配置AEM DS設定</a></td> 
   <td>作者</td> 
   <td>設定AEM DS以在發佈執行個體上提交表單，以及在製作執行個體上處理工作流程。</td> 
  </tr> 
  <tr> 
   <td><a href="#refsite">部署參考站點包</a></td> 
   <td>作者</td> 
   <td>在AEM Forms製作執行個體上部署參考網站套件。</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#optional-import-sample-data-into-microsoft-dynamics">將範例資料匯入Microsoft Dynamics</a></td> 
   <td>製作和發佈</td> 
   <td>信用卡申請、住房抵押申請和住房保險申請逐步導入樣本資料</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#configure-oauth-cloud-service-for-microsoft-dynamics">為Microsoft Dynamics配置OAuth雲端服務</a></td> 
   <td>製作和發佈</td> 
   <td>在AEM Forms中設定OAuth雲端服務，以啟用AEM Forms與Microsoft Dynamics之間的通訊。 </td> 
  </tr> 
  <tr> 
   <td><a href="#scheduler">設定Adobe Sign排程器</a></td> 
   <td>製作和發佈<br /> </td> 
   <td>變更排程器的設定，每兩分鐘檢查一次狀態。</td> 
  </tr> 
  <tr> 
   <td><a href="#sign-service">設定參考網站Adobe SignCloud Service</a></td> 
   <td>製作和發佈<br /> </td> 
   <td>隨參考站點包一起提供的配置，需要使用有效憑據重新配置。</td> 
  </tr> 
  <tr> 
   <td><a href="#anonymous">為匿名使用者設定Forms Common Configuration Service</a></td> 
   <td>發佈</td> 
   <td>配置允許匿名用戶提交、簽名和生成記錄文檔。</td> 
  </tr> 
  <tr> 
   <td><a href="#fdm">修改表單資料模型的Rest服務Swagger檔案</a></td> 
   <td>製作和發佈<br /> </td> 
   <td>修改您環境的服務。</td> 
  </tr> 
 </tbody> 
</table>

## 安裝及設定AEM Forms {#install-and-configure-aem-forms}

依照[在OSGi](/help/forms/using/installing-configuring-aem-forms-osgi.md)上安裝和設定AEM Forms中所述，安裝和部署AEM Forms。

>[!NOTE]
>
>如果多個發佈實例或製作實例和發佈實例位於不同的電腦上，則配置複製和反向複製代理。

## 配置SSL {#ssl}

必須有SSL設定才能與Adobe Sign伺服器通訊。 如需詳細步驟，請參閱[透過SSL啟用HTTP](/help/sites-administering/ssl-by-default.md)。

>[!CAUTION]
>
>請勿在`/etc/map`資料夾上配置強制SSL。

## 配置Day CQ Link Externalizer configuration {#externalizer}

在AEM中，**Externalizer**&#x200B;是OSGI服務，可讓您以程式設計方式將資源路徑（例如/path/to/my/page）轉換為外部和絕對URL(例如https://www.mycompany.com/path/to/my/page)，方法是使用預先設定的DNS來預先固定路徑。 請參閱[將URL外部化](/help/sites-developing/externalizer.md)。

>[!CAUTION]
>
>如果您使用SSL的自簽名憑證，請勿將外部化為HTTPS URL。
>
>此外，請對本地伺服器使用localhost ，而不是其主機名。

對製作和發佈執行個體執行下列步驟：

1. 前往https://*hostname>*:*port>*/system/console/configMgr中的OSGi配置。
1. 尋找並點選&#x200B;**[!UICONTROL Day CQ Link Externalizer]** configuration。

   「 Day CQ Link Externalizer」（日CQ連結外部化程式）對話框開啟，用於編輯配置。

1. 在Day CQ Link Externalizer對話方塊的Domains欄位中：

   * 在製作例項上，指定可從外部系統存取的發佈URL。 例如，主機名稱或發佈網站伺服器。
   * 在發佈例項上，指定作者和發佈URL。

1. 在製作和發佈執行個體上，請確定已在「網域」欄位中指定本機伺服器URL。
1. 點選&#x200B;**[!UICONTROL 儲存]**。 等待一段時間，以重新啟動所有服務。

## 設定Day CQ Mail Service {#cqmail}

參考網站實作需要在範例使用者填寫及提交表單時，傳送電子郵件給他們。 設定Day CQ Mail Service可讓您提供SMTP服務詳細資訊，以傳送自動電子郵件給客戶。 請參閱[設定電子郵件通知](/help/sites-administering/notification.md)。

執行下列步驟以在發佈執行個體上設定郵件服務：

1. 前往https://*hostname>*:*port>*/system/console/configMgr中的OSGi配置。
1. 尋找並點選&#x200B;**[!UICONTROL Day CQ Mail Service]**&#x200B;以開啟它進行設定。
1. 提供SMTP伺服器主機名和埠值。
1. 點選&#x200B;**[!UICONTROL 儲存]**。

>[!NOTE]
>
>您可以使用公司SMTP服務或Gmail等公共服務。 有關配置SMTP服務的資訊，請參閱SMTP服務文檔。

## 覆寫預設XSS設定 {#xss}

We.Finance參考網站的電子郵件範本包含電子郵件中的個人化連結。 這些連結的預留位置為`${placeholder}`。 傳送電子郵件前，這些預留位置會先由實際值取代。 AEM的預設XSS保護設定不允許HTML內容中的URL中出現大括弧(**{ }**)。 不過，您可以在發佈執行個體上執行下列步驟，以覆寫預設設定：

1. 將`/libs/cq/xssprotection/config.xml`複製到`/apps/cq/xssprotection/config.xml`。
1. 開啟 `/apps/cq/xssprotection/config.xml`.
1. 在`common-regexps`區段中，按如下方式修改`onsiteURL`項目並儲存檔案。

   `<regexp name="onsiteURL" value="([\p{L}\p{N}\\\.\#@\$\{\}%\+&;\-_~,\?=/!\*\(\)]*|\#(\w)+)"/>`

>[!NOTE]
>
>大括弧(**{ }**)會在HTML內容的URL中納入為接受的字元。

配置SMTP伺服器後，請嘗試使用Sarah Rose角色填寫表單，並將其另存為草稿。 儲存為草稿時，您可以選擇使用電子郵件接收草稿。 點選「**傳送電子郵件**」按鈕時，如果您收到包含應用程式草稿連結的電子郵件，表示您的電子郵件設定成功。 請確定您使用Sarah的認證登入，以查看草稿。

## 配置AEM DS設定 {#aemds}

AEM DS服務設定是參考網站使用案例中電子郵件通訊的發佈執行個體的必要設定。 有關在發佈實例上配置AEM DS服務設定的詳細步驟，請參閱[配置AEM DS設定](/help/forms/using/configuring-the-processing-server-url-.md)。

若為AEM Forms參考網站，請在AEM DS設定服務中，指定發佈伺服器的URL，而非處理伺服器的URL。

>[!CAUTION]
>
>如果您要為AEM Forms OSGi設定處理伺服器URL，請勿將`/lc`放入。

## 部署參考站點包 {#refsite}

使用Software Distribution安裝下列參考網站套件。

* [AEM-FORMS-6.4-FSI-REF-SITE](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-FSI-REF-SITE)
* [AEM-FORMS-6.4-GOV-REF-SITE](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-GOV-REF-SITE)

若要進一步了解如何使用套件，請參閱[如何使用套件](/help/sites-administering/package-manager.md)。

安裝套件並啟動製作和發佈執行個體後，請在瀏覽器中造訪下列URL:

* `https://[server]:[port]/wegov`
* `https://[server]:[port]/wefinance`

如果安裝成功，您可以存取We.Gov和We.Finance參考網站登陸頁面。

## （可選）將範例資料匯入Microsoft Dynamics {#optional-import-sample-data-into-microsoft-dynamics}

住房抵押申請和汽車保險申請參考站點配置為使用來自Microsoft Dynamics的記錄。 引用站點包安裝自定義實體和示例記錄，可將這些記錄導入Microsoft Dynamics以運行引用站點。 執行下列步驟來移轉和設定範例資料：

要導入自動保險應用程式的自定義實體，請執行以下操作：

1. 從AEM製作執行個體的`https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/WeFinanceAutoInsurance_1_0.zip`下載&#x200B;**WeFinanceAutoInsurance_1_0.zip**&#x200B;解決方案套件。
1. 在Microsoft Dynamics實例中，轉至&#x200B;**[!UICONTROL Settings]**&#x200B;菜單中的&#x200B;**[!UICONTROL Solutions]**，然後按一下&#x200B;**[!UICONTROL Import]**。 選取並匯入套件。

要導入自動保險應用程式的自定義實體，請執行以下操作：

1. 從https://[author]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/AEMFormsFSIRefsite_1_0.zip下載&#x200B;**AEMFormsFSIRefsite_1_0.zip**&#x200B;套件。 選取並匯入套件。

1. 在Microsoft Dynamics實例中，轉至&#x200B;**[!UICONTROL Settings]**&#x200B;菜單中的&#x200B;**[!UICONTROL Solutions]**，然後按一下&#x200B;**[!UICONTROL Import]**。 選取並匯入套件。

要導入客戶和保險單記錄，請執行以下操作：

1. 從您的AEM製作例項上的下列位置下載&#x200B;**We.Finance Customers.csv、We.Finance Auto Insurance Rexevals.csv**&#x200B;和&#x200B;**家庭抵押**&#x200B;資料檔案：

   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Customers.csv`
   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Auto Insurance Renewals.csv`
   * `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/Sarah%20Rose%20Contact.csv`

1. 在您的Microsoft Dynamics執行個體中，執行下列操作：

   * 轉到&#x200B;**[!UICONTROL Sales > We.Finance Customers]**，然後按一下&#x200B;**[!UICONTROL Import]**。
   * 轉至&#x200B;**[!UICONTROL Sales > We.Finance Auto Insurance]**，然後按一下&#x200B;**[!UICONTROL Import]**。
   * 轉至&#x200B;**[!UICONTROL Sales > We.Finance Home Mortgage]**，然後按一下&#x200B;**[!UICONTROL Import]**。

## 為Microsoft Dynamics配置OAuth雲端服務 {#configure-oauth-cloud-service-for-microsoft-dynamics}

在AEM Forms中設定OAuth雲端服務，以啟用AEM Forms與Microsoft Dynamics之間的通訊。 執行下列步驟，在AEM製作和發佈執行個體上設定OAuthCloud Service:

1. 在AEM製作例項上，前往「**[!UICONTROL 工具>Cloud Services>資料來源>全域]**」。 點選「 **[!UICONTROL Refsite Dynamics Integration]**」圖示，然後點選「**[!UICONTROL 屬性」]**。
1. 轉到Microsoft Azure Active Directory帳戶。 在註冊應用程式的&#x200B;**[!UICONTROL 回覆URL]**&#x200B;設定中，新增複製的雲端服務設定URL。 儲存設定。
1. 在「驗證設定」頁簽中，為Microsoft Dynamics實例指定&#x200B;**[!UICONTROL 服務根]**、**[!UICONTROL 客戶端ID]**、**[!UICONTROL 客戶端密碼]**&#x200B;和&#x200B;**[!UICONTROL 資源URL]**。 按一下「**[!UICONTROL 連線至OAuth]**」，重新導向至Microsoft Dynamics登入頁面。
1. 提供您的登入憑證。 登入後，系統會將您重新導向至AEM Forms雲端服務設定頁面。 按一下&#x200B;**[!UICONTROL 「儲存並關閉」]**。雲端服務設定已儲存。
1. 前往&#x200B;**[!UICONTROL Forms >資料整合> We.Finance]**。 選擇「自動保險（動態）」 ，然後按一下「編輯」。 Microsoft Dynamics實體會列在「資料來源」標籤下。 等待，直到所有實體從Microsoft Dynamics中擷取並列於資料來源標籤下。
1. 選擇&#x200B;**[!UICONTROL AutoInsuranceRenewal實體]**，然後按一下&#x200B;**[!UICONTROL 測試模型對象]**。 在輸入請求區段中，將客戶ID的值指定為&quot;900001&quot;，然後按一下&#x200B;**[!UICONTROL Test]**。 「輸出」部分顯示從Microsoft Dynamics(客戶ID 900001)中提取的記錄。
1. 在輸入請求區段中，將客戶ID的值指定為&quot;900001&quot;，然後按一下&#x200B;**[!UICONTROL Test]**。 「輸出」部分顯示從Microsoft Dynamics(客戶ID 900001)中提取的記錄。
1. 在發佈執行個體上重複步驟1至6。

## 設定Adobe Sign排程器 {#scheduler}

對製作和發佈例項執行下列動作：

1. 前往`https://[server]:[host]/system/console/configMgr`的AEM Web設定主控台。
1. 尋找並點選&#x200B;**[!UICONTROL Adobe Sign Configuration Service]**&#x200B;以開啟它進行設定。
1. 將&#x200B;**[!UICONTROL 狀態更新調度器表達式]**&#x200B;配置為&#x200B;**0 0/2 &amp;ast;&amp;ast;&amp;ast;?**。

   >[!NOTE]
   >
   >上述排程器設定每兩分鐘檢查一次Adobe Sign服務的狀態。

1. 點選&#x200B;**[!UICONTROL 儲存]**。

## 設定參考網站Adobe Sign雲端服務 {#sign-service}

對製作和發佈例項執行下列動作：

1. 前往&#x200B;**[!UICONTROL 工具>Cloud Services> Adobe Sign >全域]**。 選擇「**[!UICONTROL AEM Forms Reference Site Sign]**」，然後點選「**[!UICONTROL Properties]**」。

   >[!CAUTION]
   >
   >請確定https://[host]:[ssl_port]/mnt/overlay/adobesign/cloudservices/adobesign/properties.html URL已新增至Adobe Sign API應用程式OAuth設定的重新導向URL清單。

1. 指定Adobe Sign應用程式OAuth設定的用戶端ID和密碼。
1. （可選）選取「**[!UICONTROL 啟用附件的Adobe Sign也]**」選項，然後點選「**[!UICONTROL 連線至Adobe Sign]**」。 它會將附加至最適化表單的檔案附加至傳送以供簽署的對應Adobe Sign檔案。
1. 點選&#x200B;**[!UICONTROL 連線至Adobe Sign]**&#x200B;並使用您的Adobe Sign憑證登入。

## 設定Forms Common Configuration Service {#anonymous}

在發佈執行個體上執行下列動作，以允許存取匿名使用者：

1. 前往`https://[server]:[port]/system/console/configMgr`的AEM Web設定主控台。
1. 找到並點選&#x200B;**[!UICONTROL Forms Common Configuration Service]**&#x200B;以開啟它進行設定。
1. 為&#x200B;**[!UICONTROL 所有用戶]**&#x200B;配置&#x200B;**[!UICONTROL 允許]**&#x200B;欄位。
1. 點選&#x200B;**[!UICONTROL 儲存]**。

## 修改表單資料模型的Rest服務 {#fdm}

對製作和發佈例項執行下列動作：

1. 在`https://[server]:[port]/crx/de/index.jsp`前往CRXDE。
1. 導覽至&#x200B;**/conf/global/settings/cloudconfigs/fdm/roi-rest/jcr:content/swaggerFile**&#x200B;並開啟swagger檔案。
1. 根據您的環境更新主機和埠設定。
1. 儲存設定。
1. （**僅作者例項**）前往&#x200B;**[!UICONTROL 工具]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL 資料來源]** > **[!UICONTROL 全域]**。 選擇&#x200B;**[!UICONTROL roi-rest]**&#x200B;並點選&#x200B;**[!UICONTROL 屬性]**。 點選「**[!UICONTROL 驗證設定]**」，並將「驗證類型&#x200B;]**」設為「**[!UICONTROL &#x200B;基本驗證&#x200B;]**」。**[!UICONTROL &#x200B;指定`admin`/ `admin`作為用於訪問服務的用戶名/密碼。 點選&#x200B;**[!UICONTROL 儲存並關閉]**。

## 與Marketing Cloud整合 {#integrate-with-marketing-cloud}

您可以整合AEM Forms與Adobe Analytics和Adobe Target。 雖然Adobe Analytics可協助您產生報表並分析最適化表單的效能，但Adobe Target可協助您提供個人化體驗，並針對最適化表單執行A/B測試。

請執行下列動作，在AEM Forms中設定Adobe Analytics和Adobe Target。

### 設定Adobe Analytics {#configure-adobe-analytics}

AEM Forms與Adobe Analytics的整合可讓您監控及分析客戶與表單和檔案的互動情形。 它可協助您找出並修正問題區域，並採取行動以提高轉換率。

若要在參考網站中體驗此功能，請依照[設定分析和報表](/help/forms/using/configure-analytics-forms-documents.md)中所述設定您的Analytics帳戶。

若要產生報表，種子資料會與參考網站捆綁在一起。 使用種子資料之前，請執行下列操作：

1. 確保AEM雲端服務中提供We.Finance和We.Gov分析設定。 您可以透過下列其中一種方式來找到雲端服務：

   * 導覽至&#x200B;**[!UICONTROL 工具>Cloud Services>舊版Cloud Services]**，或瀏覽至https://&lt;host>:&lt;port>/libs/cq/core/content/tools/cloudservices.html。
   * 在&#x200B;**[!UICONTROL Cloud Services]**&#x200B;頁面的&#x200B;**[!UICONTROL Adobe Analytics]**&#x200B;區段下，按一下`Show Configurations`。 您可以看到We.Finance和We.Gov配置可用。 按一下以開啟設定。 在配置頁中，按一下&#x200B;**[!UICONTROL Edit]**。 提供有效的公司、用戶名、共用密碼（密碼）和資料中心，然後按一下&#x200B;**[!UICONTROL 連接至Analytics]**。 取得連線成功對話方塊後，按一下設定對話方塊上的&#x200B;**[!UICONTROL 確定]**。 在Analytics設定下設定架構，如[設定Analytics和報表](/help/forms/using/configure-analytics-forms-documents.md)中所述。

1. 導航到https://&lt;*host*>:*port*>/system/console/configMgr並執行以下操作：

   * 在&#x200B;**[!UICONTROL Web主控台設定]**&#x200B;頁面中，尋找並按一下&#x200B;**[!UICONTROL AEM Forms Analytics設定]**。
   * 在「AEM Forms Analytics設定」對話方塊的「**[!UICONTROL SiteCatalyst架構]**」欄位中，選取we-finance(we-finance)或we-gov(we-gov)。
   * 按一下「**[!UICONTROL 儲存]**」，讓頁面重新整理。

1. 導覽至https://&lt;host>:&lt;port>/aem/forms的forms manager，並執行下列操作：

   * 開啟We.Finance或We.Gov資料夾，然後選取您要查看報表的表單。
   * 按一下動作工具列中的啟用Analytics 。 為表單啟用分析後，按一下「分析報表」。 您會看到產生空白報表。 產生空白報表後，您必須提供重新整理套件隨附的種子資料，才能產生分析報表以供示範之用。

   參考網站提供分析報告，內含信用卡、住房抵押和兒童支援使用案例的種子資料。 有關種子資料的配置，請參閱[We.Finance參考站點逐步說明](/help/forms/using/finance-reference-site-walkthrough.md)和[We.Gov參考站點逐步說明](/help/forms/using/gov-reference-site-walkthrough.md)。

### 設定Target {#configure-target}

參考網站會展示AEM Forms與Adobe Target的整合，讓您在最適化檔案中加入目標式和個人化內容。 此外，還可建立最適化表單的A/B測試。

若要在參考網站中體驗整合，請執行下列操作以在AEM中設定Target:

1. 使用jvm引數`-Dabtesting.enabled=true`啟動製作快速啟動，以在伺服器上啟用A/B測試。

   **注意**:如果AEM執行個體在JBoss上執行（從Tunklying安裝開始為服務），請在檔案的 `-Dabtesting.enabled=true` 下列項目中新增 `jboss\bin\standalone.conf.bat` 參數：

   `set "JAVA_OPTS=%JAVA_OPTS% -Dadobeidp.serverName=server1 -Dfile.encoding=utf8 -Djava.net.preferIPv4Stack=true -Dabtesting.enabled=true"`

1. 訪問https://&lt;*hostname*>:&lt;*port*>/libs/cq/core/content/tools/cloudservices.html。

1. 在&#x200B;**[!UICONTROL Adobe Target]**&#x200B;區段中，按一下&#x200B;**[!UICONTROL 顯示配置]**。 您可以看到可用的We.Finance Target設定。 按一下以開啟設定。 在配置頁中，按一下&#x200B;**[!UICONTROL Edit]**。 將開啟配置的&#x200B;**[!UICONTROL 編輯元件]**&#x200B;對話框。

1. 指定與您的Target帳戶相關聯的用戶端代碼、電子郵件和密碼。 選擇API類型作為&#x200B;**[!UICONTROL REST]**。
1. 按一下&#x200B;**[!UICONTROL 連線至Adobe目標]**。 成功配置Target帳戶後，按一下&#x200B;**[!UICONTROL OK]**。 您可以看到封裝組態具有Target架構。

1. 轉到https://&lt;*hostname*>:&lt;*port*>/system/console/configMgr。

1. 按一下&#x200B;**[!UICONTROL AEM Forms Target設定]**。
1. 選取Target架構。
1. 在&#x200B;**[!UICONTROL 目標URL]**&#x200B;欄位中，指定AEM Forms的URL。 例如：https://&lt;*hostname*>:&lt;*port*>。

1. 按一下「**[!UICONTROL 儲存]**」。

信用卡申請和住房抵押申請使用案例演示了如何執行A/B測試，並演示了報告的示範用途。 如需逐步說明，請參閱[We.Finance參考網站逐步說明](/help/forms/using/finance-reference-site-walkthrough.md)。

## 下一步 {#next-step}

現在，您都已準備好探索參考網站。 如需參考網站工作流程和步驟的詳細資訊，請參閱：

* [We.金融參考網站逐步說明](/help/forms/using/finance-reference-site-walkthrough.md)
* [We.Gov參考網站逐步說明](/help/forms/using/gov-reference-site-walkthrough.md)

* [員工自助參考網站逐步說明](/help/forms/using/employee-self-service-reference-site.md)

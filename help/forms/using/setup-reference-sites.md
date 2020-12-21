---
title: 設定和設定AEM Forms參考網站
seo-title: 設定和設定AEM Forms參考網站
description: AEM Forms參考網站展示如何使用AEM Forms在組織中實作端對端工作流程。
seo-description: AEM Forms參考網站展示如何使用AEM Forms在組織中實作端對端工作流程。
uuid: 087d58a1-d84e-49ac-a82d-4e7fc708f00f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 2feb4a9c-57ad-4c6b-a572-0047bc409bbb
translation-type: tm+mt
source-git-commit: 6a8fa45ec61014acebe09048066972ecb1284641
workflow-type: tm+mt
source-wordcount: '2922'
ht-degree: 0%

---


# 設定和設定AEM Forms參考網站{#set-up-and-configure-aem-forms-reference-sites}

AEM Forms提供參考網站實作，以示範AEM Forms如何協助金融服務產業和政府機關將複雜的交易轉換為隨時隨地使用任何裝置的簡單而吸引人的數位體驗。

We.Finance和We.Gov參考網站利用現實生活中的使用案例，直接與現有和潛在客戶互動，從首次接觸開始，以個人化且具成本效益的方式管理通訊和交易。

參考網站可讓您探索並展示AEM Forms的下列主要功能。

* 簡化精彩且回應速度快的調適性表單和互動式通訊的製作體驗。
* 互動式通訊，以建立互動式、個人化和回應式的客戶通訊，以配合裝置設定和版面。
* 整合資料，以連接至不同的資料來源，透過表單資料模型預先填寫和提交表單資料。
* 表單工作流程，將商業程式和工作流程自動化。
* 進階的使用者資料管理與處理功能。
* 與Adobe Sign整合，以安全地簽署並送出最適化表單。
* 與Adobe Target整合，以提供針對性的建議並執行A/B測試，從表單獲得最大的投資報酬率。
* 與Adobe Analytics整合，以評估表單或促銷活動的效能，並做出明智的決策。
* 增強的表格填寫體驗。

參考網站提供可重複使用的資產，您可將其用作範本，以建立您自己的資產。

* 與Adobe Sign整合，以安全地簽署並送出最適化表單。

* 與Adobe Sign整合，以安全地簽署並送出最適化表單。

## 設定參考站點{#prerequisites-and-steps-to-set-up-reference-sites}的先決條件和步驟

在設定參考網站之前，請確定您有下列項目：

* **AEM Essentials**

   AEM QuickStart、AEM Forms附加元件套件和參考網站套件。 如需附加元件和參考網站套件的詳細資訊，請參閱[AEM Forms發行版本](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html)。

* **SMTP服務**
可以使用任何SMTP服務。

* **Adobe Sign開發人員帳戶和Adobe Sign API應用程式**

   若要使用數位簽署功能，您必須有Adobe Sign開發人員帳戶。 請參閱[Adobe Sign](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html)。

* 要與AEM Forms整合的Microsoft Dynamics 365執行個體。 若要執行參考網站，請將範例資料匯入Microsoft Dynamics例項，以預先填寫參考網站中使用的互動式通訊。
* AEM 6.4與Forms附加元件套件的執行中例項。 如需詳細資訊，請參閱[安裝與設定AEM Forms](installing-configuring-aem-forms-osgi.md)。

在建議的序列中執行以下步驟以設定和配置參考站點。

<table> 
 <tbody> 
  <tr> 
   <th><strong>步驟</strong></th> 
   <th><strong>設定</strong></th> 
   <th><strong>附註</strong></th> 
  </tr> 
  <tr> 
   <td><a href="#installaemforms">安裝和設定AEM Forms</a></td> 
   <td>作者與發佈</td> 
   <td>安裝和設定AEM Forms作者和發佈例項。</td> 
  </tr> 
  <tr> 
   <td><a href="#ssl">設定SSL</a></td> 
   <td>作者與發佈<br /> </td> 
   <td>啟用HTTP over SSL，以便與Adobe Sign進行安全通訊。</td> 
  </tr> 
  <tr> 
   <td><p><a href="#externalizer">設定Day CQ Link Externalizer設定</a></p> </td> 
   <td>作者與發佈<br /> </td> 
   <td><p>參考網站使用案例會針對不同的交易傳送電子郵件。 此設定是透過電子郵件傳送電子報的必要設定。 它可確保URL和影像指向發佈例項。 </p> </td> 
  </tr> 
  <tr> 
   <td><a href="#cqmail">配置日CQ郵件服務</a></td> 
   <td>作者與發佈</td> 
   <td>電子郵件通訊必要。</td> 
  </tr> 
  <tr> 
   <td><a href="#xss">覆寫預設XSS設定</a></td> 
   <td>發佈</td> 
   <td>用於覆寫受xss安全性封鎖的$、{和}字元。</td> 
  </tr> 
  <tr> 
   <td><a href="#aemds">設定AEM DS設定</a></td> 
   <td>作者</td> 
   <td>設定AEM DS，以便在發佈執行個體上提交表單，並在作者執行個體上處理工作流程。</td> 
  </tr> 
  <tr> 
   <td><a href="#refsite">部署參考站點包</a></td> 
   <td>作者</td> 
   <td>在AEM Forms作者例項上部署參考網站套件。</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#optional-import-sample-data-into-microsoft-dynamics">將範例資料匯入Microsoft Dynamics</a></td> 
   <td>作者與發佈</td> 
   <td>匯入信用卡申請、住房抵押申請及住房保險申請逐步說明的範例資料</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#configure-oauth-cloud-service-for-microsoft-dynamics">為Microsoft Dynamics設定OAuth雲端服務</a></td> 
   <td>作者與發佈</td> 
   <td>在AEM Forms中設定OAuth雲端服務，以啟用AEM Forms與Microsoft Dynamics之間的通訊。 </td> 
  </tr> 
  <tr> 
   <td><a href="#scheduler">設定Adobe Sign排程器</a></td> 
   <td>作者與發佈<br /> </td> 
   <td>更改調度程式的配置，每兩分鐘檢查一次狀態。</td> 
  </tr> 
  <tr> 
   <td><a href="#sign-service">設定參考網站Adobe Sign Cloud服務</a></td> 
   <td>作者與發佈<br /> </td> 
   <td>隨參考站點包一起提供的配置，需要使用有效的憑據重新配置。</td> 
  </tr> 
  <tr> 
   <td><a href="#anonymous">為匿名用戶配置Forms Common Configuration Service</a></td> 
   <td>發佈</td> 
   <td>此設定可讓匿名使用者提交、簽署及產生記錄檔案。</td> 
  </tr> 
  <tr> 
   <td><a href="#fdm">修改表單資料模型的Rest服務Swagger檔案</a></td> 
   <td>作者與發佈<br /> </td> 
   <td>修改您環境的服務。</td> 
  </tr> 
 </tbody> 
</table>

## 安裝和設定AEM Forms {#install-and-configure-aem-forms}

依[在OSGi](/help/forms/using/installing-configuring-aem-forms-osgi.md)上安裝和設定AEM Forms中所述，安裝和部署AEM Forms。

>[!NOTE]
>
>如果不同電腦上有多個發佈實例或作者和發佈實例，則配置複製和反向複製代理。

## 配置SSL {#ssl}

必須有SSL設定才能與Adobe Sign伺服器通訊。 如需詳細步驟，請參閱[透過SSL啟用HTTP](/help/sites-administering/ssl-by-default.md)。

>[!CAUTION]
>
>請勿在`/etc/map`資料夾上設定強制SSL。

## 配置Day CQ Link Externalizer配置{#externalizer}

在AEM中，**Externalizer**&#x200B;是OSGI服務，可讓您以程式設計方式轉換資源路徑(例如，/path/to/my/page)，透過預先設定的DNS來預先固定路徑，以匯入外部和絕對URL(例如https://www.mycompany.com/path/to/my/page)。 請參閱[將URL外部化](/help/sites-developing/externalizer.md)。

>[!CAUTION]
>
>如果您使用SSL的自簽證書，請勿將其外部化為HTTPS URL。
>
>此外，請使用localhost來取代本機伺服器的主機名稱。

對作者和發佈例項執行下列步驟：

1. 前往https://*hostname>**port>*/system/console/configMgr的「OSGi Configuration」（OSGi配置）。
1. 尋找並點選&#x200B;**[!UICONTROL Day CQ Link Externalizer]**&#x200B;組態。

   Day CQ Link Externalizer對話方塊隨即開啟，以編輯設定。

1. 在Day CQ Link Externalizer對話方塊的「網域」欄位中：

   * 在作者例項上，指定可從外部系統存取的發佈URL。 例如，主機名稱或發佈網頁伺服器。
   * 在發佈例項上，指定作者和發佈URL。

1. 在作者和發佈例項上，請確定已在「網域」欄位中指定本機伺服器URL。
1. 點選&#x200B;**[!UICONTROL Save]**。 等待一段時間，以便所有服務重新啟動。

## 配置Day CQ Mail Service {#cqmail}

參考網站實作需要在使用者填寫及送出表單時，傳送電子郵件給範例使用者。 配置Day CQ Mail服務可讓您提供SMTP服務詳細資訊，以向客戶發送自動化電子郵件。 請參閱[設定電子郵件通知](/help/sites-administering/notification.md)。

執行以下步驟以在發佈實例上配置郵件服務：

1. 前往https://*hostname>**port>*/system/console/configMgr的「OSGi Configuration」（OSGi配置）。
1. 查找並點選&#x200B;**[!UICONTROL Day CQ Mail Service]**&#x200B;以開啟它進行配置。
1. 提供SMTP伺服器主機名和埠值。
1. 點選&#x200B;**[!UICONTROL Save]**。

>[!NOTE]
>
>您可以使用公司SMTP服務或像Gmail這樣的公共服務。 有關配置SMTP服務的資訊，請參見SMTP服務文檔。

## 覆蓋預設的XSS配置{#xss}

We.Finance參考網站的電子郵件範本包含電子郵件中的個人化連結。 這些連結的預留位置為`${placeholder}`。 在傳送電子郵件之前，這些預留位置會由實際值取代。 AEM的預設XSS保護設定不允許HTML內容中的URL中出現大括弧(**{ }**)。 不過，您可以對發佈例項執行下列步驟，以覆寫預設設定：

1. 將`/libs/cq/xssprotection/config.xml`複製到`/apps/cq/xssprotection/config.xml`。
1. 開啟 `/apps/cq/xssprotection/config.xml`.
1. 在`common-regexps`部分中，按如下方式修改`onsiteURL`條目並保存檔案。

   `<regexp name="onsiteURL" value="([\p{L}\p{N}\\\.\#@\$\{\}%\+&;\-_~,\?=/!\*\(\)]*|\#(\w)+)"/>`

>[!NOTE]
>
>大括弧(**{ }**)在HTML內容的URL中會包含為接受的字元。

在配置SMTP伺服器後，嘗試使用Sarah Rose角色填寫表單並將其另存為草稿。 當您儲存為草稿時，可以選擇透過電子郵件接收草稿。 在點選「傳送電子郵件&#x200B;**」按鈕時，如果您收到電子郵件，其中包含應用程式草稿的連結，您的電子郵件設定就會成功。**&#x200B;請確定您使用Sarah的認證登入，以檢視草稿。

## 設定AEM DS設定{#aemds}

在參考網站使用案例中，「發佈」例項中必須有AEM DS服務設定，才能進行電子郵件通訊。 如需在Publish實例上設定AEM DS服務設定的詳細步驟，請參閱「設定AEM DS設定」[。](/help/forms/using/configuring-the-processing-server-url-.md)

對於AEM Forms參考網站，在「AEM DS設定服務」中，指定發佈伺服器的URL，而非處理伺服器的URL。

>[!CAUTION]
>
>如果您要為AEM Forms OSGi設定處理伺服器URL，請勿將`/lc`放入。

## 部署參考站點軟體包{#refsite}

使用「軟體分發」安裝以下參考站點軟體包。

* [AEM-FORMS-6.4-FSI-REF-SITE](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-FSI-REF-SITE)
* [AEM-FORMS-6.4-GOV-REF-SITE](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-GOV-REF-SITE)

要瞭解有關如何使用軟體包的詳細資訊，請參閱[如何使用軟體包](/help/sites-administering/package-manager.md)。

在您安裝套件並啟動作者和發佈例項後，請造訪瀏覽器中的下列URL:

* `https://[server]:[port]/wegov`
* `https://[server]:[port]/wefinance`

如果安裝成功，您可以存取We.Gov和We.Finance參考網站登陸頁面。

## （可選）將範例資料匯入Microsoft Dynamics {#optional-import-sample-data-into-microsoft-dynamics}

住房抵押申請和汽車保險申請參考網站的配置是使用Microsoft Dynamics的記錄。 參考網站套件會安裝自訂實體和範例記錄，您可將這些記錄匯入Microsoft Dynamics，以執行參考網站。 執行以下步驟來遷移和設定示例資料：

要導入汽車保險應用產品的自定義實體，請執行以下操作：

1. 從您的AEM作者例項的`https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/WeFinanceAutoInsurance_1_0.zip`下載&#x200B;**WeFinanceAutoInsurance_1_0.zip**&#x200B;解決方案套件。
1. 在您的Microsoft Dynamics實例中，轉至&#x200B;**[!UICONTROL Settings]**&#x200B;菜單中的&#x200B;**[!UICONTROL Solutions]**，然後按一下&#x200B;**[!UICONTROL Import]**。 選擇並導入包。

要導入汽車保險應用產品的自定義實體，請執行以下操作：

1. 從https://[author]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/AEMFormsFSIRefsite_1_0.zip下載&#x200B;**AEMFormsFSIRefsite_1_0.zip**&#x200B;套件。 選擇並導入包。

1. 在您的Microsoft Dynamics實例中，轉至&#x200B;**[!UICONTROL Settings]**&#x200B;菜單中的&#x200B;**[!UICONTROL Solutions]**，然後按一下&#x200B;**[!UICONTROL Import]**。 選擇並導入包。

要導入客戶和保險單記錄，請執行以下操作：

1. 從您的AEM作者例項的下列位置下載&#x200B;**We.Finance Customers.csv、We.Finance Auto Insurance Rexevals.csv**&#x200B;和&#x200B;**家庭按揭**&#x200B;資料檔案：

   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Customers.csv`
   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Auto Insurance Renewals.csv`
   * `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/Sarah%20Rose%20Contact.csv`

1. 在您的Microsoft Dynamics實例中，執行下列操作：

   * 前往&#x200B;**[!UICONTROL 銷售> We.Finance Customers]**，然後按一下&#x200B;**[!UICONTROL 匯入]**。
   * 轉至&#x200B;**[!UICONTROL 銷售> We.Finance Auto Insurance]**，然後按一下&#x200B;**[!UICONTROL 導入]**。
   * 前往&#x200B;**[!UICONTROL 銷售> We.Finance Home Mortgage]**，然後按一下&#x200B;**[!UICONTROL 匯入]**。

## 為Microsoft Dynamics {#configure-oauth-cloud-service-for-microsoft-dynamics}配置OAuth雲端服務

在AEM Forms中設定OAuth雲端服務，以啟用AEM Forms與Microsoft Dynamics之間的通訊。 執行下列步驟，在AEM作者上設定OAuth Cloud服務並發佈例項：

1. 在AEM作者例項上，請前往「**[!UICONTROL 工具>雲端服務>資料來源>全域]**」。 點選&#x200B;**[!UICONTROL Refsite Dynamics Integration]**&#x200B;圖示，點選&#x200B;**[!UICONTROL Properties]**。
1. 前往Microsoft Azure Active Directory帳戶。 在註冊應用程式的「回覆URL」設定中新增複製的雲端服務設定URL。 ****&#x200B;儲存設定。
1. 在「驗證設定」頁籤中，為Microsoft Dynamics實例指定&#x200B;**[!UICONTROL 服務根]**、**[!UICONTROL 客戶端ID]**、**[!UICONTROL 客戶端密碼]**&#x200B;和&#x200B;**[!UICONTROL 資源URL]**。 按一下「連線至重新導向至Microsoft Dynamics登入頁面的OAuth **[!UICONTROL 」。]**
1. 提供您的登入認證。 登入後，會將您重新導向至AEM Forms雲端服務設定頁面。 按一下&#x200B;**[!UICONTROL 「儲存並關閉」]**。雲端服務設定已儲存。
1. 前往&#x200B;**[!UICONTROL 表單>資料整合> We.Finance]**。 選擇「自動保險（動態）」，然後按一下「編輯」。 Microsoft Dynamics實體會列在「資料來源」標籤下。 請等待，直到從Microsoft Dynamics擷取所有實體並列在資料來源標籤下。
1. 選擇&#x200B;**[!UICONTROL AutoInsuranceRenewal實體]**，然後按一下&#x200B;**[!UICONTROL 測試模型對象]**。 在輸入請求區段中，將客戶ID的值指定為&quot;900001&quot;，然後按一下&#x200B;**[!UICONTROL Test]**。 「輸出」部分顯示從Microsoft Dynamics獲取的客戶ID 900001的記錄。
1. 在輸入請求區段中，將客戶ID的值指定為&quot;900001&quot;，然後按一下&#x200B;**[!UICONTROL Test]**。 「輸出」部分顯示從Microsoft Dynamics獲取的客戶ID 900001的記錄。
1. 在發佈實例上重複步驟1-6。

## 設定Adobe Sign排程器{#scheduler}

在作者和發佈例項上都執行下列動作：

1. 前往`https://[server]:[host]/system/console/configMgr`的「AEM Web Configuration console」(AEM Web Configuration console)。
1. 尋找並點選&#x200B;**[!UICONTROL Adobe Sign Configuration Service]**&#x200B;以開啟它進行設定。
1. 將&#x200B;**[!UICONTROL 狀態更新調度器表達式]**&#x200B;配置為&#x200B;**0 0/2 &amp;ast;&amp;ast;&amp;ast;?**。

   >[!NOTE]
   >
   >上述排程器設定每兩分鐘檢查一次Adobe Sign服務的狀態。

1. 點選&#x200B;**[!UICONTROL Save]**。

## 設定參考網站Adobe Sign雲端服務{#sign-service}

在作者和發佈例項上都執行下列動作：

1. 前往「**[!UICONTROL 工具>雲端服務> Adobe Sign >全域]**」。 選擇&#x200B;**[!UICONTROL AEM Forms Reference Site Sign]**，然後點選&#x200B;**[!UICONTROL Properties]**。

   >[!CAUTION]
   >
   >請確定https://[host]:[ssl_port]/mnt/overlay/adobesign/cloudservices/adobesign/properties.html URL已新增至Adobe Sign API應用程式的OAuth設定重新導向URL清單。

1. 指定Adobe Sign應用程式OAuth組態的用戶端ID和密碼。
1. （可選）選取「同時&#x200B;**[!UICONTROL 啟用附件的Adobe Sign」選項，然後點選「連線至Adobe Sign」。]******&#x200B;它會將附加至最適化表單的檔案附加至傳送以供簽署的對應Adobe Sign檔案。
1. 點選「**[!UICONTROL 連線至Adobe Sign]**」，並使用您的Adobe Sign認證登入。

## 配置Forms Common Configuration Service {#anonymous}

在發佈例項上執行下列動作，以允許匿名使用者存取：

1. 前往`https://[server]:[port]/system/console/configMgr`的「AEM Web Configuration console」(AEM Web Configuration console)。
1. 查找並點選&#x200B;**[!UICONTROL Forms Common Configuration Service]**&#x200B;以開啟它以進行設定。
1. 為&#x200B;**[!UICONTROL 所有用戶]**&#x200B;配置&#x200B;**[!UICONTROL 允許]**&#x200B;欄位。
1. 點選&#x200B;**[!UICONTROL Save]**。

## 修改表單資料模型{#fdm}的Rest服務

在作者和發佈例項上都執行下列動作：

1. 前往`https://[server]:[port]/crx/de/index.jsp`的CRXDE。
1. 導覽至&#x200B;**/conf/global/settings/cloudconfigs/fdm/roi-rest/jcr:content/swaggerFile**&#x200B;並開啟swagger檔案。
1. 根據您的環境更新主機和埠設定。
1. 儲存設定。
1. （**僅作者實例**）前往&#x200B;**[!UICONTROL 工具]** > **[!UICONTROL 雲端服務]** > **[!UICONTROL 資料來源]** > **[!UICONTROL global]**。 選擇&#x200B;**[!UICONTROL roi-rest]**&#x200B;並點選&#x200B;**[!UICONTROL 屬性]**。 點選「**[!UICONTROL 驗證設定]**」，並將「驗證類型&#x200B;]**」設定為「基本驗證]**」。 **[!UICONTROL **[!UICONTROL &#x200B;指定`admin`/ `admin`作為訪問服務的用戶名／密碼。 點選&#x200B;**[!UICONTROL 儲存並關閉]**。

## 與Marketing Cloud {#integrate-with-marketing-cloud}整合

您可以將AEM Forms與Adobe Analytics和Adobe Target整合。 雖然Adobe Analytics可協助您產生報告並分析最適化表單的效能，但Adobe Target可協助您提供個人化體驗，並針對最適化表單執行A/B測試。

請執行下列動作，在AEM Forms中設定Adobe Analytics和Adobe Target。

### 設定Adobe Analytics {#configure-adobe-analytics}

AEM Forms與Adobe Analytics的整合可讓您監控和分析客戶與表單和檔案的互動方式。 它可協助您找出並修正問題區域，並採取行動以提高轉換率。

若要在參考網站中體驗此功能，請依照[設定分析和報表](/help/forms/using/configure-analytics-forms-documents.md)中所述設定您的Analytics帳戶。

若要產生報表，種子資料會與參考網站搭售。 在使用種子資料之前，請執行以下操作：

1. 請確定AEM Cloud Services中提供We.Finance和We.Gov分析設定。 您可透過下列其中一種方式找到雲端服務：

   * 導覽至&#x200B;**[!UICONTROL 工具>雲端服務>舊版雲端服務]**，或瀏覽至https://&lt;host>:&lt;port>/libs/cq/core/content/tools/cloudservices.html。
   * 在&#x200B;**[!UICONTROL 雲端服務]**&#x200B;頁面的&#x200B;**[!UICONTROL Adobe Analytics]**&#x200B;區段下，按一下`Show Configurations`。 您可以看到We.Finance和We.Gov配置。 按一下以開啟配置。 在配置頁中，按一下&#x200B;**[!UICONTROL 編輯]**。 提供有效的公司、使用者名稱、共用密碼（密碼）和資料中心，然後按一下「連線至Analytics」。 ****&#x200B;在獲得連接成功對話框後，按一下配置對話框上的&#x200B;**[!UICONTROL 確定]**。 依[設定Analytics和報表](/help/forms/using/configure-analytics-forms-documents.md)中所述，在Analytics組態下設定架構。

1. 導航至https://&lt;*host*>:*port*/system/console/configMgr並執行下列操作：

   * 在&#x200B;**[!UICONTROL Web Console Configuration]**&#x200B;頁面中，尋找並按一下&#x200B;**[!UICONTROL AEM Forms Analytics Configuration]**。
   * 在「AEM表單分析設定」對話方塊的「**[!UICONTROL SiteCatalyst架構]**」欄位中，選取we-finance(we-finance)或we-gov(we-gov)。
   * 按一下&#x200B;**[!UICONTROL 保存]** ，讓頁面刷新。

1. 導覽至https://&lt;host>:&lt;port>/aem/forms的Forms Manager，並執行下列動作：

   * 開啟We.Finance或We.Gov檔案夾，並選取您要檢視報表的表單。
   * 按一下「動作工具列」中的「啟用分析」。 啟用表單分析後，按一下「分析報表」。 您可以看到產生的空白報表。 產生空白報表後，您必須提供refsite套件隨附的種子資料，才能產生分析報表以進行示範。

   參考網站提供分析報告，提供信用卡、住房抵押和子系支援使用案例的種子資料。 有關種子資料的配置，請參見[We.Finance參考站點逐步介紹](/help/forms/using/finance-reference-site-walkthrough.md)和[We.Gov參考站點逐步介紹](/help/forms/using/gov-reference-site-walkthrough.md)。

### 配置目標{#configure-target}

參考網站會展示AEM Forms與Adobe Target的整合，讓您將目標明確且個人化的內容加入最適化檔案中。 此外，還可建立最適化表單的A/B測試。

若要體驗參考網站中的整合，請執行下列動作，在AEM中設定Target:

1. 使用jvm引數`-Dabtesting.enabled=true`啟動作者快速入門，以在伺服器上啟用A/B測試。

   **注意**:如果AEM例項是在JBoss上執行，而JBoss是從Tunky安裝以服務形式啟動，請在檔 `-Dabtesting.enabled=true` 案的下列項目中新增 `jboss\bin\standalone.conf.bat` 參數：

   `set "JAVA_OPTS=%JAVA_OPTS% -Dadobeidp.serverName=server1 -Dfile.encoding=utf8 -Djava.net.preferIPv4Stack=true -Dabtesting.enabled=true"`

1. 訪問https://&lt;*hostname*>:*埠*>/libs/cq/core/content/tools/cloudservices.html。

1. 在&#x200B;**[!UICONTROL Adobe Target]**&#x200B;區段中，按一下&#x200B;**[!UICONTROL 顯示設定]**。 您可以看到可用的We.Finance Target設定。 按一下以開啟配置。 在配置頁中，按一下&#x200B;**[!UICONTROL 編輯]**。 此時將開啟配置的&#x200B;**[!UICONTROL 編輯元件]**&#x200B;對話框。

1. 指定您與Target帳戶關聯的用戶端代碼、電子郵件和密碼。 選擇API類型作為&#x200B;**[!UICONTROL REST]**。
1. 按一下「連線至Adobe目標&#x200B;]**」。**[!UICONTROL &#x200B;成功配置目標帳戶後，按一下&#x200B;**[!UICONTROL 確定]**。 您可以看到封裝的組態有Target Framework。

1. 轉到https://&lt;*hostname*>:*port*/system/console/configMgr。

1. 按一下「**[!UICONTROL AEM Forms Target設定]**」。
1. 選取Target架構。
1. 在&#x200B;**[!UICONTROL 目標URL]**&#x200B;欄位中，指定AEM Forms的URL。 例如：https://&lt;*hostname*>:*port*>。

1. 按一下&#x200B;**[!UICONTROL 「儲存」]**。

信用卡申請和住房抵押貸款申請使用案例演示了如何執行A/B測試並展示報告以進行演示。 如需逐步解說，請參閱[We.Finance參考網站逐步解說](/help/forms/using/finance-reference-site-walkthrough.md)。

## 下一步{#next-step}

現在，您都可以瀏覽參考網站。 如需參考網站工作流程和步驟的詳細資訊，請參閱：

* [We.Finance參考網站逐步說明](/help/forms/using/finance-reference-site-walkthrough.md)
* [We.Gov參考網站逐步說明](/help/forms/using/gov-reference-site-walkthrough.md)

* [員工自助服務參考網站逐步介紹](/help/forms/using/employee-self-service-reference-site.md)


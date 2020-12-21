---
title: 設定資料來源
seo-title: 設定資料來源
description: 瞭解如何設定不同類型的資料來源並運用來建立表單資料模型。
seo-description: 瞭解如何設定不同類型的資料來源並運用來建立表單資料模型。
uuid: 292217c2-8110-4232-a78b-edea212765d2
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: 1dafd400-16c0-416d-9e81-7bf53b761f98
translation-type: tm+mt
source-git-commit: b61c20c65ceade0153f5cd04fbedfd02e919d483
workflow-type: tm+mt
source-wordcount: '1418'
ht-degree: 0%

---


# 配置資料源{#configure-data-sources}

瞭解如何設定不同類型的資料來源並運用來建立表單資料模型。

![](do-not-localize/data-integeration.png)

AEM Forms Data Integration可讓您設定並連線至不同的資料來源。 下列類型是現成可用的支援。 不過，只需少量自訂，您也可以整合其他資料來源。

* 關係資料庫- MySQL、Microsoft SQL Server、IBM DB2和Oracle RDBMS。
* AEM使用者設定檔
* REST風格的Web服務
* 基於SOAP的web services
* OData服務

資料整合支援OAuth2.0、基本驗證和API金鑰驗證類型立即可用，並可實作自訂驗證以存取網站服務。 雖然RESTful、SOAP架構和OData服務已在AEM Cloud Services中設定，但AEM Web主控台中已設定關係式資料庫的JDBC和AEM使用者設定檔的連接器。

## 配置關係資料庫{#configure-relational-database}

您可以使用AEM Web Console Configuration來設定關係式資料庫。 執行下列動作：

1. 前往`https://[server]:[host]/system/console/configMgr`的AEM網頁主控台。
1. 尋找&#x200B;**[!UICONTROL Apache Sling Connection Pooled DataSource]**&#x200B;組態。 點選以在編輯模式中開啟設定。
1. 在配置對話框中，指定要配置的資料庫的詳細資訊，例如：

   * 資料來源的名稱
   * 儲存資料源名稱的資料源服務屬性
   * JDBC驅動程式的Java類名
   * JDBC連接URI
   * 用於與JDBC驅動程式建立連接的用戶名和密碼

   >[!NOTE]
   >
   >在設定資料來源之前，請務必先加密機密資訊，例如密碼。 要加密：
   >
   >1. 前往 `https://[server]:[port]/system/console/crypto`.
   >1. 在&#x200B;**[!UICONTROL 純文字檔案]**&#x200B;欄位中，指定要加密的口令或任何字串，然後按一下&#x200B;**[!UICONTROL 保護]**。

   >
   >加密的文字會出現在「受保護的文字」欄位中，您可在設定中指定。

1. 啟用「借用時測試」或「返回時測試」，以指定在分別從池借用或返回對象之前先驗證對象。********
1. 在&#x200B;**[!UICONTROL 驗證查詢]**&#x200B;欄位中指定SQL SELECT查詢，以驗證池中的連接。 查詢至少必須返回一行。 根據您的資料庫，指定下列其中一項：

   * 選擇1（MySQL和MS SQL）
   * 從雙(Oracle)中選擇1

1. 點選「**[!UICONTROL 儲存]**」以儲存設定。

## 設定AEM使用者設定檔{#configure-aem-user-profile}

您可以在AEM Web Console中使用「使用者描述檔連接器」設定來設定AEM使用者描述檔。 執行下列動作：

1. 前往`https://[server]:[host]/system/console/configMgr`的AEM網頁主控台。
1. 尋找&#x200B;**[!UICONTROL AEM Forms Data Integrations - User Profile Connector Configuration]**，然後點選以編輯模式開啟設定。
1. 在「用戶配置檔案連接器配置」對話框中，可以添加、刪除或更新用戶配置檔案屬性。 指定的屬性將可用於表單資料模型中。 使用以下格式指定用戶配置檔案屬性：

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   範例：

   * `name=profile/phoneNumber,type=string`
   * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >上例中的&#x200B;**&amp;ast;**&#x200B;表示CRXDE結構中AEM用戶配置檔案中`profile/empLocation/`節點下的所有節點。 這表示表單資料模型可以訪問`profile/empLocation/`節點下任何節點中存在的`city`類型`string`屬性。 但是，包含指定屬性的節點必須遵循一致的結構。

1. 點選「**[!UICONTROL 儲存]**」以儲存設定。

## 為雲端服務配置配置資料夾{#cloud-folder}

>[!NOTE]
>
>為RESTful、SOAP和OData服務配置雲端服務時，需要配置雲端服務資料夾。

AEM中的所有雲端服務設定都整合在AEM存放庫的`/conf`資料夾中。 依預設，`conf`資料夾包含`global`資料夾，您可在其中建立雲端服務組態。 不過，您必須針對雲端組態手動啟用它。 您也可以在`conf`中建立其他資料夾，以建立並組織雲端服務組態。

要為雲端服務配置配置資料夾：

1. 前往&#x200B;**[!UICONTROL 工具>一般>組態瀏覽器]**。
   * 如需詳細資訊，請參閱[設定瀏覽器檔案](/help/sites-administering/configurations.md)。
1. 請執行下列動作，為雲端設定啟用全域資料夾，或略過此步驟，為雲端服務設定建立並設定另一個資料夾。

   1. 在&#x200B;**[!UICONTROL 配置瀏覽器]**&#x200B;中，選擇`global`資料夾並按一下&#x200B;**[!UICONTROL 屬性]**。
   1. 在&#x200B;**[!UICONTROL 配置屬性]**&#x200B;對話框中，啟用&#x200B;**[!UICONTROL 雲配置]**。
   1. 點選&#x200B;**[!UICONTROL 儲存並關閉]**&#x200B;以儲存設定並退出對話方塊。

1. 在&#x200B;**[!UICONTROL 配置瀏覽器]**&#x200B;中，按一下&#x200B;**[!UICONTROL 建立]**。
1. 在&#x200B;**[!UICONTROL 建立設定]**&#x200B;對話方塊中，指定資料夾的標題並啟用&#x200B;**[!UICONTROL 雲端設定]**。
1. 點選「**[!UICONTROL 建立]**」以建立可用於雲端服務組態的資料夾。

## 配置REST風格的Web服務{#configure-restful-web-services}

REST風格的Web服務可在Swagger定義檔案中使用[Swagger規格](https://swagger.io/specification/)的JSON或YAML格式來說明。 若要在AEM雲端服務中設定REST風格的網站服務，請確定您的檔案系統上有Swagger檔案，或是檔案所在的URL。

執行以下操作以配置REST風格的服務：

1. 前往&#x200B;**[!UICONTROL 工具>雲端服務>資料來源]**。 點選以選取您要建立雲端設定的檔案夾。

   如需建立和設定雲端服務組態資料夾的相關資訊，請參閱[設定雲端服務組態資料夾](/help/forms/using/configure-data-sources.md#cloud-folder)。

1. 點選「**[!UICONTROL 建立]**」以開啟「建立資料來源設定」對話方塊。 ****&#x200B;指定配置的名稱和可選的標題，從&#x200B;**[!UICONTROL 服務類型]**&#x200B;下拉式清單中選擇&#x200B;**[!UICONTROL RESTful Service]**，選擇瀏覽並選擇配置的縮略圖，然後點選&#x200B;**[!UICONTROL Next]**。
1. 為RESTful服務指定以下詳細資訊：

   * 從「Swagger來源」下拉式清單中選取「URL」或「檔案」，並據以指定Swagger定義檔案的Swagger URL，或從本機檔案系統上傳Swagger檔案。
   * 選擇驗證類型— 無、OAuth2.0、基本驗證、API金鑰或自訂驗證— 訪問REST風格的服務，並相應地提供驗證的詳細資訊。

1. 點選&#x200B;**[!UICONTROL Create]**&#x200B;以建立REST風格服務的雲端設定。

## 配置SOAP web services {#configure-soap-web-services}

使用[網站服務描述語言(WSDL)規範](https://www.w3.org/TR/wsdl)來說明以SOAP為基礎的網站服務。 若要在AEM雲端服務中設定以SOAP為基礎的Web服務，請確定您擁有Web服務的WSDL URL，並執行下列動作：

1. 前往&#x200B;**[!UICONTROL 工具>雲端服務>資料來源]**。 點選以選取您要建立雲端設定的檔案夾。

   如需建立和設定雲端服務組態資料夾的相關資訊，請參閱[設定雲端服務組態資料夾](/help/forms/using/configure-data-sources.md#cloud-folder)。

1. 點選「**[!UICONTROL 建立]**」以開啟「建立資料來源設定」對話方塊。 ****&#x200B;指定配置的名稱和可選的標題，從&#x200B;**[!UICONTROL 服務類型]**&#x200B;下拉式清單中選擇&#x200B;**[!UICONTROL SOAP Web Service]**，選擇瀏覽並選擇配置的縮略圖，然後點選&#x200B;**[!UICONTROL Next]**。
1. 為SOAP Web服務指定以下內容：

   * Web服務的WSDL URL。
   * 服務端點. 在此欄位中指定一個值，以覆蓋WSDL中提及的服務端點。
   * 選擇驗證類型— 無、OAuth2.0、基本驗證、自訂驗證或X509 Token — 存取SOAP服務，並據以提供驗證的詳細資訊。

      如果您選取「X509 Token」做為「驗證」類型，請設定X509憑證。 如需詳細資訊，請參閱[設定憑證](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service)。
在**[!UICONTROL 鍵別名]**&#x200B;欄位中為X509證書指定KeyStore別名。 在&#x200B;**[!UICONTROL 即時時間]**&#x200B;欄位中，指定驗證要求保持有效的時間（以秒為單位）。 （可選）選擇簽署消息正文或時間戳標題或兩者。

1. 點選「**[!UICONTROL 建立]**」以建立SOAP網站服務的雲端設定。

## 配置OData服務{#config-odata}

OData服務由其服務根URL標識。 若要在AEM雲端服務中設定OData服務，請確定您有服務的服務根URL，並執行下列動作：

>[!NOTE]
>
>有關配置Microsoft Dynamics 365的逐步指南（線上或內部），請參閱[Microsoft Dynamics OData Configuration](/help/forms/using/ms-dynamics-odata-configuration.md)。

1. 前往&#x200B;**[!UICONTROL 工具>雲端服務>資料來源]**。 點選以選取您要建立雲端設定的檔案夾。

   如需建立和設定雲端服務組態資料夾的相關資訊，請參閱[設定雲端服務組態資料夾](/help/forms/using/configure-data-sources.md#cloud-folder)。

1. 點選「**[!UICONTROL 建立]**」以開啟「建立資料來源設定」對話方塊。 ****&#x200B;指定配置的名稱和可選標題，從&#x200B;**[!UICONTROL 服務類型]**&#x200B;下拉式清單中選擇&#x200B;**[!UICONTROL OData服務]**，選擇瀏覽並選擇配置的縮略圖，然後點選&#x200B;**[!UICONTROL Next]**。
1. 為OData服務指定以下詳細資訊：

   * 要配置的OData服務的服務根URL。
   * 選擇驗證類型— 無、OAuth2.0、基本驗證或自訂驗證— 訪問OData服務，並相應地提供驗證的詳細資訊。

   >[!NOTE]
   >
   >您必須選擇OAuth 2.0驗證類型，以OData端點作為服務根目錄與Microsoft Dynamics服務連接。

1. 點選&#x200B;**Create**&#x200B;以建立OData服務的雲端設定。

## 後續步驟{#next-steps}

您已設定資料來源。 接下來，您可以建立表單資料模型，或如果您已建立不含資料來源的表單資料模型，則可將其與您剛設定的資料來源建立關聯。 如需詳細資訊，請參閱[建立表單資料模型](/help/forms/using/create-form-data-models.md)。

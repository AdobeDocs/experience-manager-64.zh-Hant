---
title: 設定資料來源
seo-title: 設定資料來源
description: 了解如何設定不同類型的資料來源，並運用來建立表單資料模型。
seo-description: 了解如何設定不同類型的資料來源，並運用來建立表單資料模型。
uuid: 292217c2-8110-4232-a78b-edea212765d2
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: 1dafd400-16c0-416d-9e81-7bf53b761f98
feature: 表單資料模型
exl-id: a8f200ac-cf9f-47b7-9856-e62aa8b229eb
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1421'
ht-degree: 1%

---

# 配置資料源{#configure-data-sources}

了解如何設定不同類型的資料來源，並運用來建立表單資料模型。

![](do-not-localize/data-integeration.png)

AEM Forms資料整合可讓您設定並連線至不同的資料來源。 下列類型可立即使用。 不過，只要很少自訂，您也可以整合其他資料來源。

* 關係資料庫 — MySQL、Microsoft SQL Server、IBM DB2和OracleRDBMS。
* AEM使用者設定檔
* RESTful Web服務
* 基於SOAP的Web服務
* OData服務

資料整合支援OAuth2.0、基本驗證和API金鑰驗證類型，且可立即使用，並可實作自訂驗證以存取網站服務。 雖然AEM雲端服務中已設定RESTful、SOAP型和OData服務，但AEM web主控台中已設定關係資料庫的JDBC和AEM使用者設定檔的連接器。

## 配置關係資料庫{#configure-relational-database}

您可以使用AEM Web控制台配置配置關係資料庫。 請執行下列動作：

1. 前往`https://[server]:[host]/system/console/configMgr`的AEM Web主控台。
1. 尋找&#x200B;**[!UICONTROL Apache Sling Connection Pooled DataSource]**&#x200B;設定。 點選以在編輯模式中開啟設定。
1. 在配置對話框中，指定要配置的資料庫的詳細資訊，例如：

   * 資料源的名稱
   * 儲存資料源名稱的資料源服務屬性
   * JDBC驅動程式的Java類名
   * JDBC連接URI
   * 用於建立與JDBC驅動程式連接的用戶名和口令

   >[!NOTE]
   >
   >在配置資料源之前，請確保加密密碼等敏感資訊。 要加密：
   >
   >1. 前往 `https://[server]:[port]/system/console/crypto`.
   >1. 在&#x200B;**[!UICONTROL 純文字]**&#x200B;欄位中，指定要加密的密碼或任何字串，然後按一下&#x200B;**[!UICONTROL Protect]**。

   >
   >加密的文字會顯示在「受保護的文字」欄位中，您可以在配置中指定該欄位。

1. 啟用&#x200B;**[!UICONTROL 借用時測試]**&#x200B;或&#x200B;**[!UICONTROL 回訪時測試]** ，以指定在借用對象之前，或從和返回到池中，分別驗證對象。
1. 在&#x200B;**[!UICONTROL 驗證查詢]**&#x200B;欄位中指定SQL SELECT查詢，以驗證池中的連接。 查詢必須至少返回一行。 根據您的資料庫，指定下列任一項：

   * 選擇1（MySQL和MS SQL）
   * 從雙(Oracle)中選擇1

1. 點選&#x200B;**[!UICONTROL 儲存]**&#x200B;以儲存設定。

## 配置AEM用戶配置檔案{#configure-aem-user-profile}

您可以使用AEM Web Console中的「使用者設定檔連接器」設定來設定AEM使用者設定檔。 請執行下列動作：

1. 前往`https://[server]:[host]/system/console/configMgr`的AEM Web主控台。
1. 尋找&#x200B;**[!UICONTROL AEM Forms資料整合 — 使用者設定檔連接器組態]**，然後點選以在編輯模式中開啟組態。
1. 在「用戶配置檔案連接器配置」對話框中，可以添加、刪除或更新用戶配置檔案屬性。 指定的屬性將可用於表單資料模型。 使用以下格式指定用戶配置檔案屬性：

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   範例：

   * `name=profile/phoneNumber,type=string`
   * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >上例中的&#x200B;**&amp;ast;**&#x200B;表示CRXDE結構中AEM使用者設定檔中`profile/empLocation/`節點下的所有節點。 這表示表單資料模型可以存取`profile/empLocation/`節點下任何節點中出現的`string`類型的`city`屬性。 但是，包含指定屬性的節點必須遵循一致的結構。

1. 點選&#x200B;**[!UICONTROL 儲存]**&#x200B;以儲存設定。

## 配置雲服務配置的資料夾{#cloud-folder}

>[!NOTE]
>
>為RESTful、SOAP和OData服務配置雲服務時，需要配置雲服務資料夾。

AEM中的所有雲端服務設定皆整合至AEM存放庫的`/conf`資料夾中。 依預設，`conf`資料夾包含您可建立雲端服務設定的`global`資料夾。 不過，您必須為雲端設定手動啟用此功能。 您也可以在`conf`中建立其他資料夾，以建立和組織雲端服務設定。

要配置雲端服務配置的資料夾：

1. 前往「**[!UICONTROL 工具>一般>設定瀏覽器]**」。
   * 如需詳細資訊，請參閱[設定瀏覽器檔案](/help/sites-administering/configurations.md) 。
1. 請執行下列操作以啟用雲配置的全局資料夾，或跳過此步驟以建立和配置雲服務配置的其他資料夾。

   1. 在&#x200B;**[!UICONTROL Configuration Browser]**&#x200B;中，選擇`global`資料夾，然後點選&#x200B;**[!UICONTROL Properties]**。
   1. 在&#x200B;**[!UICONTROL 配置屬性]**&#x200B;對話框中，啟用&#x200B;**[!UICONTROL 雲配置]**。
   1. 點選&#x200B;**[!UICONTROL 儲存並關閉]**&#x200B;以儲存設定並退出對話方塊。

1. 在「**[!UICONTROL 設定瀏覽器]**」中，點選「**[!UICONTROL 建立]**」。
1. 在&#x200B;**[!UICONTROL 建立配置]**&#x200B;對話框中，指定資料夾的標題並啟用&#x200B;**[!UICONTROL 雲配置]**。
1. 點選&#x200B;**[!UICONTROL 建立]**&#x200B;以建立為雲端服務設定啟用的資料夾。

## 配置RESTful Web服務{#configure-restful-web-services}

RESTful Web服務可使用JSON的[Swagger規範](https://swagger.io/specification/)或Swagger定義檔案的YAML格式描述。 若要在AEM雲端服務中設定RESTful Web服務，請確定您的檔案系統上有Swagger檔案，或檔案托管所在的URL。

請執行以下操作來配置RESTful服務：

1. 前往「**[!UICONTROL 工具>Cloud Services>資料來源]**」。 點選以選取您要建立雲端設定的資料夾。

   如需建立和設定雲端服務設定資料夾的相關資訊，請參閱[設定雲端服務設定資料夾](/help/forms/using/configure-data-sources.md#cloud-folder) 。

1. 點選&#x200B;**[!UICONTROL Create]**&#x200B;以開啟&#x200B;**[!UICONTROL Create Data Source Configuration對話方塊]**。 指定配置的名稱和可選的標題，從&#x200B;**[!UICONTROL 服務類型]**&#x200B;下拉清單中選擇&#x200B;**[!UICONTROL RESTful服務]**，選擇瀏覽並選擇配置的縮略圖，然後點選&#x200B;**[!UICONTROL 下一步]**。
1. 為RESTful服務指定以下詳細資訊：

   * 從「Swagger源」下拉清單中選擇「URL」或「檔案」，並相應地指定Swagger URL到Swagger定義檔案，或從本地檔案系統上載Swagger檔案。
   * 選取驗證類型（無、OAuth2.0、基本驗證、API密鑰或自訂驗證）以存取RESTful服務，並據此提供驗證的詳細資訊。

1. 點選&#x200B;**[!UICONTROL 建立]**&#x200B;以建立RESTful服務的雲配置。

## 配置SOAP Web服務{#configure-soap-web-services}

使用[Web服務描述語言(WSDL)規範](https://www.w3.org/TR/wsdl)描述基於SOAP的Web服務。 若要在AEM雲端服務中設定以SOAP為基礎的網站服務，請確定您有網站服務的WSDL URL，並執行下列動作：

1. 前往「**[!UICONTROL 工具>Cloud Services>資料來源]**」。 點選以選取您要建立雲端設定的資料夾。

   如需建立和設定雲端服務設定資料夾的相關資訊，請參閱[設定雲端服務設定資料夾](/help/forms/using/configure-data-sources.md#cloud-folder) 。

1. 點選&#x200B;**[!UICONTROL Create]**&#x200B;以開啟&#x200B;**[!UICONTROL Create Data Source Configuration對話方塊]**。 指定配置的名稱和可選的標題，從&#x200B;**[!UICONTROL 服務類型]**&#x200B;下拉清單中選擇&#x200B;**[!UICONTROL SOAP Web Service]**，選擇瀏覽並選擇配置的縮略圖，然後點選&#x200B;**[!UICONTROL Next]**。
1. 為SOAP Web服務指定以下內容：

   * Web服務的WSDL URL。
   * 服務端點. 在此欄位中指定一個值，以覆蓋WSDL中提及的服務端點。
   * 選取驗證類型（無、OAuth2.0、基本驗證、自訂驗證或X509代號）以存取SOAP服務，並相應地提供驗證的詳細資訊。

      如果您選取「X509代號」作為「驗證類型」，請設定X509憑證。 如需詳細資訊，請參閱[設定憑證](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service)。
在**[!UICONTROL 密鑰別名]**&#x200B;欄位中指定X509證書的KeyStore別名。 在&#x200B;**[!UICONTROL 存留時間]**&#x200B;欄位中指定驗證請求保持有效的時間（以秒為單位）。 （可選）選擇簽署消息正文或時間戳標頭或兩者。

1. 點選&#x200B;**[!UICONTROL 建立]**&#x200B;以建立SOAP網站服務的雲配置。

## 配置OData服務{#config-odata}

OData服務由其服務根URL識別。 若要在AEM雲端服務中設定OData服務，請確定您有服務的服務根URL，並執行下列操作：

>[!NOTE]
>
>有關配置Microsoft Dynamics 365的線上或內部部署的逐步指南，請參閱[Microsoft Dynamics OData配置](/help/forms/using/ms-dynamics-odata-configuration.md)。

1. 前往「**[!UICONTROL 工具>Cloud Services>資料來源]**」。 點選以選取您要建立雲端設定的資料夾。

   如需建立和設定雲端服務設定資料夾的相關資訊，請參閱[設定雲端服務設定資料夾](/help/forms/using/configure-data-sources.md#cloud-folder) 。

1. 點選&#x200B;**[!UICONTROL Create]**&#x200B;以開啟&#x200B;**[!UICONTROL Create Data Source Configuration對話方塊]**。 指定配置的名稱和可選的標題，從&#x200B;**[!UICONTROL 服務類型]**&#x200B;下拉清單中選擇&#x200B;**[!UICONTROL OData服務]**，選擇瀏覽並選擇配置的縮略圖，然後點選&#x200B;**[!UICONTROL Next]**。
1. 指定OData服務的以下詳細資訊：

   * 要配置的OData服務的服務根URL。
   * 選擇身份驗證類型（無、OAuth2.0、基本身份驗證或自定義身份驗證）以訪問OData服務，並相應地提供身份驗證的詳細資訊。

   >[!NOTE]
   >
   >必須選擇OAuth 2.0身份驗證類型，以OData端點作為服務根連接到Microsoft Dynamics服務。

1. 點選&#x200B;**建立**&#x200B;以建立OData服務的雲配置。

## 後續步驟 {#next-steps}

您已設定資料來源。 接下來，您可以建立表單資料模型，或者如果您已建立表單資料模型而不使用資料來源，則可將其與您剛設定的資料來源建立關聯。 如需詳細資訊，請參閱[建立表單資料模型](/help/forms/using/create-form-data-models.md)。

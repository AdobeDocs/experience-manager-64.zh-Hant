---
title: 使用智慧內容服務設定資產標籤。
description: 了解如何使用智慧內容服務在 [!DNL Adobe Experience Manager]中設定智慧標籤和增強智慧標籤。
contentOwner: AG
feature: 智慧標籤，標籤
role: Admin
exl-id: 11c5dd92-f824-41d2-9ab2-b32bdeae01b6
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '1215'
ht-degree: 34%

---

# 使用智慧內容服務設定資產標籤 {#configure-asset-tagging-using-the-smart-content-service}

您可以使用[!DNL Adobe Developer Console]將[!DNL Adobe Experience Manager]與智慧內容服務整合。 使用此配置可從[!DNL Experience Manager]內訪問智慧內容服務。

文章詳細說明設定智慧內容服務所需的下列主要工作。 在後端， [!DNL Experience Manager]伺服器會先使用[!DNL Adobe Developer Console]閘道驗證您的服務憑證，然後再將您的請求轉送至智慧內容服務。

1. [在中建立智](#obtain-public-certificate) 慧內容服 [!DNL Experience Manager] 務設定以產生公開金鑰。[取得公開憑證](#obtain-public-certificate)以進行 OAuth 整合。

1. [在 Adobe 開發人員控制台中建立整合](#create-adobe-i-o-integration)，並上傳產生的公開金鑰。

1. [使用的](#configure-smart-content-service) API金鑰和其他憑證來設定您的部 [!DNL Adobe Developer Console]署。

1. [測試設定](#validate-the-configuration)。

1. （可選）[在資產上傳時啟用自動標籤](#enable-smart-tagging-in-the-update-asset-workflow-optional)。

## 必備條件 {#prerequisites}

使用智慧內容服務之前，請確定以下內容以在[!DNL Adobe Developer Console]上建立整合：

* Adobe ID 帳戶具有組織的管理員權限。

* 您的組織已啟用智慧內容服務。

若要啟用增強智慧標籤，除了上述外，還請安裝最新的[Experience ManagerService Pack](https://helpx.adobe.com/tw/experience-manager/aem-releases-updates.html)。

## 建立智慧內容服務設定以取得公開憑證 {#obtain-public-certificate}

公開證書允許您在[!DNL Adobe Developer Console]上驗證配置檔案。

1. 在[!DNL Experience Manager]用戶介面中，訪問&#x200B;**[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL 舊式Cloud Services]**。

1. 在「Cloud Services」頁面中，按一下&#x200B;**[!UICONTROL 資產智慧標籤]**&#x200B;下方的&#x200B;**[!UICONTROL 立即設定]**。

1. 在&#x200B;**[!UICONTROL 建立設定]**&#x200B;對話方塊中，指定智慧標籤設定的標題和名稱。 按一下&#x200B;**[!UICONTROL 建立]**。

1. 在&#x200B;**[!UICONTROL AEM智慧內容服務]**&#x200B;對話方塊中，使用下列值：

   **[!UICONTROL 服務 URL]**: `https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL 授權伺服器]**: `https://ims-na1.adobelogin.com`

   暫時將其他欄位留空（稍後將提供）。 按一下&#x200B;**[!UICONTROL 「確定」]**。

   ![Experience Manager智慧內容服務對話方塊以提供內容服務URL](assets/aem_scs.png)


   *圖：提供內容服務URL的智慧型內容服務對話方塊*

   >[!NOTE]
   >
   >以[!UICONTROL 服務URL]提供的URL無法透過瀏覽器存取，並產生404錯誤。 此配置與[!UICONTROL 服務URL]參數的值相同，工作正常。 有關整體服務狀態和維護計畫，請參閱[https://status.adobe.com](https://status.adobe.com)。

1. 按一下&#x200B;**[!UICONTROL 下載OAuth整合的公開憑證]**，然後下載公開憑證檔案`AEM-SmartTags.crt`。

   ![為智慧標籤服務建立的設定的表示](assets/smart-tags-download-public-cert.png)


   *圖：智慧標籤服務的設定*

### 在憑證過期時重新設定 {#certrenew}

憑證過期後，即不再受信任。 您無法更新已過期的憑證。若要新增憑證，請依照下列步驟操作。

1. 以管理員身分登入您的 [!DNL Experience Manager] 部署。按一 **[!UICONTROL 下「工具]** >安 **[!UICONTROL 全性]** >使 **[!UICONTROL 用者]**」。

1. 找到 **[!UICONTROL dam-update-service]** 使用者後按一下該使用者。按一下「**[!UICONTROL 金鑰存放區]**」索引標籤。

1. 刪除憑證已過期的現有 **[!UICONTROL similaritysearch]** 金鑰存放區。按一下&#x200B;**[!UICONTROL 「儲存並關閉」]**。

   ![刪除金鑰存放區中現有的similaritysearch項目，以新增安全性憑證](assets/smarttags_delete_similaritysearch_keystore.png)

   *圖：刪除金鑰存放區中現有的 `similaritysearch` 項目，以新增安全性憑證。*

1. 導覽至「 **[!UICONTROL 工具]** > **[!UICONTROL 雲端服務]** >舊 **[!UICONTROL 版雲端服務」]**。按一 **[!UICONTROL 下「資產智慧標籤]** >顯 **[!UICONTROL 示設定]** >可 **[!UICONTROL 用設定」]**。按一下所需的設定。

1. 若要下載公開憑證，請按一下「下載公開憑證以進行OAuth整合&#x200B;]**」。**[!UICONTROL 

1. 存取[https://console.adobe.io](https://console.adobe.io)並導覽至&#x200B;**[!UICONTROL 整合]**&#x200B;頁面上的現有智慧內容服務。 上傳新憑證。 如需詳細資訊，請參閱[建立Adobe開發人員控制台整合](#create-adobe-i-o-integration)中的指示。

## 建立Adobe開發人員控制台整合 {#create-adobe-i-o-integration}

若要使用智慧內容服務API，請在Adobe開發人員控制台中建立整合，以取得[!UICONTROL API金鑰](在Adobe開發人員控制台整合的[!UICONTROL 用戶端ID]欄位中產生)、 [!UICONTROL 技術帳戶ID]、 [!UICONTROL 組織ID]和[!UICONTROL 用戶端密碼]&lt;a10/&lt;A1/>智慧資產服務設定[!DNL Experience Manager]中的雲配置1/>。

1. 在瀏覽器中存取 [https://console.adobe.io](https://console.adobe.io/)。選取適當的帳戶，並確認相關聯的組織角色是系統管理員。

1. 以任何所需的名稱建立專案。按一下&#x200B;**[!UICONTROL 「新增 API」]**。

1. 在&#x200B;**[!UICONTROL 新增API]**&#x200B;頁面上，選取&#x200B;**[!UICONTROL Experience Cloud]**，然後選取&#x200B;**[!UICONTROL 智慧內容]**。 按一下&#x200B;**[!UICONTROL 下一步]**。

1. 選取&#x200B;**[!UICONTROL 「上傳您的公開金鑰」]**。提供從 [!DNL Experience Manager] 下載的憑證檔案。畫面上會顯示[!UICONTROL 已成功上傳公開金鑰]訊息。按一下&#x200B;**[!UICONTROL 下一步]**。

   [!UICONTROL 建立新的服務帳戶(JWT) 憑證]頁面會顯示剛設定的服務帳戶的公開金鑰。

1. 按一下&#x200B;**[!UICONTROL 下一步]**。

1. 在&#x200B;**[!UICONTROL 選取產品設定檔]**&#x200B;頁面上，選取&#x200B;**[!UICONTROL 「智慧內容服務」]**。按一下&#x200B;**[!UICONTROL 「儲存已設定的 API」]**。

   此時會出現一個頁面，顯示更多關於設定的資訊。請保持此頁面開啟，以便複製這些值並將其新增至[!DNL Experience Manager]中雲端組態的[!UICONTROL 資產智慧標籤服務設定]中，以設定智慧標籤。

   ![在「概覽」索引標籤中，您可以檢閱為整合提供的資訊。](assets/integration_details.png)

   *圖：Adobe開發人員控制台中整合的詳細資訊*

## 設定智慧內容服務 {#configure-smart-content-service}

若要設定整合，請使用Adobe開發人員控制台整合中的[!UICONTROL TECHNICAL ACCOUNT ID]、[!UICONTROL ORGANIZATION ID]、[!UICONTROL CLIENT SECRET]和[!UICONTROL CLIENT ID]欄位值。 建立智慧標籤雲端設定可讓您驗證[!DNL Experience Manager]部署中的API請求。

1. 在[!DNL Experience Manager]中，導覽至&#x200B;**[!UICONTROL 工具>Cloud Service>舊版Cloud Services]**&#x200B;以開啟[!UICONTROL Cloud Services]主控台。

1. 在&#x200B;**[!UICONTROL 資產智慧標籤]**&#x200B;下，開啟上述建立的設定。 在服務設定頁面上，按一下「**[!UICONTROL 編輯]**」。

1. 在「 **[!UICONTROL AEM Smart Content Service]** 」對話方塊中 **[!UICONTROL ，使用「服務URL」和「授權伺服器」欄位的預先填入值]****** 。

1. 對於[!UICONTROL Api金鑰]、[!UICONTROL 技術帳戶ID]、[!UICONTROL 組織ID]和[!UICONTROL 用戶端密碼]欄位，複製並使用在[Adobe開發人員控制台整合](#create-adobe-i-o-integration)中產生的下列值。

   | [!UICONTROL 資產智慧標記服務設定] | [!DNL Adobe Developer Console] 整合欄位 |
   |--- |--- |
   | [!UICONTROL API 金鑰] | [!UICONTROL 用戶端ID] |
   | [!UICONTROL 技術帳戶 ID] | [!UICONTROL 技術帳戶ID] |
   | [!UICONTROL 組織 ID] | [!UICONTROL 組織 ID] |
   | [!UICONTROL 用戶端密碼] | [!UICONTROL 用戶端密碼] |

## 驗證設定 {#validate-the-configuration}

完成配置後，使用JMX MBean驗證配置。 若要驗證，請遵循下列步驟。

1. 在`https://[aem_server]:[port]`訪問您的[!DNL Experience Manager]伺服器。

1. 前往&#x200B;**[!UICONTROL 工具>操作> Web控制台]**&#x200B;以開啟OSGi控制台。 按一下「**[!UICONTROL 主> JMX]**」。

1. 按一下&#x200B;**[!UICONTROL com.day.cq.dam.similaritysearch.internal.impl]**。 它會開啟&#x200B;**[!UICONTROL SimilitySearch雜項任務]**。

1. 按一下&#x200B;**[!UICONTROL validateConfigs()]**。 在&#x200B;**[!UICONTROL 驗證配置]**&#x200B;對話框中，按一下&#x200B;**[!UICONTROL 調用]**。

   驗證結果將顯示在同一對話框中。

## 在DAM更新資產工作流程中啟用智慧標籤（選用） {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. 在[!DNL Experience Manager]中，轉至&#x200B;**[!UICONTROL 工具]** > **[!UICONTROL 工作流]** > **[!UICONTROL 模型]**。

1. 在「 **[!UICONTROL 工作流模型]** 」頁面上，選擇「**[!UICONTROL DAM 更新資產]** 」工作流模型。

1. 按一下工具列中的&#x200B;**[!UICONTROL 「編輯」]**。

1. 展開「側面板」以顯示步驟。拖 **[!UICONTROL 曳DAM Workflow]**  (DAM工作流程) 區段中可用的智慧型標籤資產步驟，並將其置於&#x200B;**[!UICONTROL 「處理縮 圖」]**&#x200B;步驟之後 。

   ![在「DAM 更新資產」工作流程中，在處理縮圖步驟之後新增智慧標記資產步驟](assets/smart-tag-in-dam-update-asset-workflow.png)

   *圖：在「DAM 更新資產」工作流程中，在處理縮圖步驟之後新增智慧標記資產步驟。*

1. 在編輯模式中開啟步驟。在「 **[!UICONTROL 進階設定]**」下，確定已選取 **[!UICONTROL 「處理常式進階]** 」選項。

   ![設定DAM更新資產工作流程並新增智慧標籤步驟](assets/smart-tag-step-properties-workflow1.png)


   *圖：設定DAM更新資產工作流程並新增智慧標籤步驟*

1. 在「參 **[!UICONTROL 數]** 」頁籤中，如果希望工作流完成，即使自動標籤步驟失敗，請選擇「忽略錯誤 **** 」。

   ![設定DAM更新資產工作流程以新增智慧標籤步驟並選取處理常式進階](assets/smart-tag-step-properties-workflow2.png)


   *圖：設定DAM更新資產工作流程以新增智慧標籤步驟並選取處理常式進階*

   若無論是否對資料夾啟用智慧標記，都要在資產上傳時標記資產，請選取&#x200B;**[!UICONTROL 「忽略智慧標記旗標」]**。

   ![設定DAM更新資產工作流程以新增智慧標籤步驟，並選取「忽略智慧標籤旗標」](assets/smart-tag-step-properties-workflow3.png)


   *圖：設定DAM更新資產工作流程以新增智慧標籤步驟，並選取「忽略智慧標籤旗標」*

1. 按一下&#x200B;**[!UICONTROL 「確定」]**&#x200B;關閉程序步驟，然後儲存工作流程。

>[!MORELIKETHIS]
>
>* [管理智慧標籤](managing-smart-tags.md)
* [智慧標籤的概觀及訓練方法](enhanced-smart-tags.md)
* [訓練智慧內容服務的准則和規則](smart-tags-training-guidelines.md)


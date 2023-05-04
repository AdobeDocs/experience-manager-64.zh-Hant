---
title: 使用智慧內容服務設定資產標籤。
description: 了解如何在中設定智慧標籤和增強智慧標籤 [!DNL Adobe Experience Manager]，使用智慧內容服務。
contentOwner: AG
feature: Smart Tags,Tagging
role: Admin
exl-id: 11c5dd92-f824-41d2-9ab2-b32bdeae01b6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1340'
ht-degree: 31%

---

# 使用智慧內容服務設定資產標籤 {#configure-asset-tagging-using-the-smart-content-service}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

您可以整合 [!DNL Adobe Experience Manager] 與智慧內容服務搭配使用 [!DNL Adobe Developer Console]. 使用此配置從內訪問智慧內容服務 [!DNL Experience Manager].

>[!NOTE]
>
>* 新功能不再提供智慧內容服務 [!DNL Experience Manager Assets] 內部部署客戶。 已啟用此功能的現有內部部署客戶，可繼續使用智慧內容服務。
>* 智慧內容服務適用於現有 [!DNL Experience Manager Assets] 已啟用此功能的Managed Services客戶。
>* 新增 [!DNL Experience Manager Assets] Managed Services客戶可以依照本文所述的指示來設定智慧內容服務。


文章詳細說明設定智慧內容服務所需的下列主要工作。 在後端， [!DNL Experience Manager] 伺服器會以驗證您的服務憑證 [!DNL Adobe Developer Console] 網關，再將您的請求轉送至智慧內容服務。

1. [建立智慧內容服務](#obtain-public-certificate) 配置 [!DNL Experience Manager] 來產生公開金鑰。 [取得公開憑證](#obtain-public-certificate)以進行 OAuth 整合。

1. [在 Adobe 開發人員控制台中建立整合](#create-adobe-i-o-integration)，並上傳產生的公開金鑰。

1. [配置部署](#configure-smart-content-service) 使用API金鑰和其他憑證 [!DNL Adobe Developer Console].

1. [測試設定](#validate-the-configuration)。

1. （可選） [在資產上傳上啟用自動標籤](#enable-smart-tagging-in-the-update-asset-workflow-optional).

## 必備條件 {#prerequisites}

使用智慧內容服務之前，請確定下列項目以在上建立整合 [!DNL Adobe Developer Console]:

* Adobe ID 帳戶具有組織的管理員權限。

* 您的組織已啟用智慧內容服務。

除了上述功能，若要啟用增強智慧標籤，請同時安裝最新的 [Experience Manager服務包](https://helpx.adobe.com/tw/experience-manager/aem-releases-updates.html).

## 建立智慧內容服務設定以取得公開憑證 {#obtain-public-certificate}

公開憑證可讓您驗證設定檔，位於 [!DNL Adobe Developer Console].

1. 在 [!DNL Experience Manager] 使用者介面，存取 **[!UICONTROL 工具]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL 舊版Cloud Services]**.

1. 在「Cloud Services」頁面中，按一下 **[!UICONTROL 立即配置]** 在 **[!UICONTROL 資產智慧標籤]**.

1. 在 **[!UICONTROL 建立配置]** 對話框，指定智慧標籤配置的標題和名稱。 按一下&#x200B;**[!UICONTROL 建立]**。

1. 在 **[!UICONTROL AEM Smart Content Service]** 對話框，請使用以下值：

   **[!UICONTROL 服務 URL]**: `https://smartcontent.adobe.io/<region where your Experience Manager author instance is hosted>`

   例如， `https://smartcontent.adobe.io/apac`. 您可以指定 `na`, `emea`，或 `apac` 作為托管Experience Manager製作例項的地區。

   >[!NOTE]
   >
   >如果在2022年9月01日之前布建了Experience Manager托管服務，請使用以下服務URL:
   >`https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL 授權伺服器]**: `https://ims-na1.adobelogin.com`

   暫時將其他欄位留空（稍後將提供）。 按一下&#x200B;**[!UICONTROL 「確定」]**。

   ![Experience Manager智慧內容服務對話方塊以提供內容服務URL](assets/aem_scs.png)


   *圖：提供內容服務URL的智慧型內容服務對話方塊*

   >[!NOTE]
   >
   >URL提供為 [!UICONTROL 服務URL] 無法透過瀏覽器存取，並產生404錯誤。 設定可正常運作，且值與 [!UICONTROL 服務URL] 參數。 有關整體服務狀態和維護計畫，請參閱 [https://status.adobe.com](https://status.adobe.com).

1. 按一下 **[!UICONTROL 下載公開憑證以進行OAuth整合]**，並下載公開憑證檔案 `AEM-SmartTags.crt`.

   ![為智慧標籤服務建立的設定的表示](assets/smart-tags-download-public-cert.png)


   *圖：智慧標籤服務的設定*

### 在憑證過期時重新設定 {#certrenew}

憑證過期後，即不再受信任。 您無法更新已過期的憑證。若要新增憑證，請依照下列步驟操作。

1. 以管理員身分登入您的 [!DNL Experience Manager] 部署。按一 **[!UICONTROL 下「工具]** >安 **[!UICONTROL 全性]** >使 **[!UICONTROL 用者]**」。

1. 找到 **[!UICONTROL dam-update-service]** 使用者後按一下該使用者。按一下 **[!UICONTROL 金鑰存放區]** 標籤。

1. 刪除憑證已過期的現有 **[!UICONTROL similaritysearch]** 金鑰存放區。按一下&#x200B;**[!UICONTROL 「儲存並關閉」]**。

   ![刪除金鑰存放區中現有的similaritysearch項目，以新增安全性憑證](assets/smarttags_delete_similaritysearch_keystore.png)

   *圖：刪除金鑰存放區中現有的 `similaritysearch` 項目，以新增安全性憑證。*

1. 導覽至「 **[!UICONTROL 工具]** > **[!UICONTROL 雲端服務]** >舊 **[!UICONTROL 版雲端服務」]**。按一 **[!UICONTROL 下「資產智慧標籤]** >顯 **[!UICONTROL 示設定]** >可 **[!UICONTROL 用設定」]**。按一下所需的設定。

1. 若要下載公開憑證，請按一下 **[!UICONTROL 下載公開憑證以進行OAuth整合]**.

1. 存取 [https://console.adobe.io](https://console.adobe.io) 並導覽至 **[!UICONTROL 整合]** 頁面。 上傳新憑證。 如需詳細資訊，請參閱 [建立Adobe Developer Console整合](#create-adobe-i-o-integration).

## 建立Adobe Developer Console整合 {#create-adobe-i-o-integration}

若要使用智慧內容服務API，請在Adobe Developer Console中建立整合以取得 [!UICONTROL API金鑰] (產生於 [!UICONTROL 用戶端ID] Adobe Developer主控台整合欄位), [!UICONTROL 技術帳戶ID], [!UICONTROL 組織ID]，和 [!UICONTROL 用戶端密碼] for [!UICONTROL 資產智慧標籤服務設定] 在 [!DNL Experience Manager].

1. 在瀏覽器中存取 [https://console.adobe.io](https://console.adobe.io/)。選取適當的帳戶，並確認相關聯的組織角色是系統管理員。

1. 以任何所需的名稱建立專案。按一下&#x200B;**[!UICONTROL 「新增 API」]**。

1. 在 **[!UICONTROL 新增API]** 頁面，選取 **[!UICONTROL Experience Cloud]** 然後選取 **[!UICONTROL 智慧內容]**. 按一下&#x200B;**[!UICONTROL 下一步]**。

1. 選取&#x200B;**[!UICONTROL 「上傳您的公開金鑰」]**。提供從 [!DNL Experience Manager] 下載的憑證檔案。畫面上會顯示[!UICONTROL 已成功上傳公開金鑰]訊息。按一下&#x200B;**[!UICONTROL 下一步]**。

   [!UICONTROL 建立新的服務帳戶(JWT) 憑證]頁面會顯示剛設定的服務帳戶的公開金鑰。

1. 按一下&#x200B;**[!UICONTROL 下一步]**。

1. 在&#x200B;**[!UICONTROL 選取產品設定檔]**&#x200B;頁面上，選取&#x200B;**[!UICONTROL 「智慧內容服務」]**。按一下&#x200B;**[!UICONTROL 「儲存已設定的 API」]**。

   此時會出現一個頁面，顯示更多關於設定的資訊。請保持此頁面開啟，以複製這些值並將其新增至 [!UICONTROL 資產智慧標籤服務設定] 在 [!DNL Experience Manager] 來設定智慧標籤。

   ![在「概覽」索引標籤中，您可以檢閱為整合提供的資訊。](assets/integration_details.png)

   *圖：Adobe Developer Console整合的詳細資訊*

## 設定智慧內容服務 {#configure-smart-content-service}

若要設定整合，請使用 [!UICONTROL 技術帳戶ID], [!UICONTROL 組織ID], [!UICONTROL 用戶端密碼]，和 [!UICONTROL 用戶端ID] Adobe Developer控制台整合中的欄位。 建立智慧標籤雲端設定可讓驗證 [!DNL Experience Manager] 部署。

1. 在 [!DNL Experience Manager]，導覽至 **[!UICONTROL 工具>Cloud Service>舊版Cloud Services]** 開啟 [!UICONTROL Cloud Services] 控制台。

1. 在 **[!UICONTROL 資產智慧標籤]**，開啟上述建立的設定。 在服務設定頁面上，按一下 **[!UICONTROL 編輯]**.

1. 在「 **[!UICONTROL AEM Smart Content Service]** 」對話方塊中 **[!UICONTROL ，使用「服務URL」和「授權伺服器」欄位的預先填入值]****** 。

1. 對於欄位 [!UICONTROL Api金鑰], [!UICONTROL 技術帳戶ID], [!UICONTROL 組織ID]，和 [!UICONTROL 用戶端密碼]，複製並使用中產生的下列值 [Adobe Developer Console整合](#create-adobe-i-o-integration).

   | [!UICONTROL 資產智慧標記服務設定] | [!DNL Adobe Developer Console] 整合欄位 |
   |--- |--- |
   | [!UICONTROL API 金鑰] | [!UICONTROL 用戶端ID] |
   | [!UICONTROL 技術帳戶 ID] | [!UICONTROL 技術帳戶ID] |
   | [!UICONTROL 組織 ID] | [!UICONTROL 組織 ID] |
   | [!UICONTROL 用戶端密碼] | [!UICONTROL 用戶端密碼] |

## 驗證設定 {#validate-the-configuration}

完成配置後，使用JMX MBean驗證配置。 若要驗證，請遵循下列步驟。

1. 存取 [!DNL Experience Manager] 伺服器 `https://[aem_server]:[port]`.

1. 前往 **[!UICONTROL 「工具」>「操作」>「Web控制台」]** 來開啟OSGi主控台。 按一下 **[!UICONTROL 主要> JMX]**.

1. 按一下 **[!UICONTROL com.day.cq.dam.similaritysearch.internal.impl]**. 開啟 **[!UICONTROL 相似性搜索其他任務]**.

1. 按一下 **[!UICONTROL validateConfigs()]**. 在 **[!UICONTROL 驗證配置]** 對話框，按一下 **[!UICONTROL 叫用]**.

   驗證結果將顯示在同一對話框中。

## 在DAM更新資產工作流程中啟用智慧標籤（選用） {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. 在 [!DNL Experience Manager]，前往 **[!UICONTROL 工具]** > **[!UICONTROL 工作流程]** > **[!UICONTROL 模型]**.

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
>* [智慧標籤的概觀及訓練方法](enhanced-smart-tags.md)
>* [訓練智慧內容服務的准則和規則](smart-tags-training-guidelines.md)


---
title: 使用智慧型內容服務設定AI型標籤
description: 瞭解如何使用智慧型內容服務，在AEM中設定智慧型標籤和增強的智慧型標籤。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 90d39315207129aa4fc616e6fffb4bad5c450a7b

---


# 使用智慧型內容服務設定資產標籤 {#configure-asset-tagging-using-the-smart-content-service}

瞭解如何使用智慧型內容服務，在AEM中設定智慧型標籤和增強的智慧型標籤。

您可以將Adobe Experience Manager(AEM)與Smart Content Service整合。 使用此設定從AEM存取Smart Content Service，並自動標籤您的影像。

文章詳細說明了配置Smart Content service所需的下列主要工作。 在後端，AEM伺服器會先使用Adobe IO閘道驗證您的服務認證，然後再將您的請求轉送至Smart Content Service。

1. 在AEM中建立Smart Content service設定以產生公開金鑰。 取得OAuth整合的公開憑證。
1. 在Adobe I/O中建立整合，並上傳產生的公開金鑰。
1. 使用API金鑰和Adobe I/O的其他認證來設定您的AEM例項。
1. （可選）在資產上傳時啟用自動標籤。

## 必備條件 {#prerequisites}

在您使用智慧型內容服務之前，請確定以下各項以建立Adobe I/O整合：

* 具有組織管理員權限的Adobe ID帳戶。
* 您的組織已啟用智慧型內容服務。

除了上述功能外，若要啟用「增強智慧型標籤」，請另外安裝最新 [的AEM Service Pack](https://helpx.adobe.com/experience-manager/aem-releases-updates.html)。

## 取得公開憑證 {#obtain-public-certificate}

公開憑證可讓您在Adobe I/O上驗證您的個人檔案。

1. From the AEM user interface, tap the AEM logo, and go to **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy Cloud Services]**.

1. 在「雲端服務」頁面中，點選/按一下「 **[!UICONTROL 資產智慧標籤]** 」 **[!UICONTROL 下的「立即設定」]**。
1. 在「建 **[!UICONTROL 立設定]** 」對話方塊中，指定「智慧標籤」設定的標題和名稱。 點選／按一下「 **[!UICONTROL 建立]**」。
1. 在「 **[!UICONTROL AEM智慧型內容服務]** 」對話方塊中，使用下列值：

   **[!UICONTROL 服務 URL]**: `https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL 授權伺服器]**: `https://ims-na1.adobelogin.com`

   現在將其他欄位留空（稍後將提供）。 點選／按一下「 **[!UICONTROL 確定]**」。

   ![AEM Smart Content Service對話方塊，以提供內容服務URL](assets/aem_scs.png)

   >[!NOTE]
   >
   >以服務URL提供 [!UICONTROL 的URL] 無法透過瀏覽器存取，並產生404錯誤。 設定可正常運作，且與「服務URL」參 [!UICONTROL 數值相同] 。 如需Adobe I/O服務狀態和維護排程的整體資訊，請參 [閱https://status.adobe.com](https://status.adobe.com)。

1. 點選／按一 **[!UICONTROL 下「下載OAuth整合的公用憑證]**」，然後下載公用憑證檔案 `AEM-SmartTags.crt`。

   ![為智慧標籤服務建立的設定的表示](assets/download_link.png)

## 建立Adobe I/O整合 {#create-adobe-i-o-integration}

若要使用Smart Content Service API，請在Adobe I/O中建立整合，以產生API金鑰、技術帳戶ID、組織ID和用戶端密碼。

1. 存取 [https://console.adobe.io](https://console.adobe.io/)。
1. 從「整 **[!UICONTROL 合]** 」頁面中，選取您的組織。
1. 點選／按一下「 **[!UICONTROL 新增整合」]**。
1. 在「建 **[!UICONTROL 立新整合」頁面]** ，選取「 **[!UICONTROL 存取API」]**。 點選/按一下「 **[!UICONTROL 繼續]**」。
1. 在「 **[!UICONTROL Experience Cloud]**」下方，選取「 **[!UICONTROL 智慧型內容」]**。點選/按一下「 **[!UICONTROL 繼續]**」。

   ![建立新整合時，請從可用選項中選取「Experience cloud下的智慧型內容」](assets/smart_content.png)

1. 在下一頁，選擇「新 **[!UICONTROL 增整合」]**。 點選/按一下「 **[!UICONTROL 繼續]**」。
1. 在「整 **[!UICONTROL 合詳細資訊]** 」頁面上，指定整合閘道的名稱並新增說明。
1. 在公 **[!UICONTROL 開金鑰憑證中]**，上 `AEM-SmartTags.crt` 傳您先前下載的檔案。
1. 點選／按一下「 **[!UICONTROL 建立整合」]**。
1. 若要檢視整合資訊，請點選／按一下「 **[!UICONTROL 繼續」以取得整合詳細資訊]**。

   ![在「概述」索引標籤中，您可以檢閱為整合提供的資訊。](assets/integration_details.png)

## 設定智慧型內容服務 {#configure-smart-content-service}

若要設定整合，請使用Adobe I/O整合中「技術帳戶ID」、「組織ID」、「用戶端密碼」、「授權伺服器」和「API金鑰」欄位的值。 建立智慧型標籤雲端設定可讓AEM例項的API要求驗證。

1. 從AEM使用者介面，點選／按一下AEM標誌。 導覽至「 **[!UICONTROL 工具>雲端服務>舊版雲端服務]** 」以開啟雲端服務主控台。
1. 在「資 **[!UICONTROL 產智慧標籤]**」下，開啟上述建立的設定。 在服務設定頁面上，按一下「 **[!UICONTROL 編輯]**」。
1. 在「 **[!UICONTROL AEM Smart Content Service]** 」對話方塊中 **[!UICONTROL ，使用「服務URL」和「授權伺服器」欄位的預先填入值]****** 。
1. 對於「 API金鑰」、「 Technical Account Id」、「 Organization Id」和「Client Secret 」欄位，請使用上述產生的值。

## 驗證配置 {#validate-the-configuration}

完成配置後，可使用JMX MBean來驗證配置。 若要驗證，請遵循下列步驟。

1. 在AEM中，若要開啟OSGi主控台，請按一 **[!UICONTROL 下「工具>作業> Web Console]**」。 按一 **[!UICONTROL 下「主要> JMX]**」。
1. 按一 **[!UICONTROL 下com.day.cq.dam.similaritysearch.internal.impl]**。 它會開啟「 **[!UICONTROL SimiliarySearch雜項工作」。]**
1. 按一 **[!UICONTROL 下validateConfigs()]**。 在「驗證 **[!UICONTROL 配置」對話]** ，按一下 **[!UICONTROL 調用]**。

   驗證結果會顯示在相同的對話方塊中。

## 在DAM更新資產工作流程中啟用智慧標籤（可選） {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. 從AEM使用者介面，點選／按一下AEM標誌，然後前往「工具>工 **[!UICONTROL 作流程>模型」]**。
1. 在「工 **[!UICONTROL 作流模型]** 」頁面上，選擇 **** 「DAM更新資產」工作流模型。
1. 從工具列點選/ **[!UICONTROL 按一下]** 「編輯」。
1. 展開「側面板」以顯示步驟。拖 **[!UICONTROL 曳DAM Workflow]**  (DAM工作流程) 區段中可用的智慧型標籤資產步驟，並將其置於「處理縮 **[!UICONTROL 圖」步驟之後]** 。

   ![在「DAM更新資產」工作流程中，在流程縮圖步驟之後新增智慧型標籤資產步驟](assets/chlimage_1-105.png)

1. 在編輯模式中開啟步驟。在「 **[!UICONTROL 進階設定]**」下，確定已選 **[!UICONTROL 取「處理常式進階]** 」選項。

   ![chlimage_1-106](assets/chlimage_1-106.png)

1. 在「參 **[!UICONTROL 數]** 」頁籤中，如果希望工作流完成，即使自動標籤步驟失敗，請選擇「忽略錯誤 **** 」。

   ![chlimage_1-107](assets/chlimage_1-107.png)

   若要在資產上傳時標籤資產，而不論資料夾上是否啟用智慧型標籤，請選取「忽略智慧 **[!UICONTROL 型標籤標籤」]**。

   ![chlimage_1-108](assets/chlimage_1-108.png)

1. 點選／按一 **[!UICONTROL 下「確定]** 」以關閉流程步驟，然後儲存工作流程。

>[!MORELIKETHIS]
>
>* [瞭解AEM資產中的智慧型標籤](https://helpx.adobe.com/experience-manager/kt/assets/using/smart-tags-feature-video-understand.html)
>* [搭配AEM資產使用智慧標籤](https://helpx.adobe.com/experience-manager/kt/assets/using/smart-tags-feature-video-use.html)
>* [搭配AEM資產使用增強的智慧標籤](https://helpx.adobe.com/experience-manager/kt/assets/using/enhanced-smart-tags-feature-video-use.html)
>* [在AEM Assets中設定增強的智慧標籤](https://helpx.adobe.com/experience-manager/kt/assets/using/enhanced-smart-tags-technical-video-setup.html)


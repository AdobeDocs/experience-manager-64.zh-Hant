---
title: 為您的數位資產加上浮水印
description: 了解如何使用浮水印功能為資產加上數位浮水印。
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: ed01143c-b516-44f8-aceb-ad2e3f0106b2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 4%

---

# 為您的數位資產加上浮水印 {#watermarking}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

[!DNL Adobe Experience Manager Assets] 可讓您為資產加上數位浮水印，協助使用者驗證資產的真實性和版權所有權。 [!DNL Experience Manager Assets] 支援在PNG和JPEG檔案上用作浮水印的文本。

Adobe Experience Manager Assets可讓您為影像加上數位浮水印，協助使用者驗證資產的真實性和版權所有權。 [!DNL Experience Manager] Assets支援在PNG和JPEG檔案上作為浮水印使用的文字。

若要對資產套用浮水印，請在 [!UICONTROL DAM更新資產] 工作流程。

1. 存取 [!DNL Experience Manager] 使用者介面，然後前往 **[!UICONTROL 工具]** > **[!UICONTROL 工作流程]** > **[!UICONTROL 模型]**.
1. 從「工作流模型」頁中，選擇 **[!UICONTROL DAM更新資產]** 工作流程，按一下 **[!UICONTROL 編輯]**.

1. 從側面板拖動 **[!UICONTROL 添加浮水印]** 步驟並將其新增至 [!UICONTROL DAM更新資產] 工作流程。

   ![在DAM更新資產工作流程中拖曳新增浮水印步驟](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >放置 [!UICONTROL 添加浮水印] 在 [!UICONTROL 處理縮圖] 步驟。

1. 開啟 **[!UICONTROL 添加浮水印]** 顯示其屬性的步驟。
1. 在 **[!UICONTROL 引數]** 頁簽，在各種欄位中指定有效值，包括文本、字型類型、大小、顏色、位置、方向等。 若要確認變更，請按一下 **[!UICONTROL 完成]**.

   ![在「資產」的「新增浮水印」步驟中提供引數](assets/arguments_add_watermark_aem_assets.png)

1. 使用浮水印 **[!UICONTROL 步驟儲存DAM更新資產]** (Dam Update Asset)工作流程。
1. 從 [!DNL Experience Manager] 使用者介面上傳範例資產。 浮水印會隨字型大小、顏色等一起出現在您在上述步驟中設定的位置。

要以寫程式方式或使用動態資訊為PDF文檔加水印，請考慮使用 [[!DNL Experience Manager] 檔案服務](/help/forms/using/overview-aem-document-services.md) 提供。

## 提示和限制 {#tips-limitations}

* 僅支援基於文本的水印。 影像不會作為水印使用，即使您在建立 [!UICONTROL 添加水印過程].
* 僅支援對PNG和JPEG檔案加上水印。 其他資產格式不會加上浮水印。

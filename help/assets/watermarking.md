---
title: 將浮水印新增至您的數位資產
description: 瞭解如何使用浮水印功能將數位水印新增至資產。
contentOwner: AG
feature: Asset Management
role: Business Practitioner,Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 3%

---


# 浮水印您的數位資產{#watermarking}

[!DNL Adobe Experience Manager Assets] 可讓您在資產中加入數位浮水印，協助使用者驗證資產的真實性和版權所有權。[!DNL Experience Manager Assets] 支援在PNG和JPEG檔案上用作浮水印的文字。

Adobe Experience Manager(AEM)Assets可讓您在影像中加入數位浮水印，協助使用者驗證資產的真實性和版權所有權。 AEM Assets支援在PNG和JPEG檔案上用作浮水印的文字。

若要能夠套用資產上的浮水印，請在[!UICONTROL DAM更新資產]工作流程中新增浮水印步驟。

1. 訪問[!DNL Experience Manager]用戶介面，並轉到&#x200B;**[!UICONTROL 工具]** > **[!UICONTROL 工作流]** > **[!UICONTROL 模型]**。
1. 從「工作流模型」頁中，選擇&#x200B;**[!UICONTROL DAM更新資產]**&#x200B;工作流，然後按一下&#x200B;**[!UICONTROL 編輯]**。

1. 從側面板拖曳「新增浮水印」步驟，並將其新增至「DAM更新資產」工作流程。****

   ![在DAM更新資產工作流程中拖曳新增浮水印步驟](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >將[!UICONTROL Add Watermark]步驟置於[!UICONTROL Process Thumbnail]步驟之前的任意位置。

1. 開啟&#x200B;**[!UICONTROL 新增浮水印]**&#x200B;步驟以顯示其屬性。
1. 在&#x200B;**[!UICONTROL 參數]**&#x200B;標籤中，在各種欄位中指定有效值，包括文字、字型類型、大小、顏色、位置、方向等。 要確認更改，請按一下&#x200B;**[!UICONTROL Done]**。

   ![在「資產」的「新增浮水印」步驟中提供引數](assets/arguments_add_watermark_aem_assets.png)

1. 使用浮水印 **[!UICONTROL 步驟儲存DAM更新資產]** (Dam Update Asset)工作流程。
1. 從使用者AEM介面上傳範例資產。 浮水印會以字型大小、顏色等顯示在您在上述步驟中設定的位置。

若要以程式設計方式或使用動態資訊加上PDF檔案水印，請考慮使用[AEM Document Services](/help/forms/using/overview-aem-document-services.md)產品。

## 提示和限制{#tips-limitations}

* 僅支援文字浮水印。 雖然您可以在建立[!UICONTROL 新增浮水印處理]時上傳影像，但影像不會當做浮水印使用。
* 僅支援PNG和JPEG檔案加浮水印。 其他資產格式不會浮水印。

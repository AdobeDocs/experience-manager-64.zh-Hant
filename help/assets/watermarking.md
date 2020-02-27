---
title: 加上影像浮水印
description: 使用浮水印功能，將數位水印新增至PNG和JPEG影像。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0e0e2aa693c30c8e1ef1033b936b82d83e5b348e

---


# 浮水印您的資產 {#watermarking}

Adobe Experience Manager(AEM)Assets可讓您在影像中新增數位浮水印，協助使用者驗證資產的真實性和版權所有權。 AEM Assets支援將文字用作PNG和JPEG檔案上的浮水印。

若要能夠套用浮水印至資產，請在「 [!UICONTROL DAM更新資產] 」工作流程中新 [!UICONTROL 增浮水印步驟] 。

1. Tap the AEM logo, and go to **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. 從「工作流模型」頁面中，選擇「 **[!UICONTROL DAM更新資產」工作流]** ，然後按一下「 **[!UICONTROL 編輯」]**。

1. 從側面板拖曳「新增浮水印 **[!UICONTROL 」步驟，並將其新增至]** DAM更新資產工作流程  。

   ![在DAM更新資產工作流程中新增浮水印步驟](assets/add_watermark_step_aem_assets.png)

   >[!NOTE]
   >
   >將「新增 [!UICONTROL 浮水印] 」步驟放在「處理縮 [!UICONTROL 圖」步驟之前] 。

1. 開啟「 **[!UICONTROL 新增浮水印]** 」步驟以顯示其屬性。
1. 在「參 **[!UICONTROL 數]** 」標籤中，在各種欄位中指定有效值，包括文字、字型類型、大小、顏色、位置、方向等。 若要確認變更，請點選／按一下「完成」圖示。

   ![在「資產」的「新增浮水印」步驟中提供引數](assets/arguments_add_watermark_aem_assets.png)

1. 使用浮水印 **[!UICONTROL 步驟儲存DAM更新資產]** (Dam Update Asset)工作流程。
1. 從AEM使用者介面上傳範例資產。 浮水印會以字型大小、顏色等顯示在您在上述步驟中設定的位置。

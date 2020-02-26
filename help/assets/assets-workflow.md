---
title: 套用工作流程來處理您的數位資產
description: 瞭解如何將工作流程套用至AEM Assets中的資產、檔案夾和系列，以處理您的數位資產。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# 將工作流程套用至資產 {#applying-workflows-to-assets}

將工作流程套用至數位資產與網站頁面相同。 如需如何在AEM中建立和使用工作流程的完整指南，請參閱「啟 [動工作流程」](../sites-authoring/workflows-participating.md)。

在數位資產中使用工作流程來啟用資產或建立浮水印。 資產的許多工作流程都會自動開啟。 例如，編輯影像後自動建立轉譯的工作流程會自動開啟。

如果傳統UI中的工作流程在觸控式UI中不可用，例如「要求啟用」和「要求停用」，請參閱「在觸控式UI中 [提供工作流程模型](../sites-developing/workflows-models.md#make-workflow-models-available-in-touchui)」。

## 套用工作流程至AEM資產 {#applying-a-workflow-to-an-aem-asset}

如需將工作流程套用至AEM資產的詳細資訊，請參 [閱「在資產上啟動工作流程」](managing-assets-touch-ui.md#starting-a-workflow-on-an-asset)。

## 將工作流程套用至多個資產 {#applying-a-workflow-to-multiple-assets}

1. 從「資產」主控台，導覽至您要啟動工作流程的資產所在的位置，然後選取資產。
1. 按一下「GlobalNav」圖示，然後從選單中選 **[!UICONTROL 擇「時間軸]** 」以顯示時間軸。

   ![chlimage_1-136](assets/chlimage_1-136.png)

1. Click the **[!UICONTROL Actions]** (arrow) icon at the bottom.

   ![chlimage_1-137](assets/chlimage_1-137.png)

1. 按一下「 **[!UICONTROL 開始工作流程]**」。
1. In the **[!UICONTROL Start Workflow]** dialog, select a workflow model from the list.

   ![chlimage_1-138](assets/chlimage_1-138.png)

1. （可選）指定工作流的標題，可用來參考工作流實例。
1. 按一 **[!UICONTROL 下「開始]** 」，然後按一 **[!UICONTROL 下對話方塊中的「確認]** 」。工作流程會在您選取的所有資產上執行。

## 將工作流程套用至多個檔案夾 {#applying-a-workflow-to-multiple-folders}

將工作流程套用至多個檔案夾的程式，類似於將工作流程套用至多個資產的程式。 在「資產」主控台中選取資料夾，並執行「將工作流程套用至多 [個資產」程式的步驟2-7](assets-workflow.md#applying-a-workflow-to-multiple-assets)。

## 將工作流程套用至系列 {#applying-a-workflow-to-a-collection}

如需將工作流程套用至系列的詳細資訊，請參 [閱在系列上執行工作流程](managing-collections-touch-ui.md#running-a-workflow-on-a-collection)。

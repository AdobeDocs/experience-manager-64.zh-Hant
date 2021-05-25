---
title: 將翻譯雲服務應用於資料夾
description: 將翻譯雲服務應用於資料夾
contentOwner: AG
feature: 轉換
role: Administrator
exl-id: 87883a3f-db95-41f4-b0aa-cdaeb7e6f555
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 55%

---

# 將翻譯雲服務應用於資料夾{#applying-translation-cloud-services-to-folders}

Adobe Experience Manager(AEM)可讓您從所選翻譯提供者取得雲端型翻譯服務，確保資產能根據您的需求進行翻譯。

您可以直接將翻譯雲端服務套用至資產資料夾，以便在翻譯工作流程中使用。

## 應用翻譯服務{#applying-the-translation-services}

直接將翻譯雲端服務套用至您的資產資料夾，無需在您建立或更新翻譯工作流程時設定翻譯服務。

1. 從「資產」UI中，選取您要套用翻譯服務的資料夾。
1. 在工具列中，按一下/點選「屬 **[!UICONTROL 性」圖示]** ，以顯示「資 **** 料夾屬性」頁面。

   ![chlimage_1-215](assets/chlimage_1-215.png)

1. 導覽至「 **[!UICONTROL 雲端服務]** 」標籤。
1. 從「Cloud Service配置」清單中，選擇所需的翻譯提供程式。 例如，如果要從Microsoft獲得翻譯服務，請選擇&#x200B;**[!UICONTROL Microsoft Translator]**。

   ![chlimage_1-216](assets/chlimage_1-216.png)

1. 選擇翻譯提供程式的連接器。

   ![chlimage_1-217](assets/chlimage_1-217.png)

1. 在工具列中，按一下/點選「 **[!UICONTROL 儲存]**」，然後按一下「確定 **** 」以關閉對話方塊。轉譯服務會套用至資料夾。

## 應用自定義翻譯連接器{#applying-custom-translation-connector}

如果要為要用於翻譯工作流的翻譯服務應用自定義連接器。若要套用自訂連接器，請先從「封裝管理員」安裝連接器。然後，從雲端服務主控台設定連接器。在您設定連接器後，「套用轉譯服務」中所述的「雲端服務」標籤中的連接器清 [單中會顯示此連接器](transition-cloud-services.md#applying-the-translation-services)。在您應用自定義連接器並運行翻譯工作流後，翻譯項目的「 **[!UICONTROL Translation Summary]** 」 (翻譯摘要) 表徵圖會在heads **[!UICONTROL Provider]** and **[!UICONTROL Method下顯示連接器詳細資訊]**。

1. 從「封裝管理器」安裝連接器。
1. 按一下/點選AEM標誌，然後導覽至「**[!UICONTROL 工具>部署>Cloud Services」]**。
1. 在「雲端服務」頁面的「 **[!UICONTROL 協力廠商服務]** 」下，找 **[!UICONTROL 出您安裝的連接器]** 。

   ![chlimage_1-218](assets/chlimage_1-218.png)

1. 按一下/點選&#x200B;**[!UICONTROL 立即設定]**&#x200B;連結以開啟&#x200B;**[!UICONTROL 建立設定]**&#x200B;對話方塊。

   ![chlimage_1-219](assets/chlimage_1-219.png)

1. 指定連接器的標題和名稱，然後按一下/點選「建 **[!UICONTROL 立」]**。自訂連接器位於「套用轉譯服務」步驟5中所述「 **[!UICONTROL 雲端服務]** 」標籤的連 [接器清單中](#applying-the-translation-services)。
1. 在套用自訂連接器後，執行「 [建立翻譯專案](translation-projects.md) 」中所述的任何翻譯工作流程。驗證「項目」控制台中翻譯項 **[!UICONTROL 目的「翻譯摘要]** 」表徵圖中連接器的詳 **[!UICONTROL 細資訊]** 。

   ![chlimage_1-220](assets/chlimage_1-220.png)

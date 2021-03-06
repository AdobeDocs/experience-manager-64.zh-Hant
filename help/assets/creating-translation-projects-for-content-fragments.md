---
title: 建立內容片段的翻譯專案
seo-title: Creating Translation Projects for Content Fragments
description: 了解如何翻譯內容片段。
seo-description: Learn how to translate content fragments.
uuid: 23176e70-4003-453c-af25-6499a5ed3f6d
contentOwner: heimoz
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: managing-assets
content-type: reference
discoiquuid: d2decc31-a04b-4a8e-bb19-65f21cf7107e
exl-id: 4b9fd241-82db-466e-95bd-6d212717801d
feature: Content Fragments
role: User
source-git-commit: 8948bca63f1f5ec9d94ede2fb845ed01b4e23333
workflow-type: tm+mt
source-wordcount: '968'
ht-degree: 0%

---

# 建立內容片段的翻譯專案 {#creating-translation-projects-for-content-fragments}

除了資產外，Adobe Experience Manager(AEM)資產支援[內容片段](content-fragments.md)（包括變數）的語言復本工作流程。 在內容片段上執行語言副本工作流程不需要額外的最佳化。 在每個工作流程中，會傳送整個內容片段以供翻譯。

您可以在內容片段上執行的工作流程類型，與您針對資產執行的工作流程類型完全相同。 此外，每個工作流程類型中可用的選項都符合資產對應工作流程類型底下可用的選項。

您可以在內容片段上執行下列語言副本工作流程類型：

**建立和翻譯**

在此工作流程中，要翻譯的內容片段會複製到您要翻譯之語言的語言根目錄。 此外，系統會根據您選擇的選項，在「專案」主控台中為內容片段建立翻譯專案。 視設定而定，翻譯專案可以手動啟動，或在建立翻譯專案後立即自動執行。

**更新語言副本**

當更新或修改源內容片段時，需要重新換算相應的地區/語言特定內容片段。 更新語言副本工作流轉換附加的內容片段組，並將其包含在特定地區的語言副本中。 在這種情況下，翻譯的內容片段會新增至已包含先前翻譯內容片段的目標資料夾。

## 建立和翻譯工作流程 {#create-and-translate-workflow}

「建立和翻譯」工作流包含以下選項。 與每個選項相關聯的程式步驟類似於與資產的對應選項相關聯的步驟。

* 僅建立結構：如需程式步驟，請參閱[僅建立資產的結構](translation-projects.md#create-structure-only)。
* 建立新翻譯專案：有關過程步驟，請參閱[為資產建立新的翻譯項目](translation-projects.md#create-a-new-translation-project)。
* 新增至現有的翻譯專案：有關過程步驟，請參閱[添加到資產的現有翻譯項目](translation-projects.md#add-to-existing-translation-project)。

## 更新語言副本工作流 {#update-language-copies-workflow}

「更新語言副本」工作流包含以下選項。 與每個選項相關聯的程式步驟類似於與資產的對應選項相關聯的步驟。

* 建立新翻譯專案：有關過程步驟，請參閱[為資產建立新的翻譯項目](translation-projects.md#create-a-new-translation-project)（更新工作流）。
* 新增至現有的翻譯專案：有關過程步驟，請參閱[添加到資產的現有翻譯項目](translation-projects.md#add-to-existing-translation-project)（更新工作流）。

您也可以建立片段的暫時語言副本，類似為資產建立臨時副本的方式。 如需詳細資訊，請參閱[建立資產的臨時語言副本](translation-projects.md#creating-temporary-language-copies)。

## 轉譯混合媒體片段 {#translating-mixed-media-fragments}

[!DNL Experience Manager] 可讓您翻譯包含各種類型媒體資產和集合的內容片段。如果您翻譯的內容片段包含內嵌資產，則這些資產的翻譯副本會儲存在目標語言根目錄下。

如果內容片段包含集合，則集合內的資產會與內容片段一併翻譯。 資產的翻譯副本儲存在與來源語言根目錄下來源資產的實際位置相符的位置的適當目標語言根目錄中。

若要翻譯包含混合媒體的內容片段，請先編輯預設的翻譯架構，以啟用翻譯與內容片段相關聯的內嵌資產和集合。

1. 按一下/點選[!DNL Experience Manager]標誌，然後導覽至「**[!UICONTROL 工具>部署>Cloud Services」]**。
1. 在&#x200B;**[!UICONTROL Adobe Marketing Cloud]**&#x200B;下找到&#x200B;**[!UICONTROL 翻譯整合]**，然後按一下/點選&#x200B;**[!UICONTROL 顯示設定]**。

   ![chlimage_1-444](assets/chlimage_1-444.png)

1. 從可用配置清單中，按一下/點選「預設配置（翻譯整合配置）」]**以開啟「預設配置」**[!UICONTROL 「預設配置」]**頁。**[!UICONTROL 

   ![chlimage_1-445](assets/chlimage_1-445.png)

1. 按一下工具欄中的&#x200B;**[!UICONTROL 編輯]**&#x200B;以顯示&#x200B;**[!UICONTROL 翻譯配置]**&#x200B;對話框。

   ![chlimage_1-446](assets/chlimage_1-446.png)

1. 導覽至&#x200B;**[!UICONTROL Assets]**&#x200B;標籤，然後從&#x200B;**[!UICONTROL Translate Content Fragment Assets]**&#x200B;清單中選擇&#x200B;**[!UICONTROL Inline Media Assets and Associated Collections]**。 按一下/點選&#x200B;**[!UICONTROL 確定]**&#x200B;以儲存變更。

   ![chlimage_1-447](assets/chlimage_1-447.png)

1. 從英文根資料夾中，開啟內容片段。

   ![chlimage_1-448](assets/chlimage_1-448.png)

1. 按一下/點選「**[!UICONTROL 插入資產]**」圖示。

   ![chlimage_1-449](assets/chlimage_1-449.png)

1. 將資產插入內容片段。

   ![chlimage_1-450](assets/chlimage_1-450.png)

1. 按一下/點選&#x200B;**[!UICONTROL 「關聯內容]**」圖示。

   ![chlimage_1-451](assets/chlimage_1-451.png)

1. 按一下/點選「 **[!UICONTROL 關聯內容]**」。

   ![chlimage_1-452](assets/chlimage_1-452.png)

1. 選取集合併將其納入內容片段。 按一下/點選&#x200B;**[!UICONTROL 儲存]**。

   ![chlimage_1-453](assets/chlimage_1-453.png)

1. 選取內容片段，然後按一下/點選&#x200B;**[!UICONTROL GlobalNav]**&#x200B;圖示。
1. 從菜單中選擇&#x200B;**[!UICONTROL 引用]**&#x200B;以顯示&#x200B;**[!UICONTROL 引用]**&#x200B;窗格。

   ![chlimage_1-454](assets/chlimage_1-454.png)

1. 按一下/點選&#x200B;**[!UICONTROL **[!UICONTROL  Copys ]**下的「語言副本」(Language Copies)，以顯示語言副本。]**

   ![chlimage_1-455](assets/chlimage_1-455.png)

1. 從面板底部按一下/點選&#x200B;**[!UICONTROL 「建立並翻譯」]**&#x200B;以顯示「**[!UICONTROL 建立並翻譯」]**&#x200B;對話方塊。

   ![chlimage_1-456](assets/chlimage_1-456.png)

1. 從&#x200B;**[!UICONTROL 目標語言]**&#x200B;清單中選擇目標語言。

   ![chlimage_1-457](assets/chlimage_1-457.png)

1. 從&#x200B;**[!UICONTROL Project]**&#x200B;清單中選擇翻譯項目類型。

   ![chlimage_1-458](assets/chlimage_1-458.png)

1. 在「**[!UICONTROL 專案標題]**」方塊中指定專案標題，然後按一下/點選「**建立**」。

   ![chlimage_1-459](assets/chlimage_1-459.png)

1. 導覽至&#x200B;**[!UICONTROL 專案]**&#x200B;控制台，並開啟您所建立翻譯專案的專案資料夾。

   ![chlimage_1-460](assets/chlimage_1-460.png)

1. 按一下/點選專案方塊，開啟專案詳細資訊頁面。

   ![chlimage_1-461](assets/chlimage_1-461.png)

1. 在「翻譯工作」方塊中，驗證要翻譯的資產數量。
1. 從&#x200B;**[!UICONTROL 翻譯工作]**&#x200B;表徵圖中，啟動翻譯工作。

   ![chlimage_1-462](assets/chlimage_1-462.png)

1. 按一下「翻譯工作」表徵圖底部的點以顯示翻譯工作的狀態。

   ![chlimage_1-463](assets/chlimage_1-463.png)

1. 按一下/點選內容片段，以檢查翻譯的相關資產路徑。

   ![chlimage_1-464](assets/chlimage_1-464.png)

1. 在「集合」控制台中查看集合的語言副本。

   ![chlimage_1-465](assets/chlimage_1-465.png)

   請注意，系列的內容只會翻譯。 系列本身不會翻譯。

1. 導覽至已轉譯之相關資產的路徑。 請注意，翻譯的資產會儲存在目標語言根目錄下。

   ![chlimage_1-466](assets/chlimage_1-466.png)

1. 導覽至系列內隨內容片段翻譯的資產。 請注意，資產的翻譯副本會儲存在適當的目標語言根目錄中。

   ![chlimage_1-467](assets/chlimage_1-467.png)

   >[!NOTE]
   >
   >將內容片段新增至現有專案或執行更新工作流程的程式，與資產的對應程式類似。 有關這些程式的指引，請參閱所述資產程式。

---
title: 資產範本
description: 了解 [!DNL Experience Manager] Assets中的資產範本，以及如何使用資產範本建立行銷宣傳資料。
uuid: 7ba87c1d-70cd-4b89-86f3-971b93885f1e
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 340b62f7-2405-4d2d-846d-2c444d6cc77b
feature: Asset Management,Developer Tools
role: User
exl-id: 9b4f16e6-dd91-4179-9629-576d801fcf43
source-git-commit: 1679bbab6390808a1988cb6fe9b7692c3db31ae4
workflow-type: tm+mt
source-wordcount: '1574'
ht-degree: 0%

---

# 資產範本 {#asset-templates}

資產範本是特殊的資產類別，可協助您快速重新調整視覺化豐富內容的用途，以用於數位和列印媒體。 資產範本包含兩個部分：固定訊息區段和可編輯區段。

固定報文傳送部分可包含專有內容，如品牌徽標和禁用編輯的版權資訊。 可編輯的區段可包含欄位中的視覺和文字內容，可編輯這些欄位以自訂訊息。

在保護全局簽名的同時進行有限的編輯的靈活性使得資產模板成為快速調整內容和分發內容的理想構建塊，從而成為各種功能的內容偽影。 重新調整內容用途有助於降低管理列印和數位頻道的成本，並在這些頻道間提供全方位且一致的體驗。

身為行銷人員，您可以在[!DNL Experience Manager]資產中儲存和管理範本，並使用單一基本範本輕鬆建立多個個人化列印體驗。 您可以建立各種類型的行銷宣傳資料，包括小冊子、傳單、明信片、名片等，以便向客戶清晰地傳達您的行銷訊息。 您也可以從現有或新的打印輸出組合多頁打印輸出。 最重要的是，您可以輕鬆同時提供數位和列印體驗，為使用者提供一致且整合的體驗。

雖然資產範本大多是InDesign檔案，但熟練掌握InDesign並不妨礙製作精美的成品。 建立目錄時，您不需要將InDesign範本的欄位與產品欄位對應。 您可以直接在Web介面上以WYSIWYG模式編輯模板。 不過，若要讓InDesign處理您的編輯變更，您必須先設定[!DNL Experience Manager]資產以與InDesign伺服器整合。

能夠從網頁介面編輯InDesign範本，有助於促進創意與行銷人員之間更緊密的合作，同時縮短當地促銷活動的上市時間。

您可以對資產範本執行下列動作：

* 從Web介面修改可編輯的模板欄位
* 控制文本的基本樣式，例如字型大小、樣式和標籤級別的類型
* 使用內容選擇器變更範本內的影像
* 預覽範本編輯
* 合併多個模板檔案以建立多頁對象

為宣傳材料選擇模板時，[!DNL Assets]將建立可編輯的模板副本。 原始範本會保留，以確保您的全域標牌保持不變，且可重複使用以強製品牌一致性。

您可以以下列格式匯出父資料夾內更新的檔案：

* INDD
* PDF
* JPG

您也可以將這些格式的輸出下載到您的本機系統。

## 建立宣傳資料 {#creating-a-collateral}

假設您想要製作可打印的數位宣傳資料，例如手冊、傳單和廣告，以供即將推出的活動之用，並與全球直銷商分享。 根據範本建立宣傳資料有助於跨管道提供統一的客戶體驗。 設計人員可以使用創意解決方案(如InDesign)建立促銷活動範本（單頁或多頁），並為您上傳範本至[!DNL Assets]。 在建立宣傳資料之前，請先將一個或多個INDD模板上載到Experience Manager，並提前提供。

1. 按一下[!DNL Experience Manager]標誌，然後按一下「導覽」頁面上的&#x200B;**[!UICONTROL Assets]**。
1. 從選項中，選擇&#x200B;**[!UICONTROL 模板]**。

   ![chlimage_1-306](assets/chlimage_1-306.png)

1. 按一下/點選&#x200B;**[!UICONTROL 建立]**，然後從功能表中選擇要建立的宣傳品。 例如，選擇&#x200B;**[!UICONTROL 手冊]**。

   ![chlimage_1-307](assets/chlimage_1-307.png)

1. 先將一或多個INDD範本上傳至Experience Manager，並提供使用。 選擇手冊的模板，然後按一下/點選&#x200B;**[!UICONTROL Next]**。

   ![chlimage_1-308](assets/chlimage_1-308.png)

1. 指定手冊的名稱和可選說明。

   ![chlimage_1-309](assets/chlimage_1-309.png)

1. （可選）按一下/點選&#x200B;**[!UICONTROL 標籤]**&#x200B;欄位旁的&#x200B;**[!UICONTROL 標籤]**&#x200B;圖示，然後為手冊選取一或多個標籤。 按一下/點選&#x200B;**[!UICONTROL 確認]**&#x200B;以確認您的選取項目。

   ![chlimage_1-310](assets/chlimage_1-310.png)

1. 按一下&#x200B;**[!UICONTROL 建立]**。對話方塊會確認已建立新手冊。 按一下/點選&#x200B;**[!UICONTROL 開啟]**&#x200B;以在編輯模式中開啟手冊。

   ![chlimage_1-310](assets/chlimage_1-311.png)

   或者，關閉對話框，導航到您開始的「模板」頁中的資料夾，以查看您建立的手冊。 宣傳品的類型會顯示在其縮圖上的卡片視圖中。 例如，在此情況下，手冊會顯示在縮圖上。

   ![chlimage_1-312](assets/chlimage_1-312.png)

## 編輯宣傳資料 {#editing-a-collateral}

建立宣傳資料後，您可以立即編輯它。 或者，您也可以從「範本」頁面或資產頁面開啟它。

1. 要開啟宣傳資料進行編輯，請執行以下操作之一：

   * 開啟您在[建立宣傳資料](asset-templates.md#creating-a-collateral)的步驟7中建立的宣傳資料（在本例中為手冊）。
   * 從「模板」頁，導航到建立宣傳品的資料夾，然後按一下/點選宣傳品縮圖上的「編輯快速操作」。
   * 在宣傳品的資產頁面中，按一下/點選工具列中的「編輯」圖示。
   * 選擇宣傳品，然後按一下/點選工具列中的「編輯」表徵圖。

   ![chlimage_1-313](assets/chlimage_1-313.png)

   資產尋找器和文字編輯器會顯示在頁面左側。 文字編輯器預設為開啟。

   您可以使用文字編輯器來修改要顯示在文字欄位中的文字。 您可以在標籤層級修改字型大小、樣式、顏色和類型。

   使用資產尋找器，您可以在[!DNL Assets]內瀏覽或搜尋影像，並將範本中的可編輯影像取代為您所選擇的影像。

   ![chlimage_1-314](assets/chlimage_1-314.png)

   可編輯的項目會顯示在右側。 若要在[!DNL Assets]中編輯欄位，必須在InDesign中標籤範本中對應欄位。 換言之，它們應在InDesign中設為可編輯。

   ![chlimage_1-315](assets/chlimage_1-315.png)

   >[!NOTE]
   >
   >確保您的[!DNL Experience Manager]實例與InDesign伺服器整合，以啟用[!DNL Assets]從InDesign模板中提取資料並使其可供編輯。 如需詳細資訊，請參閱[整合 [!DNL Assets] 與InDesign Server](indesign.md)。

1. 若要修改可編輯欄位中的文字，請按一下/點選可編輯欄位清單中的文字欄位，然後編輯欄位中的文字。

   ![chlimage_1-316](assets/chlimage_1-316.png)

   可以使用提供的選項編輯文本屬性，例如字型樣式、顏色、大小。

1. 按一下/點選&#x200B;**[!UICONTROL 預覽]**&#x200B;圖示以預覽文字變更。

   ![chlimage_1-317](assets/chlimage_1-317.png)

1. 若要交換影像，請按一下/點選&#x200B;**[!UICONTROL 資產尋找器]**&#x200B;圖示。

   ![chlimage_1-318](assets/chlimage_1-318.png)

1. 從可編輯欄位清單中選取影像欄位，然後從資產選擇器拖曳所需影像至可編輯欄位。

   ![chlimage_1-319](assets/chlimage_1-319.png)

   您也可以使用關鍵字、標籤，並根據其發佈狀態來搜尋影像。 您可以瀏覽[!DNL Assets]儲存庫，並導覽至所需影像的位置。

   ![chlimage_1-320](assets/chlimage_1-320.png)

1. 按一下/點選&#x200B;**[!UICONTROL 預覽]**&#x200B;圖示以預覽影像。

   ![chlimage_1-321](assets/chlimage_1-321.png)

1. 要編輯多頁宣傳資料中的特定頁，請使用底部的頁導航器。

   ![chlimage_1-322](assets/chlimage_1-322.png)

1. 按一下/點選工具列上的&#x200B;**[!UICONTROL 預覽]**&#x200B;圖示，以預覽所有變更。 按一下/點選&#x200B;**[!UICONTROL Done]**&#x200B;以儲存對宣傳品的編輯變更。

   >[!NOTE]
   >
   >只有當宣傳品中可編輯的影像欄位沒有缺少任何表徵圖時，才會啟用「預覽」和「完成」表徵圖。 如果您的宣傳品中缺少表徵圖，則是因為[!DNL Experience Manager]無法解析InDesign模板中的影像。 在下列情況下，[!DNL Experience Manager]通常無法解析影像：
   >
   >* 映像未嵌入到基礎InDesign模板中
   >* 從本地檔案系統連結影像

   >
   >要啟用[!DNL Experience Manager]解析影像，請執行以下操作：
   >
   >* 建立InDesign範本時內嵌影像（請參閱[關於連結和內嵌圖形](https://helpx.adobe.com/indesign/using/graphics-links.html)）。
   >* 將[!DNL Experience Manager]裝載到您的本地檔案系統，然後將缺少的表徵圖映射為現有的[!DNL Experience Manager]資產。

   >
   >有關使用InDesign文檔的詳細資訊，請參閱 [!DNL Experience Manager]](https://helpx.adobe.com/experience-manager/kb/best-practices-idd-docs-aem.html)中的[使用InDesign文檔的最佳做法。

1. 若要為手冊產生PDF轉譯，請在對話方塊中選取Acrobat選項，然後按一下&#x200B;**[!UICONTROL 繼續]**。
1. 宣傳資料建立在您開始使用的資料夾中。 要查看格式副本，請開啟宣傳資料，然後從GlobalNav清單中選擇&#x200B;**[!UICONTROL 格式副本]**。

   ![chlimage_1-323](assets/chlimage_1-323.png)

1. 從轉譯清單按一下/點選PDF轉譯，以下載PDF檔案。 開啟PDF檔案以審閱宣傳資料。

   ![chlimage_1-324](assets/chlimage_1-324.png)

## 合併抵押品 {#merge-collateral}


1. 按一下或點選「**[!UICONTROL 工具>資產]**」。
1. 從選項中，選擇&#x200B;**[!UICONTROL 模板]**。
1. 按一下/點選「**[!UICONTROL 建立]**」，然後從功能表選擇「**[!UICONTROL 合併]**」。

   ![chlimage_1-325](assets/chlimage_1-325.png)

1. 在「範本合併」頁面中，按一下/點選「合併」圖示。

   ![chlimage_1-326](assets/chlimage_1-326.png)

1. 導航到要合併的宣傳品的位置，按一下/點選要合併的宣傳品的縮圖以選擇它們。

   ![chlimage_1-327](assets/chlimage_1-327.png)

   您甚至可以從OmniSearch方塊搜尋範本。

   ![chlimage_1-328](assets/chlimage_1-328.png)

   您可以瀏覽[!DNL Assets]儲存庫或集合，並導覽至所需範本的位置，然後選取它們以合併。

   ![chlimage_1-329](assets/chlimage_1-329.png)

   您可以套用各種篩選器以搜尋所需的範本。 例如，您可以根據檔案類型或標籤來搜尋範本。

   ![chlimage_1-330](assets/chlimage_1-330.png)

1. 從工具列按一下/點選「 **[!UICONTROL Next]** 」。
1. 在&#x200B;**[!UICONTROL 預覽和重新排序]**&#x200B;螢幕中，根據需要重新排列模板並預覽要合併的模板選擇。 然後，按一下/點選工具列中的「**[!UICONTROL Next]** 」。

   ![chlimage_1-331](assets/chlimage_1-331.png)

1. 在「配置模板」螢幕中，指定宣傳品的名稱。 （可選）指定您認為適當的任何標籤。 如果要導出PDF格式的輸出，請選擇&#x200B;**[!UICONTROL Acrobat(.PDF)]**&#x200B;選項。 預設情況下，宣傳資料將以JPG和InDesign格式導出。 要更改多頁宣傳品的顯示縮略圖，請按一下/點選&#x200B;**[!UICONTROL 更改縮略圖]**。

   ![chlimage_1-332](assets/chlimage_1-332.png)

1. 按一下/點選&#x200B;**[!UICONTROL 儲存]**，然後按一下/點選對話方塊中的&#x200B;**[!UICONTROL 確定]**&#x200B;以關閉對話方塊。 多頁宣傳資料建立在您開始使用的資料夾中。

   >[!NOTE]
   >
   >您以後不能編輯合併的宣傳資料，也不能使用它建立其他宣傳資料。

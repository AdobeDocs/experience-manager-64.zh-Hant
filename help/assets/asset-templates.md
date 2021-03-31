---
title: 資產範本
description: 瞭解AEM Assets的資產範本，以及如何使用資產範本建立行銷文宣。
uuid: 7ba87c1d-70cd-4b89-86f3-971b93885f1e
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 340b62f7-2405-4d2d-846d-2c444d6cc77b
feature: 資產管理，開發人員工具
role: 業務從業人員
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '1610'
ht-degree: 0%

---


# 資產範本 {#asset-templates}

資產範本是一類特殊的資產，可協助您快速將視覺化豐富的內容重新運用於數位和印刷媒體。 資產範本包含兩個部分：固定訊息區段和可編輯區段。

固定訊息區段可包含專屬內容，例如品牌標誌和禁止編輯的版權資訊。 可編輯的區段可在欄位中包含視覺和文字內容，可編輯這些內容以自訂訊息。

在確保全域簽名安全的同時進行有限編輯的靈活性，使資產範本成為快速調整內容和發佈內容的理想建置區塊，成為各種功能的內容偽影。 重新調整內容用途有助於降低管理印刷和數位通道的成本，並跨這些通道提供全方位且一致的體驗。

身為行銷人員，您可以在AEM Assets儲存和管理範本，並使用單一基本範本輕鬆建立多種個人化印刷體驗。 您可以建立各種類型的行銷文宣，包括簡介手冊、傳單、明信片、名片等，以便向客戶清楚傳達行銷訊息。 您也可以從現有或新的列印輸出組合多頁列印輸出。 最重要的是，您可以輕鬆同時提供數位和印刷體驗，為使用者提供一致、整合的體驗。

雖然資產範本大多是InDesign檔案，但InDesign的熟練程度並不妨礙製作亮眼的文物。 您不需要將InDesign範本的欄位與建立目錄時所需的產品欄位對應。 您可以直接在Web介面上，在WYSIWYG模式下編輯範本。 不過，要InDesign處理編輯更改，您必須先將AEM Assets配置為與InDesign伺服器整合。

能夠從網頁介面編輯InDesign範本，有助於促進創意與行銷人員之間的協作，同時縮短當地促銷活動的上市時間。

您可以使用資產範本執行下列動作：

* 從網頁介面修改可編輯的範本欄位
* 控制文字的基本樣式，例如字型大小、樣式和文字在標籤層級
* 使用內容選擇器變更範本中的影像
* 預覽範本編輯
* 合併多個範本檔案以建立多頁對象

當您為宣傳品選擇範本時，AEM Assets會建立範本副本，供您編輯。 原始範本會保留，以確保全域標牌保持完整，並可重複使用以強製品牌一致性。

您可以以下列格式匯出父資料夾內的更新檔案：

* INDD
* PDF
* JPG

您也可以將這些格式的輸出下載到本機系統。

## 建立宣傳品{#creating-a-collateral}

假設您想要建立數位可列印的宣傳品，例如簡介手冊、傳單和廣告，以便在即將到來的宣傳活動中展示，並與全球的經銷商分享。 根據範本建立宣傳品有助於跨通道提供統一的客戶體驗。 設計人員可使用創意解決方案(例如InDesign)建立促銷活動範本（單頁或多頁），並為您上傳範本至AEM Assets。 在建立宣傳品之前，請先將一或多個INDD範本上傳至並預先Experience Manager使用。

1. 按一下或點AEM選標誌，然後按一下／點選「導覽」頁面上的「資產」****。
1. 從選項中選擇&#x200B;**[!UICONTROL 模板]**。

   ![chlimage_1-306](assets/chlimage_1-306.png)

1. 按一下／點選&#x200B;**[!UICONTROL Create]** ，然後從菜單中選擇要建立的宣傳品。 例如，選擇&#x200B;**[!UICONTROL 手冊]**。

   ![chlimage_1-307](assets/chlimage_1-307.png)

1. 將一或多個INDD範本上傳至Experience Manager，並提前使用。 選擇手冊的範本，然後按一下／點選&#x200B;**[!UICONTROL Next]**。

   ![chlimage_1-308](assets/chlimage_1-308.png)

1. 指定手冊的名稱和選用說明。

   ![chlimage_1-309](assets/chlimage_1-309.png)

1. （可選）按一下／點選&#x200B;**[!UICONTROL Tags]**&#x200B;欄位旁的&#x200B;**[!UICONTROL Tags]**&#x200B;圖示，並為手冊選取一或多個標籤。 按一下／點選&#x200B;**[!UICONTROL 確認]**&#x200B;以確認您的選擇。

   ![chlimage_1-310](assets/chlimage_1-310.png)

1. 按一下&#x200B;**[!UICONTROL 建立]**。對話方塊會確認已建立新的手冊。 按一下／點選&#x200B;**[!UICONTROL 開啟]**，以編輯模式開啟手冊。

   ![chlimage_1-310](assets/chlimage_1-311.png)

   或者，關閉對話方塊並導覽至您開始使用的「範本」頁面中的資料夾，以檢視您建立的手冊。 在卡片檢視中，文宣的類型會出現在其縮圖上。 例如，在此例中，手冊會顯示在縮圖上。

   ![chlimage_1-312](assets/chlimage_1-312.png)

## 編輯宣傳品{#editing-a-collateral}

您可以在建立宣傳品後立即加以編輯。 或者，您也可以從「範本」頁面或資產頁面開啟它。

1. 要開啟文宣進行編輯，請執行下列操作之一：

   * 開啟您在[建立宣傳品](asset-templates.md#creating-a-collateral)步驟7中建立的宣傳品（在本例中為手冊）。
   * 從「模板」頁面，導航到建立宣傳品的資料夾，然後按一下／按一下宣傳品縮圖上的「編輯」快速操作。
   * 在宣傳品的資產頁面中，按一下／點選工具列中的「編輯」圖示。
   * 選擇宣傳品，然後從工具列中按一下／點選「編輯」表徵圖。

   ![chlimage_1-313](assets/chlimage_1-313.png)

   資產搜尋器和文字編輯器會顯示在頁面的左側。 文字編輯器預設為開啟。

   您可以使用文字編輯器修改要在文字欄位中顯示的文字。 您可以在標籤層級修改字型大小、樣式、顏色和文字。

   使用資產搜尋器，您可以瀏覽或搜尋AEM Assets的影像，並將範本中可編輯的影像取代為您選擇的影像。

   ![chlimage_1-314](assets/chlimage_1-314.png)

   可編輯的內容會顯示在右側。 若要在AEM Assets編輯欄位，範本中的對應欄位必須以InDesign標籤。 換句話說，應將它們標籤為可在InDesign中編輯。

   ![chlimage_1-315](assets/chlimage_1-315.png)

   >[!NOTE]
   >
   >確保您的AEM實例與InDesign伺服器整合，使AEM Assets能夠從InDesign模板中提取資料並使其可供編輯。 如需詳細資訊，請參閱[將AEM Assets與InDesign Server整合](indesign.md)。

1. 若要修改可編輯欄位中的文字，請按一下／點選可編輯欄位清單中的文字欄位，並編輯欄位中的文字。

   ![chlimage_1-316](assets/chlimage_1-316.png)

   您可以使用提供的選項編輯文字屬性，例如字型樣式、顏色、大小。

1. 按一下／點選&#x200B;**[!UICONTROL 預覽]**&#x200B;圖示以預覽文字變更。

   ![chlimage_1-317](assets/chlimage_1-317.png)

1. 若要交換影像，請按一下／點選&#x200B;**[!UICONTROL Asset Finder]**&#x200B;圖示。

   ![chlimage_1-318](assets/chlimage_1-318.png)

1. 從可編輯欄位清單中選取影像欄位，然後從資產選擇器拖曳所要的影像至可編輯欄位。

   ![chlimage_1-319](assets/chlimage_1-319.png)

   您也可以使用關鍵字、標籤，並根據其發佈狀態來搜尋影像。 您可以瀏覽AEM Assets儲存庫並導航到所需映像的位置。

   ![chlimage_1-320](assets/chlimage_1-320.png)

1. 按一下／點選&#x200B;**[!UICONTROL 預覽]**&#x200B;圖示以預覽影像。

   ![chlimage_1-321](assets/chlimage_1-321.png)

1. 要編輯多頁宣傳品中的特定頁面，請使用底部的頁面導覽器。

   ![chlimage_1-322](assets/chlimage_1-322.png)

1. 按一下／點選工具列上的&#x200B;**[!UICONTROL 預覽]**&#x200B;圖示，以預覽所有變更。 按一下／點選&#x200B;**[!UICONTROL Done]** ，將編輯更改保存到宣傳品。

   >[!NOTE]
   >
   >只有當宣傳品中的可編輯影像欄位沒有任何缺少的表徵圖時，才會啟用「預覽」和「完成」表徵圖。 如果您的宣傳品中缺少表徵圖，則AEM是因為無法解析InDesign模板中的影像。 通常，AEM在下列情況下無法解析影像：
   >
   >* 影像未內嵌在基礎InDesign範本中
   >* 從本機檔案系統連結影像

   >
   >若要啟AEM用解析影像，請執行下列動作：
   >
   >* 建立InDesign範本時內嵌影像（請參閱[關於連結和內嵌圖形](https://helpx.adobe.com/indesign/using/graphics-links.html)）。
   >* 載入AEM您的本機檔案系統，然後將遺失的圖示與現有資產AEM對應。

   >
   >有關使用InDesign文檔的詳細資訊，請參閱](https://helpx.adobe.com/experience-manager/kb/best-practices-idd-docs-aem.html)中的[使用InDesign文檔的AEM最佳做法。

1. 若要為手冊產生PDF轉譯，請在對話方塊中選取「Acrobat」選項，然後按一下「繼續&#x200B;****」。
1. 宣傳品是在您開始使用的資料夾中建立的。 要查看轉譯，請開啟宣傳品並從GlobalNav清單中選擇&#x200B;**[!UICONTROL 轉譯]**。

   ![chlimage_1-323](assets/chlimage_1-323.png)

1. 從轉譯清單中按一下／點選PDF轉譯，以下載PDF檔案。 開啟PDF檔案以檢閱文宣。

   ![chlimage_1-324](assets/chlimage_1-324.png)

## 合併宣傳品{#merge-collateral}


1. 按一下或點選「**[!UICONTROL 工具>資產]**」。
1. 從選項中選擇&#x200B;**[!UICONTROL 模板]**。
1. 按一下／點選&#x200B;**[!UICONTROL 建立]**&#x200B;並從菜單中選擇&#x200B;**[!UICONTROL 合併]**。

   ![chlimage_1-325](assets/chlimage_1-325.png)

1. 在「範本合併」頁面中，按一下／點選「合併」圖示。

   ![chlimage_1-326](assets/chlimage_1-326.png)

1. 導航到要合併的宣傳品的位置，按一下／點選要合併的宣傳品的縮圖以選擇它們。

   ![chlimage_1-327](assets/chlimage_1-327.png)

   您甚至可以從OmniSearch方塊中搜尋範本。

   ![chlimage_1-328](assets/chlimage_1-328.png)

   您可以瀏覽AEM Assets儲存庫或系列，並導航到所需模板的位置，然後選擇它們進行合併。

   ![chlimage_1-329](assets/chlimage_1-329.png)

   您可以套用各種篩選條件來搜尋所需的範本。 例如，您可以根據檔案類型或標籤來搜尋範本。

   ![chlimage_1-330](assets/chlimage_1-330.png)

1. 從工具列按一下／點選「**[!UICONTROL Next]**」。
1. 在&#x200B;**[!UICONTROL 預覽與重新排序]**&#x200B;畫面中，視需要重新排列範本，並預覽要合併的範本選擇。 然後，從工具列按一下／點選「**[!UICONTROL Next]**」。

   ![chlimage_1-331](assets/chlimage_1-331.png)

1. 在「配置模板」螢幕中，指定宣傳品的名稱。 （可選）指定您認為適當的任何標籤。 如果要以PDF格式導出輸出，請選擇&#x200B;**[!UICONTROL Acrobat(.PDF)]**&#x200B;選項。 預設情況下，文宣將以JPG和InDesign格式導出。 要更改多頁文宣的顯示縮圖，請按一下／點選&#x200B;**[!UICONTROL 更改縮圖]**。

   ![chlimage_1-332](assets/chlimage_1-332.png)

1. 按一下／點選&#x200B;**[!UICONTROL Save]** ，然後按一下／點選對話框中的&#x200B;**[!UICONTROL OK]**&#x200B;以關閉對話框。 多頁宣傳資料是在您開始使用的資料夾中建立。

   >[!NOTE]
   >
   >您以後無法編輯合併的宣傳品，也無法用它來建立其他宣傳品。


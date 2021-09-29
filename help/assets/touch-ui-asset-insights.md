---
title: 使用Assets Insights功能追蹤影像的使用情況
description: 「資產前瞻分析」功能可讓您追蹤使用者評等，以及第三方網站、行銷活動和Adobe創意解決方案所使用影像的使用統計資料。
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: a9604b09-1c83-4c1e-aff7-13107b898cb3
source-git-commit: a778c3bbd0e15bb7b6de2d673b4553a7bd146143
workflow-type: tm+mt
source-wordcount: '793'
ht-degree: 6%

---

# Assets Insights {#asset-insights}

了解「資產前瞻分析」功能如何讓您追蹤第三方網站、行銷活動和Adobe創意解決方案中所使用資產的使用者評等和使用統計資料。

「資產前瞻分析」功能可讓您追蹤第三方網站、行銷活動和Adobe創意解決方案中使用的資產的使用者評等和使用統計資料，以獲得有關其效能和人氣的深入分析。

Assets Insights會擷取使用者活動詳細資料，例如資產被評分、點按的次數，以及曝光次數（資產在網站上載入的次數）。 它會根據這些統計資料，為資產指派分數。 您可以使用分數和績效統計資料來選取要納入目錄、行銷活動等的熱門資產。 您甚至可以根據這些統計資料制定資產的存檔和許可證更新策略。

若要讓「資產前瞻分析」從網站擷取資產的使用量統計資料，您必須在網站代碼中包含資產的內嵌代碼。

若要讓「資產前瞻分析」顯示資產的使用統計資料，請先設定從[!DNL Adobe Analytics]擷取報表資料的功能。 如需詳細資訊，請參閱[設定Assets Insights](touch-ui-configuring-asset-insights.md)。 若要在內部部署安裝中使用此功能，請分別購買[!DNL Adobe Analytics]授權。 [!DNL Managed Services]上的客戶會收到與[!DNL Experience Manager]捆綁的[!DNL Analytics]許可證。 請參閱[Managed Services產品說明](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html)。

>[!NOTE]
>
>深入分析受支援，僅針對影像提供。

## 檢視資產的統計資料 {#viewing-statistics-for-an-asset}

您可以從中繼資料頁面檢視「資產前瞻分析」分數。

1. 從「資產」使用者介面(UI)中，選取資產，然後點選/按一下工具列中的&#x200B;**[!UICONTROL 屬性]**&#x200B;圖示。
1. 從「屬性」頁面，點選/按一下&#x200B;**[!UICONTROL Insights]**&#x200B;標籤。
1. 在&#x200B;**[!UICONTROL Insights]**&#x200B;索引標籤中檢閱資產的使用情況詳細資料。 **[!UICONTROL 分數]**&#x200B;區段說明資產的資產使用總計和效能分數。

   使用分數說明資產在各種解決方案中的使用次數。

   **[!UICONTROL 曝光數]**&#x200B;分數是資產在網站上載入的次數。 顯示在&#x200B;**[!UICONTROL Clicks]**&#x200B;下方的數字為資產的點按次數。

1. 查看&#x200B;**[!UICONTROL 使用統計資料]**&#x200B;部分，了解資產所屬的實體以及最近使用了哪些創意解決方案。 使用率越高，資產在使用者中受歡迎的機率就越大。 使用資料顯示在以下標題下：

   * **[!UICONTROL 資產]**:資產屬於集合或複合資產的次數
   * **[!UICONTROL 網頁與行動]**:資產加入網站和應用程式的次數
   * **[!UICONTROL 社交]**:資產用於解決方案(例如Adobe Social和Adobe Campaign)的次數
   * **[!UICONTROL 電子郵件]**:資產用於電子郵件促銷活動的次數

   ![usage_statistics](assets/usage_statistics.png)

   >[!NOTE]
   >
   >「資產前瞻分析」功能會定期從[!DNL Adobe Analytics]擷取解決方案資料，解決方案區段可能不會顯示最新資料。 顯示資料的時段取決於Assets Insights執行擷取[!DNL Analytics]資料的擷取作業排程。

1. 要以圖形方式查看某個時段內資產的效能統計資訊，請在「效能統計資訊」部分中 **[!UICONTROL 選擇該時段]** 。詳細資訊 (包括點按次數和印象) 會顯示為圖形的趨勢線。

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >與解決方案區段中的資料不同，效能統計區段會顯示最新的資料。

1. 若要取得您包含在網站中之資產的內嵌程式碼，以取得效能資料，請按一下資產縮圖下方的&#x200B;**[!UICONTROL 取得內嵌程式碼]**。 如需如何將內嵌程式碼包含在協力廠商網頁的詳細資訊，請參閱[使用頁面追蹤器及在網頁中內嵌程式碼](touch-ui-using-page-tracker.md)。

   ![chlimage_1-303](assets/chlimage_1-303.png)

## 檢視資產的匯總統計資料 {#viewing-aggregate-statistics-for-assets}

您可以使用前瞻分析檢視同時檢視資料夾內所有資產 **[!UICONTROL 的分數]**。

1. 在「資產」UI中，導覽至包含您要檢視其分析之資產的資料夾。
1. 點選/按一下工具列中的「配置」圖示，然後選擇&#x200B;**[!UICONTROL 前瞻分析檢視]**。
1. 頁面會顯示資產的使用分數。 比較各種資產的評等並得出深入分析。

## 排程背景工作 {#scheduling-background-job}

Assets Insights會定期從Adobe Analytics報表套裝擷取資產的使用資料。 根據預設，Assets Insights會每24小時在凌晨2:00執行背景工作，以擷取資料。 不過，您可以透過從Web主控台設定&#x200B;**[!UICONTROL Adobe CQ DAM資產效能報表同步工作]**&#x200B;服務，以修改頻率和時間。

1. 點選[!DNL Experience Manager]標誌，然後前往「**[!UICONTROL 工具>操作> Web Console]**」。
1. 開啟&#x200B;**[!UICONTROL Adobe CQ DAM資產效能報表同步工作]**&#x200B;服務設定。

   ![chlimage_1-304](assets/chlimage_1-304.png)

1. 在屬性調度器表達式中指定作業所需的調度器頻率和開始時間。 儲存變更。

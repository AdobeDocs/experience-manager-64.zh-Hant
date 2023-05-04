---
title: '"[!DNL Experience Manager Assets] 首頁體驗」'
description: 個人化資產首頁以提供豐富的歡迎畫面體驗，包括資產近期活動的快照。
contentOwner: AG
feature: Developer Tools,Asset Management
role: Admin,User
exl-id: f47c6da7-aa21-4f49-9c66-2a8091e19561
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 2%

---

# [!DNL Adobe Experience Manager Assets] 首頁體驗 {#aem-assets-home-page-experience}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

個人化 [!DNL Experience Manager Assets] 豐富歡迎畫面體驗的首頁，包括資產近期活動的快照。

此 [!DNL Adobe Experience Manager Assets] 首頁提供豐富且個人化的歡迎畫面體驗，包含最近活動的快照，例如最近檢視或上傳的資產。

預設會停用「資產首頁」。 要啟用它，請執行以下步驟：

1. 若要存取 [!DNL Experience Manager] Configuration Manager，按一下 **[!UICONTROL 「工具」>「操作」>「Web控制台」]**.
1. 開啟 **Day CQ DAM事件記錄器** 服務。
1. 選取 **[!UICONTROL 啟用此服務]** 啟用活動記錄。

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. 從 **事件類型** 清單中，選擇要記錄的事件並保存更改。

   >[!CAUTION]
   >
   >啟用「已檢視資產」、「已檢視專案」和「已檢視集合」選項，可大幅增加記錄的事件數。

1. 開啟 **[!UICONTROL DAM資產首頁功能旗標]** 從Configuration Manager提供服務 `https://[AEM_server]:[port]/system/console/configMgr`.
1. 選取 **[!UICONTROL isEnabled.name]** 選項啟用「資產首頁」功能。 儲存變更。

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. 開啟 **[!UICONTROL 使用者偏好設定]** 對話框，然後選擇 **[!UICONTROL 啟用資產首頁]**. 儲存變更。

   ![user_preferences](assets/user_preferences.png)

啟用「資產」首頁後，從「導覽」頁面導覽至「資產」使用者介面。

![home_page](assets/home_page.png)

點選/按一下 **[!UICONTROL 按一下這裡以設定您的體驗連結]** 新增使用者名稱、背景影像和設定檔影像。

「資產」首頁包含下列章節：

* 歡迎區段
* 介面工具集區段

**歡迎區段**

如果您的設定檔存在，歡迎區段會顯示寄送給您的歡迎訊息。 此外，它還會顯示您的個人資料圖片和歡迎影像（如果已設定）。

如果您的個人資料不完整，歡迎區段會顯示一般歡迎訊息和個人資料圖片的預留位置。

**介面工具集區段**

此部分顯示在「歡迎」部分下方，並在以下部分下顯示現成的Widget:

* 活動
* 最近
* 探索

**活動**:在本節中， **我的活動** 介面工具集會顯示登入使用者使用資產（包括不轉譯的資產）執行的最新活動，例如資產上傳、下載、資產建立、編輯、留言、註解和共用。

**最近**:此 **最近查看** 此部分下的介面工具集顯示登錄用戶最近訪問的實體，包括資料夾、集合和項目。

**Discover**:此 **新增** 此區段下的介面工具集會顯示最近上傳至的資產和轉譯 [!DNL Assets] 例項。

若要啟用清除使用者活動資料，請啟用 **DAM事件清除服務** 從Configuration Manager。 啟用此服務後，系統會刪除登入使用者超過指定數目的活動。

「歡迎」畫面提供簡單的導覽輔助工具，例如工具列上的圖示，可存取資料夾、收藏和目錄。

>[!NOTE]
>
>啟用Day CQ DAM Event Recorder和DAM Event Purge服務可增加對JCR的寫入操作和搜尋索引，如此可大幅增加 [!DNL Experience Manager] 伺服器。 上的額外負載 [!DNL Experience Manager] 伺服器會影響其效能。

>[!CAUTION]
>
>擷取、篩選及清除資產首頁所需的使用者活動會對效能造成額外負荷。 因此，管理員應該為目標使用者有效配置首頁。
>
>Adobe建議執行大量作業的管理員和使用者避免使用資產首頁功能，以防止使用者活動增加。 此外，管理員可借由設定來排除特定使用者的記錄活動 **Day CQ DAM事件記錄器** 從Configuration Manager。
>
>如果您使用此功能，Adobe建議您根據伺服器負載排程清除頻率。

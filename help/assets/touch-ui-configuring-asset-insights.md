---
title: 設定Assets Insights
description: 了解如何在 [!DNL Experience Manager] 資產。
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: b0d62dd3-1868-4d73-95f7-3d6c3ff474d9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 11%

---

# 設定Assets Insights {#configuring-asset-insights}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets擷取使用資料 [!DNL Experience Manager] 協力廠商網站使用的資產。 若要讓Assets Insights能夠擷取此資料並產生深入分析，請先設定功能以與Adobe Analytics整合。

>[!NOTE]
>
>僅支援並提供影像見解。

1. 在 AEM 中，按一下&#x200B;**[!UICONTROL 「工具」>「資產」]**。

   ![chlimage_1-210](assets/chlimage_1-210.png)

1. 按一下「 **[!UICONTROL 前瞻分析設定]** 」資訊卡。
1. 在精靈中，選取資料中心並提供您的認證，包括組織名稱、使用者名稱和密碼。

   ![chlimage_1-211](assets/insights_config2.png)

1. 按一下/點選「 **[!UICONTROL 驗證]**」。
1. 之後 [!DNL Experience Manager] 驗證您的憑證，從 **[!UICONTROL 報表套裝]** 清單中，選擇您要Adobe Analytics Insights擷取資料的Analytics報表套裝。 按一下 **[!UICONTROL 新增]**.
1. 之後 [!DNL Experience Manager] 設定您的報表套裝，按一下/點選 **[!UICONTROL 完成]**.

## 頁面追蹤器 {#page-tracker}

設定Analytics帳戶後，系統會為您產生頁面追蹤器程式碼。 啟用Assets Insights以追蹤 [!DNL Experience Manager] 協力廠商網站中使用的資產，請在網站程式碼中加入頁面追蹤器程式碼。 在中使用頁面追蹤器公用程式 [!DNL Experience Manager] 產生頁面追蹤器程式碼的資產。 如需如何在協力廠商網頁中加入頁面追蹤器程式碼的詳細資訊，請參閱 [在網頁中使用頁面追蹤器和內嵌程式碼](touch-ui-using-page-tracker.md).

1. 在AEM中，按一下 **[!UICONTROL 工具>資產]**.

   ![chlimage_1-214](assets/chlimage_1-214.png)

1. 在導覽頁 **[!UICONTROL 面中]** ，按一下 **** 前瞻分析頁面追蹤器卡片。
1. 按一下 **[!UICONTROL 下載]** 圖示來下載頁面追蹤器程式碼。

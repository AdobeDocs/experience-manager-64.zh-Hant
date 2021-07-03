---
title: 設定Assets Insights
description: 了解如何在AEM Assets中設定Assets Insights。
contentOwner: AG
feature: 資產分析，資產報表
role: User,Admin
exl-id: b0d62dd3-1868-4d73-95f7-3d6c3ff474d9
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 10%

---

# 設定Assets Insights {#configuring-asset-insights}

Adobe Experience Manager(AEM)Assets會從Adobe Analytics擷取協力廠商網站所使用AEM資產的使用情況資料。 若要讓Assets Insights能夠擷取此資料並產生深入分析，請先設定功能以與Adobe Analytics整合。

>[!NOTE]
>
>僅支援並提供影像見解。

1. 在 AEM 中，按一下&#x200B;**[!UICONTROL 「工具」>「資產」]**。

   ![chlimage_1-210](assets/chlimage_1-210.png)

1. 按一下「 **[!UICONTROL 前瞻分析設定]** 」資訊卡。
1. 在精靈中，選取資料中心並提供您的認證，包括組織名稱、使用者名稱和密碼。

   ![chlimage_1-211](assets/insights_config2.png)

1. 按一下/點選「 **[!UICONTROL 驗證]**」。
1. AEM驗證您的憑證後，從&#x200B;**[!UICONTROL 報表套裝]**&#x200B;清單中，選擇您要讓Assets Insights擷取資料的Adobe Analytics報表套裝。 按一下&#x200B;**[!UICONTROL 「新增」]**。
1. 在AEM設定您的報表套裝後，按一下/點選&#x200B;**[!UICONTROL Done]**。

## 頁面追蹤器 {#page-tracker}

設定Analytics帳戶後，系統會為您產生頁面追蹤器程式碼。 若要啟用Assets Insights以追蹤第三方網站中使用的AEM資產，請在網站代碼中加入頁面追蹤器代碼。 使用AEM Assets中的頁面追蹤器公用程式來產生頁面追蹤器程式碼。 如需如何將您的頁面追蹤器程式碼納入第三方網頁的詳細資訊，請參閱[在網頁中使用頁面追蹤器及內嵌程式碼](touch-ui-using-page-tracker.md)。

1. 在AEM中，按一下&#x200B;**[!UICONTROL 工具>資產]**。

   ![chlimage_1-214](assets/chlimage_1-214.png)

1. 在導覽頁 **[!UICONTROL 面中]** ，按一下 **** 前瞻分析頁面追蹤器卡片。
1. 按一下&#x200B;**[!UICONTROL 下載]**&#x200B;圖示以下載頁面追蹤器程式碼。

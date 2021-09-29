---
title: 設定Assets Insights
description: 了解如何在 [!DNL Experience Manager] Assets中設定Assets Insights。
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Admin
exl-id: b0d62dd3-1868-4d73-95f7-3d6c3ff474d9
source-git-commit: a778c3bbd0e15bb7b6de2d673b4553a7bd146143
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 10%

---

# 設定Assets Insights {#configuring-asset-insights}

Adobe Experience Manager Assets會從Adobe Analytics擷取協力廠商網站所使用資產的使用資料[!DNL Experience Manager]。 若要讓Assets Insights能夠擷取此資料並產生深入分析，請先設定功能以與Adobe Analytics整合。

>[!NOTE]
>
>僅支援並提供影像見解。

1. 在 AEM 中，按一下&#x200B;**[!UICONTROL 「工具」>「資產」]**。

   ![chlimage_1-210](assets/chlimage_1-210.png)

1. 按一下「 **[!UICONTROL 前瞻分析設定]** 」資訊卡。
1. 在精靈中，選取資料中心並提供您的認證，包括組織名稱、使用者名稱和密碼。

   ![chlimage_1-211](assets/insights_config2.png)

1. 按一下/點選「 **[!UICONTROL 驗證]**」。
1. 在[!DNL Experience Manager]驗證您的憑證後，從&#x200B;**[!UICONTROL 報表套裝]**&#x200B;清單中，選擇您要讓Assets Insights擷取資料的Adobe Analytics報表套裝。 按一下&#x200B;**[!UICONTROL 「新增」]**。
1. 在[!DNL Experience Manager]設定報表套裝後，按一下/點選&#x200B;**[!UICONTROL Done]**。

## 頁面追蹤器 {#page-tracker}

設定Analytics帳戶後，系統會為您產生頁面追蹤器程式碼。 若要啟用「資產前瞻分析」以追蹤第三方網站中使用的[!DNL Experience Manager]資產，請在網站程式碼中加入頁面追蹤器程式碼。 使用[!DNL Experience Manager]資產中的頁面追蹤器公用程式來產生頁面追蹤器程式碼。 如需如何將您的頁面追蹤器程式碼納入第三方網頁的詳細資訊，請參閱[在網頁中使用頁面追蹤器及內嵌程式碼](touch-ui-using-page-tracker.md)。

1. 在AEM中，按一下&#x200B;**[!UICONTROL 工具>資產]**。

   ![chlimage_1-214](assets/chlimage_1-214.png)

1. 在導覽頁 **[!UICONTROL 面中]** ，按一下 **** 前瞻分析頁面追蹤器卡片。
1. 按一下&#x200B;**[!UICONTROL 下載]**&#x200B;圖示以下載頁面追蹤器程式碼。

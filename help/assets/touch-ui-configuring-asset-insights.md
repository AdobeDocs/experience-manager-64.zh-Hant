---
title: 設定資產分析
description: 瞭解如何在AEM Assets中設定資產分析。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 10%

---


# 設定資產分析{#configuring-asset-insights}

Adobe Experience Manager(AEM)Assets會從Adobe Analytics擷取協力廠商網站所使用之AEM資產的使用資料。 若要讓「資產前瞻分析」擷取此資料並產生前瞻分析，請先設定功能以與Adobe Analytics整合。

>[!NOTE]
>
>只有影像才支援並提供見解。

1. 在 AEM 中，按一下&#x200B;**[!UICONTROL 「工具」>「資產」]**。

   ![chlimage_1-210](assets/chlimage_1-210.png)

1. 按一下「 **[!UICONTROL 前瞻分析設定]** 」資訊卡。
1. 在嚮導中，選擇資料中心並提供您的憑據，包括組織名稱、用戶名和密碼。

   ![chlimage_1-211](assets/insights_config2.png)

1. 按一下/點選「 **[!UICONTROL 驗證]**」。
1. AEM驗證您的認證後，從&#x200B;**[!UICONTROL 報表套裝]**&#x200B;清單中，選擇Adobe Analytics報表套裝，讓您從中擷取資產分析。 按一下&#x200B;**[!UICONTROL 「新增」]**。
1. AEM設定您的報表套裝後，按一下／點選&#x200B;**[!UICONTROL Done]**。

## 頁面追蹤器{#page-tracker}

在您設定Analytics帳戶後，就會產生頁面追蹤器代碼。 若要啟用「資產前瞻分析」來追蹤協力廠商網站中使用的AEM資產，請在網站程式碼中加入頁面追蹤器程式碼。 使用AEM Assets中的「頁面追蹤器」公用程式來產生頁面追蹤器代碼。 如需如何在協力廠商網頁中加入頁面追蹤程式碼的詳細資訊，請參閱[在網頁中使用頁面追蹤程式碼和內嵌程式碼](touch-ui-using-page-tracker.md)。

1. 在AEM中，按一下「**[!UICONTROL 工具>資產]**」。

   ![chlimage_1-214](assets/chlimage_1-214.png)

1. 在導覽頁 **[!UICONTROL 面中]** ，按一下 **** 前瞻分析頁面追蹤器卡片。
1. 按一下&#x200B;**[!UICONTROL 下載]**&#x200B;圖示以下載頁面追蹤器代碼。
---
title: 使用起始點
seo-title: Working with Startpoints
description: 從Workbench中定義的行動裝置使用AEM Forms程式的步驟。
seo-description: Steps to work with a AEM Forms process from your Mobile device defined in Workbench.
uuid: 9c51ce52-e7ba-43d3-a85c-67067f680ccb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 265eee8a-364e-4edf-b2a0-f42617169944
exl-id: ef9352c7-c164-4cbf-8f18-5b97aa5f56be
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 1%

---

# 使用起始點 {#working-with-startpoints}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

起始點調用在Workbench中建立的進程。 它與表單關聯，表單提交時該表單將調用該流程。 請參閱 [Geometrixx金融參考網站逐步說明](/help/forms/using/finance-reference-site-walkthrough.md) 了解流程。

>[!NOTE]
>
>提及此概念時，術語起始點、開始程式和表單可交互使用。

若要從AEM Forms應用程式啟動程式，您必須具備類型的起始點 **工作區** 在您的程式中。 此外，您需要選取 **[!UICONTROL 顯示於行動工作區]** 選項。

![mws_startpoint_select_option](assets/mws_startpoint_select_option.png)

**要啟動在Workbench中定義的流程，請執行以下操作**

1. 若要檢視AEM Forms應用程式中可用的起始點，請前往 [主畫面](/help/forms/using/home-screen.md).
1. 在 **[!UICONTROL 首頁]** 螢幕，依預設， **[!UICONTROL 全部Forms]** 清單。

   起始點與表單相關聯。 點選清單中的起始點關聯表單以開啟它。

   將開啟與起始點關聯的表單。

1. 在 **[!UICONTROL 起始點]** 表單。

   您可以使用 [附件](/help/forms/using/add-attachments.md) 按鈕。

1. 填寫表單後，點選 **提交** 按鈕。

如果應用程式離線，表單及其資料會儲存在「寄件匣」資料夾中。

如果應用程式上線，則任務會與AEM Forms伺服器同步，並指派給程式中指定的使用者。

要處理任務清單中的任務，請參閱 [開啟任務](/help/forms/using/open-task.md).

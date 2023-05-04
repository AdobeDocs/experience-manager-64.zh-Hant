---
title: 將您的反向連結篩選器設為允許空白
seo-title: Setting Your Referrer Filter to Allow Empty
description: 請詳閱本頁面，了解反向連結篩選。 若要允許AEM Mobile應用程式檢視器檢視您的Author例項上的應用程式，您必須將HTML反向連結篩選器設為「允許空白」。
seo-description: Follow this page to learn about Referrer Filter. In order to allow the AEM Mobile Application Viewer to view apps on your Author instance, you'll need to set your HTML referrer filter to 'allow empty'.
uuid: 4fb0f95c-ac8f-4a14-8c46-6616d9d4f380
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
discoiquuid: 8fb7d088-94bf-4799-98b3-8fa58eef83df
exl-id: 81828b4c-cf0f-4722-8ae3-2e24be91a09b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 3%

---

# 將您的反向連結篩選器設為允許空白{#setting-your-referrer-filter-to-allow-empty}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>Adobe建議針對需要單頁應用程式架構用戶端轉譯（例如React）的專案使用SPA編輯器。 [深入了解](/help/sites-developing/spa-overview.md).

若要允許AEM Mobile應用程式檢視器檢視您的Author例項上的應用程式，您必須將HTML反向連結篩選器設為「允許空白」。

如果您不想使用「應用程式檢視器」來檢閱開發和測試狀態中的應用程式，則不需要變更反向連結篩選器的預設設定。

在您執行中的AEM Author例項中，導覽至： [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr) 和搜尋「Apache Sling Referrer Filter」。 按一下以編輯反向連結篩選器並勾選「允許空白」核取方塊（請參閱下圖）。 下一步按「儲存」按鈕並關閉瀏覽器頁面。

![反向連結篩選設定](assets/chlimage_1-106.png)

---
title: 選擇匯總的使用情況統計資訊收集
seo-title: Opting Into Aggregated Usage Statistics Collection
description: 了解如何選擇匯總的使用量統計資料。
seo-description: Learn how to opt into aggregated usage statistics.
uuid: 835fd281-da4f-42ef-bae8-9ca91a29bc65
contentOwner: raiman
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 0c2b1c67-2fa4-4b2e-8512-0973177656e2
exl-id: f3cfa30a-ca15-48db-bacf-1aebbd0ad458
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 3%

---

# 選擇匯總的使用情況統計資訊收集{#opting-into-aggregated-usage-statistics-collection}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 簡介 {#introduction}

您可以傳送與AEM互動的Adobe統計資料，協助改善Adobe Marketing Cloud。 此資訊不包含任何有關您公司網站訪客的資料，且僅用於協助Adobe提供、支援及改善您的使用者體驗。

您可以使用觸控式UI或Web主控台，選擇加入使用量統計資料收集。

>[!NOTE]
>
>有各種資料保護和隱私法規；包括，例如GDPR和CCPA。 AEM Sites已準備好協助客戶履行其資料保護和隱私權法規遵循義務。 此頁面會引導客戶完成選擇加入（或退出）匯總使用量統計資料收集的程式。
>
>如需詳細資訊，另請參閱 [Adobe的隱私中心](https://www.adobe.com/tw/privacy.html).

>[!NOTE]
>
>您也可以隨時選擇退出，方法是使用 [Web主控台](/help/sites-deploying/opt-in-aggregated-usage-statistics.md#opt-in-by-using-the-web-console) 或不在AEM選擇加入畫面上選取選擇加入選項。

## 使用觸控式UI選擇加入 {#opt-in-by-using-the-touch-ui}

首次啟動AEM時，您可以使用觸控式UI選擇加入，如下所示：

1. 在AEM導覽畫面上，按一下 **收件匣** （鈴）表徵圖。

   ![usage_statisticsnavigationscreen](assets/usage_statisticsnavigationscreen.png)

1. 在下拉式清單中，按一下「**啟用匯總的使用情況統計資訊收集**」。

   ![usage_statisticsnavigationscreen2](assets/usage_statisticsnavigationscreen2.png)

1. 在選擇加入畫面上，選取「**允許收集匯總的使用量統計資訊**」。

   ![usage_statisticsopt_inscreen](assets/usage_statisticsopt-inscreen.png)

1. 按一下「**完成**」。

## 使用Web主控台選擇加入 {#opt-in-by-using-the-web-console}

您可以使用Web主控台選擇加入（或選擇退出），如下所示：

1. 在AEM導覽畫面上，按一下 **工具** 然後 **操作**.

   ![usage_statisticssopshaboard](assets/usage_statisticsopsdashboard.png)

1. 在「操作」(Operations)窗口中，按一下 **Web主控台**.

   ![usage_statisticswebconsole](assets/usage_statisticswebconsole.png)

1. 搜索「**匯總使用情況統計資訊收集**」。
1. 按一下 **編輯** 表徵圖。

   ![usage_statisticscollectionedit](assets/usage_statisticscollectionedit.png)

1. 選取 **已啟用** 核取方塊。 或者，如果您要選擇退出使用狀況統計資料收集，可以取消選取核取方塊。

   ![usage_statisticsselect](assets/usage_statisticsselect.png)

1. 按一下「**儲存**」。

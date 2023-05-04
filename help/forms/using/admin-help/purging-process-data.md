---
title: 清除流程資料
seo-title: Purging process data
description: 調用長壽命進程時生成的進程資料可能會變得太大，導致AEM表單效能降低，並且會使用不必要的磁碟空間。 了解如何清除流程資料。
seo-description: Process data that is generated when a long-lived process is invoked can become too large, resulting in lower AEM forms performance and the use of unnecessary disk space. See how you can purge process data.
uuid: 2f04452c-71c6-452c-88c2-7560d35e7dec
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 3157bb92-4b07-40f2-be4c-8f5807f9a380
exl-id: ecedde63-abbb-4e69-901e-1e4b7a59f539
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 2%

---

# 清除流程資料 {#purging-process-data}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

調用長壽命進程時生成的進程資料可能會變得太大，導致AEM表單效能降低，並且會使用不必要的磁碟空間。 當不再需要記錄時，最好清除流程資料。 AEM forms提供多種清除程式資料的方式：

* 您可以使用管理控制台執行與長期流程相關的過時記錄的一次性清除，或計畫定期自動清除。 (請參閱 [從作業管理員資料庫中清除記錄](/help/forms/using/admin-help/purge-records-job-manager-database.md#purge-records-from-the-job-manager-database).)
* 您可以使用AEM Forms Java API和網站服務API，以程式設計方式清除與長期程式相關的程式資料。 (請參閱 [使用AEM表單進行程式設計](https://www.adobe.com/go/learn_aemforms_programming_63).)
* 使用流程清除工具根據流程名稱和其他參數清除流程。 有關詳細資訊，請參閱流程清除工具自述檔案，位於 *[aem_forms根]*\sdk\misc\Foundation\ProcessPurgeTool\ReadMe.txt。

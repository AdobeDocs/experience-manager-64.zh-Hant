---
title: '"DB2資料庫：每週運行進程」'
seo-title: "DB2 database: Running a process weekly"
description: 了解如何改進AEM Forms DB2資料庫的效能。
seo-description: See how you can improve the performance of your AEM forms DB2 database.
uuid: 36070087-c250-41df-a841-aa922e777697
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: fc0e8183-5d50-4fc0-997a-5f3168ba0d70
exl-id: f40fcfab-63e0-4e43-aac5-95426e3dd1fb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 2%

---

# DB2資料庫：每週運行進程{#db-database-running-a-process-weekly}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

如果您的AEM表單DB2資料庫開始緩慢執行，每週執行下列程式可改善其效能：

1. 啟動DB2控制中心：

   (Windows)選擇「開始」>「程式」>「IBM DB2」>「常規管理工具」>「控制中心」。

   （Linux和UNIX）在命令提示符下，鍵入 `db2jcc` 命令。

1. 在DB2控制中心對象樹中，按一下所有資料庫。
1. 按一下為AEM表單建立的資料庫，然後按一下表格資料夾。
1. 選擇「內容」窗格中的所有資料庫表，按一下右鍵並選擇「運行統計資訊」。
1. 轉至「統計>索引統計」。
1. 選擇收集所有索引的統計資訊，選擇收集具有擴展詳細統計資訊的索引的統計資訊，然後按一下確定。

進程完成時，將顯示一條消息。 關閉訊息。

---
title: Oracle資料庫最大開啟游標閾值
seo-title: Oracle database maximum open cursors threshold
description: 了解如何為Oracle中開啟的游標配置最大值。
seo-description: Learn about configuring a maximum value for open cursors in Oracle.
uuid: c1d20997-f853-4772-b1c6-8cea73221d0a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d3565776-1b7d-498c-9840-b17f80170d9b
exl-id: ad14ff27-964f-481f-a8ef-052d9cfb7734
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 4%

---

# Oracle資料庫最大開啟游標閾值 {#oracle-database-maximum-open-cursors-threshold}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

要為Oracle中開啟的游標配置最大值，您可能需要將此值調整為適合您的應用程式的數字。 顯然，在中等負載下，開啟的游標平均數為2700。 建議您從3000的上限開始。 如需詳細資訊，請前往 [https://www.orafaq.com/node/758](https://www.orafaq.com/node/758).

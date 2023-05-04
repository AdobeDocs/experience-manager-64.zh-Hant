---
title: EMC Documentum用戶的Connector備份策略
seo-title: Backup strategy for Connector for EMC Documentum users
description: 檢查如何為EMC Documentum用戶建立Connector備份策略。
seo-description: Check how to create a backup strategy for Connector for EMC Documentum users.
uuid: 5d8a0476-5231-4e1d-96c4-ae3df68e09f0
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e83b1a59-a730-4d22-9d58-1c9c38e5d534
exl-id: 933c3903-2040-41f4-b803-4d672ce9a2dc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 2%

---

# EMC Documentum用戶的Connector備份策略 {#backup-strategy-for-connector-for-emc-documentum-users}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

如果安裝了EMC Documentum的連接器，則除本章中的說明外，您的備份和恢復策略必須包括備份（或恢復）各個ECM系統所安裝的電腦。 （請參閱ECM Documentum文檔）。

使用ECM存放庫並執行下列工作，以備份AEM表單環境：

* 依照本檔案所述的指示備份AEM表單。
* 按照 [備份EMC Documentum Content Server](/help/forms/using/admin-help/backing-recovering-emc-documentum-repository.md#back-up-the-emc-documentum-content-server).

使用ECM存放庫並執行下列作業，以還原AEM表單環境：

* 按照 [恢復EMC Documentum Content Server](/help/forms/using/admin-help/backing-recovering-emc-documentum-repository.md#restore-the-emc-documentum-content-server).
* 依照本檔案所述的指示還原AEM表單。

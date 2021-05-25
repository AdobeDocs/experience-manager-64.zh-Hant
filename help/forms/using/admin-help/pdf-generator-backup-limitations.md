---
title: PDF產生器備份限制
seo-title: PDF產生器備份限制
description: 了解PDF產生器備份限制。
seo-description: 了解PDF產生器備份限制。
uuid: 9537ffde-4396-46d1-81ea-edcd25923ffb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 23386353-b2bf-49f1-947a-dd7587bba175
noindex: true
exl-id: d2ba9881-02b6-470b-b110-7d4609e6ab24
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# PDF生成器備份限制{#pdf-generator-backup-limitations}

無法備份PDF生成器用於轉換檔案的臨時目錄。 即使服務會正確還原，資料仍會遺失，因為PDF產生器會以設定的間隔檢閱並清除暫時目錄的內容。

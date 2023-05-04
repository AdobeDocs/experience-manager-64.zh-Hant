---
title: 啟用和禁用安全備份模式
seo-title: Enabling and disabling safe backup mode
description: 在「備份設定」頁上，您可以以安全備份模式操作AEM表單，以便可靠地備份資料庫和全局文檔儲存(GDS)(GDS)目錄。 了解如何啟用和禁用安全備份模式。
seo-description: On the Backup Settings page, you can operate AEM forms in safe backup mode so that you can reliably back up your database and Global Document Storage (GDS) (GDS) directory. Learn how to enable and disable safe backup mode.
uuid: 2fdeaeaf-e969-40a4-8aee-1f2b627d3942
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9fda71e4-78a1-4581-9d02-bf06a75c3bcb
exl-id: 309a8cef-e84d-485b-9a7c-786a93e83c85
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 2%

---

# 啟用和禁用安全備份模式 {#enabling-and-disabling-safe-backup-mode}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

在「備份設定」頁上，您可以以安全備份模式操作AEM表單，以便可靠地備份資料庫和全局文檔儲存(GDS)(GDS)目錄。

雖然AEM表單處於安全備份模式，但它正常運行，只是它沒有主動從GDS目錄中刪除檔案。

>[!NOTE]
>
>設定此選項不會備份您的系統；它為備份準備了系統。

## 啟用安全備份模式 {#enable-safe-backup-mode}

1. 在管理控制台中，按一下「設定」>「核心繫統設定」>「備份設定」。
1. 在「備份設定」頁上，選擇「在安全備份模式下操作」 ，然後按一下「確定」。

>[!NOTE]
>
>如果系統已在安全備份模式下運行，則按一下「確定」時將不會建立新保留。

## 禁用安全備份模式 {#disable-safe-backup-mode}

1. 在管理控制台中，按一下「設定」>「核心繫統設定」>「備份設定」。
1. 在「備份設定」頁上，取消選擇「在安全備份模式下操作」，然後按一下「確定」。

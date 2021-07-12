---
title: 設定最適化表單快取
seo-title: 設定最適化表單快取
description: '最適化表單快取是專為最適化表單和檔案而設計。 它快取最適化表單和最適化檔案，以縮短在用戶端上轉譯最適化表單或檔案所需的時間。 '
seo-description: '最適化表單快取是專為最適化表單和檔案而設計。 它快取最適化表單和最適化檔案，以縮短在用戶端上轉譯最適化表單或檔案所需的時間。 '
uuid: 3bd4e405-1eab-4e02-95cd-eb6ac25d18e3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: dd18f7b5-882d-4e81-ab3d-85f1e5d74992
role: Admin
exl-id: 6a610e9d-beec-486d-b1d2-78b5fec44c52
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 1%

---

# 設定最適化表單快取 {#configure-adaptive-forms-cache}

快取是一種縮短資料存取時間、減少延遲並改善輸入/輸出(I/O)速度的機制。 適用性表單快取僅會儲存適用性表單的HTML內容和JSON結構，而不儲存任何預先填入的資料。 有助於縮短在用戶端上轉譯最適化表單或檔案所需的時間。 專為最適化表單而設計，也支援最適化檔案。

>[!NOTE]
>
>使用最適化表單快取時，請使用AEM Dispatcher來快取適用性表單或檔案的用戶端程式庫（CSS和JavaScript）。

>[!NOTE]
>
>開發自訂元件時，請在用於開發的伺服器上，停用最適化表單快取。

## 配置快取 {#configure-the-cache}

執行下列步驟以設定最適化表單快取：

1. 前往`https://[server]:[port]/system/console/configMgr`的AEM Web主控台組態管理器。
1. 按一下「**適用性表單和互動式通訊Web通道配置**」以編輯其配置值。
1. 在「編輯配置值」對話方塊中，在「**適用性Forms數量**」欄位中指定AEM Forms伺服器例項可快取的表單或檔案數上限。 預設值為 100。

   >[!NOTE]
   >
   >若要停用快取，請將「適用性Forms數量」欄位中的值設為&#x200B;**0**。 當禁用或更改快取配置時，將重置快取，並從快取中刪除所有表單和文檔。

   ![適用性表單HTML快取的設定對話方塊](assets/cache-configuration-edit.png)

1. 按一下&#x200B;**儲存**&#x200B;以儲存設定。

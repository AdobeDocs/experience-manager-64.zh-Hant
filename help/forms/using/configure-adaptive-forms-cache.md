---
title: 配置自適應表單快取
seo-title: 配置自適應表單快取
description: '最適化表單快取是專為最適化表單和檔案而設計。 它快取最適化表單和最適化檔案，以縮短在用戶端上轉換最適化表單或檔案所需的時間。 '
seo-description: '最適化表單快取是專為最適化表單和檔案而設計。 它快取最適化表單和最適化檔案，以縮短在用戶端上轉換最適化表單或檔案所需的時間。 '
uuid: 3bd4e405-1eab-4e02-95cd-eb6ac25d18e3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: dd18f7b5-882d-4e81-ab3d-85f1e5d74992
translation-type: tm+mt
source-git-commit: 49b7cff2c1583ee1eb929434f27c1989558e197f
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---


# 配置自適應表單快取{#configure-adaptive-forms-cache}

快取是縮短資料存取時間、減少延遲並改善輸入／輸出(I/O)速度的機制。 最適化表單快取只儲存最適化表單的HTML內容和JSON結構，而不儲存任何預先填入的資料。 它有助於縮短在用戶端上轉換最適化表單或檔案所需的時間。 它專為最適化表單而設計，也支援最適化檔案。

>[!NOTE]
>
>使用最適化表單快取時，請使用AEM Dispatcher快取最適化表單或檔案的用戶端程式庫（CSS和JavaScript）。

>[!NOTE]
>
>在開發自訂元件時，在用於開發的伺服器上，請停用最適化表單快取。

## 配置快取{#configure-the-cache}

執行以下步驟以配置自適應表單快取：

1. 前往`https://[server]:[port]/system/console/configMgr`的AEM網頁主控台組態管理器。
1. 按一下&#x200B;**自適應表單和互動式通信Web通道配置**&#x200B;以編輯其配置值。
1. 在編輯設定值對話方塊中，在&#x200B;**Number of Adaptive Forms**&#x200B;欄位中指定AEM Forms伺服器執行個體可快取的表單或檔案數上限。 預設值為100。

   >[!NOTE]
   >
   >要禁用快取，請將「最適化表單數」欄位中的值設定為&#x200B;**0**。 當禁用或更改快取配置時，將重置快取，並從快取中刪除所有表單和文檔。

   ![最適化表單HTML快取的設定對話方塊](assets/cache-configuration-edit.png)

1. 按一下&#x200B;**保存**&#x200B;保存配置。


---
title: 一致性和遍歷檢查
seo-title: Consistency and Traversal Checks
description: 了解如何執行一致性和周遊檢查。
seo-description: Learn how to perform consistency and traversal checks.
uuid: 0304e378-7c60-4bf5-9052-d01149d2a6df
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
discoiquuid: af9a3e9d-194a-42e5-be28-b238e0c1e55e
feature: Configuring
exl-id: 67dfa0f7-24ac-41ae-83c9-3bb1a8656502
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 3%

---

# 一致性和遍歷檢查{#consistency-and-traversal-checks}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

升級時，工作區不一致可能會造成問題。 您可以運行測試升級以查看這是否是問題，或者以預防性操作的方式運行一致性檢查。

如果您執行因工作區不一致而失敗的測試升級，您會在crx-quickstart/logs/crx/error.log中看到類似下列的項目：

```xml
*ERROR* TarPersistenceManager: No bundle found for uuid 'deadbeef-cafe-babe-cafe-babecafebabe'
 ...
*ERROR* RepositoryImpl: Failed to initialize workspace 'crx.default'
javax.jcr.RepositoryException: Error indexing workspace: Error indexing workspace: Error indexing workspace
...
```

## 執行一致性檢查 {#perform-a-consistency-check}

要執行一致性檢查，請導航到JMX Mbean** com.adobe.granite（儲存庫）**的管理頁。 從AEM主畫面，前往：

**「工具」>「Web控制台」>「主（在菜單欄上）」>「JMX」>「com.adobe.granite（儲存庫）」**

在預設安裝中，可在以下位置找到：  **[|顯示我|](http://localhost:4502/system/console/jmx/com.adobe.granite%3Atype%3DRepository)**

在 **操作** 區段，您會找到兩種方法： **`traversalCheck`** 和 **`consistencyCheck`**. 要執行檢查，請按一下操作並輸入所需的參數。

![chlimage_1-117](assets/chlimage_1-117.png)

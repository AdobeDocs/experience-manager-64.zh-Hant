---
title: Granite操作 — 使用者和群組管理
seo-title: Granite操作 — 使用者和群組管理
description: 了解Granite使用者和群組管理。
feature: 安全性
seo-description: 了解Granite使用者和群組管理。
uuid: 7b6b7767-712c-4cc8-8d90-36f26280d6e3
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 95ab2e54-0f8d-49e0-ad20-774875f6f80a
exl-id: bd29e81d-eb4a-4764-96f2-84e091836a8a
source-git-commit: 40a4e01eea3e20fda6d0b2c8af985f905039e320
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 4%

---

# Granite操作 — 用戶和組管理{#granite-operations-user-and-group-administration}

由於Granite併入了JCR API規格的CRX存放庫實作，因此有其自己的使用者和群組管理。

這些帳戶是[AEM帳戶](/help/sites-administering/security.md)的基礎，若/當透過[AEM使用者主控台](/help/sites-administering/security.md#accessing-user-administration-with-the-security-console)存取帳戶時，會反映透過Granite管理所做的任何帳戶變更(例如`http://localhost:4502/useradmin`)。 從AEM使用者主控台，您也可以管理權限和其他AEM詳細資訊。

觸控最佳化UI的&#x200B;**[Tools](/help/sites-administering/tools-consoles.md)**&#x200B;主控台均提供Granite使用者和群組管理主控台：

![chlimage_1-72](assets/chlimage_1-72.png)

從工具控制台選擇&#x200B;**用戶**&#x200B;或&#x200B;**組**&#x200B;將開啟相應的控制台。 在這兩個選項中，您都可以使用點選方塊，然後從工具列執行動作，或透過&#x200B;**Name**&#x200B;下的連結開啟帳戶詳細資訊。

* [使用者管理](#user-administration)

   ![chlimage_1-73](assets/chlimage_1-73.png)

   **Users**&#x200B;控制台列出：

   * 用戶名
   * 使用者登入名稱（帳戶名稱）
   * 帳戶獲得的任何標題

* [群組管理](#group-administration)

   ![chlimage_1-74](assets/chlimage_1-74.png)

   **群組**&#x200B;控制台列出：

   * 群組名稱
   * 群組說明
   * 群組中的使用者/群組數

## 用戶管理{#user-administration}

### 添加新用戶{#adding-a-new-user}

1. 使用&#x200B;**Add User**&#x200B;表徵圖：

   ![](do-not-localize/chlimage_1-1.png)

1. 將開啟「**建立用戶**」表單：

   ![chlimage_1-75](assets/chlimage_1-75.png)

   您可以在此處輸入帳戶的使用者詳細資訊（大多為標準且不言自明）:

   * **ID**

      這是使用者帳戶的唯一識別碼。 此為必填項目，不能包含空格。

   * **電子郵件地址**
   * **密碼**

      密碼是必填的。

   * **重新鍵入密碼**

      這是強制性的，因為這是確認密碼所需的。

   * **名字**
   * **姓氏**
   * **電話號碼**
   * **職稱**
   * **街道**
   * **行動**
   * **城市**
   * **郵遞區號**
   * **國家/地區**
   * **狀態**
   * **標題**
   * **性別**
   * **關於**
   * **帳戶設定**

      * ****
狀態您可以將帳戶標幟為 
**** 使用中或 **非使用中**。
   * **相片**

      您可以在此上傳像片以作為頭像。

      接受的檔案類型: `.jpg .png .tif .gif`

      首選大小：`240x240px`

   * **新增使用者至群組**

      使用「選擇」下拉清單選擇用戶應是其成員的組。 選取後，在儲存之前，請使用名稱的&#x200B;**X**&#x200B;來取消選取。

   * **群組**

      用戶當前所屬的組的清單。 在保存之前，使用名稱&#x200B;**X**&#x200B;取消選擇。


1. 定義使用者帳戶時：

   * **** 取消中止註冊。
   * **** 薩韋托完成註冊。系統會以訊息確認使用者帳戶的建立。

### 編輯現有用戶{#editing-an-existing-user}

1. 從「使用者」主控台中使用者名稱下的連結存取使用者詳細資訊。

1. 您現在可以編輯[新增使用者](#adding-a-new-user)中的詳細資訊。

1. 從「使用者」主控台中使用者名稱下的連結存取使用者詳細資訊。

1. 您現在可以編輯[新增使用者](#adding-a-new-user)中的詳細資訊。

### 更改現有用戶{#changing-the-password-for-an-existing-user}的密碼

1. 從「使用者」主控台中使用者名稱下的連結存取使用者詳細資訊。

1. 您現在可以編輯[新增使用者](#adding-a-new-user)中的詳細資訊。 在&#x200B;**帳戶設定**&#x200B;下面有&#x200B;**更改密碼**&#x200B;的連結。

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. 將開啟「**更改密碼**」對話框。 輸入並重新鍵入新密碼以及密碼。 使用&#x200B;**OK**&#x200B;確認更改。

   ![chlimage_1-77](assets/chlimage_1-77.png)

   訊息會確認密碼已變更。

### 快速組分配{#quick-group-assignment}

1. 使用點按方塊來標幟一或多個使用者。
1. 使用&#x200B;**Groups**&#x200B;圖示：

   ![](do-not-localize/chlimage_1-2.png)

   要開啟組選擇下拉清單：

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. 在選取方塊中，您可以選取或取消選取使用者帳戶應屬於的群組。

1. 當您已指派或未指派群組時，請視需要使用：

   * **** 取消中止更改
   * **** Saveto確認變更

### 刪除現有用戶詳細資訊{#deleting-existing-user-details}

1. 使用點按方塊來標幟一或多個使用者。
1. 使用&#x200B;**Delete**&#x200B;圖示來刪除使用者詳細資訊：

   ![](do-not-localize/chlimage_1-3.png)

1. 系統會要求您確認刪除，然後會傳送訊息確認確實已發生刪除。

## 組管理{#group-administration}

### 添加新組{#adding-a-new-group}

1. 使用「新增群組」圖示：

   ![](do-not-localize/chlimage_1-4.png)

1. 將開啟「**建立組**」表單：

   ![chlimage_1-79](assets/chlimage_1-79.png)

   您可以在此處輸入群組詳細資訊：

   * **ID**

      這是群組的唯一識別碼。 此為必填項目，不能包含空格。

   * **名稱**

      組的名稱；它將顯示在「組」控制台中。

   * **說明**

      群組的說明。

   * **新增成員到群組**

      使用「選取」下拉式清單來選取要新增至群組的使用者。 選取後，在儲存之前，請使用名稱的&#x200B;**X**&#x200B;來取消選取。

   * **群組成員**

      群組中的使用者清單。 在保存之前，使用名稱&#x200B;**X**&#x200B;取消選擇。

1. 定義群組後，請使用：

   * **** 取消中止註冊。
   * **** 薩韋托完成註冊。將用消息確認組的建立。

### 編輯現有組{#editing-an-existing-group}

1. 從「群組」控制台中群組名稱下的連結存取群組詳細資訊。

1. 您現在可以在[新增群組](#adding-a-new-group)中編輯並儲存詳細資料。

### 複製現有組{#copying-an-existing-group}

1. 使用點按方塊來標幟群組。
1. 使用&#x200B;**Copy**&#x200B;圖示來複製群組詳細資訊：

   ![](do-not-localize/chlimage_1-5.png)

1. 將開啟「**編輯組設定**」表單。

   群組ID將與原始ID相同，但前置詞為`Copy of`。 由於ID不能包含空格，因此您必須編輯此檔案。 其他所有詳細資訊將與原始資訊相同。

   您現在可以在[新增群組](#adding-a-new-group)中編輯並儲存詳細資料。

### 刪除現有組{#deleting-an-existing-group}

1. 使用點按方塊來標幟一或多個群組。
1. 使用&#x200B;**Delete**&#x200B;圖示來刪除群組詳細資訊：

   ![](do-not-localize/chlimage_1-6.png)

1. 系統會要求您確認刪除，然後會傳送訊息確認確實已發生刪除。

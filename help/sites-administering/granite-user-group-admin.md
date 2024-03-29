---
title: Granite操作 — 使用者和群組管理
seo-title: Granite Operations - User and Group Administration
description: 了解Granite使用者和群組管理。
feature: Security
seo-description: Learn about Granite user and group administration.
uuid: 7b6b7767-712c-4cc8-8d90-36f26280d6e3
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 95ab2e54-0f8d-49e0-ad20-774875f6f80a
exl-id: bd29e81d-eb4a-4764-96f2-84e091836a8a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 5%

---

# Granite操作 — 使用者和群組管理{#granite-operations-user-and-group-administration}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

由於Granite併入了JCR API規格的CRX存放庫實作，因此有其自己的使用者和群組管理。

該等賬目乃本集團根 [AEM帳戶](/help/sites-administering/security.md) 若/當透過 [AEM Users Console](/help/sites-administering/security.md#accessing-user-administration-with-the-security-console) (例如 `http://localhost:4502/useradmin`)。 從AEM使用者主控台，您也可以管理權限和其他AEM詳細資訊。

Granite使用者和群組管理主控台均可從 **[工具](/help/sites-administering/tools-consoles.md)** 觸控最佳化UI的主控台：

![chlimage_1-72](assets/chlimage_1-72.png)

選擇 **使用者** 或 **群組** 從「工具」控制台開啟適當的控制台。 在這兩個選項中，您都可以使用點按方塊，然後從工具列執行動作，或透過下方的連結開啟帳戶詳細資訊 **名稱**.

* [使用者管理](#user-administration)

   ![chlimage_1-73](assets/chlimage_1-73.png)

   此 **使用者** 控制台清單：

   * 用戶名
   * 使用者登入名稱（帳戶名稱）
   * 帳戶獲得的任何標題

* [群組管理](#group-administration)

   ![chlimage_1-74](assets/chlimage_1-74.png)

   此 **群組** 控制台清單：

   * 群組名稱
   * 群組說明
   * 群組中的使用者/群組數

## 使用者管理 {#user-administration}

### 新增使用者 {#adding-a-new-user}

1. 使用 **添加用戶** 圖示：

   ![](do-not-localize/chlimage_1-1.png)

1. 此 **建立使用者** 表單會開啟：

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

      * **狀態**
您可以將帳戶標幟為 
**活動** 或 **非活動**.
   * **相片**

      您可以在此上傳像片以作為頭像。

      接受的檔案類型: `.jpg .png .tif .gif`

      首選大小： `240x240px`

   * **新增使用者至群組**

      使用「選擇」下拉清單選擇用戶應是其成員的組。 選取後，請使用 **X** 名稱取消選取，再儲存。

   * **群組**

      用戶當前所屬的組的清單。 使用 **X** 名稱取消選取，再儲存。


1. 定義使用者帳戶時：

   * **取消** 中止註冊。
   * **儲存** 完成註冊。 系統會以訊息確認使用者帳戶的建立。

### 編輯現有使用者 {#editing-an-existing-user}

1. 從「使用者」主控台中使用者名稱下的連結存取使用者詳細資訊。

1. 您現在可以編輯詳細資訊，如 [新增使用者](#adding-a-new-user).

1. 從「使用者」主控台中使用者名稱下的連結存取使用者詳細資訊。

1. 您現在可以編輯詳細資訊，如 [新增使用者](#adding-a-new-user).

### 更改現有用戶的密碼 {#changing-the-password-for-an-existing-user}

1. 從「使用者」主控台中使用者名稱下的連結存取使用者詳細資訊。

1. 您現在可以編輯詳細資訊，如 [新增使用者](#adding-a-new-user). 在 **帳戶設定** 有 **更改密碼**.

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. 此 **更改密碼** 對話框將開啟。 輸入並重新鍵入新密碼以及密碼。 使用 **確定** 以確認變更。

   ![chlimage_1-77](assets/chlimage_1-77.png)

   訊息會確認密碼已變更。

### 快速組分配 {#quick-group-assignment}

1. 使用點按方塊來標幟一或多個使用者。
1. 使用 **群組** 圖示：

   ![](do-not-localize/chlimage_1-2.png)

   要開啟組選擇下拉清單：

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. 在選取方塊中，您可以選取或取消選取使用者帳戶應屬於的群組。

1. 當您已指派或未指派群組時，請視需要使用：

   * **取消** 中止變更
   * **儲存** 確認變更

### 刪除現有用戶詳細資訊 {#deleting-existing-user-details}

1. 使用點按方塊來標幟一或多個使用者。
1. 使用 **刪除** 表徵圖刪除用戶詳細資訊：

   ![](do-not-localize/chlimage_1-3.png)

1. 系統會要求您確認刪除，然後會傳送訊息確認確實已發生刪除。

## 群組管理 {#group-administration}

### 新增群組 {#adding-a-new-group}

1. 使用「新增群組」圖示：

   ![](do-not-localize/chlimage_1-4.png)

1. 此 **建立群組** 表單會開啟：

   ![chlimage_1-79](assets/chlimage_1-79.png)

   您可以在此處輸入群組詳細資訊：

   * **ID**

      這是群組的唯一識別碼。 此為必填項目，不能包含空格。

   * **名稱**

      組的名稱；它將顯示在「組」控制台中。

   * **說明**

      群組的說明。

   * **新增成員到群組**

      使用「選取」下拉式清單來選取要新增至群組的使用者。 選取後，請使用 **X** 名稱取消選取，再儲存。

   * **群組成員**

      群組中的使用者清單。 使用 **X** 名稱取消選取，再儲存。

1. 定義群組後，請使用：

   * **取消** 中止註冊。
   * **儲存** 完成註冊。 將用消息確認組的建立。

### 編輯現有群組 {#editing-an-existing-group}

1. 從「群組」控制台中群組名稱下的連結存取群組詳細資訊。

1. 您現在可以編輯詳細資料，並將其儲存為 [新增群組](#adding-a-new-group).

### 複製現有群組 {#copying-an-existing-group}

1. 使用點按方塊來標幟群組。
1. 使用 **複製** 複製群組詳細資訊的圖示：

   ![](do-not-localize/chlimage_1-5.png)

1. 此 **編輯群組設定** 表單即會開啟。

   群組ID將與原始ID相同，但前置詞為 `Copy of`. 由於ID不能包含空格，因此您必須編輯此檔案。 其他所有詳細資訊將與原始資訊相同。

   您現在可以編輯詳細資料，並將其儲存為 [新增群組](#adding-a-new-group).

### 刪除現有群組 {#deleting-an-existing-group}

1. 使用點按方塊來標幟一或多個群組。
1. 使用 **刪除** 刪除組詳細資訊的表徵圖：

   ![](do-not-localize/chlimage_1-6.png)

1. 系統會要求您確認刪除，然後會傳送訊息確認確實已發生刪除。

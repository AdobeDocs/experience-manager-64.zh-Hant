---
title: 以寫程式方式管理PreferencesNodes
seo-title: Programmatically managing the PreferencesNodes
description: 使用Preferences Manager Service API(Java)以寫程式方式管理Preferences節點。
seo-description: Use the Preferences Manager Service API (Java) to programmatically manage the Preferences Nodes.
uuid: f0cb117a-a6cc-4ca5-8511-b3bc9f6738e9
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 9d4dba7f-49d8-4112-bc8a-04dafc99a936
role: Developer
exl-id: d580b32c-a344-4a8c-bd61-0949da76d981
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---

# 以寫程式方式管理首選項節點 {#programmatically-managing-the-preferencesnodes}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

本主題說明如何使用Preferences Manager Service API(Java)以程式設計方式管理Preferences節點。

您可以從管理員UI手動變更配置設定。 若要變更選項，請導覽至 `Home>Settings>User Management> Configuration>Manual Configuration`. 匯入 `config.xml` 進行變更後，您會注意到除了在節點進行的變更以外的所有變更 `/Adobe/Adobe Experience Manager Forms/Config/UM persist` 會遺失。 「使用者管理匯入和匯出」的預覽不支援變更其他元件的組態設定。 現在，您可以透過 `PreferencesManagerServiceClient` API。

**步驟摘要**&#x200B;要以寫程式方式管理「首選項節點」，請執行以下步驟：

1. 包含專案檔案。
1. 建立PreferencesManagerService客戶端
1. 調用適當的角色或權限操作

**包含項目檔案**

在您的開發專案中加入必要的檔案。 如果您使用Java建立客戶端應用程式，請包括必要的JAR檔案。 如果您使用Web服務，請確定您包含Proxy檔案。

**建立PreferencesManagerService客戶端**

在以寫程式方式執行User Management PreferencesManagerService操作之前，必須建立PreferencesManagerService客戶端。 使用Java API可通過建立PreferencesManagerServiceClient對象來完成。

**調用適當的角色或權限操作**

建立服務客戶端後，可以調用首選項管理器操作。 服務客戶端允許您讀取和設定權限。

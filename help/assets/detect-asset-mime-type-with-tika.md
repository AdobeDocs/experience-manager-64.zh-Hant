---
title: 使用Apache Tika偵測數位資產的MIME類型
description: 啟用Apache Tika可協助AEM Assets在上傳作業期間（而非檔案副檔名）從內容資料流偵測資產的MIME類型。
contentOwner: AG
feature: 中繼資料，開發人員工具，資產管理
role: Admin,Architect
exl-id: 6c9e53e9-5e54-4816-9431-41e796340d1e
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 3%

---

# 使用Apache Tika偵測數位資產的MIME類型 {#detecting-mime-type-of-assets-using-apache-tika}

通常，Adobe Experience Manager(AEM)Assets會偵測您從其副檔名上傳的資產的MIME類型。 如果您使用Apache Tika來上傳資產，AEM Assets會在上傳作業期間從內容資料流中偵測其MIME類型，而非從副檔名。

此功能預設為停用。 若要啟用功能，請從Configuration Manager設定&#x200B;**Day CQ DAM Mime Type**&#x200B;服務。

>[!NOTE]
>
>使用Apache Tika程式庫進行MIME類型偵測是一項耗用大量資源的作業。

1. 轉到`https://[AEM_server]:[port]/system/console/configMgr`以開啟Configuration Manager Web控制台。
1. 從服務清單中，找到&#x200B;**[!UICONTROL Day CQ DAM Mime Type Service]** ，然後點選/按一下旁邊的&#x200B;**[!UICONTROL Edit]**&#x200B;圖示，以在「編輯」模式中開啟它。

1. 選取&#x200B;**[!UICONTROL 從內容偵測MIME]**&#x200B;選項，以啟用剖析已上傳資產以在忽略副檔名時判斷其MIME類型。 依預設，會取消選取此選項。

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. 按一下/點選「 **[!UICONTROL 儲存]** 」以儲存變更。

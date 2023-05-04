---
title: 使用Apache Tika偵測數位資產的MIME類型
description: 啟用Apache Tika以提供說明 [!DNL Experience Manager] 在上傳作業期間，資產會從內容資料流偵測資產的MIME類型，而非副檔名。
contentOwner: AG
feature: Metadata,Developer Tools,Asset Management
role: Admin,Architect
exl-id: 6c9e53e9-5e54-4816-9431-41e796340d1e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 5%

---

# 使用Apache Tika偵測數位資產的MIME類型 {#detecting-mime-type-of-assets-using-apache-tika}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets通常會偵測您從其副檔名上傳的MIME類型資產。 如果您使用Apache Tika上傳資產， [!DNL Experience Manager] 在上傳作業期間，資產會從內容資料流中偵測其MIME類型，而非副檔名。

此功能預設為停用。 若要啟用功能，請設定 **Day CQ DAM Mime類型** 服務。

>[!NOTE]
>
>使用Apache Tika程式庫進行MIME類型偵測是一項耗用大量資源的作業。

1. 前往 `https://[AEM_server]:[port]/system/console/configMgr` 以開啟Configuration Manager Web控制台。
1. 從服務清單中，找到 **[!UICONTROL Day CQ DAM Mime類型服務]** 並點選/按一下 **[!UICONTROL 編輯]** 表徵圖，以在「編輯」模式下開啟它。

1. 選取 **[!UICONTROL 從內容中檢測MIME]** 選項，啟用已上傳資產的剖析，以在忽略副檔名時判斷其MIME類型。 依預設，會取消選取此選項。

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. 按一下/點選「 **[!UICONTROL 儲存]** 」以儲存變更。

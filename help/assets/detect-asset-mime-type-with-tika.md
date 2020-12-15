---
title: 使用Apache Tika來偵測數位資產的MIME類型
description: 啟用Apache Tika可協助AEM Assets在上傳作業期間，從內容串流偵測MIME類型的資產，而非副檔名。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 3%

---


# 使用Apache Tika來偵測數位資產的MIME類型{#detecting-mime-type-of-assets-using-apache-tika}

通常，Adobe Experience Manager(AEM)Assets會偵測您從其副檔名上傳的MIME資產類型。 如果您使用Apache Tika上傳資產，AEM Assets會在上傳作業期間從內容串流偵測其MIME類型，而非副檔名。

此功能預設為停用。 要啟用該功能，請從Configuration Manager配置&#x200B;**Day CQ DAM Mime Type**&#x200B;服務。

>[!NOTE]
>
>使用Apache Tika程式庫進行MIME類型偵測是一項耗用大量資源的作業。

1. 轉到`https://[AEM_server]:[port]/system/console/configMgr`以開啟Configuration Manager Web控制台。
1. 從服務清單中，找到&#x200B;**[!UICONTROL Day CQ DAM Mime Type Service]** ，並點選／按一下該服務旁邊的&#x200B;**[!UICONTROL 編輯]**&#x200B;表徵圖以在編輯模式下開啟該服務。

1. 選取「從內容偵測MIME」選項，以啟用剖析已上傳資產，在忽略副檔名時判斷其MIME類型。 ****&#x200B;依預設，會取消選取此選項。

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. 按一下/點選「 **[!UICONTROL 儲存]** 」以儲存變更。

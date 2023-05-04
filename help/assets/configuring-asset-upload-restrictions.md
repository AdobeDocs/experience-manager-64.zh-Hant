---
title: 設定資產上傳限制
description: 了解如何設定Adobe Experience Manager Assets以限制使用者可上傳的資產（檔案）類型。
contentOwner: AG
feature: Upload,Asset Ingestion,Asset Management
role: Admin,Architect
exl-id: 0d817cfa-ae06-442a-ad89-5fe619bb2eff
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 32%

---

# 設定資產上傳限制 {#configuring-asset-upload-restrictions}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

您可以設定Adobe Experience Manager Assets以限制使用者可上傳的資產（檔案）類型。 此功能可協助您避免使用者以不適當的格式上傳資產或上傳任何惡意檔案的可能性。 此 `Day CQ DAM Asset Upload Restriction` 服務可讓您控制使用者可上傳的檔案類型。 依預設， [!DNL Experience Manager] Assets可讓使用者上傳所有MIME類型的資產。 不過，您可以設定服務，限制使用者僅上傳特定MIME類型的檔案。

1. 若要開啟Configuration Manager Web控制台，請訪問 `https://[AEM_server]:[port]/system/console/configMgr`.
1. 開啟 **[!UICONTROL 日CQ DAM資產上傳限制]** 服務。 依預設， **允許所有MIME** 選項，允許用戶上載所有MIME類型的檔案。

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. 若要限制使用者僅上傳某些MIME類型的檔案，請取消選取 **[!UICONTROL llow all MIME]** (llow all MIME **[!UICONTROL )選項，並使用規則運算式在「允許的資產MIME(regex)]** 」欄位中指定允許的MIME類型。

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. 按一下/點選「 **[!UICONTROL 儲存]** 」以儲存變更。如果您為允許的MIME類型指定MIME字串，則對於任何MIME類型不符合這些欄位中已設定之MIME字串的資產，上傳作業會失敗。

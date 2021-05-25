---
title: 設定資產上傳限制
description: 了解如何設定Adobe Experience Manager(AEM)資產，以限制使用者可上傳的資產（檔案）類型。
contentOwner: AG
feature: 上傳，資產擷取，資產管理
role: Administrator,Architect
exl-id: 0d817cfa-ae06-442a-ad89-5fe619bb2eff
source-git-commit: 440194476a89092451f9fae80b5c63f055fca54e
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 29%

---

# 設定資產上傳限制{#configuring-asset-upload-restrictions}

您可以設定Adobe Experience Manager(AEM)資產，以限制使用者可上傳的資產（檔案）類型。 此功能可協助您避免使用者以不適當的格式上傳資產或上傳任何惡意檔案的可能性。 `Day CQ DAM Asset Upload Restriction`服務可讓您控制使用者可上傳的檔案類型。 依預設，AEM Assets可讓使用者上傳所有MIME類型的資產。 不過，您可以設定服務，限制使用者僅上傳特定MIME類型的檔案。

1. 要開啟Configuration Manager Web控制台，請訪問`https://[AEM_server]:[port]/system/console/configMgr`。
1. 在「編輯」模式中開啟&#x200B;**[!UICONTROL Day CQ DAM Asset Upload Restriction]**&#x200B;服務。 預設情況下，選擇&#x200B;**允許所有MIME**&#x200B;選項，該選項允許用戶上載所有MIME類型的檔案。

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. 若要限制使用者僅上傳某些MIME類型的檔案，請取消選取 **[!UICONTROL llow all MIME]** (llow all MIME **[!UICONTROL )選項，並使用規則運算式在「允許的資產MIME(regex)]** 」欄位中指定允許的MIME類型。

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. 按一下/點選「 **[!UICONTROL 儲存]** 」以儲存變更。如果您為允許的MIME類型指定MIME字串，則對於任何MIME類型不符合這些欄位中已設定之MIME字串的資產，上傳作業會失敗。

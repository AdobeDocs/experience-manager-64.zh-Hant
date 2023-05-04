---
title: 多語言資產
description: 了解如何自動將資產（包括二進位檔、中繼資料和標籤）轉譯為多種語言的工作流程。
contentOwner: AG
feature: Asset Management
role: Admin
exl-id: 8e065137-3599-48af-a040-6923b7b5e1d9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 5%

---

# 多語言資產 {#multilingual-assets}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager(AEM)Assets可讓您自動處理資產的翻譯工作流程（包括二進位檔、中繼資料和標籤），以產生其他語言的資產，以便用於多語言專案。

為了自動化翻譯工作流，您整合了翻譯服務提供商與 [!DNL Experience Manager] 並建立專案，將資產翻譯成多種語言。 [!DNL Experience Manager] 支援人工和機器翻譯工作流程。

人類翻譯：翻譯的資產會傳回並匯入AEM。 當您的翻譯提供者與AEM整合時，資產會自動在 [!DNL Experience Manager] 和翻譯提供者。

機器翻譯：機器翻譯服務會立即轉譯資產的中繼資料和標籤。

換算資產包括下列各項：

1. [連接 [!DNL Experience Manager] 翻譯服務提供商](/help/sites-administering/tc-tic.md#connecting-to-a-translation-service-provider)
1. [建立翻譯整合框架配置](/help/sites-administering/tc-tic.md)
1. [準備翻譯資產](preparing-assets-for-translation.md)
1. [將翻譯雲服務應用於資料夾](transition-cloud-services.md)
1. [建立翻譯專案](translation-projects.md)

如果您的翻譯服務提供者未提供連接器以與AEM整合，請使用 [替代過程](/help/sites-administering/tc-manage.md#exporting-a-translation-job).

另請參閱 [建立內容片段的翻譯專案](creating-translation-projects-for-content-fragments.md).

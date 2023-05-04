---
title: 翻譯多語言網站的內容
seo-title: Translating Content for Multilingual Sites
description: 了解如何翻譯多語言網站的內容。
seo-description: Learn how to translate content for multilingual sites.
uuid: b8047f6f-e86a-495d-9b80-731ac7d83c66
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 67faa2ee-cb12-44b0-8bfb-534d1d6c360a
legacypath: /content/docs/en/aem/6-0/administer/integration/third-party-services/machine-translation
feature: Language Copy
exl-id: 3a3f5c4d-6c3f-4201-acc8-dbd138bb59ba
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 75%

---

# 翻譯多語言網站的內容{#translating-content-for-multilingual-sites}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

自動翻譯頁面內容、資產和使用者產生的內容，以建立和維護多語言網站。 若要自動化翻譯工作流程，您可以將翻譯服務提供商與 AEM 相整合，並建立用於將內容翻譯成多種語言的專案。AEM 支援人工和機器翻譯工作流程。

* 人工翻譯：內容將傳送給您的翻譯提供商並由專業翻譯人員翻譯。完成後，翻譯後的內容將傳回並匯入到 AEM 中。如果您的翻譯提供商與 AEM 相整合，內容會在 AEM 和翻譯提供商之間自動傳送。
* 機器翻譯：機器翻譯服務會立即翻譯您的內容。

翻譯內容涉及以下步驟：

1. [將 AEM 與您的翻譯服務提供商連接](/help/sites-administering/tc-tic.md#connecting-to-a-translation-service-provider)並[建立翻譯整合框架設定](/help/sites-administering/tc-tic.md)。

1. [將您語言主版的頁面](/help/sites-administering/tc-tic.md#configuring-pages-for-translation) 與翻譯服務和框架設定相關聯。
1. [識別要翻譯的內容類型](/help/sites-administering/tc-rules.md)。
1. 編寫語言主版並建立語言副本的根頁面，[以備妥內容進行翻譯](/help/sites-administering/tc-prep.md)。
1. [建立翻譯專案](/help/sites-administering/tc-manage.md)以收集要翻譯的內容並準備翻譯流程。
1. 使用翻譯專案[管理內容翻譯流程](/help/sites-administering/tc-manage.md)。

如果您的翻譯服務提供商不提供連接器以與 AEM 整合，AEM 支援手動擷取和重新插入 XML 格式的翻譯內容。

>[!NOTE]
>
>您的使用者必須是專案管理員群組的成員，才能使用語言副本功能。

## 最佳做法 {#best-practices}

[翻譯最佳做法](/help/sites-administering/tc-bp.md)頁面包含與您的實作相關的重要資訊。

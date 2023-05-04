---
title: ContextHub
seo-title: ContextHub
description: ContextHub是儲存、操控和呈現內容資料的架構
seo-description: ContextHub is a framework for storing, manipulating, and presenting context data
uuid: 14e6ff4f-ffbe-454a-b2ec-a35333526e27
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: acf5c17a-95b7-43ba-9734-241e20f4f374
exl-id: 0a6b815a-5055-4c44-96d1-ff238b4285f3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 2%

---

# ContextHub{#contexthub}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

ContextHub是儲存、操控和呈現內容資料的架構。 用戶端Javascript API可讓您存取資料，以個人化內容。

>[!NOTE]
>
>此 [We.Retail參考實作](/help/sites-developing/we-retail.md) 實作ContextHub ，並可在您將ContextHub整合至自己的專案時作為參考。

>[!CAUTION]
>
>包含由 [We.Retail參考實作](/help/sites-developing/we-retail.md) ( `/libs/settings/cloudsettings/legacy`)只應作為建立自己設定的參考。
>
>在專案中，不應將其用作您自己的ContextHub設定。

## 持久性 {#persistence}

ContextHub會在用戶端上儲存保留的內容資料。 ContextHub Javascript API可讓您視需要存取儲存區，以建立、更新和刪除資料。 因此，ContextHub代表您頁面上的資料層。

每個ContextHub存放區都是預先定義的存放區類型的例項：

* ContextHub提供數個 [範例存放區類型](/help/sites-developing/ch-samplestores.md).
* 使用AEM主控台 [建立儲存](/help/sites-administering/contexthub-config.md#creating-a-contexthub-store).
* 開發人員可 [建立自訂商店類型](/help/sites-developing/ch-extend.md#creating-custom-store-candidates).
* 開發人員可 [存取儲存資料](/help/sites-developing/ch-adding.md#interacting-with-contexthub-stores) 透過JavaScript。

## Segmentation {#segmentation}

ContextHub包含區段引擎，可管理區段並判斷要針對目前內容解析哪些區段。 已定義數個區段。 您可以將Javascript API用於 [判斷已解析的區段](/help/sites-developing/ch-adding.md#determining-resolved-contexthub-segments).

## 簡報 {#presentation}

此 [ContextHub工具列](/help/sites-authoring/ch-previewing.md) 可讓行銷人員和作者查看和操控儲存資料，以模擬編寫頁面時的使用者體驗。 工具列由提供ContextHub存放區存取權的UI模組群組組成。

每個ContextHub UI模組都是預先定義模組類型的例項：

* ContextHub提供數個 [範例模組類型](/help/sites-developing/ch-samplemodules.md).
* 使用AEM主控台 [新增UI模組](/help/sites-administering/contexthub-config.md#adding-a-ui-module)和 [在UI模式中將它們分組](/help/sites-administering/contexthub-config.md#adding-a-ui-mode).

* 開發人員可 [建立自訂模組類型](/help/sites-developing/ch-extend.md#creating-contexthub-ui-module-types).

開發人員需 [將ContextHub元件新增至頁面](/help/sites-developing/ch-adding.md).

---
title: Live Copy 概觀主控台
seo-title: Live Copy Overview Console
description: 了解Live Copy概觀主控台的基本概念。
seo-description: Learn about the basics of the Live Copy Overview Console.
uuid: 6b1841ec-950e-455b-9b30-b5f5050a67b8
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 3763e985-7dd8-47fd-bfdf-2368b424c270
feature: Multi Site Manager
exl-id: 96238d40-c19a-4c1f-9400-c7bb8636b448
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 28%

---

# Live Copy 概觀主控台{#live-copy-overview-console}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

此 **即時副本概述** 可讓您：

* 檢視/管理整個網站的繼承：

   * 檢視Blueprint樹狀結構和對應的Live Copy結構，及其繼承狀態
   * 更改繼承狀態；例如，暫停，繼續
   * 檢視Blueprint和Live Copy屬性

* 執行轉出動作

## 開啟 Live Copy 概觀 {#opening-the-live-copy-overview}

您可以從以下位置開啟 Live Copy 概觀：

* [藍圖頁面的參考側面板 (Sites 主控台)](#opening-live-copy-overview-references-for-a-blueprint-page)
* [藍圖頁面的屬性](#opening-live-copy-overview-properties-of-a-blueprint-page)

### 開啟即時副本概述 — Blueprint頁面的參考 {#opening-live-copy-overview-references-for-a-blueprint-page}

**Live Copy 概觀**&#x200B;可以從 **Sites** 主控台的&#x200B;**參考**&#x200B;側面板開啟：

1. 在 **網站** 主控台， [導覽至您的blueprint頁面並加以選取](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. 開啟 **[參考](/help/sites-authoring/basic-handling.md#references)** 面板和選取 **Live Copies**.

   ![chlimage_1-359](assets/chlimage_1-359.png)

   >[!NOTE]
   >
   >您也可以先開啟「參考」，然後選取Blueprint。

1. 選擇 **即時副本概述** 顯示和使用與所選Blueprint相關的所有Live Copy的概述。
1. 使用&#x200B;**關閉**&#x200B;以退出並返回 **Sites** 主控台。

### 開啟即時副本概述 — Blueprint頁面的屬性 {#opening-live-copy-overview-properties-of-a-blueprint-page}

**Live Copy 概觀**&#x200B;可以在檢視藍圖頁面的屬性時開啟：

1. 開啟相關藍圖頁面的&#x200B;**屬性**。
1. 開啟&#x200B;**藍圖**&#x200B;索引標籤 - **Live Copy 概觀** 選項將顯示在頂端工具列中：

   ![chlimage_1-360](assets/chlimage_1-360.png)

1. 選擇 **即時副本概述** 顯示和使用與目前Blueprint相關的所有即時副本的概觀。

   >[!NOTE]
   >
   >有關詳細資訊，另請參閱知識庫文章 [Livecopy狀態訊息 — 最新/綠色/同步](https://helpx.adobe.com/experience-manager/kb/livecopy-status-message---up-to-date-green-in-sync.html).

1. 使用&#x200B;**關閉**&#x200B;以退出並返回 **Sites** 主控台。

## 使用 Live Copy 概觀 {#using-the-live-copy-overview}

此 **即時副本概述** 也可用來在即時副本上執行動作：

1. 開啟 **Live Copy 概觀**。
1. 選取所需的Blueprint或即時副本頁面 — 工具列將會更新，以顯示可用的動作。 此 [動作](/help/sites-administering/msm.md#terms-used) 可用取決於您是否選取 [Blueprint](#actions-for-a-blueprint-page) 或 [即時副本](#actions-for-a-live-copy-page) 頁面：

### 藍圖頁面的動作 {#actions-for-a-blueprint-page}

選擇藍圖頁面時，可以執行以下動作：

![chlimage_1-361](assets/chlimage_1-361.png)

* 編輯

   * 開啟Blueprint頁面進行編輯。

* [推出](/help/sites-administering/msm.md#rollout-and-synchronize)

   * 執行轉出以將變更從來源推送至LiveCopy。

### Live Copy 頁面的動作 {#actions-for-a-live-copy-page}

選取即時副本頁面時，可使用下列動作：

![chlimage_1-362](assets/chlimage_1-362.png)

* 編輯

   * 開啟即時副本頁面進行編輯。

* [關係狀態](#relationship-status)

   * 檢視狀態和繼承的相關資訊。

* [同步](/help/sites-administering/msm.md#rollout-and-synchronize)

   * 同步即時副本，以從來源提取變更至即時副本。

* [重設](/help/sites-administering/msm-livecopy.md#resetting-a-live-copy-page)

   * 重設即時副本頁面以移除所有繼承取消，並將頁面傳回與來源頁面相同的狀態。

* [暫停](/help/sites-administering/msm.md#suspending-and-cancelling-inheritance-and-synchronization)

   * 暫時停用即時副本與其Blueprint頁面之間的即時關係。

* [繼續](/help/sites-administering/msm-livecopy.md#resuming-inheritance-for-a-page)

   * 「恢復」允許您恢復已暫停的關係。

* [分離](/help/sites-administering/msm.md#detaching-a-live-copy)

   * 永久移除即時副本與其Blueprint頁面之間的即時關係。

## 關係狀態 {#relationship-status}

此 **關係狀態** 主控台有兩個標籤，提供一系列功能：

* [關係狀態資訊](#relationship-status-information)
* [即時副本資訊](#live-copy-information)

### 關係狀態資訊 {#relationship-status-information}

此索引標籤提供Blueprint與Live Copy之間關係狀態的詳細資訊：

![chlimage_1-363](assets/chlimage_1-363.png)

### 即時副本資訊 {#live-copy-information}

此索引標籤可讓您檢視和編輯即時副本設定：

![chlimage_1-364](assets/chlimage_1-364.png)

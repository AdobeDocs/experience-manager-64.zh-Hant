---
title: 元件主控台
seo-title: Components Console
description: 元件主控台
seo-description: null
uuid: 308b7fa1-9525-43f3-8c15-1076485b3f8c
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 8774c38a-abd2-4dc2-868e-d6760c96f3f6
exl-id: fa583a06-e75c-41de-a977-7e459ab8bca9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 21%

---

# 元件主控台{#components-console}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

元件控制台可讓您瀏覽為執行個體定義的所有元件，並檢視每個元件的金鑰資訊。

可從 **工具** -> **一般** -> **元件**. 在主控台中，卡片和清單檢視可供使用。由於沒有元件的樹結構，因此列視圖不可用。

![chlimage_1-301](assets/chlimage_1-301.png)

>[!NOTE]
>
>元件控制台顯示系統中的所有元件。 此 [元件瀏覽器](/help/sites-authoring/author-environment-tools.md#components-browser) 顯示可供作者使用的元件，並隱藏以句點( `.`)。

## 搜尋 {#search-features}

使用「 **僅內容****** 」圖示 (左上角)，您可以開啟「搜尋」面板以搜尋和/或篩選元件：

![chlimage_1-302](assets/chlimage_1-302.png)

## 元件詳細資訊 {#component-details}

若要檢視特定元件的詳細資訊，請點選/按一下所需資源。 提供三個標籤：

* **屬性**

   ![screen_shot_2018-03-27at165847](assets/screen_shot_2018-03-27at165847.png)

   在「屬性」索引標籤上，您可以：

   * 查看元件的常規屬性。
   * 檢視 [已定義表徵圖或縮寫](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) （元件）。

      * 按一下圖示的來源即會將您導向該元件。
   * 檢視 **資源類型** 和 **資源超類型** （若已定義）。

      * 按一下「資源超類型」(Resource Super Type)會將您導向該元件。
   >[!NOTE]
   >
   >因為 `/apps` 在運行時無法編輯，元件控制台是只讀的。

* **原則**

   ![chlimage_1-303](assets/chlimage_1-303.png)

* **即時使用情況**

   ![chlimage_1-304](assets/chlimage_1-304.png)

   >[!CAUTION]
   >
   >由於為此檢視收集的資訊性質的緣故，可能需要一段時間才能加以整理/顯示。

* **文件**

   如果開發人員已提供 [元件的檔案](/help/sites-developing/developing-components.md#documenting-your-component)，則會顯示在 **檔案** 標籤。 如果沒有可用的檔案，則 **檔案** 標籤。

   ![chlimage_1-305](assets/chlimage_1-305.png)

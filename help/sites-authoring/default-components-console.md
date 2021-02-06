---
title: 元件主控台
seo-title: 元件主控台
description: 'null'
seo-description: 'null'
uuid: 308b7fa1-9525-43f3-8c15-1076485b3f8c
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 8774c38a-abd2-4dc2-868e-d6760c96f3f6
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 21%

---


# 元件主控台{#components-console}

「元件」控制台允許您瀏覽為實例定義的所有元件，並查看每個元件的鍵資訊。

可從&#x200B;**Tools** -> **General** -> **Components**&#x200B;訪問。 在主控台中，卡片和清單檢視可供使用。由於沒有元件的樹結構，因此列視圖不可用。

![chlimage_1-301](assets/chlimage_1-301.png)

>[!NOTE]
>
>「元件控制台」顯示系統中的所有元件。 [元件瀏覽器](/help/sites-authoring/author-environment-tools.md#components-browser)顯示作者可使用的元件，並隱藏以句點(`.`)開頭的任何元件群組。

## 搜尋 {#search-features}

使用「 **僅內容****** 」圖示 (左上角)，您可以開啟「搜尋」面板以搜尋和/或篩選元件：

![chlimage_1-302](assets/chlimage_1-302.png)

## 元件詳細資訊{#component-details}

要查看有關特定元件的詳細資訊，請點選／按一下所需資源。 三個標籤提供：

* **屬性**

   ![screen_shot_2018-03-27at165847](assets/screen_shot_2018-03-27at165847.png)

   在「屬性」標籤上，您可以：

   * 查看元件的常規屬性。
   * 查看如何為元件定義[表徵圖或縮寫。](/help/sites-developing/components-basics.md#component-icon-in-touch-ui)

      * 按一下圖示的來源後，您就會前往該元件。
   * 查看元件的&#x200B;**資源類型**&#x200B;和&#x200B;**資源超級類型**（如果已定義）。

      * 按一下「資源超級類型」(Resource Super Type)將帶您進入該元件。
   >[!NOTE]
   >
   >由於`/apps`在運行時不可編輯，因此元件控制台是只讀的。

* **原則**

   ![chlimage_1-303](assets/chlimage_1-303.png)

* **即時使用情況**

   ![chlimage_1-304](assets/chlimage_1-304.png)

   >[!CAUTION]
   >
   >由於為此視圖收集的資訊的性質，可能需要一段時間才能進行整理／顯示。

* **文件**

   如果開發人員已提供元件[的文檔，則它將出現在&#x200B;**Documentation**&#x200B;頁籤上。 ](/help/sites-developing/developing-components.md#documenting-your-component)如果沒有可用的文檔，則不會顯示&#x200B;**Documentation**&#x200B;頁籤。

   ![chlimage_1-305](assets/chlimage_1-305.png)


---
title: 使用 ContextHub 資料預覽頁面
seo-title: 使用 ContextHub 資料預覽頁面
description: ContextHub工具列顯示來自ContextHub存放區的資料，並可讓您變更存放區資料，且對於預覽內容很實用
seo-description: ContextHub工具列顯示來自ContextHub存放區的資料，並可讓您變更存放區資料，且對於預覽內容很實用
uuid: 0150555a-0a92-4692-a706-bbe59fd34d6a
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: personalization
discoiquuid: f281ef8c-0831-470c-acb7-189f20452a50
exl-id: 24f94dd5-62a4-4ac3-9a1b-a8e189da9958
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 4%

---

# 使用 ContextHub 資料預覽頁面{#previewing-pages-using-contexthub-data}

[ContextHub](/help/sites-developing/contexthub.md)工具列顯示ContextHub商店的資料，並可讓您變更商店資料。 ContextHub工具列可用來預覽由ContextHub商店中的資料所決定的內容。

工具列包含一系列包含一或多個UI模組的UI模式。

* UI模式是顯示在工具列左側的圖示。 當您按一下或點選圖示時，工具列會顯示其包含的UI模組。
* UI模組會顯示一或多個ContextHub存放區的資料。 有些UI模組也可讓您操控儲存資料。

ContextHub會安裝數個UI模式和UI模組。 您的管理員可能已設定[ ContextHub](/help/sites-administering/contexthub-config.md)以顯示不同的內容。

![screen_shot_2018-03-23at093446](assets/screen_shot_2018-03-23at093446.png)

## 顯示ContextHub工具欄{#revealing-the-contexthub-toolbar}

ContextHub工具列可在「預覽」模式中使用。 工具列僅適用於製作執行個體，且僅在管理員啟用時才可用。

![screen_shot_2018-03-23at093730](assets/screen_shot_2018-03-23at093730.png)

1. 在開啟您的頁面進行編輯時，在工具列上按一下或點選「預覽」。

   ![chlimage_1-219](assets/chlimage_1-219.png)

1. 若要顯示工具列，請按一下或點選「ContextHub」圖示。

   ![](do-not-localize/screen_shot_2018-03-23at093621.png)

## UI模組功能{#ui-module-features}

每個UI模組提供的功能集不同，但下列功能類型很常見。 因為UI模組是可擴充的，您的開發人員可視需要實作其他功能。

### 工具欄內容{#toolbar-content}

UI模組可以顯示工具列中一或多個ContextHub存放區的資料。 UI模組會使用圖示和標題來識別自己。

![screen_shot_2018-03-23at093936](assets/screen_shot_2018-03-23at093936.png)

### 快顯內容{#popup-content}

有些UI模組在按一下或點選時會全面顯示快顯視窗。 彈出式功能表通常包含的工具列上顯示的其他資訊以外的其他資訊。

![screen_shot_2018-03-23at094003](assets/screen_shot_2018-03-23at094003.png)

### 彈出式Forms {#popup-forms}

模組的快顯覆蓋可以包含表單元素，讓您能夠變更ContextHub存放區中的資料。 如果頁面內容由儲存資料決定，您可以使用表單並觀察頁面內容的變更。

### 全螢幕模式 {#fullscreen-mode}

彈出式覆蓋圖可包含您按一下或點選以展開彈出式內容的圖示，以覆蓋整個瀏覽器視窗或畫面。

![](do-not-localize/chlimage_1-18.png)

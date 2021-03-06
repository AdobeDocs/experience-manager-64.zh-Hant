---
title: 骨幹互動
seo-title: 骨幹互動
description: 關於在AEM Forms工作區中使用骨幹JavaScript模型的概念資訊。
seo-description: 關於在AEM Forms工作區中使用骨幹JavaScript模型的概念資訊。
uuid: c70da848-e514-42bc-a59b-44a7c00aa529
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: d363eec3-172b-413e-9743-ed51804ea1e9
exl-id: f726cb73-732c-4893-bdb5-10ddcf4a340a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# 骨幹交互{#backbone-interaction}

骨幹是一個庫，可幫助在Web應用程式中建立和遵循MVC體系結構。 骨幹的基本思想是將介面組織成邏輯視圖，由模型支援，每個模型在模型更改時可獨立更新，而無需重繪頁面。 有關骨幹的詳細資訊，請參閱[https://backbonejs.org](https://backbonejs.org/)。

一些重要概念如下：

**骨幹** 模型包含資料，以及與此資料相關的大部分邏輯。

**骨** 乾視圖用於表示相應模型的狀態。骨幹視圖的行為實際上類似於控制器，監聽用戶介面事件（如用戶點擊）或模型事件（如資料更改），並酌情修改用戶介面。

**HTML范** 本包裝函式範本，其預留位置由模型填入。

**AEM Forms** workspace包含數個個別元件。每個元件：

* 表示單個邏輯用戶介面元素。
* 可以是類似元件的集合。
* 由骨幹模型、骨幹視圖和HTML模板組成。
* 包含對服務的參考。
* 包含對必需實用程式的引用。

初始化元件時，會建立下列物件：

* 為元件建立新的骨幹模型實例。 服務會插入模型中。
* 建立「骨幹」視圖的新實例。
* 相應模型、HTML模板和實用程式的實例將插入到視圖中。

在「骨幹網」視圖中，有一個事件映射，它映射由於用戶介面與相應處理程式交互而產生的各種事件。 初始化元件後，就會啟動此映射。

初始化檢視時，檢視會呼叫其對應的模型，從伺服器擷取資料。 一旦檢視所需的所有資料都可用後，檢視就會以HTML範本指定的格式轉譯資料。 多個視圖可共用同一模型進行通信。

![](do-not-localize/aem_forms_workflow.png)

範例：

1. 用戶按一下任務清單中的任務模板。
1. 任務視圖監聽該點擊，並調用任務模型上的呈現函式。
1. 任務模型隨後會呼叫服務，此服務是所有與AEM Forms伺服器通訊的共同點。
1. 服務類別會透過ajax呼叫AEM Forms REST端點以取得呈現方法。
1. 此Ajax呼叫的成功回呼是在任務模型中定義。
1. 任務模型會將骨幹事件引發為呈現呼叫完成的通知。
1. 另一個視圖，任務詳細資訊視圖從任務模型監聽此事件。
1. 然後，任務詳細資訊視圖將更改任務詳細資訊模板，以向用戶顯示呈現的任務（表單、詳細資訊、附件、附註等）。

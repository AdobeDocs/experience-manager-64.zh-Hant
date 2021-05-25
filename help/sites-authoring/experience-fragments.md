---
title: 體驗片段
seo-title: 體驗片段
description: 體驗片段
seo-description: 'null'
uuid: be1aceef-eb6e-47e5-a920-be5cc6de6191
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 1fe58af0-3005-46fc-8717-5d32557947ed
exl-id: 8906b3ab-cb08-4b3e-8796-334e36b1e491
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1312'
ht-degree: 7%

---

# 體驗片段{#experience-fragments}

體驗片段是一或多個元件的群組，包括可在頁面中參照的內容和版面。 它們可包含任何元件。

體驗片段：

* 是體驗（頁面）的一部分。
* 可用於多個頁面。
* 以範本為基礎（僅可編輯），以定義結構和元件。
* 由段落系統中的一個或多個元件（具有佈局）組成。
* 可包含其他體驗片段。
* 可與其他元件（包括其他體驗片段）結合，以形成完整的頁面（體驗）。
* 可能有不同的變數，可能會共用內容和/或元件。
* 可劃分為可跨片段的多個變數使用的建立區塊。

您可以使用體驗片段：

* 如果作者想要重複使用頁面的部分（體驗的片段），則需要複製並貼上該片段。 建立和維護這些複製/貼上體驗非常耗時，且容易發生使用者錯誤。 體驗片段不需要複製/貼上。
* 支援無頭式CMS使用案例。 作者只想使用AEM進行製作，而不想提供給客戶。 協力廠商系統/接觸點會使用該體驗，然後傳送給使用者。

>[!NOTE]
>
>體驗片段的寫入存取權要求使用者帳戶須在群組中註冊：
>
>`experience-fragments-editors`
>
>如果您遇到任何問題，請與系統管理員聯繫。

## 何時該使用體驗片段？{#when-should-you-use-experience-fragments}

該使用體驗片段的情況：

* 每當您想要重複使用體驗時。

   * 將透過相同或類似內容重複使用的體驗

* 當您使用AEM作為協力廠商的內容傳遞平台時。

   * 任何想使用AEM作為內容傳遞平台的解決方案
   * 將內容嵌入第三方接觸點

* 如果您的體驗有不同的變體或轉譯。

   * 管道或內容特定變數
   * 對群組有意義的體驗（例如跨管道具有不同體驗的促銷活動）

* 使用全通路商務時。

   * 大規模分享社交媒體頻道上與商務相關的內容
   * 將接觸點設為交易式

## 組織您的體驗片段{#organizing-your-experience-fragments}

建議您：
* 使用資料夾來組織您的體驗片段，

* [在這些資料夾上設定允許的範本](#configure-allowed-templates-folder)。

建立資料夾可讓您：

* 為您的體驗片段建立有意義的結構；例如，根據分類

   >[!NOTE]
   >
   >不需要將體驗片段的結構與網站的頁面結構對齊。

* [在資料夾層級分配允許的範本](#configure-allowed-templates-folder)

   >[!NOTE]
   >
   >您可以使用[範本編輯器](/help/sites-authoring/templates.md)建立自己的範本。

下列範例顯示根據`Contributors`結構化的體驗片段。 使用的結構也說明如何使用其他功能，例如多網站管理（包括語言副本）。

>[!CAUTION]
>
>以下螢幕截圖是使用Adobe Experience Manager作為Cloud Service從WKND網站擷取的。

![體驗片段的資料夾](assets/xf-folders.png)

## 建立和設定體驗片段的資料夾{#creating-and-configuring-a-folder-for-your-experience-fragments}

若要建立和設定體驗片段的資料夾，建議您：

1. [建立資料夾](/help/sites-authoring/managing-pages.md#creating-a-new-folder)。

1. [設定該資料夾允許的體驗片段範本](#configure-allowed-templates-folder)。

>[!NOTE]
>
>您也可以設定執行個體](#configure-allowed-templates-instance)的[允許範本，但此方法為&#x200B;**not**，因為值可能會在升級時覆寫。

### 配置資料夾{#configure-allowed-templates-folder}的允許模板

>[!NOTE]
>
>這是指定&#x200B;**[!UICONTROL 允許的範本]**&#x200B;的建議方法，因為值在升級時不會覆寫。

1. 導覽至必要的&#x200B;**[!UICONTROL 體驗片段]**&#x200B;資料夾。

1. 選擇資料夾，然後選擇&#x200B;**[!UICONTROL 屬性]**。

1. 在&#x200B;**[!UICONTROL 允許的範本]**&#x200B;欄位中指定用於擷取所需範本的規則運算式。

   例如：
   `/conf/(.*)/settings/wcm/templates/experience-fragment(.*)?`

   ![體驗片段屬性 — 允許的範本](assets/xf-folders-templates.png)

1. 選擇&#x200B;**[!UICONTROL 保存並關閉]**。

### 配置實例{#configure-allowed-templates-instance}的允許模板

>[!CAUTION]
>
>不建議使用此方法更改&#x200B;**[!UICONTROL 允許的模板]**，因為指定的模板可能在升級時被覆蓋。
>
>請使用此對話框僅供參考。

1. 導覽至必要的&#x200B;**[!UICONTROL 體驗片段]**&#x200B;主控台。

1. 選擇&#x200B;**[!UICONTROL 配置選項]**:

   ![配置按鈕](assets/xf-folders-18.png)

1. 在&#x200B;**[!UICONTROL 設定體驗片段]**&#x200B;對話方塊中指定所需的範本：

   ![設定體驗片段](assets/xf-folders-19.png)

1. 選擇&#x200B;**[!UICONTROL 保存]**。

## 建立體驗片段{#creating-an-experience-fragment}

若要建立體驗片段：

1. 從全域導覽中選取&#x200B;**[!UICONTROL 體驗片段]**。

   ![screen_shot_2018-04-05at92221am1](assets/screen_shot_2018-04-05at92221am1.png)

1. 導航到所需資料夾，然後選擇&#x200B;**[!UICONTROL Create]**。

1. 選取&#x200B;**[!UICONTROL 體驗片段]**&#x200B;以開啟&#x200B;**[!UICONTROL 建立體驗片段]**&#x200B;精靈。

   依次選擇所需 **[!UICONTROL 的範本]**、下 **[!UICONTROL 一步]**:

   ![xf-authoring-02](assets/xf-authoring-02.png)


1. 輸入 **[!UICONTROL 體驗]**&#x200B;片段的屬性。

   **[!UICONTROL Title]**&#x200B;是必填項。 如果將&#x200B;**[!UICONTROL Name]**&#x200B;留空，則將從&#x200B;**[!UICONTROL Title]**&#x200B;衍生。

   ![xf-authoring-03](assets/xf-authoring-03.png)

1. 按一下&#x200B;**[!UICONTROL 建立]**。

   將顯示一條消息。 選取:

   * **** Doneto返回主控台
   * **** 開啟以開啟片段編輯器

## 編輯體驗片段{#editing-your-experience-fragment}

體驗片段編輯器提供與一般頁面編輯器類似的功能。 如需如何使用頁面內容的詳細資訊，請參閱[編輯頁面內容](/help/sites-authoring/editing-content.md) 。

以下范常式式說明如何為產品建立預告：

1. 從[元件瀏覽器](/help/sites-authoring/author-environment-tools.md#components-browser)拖放&#x200B;**[!UICONTROL 類別預告]**。

   ![xf-authoring-04](assets/xf-authoring-04.png)

1. 從元件工具欄中選擇&#x200B;**[[!UICONTROL 配置]](/help/sites-authoring/editing-content.md#edit-configure-copy-cut-delete-paste)**。
1. 新增資 **[!UICONTROL 產]** ，並視需要 **[!UICONTROL 定義屬性]** 。
1. 使用&#x200B;**[!UICONTROL Done]**（勾選圖示）確認定義。
1. 視需要新增更多元件。

## 建立體驗片段變異{#creating-an-experience-fragment-variation}

您可以根據您的需求建立體驗片段的變體：

1. 開啟您的片段以進行[編輯](/help/sites-authoring/experience-fragments.md#editing-your-experience-fragment)。
1. 開啟&#x200B;**[!UICONTROL Variations]**&#x200B;標籤。

   ![xf-authoring-06](assets/xf-authoring-06.png)

1. **** 建立可讓您建立：

   * **[!UICONTROL 變異]**
   * **[!UICONTROL 變數為 live-copy]**.

1. 定義所需的屬性：

   * **[!UICONTROL 範本]**
   * **[!UICONTROL 標題]**
   * **[!UICONTROL 名稱]**;若保留為空白，則從標題衍生
   * **[!UICONTROL 說明]**
   * **[!UICONTROL 變數標記]**

   ![xf-authoring-07](assets/xf-authoring-07.png)

1. 使用&#x200B;**[!UICONTROL Done]**（勾選圖示）確認，新變數將顯示在面板中：

   ![xf-authoring-08](assets/xf-authoring-08.png)

## 使用您的體驗片段{#using-your-experience-fragment}

編寫頁面時，您現在可以使用體驗片段：

1. 開啟任何頁面進行編輯。

   例如：[http://localhost:4502/editor.html/content/we-retail/language-masters/en/products/men.html](http://localhost:4502/editor.html/content/we-retail/language-masters/en/products/men.html)

1. 從「元件」瀏覽器拖曳元件至頁面段落系統，建立體驗片段元件的例項：

   ![xf-authoring-09](assets/xf-authoring-09.png)

1. 將實際的體驗片段新增至元件例項；其中之一：

   * 從「資產瀏覽器」拖曳所需片段，並拖放至元件
   * 從元件工具欄中選擇&#x200B;**[!UICONTROL 配置]**&#x200B;並指定要使用的片段，使用&#x200B;**Done**&#x200B;確認（勾選）

   ![xf-authoring-10](assets/xf-authoring-10.png)

   >[!NOTE]
   >
   >在元件工具列中，編輯作為在片段編輯器中開啟片段的捷徑。

## 建置區塊 {#building-blocks}

您可以選取一或多個元件，以建立要在片段內回收的建置區塊：

### 建立構建塊{#creating-a-building-block}

要建立新的構建塊：

1. 在體驗片段編輯器中，選取您要重新使用的元件：

   ![xf-authoring-12](assets/xf-authoring-12.png)

1. 從元件工具欄中，選擇&#x200B;**[!UICONTROL 轉換為構建塊]**:

   ![xf-authoring-13-icon](assets/xf-authoring-13-icon.png)

   例如：

   ![xf-authoring-13](assets/xf-authoring-13.png)

1. 輸入建置塊的名 **[!UICONTROL 稱]**，並使用 **[!UICONTROL Convert確認]**:

   ![xf-authoring-14](assets/xf-authoring-14.png)

1. 建 **立區塊** (Building Block)將顯示在頁籤中，並可在段落系統中選擇：

   ![xf-authoring-15](assets/xf-authoring-15.png)

### 管理構建塊{#managing-a-building-block}

您的構建塊顯示在&#x200B;**[!UICONTROL 構建塊]**&#x200B;頁簽中。 對於每個區塊，可使用下列動作：

* 前往主版:在新標籤中開啟主變數
* 重新命名
* 刪除

![xf-authoring-16](assets/xf-authoring-16.png)

### 使用構建塊{#using-a-building-block}

您可以將建置區塊拖曳至任何片段的段落系統，如同任何元件。

## 純HTML格式副本{#the-plain-html-rendition}

使用URL中的`.plain.`選取器，可以存取純HTML轉譯。

這可從瀏覽器取得，但其主要用途是允許其他應用程式（例如協力廠商網頁應用程式、自訂行動實作）僅使用URL直接存取體驗片段的內容。

純HTML轉譯會將通訊協定、主機和內容路徑新增至以下路徑：

* 類型：`src`、`href`或`action`

* 或結尾為：`-src`或`-href`

例如：

`.../brooklyn-coat/master.plain.html`

>[!NOTE]
>
>連結一律會參考發佈例項。 協力廠商會使用這些連結，因此系統一律會從發佈例項呼叫連結，而非作者。

![xf-authoring-17](assets/xf-authoring-17.png)

## 匯出體驗片段{#exporting-experience-fragments}

依預設，體驗片段會以HTML格式傳送。 AEM和協力廠商管道皆可使用。

若要匯出至Adobe Target，會使用HTML。 如需完整資訊，請參閱[體驗片段的Target整合](/help/sites-administering/experience-fragments-target.md) 。

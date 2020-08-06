---
title: 體驗片段
seo-title: 體驗片段
description: 'null'
seo-description: 'null'
uuid: be1aceef-eb6e-47e5-a920-be5cc6de6191
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 1fe58af0-3005-46fc-8717-5d32557947ed
translation-type: tm+mt
source-git-commit: 6f6952686446359485f180050219a12db9d3969a
workflow-type: tm+mt
source-wordcount: '1311'
ht-degree: 7%

---


# 體驗片段{#experience-fragments}

「體驗片段」是一組或多個元件，包括可在頁面中參考的內容和版面。 它們可包含任何元件。

體驗片段：

* 是體驗（頁面）的一部分。
* 可跨多頁使用。
* 以範本（僅可編輯）為基礎，以定義結構和元件。
* 由段落系統中具有版面的一個或多個元件組成。
* 可以包含其他體驗片段。
* 可與其他元件（包括其他體驗片段）結合，以形成完整頁面（體驗）。
* 可以有不同的變化，這些變化可能會共用內容和／或元件。
* 可以細分為建置區塊，以便用於多種片段變化。

您可以使用體驗片段：

* 如果作者想要重複使用頁面的部分（體驗的片段），則必須複製並貼上該片段。 建立和維護這些複製／貼上體驗不但耗時，而且容易發生使用者錯誤。 體驗片段可免除複製／貼上的需求。
* 支援無頭CMS使用案例。 作者只想使用AEM來製作內容，但不想將內容傳送給客戶。 協力廠商系統／觸點會使用該體驗，然後傳送給使用者。

>[!NOTE]
>
>體驗片段的寫入存取權要求使用者帳戶必須註冊在群組中：
>
>`experience-fragments-editors`
>
>如果您遇到任何問題，請聯絡您的系統管理員。

## 何時應使用體驗片段？ {#when-should-you-use-experience-fragments}

應使用體驗片段：

* 無論何時您想要重複使用體驗。

   * 可重複使用相同或類似內容的體驗

* 當您將AEM當做協力廠商的內容傳送平台時。

   * 任何想要使用AEM做為內容傳送平台的解決方案
   * 將內容內嵌至協力廠商觸點

* 如果您有「體驗」，但有不同的變化或轉譯。

   * 頻道或內容特定變化
   * 對群組有意義的體驗（例如跨通道具有不同體驗的促銷活動）

* 當您使用全通道商務時。

   * 在社交媒體頻道上大規模分享商務相關內容
   * 讓觸點成為交易性

## 組織您的體驗片段 {#organizing-your-experience-fragments}

建議您：
* 使用資料夾來組織您的體驗片段，

* [在這些資料夾上設定允許的範本](#configure-allowed-templates-folder)。

建立資料夾允許您：

* 為您的體驗片段建立有意義的結構； 例如，根據分類

   >[!NOTE]
   >
   >您不需要將體驗片段的結構與網站的頁面結構對齊。

* [在資料夾級別分配允許的模板](#configure-allowed-templates-folder)

   >[!NOTE]
   >
   >您可以使用范 [本編輯器](/help/sites-authoring/templates.md) ，建立您自己的範本。

下列範例顯示依據建構的「體驗片段」 `Contributors`。 使用的結構也說明如何使用其他功能，例如多網站管理（包括語言副本）。

>[!CAUTION]
>
>以下螢幕擷取是從WKND網站使用Adobe Experience Manager做為雲端服務擷取的。

![體驗片段的資料夾](assets/xf-folders.png)

## 建立和設定您的體驗片段的資料夾 {#creating-and-configuring-a-folder-for-your-experience-fragments}

若要建立並設定您的體驗片段資料夾，建議您：

1. [建立資料夾](/help/sites-authoring/managing-pages.md#creating-a-new-folder)。

1. [設定該資料夾允許的體驗片段範本](#configure-allowed-templates-folder)。

>[!NOTE]
>
>您也可以設定例項 [的「允許範本」](#configure-allowed-templates-instance)，但不建議使 **用此方法** ，因為升級時可能會覆寫值。

### 為資料夾配置允許的模板 {#configure-allowed-templates-folder}

>[!NOTE]
>
>這是指定允許範本的建 **[!UICONTROL 議方法]**，因為升級時不會覆寫值。

1. 導覽至所需的 **[!UICONTROL Experience Fragments]** 檔案夾。

1. 選擇資料夾，然後選擇「 **[!UICONTROL 屬性]**」。

1. 在「允許的範本」欄位中指定擷取所需範本 **[!UICONTROL 的規則運算式]** 。

   例如：
   `/conf/(.*)/settings/wcm/templates/experience-fragment(.*)?`

   ![體驗片段屬性——允許的範本](assets/xf-folders-templates.png)

1. Select **[!UICONTROL Save and Close]**.

### 為實例配置允許的模板 {#configure-allowed-templates-instance}

>[!CAUTION]
>
>建議您不要使用此方 **[!UICONTROL 法變更「允許的範本]** 」，因為升級時可能會覆寫指定的範本。
>
>請僅供參考之用。

1. 導覽至所需的 **[!UICONTROL Experience Fragments]** Console。

1. 選擇 **[!UICONTROL 配置選項]**:

   ![「配置」按鈕](assets/xf-folders-18.png)

1. 在「設定體驗片段」對話 **[!UICONTROL 方塊中指定必要的範本]** :

   ![設定體驗片段](assets/xf-folders-19.png)

1. 選擇 **[!UICONTROL 保存]**。

## 建立體驗片段 {#creating-an-experience-fragment}

若要建立體驗片段：

1. 從全 **[!UICONTROL 域導覽中選取]** 「體驗片段」。

   ![screen_shot_2018-04-05at92221am1](assets/screen_shot_2018-04-05at92221am1.png)

1. 導覽至所需資料夾，然後選取「 **[!UICONTROL 建立]**」。

1. 選擇 **[!UICONTROL 體驗片段]** ，以開啟「 **[!UICONTROL 建立體驗片段」精靈]** 。

   依次選擇所需 **[!UICONTROL 的範本]**、下 **[!UICONTROL 一步]**:

   ![xf-authoring-02](assets/xf-authoring-02.png)


1. 輸入 **[!UICONTROL 體驗]**&#x200B;片段的屬性。

   標 **[!UICONTROL 題]** 是必填的。 如果名 **[!UICONTROL 稱]** (Name)留空，則會從標題( **[!UICONTROL Title)中衍生出來]**。

   ![xf-authoring-03](assets/xf-authoring-03.png)

1. 按一下&#x200B;**[!UICONTROL 建立]**。

   將顯示一條消息。 選取:

   * **[!UICONTROL 完成]** ：返回控制台
   * **[!UICONTROL 開啟]** ，以開啟片段編輯器

## 編輯您的體驗片段 {#editing-your-experience-fragment}

體驗片段編輯器提供與一般頁面編輯器類似的功能。 如需 [使用頁面內容的詳細資訊](/help/sites-authoring/editing-content.md) ，請參閱編輯頁面內容。

以下示例過程說明如何為產品建立摘要：

1. 從元件瀏覽器 **[!UICONTROL 拖放類別摘]** 要 [](/help/sites-authoring/author-environment-tools.md#components-browser)。

   ![xf-authoring-04](assets/xf-authoring-04.png)

1. 從組 **[!UICONTROL 件工具欄](/help/sites-authoring/editing-content.md#edit-configure-copy-cut-delete-paste)**中選擇「配置」。
1. 新增資 **[!UICONTROL 產]** ，並視需要 **[!UICONTROL 定義屬性]** 。
1. 使用「完成」(勾選 **[!UICONTROL 圖示]** )確認定義。
1. 視需要新增更多元件。

## Creating An Experience Fragment Variation {#creating-an-experience-fragment-variation}

您可以根據您的需求，建立不同的體驗片段：

1. 開啟您的片段以 [進行編輯](/help/sites-authoring/experience-fragments.md#editing-your-experience-fragment)。
1. 開啟「變 **[!UICONTROL 數]** 」標籤。

   ![xf-authoring-06](assets/xf-authoring-06.png)

1. **Create** （建立）允許您建立：

   * **[!UICONTROL 變異]**
   * **[!UICONTROL 變數為 live-copy]**.

1. 定義所需屬性：

   * **[!UICONTROL 範本]**
   * **[!UICONTROL 標題]**
   * **[!UICONTROL 名稱]**; 如果保留空白，則會從「標題」衍生
   * **[!UICONTROL 說明]**
   * **[!UICONTROL 變數標記]**

   ![xf-authoring-07](assets/xf-authoring-07.png)

1. 使用「完 **[!UICONTROL 成]** （勾選圖示）確認」，新變數會顯示在面板中：

   ![xf-authoring-08](assets/xf-authoring-08.png)

## 使用您的體驗片段 {#using-your-experience-fragment}

您現在可以在編寫頁面時使用體驗片段：

1. 開啟任何頁面進行編輯。

   例如： [http://localhost:4502/editor.html/content/we-retail/language-masters/en/products/men.html](http://localhost:4502/editor.html/content/we-retail/language-masters/en/products/men.html)

1. 將元件從「元件」瀏覽器拖曳至頁面段落系統，以建立「體驗片段」元件的例項：

   ![xf-authoring-09](assets/xf-authoring-09.png)

1. 將實際的體驗片段新增至元件例項； 其中：

   * 從「資產瀏覽器」拖曳必要片段至元件
   * Select **[!UICONTROL Configure]** from the component toolbar and specify the fragment to use, confirm with **Done** (tick)

   ![xf-authoring-10](assets/xf-authoring-10.png)

   >[!NOTE]
   >
   >在元件工具列中，編輯會以捷徑方式在片段編輯器中開啟片段。

## 建置區塊 {#building-blocks}

您可以選取一或多個元件，以建立要在片段內回收的建置區塊：

### 建立構建塊 {#creating-a-building-block}

要建立新的構建塊：

1. 在「體驗片段」編輯器中，選取您要重複使用的元件：

   ![xf-authoring-12](assets/xf-authoring-12.png)

1. 從元件工具欄中，選擇「 **[!UICONTROL 轉換為構建塊]**:

   ![xf-authoring-13-icon](assets/xf-authoring-13-icon.png)

   例如：

   ![xf-authoring-13](assets/xf-authoring-13.png)

1. 輸入建置塊的名 **[!UICONTROL 稱]**，並使用 **[!UICONTROL Convert確認]**:

   ![xf-authoring-14](assets/xf-authoring-14.png)

1. 建 **立區塊** (Building Block)將顯示在頁籤中，並可在段落系統中選擇：

   ![xf-authoring-15](assets/xf-authoring-15.png)

### 管理構建塊 {#managing-a-building-block}

您的構建塊在「構建塊」( **[!UICONTROL Building Blocks)頁籤中可見]** 。 對於每個塊，可以執行以下操作：

* 前往主版:在新標籤中開啟主變數
* 重新命名
* 刪除

![xf-authoring-16](assets/xf-authoring-16.png)

### 使用構建塊 {#using-a-building-block}

您可以將構建塊拖動到任何片段的段落系統，如同任何元件。

## 純HTML轉譯 {#the-plain-html-rendition}

使用URL `.plain.` 中的選擇器，您可以存取純HTML轉譯。

這可從瀏覽器取得，但其主要用途是允許其他應用程式（例如協力廠商網頁應用程式、自訂行動裝置實作）僅使用URL直接存取體驗片段的內容。

純HTML轉譯會將通訊協定、主機和內容路徑新增至下列路徑：

* 類型： `src`、 `href`或 `action`

* 或結尾為： `-src`或 `-href`

例如：

`.../brooklyn-coat/master.plain.html`

>[!NOTE]
>
>連結一律會參照發佈例項。 這些連結會由協力廠商使用，因此一律會從發佈例項呼叫連結，而非作者。

![xf-authoring-17](assets/xf-authoring-17.png)

## 匯出體驗片段 {#exporting-experience-fragments}

依預設，體驗片段會以HTML格式傳送。 AEM和協力廠商管道都可使用此功能。

若要匯出至Adobe Target，請使用HTML。 如需 [完整資訊，請參閱Target與體驗片段整合](/help/sites-administering/experience-fragments-target.md) 。


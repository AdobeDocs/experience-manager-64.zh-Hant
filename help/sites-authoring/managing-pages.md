---
title: 建立及組織頁面
seo-title: Creating and Organizing Pages
description: 如何使用AEM建立和管理頁面
seo-description: How to create and manage pages with AEM
uuid: 9bdc3222-6a0c-48a2-be1d-79ceb3bbc828
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: a727c57c-87a9-46c2-8d9b-1348f1ed8ac4
exl-id: 0182155a-0156-458c-b89b-35ab3e27819e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2331'
ht-degree: 5%

---

# 建立及組織頁面{#creating-and-organizing-pages}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

本節說明如何使用Adobe Experience Manager(AEM)建立和管理頁面，以便您 [建立內容](/help/sites-authoring/editing-content.md) 在那幾頁。

>[!NOTE]
>
>您的帳戶需要 [適當的訪問權限](/help/sites-administering/security.md) 和 [權限](/help/sites-administering/security.md#permissions) ，在建立、複製、移動、編輯和刪除等頁面上執行操作。
>
>如果您遇到任何問題，建議您與系統管理員聯繫。

>[!NOTE]
>
>有 [鍵盤快捷鍵](/help/sites-authoring/keyboard-shortcuts.md) 可從網站主控台使用，讓組織頁面更有效率。

## 組織您的網站 {#organizing-your-website}

身為作者，您需要在AEM中組織網站。 這包括建立和命名您的內容頁面，以便：

* 您可在製作環境中輕鬆找到這些標籤
* 您網站的訪客可在發佈環境中輕鬆瀏覽網站

您也可以使用 [資料夾](#creating-a-new-folder) 協助組織內容。

網站的結構可視為存放您內容頁面的樹狀結構。 這些內容頁面的名稱會用來形成URL，而標題會在檢視頁面內容時顯示。

下列是We.Retail網站的範例，其中有遠足短褲頁面( `desert-sky-shorts`):

* 製作環境： `http://localhost:4502/editor.html/content/we-retail/us/en/products/equipment/hiking/desert-sky-shorts.html`

* 發佈環境： `http://localhost:4503/content/we-retail/us/en/products/equipment/hiking/desert-sky-shorts.html`

視您執行個體的設定而定，請使用 `/content` 在發佈環境中可能是選用項目。

```xml
 /content
 /we-retail
  /us
   /en
    /products
     /equipment
      /hiking
       /desert-sky-shorts
       /hiking-poles
       /... 
      /running...
      /surfing...
      /...
     /seasonal...
     /...
    /about-us
    /experience
    /...
   /es...
  /de...
  /fr...
  /...
 /...
```

此結構可從 **網站** 主控台，您可 [瀏覽您網站的頁面](/help/sites-authoring/basic-handling.md#product-navigation) 和在頁面上執行動作。 您也可以建立新網站和 [新頁面](#creating-a-new-page).

您可以從標題列的階層連結看到向上的分支：

![screen_shot_2018-03-22at104706](assets/screen_shot_2018-03-22at104706.png)

### 頁面命名慣例 {#page-naming-conventions}

建立新頁面時，有兩個索引鍵欄位：

* **[標題](#title)**:

   * 這會在主控台中向使用者顯示，並在編輯時顯示在頁面內容頂端。
   * 此欄位為必填.

* **[名稱](#name)**:

   * 這用於生成URI。
   * 此欄位的用戶輸入為可選。 如果未指定，則從標題派生名稱。 請參閱下節 [頁面名稱限制和最佳作法](/help/sites-authoring/managing-pages.md#page-name-restrictions-and-best-practices) 以取得詳細資訊。

#### 頁面名稱限制和最佳作法 {#page-name-restrictions-and-best-practices}

頁面 **標題****和名稱可以單獨建立** ，但是是相關的：

* 建立頁面時，僅 **標題** 欄位為必填。 若否 **名稱** 會在建立頁面時提供，AEM會從標題的前64個字元產生名稱（遵循下列驗證）。 僅使用前64個字元，以支援短頁面名稱的最佳作法。

* 如果作者手動指定頁面名稱，64個字元的限制不適用，但頁面名稱長度的其他技術限制可能會適用。

>[!NOTE]
>
>定義頁面名稱時，最佳的經驗法則是盡可能保持頁面名稱簡短，但盡可能表達力和令人難忘，讓讀者更容易理解。 請參閱 [W3C樣式指南](https://www.w3.org/Provider/Style/TITLE.html) 針對 `title` 元素以取得詳細資訊。
>
>另請記住，有些瀏覽器（例如舊版IE）只能接受長度達特定的URL，因此也有技術原因需要縮短頁面名稱。

建立新頁面時，AEM將 [根據慣例驗證頁面名稱](/help/sites-developing/naming-conventions.md) 由AEM和JCR強加。

允許的字元數下限為：

* &#39;a&#39;到&#39;z&#39;
* &#39;A&#39;到&#39;Z&#39;
* &#39;0&#39;到&#39;9&#39;
* _（下划線）
* `-` （連字型大小/減號）

所有允許字元的完整詳細資訊，請參閱 [命名慣例](/help/sites-developing/naming-conventions.md).

>[!NOTE]
>
>如果AEM在 [MongoMK持久性管理器部署](/help/sites-deploying/recommended-deploys.md)，頁面名稱上限為150個字元。

#### 標題 {#title}

如果您在建立新頁面時只提供頁面 **Title** ,AEM會從此字串衍生頁面 **Name**[ ，並根據AEM和JCR所強加的慣例來驗證名稱。](/help/sites-developing/naming-conventions.md)A **標題** 包含無效字元的欄位將被接受，但派生的名稱將替換無效字元。 例如：

| 標題 | 衍生名稱 |
|---|---|
| 捨恩 | schoen.html |
| SC%&amp;&amp;ast;ç+ | sc---c-.html |

#### 名稱 {#name}

提供頁面時 **名稱** 建立新頁面時，AEM將 [根據慣例驗證名稱](/help/sites-developing/naming-conventions.md) 由AEM和JCR強加。 您無法提交 **名稱** 欄位。 當AEM偵測到無效字元時，欄位將會強調顯示並顯示說明訊息。

![screen_shot_2018-03-22at104817](assets/screen_shot_2018-03-22at104817.png)

>[!NOTE]
>
>除非是語言根，否則應避免使用ISO-639-1所定義的雙字母代碼作為頁面名稱。
>
>請參閱 [準備翻譯內容](/help/sites-administering/tc-prep.md) 以取得更多資訊。

### 範本 {#templates}

在AEM中，範本會指定專用的頁面類型。 模板將用作建立任何新頁面的基礎。

範本定義包含縮圖影像和其他屬性的頁面結構。 例如，您可能有不同的產品頁面、網站地圖和聯絡資訊範本。 模板由 [元件](#components).

AEM隨附數個現成可用的範本。 可用的範本取決於個別網站。 關鍵欄位為：

* **標題**
產生的網頁上顯示的標題。

* **名稱**
為頁面命名時使用。

* **範本**
可在生成新頁面時使用的模板清單。

>[!NOTE]
>
>若已在您的執行個體上設定， [範本作者可使用範本編輯器建立範本](/help/sites-authoring/templates.md).

### 元件 {#components}

元件是AEM提供的元素，可讓您新增特定類型的內容。 AEM隨附一系列 [現成可用的元件](/help/sites-authoring/default-components-console.md) 提供全面功能。 這些類別包括：

* 文字
* 影像
* Slideshow
* 影片
* 還有更多

建立並開啟頁面後，您可以 [使用元件新增內容](/help/sites-authoring/editing-content.md#inserting-a-component)，可從 [元件瀏覽器](/help/sites-authoring/author-environment-tools.md#components-browser).

>[!NOTE]
>
>此 [元件主控台](/help/sites-authoring/default-components-console.md) 提供執行個體上元件的概觀。

## 管理頁面 {#managing-pages}

### 建立新頁面 {#creating-a-new-page}

除非您事先已為您建立所有頁面，否則您必須先建立頁面，才能開始建立內容：

1. 開啟Sites主控台(例如 [http://localhost:4502/sites.html/content](http://localhost:4502/sites.html/content))。
1. 導覽至您要建立新頁面的位置。
1. 使用工具列中的「建立」 **** ，開啟下拉式選取器，然後從清單中選 **取「頁面** 」:

   ![screen_shot_2018-03-22at104944](assets/screen_shot_2018-03-22at104944.png)

1. 從精靈的第一階段，您可以執行下列任一動作：

   * 選取您要用來建立新頁面的範本，然後按一下/點選 **下一個** 繼續。
   * **取消** 中止程式。

   ![chlimage_1-8](assets/chlimage_1-8.png)

1. 從精靈的最後一個階段，您可以執行下列任一操作：

   * 使用三個標籤輸入 [頁面屬性](/help/sites-authoring/editing-page-properties.md) 您要指派給新頁面，然後按一下/點選 **建立** 來實際建立頁面。
   * 使用 **返回** 返回到模板選擇。

   關鍵欄位包括：

   * **標題**:

      * 這會向使用者顯示，且為必要項目。
   * **名稱**:

      * 這用於生成URI。 如果未指定，則從標題派生名稱。
      * 如果您提供頁面 **名稱** 建立新頁面時，AEM將 [根據慣例驗證名稱](/help/sites-developing/naming-conventions.md) 被AEM和JCR所取代。
      * 您 **無法提交無效字元** 在 **名稱** 欄位。 當AEM偵測到無效字元時，欄位會反白顯示，並顯示說明訊息，指出需要移除/取代的字元。

   >[!NOTE]
   >
   >請參閱 [頁面命名慣例](#page-naming-conventions).

   建立新頁面所需的最低資訊為 **標題**.

   ![chlimage_1-9](assets/chlimage_1-9.png)

1. 使用 **建立** 以完成程式並建立新頁面。 確認對話方塊會詢問您是否要 **開啟** 頁面立即顯示，或返回主控台(**完成**):

   ![chlimage_1-10](assets/chlimage_1-10.png)

   >[!NOTE]
   >
   >如果您使用該位置已存在的名稱建立頁面，系統將通過附加數字自動生成該名稱的變化。 例如，若 `winter` 已存在新頁面將變成 `winter0`.

1. 如果您返回主控台，則會看到您的新頁面：

   ![screen_shot_2018-03-22at105321](assets/screen_shot_2018-03-22at105321.png)

>[!CAUTION]
>
>建立頁面後，就無法變更其範本，除非您 [使用新範本建立啟動](/help/sites-authoring/launches-creating.md#create-launch-with-new-template)，不過這會遺失任何已存在的內容。

### 開啟頁面進行編輯 {#opening-a-page-for-editing}

建立頁面或導覽至現有頁面（在主控台中）後，您可以開啟它進行編輯：

1. 開啟 **網站** 控制台。
1. 導覽，直到找到您要編輯的頁面為止。
1. 使用下列任一項來選取您的頁面：

   * [快速動作](/help/sites-authoring/basic-handling.md#quick-actions)
   * [選擇模式](/help/sites-authoring/basic-handling.md#product-navigation) 和工具欄

   然後選取 **編輯** 圖示：

   ![screen_shot_2018-03-22at105355](assets/screen_shot_2018-03-22at105355.png)

1. 頁面將會開啟，您可以 [編輯頁面](/help/sites-authoring/editing-content.md) 視需要。

>[!NOTE]
>
>從頁面編輯器導覽至其他頁面只能在「預覽」模式中，因為連結在「編輯」模式中未處於作用中狀態。

### 複製和貼上頁面 {#copying-and-pasting-a-page}

您可以將頁面及其所有子頁面複製到新位置：

1. 在 **網站** 主控台，導覽，直到找到您要複製的頁面為止。
1. 使用下列任一項選取您的頁面：

   * [快速動作](/help/sites-authoring/basic-handling.md#quick-actions)
   * [選擇模式](/help/sites-authoring/basic-handling.md#product-navigation) 和工具欄

   然後 **複製** 頁面圖示：

   ![screen_shot_2018-03-22at105425](assets/screen_shot_2018-03-22at105425.png)

   >[!NOTE]
   >
   >如果您處於選取模式，則複製頁面時，就會自動退出。

1. 導覽至頁面新復本的位置。
1. 使用 **貼上** 頁面圖示：

   ![screen_shot_2018-03-22at105510](assets/screen_shot_2018-03-22at105510.png)

   原始頁面和任何子頁面的副本將在此位置建立。

   >[!NOTE]
   >
   >如果將頁面複製到與原始頁面同名的頁面已存在的位置，系統將通過附加數字自動生成名稱的變化。 例如，若 `winter` 已存在 `winter` 將 `winter1`.

### 移動或重新命名頁面 {#moving-or-renaming-a-page}

>[!NOTE]
>
>重新命名頁面也受 [頁面命名慣例](#page-naming-conventions) 指定新頁面名稱時。

>[!NOTE]
>
>頁面只能移至允許頁面所依據之範本的位置。 請參閱 [範本可用性](/help/sites-developing/templates.md#template-availability) 以取得更多資訊。

移動或重新命名頁面的程式基本相同，由相同精靈處理。 使用此嚮導，您可以：

* 重新命名頁面而不移動它。
* 移動頁面而不重新命名。
* 同時移動並重新命名。

AEM提供您更新任何內部連結的功能，這些連結會參照被重新命名/移動的頁面。 您可以逐頁完成這項作業，以提供完全的彈性。

1. 導覽，直到找到您要移動的頁面為止。
1. 使用下列任一項選取您的頁面：

   * [快速動作](/help/sites-authoring/basic-handling.md#quick-actions)
   * [選擇模式](/help/sites-authoring/basic-handling.md#product-navigation) 和工具欄

   然後選取 **移動** 頁面圖示：

   ![screen_shot_2018-03-22at105534](assets/screen_shot_2018-03-22at105534.png)

   這會開啟移動頁面精靈。

1. 從 **重新命名** 您可以執行以下任一操作：

   * 指定移動頁面後要擁有的名稱，然後按一下/點選 **下一個** 繼續。
   * **取消** 中止程式。

   ![chlimage_1-11](assets/chlimage_1-11.png)

   如果您只要移動頁面，頁面名稱可以維持不變。

   >[!NOTE]
   >
   >如果將頁面移至已存在同名頁面的位置，系統會透過附加數字來自動產生名稱的變異。 例如，若 `winter` 已存在 `winter` 將 `winter1`.

1. 從 **選擇目標** 您可以執行以下任一操作：

   * 使用 [欄檢視](/help/sites-authoring/basic-handling.md#column-view) 要導覽至頁面的新位置，請執行以下操作：

      * 按一下目的地的縮圖，以選取目的地。
      * 按一下 **下一個** 繼續。
   * 使用 **返回** 返回頁名規範。

   ![chlimage_1-12](assets/chlimage_1-12.png)

   >[!NOTE]
   >
   >如果將頁面移至已存在同名頁面的位置，系統會透過附加數字來自動產生名稱的變異。 例如，若 `winter` 已存在 `winter` 將 `winter1`.

1. 如果頁面連結或參照，則這些參照會列在 **調整/重新發佈** 步驟。 您可以指出哪些項目應適當加以調整並重新發佈。

   ![chlimage_1-13](assets/chlimage_1-13.png)

1. 選取 **移動** 會完成程式，並視需要移動/重新命名頁面。

>[!NOTE]
>
>如果頁面已發佈，移動頁面會自動解除發佈。依預設，移動完成時會重新發佈它，但您可以取消勾選 **重新發佈** 欄位 **調整/重新發佈** 步驟。

>[!NOTE]
>
>如果頁面未以任何方式參照，則 **調整/重新發佈** 步驟。

### 刪除頁面 {#deleting-a-page}

1. 導覽，直到您看到要刪除的頁面為止。
1. 使用 [選擇模式](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) 若要選取所需頁面，請使用 **刪除** 從工具列：

   ![screen_shot_2018-03-22at105622](assets/screen_shot_2018-03-22at105622.png)

   >[!NOTE]
   >
   >為了安全起見，「刪 **** 除」頁面圖示不能作為快速動作使用。

1. 對話會要求確認。

   * **您要在刪除前先封存頁面嗎?**  — 如果選中此選項，則刪除時將建立要刪除的頁面的版本。
      * [版本可在稍後還原。](/help/sites-authoring/working-with-page-versions.md)
      * 無法還原沒有舊版刪除的頁面。
      * 此選項僅適用於AEM 6.4.7.0版。
   * **取消** 中止動作
   * **刪除** 若要確認動作：

      * 如果頁面沒有參考，則會刪除頁面。
      * 如果頁面有參考，則訊息方塊會通知您 **參考一或多個頁面。** 您可以選取 **強制刪除** 或 **取消**.

>[!NOTE]
>
>如果頁面已發佈，則會在刪除前自動取消發佈。

### 鎖定頁面 {#locking-a-page}

您可以 [鎖定/解除鎖定頁面](/help/sites-authoring/editing-content.md#locking-a-page) 或編輯個別頁面時傳送。 關於頁面是否已鎖定的資訊也會顯示在兩個位置中。

![screen_shot_2018-03-22at105713](assets/screen_shot_2018-03-22at105713.png) ![screen_shot_2018-03-22at105720](assets/screen_shot_2018-03-22at105720.png)

### 建立新資料夾 {#creating-a-new-folder}

您可以建立資料夾，以協助組織您的檔案和頁面。

>[!NOTE]
>
>資料夾也受 [頁面命名慣例](#page-naming-conventions) 指定新資料夾名稱時。

>[!CAUTION]
>
>* 資料夾只能直接在 **網站** 或在其他資料夾下。 無法在頁面下建立。
>* 標準動作移動、複製、貼上、刪除、發佈、取消發佈，以及檢視/編輯屬性可在資料夾上執行。
>* 資料夾無法用於即時副本中的選擇。
>


1. 開啟 **網站** 控制台並導覽至所需位置。
1. 若要開啟選項清單，請選取 **建立** 從工具列
1. 選擇 **資料夾** 來開啟對話框。 您可以在此輸入 **名稱** 和 **標題**:

   ![chlimage_1-14](assets/chlimage_1-14.png)

1. 選擇 **建立** 來建立資料夾。

---
title: 茶匙和策略
seo-title: 茶匙和策略
description: 行銷活動通常使用茶匙作為機制，吸引特定訪客群體進入關注其興趣的內容。 為特定促銷活動定義一或多個茶匙。
seo-description: 行銷活動通常使用茶匙作為機制，吸引特定訪客群體進入關注其興趣的內容。 為特定促銷活動定義一或多個茶匙。
uuid: 496caa14-2e91-4544-b3fc-12e0fe0da88d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 86a31407-96a4-467c-9468-da4095ca38d5
exl-id: 311ffab4-8bc9-486b-9ca5-a958f13f16f8
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 5%

---

# 茶匙和策略{#teasers-and-strategies}

行銷活動通常使用茶匙作為機制，吸引特定訪客群體進入關注其興趣的內容。 為特定促銷活動定義一或多個茶匙。

>[!NOTE]
>
>AEM 6.2已棄用Teaser元件。

* **品牌** 頁面會儲存在網站的「促銷活動」區段中。品牌包含個別的促銷活動。

* **促銷** 活動頁面會儲存在網站的「促銷活動」區段中。每個促銷活動都有個別頁面，預告定義會保留在其中。 容器（或概觀）頁面也包含與個別宣傳預告頁面相關的特定資訊和統計資料。

AEM內的茶匙由幾部分組成：

* **預告** 頁面會儲存在適當的促銷活動頁面下，並保留每個特定促銷活動可用的預告段落定義。顯示預告段落時會使用這些定義；包括內容變異，用於選取變異和提升因子的區段。
* **預告元件**&#x200B;可立即使用，並可讓您在內容頁面中建立特定預告段落的例項。 您可以從sidekick拖曳預告元件，然後指定您的預告定義以建立您自己的預告段落。 **注意：** AEM 6.2已棄用Teaser元件。

* **預告** 段落是內容頁面中預告的實際實例。這吸引了一部分遊客到關注他們興趣的內容。
* 將促銷活動內容集中在特定訪客群體上的頁面。 通常宣傳段落會將訪客導向至這類頁面。

## 策略 {#strategies}

將宣傳預告段落新增至頁面時，您需要定義&#x200B;**Strategy**。

這是因為數個茶匙可供選取，因為其指派的區段都能成功解析。 然後， **Strategy**&#x200B;會指定用於選擇所顯示預告的額外標準：

* **點按流分數**，是根據訪客用戶端內容中保留的標籤與相關標籤點擊（顯示訪客點按包含個別標籤之頁面的頻率）而得。會比較預告頁面上定義之標籤的點擊率。
* **隨機**，用於「隨機」選取；使用為頁面產生的隨機因素，這可在用戶端內容 [中看到](/help/sites-administering/client-context.md)。

* **** 固定已解析的區段清單。順序是促銷活動容器頁面內的茶匙的順序。

區段的[提升因子](/help/sites-administering/campaign-segmentation.md#boost-factor)也會影響選取。 這是新增至區段定義的加權因數，以增加/減少其被選取的相對可能性。

各種選擇標準的流程和相互關係最好以範例來說明（此方法也可用來確保您的茶具將觸及所需對象）。

如果已建立下列區段並指派其各自的提升系數：

| 區段 | 提升因子 |
|---|---|
| S1 | 0 |
| S2 | 0 |
| S3 | 10 |
| S4 | 30 |
| S5 | 0 |
| S6 | 100 |

我們使用下列宣傳預告定義：

<table> 
 <tbody> 
  <tr> 
   <td>行銷活動</td> 
   <td>Teaser</td> 
   <td>指派的區段</td> 
   <td>指派的標籤 </td> 
  </tr> 
  <tr> 
   <td>C1</td> 
   <td>T1</td> 
   <td>S1、S2</td> 
   <td>商業、行銷</td> 
  </tr> 
  <tr> 
   <td>C1</td> 
   <td>T2 </td> 
   <td>S1</td> 
   <td><br /> </td> 
  </tr> 
  <tr> 
   <td>C1 </td> 
   <td>T3</td> 
   <td>S3、S4</td> 
   <td><br /> </td> 
  </tr> 
  <tr> 
   <td>C1 </td> 
   <td>T4</td> 
   <td>S2、S5</td> 
   <td><br /> </td> 
  </tr> 
  <tr> 
   <td>C1 </td> 
   <td>T5</td> 
   <td>S1、S2、S6</td> 
   <td>行銷</td> 
  </tr> 
  <tr> 
   <td>C1 </td> 
   <td>T6</td> 
   <td>S6</td> 
   <td>商務<br /> </td> 
  </tr> 
 </tbody> 
</table>

如果我們將此套用至下列位置的訪客：

* **S1**、 **S2** 和 **S6** 成功解析

* 標籤&#x200B;**marketing**&#x200B;有3次點擊
* 標籤&#x200B;**business**&#x200B;有6次點擊

我們可以看到結果：

* 符合成功 — 是否能為目前的訪客成功解析指派給預告的任何區段？
* 提升因子 — 所有適用區段的最高提升因子
* 點按資料流分數 — 所有適用標籤點擊的累積總計

策略前計算：

<table> 
 <tbody> 
  <tr> 
   <td>行銷活動</td> 
   <td>Teaser</td> 
   <td>指派的區段</td> 
   <td>標記 </td> 
   <td>成功匹配？</td> 
   <td>產生的提升因子</td> 
   <td>產生的點按流分數 </td> 
  </tr> 
  <tr> 
   <td>C1</td> 
   <td>T1</td> 
   <td>S1、S2</td> 
   <td>商業、行銷</td> 
   <td>是</td> 
   <td>0</td> 
   <td>9</td> 
  </tr> 
  <tr> 
   <td>C1</td> 
   <td>T2 </td> 
   <td>S1</td> 
   <td><br /> </td> 
   <td>是</td> 
   <td>0</td> 
   <td><br /> </td> 
  </tr> 
  <tr> 
   <td>C1 </td> 
   <td>T3</td> 
   <td>S3、S4</td> 
   <td><br /> </td> 
   <td>否</td> 
   <td><br /> </td> 
   <td><br /> </td> 
  </tr> 
  <tr> 
   <td>C1 </td> 
   <td>T4</td> 
   <td>S2、S5</td> 
   <td><br /> </td> 
   <td>是<br /> </td> 
   <td>0<br /> </td> 
   <td><br /> </td> 
  </tr> 
  <tr> 
   <td>C1 </td> 
   <td>T5</td> 
   <td>S1、S2、S6</td> 
   <td>行銷</td> 
   <td>是</td> 
   <td>100</td> 
   <td>3</td> 
  </tr> 
  <tr> 
   <td>C1 </td> 
   <td>T6</td> 
   <td>S6</td> 
   <td>商務</td> 
   <td>是</td> 
   <td>100</td> 
   <td>6 </td> 
  </tr> 
 </tbody> 
</table>

這些值可根據套用至宣傳預告段落的&#x200B;**Strategy**，來判斷訪客將看到的宣傳預告：

<table> 
 <tbody> 
  <tr> 
   <td>策略</td> 
   <td>產生的預告</td> 
   <td>評論</td> 
  </tr> 
  <tr> 
   <td>第一個</td> 
   <td>T5</td> 
   <td>只有T5和T6被視為其段，它們都解析<i>和</i>，它們具有最高的提升因子。 返回的清單按T5、T6的順序排列；以便選擇並顯示T5。</td> 
  </tr> 
  <tr> 
   <td>隨機</td> 
   <td>T5或T6</td> 
   <td>兩個茶匙都有各自解決的區段，且提升系數相同。 因此，兩茶匙以相同比例顯示。</td> 
  </tr> 
  <tr> 
   <td>點按流分數</td> 
   <td>T6</td> 
   <td><p>T1、T4、T5和T6的區段都會針對訪客解析。 T5和T6的升高因子則排除T1和T4。 最後，T6的點按資料流分數越高，系統便會選取此分數。</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>在上述解析度技術之後，如果有多個預告可供選擇，則內部選擇（隨機）將選擇一個預告供顯示。
>
>例如，如果策略是「點按流分數」，而T5的點按流分數與T6相同（即6而非3），則會使用內部選取（隨機）來選取這兩者之一。

「預告頁面/段落」可用來將特定訪客區段導向著重於其興趣的內容。 它們可以呈現一系列選項供訪客選擇，或僅顯示一個以特定訪客區段為基礎的預告段落；例如，顯示的預告段落可能取決於訪客的年齡。

預告頁面通常是會持續特定一段時間的臨時動作，直到被下一個預告頁面取代為止。

建立您的品牌和行銷活動後，您可以建立並設定您的預告體驗。

## 為您的Teaser {#creating-a-touchpoint-for-your-teaser}建立接觸點

>[!NOTE]
>
>AEM 6.2已棄用Teaser元件。

1. 導覽至內容頁面，您想要放置將導向促銷活動頁面的預告段落。
1. 將&#x200B;**Teaser**&#x200B;元件（可在sidekick的&#x200B;**Personalization**&#x200B;區段中取得）新增至所需位置。 首次建立時，它會顯示促銷活動路徑尚未設定：

   ![chlimage_1-4](assets/chlimage_1-4.png)

1. 編輯宣傳預告元件以新增：

   * **包含**
個別宣傳預告頁面之促銷活動頁面的促銷活動PathPath;區段會確切決定要顯示哪個預告。
   * **[](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#strategies)**
成功解析多個區段時用於選取的StrategyMethod。
   ![chlimage_1-5](assets/chlimage_1-5.png)

1. 按一下&#x200B;**OK**&#x200B;以儲存。 根據您在預告上設定的區段，以及您目前登入的使用者設定檔，將會顯示適當的內容：

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. 將滑鼠移至預告段落上以顯示問號圖示（元件的右下角）。 按一下這個按鈕即可檢視套用的區段，以及這些區段目前是否已解析。

   ![chlimage_1-7](assets/chlimage_1-7.png)

## 預告概述{#teaser-overview}

除了MCM中的促銷活動檢視外，促銷活動頁面也提供與其連接的茶匙的資訊：

1. 從&#x200B;**網站**&#x200B;主控台，開啟促銷活動頁面；例如：

   `http://localhost:4502/content/campaigns/geometrixx-outdoors/storefront/summer.html`

   這會顯示預告定義和檢視統計資料的概述：

   ![chlimage_1-8](assets/chlimage_1-8.png)

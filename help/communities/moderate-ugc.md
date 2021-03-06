---
title: 調節社群內容
seo-title: 調節社群內容
description: 協調概念和動作
seo-description: 協調概念和動作
uuid: a24d09e7-3260-4eec-844e-97e6849c94d8
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: d11b8fc8-5e98-4a77-a536-d445ac88e1b3
role: Admin
exl-id: 9865b366-b9e5-40f3-8863-789ccfb792f5
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '1519'
ht-degree: 0%

---

# 調節社群內容 {#moderating-community-content}

## 概覽 {#overview}

當成員（登入網站訪客）透過與下列其中一個社群元件互動來發佈來自已發佈社群網站的內容時，會建立社群內容(也稱為使用者產生的內容(UGC)):

* [部落格](blog-feature.md):成員發佈部落格文章或評論
* [日曆](calendar.md):發佈日曆事件或留言的成員
* [評論](comments.md):成員發佈評論或回複評論
* [論壇](forum.md):成員發佈新主題或回復主題
* [構想](ideation-feature.md):成員發佈構想或留言
* [QnA](working-with-qna.md):成員可建立問題或回答問題
* [評論](reviews.md):評分項目時，成員會張貼留言

UGC的調節有助於識別正面貢獻以及限制負面貢獻（例如垃圾訊息和辱罵性語言）。 UGC可從數個環境中審核：

* [大量協調主控台](moderation.md)

   管理員和[社群協調者](users.md)可在公用環境中存取「協調」主控台，也可由製作環境中的管理員存取。 當社群內容儲存在[公用存放區](working-with-srp.md)中時，就可能發生此情況。

* [內容內協調](in-context.md)

   發佈環境中的協調可由管理員和社群協調者直接在發佈內容的頁面上執行。

## 協調動作 {#moderation-actions}

可對發佈內容(UGC)執行的動作會依使用者身分和環境而有所不同。 下表使用下列術語，根據使用者身分描述各種角色：

* `Admin`\
   [community-administrators](users.md)組的成員用戶
* `Moderator`
社群協調者 [群](users.md#publishenvironmentusersandgroups) 組的成員(具 [有協調者權限](in-context.md#moderatorpermissions))
* `Creator`\
   發佈內容的使用者
* `Member`\
   沒有特殊權限的登入使用者
* `Visitor`
匿名用戶

<table> 
 <tbody>
  <tr>
   <td> </td> 
   <td><strong>管理員</strong></td> 
   <td><strong>版主</strong></td> 
   <td><strong>產生器</strong></td> 
   <td><strong>成員</strong></td> 
   <td><strong>訪客</strong></td> 
   <td><strong>事件<br />已觸發</strong></td> 
   <td><strong>已預先審核</strong></td> 
  </tr>
  <tr>
   <td><strong>編輯/<br />刪除</strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td><strong>剪下</strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td><strong>拒絕</strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>X</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><strong>關閉/<br />重新開啟</strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>X</td> 
   <td>X<br /> </td> 
  </tr>
  <tr>
   <td><strong>標幟/<br />取消標幟</strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td>X</td> 
   <td> </td> 
   <td>X</td> 
   <td> </td> 
  </tr>
  <tr>
   <td><strong>允許</strong></td> 
   <td>X</td> 
   <td>X</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>X</td> 
   <td>X</td> 
  </tr>
 </tbody>
</table>

### 編輯/刪除 {#edit-delete}

貼文發表後，建立者、管理員或社群版主可以編輯或刪除貼文。

刪除UGC後，該UGC將從儲存庫中刪除，並且可能無法恢復。

### 剪下 {#cut}

管理員或社區協調者可以將一個或多個論壇主題或QnA問題從一個位置移動到另一個位置。 這包括從一個社群網站到另一個社群網站，前提是同一成員在這兩個網站上都擁有協調權限。

選取「剪下」動作後，內容會複製到剪貼簿。 多則貼文可以複製，並以群組形式移動至新位置。

![](assets/cutugc.png) ![cutugcputbackugc](assets/putbackugc.png)

在另一個位置，當剪貼簿中出現內容時，新貼文旁會顯示「貼上」按鈕，其中數字代表將貼上的貼文數量。 「貼上」按鈕包含清除剪貼簿而非貼上的選項。

![chlimage_1-218](assets/chlimage_1-218.png) ![chlimage_1-219](assets/chlimage_1-219.png)

### 拒絕 {#deny}

版主可能不允許UGC在已發佈的網站上保持可見。 對於管理員和社群協調者，貼文仍可供使用，且會加上垃圾訊息注釋。

### 關閉/重新開啟 {#close-reopen}

「關閉」動作會針對整個對話線程（論壇主題或初始評論）執行，並包含所有後續貼文或回覆。

關閉時，不僅無法進一步回覆，也不允許任何協調動作。

要執行任何操作，主題或注釋必須重新開啟。

管理員或社群協調者可以執行「關閉/重新開啟」動作。

### 標幟/取消標幟 {#flag-unflag}

標幟是任何已登入成員（內容的建立者除外）的方法，用以指出貼文內容有問題。 標籤後，會出現取消標幟圖示，讓相同的成員取消標幟內容。

內容內協調可設定為允許成員在標籤貼文時選取原因。 可配置可選標誌原因清單，包括是否可輸入自定義原因。 標幟原因會以UGC儲存，但原因不會觸發任何特定動作。 只有標幟數會觸發通知。 標幟內容會以此方式加上註解，以便協調者可依此方式行動。

系統會追蹤所有已標幟、已標幟以及標幟原因，並在達到臨界值時傳送事件。 如果社群版主允許UGC，則會封存這些標幟。 在允許和歸檔後，如果有後續的標籤，則會將其歸檔，就像以前沒有標籤一樣。

### 允許 {#allow}

「允許」動作是UGC的選項，其已標籤、拒絕或未在預先審核的系統中核准。 「允許」動作會清除任何已標幟或已拒絕/垃圾訊息狀態，並封存任何已標幟資料。

## 常見的協調概念 {#common-moderation-concepts}

### 預先協調 {#premoderation}

UGC經過預先審核後，貼文在經過協調動作核准後，才會顯示在已發佈的網站上。 在建立[社群網站](sites-console.md)期間，核取方塊` [Content is Premoderated](sites-console.md#moderation)`將啟用整個網站的預先協調。 將元件放在頁面上後，即可使用其編輯對話方塊中的設定，將支援協調的元件設定為預先協調：

* [](comments.md) 評論和 [評論](reviews.md)

   在「**[!UICONTROL 使用者協調]**」標籤上，勾選「**[!UICONTROL 預先協調]**」

* [論壇](forum.md)、 [構思](ideation-feature.md)、 [QnA](working-with-qna.md)和日曆 [](calendar.md) 設定 **** 標籤，勾選 **[!UICONTROL 已審核]**

### 垃圾郵件檢測 {#spam-detection}

垃圾訊息偵測是自動協調功能，可將提交的使用者產生的內容標示為垃圾訊息，以篩選掉不想要的片段。 啟用後，它會根據預先設定的垃圾訊息集合來識別使用者產生的內容是否為垃圾訊息。 預設的垃圾郵件字詞提供於

`/libs/settings/community/sites/moderation/spamdetector-conf/profiles/spam_words.txt`。

但是，要自定義或擴展預設垃圾郵件字詞，請在/apps目錄中建立一組字詞，並遵循預設垃圾郵件字詞的結構，方法為[overlay](overlay-comments.md)。

使用者產生的包含垃圾訊息字詞的貼文（涵蓋所有內容類型，例如部落格、論壇和留言），在貼文上方會標示為「此貼文已分類為垃圾訊息」。

版主可以看到這樣的貼文，並標示相同的貼文，以允許或拒絕出現在網站上。 這些貼文的協調動作可在內容內或透過大量協調UI來執行。

![垃圾郵件檢測](assets/spamdetection.png)

要啟用垃圾郵件檢測引擎，請執行以下步驟：

1. 開啟[Web控制台](http://localhost:4502/system/console/configMgr)，方法是前往`/system/console/configMgr`。

1. 找出&#x200B;**[!UICONTROL AEM Communities自動協調]**&#x200B;設定，並加以編輯。
1. 新增`SpamProcess`項目。

![垃圾郵件處理](assets/spamprocess.png)

>[!NOTE]
>
>垃圾郵件檢測僅針對英語區域設定實施。

### 情緒 {#sentiment}

情緒是根據貼文(UGC)中呈現的正面和負面關鍵字([watchwords](#configuringwatchwords))數目計算。

情緒分析使用一組預先設定的規則，並計算UGC的情緒。 預設規則位於`/libs/cq/workflow/components/workflow/social/sentiments/rules.`

規則產生的值從1（所有負面，無正面字詞）到10（所有正面，無負面字詞）。 情緒值5為中性情緒，為預設值。

/libs元件中定義的規則為：

* 規則1:如果沒有正面字詞，且至少有一個負面字詞，則將值設為1
* 規則2:如果沒有負面字詞，且至少有一個正面字詞，則將值設為10
* 規則3:如果負面字詞多於正面字詞，請將值設為3
* 第4條：如果正面字詞多於負面字詞，請將值設為8

若要覆寫或新增規則，請依照預設規則的結構，在/apps目錄中建立一組規則。 編輯情緒設定以識別規則的位置。

分析後，情緒會與UGC一起儲存。

在[大量協調控制台](moderation.md)中，可以根據情緒是負面、中性或正面來篩選和檢視UGC。

#### 口碑 {#watchwords}

AEM社群提供*watchword analyzer *作為評估[情緒](#sentiment)的程式中的步驟。 關注字詞對情緒值的貢獻，是因為張貼內容中使用的負面和正面關注字詞，以及禁止字詞的比較。

#### 設定情緒和觀看字詞 {#configure-sentiment-and-watchwords}

正面和負面觀看字清單可自訂，因為可以是情緒規則。

預設的監視字詞清單可以作為節點的屬性在儲存庫中輸入，類似於預設值，或者通過使用字詞清單配置OSGi服務`sentimentprocess.name`來覆蓋預設值。

也可以修改&#x200B;**sentimentprocess.name**&#x200B;以參考一組自訂情緒規則的位置。

若要設定情緒和口號：

* 在製作例項上
* 以管理員身分登入
* 開啟[Web控制台](http://localhost:4502/system/console/configMgr)
* 找到`sentimentprocess.name`
* 選取要在編輯模式中開啟的設定

![情緒過程](assets/sentimentprocess.png)

* **正**
面關注字詞(Besitive Watchwords)導致正面情緒覆寫預設值的以逗號分隔的字詞清單。預設為空白清單。

* **負**
面字詞(Negative Watchwords)導致負面情緒且覆寫預設值的以逗號分隔的字詞清單。預設為空白清單。

* **監視詞節點的顯**
式路徑包含預設值的節點的儲存庫位置 
`positive` 和指 `negative` 定預設監看字的屬性。預設值為`/libs/settings/community/watchwords/default`。

* **情緒**
規則根據正面和負面關鍵字計算情緒之規則的存放庫位置。預設為 
`/libs/cq/workflow/components/workflow/social/sentiments/rules` （不過，不再涉及任何工作流程）。

以下是當`Explicit Path to Watchwords Node`設為`/libs/settings/community/watchwords/default`時，預設關注字詞的自訂項目範例。

![crxde](assets/crxde.png)

### 版主權限 {#moderator-permissions}

將下列權限指派給相同資源時，統稱為&#x200B;**`moderator permissions`**:

* `Read`
* **`Modify`**
* `Create`
* `Delete`
* `Replicate`

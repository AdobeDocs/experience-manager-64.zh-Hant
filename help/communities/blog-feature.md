---
title: 部落格功能
seo-title: 部落格功能
description: 以日誌格式提供社區資訊
seo-description: 以日誌格式提供社區資訊
uuid: 01f1a547-d22b-4da6-a69c-ab420e5a9e19
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: d5519211-8a04-4699-97bc-e162ec0f3781
exl-id: 12ae8b4c-73c5-4ec9-beea-b682b55ebdfd
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1604'
ht-degree: 4%

---

# 部落格功能{#blog-feature}

## 簡介 {#introduction}

AEM Communities的部落格功能已從編寫活動轉換為在發佈環境中發生的真正社群活動。

部落格功能支援以日誌格式提供社群資訊。 部落格項目是由授權成員（註冊、登入使用者）在發佈環境中撰寫。

部落格功能提供：

* 發佈端建立部落格文章和評論
* RTF編輯
* 內嵌影像（支援拖放）
* 嵌入的社交網路內容([oEmbed support](blog-developer-basics.md#allowing-rich-media))
* 草稿模式
* 排程發佈
* 代表撰寫（[特權成員](users.md#privileged-members-group)可以代表不同社群成員建立內容）
* [部落格文章與評論的內](moderate-ugc.md) 容與大量協調

本檔案的本節說明

* 將部落格功能新增至AEM網站
* 部落格元件的組態設定

>[!NOTE]
>
>元件`Journal`和`Journal Sidebar`的標題為`Blog`和`Blog Sidebar`。
>
>AEM 6.0及舊版中的部落格功能現已移除。 此範本以範本為基礎，僅允許作者在製作環境中建立內容。

## 將部落格元件添加到頁面{#adding-blog-components-to-a-page}

如果想要以作者模式將部落格新增至頁面，請使用元件瀏覽器來尋找

* `Communities / Blog`
* `Communities / Blog Sidebar`

並將它們拖曳到應該出現部落格的頁面上。

如需必要資訊，請造訪[Communities Components Basics](basics.md)。

當包含[必要的用戶端程式庫](blog-developer-basics.md#essentials-for-client-side)時，以下是`Blog`元件的顯示方式：

![chlimage_1-147](assets/chlimage_1-147.png)

以及`Blog Sidebar`將如何出現：

![chlimage_1-148](assets/chlimage_1-148.png)

### 配置部落格{#configuring-blog}

選取要存取的放置`Blog`元件，並選取開啟編輯對話方塊的`Configure`圖示。

![配置](assets/chlimage_1-149.png) ![iconBlog設定](assets/Blog-configure.png)

#### 設定頁簽{#settings-tab}

在&#x200B;**[!UICONTROL Settings]**&#x200B;標籤下，指定部落格的基本功能：

* **[!UICONTROL 允許附]**
件縮圖如果選中，則會建立附加影像的縮圖。

* **[!UICONTROL 最大附加縮]**
圖大小附件縮圖影像的最大大小（以像素為單位）。預設值為800 x 800。

* **[!UICONTROL 縮圖的最小影]**
像大小最小影像大小（以位元組為單位），用於產生內嵌影像的縮圖。預設值為100000位元組(100kb)。

* **[!UICONTROL 最大縮]**
圖大小內嵌影像縮圖影像的最大大小（以像素為單位）。預設值為800 x 800。

* **[!UICONTROL 允許特]**
權成員如果選中此選項，則僅允許特權成員建立內容。

* **[!UICONTROL 允許的特]**
權成員添加允許建立內容的特權成員。

* **[!UICONTROL 在作者編輯模式中封鎖使用者產生的]**
內容如果已啟用，則在作者模式中編輯時封鎖使用者產生的內容。

* **[!UICONTROL 日誌]**
標題要在頁上顯示的部落格標題。
   >注意:
   >日誌標題用於自動建立部落格的URL。 您在此處指定的日誌標題最多使用50個字元（唯一性附加5個字元），以建立部落格的URL。

* **[!UICONTROL 日誌]**
說明部落格說明。

* **[!UICONTROL 每頁主題]**

   定義每頁顯示的部落格項目/留言數。 預設為10。

* **[!UICONTROL 已審核]**

   如果選中此選項，則發佈部落格條目和評論必須獲得批准，才會出現在發佈站點上。 預設為未勾選。

* **[!UICONTROL 已關閉]**

   如果選中，則將關閉部落格，以查看新的部落格條目和評論。 預設為未勾選。

* **[!UICONTROL RTF 編輯器]**

   如果選中，則可以使用標籤輸入部落格條目和注釋。 已勾選預設值。

* **[!UICONTROL 允許標記]**

   如果選中此選項，則允許成員向其貼文中添加標籤標籤（請參閱&#x200B;**[!UICONTROL 標籤欄位]**&#x200B;標籤）。 預設為未勾選。

* **[!UICONTROL 允許檔案上傳]**

   如果選中此選項，則允許將檔案附件添加到部落格條目或注釋中。 預設為未勾選。

* **[!UICONTROL 最大檔案大小]**

   僅當檢查`Allow File Uploads`時相關。 此欄位將限制上傳檔案的大小（以位元組為單位）。 預設為104857600(10 Mb)。

* **[!UICONTROL 允許的檔案類型]**

   僅當檢查`Allow File Uploads`時相關。 副檔名清單（以逗號分隔）以「點」分隔。 例如：.jpg、.jpeg、.png、.doc、.docx、.pdf。 如果指定了任何檔案類型，則不允許上載未指定的檔案類型。 未指定預設值，因此允許所有檔案類型。

* **[!UICONTROL 附加影像檔案最大大小]**

   僅在勾選「允許檔案上傳」時相關。 上傳的影像檔案可能具有的最大位元組數。 預設為2097152(2 Mb)。

* **[!UICONTROL 允許回覆]**

   如果選中，則允許對發佈到部落格條目的評論進行回覆。 預設為未勾選。

* **[!UICONTROL 允許使用者刪除評論和主題]**

   如果選中，則允許成員刪除他們發佈的評論和部落格條目。 預設為未勾選。

* **[!UICONTROL 允許關注]**

   若勾選此選項，請為部落格文章加入下列功能，讓成員能[收到新貼文的通知](notifications.md)。 預設為未勾選。

* **[!UICONTROL 允許電子郵件訂閱]**

   若勾選此選項，允許透過電子郵件([subscription](subscriptions.md))通知成員新貼文。 需要檢查`Allow Following`，並配置[電子郵件](email.md)。 預設為未勾選。

* **[!UICONTROL 允許投票]**

   如果勾選此選項，請加入包含部落格項目的投票功能。 預設為未勾選。

* **[!UICONTROL 顯示徽章]**

   如果選中，則顯示已獲得的並已分配[徽章](implementing-scoring.md)，並包含成員的部落格條目。 預設為未勾選。

* **[!UICONTROL 允許主要內容]**

   若勾選，可將構想識別為[精選內容](featured.md)。 預設為未勾選。

#### 使用者協調標籤{#user-moderation-tab}

在&#x200B;**[!UICONTROL 使用者協調]**&#x200B;標籤下，指定協調設定：

* **[!UICONTROL 拒絕貼文]**

   若勾選此選項，信任的成員協調者將可拒絕貼文，並防止貼文出現在公開論壇上。 預設為未勾選。

* **[!UICONTROL 關閉/重新開啟主題]**

   如果選中，受信任的成員協調者可以關閉主題以進一步編輯和評論，也可以重新開啟主題。 預設為未勾選。

* **[!UICONTROL 標幟貼文]**

   如果選中，則允許成員將其他主題或評論標籤為不適當。 預設為未勾選。

* **[!UICONTROL 標誌原因清單]**

   如果選中，則允許成員從下拉清單中選擇其標籤主題或評論為不適當的原因。 預設為未勾選。

* **[!UICONTROL 自訂標幟原因]**

   如果選中，則允許成員輸入自己的原因，將主題或評論標籤為不適當。 預設為未勾選。

* **[!UICONTROL 協調臨界值]**

   輸入在通知協調者之前，成員必須標籤主題或評論的次數。 預設為1（一次）。

* **[!UICONTROL 標幟限制]**

   輸入主題或留言在從公共視圖中隱藏之前必須標籤的次數。 如果設為–1，則標籤的主題或評論永遠不會在公共視圖中隱藏。 否則，此數字必須大於或等於協調臨界值。 預設為5。

#### 標籤欄位標籤{#tag-field-tab}

在&#x200B;**[!UICONTROL 標籤欄位]**&#x200B;標籤下，指定如果在&#x200B;**[!UICONTROL 設定]**&#x200B;標籤上勾選&#x200B;**[!UICONTROL 允許標籤]**，可套用哪些標籤：

* **[!UICONTROL 允許的命名空間]**

   若已在&#x200B;**[!UICONTROL Settings]**&#x200B;標籤下勾選`Allow Tagging`則相關。 可套用的標籤僅限於所檢查命名空間類別中的標籤。 命名空間清單包含「標準標籤」（預設命名空間）以及「包含所有標籤」。 預設值未勾選，這表示允許所有命名空間。

* **[!UICONTROL 建議限制]**

   輸入要作為建議顯示給論壇成員的標籤數。 值–1表示沒有限制。 預設為0。

### 配置部落格側欄{#configuring-blog-sidebar}

按兩下`Blog Sidebar`元件時，將開啟編輯對話框。

在&#x200B;**[!UICONTROL 日誌側欄設定]**&#x200B;標籤下，指定存檔的日期格式以及要在側欄中顯示的條目類型：

![chlimage_1-151](assets/chlimage_1-151.png)

* **[!UICONTROL 日期格式]**

   用於為部落格條目的存檔顯示的格式。 格式使用遵循Java慣例的預留位置。

   * yyyy:全年，就像』2015年
   * yy:短年，比如』15年
   * MMMMMM:整個月，像6月
   * 嗯：像6月一樣
   * MM:月數，如06

   預設值為&quot;yyyy MMMM&quot;，會顯示例如&quot;2015年6月&quot;

* **[!UICONTROL 視圖類型]**

   要在側欄中顯示的部落格項目的標題和類型。 選擇是

   * 作者
   * 類別
   * 封存

* **[!UICONTROL 日誌元件路徑]**

   *（可選）* 要列出部落格文章的部落格資源位置。若保留為空白，則會使用顯示在相同頁面上的resourceType `social/journal/components/hbs/journal`元件。

   * 例如， `/content/sites/engage/en/blog/jcr:content/content/primary/blog`

* **[!UICONTROL 建議限制]**

   要顯示的部落格文章數。 值–1表示無限制。 預設為–1。

## 網站訪客體驗{#site-visitor-experience}

在發佈環境中，部落格功能會依照建立的順序，顯示最新的部落格文章，之後會顯示較舊的部落格文章。 部落格側邊欄可讓網站訪客套用篩選器，以限制所顯示部落格文章的選取。

部落格文章後面會有貼文或檢視留言的連結。

選取部落格文章時，會顯示部落格文章和評論（如果已啟用）。

其他功能取決於網站訪客是版主、管理員、社群成員、有權限的成員還是匿名。

### 使用文章{#working-with-articles}

建立新部落格文章時，您可以選擇

1. 立即發佈
1. 發佈草稿
1. 在排程日期和時間發佈

部落格文章會顯示在適當的標籤下（已發佈、草稿或已排程），供能夠在發佈時撰寫的成員使用。

#### 協調者和管理員{#moderators-and-administrators}

當登入的使用者擁有版主或管理員權限時，他們可以對發佈至部落格的所有部落格文章和留言執行[仲裁任務](moderate-ugc.md)（元件的設定允許）。

![chlimage_1-152](assets/chlimage_1-152.png)

### 成員 {#members}

當登入的使用者是社群成員或[特權成員](users.md#privileged-members-group)時（視設定而定），他們可以選取`New Article`來建立和張貼新的部落格文章。

具體而言，他們可以：

* 建立新部落格文章
* 代表其他成員發佈新的部落格文章
* 發佈評論到部落格文章
* 編輯自己的部落格文章或評論
* 刪除自己的部落格文章或評論
* 為他人的部落格文章或評論加上標籤

![chlimage_1-153](assets/chlimage_1-153.png) ![chlimage_1-154](assets/chlimage_1-154.png)

### 匿名 {#anonymous}

未登錄的網站訪客只能閱讀已發佈的部落格文章和評論，如有支援，可以翻譯，但不得添加部落格文章或評論，也不得標籤他人的文章或評論。

![chlimage_1-155](assets/chlimage_1-155.png)

## 其他資訊 {#additional-information}

如需詳細資訊，請參閱開發人員的[部落格要點](blog-developer-basics.md)頁面。

有關部落格條目和留言的調節，請參閱[調節用戶生成的內容](moderate-ugc.md)。

有關標籤部落格條目和注釋的資訊，請參閱[標籤用戶生成的內容](tag-ugc.md)。

有關部落格條目和注釋的翻譯，請參閱[ Transling User Generated Content](translate-ugc.md)。

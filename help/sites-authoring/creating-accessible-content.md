---
title: 建立可存取的內容 (符合 WCAG 2.0)
seo-title: Creating Accessible Content (WCAG 2.0 Conformance)
description: 協助殘疾人存取及使用網路內容
seo-description: Help make web content accessible to, and usable by, persons with disabilities
uuid: 416be3a1-6f02-4911-a69e-cae1825ee022
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 3d4258de-c0bb-4952-b6f0-0c5f2a15e531
exl-id: f792a65d-35f5-4143-bec2-c64de3f567b4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '8959'
ht-degree: 8%

---

# 建立可存取的內容 (符合 WCAG 2.0){#creating-accessible-content-wcag-conformance}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

WCAG 2.0 包含一系列無需仰賴技術的指引和成功標準，有助身心障礙人士存取與使用網路內容。

>[!NOTE]
>
>另請參閱:
>
>* 我們的 [WCAG 2.0快速指南](/help/managing/qg-wcag.md) 詳細資訊
>* [設定RTF編輯器以產生無障礙內容](/help/sites-administering/rte-accessible-content.md)
>


這些分級會根據三個合規級別進行：A級（最低）、AA級和AAA級（最高）。 簡要地說，這些級別的定義如下：

* **** A級：您的網站達到基本的最低協助功能等級。要達到此級別，將滿足所有A級成功標準。
* **** AA級：這是您努力追求的最佳無障礙環境支援等級，其中您的網站可達到更高的無障礙環境支援等級，因此大部分使用者都可使用大部分的技術。要達到此級別，將滿足所有A級和A級成功標準。
* **** AAA級：您的網站可達到非常高的協助功能。要達到此級別，將滿足所有A級、AA級和AAA級成功標準。

建立網站時，您必須決定要讓網站遵循的整體等級。

以下章節介紹 [WCAG 2.0指引](https://www.w3.org/TR/WCAG20/#guidelines) 與A級和AA級的相關成功標準 [合格級別](https://www.w3.org/TR/UNDERSTANDING-WCAG20/conformance.html).

>[!NOTE]
>
>由於無法滿足某些類型內容的所有AAA級成功標準，因此不建議將此級別符合作為一般策略所必需。

>[!NOTE]
>
>在本檔案中，我們使用：
>
>* 短名 [WCAG 2.0指引](https://www.w3.org/TR/WCAG20/#guidelines).
>* 在 [WCAG 2.0指引](https://www.w3.org/TR/WCAG20/#guidelines) 以輔助與WCAG網站的交叉參照。
>


## 原則1:可感知 {#principle-perceivable}

[原則1:可感知(Perceivable) — 資訊和用戶介面元件必須以用戶能夠感知的方式顯示給用戶。](https://www.w3.org/TR/WCAG20/#perceivable)

### 替代文字(1.1) {#text-alternatives}

[准則1.1文本替代：為任何非文字內容提供替代文字的內容，以便將其變更為人們需要的其他形式，例如大型印刷品、盲文、語音、符號或更簡單的語言。](https://www.w3.org/TR/WCAG20/#text-equiv)

### 非文字內容(1.1.1) {#non-text-content}

* 成功標準1.1.1
* A級
* 非文字內容：呈現給使用者的所有非文字內容都有可達到同等目的的替代文字，但下列情形除外。

#### 用途 — 非文字內容(1.1.1) {#purpose-non-text-content}

網頁上的資訊可以以許多不同的非文本格式提供，如圖片、視頻、動畫、圖表和圖形。 盲人或視力嚴重受損的人無法看到非文本內容，但他們可以通過螢幕閱讀器讀取文本內容或通過盲文顯示設備以觸覺形式顯示文本內容來訪問文本內容。 因此，通過以圖形格式提供內容的文本替代項，看不到圖形內容的人可以訪問內容提供的資訊的同等版本。

另一個有用的好處是，文本替代項使得非文本內容能夠根據搜索引擎技術編製索引。

#### 如何達成 — 非文字內容(1.1.1) {#how-to-meet-non-text-content}

對於靜態圖形，基本要求是為圖形提供等效文本替代。 您可以在 **替代文字** 欄位：

>[!NOTE]
>
>有些現成可用的元件(例如 **Carousel** 和 **Slideshow** )不提供將替代文字說明新增至影像的方式。當針對您的AEM例項實作這些版本時，您的開發團隊將需要設定這些元件以支援 `alt` 屬性，讓作者可將其新增至內容(請參閱 [新增對其他HTML元素和屬性的支援](/help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes))。

此 **替代文字** 欄位在 **影像** 元件對話方塊中 **中繼資料** 標籤：

![在觸控最佳化UI中編輯影像元件的對話方塊；顯示「替代文字」欄位。](assets/screen_shot_2018-03-21at165045.png)

AEM需要 **替代文字** 欄位以預設填入。 如果影像是純裝飾性的，而替代性文字是無意義的，則 **影像是裝飾** 選項。

#### 建立良好的文字替代項目 {#creating-good-text-alternatives}

非文字內容有多種形式，因此替代文字的值取決於圖形在網頁中扮演的角色。 以下是一些一般經驗法則：

* 替代案文應簡明扼要，但應清楚掌握非文本內容提供的基本資訊。
* 應避免過長的說明（超過100個字元）。 如果替代文字需要更詳細的資訊：

   * 在替代文字中提供簡短說明
   * 和在相同頁面或個別網頁其他地方的文字中有較長的說明。 將影像設為連結，或將文字連結放置在影像旁，以連結至此個別說明。

* 替代文字不應複製相同頁面附近文字表單中提供的內容。 請記住，許多影像都是頁面文字中已涵蓋點的圖解，因此可能已存在詳細的文字替代項目。
* 如果非文本內容是指向其他頁面或文檔的連結，並且沒有其他文本構成同一連結的一部分，則影像的替代文本必須指示連結的目的地，而不是描述影像。
* 如果非文字內容包含在按鈕元素中，並且沒有構成相同按鈕一部分的文字，則影像的替代文字必須指示按鈕的功能，而不是描述影像。
* 為影像指定空白(null)替代文字是完全可接受的，但前提是影像沒有替代文字（例如，純粹是裝飾圖形），或頁面文字中已存在相等文字。

此 [W3C草稿：HTML5提供有用文本替代項的技術](https://dev.w3.org/html5/alt-techniques/) 有針對不同類型影像提供適當替代文字的更多詳細資料和範例。

需要替代文字的特定非文字內容類型可能包括：

* 說明性照片：這些是人、物體或地方的影像。 想想照片在頁面上的作用；適當的文字對應項目可能 *[對象]的照片*，但可能取決於周圍的文字。
* 表徵圖：這些是傳送特定資訊的小型像形圖（圖形）。 必須在頁面和網站間一致地使用。 頁面或網站上的圖示所有例項都應有相同的簡短文字替代項目，除非這麼做會造成相鄰文字的不必要重複。
* 圖表和圖形：這些通常代表數值資料。 因此，提供文本替代的一個選項可能是包含圖表或圖形中顯示的主要趨勢的簡要摘要。 如有必要，也可使用 **說明** 欄位 **進階** 「影像屬性」頁簽。 此外，您可以在頁面或網站其他地方以表格形式提供來源資料。

   ![圖表範例。 以下是提供替代方案的最佳方法。](assets/chlimage_1.jpeg)

   若要提供此範例圖表的替代方案，請新增簡明 `alt` 將文字加到影像本身，然後以全文替代方式跟隨影像。

   ```xml
   <p><img src="figure1.gif" alt="Figure 1" ></p>
   <p> Figure 1. Distribution of Articles by Journal Category.
   Pie chart: Language=68%, Education=14% and Science=18%.</p>
   ```

   >[!NOTE]
   >
   >上述程式碼片段僅用於說明順序。 建議使用 **影像** 元件(而非 `img src` 上述使用的參考。

   在AEM中，您可以使用 **替代文字** 和 **說明** 影像設定對話方塊中的欄位 — 如 [如何達成 — 非文字內容(1.1.1)](#how-to-meet-non-text-content).

* 地圖、圖表、流程圖：用於提供空間資料的圖形(例如。若要支援描述物件或程式之間的關係)，請確定關鍵訊息是以文字格式提供。對於地圖，提供等同全文的地圖可能不切實際，但如果提供地圖以幫助人們找到特定位置的方式，則地圖影像的替代文字可以簡短地標示 *X*，然後在頁面其他地方的文字或透過 **Image元件的「** Advanced **」 (進階) 索引標籤中的「** Description **** 」 (說明) 欄位，提供指向該位置的指示。
* 驗證碼：驗證碼是 *完全自動化的公共圖靈測試*. 這是一種用於網頁上的安全檢查，用於區分人類和惡意軟體，但可能造成無障礙障礙。 這些影像需要使用者描述他們看到的內容，才能通過安全性測試。 顯然無法為影像提供替代文字，因此您需要考慮替代的非圖形解決方案。

   W3C提供了一些建議，例如：每種方法都有各自的優點和缺點。

   * 邏輯拼圖
   * 使用聲音輸出而非影像
   * 有限使用帳戶和垃圾郵件篩選器。

* 背景影像：這些是使用階層式樣式表(CSS)而非HTML來達成。 這表示無法指定替代文字值。 因此，背景影像不應提供重要的文字資訊 — 如果提供了，這些資訊也必須在頁面的文字中提供。

   但是，當無法顯示影像時，必須顯示替代背景。

   >[!NOTE]
   >
   >背景文字與前景文字之間應有適當的對比度；詳細討論 [對比度（最低）(1.4.3)](#contrast-minimum).

#### 詳細資訊 — 非文字內容(1.1.1) {#more-information-non-text-content}

* [了解成功標準1.1.1](https://www.w3.org/TR/UNDERSTANDING-WCAG20/text-equiv-all.html)
* [如何符合成功標準1.1.1](https://www.w3.org/WAI/WCAG20/quickref/#text-equiv)
* [W3C:HTML5提供有用文本替代項的技術（草稿）](https://dev.w3.org/html5/alt-techniques/)
* [驗證碼的W3C說明和替代方案](https://www.w3.org/TR/turingtest/)

### 時間型媒體(1.2) {#time-based-media}

[准則1.2以時間為基礎的媒體：提供以時間為基礎的媒體的替代方案。](https://www.w3.org/TR/WCAG20/#text-equiv)

這涉及 *時間型*. 這涵蓋使用者可播放的內容（例如視訊、音訊和動畫內容），且可以預先錄制或即時資料流。

### 僅限音訊和僅限視訊（預錄）(1.2.1) {#audio-only-and-video-only-pre-recorded}

* 成功標準1.2.1
* A級
* 僅限音訊和僅限視訊（預錄）:對於預錄的純音頻和預錄的純視頻媒體，以下是真的，但音頻或視頻是文本的替代媒體且明確標籤為這樣的媒體除外：

   * 僅預錄音頻：提供了用於基於時間的媒體的替代，該替代提供用於預錄的僅音頻內容的等效資訊。
   * 僅預錄視頻：提供了用於基於時間的媒體的替代媒體或音頻軌道，該音頻軌道為預錄的僅視頻內容呈現等同資訊。

#### 用途 — 僅限音訊和僅限視訊（預錄）(1.2.1) {#purpose-audio-only-and-video-only-pre-recorded}

視訊和音訊的協助工具問題可能會發生：

* 沒有音軌或音軌時，視覺受損的人無法告知影片或動畫中發生的情況；
* 聽力受損或失聰的人，聽不到音軌；
* 那些能聽到背景音樂，但不理解人們說什麼的人（例如，因為他們所說的語言是他們不懂的）。

使用不支援以特定媒體格式播放內容(例如AdobeFlash)的瀏覽器或裝置的使用者，也可能無法使用視訊或音訊。

以不同格式提供此資訊，例如文字（或無音訊的視訊音訊），可讓無法存取原始內容的使用者存取。

#### 如何達成 — 僅限音訊和僅限視訊（預錄）(1.2.1) {#how-to-meet-audio-only-and-video-only-pre-recorded}

* 如果內容預先錄制的音訊沒有視訊（例如播客）:

   * 在內容之前或之後立即提供連結至音訊內容的文字記錄。

      文字記錄應是HTML頁面，其文字等同於所有口語和非口語重要內容，還應包含說話者的指示、設定的描述、聲音表達以及任何其他重要音頻的描述。

* 如果內容是動畫或預錄的無音頻視頻：

   * 在內容之前或之後，提供連結給視訊所提供資訊的同等文字說明
   * 或MP3等常用音訊格式的等效音訊說明。

>[!NOTE]
>
>如果提供音訊或視訊內容作為網頁上已存在其他格式內容的替代內容，則無需遵循上述要求。 例如，如果影片說明文字指示清單，則此影片不需要替代項目，因為文字指示已作為影片的替代項目。

在AEM網頁中插入多媒體(尤其是Flash內容)與插入影像類似。 然而，由於多媒體內容遠不止是靜止的影像，所以在控制多媒體的播放方式方面存在多種不同的設定和選項。

>[!NOTE]
>
>當您將多媒體與資訊內容搭配使用時，您還必須建立替代內容的連結。 例如，要包括文本記錄，請建立一個HTML頁以顯示該記錄，然後在音頻內容旁或下面添加一個連結。

#### 詳細資訊 — 僅限音訊和僅限視訊（預錄）(1.2.1) {#more-information-audio-only-and-video-only-pre-recorded}

* [了解成功標準1.2.1](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-av-only-alt.html)
* [如何符合成功標準1.2.1](https://www.w3.org/WAI/WCAG20/quickref/#media-equiv)

### 字幕（預錄）(1.2.2) {#captions-pre-recorded}

* 成功標準1.2.2
* A級
* 字幕（預錄）:為同步媒體中所有預錄音頻內容提供字幕，除非該媒體是文本的媒體替代品，並且清楚地標籤為這樣。

#### 用途 — 字幕（預錄）(1.2.2) {#purpose-captions-pre-recorded}

失聰或聽力障礙的人無法或很難取得音訊內容。 字幕是口語和非口語音頻的等效文本，在視頻中的適當時間顯示在螢幕上。 它們讓聽不到音訊的人了解正在發生的情況。

>[!NOTE]
>
>如果在視頻或動畫的同一頁上提供適當的文本或非文本等效項（提供直接等效的資訊），則不需要字幕。

#### 如何符合 — 字幕（預錄）(1.2.2) {#how-to-meet-captions-pre-recorded}

字幕可以是：

* 開啟：播放視訊時一律顯示)
* 已關閉：字幕可由用戶開啟或關閉

盡可能使用隱藏式字幕，因為這可讓使用者選擇是否檢視字幕。

對於隱藏式字幕，您需要以適當的格式建立並提供同步的字幕檔案(例如 [SMIL](https://www.w3.org/AudioVideo/))和影片檔案(有關如何執行此作業的詳細資訊，不在本指南的討論範圍內，但我們已提供下列教學課程的連結 [更多資訊 — 字幕（預錄）(1.2.2)](#more-information-captions-pre-recorded))。 請務必提供附註，讓使用者知道字幕可供視訊使用。

如果必須使用開啟字幕，請將文本嵌入視頻軌道。 這可以使用允許將標題覆蓋到視頻上的視頻編輯應用程式來實現。

#### 更多資訊 — 字幕（預錄）(1.2.2) {#more-information-captions-pre-recorded}

* [了解成功標準1.2.2](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-captions.html):
* [如何符合成功標準1.2.2](https://www.w3.org/WAI/WCAG20/quickref/#media-equiv)
* [W3C:同步多媒體](https://www.w3.org/AudioVideo/)
* [字幕、筆錄和音頻描述 — 由WebAIM提供](https://webaim.org/techniques/captions/)

### 音訊說明或替代媒體（預錄）(1.2.3) {#audio-description-or-media-alternative-pre-recorded}

* 成功標準1.2.3
* A級
* 音訊說明或替代媒體（預錄）:為同步媒體提供基於時間的媒體或音頻描述的預錄視頻內容的替代物，除非該媒體是文本的媒體替代物並且清楚地標籤為這樣。

#### 用途 — 音訊說明或替代媒體（預錄）(1.2.3) {#purpose-audio-description-or-media-alternative-pre-recorded}

如果僅以視覺方式提供視頻或動畫中的資訊，或如果音軌未提供足夠的資訊，以便了解視覺上正在發生的情況，盲人或視力障礙者將會遇到無障礙障礙。

#### 如何達成 — 音訊說明或替代媒體（預錄）(1.2.3) {#how-to-meet-audio-description-or-media-alternative-pre-recorded}

有兩種方法可滿足此成功標準。 兩者皆可接受：

1. 包含視訊內容的其他音訊說明。 這可以通過以下三種方式之一實現：

   * 在現有對話方塊中暫停期間，提供場景中未作為現有音頻軌道一部分顯示的更改的相關資訊；
   * 提供新的、附加的和可選的音軌，其中包含原始音軌，但也包含有關場景更改的額外音頻資訊。

      * 這可讓使用者在現有的音訊軌道( *不* 包含音訊說明)和新的音訊軌道( *does* 包含音訊說明)。
      * 這可防止不需要額外說明的使用者中斷。
   * 建立視訊內容的第二版，以允許擴充音訊說明。 這可借由在適當點暫停音訊和視訊，減少在現有對話方塊之間的間隙內提供詳細音訊說明的相關困難。 因此，在動作再次開始之前，可以提供更長的音訊說明。 如上一個範例，最好以選用的額外音訊追蹤提供，以免中斷不需要其他說明的使用者。


1. 提供與視頻或動畫的音頻和視覺元素相當的適當文本文本記錄。 這應當包括，在適當情況下，說明誰在說話，說明設定，聲音表達。 視其長度而定，可以將記錄放在與視頻或動畫相同的頁面上，或放在單獨的頁面上；如果選擇後一個選項，請提供視頻或動畫旁邊的轉錄的連結。

有關如何建立音訊描述視訊的確切詳細資訊，不在本指南的討論範圍內。 建立視訊和音訊說明可能很耗時，但其他Adobe產品可協助您完成這些工作。 如果您在Adobe Flash Professional中建立內容，您也應建立指令碼，提示使用者下載適當的外掛程式，並透過 `<noscript>` 元素。

#### 詳細資訊 — 音訊說明或替代媒體（預錄）(1.2.3) {#more-information-audio-description-or-media-alternative-pre-recorded}

* [了解成功標準1.2.3](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-audio-desc.html):
* [如何符合成功標準1.2.3](https://www.w3.org/WAI/WCAG20/quickref/#qr-media-equiv-audio-desc)
* [Adobe Encore CS5](https://www.adobe.com/products/premiere/encore/)

### 字幕（正常）(1.2.4)  {#captions-live}

* 成功標準1.2.4
* AA級
* 字幕（即時）:為同步媒體中的所有即時音頻內容提供字幕。

#### 用途 — 字幕（正式啟用）(1.2.4) {#purpose-captions-live}

此成功標準與 [字幕（預錄）](#captions-pre-recorded) 它解決了聾人或聽力障礙者所遇到的無障礙障礙障礙，但此成功標準涉及即時演示，如網播。

#### 如何符合 — 字幕（正式啟用）(1.2.4) {#how-to-meet-captions-live}

遵循 [字幕（預錄）](#captions-pre-recorded) 上。 但是，由於媒體的即時性，必須盡快建立字幕提供，以響應正在發生的情況。 因此，您應考慮使用即時字幕或語音轉文字工具。

本檔案不提供詳細說明，但下列資源提供實用資訊：

* [WebAIM:即時字幕](https://www.webaim.org/techniques/captions/realtime.php)
* [AccessIT（華盛頓大學）:字幕是否可以使用語音識別自動生成？](https://www.washington.edu/accessit/articles?1209)

#### 更多資訊 — 字幕（正式啟用）(1.2.4) {#more-information-captions-live}

* [了解成功標準1.2.4](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-real-time-captions.html)
* [如何符合成功標準1.2.4](https://www.w3.org/WAI/WCAG20/quickref/#qr-media-equiv-real-time-captions)

### 音訊說明（預錄）(1.2.5)  {#audio-description-pre-recorded}

* 成功標準1.2.5
* AA級
* 音頻描述（預錄）:提供同步媒體中所有預錄視頻內容的音頻描述。

#### 用途 — 音訊說明（預錄）(1.2.5) {#purpose-audio-description-pre-recorded}

此成功標準與 [音訊說明或替代媒體（預錄）](#audio-description-or-media-alternative-pre-recorded)，但作者必須提供更詳細的音訊說明才能符合AA級。

#### 如何達成 — 音訊說明（預錄）(1.2.5) {#how-to-meet-audio-description-pre-recorded}

遵循 [音訊說明或替代媒體（預錄）](#audio-description-or-media-alternative-pre-recorded).

#### 詳細資訊 — 音訊說明（預錄）(1.2.5) {#more-information-audio-description-pre-recorded}

* [了解成功標準1.2.5](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-audio-desc-only.html)
* [如何符合成功標準1.2.5](https://www.w3.org/WAI/WCAG20/quickref/#qr-media-equiv-audio-desc-only)

### 適應性(1.3) {#adaptable}

[准則1.3適應性：建立可以以不同方式呈現的內容（例如更簡單的版面），而不會遺失資訊或結構。](https://www.w3.org/TR/WCAG20/#content-structure-separation)

此指引涵蓋支援以下人員的必要需求：

* 可能無法存取作者在 *標準* 二維、多欄、彩色網頁佈局

* 可使用純音或替代的視覺顯示，例如大文字或高對比。

### 資訊和關係(1.3.1)  {#info-and-relationships}

* 成功標準1.3.1
* A級
* 資訊和關係：通過展示傳遞的資訊、結構和關係可以寫程式地確定或在文本中可用。

#### 用途 — 資訊和關係(1.3.1) {#purpose-info-and-relationships}

許多殘疾人使用的輔助技術都依賴結構資訊來有效顯示或輸出內容。 此結構資訊可以採用頁標題、表行和列標題及清單類型的形式。 例如，螢幕助讀程式可讓使用者從標題瀏覽至標題的頁面。 不過，當頁面內容看起來只是透過視覺樣式(而非基礎HTML)有結構時，輔助技術就無法使用結構資訊，限制了其支援更輕鬆瀏覽的能力。

此成功標準的存在，是為了確保這類結構資訊能透過HTML提供，讓瀏覽器和輔助技術能夠存取及運用資訊。

#### 如何達成 — 資訊和關係(1.3.1) {#how-to-meet-info-and-relationships}

AEM可讓您使用適當的HTML元素輕鬆建立網頁。 在RTE中開啟頁面內容（文字元件），然後使用 **Paraformat** （段落符號），以指定適當的結構元素（例如段落、標題等）。

下圖顯示已設定為段落文本樣式的文本。

![以來源編輯模式（傳統UI）顯示的段落元素範例。](assets/screen_shot_2018-03-21at165623.png)

您可以透過下列方式，確定您的網頁已獲得適當的結構：

* **使用標題：**

   只要您已啟用RTE的協助工具功能(請參閱 [AEM與協助工具](#AdobeExperienceManagerandAccessibility)), AEM提供3層頁面標題。 您可以使用這些項目來識別內容的區段和子區段。標題1是標題的最高級別，標題3是最低級別。系統管理員可以配置系統以允許使用更多標題級別。

   下圖示範不同標題類型的範例。

   ![下拉式選取器（傳統UI）中顯示的標題H1到H3。](assets/screen_shot_2018-03-21at165719.png)

* **強調的文本**:

   使用或元素來指示強調。 請勿使用標題來反白標示段落中的文字。

   * 突出顯示要強調的文本；
   * 按一下 **B** 表徵圖 &lt;strong>)或 **我** 表徵圖 &lt;em>) **屬性** 面板(確定已選取HTML)。

   >[!NOTE]
   >
   >標準AEM安裝中的RTE已設定為使用：
   >
   >* &lt;b> for &lt;strong>
   * &lt;i> for &lt;em>

   它們實際上相同，但和較好，因為它們是語義正確的html。 您的開發團隊可以將RTE設定為在開發專案例項時使用和（而非和）。

* **使用清單**:您可以使用HTML來指定三種不同的清單類型：

   * 此 `<ul>` 元素用於 *未排序* 清單（項目符號）清單。 個別清單項目的識別方式為 `<li>` 元素。

      在RTE中，使用 **項目符號清單** 表徵圖。

   * 此 `<ol>` 元素用於 *編號清單*. 個別清單項目的識別方式為 `<li>` 元素。

      在RTE中，使用 **編號清單** 表徵圖。
   如果要將現有內容更改為特定清單類型，請突出顯示相應的文本並選擇相應的清單類型。 如先前顯示如何輸入段落文字的範例所示，適當的清單元素會自動新增至您的HTML。

   在全螢幕模式中，會顯示個別 **的「項目符號清單** 」和「 **** 編號清單」圖示。當未處於全螢幕模式時，單一「清單」圖示後面會提供這兩個 **選項** 。

   ![](do-not-localize/screen_shot_2018-03-21at165756.png)

   >[!NOTE]
   `<dl>` 不受RTE支援。

* **使用表**:

   必須使用HTML表元素來標識資料表：

   * one `<table>` 元素
   * a `<tr>` 表格每一列的元素
   * a `<th>` 元素
   * a `<td>` 元素

   >[!NOTE]
   在傳統UI中，表格應使用 **表格** 元件。

   此外，可訪問的表還使用以下元素和屬性：

   * 此 `<caption>` 元素可用來提供表格的可見標題。 字幕預設會出現在表格的正中，但可使用CSS適當定位。 註解以寫程式方式與表格相關聯，因此它是提供內容介紹的有用方法。
   * 此 `<summary>` 元素可協助無視的使用者提供視力不佳的使用者看得到的概要，以更輕鬆地了解表格中顯示的資訊。 若使用複雜或非常規的表格配置，此屬性特別實用（此屬性不會顯示在瀏覽器中，而只會讀出至輔助技術）。
   * 此 `scope` 屬性 `<th>` 元素用於指示儲存格代表特定列或特定欄的標題。 類似的方法是在複雜表格中使用標題和id屬性，其中資料儲存格可與一或多個標題相關聯。

   >[!NOTE]
   預設情況下，這些元素和屬性不直接可用，但系統管理員可以在 **表屬性** 對話框(請參見 [新增對其他HTML元素和屬性的支援](/help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes))。

   新增 **表格** 您可以 **表屬性** 使用對話方塊。

   * 適當 **註解**.
   * 理想情況下，請移除「寬 **度」、「邊框高度」、「邊框高度」、「邊框高度**」、「單元格間距」、「單元格間距 **」、「單元格**************&#x200B;間距」的預設值。因為這些屬性可以在全局樣式表中設定。

   ![「表屬性」對話框。](assets/chlimage_1-205.png)

   然後，您就可以使用 **電池特性** 選擇單元格是資料還是標題單元格，如果標題單元格，則選擇它是與行或列還是兩者相關：

   ![調用屬性對話框；將列（通常是第一行）設定為標題列。](assets/chlimage_1-206.png)

* **複雜資料表：**

   在某些情況下，如果有具有兩個或多個標題級別的複雜表，則基本表屬性可能不足以提供所有必要的結構資訊。 對於這些類型的複雜表格，需要使用header和 **id屬性在標題及其相關儲存格之間建** 立直 **接** 關係。例如，在下表的標題和ID中，會對輔助技術使用者進行程式化關聯。

   >[!NOTE]
   id屬性在現成可用的安裝中無法使用。 可透過在RTE中設定HTML規則和序列化程式來啟用。

   >[!NOTE]
   在傳統UI中，表格應使用 **表格** 元件。

   ```xml
   <table>
      <tr>
        <th rowspan="2" id="h">Homework</th>
        <th colspan="3" id="e">Exams</th>
        <th colspan="3" id="p">Projects</th>
      </tr>
      <tr>
        <th id="e1" headers="e">1</th>
        <th id="e2" headers="e">2</th>
        <th id="ef" headers="e">Final</th>
        <th id="p1" headers="p">1</th>
        <th id="p2" headers="p">2</th>
        <th id="pf" headers="p">Final</th>
      </tr>
      <tr>
       <td headers="h">15%</td>
       <td headers="e e1">15%</td>
       <td headers="e e2">15%</td>
       <td headers="e ef">20%</td>
       <td headers="p p1">10%</td>
       <td headers="p p2">10%</td>
       <td headers="p pf">15%</td>
      </tr>
   </table>
   ```

   要在AEM中實現此目標，必須使用源編輯模式直接添加標籤。

   >[!NOTE]
   標準安裝中不立即提供此功能。 它需要RTE、HTML規則和序列化程式的配置。

#### 更多資訊 — 資訊和關係(1.3.1) {#more-information-info-and-relationships}

* [了解成功標準1.3.1](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation-programmatic.html)
* [如何符合成功標準1.3.1](https://www.w3.org/WAI/WCAG20/quickref/#qr-content-structure-separation-programmatic)

### 感官特性(1.3.3)  {#sensory-characteristics}

* 成功標準1.3.3
* A級
* 感官特徵：為了解和操作內容而提供的指令不僅依賴於部件的感官特性，如形狀、大小、視覺位置、方向或聲音。

#### 目的 — 感官特性(1.3.3) {#purpose-sensory-characteristics}

設計人員在展示資訊時，往往關注視覺設計特徵，如顏色、形狀、文本樣式或內容的絕對或相對位置。 這些設計技術在傳達資訊方面可能非常強大，但是盲人或視障者可能無法訪問需要視覺識別屬性（如位置、顏色或形狀）的資訊。

同樣，需要區分不同聲音（例如男性或女性口語內容）的資訊，如果沒有反映在音頻內容的任何替代文本中，則會對聽力受損的人造成無障礙障礙。

>[!NOTE]
有關顏色替代品的相關需求，請參閱 [顏色的使用](#use-of-color).

#### 如何滿足 — 感官特性(1.3.3) {#how-to-meet-sensory-characteristics}

請確定任何仰賴頁面內容視覺特性的資訊也會以替代格式顯示。

* 不要依賴視覺位置提供資訊。 例如，如果您想要將使用者引導至頁面右側的功能表，以存取詳細資訊，請勿參閱 *右邊的菜單*;請改為命名功能表（例如透過標題），並在文字中參照該名稱。
* 請勿以文字樣式（例如粗體或斜體文字）作為傳達資訊的唯一方式。

>[!NOTE]
如果明白描述性詞語在非視覺內容中有意義，則可接受使用。 例如，使用 *abos* 和 *low* 通常是可接受的值，因為它們分別暗示特定內容之前和之後的內容；當內容被朗讀時，這仍然有意義。

#### 更多資訊 — 感官特性(1.3.3) {#more-information-sensory-characteristics}

* [了解成功標準1.3.3](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation-understanding.html)
* [如何符合成功標準1.3.3](https://www.w3.org/WAI/WCAG20/quickref/#qr-content-structure-separation-understanding)

### 可區分(1.4) {#distinguishable}

[准則1.4可區分：讓使用者更輕鬆查看和聽取內容，包括將前景與背景分開。](https://www.w3.org/TR/WCAG20/#visual-audio-contrast)

### 顏色的使用(1.4.1)  {#use-of-color}

* 成功標準1.4.1
* A級
* 顏色的使用：顏色不是唯一用於傳遞資訊、指示動作、提示響應或區分視覺元素的視覺手段。

>[!NOTE]
此成功標準專門處理色彩感知。 其他形式的感知涵蓋於 [適應性(1.3)](#adaptable);包括對顏色的可寫程式訪問和其他可視演示編碼。

#### 用途 — 顏色的使用(1.4.1) {#purpose-use-of-color}

顏色是增強網頁審美吸引力的一種明顯有效的方法，也是資訊傳遞的有用手段。 然而，從失明到彩色視覺缺乏，都存在著一系列視覺缺陷，這意味著有些人無法區分某些顏色。 這使得顏色編碼成為提供資訊的不可靠方式。

例如，有紅綠色視覺缺陷的人將無法區分綠色的陰影和紅色的陰影。 他們可能會將這兩種顏色視為第三種顏色（例如棕色），在這種情況下，他們將無法區分紅色、綠色和棕色。

此外，使用純文字瀏覽器、單色顯示裝置或檢視頁面黑白打印輸出的使用者無法察覺顏色。

#### 如何達成 — 色彩的使用(1.4.1) {#how-to-meet-use-of-color}

無論使用何種顏色來傳達資訊，都要確保資訊可用，而無需查看顏色。

例如，請確定文字中也明確提供顏色提供的資訊。 下圖顯示顏色和文本如何指示效能的座位可用性：

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>效能</strong></p> </td> 
   <td><p><strong>可用性</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>星期二3月16日<sup>th</sup></p> </td> 
   <td><p>可用座位</p> </td> 
  </tr> 
  <tr> 
   <td><p>星期三3月17日</p> </td> 
   <td><p>可用座位</p> </td> 
  </tr> 
  <tr> 
   <td><p>星期四3月18日<sup>th</sup></p> </td> 
   <td><p>售完</p> </td> 
  </tr> 
 </tbody> 
</table>

如果使用顏色作為提供資訊的提示，則應提供其他視覺提示，如更改樣式（如粗體、斜體字）或字型。 這有助於視力不足或彩色視力不足的人識別資訊。 然而，這無法完全依賴，因為這對根本看不到頁面的人毫無幫助。

#### 更多資訊 — 顏色的使用(1.4.1) {#more-information-use-of-color}

* [了解成功標準1.4.1](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/working-examples/G183/link-contrast.html)
* [如何符合成功標準1.4.1](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/working-examples/G183/link-contrast.html)
* [符合3:1對比率的指引，包含「網路安全」顏色清單](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/working-examples/G183/link-contrast.html)

### 對比度（最低）(1.4.3) {#contrast-minimum}

* 成功標準1.4.3
* AA級
* 對比度（最小值）:文本和影像的視覺呈現具有至少4.5:1的對比度，但以下除外：

   * 大文本：大型文本和影像的對比度至少為3:1。
   * 附帶：屬於非活動用戶介面元件的文本或影像，屬於純裝飾、任何人都看不到，或屬於包含顯著的其他視覺內容的圖片的一部分，沒有對比要求。
   * Logotype:屬於標誌或品牌名稱的文字沒有最低的對比要求。

#### 用途 — 對比（最低）(1.4.3) {#purpose-contrast-minimum}

某些視覺障礙的人可能無法區分某些低對比度顏色對。 如果以下情況之一，這些人可能會遇到無障礙問題：

* 文字與背景顏色對比較差。
* 文本（如連結文本和非連結文本）的顏色編碼在識別資訊方面具有重要意義。

>[!NOTE]
純粹用於裝飾目的的文字會排除在此成功標準之外。

#### 如何達成 — 對比（最低）(1.4.3) {#how-to-meet-contrast-minimum}

請確定文字與背景對比充分。 對比度取決於相關文本的大小和樣式：

* 對於大小小於18點（或14點粗體）的文本，文本/影像與背景的對比度應至少為4.5:1。
* 對於大小至少為18點（或14點粗體）的文本，對比度應至少為3:1。
* 如果已構圖背景，則應對所有文本週圍的背景進行著色，以保持4.5:1或3:1的比例。

若要檢查對比度，請使用顏色對比工具，例如 [Paciello Group Color Contrast Analyser](https://www.paciellogroup.com/resources/contrast-analyser.html) 或 [WebAIM顏色對比檢查程式](https://www.webaim.org/resources/contrastchecker/). 這些工具可讓您檢查色彩配對，並報告任何對比問題。

或者，如果您不太在意指定頁面的外觀，可以選擇不指定背景和前景文字顏色。 不需要對比度檢查，因為用戶的瀏覽器將確定文本和背景的顏色。

如果無法達到建議的對比層級，您需要提供頁面替代版本的連結（沒有顏色對比問題），或讓使用者根據自己的需求調整頁面色彩配置的對比。

#### 更多資訊 — 對比（最低）(1.4.3) {#more-information-contrast-minimum}

* [了解成功標準1.4.3](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-contrast.html)
* [如何符合成功標準1.4.3](https://www.w3.org/WAI/WCAG20/quickref/#qr-visual-audio-contrast-contrast)

### 文字影像(1.4.5) {#images-of-text}

* 成功標準1.4.5
* AA級
* 文字影像：如果所使用的技術能夠實現視覺呈現，則使用文本來傳達資訊，而不是文本的影像，但以下除外：

   * 可自訂：文本的影像可以根據用戶的需求進行可視化定製；
   * 基本：對所傳送的資訊而言，特定的文本表述是必不可少的。

>[!NOTE]
Logotype（屬於標誌或品牌名稱的文字）被視為必要項目。

#### 用途 — 文字影像(1.4.5) {#purpose-images-of-text}

當偏好特定文字樣式時，通常會使用文字影像；例如，logotype或如果文本是從其他源（例如掃描紙文檔）生成的。 然而，與以HTML呈現和使用CSS設定樣式的文字相比，文字的影像缺乏變更大小或外觀的彈性，這對於視覺障礙或閱讀困難的人來說可能是必要的。

#### 如何相遇 — 文字影像(1.4.5) {#how-to-meet-images-of-text}

如果必須使用文字影像，請使用CSS將文字影像取代為HTML中的等同文字，讓文字以可自訂的方式提供。 如需如何達成此目標的範例，請參閱 [C30:使用CSS將文本替換為文本的影像，並提供用戶介面控制項以切換](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/C30).

#### 詳細資訊 — 文字影像(1.4.5) {#more-information-images-of-text}

* [了解成功標準1.4.5](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-text-presentation.html)
* [如何符合成功標準1.4.5](https://www.w3.org/WAI/WCAG20/quickref/#qr-visual-audio-contrast-text-presentation)

## 原則2:可操作 {#principle-operable}

[原則2:可操作 — 用戶介面元件和導航必須可操作。](https://www.w3.org/TR/WCAG20/#operable)

### 暫停、停止、隱藏(2.2.2)  {#pause-stop-hide}

* 成功標準2.2.2
* A級
* 暫停、停止、隱藏：對於移動、閃爍、滾動或自動更新資訊，以下是true:

   * 移動、閃爍、滾動：對於(a)自動啟動、(b)持續超過五秒、(c)與其他內容並行顯示的任何移動、閃爍或滾動資訊，有一種機制供用戶暫停、停止或隱藏，除非移動、閃爍或滾動是活動必不可少的一部分；
   * 自動更新：對於(a)自動啟動和(b)與其他內容並行顯示的任何自動更新資訊，有一種機制可讓使用者暫停、停止或隱藏更新，或控制更新的頻率，除非自動更新是活動的一部分，而其至關重要。

備注點有：

1. 有關閃爍或閃爍內容的要求，請參閱 [請勿以已知會導致癲癇發作的方式設計內容(2.3)](#seizures).
1. 由於任何不符合此成功標準的內容都可能干擾使用者使用整個頁面的能力，因此網頁上的所有內容（無論是否用於符合其他成功標準）都必須符合此成功標準。 請參閱 [合規要求5:無干擾](https://www.w3.org/TR/WCAG20/#cc5).
1. 由軟體定期更新或流向用戶代理的內容不需要保留或呈現在暫停啟動和恢復呈現之間產生或接收的資訊，因為這在技術上可能不可能，並且在許多情況下可能誤導用戶。
1. 如果在預載入階段或類似情況中不能對所有用戶進行交互，並且如果不指示進度，則可能會混淆用戶或導致他們認為內容已凍結或損壞，則可以認為動畫是必不可少的。

#### 用途 — 暫停、停止、隱藏(2.2.2) {#purpose-pause-stop-hide}

某些使用者可能會發現移動的內容會分散注意力，而且難以集中在頁面的其他部分。 此外，對於無法跟上移動文字的人，這類內容可能很難閱讀。

#### 如何相遇 — 暫停、停止、隱藏(2.2.2) {#how-to-meet-pause-stop-hide}

根據內容的性質，在建立包含移動、閃爍或閃爍內容的網頁時，可以應用以下一個或多個建議：

* 提供暫停捲動內容的方法，讓使用者有足夠的時間閱讀內容。 例如，新聞提示或自動更新的文字。
* 請確定連結的內容在5秒後停止閃爍。
* 使用適當技術來顯示可由瀏覽器停用的閃爍內容。 例如，圖形交換格式(GIF)或動畫可移植網路圖形(APNG)檔案。
* 在網頁上提供表單控制項，以允許使用者停用頁面上所有閃爍的內容。
* 如果無法執行上述任何操作，請提供包含所有內容的頁面連結，但不要閃爍。

#### 詳細資訊 — 暫停、停止、隱藏(2.2.2) {#more-information-pause-stop-hide}

* [了解成功標準2.2.2](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-pause.html)
* [如何符合成功標準2.2.2](https://www.w3.org/WAI/WCAG20/quickref/#qr-time-limits-pause)

### 緝獲量(2.3) {#seizures}

[准則2.3緝獲量：請勿以已知會導致癲癇的方式設計內容。](https://www.w3.org/TR/WCAG20/#seizure)

### 三個Flash或低於臨界值(2.3.1) {#three-flashes-or-below-threshold}

* 成功標準2.3.1
* A級
* 三個Flash或低於臨界值：網頁不包含任何在任何一秒內閃爍超過三次，或閃爍低於一般閃爍閾值和紅色閃爍閾值。

>[!NOTE]
由於任何不符合此成功標準的內容都可能干擾使用者使用整個頁面的能力，因此網頁上的所有內容（無論是否用於符合其他成功標準）都必須符合此成功標準。 請參閱 [合規要求5:無干擾](https://www.w3.org/TR/WCAG20/#cc5).

#### 用途 — 三個Flash或低於臨界值(2.3.1) {#purpose-three-flashes-or-below-threshold}

在某些情況下，閃爍的內容可能導致感光性癲癇。 此成功標準可讓這類使用者存取和體驗所有內容，而不必擔心內容閃爍的問題。

#### 如何達成 — 三個Flash或低於臨界值(2.3.1) {#how-to-meet-three-flashes-or-below-threshold}

您應採取步驟，確認已套用下列技術：

* 在任何一秒的時間內，元件不會閃爍超過三次；
* 如果無法符合上述條件，則在 *小安全區* 畫面上的像素。 此區域是使用複雜公式計算，涵蓋於 [G176:保持閃光區足夠小](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/G176)，因此只有在閃爍內容時才應遵循此技術 *絕對* 必要。

#### 詳細資訊 — 三個Flash或低於臨界值(2.3.1) {#more-information-three-flashes-or-below-threshold}

* [了解成功標準2.3.1](https://www.w3.org/TR/UNDERSTANDING-WCAG20/seizure-does-not-violate.html)
* [如何符合成功標準2.3.1](https://www.w3.org/WAI/WCAG20/quickref/#seizure)

### 標題為(2.4.2)的頁面  {#page-titled}

* 成功標準2.4.2
* A級
* 標題為：網頁的標題可描述主題或用途。

#### 用途 — 標題為(2.4.2)的頁面 {#purpose-page-titled}

此成功標準可協助所有人（不論是否有任何特定障礙）快速識別網頁內容，而無須完整閱讀頁面。 若在瀏覽器標籤中開啟數個網頁，這特別實用，因為頁面標題會顯示在標籤中，因此可快速找到。

#### 如何相遇 — 標題為(2.4.2)的頁面 {#how-to-meet-page-titled}

在AEM中建立新HTML頁面時，您可以指定頁面標題。 請確定標題足以說明頁面的內容，讓訪客能夠快速識別內容是否實際與其需求相關。

編輯頁面時，您也可以編輯頁面標題，頁面資訊——屬 **性可****存取。**

#### 更多資訊 — 標題為(2.4.2)的頁面 {#more-information-page-titled}

* [了解成功標準2.4.2](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-title.html)
* [如何符合成功標準2.4.2](https://www.w3.org/WAI/WCAG20/quickref/#qr-navigation-mechanisms-title)

### 連結用途（內容中）(2.4.4)  {#link-purpose-in-context}

* 成功標準2.4.4
* A級
* 連結用途（在內容中）:每個連結的用途可以單獨從連結文本中確定，或者從連結文本連同其以程式設計方式確定的連結上下文一起確定，除非在通常情況下連結的目的對用戶是不明確的。

#### 用途 — 連結用途（內容中）(2.4.4) {#purpose-link-purpose-in-context}

對所有使用者而言，無論是否受到損害，透過適當連結文字清楚指出連結的方向至關重要。 這可協助使用者決定是否確實要追蹤連結。 對有視力的使用者而言，有意義的連結文字在頁面上有數個連結時（尤其是如果頁面是文字密集型的話）非常有用，因為有意義的連結文字可更清楚地指出目標頁面的功能。 雖然輔助技術的使用者可以產生單一頁面上所有連結的清單，但可以更輕鬆地了解上下文之外的連結文字。

#### 如何達成 — 連結用途（在內容中）(2.4.4) {#how-to-meet-link-purpose-in-context}

最重要的是，請確定連結的文字中已清楚說明連結的用途。

* 錯誤範例：

   * 文字：如需2010年秋季的晚間課程詳細資訊，請按一下 <u>此處</u>.
   * 原因：它沒有明確、明確地指明其目的地。

* 範例：

   * 文字： <u>2010年秋季的夜班</u>  — 詳細資訊。
   * 原因：稍微調整連結元素的文字和位置，即可改善連結文字：

連結的措辭應在各頁面上一致，尤其是導覽列。 例如，若特定頁面的連結已命名為 **出版物** 在單一頁面上，使用其他頁面上的該文字以確保一致性。

然而，在編寫時，關於標題的使用有一些問題：

* 標題屬性中包含的文字通常僅作為工具提示彈出式視窗供滑鼠使用者使用，且無法使用鍵盤存取。
* 螢幕助讀程式可讀取標題屬性，但此功能預設可能未啟用；因此，使用者可能不知道標題屬性存在。
* 很難改變標題文本的外觀，這意味著有些人可能很難或不可能閱讀。

因此，雖然title屬性可用來提供連結的額外內容，請注意其限制，請勿將其用作適當連結文字的替代項目。

當連結由影像組成時，請確定影像的替代文字說明連結的目的地。 例如，如果將書架的影像設為個人出版物的連結，則應閱讀替代文字 **約翰·史密斯的出版物** 和 **書架**.

或者，如果連結錨點除了影像元素外還包含描述連結用途的文字（因此文字會出現在影像旁邊），請為影像使用空白的alt屬性：

```xml
<a href="publications.html">
<img src = "bookshelf.jpg" alt = "" />
John Smith’s publications
</a>
```

>[!NOTE]
上述程式碼片段為圖例，建議您使用 **影像** 元件。

雖然建議您提供可識別連結目的的連結文字而不需要額外內容，但您可以認識到，這並非總是可行的。 無內容連結可用於下列情況，其HTML範例可在 [如何符合成功標準2.4.4](https://www.w3.org/WAI/WCAG20/quickref/#qr-navigation-mechanisms-refs).

* 連結文字屬於密切相關連結清單的一部分，以及包含連結的清單項目提供足夠的內容時。
* 若連結的目的可從 *前置* （非以下）段文本。
* 若連結包含在資料表中，因此可從相關標題中清楚識別目的。
* 如果連結清單包含在一組標題中，而標題本身提供了適當的上下文。
* 其中，連結清單包含在巢狀連結中，而巢狀連結上方的父清單項目提供適當的內容。

在某些情況下，頁面上會有數個連結（每個連結以複雜但必要的詳細資訊提供連結的方向），因此提供可顯示完全相同內容但連結文字未如詳細的替代版網頁可能是適當的。

或者，可以使用指令碼，使得在連結本身內提供最少量的文本，但在激活定位到頁面頂部的適當控制項時，連結文本是 *擴充* 進一步細節。 使用CSS是類似的方法 *隱藏* 目視使用者的完整連結，但仍會以全螢幕輸出給螢幕助讀程式使用者。 這不在本檔案的範圍內，但有關如何達成此目標的詳細資訊，請參閱 [詳細資訊 — 連結用途（內容中）(2.4.4)](#more-information-link-purpose-in-context) 區段。

#### 詳細資訊 — 連結用途（內容中）(2.4.4) {#more-information-link-purpose-in-context}

* [了解成功標準2.4.4](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-refs.html)
* [如何符合成功標準2.4.4](https://www.w3.org/WAI/WCAG20/quickref/#qr-navigation-mechanisms-refs)
* [C7:使用CSS隱藏連結文字的一部分](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/C7)

## 原則3:可理解 {#principle-understandable}

[原則3:可理解 — 資訊和用戶介面的操作必須可理解。](https://www.w3.org/TR/WCAG20/#understandable)

### 讓文字內容可讀且可理解(3.1) {#make-text-content-readable-and-understandable}

[准則3.1可讀：讓文字內容可讀且可理解。](https://www.w3.org/TR/WCAG20/#meaning)

### 頁面語言(3.1.1) {#language-of-page}

* 成功標準3.1.1
* A級
* 頁面語言：每個網頁的預設人類語言可以程式設計地決定。

#### 用途 — 頁面語言(3.1.1) {#purpose-language-of-page}

此成功標準的目的在於確保文字和其他語言內容正確轉譯。 若是螢幕助讀程式使用者，這可確保內容正確發音，而視覺瀏覽器更可能正確顯示特定字元集。

#### 如何相遇 — 頁面語言(3.1.1) {#how-to-meet-language-of-page}

為符合此成功標準，可使用 `lang` 屬性 `<html>` 元素。 例如：

* 如果一頁是英文， `<html>` 元素應該讀取： `<html lang = “en-gb”>`

* 而將頁面轉譯為美文應採用下列標準： `<html lang = “en-us”>`

**在AEM中，您的頁面預設語言是在建立頁面時設定，但在編輯頁面時也可以變更，頁面可由** Sidekick **-** Page **標籤-** Page Properties...存取- **Advanced** 頁籤。

#### 更多資訊 — 頁面語言(3.1.1) {#more-information-language-of-page}

* [了解成功標準3.1.1](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-doc-lang-id.html)
* [如何符合成功標準3.1.1](https://www.w3.org/WAI/WCAG20/quickref/#qr-meaning-doc-lang-id)
* 代碼基於ISO 639-1。 您可以在 [W3學校站點](https://www.w3schools.com/tags/ref_language_codes.asp).

### 部件語言(3.1.2)  {#language-of-parts}

* 成功標準3.1.2
* AA級
* 部件語言：可以以寫程式方式確定內容中每個段落或短語的人類語言，但是，適當的名稱、技術術語、不確定語言的單詞以及作為立即圍繞文本的白話的一部分的單詞或短語除外。

#### 目的 — 部件的語言(3.1.2) {#purpose-language-of-parts}

此成功標準的用途與成功標準類似 [頁面語言](#language-of-page)，但適用於單一頁面上包含多種語言內容的網頁（例如，由於引號或不常見的借記字詞）除外。

套用此成功標準的頁面允許：

* 盲文轉換軟體，以插入帶重音字元。
* 螢幕助讀程式可正確讀出那些未使用預設語言的單詞。
* Google翻譯工具等翻譯工具可將內容從一種語言正確翻譯為另一種語言。

#### 如何交集 — 部件語言(3.1.2) {#how-to-meet-language-of-parts}

此 `lang` 屬性可用來識別內容語言中的變更。 例如，德文引號（ISO 639-1代碼&quot;de&quot;）如下所示：

```xml
<blockquote cite = "John F. Kennedy" lang = "de"> 
     <p>Ich bin ein Berliner</p>
 </blockquote>
```

>[!NOTE]
現成可用的執行個體不支援區塊引號。 可開發自訂元件以支援此功能。

同樣地，若 `span` 元素的使用方式如下：

```xml
<p>The only French phrase I know is <span lang = “fr”>je ne sais quoi</span>.</p>
```

>[!NOTE]
在包含不同語言的名稱或城市，或使用在預設語言中已司空見慣的借詞或片語時(例如 *幸福* 英文)。

若要新增跨度元素（使用適當的語言），您可以在RTE的來源編輯模式中手動編輯HTML標籤，使其如上所示。 或者， `lang` 屬性可由系統管理員包含在RTE中(請參閱 [新增對其他HTML元素和屬性的支援](/help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes))。

#### 更多資訊 — 部件語言(3.1.2) {#more-information-language-of-parts}

* [了解成功標準3.1.2](https://www.w3.org/TR/2016/NOTE-UNDERSTANDING-WCAG20-20161007/meaning-other-lang-id.html)
* [如何符合成功標準3.1.2](https://www.w3.org/WAI/WCAG20/quickref/#qr-meaning-other-lang-id)

### 幫助用戶避免和糾正錯誤(3.3) {#help-users-avoid-and-correct-mistakes}

[准則3.3投入援助：協助使用者避免和修正錯誤。](https://www.w3.org/TR/WCAG20/#minimize-error)

### 標籤或說明(3.3.2) {#labels-or-instructions}

* 成功標準3.3.2
* A級
* 標籤或指示：當內容需要用戶輸入時，提供標籤或指示。

#### 用途 — 標籤或指示(3.3.2) {#purpose-labels-or-instructions}

提供說明以協助使用者填寫表單是介面可用性良好實務的基本部分。 這麼做對於視覺或認知功能障礙的人特別有幫助，因為他們原本可能很難理解表單的版面配置，以及要在特定表單欄位中提供的資料類型。

在AEM中，新增表單元件時會新增預設標籤，例如 **文字欄位**，前往頁面。 此預設標題取決於元件類型。您可以在 **標題和文字** 頁簽。 務必確保標籤可協助使用者了解與每個表單元件相關聯的資料。

![標題和文本頁簽（編輯對話框）;已新增「說明」標題。](assets/chlimage_1-207.png)

此 **標題** 欄位必須用於欄位元素，因為它提供可用於輔助技術的標籤。 僅在欄位旁的文字中寫標籤是不夠的。

對於某些表單元件，您也可以使用「隱藏標題」核取方塊以視覺化方式 **隱藏標籤** 。以此方式隱藏的標籤仍適用於輔助技術，但無法顯示在螢幕上。雖然這在某些情況下是個好方法，但通常最好盡可能加入視覺標籤，因為有些使用者可能會看到畫面的一小部分 (一次看一個欄位)，並需要標籤來正確識別欄位。

#### 影像按鈕 {#image-buttons}

其中使用影像按鈕(例如 **Image Button** 元件)時，編輯對話方塊的「標題」和「文字」索引標籤中的「標題 ******** 」欄位實際上會提供影像的替代文字，而非標籤。因此，在以下範例中，包含文字的影像 `Submit` 的alt文字為 `Submit`，使用編輯對話方塊中的 **Title** 欄位新增。

![在「標題」欄位中設定了「替代文字」的影像按鈕（編輯對話方塊）。](assets/chlimage_1-208.png)

#### 表單欄位群組 {#groups-of-form-fields}

如果有一組相關控制項，例如 **Radio Group**，則可能需要該群組的標題以及個別控制項。在AEM中新增一組選項按鈕時，「標題 **」欄位會提供此群組標題，而個別標題會指定為選項按鈕(** Items ****)。

![新增項目至選項群組。 群組標題是「聯絡我的方式」 — 在「標題」欄位中定義。](assets/chlimage_1-209.png)

不過，群組標題和選項按鈕本身之間沒有程式化關聯。範本編輯人員必須將標題包住必要 `fieldset` 和 `legend` 標籤，才能建立此關聯，而這只能透過編輯頁面原始碼來完成。或者，系統管理員可以新增對這些元素的支援，使這些元素顯示在 **欄位屬性** 對話方塊(請參閱 [新增對其他HTML元素和屬性的支援](/help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes))。

#### 其他Forms考量事項 {#additional-considerations-for-forms}

如果要以特定格式輸入資料，請在標籤文字中清楚說明。 例如，如果必須在 `DD-MM-YYYY` 格式，具體說明這是標籤的一部分。 這表示當螢幕助讀程式的使用者遇到欄位時，會自動宣佈標籤，以及格式的其他資訊。

如果表單欄位的輸入是必填的，請使用標籤中的必要字詞來清楚說明。AEM在需要欄位時新增星號，但最好將字詞加入標 `required`簽本身(在編輯對話方塊的「 **Title** 」欄位中)。

![在「標題」欄位中新增螢幕助讀程式使用者的其他資訊（必要字詞）。](assets/chlimage_1-210.png)

標籤的定位也很重要，因為這有助於他們找到適當的欄位。 當使用者面臨複雜表單時，這尤其重要。 請遵守以下公約：

* 複選框或單選按鈕：標籤會立即放置在欄位的右側。
* 所有其他表單元件（例如文字方塊、下拉式方塊）:標籤會緊接在欄位的上方或緊鄰左側。

以功能非常有限的簡單形式，適當標示 `Submit` 按鈕可作為相鄰欄位的標籤(例如 `Search`)。 這在尋找標籤文字的空格可能很困難的情況下很有用。

#### 更多資訊 — 標籤或說明(3.3.2) {#more-information-labels-or-instructions}

* [了解成功標準3.3.2](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-cues.html)
* [如何符合成功標準3.3.2](https://www.w3.org/WAI/WCAG20/quickref/#qr-minimize-error-cues)

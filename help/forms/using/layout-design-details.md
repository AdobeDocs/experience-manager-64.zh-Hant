---
title: 版面設計
seo-title: Layout Design
description: 版面設計詳細資訊說明如何建立要用於信函或互動式通訊的版面。
seo-description: Layout Design Details explains how you can create layouts to be used for your letters or Interactive Communications.
uuid: b21af474-07f5-4bfe-af7d-0c322e2452ae
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management, interactive-communications
discoiquuid: 046b1bf9-1ac7-4e2e-ab37-6fe5422dfa20
feature: Correspondence Management
exl-id: 92f90e7f-2869-4201-a927-47de1fc08f5c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 0%

---

# 版面設計 {#layout-design}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

XFA表單範本或XDP是以下項目的範本：

* [字母](/help/forms/using/create-letter.md)
* [列印管道](/help/forms/using/web-channel-print-channel.md#printchannel) of [互動式通訊](/help/forms/using/interactive-communications-overview.md)

* 布局片段

XDP是在AdobeForms Designer中設計。 本文詳細說明如何設計您的XDP，以建立有效的對應/互動式通訊，例如在何處使用表單欄位或目標區域，以及何時使用版面片段。

## 為信函或Interactive Communications的打印通道建立佈局 {#creating-a-layout-for-letters-or-for-interactive-communications-print-channel}

佈局定義交互通信的信函/打印通道的圖形佈局。 版面可包含典型的表單欄位，例如「地址」和「參考編號」。 它也包含表示目標區域的空子格式。 在表單設計工具中建立版面，當應用程式專員將其上傳至AEM伺服器時。 從那裡，可以在建立通信模板或打印交互通信通道時選擇佈局。

![設計器：建立版面](assets/claimsubrogationlayout.png)

按照以下步驟建立互動式通信的信函/打印通道的佈局：

1. 分析版面配置，並決定所有頁面上重複的內容；通常頁首與頁尾適用於此類別。 此內容會放置在版面的主版頁面上。 其餘內容會移至版面的內文頁面。 在原則夾克中，標誌和公司地址可新增至主版頁面頁首和頁尾。 例如，取消通知使用相同的佈局。
1. 設計內文頁面時，將頁面內容分成幾個區段。 每個區段的設計都為內嵌於版面本身的子表單或片段版面。 如果節包含表，則將節建模為佈局片段。
1. 佈局的設計如下：

   1. 將每個區段設為包含區段所有元素的個別子表單。
   1. 將每個區段子表單的子表單設為相同父子表單的子表單。 父子表單的佈局設定為「流」，以便在大資料合併到前幾個節時允許節向下移動。
   1. 節主要居住地也可跨其他佈局重複使用。 建立為片段版面。
   1. 章節其他興趣詳細資訊只包含兩個元素，一個放在下面，可以包含大資料，而且設計為流。
   1. 其它部分在特定位置包含元素，以便設計為定位佈局。
   1. 如果區段包含特定位置的元素，且這些元素包含大量資料，則將區段分割為子表單。 然後排列子表單以達到所需的行為。
   1. 對於「主居住區」部分，添加佔位符目標區域。 此預留位置注定會在信函/互動式通訊設計時分割主要住宅。
   1. 將版面（以及使用版面的片段，若有的話）上傳至AEM Forms伺服器。

## 使用結構 {#using-schema}

您可以在版面或版面片段中使用架構，但不是必要項目。 如果您使用結構，請確定下列事項：

1. 信函/互動式通訊中使用的版面配置和所有片段配置使用與信函/互動式通訊相同的架構。
1. 填入資料所需的所有欄位都會系結至結構。

## 建立可關聯欄位 {#creating-relatable-fields}

依預設，所有欄位都可視為與各種其他資料來源相關。 如果您的佈局包含任何與資料源不相關的欄位，請使用「_int」（內部）尾碼為欄位命名；例如pageCount_int。

可關聯欄位必須：

* 是XFA &lt;field> 或 &lt;exclgroup>
* 具有XFA綁定引用
* 如果 &lt;exclgroup>，必須至少有一個子單選按鈕欄位；否則，無法判斷其值類型

可關聯欄位必須：

* 有名字

可關聯欄位不得：

* 在名稱中加上「_int」尾碼
* 已將綁定設定為「無」
* 是 &lt;exclgroup> 元素

只要可關聯欄位符合上述標準，它就可以位於佈局中的任何位置和嵌套深度。 您可以在主版頁面中使用可關聯的欄位。

欄位的版面配置比目標區域子表單更靈活；但它們會系結至單一值類型。 您可以讓欄位變大，或將其設為固定寬度和高度等。 解析的模組或規則結果會推送至欄位。

## 決定何時使用子表單和文字欄位 {#deciding-when-to-use-subforms-and-text-nbsp-fields}

如果您想要以自上而下的垂直流版面（多個段落或影像）擷取多個模組內容，請使用子表單。 您的版面必須處理子表單高度增加以容納其內容的事實。 如果您無法確定與子表單/目標相關聯的內容長度從未超過版面中為子表單保留的空間，請在流式子表單容器內將子表單建立為子表單。 此程式可確保子表單下方的版面物件隨著子表單成長而向下流動。

如果要將模組資料或資料字典元素資料擷取到版面的結構中（因為欄位已系結至資料），或在主版頁面上顯示模組內容，請使用欄位。 請記住，主版頁面中的內容無法與內文頁面內容一起流動，因此您必須確定影像欄位是作為標題標誌使用。 此表格提供更多標準，以決定在版面中使用子表單或欄位的時間。

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>在</strong></p> </td> 
   <td><p><strong>在</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>它包含元素的組合，例如姓氏和名字</p> </td> 
   <td><p>它包含單個元素，如策略編號。</p> </td> 
  </tr> 
  <tr> 
   <td><p>包括多個段落</p> </td> 
   <td><p>文本已包裝並對齊</p> </td> 
  </tr> 
  <tr> 
   <td><p>重複、選用和條件式資料群組會系結至子表單，以降低使用指令碼來達到相同結果時可能發生設計錯誤的風險</p> </td> 
   <td><p>信函/互動式通訊的所有頁面上都會顯示組織標誌和地址等元素。 在這種情況下，請為這些元素建立表單欄位，並將它們放在主版頁面上。 如果將欄位綁定設定為「無資料綁定」，則在信函/互動式通信編輯器中，沒有欄位將顯示為可關聯的欄位。 如果要將某些類型的內容與這些欄位相關，它們必須具有綁定。</p> <p>如果您的公司地址包含多行資料，請使用帶有「允許多行」選項的文本欄位來表示佈局上的地址。</p> <p>如果文本欄位的資料類型設定為純文字檔案，則會使用模組輸出的純文字檔案版本，而不是RTF版本（會捨棄所有格式）。 若要保留格式，請將文字欄位的資料類型設為RTF。</p> </td> 
  </tr> 
  <tr> 
   <td><p>已流動文字</p> </td> 
   <td><p>文本欄位和影像欄位用於主版頁面。 主版頁面無法將子表單用作目標區域。</p> </td> 
  </tr> 
  <tr> 
   <td><p>對象進行分組和組織，而無需將子表單綁定到資料元素</p> </td> 
   <td><p> </p> </td> 
  </tr> 
  <tr> 
   <td><p>子表單內有一個文字欄位。 子表單可以增大，且不會覆寫版面上子表單下方的其他物件。</p> </td> 
   <td><p>您需要在後續程式中輕鬆存取其資料。</p> </td> 
  </tr> 
 </tbody> 
</table>

## 設定重複性要素 {#setting-up-repetitive-elements}

當信函/互動式通訊的所有頁面上都出現您組織的標誌和地址等元素時，請為這些元素建立表單欄位，並將其置於主版頁面上。 對這些欄位使用名稱（欄位名稱）綁定。

## 指定伺服器呈現格式 {#specify-the-server-nbsp-render-format}

將佈局的伺服器呈現格式使用動態XML表單；否則，任何基於此版面的字母/互動式通訊都無法正確轉譯。 預設情況下，Forms Designer中的伺服器呈現格式會設為「動態XML表單」。 若要確保使用正確的格式：

* 在設計工具中，按一下 **[!UICONTROL 檔案>表單屬性>預設]**，並確保「PDF呈現/格式」設定設為「動態XML表單」。

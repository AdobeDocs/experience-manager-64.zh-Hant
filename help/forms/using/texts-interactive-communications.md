---
title: 互動式通信中的文本
seo-title: Text in Interactive Communications
description: 建立和編輯要用於互動式通信的文本文檔片段 — 文本是用於構建互動式通信的四種文檔片段類型之一。 其他三個是條件、清單和版面片段。
seo-description: Creating and editing text document fragments to be used in Interactive Communications
uuid: b2188d34-14f9-4c4e-bbe0-a2e763ed2958
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 7677327a-cc56-413b-b2e3-7b10d0d0319d
feature: Interactive Communication
exl-id: a689aead-7b39-4d66-8922-ae8910c5e9ef
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2269'
ht-degree: 0%

---

# 互動式通信中的文本 {#texts-in-interactive-communications}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

建立和編輯要用於互動式通信的文本文檔片段 — 文本是用於構建互動式通信的四種文檔片段類型之一。 其他三個是條件、清單和版面片段。

## 概觀 {#overview}

文本文檔片段由一個或多個文本段落組成。 段落可以是靜態的或動態的。 動態段落可包含表單資料模型屬性和變數。 您也可以套用規則，並在文字檔案片段內重複。 例如，稱號中的客戶名稱可以是表單資料模型(FDM)屬性，其值可在執行階段使用。 通過更改這些值，可以使用相同的互動式通信為不同的客戶準備使用代理UI的互動式通信。

Interactive Communication中的文本文檔片段支援以下類型的動態資料：

* **資料模型物件**:資料屬性使用後端資料來源。
* **規則型內容**:根據規則出現或隱藏的文字內容部分。 規則也可以以表單資料模型屬性和變數為基礎。
* **變數**:在文字檔案片段中，變數不會系結至後端資料來源。 代理程式在準備互動式通訊以提交至後續程式時，會填入/選取變數中的值，或將變數系結至資料來源。
* **重複**:您的互動式通信中可能有動態資訊，例如信用卡對帳單中的交易，其發生次數可能隨著每個生成的互動式通信而不斷變化。 使用重複，可以格式化和構造此類動態資訊。 如需詳細資訊，請參閱 [內嵌條件和重複](cm-inline-condition.md).

## 建立文字 {#createtext}

1. 選擇 **`[!UICONTROL Forms]`** > **[!UICONTROL 檔案片段]**.
1. 選擇 **`[!UICONTROL Create]`** > **[!UICONTROL 文字]**.
1. 指定下列資訊：

   * **[!UICONTROL 標題]**:（可選）輸入文本文檔片段的標題。 標題不一定唯一，可以有特殊字元和非英文字元。 文字會以標題（如果有）參照，例如縮圖和屬性中。
   * **[!UICONTROL 名稱]**:資料夾內文字的唯一名稱。 任何狀態中都不能有兩個檔案片段（文字、條件或清單）在資料夾中以相同名稱存在。 在「名稱」欄位中，您只能輸入英文字元、數字和連字型大小。 系統會根據「標題」欄位自動填入「名稱」欄位。 在「標題」欄位中輸入的特殊字元、空格、數字和非英文字元在「名稱」欄位中會以連字型大小取代。 雖然「標題」欄位中的值會自動複製到「名稱」，但您可以編輯值。
   * **[!UICONTROL 說明]**:輸入文字的說明。
   * **[!UICONTROL 表單資料模型]**:（可選）選擇「表單資料模型」單選按鈕，以根據表單資料模型建立文本。 選擇「表單資料模型」單選按鈕時， **[!UICONTROL 表單資料模型*]** 欄位。 瀏覽並選取表單資料模型。 為互動式通訊建立文字和條件時，請務必使用您要在互動式通訊中使用的相同資料模型。 如需表單資料模型的詳細資訊，請參閱 [資料整合](/help/forms/using/data-integration.md).
   * **[!UICONTROL 標籤]**:（可選）要建立自定義標籤，請在文本欄位中輸入值，然後按Enter。 儲存此文字時，會建立新新增的標籤。

1. 點選 **[!UICONTROL 下一個]**.

   「建立文本」頁面。 如果已選擇建立基於表單資料模型的文本，則表單資料模型屬性會顯示在左窗格中。

1. 在文字中輸入，然後使用下列選項在文字中設定格式、設定條件及插入表單資料模型屬性和變數：

   * [表單資料模式](#formdatamodel)
   * [變數](#variables)
   * [規則編輯器](#rules)
   * [格式選項](#formatting)

      * [從其他應用程式複製貼上格式化文本](#paste)
      * [突出顯示部分文本](#highlight)
   * [重複](/help/forms/using/cm-inline-condition.md)
   * [特殊字元](#special)
   * [搜索和替代文字](#search-features)
   * [鍵盤快速鍵](/help/forms/using/keyboard-shortcuts.md)


1. 點選 **[!UICONTROL 儲存]**.

   已建立文字。 現在，您可以在建立互動式通訊時，繼續將文字當作建置區塊。

## 編輯文字 {#edittext}

您可以使用下列步驟編輯現有的文本文檔片段。 您也可以選擇在互動式通訊編輯器中編輯文字檔案片段。

1. 選擇 **`[!UICONTROL Forms]`** > **[!UICONTROL 檔案片段]**.
1. 導航到文本文檔片段並選擇它。
1. 點選 **[!UICONTROL 編輯]**.
1. 進行必要的變更。 如需文字選項的詳細資訊，請參閱 [建立文字](#createtext).
1. 點選 **[!UICONTROL 儲存]** 然後點選 **[!UICONTROL 關閉]**.

## 使用表單資料模型屬性個人化文字檔案片段 {#formdatamodel}

您可以插入表單資料模型屬性，以個人化文字檔案片段。 通過在文本中插入表單資料模型屬性，可以在預覽互動式通信時從關聯的資料源中獲取並填充收件人特定的資料。 如需表單資料模型的詳細資訊，請參閱 [AEM Forms資料整合](/help/forms/using/data-integration.md).

如果在建立文本時指定了表單資料模型，則表單資料模型中的屬性將出現在文本編輯器的左窗格中。 指定的表單資料模型應與文本文檔片段以及包含該片段的互動式通信相同。

![insertfdmelementtext](assets/insertfdmelementtext.png)

* 要將FDM屬性插入文本，請將游標置於要插入屬性的位置，然後選擇 **`[A]`** 點選左窗格中的屬性，然後點選 **`[B]`** **[!UICONTROL 添加選定內容]**. 您也可以按兩下屬性，將其插入 **`[C]`** 游標位置。 表單資料模型屬性會以褐色背景顏色強調顯示。

* 若要允許代理在 [準備併發送互動式通信](/help/forms/using/prepare-send-interactive-communication.md) 使用代理UI，點選 **`[D]`** 該屬性的鎖定圖示，並確保其處於未鎖定狀態。 屬性的預設狀態已鎖定，代理無法在代理UI中編輯屬性。

您也可以使用表單資料模型屬性來建構用於顯示或隱藏部分內容的規則。 如需詳細資訊，請參閱 [在文字中建立規則](#rules).

## 在文字檔案片段中建立和使用變數 {#variables}

變數是建立互動式通訊時可系結的預留位置。 變數可系結至表單資料模型屬性或文字片段。 您也可以保留變數供代理程式填入。

在下列情況下，您可以使用變數，而非表單資料模型屬性：

* 文本文檔片段用於多個互動式通信中，其中不同互動式通信需要不同的綁定。
* 文本文檔片段建立時沒有表單資料模型。 您可以插入變數，並稍後在建立互動式通訊時將它們綁定到表單資料模型屬性。
* 您需要綁定和檢索文本文檔片段中的文本。 只有這些文字檔案片段可系結至變數，其中不應有任何變數。

在建立或編輯文本文檔片段時，可以建立和插入變數。 您建立的變數會顯示在代理UI的「資料」索引標籤中。 此代理會指定變數的值，同時 [使用Agent UI準備和發送互動式通信](/help/forms/using/prepare-send-interactive-communication.md).

### 建立變數 {#create-variables}

1. 在左窗格中，點選 **[!UICONTROL 變數]**.

   「變數」窗格隨即出現。

   ![變數窗格](assets/variablespane.png)

1. 點選 **[!UICONTROL 建立]**.

   「建立變數」窗格隨即出現。

1. 輸入下列資訊並點選 **[!UICONTROL 建立]**:

   * **[!UICONTROL 姓名*]**:變數的名稱。
   * **[!UICONTROL 說明]**:（可選）輸入有關變數的說明。
   * **[!UICONTROL 類型*]**:選取變數類型：字串、數字、布林或日期。
   * **[!UICONTROL 僅允許特定值]**:對於字串和數字變數，您可以確保代理從特定值集中為代理UI中的預留位置進行選擇。 若要指定值集，請選取此選項，然後指定 **[!UICONTROL 值]** 欄位。

1. 點選 **[!UICONTROL 建立]**.

   變數會建立並列在「變數」窗格中。

1. 若要在文字中插入變數，請將游標置於適當位置，選取變數，然後點選 **[!UICONTROL 添加選定內容]**.

   ![變數插入](assets/variableinserted.png)

   變數會以淺藍色背景顏色反白顯示，而表單資料模型屬性則會以淺藍色反白顯示。

1. 點選 **[!UICONTROL 儲存]**.

## 在文字中建立規則 {#rules}

在文字中使用規則編輯器，您可以建立規則，以根據 **預設條件**. 這些條件可以根據：

* 字串
* 數字
* 數學表達式
* 日期
* 關聯表單資料模型的屬性
* 您可能在文字中建立的任何變數

### 在文字中建立規則 {#create-rules-in-text}

1. 在建立或編輯文字時，選取要使用規則條件化的文字字串、段落或內容。

   ![selectcontentapplyrule](assets/selectcontentapplyrule.png)

1. 點選 **[!UICONTROL 建立規則]**.

   將出現「建立規則」對話框。 除了字串、數字、數學運算式和日期之外，規則編輯器中也提供下列項目，用於建立規則的陳述式：

   * 關聯表單資料模型的屬性
   * 您可能已建立的任何變數

   選擇要評估的適當選項。

   ![規則編輯器](assets/ruleeditor.png)

   ![ruleeditorfdm](assets/ruleeditorfdm.png)

   >[!NOTE]
   >
   >建立規則時不支援集合屬性來條件化和顯示文字。

1. 選取適當的運算子以評估規則，例如「等於」、「包含」和「開頭為」。

   ![ruleeditorfdm-1](assets/ruleeditorfdm-1.png)

1. 插入評估表達式、值、資料模型屬性或變數。

   ![如果根據FDM的來源資料收件者位置為US，則顯示所選文字的規則](assets/ruleeditorfdm-1-1.png)

   如果根據FDM的來源資料收件者位置為US，則顯示所選文字的規則

   * 在建立或編輯規則時，您也可以點選 ![icon_resize](assets/icon_resize.png) （調整大小）以展開「建立規則/編輯規則」對話方塊。 展開的全視窗對話方塊可讓您拖放表單資料模型屬性和變數以建立規則。 再次點選「調整大小」，返回「建立規則」對話方塊。
   * 您也可以在規則中建立多個條件。
   * 您也可以建立重疊的規則，其中規則會套用至已套用規則之內容的一部分。

1. 點選 **[!UICONTROL 完成]**.

   規則會套用。 套用規則的文字或內容會以綠色強調顯示。 將滑鼠移至醒目提示的左側控點時，套用的規則隨即出現。

   ![appliedruletext](assets/appliedruletext.png)

   按一下套用規則的左側控制代碼時，您會獲得可編輯或移除規則的選項。

## 格式化文字 {#formatting}

建立或編輯文字時，工具列會根據您選擇進行的編輯類型而變更：段落、對齊或清單：

選擇工具欄類型：段落、對齊或清單

![字型編輯工具列](do-not-localize/paragraphtoolbar-1.png)

字型編輯工具列

![對齊工具欄](assets/alignmenttoolbar.png)

對齊工具欄

![清單工具欄](do-not-localize/listingtoolbar.png)

清單工具欄

### 加亮/強調部分文本 {#highlight}

要突出顯示或強調可編輯的文檔片段中的部分文本，請選擇該文本並點選「突出顯示顏色」。

![textbackgroundcolorapplied-1](assets/textbackgroundcolorapplied-1.png)

您可以直接點選基本顏色 **`[A]`** 顯示在「基本顏色」調色板中或點選 **選擇** 使用滑桿後 **`[B]`** 來選擇適當的顏色。

（可選）您也可以轉到「高級」頁簽，以選擇適當的「色相」、「明度」和「飽和度」 **`[C]`** 要建立精確顏色，然後點選「選擇」 **`[D]`** ，以應用顏色來突出顯示文本。

![textbackgroundcolor-2](assets/textbackgroundcolor-2.png)

### 貼上格式化文字 {#paste}

要重複使用其他應用程式中存在的文本的一個或多個段落，例如，從Microsoft® Word或HTML頁面，請將文本複製並貼到文本編輯器中。 複製文本的格式將保留在文本編輯器中。

您可以在可編輯的文字檔案片段中複製並貼上一或多段文字。 例如，您可能有一份Microsoft® Word文檔，其中包含可接受居住校樣的項目符號清單，如下所示：

![pastetextmsword-2](assets/pastetextmsword-2.png)

您可以直接從Microsoft® Word檔案複製文字並貼上至可編輯的文字檔案片段。 文本文檔片段中保留格式（如項目符號清單、字型和文本顏色）。

![pastetexteditablemodule-1](assets/pastetexteditablemodule-1.png)

>[!NOTE]
>
>但貼上文字的格式有一些 [限制](https://helpx.adobe.com/aem-forms/kb/cm-copy-paste-text-limitations.html).

## 在文本中插入特殊字元 {#special}

如果需要，請在文檔片段中插入特殊字元。 例如，您可以使用「特殊字元」浮動視窗來插入：

* 貨幣符號，如€、¥和£
* 數學符號，如∑、√、∂和^
* 標點符號，例如&quot;和&quot;

![specialcharacters-2](assets/specialcharacters-2.png)

文字編輯器內建支援210個特殊字元。 管理員可 [新增支援更多/自訂特殊字元，可依自訂](/help/forms/using/custom-special-characters.md).

## 搜索和替代文字 {#search-features}

處理包含大量文字的文字檔案片段時，您需要搜尋特定的文字字串。 您也可能需要將特定文字字串取代為替代字串。

「查找和替換」功能允許您搜索（和替換）文本文檔片段中的任何文本字串。 此功能也包含強大的規則運算式搜尋功能。

1. 為開啟文本文檔片段 [編輯](#edittext).
1. 點選 **[!UICONTROL 查找和替換]**.

1. 在 **[!UICONTROL 查找]** 框中，選擇「替換」 **[!UICONTROL 取代]** 文字方塊和點選 **[!UICONTROL 取代]**.

1. 如果找到所搜尋的文字，則會以取代文字取代文字。

   * 如果找到搜索文本的另一個實例，則該實例將在文本文檔片段中突出顯示。 如果您點選 **[!UICONTROL 取代]** 同樣，如果找到第三個實例，則替換突出顯示的實例，游標向前移動。
   * 如果找不到其他實例，則「查找和替換」對話框將顯示一條消息：已到模組結束。

   您也可以點選「全部取代」，一次取代所有匹配項。

   「尋找和取代」也包含功能強大的規則運算式搜尋。 若要在搜尋中使用規則運算式，請選取 **[!UICONTROL Reg ex]** 然後點選 **[!UICONTROL 查找]** 或 **[!UICONTROL 取代]**.

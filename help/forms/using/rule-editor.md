---
title: 適用性表單規則編輯器
seo-title: 適用性表單規則編輯器
description: 適用性表單規則編輯器可讓您新增動態行為，並將複雜邏輯建置至表單中，而不需編碼或編寫指令碼。
seo-description: 適用性表單規則編輯器可讓您新增動態行為，並將複雜邏輯建置至表單中，而不需編碼或編寫指令碼。
uuid: 15c9bb41-ddae-4d3e-b130-5eb1b7572e6e
content-type: reference
topic-tags: adaptive_forms, develop
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 66a3528a-489b-4fd0-be6c-b8c4b9b1f908
feature: 適用性表單
exl-id: 7cd73bdf-6717-4923-91ca-e8b6d44429ca
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '6354'
ht-degree: 0%

---

# 適用性表單規則編輯器{#adaptive-forms-rule-editor}

## 概覽 {#overview}

Adobe Experience Manager Forms中的規則編輯器功能可讓表單業務使用者和開發人員針對最適化表單物件撰寫規則。 這些規則會根據預設條件、使用者輸入和表單上的使用者動作，定義要在表單物件上觸發的動作。 它有助於進一步簡化表單填寫體驗，確保準確性和速度。

規則編輯器提供直覺且簡化的使用者介面，可編寫規則。 規則編輯器為所有使用者提供視覺編輯器。 此外，規則編輯器僅針對表單高級用戶提供編寫規則和指令碼的代碼編輯器。 您可以使用規則對適用性表單物件執行的一些重要動作包括：

* 顯示或隱藏對象
* 啟用或禁用對象
* 為對象設定值
* 驗證物件的值
* 執行函式以計算對象的值
* 調用表單資料模型服務並執行操作
* 設定對象的屬性

規則編輯器取代了AEM 6.1 Forms及舊版中的指令碼功能。 不過，您現有的指令碼會保留在新的規則編輯器中。 如需在規則編輯器中使用現有指令碼的詳細資訊，請參閱[規則編輯器對現有指令碼的影響](/help/forms/using/rule-editor.md#p-impact-of-rule-editor-on-existing-scripts-p)。

新增至Forms-power-users群組的使用者可以建立新指令碼並編輯現有的指令碼。 表單使用者群組中的使用者可以使用指令碼，但無法建立或編輯指令碼。

## 了解規則{#understanding-a-rule}

規則是動作和條件的組合。 在規則編輯器中，動作包括隱藏、顯示、啟用、停用或計算表單中物件的值等活動。 條件是布林運算式，通過對表單對象的狀態、值或屬性執行檢查和操作來評估。 動作是根據評估條件所傳回的值（`True`或`False`）執行。

規則編輯器提供一組預先定義的規則類型，例如「時間」、「顯示」、「隱藏」、「啟用」、「停用」、「設定值」和「驗證」，以協助您編寫規則。 每個規則類型都可讓您定義規則中的條件和動作。 本檔案進一步詳細說明每種規則類型。

規則通常遵循下列其中一個結構：

**條件 —** 動作在此結構中，規則會先定義條件，接著定義要觸發的動作。此結構可與寫程式語言中的if-then陳述式比較。

在規則編輯器中，**When**&#x200B;規則類型可強制執行條件 — 動作結構。

**動作條** 件在此結構中，規則會先定義要觸發的動作，接著定義評估的條件。此結構的另一個變數是action-condition-alternate動作，也定義了條件傳回False時要觸發的替代動作。

規則編輯器中的「顯示」、「隱藏」、「啟用」、「禁用」、「設定值」和「驗證」規則類型強制實施action-condition規則結構。 預設情況下，「顯示」的替代操作為「隱藏」，「啟用」的替代操作為「禁用」，反之亦然。 不能更改預設替代操作。

>[!NOTE]
>
>可用的規則類型，包括您在規則編輯器中定義的條件和動作，也取決於您要建立規則的表單物件類型。 規則編輯器僅顯示有效的規則類型和選項，用於編寫特定表單對象類型的條件和操作語句。 例如，您沒有看到面板物件的「驗證」、「設定值」、「啟用」和「停用」規則類型。

如需規則編輯器中可用規則類型的詳細資訊，請參閱規則編輯器](/help/forms/using/rule-editor.md#p-available-rule-types-in-rule-editor-p)中的「可用規則類型」。[

### 選擇規則結構{#guidelines-for-choosing-a-rule-construct}的指南

雖然您可以使用任何規則結構來達到大部分的使用案例，但以下提供一些准則以供您選擇一個結構而非另一個結構。 如需規則編輯器中可用規則的詳細資訊，請參閱規則編輯器](/help/forms/using/rule-editor.md#p-available-rule-types-in-rule-editor-p)中的「可用規則類型」。[

* 建立規則時，一般的經驗法則是在您要撰寫規則的物件內容中加以思考。 請考慮您要根據用戶在欄位A中指定的值來隱藏或顯示欄位B。在此情況下，您正在評估欄位A上的條件，並根據它返回的值，您將觸發欄位B上的操作。

   因此，如果您要在欄位B上撰寫規則（您要評估條件的物件），請使用condition-action結構或When規則類型。 同樣地，請使用action-condition結構，或在欄位A上使用Show或Hide規則類型。

* 有時，您需要根據一個條件執行多個動作。 在這種情況下，建議使用條件 — 動作結構。 在此結構中，您可以評估條件一次，並指定多個動作陳述式。

   例如，要根據條件來隱藏欄位B、C和D，以檢查用戶在欄位A中指定的值，請使用條件 — 操作結構或當欄位A上的規則類型編寫一個規則，並指定操作來控制欄位B、C和D的可見性。否則，您需要在欄位B、C和D上使用三個不同的規則，其中每個規則都檢查條件，並顯示或隱藏相應的欄位。 在此示例中，在一個對象上編寫「當」規則類型比在三個對象上顯示或隱藏規則類型更有效。

* 若要根據多個條件觸發動作，建議使用action-condition建構。 例如，要通過評估欄位B、C和D上的條件來顯示和隱藏欄位A，請在欄位A上使用「顯示」或「隱藏」規則類型。
* 如果規則包含一個條件的動作，請使用條件 — 動作或動作條件結構。
* 如果規則檢查條件，並在提供欄位中的值或退出欄位時立即執行動作，建議在評估條件的欄位上使用condition-action結構或When規則類型來編寫規則。
* 當用戶更改應用了When規則的對象的值時，將評估When規則中的條件。 不過，如果您想要在值在伺服器端變更時觸發動作，例如在預先填入值時，建議您撰寫當欄位初始化時觸發動作的「時間」規則。
* 在編寫下拉清單、單選按鈕或複選框對象的規則時，這些表單對象的選項或值在規則編輯器中預先填充。

## 規則編輯器{#available-operator-types-and-events-in-rule-editor}中可用的運算子類型和事件

規則編輯器提供下列邏輯運算子和事件，您可使用這些運算子和事件建立規則。

* **等於**
* **不等於**
* **開頭為**
* **結尾為**
* **包含**
* **為空**
* **不為空**
* **已選取：** 當使用者為核取方塊、下拉式清單、選項按鈕選取特定選項時，會傳回true。
* **初始化（事件）:** 表單物件在瀏覽器中轉譯時傳回true。
* **已變更（事件）:** 當使用者變更表單物件的輸入值或選取的選項時，會傳回true。

## 規則編輯器{#available-rule-types-in-rule-editor}中可用的規則類型

規則編輯器提供一組預先定義的規則類型，您可用來編寫規則。 讓我們詳細查看每個規則類型。 有關在規則編輯器中寫入規則的詳細資訊，請參閱[寫入規則](/help/forms/using/rule-editor.md#p-write-rules-p)。

### 時間 {#when}

**When**&#x200B;規則類型遵循&#x200B;**condition-action-alternate action**&#x200B;規則結構，有時只遵循&#x200B;**condition-action**&#x200B;結構。 在此規則類型中，您首先指定評估條件，然後在滿足條件時觸發動作(`True`)。 使用When規則類型時，可以使用多個AND和OR運算子來建立[巢狀運算式](#nestedexpressions)。

使用「時間」(When)規則類型，可以評估表單對象上的條件，並對一個或多個對象執行操作。

簡單來說，典型的「當時」規則的結構如下：

```bash
When on Object A:

(Condition 1 AND Condition 2 OR Condition 3) is TRUE;

Then, do the following:

Action 2 on Object B;  
AND  
Action 3 on Object C;
```

如果您有多值元件（如選項按鈕或清單），則在為該元件建立規則時，系統會自動擷取選項，並供規則建立者使用。 您不需要再次輸入選項值。

例如，清單有四個選項：紅、藍、綠、黃。 建立規則時，會自動擷取選項（選項按鈕），並讓規則建立者使用，如下所示：

![多值displayoptions](assets/multivaluefcdisplaysoptions.png)

撰寫「時間」規則時，您可以觸發「清除值」動作。 「清除值」(Clear Value Of)操作會清除指定對象的值。 在When語句中將「清除值」(Clear Value)設定為選項，允許您使用多個欄位建立複雜條件。

![clearvalue](assets/clearvalueof.png)

**** 隱藏隱藏指定的對象。

**** Show顯示指定的對象。

**** Enable啟用指定的對象。

**** DisableDisables指定的對象。

**調用** 服務調用在表單資料模型中配置的服務。選擇「調用服務」操作時，將顯示一個欄位。 點選欄位時，它會顯示您AEM執行個體上所有表單資料模型中設定的所有服務。 選擇表單資料模型服務時，將顯示其他欄位，您可以在其中使用指定服務的輸入和輸出參數映射表單對象。 請參閱叫用表單資料模型服務的範例規則。

除了表單資料模型服務外，還可以指定直接WSDL URL來調用Web服務。 但是，表單資料模型服務有許多優點，並且建議使用調用服務的方法。

如需在表單資料模型中設定服務的詳細資訊，請參閱[AEM Forms資料整合](/help/forms/using/data-integration.md)。

**設定** 值ofComputes並設定指定對象的值。您可以將對象值設定為字串、另一個對象的值、使用數學表達式或函式的計算值、對象的屬性值或配置的表單資料模型服務的輸出值。 當您選擇Web服務選項時，它會顯示在AEM例項上所有表單資料模型中設定的所有服務。 選擇表單資料模型服務時，將顯示其他欄位，您可以在其中使用指定服務的輸入和輸出參數映射表單對象。

如需在表單資料模型中設定服務的詳細資訊，請參閱[AEM Forms資料整合](/help/forms/using/data-integration.md)。

**設** 定屬性設定指定對象的屬性的值。

**清除** 值清除指定對象的值。

**設定** FocusSets焦點在指定的對象上。

**保存** 表單保存表單。

**提交** 表單提交表單。

**重設** 表單重設表單。

**驗證** 表單驗證表單。

**添加** 實例添加指定的可重複面板或表行的實例。

**刪** 除實例刪除指定的可重複面板或表行的實例。

### 設定下列項目的值: {#set-value-of}

**[!UICONTROL 設定值]**&#x200B;規則類型允許您根據是否滿足指定條件來設定表單對象的值。 該值可以設定為另一對象的值、常值字串、從數學表達式或函式導出的值、另一對象的屬性的值或表單資料模型服務的輸出。 同樣地，您也可以檢查元件、字串、屬性，或從函式或數學運算式衍生的值上的條件。

請注意，「設定值」規則類型不適用於所有表單對象，如面板和工具欄按鈕。 規則的標準設定值具有下列結構：

將對象A的值設定為：

（字串ABC）或\
（對象C的對象屬性X）OR\
（來自函式的值）OR\
（數學表達式中的值）OR\
（資料模型服務或web服務的輸出值）;

時機（選用）:

（條件1、條件2、條件3）為TRUE;

以下示例將`dependentid`欄位中的值作為輸入，並將`Relation`欄位的值設定為`getDependent`表單資料模型服務的`Relation`參數的輸出。

![set-value-web-service](assets/set-value-web-service.png)

使用表單資料模型服務設定值規則範例

>[!NOTE]
>
>此外，您也可以使用「設定規則的值」，從表單資料模型服務或網站服務的輸出，填入下拉式清單元件中的所有值。 不過，請確定您選擇的輸出引數為陣列類型。 陣列中傳回的所有值都可在指定的下拉式清單中使用。

### 顯示 {#show}

使用&#x200B;**Show**&#x200B;規則類型，您可以根據是否滿足條件編寫規則以顯示或隱藏表單對象。 如果條件不滿足，則顯示規則類型也會觸發隱藏動作，或傳回`False`。

典型的「顯示」規則的結構如下：

`Show Object A;`

`When:`

`(Condition 1 OR Condition 2 OR Condition 3) is TRUE;`

`Else:`

`Hide Object A;`

### 隱藏 {#hide}

與「顯示」規則類型類似，您可以使用&#x200B;**Hide**&#x200B;規則類型來根據是否滿足條件來顯示或隱藏表單對象。 如果條件不滿足，則「隱藏」規則類型也會觸發「顯示」動作，或傳回`False`。

典型的隱藏規則結構如下：

`Hide Object A;`

`When:`

`(Condition 1 AND Condition 2 AND Condition 3) is TRUE;`

`Else:`

`Show Object A;`

### 啟用 {#enable}

**啟用**&#x200B;規則類型可讓您根據是否滿足條件來啟用或停用表單物件。 如果條件不滿足，則「啟用」規則類型也會觸發「停用」動作，或傳回`False`。

一般的「啟用」規則的結構如下：

`Enable Object A;`

`When:`

`(Condition 1 AND Condition 2 AND Condition 3) is TRUE;`

`Else:`

`Disable Object A;`

### 停用 {#disable}

與「啟用」規則類型類似， **Disable**&#x200B;規則類型允許您根據是否滿足條件來啟用或禁用表單對象。 如果條件不滿足，則禁用規則類型也會觸發啟用操作或返回`False`。

典型的「停用」規則的結構如下：

`Disable Object A;`

`When:`

`(Condition 1 OR Condition 2 OR Condition 3) is TRUE;`

`Else:`

`Enable Object A;`

### 驗證 {#validate}

**Validate**&#x200B;規則類型使用運算式驗證欄位中的值。 例如，您可以撰寫運算式來檢查用於指定名稱的文字方塊是否不包含特殊字元或數字。

典型的驗證規則結構如下：

`Validate Object A;`

`Using:`

`(Expression 1 AND Expression 2 AND Expression 3) is TRUE;`

>[!NOTE]
>
>如果指定的值不符合驗證規則，您可以向使用者顯示驗證訊息。 您可以在側欄中元件屬性的&#x200B;**[!UICONTROL 指令碼驗證訊息]**&#x200B;欄位中指定訊息。

![指令碼驗證](assets/script-validation.png)

## 了解規則編輯器使用者介面{#understanding-the-rule-editor-user-interface}

規則編輯器提供完整且簡單的使用者介面，可編寫及管理規則。 您可以以製作模式從最適化表單中啟動規則編輯器使用者介面。

若要啟動規則編輯器使用者介面：

1. 在製作模式中開啟最適化表單。
1. 點選您要為其編寫規則的表單物件，然後在「元件工具列」中點選![edit-rules](assets/edit-rules.png)。 規則編輯器使用者介面隨即顯示。

   ![建立規則](assets/create-rules.png)

   此視圖將列出選定表單對象上的任何現有規則。 有關管理現有規則的資訊，請參閱[管理規則](/help/forms/using/rule-editor.md#p-manage-rules-p)。

1. 點選&#x200B;**[!UICONTROL 建立]**以撰寫新規則。 規則編輯器使用者介面的視覺編輯器在您首次啟動規則編輯器時，會預設開啟。
   ![規則編輯器UI](assets/rule-editor-ui.png)

   [按一](assets/rule-editor-ui-1.png)
  下放大讓我們詳細查看規則編輯器UI的每個元件。

### A.元件規則顯示{#a-component-rule-display}

顯示您用來啟動規則編輯器的適用性表單物件標題，以及目前選取的規則類型。 在上述範例中，規則編輯器是從名為Salary的適用性表單物件啟動，而選取的規則類型為When。

### B.表單對象和函式{#b-form-objects-and-functions-br}

規則編輯器使用者介面左側的窗格包含兩個標籤： **[!UICONTROL Forms物件]**&#x200B;和&#x200B;**[!UICONTROL 函式]**。

「表單對象」頁簽顯示適用性表單中包含的所有對象的分層視圖。 它顯示對象的標題和類型。 撰寫規則時，您可以將表單物件拖放至規則編輯器。 在將物件或函式拖放至預留位置時建立或編輯規則時，預留位置會自動取用適當的值類型。

已應用一個或多個有效規則的表單對象標籤為綠色圓點。 如果應用於表單對象的任何規則無效，則表單對象將標籤為黃色圓點。

「函式」索引標籤包含一組內建函式，例如「總和」、「最小值」、「最大值」、「平均值」、「數量」和「驗證表單」。 您可以使用這些函式來計算可重複面板和表格列中的值，並在撰寫規則時於動作和條件陳述式中使用這些值。 但您也可以建立[自訂函式](/help/forms/using/rule-editor.md#custom-functions)。

![函式頁簽](assets/functions.png)

>[!NOTE]
>
>您可以在「Forms對象和函式」頁簽中對對象和函式名稱和標題執行文本搜索。

在表單對象的左樹中，可以點選表單對象以顯示應用於每個對象的規則。 您不僅可以瀏覽各種表單物件的規則，還可以在表單物件之間複製貼上規則。 如需詳細資訊，請參閱[複製貼上規則](/help/forms/using/rule-editor.md#p-copy-paste-rules-p)。

### C.表單對象和函式切換{#c-form-objects-and-functions-toggle-br}

切換按鈕在點選時切換表單對象和函式窗格。

### D.可視化規則編輯器{#d-visual-rule-editor}

可視化規則編輯器是規則編輯器用戶介面的可視化編輯器模式中您在其中編寫規則的區域。 它可讓您選取規則類型，並據以定義條件和動作。 在規則中定義條件和動作時，您可以從「表單對象和函式」窗格拖放表單對象和函式。

有關使用可視化規則編輯器的詳細資訊，請參閱[寫入規則](/help/forms/using/rule-editor.md#p-write-rules-p)。

### E.可視化代碼編輯器切換器{#e-visual-code-editors-switcher}

表單功能使用者群組中的使用者可以存取程式碼編輯器。 對於其他使用者，無法使用程式碼編輯器。 如果您有權限，可以使用規則編輯器上方的切換器，從視覺編輯器模式切換為規則編輯器的程式碼編輯器模式（反之亦然）。 第一次啟動規則編輯器時，它會以視覺編輯器模式開啟。 您可以在可視化編輯器模式下編寫規則，或切換到代碼編輯器模式以編寫規則指令碼。 不過，請注意，如果您修改規則或在程式碼編輯器中撰寫規則，則無法切換回該規則的視覺編輯器，除非您清除程式碼編輯器。

AEM Forms會追蹤您上次用來撰寫規則的規則編輯器模式。 下次啟動規則編輯器時，該編輯器會在該模式中開啟。 不過，您也可以設定預設模式，以在指定模式中開啟規則編輯器。 若要這麼做：

1. 前往AEM Web主控台，網址為https://[host]:[port]/system/console/configMgr。
1. 按一下可編輯&#x200B;**[!UICONTROL 適用性表單和互動式通訊Web通道配置]**。
1. 從&#x200B;**[!UICONTROL 規則編輯器的預設模式]**&#x200B;下拉式清單中選擇&#x200B;**[!UICONTROL 可視化編輯器]**&#x200B;或&#x200B;**[!UICONTROL 代碼編輯器]**

1. 按一下「**[!UICONTROL 儲存]**」。

### F.完成和取消按鈕{#f-done-and-cancel-buttons}

**[!UICONTROL Done]**&#x200B;按鈕用於儲存規則。 您可以儲存不完整的規則。 但是，不完整無效且未執行。 下次從相同表單物件啟動規則編輯器時，會列出表單物件上儲存的規則。 您可以在該檢視中管理現有規則。 如需詳細資訊，請參閱[管理規則](/help/forms/using/rule-editor.md#p-manage-rules-p)。

**[!UICONTROL 取消]**&#x200B;按鈕會捨棄您對規則所做的任何變更並關閉規則編輯器。

## 寫入規則{#write-rules}

您可以使用可視化規則編輯器或代碼編輯器來編寫規則。 第一次啟動規則編輯器時，會以視覺編輯器模式開啟規則編輯器。 您可以切換至程式碼編輯器模式並撰寫規則。 不過，請注意，如果您在程式碼編輯器中撰寫或修改規則，則無法切換至該規則的視覺編輯器，除非您清除程式碼編輯器。 下次啟動規則編輯器時，它會以您上次用來建立規則的模式開啟。

先來看看如何使用視覺編輯器撰寫規則。

### 使用可視編輯器{#using-visual-editor}

讓我們使用下列範例表單，了解如何在視覺化編輯器中建立規則。

![create-rule-example](assets/create-rule-example.png)

貸款申請表示例中的「貸款要求」部分要求申請人指定其婚姻狀況、薪金，如果已婚，其配偶的薪金。 此規則會根據用戶輸入計算貸款資格金額，並顯示在「貸款資格」欄位中。 套用下列規則以實作案例：

* 只有在婚姻狀況已婚時，才顯示「配偶的薪金」欄位。
* 貸款資格金額是薪金總額的50%。

執行下列步驟來編寫規則：

1. 首先，根據用戶為「婚姻狀態」單選按鈕選擇的選項，編寫規則以控制「配偶薪金」欄位的可見性。

   以編寫模式開啟貸款申請表。 點選「**婚姻狀態**」元件，然後點選「![edit-rules](assets/edit-rules.png)」。 接下來，點選&#x200B;**[!UICONTROL 建立]**&#x200B;以啟動規則編輯器。

   ![write-rules-visual-editor-1](assets/write-rules-visual-editor-1.png)

   啟動規則編輯器時，預設會選取「時間」規則。 此外，在When語句中指定了啟動規則編輯器時的表單對象（在本例中是婚姻狀態）。

   雖然您無法更改或修改所選對象，但可以使用規則下拉式清單（如下所示）選擇其他規則類型。 如果您想要在另一個物件上建立規則，請點選「取消」以退出規則編輯器，然後從所需的表單物件重新啟動。

1. 點選「**[!UICONTROL 選取狀態]**」下拉式清單，然後選取「**[!UICONTROL 等於]**」。 將顯示&#x200B;**[!UICONTROL 輸入字串]**&#x200B;欄位。

   ![write-rules-visual-editor-2](assets/write-rules-visual-editor-2.png)

   在「婚姻狀態」單選按鈕中，分別為&#x200B;**0**&#x200B;和&#x200B;**1**&#x200B;值分配&#x200B;**已婚**&#x200B;和&#x200B;**單個**&#x200B;選項。 您可以驗證「編輯」選項按鈕對話框的「標題」頁簽中的分配值，如下所示。

   ![來自規則編輯器的選項按鈕值](assets/radio-button-values.png)

1. 在規則的&#x200B;**輸入字串**&#x200B;欄位中，指定&#x200B;**0**。

   ![write-rules-visual-editor-4](assets/write-rules-visual-editor-4.png)

   已將條件定義為`When Marital Status is equal to Married`。 接下來，定義若此條件為True，則要執行的動作。

1. 在Then語句中，從&#x200B;**[!UICONTROL Select Action]**&#x200B;下拉式清單中選擇&#x200B;**[!UICONTROL Show]**。

   ![write-rules-visual-editor-5](assets/write-rules-visual-editor-5.png)

1. 從&#x200B;**Drop對象上的「表單對象」頁簽拖放**&#x200B;配偶薪金&#x200B;**欄位，或選擇此處**&#x200B;欄位。 或者，點選「**Drop object（放置對象）」或選擇「here**（此處）」欄位，然後從彈出菜單中選擇「**配偶薪金**」欄位，該欄位將列出窗體中的所有表單對象。

   ![write-rules-visual-editor-6](assets/write-rules-visual-editor-6.png)

   規則編輯器中的規則顯示如下。

   ![write-rules-visual-editor-7](assets/write-rules-visual-editor-7.png)

   點選&#x200B;**Done**&#x200B;以儲存規則。

1. 重複步驟1到5以定義另一個規則，以在婚姻狀態為「單身」時隱藏「配偶薪金」欄位。 規則編輯器中的規則顯示如下。

   ![write-rules-visual-editor-8](assets/write-rules-visual-editor-8.png)

   >[!NOTE]
   >
   >或者，您可以在「配偶薪金」欄位上編寫一個「顯示」規則，而不是在「婚姻狀態」欄位上編寫兩個「當」規則，以實施相同的行為。

   ![write-rules-visual-editor-9](assets/write-rules-visual-editor-9.png)

1. 接下來，編寫一個規則以計算貸款資格金額（該金額是總薪金的50%），並將其顯示在「貸款資格」欄位中。 要達到此目的，請在「貸款資格」欄位上建立&#x200B;**設定**&#x200B;規則的值。

   在製作模式中，點選&#x200B;**[!UICONTROL Loan Apbility]**&#x200B;欄位，然後點選![edit-rules](assets/edit-rules.png)。 接下來，點選&#x200B;**[!UICONTROL 建立]**&#x200B;以啟動規則編輯器。

1. 從規則下拉式清單中選取&#x200B;**[!UICONTROL 設定]**&#x200B;規則的值。

   ![write-rules-visual-editor-10](assets/write-rules-visual-editor-10.png)

1. 點選「**[!UICONTROL 選取選項]**」 ，然後選取「**[!UICONTROL 數學運算式]**」。 將開啟一個用於編寫數學表達式的欄位。

   ![write-rules-visual-editor-11](assets/write-rules-visual-editor-11.png)

1. 在運算式欄位中：

   * 從「Forms對象」頁簽中，選擇或拖放第一個&#x200B;**拖放對象中的**&#x200B;薪金&#x200B;**欄位，或選擇此處**&#x200B;欄位。
   * 從&#x200B;**Select Operator**&#x200B;欄位中選擇&#x200B;**Plus**。
   * 從「Forms對象」頁簽中，選擇或拖放其他&#x200B;**拖放對象中的**&#x200B;配偶薪金&#x200B;**欄位，或選擇此處**&#x200B;欄位。

   ![write-rules-visual-editor-12](assets/write-rules-visual-editor-12.png)

1. 接下來，點選運算式欄位周圍醒目提示的區域，然後點選「**延伸運算式**」。

   ![write-rules-visual-editor-13](assets/write-rules-visual-editor-13.png)

   在擴展表達式欄位中，從&#x200B;**Select Operator**&#x200B;欄位中選擇&#x200B;**除以**，從&#x200B;**Select Option**&#x200B;欄位中選擇&#x200B;**Number**。 然後，在數字欄位中指定&#x200B;**2**。

   ![write-rules-visual-editor-14](assets/write-rules-visual-editor-14.png)

   >[!NOTE]
   >
   >您可以使用「選取選項」欄位中的元件、函式、數學表達式和屬性值來建立複雜的表達式。

   接下來，建立條件，當傳回True時，運算式會執行。

1. 點選&#x200B;**新增條件**&#x200B;以新增When陳述式。

   ![write-rules-visual-editor-15](assets/write-rules-visual-editor-15.png)

   在When語句中：

   * 從「Forms對象」頁簽中，選擇或拖放第一個&#x200B;**放置對象中的**&#x200B;婚姻狀態&#x200B;**欄位，或選擇此處**&#x200B;欄位。
   * 從&#x200B;**Select Operator**&#x200B;欄位中選擇等於&#x200B;**的i**。
   * 在其他&#x200B;**Drop對象中選擇字串，或選擇此處**&#x200B;欄位，並在&#x200B;**Enter a String**&#x200B;欄位中指定&#x200B;**Fribed**。

   規則編輯器中最後會顯示如下。  ![write-rules-visual-editor-16](assets/write-rules-visual-editor-16.png)

   點選&#x200B;**Done**&#x200B;以儲存規則。

1. 重複步驟7到12，以定義另一個規則，以計算婚姻狀態為「單一」時的貸款資格。 規則編輯器中的規則顯示如下。

   ![write-rules-visual-editor-17](assets/write-rules-visual-editor-17.png)

>[!NOTE]
>
>或者，您也可以使用「設定值」規則來計算「何時」規則中的貸款資格，該規則是您為顯示 — 隱藏「配偶薪金」欄位而建立的。 「婚姻狀態為單一」時產生的組合規則，在規則編輯器中顯示如下。
>
>同樣，您可以編寫一個組合規則，以控制「配偶薪金」欄位的可見性，並在「婚姻狀態」為「已婚」時計算貸款資格。

![write-rules-visual-editor-18](assets/write-rules-visual-editor-18.png)

### 使用代碼編輯器{#using-code-editor}

新增至Forms-power-users群組的使用者可使用程式碼編輯器。 規則編輯器會自動為您使用視覺編輯器建立的任何規則產生JavaScript程式碼。 您可以從視覺編輯器切換至程式碼編輯器，以檢視產生的程式碼。 不過，如果您修改程式碼編輯器中的規則程式碼，則無法切換回視覺編輯器。 如果您偏好在程式碼編輯器中撰寫規則，而非使用視覺化編輯器，則可在程式碼編輯器中重新撰寫規則。 可視化程式碼編輯器切換器可協助您在兩種模式之間切換。

程式碼編輯器JavaScript是最適化表單的運算式語言。 所有運算式都是有效的JavaScript運算式，且會使用最適化表單指令碼模型API。 這些運算式會傳回特定類型的值。 如需適用性表單類別、事件、物件和公用API的完整清單，請參閱適用性表單的[ JavaScript程式庫API參考](https://helpx.adobe.com/experience-manager/6-4/forms/javascript-api/index.html)。

如需在程式碼編輯器中撰寫規則的准則詳細資訊，請參閱[適用性表單運算式](/help/forms/using/adaptive-form-expressions.md)。

在規則編輯器中撰寫JavaScript程式碼時，下列視覺提示可協助您處理結構和語法：

* 語法重點說明
* 自動縮排
* 表單對象、函式及其屬性的提示和建議
* 自動完成表單元件名稱和常見的JavaScript函式

![javascriptrueditor](assets/javascriptruleeditor.png)

#### 規則編輯器{#custom-functions}中的自訂函式

除了列在「函式輸出」下方的*Sum of、*等現成可用函式外，您還可以撰寫您經常需要的自訂函式。 請確定您撰寫的函式上方附有`jsdoc`。

需要附帶`jsdoc`:

* 如果您想要自訂設定和說明。
* 因為在`JavaScript,`中聲明函式有多種方式，而注釋可讓您追蹤函式。

如需詳細資訊，請參閱[usejsdoc.org](https://usejsdoc.org/)。

支援的`jsdoc`標籤：

* **私人**

   語法：`@private`

   私人函式未包含為自訂函式。

* **名稱**

   語法：`@name funcName <Function Name>`

   或者，您也可以使用：`@function funcName <Function Name>` **或** `@func` `funcName <Function Name>`。`,`

   `funcName` 是函式的名稱（不允許使用空格）。

   `<Function Name>` 是函式的顯示名稱。

* **成員**

   語法：`@memberof namespace`

   將命名空間附加到函式。

* **參數**

   語法：`@param {type} name <Parameter Description>`

   或者，您也可以使用：`@argument` `{type} name <Parameter Description>` **或** `@arg` `{type}` `name <Parameter Description>`。

   顯示函式使用的參數。 函式可以有多個參數標籤，每個參數的標籤會依發生順序排列。

   `{type}` 代表參數類型。允許的參數類型為：

   1. 字串
   1. 數字
   1. 布林值

   所有其他參數類型則分為上述其中一個類型。 不支援無。 請確定您選取上述其中一種類型。 類型不區分大小寫。 參數`name`中不允許空格。 `<Parameter Descrption>`

* **傳回類型**

   語法：`@return {type}`

   或者，您也可以使用`@returns {type}`。

   新增函式的相關資訊，例如其目標。

   {type}表示函式的返回類型。 允許的傳回類型包括：

   1. 字串
   1. 數字
   1. 布林值
   1. 日期
   1. 陣列

   所有其他回訪類型則歸入上述其中一個類別。 不支援無。 請確定您選取上述其中一種類型。 傳回類型不區分大小寫。

>[!NOTE]
>
>自訂函式之前的註解會用於摘要。 摘要可延伸至多行，直到遇到標籤為止。 在規則產生器中將大小限制為單一，以取得簡明說明。

**新增自訂函式**

例如，您想要新增自訂函式，以計算平方的面積。 側長是自訂函式的使用者輸入，在表單中使用數值方塊接受。 計算的輸出會顯示在表單中的另一個數值方塊中。 若要新增自訂函式，您必須先建立用戶端程式庫，然後將其新增至CRX存放庫。

執行下列步驟建立用戶端程式庫，並將其新增至CRX存放庫。

1. 建立用戶端程式庫。 如需詳細資訊，請參閱[使用用戶端程式庫](/help/sites-developing/clientlibs.md)。
1. 在CRXDE中，將字串類型值`customfunction`的屬性`categories`新增至`clientlib`資料夾。

   >[!NOTE]
   >
   >`customfunction`是範例類別。您可以為在`clientlib`資料夾中建立的類別選擇任何名稱。

在CRX存放庫中新增用戶端程式庫後，請在最適化表單中使用。 它可讓您將自訂函式當成表單中的規則。 執行下列步驟，在最適化表單中新增用戶端程式庫。

1. 在編輯模式中開啟表單。

   若要在編輯模式中開啟表單，請選取表單並點選&#x200B;**開啟**。

1. 在編輯模式中，選取元件，然後點選![欄位層級](assets/field-level.png) > **適用性表單容器**，然後點選![cmppr](assets/cmppr.png)。
1. 在側欄的「用戶端程式庫名稱」下，新增用戶端程式庫。 （範例中為`customfunction`）。

   ![添加自定義函式客戶端庫](assets/clientlib.png)

1. 選取輸入數值方塊，然後點選![edit-rules](assets/edit-rules.png)以開啟規則編輯器。
1. 點選&#x200B;**建立規則**。 使用下列選項，建立規則以在表單的「輸出」欄位中儲存輸入的平方值。
   [ ![使用自訂函式建立規](assets/add-custom-rule.png)](assets/add-custom-rule-1.png)則點 **選完成**。已新增您的自訂函式。

#### 函式聲明支援的類型{#function-declaration-supported-types}

**函式語句**

```
function area(len) {
    return len*len;
}
```

此函式包含時沒有`jsdoc`注釋。

**函式表達式**

```
var area;
//Some codes later
/** */
area = function(len) {
    return len*len;
};
```

**函式表達式和語句**

```
var b={};
/** */
b.area = function(len) {
    return len*len;
}
```

**函式聲明為變數**

```
/** */
var x1,
    area = function(len) {
        return len*len;
    },
    x2 =5, x3 =true;
```

限制：自訂函式只會從變數清單中挑選第一個函式聲明（若相加）。 您可以對每個已宣告的函式使用函式運算式。

**函式聲明作為對象**

```
var c = {
    b : {
        /** */
        area : function(len) {
            return len*len;
        }
    }
};
```

>[!NOTE]
>
>請務必對每個自訂函式使用`jsdoc`。 雖然建議使用`jsdoc`註解，但請加入空的`jsdoc`註解，將函式標示為自訂函式。 這會啟用自訂函式的預設處理。

## 管理規則{#manage-rules}

當您點選物件並點選![edit-rules1](assets/edit-rules1.png)時，表單物件上的任何現有規則都會列出。 您可以檢視標題並預覽規則摘要。 此外，UI可讓您展開和檢視完整的規則摘要、變更規則的順序、編輯規則和刪除規則。

![清單規則](assets/list-rules.png)

您可以對規則執行下列動作：

* **展開/折疊**:規則清單中的「內容」欄會顯示規則內容。如果預設檢視中未顯示整個規則內容，請點選![expand-rule-content](assets/expand-rule-content.png)以展開它。

* **重新排序**:您建立的任何新規則都會堆疊在規則清單的底部。規則會從上到下執行。 頂端的規則會先執行，接著執行相同類型的其他規則。 例如，如果規則分別位於從上到下的第一個、第二個、第三個和第四個位置的「時間」、「顯示」、「啟用」和「時間」，則頂端的「時間」規則會先執行，而後是第四個位置的「時間」規則。 然後，將執行「顯示」和「啟用」規則。

   您可以點選規則![sort-rules](assets/sort-rules.png)以變更規則的順序，或將其拖曳至清單中的所需順序。

* **編輯**:若要編輯規則，請選取規則標題旁的核取方塊。畫面上會顯示其他編輯和刪除規則的選項。 點選&#x200B;**編輯**&#x200B;以視覺或程式碼編輯器模式，根據用來建立規則的模式，在規則編輯器中開啟選取的規則。

* **刪除**:若要刪除規則，請選取規則並點選「 **刪除**」。

* **啟用/停用**:您可能需要暫時暫停規則的使用。您可以選取一或多個規則，然後點選「動作」工具列中的「停用」以停用這些規則。 如果停用規則，則不會在執行階段執行。 若要啟用已停用的規則，您可以選取該規則，然後點選動作工具列中的「啟用」。 規則的狀態欄會顯示規則已啟用或已停用。

![禁用](assets/disablerule.png)

## 複製貼上規則{#copy-paste-rules}

您可以將規則從一個欄位複製並貼到其他類似欄位，以節省時間。

若要複製貼上規則，請執行下列動作：

1. 點選您要從中複製規則的表單物件，然後在元件工具列中點選![editrule](assets/editrule.png)。 規則編輯器用戶介面隨即出現，並選定了表單對象，現有規則隨即出現。

   ![複製規則](assets/copyrule.png)

   有關管理現有規則的資訊，請參閱[管理規則](/help/forms/using/rule-editor.md#p-manage-rules-p)。

1. 選取規則標題旁的核取方塊。 管理規則的其他選項隨即顯示。 點選「 **複製**」。

   ![copyrule2](assets/copyrule2.png)

1. 選取您要貼上規則的其他表單物件，然後點選「**貼上**」。 此外，您可以編輯規則以進行變更。

   >[!NOTE]
   >
   >只有當該表單物件支援複製規則的事件時，您才能將規則貼到另一個表單物件。 例如，按鈕支援點按事件。 您可以將包含點按事件的規則貼到按鈕，但不貼到核取方塊。

1. 點選&#x200B;**Done**&#x200B;以儲存規則。

## 巢狀運算式 {#nestedexpressions}

規則編輯器可讓您使用多個AND和OR運算子來建立巢狀規則。 您可以在規則中混合使用多個AND和OR運算子。

以下是一個嵌套規則的示例，該規則在滿足所需條件時向用戶顯示有關子女監護資格的消息。

![複合表達](assets/complexexpression.png)

您也可以拖放規則內的條件來加以編輯。 點選並暫留在條件之前的控制滑塊（![控制滑塊](assets/handle.png)）。 一旦指標變成手形符號（如下所示），將條件拖放至規則內的任意位置。 規則結構會變更。

![拖放](assets/drag-and-drop.png)

## 日期運算式條件 {#dateexpression}

規則編輯器可讓您使用日期比較來建立條件。

以下是範例條件，若已取得房屋上的抵押貸款，則會顯示靜態文字物件，使用者會填寫日期欄位，以表示此條件。

當使用者填入的物業抵押日期為過去時，最適化表單會顯示收入計算的相關附註。 以下規則將用戶填寫的日期與當前日期進行比較，如果用戶填寫的日期早於當前日期，則表單將顯示文本消息（名為「收入」）。

![dateexpressioncondition](assets/dateexpressioncondition.png)

當填充日期早於當前日期時，表單將顯示文本消息（收入），如下所示：

![dateexpressionconditionsmet](assets/dateexpressionconditionmet.png)

## 數字比較條件{#number-comparison-conditions}

規則編輯器可讓您建立比較兩個數字的條件。

如果申請者目前住址的月數少於36，以下是顯示靜態文字物件的範例條件。

![numbercomparoncondition](assets/numbercomparisoncondition.png)

當用戶表示他已經在他目前的住宅地址居住了不到36個月時，表格顯示通知，可以請求額外的居住證明。

![請求的additionalproofflows](assets/additionalproofrequested.png)

## 規則編輯器對現有指令碼{#impact-of-rule-editor-on-existing-scripts}的影響

在AEM 6.1 Forms Feature Pack 1之前的AEM Forms版本中，表單作者和開發人員可用來在「編輯」元件對話方塊的「指令碼」索引標籤中撰寫運算式，將動態行為新增至最適化表單。 規則編輯器現在會取代「指令碼」索引標籤。

您必須在「指令碼」索引標籤中撰寫的任何指令碼或運算式，都可在規則編輯器中使用。 雖然您無法在可視化編輯器中檢視或編輯指令碼，但如果您是表單功能使用者群組的成員，則可在程式碼編輯器中編輯指令碼。

## 規則範例 {#example}

### 調用表單資料模型服務 {#invoke}

考慮一個以貸款金額、保有期和申請人的信用評分作為輸入並返回貸款計畫（包括EMI金額和利率）的Web服務`GetInterestRates`。 您可以使用Web服務作為資料源建立表單資料模型。 可將資料模型對象和`get`服務添加到表單模型。 服務會顯示在表單資料模型的「服務」標籤中。 然後，建立包含資料模型物件欄位的最適化表單，以擷取貸款金額、保有權和信用分數的使用者輸入。 新增按鈕以觸發Web服務擷取計畫詳細資訊。 輸出會填入適當欄位。

以下規則顯示如何配置調用服務操作以完成示例方案。

![example-invoke-services](assets/example-invoke-services.png)

### 使用When規則{#triggering-multiple-actions-using-the-when-rule}觸發多個動作

在貸款申請表中，您要獲取貸款申請人是否為現有客戶。 根據使用者提供的資訊，應顯示或隱藏客戶ID欄位。 此外，如果使用者是現有客戶，您也想將焦點設定在客戶ID欄位上。 貸款申請表包含下列部分：

* 選擇鈕&#x200B;**您是現有Geometrixx客戶嗎？**，可提供「是」和「否」選項。「是」的值為&#x200B;**0**，「否」為&#x200B;**1**。

* 文字欄位&#x200B;**Geometrixx客戶ID**，用於指定客戶ID。

在選項按鈕上撰寫「執行時間」規則以實作此行為時，規則會在視覺規則編輯器中顯示如下。  ![when-rule-example](assets/when-rule-example.png)

在範例規則中，When區段中的陳述式為條件，當傳回True時，會執行Then區段中指定的動作。

規則在程式碼編輯器中顯示如下。

![when-rule-example-code](assets/when-rule-example-code.png)

### 在規則{#using-a-function-output-in-a-rule}中使用函式輸出

在採購訂單表單中，您有下表，用戶將在其中填寫訂單。 在下表中：

* 第一列是可重複的，因此使用者可以訂購多個產品並指定不同的數量。 其元素名稱為`Row1`。
* 可重複行的「產品數量」列中的單元格標題為「數量」。 此儲存格的元素名稱為`productquantity`。
* 表格中的第二行是不可重複的，此行中「產品數量」列中的單元格標題為「總數量」。

![example-function-table](assets/example-function-table.png)

**A.** 行1 **B.** 數量 **C.** 總數

現在，您想要在「產品數量」欄中新增所有產品的指定數量，並在「總數量」儲存格中顯示總和。 您可以在「總量」儲存格上撰寫「設定規則值」，如下所示。

![example-function-output](assets/example-function-output.png)

![example-function-output-code](assets/example-function-output-code.png)

### 使用表達式{#validating-a-field-value-using-expression}驗證欄位值

在上例中解釋的採購訂單表單中，您希望限制用戶訂購超過一個數量且定價超過10000的任何產品。 若要這麼做，您可以撰寫驗證規則，如下所示。

![example-validate](assets/example-validate.png)

![example-validate-code](assets/example-validate-code.png)

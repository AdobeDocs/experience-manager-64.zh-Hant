---
title: 建立無障礙的最適化表單
seo-title: Creating accessible adaptive forms
description: AEM Forms提供工具，並協助您建立無障礙的最適化表單，並符合無障礙標準。
seo-description: AEM Forms provides you tools and to create accessible adaptive forms and helps comply with accessibility standards.
uuid: eceb3282-0b90-4e0a-8b89-137d27029747
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 96d9ad52-074b-4084-b818-abce79282776
feature: Adaptive Forms
exl-id: adad26fa-b27a-4bd7-806c-4ddfbaae7a37
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 0%

---

# 建立無障礙的最適化表單 {#creating-accessible-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 簡介 {#introduction}

無障礙表單是每個人都能使用的表單，包括有特殊需求的使用者。 Adobe Experience Manager(AEM)包含許多增強不同功能使用者適用性表單可用性的功能。 此解決方案也協助表單作者建立無障礙的最適化表單。

將協助工具建置至最適化表單中，不僅可讓內容的受眾盡可能廣泛，而且在必須符合協助工具標準的地理位置提供檔案時，也需要這麼做。 AEM Forms可協助表單開發人員遵守無障礙標準。

編寫最適化表單時，作者應考量下列幾點，以建立無障礙的最適化表單：

* 為表單控制項提供適當標籤
* 為影像提供等效文字
* 提供足夠的顏色對比度
* 確保窗體控制項可鍵盤訪問

## 為表單控制項提供適當標籤 {#provide-proper-labels-for-form-controls}

元件的標籤或標題可識別表單元件代表的內容。 例如，文字「名字」會告訴使用者，他們必須在文字欄位中輸入名字。 為了供螢幕閱讀器訪問，標籤以寫程式方式與表單元件相關聯。 或者，表單控制項配置有附加的輔助資訊。

螢幕助讀程式感知的標籤不一定與視覺標題相同。 在某些情況下，您可能會想要更明確地說明控制項的用途。 對於表單中的每個欄位物件，協助工具選項可用來指定螢幕助讀程式要朗讀的內容，以識別特定的表單欄位。

若要使用協助工具選項，請遵循下列步驟：

1. 選取元件並點選 ![cppr](assets/cmppr.png).
1. 按一下 **協助工具** ，選擇所需的協助工具選項。

### 表單元件中的協助工具選項 {#accessibility-options-in-form-components}

![表單元件中的協助工具選項](assets/accessibility-options.png)

**自訂文字** 表單作者會在協助工具選項自訂文字欄位中提供內容。 輔助技術（例如螢幕閱讀器）會使用此自訂文字。 在大多數情況下，使用標題設定是最佳選項。 請考慮僅在無法使用標題或簡短說明時建立自訂螢幕Reader文字。

**簡短說明** 對於大部分元件，當使用者將指標暫留在元件上時，執行階段會顯示簡短說明。 您可以在說明內容選項下的簡短說明欄位中設定此選項。

**標題** 使用此選項，讓AEM Forms將與表單欄位相關聯的視覺標籤作為螢幕助讀程式文字。

**名稱** 您可以在「綁定」頁簽的「名稱」欄位中指定值。 名稱不能包含任何空格。

**無** 選擇「無」會導致已發佈的表單中沒有表單對象的名稱。 表單控制項不建議使用「無」設定。

>[!NOTE]
>
>選項按鈕和核取方塊只能有兩個協助工具選項，即自訂文字和標題。

>[!NOTE]
>
>針對XFA型適用性表單，協助工具選項繼承自XDP中設定的協助工具選項。 XDP提供的工具提示會對應至「簡短說明」，而「註解」會對應至「標題」。 其他選項的運作方式。

## 為影像提供等效文字 {#provide-text-equivalents-for-images}

影像有助於改善某些使用者的理解。 不過，對於使用螢幕助讀程式的使用者，影像會降低表單的協助工具。 如果您選擇使用影像，請為所有影像提供文字說明。

請確定文字以表單說明物件及其用途。 螢幕助讀程式在遇到影像時會讀取此替代文字。 影像必須一律指定替代文字。

選取影像元件並點選 ![cppr](assets/cmppr.png). 在側欄的「屬性」下，指定影像的替代文字。

![影像的替代文字](assets/image-properties.png)

## 提供足夠的顏色對比度 {#provide-sufficient-color-contrast}

協助工具設計需要考慮其他色彩使用准則。 表單作者可以強調顯示各種表單元件，借此使用顏色來改善表單的外觀。 然而，不當使用顏色可能使不同能力的人很難或無法閱讀一種形式。

視力障礙的使用者需要文字與背景之間的高對比度來閱讀數位內容。 如果沒有足夠的對比，某個表單可能會變得很困難，甚至是不可能，讓某些使用者閱讀。

建議您使用預設的字型和背景顏色，即白色背景中的黑色內容。 如果更改預設顏色，請選擇淺色背景顏色的深色前景顏色，或者反之亦然。

請參閱 [建立最適化表單的自訂主題](/help/forms/using/creating-custom-adaptive-form-themes.md)，以取得變更最適化表單的顏色對比和主題的詳細資訊。

## 確保窗體控制項可鍵盤訪問 {#ensure-that-form-controls-are-keyboard-accessible}

只能使用鍵盤或等效的輸入設備來完全填充可訪問的表單。 移動性降低或視力受損的用戶可能別無選擇，只能使用鍵盤，而許多可以使用滑鼠的用戶更喜歡鍵盤輸入。 通過允許使用各種輸入方法，您不僅可以建立可訪問的表單，還可以建立更適合所有用戶偏好的表單。

下列鍵盤快速鍵可在AEM Forms中使用。

| 動作 | 鍵盤快速鍵 |
|---|---|
| 通過表單向前移動游標 | 定位字元 |
| 將游標向後移動到窗體中 | Shift+Tab鍵 |
| 移至下一個面板 | Alt+向右箭頭 |
| 移至上一個面板 | Alt+向左箭頭 |
| 重設表單中填入的資料 | Alt+R |
| 提交表單 | Alt+S | configuring-watched-folder-endpoints.md |

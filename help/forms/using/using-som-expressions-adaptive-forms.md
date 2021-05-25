---
title: 在最適化表單中使用SOM運算式
seo-title: 在最適化表單中使用SOM運算式
description: 了解如何擷取最適化表單面板的SOM運算式。
seo-description: 了解如何擷取最適化表單面板的SOM運算式。
uuid: 4bc80e2a-3563-48a3-996d-021b701bc2ee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 7dff7ef2-80d1-434a-b9b0-ac6654736602
feature: 適用性表單
exl-id: e4680ede-6a02-4b8b-8a6f-9599a05da8e7
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# 在適用性表單{#using-som-expressions-in-adaptive-forms}中使用SOM運算式

適用性表單會模型化為AEM頁面，在AEM存放庫中以JCR內容結構表示。 內容結構的關鍵元素為guideContainer節點。 在guideContainer下方，可能包含巢狀面板和欄位的rootPanel。

可以使用指令碼對象模型(SOM)來參考特定文檔對象模型(DOM)中的值、屬性和方法。 DOM將記憶體對象和屬性組織在樹層次中。 SOM表達式引用欄位/繪製元素和面板。

下圖描述了當您將元件添加到表單時，自適應表單將轉換為的節點結構。 例如，您可以將面板新增至根面板，以及在執行階段轉換為DOM的面板中的選項按鈕。 適用性形式的單選按鈕欄位的SOM運算式指定為`guide[0].guide1[0].guideRootPanel[0].panel1[0].radiobutton[0]`。

![DOM樹](assets/hierarchy-1.png)

適用性表單中任何元素的SOM運算式都會加上前置詞`guide[0].guide1[0]`。 元件在節點結構層次中的位置用於導出其SOM表達式。

![具有兩個單選按鈕的DOM樹](assets/hierarchy_radio_button.png)

當您變更最適化表單中選項按鈕的位置時，SOM運算式會變更。 在創作模式中，可以使用「查看SOM表達式」選項查看AEM Forms中欄位或元素的SOM表達式。 當您以滑鼠右鍵按一下欄位或元素時，選項便會出現在面板上。

![在最適化表單中擷取SOM運算式](assets/som-expressions.png)

在面板內，您可以從面板工具列存取功能。 此功能可協助最適化表單作者編寫指令碼。

![使用面板工具欄提取SOM表達式](assets/som-expression.png)

[GuideBridge](https://helpx.adobe.com/aem-forms/6/javascript-api/GuideBridge.md)中列出的某些API會使用元素的SOM運算式。 例如，若要以最適化表單將焦點放在特定欄位，請將對應的SOM運算式傳遞至`guideBridge`中的`getFocus`API。

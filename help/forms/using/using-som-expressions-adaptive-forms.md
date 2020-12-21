---
title: 在最適化表單中使用SOM表達式
seo-title: 在最適化表單中使用SOM表達式
description: 瞭解如何擷取最適化表單面板的SOM運算式。
seo-description: 瞭解如何擷取最適化表單面板的SOM運算式。
uuid: 4bc80e2a-3563-48a3-996d-021b701bc2ee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 7dff7ef2-80d1-434a-b9b0-ac6654736602
translation-type: tm+mt
source-git-commit: f824b449b85ad7900aaf73fd79614f5e6140f873
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---


# 在最適化表單{#using-som-expressions-in-adaptive-forms}中使用SOM表達式

最適化表單會建模為AEM頁面，在AEM儲存庫中會以JCR內容結構表示。 內容結構的關鍵元素為guideContainer節點。 在guideContainer下方，有rootPanel，其中可能包含巢狀面板和欄位。

可以使用指令碼對象模型(SOM)來引用特定文檔對象模型(DOM)中的值、屬性和方法。 DOM將記憶體對象和屬性組織在樹層次中。 SOM表達式引用欄位／繪製元素和面板。

下圖描述了在向表單添加元件時，自適應表單轉換為的節點結構。 例如，您可以新增面板至根面板，並在面板中新增選項按鈕，在執行時期轉換為DOM。 最適化格式的單選按鈕欄位的SOM表達式指定為`guide[0].guide1[0].guideRootPanel[0].panel1[0].radiobutton[0]`。

![DOM樹](assets/hierarchy-1.png)

自適應形式中任何元素的SOM表達式都由`guide[0].guide1[0]`前置詞。 元件在節點結構層次中的位置用於導出其SOM表達式。

![具有兩個單選按鈕的DOM樹](assets/hierarchy_radio_button.png)

當您在最適化表單中變更選項按鈕的位置時，SOM運算式會變更。 在編寫模式中，您可以使用「檢視SOM運算式」選項，檢視AEM Forms中欄位或元素的SOM運算式。 當您以滑鼠右鍵按一下欄位或元素時，該選項就會出現在面板上。

![在自適應形式中提取SOM表達式](assets/som-expressions.png)

在面板中，您可以從面板工具列存取功能。 此功能可協助最適化表單作者編寫指令碼。

![使用面板工具列擷取SOM運算式](assets/som-expression.png)

[GuideBridge](https://helpx.adobe.com/aem-forms/6/javascript-api/GuideBridge.md)中列出的某些API會使用元素的SOM運算式。 例如，要以自適應形式將焦點放在特定欄位中，請將相應的SOM表達式傳遞到`guideBridge`中的`getFocus`API。


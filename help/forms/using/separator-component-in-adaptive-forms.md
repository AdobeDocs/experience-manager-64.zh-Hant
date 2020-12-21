---
title: 自適應形式中的分隔器元件
seo-title: 自適應形式中的分隔器元件
description: 您可以使用分隔符號元件以視覺化方式分隔表單的區段。
seo-description: 您可以使用分隔符號元件以視覺化方式分隔表單的區段。
uuid: d51c3797-8227-41ed-88cd-c56cc129eb86
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: ba674a2d-7c78-430e-8e17-1a18619e71cb
translation-type: tm+mt
source-git-commit: db4d19e3af11f04369fc7f6a7c13377962f0650a
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---


# 自適應形式{#separator-component-in-adaptive-forms}中的分隔符元件

您可以使用分隔元件以視覺化方式分隔表單的面板。 通過指定分隔符元件的以下屬性，可以定義分隔符元件的整體外觀和樣式：

* **元素名稱：** 指定元件的名稱。SOM表達式用「元素名稱」(Element Name)欄位中指定的值來處理元件。
* **粗細：** 指定分隔符號元件的粗細（以像素為單位）。
* **Colspan：指** 定分隔符號元件所涵蓋的欄數。
* **CSS類：指** 定分隔符號元件的自訂CSS類
* **內嵌樣式：** 有了AEM Forms，您現在可以將內嵌CSS樣式套用至個別的可調式表單元件，並即時預覽變更。

要指定分隔符元件的屬性：

1. 選取分隔符號元件，然後點選![cmppr](assets/cmppr.png)。 屬性會在側欄中開啟。
1. 按一下「內嵌CSS屬性」區段中的標籤，以指定CSS屬性。 例如：a.在「欄位」頁籤中，按一下「添加項目」。 ****&#x200B;將添加一個包含兩個欄位的行。
1. 在左方的第一個欄位中，指定您要套用的CSS3屬性。 例如，**border**。 您也可以按一下向下箭頭按鈕來選取屬性。 下拉式清單並非完整無遺，您可以在此欄位中指定任何支援的CSS3屬性名稱。
1. 在相鄰欄位中，指定指定CSS3屬性的有效值。 例如，**3px純黑**。
1. 按一下「新增項目&#x200B;**」以指定另一個屬性及其值。**
1. 按一下「預覽」，預覽表單中的變更。****
1. 按一下&#x200B;**OK**&#x200B;確認更改，或按一下**取消**退出對話框而不進行任何更改。


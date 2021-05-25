---
title: 'AEM Forms中的預留位置文字 '
seo-title: 'AEM Forms中的預留位置文字 '
description: 預留位置文字旨在在控制項沒有值時，協助使用者輸入資料。 可以是範例值或預期格式的簡短說明。
seo-description: 預留位置文字旨在在控制項沒有值時，協助使用者輸入資料。 可以是範例值或預期格式的簡短說明。
uuid: 553ed988-ad2c-4bdb-bf1e-332e48cf7dfa
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 2d7367fa-6cb8-40a1-8566-1fd0d46fdfde
feature: 適用性表單
exl-id: 26a1a5f7-b4d4-4f38-81a4-5f2d39702138
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 1%

---

# AEM Forms {#placeholder-text-in-aem-forms}中的預留位置文字

佔位符文本表示一個單詞或短片語。 其目的是在控制項沒有值時，協助使用者輸入資料。 預留位置文字可以是範例值或預期格式的簡短說明。 佔位符文本在用戶輸入值之前顯示，在用戶輸入或選擇值時將刪除它。

>[!NOTE]
>
>如果指定，佔位符文本必須具有一個不包含新行字元的值。

![含有和不含預留位置文字的日期元件](assets/dat-picker-place-holder-text.png)

**A.具有** 預留位置文本的日期 **元件B.** 不含預留位置文本的日期元件

「密碼」框、「日期選擇器」、「數值」框和文本框欄位的AEM Forms支援佔位符文本。\
原生HTML5日期介面工具集不支援預留位置文字。 要指定佔位符文本，請執行以下操作：

1. 按一下右鍵支援佔位符文本的元件，然後按一下&#x200B;**Edit**。 將出現「編輯元件」(Edit component)對話框。

1. 開啟&#x200B;**標題和文本**&#x200B;頁簽。
1. 在&#x200B;**預留位置文本框**&#x200B;中指定單詞或短片。 按一下&#x200B;**「確定」**。

>[!NOTE]
>
>Microsoft Internet Explorer 9不支援佔位符文本。

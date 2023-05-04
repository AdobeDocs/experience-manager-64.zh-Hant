---
title: AEM Forms中的預留位置文字
seo-title: Placeholder text in AEM Forms
description: 預留位置文字旨在在控制項沒有值時，協助使用者輸入資料。 可以是範例值或預期格式的簡短說明。
seo-description: Placeholder text is intended to aid the user with data entry when the control has no value. It could be a sample value or a brief description of the expected format.
uuid: 553ed988-ad2c-4bdb-bf1e-332e48cf7dfa
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 2d7367fa-6cb8-40a1-8566-1fd0d46fdfde
feature: Adaptive Forms
exl-id: 26a1a5f7-b4d4-4f38-81a4-5f2d39702138
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 2%

---

# AEM Forms中的預留位置文字 {#placeholder-text-in-aem-forms}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

佔位符文本表示一個單詞或短片語。 其目的是在控制項沒有值時，協助使用者輸入資料。 預留位置文字可以是範例值或預期格式的簡短說明。 佔位符文本在用戶輸入值之前顯示，在用戶輸入或選擇值時將刪除它。

>[!NOTE]
>
>如果指定，佔位符文本必須具有一個不包含新行字元的值。

![含有和不含預留位置文字的日期元件](assets/dat-picker-place-holder-text.png)

**答：** 含預留位置文字的日期元件 **B.** 沒有預留位置文字的日期元件

「密碼」框、「日期選擇器」、「數值」框和文本框欄位的AEM Forms支援佔位符文本。\
原生HTML5日期介面工具集不支援預留位置文字。 要指定佔位符文本，請執行以下操作：

1. 以滑鼠右鍵按一下支援預留位置文字的元件，然後按一下 **編輯**. 將出現「編輯元件」(Edit component)對話框。

1. 開啟 **標題和文字** 標籤。
1. 在 **佔位符文本框**. 按一下&#x200B;**「確定」**。

>[!NOTE]
>
>Microsoft Internet Explorer 9不支援預留位置文字。

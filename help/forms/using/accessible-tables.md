---
title: 在HTML5表單中建立可存取的複雜表格
seo-title: Create accessible complex tables in HTML5 forms
description: 了解如何在HTML5表單中建立無障礙的表格。
seo-description: Learn how to create accessible tables in HTML5 forms.
uuid: e52562d2-4dc3-4359-9dbb-c18614921808
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 3504afe1-abf5-4fbf-a0d2-e093361764bd
feature: Mobile Forms
exl-id: a3337bb1-635c-4dc9-b438-3a829d4a9e03
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 1%

---

# 在HTML5表單中建立可存取的複雜表格 {#create-accessible-complex-tables-in-html-forms}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

HTML5中表格的預設實作Forms會使用HTMLDIV元素來轉譯表格。 演算作業需使用ARIA角色，才能滿足協助工具的需求。

為避免螢幕助讀程式出現無法完全支援資料表使用的ARIA角色的協助工具問題，HTML5 Forms提供表格的替代轉譯。 這些表基於Designer中引入的新表格式，該格式還支援：

* 列標題
* 列跨

若要在HTML5 Forms中使用新格式，請將表格標示為複雜。 若要將表格標示為複雜，請新增 `extras` 標籤，如下所示：

```
</extras>
 <text name="complexTable">1</text>
 </extras>
```

標籤為 *complexTable* 請依照原生HTML轉譯操作，並為特定螢幕助讀程式提供更好的協助工具支援。  若要建立列範圍，請選取同一欄中表格的連續儲存格，按一下滑鼠右鍵選取範圍，然後按一下 **[!UICONTROL 合併儲存格]**.

***注意：**建立列跨只適用於最左側的儲存格。*

若要將列標示為列標題，請選取列中的所有儲存格，在選取項目上按一下滑鼠右鍵，然後按一下 **[!UICONTROL 標籤標題]**.

若要將儲存格標示為欄標題，請選取欄中的任何儲存格，按一下滑鼠右鍵選取範圍，然後按一下 **[!UICONTROL 標籤標題]**.

新 *AccessibleTable* 格式：

* 如果表中使用行範圍，則不支援可增長欄位
* 不支援嵌套表（表單元格內的表）
* 對行跨的支援僅限於標題行和標題單元格
* 支援僅限於常規表
* 不支援以rowspan > 1填入表格

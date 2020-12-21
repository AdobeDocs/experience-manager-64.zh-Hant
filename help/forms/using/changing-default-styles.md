---
title: 變更HTML5表格的預設樣式
seo-title: 變更HTML5表格的預設樣式
description: HTML5表格樣式是以CSS為基礎。 您可以變更表單的預設樣式。
seo-description: HTML5表格樣式是以CSS為基礎。 您可以變更表單的預設樣式。
uuid: dab888b1-d1a9-4990-ab21-96570beafd26
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: a9ab5a78-2add-46e1-a8f2-444d0f25f43a
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---


# 變更HTML5表單的預設樣式{#changing-default-styles-of-html-forms}

HTML5表格會使用HTML5功能來轉譯，而轉譯表格的樣式則會使用CSS來完成。 HTML5表格的預設外觀類似其PDF轉譯。 開發人員可使用自訂CSS來變更HTML5表格的預設外觀。

本文提供變更HTML5表單樣式的逐步資訊，而[樣式簡介](/help/forms/using/css-styles.md)文章包含HTML5表單各樣式方面的詳細資訊。 請務必先閱讀「樣式簡介」，然後再執行本文中提及的步驟。

以下兩張影像顯示預設和自訂樣式之間的差異。

![pictures-002-small](assets/pictures-002-small.png)

## 設定表單的樣式{#style-your-forms}

1. **選擇要新增自訂樣式的描述檔**

   在URL存取CRX DE介面：**https://&lt;server>:&lt;port>/crx/de**&#x200B;並建立描述檔或選擇現有的描述檔。 要瞭解如何建立配置檔案，請參閱[建立新配置檔案](/help/forms/using/custom-profile.md)

1. **建立CSS樣式表以設定HTML5表格的樣式**

   導覽至您已建立描述檔轉譯器的檔案夾，並建立CSS樣式表檔案。 要執行的步驟包括

   1. 按一下右鍵該資料夾，然後從菜單中選擇&#x200B;**create** -> **create File**
   若要瞭解在HTML5表單中為特定元件建立哪些CSS類別，請參閱[樣式簡介](/help/forms/using/css-styles.md)。

1. **在「描述檔轉譯器」中包含樣式表**

   在CRX DE中開啟「描述檔轉譯器」頁面（jsp檔案），並將CSS檔案加入XFA用戶端程式庫正下方的頁面中。 請執行這些步驟，將CSS檔案包含在描述檔中。

   1. 在轉譯器頁面中搜尋下列行：

      &lt;cq:includeclientlib categories=&quot;xfaforms.profile&quot; />

   1. 在上面的行下插入以下內容，以包括樣式表：

      &lt;link href=&quot;/path/to/stylesheet&quot; rel=&quot;stylesheet&quot; type=&quot;text/css&quot; />

   1. 儲存檔案。


---
title: 更改HTML5表單的預設樣式
seo-title: Changing default styles of HTML5 forms
description: HTML5表單樣式是以CSS為基礎。 您可以變更表單的預設樣式。
seo-description: HTML5 forms styling is based on CSS. You can change the default styles of the form.
uuid: dab888b1-d1a9-4990-ab21-96570beafd26
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: a9ab5a78-2add-46e1-a8f2-444d0f25f43a
feature: Mobile Forms
exl-id: 74e54d96-e418-40aa-9b93-561fbdd6312d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 2%

---

# 更改HTML5表單的預設樣式 {#changing-default-styles-of-html-forms}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

HTML5表單是使用HTML5功能呈現，而呈現表單的樣式是使用CSS完成。 HTML5表單的預設外觀與其PDF轉譯類似。 開發人員可使用自訂CSS來變更HTML5表單的預設外觀。

本文提供逐步資訊，以變更HTML5表單的樣式，以及 [樣式簡介](/help/forms/using/css-styles.md) 文章包含有關HTML5表單各種樣式方面的詳細資訊。 請務必先閱讀樣式文章的簡介，再執行本文提及的步驟。

以下兩張影像顯示預設樣式和自訂樣式之間的差異。

![圖片–002 — 小](assets/pictures-002-small.png)

## 設定表單樣式 {#style-your-forms}

1. **選擇要新增自訂樣式的設定檔**

   在URL存取CRX DE介面： **https://&lt;server>:&lt;port>/crx/de** 和建立設定檔或選擇現有設定檔。 若要了解如何建立設定檔，請參閱 [建立新設定檔](/help/forms/using/custom-profile.md)

1. **建立CSS樣式表以設定HTML5表單的樣式**

   導覽至您建立描述檔轉譯器的資料夾，並建立CSS樣式表檔案。 以下步驟為

   1. 以滑鼠右鍵按一下資料夾並選取 **建立** -> **建立檔案** 從功能表
   若要了解要在HTML5表單中為特定元件建立哪些CSS類別，請參閱 [樣式簡介](/help/forms/using/css-styles.md).

1. **在描述檔轉譯器中加入樣式表**

   在CRX DE中開啟「描述檔轉譯器」頁面（jsp檔案），並將CSS檔案包含在XFA用戶端程式庫正下方的頁面中。 執行這些步驟以將CSS檔案包含在設定檔中。

   1. 在轉譯器頁面中搜尋下列行：

      &lt;cq:includeClientLib categories=&quot;xfaforms.profile&quot; />

   1. 在上面的行下插入以下內容以包括樣式表：

      &lt;link href=&quot;/path/to/stylesheet&quot; rel=&quot;stylesheet&quot; type=&quot;text/css&quot;/>

   1. 儲存檔案。

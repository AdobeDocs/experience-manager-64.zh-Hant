---
title: 設計可存取的HTML5表單
seo-title: 設計可存取的HTML5表單
description: HTML5表格使用ARIA HTML5協助工具標準。 這些表單支援標籤式導覽，經認證可與一般螢幕閱讀程式相容。
seo-description: HTML5表格使用ARIA HTML5協助工具標準。 這些表單支援標籤式導覽，經認證可與一般螢幕閱讀程式相容。
uuid: b7757079-5f06-4818-8488-11d67cbe3522
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: ccc59dd5-c0cf-415a-b71a-5bc0cf452ede
feature: 行動表單
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# 設計可存取的HTML5表單{#designing-accessible-html-forms}

HTML5表格使用ARIA HTML5協助工具標準來產生可存取的HTML表格。 這些表單支援標籤式導覽（Mozilla FireFox除外），經認證可與一般螢幕閱讀程式相容。 若要產生具備良好協助功能的HTML5表格，請根據某些[基本設計准則](/help/forms/using/best-practices-for-html5-forms.md)來設計XFA表格範本。 設計准則包括設定正確的標籤順序，以及為每個表單控制項提供「說話文字」內容。 AEM Forms設計人員支援這些表格控制屬性的設定，以產生可存取的PDF和HTML5表格。

*注意：標籤式導覽不涵蓋受保護的欄位，例如顯示值總和的計算欄位。為了讓螢幕閱讀程式讀取受保護欄位的值，請在受保護欄位的上方或旁邊放置一個空的「唯讀」欄位。 將受保護欄位的值指派給新的唯讀欄位。 螢幕閱讀程式或標籤式導覽可以挑選此唯讀欄位，並將它當成受保護欄位的值。*

AEM Forms設計人員包含許多可傳遞給螢幕閱讀程式的「說話文字」選項。 對於表單中的每個對象，用戶可以為螢幕閱讀器文本指定以下幾種設定之一：

* 自訂螢幕閱讀程式文字，可使用「協助工具」浮動視窗來設定。 作者可以註解按鈕和欄位的名稱，以及其用途。
* 工具提示，可在「協助工具」浮動視窗中設定。
* 表單欄位的標題。
* 對象的名稱，如「綁定」頁籤的「名稱」選項中指定。

![協助工具](assets/accessibility.png)

當表單控制項上有多個選項(例如工具提示、螢幕Reader文字和標題)時，螢幕Reader只會使用其中一個屬性。 預設順序為自訂畫面Reader文字、工具提示、標題和名稱。 使用「輔助功能」浮動視窗中的「畫面Reader **優先順序**」選項，您可以覆寫預設順序。

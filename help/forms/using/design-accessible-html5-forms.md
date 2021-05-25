---
title: 設計可存取的HTML5表單
seo-title: 設計可存取的HTML5表單
description: HTML5表單使用ARIA HTML5協助工具標準。 這些表單支援標籤式導覽，經認證可與常見螢幕助讀程式相容。
seo-description: HTML5表單使用ARIA HTML5協助工具標準。 這些表單支援標籤式導覽，經認證可與常見螢幕助讀程式相容。
uuid: b7757079-5f06-4818-8488-11d67cbe3522
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: ccc59dd5-c0cf-415a-b71a-5bc0cf452ede
feature: 行動表單
exl-id: 64d8cf2c-8180-49ce-a725-48cd03476fb8
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# 設計可訪問的HTML5表單{#designing-accessible-html-forms}

HTML5表單使用ARIA HTML5協助工具標準，產生可存取的HTML表單。 這些表單支援頁簽式導覽（Mozilla FireFox除外），經認證可與常見螢幕助讀程式相容。 若要產生具有良好協助工具功能的HTML5表單，請根據某些[基本設計准則](/help/forms/using/best-practices-for-html5-forms.md)來設計XFA表單範本。 設計准則包括配置正確的頁簽順序和為每個表單控制項提供「說話文字」內容。 AEM Forms Designer支援設定這些表單控制項屬性，以產生可存取的PDF和HTML5表單。

*注：標籤式導航不涵蓋受保護的欄位，如顯示值總和的計算欄位。要使螢幕助讀程式讀取受保護欄位的值，請將空的只讀欄位置於受保護欄位的頂部或旁邊。 將受保護欄位的值分配給新的只讀欄位。 螢幕助讀程式或頁簽式導航可以選擇此只讀欄位，並將其作為受保護欄位的值來說明。*

AEM Forms Designer包含許多可傳遞至螢幕助讀程式的「說話文字」選項。 對於表單中的每個物件，使用者可以為螢幕助讀程式文字指定數個設定之一：

* 自訂螢幕助讀程式文字，可使用協助工具浮動視窗來設定。 作者可在按鈕和欄位的名稱及其用途上加上注釋。
* 工具提示，可在協助工具浮動視窗中設定。
* 表單上欄位的註解。
* 對象的名稱，如「綁定」頁簽的「名稱」選項中指定。

![協助工具](assets/accessibility.png)

當表單控制項上有多個選項(如工具提示、螢幕Reader文字和註解)時，螢幕Reader僅使用其中一個屬性。 預設順序為「自訂螢幕Reader文字」、「工具提示」、「註解」和「名稱」。 您可以使用「輔助工具」浮動視窗中的「螢幕Reader **優先**」選項來覆寫預設順序。

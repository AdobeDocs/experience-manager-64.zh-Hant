---
title: 設定國際化選項
seo-title: Setting internationalization options
description: 了解如何指定用於呈現表單的地區，以及如何指定用於編碼輸出流的字元集。
seo-description: Learn how to specify the locale used to render forms and how to specify the character set used to encode the output stream.
uuid: bb77f5f3-634f-4285-9b10-c4dd40085e69
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e845d13f-bef2-442d-af9a-4f92d7616a46
exl-id: 1fb51e4a-e0e8-4a58-8877-98337fe29fac
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 3%

---

# 設定國際化選項{#setting-internationalization-options}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 指定用於呈現表單的區域 {#specify-the-locale-used-to-render-forms}

可以指定在呈現PDF表單時使用的區域設定。 PDF表單上的欄位使用指定的區域設定來顯示資料。 例如，如果地區設定為德文，表單會對數值使用德文小數分隔符號。 語言環境還用於將驗證消息發送到客戶端設備（如Web瀏覽器），作為HTML轉換的一部分。

1. 在管理主控台中，按一下「服務> Forms」。
1. 在「國際化」下，在「語言」清單中，選擇用於呈現表單的區域設定。 預設值為英文（美國）。
1. 按一下「儲存」。

## 指定用於對輸出流編碼的字元集 {#specify-the-character-set-used-to-encode-the-output-stream}

1. 在「國際化」下，在「字元集」清單中，選擇一個字元集。 此設定取決於使用的API，可以是renderHTMLForm或renderPDFForm。 要指定列出的字元集以外的字元集，請選擇「自定義」並在顯示的框中指定編碼值。

   對於HTML轉換，AEM表單支援由 `java.nio.charset` 包。 如果sFormPreference為PDFForm，則僅支援特定字元集。 字元集必須是有效的規範名稱。 預設值為ISO-8859-1。

1. 按一下「儲存」。

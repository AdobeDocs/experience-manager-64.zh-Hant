---
title: 在設計器中更改頁面零內容
seo-title: Changing Page Zero content in Designer
description: 在非Adobe PDF檢視器中檢視時，您知道如何變更XFAPDF的「頁面零」上顯示的訊息？
seo-description: Do you know how you can change the message displayed on Page Zero of an XFA PDF when viewing it in a non-Adobe PDF viewer?
uuid: 5697f203-bb24-437d-a692-bc4bc2609b88
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: f458054e-885c-4c7a-afcd-ad1e4465e0c1
feature: Adaptive Forms
exl-id: 0ae34ddd-9a8d-48df-af2d-80c3fe6abd62
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 3%

---

# 在設計器中更改頁面零內容 {#changing-page-zero-content-in-designer}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

當非Adobe PDF檢視器(例如Chrome或Firefox中的預設PDF檢視器)無法讀取PDF/XFA表單的內容時，依預設會顯示「頁面零」內容。 預設的Page Zero訊息如下所示。

![defaultpage0message](assets/defaultpage0message.png)

AEM Forms Feature Pack 1版設計工具可讓您變更頁面零上顯示的訊息。 要更改「零頁」消息，請執行以下步驟：

1. 確認已安裝AEM Forms Feature Pack 1版Designer。 您可以從設計工具的「關於」畫面中檢查版本。

1. 開啟您要變更「頁面零」內容的表單。

1. 按一下 **檔案>表單屬性**.

1. 在「表單屬性」對話方塊中，按一下 ![plus](assets/plus.png) （加號圖示）以新增自訂屬性。

1. 指定 **_pagezerocontent** 作為屬性的名稱。
1. 以RTF格式新增「頁面零」訊息作為值。 例如：

   `<body xmlns="https://www.w3.org/1999/xhtml" xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/acrreader.</p></body>`

1. 將表單儲存為PDF。

1. 在瀏覽器中檢視PDF表單，確認訊息已更新。 上述範例值顯示如下：

   ![changedmessage](assets/changedmessage.png)

>[!NOTE]
>
>當您重新開啟表單時，您剛建立的自訂屬性可能無法在「表單屬性」對話方塊中正確顯示。 不過，此功能正常運作，表單會顯示更新的「頁面零」訊息。

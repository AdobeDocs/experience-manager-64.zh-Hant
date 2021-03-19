---
title: 在設計人員中變更頁面零內容
seo-title: 在設計人員中變更頁面零內容
description: 您知道在非Adobe PDF檢視器中檢視XFA PDF時，如何變更XFA PDF「零頁」上顯示的訊息？
seo-description: 您知道在非Adobe PDF檢視器中檢視XFA PDF時，如何變更XFA PDF「零頁」上顯示的訊息？
uuid: 5697f203-bb24-437d-a692-bc4bc2609b88
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: f458054e-885c-4c7a-afcd-ad1e4465e0c1
feature: 適用性表單
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 2%

---


# 在Designer {#changing-page-zero-content-in-designer}中更改頁面零內容

當非Adobe PDF檢視器（例如Chrome或Firefox中的預設PDF檢視器）無法讀取PDF/XFA表單的內容時，預設會顯示「零頁」內容。 預設「頁面零」訊息如下所示。

![defaultpage0message](assets/defaultpage0message.png)

AEM FormsFeature Pack 1版的Designer可讓您變更顯示在Page Zero上的訊息。 要更改「零頁」消息，請執行以下步驟：

1. 確定您已安裝AEM Forms功能套件1版設計工具。 您可以從設計人員的「關於」畫面中檢查版本。

1. 開啟您要變更「零頁」內容的表單。

1. 按一下「**檔案>表單屬性**」。

1. 在「表單屬性」對話方塊中，按一下![plus](assets/plus.png)（加號圖示）以新增自訂屬性。

1. 指定&#x200B;**_pagezerocontent**&#x200B;作為屬性的名稱。
1. 以Rich Text格式新增「零頁」訊息為值。 例如：

   `<body xmlns="https://www.w3.org/1999/xhtml" xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/acrreader.</p></body>`

1. 將表單儲存為PDF。

1. 在瀏覽器中檢視PDF表格，確認訊息已更新。 上述範例值顯示如下：

   ![更改消息](assets/changedmessage.png)

>[!NOTE]
>
>當您重新開啟表單時，您剛建立的自訂屬性可能無法正確顯示在「表單屬性」對話方塊中。 不過，它運作正常，而且表單會顯示更新的「零頁」訊息。


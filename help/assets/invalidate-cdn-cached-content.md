---
title: 使 CDN 快取內容失效
seo-title: 使 CDN 快取內容失效
description: 停用您的CDN（內容傳送網路）快取內容可讓您快速更新由Dynamic Media傳送的資產，而不需等待快取過期。
seo-description: 停用您的CDN（內容傳送網路）快取內容可讓您快速更新由Dynamic Media傳送的資產，而不需等待快取過期。
uuid: 0fd88e31-9745-4c98-a245-9f5d0766cad4
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e6c9b50b-c27c-48bf-b3c0-9994e7bf6d7e
exl-id: 335c7a78-a00f-451b-8e53-225830d429c6
feature: Asset Management,CDN Cache
role: Administrator,Business Practitioner,Developer
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 28%

---

# 使 CDN 快取內容失效 {#invalidating-your-cdn-cached-content}

Dynamic Media資產由CDN快取，以便快速傳送。 不過，當您更新資產時，可能會希望這些變更立即生效。 停用您的CDN（內容傳送網路）快取內容可讓您快速更新由Dynamic Media傳送的資產，而不需等待快取過期。

另請參見[Dynamic MediaClassic](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html)中的快取概述。

**若要使CDN快取內容無效：**

1. 登入您的Dynamic Media經典案頭應用程式。

   [Dynamic Media經典案頭應用程式](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html?lang=en#system-requirements-dmc-app)

   您的憑據和登錄是在設定時由Adobe提供的。 如果您沒有此資訊，請聯絡技術支援。

1. 按一 **[!UICONTROL 下「設定>應用程式設定>一般設定」]**。
1. 在「應用程式一般設定」頁面的「伺服器」群組標題下，找到&#x200B;**[!UICONTROL CDN失效範本]**&#x200B;文字方塊。

1. 指定用於使CDN（內容傳送網路）快取失效的範本。

   例如，假設您輸入參照`<ID>`的影像URL（包括影像預設集或修飾元），而不是像下列範例中的特定影像ID:

   `https://server.com/is/image/Company/<ID>?$product$`

   如果範本僅包含`<ID>`，則Dynamic Media填入`https://<server>/is/image`，其中`<server>`是「一般設定」中定義的發佈伺服器名稱，而&lt;ID>是選取無效的資產。

1. 在頁面的右下角，按一下&#x200B;**[!UICONTROL 關閉]**。
1. 在Dynamic MediaClassic案頭應用程式的使用者介面中，選取一或多個資產，然後按一下「檔案>使CDN失效」]**。**[!UICONTROL &#x200B;您會看到一個清單，列出您所建立的範本和選取的資產所產生的一或多個URL。 它使用「應用程式一般設定」下「已發佈伺服器名稱」下所列的伺服器URL。

   例如，在上一步驟中設定「CDN失效範本」時，假設您選取了名為`Backpack_B`的單一影像資產影像。 當您按一下「檔案>使CDN失效」時，會在「CDN失效」使用者介面中產生下列產生的URL:****

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. 在URL清單框中，按一下&#x200B;**[!UICONTROL 繼續]**&#x200B;以清除每個特定URL的快取。 請注意，您可以編輯URL，或是透過輸入或貼入URL清單方塊來新增URL;您不需要事先設定CDN失效範本。

   按一下&#x200B;**[!UICONTROL 繼續]**&#x200B;後，將顯示一個指示器，用於估計清除快取所需的時間。

   如果您選取多個資產，然後按一下「 **[!UICONTROL 檔案>使CDN失效]**」，則儲存的範本URL會參照每個 **[!UICONTROL 資產]**。因此，您可以定義 **[!UICONTROL CDN無效範本]** ，以參考網站上參考的每個URL影像預設集 (例如產品詳細資訊、搜尋結果等)。然後，當您從快取中選取一或影像以進行失效時，URL會自動填入介面。

   >[!NOTE]
   >
   >當您選取資產，然後按一下「檔案 **[!UICONTROL >使CDN無效]**」時，Dynamic media會使用無效的CDN範本，自動建立要使內容傳送網路(CDN)無效的URL。如果「 **[!UICONTROL CDN失效範本」文字方塊中沒有任何項目]** ，則會顯示空白的URL清單。CDN的快取並非以資產為基礎；它是以URL為基礎。因此，您必須注意您網站上的完整URL。在您決定這些URL後，可以在步驟的前面將它們新 **[!UICONTROL 增至「使CDN範本無效]** 」文字方塊。然後，您可以選取這些資產，並在單一步驟中使URL無效。
   >
   >另一個選項是將完整的URL新增至&#x200B;**[!UICONTROL 使CDN]**&#x200B;清單無效。 如果您遵循此方法，在前往「**[!UICONTROL 檔案>使CDN]**」選項之前，不必先在Dynamic MediaClassic中選取資產。

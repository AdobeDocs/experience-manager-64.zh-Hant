---
title: 使 CDN 快取內容失效
seo-title: Invalidating your CDN cached content
description: 使您的CDN（內容傳遞網路）快取內容失效可讓您快速更新由Dynamic Media傳送的資產，而不必等待快取過期。
seo-description: Invalidating your CDN (Content Delivery Network) cached content lets you quickly update assets that are delivered by Dynamic Media, instead of waiting for the cache to expire.
uuid: 0fd88e31-9745-4c98-a245-9f5d0766cad4
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e6c9b50b-c27c-48bf-b3c0-9994e7bf6d7e
exl-id: 335c7a78-a00f-451b-8e53-225830d429c6
feature: Asset Management,CDN Cache
role: Admin,User,Developer
source-git-commit: 0120fe1303aa3b7f5aa7db39eaf40ff127f2e338
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 29%

---

# 使 CDN 快取內容失效 {#invalidating-your-cdn-cached-content}

Dynamic Media資產由CDN快取，以便快速傳遞。 不過，當您更新資產時，可能會希望這些變更立即生效。 使您的CDN（內容傳遞網路）快取內容失效可讓您快速更新由Dynamic Media傳送的資產，而不必等待快取過期。

另請參閱[Dynamic Media Classic](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html)中的快取概觀。

**若要使CDN快取內容無效：**

1. 登入您的Dynamic Media Classic案頭應用程式。

   [Dynamic Media Classic案頭應用程式](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html#system-requirements-dmc-app)

   配置時Adobe提供了您的憑據和登錄。 如果您沒有此資訊，請聯繫技術支援。

1. 按一 **[!UICONTROL 下「設定>應用程式設定>一般設定」]**。
1. 在「應用程式一般設定」頁面的「伺服器」群組標題下，找出&#x200B;**[!UICONTROL CDN無效範本]**&#x200B;文字方塊。

1. 指定用於使CDN（內容傳遞網路）快取失效的範本。

   例如，假設您輸入參考`<ID>`的影像URL（包括影像預設集或修飾元），而非如下列範例所示的特定影像ID:

   `https://server.com/is/image/Company/<ID>?$product$`

   如果範本僅包含`<ID>`，則Dynamic Media會填入`https://<server>/is/image`，其中`<server>`為一般設定中定義的發佈伺服器名稱，而&lt;ID>為選取失效的資產。

1. 在頁面的右下角，按一下&#x200B;**[!UICONTROL Close]**。
1. 在Dynamic Media Classic案頭應用程式的使用者介面中，選取一或多個資產，然後按一下「**[!UICONTROL 檔案>使CDN失效」]**。 您會看到從您建立的範本和您選取的資產產生的一或多個URL清單。 它使用「應用程式一般設定」下「已發佈伺服器名稱」下列的伺服器URL。

   例如，在上一個步驟中設定了「CDN失效範本」後，假設您選取了名為`Backpack_B`的單一影像資產影像。 按一下「**[!UICONTROL 檔案>使CDN無效]**」時，會在CDN無效使用者介面中產生下列URL:

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. 在URL清單方塊中，按一下&#x200B;**[!UICONTROL Continue]**&#x200B;以清除每個特定URL的快取。 請注意，您可以編輯URL，或輸入或貼入URL清單方塊以新增URL;您不需要預先設定CDN無效範本。

   按一下&#x200B;**[!UICONTROL 繼續]**&#x200B;後，將顯示一個指示器，為您提供清除快取所需的時間估計。

   如果您選取多個資產，然後按一下「 **[!UICONTROL 檔案>使CDN失效]**」，則儲存的範本URL會參照每個 **[!UICONTROL 資產]**。因此，您可以定義 **[!UICONTROL CDN無效範本]** ，以參考網站上參考的每個URL影像預設集 (例如產品詳細資訊、搜尋結果等)。然後，當您從快取中選取一或影像以進行失效時，URL會自動填入介面。

   >[!NOTE]
   >
   >當您選取資產，然後按一下「檔案 **[!UICONTROL >使CDN無效]**」時，Dynamic media會使用無效的CDN範本，自動建立要使內容傳送網路(CDN)無效的URL。如果「 **[!UICONTROL CDN失效範本」文字方塊中沒有任何項目]** ，則會顯示空白的URL清單。CDN的快取並非以資產為基礎；它是以URL為基礎。因此，您必須注意您網站上的完整URL。在您決定這些URL後，可以在步驟的前面將它們新 **[!UICONTROL 增至「使CDN範本無效]** 」文字方塊。然後，您可以選取這些資產，並在單一步驟中使URL無效。
   >
   >另一個選項是將完整的URL新增至&#x200B;**[!UICONTROL 使CDN]**&#x200B;清單無效。 如果您依照此方法操作，則不必先在Dynamic Media Classic中選取資產，再前往「**[!UICONTROL 檔案>使CDN失效]**」選項。

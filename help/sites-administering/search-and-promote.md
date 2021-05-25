---
title: 與AdobeSearch&Promote整合
seo-title: 與AdobeSearch&Promote整合
description: 了解如何與AdobeSearch&Promote整合。
seo-description: 了解如何與AdobeSearch&Promote整合。
uuid: ddc4510a-9bd1-4238-a8a8-5f4f563edd8d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 87e62346-98d5-40ec-a3ef-904adf667425
exl-id: 2bbcc8d0-c1c7-4901-836f-44b8a2153a46
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 0%

---

# 與AdobeSearch&amp;Promote整合{#integrating-with-adobe-search-promote}

若要從您的網站呼叫AdobeSearch&amp;Promote服務，請執行下列工作：

1. 指定雲端的URL。
1. 設定與Search&amp;Promote服務的連線。
1. 將Search&amp;Promote元件新增至[!UICONTROL Sidekick]。
1. 使用元件來製作內容。 (請參閱[將Search&amp;Promote功能新增至網頁](/help/sites-authoring/search-and-promote.md)。)
1. 將橫幅新增至您的頁面。 橫幅影像對Search&amp;Promote資料很敏感。
1. 產生要使用的Search&amp;Promote服務的網站地圖。

>[!NOTE]
>
>如果您使用Search&amp;Promote搭配自訂的代理設定，您需要設定兩個HTTP用戶端代理設定，因為AEM的某些功能使用3.x API，而其他一些功能則使用4.x API:
>
>* 3.x的設定為[http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x的設定為[http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)

>



## 變更Search&amp;Promote服務URL {#changing-the-search-promote-service-url}

為Search&amp;Promote服務配置的預設URL為`https://searchandpromote.omniture.com/px/`。 若要使用不同的服務，請使用OSGi主控台來指定不同的URL。

**若要變更Search&amp;Promote服務URL**:

1. 開啟[!UICONTROL OSGi]主控台，然後點選&#x200B;**[!UICONTROL Configuration]**&#x200B;標籤。 ([http://localhost:4502/system/console/configMgr.](http://localhost:4502/system/console/configMgr))

1. 按一下&#x200B;**[!UICONTROL Day CQ Configuration]**&#x200B;項目。
1. 在&#x200B;**[!UICONTROL 遠程伺服器URI]**&#x200B;文本欄位中，輸入URL，然後點選&#x200B;**[!UICONTROL 保存]**。

## 配置與Search&amp;Promote{#configuring-the-connection-to-search-promote}的連接

設定一或多個與Search&amp;Promote的連線，讓您的網頁可與服務互動。 要連接，您需要Search&amp;Promote帳戶的成員標識和帳號。

**若要設定與Search&amp;Promote的連線**:

1. 從&#x200B;**[!UICONTROL 工具]**&#x200B;表徵圖> **[!UICONTROL 部署]**&#x200B;中，選擇&#x200B;**[!UICONTROL Cloud Services]**。

   這會帶您前往「Cloud Services控制面板」。 如果在本機電腦上，控制面板的url將如下所示：

   [http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html)

1. 在[!UICONTROL Cloud Services]頁面中，點選&#x200B;**[!UICONTROL AdobeSearch&amp;Promote]**&#x200B;連結或&#x200B;**[!UICONTROL Search&amp;Promote]**&#x200B;圖示。

1. 如果這是您第一次設定AdobeSearch&amp;Promote，請點選&#x200B;**[!UICONTROL 立即設定]**&#x200B;以開啟[!UICONTROL 建立設定]面板。

   如果您想要進一步了解Search&amp;Promote，請按一下「**[!UICONTROL 深入了解]**」。

   ![chlimage_1-409](assets/chlimage_1-409.png)

1. 輸入頁面作者可辨識的&#x200B;**[!UICONTROL Title]**，然後輸入唯一的&#x200B;**[!UICONTROL Name]**，然後點選&#x200B;**[!UICONTROL Create]**。

   此外，新建立的「配置」將顯示在&#x200B;**[!UICONTROL Cloud Services儀表板]** AdobeSearch&amp;Promote清單項的&#x200B;**[!UICONTROL 可用配置]**&#x200B;下。

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. 在[!UICONTROL 編輯元件]對話方塊中，將下列項目新增至欄位：

   * **[!UICONTROL 成員 ID]**
   * **[!UICONTROL 帳號]**

   >[!NOTE]
   >
   >若要自行取得此資訊，請登入下列項目：
   >
   >[https://searchandpromote.omniture.com/center/](https://searchandpromote.omniture.com/center/)
   >
   >使用有效的Seach&amp;Promote憑證（電子郵件/密碼）。
   >
   >請注意瀏覽器位址列中的URL。 看起來應類似下列：
   >
   >[](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >[https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >其中&#x200B;**XXXXXXX**&#x200B;對應於您的&#x200B;**[!UICONTROL 成員id]**，而&#x200B;**[!UICONTROL spYYYYYYY]**&#x200B;對應於您的帳號。

1. 點選&#x200B;**[!UICONTROL 連線至Search&amp;Promote]**。

   出現連線成功訊息時，點選&#x200B;**[!UICONTROL 確定]**。

   (連接後，按鈕文本將更改為&#x200B;**[!UICONTROL Re-Connect To Search&amp;Promote]**。)

1. 點選&#x200B;**[!UICONTROL 確定]**。 此時會針對您剛建立的組態顯示「Search&amp;Promote設定」頁面。

## 配置資料中心{#configuring-the-data-center}

如果您的Search&amp;Promote帳戶位於亞洲或歐洲，則需要更改預設資料中心，使其指向正確的資料中心（預設資料中心用於北美帳戶）。

**要配置資料中心**:

1. 導覽至`http://localhost:4502/system/console/configMgr/com.day.cq.searchpromote.impl.SearchPromoteServiceImpl`的Web主控台

   ![chlimage_1-411](assets/chlimage_1-411.png)

1. 根據伺服器的位置，將URI更改為以下任一項：

   * 北美：[https://center.atomz.com/px/](https://center.atomz.com/px/)
   * 歐洲、中東和非洲：[https://center.lon5.atomz.com/px/](https://center.lon5.atomz.com/px/)
   * APAC:[https://center.sin2.atomz.com/px/](https://center.sin2.atomz.com/px/)

1. 點選&#x200B;**[!UICONTROL 儲存]**。

## 將Search&amp;Promote元件新增至Sidekick {#adding-search-promote-components-to-sidekick}

在[!UICONTROL Design]模式中，編輯&#x200B;**[!UICONTROL par]**&#x200B;元件以允許[!UICONTROL Sidekick]中的Search&amp;Promote元件。 （如需詳細資訊，請參閱[元件](/help/sites-developing/components.md)檔案）。

有關使用元件的資訊，請參閱[向網頁添加Search&amp;Promote功能](/help/sites-authoring/search-and-promote.md)。

## 指定您的頁面使用{#specifying-the-search-promote-service-that-your-pages-use}的Search&amp;Promote服務

設定網頁，使其使用特定Search&amp;Promote服務。 Search&amp;Promote元件會自動使用其主機頁面的服務。

配置Search&amp;Promote的屬性時，所有子頁都會繼承設定。 如果需要，您可以配置子頁以覆蓋繼承的設定。

>[!NOTE]
>
>必須已配置服務連接。 請參閱[將連線設定為Search&amp;Promote](#configuring-the-connection-to-search-promote)。

1. 開啟&#x200B;**[!UICONTROL 頁面屬性]**&#x200B;對話方塊。 例如，在&#x200B;**[!UICONTROL Websites]**&#x200B;頁面上，以滑鼠右鍵按一下該頁面，然後按一下&#x200B;**[!UICONTROL Properties]**。

1. 按一下&#x200B;**[!UICONTROL Cloud Services]**&#x200B;標籤。

1. 若要停用上層頁面中雲端服務設定的繼承，請按一下繼承路徑旁的掛鎖圖示。

   ![鬆緊遺產掛鎖](assets/sandpinheritpadlock.png)

1. 按一下「**[!UICONTROL 添加服務]**」，選擇「**[!UICONTROL AdobeSearch&amp;Promote]**」，然後按一下「**[!UICONTROL 確定]**」。

1. 選擇Search&amp;Promote帳戶的連接配置，然後按一下&#x200B;**[!UICONTROL 確定]**。

## 產品摘要{#product-feed}

Search&amp;Promote整合可讓您執行下列動作：

* 使用[!UICONTROL eCommerce] API，不受基礎存放庫結構和商務平台影響。
* 運用Search&amp;Promote的[!UICONTROL Index Connector]功能，以XML格式提供產品摘要。
* 運用Search&amp;Promote的[!UICONTROL 遠端控制]功能，執行產品摘要的隨選或排程請求。
* 不同Search&amp;Promote帳戶的摘要產生（設定為雲端服務設定）。

如需詳細資訊，請參閱[產品摘要](/help/sites-administering/product-feed.md)。

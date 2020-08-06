---
title: 與Adobe Search&Promote整合
seo-title: 與Adobe Search&Promote整合
description: 瞭解如何與Adobe Search&Promote整合。
seo-description: 瞭解如何與Adobe Search&Promote整合。
uuid: ddc4510a-9bd1-4238-a8a8-5f4f563edd8d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 87e62346-98d5-40ec-a3ef-904adf667425
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 0%

---


# 與Adobe Search&amp;Promote整合{#integrating-with-adobe-search-promote}

若要從您的網站呼叫Adobe Search&amp;Promote服務，請執行下列工作：

1. 指定雲端的URL。
1. 設定與Search&amp;Promote服務的連線。
1. 將Search&amp;Promote元件新增至 [!UICONTROL Sidekick]。
1. 使用元件來製作內容。 (請參 [閱新增Search&amp;Promote功能至網頁](/help/sites-authoring/search-and-promote.md))。
1. 將橫幅新增至您的頁面。 橫幅影像對Search&amp;Promote資料十分敏感。
1. 產生要使用之Search&amp;Promote服務的網站地圖。

>[!NOTE]
>
>如果您使用Search&amp;Promote與自訂的Proxy設定，則需要設定兩個HTTP Client Proxy設定，因為AEM的某些功能是使用3.x API，而其他部分則使用4.x API:
>
>* 3.x已設定為 [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x已設定為 [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)

>



## 變更Search&amp;Promote服務URL {#changing-the-search-promote-service-url}

為Search&amp;Promote服務設定的預設URL為 `https://searchandpromote.omniture.com/px/`。 若要使用不同的服務，請使用OSGi主控台來指定不同的URL。

**若要變更Search&amp;Promote服務URL**:

1. 開啟 [!UICONTROL OSGi主控台] ，並點選「 **[!UICONTROL Configuration]** 」（設定）標籤。 ([http://localhost:4502/system/console/configMgr.](http://localhost:4502/system/console/configMgr))

1. 按一下 **[!UICONTROL Day CQ Search&amp;Promote設定項目]** 。
1. 在「遠 **[!UICONTROL 程伺服器URI]** 」文本欄位中，輸入URL，然後點選「 **[!UICONTROL 保存」]**。

## 設定與Search&amp;Promote的連線 {#configuring-the-connection-to-search-promote}

設定一或多個與Search&amp;Promote的連線，讓您的網頁可與服務互動。 若要連線，您需要Search&amp;Promote帳戶的成員識別碼和帳號。

**若要設定與Search&amp;Promote的連線**:

1. 從「工 **[!UICONTROL 具]** 」圖示>「 **[!UICONTROL 部署]**」中，選 **[!UICONTROL 取「雲端服務」]**。

   這會帶您前往「雲端服務儀表板」。 如果在本機電腦上，控制面板的URL會如下所示：

   [http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html)

1. 在「 [!UICONTROL Cloud Services] 」頁面中，點選 **[!UICONTROL Adobe Search&amp;Promote]** 連結或 **** Search&amp;Promote圖示。

1. 如果這是您第一次設定Adobe Search&amp;Promote，請點選「立即 **[!UICONTROL 設定]** 」以開啟「  建立設定」面板。

   如果您想要進一步瞭解Search&amp;Promote，請按一下「更 **[!UICONTROL 多資訊]** 」。

   ![chlimage_1-409](assets/chlimage_1-409.png)

1. 輸入頁 **[!UICONTROL 面作者可辨識的標題]** ，然後輸入唯一的 **[!UICONTROL 名稱]**，然後點選「 **[!UICONTROL 建立]**」。

   此外，新建立的「設定」會出現在 **[!UICONTROL 「雲端服務」控制面板]****** 「Adobe Search&amp;Promote」清單項目的「可用設定」下方。

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. 在「編 [!UICONTROL 輯元件] 」對話方塊中，將下列項目新增至欄位：

   * **[!UICONTROL 成員 ID]**
   * **[!UICONTROL 帳號]**

   >[!NOTE]
   >
   >若要自行取得此資訊，請登入下列：
   >
   >[https://searchandpromote.omniture.com/center/](https://searchandpromote.omniture.com/center/)
   >
   >使用您的有效Seach&amp;Promote憑證（電子郵件／密碼）。
   >
   >請注意您瀏覽者位址列中的URL。 其外觀應類似下列：
   >
   >[](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >[https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >其中 **XXXXXXXXX** 與您的 **[!UICONTROL Member id]** , **[!UICONTROL spYYYYYYYY]** 與您的帳號相對應。

1. Tap **[!UICONTROL Connect To Search&amp;Promote]**.

   出現連線成功訊息時，點選「 **[!UICONTROL 確定]**」。

   (連線後，按鈕文字會變 **[!UICONTROL 更為「重新連線至Search&amp;Promote]**」)。

1. 點選「 **[!UICONTROL 確定]**」。 此時會針對您剛建立的組態顯示「Search&amp;Promote設定」頁面。

## 配置資料中心 {#configuring-the-data-center}

如果您的Search&amp;Promote帳戶位於亞洲或歐洲，您必須變更預設資料中心，使其指向正確的資料中心（預設資料中心是北美帳戶的資料中心）。

**要配置資料中心**:

1. 導覽至Web主控台，網址為 `http://localhost:4502/system/console/configMgr/com.day.cq.searchpromote.impl.SearchPromoteServiceImpl`

   ![chlimage_1-411](assets/chlimage_1-411.png)

1. 根據伺服器的位置，將URI更改為以下任一項：

   * 北美洲： [https://center.atomz.com/px/](https://center.atomz.com/px/)
   * EMEA: [https://center.lon5.atomz.com/px/](https://center.lon5.atomz.com/px/)
   * 亞太： [https://center.sin2.atomz.com/px/](https://center.sin2.atomz.com/px/)

1. 點選「 **[!UICONTROL 儲存]**」。

## 將Search&amp;Promote元件新增至Sidekick {#adding-search-promote-components-to-sidekick}

在 [!UICONTROL Design] 模式中，編輯 **[!UICONTROL par]** 元件以允許Sidekick中的Search&amp;Promote [!UICONTROL 元件]。 (See the [Components](/help/sites-developing/components.md) documentation for more information.)

如需使用元件的詳細資訊，請 [參閱新增Search&amp;Promote功能至網頁](/help/sites-authoring/search-and-promote.md)。

## 指定您的頁面所使用的Search&amp;Promote服務 {#specifying-the-search-promote-service-that-your-pages-use}

設定網頁，使其使用特定的Search&amp;Promote服務。 Search&amp;Promote元件會自動使用其主機頁面的服務。

當您設定頁面的Search&amp;Promote屬性時，所有子頁面都會繼承設定。 如有需要，您可以設定子頁面來覆寫繼承的設定。

>[!NOTE]
>
>必須已配置服務連接。 請參 [閱設定與Search&amp;Promote的連線](#configuring-the-connection-to-search-promote)。

1. 開啟「頁 **[!UICONTROL 面屬性]** 」對話方塊。 例如，在「網站 **[!UICONTROL 」頁面]** ，以滑鼠右鍵按一下頁面，然後按一下「屬 **[!UICONTROL 性」]**。

1. 按一下「 **[!UICONTROL 雲端服務]** 」標籤。

1. 要禁用父頁面中雲服務配置的繼承，請按一下繼承路徑旁的掛鎖表徵圖。

   ![松皮繼承鎖](assets/sandpinheritpadlock.png)

1. 按一 **[!UICONTROL 下「新增服務]**」，選 **[!UICONTROL 取「Adobe Search&amp;Promote]**」，然後按一下「 **[!UICONTROL 確定]**」。

1. 選取Search&amp;Promote帳戶的連線設定，然後按一下「確 **[!UICONTROL 定」]**。

## Product Feed {#product-feed}

Search&amp;Promote整合可讓您執行下列動作：

* 使用 [!UICONTROL eCommerce] API，獨立於基礎儲存庫結構和商務平台。
* 運用Search&amp; [!UICONTROL Promote的「索引連接器] 」功能，以XML格式提供產品饋送。
* 運用 [!UICONTROL Search&amp;Promote的「遠端控制] 」功能，執行產品饋送的隨選或排程要求。
* 不同Search&amp;Promote帳戶的動態消息產生，設定為雲端服務設定。

如需詳細資訊，請參閱 [產品摘要](/help/sites-administering/product-feed.md)。

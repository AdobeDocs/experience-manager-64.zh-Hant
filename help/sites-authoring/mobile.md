---
title: 為行動裝置製作頁面
seo-title: Authoring a Page for Mobile Devices
description: 為行動裝置製作內容時，您可以在多個模擬器之間切換，以查看一般使用者所看到的內容
seo-description: When authoring for mobile, you can switch between several emulators to see what the end-user sees
uuid: a7a1ba68-d608-4819-88d1-0dab5955d3f4
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 9554cdb3-b604-4d50-9760-89b9e7a7755f
exl-id: 97f0b0d2-7d7b-4a90-a4e5-348a306e1622
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 1%

---

# 為行動裝置製作頁面{#authoring-a-page-for-mobile-devices}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

製作行動頁面時，頁面的顯示方式會模擬行動裝置。 編寫頁面時，您可以在多個模擬器之間切換，以查看使用者在存取頁面時所看到的內容。

裝置會根據裝置呈現頁面的功能，分組為類別功能、智慧型和觸控。 當使用者存取行動頁面時，AEM會偵測裝置並傳送與其裝置群組對應的表示法。

>[!NOTE]
>
>若要根據現有標準網站建立行動網站，請建立標準網站的即時副本。 (請參閱 [為不同管道建立即時副本](/help/sites-administering/msm-livecopy.md).)
>
>AEM開發人員可以建立新裝置群組。 (請參閱 [建立裝置群組篩選器](/help/sites-developing/groupfilters.md).)

請依照下列程式製作行動頁面：

1. 從全局導航開啟 **網站** 控制台。
1. 開啟頁面 **We.Retail** -> **美國** -> **英文**.

1. 切換至 **預覽** 模式。
1. 按一下頁面頂端的裝置圖示，切換至所需的模擬器。
1. 將元件從元件瀏覽器拖放至頁面。

頁面看起來類似下列：

![mobileipademu](assets/mobileipademu.png)

>[!NOTE]
>
>當從行動裝置要求製作執行個體上的頁面時，模擬器會停用。

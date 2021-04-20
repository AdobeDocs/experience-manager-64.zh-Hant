---
title: 交付Dynamic Media資產
seo-title: 交付Dynamic Media資產
description: 瞭解如何提供動態媒體資產
seo-description: 瞭解如何提供動態媒體資產
uuid: e87754a9-4c34-4658-9971-cd7ceb26523f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: ec394bd3-2fa6-4f50-b974-bc10f643ecac
exl-id: e5110a90-ddc9-4244-8466-f91adfca8469
feature: Asset Management
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 11%

---

# 交付Dynamic Media資產{#delivering-dynamic-media-assets}

如何提供動態媒體資產（視訊和影像）取決於網站的實作方式。

有了Dynamic Media，你有幾種選擇：

* 如果您的網站是裝載AEM在上，則您要直接將動態媒體資產新增至您的頁面。
* 如果您的網站未AEM開啟，您可以選擇：

   * 將您的視訊或影像內嵌在您的網站上。
   * 將URL連結至您的Web應用程式。 當您想要將視訊播放器發佈為快顯視窗或強制視窗時，請使用連結。
   * 如果您的網站回應速度快，您可以[傳送最佳化的影像。](responsive-site.md)

>[!NOTE]
>
>智慧型影像功能可與您現有的影像預設集搭配使用，並在傳送時的最後一毫秒使用智慧功能，根據瀏覽器或網路連線速度進一步降低影像檔案大小。 如需詳細資訊，請參閱[智慧型影像](imaging-faq.md)。

如需詳細資訊，請參閱下列主題：

* [新增Dynamic Media資產至網頁](adding-dynamic-media-assets-to-pages.md)
* [將視訊或影像檢視器內嵌在網頁上](embed-code.md)
* [在 Dynamic Media 中啟用超連結保護](https://helpx.adobe.com/tw/experience-manager/6-4/assets/using/hotlink-protection.html)
* 整合數位非可見浮水印(Digimarc)與Dynamic Media（即將推出）
* [將 URL 連結至您的 Web 應用程式](linking-urls-to-yourwebapplication.md)
* [為回應式網站傳送最佳化影像](responsive-site.md)
* [HTTP2 傳送內容](http2.md)
* [使 CDN 快取內容失效](invalidate-cdn-cached-content.md)
* [使用規則集轉換 URL](using-rulesets-to-transform-urls.md)

## HTTP/2交付Dynamic Media資產{#http-delivery-of-dynamic-media-assets}

現在AEM支援透過HTTP/2傳送所有Dynamic Media內容（影像和視訊）。 也就是說，影像或視訊的已發佈URL或內嵌程式碼可與任何接受代管資產的應用程式整合。 然後，該已發佈資產會透過HTTP/2通訊協定傳送。 這種傳送方式改善了瀏覽器和伺服器通訊的方式，讓所有Dynamic Media資產的回應和載入時間都更佳。

如需詳細資訊，請參閱[HTTP/2內容傳送常見問題](/help/sites-administering/scene7-http2faq.md)。

---
title: 傳送Dynamic Media資產
seo-title: 傳送Dynamic Media資產
description: 了解如何傳送動態媒體資產
seo-description: 了解如何傳送動態媒體資產
uuid: e87754a9-4c34-4658-9971-cd7ceb26523f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: ec394bd3-2fa6-4f50-b974-bc10f643ecac
exl-id: e5110a90-ddc9-4244-8466-f91adfca8469
feature: 資產管理
role: Business Practitioner
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 11%

---

# 傳送Dynamic Media資產{#delivering-dynamic-media-assets}

視訊和影像皆然，您如何傳送動態媒體資產取決於網站的實作方式。

有了Dynamic Media，您有幾個選項：

* 如果您的網站托管於AEM，則您想要直接將動態媒體資產新增至頁面。
* 如果您的網站不在AEM上，您可以選擇：

   * 將您的視訊或影像嵌入網站。
   * 將URL連結至您的Web應用程式。 當您想要以快顯視窗或強制回應視窗的形式傳送視訊播放器時，請使用連結。
   * 如果您的網站回應迅速，您可以[傳送最佳化的影像。](responsive-site.md)

>[!NOTE]
>
>智慧型影像處理可與您現有的影像預設集搭配使用，並會在傳送時的最後毫秒內運用智慧，根據瀏覽器或網路連線速度進一步縮小影像檔案大小。 如需詳細資訊，請參閱[智慧影像](imaging-faq.md)。

如需詳細資訊，請參閱下列主題：

* [將Dynamic Media Assets新增至網頁](adding-dynamic-media-assets-to-pages.md)
* [將視訊或影像檢視器內嵌在網頁上](embed-code.md)
* [在 Dynamic Media 中啟用超連結保護](https://helpx.adobe.com/tw/experience-manager/6-4/assets/using/hotlink-protection.html)
* 整合數位不可見浮水印(Digimarc)與Dynamic Media（即將推出）
* [將 URL 連結至您的 Web 應用程式](linking-urls-to-yourwebapplication.md)
* [為回應式網站傳送最佳化影像](responsive-site.md)
* [HTTP2 傳送內容](http2.md)
* [使 CDN 快取內容失效](invalidate-cdn-cached-content.md)
* [使用規則集轉換 URL](using-rulesets-to-transform-urls.md)

## HTTP/2傳送Dynamic Media資產{#http-delivery-of-dynamic-media-assets}

AEM現在支援透過HTTP/2傳送所有Dynamic Media內容（影像和影片）。 也就是說，影像或視訊的已發佈URL或內嵌程式碼可與接受託管資產的任何應用程式整合。 然後會透過HTTP/2通訊協定來傳送已發佈的資產。 此傳遞方法可改善瀏覽器和伺服器通訊的方式，讓所有Dynamic Media資產的回應和載入時間都更佳。

請參閱[HTTP/2內容傳送常見問題](/help/sites-administering/scene7-http2faq.md)以了解更多資訊。

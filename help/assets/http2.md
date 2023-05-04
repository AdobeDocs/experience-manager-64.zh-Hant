---
title: HTTP2內容傳送
seo-title: HTTP2 Delivery of Content
description: HTTP/2改進了瀏覽器和伺服器的通信方式，允許更快地傳輸資訊，同時降低所需的處理能力。
seo-description: HTTP/2 improves the way browsers and servers communicate, allowing for faster transfer of information while reducing the amount of needed processing power.
uuid: d9deb945-bdf5-4d6b-95c8-8bae4442e618
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: c8e145ad-f021-4043-8190-62151775e296
exl-id: 59cd9f8c-6d01-448d-bf57-bdc9fd2e381b
feature: Asset Management
role: Admin,User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 3%

---

# HTTP2內容傳送 {#http-delivery-of-content}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Adobe 很榮幸宣佈推出有助於提升整體效能的 HTTP/2 內容傳送。

## 什麼是HTTP/2? {#what-is-http}

HTTP/2改進了瀏覽器和伺服器的通信方式，允許更快地傳輸資訊，同時降低所需的處理能力。

以下網站以簡單簡短的方式描述HTTP/2及其優點：

[https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/](https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/)

## 轉移至HTTP/2以進行內容傳送的主要優點為何？ {#what-are-the-key-benefits-of-moving-to-http-for-content-delivery}

效能改善會因網站程式碼、您使用Dynamic Media的方式、消費者裝置、畫面和位置等因素而有所不同。

Adobe自己的測試得出以下結果：

* 針對影像，視裝置和瀏覽器而定，回應時間已改善7%至28%。 效能提升最顯著的是iOS裝置。
* 對於檢視器，載入時間效能提升了15%。

下列示範說明HTTP/1與HTTP/2載入的差異：

[https://http2.akamai.com/demo](https://http2.akamai.com/demo)

## 我是否有資格切換至HTTP/2? {#am-i-eligible-to-switch-over-to-http}

若要使用HTTP/2，您必須符合下列需求：

* 為您的多媒體請求使用安全HTTPS。
* 將Adobe隨附的CDN（內容傳遞網路）作為Dynamic Media授權的一部分。
* 使用專用（非公司 — h.assetsadobe#.com）網域。

   如果您已有專用網域，則可以透過技術支援選擇加入。

   如果您沒有專用網域，Adobe會將您的轉換排程安排在2018年使用HTTP/2。

## 為我的Dynamic Media帳戶啟用HTTP/2的程式為何？ {#what-is-the-process-for-enabling-http-for-my-dynamic-media-account}

您必須啟動切換至HTTP/2的請求；不會自動為您完成。

1. 啟動技術支援請求以切換到HTTP2。 請參閱 [存取客戶支援入口網站](https://helpx.adobe.com/experience-manager/kb/accessing-aem-support-portal.html).

   1. 在您的支援請求中提供下列資訊：

      1. 主要聯繫人姓名、電子郵件、電話。
      1. 要轉換為HTTP2的所有網域。
      1. 確認您是否使用安全HTTPS處理多媒體請求。
      1. 確認您是透過Adobe使用CDN，且不是以直接關係進行管理。
      1. 確認您使用的是專用網域。 如果您使用Dynamic Media，表示您已使用專用網域。
   1. 技術支援會根據提交請求的順序，將您新增至HTTP/2客戶等待清單。
   1. 當Adobe準備好處理您的請求時，支援人員會聯絡您以協調轉變並設定目標日期。
   1. 完成後會收到通知，並可驗證轉換是否成功轉換至HTTP2。

      由於瀏覽器未說明此事實，因此必須下載擴充功能。

      Firefox和Chrome有名為「HTTP/2和SPDY指標」的擴充功能。 瀏覽器僅安全支援http/2，因此必須使用https呼叫URL進行驗證。 如果支援http/2，則會以藍色Flash符號和標題「X-Firefox-Spdy」的形式以擴充功能表示：&quot;h2&quot;。


## 何時可望轉換為HTTP/2? {#when-can-i-expect-to-be-transitioned-over-to-http}

系統會依技術支援接收請求的順序來處理請求。

>[!NOTE]
>
>可能會有很長的前置時間，因為轉換至HTTP/2涉及清除快取。 因此，一次只能處理少數客戶轉變。

## 轉到HTTP/2有什麼風險？ {#what-are-the-risks-with-moving-to-http}

轉換至HTTP/2會清除CDN中的快取，因為它涉及移至新的CDN設定。

非快取內容會直接點擊Adobe的原始伺服器，直到重新建置快取為止。 因此，Adobe計劃一次處理一些客戶轉變，以在從來源提取請求時維持可接受的效能。

## 如何驗證URL或網站是否已透過HTTP/2啟動？ {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

由於瀏覽器未說明此事實，因此必須下載擴充功能。

Firefox和Chrome有名為「HTTP/2和SPDY指標」的擴充功能。 瀏覽器僅安全支援http/2，因此必須使用https呼叫URL進行驗證。 如果支援http/2，則會以藍色Flash符號和標題「X-Firefox-Spdy」的形式以擴充功能表示：&quot;h2&quot;。

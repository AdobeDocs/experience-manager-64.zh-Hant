---
title: 發佈Dynamic Media Assets
description: 如何發佈Dynamic Media資產，包括這些資產的HTTP/2傳送。
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: ebe30c07-1d76-4338-b301-49591f981688
feature: Asset Management
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 9%

---

# 發佈Dynamic Media Assets {#publishing-dynamic-media-assets}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

您可以選取資產並點選，以發佈Dynamic Media資產 **[!UICONTROL 發佈]**. 發佈動態媒體資產後，您就可以透過URL或內嵌方式，將其加入網頁。

您也可以立即發佈上傳的資產，不需任何使用者干預。 請參閱 [設定Dynamic Media - Scene7模式](config-dms7.md).

在「資 **[!UICONTROL 訊卡檢視]**」中，資產名稱正下方會顯示一個小型全球圖示，以指出資產已發佈。在「清 **[!UICONTROL 單檢視]**」中，「已發佈」 **** 欄會指出已發佈或未發佈的資產。

>[!NOTE]
>
>如果資產已發佈，則您可以使用AEM將資產移至其他資料夾，然後從新位置重新發佈，仍可使用原始發佈的資產位置，以及新重新發佈的資產。 但原始已發佈資產「遺失」至AEM，無法取消發佈。 因此，最佳作法是先取消發佈資產，再將其移至其他資料夾。

如果您想在對視訊資產進行編碼後立即發佈，請確定編碼已完成。 當視訊仍在編碼時，系統可讓您知道視訊處理工作流程正在進行中。 完成視訊編碼後，您應該可以預覽視訊轉譯。 此時，您就可以安全地發佈視訊，而不會發生任何發佈錯誤。

另請參閱 [將URL連結至您的Web應用程式](linking-urls-to-yourwebapplication.md).

另請參閱 [將視訊檢視器內嵌在網頁上。](embed-code.md)

>[!NOTE]
>
>* 必須發佈資產才能使用URL。 如果資產未發佈，則複製URL並貼入網頁瀏覽器將無法運作。
>* 必須啟用並發佈影像預設集和檢視器預設集，才能即時傳送。
>


如需發佈集或資產的詳細資訊，請參閱 [發佈資產。](managing-assets-touch-ui.md)

## HTTP/2傳送Dynamic Media資產 {#http-delivery-of-dynamic-media-assets}

AEM現在支援透過HTTP/2傳送所有Dynamic Media內容（影像和影片）。 也就是說，影像或視訊的已發佈URL或內嵌程式碼可與接受託管資產的任何應用程式整合。 然後會透過HTTP/2通訊協定來傳送已發佈的資產。 此傳遞方法可改善瀏覽器和伺服器通訊的方式，讓所有Dynamic Media資產的回應和載入時間都更佳。

請參閱 [HTTP/2傳送內容常見問題](/help/sites-administering/scene7-http2faq.md) 了解更多。

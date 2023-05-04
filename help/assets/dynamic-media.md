---
title: 使用 Dynamic Media
seo-title: Working with Dynamic Media
description: 了解如何使用Dynamic Media來傳送資產，供網站、行動裝置和社交網站使用。
seo-description: Learn how to use Dynamic Media to deliver assets for consumption on web, mobile, and social sites.
uuid: 4dc0f436-d20e-4e8b-aeff-5515380fa44d
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: introduction
content-type: reference
discoiquuid: a8063d43-923a-42ac-9a16-0c7fadd8f73f
exl-id: f8a3936e-82b5-46c7-9614-b97162e27d6a
feature: Asset Management,Renditions
role: Admin,User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 8%

---

# 使用 Dynamic Media {#working-with-dynamic-media}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

[Dynamic Media](https://www.adobe.com/solutions/web-experience-management/dynamic-media.html) 可協助您隨需提供豐富的視覺化銷售和行銷資產，並自動調整規模以供網頁、行動裝置和社交網站使用。 Dynamic Media透過其全球、可擴充、效能最佳化的網路，使用一組主資產即時產生並提供多種多樣化內容變異。

動態媒體提供互動式檢視體驗，包括縮放、360度回轉和視訊。 Dynamic Media獨特地整合了Adobe Experience Manager數位資產管理(Assets)解決方案的工作流程，以簡化和簡化數位行銷活動管理流程。

<!-- DEAD ARTICLE >[!NOTE]
>
>A Community article is available on [Working with Adobe Experience Manager and Dynamic Media](https://helpx.adobe.com/experience-manager/using/aem_dynamic_media.html). -->

## 你能用Dynamic Media做什麼 {#what-you-can-do-with-dynamic-media}

Dynamic Media可讓您在發佈資產之前先管理資產。 如何使用一般資產，將詳細說明 [使用數位資產](managing-assets-touch-ui.md). 一般主題包括上傳、下載、編輯和發佈資產；檢視及編輯屬性，以及搜尋資產。

僅限Dynamic-Media的功能包括：

* [輪播橫幅](carousel-banners.md)
* [影像集](image-sets.md)
* [互動式影像](interactive-images.md)
* [互動式影片](interactive-videos.md)
* [混合媒體集](mixed-media-sets.md)
* [全景影像](panoramic-images.md)

* [迴轉集](spin-sets.md)
* [影片](video.md)
* [傳送Dynamic Media資產](delivering-dynamic-media-assets.md)
* [管理資產](managing-assets.md)
* [使用「快速檢視」建立自訂快顯視窗](custom-pop-ups.md)

另請參閱 [設定Dynamic Media](administering-dynamic-media.md).

>[!NOTE]
>
>若要了解使用Dynamic Media與整合Dynamic Media Classic與AEM之間的差異，請參閱 [Dynamic Media Classic整合與Dynamic Media](/help/sites-administering/scene7.md#aem-scene-integration-versus-dynamic-media).

## Dynamic Media啟用與Dynamic Media停用 {#dynamic-media-on-versus-dynamic-media-off}

您可以借由下列特性來判斷Dynamic Media是否已啟用（開啟）:

* 下載或預覽資產時，可使用動態轉譯。
* 影像集、回轉集、混合媒體集皆可使用。
* 會建立PTIFF轉譯。

當您按一下影像資產時，資產的檢視與Dynamic Media不同 [已啟用](config-dynamic.md#enabling-dynamic-media). Dynamic Media使用隨需HTML5檢視器。

### 動態轉譯 {#dynamic-renditions}

動態轉譯，例如影像和檢視器預設集(位於 **[!UICONTROL 動態]**)即可使用。

![chlimage_1-358](assets/chlimage_1-358.png)

### 影像集，旋轉集，混合媒體集 {#image-sets-spins-sets-mixed-media-sets}

如果已啟用Dynamic Media，則可使用影像集、回轉集和混合媒體集。

![chlimage_1-359](assets/chlimage_1-359.png)

### PTIFF轉譯 {#ptiff-renditions}

啟用Dynamic Media的資產包括 `pyramid.tiffs`.

![chlimage_1-360](assets/chlimage_1-360.png)

### 資產檢視變更 {#asset-views-change}

啟用Dynamic Media後，按一下 `+` 和 `-` 按鈕。 您也可以按一下/點選以放大至特定區域。 還原功能可將您帶到原始版本，您可以按一下對角線箭頭來使影像成為全螢幕。 啟用Dynamic Media的項目如下所示：

![chlimage_1-361](assets/chlimage_1-361.png)

停用Dynamic Media後，您可以放大和縮小並回復成原始大小：

![chlimage_1-362](assets/chlimage_1-362.png)

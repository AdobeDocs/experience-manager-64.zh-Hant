---
title: 自訂和擴充資產
description: 了解您可以透過哪些方式自訂和擴充Asset Share和Asset Editor，為使用者提供量身打造的介面和功能集。
contentOwner: AG
feature: Developer Tools
role: Developer
exl-id: 0291690b-874a-483d-901f-f02cb6d8ab28
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 1%

---

# 自訂和擴充資產 {#customizing-and-extending-assets}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Adobe編輯器是Enterprise Manager網站的使用者用來尋找、檢視和操控存放庫中數位資產的主要存取點。

作為 [!DNL Experience Manager] 開發人員，您可以透過多種方式自訂和擴充資產編輯器，為使用者提供量身打造的介面和一組功能。

可自訂或增強功能的下列方面：

* [擴充資產編輯器](asseteditorx.md)
* [擴充資產搜尋](searchx.md)
* [使用媒體處理常式和工作流程處理資產](media-handlers.md)
* [將資產與活動資料流整合](extending-activity-stream.md)
* [Assets Proxy Development](proxy.md)
* [設定ImageMagick的最佳作法](best-practices-for-imagemagick.md)

## 自訂外觀和風格 {#customizing-the-look-and-feel}

可自訂資產編輯器外觀和風格的下列方面：

* 徽標：您可以將自己組織的標誌新增至介面。
* 顏色和字型：您可以更改介面中使用的顏色和字型。
* HTML代碼：若要進行更徹底的自訂，您可以變更定義介面的基礎HTML程式碼。

## 自訂轉譯 {#customizing-renditions}

在 [!DNL Experience Manager Assets] 術語轉譯是資產呈現的形式。 一般而言，特定資產可能具有多個轉譯。 例如，全彩影像可能具有一個原始大小的格式副本，另一個格式副本具有縮小的大小，而另一個格式副本則同時縮小並轉換為灰度。

您可以自訂特定資產可用的轉譯，並建立新的轉譯。

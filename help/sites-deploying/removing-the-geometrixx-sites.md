---
title: 移除Geometrixx網站
seo-title: Removing the Geometrixx Sites
description: 了解如何移除範例Geometrixx內容。
seo-description: Learn how to remove the sample Geometrixx content.
uuid: 07d20837-3375-4e64-bb07-3e4d10452335
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
discoiquuid: 56761a36-ce21-46e1-856f-75a7e94acae9
exl-id: 495031fb-b559-4071-abc4-93d238ce136d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---

# 移除Geometrixx網站{#removing-the-geometrixx-sites}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

AEM隨附一組範例Geometrixx網站。 您可以透過 **封裝管理員**.

個別geometrixx相關套件包括：

* `cq-geometrixx-outdoors-ugc-pkg-*<version>*.zip`
* `cq-geometrixx-pkg-*<version>*.zip`
* `cq-content-mac-*<version>*.zip`
* `cq-geometrixx-login-pkg-*<version>*.zip`
* `cq-geometrixx-users-pkg-*<version>*.zip`
* `cq-geometrixx-workflow-pkg-*<version>*.zip`
* `cq-geometrixx-outdoors-pkg-*<version>*.zip`
* `cq-geometrixx-commons-pkg-*<version>*.zip`
* `cq-geometrixx-media-pkg-*<version>*.zip`

若要移除個別套件，請按一下「 」即可 **解除安裝** 包上。

此外還有一個超級包：

* `cq-geometrixx-all-pkg-5.6.12.zip`

此套件包含上述所有個別套件。 若要一次移除所有與geometrixx相關的內容，請按一下 **解除安裝** 在這個包裹上。 超級包將進入卸載狀態，所有單個包將從包管理器視圖中消失。

您現在有「空白」AEM例項，沒有任何示範網站。

>[!NOTE]
>
>升級時，會自動重新安裝geometrixx sites。 如果您不想要這些範例，則升級後可能需要移除geometrixx網站。

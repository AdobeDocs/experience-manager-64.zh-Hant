---
title: Content Services
seo-title: Content Services
description: Content Services
seo-description: null
uuid: 7bd09c91-3931-400b-bdfc-b064b9ca9668
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
discoiquuid: 6a7e5472-cb57-4c78-b183-7c6dcac11a4e
exl-id: e900d93e-f7cd-4a0d-a866-7fc6c7882797
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 4%

---

# Content Services{#content-services}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>Adobe建議針對需要單頁應用程式架構用戶端轉譯（例如React）的專案使用SPA編輯器。 [深入了解](/help/sites-developing/spa-overview.md).

>[!CAUTION]
>
>「內容服務」功能僅記錄為預覽用途。
>
>6.3 GA Service Pack 1版可能會有所變更。

AEM Mobile Content Services是輕量型的功能，可要求由AEM管理的內容。 這可讓所有應用程式開發人員以高效能的方式擷取內容，而無須深入了解AEM內容存放庫(JCR)和Web架構(Sling)。 它可讓要求的應用程式與內容存放庫脫鈎。

Content Services引進了數種新的AEM結構，讓開發人員無需了解該內容的儲存庫結構，即可存取AEM管理內容。

這些結構對於保持靈活性和通過在AEM管理內容和使用內容的移動應用之間提供抽象層來支援未來擴展是必要的。 這可讓AEM內容服務在原生應用程式的內容需求和AEM內容存放庫之間，作為抽象層運作。

內容服務可以以資產、封裝HTML(HTML/CSS/JS)或獨立於管道的內容形式提供內容。

>[!CAUTION]
>
>**必備條件:**
>
>開始使用「內容服務」之前，請務必啟用「內容服務」標幟。 若要啟用在應用程式中建立和管理模型，您必須在設定瀏覽器中啟用資料模型。
>
>請參閱 **[管理內容服務](/help/mobile/developing-content-services.md)** 以取得詳細資訊。
>
>請參閱 [設定瀏覽器檔案](/help/sites-administering/configurations.md) 以取得更多資訊。

![chlimage_1-143](assets/chlimage_1-143.png)

在您在設定瀏覽器中設定了「內容服務」標幟並啟用了資料模型後，請參閱以下資源以開始使用AEM Mobile內容服務，熟悉內容服務概念，例如模型管理、實體管理，接著是AEM Mobile內容服務的內容傳送/呈現。

* 儲存庫中的模型
* 轉譯和傳送

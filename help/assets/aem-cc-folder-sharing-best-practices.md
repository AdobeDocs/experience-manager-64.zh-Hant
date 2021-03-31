---
title: 與AEM Assets共用資料夾與Creative Cloud
description: 配置和最佳做法，允許Adobe Experience Manager資產用戶與Adobe Creative Cloud用戶交換資產資料夾。
contentOwner: AG
feature: 協作
role: 業務從業人員，管理員
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 0%

---


# AEMCreative Cloud共用最佳實踐的資料夾{#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>不再AEM提倡「Creative Cloud資料夾共用」功能。 Adobe強烈建議使用較新的功能，例如[Adobe資產連結](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html)或[案頭應用AEM程式](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)。 進一步瞭解[和AEMCreative Cloud整合最佳實踐](/help/assets/aem-cc-integration-best-practices.md)。

Adobe Experience Manager(AEM)可以配置為允許AEM Assets的用戶與Creative Cloud用戶共用資料夾，以便在Creative Cloud資產服務中作為共用資料夾使用。 此功能可用於創意團隊與AEM Assets使用者之間交換檔案，尤其是當創意使用者無法存取AEM Assets例項（他們不在企業網路上）時。

這種整合可用於兩種使用案例，尤其是與沒有直接存取AEM Assets的使用者合作時：

* 與「Creative Cloud檔案」使用者分享AEM Assets的一組特定資產（例如，為新行銷活動設計作品的一組創意簡報和核准資產）
* 從Creative Cloud用戶接收新檔案。

>[!NOTE]
>
>在閱讀本檔案之前，您可以先閱讀整體[AEM和Creative Cloud整合最佳實務](aem-cc-integration-best-practices.md)，以取得主題的更高層次概述。

## 概覽 {#overview}

要AEMCreative Cloud資料夾共用，需要在AEM Assets和Creative Cloud帳戶之間共用資料夾和檔案。 創意專業人員可在其桌上型電腦上使用Creative Cloud案頭應用程式，此外，還可使用Adobe CreativeSync技術，將共用資料夾直接在光碟上提供。

下圖提供整合的概觀。

![chlimage_1-406](assets/chlimage_1-406.png)

整合包含下列元素：

* **AEM Assets** 伺服器部署在企業網路中（受管理服務或內部部署）:資料夾共用會從這裡開始。
* **Adobe Marketing Cloud資產核心服務**:充當與Creative Cloud儲存服AEM務之間的中介。使用整合的公司管理員需要在Marketing Cloud組織與AEM Assets實例之間建立信任關係。 它們還[定義了已批准的Creative Cloud協作者清單](https://experienceleague.adobe.com/docs/core-services/interface/assets/t-admin-add-cc-user.html?lang=en#assets),AEM Assets用戶也可以共用資料夾，以提高安全性。
* **Creative Cloud資產web services** (儲存和Creative Cloud檔案web UI):這是特定的Creative Cloud用戶(與其共用了AEM Assets資料夾)能夠接受邀請並查看其Creative Cloud帳戶儲存中資料夾的位置。
* **Creative Cloud案頭應用程式**:（可選）可讓創意使用者透過與Creative Cloud資產儲存空間同步，從案頭直接存取共用資料夾／檔案。

## 特性和限制{#characteristics-and-limitations}

* **變更的單向傳播：檔案變更只會向單一方向傳播——從系統(或AEMCreative Cloud資產)傳播，該資產原本是建立（上傳）的。** 此整合無法提供兩個系統之間完全自動化的雙向同步。

* **版本設定:**

   * 只AEM有在更新時，才會在檔案產生於並在更新時AEM建立資產版本。
   * Creative Cloud資產提供其專屬的[版本控制功能](https://helpx.adobe.com/creative-cloud/help/versioning-faq.html)，其目標是「進行中的工作」更新（基本上，可將更新儲存長達10天）

* **空間限制：** 檔案交換的大小和數量受創意使用者的特定 [Creative Cloud](https://helpx.adobe.com/creative-cloud/kb/file-storage-quota.html) 資產配額（視訂閱層級而定）和檔案大小上限5GB的限制。此外，該組織在Adobe Marketing Cloud資產核心服務中的資產配額也限制了空間。

* **空間需求：** 共用資料夾中的檔案也必須實際儲存在AEMCreative Cloud帳戶中，然後在Marketing Cloud資產核心服務中使用快取副本。
* **網路和頻寬：** 共用資料夾中的檔案和所有更新都必須透過網路在系統之間傳輸。您應確保僅共用相關檔案和更新。
* **資料夾類型**:不支援共用類型的「資 `sling:OrderedFolder`產」檔案夾。如果要共用資料夾，在AEM Assets建立資料夾時，不要選擇「已訂購」選項。

## 最佳做法{#best-practices}

利用「到Creative Cloud」資料夾共AEM享的最佳做法包括：

* **卷考量：** AEM/Creative Cloud資料夾共用應用於共用較少的檔案，例如與特定促銷活動或活動相關的檔案。若要共用較大的資產集（如組織中所有已核准的資產），請使用其他分發方法(例如AEM Assets品牌入口網站)或案頭應AEM用程式。
* **避免共用深層次：共** 用會以遞歸方式運作，不允許選擇性取消共用。通常，只有沒有子資料夾或具有非常淺層層次的資料夾（如1個子資料夾級別）才應考慮共用。
* **單向共用的個別檔案夾：應使用個別的檔案夾，將最終資產從AEM Assets共用至Creative Cloud檔案，並將創意就緒的資產從Creative Cloud檔案共用回AEM Assets。** 再加上這些資料夾的良好命名慣例，讓AEM Assets和Creative Cloud使用者都能更容易瞭解工作環境。
* **避免在共用資料夾中使用WIP：不應將共用資料夾用於「正在進行的工作」(Work in Progress)-在「Creative Cloud檔案」中使用單獨的資料夾執行需要頻繁更改檔案的工作。** 
* **在共用資料夾之外開始新作品：新設計（創意檔案）應在「Creative Cloud檔案」中的個別WIP資料夾中啟動，當它們準備好與AEM Assets使用者共用時，應將它們移動或儲存至共用資料夾。** 
* **簡化共用結構：** 若要建立更易於管理的作業設定，請考慮簡化共用結構。與其與所有創意使用者共用，AEM Assets資料夾應僅與團隊代表共用，例如創意主管或團隊經理。 創意部門的經理會收到最終資產、決定工作指派，然後讓設計人員在WIP資產的Creative Cloud帳戶中工作。 他們可使用Creative Cloud協作功能來協調工作，最後選擇並放回可共用至AEM Assets的資產，放入可供創意使用的共用資料夾。

下圖說明以AEM Assets現有最終資產為基礎建立新設計的範例設定。

![chlimage_1-407](assets/chlimage_1-407.png)

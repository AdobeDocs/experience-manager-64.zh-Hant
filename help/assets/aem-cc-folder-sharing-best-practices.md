---
title: 與共用AEM Assets資料夾與Creative Cloud
description: 設定和最佳實務，可讓Adobe Experience Manager Assets使用者與Adobe Creative Cloud使用者交換資產資料夾。
contentOwner: AG
feature: Collaboration
role: User,Admin
exl-id: 7e2adfcc-410d-4574-8f7e-39aceecfdd4b
source-git-commit: 0120fe1303aa3b7f5aa7db39eaf40ff127f2e338
workflow-type: tm+mt
source-wordcount: '1059'
ht-degree: 0%

---

# AEM到Creative Cloud資料夾共用最佳實務 {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>不建議使用AEM到Creative Cloud資料夾共用功能。 Adobe強烈建議使用較新的功能，例如[Adobe資產連結](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html)或[AEM案頭應用程式](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)。 進一步了解[AEM和Creative Cloud整合最佳實務](/help/assets/aem-cc-integration-best-practices.md)。

Adobe Experience Manager(AEM)可設定為允許AEM Assets中的使用者與Creative Cloud使用者共用資料夾，以便在Creative Cloud資產服務中以共用資料夾的形式提供。 此功能可用來在創意團隊與AEM Assets使用者之間交換檔案，尤其是當創意使用者無法存取AEM Assets執行個體時（他們不在企業網路上）。

這類整合可用於兩種使用案例，尤其是與沒有直接存取AEM Assets的使用者合作時：

* 與「Creative Cloud檔案」使用者共用AEM Assets的一組特定資產（例如創意簡報和一組已核准資產，以供新行銷活動的設計工作使用）
* 接收Creative Cloud用戶的新檔案。

>[!NOTE]
>
>閱讀本檔案前，您可以先檢閱整體[AEM和Creative Cloud整合最佳實務](aem-cc-integration-best-practices.md)，以了解主題的更高層級概覽。

## 概覽 {#overview}

AEM到Creative Cloud資料夾共用仰賴於AEM Assets帳戶和Creative Cloud帳戶之間，資料夾和檔案的伺服器端共用。 在案頭上使用Creative Cloud案頭應用程式的創意專業人員，可以使用Adobe CreativeSync技術，在其磁碟上直接提供共用資料夾。

下圖提供整合的概觀。

![chlimage_1-406](assets/chlimage_1-406.png)

整合包含下列元素：

* **AEM Assets** 伺服器部署在企業網路中（受管服務或內部部署）:資料夾共用會在此啟動。
* **Adobe Marketing Cloud Assets核心服務**:充當AEM和Creative Cloud儲存服務之間的中介。使用整合之公司的管理員需要在Marketing Cloud組織與AEM Assets例項之間建立信任關係。 它們也[定義已核准Creative Cloud共同作業人員的清單](https://experienceleague.adobe.com/docs/core-services/interface/assets/t-admin-add-cc-user.html#assets),AEM Assets使用者也可以共用資料夾以提供額外安全性。
* **Creative Cloud資產Web服務** (儲存和Creative Cloud檔案Web UI):這是共用AEM Assets資料夾的特定Creative Cloud使用者能夠接受邀請並在其Creative Cloud帳戶儲存體中查看資料夾的位置。
* **Creative Cloud案頭應用程式**:（可選）可透過與Creative Cloud資產儲存空間同步，從創意使用者的案頭直接存取共用資料夾/檔案。

## 特徵和限制 {#characteristics-and-limitations}

* **變更的單向傳播：** 檔案變更只會傳播至一個方向 — 從資產最初建立（上傳）的系統(AEM或Creative Cloud資產)。整合不提供兩個系統之間完全自動化的雙向同步。

* **版本設定:**

   * AEM只會在檔案源自AEM且在該處更新時，建立資產的版本。
   * Creative Cloud資產提供其專屬的[版本化功能](https://helpx.adobe.com/creative-cloud/help/versioning-faq.html)，該功能鎖定在進行中工作更新（基本上，最多可儲存10天的更新）

* **空間限制：** 檔案交換的大小和數量受創意使用 [者特](https://helpx.adobe.com/creative-cloud/kb/file-storage-quota.html) 定Creative Cloud資產配額（視訂閱層級而定）和檔案大小上限5GB的限制。此外，組織在Adobe Marketing Cloud Assets核心服務中的資產配額，也限制了空間。

* **空間需求：** 共用資料夾中的檔案也需實際儲存在AEM中，然後儲存在Creative Cloud帳戶中，並在Marketing Cloud資產核心服務中提供快取副本。
* **網路和頻寬：** 共用資料夾中的檔案和所有更新都需要通過網路在系統之間傳輸。您應確保僅共用相關檔案和更新。
* **資料夾類型**:不支援共用類型的「資 `sling:OrderedFolder`產」資料夾。如果要共用資料夾，在AEM Assets中建立資料夾時，請勿選取「已排序」選項。

## 最佳實務 {#best-practices}

善用AEM來Creative Cloud資料夾共用的最佳實務包括：

* **數量考量：** AEM/Creative Cloud資料夾共用應用來共用較少數量的檔案，例如與特定促銷活動或活動相關的檔案。若要共用較大的資產集（如組織中所有已核准的資產），請使用其他分送方法(例如AEM Assets Brand Portal)或AEM案頭應用程式。
* **避免共用深層階層：** 共用會遞回運作，不允許選擇性取消共用。通常，共用時應僅考慮沒有子資料夾或具有非常淺的層次結構（如1個子資料夾級別）的資料夾。
* **單向共用的個別資料夾：** 應使用個別資料夾來共用最終資產，從AEM Assets共用至Creative Cloud檔案，以及從Creative Cloud檔案將創意就緒的資產共用回AEM Assets。此外，這些資料夾的命名慣例也很好，可為AEM Assets和Creative Cloud使用者建立更容易理解的工作環境。
* **避免在共用資料夾中進行WIP:** 不應將共用資料夾用於進行中的工作 — 在Creative Cloud檔案中使用個別資料夾來執行需要經常變更檔案的工作。
* **在共用資料夾之外開始新工作：** 新設計（創作檔案）應在「Creative Cloud檔案」的個別WIP資料夾中啟動，當它們準備好與AEM Assets使用者共用時，應將其移動或儲存至共用資料夾。
* **簡化共用結構：** 為了提供更方便管理的作業設定，請考慮簡化共用結構。AEM Assets資料夾不應與所有創意使用者共用，而應僅與團隊代表共用，例如創意總監或團隊經理。 創意層的經理將接收最終資產、決定工作分配，然後讓設計師在自己的Creative Cloud帳戶中處理在製品資產。 他們可以使用Creative Cloud協作功能來協調工作，最後選取已準備好要共用回AEM Assets的資產，並將其放入可供創意內容使用的共用資料夾。

下圖說明根據AEM Assets中現有最終資產建立新設計的範例設定。

![chlimage_1-407](assets/chlimage_1-407.png)

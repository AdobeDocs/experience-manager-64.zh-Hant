---
title: 與共用Experience Manager Assets資料夾與Creative Cloud
description: 設定和最佳實務，可讓Adobe Experience Manager Assets使用者與Adobe Creative Cloud使用者交換資產資料夾。
contentOwner: AG
feature: Collaboration
role: User,Admin
exl-id: 7e2adfcc-410d-4574-8f7e-39aceecfdd4b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 0%

---

# [!DNL Experience Manager] to [!DNL Creative Cloud] 資料夾共用最佳作法 {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>不再使用「Creative Cloud資料夾共用」功能的Experience Manager。 Adobe強烈建議使用較新的功能，例如 [Adobe資產連結](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html) 或 [Experience Manager案頭應用程式](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html). 深入了解 [Experience Manager與Creative Cloud整合最佳實務](/help/assets/aem-cc-integration-best-practices.md).

Adobe Experience Manager可經過設定，以允許Experience Manager Assets中的使用者與Creative Cloud使用者共用資料夾，讓這些資料夾可在Creative Cloud資產服務中當作共用資料夾使用。 此功能可用來在創意團隊與Experience Manager Assets使用者之間交換檔案，尤其是當創意使用者無法存取Experience Manager Assets執行個體時（他們不在企業網路上）。

這類整合可用於兩種使用案例，尤其是與沒有直接存取Experience Manager Assets的使用者合作時：

* 與「Creative Cloud檔案」使用者共用Experience Manager Assets的一組特定資產（例如創意簡報和一組已核准資產，以供新行銷活動的設計工作使用）
* 接收Creative Cloud用戶的新檔案。

>[!NOTE]
>
>閱讀本檔案之前，您可以檢閱整體 [Experience Manager與Creative Cloud整合最佳實務](aem-cc-integration-best-practices.md) 以取得主題的更高層級概觀。

## 概觀 {#overview}

Experience Manager到Creative Cloud資料夾共用仰賴於在Experience Manager Assets帳戶和Creative Cloud帳戶之間共用資料夾和檔案的伺服器端。 在案頭上使用Creative Cloud案頭應用程式的創意專業人員，可以使用Adobe CreativeSync技術，在其磁碟上直接提供共用資料夾。

下圖提供整合的概觀。

![chlimage_1-406](assets/chlimage_1-406.png)

整合包含下列元素：

* **[!DNL Assets]伺服器** 部署在企業網路（受管服務或內部部署）中：資料夾共用會在此啟動。
* **Adobe Marketing Cloud Assets核心服務**:充當Experience Manager和Creative Cloud儲存服務之間的中介。 使用整合之公司的管理員需要在Marketing Cloud組織與Experience Manager Assets例項之間建立信任關係。 它們也 [定義已核准的Creative Cloud共同作業人員清單](https://experienceleague.adobe.com/docs/core-services/interface/assets/t-admin-add-cc-user.html#assets)，資產使用者也可以共用資料夾以提供額外安全性。
* **Creative Cloud資產網站服務** (儲存和Creative Cloud檔案Web UI):這是共用「Creative Cloud」資料夾的特定Creative Cloud使用者能夠接受邀請並在其資產帳戶儲存體中查看資料夾的位置。
* **Creative Cloud案頭應用程式**:（可選）可透過與Creative Cloud資產儲存空間同步，從創意使用者的案頭直接存取共用資料夾/檔案。

## 特徵和限制 {#characteristics-and-limitations}

* **更改的單向傳播：** 檔案變更只會傳播至一個方向 — 從資產最初建立（上傳）的系統(Experience Manager或Creative Cloud資產)。 整合不提供兩個系統之間完全自動化的雙向同步。

* **版本設定:**

   * Experience Manager只會在檔案源自Experience Manager且在該處更新時，建立資產的版本。
   * Creative Cloud資產提供專屬 [版本化功能](https://helpx.adobe.com/creative-cloud/help/versioning-faq.html) 此更新針對進行中工作更新（基本上，會儲存最多10天的更新）

* **空間限制：** 交換的檔案的大小和數量受特定 [Creative Cloud資產配額](https://helpx.adobe.com/creative-cloud/kb/file-storage-quota.html) 對於創意使用者（視訂閱層級而定），且檔案大小上限為5GB。 此外，組織在Adobe Marketing Cloud Assets核心服務中的資產配額，也限制了空間。

* **空間需求：** 共用資料夾中的檔案也需實際儲存在Experience Manager中，然後儲存在Creative Cloud帳戶中，且Marketing Cloud資產核心服務會提供快取副本。
* **網路和頻寬：** 共用資料夾中的檔案和所有更新需要通過網路在系統之間傳輸。 您應確保僅共用相關檔案和更新。
* **資料夾類型**:共用類型的「資產」資料夾 `sling:OrderedFolder`不支援。 如果要共用資料夾，在Experience Manager Assets中建立資料夾時，請勿選取「已排序」選項。

## 最佳實務 {#best-practices}

善用Experience Manager來Creative Cloud資料夾共用的最佳實務包括：

* **卷考量事項：** Experience Manager時，「Creative Cloud資料夾共用」應用來共用較少的檔案，例如與特定促銷活動或活動相關的檔案。 若要共用較大的資產集（如組織中所有已核准的資產），請使用其他分送方法(例如Experience Manager Assets Brand Portal)或Experience Manager案頭應用程式。
* **避免共用深層階層：** 共用會遞回運作，不允許選擇性取消共用。 通常，共用時應僅考慮沒有子資料夾或具有非常淺的層次結構（如1個子資料夾級別）的資料夾。
* **將資料夾分開以進行單向共用：** 您應使用個別資料夾，將最終資產從Experience Manager Assets共用至Creative Cloud檔案，以及將創意就緒資產從Creative Cloud檔案共用至 [!DNL Assets]. 此外，這些資料夾的命名慣例也很好，可為Experience Manager Assets和Creative Cloud使用者建立更容易理解的工作環境。
* **避免在共用資料夾中出現WIP:** 共用資料夾不應用於進行中的工作 — 在Creative Cloud檔案中使用單獨的資料夾來執行需要頻繁更改檔案的工作。
* **在共用資料夾之外開始新工作：** 新設計（創作檔案）應在「Creative Cloud檔案」中個別的WIP資料夾中啟動，當它們準備好與Experience Manager Assets使用者共用時，應將其移動或儲存至共用資料夾。
* **簡化共用結構：** 要建立更易於管理的操作設定，請考慮簡化共用結構。 Experience Manager Assets資料夾不應與所有創意使用者共用，而應僅與團隊代表共用，例如創意總監或團隊經理。 創意層的經理將接收最終資產、決定工作分配，然後讓設計師在自己的Creative Cloud帳戶中處理在製品資產。 他們可以使用Creative Cloud協作功能來協調工作，最後選取已準備好要共用回Experience Manager Assets的資產，並將其放入可供創意內容使用的共用資料夾。

下圖說明根據Experience Manager Assets中現有最終資產建立新設計的範例設定。

![chlimage_1-407](assets/chlimage_1-407.png)

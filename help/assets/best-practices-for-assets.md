---
title: 使用AEM管理資產的最佳作法
description: 確定並遵守最佳做法，根據 [!DNL Experience Manager] 資產部署及用於內嵌及處理資產的功能。
contentOwner: AG
feature: Asset Management
role: Architect,Admin
exl-id: e2ab924b-53cb-4011-8c0a-9e8e59dd2f16
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 0%

---

# 最佳實務 [!DNL Experience Manager] 資產 {#best-practices-for-assets}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets是提供高品質數位行銷體驗的重要一環，透過提升內容速度，有助於達成業務目標。 若您在 [!DNL Assets] 或定期/定期上傳許多資產，包括影片和動態媒體，最佳化您的數位資產管理體驗對系統效率至關重要。

視您所定位的 [!DNL Assets] 針對您的組織，以及您用來擷取資產、產生轉譯和擷取中繼資料的功能，識別並遵循不同區域的最佳實務，可大幅增強負載下的系統穩定性和效能。

檢閱下列指南後，您將擁有相關知識和工具，以建立和管理符合您需求的企業資產管理系統。

* [資產效能調整指南](performance-tuning-guidelines.md)
包括一組最佳實務，可在實作中的任何時間點依循，即使在上線後亦然，以確保能充分運用您的系統。
* [資產規模調整指南](assets-sizing-guide.md)
在編製Assets實施的估計值時，務必確保在資產儲存、CPU、記憶體、IO和網路吞吐量方面有足夠的可用資源。 若要調整其中許多項目的大小，必須了解要將多少資產載入系統中。 本指南包括有助於確定用於評估部署所需的基礎架構和資源的有效指標的最佳實踐 [!DNL Experience Manager] 資產和大小調整工具。
* [資產移轉指南](assets-migration-guide.md)
如果您想要將資產從舊版系統移轉至 [!DNL Experience Manager] 資產，有幾個步驟可考慮簡化移轉程式。 移轉指南包含您將資產帶入作業的最佳實務 [!DNL Experience Manager] 按階段進行。 這包括套用中繼資料、產生轉譯，以及啟動資產以發佈部署。
* [資產網路考量事項](assets-network-considerations.md)
處理時 [!DNL Experience Manager] 部署、了解網路拓撲對於了解網路效能、識別中斷點和描述預期的用戶體驗非常重要。 「資產網路考量事項」檔案會在設計您的 [!DNL Experience Manager] 資產部署。
* [Assets監控指南](assets-monitoring-best-practices.md)
在 [!DNL Experience Manager] 部署後，您應監視某些任務和一般系統，以確保系統的完整性和操作的效率。 「監控」指南包含監控系統各個層面的最佳實務。
* （已過時） [資產卸載指南](assets-offloading-best-practices.md)
在中處理大型檔案和執行工作流程 [!DNL Experience Manager] 資產可能會耗用大量CPU、記憶體和I/O資源。 卸載這些任務可以減少CPU、記憶體和IO開銷。 Assets卸載指南包含Assets卸載的建議使用案例和最佳實務。
* [[!DNL Experience Manager] 案頭應用程式最佳作法](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
   [!DNL Experience Manager] 案頭應用程式會將您的數位資產管理(DAM)解決方案與案頭連結，讓您可以開啟 [!DNL Experience Manager] 網頁UI直接放在案頭上。 [!DNL Experience Manager] 案頭應用程式的簡單易用工作流程，採用案頭作業系統提供的網路共用技術。 本指南說明的主要功能，以及建議使用 [!DNL Experience Manager] 案頭應用程式。
* [[!DNL Experience Manager] 和Creative Cloud整合最佳實務](aem-cc-integration-best-practices.md)
您可以整合 [!DNL Experience Manager] 以多種方式Creative Cloud部署。 遵循一些最佳實務來簡化您的整合和資產轉移工作流程，有助於實現最高效率。 本指南包含整合的相關最佳實務 [!DNL Experience Manager] 資產與Adobe Creative Cloud。
* （已過時） [[!DNL Experience Manager] Creative Cloud資料夾共用最佳實務](aem-cc-folder-sharing-best-practices.md)
您可以設定 [!DNL Experience Manager] 允許DAM中的使用者與Creative Cloud使用者共用資料夾，以便在Creative Cloud資產服務中以共用資料夾的形式提供。 此功能可用於創意團隊與DAM使用者之間交換檔案。 本指南說明善用 [!DNL Experience Manager] Creative Cloud資料夾共用功能。

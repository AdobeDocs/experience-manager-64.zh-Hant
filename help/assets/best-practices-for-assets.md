---
title: 使用AEM管理資產的最佳作法
description: 根據AEM Assets部署以及用於擷取和處理資產的功能，識別並遵循可增強負載下系統穩定性和效能的最佳實務。
contentOwner: AG
feature: 資產管理
role: Architect,Admin
exl-id: e2ab924b-53cb-4011-8c0a-9e8e59dd2f16
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 0%

---

# AEM Assets最佳作法 {#best-practices-for-assets}

Adobe Experience Manager(AEM)Assets是提供高品質數位行銷體驗的重要一環，透過提升內容速度，有助於達成業務目標。 如果您在AEM Assets內處理大量資產，或定期/定期上傳許多資產，包括影片和動態媒體，最佳化數位資產管理體驗對於提高系統效率至關重要。

視您為組織定位AEM Assets的方式，以及您在資產擷取、轉譯產生和中繼資料擷取方面所使用的功能而定，在不同區域識別並遵循最佳實務，可大幅增強負載下的系統穩定性和效能。

檢閱下列指南後，您將擁有相關知識和工具，以建立和管理符合您需求的企業資產管理系統。

* [資產效能調](performance-tuning-guidelines.md)
校指南包含一套最佳實務，可在實作的任何時間點依循，即使您上線後亦然，以確保能充分運用您的系統。
* [資產規](assets-sizing-guide.md)
模調整指南在為資產實作編製估計值時，務必確保在資產儲存、CPU、記憶體、IO和網路吞吐量方面有足夠的可用資源。若要調整其中許多項目的大小，必須了解要將多少資產載入系統中。 本指南包含可協助判斷評估部署AEM Assets所需基礎架構和資源之有效量度的最佳實務，以及規模調整工具。
* [資產移](assets-migration-guide.md)
轉指南如果您想要將資產從舊版系統移轉至AEM Assets，請考慮執行數個步驟以簡化移轉程式。移轉指南包含您執行之工作的相關最佳實務，以分階段將資產帶入AEM。 這包括套用中繼資料、產生轉譯，以及啟動資產以發佈部署。
* [Assets網路考](assets-network-considerations.md)
量事項處理AEM部署時，了解網路拓撲對於了解網路效能、識別中斷點和描述預期的用戶體驗至關重要。「Assets網路考量事項」檔案會在設計AEM Asset部署時討論網路考量事項。
* [資產監](assets-monitoring-best-practices.md)
控指南部署AEM後，您應監控特定任務和一般系統，以確保系統的完整性和操作的效率。「監控」指南包含監控系統各個層面的最佳實務。
* （已過時）[資產卸載指南](assets-offloading-best-practices.md)
在AEM Assets中處理大型檔案和執行工作流程可能會耗用大量CPU、記憶體和I/O資源。 卸載這些任務可以減少CPU、記憶體和IO開銷。 Assets卸載指南包含Assets卸載的建議使用案例和最佳實務。
* [AEM案頭應用程](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
式最佳實務AEM案頭應用程式會將您的數位資產管理(DAM)解決方案連結至案頭，讓您可以直接在案頭開啟AEM網頁UI中可用的檔案。AEM案頭應用程式的簡單易用工作流程，是使用案頭作業系統提供的網路共用技術來啟用。 本指南說明AEM案頭應用程式的主要功能及建議使用方式。
* [AEM與Creative Cloud整合最](aem-cc-integration-best-practices.md)
佳實務您可以透過多種方式整合AEM部署與Creative Cloud。遵循一些最佳實務來簡化您的整合和資產轉移工作流程，有助於實現最高效率。 本指南包含有關整合AEM Assets與Adobe Creative Cloud的最佳實務。
* （已廢止）[AEM以Creative Cloud共用最佳實務的資料夾](aem-cc-folder-sharing-best-practices.md)
您可以設定AEM ，讓DAM中的使用者與Creative Cloud(CC)使用者共用資料夾，以便在Creative Cloud資產服務中以共用資料夾的形式提供。 此功能可用於創意團隊與DAM使用者之間交換檔案。 本指南說明運用AEM來Creative Cloud資料夾共用功能的最佳實務。

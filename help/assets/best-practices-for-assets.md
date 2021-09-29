---
title: 使用AEM管理資產的最佳作法
description: 根據 [!DNL Experience Manager] 資產部署和用於資產內嵌和處理的功能，確定並遵守可增強負載下系統穩定性和效能的最佳實踐。
contentOwner: AG
feature: Asset Management
role: Architect,Admin
exl-id: e2ab924b-53cb-4011-8c0a-9e8e59dd2f16
source-git-commit: de5632ff0ee87a4ded88e792b57e818baf4c01a3
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---

# [!DNL Experience Manager]資產的最佳實務 {#best-practices-for-assets}

Adobe Experience Manager Assets是提供高品質數位行銷體驗的重要一環，透過提升內容速度，有助於達成業務目標。 如果您在[!DNL Assets]內處理大量資產，或定期/定期上傳許多資產，包括視訊和動態媒體，最佳化數位資產管理體驗對於提高系統效率至關重要。

根據您為組織定位[!DNL Assets]的方式，以及您用於資產擷取、轉譯產生和中繼資料擷取的功能，識別並遵循不同區域的最佳實務，可大幅增強負載下的系統穩定性和效能。

檢閱下列指南後，您將擁有相關知識和工具，以建立和管理符合您需求的企業資產管理系統。

* [資產效能調](performance-tuning-guidelines.md)
校指南包含一套最佳實務，可在實作的任何時間點依循，即使您上線後亦然，以確保能充分運用您的系統。
* [資產規](assets-sizing-guide.md)
模調整指南在為資產實作編製估計值時，務必確保在資產儲存、CPU、記憶體、IO和網路吞吐量方面有足夠的可用資源。若要調整其中許多項目的大小，必須了解要將多少資產載入系統中。 本指南包含最佳實務，可協助判斷評估[!DNL Experience Manager]資產部署所需基礎架構和資源的有效量度，以及規模調整工具。
* [資產移](assets-migration-guide.md)
轉指南如果您想要將資產從舊版系統移轉至 [!DNL Experience Manager] 資產，請考慮執行數個步驟以簡化移轉程式。移轉指南包含您執行之工作的相關最佳實務，以分階段方式將資產帶入[!DNL Experience Manager]。 這包括套用中繼資料、產生轉譯，以及啟動資產以發佈部署。
* [資產網路](assets-network-considerations.md)
考量事項處 [!DNL Experience Manager] 理部署時，了解網路拓撲對於了解網路效能、識別中斷點和描述預期的用戶體驗至關重要。「資產網路考量事項」檔案會在設計[!DNL Experience Manager]資產部署時討論網路考量事項。
* [資產監](assets-monitoring-best-practices.md)
控指南部 [!DNL Experience Manager] 署後，您應監控特定任務和一般系統，以確保系統的完整性和操作的效率。「監控」指南包含監控系統各個層面的最佳實務。
* （已過時）[資產卸載指南](assets-offloading-best-practices.md)
在[!DNL Experience Manager]資產中處理大型檔案和執行工作流程可能會耗用大量CPU、記憶體和I/O資源。 卸載這些任務可以減少CPU、記憶體和IO開銷。 Assets卸載指南包含Assets卸載的建議使用案例和最佳實務。
* [[!DNL Experience Manager] 案頭應用程式最佳作法](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
   [!DNL Experience Manager] 案頭應用程式會將您的數位資產管理(DAM)解決方案與案頭連結，讓您可以直接在案頭開啟網頁UI [!DNL Experience Manager] 中可用的檔案。[!DNL Experience Manager] 案頭應用程式的簡單易用工作流程，採用案頭作業系統提供的網路共用技術。本指南說明[!DNL Experience Manager]案頭應用程式的主要功能和建議使用。
* [[!DNL Experience Manager] 和Creative Cloud整合最](aem-cc-integration-best-practices.md)
佳實務您可以透過多 [!DNL Experience Manager] 種方式整合部署與Creative Cloud。遵循一些最佳實務來簡化您的整合和資產轉移工作流程，有助於實現最高效率。 本指南包含將[!DNL Experience Manager]資產與Adobe Creative Cloud整合的相關最佳實務。
* （已廢止）[[!DNL Experience Manager] Creative Cloud資料夾共用最佳實務](aem-cc-folder-sharing-best-practices.md)
您可以設定[!DNL Experience Manager] ，讓DAM中的使用者與Creative Cloud(CC)使用者共用資料夾，以便在Creative Cloud資產服務中以共用資料夾的形式使用。 此功能可用於創意團隊與DAM使用者之間交換檔案。 本指南說明運用[!DNL Experience Manager]Creative Cloud資料夾共用功能的最佳實務。

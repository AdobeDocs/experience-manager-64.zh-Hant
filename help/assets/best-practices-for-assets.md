---
title: 使用
description: 根據AEM Assets部署和用於收集和處理資產的功能，確定並遵守可在負載下增強系統穩定性和效能的最佳做法。
contentOwner: AG
feature: 資產管理
role: 架構師，管理員
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 0%

---


# AEM Assets的最佳做法{#best-practices-for-assets}

Adobe Experience Manager(AEM)資產是提供高品質數位行銷體驗的關鍵部分，透過提高內容速度，有助於達成業務目標。 如果您在AEM Assets地區使用大量資產，或定期／定期上傳多個資產，包括視訊和動態媒體，最佳化數位資產管理體驗對系統效率至關重要。

根據您為組織定位AEM Assets的方式，以及您在資產擷取、轉譯產生和中繼資料擷取方面所使用的功能，識別並遵循不同領域的最佳實務可大幅提升負載下的系統穩定性和效能。

在檢閱下列指南後，您將擁有建立和管理符合您需求的企業資產管理系統所需的知識和工具。

* [資產效能調](performance-tuning-guidelines.md)
整指南包含一組最佳實務，可在實作中隨時遵循，即使在您上線後亦然，以確保您充分運用系統。
* [資產規](assets-sizing-guide.md)
模指南在編製資產實作的估計值時，務必確保在資產儲存、CPU、記憶體、IO和網路吞吐量方面有足夠的可用資源。確定其中許多項目的大小需要瞭解系統中要載入多少資產。 本指南包含最佳實務，可協助判斷評估部署AEM Assets所需的基礎架構和資源的有效指標，以及調整規模工具。
* [資產移](assets-migration-guide.md)
轉指南如果您想將資產從舊式系統移轉至AEM Assets，有幾個步驟可考慮簡化移轉程式。移轉指南包含您執行之工作的最佳實務，讓資產以階AEM段的方式運入。 這包括套用中繼資料、產生轉譯，以及啟動資產以發佈部署。
* [資產網](assets-network-considerations.md)
路考量處AEM理部署時，瞭解網路拓撲對於瞭解網路效能、識別阻塞點以及描述預期的使用者體驗非常重要。「資產網路考量事項」檔案會討論設計資產部署時的網AEM路考量事項。
* [資產監](assets-monitoring-best-practices.md)
控指AEM南部署完成後，您應監控特定工作和一般系統，以確保系統的完整性和操作效率。「監控」指南包含監控系統各個方面的最佳實踐。
* （已過時）[資產卸載指南](assets-offloading-best-practices.md)
在AEM Assets處理大型檔案和執行工作流程可能耗用大量CPU、記憶體和I/O資源。 卸載這些任務可以減少CPU、記憶體和IO開銷。 資產卸載指南包含資產卸載的建議使用案例和最佳做法。
* [案頭應AEM用程式最佳範例AEM案頭應用程式會將您的數位資產管理(DAM)解決方案連結至您的案頭，讓您可以直接在案頭上開啟網AEM頁UI中的檔案。](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
案頭AEM應用程式的簡單好用工作流程，是使用案頭作業系統提供的網路共用技術。 本指南說明主要功能以及建議使用案頭應用AEM程式。
* [和AEMCreative Cloud整合最](aem-cc-integration-best-practices.md)
佳實務您可以AEM以多種方式整合部署與Creative Cloud。遵循一些最佳實務，以簡化您的整合與資產轉讓工作流程，協助您達到最高效率。 本指南包含有關將AEM Assets與Adobe Creative Cloud整合的最佳做法。
* （不建議使用）[將共AEM用最佳做法的Creative Cloud資料夾](aem-cc-folder-sharing-best-practices.md)
您可以設AEM定允許DAM中的使用者與Creative Cloud(CC)使用者共用資料夾，以便在Creative Cloud資產服務中以共用資料夾的形式提供。 此功能可用於創意團隊與DAM使用者之間交換檔案。 本指南說明如何運用資料夾共用功AEM能的最佳實務。

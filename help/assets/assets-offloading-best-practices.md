---
title: 資產卸載最佳實務
description: 在 [!DNL Experience Manager] Assets中卸載資產擷取和復寫工作流程的建議使用案例和最佳實務。
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: 3ecc8988-add1-47d5-80b4-984beb4d8dab
source-git-commit: cc6de21180c9fff74f7d64067db82f0c11ac9333
workflow-type: tm+mt
source-wordcount: '1805'
ht-degree: 0%

---

# 資產卸載最佳實務 {#assets-offloading-best-practices}

>[!WARNING]
>
>此功能從[!DNL Experience Manager] 6.4起淘汰，並在[!DNL Experience Manager] 6.5中移除。請據此規劃。

在Adobe Experience Manager Assets中處理大型檔案和執行工作流程可能會耗用大量CPU、記憶體和I/O資源。 尤其是資產的大小、工作流程、使用者人數和資產擷取頻率可能會影響整體系統效能。 耗用最多資源的作業包括資產擷取和復寫工作流程。 在單一製作例項上大量使用這些工作流程可能會對製作效率造成負面影響。

將這些任務卸載到專用的工作實例可以減少CPU、記憶體和IO開銷。 通常，卸載的思想是將佔用大量CPU/記憶體/IO資源的任務分發到專用的工作實例。 以下章節包含資產卸載的建議使用案例。

## [!DNL Experience Manager Assets] 卸載 {#aem-assets-offloading}

[!DNL Experience Manager] Assets會實作原生資產專屬的工作流程擴充功能，以進行卸載。它以卸載架構提供的一般工作流程擴充功能為基礎，但在實施中包含其他資產專屬功能。 「資產」卸載的目標是對上傳的資產執行DAM更新資產工作流程。 資產卸載可讓您進一步控制擷取工作流程。

## [!DNL Experience Manager] 資產卸載元件 {#aem-assets-offloading-components}

下圖描述資產卸載流程中的主要元件：

![chlimage_1-55](assets/chlimage_1-55.png)

### DAM更新資產卸載工作流程 {#dam-update-asset-offloading-workflow}

「DAM更新資產卸載」工作流程會在使用者上傳資產的主要（作者）伺服器上執行。 此工作流程由一般工作流程啟動器觸發。 此卸載工作流程不會處理上傳的資產，而是使用主題&#x200B;*com/adobe/granite/workflow/offloading*&#x200B;建立新作業。 卸載工作流程會新增目標工作流程的名稱，也就是「DAM更新資產」工作流程，以及資產的路徑至工作的裝載。 建立卸載作業後，主實例上的卸載工作流將等待卸載作業運行。

### 工作經理 {#job-manager}

作業管理器將新作業分發給工作實例。 在設計發佈機制時，請務必考慮主題啟用。 只能將作業指派給啟用作業主題的例項。 在主要上禁用主題`com/adobe/granite/workflow/offloading`，並在工作人員上啟用該主題，以確保將該作業分配給該工作人員。

### [!DNL Experience Manager] 卸載 {#aem-offloading}

卸載框架標識分配給工作實例的工作流卸載作業，並使用複製將它們物理地傳輸給工作，包括它們的裝載（例如要捕獲的影像）。

### 工作流程卸載作業使用者 {#workflow-offloading-job-consumer}

在工作人員上寫入作業後，作業管理員會呼叫負責&#x200B;*com/adobe/granite/workflow/offloading*&#x200B;主題的作業使用者。 接著，工作使用者會對資產執行DAM更新資產工作流程。

## Sling拓撲 {#sling-topology}

Sling拓撲將[!DNL Experience Manager]實例分組，使它們能夠彼此感知，而不受基礎持久性的影響。 Sling拓撲的這項特性可讓您為非叢集、叢集和混合情境建立拓撲。 實例可向整個拓撲顯示屬性。 該框架提供用於偵聽拓撲（實例和屬性）中的更改的回調。 Sling拓撲為Sling分佈式作業提供了基礎。

### Sling分佈式作業 {#sling-distributed-jobs}

Sling分佈式作業有助於在作為拓撲成員的一組實例之間分配作業。 Sling作業以功能的概念為基礎。 作業由其作業主題定義。 要運行作業，實例必須為特定作業主題提供作業用戶。 作業主題是分配機制的主要驅動因素。

作業只會分配給為主題提供作業使用者的例項。 通過在實例上啟用/禁用作業使用者，您可以定義實例的功能並影響分發機制。 實例的可用作業用戶被廣播到整個拓撲。

在此情境中，術語分配表示將作業分配給提供作業消費者的特定實例。 執行個體的指派會儲存在存放庫中。 換言之，依預設，Sling分佈式作業可指派給拓撲中的任何例項。 但是，其他作業只能由共用同一儲存庫的實例運行。 這意味著這些作業只能由屬於同一群集的實例運行。 分配給不同群集實例的作業不會運行。

### 花崗岩卸載框架 {#granite-offloading-framework}

Granite卸載架構可補充Sling作業分發，以執行指派給非叢集例項的作業。 它不執行任何分發（實例分配）。 不過，它會識別分發至非叢集例項的Sling作業，並將它們傳輸至目標例項以執行。 目前，卸載使用複製來執行此作業傳輸。 要運行作業，卸載會定義輸入和輸出，然後將其與作業組合以構建作業裝載。

Sling分佈式作業提供作業和分發框架。 Granite卸載只會處理作業分配至非叢集執行個體的特殊情況下的傳輸。

除了傳輸外，卸載框架還為工作流引擎提供了擴展。 它可讓架構在工作流程中建立分散的作業，並等待其完成，然後再推進工作流程。 是使用工作流程引擎的工作流程外部步驟API來實作。 其中一個擴充功能有助於工作流程的一般分發。 不支援分送單一工作流程步驟。

卸載框架還隨附一個用戶介面(UI)，以可視化並控制整個拓撲中啟用的作業主題。 UI可讓您輕鬆設定Sling分散作業的主題啟用。 您也可以在不使用UI的情況下設定卸載。

## 資產卸載的一般指引和最佳作法 {#general-guidance-and-best-practices-for-asset-offloading}

每個實作都是唯一的，因此沒有一刀切的卸載設定。 以下章節提供資產擷取卸載的相關指引和最佳實務。

資產卸載還會對系統施加間接費用，包括操作間接費用。 如果您遇到資產擷取載入的問題，Adobe建議您先改善設定，而不要卸載。 移至資產卸載前，請考慮下列選項：

* 擴展硬體
* 最佳化工作流程
* 使用暫時性工作流程
* 限制用於工作流的核心數量

如果您認為資產卸載是適合您的方法，Adobe會提供下列指引：

* 建議使用TarMK型部署
* 以TarMK為基礎的資產卸載並非專為大規模橫向擴展而設計
* 確保作者與工作人員之間的網路效能令人滿意

### 建議的資產卸載部署 {#recommended-assets-offloading-deployment}

若使用[!DNL Experience Manager]和Oak，可能有數個部署案例。 若為資產卸載，建議使用共用資料存放區的TarMK型部署。 下圖概述建議的部署：

![chlimage_1-56](assets/chlimage_1-56.png)

如需設定資料存放區的詳細資訊，請參閱[設定AEM](../sites-deploying/data-store-config.md)中的節點存放區和資料存放區。

### 關閉自動代理管理 {#turning-off-automatic-agent-management}

Adobe建議您關閉自動代理管理，因為它不支援無二進位複製，在設定新的卸載拓撲時可能會造成混淆。 此外，它不會自動支援無二進位複製所需的正向複製流。

1. 從URL `http://localhost:4502/system/console/configMgr`開啟Configuration Manager。
1. 開啟`OffloadingAgentManager`(`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingAgentManager`)的配置。
1. 禁用自動代理管理。

### 使用正向複製 {#using-forward-replication}

預設情況下，卸載傳輸使用反向複製將卸載的資產從工作器拉回到主伺服器。 反向複製代理不支援無二進位複製。 您應將卸載配置為使用轉發複製將卸載的資產從工作器推回主伺服器。

1. 如果您使用反向複製從預設配置遷移，請禁用或刪除主和工作器上名為「 `offloading_outbox`」和「 `offloading_reverse_*`」的所有代理，其中&amp;ast;代表target例項的Sling id。
1. 在每個工作器上，建立指向主工作器的新轉發複製代理。 該過程與從主代理到工作代理建立轉發代理相同。 有關設定卸載複製代理的說明，請參閱[建立卸載的複製代理](../sites-deploying/offloading.md#creating-replication-agents-for-offloading)。
1. 開啟`OffloadingDefaultTransporter`(`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter`)的配置。
1. 將屬性`default.transport.agent-to-master.prefix`的值從`offloading_reverse`變更為`offloading`。

<!-- TBD: Make updates to the configuration for allow and block list after product updates are done.
TBD: Update the property in the last step when GRANITE-30586 is fixed.
-->

### 在作者和背景工作之間使用共用資料存放區和無二進位復寫  {#using-shared-datastore-and-binary-less-replication-between-author-and-workers}

建議使用無二進位檔復寫，以減少資產卸載的傳輸開銷。 若要了解如何為共用資料存放區設定無二進位檔復寫，請參閱[在AEM](/help/sites-deploying/data-store-config.md)中設定節點存放區和資料存放區。 資產卸載的程式並不不同，只是涉及其他復寫代理。 因為無二進位複製只與轉發複製代理一起使用，因此您也應對所有卸載代理使用轉發複製。

### 關閉運輸包 {#turning-off-transport-packages}

依預設，卸載會建立包含卸載作業和作業裝載（原始資產）的內容包，並使用單一復寫請求傳輸此單一卸載包。 使用無二進位檔的復寫時，建立這些卸載套件會產生反作用，因為在建立套件時，會將二進位檔序列化至套件中。 可以關閉這些傳輸包的使用，這會導致卸載作業和負載在多個複製請求中傳輸，每個有效負載條目各一個。 這樣，就可以利用無二進位複製的好處。

1. 在[http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter](http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter)開啟&#x200B;*OffloadingDefaultTransporter*&#x200B;元件的元件配置
1. 禁用屬性&#x200B;*複製包(default.transport.contentpackage)*。

### 禁用工作流模型的傳輸 {#disabling-the-transport-of-workflow-model}

依預設，*DAM更新資產卸載*&#x200B;卸載工作流程會新增要在背景工作上呼叫的工作流程模型至工作裝載。 由於此工作流程預設會遵循現成可用的&#x200B;*DAM更新資產*&#x200B;模型，因此可以移除此額外的裝載。

如果從作業裝載中停用工作流模型，請務必使用其他工具（例如封裝管理器）將變更分發至參考的工作流模型。

若要停用工作流程模型的傳輸，請修改「DAM更新資產卸載」工作流程。

1. 從[http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html)開啟工作流控制台。
1. 開啟「模型」(Models)頁簽。
1. 開啟「DAM更新資產卸載」工作流程模型。
1. 開啟「DAM工作流程卸載」步驟的步驟屬性。
1. 開啟「參數」(Arguments)頁簽，取消選擇「添加模型以輸入」(Add Model To Input)和「添加模型到輸出」(Add Model To Output)選項。
1. 保存對模型的更改。

### 最佳化輪詢間隔 {#optimizing-the-polling-interval}

工作流程卸載是使用主要伺服器上的外部工作流程來實施的，該工作流程會輪詢背景工作上已卸載的工作流程是否完成。 外部工作流進程的預設輪詢間隔為5秒。 Adobe建議您將「資產」卸載步驟的輪詢間隔至少增加至15秒，以減少主要伺服器的卸載開銷。

1. 從[http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html)開啟工作流控制台。

1. 開啟「模型」(Models)頁簽。
1. 開啟「DAM更新資產卸載」工作流程模型。
1. 開啟「DAM工作流程卸載」步驟的步驟屬性。
1. 開啟「公域」標籤，並調整Period屬性的值。
1. 保存對模型的更改。

## 更多資源 {#more-resources}

本檔案著重於資產卸載。 以下是卸載的其他檔案：

* [卸載作業](/help/sites-deploying/offloading.md)
* [資產工作流程卸載程式](/help/sites-administering/workflow-offloader.md)

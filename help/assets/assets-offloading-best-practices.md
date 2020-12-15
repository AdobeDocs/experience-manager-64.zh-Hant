---
title: 資產卸載最佳做法
description: 建議在AEM Assets中卸載資產擷取和複製工作流程的使用案例和最佳實務。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 31d652ee04fe75e96f96c9ddc5a6f2c3c64bd630
workflow-type: tm+mt
source-wordcount: '1818'
ht-degree: 0%

---


# 資產卸載最佳實踐{#assets-offloading-best-practices}

>[!WARNING]
>
>此功能已過時，不再支援AEM 6.4，並在AEM 6.5中移除。相應計畫。

在Adobe Experience Manager(AEM)Assets中處理大型檔案和執行工作流程可能會耗用大量的CPU、記憶體和I/O資源。 尤其是，資產的大小、工作流程、使用者人數和資產擷取頻率都會影響整體系統效能。 最耗用資源的作業包括AEM資產擷取和複製工作流程。 在單一AEM製作例項上大量使用這些工作流程可能會對製作效率造成負面影響。

將這些任務卸載到專用的工作器實例可以減少CPU、記憶體和IO開銷。 通常，卸載的思想是將消耗大量CPU/記憶體/IO資源的任務分發到專用工作器實例。 以下各節包括資產卸載的建議使用案例。

## AEM Assets Offloading {#aem-assets-offloading}

AEM Assets會建置原生資產特定的工作流程擴充功能，以進行卸載。 它以卸載框架提供的一般工作流程擴充為基礎，但在實施中包含其他資產特定功能。 「資產」卸載的目的，是在已上傳的資產上有效執行「DAM更新資產」工作流程。 資產卸載可讓您更精確地控制擷取工作流程。

## AEM Assets Offloading Components {#aem-assets-offloading-components}

下圖描述了資產卸載流程中的主要元件：

![chlimage_1-55](assets/chlimage_1-55.png)

### DAM更新資產卸載工作流{#dam-update-asset-offloading-workflow}

DAM更新資產卸載工作流程會在使用者上傳資產的主要（作者）伺服器上執行。 此工作流程是由一般工作流程啟動程式所觸發。 此卸載工作流程不會處理已上載的資產，而是使用主題&#x200B;*com/adobe/granite/workflow/offloading*&#x200B;建立新作業。 卸載工作流將添加目標工作流的名稱——在此例中為「DAM更新資產」工作流，以及資產路徑到作業裝載。 在建立卸載作業後，主實例上的卸載工作流將等待卸載作業運行。

### 作業管理器{#job-manager}

作業管理器將新作業分發給工作器實例。 在設計分發機制時，必須考慮主題啟用。 作業只能指派給啟用作業主題的例項。 禁用主卷上的主題`com/adobe/granite/workflow/offloading` ，並在工作器上啟用該主題，以確保將該作業分配給該工作器。

### AEM卸載{#aem-offloading}

卸載框架標識分配給工作器實例的工作流卸載作業，並使用複製將它們物理地傳輸到工作器，包括它們的裝載（例如，要捕獲的映像）。

### 工作流卸載作業使用者{#workflow-offloading-job-consumer}

在員工上寫入作業後，作業管理員會呼叫負責&#x200B;*com/adobe/granite/workflow/offloading*&#x200B;主題的作業使用者。 然後，作業使用者會在資產上執行DAM更新資產工作流程。

## Sling Topology {#sling-topology}

Sling拓撲會將AEM例項分組，讓它們能夠彼此感知，不受基礎永續性的影響。 Sling拓撲的這項特性可讓您建立適用於非叢集、叢集和混合藍本的拓撲。 實例可以向整個拓撲顯示屬性。 該框架提供回呼，用於監聽拓撲中的更改（實例和屬性）。 Sling拓撲為Sling分佈式作業提供基礎。

### Sling distributed jobs {#sling-distributed-jobs}

Sling分佈式作業有助於在屬於拓撲成員的一組實例之間分配作業。 Sling工作是以功能為基礎。 作業由其作業主題定義。 要運行作業，實例必須為特定作業主題提供作業使用者。 作業主題是分配機制的主要驅動因素。

作業僅分配給為主題提供作業使用者的實例。 通過在實例上啟用／禁用作業使用者，您可以定義實例的功能並影響分配機制。 實例的可用作業用戶被廣播到整個拓撲。

在此上下文中，術語分配表示將作業分配給提供作業使用者的特定實例。 對實例的分配儲存在儲存庫中。 換言之，Sling分佈式作業可依預設指派給拓撲中的任何例項。 但是，其他作業只能由共用同一儲存庫的實例運行。 這意味著這些作業只能由屬於同一群集的實例運行。 不運行分配給不同群集實例的作業。

### 花崗岩卸載框架{#granite-offloading-framework}

Granite卸載架構可彌補Sling作業散發的不足，以執行指派給非叢集例項的作業。 它不執行任何分發（例項分配）。 不過，它會識別散發至非叢集例項的Sling工作，並將它們傳輸至目標例項以執行。 目前，卸載使用複製來執行此作業傳輸。 要運行作業，卸載定義輸入和輸出，然後將其與作業組合以構建作業裝載。

Sling分佈式作業提供作業和分發架構。 Granite卸載只負責將作業分配給非群集實例的特殊情況的傳輸。

除了傳輸外，卸載框架還為工作流引擎提供了擴展。 它允許框架在工作流中建立分佈式作業，並等待其完成，然後再進行工作流。 它是使用工作流引擎的工作流外部步驟API來實現的。 其中一個擴充功能有助於一般分發工作流程。 不支援散發單一工作流程步驟。

卸載框架還提供用戶介面(UI)，可直觀地顯示和控制整個拓撲中的作業主題啟用。 UI可讓您方便地設定Sling分散作業的主題啟用。 您也可以設定不使用UI的卸載。

## 資產卸載的一般指南和最佳做法{#general-guidance-and-best-practices-for-asset-offloading}

每個實作都是獨一無二的，因此，沒有一種「一刀切」的卸載配置。 以下章節提供有關資產擷取卸載的指引和最佳實務。

資產卸載也會對系統施加間接費用，包括工序間接費用。 如果您遇到資產擷取載入的問題，Adobe建議您先改善設定，而不要卸載。 移至資產卸載前，請考慮下列選項：

* 擴展硬體
* 最佳化工作流程
* 使用瞬時工作流程
* 限制用於工作流的內核數

如果您認為資產卸載是適合您的方法，Adobe會提供下列指引：

* 建議使用TarMK部署
* 基於TarMK的資產卸載不適用於廣泛的橫向擴展
* 確保作者和工作者之間的網路效能令人滿意

### 建議的資產卸載部署{#recommended-assets-offloading-deployment}

有了AEM和Oak，您就可能有數種部署藍本。 對於資產卸載，建議使用共用資料儲存進行基於TarMK的部署。 下圖概述了建議的部署：

![chlimage_1-56](assets/chlimage_1-56.png)

如需有關設定資料儲存區的詳細資訊，請參閱「在AEM中設定節點儲存區和資料儲存區」。[](../sites-deploying/data-store-config.md)

### 關閉自動代理管理{#turning-off-automatic-agent-management}

Adobe建議您關閉自動代理管理，因為它不支援無二進位複製，在設定新的卸載拓撲時可能會造成混淆。 此外，它不自動支援無二進位複製所需的前向複製流。

1. 從URL `http://localhost:4502/system/console/configMgr`開啟Configuration Manager。
1. 開啟`OffloadingAgentManager`(`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingAgentManager`)的配置。
1. 禁用自動代理管理。

### 使用前向複製{#using-forward-replication}

預設情況下，卸載傳輸使用反向複製將卸載的資產從工作器拉回主伺服器。 反向複製代理不支援無二進位複製。 您應將卸載配置為使用轉發複製將卸載的資產從工作器推回主伺服器。

1. 如果使用反向複製從預設配置遷移，請禁用或刪除主和工作器上名為&quot; `offloading_outbox`&quot;和&quot; `offloading_reverse_*`&quot;的所有代理，其中&amp;ast;代表目標例項的Sling ID。
1. 在每個工作器上，建立指向主伺服器的新轉發複製代理。 該過程與從主代理向工作者建立轉發代理相同。 有關設定卸載複製代理的說明，請參見[建立卸載的複製代理](../sites-deploying/offloading.md#creating-replication-agents-for-offloading)。
1. 開啟`OffloadingDefaultTransporter`(`http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter`)的配置。
1. 將屬性`default.transport.agent-to-master.prefix`的值從`offloading_reverse`變更為`offloading`。

<!-- TBD: Make updates to the configuration for allow and block list after product updates are done.
TBD: Update the property in the last step when GRANITE-30586 is fixed.
-->

### 在作者和工作者之間使用共用資料儲存和無二進位複製{#using-shared-datastore-and-binary-less-replication-between-author-and-workers}

建議使用無二進位複製以減少資產卸載的傳輸開銷。 要瞭解如何為共用資料儲存設定無二進位複製，請參閱[在AEM中配置節點儲存和資料儲存。 ](/help/sites-deploying/data-store-config.md)對於Assets卸載，此過程並不不同，只是涉及其他複製代理。 由於無二進位複製只適用於轉發複製代理，因此您還應對所有卸載代理使用轉發複製。

### 關閉傳輸包{#turning-off-transport-packages}

預設情況下，卸載會建立包含卸載作業和作業裝載（原始資產）的內容包，並使用單個複製請求傳輸此單個卸載包。 使用無二進位複製時，建立這些卸載軟體包會起到反作用，因為在建立軟體包時，二進位檔案將再次序列化到軟體包中。 可以關閉這些傳輸包的使用，這會導致卸載作業和裝載在多個複製請求中傳輸，每個裝載條目各一個。 這樣，就可以利用無二進位複製的好處。

1. 在[http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter](http://localhost:4502/system/console/configMgr/com.adobe.granite.offloading.impl.transporter.OffloadingDefaultTransporter)開啟&#x200B;*OffloadingDefaultTransporter*&#x200B;元件的元件組態
1. 禁用屬性&#x200B;*複製包(default.transport.contentpackage)*。

### 禁用工作流模型{#disabling-the-transport-of-workflow-model}的傳輸

預設情況下，*DAM更新資產卸載*&#x200B;卸載工作流將工作流模型添加到作業裝載中，以調用該工作流模型。 由於此工作流程預設會遵循現成可用的&#x200B;*DAM更新資產*&#x200B;模型，因此可移除此額外的裝載。

如果工作流程模型已從作業裝載中停用，請確定您使用其他工具（例如封裝管理器）分發對參考工作流程模型的變更。

若要停用工作流模型的傳輸，請修改「DAM更新資產卸載」工作流。

1. 從[http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html)開啟工作流程主控台。
1. 開啟「模型」(Models)頁籤。
1. 開啟「DAM更新資產卸載」工作流程模型。
1. 開啟「DAM工作流程卸載」步驟的步驟屬性。
1. 開啟「參數」(Arguments)頁籤，取消選擇「將模型添加到輸入」(Add Model To Input)和「將模型添加到輸出」(Add Model To Output)選項。
1. 將更改保存到模型。

### 優化輪詢間隔{#optimizing-the-polling-interval}

工作流卸載是使用主伺服器上的外部工作流實現的，該外部工作流輪詢工作器上卸載的工作流是否完成。 外部工作流進程的預設輪詢間隔為5秒。 Adobe建議您將「資產」卸載步驟的輪詢間隔提高至少15秒，以降低主要系統的卸載開銷。

1. 從[http://localhost:4502/libs/cq/workflow/content/console.html](http://localhost:4502/libs/cq/workflow/content/console.html)開啟工作流程主控台。

1. 開啟「模型」(Models)頁籤。
1. 開啟「DAM更新資產卸載」工作流程模型。
1. 開啟「DAM工作流程卸載」步驟的步驟屬性。
1. 開啟「共用」標籤，並調整「期間」屬性的值。
1. 將更改保存到模型。

## 更多資源{#more-resources}

本檔案著重於資產卸載。 以下是有關卸載的一些其他文檔：

* [卸載作業](/help/sites-deploying/offloading.md)
* [資產工作流程卸載程式](/help/sites-administering/workflow-offloader.md)


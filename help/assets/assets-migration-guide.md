---
title: 將資產大量移轉至Adobe Experience Manager Assets
description: 如何將資產帶入AEM、套用中繼資料、產生轉譯，以及啟用資產以發佈例項。
contentOwner: AG
feature: Migration,Renditions,Asset Management
role: Architect,Admin
exl-id: 31da9f3d-460a-4b71-9ba0-7487f1b159cb
source-git-commit: 63a4304a1a10f868261eadce74a81148026390b6
workflow-type: tm+mt
source-wordcount: '1772'
ht-degree: 8%

---

# 資產移轉指南 {#assets-migration-guide}

將資產移轉至AEM時，需考慮數個步驟。 從其當前主目錄中提取資產和元資料不屬於本文檔的範圍，因為它在實施之間差異很大。 相反地，本檔案說明如何將這些資產帶入AEM、套用其中繼資料、產生轉譯，以及啟用或發佈資產。

## 必備條件 {#prerequisites}

在執行下列任何步驟之前，請檢閱並實作[資產效能調整秘訣](performance-tuning-guidelines.md)中的指引。 許多步驟（如配置最大併發作業）都提高了伺服器在負載下的穩定性和效能。 在系統載入資產後，其他步驟（例如檔案資料存放區設定）將難以執行。

>[!NOTE]
>
>下列資產移轉工具不屬於Adobe Experience Manager。 Adobe客戶支援不支援這些工具。
>
>* ACS [!DNL Experience Manager]工具標籤製作器
>* ACS [!DNL Experience Manager]工具CSV資產匯入工具
>* ACS Commons Bulk Workflow Manager
>* ACS Commons Fast Action Manager
>* 合成工作流程

>
>本軟體為開放原始碼， [Apache v2授權涵蓋此軟體](https://adobe-consulting-services.github.io/pages/license.html)。若要提出問題或報告問題，請造訪ACS 工具和 [ [!DNL Experience Manager] ACS 公域的GitHub](https://github.com/Adobe-Consulting-Services/acs-aem-commons/issues)[ [!DNL Experience Manager] 問題](https://github.com/Adobe-Consulting-Services/acs-aem-tools/issues)。

## 遷移至[!DNL Experience Manager] {#migrate-to-aem}

將資產移轉至[!DNL Experience Manager]需要數個步驟，且應視為分階段程式。 移轉階段如下：

1. 停用工作流程。
1. 載入標籤。
1. 擷取資產。
1. 處理轉譯。
1. 啟動資產。
1. 啟用工作流程。

![chlimage_1-223](assets/chlimage_1-223.png)

### 停用工作流程 {#disable-workflows}

開始遷移之前，請禁用`DAM Update Asset`工作流的啟動器。 最好將所有資產內嵌至系統，然後批次執行工作流程。 如果您在移轉進行時已上線，您可以排程這些活動在非工作時間執行。

### 載入標籤 {#load-tags}

您可能已準備好將標籤分類套用至影像。 CSV資產匯入工具和中繼資料設定檔功能等工具可協助將標籤套用至資產自動化。 在此之前，請在Experience Manager中新增標籤。 [ACS [!DNL Experience Manager] 工具標籤製作器](https://adobe-consulting-services.github.io/acs-aem-tools/features/tag-maker/index.html)功能可讓您使用載入至系統的Microsoft Excel試算表填入標籤。

### 內嵌資產 {#ingest-assets}

將資產擷取至系統中時，效能和穩定性是重要考量。 在Experience Manager中載入大量資料時，請確保系統效能良好。 這樣可以最大限度地減少添加資料所需的時間，並有助於避免系統過載。 這有助於防止系統當機，特別是在已投入生產的系統中。

將資產載入系統有兩種方法：使用HTTP的推送式方法，或使用JCR API的提取式方法。

#### 透過HTTP推送 {#push-through-http}

Adobe的Managed Services團隊使用名為Glutton的工具，將資料載入客戶環境中。 Glutton是一個小型Java應用程式，它將所有資產從一個目錄載入到[!DNL Experience Manager]實例上的另一個目錄。 您也可以使用工具（例如Perl指令碼）將資產張貼至存放庫，而不是使用Glutton。

使用透過https推送的方式有兩個主要缺點：

1. 透過HTTP將資產傳輸至伺服器。 這需要相當多的開銷，而且非常耗時，因而延長了執行遷移所花費的時間。
1. 如果您有必須套用至資產的標籤和自訂中繼資料，此方法需要執行第二個自訂程式，才能在匯入資產後將此中繼資料套用至資產。

擷取資產的另一種方法是從本機檔案系統提取資產。 不過，如果您無法將外部硬碟或網路共用裝載至伺服器以執行提取式方法，則透過HTTP張貼資產是最佳選項。

#### 從本地檔案系統提取 {#pull-from-the-local-file-system}

[ACS [!DNL Experience Manager] 工具CSV資產匯入工具](https://adobe-consulting-services.github.io/acs-aem-tools/features/csv-asset-importer/index.html)從檔案系統提取資產，並從CSV檔案提取資產中繼資料以匯入資產。 [!DNL Experience Manager] Asset Manager API可用來將資產匯入系統，並套用已設定的中繼資料屬性。 理想情況下，資產會透過網路檔案裝載或外部驅動器裝載在伺服器上。

當資產未通過網路傳輸時，整體效能會大大提高。 此方法通常是將資產載入存放庫的最有效方法。 此外，您可以透過單一步驟匯入所有資產和中繼資料，因為工具支援中繼資料擷取。 套用中繼資料不需要其他步驟，例如使用個別工具。

### 處理轉譯 {#process-renditions}

將資產載入系統後，您需要透過DAM更新資產工作流程處理資產，以擷取中繼資料並產生轉譯。 執行此步驟之前，您必須複製並修改DAM更新資產工作流程，以符合您的需求。 您可能不需要預設工作流程中的某些步驟，例如Dynamic Media Classic PTIFF產生或InDesign伺服器整合。

根據您的需求設定工作流程後，您有兩個選項可執行：

1. 最簡單的方法是[ACS Commons&#39; Bulk Workflow Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/bulk-workflow-manager.html)。 此工具允許您執行查詢，並通過工作流處理查詢結果。 還有設定批大小的選項。
1. 您可搭配「合成工 [作流程」使用ACS Commons Fast Action Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html)[](https://adobe-consulting-services.github.io/acs-aem-commons/features/synthetic-workflow.html)。雖然此方法的參與度要高得多，但可讓您移除[!DNL Experience Manager]工作流程引擎的額外負荷，同時最佳化伺服器資源的使用。 此外，Fast Action Manager還通過動態監控伺服器資源並調節系統上的負載，進一步提高了效能。ACS Commons功能頁上提供了示例指令碼。

### 啟動資產 {#activate-assets}

若是具有發佈層級的部署，您需要將資產啟動至發佈伺服器陣列。 雖然Adobe建議執行多個單一發佈執行個體，但將所有資產複製到單一發佈執行個體然後複製該執行個體最有效率。 在啟動大量資產時，觸發樹狀結構啟動後，您可能需要進行干預。 原因如下：觸發啟動時，項目會新增至Sling作業/事件佇列。 此佇列的大小開始超過約40,000個項目後，處理速度大幅放緩。 當此隊列的大小超過100,000個項後，系統穩定性就會開始受到影響。

若要解決此問題，您可以使用[快速動作管理員](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html)來管理資產復寫。 這樣就不需要使用Sling佇列，降低開銷，同時限制工作負載以防止伺服器過載。 功能的檔案頁面上顯示了使用FAM管理復寫的範例。

將資產傳送至發佈農場的其他選項包括使 [用vlt-rcp](https://jackrabbit.apache.org/filevault/rcp.html)[或oak-run](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run)，這些工具是Jackrabbit的一部份。另一個選項是對[!DNL Experience Manager]基礎架構使用開放源碼工具，該工具稱[Grabbit](https://github.com/TWCable/grabbit)，該工具聲稱其效能比vlt快。

對於其中任何方法，請注意製作例項上的資產未顯示為已啟動。 若要處理以正確啟動狀態標籤這些資產，您也需執行指令碼，將資產標示為已啟動。

>[!NOTE]
>
>Adobe不維護或支援Grabbit。

### 原地複製發佈 {#clone-publish}

啟動資產後，您可以複製發佈執行個體，以建立部署所需的所有復本。 克隆伺服器相當簡單，但有一些重要步驟需要記住。 若要原地複製發佈：

1. 備份源實例和資料儲存。
1. 將實例和資料儲存的備份還原到目標位置。 下列步驟皆參考此新例項。
1. 在`crx-quickstart/launchpad/felix`下對`sling.id`執行檔案系統搜索。 刪除此檔案。
1. 在資料儲存的根路徑下，找到並刪除任何`repository-XXX`檔案。
1. 編輯`crx-quickstart/install/org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config`和`crx-quickstart/launchpad/config/org/apache/jackrabbit/oak/plugins/blob/datastore/FileDataStore.config`以指向新環境中資料儲存區的位置。
1. 啟動環境。
1. 更新作者上任何復寫代理的設定，以指向新執行個體上正確的發佈執行個體或調度程式排清代理，以指向新環境的正確調度程式。

### 啟用工作流程 {#enable-workflows}

完成移轉後，應重新啟用DAM更新資產工作流程的啟動器，以支援產生轉譯和擷取中繼資料，以持續使用日常系統。

## 跨[!DNL Experience Manager]部署移轉資產 {#migrate-between-aem-instances}

雖然並不像以前那麼常見，但有時您需要將大量資料從一個[!DNL Experience Manager]實例遷移到另一個實例；例如，執行[!DNL Experience Manager]升級時，請升級硬體，或遷移到新的資料中心，例如進行AMS遷移。

在此情況下，資產已填入中繼資料，且已產生轉譯。 您只需專注於將資產從一個執行個體移至另一個執行個體。 在[!DNL Experience Manager]執行個體之間移轉時，請執行下列步驟：

1. 停用工作流程：由於您要移轉轉譯項目和我們的資產，因此想要停用DAM更新資產的工作流程啟動器。

1. 移轉標籤：由於您已在源[!DNL Experience Manager]實例中載入了標籤，因此您可以在內容包中建立標籤，並在目標實例上安裝該包。

1. 移轉資產：建議使用兩種工具將資產從一個[!DNL Experience Manager]例項移至另一個例項：

   * **Vault Remote Copy**(或 `vlt rcp`)允許您跨網路使用vlt。您可以指定源目錄和目標目錄，然後vlt從一個實例下載所有儲存庫資料並將其載入到另一個實例。 Vlt rcp記錄在[https://jackrabbit.apache.org/filevault/rcp.html](https://jackrabbit.apache.org/filevault/rcp.html)
   * **** Grabbitis是Time Warner Cable為實作而開發的開放原始碼內容同步 [!DNL Experience Manager] 工具。因為它使用連續的資料流，與vlt rcp相比，它的延遲更低，並聲稱速度比vlt rcp快2到10倍。 Grabbit也僅支援增量內容的同步，這可讓其在完成初始遷移過程後同步更改。

1. 啟動資產：遵循針對初始移轉至AEM而記錄的[啟用資產](#activate-assets)指示。

1. 原地複製發佈：和新移轉一樣，載入單一發佈執行個體並複製執行個體比在兩個節點上啟動內容更有效率。 請參閱[複製發佈。](#clone-publish)

1. 啟用工作流程：完成移轉後，請重新啟用DAM更新資產工作流程的啟動器，以支援產生轉譯和擷取中繼資料，以持續使用日常系統。

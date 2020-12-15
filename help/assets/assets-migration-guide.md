---
title: 將資產大量移轉至Adobe Experience Manager Assets
description: 如何將資產匯入AEM、套用中繼資料、產生轉譯，以及啟用資產以發佈例項。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 976d037d701eb7cc61a62e14e554675961d6179c
workflow-type: tm+mt
source-wordcount: '1789'
ht-degree: 11%

---


# 資產遷移指南{#assets-migration-guide}

將資產移轉至AEM時，需考慮數個步驟。 從目前的首頁擷取資產和中繼資料，不受本檔案的限制，因為不同實作之間的差異很大。 本檔案會說明如何將這些資產匯入AEM、套用其中繼資料、產生轉譯，以及啟用或發佈資產。

## 必備條件 {#prerequisites}

在執行下列任何步驟之前，請先檢閱並實作[資產效能調整提示](performance-tuning-guidelines.md)中的指引。 許多步驟（例如設定最大併發作業）都可增強伺服器在負載下的穩定性和效能。 在系統載入資產後，其他步驟（例如檔案資料存放區設定）將很難執行。

>[!NOTE]
>
>以下資產移轉工具不屬於Adobe Experience Manager的一部分。 Adobe客戶服務不支援這些工具。
>
>* ACS AEM Tools Tag Maker
>* ACS AEM工具CSV資產匯入工具
>* ACS Commons Bulk Workflow Manager
>* ACS Commons Fast Action Manager
>* 合成工作流程

>
>
本軟體為開放原始碼， [Apache v2授權涵蓋此軟體](https://adobe-consulting-services.github.io/pages/license.html)。若要提出問題或報告問題，請造訪ACS AEM工具和 [ACS AEM公域的GitHub](https://github.com/Adobe-Consulting-Services/acs-aem-commons/issues)[問題](https://github.com/Adobe-Consulting-Services/acs-aem-tools/issues)。

## 移轉至AEM {#migrate-to-aem}

將資產移轉至AEM需要幾個步驟，且應視為分階段程式。 遷移的階段如下：

1. 停用工作流程。
1. 載入標籤。
1. 收錄資產。
1. 處理轉譯。
1. 啟動資產。
1. 啟用工作流程。

![chlimage_1-223](assets/chlimage_1-223.png)

### 停用工作流程{#disable-workflows}

開始遷移之前，請禁用`DAM Update Asset`工作流的啟動程式。 最好將所有資產內嵌至系統，然後以批次執行工作流程。 如果您在進行移轉時已上線，您可以排程這些活動在下班時間執行。

### 載入標籤{#load-tags}

您可能已經有了要套用至影像的標籤分類法。 CSV資產匯入工具和中繼資料描述檔功能等工具可協助自動將標籤套用至資產。 在此之前，請在Experience Manager中新增標籤。 [ACS AEM Tools Tag Maker](https://adobe-consulting-services.github.io/acs-aem-tools/features/tag-maker/index.html)功能可讓您使用載入系統的Microsoft Excel試算表填入標籤。

### 收錄資產{#ingest-assets}

在將資產放入系統時，效能與穩定性是重要的考量。 在Experience Manager中載入大量資料時，請確保系統運作良好。 這樣可以最大限度地減少添加資料所需的時間，並有助於避免系統過載。 這有助於防止系統崩潰，特別是在已在生產的系統中。

將資產載入系統有兩種方法：使用HTTP的推播方式或使用JCR API的推播方式。

#### 推送HTTP {#push-through-http}

Adobe的「受管理服務」團隊使用名為Glutton的工具，將資料載入客戶環境。 Glutton是小型Java應用程式，可從一個目錄將所有資產載入AEM例項上的另一個目錄。 您也可以使用諸如Perl指令碼之類的工具將資產發佈到儲存庫中，而不是Glutton。

使用推送https的方法有兩個主要的缺點：

1. 透過HTTP將資產傳輸至伺服器。 這需要相當多的開銷，而且非常耗時，因而延長了執行遷移所需的時間。
1. 如果您有必須套用至資產的標籤和自訂中繼資料，此方法需要執行第二個自訂程式，以便在匯入資產後，將此中繼資料套用至資產。

接收資產的另一種方法是從本地檔案系統提取資產。 不過，如果您無法將外部磁碟機或網路共用載入伺服器，以執行以拉式為基礎的方式，則最好透過HTTP張貼資產。

#### 從本地檔案系統{#pull-from-the-local-file-system}中提取

[ACS AEM Tools CSV Asset Importer](https://adobe-consulting-services.github.io/acs-aem-tools/features/csv-asset-importer/index.html)會從CSV檔案中提取資產，以匯入資產。 AEM Asset Manager API可用來將資產匯入系統並套用已設定的中繼資料屬性。 理想情況下，資產會透過網路檔案載入或透過外部磁碟機載入伺服器。

當資產未透過網路傳輸時，整體效能會大幅提升。 此方法通常是將資產載入儲存庫的最有效方法。 此外，您可以在單一步驟中匯入所有資產和中繼資料，因為此工具支援中繼資料擷取。 套用中繼資料不需要其他步驟，例如使用個別工具。

### 處理轉譯{#process-renditions}

將資產載入系統後，您需要透過DAM更新資產工作流程來處理這些資產，以擷取中繼資料並產生轉譯。 在執行此步驟之前，您需要複製並修改DAM更新資產工作流程，以符合您的需求。 您可能不需要在預設工作流程中執行某些步驟，例如產生Scene7 PTIFF或整合InDesign伺服器。

根據您的需求設定工作流程後，您有兩個選項可加以執行：

1. 最簡單的方法是[ACS公域的批量工作流管理器](https://adobe-consulting-services.github.io/acs-aem-commons/features/bulk-workflow-manager.html)。 此工具允許您執行查詢，並通過工作流處理查詢結果。 還有設定批次大小的選項。
1. 您可搭配「合成工 [作流程」使用ACS Commons Fast Action Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html)[](https://adobe-consulting-services.github.io/acs-aem-commons/features/synthetic-workflow.html)。雖然此方法的參與度更高，但可讓您移除AEM工作流程引擎的額外負荷，同時最佳化伺服器資源的使用。此外，Fast Action Manager還通過動態監控伺服器資源並調節系統上的負載，進一步提高了效能。ACS Commons功能頁上提供了示例指令碼。

### 啟動資產{#activate-assets}

對於具有發佈層的部署，您需要將資產啟動至發佈群。 雖然Adobe建議執行多個單一發佈例項，但將所有資產複製至單一發佈例項，然後複製該例項最有效率。 在啟動大量資產時，在觸發樹狀結構啟動後，您可能需要進行干預。 原因如下：當觸發啟動時，項目會新增至Sling工作／事件佇列。 當此佇列的大小開始超過約40,000個項目後，處理速度大幅降低。 當此隊列的大小超過100,000個項目後，系統穩定性就會開始受到影響。

要解決此問題，可以使用[Fast Action Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html)管理資產複製。 這樣不需使用Sling佇列，降低開銷，同時可調節工作負載，以防止伺服器過載。 使用FAM管理複製的範例顯示在功能的檔案頁面上。

將資產傳送至發佈農場的其他選項包括使 [用vlt-rcp](https://jackrabbit.apache.org/filevault/rcp.html)[或oak-run](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run)，這些工具是Jackrabbit的一部份。另一個選擇是針對您的AEM基礎架構使用開放來源工具，稱為 [Grabbit](https://github.com/TWCable/grabbit)，該工具聲稱其效能比vlt快。

對於上述任何方法，但須注意的是，作者實例上的資產並未顯示為已啟動。 若要處理以正確啟動狀態來標籤這些資產，您還需要執行指令碼，將資產標示為已啟動。

>[!NOTE]
>
>Adobe不維護或支援Grabbit。

### 複製發佈{#clone-publish}

在啟動資產後，您可以複製您的發佈例項，以建立部署所需的份數。 克隆伺服器相當簡單，但需要記住一些重要步驟。 若要複製發佈：

1. 備份源實例和資料儲存。
1. 將實例和資料儲存的備份還原到目標位置。 以下步驟均參考此新實例。
1. 在`crx-quickstart/launchpad/felix`下對`sling.id`執行檔案系統搜索。 刪除此檔案。
1. 在資料儲存的根路徑下，找到並刪除任何`repository-XXX`檔案。
1. 編輯`crx-quickstart/install/org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config`和`crx-quickstart/launchpad/config/org/apache/jackrabbit/oak/plugins/blob/datastore/FileDataStore.config` ，以指向新環境中資料儲存區的位置。
1. 啟動環境。
1. 更新作者上任何複製代理的配置，以指向新實例上正確的發佈實例或調度器刷新代理，以指向新環境的正確調度程式。

### 啟用工作流程{#enable-workflows}

完成移轉後，應重新啟用DAM更新資產工作流程的啟動器，以支援轉譯產生和中繼資料擷取，以持續使用日常系統。

## 跨AEM部署移轉資產{#migrate-between-aem-instances}

雖然不是這麼常見，但有時您需要將大量資料從一個AEM例項移轉至另一個例項；例如，當您執行AEM升級、升級硬體或移轉至新的資料中心時，例如AMS移轉。

在這種情況下，您的資產已填入中繼資料，且已產生轉譯。 您只需專注於將資產從一個實例移至另一個實例。 在AEM例項之間移轉時，請執行下列步驟：

1. 停用工作流程：由於您要移轉轉譯以及我們的資產，所以您想要停用DAM更新資產的工作流程啟動器。

1. 移轉標籤：由於您已在來源AEM例項中載入標籤，因此您可以在內容套件中建立標籤，並在目標例項上安裝套件。

1. 移轉資產：建議使用兩種工具，將資產從一個AEM例項移至另一個：

   * **Vault Remote Copy**，或 `vlt rcp`，允許您跨網路使用vlt。您可以指定源目錄和目標目錄，並從一個實例下載所有儲存庫資料並將其載入到另一個實例。 Vlt rcp記載於[https://jackrabbit.apache.org/filevault/rcp.html](https://jackrabbit.apache.org/filevault/rcp.html)
   * **Grabbitis是** Time Warner Cable為其AEM實作而開發的開放原始碼內容同步工具。由於它使用連續的資料流，與vlt rcp相比，它的延遲更低，並聲稱速度比vlt rcp快2到10倍。 Grabbit也僅支援Delta內容的同步，這可讓Grabbit在初始移轉通過完成後同步變更。

1. 啟動資產：請依照針對初次移轉至AEM所記錄之[啟動資產](#activate-assets)的指示進行。

1. 仿製發佈：和新移轉一樣，載入單一發佈執行個體並進行仿製比在兩個節點上啟動內容更有效率。 請參閱[克隆發佈。](#clone-publish)

1. 啟用工作流程：完成移轉後，請重新啟用DAM更新資產工作流程的啟動器，以支援產生轉譯和中繼資料擷取，以持續使用日常系統。

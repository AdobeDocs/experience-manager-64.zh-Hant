---
title: 資產效能調整指南
description: 以下重點領域 [!DNL Experience Manager] 配置、對硬體、軟體和網路元件的更改，以消除瓶頸並優化 [!DNL Experience Manager] 資產。
contentOwner: AG
feature: Asset Management
role: Architect,Admin
exl-id: 6c1bff46-f9e0-4638-9374-a9e820d30534
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3203'
ht-degree: 1%

---

# 資產效能調整指南 {#assets-performance-tuning-guide}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets設定包含許多硬體、軟體和網路元件。 根據您的部署方案，您可能需要對硬體、軟體和網路元件進行特定配置更改，以消除效能瓶頸。

此外，識別並遵守某些硬體和軟體優化指南有助於建立良好的基礎，使您的 [!DNL Experience Manager] 資產部署，以符合效能、延展性和可靠性的預期。

在 [!DNL Experience Manager] 資產可能會影響使用者互動式效能、資產處理、下載速度等方面的體驗。

事實上，效能最佳化是您在為任何專案建立目標量度之前所執行的基本任務。

以下是您可在發現效能問題並修正其後，再對使用者造成影響的關鍵重點區域。

## Platform {#platform}

同時 [!DNL Experience Manager] 在多種平台上均受支援，因此Adobe在Linux和Windows上對本機工具的支援最強，有助於實現最佳效能和易於實施。 理想情況下，您應部署64位作業系統，以滿足 [!DNL Experience Manager] 資產部署。 與任何 [!DNL Experience Manager] 部署時，您應盡可能實作TarMK。 雖然TarMK無法擴展至單一製作例項以外，但其執行效能比MongoMK好。 您可以新增TarMK卸載例項，以提升您的工作流程處理能力 [!DNL Experience Manager] 資產部署。

### 臨時資料夾 {#temp-folder}

若要改善資產上傳時間，請對Java臨時目錄使用高效能儲存。 在Linux和Windows上，可使用RAM驅動器或SSD。 在基於雲的環境中，可以使用等效的高速儲存類型。 例如，在Amazon EC2中， [短暫的行駛](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html) 可將驅動器用於臨時資料夾。

假設伺服器有足夠的記憶體，請配置RAM驅動器。 在Linux上，運行以下命令以建立8 GB RAM驅動器：

```shell
mkfs -q /dev/ram1 800000
 mkdir -p /mnt/aem-tmp
 mount /dev/ram1 /mnt/aem-tmp
 df -H | grep aem-tmp
```

在Windows OS中，您必須使用第三方驅動程式來建立RAM驅動器，或僅使用高效能儲存（如SSD）。

在高效能臨時卷準備就緒後，請設定JVM參數-Djava.io.tmpdir。 例如，您可以將以下的JVM參數添加到AEM的bin/start指令碼中的CQ_JVM_OPTS變數中：

`-Djava.io.tmpdir=/mnt/aem-tmp`

## Java配置 {#java-configuration}

### Java版本 {#java-version}

由於Oracle自2015年4月起已停止發行Java 7更新，因此Adobe建議部署 [!DNL Experience Manager] Java 8上的資產。 在某些情況下，它表現出改進的效能。

### JVM參數 {#jvm-parameters}

應設定以下JVM參數：

* `-XX:+UseConcMarkSweepGC`
* `-Doak.queryLimitInMemory`=500000
* `-Doak.queryLimitReads`=100000
* `-Dupdate.limit`=250000
* `-Doak.fastQuerySize`=true

## 資料儲存和記憶體配置 {#data-store-and-memory-configuration}

### 檔案資料儲存配置 {#file-data-store-configuration}

建議將資料存放區與區段存放區分開， [!DNL Experience Manager] Assets使用者。 此外，設定 `maxCachedBinarySize` 和 `cacheSizeInMB` 參數可協助最大化效能。 設定 `maxCachedBinarySize` 到快取中可保留的最小檔案大小。 指定要用於內資料儲存的記憶體內快取的大小 `cacheSizeInMB`. Adobe建議您將此值設定為堆大小總計的2-10%之間。 不過，負載/效能測試有助於確定理想的設定。

### 配置緩衝映像快取的最大大小 {#configure-the-maximum-size-of-the-buffered-image-cache}

將大量資產上傳至Adobe Experience Manager時，若要避免記憶體耗用量出現非預期的尖峰，並防止JVM因OutOfMemoryErrors而失敗，請減少已設定的緩衝影像快取的最大大小。 假設您有一個系統具有最大堆(- `Xmx`參數)(5 GB)、Oak BlobCache設定為1 GB，檔案快取設定為2 GB。 在這種情況下，緩衝快取最多需要1.25 GB和記憶體，這將僅留下0.75 GB記憶體，以備意外的尖峰。

在OSGi Web控制台中配置緩衝快取大小。 At `https://host:port/system/console/configMgr/com.day.cq.dam.core.impl.cache.CQBufferedImageCache`，請設定屬性 `cq.dam.image.cache.max.memory` 位元組。 例如，1073741824為1 GB(1024 x 1024 x 1024 = 1 GB)。

從 [!DNL Experience Manager] 6.1 SP1，如果您使用 `sling:osgiConfig` 用於配置此屬性的節點，請確保將資料類型設定為Long。 如需詳細資訊，請參閱 [CQBufferedImageCache在資產上傳期間取用堆](https://helpx.adobe.com/experience-manager/kb/cqbufferedimagecache-consumes-heap-during-asset-uploads.html).

### 共用資料儲存 {#shared-data-stores}

實作S3或共用檔案資料存放區有助於在大規模實作中節省磁碟空間並增加網路吞吐量。 如需使用共用資料存放區的優點和缺點的詳細資訊，請參閱 [資產規模調整指南](assets-sizing-guide.md).

### S3資料儲存 {#s-data-store}

以下S3資料儲存配置( `org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.cfg`)幫助Adobe從現有檔案資料儲存區提取12.8 TB的二進位大型物件(BLOB)至客戶網站的S3資料儲存區：

```conf
accessKey=<snip>
 secretKey=<snip>
 s3Bucket=<snip>
 s3Region=us-standard
 s3EndPoint=<a href="https://s3.amazonaws.com/">s3.amazonaws.com</a>
 connectionTimeout=120000
 socketTimeout=120000
 maxConnections=80
 writeThreads=60
 concurrentUploadsThreads=30
 asyncUploadLimit=30
 maxErrorRetry=1000
 path=/opt/author/crx-quickstart/repository/datastore
 s3RenameKeys=false
 s3Encryption=SSE_S3
 proactiveCaching=true
 uploadRetries=1000
 migrateFailuresCount=400
```

## 網路最佳化 {#network-optimization}

Adobe建議啟用HTTPS，因為許多公司都有可偵聽HTTP流量的防火牆，這會對上傳和損毀檔案造成負面影響。 對於大型檔案上傳，請確保用戶有有線連接到網路，因為WiFi網路很快就飽和了。 有關確定網路瓶頸的指南，請參見 [資產規模調整指南](assets-sizing-guide.md). 要通過分析網路拓撲來評估網路效能，請參見 [資產網路考量事項](assets-network-considerations.md).

主要取決於可用頻寬的數量和負載 [!DNL Experience Manager] 例項。 常見的配置選項（包括防火牆或代理）有助於提高網路效能。 請謹記以下幾點：

* 根據您的實例類型（小、中、大），確保您有足夠的網路頻寬 [!DNL Experience Manager] 例項。 如果 [!DNL Experience Manager] 托管於AWS。
* 若您的 [!DNL Experience Manager] 例項托管於AWS上，您可透過通用的擴充政策受益。 如果使用者預期會有高負載，請更新執行個體。 縮減其大小以適度/低負載。
* HTTPS:大部分的使用者都有可偵聽HTTP流量的防火牆，這可能會對上傳檔案或在上傳作業期間損毀的檔案造成負面影響。
* 大檔案上載：確保用戶有到網路的有線連接（WiFi連接快速飽和）。

## 工作流程 {#workflows}

### 暫時性工作流程 {#transient-workflows}

盡可能將「DAM更新資產」工作流程設為「暫時」。 此設定可大幅降低處理工作流程所需的開銷，因為在此情況下，工作流程不需要通過正常的追蹤和封存流程。

>[!NOTE]
>
>依預設，「DAM更新資產」工作流程在中設為「暫時」 [!DNL Experience Manager] 6.3.在此情況下，您可以略過以下程式。

1. 開啟 `http://localhost:4502/miscadmin` 在 [!DNL Experience Manager] 要配置的實例。

1. 從導覽樹狀結構中，展 **[!UICONTROL 開「工具]** >工 **[!UICONTROL 作流程]** >模 **[!UICONTROL 型>]** dam ****」。
1. 按兩下 **[!UICONTROL DAM更新資產]**.
1. 從浮動工具面板，切換至 **[!UICONTROL 頁面]** ，然後按一下 **[!UICONTROL 頁面屬性]**.
1. 選擇 **[!UICONTROL 暫時性工作流程]** 按一下 **[!UICONTROL 確定]**.

   >[!NOTE]
   >
   >有些功能不支援暫時性工作流程。 若您的 [!DNL Experience Manager] 資產部署需要這些功能，請勿設定暫時性工作流程。

   如果無法使用暫時性工作流程，請定期執行工作流程清除，刪除封存的DAM更新資產工作流程，以確保系統效能不會降低。

   通常，您應每週執行清除工作流程。 不過，在資源密集型情況（例如在大規模資產擷取期間）中，您可以更頻繁地執行它。

   若要設定工作流程清除，請透過OSGi主控台新增「AdobeGranite工作流程清除」設定。 接下來，在每週維護窗口中配置並計畫工作流。

   如果清除執行時間太長，就會逾時。 因此，您應確保清除作業完成，以避免因工作流程數量過多而導致清除工作流程無法完成的情況。

   例如，執行許多非暫時性工作流程後（會建立工作流程例項節點），您可以執行 [ACS AEM Commons工作流程移除器](https://adobe-consulting-services.github.io/acs-aem-commons/features/workflow-remover.html) 臨機。 它會立即移除冗餘、已完成的工作流程例項，而非等待AdobeGranite工作流程清除排程器執行。

### 最大並行作業數 {#maximum-parallel-jobs}

依預設， [!DNL Experience Manager] 運行的最大並行作業數等於伺服器上的處理器數。 此設定的問題在於，在負載過重的期間，所有處理器都會被DAM更新資產工作流程佔用，導致UI回應速度變慢，並防止 [!DNL Experience Manager] 運行其他保護伺服器效能和穩定性的進程。 作為一個良好做法，請執行以下步驟，將此值設定為伺服器上可用處理器的一半：

1. 開啟 [!DNL Experience Manager] 作者，前往 [http://localhost:4502/system/console/slingevent](http://localhost:4702/system/console/slingevent).
1. 在與您的實施相關的每個工作流程佇列上，按一下「編輯」 ，例如「Granite暫時性工作流程佇列」 。
1. 更改「最大並行作業數」的值，然後按一下「保存」。

將隊列設定為可用處理器的一半是一個可行的解決方案。 但是，您可能必須增加或減少此數量，以實現最大吞吐量，並按環境調整。 暫時和非暫時性工作流程以及其他程式（例如外部工作流程）有不同的佇列。 如果設定為50%的處理器同時處於活動狀態的多個隊列，則系統可以快速超載。 大量使用的佇列在不同使用者實施中大不相同。 因此，您可能必須仔細配置它們，以實現最高效率，而不犧牲伺服器穩定性。

### 卸載 {#offloading}

若是大量耗用資源的工作流程或工作流程（例如視訊轉碼），您可以將DAM更新資產工作流程卸載至第二個製作例項。 卸載的問題通常是，卸載工作流程處理後儲存的任何負載都會被執行個體之間往返複製內容的成本所抵消。

截止日期 [!DNL Experience Manager] 6.2和 [!DNL Experience Manager] 6.1，您可以使用無二進位檔的復寫執行卸載。 在此模型中，製作例項共用通用資料存放區，且只會透過轉送復寫來回傳送中繼資料。 雖然此方法適用於共用檔案資料存放區，但S3資料存放區可能會有問題。 由於背景寫入執行緒可能會導致延遲，因此在卸載作業開始之前，資產可能尚未寫入資料存放區。

### DAM更新資產設定 {#dam-update-asset-configuration}

「DAM更新資產」工作流程包含為工作設定的完整步驟，例如Dynamic Media Classic PTIFF產生和InDesign Server整合。 不過，大部分使用者可能不需要執行其中幾個步驟。 Adobe建議您建立DAM更新資產工作流程模型的自訂復本，並移除任何不必要的步驟。 在此情況下，請更新DAM更新資產的啟動器，以指向新模型。

>[!NOTE]
>
>密集執行DAM更新資產工作流程可大幅增加檔案資料存放區的大小。 由Adobe進行的實驗結果表明，如果在8小時內執行約5500個工作流程，則資料存放區大小可增加約400 GB。
>
>這是臨時增加，在運行資料儲存垃圾收集任務後，資料儲存被還原為原始大小。
>
>通常，資料存放區垃圾收集任務與其他計畫維護任務一起每週運行。
>
>如果您的磁碟空間有限，且大量執行DAM更新資產工作流程，請考慮更頻繁地排程垃圾收集任務。

#### 生成運行時格式副本 {#runtime-rendition-generation}

客戶在其網站上使用各種大小和格式的影像，或用於分發給業務合作夥伴。 由於每個轉譯都會增加儲存庫中資產的空間，因此Adobe建議審慎使用此功能。 若要減少處理和儲存影像所需的資源量，您可以在執行階段產生這些影像，而非在擷取期間以轉譯的形式產生。

許多Sites客戶會實作影像servlet，在要求影像時調整大小並裁切影像，這會對發佈例項造成額外負載。 不過，只要可快取這些影像，就可緩解挑戰。

另一種方法是使用Dynamic Media Classic技術完全放棄影像處理。 此外，您可以部署Brand Portal，不但可接管 [!DNL Experience Manager] 基礎架構，也包括整個發佈層級。

#### ImageMagick {#imagemagick}

如果您自訂「DAM更新資產」工作流程，使用ImageMagick產生轉譯，Adobe建議您在 */etc/ImageMagick/*. 預設情況下，ImageMagick會使用作業系統卷上的整個可用磁碟空間和可用記憶體。 在 `policymap` policy.xml的一節，以限制這些資源。

```xml
<policymap>
  <!-- <policy domain="system" name="precision" value="6"/> -->
  <policy domain="resource" name="temporary-path" value="/ephemeral0/imagemagick_tmp"/>
  <policy domain="resource" name="memory" value="1000MiB"/>
  <policy domain="resource" name="map" value="1000MiB"/>
  <!-- <policy domain="resource" name="area" value="1gb"/> -->
  <policy domain="resource" name="disk" value="10000MiB"/>
  <!-- <policy domain="resource" name="file" value="768"/> -->
  <policy domain="resource" name="thread" value="1"/>
  <policy domain="resource" name="throttle" value="50"/>
  <!-- <policy domain="resource" name="time" value="3600"/> -->
</policymap>
```

此外，在 *configure.xml* 檔案（或設定環境變數） `MAGIC_TEMPORARY_PATH`)到具有足夠空間和IOPS的磁碟分區。

>[!CAUTION]
>
>如果ImageMagick使用所有可用磁碟空間，配置錯誤可能會使伺服器不穩定。 使用ImageMagick處理大型檔案所需的策略更改可能會影響 [!DNL Experience Manager] 效能。 如需詳細資訊，請參閱 [安裝和配置ImageMagick](best-practices-for-imagemagick.md).

>[!NOTE]
>
>ImageMagick `policy.xml` 和 `configure.xml` 檔案可能位於 `/usr/lib64/ImageMagick-*/config/` 而非 `/etc/ImageMagick/`. 請參閱 [ImageMagick檔案](https://www.imagemagick.org/script/resources.php) 以取得設定檔案位置的詳細資訊。

如果您使用 [!DNL Experience Manager] 如果您打算處理大量大型PSD或PSB檔案，請在Adobe Managed Services(AMS)上聯絡Adobe客戶支援。 Experience Manager 可能無法處理超過 30000 x 23000 像素的極高解析度 PSB 檔案。

<!-- 

#### Sub-asset generation and page extraction {#sub-asset-generation-and-page-extraction}

During asset uploads, AEM's workflow creates a separate asset for each page in PDF and Office documents. Each of these pages is an asset by itself, which consumes additional disk space, requires versioning and additional workflow processing. If you do not require separate pages, disable Sub Asset Generation and Page Extraction.

To disable Sub Asset generation, do the following:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Models]** tab
1. Double click the **[!UICONTROL DAM Update Asset]** workflow model
1. Delete **[!UICONTROL Process Sub Asset]** step from **[!UICONTROL DAM Update Asset]** workflow model.

1. Click on **[!UICONTROL Save]**

To disable Page Extraction:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Launchers]** tab
1. Select a launcher that launches **[!UICONTROL DAM Parse Word Documents]** workflow model 
1. Click **[!UICONTROL Edit]**
1. Select **[!UICONTROL Disable]**
1. Click **[!UICONTROL OK]**
1. Repeat steps 3-6 for other launcher items that use **DAM Parse Word Documents **workflow model 

-->

<!--
# Sub-asset generation and page extraction {#sub-asset-generation-and-page-extraction}

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).

During asset uploads, AEM's workflow creates a separate asset for each page in PDF and Office documents. Each of these pages is an asset by itself, which consumes additional disk space, requires versioning and additional workflow processing. If you do not require separate pages, disable Sub Asset Generation and Page Extraction.

To disable Sub Asset generation, do the following:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Models]** tab
1. Double click the **[!UICONTROL DAM Update Asset]** workflow model
1. Delete **[!UICONTROL Process Sub Asset]** step from **[!UICONTROL DAM Update Asset]** workflow model.

1. Click on **[!UICONTROL Save]**

To disable Page Extraction:

1. Open the **[!UICONTROL Workflow Console]** tool by going to */libs/cq/workflow/content/console.html*

1. Select the **[!UICONTROL Launchers]** tab
1. Select a launcher that launches **[!UICONTROL DAM Parse Word Documents]** workflow model.
1. Click **[!UICONTROL Edit]**
1. Select **[!UICONTROL Disable]**
1. Click **[!UICONTROL OK]**
1. Repeat steps 3-6 for other launcher items that use **DAM Parse Word Documents** workflow model.
-->

### XMP回寫 {#xmp-writeback}

XMP回寫會在AEM中修改中繼資料時更新原始資產，結果如下：

* 資產本身已修改
* 資產的版本已建立
* 對資產執行DAM更新資產

所列結果消耗了大量資源。 因此，Adobe建議 [禁用XMP回寫](https://helpx.adobe.com/experience-manager/kb/disable-xmp-writeback.html)，若非必要。

如果已勾選執行工作流程標幟，匯入大量中繼資料可能會導致耗用大量資源的XMP回寫活動。 在精益伺服器使用期間規劃此類匯入，以免其他使用者的效能受到影響。

## 複製 {#replication}

將資產複製至大量發佈執行個體時（例如在Sites實作中）,Adobe建議您使用鏈式復寫。 在這種情況下，製作例項會複製到單一發佈例項，然後複製到其他發佈例項，釋放製作例項。

### 配置鏈複製 {#configure-chain-replication}

1. 選擇要用於將複製連結到
1. 在該發佈執行個體上，新增指向其他發佈執行個體的復寫代理
1. 在這些復寫代理上，啟用 **[!UICONTROL 接收時]** 在 **[!UICONTROL 觸發器]** 標籤

>[!NOTE]
>
>Adobe不建議自動啟用資產。 不過，如有需要，Adobe建議您將此作為工作流程的最後一步，通常是DAM更新資產。

## 搜索索引 {#search-indexes}

請務必實作最新的Service Pack和效能相關Hotfix，因為它們通常包含系統索引的更新。 請參閱 [效能調校提示 | 6.x](https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html) ，以根據您的AEM版本來最佳化可套用的索引。

為您經常運行的查詢建立自定義索引。 如需詳細資訊，請參閱 [分析慢速查詢的方法](https://aemfaq.blogspot.com/2014/08/oak-query-log-file-analyzer-tool.html) 和 [自訂索引](/help/sites-deploying/queries-and-indexing.md). 如需查詢和索引最佳實務的其他相關分析，請參閱 [查詢和建立索引的最佳實務](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

### Lucene索引配置 {#lucene-index-configurations}

您可以對Oak索引設定進行一些最佳化，以協助改善 [!DNL Experience Manager] 資產效能：

更新LuceneIndexProvider配置：

1. 導覽至/system/console/configMgrorg.apache.jackrabbit.oak.plugins.index.lucene.LuceneIndexProviderService
1. 啟用 **[!UICONTROL CopyOnRead 、 CopyOnWrite和預先擷取索引檔案]** 在舊版中 [!DNL Experience Manager] 6.2.這些值預設會在 [!DNL Experience Manager] 6.2及更新版本。

更新索引配置以改進重新索引時間：

1. 開啟CRXDe /crx/de/index.jsp並以管理使用者身分登入
1. 瀏覽至/oak:index/lucene
1. 新增字串[] 已命名的屬性 **[!UICONTROL excludedPaths]** 值為「/var」、「/etc/workflow/instances」和「/etc/replication」時，
1. 瀏覽至/oak:index/damAssetLucene
1. 新增字串[] 已命名的屬性 **[!UICONTROL includedPaths]** 具有一個值「/content/dam」
1. 儲存

(僅限AEM6.1和6.2)更新ntBaseLucene索引以改善資產刪除和移動效能：

1. 瀏覽至 */oak:index/ntBaseLucene/indexRules/nt:base/properties*
1. 添加兩個nt：非結構化節點 **[!UICONTROL slingResource]** 和 **[!UICONTROL damResolvedPath]** 在 */oak:index/ntBaseLucene/indexRules/nt:base/properties*
1. 在節點上設定以下屬性（其中ordered和propertyIndex屬性屬於類型） *布林值*:

   slingResource

   name=&quot;sling:resource&quot;

   ordered=false

   propertyIndex= true

   type=&quot;String&quot;

   damResolvedPath

   name=&quot;dam:resolvedPath&quot;

   ordered=false

   propertyIndex=true

   type=&quot;String&quot;

1. 在/oak:index/ntBaseLucene節點上，設定屬性 `reindex=true`
1. 按一下 **[!UICONTROL 全部儲存]**
1. 監視error.log以查看何時完成索引：

   已完成索引的重新索引： [/oak:index/ntBaseLucene]

1. 您也可以看到已完成索引，方法是重新整理CRXDe中的/oak:index/ntBaseLucene節點，因為重新索引屬性會回復為false
1. 索引完成後，返回CRXDe並設定 **[!UICONTROL type]** 這兩個索引上的屬性

   * */oak:index/slingResource*
   * */oak:index/damResolvedPath*

1. 按一下 **[!UICONTROL 全部儲存]**

禁用Lucene文本提取：

如果您的使用者不需要搜尋資產內容(例如搜尋PDF檔案中包含的文字)，則您可以停用此功能來改善索引效能。

1. 前往 [!DNL Experience Manager] 套件管理程式/crx/packmgr/index.jsp
1. 上傳並安裝以下套件

[取得檔案](assets/disable_indexingbinarytextextraction-10.zip)

### 猜測總計 {#guess-total}

建立生成大型結果集的查詢時，請使用 `guessTotal` 參數，以避免執行時記憶體使用率過高。

## 已知問題 {#known-issues}

### 大型檔案 {#large-files}

與AEM中的大型檔案有兩個主要的已知問題。 當檔案的大小大於2 GB時，冷備用同步可能會出現記憶體不足的情況。 在某些情況下，它會阻止備用同步運行。 在其他情況下，會造成主要執行個體當機。 此情境適用於 [!DNL Experience Manager] 大於2GB，包括內容套件。

同樣，當檔案在使用共用S3資料儲存時達到2GB大小時，檔案可能需要一些時間才能從快取完全保存到檔案系統。 因此，使用無二進位複製時，可能無法在複製完成之前保存二進位資料。 此情況可能會導致問題，尤其是如果資料的可用性很重要，例如在卸載情況下。

## 效能測試 {#performance-testing}

每 [!DNL Experience Manager] 部署，建立效能測試制度，以便快速發現並解決瓶頸。 以下是需要關注的一些關鍵領域。

### 網路測試 {#network-testing}

針對客戶的所有網路效能問題，請執行以下任務：

* 從客戶網路內測試網路效能
* 從Adobe網路內測試網路效能。 若為AMS客戶，請與您的CSE合作，從Adobe網路內進行測試。
* 從另一個接入點測試網路效能
* 使用網路基準工具
* 對Dispatcher進行測試

### [!DNL Experience Manager] 執行個體測試 {#aem-instance-testing}

要通過高效的CPU利用率和負載共用來最大限度地減少延遲並實現高吞吐量，請監視您的 [!DNL Experience Manager] 例項。 特別是：

* 對 [!DNL Experience Manager] 執行個體
* 監控上傳效能和UI回應

## [!DNL Experience Manager] 資產績效檢查清單 {#aem-assets-performance-checklist}

* 啟用HTTPS來繞過任何企業HTTP流量偵測器。
* 使用有線連線上傳大量資產。
* 設定最佳JVM參數。
* 配置檔案系統DataStore或S3 DataStore。
* 停用子資產產生。 如果已啟用，AEM工作流程會為多頁資產中的每個頁面建立個別資產。 這些頁面都是個別資產，會耗用額外的磁碟空間、需要版本設定，以及處理額外的工作流程。 如果您不需要個別頁面，請停用子資產產生和頁面擷取活動。
* 啟用暫時性工作流程。
* 調整Granite工作流程佇列，以限制同時執行的工作。
* 配置ImageMagick以限制資源消耗。
* 從「DAM更新資產」工作流程中移除不必要的步驟。
* 設定工作流程和版本清除。
* 優化Lucene索引配置。
* 使用最新的Service Pack和Hotfix來最佳化索引。 請向Adobe客戶支援洽詢任何其他可用的索引最佳化。
* 使用 `guessTotal` 以最佳化查詢效能。
* 如果您設定 [!DNL Experience Manager] 從檔案的內容檢測檔案類型(通過配置 [!UICONTROL Day CQ DAM Mime類型服務] 在 [!UICONTROL [!DNL Experience Manager] Web主控台])，請在非尖峰時段大量上傳許多檔案，因為操作耗用大量資源。

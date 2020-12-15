---
title: 資產規模指南
description: '最佳實務，可判斷評估部署AEM Assets所需基礎架構和資源的有效度量。 '
uuid: f847c07d-2a38-427a-9c38-8cdca3a1210c
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 82c1725e-a092-42e2-a43b-72f2af3a8e04
translation-type: tm+mt
source-git-commit: 6aec5927c00f70ce2c044ffd56cabbf68a81071a
workflow-type: tm+mt
source-wordcount: '1856'
ht-degree: 0%

---


# 資產規模調整指南{#assets-sizing-guide}

在調整Adobe Experience Manager(AEM)Assets實作環境的大小時，請務必確保在磁碟、CPU、記憶體、IO和網路總處理能力方面有充足的可用資源。 確定這些資源的數量需要瞭解系統中載入了多少資產。 如果沒有更佳的量度，您可以將現有資料庫的大小除以資料庫的年齡，以找出建立資產的比率。

## 磁碟{#disk}

### DataStore {#datastore}

在調整資產實作所需磁碟空間大小時，常會出錯的一個常見錯誤，是根據要傳入系統的原始影像大小來計算。 依預設，AEM會除原始影像外，建立三個轉譯，以用於轉譯AEM UI元素。 在先前的實作中，觀察到這些轉譯假設的資產大小是所擷取資產的兩倍。

除了現成可用的轉譯外，大部分使用者都會定義自訂轉譯。 除了轉譯外，AEM Assets還可讓您從常用檔案類型（例如InDesign和Illustrator）擷取子資產。

最後，AEM的版本控制功能會將資產的復本儲存在版本記錄中。 您可以經常設定要清除的版本。 但是，許多用戶選擇長時間保留系統中的版本，這會佔用更多儲存空間。

考慮到這些因素，您需要一種方法來計算可接受的精確儲存空間，以儲存用戶資產。

1. 確定要載入到系統中的資產的大小和數量。
1. 取得要上傳至AEM的資產的代表性範例。 例如，如果您打算將PSD、JPG、AI和PDF檔案載入系統，則需要每個檔案格式的多張範例影像。 此外，這些範例應代表不同檔案大小和複雜的影像。
1. 定義要使用的轉譯。
1. 使用ImageMagick或Adobe的Creative Cloud應用程式在AEM中建立轉譯。 除了使用者指定的轉譯外，還可建立立即可用的轉譯。 對於實作Scene7的使用者，您可以使用IC二進位檔產生要儲存在AEM中的PTIFF轉譯。
1. 如果您打算使用子資產，請針對適當的檔案類型產生子資產。 請參閱線上檔案，瞭解如何從InDesign檔案產生子頁面，或從Illustrator圖層產生PNG/PDF檔案。
1. 比較輸出影像、轉譯和子資產與原始影像的大小。 它允許您在載入系統時生成預期的增長系數。 例如，如果您在處理1GB的資產後，產生合併大小為3GB的轉譯和子資產，轉譯的增長率是3。
1. 確定資產版本在系統中維護的最長時間。
1. 確定系統中修改現有資產的頻率。 如果AEM是創意工作流程中的協作中心，變更的數量就會很高。 如果僅將完成的資產上傳到系統，則此數字會低得多。
1. 確定每個月有多少資產載入到系統。 如果您不確定，請確定目前可用的資產數目，並除以最舊資產的年齡，以計算大致數目。

執行步驟1-9可協助您判斷下列項目：

* 要載入的資產的原始大小
* 要載入的資產數
* 轉譯增長率
* 每月進行的資產修改數
* 維護資產版本的月數
* 每月載入的新資產數
* 分配空間的年份增長

您可以在「網路規模」試算表中指定這些數字，以決定您的資料儲存所需的總空間。 此外，它也是判斷維護資產版本或修改AEM中資產對磁碟成長影響的實用工具。

工具中填入的範例資料說明執行上述步驟的重要性。 如果僅根據要載入的原始映像(1TB)對資料儲存區進行大小調整，則可能將儲存庫大小低估了15倍。

[取得檔案](assets/disk_sizing_tool.xlsx)

### 共用資料儲存{#shared-datastores}

對於大型資料儲存，您可以通過網路連接驅動器上的共用檔案資料儲存或通過S3資料儲存來實施共用資料儲存。 在這種情況下，個別執行個體不需要維護二進位檔的副本。 此外，共用資料儲存有助於無二進位複製，並有助於減少將資產複製到發佈環境或卸載實例的頻寬。

#### 使用案例{#use-cases}

資料儲存可在主實例和備用作者實例之間共用，以最小化在主實例中進行更改以更新備用實例所花費的時間。 Adobe建議在主要作者實例和卸載作者實例之間共用資料儲存，以減少工作流卸載的開銷。 您也可以在作者和發佈實例之間共用資料儲存，以最大限度地減少複製過程中的流量。

#### 缺點{#drawbacks}

由於有一些缺陷，因此不建議在所有情況下共用資料儲存。

#### 單點故障{#single-point-of-failure}

有共用資料儲存，在基礎架構中引入單點故障。 假設您的系統有一個作者和兩個發佈實例，每個實例都有自己的資料儲存。 如果其中任何一個崩潰，其他兩個仍然可以繼續運行。 但是，如果資料儲存是共用的，則單個磁碟故障可能會破壞整個基礎架構。 因此，請確保您維護共用資料儲存的備份，以便從中快速恢復資料儲存。

與常規磁碟體系結構相比，為共用資料儲存部署AWS S3服務是首選，因為它顯著降低了故障的可能性。

#### 複雜性增加{#increased-complexity}

共用資料儲存區也會增加作業的複雜性，例如廢棄項目收集。 通常，按一下即可啟動獨立資料儲存的廢棄項目收集。 但是，共用資料儲存除了在單個節點上運行實際收集外，還需要對使用資料儲存的每個成員執行標籤掃描操作。

對於AWS操作，實施單個中心位置（通過S3），而不是構建EBS卷的RAID陣列，可以顯著抵消系統的複雜性和操作風險。

#### 效能顧慮{#performance-concerns}

共用資料儲存要求二進位檔案儲存在所有實例之間共用的網路掛載驅動器上。 由於這些二進位檔案是通過網路訪問的，因此系統效能會受到負面影響。 通過使用快速網路連接到快速磁碟陣列，可以部分減輕此影響。 然而，這是個昂貴的提議。 對於AWS操作，所有磁碟都是遠程的，需要網路連接。 臨時卷在實例啟動或停止時丟失資料。

#### 延遲{#latency}

S3實現中的延遲由背景寫入線程引入。 備份過程必須考慮此延遲和任何卸載過程。 當卸載作業開始時，S3資產可能不存在於S3中。 此外，在進行備份時，Lucene索引可能仍不完整。 它適用於寫入S3資料儲存並從其他實例訪問的任何時間敏感檔案。

### 節點儲存／文檔儲存{#node-store-document-store}

由於NodeStore或DocumentStore所消耗的資源，因此很難獲得精確的NodeStore或DocumentStore大小：

* 資產中繼資料
* 資產版本
* 審核日誌
* 封存和作用中的工作流程

由於二進位檔案儲存在資料儲存中，因此每個二進位檔案都佔用了一些空間。 大多數儲存庫的大小都低於100GB。 但是，可能存在大到1TB的較大儲存庫。 此外，要執行離線壓縮，需要在卷上有足夠的可用空間以在預壓縮版本旁邊重寫壓縮的儲存庫。 一個很好的經驗法則是，將磁碟的大小調整為儲存庫預期大小的1.5倍。

對於儲存庫，請使用IOPS級別大於3000的SSD或磁碟。 為避免IOPS引入效能瓶頸的可能性，請監控CPU IO等待級別，以發現問題的早期跡象。

[取得檔案](assets/aem_environment_sizingtool.xlsx)

## 網路{#network}

AEM Assets有許多使用案例，讓網路效能比我們許多AEM專案更重要。 客戶可以擁有快速的伺服器，但如果網路連線不夠大，無法支援從系統上傳和下載資產的使用者負載，則仍會顯得緩慢。 在[AEM Asset的使用者體驗（例項調整、工作流程評估和網路拓撲](assets-network-considerations.md)）考量中，有一套良好的方法可判斷使用者與AEM的網路連線中的阻塞點。

## WebDAV {#webdav}

如果您將AEM案頭應用程式加入組合中，網路問題會更嚴重，因為WebDAV通訊協定效率不彰。

為了說明這些效率低下的問題，Adobe在OS X上使用WebDAV測試了系統效能。開啟、編輯3.5MB的InDesign檔案，並儲存變更。 有人提出以下意見：

* 總共產生約100個HTTP要求，以完成作業
* 檔案已透過HTTP上傳四次
* 檔案已透過HTTP下載一次
* 整個操作用了42秒完成
* 共傳輸18MB資料

在分析WebDAV上檔案的平均儲存時間時，發現效能會隨著頻寬的增加而大幅提升，直到5-10Mbps等級。 因此，Adobe建議同時存取系統的每位使用者至少應有10Mbps的上傳速度和5-10Mbps的頻寬。

如需詳細資訊，請參閱「疑難排解AEM案頭應用程式」[。](https://helpx.adobe.com/experience-manager/kb/troubleshooting-companion-app.html)

## 限制 {#limitations}

在調整實施規模時，請務必牢記系統限制。 如果建議的實作超過這些限制，請運用創意策略，例如將資產分割為多個資產實作。

檔案大小並非導致記憶體不足(OOM)問題的唯一因素。 這也取決於影像的尺寸。 啟動AEM時，提供較高的堆積大小，以避免OOM問題。

此外，您還可以編輯配置管理器中`com.day.cq.dam.commons.handler.StandardImageHandler`元件的閾值大小屬性，以使用大於零的中間臨時檔案。

## 資產數目上限{#maximum-number-of-assets}

<!-- Currently, Adobe has not tested the system for loading greater than 8 million assets. There are limitations both on the number of documents that can exist in an Oak repository and the number of files that can exist in a datastore.

While the limit for the number of nodes in a repository has not been determined, assuming each asset generates roughly 30 nodes, putting the 8 million asset test at 240 million nodes from the assets alone. This does not include audit logs, archived workflows, or versions. -->

由於檔案系統限制，資料儲存中可存在的檔案數限制為21億。 儲存庫在達到資料儲存限制之前，很可能會由於節點數過多而遇到問題。

如果轉譯產生不正確，請使用Camera Raw程式庫。 但是，在這種情況下，影像的最長邊不應大於65000像素。 此外，影像不應包含512 MP(512 &amp;ast;1024 &amp;ast;1024像素)」。 *資產規模無關緊要*。

AEM的特定堆疊支援的TIFF檔案(OOTB)大小很難精確估計，因為其他因素（例如像素大小影響處理）。 AEM可能會處理大小為255 MB OOTB的檔案，但無法處理大小為18 MB的檔案，因為後者包含的像素數比前者高得多。

## 資產大小{#size-of-assets}

依預設，AEM可讓您上傳檔案大小高達2 GB的資產。 若要在AEM中上傳超大型資產，請參閱[上傳超大型資產的設定](managing-video-assets.md#configuration-to-upload-video-assets-that-are-larger-than-gb)。

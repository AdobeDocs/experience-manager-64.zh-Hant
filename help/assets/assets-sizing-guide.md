---
title: Assets 規模調整指南
description: 確定用於評估部署所需的基礎架構和資源的有效指標的最佳實踐 [!DNL Experience Manager] 資產。
uuid: f847c07d-2a38-427a-9c38-8cdca3a1210c
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 82c1725e-a092-42e2-a43b-72f2af3a8e04
feature: Asset Management
role: Architect,Admin
exl-id: 6115e5e8-9cf5-417c-91b3-0c0c9c278b5b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1876'
ht-degree: 0%

---

# Assets 規模調整指南 {#assets-sizing-guide}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

調整Adobe Experience Manager Assets實作的環境大小時，務必確保在磁碟、CPU、記憶體、IO和網路吞吐量方面有足夠的可用資源。 若要調整其中許多資源的大小，必須了解有多少資產正在載入到系統中。 如果沒有更好的量度，您可以將現有程式庫的大小除以程式庫的年齡，以找出建立資產的速率。

## 磁碟 {#disk}

### DataStore {#datastore}

調整資產實施所需的磁碟空間大小時，常會發生錯誤，即根據要擷取至系統的原始影像大小計算。 依預設， [!DNL Experience Manager] 除了原始影像外，還會建立三個轉譯，以用於轉譯 [!DNL Experience Manager] UI元素。 在先前的實作中，觀察到這些轉譯會假設的資產大小是擷取資產的兩倍。

除了現成可用的轉譯外，大部分使用者都會定義自訂轉譯。 除了轉譯外，「資產」還可讓您從常見的檔案類型(例如InDesign和Illustrator)擷取子資產。

最後，AEM版本設定功能會儲存版本記錄中資產的重複項目。 您可以經常設定要清除的版本。 但是，許多用戶選擇長時間保留系統中的版本，這會佔用更多的儲存空間。

考慮到這些因素，您需要一種方法來計算可接受的準確儲存空間以儲存用戶資產。

1. 決定要載入至系統的資產大小和數量。
1. 取得要上傳至AEM的資產的代表性範例。 例如，如果您打算將PSD、JPG、AI和PDF檔案載入到系統中，則需要每個檔案格式的多個示例影像。 此外，這些示例應代表不同的檔案大小和影像的複雜性。
1. 定義要使用的轉譯。
1. 在中建立轉譯 [!DNL Experience Manager] 使用ImageMagick或Adobe的Creative Cloud應用程式。 除了使用者指定的轉譯外，還可建立現成可用的轉譯。 對於實作Dynamic Media Classic的使用者，您可以使用IC二進位檔來產生要儲存在AEM中的PTIFF轉譯。
1. 如果您打算使用子資產，請針對適當的檔案類型產生子資產。 請參閱線上檔案，了解如何從InDesign檔案產生子頁面，或從Illustrator圖層產生PNG/PDF檔案。
1. 比較輸出影像、轉譯和子資產與原始影像的大小。 它允許您在載入系統時生成預期的增長因子。 例如，如果您在處理1GB資產後產生轉譯和子資產，其總大小為3GB，則轉譯增長因數為3。
1. 決定系統中要維護資產版本的最長時間。
1. 決定系統中修改現有資產的頻率。 若 [!DNL Experience Manager] 是創意工作流程中的共同作業中心，變更的數量相當多。 如果只將已完成的資產上傳至系統，則此數字會低很多。
1. 決定每月要將多少資產載入系統中。 如果您不確定，請確定目前可用的資產數量，並將數量除以最舊資產的年齡，以計算約數。

執行步驟1-9可協助您判斷下列項目：

* 要載入的資產原始大小
* 要載入的資產數
* 轉譯增長因子
* 每月進行的資產修改數
* 維護資產版本的月數
* 每月載入的新資產數
* 分配空間的年增長

您可以在網路規模試算表中指定這些數字，以決定資料存放區所需的總空間。 此外，它也是判斷維護資產版本或修改資產對 [!DNL Experience Manager] 磁碟增長。

填入工具中的範例資料說明執行上述步驟的重要性。 如果您僅根據要載入的原始影像來調整資料存放區的大小(1TB)，您可能已將存放庫大小低估了15倍。

[取得檔案](assets/disk_sizing_tool.xlsx)

### 共用資料存放區 {#shared-datastores}

對於大型資料存放區，您可以透過網路連接硬碟上的共用檔案資料存放區或S3資料存放區來實作共用資料存放區。 在這種情況下，個別執行個體不需要維護二進位檔的復本。 此外，共用資料存放區可促進無二進位檔復寫，並有助於減少將資產複製至發佈環境或卸載例項的頻寬。

#### 使用案例 {#use-cases}

資料存放區可在主要製作執行個體和備用製作執行個體之間共用，以將更新備用執行個體與主要執行個體中所做變更所花費的時間減至最少。 Adobe建議在主要製作例項和卸載製作例項之間共用資料存放區，以減少工作流程卸載時的開銷。 您也可以在製作與發佈執行個體之間共用資料存放區，以將復寫期間的流量減至最少。

#### 缺點 {#drawbacks}

由於有些缺陷，因此不建議在所有情況下共用資料存放區。

#### 單點故障 {#single-point-of-failure}

有共用資料儲存，會在基礎架構中引入單點故障。 假設您的系統有一個製作和兩個發佈執行個體，每個都有自己的資料存放區。 如果其中任何一個崩潰，其他兩個仍然可以繼續運行。 但是，如果資料儲存被共用，則單個磁碟故障可能會破壞整個基礎架構。 因此，請務必維護共用資料存放區的備份，以便快速還原資料存放區。

更偏好將AWS S3服務部署至共用資料存放區，因為與一般磁碟架構相比，這可大幅降低失敗的機率。

#### 增加複雜性 {#increased-complexity}

共用資料儲存區也增加了操作的複雜性，例如垃圾收集。 通常，只需按一下即可啟動獨立資料儲存的垃圾收集。 但是，共用資料儲存區除了在單個節點上運行實際集合之外，還需要對使用資料儲存的每個成員執行標籤掃描操作。

對於AWS操作，實施單個中央位置（通過S3），而不是構建EBS卷的RAID陣列，可以顯著抵消系統的複雜性和操作風險。

#### 績效考量 {#performance-concerns}

共用資料存放區需要將二進位檔案儲存在所有執行個體之間共用的網路裝載驅動器上。 由於這些二進位檔是透過網路存取，因此系統效能會受到不利影響。 通過使用快速網路連接到快速磁碟陣列，可以部分減輕影響。 然而，這是個代價高昂的提議。 在AWS操作中，所有磁碟都是遠程磁碟，需要網路連接。 執行個體啟動或停止時，短暫的卷會丟失資料。

#### 延遲性 {#latency}

S3實作中的延遲是由背景寫入執行緒所引入。 備份過程必須考慮此延遲和任何卸載過程。 卸載工作開始時，S3資產可能不存在於S3中。 此外，備份時，Lucene索引可能仍不完整。 它適用於寫入S3資料存放區並從其他執行個體存取的任何時效檔案。

### 節點儲存/文檔儲存 {#node-store-document-store}

由於以下資源消耗，很難獲得NodeStore或DocumentStore的精確大小調整圖：

* 資產中繼資料
* 資產版本
* 稽核記錄
* 封存的作用中工作流程

因為二進位檔會儲存在資料存放區中，每個二進位檔都會佔用一些空間。 大多數儲存庫的大小都低於100GB。 但是，可能會有大到1 TB的儲存庫。 此外，要執行離線壓縮，需要在卷上有足夠的可用空間以在預壓縮版本旁邊重寫壓縮的儲存庫。 經驗法則是，將磁碟的大小調整為儲存庫預期大小的1.5倍。

對於儲存庫，使用IOPS級別大於3000的SSD或磁碟。 要消除IOPS引入效能瓶頸的機會，請監視CPU IO等待級別以發現問題的早期跡象。

[取得檔案](assets/aem_environment_sizingtool.xlsx)

## 網路 {#network}

[!DNL Assets] 有許多使用案例使網路效能比 [!DNL Experience Manager] 專案。 客戶可以擁有快速的伺服器，但如果網路連線不足以支援從系統上傳和下載資產的使用者載入，則速度仍會緩慢。 在確定用戶的網路連接中的阻塞點時，有一種良好的方法 [!DNL Experience Manager] at [[!DNL Experience Manager]  用戶體驗、實例大小、工作流評估和網路拓撲的資產考量](assets-network-considerations.md).

## WebDAV {#webdav}

如果您新增 [!DNL Experience Manager] 案頭應用程式的組合，網路問題變得更加嚴重，因為WebDAV協定效率低下。

為了說明這些低效性，Adobe在OS X上使用WebDAV測試了系統效能。開啟、編輯了3.5MB的InDesign檔案，並保存了更改。 有以下意見：

* 總共生成了約100個HTTP請求，以完成操作
* 檔案已透過HTTP上傳四次
* 檔案已透過HTTP下載一次
* 完成整個操作需要42秒
* 總共傳輸了18 MB的資料

在分析WebDAV上檔案的平均保存時間時，發現效能會隨著頻寬的增加而顯著提高，直到達到5-10Mbps級別。 因此，Adobe建議同時訪問系統的每個用戶至少應具有10Mbps的上載速度和5-10Mbps的頻寬。

如需詳細資訊，請參閱 [疑難排解 [!DNL Experience Manager] 案頭應用程式](https://helpx.adobe.com/experience-manager/kb/troubleshooting-companion-app.html).

## 限制 {#limitations}

調整實作規模時，請務必牢記系統限制。 如果建議的實作超過這些限制，請運用創意策略，例如在多個Assets實作間分割資產。

檔案大小不是導致記憶體不足(OOM)問題的唯一因素。 也取決於影像的尺寸。 在啟動AEM時提供較高的堆大小，可以避免OOM問題。

此外，您也可以編輯 `com.day.cq.dam.commons.handler.StandardImageHandler` 元件，以使用大於零的中間臨時檔案。

## 資產數上限 {#maximum-number-of-assets}

<!-- Currently, Adobe has not tested the system for loading greater than 8 million assets. There are limitations both on the number of documents that can exist in an Oak repository and the number of files that can exist in a datastore.

While the limit for the number of nodes in a repository has not been determined, assuming each asset generates roughly 30 nodes, putting the 8 million asset test at 240 million nodes from the assets alone. This does not include audit logs, archived workflows, or versions. -->

由於檔案系統限制，資料儲存中可能存在的檔案數量限制可能為21億。 在達到資料存放區限制之前，儲存庫很可能會因為節點數過多而遇到問題。

如果轉譯錯誤產生，請使用Camera Raw程式庫。 但是，在此情況下，影像的最長邊不應大於65000像素。 此外，影像不應包含超過512 MP(512 &amp;ast;1024&amp;ast;1024像素)」。 *資產規模無關緊要*.

很難準確估計TIFF檔案的大小，該檔案支援的現成可用(OOTB)具有特定堆 [!DNL Experience Manager] 因為像素大小等其他因素會影響處理。 有可能 [!DNL Experience Manager] 可以處理大小為255 MB OOTB的檔案，但無法處理大小為18 MB的檔案，因為後者包含的像素比前者要高得多。

## 資產規模 {#size-of-assets}

依預設， [!DNL Experience Manager] 可讓您上傳檔案大小高達2 GB的資產。 若要在AEM中上傳超大型資產，請參閱 [上傳超大型資產的設定](managing-video-assets.md#configuration-to-upload-video-assets-that-are-larger-than-gb).

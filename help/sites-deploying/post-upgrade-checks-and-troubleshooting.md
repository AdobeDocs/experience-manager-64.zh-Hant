---
title: 升級後檢查和疑難排解
seo-title: 升級後檢查和疑難排解
description: 了解如何疑難排解升級後可能出現的問題。
seo-description: 了解如何疑難排解升級後可能出現的問題。
uuid: 3f83e8fc-1c45-4ef0-b8da-d29ff483d3d5
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: bc8c9aa2-f669-41f3-a526-6146ff5cf0cd
feature: 升級
exl-id: edd6e933-59ed-4d7e-8934-7e2ec485cfb9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1888'
ht-degree: 0%

---

# 升級後檢查和故障排除{#post-upgrade-checks-and-troubleshooting}

## 升級後檢查{#post-upgrade-checks}

在[就地升級後](/help/sites-deploying/in-place-upgrade.md)應執行下列活動以完成升級。 假設AEM已從6.4 jar啟動，且已部署升級的程式碼基底。

* [驗證升級成功的日誌](#verify-logs-for-upgrade-success)

* [驗證OSGi套件組合](#verify-osgi-bundles)

* [驗證Oak版本](#verify-oak-version)

* [Inspect PreUpgradeBackup資料夾](#inspect-preupgradebackup-folder)

* [頁面的初始驗證](#initial-validation-of-pages)
* [套用AEM Service Pack](#apply-aem-service-packs)

* [移轉AEM功能](#migrate-aem-features)

* [驗證計畫維護配置](#verify-scheduled-maintenance-configurations)

* [啟用複製代理](#enable-replication-agents)

* [啟用自訂排程作業](#enable-custom-scheduled-jobs)

* [執行測試計畫](#execute-test-plan)

### 驗證升級成功的日誌{#verify-logs-for-upgrade-success}

**upgrade.log**

過去，檢查執行個體的升級後狀態需要仔細檢查各種記錄檔、存放庫的部分和啟動面板。 產生升級後報表有助於在上線前偵測有缺陷的升級。

此功能的主要用途是減少需要手動解釋或跨多個端點執行複雜解析邏輯，才能判斷升級是否成功。 該解決方案旨在為外部自動化系統提供明確的資訊，以便對更新的成功或已識別的失敗做出反應。

更具體來說，它可確保：

* 升級框架檢測到的升級故障可以集中在單個升級報告中；
* 升級報告包括關於必要手動干預的指標。

為了解決此問題，已對`upgrade.log`檔案中產生記錄檔的方式進行變更。

以下範例報表在升級期間未顯示任何錯誤：

![1487887443006](assets/1487887443006.png)

以下範例報表顯示升級程式期間未安裝的套件組合：

![1487887532730](assets/1487887532730.png)

**error.log**

在使用目標版本jar啟動AEM期間和之後，應仔細檢閱error.log。 應審核任何警告或錯誤。 一般而言，最好在記錄的開頭尋找問題。 記錄中稍後發生的錯誤實際上可能是在檔案早期調用的根本原因的副作用。 如果出現重複的錯誤和警告，請參閱下面的[分析升級的問題。](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md#analyzing-issues-with-upgrade)

### 驗證OSGi套件組合{#verify-osgi-bundles}

導覽至OSGi主控台`/system/console/bundles`，並查看是否有任何套件組合未啟動。 如果任何套件組合處於已安裝狀態，請諮詢`error.log`以判斷根問題。

### 驗證Oak版本{#verify-oak-version}

升級後，您應會看到Oak版本已更新至&#x200B;**1.8.2**。 若要驗證Oak版本，請導覽至OSGi主控台，並查看與Oak套件組合相關聯的版本：Oak Core、Oak Commons、Oak Segment Tar。

### Inspect PreUpgradeBackup資料夾{#inspect-preupgradebackup-folder}

在升級期間，AEM會嘗試備份自訂內容，並將其儲存在`/var/upgrade/PreUpgradeBackup/<time-stamp-of-upgrade>`下方。 若要以CRXDE Lite方式查看此資料夾，您可能需要[暫時啟用CRXDE Lite](/help/sites-administering/enabling-crxde-lite.md)。

具有時間戳的資料夾應具有名為`mergeStatus`且值為`COMPLETED`的屬性。 **to-process**&#x200B;資料夾應為空，而&#x200B;**被覆寫**&#x200B;節點指示在升級期間已覆寫哪些節點。 **pendlits**&#x200B;節點下方的內容表示升級期間無法安全合併的內容。 如果您的實作相依於任何子節點（且升級的程式碼套件尚未安裝），則需要手動合併這些節點。

在「預備」或「生產」環境中，停用本練習後的CRXDE Lite。

### 頁面{#initial-validation-of-pages}的初始驗證

對AEM中的數個頁面執行初始驗證。 如果升級製作環境，請開啟「開始」頁面和「歡迎」頁面(`/aem/start.html`, `/libs/cq/core/content/welcome.html`)。 在製作和發佈環境中，會開啟幾個應用程式頁面並煙霧測試，讓它們可正確呈現。 如果發生任何問題，請洽詢`error.log`以進行疑難排解。

### 套用AEM Service Pack {#apply-aem-service-packs}

套用任何相關的AEM 6.4 Service Pack（若已發行）。

### 遷移AEM功能{#migrate-aem-features}

AEM中的數項功能需要進行升級後執行其他步驟。 您可以在[升級代碼和自訂](/help/sites-deploying/upgrading-code-and-customizations.md)頁面上找到這些功能的完整清單以及在AEM 6.4中移轉這些功能的步驟。

### 驗證計畫維護配置{#verify-scheduled-maintenance-configurations}

#### 啟用資料儲存垃圾收集{#enable-data-store-garbage-collection}

如果使用檔案資料儲存，請確保資料儲存垃圾收集任務已啟用並添加到每週維護清單中。 說明如下： [此處](/help/sites-administering/data-store-garbage-collection.md)。

>[!NOTE]
>
>S3自訂資料存放區安裝或使用共用資料存放區時，不建議使用此設定。

#### 啟用線上修訂清除{#enable-online-revision-cleanup}

如果使用MongoMK或新的TarMK區段格式，請確定已啟用修訂清除任務，並將其新增至每日維護清單。 說明列於[此處](/help/sites-deploying/revision-cleanup.md)。

### 執行測試計畫{#execute-test-plan}

根據&#x200B;**測試過程**&#x200B;部分下定義的[升級代碼和自定義](/help/sites-deploying/upgrading-code-and-customizations.md)執行詳細測試計畫。

### 啟用複製代理{#enable-replication-agents}

發佈環境完全升級和驗證後，請在製作環境上啟用復寫代理。 驗證代理程式是否能連線至個別的發佈執行個體。 有關事件順序的詳細資訊，請參閱[升級過程](/help/sites-deploying/upgrade-procedure.md)。

### 啟用自定義計畫作業{#enable-custom-scheduled-jobs}

此時，任何程式碼基底中的已排程作業都可啟用。

## 分析升級{#analyzing-issues-with-upgrade}的問題

本節包含在升級至AEM 6.4程式時可能會遇到的問題情況。

這些案例應有助於追蹤升級相關問題的根本原因，並有助於識別專案或產品特定問題。

### 在升級{#dynamic-media-cloud-configuration}後重新建立Dynamic Media雲端設定

從舊版升級至AEM 6.4後，從舊版設定的Dynamic Media雲端組態可能無法從AEM 6.4觸控式UI中存取。 若要解決此問題，請使用「CRXDE Lite」移除先前的設定，然後建立新的Dynamic Media雲端設定。 另請參閱AEM 6.4](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md)中的[Dynamic Media存放庫重新調整架構。

### 儲存庫遷移失敗{#repository-migration-failing-}

從CRX2移轉至Oak的資料，應適用於以CQ 5.4為基礎的來源例項開始的任何案例。請務必確實遵循本檔案中的升級指示，包括`repository.xml`的準備工作，確認系統未透過JAAS啟動自訂驗證器，且執行個體在開始移轉前已檢查是否不一致。

如果遷移仍然失敗，則可通過檢查`upgrade.log`查明根本原因。 如果問題尚未知，請向客戶支援部門報告。

### 升級未運行{#the-upgrade-did-not-run}

開始準備步驟之前，請務必使用java -jar aem-quickstart.jar命令執行，以便先執行&#x200B;**source**&#x200B;例項。 這是必需的，以確保正確生成quickstart.properties檔案。 如果缺少，則升級將無法運作。 或者，您也可以查看源實例安裝資料夾中的`crx-quickstart/conf`下，以檢查檔案是否存在。 此外，啟動AEM以開始升級時，必須使用java -jar aem-quickstart.jar命令執行。 在升級模式下，從啟動指令碼啟動不會啟動AEM。

### 包和包無法更新{#packages-and-bundles-fail-to-update-}

如果升級期間無法安裝套件，則其包含的套件組合也不會更新。 此類問題通常是資料儲存配置錯誤所致。 它們也會在error.log中顯示為&#x200B;**ERROR**&#x200B;和&#x200B;**WARN**&#x200B;訊息。 由於在大多數情況下，預設登錄可能無法工作，因此您可以直接使用CRXDE來檢查並查找配置問題。

### 某些AEM套件組合未切換至作用中狀態{#some-aem-bundles-are-not-switching-to-the-active-state}

如果套件組合未啟動，則應檢查是否有未滿足的依賴項。

如果存在此問題，但問題基於失敗的包安裝，導致包無法升級，則它們將被視為與新版本不相容。 如需如何疑難排解此問題的詳細資訊，請參閱上方的&#x200B;**套件和套件組合無法更新**。

建議您將最新AEM 6.4執行個體的套件組合清單與升級的執行個體進行比較，以偵測未升級的套件組合。 這將提供`error.log`中要搜尋內容的更詳細範圍。

### 未切換到活動狀態{#custom-bundles-not-switching-to-the-active-state}的自定義套件組

如果您的自訂套件組合未切換至作用中狀態，則很可能有程式碼未匯入變更API。 這通常會導致未滿足的相依性。

已移除的API應在先前版本中標示為已過時。 在本淘汰通知中，您可能會找到有關直接移轉程式碼的指示。 Adobe旨在盡可能實現語義版本化，以便版本可以指示中斷的更改。

還最好檢查導致問題的更改是否絕對必要，如果不是，則還原它。 另外，在嚴格的語義版本化之後，檢查包導出的版本增加是否超出必要。

### 運行不正常的平台UI {#malfunctioning-platform-ui}

若升級後某些UI功能無法正常運作，您應先檢查介面的自訂覆蓋。 某些結構可能已變更，且覆蓋可能需要更新或已淘汰。

接下來，檢查是否有任何Javascript錯誤，這些錯誤可追蹤至連結至用戶端程式庫的自訂新增擴充功能。 自訂CSS也適用，這可能會導致AEM配置問題。

最後，檢查Javascript可能無法處理的錯誤設定。 停用不當的擴充功能通常會發生此情況。

### 故障的自定義元件、模板或UI擴展{#malfunctioning-custom-components-templates-or-ui-extensions}

在大多數情況下，這些問題的根本原因與未啟動的套件或未安裝的套件的根本原因相同，而問題最初使用元件時發生的唯一差異。

處理錯誤自訂程式碼的方式是先進行煙霧測試，以找出原因。 找到建議後，請查看文章[link]區段中的建議，以了解修正建議的方式。

### {#missing-customizations-under-etc}下缺少自定義項

`/apps` 和 `/libs` 已由升級妥善處理，但升級後 `/etc` 可能需要手動還原 `/var/upgrade/PreUpgradeBackup` 下的變更。請務必檢查此位置，以找出需要手動合併的任何內容。

### 分析error.log和upgrade.log {#analyzing-the-error-log-and-upgrade-log}

在大多數情況下，需要查詢日誌以查找錯誤的原因。 但是，在升級時，也必須監控相依性問題，因為舊套件組合可能無法正確升級。

執行此操作的最佳方式是移除所有預期與您所面臨問題無關的訊息，從而刪除error.log 。 您可以透過如grep的工具，使用：

```shell
grep -v UnrelatedErrorString
```

某些錯誤訊息可能無法立即解釋。 在此情況下，查看錯誤發生的上下文也有助於了解錯誤的建立位置。 您可以使用以下項目來區隔錯誤：

* `grep -B` 在錯誤前加行；

或

* `grep -A` 以在後面添加行。

在一些情況下，也可以找到WARN消息，因為可能存在導致此狀態的有效案例，並且應用程式並不總是能夠確定這是否是實際錯誤。 也請務必查詢這些訊息。

### 聯繫Adobe支援{#contacting-adobe-support}

如果您已閱讀本頁的建議，但仍然看到問題，請聯絡Adobe支援。 要向負責您案例的支援工程師提供盡可能多的資訊，請確保從您的升級中包括upgrade.log檔案。

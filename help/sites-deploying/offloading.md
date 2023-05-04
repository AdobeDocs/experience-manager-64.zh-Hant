---
title: 卸載作業
seo-title: Offloading Jobs
description: 了解如何在拓撲中配置和使用AEM實例，以執行特定類型的處理。
seo-description: Learn how to configure and use AEM instances in a topology in order to perform specific types of processing.
uuid: e971d403-dfd2-471f-b23d-a67e35f1ed88
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 370151df-3b8e-41aa-b586-5c21ecb55ffe
feature: Configuring
exl-id: b10bf1b6-0360-45ca-b1aa-f4184cbfb5c0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2818'
ht-degree: 1%

---

# 卸載作業{#offloading-jobs}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 簡介 {#introduction}

卸載分配處理任務量為拓撲中的Experience Manager實例。 透過卸載，您可以使用特定Experience Manager例項來執行特定類型的處理。 專門處理可讓您最大限度地利用可用的伺服器資源。

卸載以 [Apache Sling Discovery](https://sling.apache.org/documentation/bundles/discovery-api-and-impl.html) 和Sling JobManager功能。 要使用卸載，請將Experience Manager群集添加到拓撲，並標識群集處理的作業主題。 叢集由一或多個Experience Manager例項組成，因此將單一例項視為叢集。

有關將實例添加到拓撲的資訊，請參見 [管理拓撲](/help/sites-deploying/offloading.md#administering-topologies).

### 工作分配 {#job-distribution}

Sling JobManager和JobConsumer可建立拓撲中處理的作業：

* 作業管理員：為特定主題建立作業的服務。
* JobConsumer:執行一個或多個主題的作業的服務。 可為同一主題註冊多個JobConsumer服務。

JobManager建立作業時，卸載框架將在拓撲中選擇一個Experience Manager群集以執行該作業：

* 群集必須包含一個或多個運行為作業主題註冊的JobConsumer的實例。
* 群集中必須至少為一個實例啟用該主題。

請參閱 [設定主題耗用量](/help/sites-deploying/offloading.md#configuring-topic-consumption) 以了解如何精簡工作分配。

![chlimage_1-109](assets/chlimage_1-109.png)

當Offloading框架選擇群集以執行作業，且群集由多個實例組成時，Sling Distribution將確定群集中的哪個實例執行該作業。

### 工作負載 {#job-payloads}

卸載框架支援將作業與儲存庫中的資源關聯的作業裝載。 為處理資源建立作業，並將該作業卸載到另一台電腦時，作業裝載非常有用。

建立工作時，裝載只保證位於建立工作的執行個體上。 卸載作業時，複製代理確保在最終取用該作業的執行個體上建立裝載。 作業執行完成時，反向復寫會將裝載複製回建立作業的執行個體。

## 管理拓撲 {#administering-topologies}

拓撲是鬆散耦合的Experience Manager群集，它們參與卸載。 群集由一個或多個Experience Manager伺服器實例（單個實例被視為群集）組成。

每個Experience Manager執行個體會執行下列卸載相關服務：

* 發現服務：向拓撲連接器發送連接拓撲的請求。
* 拓撲連接器：接收加入請求，接受或拒絕每個請求。

拓撲的所有成員的發現服務指向其中一個成員的拓撲連接器。 在以下各節中，此成員稱為根成員。

![chlimage_1-110](assets/chlimage_1-110.png)

拓撲中的每個群集都包含一個被識別為領導者的實例。 群集領導者代表群集的其他成員與拓撲交互。 當領導者離開群集時，將自動選擇群集的新領導者。

### 查看拓撲 {#viewing-the-topology}

使用拓撲瀏覽器來探索Experience Manager實例所參與的拓撲的狀態。 拓撲瀏覽器顯示拓撲的群集和實例。

對於每個群集，您會看到一個群整合員清單，該清單指示每個成員加入群集的順序，以及哪個成員是領導者。 「當前」屬性指示當前管理的實例。

對於群集中的每個實例，您可以看到幾個與拓撲相關的屬性：

* 執行個體之工作使用者的允許主題清單。
* 為連接拓撲而公開的端點。
* 為卸載註冊實例的作業主題。
* 執行個體處理的作業主題。

1. 使用觸控式UI，按一下「工具」標籤。 ([http://localhost:4502/tools.html](http://localhost:4502/tools.html))
1. 在「Granite操作」區域中，按一下「卸載瀏覽器」。
1. 在導航面板中，按一下拓撲瀏覽器。

   將顯示參與拓撲的群集。

   ![chlimage_1-111](assets/chlimage_1-111.png)

1. 按一下群集以查看群集中實例的清單及其ID、當前狀態和領導狀態。
1. 按一下執行個體ID以查看更詳細的屬性。

您也可以使用Web控制台查看拓撲資訊。 控制台提供有關拓撲群集的進一步資訊：

* 哪個執行個體是本機執行個體。
* 此實例用於連接到拓撲（傳出）的拓撲連接器服務，以及連接到此實例（傳入）的服務。
* 更改拓撲和實例屬性的歷史記錄。

使用以下過程開啟Web控制台的「拓撲管理」頁：

1. 在瀏覽器中開啟Web主控台。 ([http://localhost:4502/system/console](http://localhost:4502/system/console))
1. 按一下「主」>「拓撲管理」。

   ![chlimage_1-112](assets/chlimage_1-112.png)

### 配置拓撲成員 {#configuring-topology-membership}

Apache Sling Resource-Based Discovery Service在每個執行個體上執行，以控制Experience Manager執行個體與拓撲互動的方式。

發現服務向拓撲連接器服務發送定期POST請求（心率），以建立和維護與拓撲的連接。 拓撲連接器服務維護允許加入拓撲的IP地址或主機名的允許清單：

* 要將實例連接到拓撲，請指定根成員的拓撲連接器服務的URL。
* 要啟用實例加入拓撲，請將實例添加到根成員的拓撲連接器服務的允許清單中。

使用Web主控台或sling:OsgiConfig節點來設定org.apache.sling.discovery.impt.Config服務的下列屬性：

<table> 
 <tbody> 
  <tr> 
   <th>屬性名稱</th> 
   <th>OSGi名稱</th> 
   <th>說明</th> 
   <th>預設值</th> 
  </tr> 
  <tr> 
   <td>心率逾時（秒）</td> 
   <td>heartbeatTimeout</td> 
   <td>在目標執行個體被視為無法使用之前，等候心率回應的秒數。 </td> 
   <td>20</td> 
  </tr> 
  <tr> 
   <td>心率間隔（秒）</td> 
   <td>heartbeatInterval</td> 
   <td>心率之間的秒數。</td> 
   <td>15</td> 
  </tr> 
  <tr> 
   <td>最小事件延遲（秒）</td> 
   <td>minEventDelay</td> 
   <td><p>當拓撲發生更改時，將狀態從TOPOLOGY_CHANGED延遲到TOPOLOGY_CHANGED的時間。 當狀態為TOPOLOGY_CHANGENG時，每發生一次更改都會將延遲增加此時間量。</p> <p>這種延遲可防止聽眾被事件淹沒。 </p> <p>要不使用延遲，請指定0或負數。</p> </td> 
   <td>3</td> 
  </tr> 
  <tr> 
   <td>拓撲連接器URL</td> 
   <td>topologyConnectorUrl</td> 
   <td>用於發送心率消息的拓撲連接器服務的URL。</td> 
   <td>http://localhost:4502/libs/sling/topology/connector</td> 
  </tr> 
  <tr> 
   <td>拓撲連接器允許清單</td> 
   <td>topologyConnectorWhitelist</td> 
   <td>本地拓撲連接器服務允許的IP地址或主機名清單。 </td> 
   <td><p>localhost</p> <p>127.0.0.1</p> </td> 
  </tr> 
  <tr> 
   <td>儲存庫描述符名稱</td> 
   <td>leaderElectionRepositoryDescriptor</td> 
   <td> </td> 
   <td>&lt;無值&gt;</td> 
  </tr> 
 </tbody> 
</table>

使用以下過程將CQ實例連接到拓撲的根成員。 該過程將實例指向根拓撲成員的拓撲連接器URL。 對拓撲的所有成員執行此過程。

1. 在瀏覽器中開啟Web主控台。 ([http://localhost:4502/system/console](http://localhost:4502/system/console))
1. 按一下「主」>「拓撲管理」。
1. 按一下配置發現服務。
1. 將項添加到拓撲連接器URL屬性，並指定根拓撲成員的拓撲連接器服務的URL。 URL的格式為https://rootservername:4502/libs/sling/topology/connector。

對拓撲的根成員執行以下過程。 該過程將其他拓撲成員的名稱添加到其發現服務允許清單中。

1. 在瀏覽器中開啟Web主控台。 ([http://localhost:4502/system/console](http://localhost:4502/system/console))
1. 按一下「主」>「拓撲管理」。
1. 按一下配置發現服務。
1. 對於拓撲的每個成員，向拓撲連接器允許清單屬性中添加一個項，並指定拓撲成員的主機名或IP地址。

## 設定主題耗用量 {#configuring-topic-consumption}

使用卸載瀏覽器為拓撲中的Experience Manager實例配置主題消耗。 對於每個例項，您可以指定它所取用的主題。 例如，要配置拓撲，以便只有一個實例使用特定類型的主題，請禁用除一個實例之外的所有實例上的主題。

作業是使用循環邏輯啟用相關主題的已分配數量例項。

1. 使用觸控式UI，按一下「工具」標籤。 ([http://localhost:4502/tools.html](http://localhost:4502/tools.html))
1. 在「Granite操作」區域中，按一下「卸載瀏覽器」。
1. 在導覽面板中，按一下卸載瀏覽器。

   會出現卸載主題和可以使用主題的伺服器實例。

   ![chlimage_1-113](assets/chlimage_1-113.png)

1. 若要停用例項主題的耗用，請按一下執行個體旁的topc名稱下方的「停用」 。
1. 若要設定執行個體的所有主題使用，請按一下任何主題下方的執行個體識別碼。

   ![chlimage_1-114](assets/chlimage_1-114.png)

1. 按一下主題旁的以下按鈕之一以配置實例的消耗行為，然後按一下「保存」：

   * 已啟用：此實例將利用此主題的作業。
   * 已禁用：此實例不會使用此主題的作業。
   * 獨家：此例項僅用於此主題的作業。

   **注意：** 為主題選擇「獨佔」時，所有其他主題將自動設定為「禁用」。

### 已安裝的作業消費者 {#installed-job-consumers}

安裝了多個JobConsumer實施，並附帶Experience Manager。 註冊這些JobCondusers的主題顯示在卸載瀏覽器中。 顯示的其他主題是自訂JobCondusers已註冊的主題。 下表介紹了預設的JobCondusers。

| 作業主題 | 服務PID | 說明 |
|---|---|---|
| / | org.apache.sling.event.impl.jobs.deprecated.EventAdminBridge | 與Apache Sling一起安裝。 處理OSGi事件管理員為了回溯相容而產生的作業。 |
| com/day/cq/replication/job/&amp;ast; | com.day.cq.replication.impl.AgentManagerImpl | 復製作業負載的複製代理。 |
| com/adobe/granite/workflow/offloading | com.adobe.granite.workflow.core.offloading.WorkflowOffloadingJobConsumer | 處理DAM更新資產卸載程式工作流程產生的作業。 |

### 停用和啟用執行個體的主題 {#disabling-and-enabling-topics-for-an-instance}

Apache Sling Job Consumer Manager服務提供主題允許清單和封鎖清單屬性。 設定這些屬性以啟用或停用處理Experience Manager例項上的特定主題。

**注意：** 如果實例屬於某個拓撲，則還可以在拓撲中的任何電腦上使用卸載瀏覽器來啟用或禁用主題。

建立啟用主題清單的邏輯首先允許允許清單中的所有主題，然後刪除塊清單上的主題。預設情況下，所有主題都啟用(允許清單值為 `*`)且未停用任何主題（封鎖清單沒有值）。

使用Web主控台或 `sling:OsgiConfig` 節點來設定下列屬性。 針對 `sling:OsgiConfig` 節點，則Job Consumer Manager服務的PID為org.apache.sling.event.impl.jobs.JobConsumerManager。

| Web主控台中的屬性名稱 | OSGi ID | 說明 |
|---|---|---|
| 主題白名單 | job.consumermanager.whitelist | 本地JobManager服務處理的主題清單。 預設值為&amp;ast;會將所有主題發送到註冊的TopicConsumer服務。 |
| 主題黑名單 | job.consumermanager.blacklist | 本地JobManager服務不處理的主題清單。 |

## 建立要卸載的複製代理 {#creating-replication-agents-for-offloading}

卸載框架使用複製在作者和工作者之間傳輸資源。 卸載框架會在實例加入拓撲時自動建立複製代理。 代理將使用預設值建立。 您必須手動更改代理用於驗證的密碼。

>[!CAUTION]
>
>自動生成的複製代理的已知問題要求您手動建立新的複製代理。 依照 [使用自動生成的複製代理時出現問題](/help/sites-deploying/offloading.md#problems-using-the-automatically-generated-replication-agents) 建立卸載代理之前。

建立複製代理，用於在執行個體之間傳輸作業裝載以供卸載。 下圖顯示從作者卸載至背景執行個體所需的代理。 製作者的Sling ID為1，工作執行個體的Sling ID為2:

![chlimage_1-115](assets/chlimage_1-115.png)

此設定需要下列三個代理：

1. 製作實例上的一個外發代理，該代理會複製到工作實例。
1. 製作執行個體上的反向代理，會從背景執行個體上的寄件匣提取。
1. 工作實例上的發件箱代理。

此復寫配置類似於製作與發佈執行個體之間使用的配置。 不過，針對卸載情況，所有相關例項都是製作例項。

>[!NOTE]
>
>卸載框架使用拓撲獲取卸載實例的IP地址。 然後，框架會根據這些IP地址自動建立複製代理。 如果卸載實例的IP地址稍後更改，則在實例重新啟動後，該更改將自動在拓撲上進行提示。 但是，卸載框架不會自動更新複製代理以反映新的IP地址。 要避免這種情況，請對拓撲中的所有實例使用固定的IP地址。

### 為卸載命名複製代理 {#naming-the-replication-agents-for-offloading}

對 ***名稱*** 複製代理的屬性，以便卸載框架自動為特定工作實例使用正確的代理。

**在製作執行個體上命名傳出代理：**

`offloading_<slingid>`，其中 `<slingid>` 是worker執行個體的Sling ID。

範例: `offloading_f5c8494a-4220-49b8-b079-360a72f71559`

**在製作例項上命名反向代理：**

`offloading_reverse_<slingid>`，其中 `<slingid>` 是worker執行個體的Sling ID。

範例: `offloading_reverse_f5c8494a-4220-49b8-b079-360a72f71559`

**在工作執行個體上命名發件箱：**

`offloading_outbox`

### 建立傳出代理 {#creating-the-outgoing-agent}

1. 建立 **復寫代理** 在作者上。 (請參閱 [複製代理的文檔](/help/sites-deploying/replication.md))。 指定任何 **標題**. 此 **名稱** 必須遵循命名慣例。
1. 使用下列屬性建立代理：

   | 屬性 | 值 |
   |---|---|
   | 設定>序列化類型 | 預設 |
   | 傳輸>傳輸URI | https://*`<ip of target instance>`*:*`<port>`*`/bin/receive?sling:authRequestLogin=1` |
   | 傳輸>傳輸用戶 | 目標實例上的複製用戶 |
   | 傳輸>傳輸密碼 | 目標實例上的複製用戶密碼 |
   | 「延伸> HTTP方法」 | POST |
   | 觸發器>忽略預設值 | True |

### 建立反向代理 {#creating-the-reverse-agent}

1. 建立 **反向複製代理** 在作者上。 (請參閱 [複製代理的文檔](/help/sites-deploying/replication.md).) 指定任何 **標題**. 此 **名稱** 必須遵循命名慣例。
1. 使用下列屬性建立代理：

   | 屬性 | 值 |
   |---|---|
   | 設定>序列化類型 | 預設 |
   | 傳輸>傳輸URI | https://*`<ip of target instance>`*:*`<port>`*`/bin/receive?sling:authRequestLogin=1` |
   | 傳輸>傳輸用戶 | 目標實例上的複製用戶 |
   | 傳輸>傳輸密碼 | 目標實例上的複製用戶密碼 |
   | 「延伸> HTTP方法」 | GET |

### 建立寄件匣代理 {#creating-the-outbox-agent}

1. 建立 **復寫代理** 在工作實例上。 (請參閱 [複製代理的文檔](/help/sites-deploying/replication.md).) 指定任何 **標題**. 此 **名稱** 必須 `offloading_outbox`.
1. 使用下列屬性建立代理。

   | 屬性 | 值 |
   |---|---|
   | 設定>序列化類型 | 預設 |
   | 傳輸>傳輸URI | repo://var/replication/outbox |
   | 觸發器>忽略預設值 | True |

### 尋找Sling ID {#finding-the-sling-id}

使用下列其中一種方法取得Experience Manager例項的Sling ID:

* 開啟Web主控台，然後在Sling Settings中尋找Sling ID屬性的值([http://localhost:4502/system/console/status-slingsettings](http://localhost:4502/system/console/status-slingsettings))。 如果實例尚不是拓撲的一部分，則此方法是有效的。
* 如果實例已是拓撲的一部分，請使用拓撲瀏覽器。

## 卸載DAM資產的處理 {#offloading-the-processing-of-dam-assets}

設定拓撲的例項，讓特定例項執行在DAM中新增或更新的資產的後台處理。

依預設，當DAM資產變更或新增一個至DAM時，Experience Manager會執行「DAM更新資產」工作流程。 變更預設行為，讓Experience Manager改為執行DAM更新資產卸載程式工作流程。 此工作流將生成一個JobManager作業，該作業的主題為 `com/adobe/granite/workflow/offloading`. 然後，配置拓撲，以便將作業卸載到專用工作器。

>[!CAUTION]
>
>搭配工作流程卸載使用時，不應使工作流程為暫時性。 例如，DAM更新資產工作流程在用於資產卸載時不得為暫時性。 若要在工作流程上設定/取消設定暫時標幟，請參閱 [暫時性工作流程](/help/assets/performance-tuning-guidelines.md#workflows).

以下過程假定卸載拓撲的以下特性：

* 一或多個Experience Manager例項正在編寫使用者與互動的例項，以新增或更新DAM資產。
* 使用者不會直接與處理DAM資產的一或多個Experience Manager例項互動。 這些例項專用於DAM資產的背景處理。

1. 在每個Experience Manager實例上，配置發現服務，使其指向根拓撲連接器。 (請參閱 [配置拓撲成員](#title4).)
1. 配置根拓撲連接器，使連接實例位於允許清單中。
1. 開啟卸載瀏覽器並停用 `com/adobe/granite/workflow/offloading` 使用者互動以上傳或變更DAM資產的例項主題。

   ![chlimage_1-116](assets/chlimage_1-116.png)

1. 在使用者互動以上傳或變更DAM資產的每個執行個體上，設定工作流程啟動器以使用DAM更新資產卸載工作流程：

   1. 開啟工作流程主控台。
   1. 按一下「啟動器」頁簽。
   1. 找出執行DAM更新資產工作流程的兩個啟動器設定。 一個啟動器配置事件類型是「已建立節點」，另一個類型是「已修改節點」。
   1. 變更這兩種事件類型，以執行DAM更新資產卸載工作流程。 (如需啟動器設定的相關資訊，請參閱 [節點變更時啟動工作流程](/help/sites-administering/workflows-starting.md).)

1. 在執行DAM資產背景處理的執行個體上，停用執行DAM更新資產工作流程的工作流程啟動器。

## 延伸閱讀 {#further-reading}

除了本頁顯示的詳細資訊外，您還可以閱讀以下內容：

* 如需使用Java API來建立工作和工作使用者的相關資訊，請參閱 [為卸載建立並佔用作業](/help/sites-developing/dev-offloading.md).
* 如需資產卸載的一般准則和最佳實務，請參閱 [資產卸載的一般准則和最佳作法](/help/assets/assets-offloading-best-practices.md#general-guidance-and-best-practices-for-asset-offloading).
* 要了解如何禁用卸載代理的自動建立，請參閱 [關閉自動代理管理](/help/assets/assets-offloading-best-practices.md#turning-off-automatic-agent-management).

---
title: 艱難的一天
seo-title: Tough Day
description: Tough Day（嚴格日）測試模擬在最壞情況下約1000位作者的每日負載，同時進行所有操作。
seo-description: The Tough Day test simulates the daily load of around 1000 authors in a worst-case scenario with all the operations going on at the same time.
uuid: 7a13efe0-c455-4af0-ad7b-c39cb2479d74
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: f48fa5ba-749b-4d3d-a4dd-c802006c8f07
exl-id: 80442184-212a-424d-b320-5b301a54f974
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1931'
ht-degree: 1%

---

# 艱難的一天{#tough-day}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 艱難的第2天 {#what-is-tough-day}

艱難的第2天是一項應用程式，可讓您強制測試AEM執行個體的限制。 可透過預設測試套裝立即執行，或依您的測試需求設定。 你可以看 [這個錄音](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2017/aem-toughday2-stress-testing-benchmarking-tool.html) 以呈現應用程式。

## 如何經營艱難的第2天 {#how-to-run-tough-day}

從下載最新版的Tough Day 2 [Adobe存放庫](https://repo1.maven.org/maven2/com/adobe/qe/toughday2/). 下載應用程式後，您可以提供 `host` 參數。 在下列範例中，AEM例項會在本機執行，因此 `localhost` 值的使用方式：

```xml
java -jar toughday2.jar --host=localhost
```

新增參數後執行的預設套裝名為 `toughday`. 其包含下列使用案例：

* 建立頁面和其即時副本（包括轉出）
* 取得首頁
* 在querybuilder中執行查詢
* 建立資產階層
* 刪除資產

套裝包含15%寫入動作和85%讀取動作。

若要執行套裝測試，Tough Day 2將安裝其預設內容套件。 若要避免此情況，請設定 `installsamplecontent` 參數 `false`，但請記住，您也應變更要執行之測試的預設路徑。 如果在沒有參數的情況下運行jar，則Tough Day 2（艱難日2）將顯示 [說明資訊](/help/sites-developing/tough-day.md#getting-help).

一般而言，您可以依照此模式使用應用程式：

```xml
java -jar toughday2.jar [--help | --help_full | --help_tests | --help_publish]  [<global arguments> | <actions> | --runmode | --publishmode]
```

>[!NOTE]
>
>艱難的第2天沒有清理步驟。 因此，建議在複製的測試執行個體上執行Tough Day 2 ，而非在主要生產執行個體上。 測試後應捨棄測試執行個體。

### 取得說明 {#getting-help}

艱難的第2天提供了一系列可從命令行訪問的幫助選項。 例如：

```xml
java -jar toughday2.jar --help_full
```

在下表中，您可以找到相關的說明參數。

<table> 
 <tbody> 
  <tr> 
   <td><strong>參數</strong></td> 
   <td><strong>說明</strong></td> 
   <td><strong>範例</strong></td> 
  </tr> 
  <tr> 
   <td>--說明</td> 
   <td>打印全局資訊，例如：可用的動作、預先定義的套裝、執行模式和全域參數。</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>—help_publish</td> 
   <td>打印所有可用的發佈器。</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>—help_tests</td> 
   <td>打印測試類及其說明。</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>—help_full</td> 
   <td>列印上述所有項目，以及測試、發佈商和套裝元件。</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> —help —runmode/publishmode type=&lt;mode&gt;</td> 
   <td>列出有關指定運行模式或發佈模式的資訊。</td> 
   <td><p>java -jar toughday2.jar —help —runmode type=constantload</p> <p>java -jar toughday2.jar —help —publishmode type=intervals</p> </td> 
  </tr> 
  <tr> 
   <td>—help —suite=&lt;suitename&gt;</td> 
   <td>列出指定套裝的所有測試及其各自的可設定屬性。</td> 
   <td><br /> java -jar toughday2.jar —help —suite=get_tests</td> 
  </tr> 
  <tr> 
   <td> —help —tag=&lt;tag&gt;</td> 
   <td><br /> 列出具有指定標籤的所有項目。</td> 
   <td>java -jar toughday2.jar —help —tag=publish</td> 
  </tr> 
  <tr> 
   <td> — 說明 &lt;testclass publisherclass=""&gt;</td> 
   <td><br /> 列出給定測試或發佈器的所有可配置屬性。</td> 
   <td><p>java -jar toughday2.jar — 幫助上傳PDFTest</p> <p>java -jar toughday2.jar — 幫助CSVPublisher</p> </td> 
  </tr> 
 </tbody> 
</table>

### 全域參數 {#global-parameters}

艱難的第2天提供設定或變更測試環境的全域參數。 包括目標主機、埠號、使用的通訊協定、執行個體的使用者和密碼等。 例如：

```xml
java -jar toughday2.jar --host=host --protocol=https --port=4502 --duration=30m --dryrun=true 
```

您可以在下列清單中找到相關參數：

| **參數** | **說明** | **預設值** | **可能的值** |
|---|---|---|---|
| `--installsamplecontent=<Val>` | 安裝或略過預設的Tough Day 2內容套件。 | true | true或false |
| `--protocol=<Val>` | 用於主機的協定。 | http | http或https |
| `--host=<Val>` | 要定位的主機名或IP。 |  |  |
| `--port=<Val>` | 主機的埠。 | 4502 |  |
| `--user=<Val>` | 例項的使用者名稱。 | 管理員 |  |
| `--password=<Val>` | 給定用戶的密碼。 | 管理員 |  |
| `--duration=<Val>` | 測試的持續時間。 可以以(**s**)秒，(**m**)inutes,(**h**)**d**)天。 | 1d |  |
| `--timeout=<Val>` | 測試在中斷並標示為失敗之前的執行時間。 以秒為單位表示。 | 180 |  |
| `--suite=<Val>` | 值可以是預先定義之測試套裝的一或清單（以逗號區隔）。 | 強度 |  |
| `--configfile=<Val>` | 目標yaml配置檔案。 |  |  |
| `--contextpath=<Val>` | 例項的內容路徑。 |  |  |
| `--loglevel=<Val>` | Tough Day 2引擎的日誌級別。 | 資訊 | 全部，調試，資訊，警告，錯誤，致命，關閉 |
| `--dryrun=<Val>` | 如果為true，則列印產生的設定，且不會執行任何測試。 | false | true或false |

## 自訂 {#customizing}

定制可以通過兩種方式實現：命令行參數或yaml配置檔案。 **組態檔通常用於大型自訂套裝，且會覆寫第2天的預設參數。 命令行參數會覆蓋配置檔案和預設參數。**

儲存測試設定的唯一方法是以yaml格式複製。 如需其他詳細資訊，請參閱 [toughday.yaml](https://repo.adobe.com/nexus/service/local/repositories/releases/content/com/adobe/qe/toughday2/0.2.1/toughday2-0.2.1.yaml) 以下各節中的設定和yaml設定範例。

### 新增測試 {#adding-a-new-test}

如果您不想使用預設值 `toughday` 套裝，您可使用 `add` 參數。 下列範例說明如何新增 `CreateAssetTreeTest` 使用命令行參數或yaml配置檔案進行測試。

使用命令列參數：

```xml
java -jar toughday2.jar --host=localhost --add CreateAssetTreeTest
```

使用yaml配置檔案：

```xml
globals:
  host : localhost
tests:
  - add : CreateAssetTreeTest
```

### 新增相同測試的多個例項  {#adding-multiple-instances-of-the-same-test}

您也可以新增及執行相同測試的多個例項，但每個例項必須具有唯一的名稱。 以下範例說明如何使用命令列參數或yaml設定檔案，新增相同測試的兩個例項。

使用命令列參數：

```xml
java -jar toughday2.jar --host=localhost --add CreateAssetTreeTest name=FirstAssetTree --add CreateAssetTreeTest name=SecondAssetTree
```

使用yaml配置檔案：

```xml
globals:
  host : localhost
tests:
  - add : CreateAssetTreeTest
    properties:
      name : FirstAssetTree
  - add : CreateAssetTreeTest
    properties:
      name : SecondAssetTree
```

### 變更測試屬性 {#changing-the-test-properties}

如果需要更改一個或多個測試屬性，可將該屬性添加到命令行或yaml配置檔案。 若要查看所有可用的測試屬性，請新增 `--help <TestClass/PublisherClass>` 命令列的參數，例如：

```xml
java -jar toughday2.jar --help CreatePageTreeTest
```

請記住，yaml配置檔案將覆蓋第2天的預設參數，命令行參數將覆蓋配置檔案和預設值。

下列範例說明如何變更 `template` 屬性 `CreatePageTreeTest` 使用命令行參數或yaml配置檔案進行測試。

使用命令列參數：

```xml
java -jar toughday2.jar --host=localhost --add CreatePageTreeTest template=/conf/toughday-templates/settings/wcm/templates/toughday-template
```

使用yaml配置檔案：

```xml
globals:
  host : localhost
tests:
  - add : CreatePageTreeTest
    properties:
      template : /conf/toughday-templates/settings/wcm/templates/toughday-template
```

### 使用預先定義的測試套裝 {#working-with-predefined-test-suites}

下列範例說明如何將測試新增至預先定義的套裝，以及如何重新設定現有測試並從預先定義的套裝中排除。

您可以使用 `add` 參數，並指定目標預先定義的套裝。

使用命令列參數：

```xml
java -jar toughday2.jar --host=localhost --suite=toughday --add CreatePageTreeTest
```

使用yaml配置檔案：

```xml
globals:
  host : localhost
  suite : toughday
tests:
  - add : CreatePageTreeTest
```

指定套裝中的現有測試也可以使用 `config`* *參數。 請注意，您還必須指定測試的套件名稱和實際名稱（而不是測試類名稱）。 您可以在 `name` 測試類的屬性。 如需如何尋找測試屬性的詳細資訊，請參閱 [更改測試屬性](/help/sites-developing/tough-day.md#changing-the-test-properties) 區段。

在以下範例中， `CreatePageTreeTest` （已命名） `UploadAsset`)已變更為「NewAsset」。

使用命令列參數：

```xml
java -jar toughday2.jar --host=localhost --suite=toughday --config UploadAsset title=NewAsset
```

使用yaml配置檔案：

```xml
globals:
  host : localhost
  suite : toughday
tests:
  - config : UploadAsset
    properties :
      title : NewAsset 
```

此外，您也可以使用，從預先定義的套裝或發佈器，從預設設定中移除測試，並 `exclude` 參數。 請注意，您還必須指定測試的套裝名稱和實際名稱(而不是測試C `lass` 名稱)。 您可以在 `name` 測試類的屬性。 在以下範例中， `CreatePageTreeTest` （已命名） `UploadAsset`)測試從toughday套裝中移除。

使用命令列參數：

```xml
java -jar toughday2.jar --host=localhost --suite=toughday --exclude UploadAsset
```

使用yaml配置檔案：

```xml
globals:
  host : localhost
  suite : toughday
tests:
  - exclude : UploadAsset 
```

### 執行模式 {#run-modes}

艱難的第2天可以以下列其中一種模式執行： **正常** 和 **恆載荷**.

此 **正常** 執行模式有兩個參數：

* `concurrency`  — 並發表示Tough Day 2為測試執行而建立的線程數。 在這些執行緒上，會執行測試，直到持續時間已用完或不再執行測試為止。

* `waittime`  — 同一線程上兩個連續測試執行之間的等待時間。 值必須以毫秒錶示。

以下範例說明如何使用命令列來新增參數：

```xml
java -jar toughday2.jar --host=localhost --add CreateAssetTreeTest --runmode=normal concurrency=20
```

或使用yaml配置檔案：

```xml
runmode:
  type : normal
  waittime : 300
  concurrency : 200
```

此 **恆載荷** 運行模式與正常運行模式不同，它通過生成恆定數量的已啟動測試執行，而不是恆定數量的線程。 可以使用具有相同名稱的運行模式參數來設定負載。

### 測試選擇 {#test-selection}

對於兩種運行模式，測試選擇過程都相同，其步驟如下：所有測試都有 `weight` 屬性，它決定執行緒中的可能性。 例如，如果我們有兩項測試，一項的權重為5，另一項的權重為10，則後者執行的可能性是前者的2倍。

此外，測試可以 `count` 屬性，此屬性會將執行數限制為指定數字。 通過此數字後，將不再執行測試。 所有已執行的測試執行個體都會依照設定完成執行。 以下示例說明如何在命令行或使用yaml配置檔案添加這些參數。

```xml
java -jar toughday2.jar --host=localhost --add CreateAssetTreeTest weight=5 --add CreatePageTreeTest weight=10 count=100 --runmode=normal concurrency=20 
```

或

```xml
- add : CreateAssetTreeTest
    properties :
      name : UploadAsset
      weight : 5
      base : 3
      foldertitle : IAmAFolder
      assettitle : IAmAnAsset
      count : 100
```

>[!NOTE]
>
>由於並行執行，實際的測試執行數量將不會完全等同於 `count` 參數。 期望與運行線程數成比例的偏差(由 `concurrency parameter`)。

### 排練 {#dry-run}

乾式執行會剖析所有指定的輸入（命令列參數或設定檔案），並將其與預設值合併，然後輸出結果。 它不執行任何測試。

```xml
java -jar toughday2.jar --host=localhost --suite=toughday --add CreatePageTreeTest --dryrun=true
```

## 輸出 {#output}

艱難的第2天會輸出測試量度和記錄。 如需詳細資訊，請閱讀下列章節。

### 測試量度 {#test-metrics}

艱難的第2天目前報告9個您可評估的測試量度。 量度搭配 **&amp;ast;** 只有在成功執行後才會報告符號：

| **名稱** | **說明** |
|---|---|
| 時間戳記 | 上次完成測試運行的時間戳。 |
| 已通過 | 成功執行的次數。 |
| 已失敗 | 失敗的運行數。 |
| 最小(&amp;A); | 測試執行的最短持續時間。 |
| 最大值(&amp;A); | 測試執行的最長持續時間。 |
| 中位數(&amp;A); | 所有測試執行的計算中位數持續時間。 |
| 平均(&amp;A); | 所有測試執行的計算平均持續時間。 |
| StdDev&amp;Ast; | 標準差。 |
| 90便士(&amp;A); | 第90個百分位。 |
| 99便士(&amp;A); | 第99個百分位。 |
| 99.9便士(&amp;A); | 第99.9個百分位數。 |
| 實際吞吐量(&amp;A); | 運行數除以已用執行時間。 |

這些量度是在發佈者的協助下撰寫，可與 `add` 參數（類似於新增測試）。 目前有兩個選項：

* **CSVPublisher**  — 輸出為CSV檔案。
* **ConsolePublisher**  — 輸出會顯示在主控台中。

依預設，會啟用兩個發佈者。

此外，報告量度的模式有兩種：

* 此 **簡單** 發佈模式 — 報告從執行開始到發佈點的結果。
* 此 **間隔** 發佈模式 — 在指定時間範圍內報告結果。 您可以使用 **間隔** 發佈模式參數。

下列範例說明如何設定 `intervals` 在命令行或使用yaml配置檔案進行參數設定。

使用命令列參數：

```xml
java -jar toughday2.jar --host=localhost --add CreatePageTreeTest --publishmode type=intervals interval=10s 
```

使用yaml配置檔案：

```xml
publishmode:
     type : intervals 
     interval : 10s 
     tests: 
        -add : CreatePageTreeTest
```

### 記錄 {#logging}

Tough Day 2會在您執行Tough Day 2的相同目錄中建立記錄檔資料夾。 此資料夾包含兩種記錄檔：

* **toughday.log**:包含與應用程式狀態、調試資訊和全局消息相關的消息。
* **toughday_&lt;testname>.log**:與指定測試相關的訊息。

不會覆寫記錄檔，後續執行會將訊息附加至現有記錄檔。 記錄有數個層級，如需詳細資訊，請參閱 ` [loglevel parameter](/help/sites-developing/tough-day.md#global-parameters)`.

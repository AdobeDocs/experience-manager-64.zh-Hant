---
title: 社群功能的Analytics設定
seo-title: 社群功能的Analytics設定
description: 設定社群分析
seo-description: 設定社群分析
uuid: 625a253f-b198-40e8-b34c-dff337fb0eff
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 36ea97a4-4e13-4e89-866b-495f3c30cb94
translation-type: tm+mt
source-git-commit: 501a6c470113d249646f4424a19ee215a82b032d
workflow-type: tm+mt
source-wordcount: '2787'
ht-degree: 3%

---


# 社群功能的Analytics設定 {#analytics-configuration-for-communities-features}

## 概覽 {#overview}

Adobe Analytics和Adobe Experience Manager(AEM)都是Adobe Marketing Cloud的解決方案。

Adobe Analytics可針對AEM Communities進行設定，如此當會員與支援的「社群」功能互動時，事件就會傳送至產生報表的Adobe Analytics。

例如，當啟用社群網站的成員檢視指派給他們的視訊資源時，資源播放器會傳送事件至Analytics，包括視訊心率資料。 在社群網站上，管理員可以看到各種有關視訊播放的報表。

此外，必須分析以下事項：

* 在發佈環境中：

   * 報告社群趨 [勢](trends.md)
   * 允許網站訪客依「檢視次數最多」、「最活躍」、「最喜歡」排序
   * 檢視UGC清單的計數

* 在作者環境中：

   * 在成員管理主控台中顯 [示參與率資料](members.md) （檢視、貼文、關注、按贊）
   * 用於啟用資源報告的趨勢摘要、視訊心率和視訊裝 [置](reports.md)

支援的社群功能包括：

* [啟用資源](resources.md)
* [論壇](forum.md)
* [QnA](working-with-qna.md)
* [部落格](blog-feature.md)
* [檔案庫](file-library.md)
* [日曆](calendar.md)

本節說明如何將Analytics報表套裝與社群功能連接。 基本步驟為：

1. [複製加密金鑰](#replicate-the-crypto-key) ，以確保所有AEM例項都能正確執行加密／解密
1. 準備Adobe Analytics報 [表套裝](#adobe-analytics-report-suite-for-video-reporting)
1. 建立AEM Analytics雲端 [服務](#aem-analytics-cloud-service-configuration) 和架 [構](#aem-analytics-framework-configuration)
1. [啟用社群網站的Analytics](#enable-analytics-for-a-community-site)
1. [驗證](#verify-analytics-to-aem-variable-mapping) Analytics與AEM變數對應
1. 識別主 [要發行者](#primary-publisher)
1. [發佈](#publish-community-site-and-analytics-cloud-service) 社群網站
1. 設 [定從Adobe Analytics匯入報表資料](#obtaining-reports-from-analytics) 至社群網站

## 必備條件 {#prerequisites}

若要設定Analytics for Communities功能，必須與您的帳戶代表合作，以設定Adobe Analytics帳戶和報 [表套裝](#adobe-analytics-report-suite-for-video-reporting)。 建立後，應提供下列資訊：

* 公司名稱

   與Adobe Analytics帳戶關聯的公司
* 使用者名稱

   獲授權管理Analytics帳戶之使用者的登入使用者名稱

   （應包含Web服務存取權限）

* 密碼

   授權使用者的登入密碼

* Analytics資料中心

   帳戶的Analytics資料中心URL

* 報表套裝

   要使用的Analytics報表套裝名稱

## 適用於視訊報告的Adobe Analytics報表套裝 {#adobe-analytics-report-suite-for-video-reporting}

使用Adobe Marketing Cloud的「報表套裝管 [理員」](https://docs.adobe.com/content/help/en/analytics/admin/manage-report-suites/new-report-suite/new-report-suite.html)，可以設定Analytics報表套裝，讓社群網站能夠提供社群功能的報表。

透過「公司名 [稱」和「使用者名稱」登入](https://docs.adobe.com/content/help/en/analytics/analyze/analysis-workspace/home.html) Adobe Marketing Cloud [](analytics.md#prerequisites)，您可以設定新的或現有的報表套裝，以便：

* [11轉換變數](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/conversion-variables/conversion-var-admin.html) (evar)

   * **`evar1`** 啟用 **`evar11`**
   * 可重複使用（重新命名）現有的evar，或建立新evar以用於社群功能

* [7成功事件](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/success-events/success-event.html) （事件）

   * **`event1`** 啟用 **`event7`**
   * 類型 **`Counter`**

      * 非 **`Counter (no subrelations)`**
   * 可重新使用（重新命名）現有事件或建立新事件以用於社群功能


* [視訊管理](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html)

   * 視訊報告主控台

      * 啟用 `Video Core`
      * 選擇保存
   * 視訊核心測量主控台

      * 選取 `Use Solution Variables`
      * 選擇保存


如果使用新 **的報表套裝**，請注意，新的報表套裝可能只有4個eVar和6個事件變數，而社群則需要11個eVar和7個事件變數。

如果使用 **現有報表套裝**，則可能需要在啟 [動社群網站的Analytics架構前修改變數對應](#modifying-analytics-variable-mapping) 。 請連絡您的帳戶代表，以瞭解有關社群專用變數的任何疑慮。

>[!CAUTION]
>
>**若使用現有報表套裝，且報表套裝已在**
>
>* **`evar1`** through **`evar11`**
>* **`event1`** through **`event7`**

>
>
**然後，在社群網站發佈之前，** 請務必移動AEM變數，在社群網站啟用Analytics時，這些AEM變數會自動對應至Analytics變數，以還原預先存在的對應。
>
>若要還原預先存在的對應並將AEM變數移至其他Analytics變數，請參閱修改Analytics變 [數對應一節](#modifying-analytics-variable-mapping)。
>
>如果不這樣做，可能會導致無法恢復的資料丟失。

### 視訊心率分析 {#video-heartbeat-analytics}

授權視訊心率分析時，會指 `Marketing Cloud Org Id` 派一個。

若要在設定視訊報表的Analytics報 [表套裝後啟用視訊心率報表](#adobe-analytics-report-suite-for-video-reporting):

* 建立 [Analytics雲端服務](#aem-analytics-cloud-service-configuration)
* 為社 [群網站啟用Analytics](#enable-analytics-for-a-community-site)
* 將與社 `Marketing Cloud Org Id` 群網站建立關聯

可 `Marketing Cloud Org Id` 以在建立社區站點時或更 [新時](sites-console.md#enablement) ，通過修改社 [區站點屬](sites-console.md#modifying-site-properties) 性來輸入。 [](#aem-analytics-cloud-service-configuration)

![chlimage_1-264](assets/chlimage_1-264.png)

啟用視訊心率分析時，視訊播放器的Javascript(JS)程式碼會執行個體化視訊心率程式庫程式碼（也包含在JS中），此程式碼會處理每10秒傳送視訊狀態更新至Analytics視訊追蹤伺服器的所有邏輯（不可設定），並最終傳送視訊工作階段的累積報表至主要Analytics伺服器。

若未啟用，則不會執行個體化視訊心率程式碼，且只會將視訊進度和繼續位置追蹤持續保存至SRP以進行報告。

## AEM Analytics Cloud服務設定 {#aem-analytics-cloud-service-configuration}

若要建立新的Analytics整合，並使用作者例項上的標準UI，將Adobe Analytics與AEM社群網站整合：

* 從全域導覽： **[!UICONTROL 工具>部署>雲端服務]**
* 向下捲動至 **[!UICONTROL Adobe Analytics]**
* 選擇「 **[!UICONTROL 立即配置]** 」或 **[!UICONTROL 「顯示配置」]**

![chlimage_1-265](assets/chlimage_1-265.png)

### 「建立配置」對話框 {#create-configuration-dialog}

* 選擇 `[+]` 可用配置旁 **[!UICONTROL 邊的表徵圖]** ，以建立新配置

在「建立配置」對話框中，要輸入的值標識配置。

![chlimage_1-266](assets/chlimage_1-266.png)

* **[!UICONTROL 標題]**

   （必要）設定的顯示標題。

   例如，輸入 *Enablement Community Analytics*

* **[!UICONTROL 名稱]**

   （可選）如果未指定，名稱將預設為從標題派生的有效節點名稱。

   For example, enter *communities*


* **[!UICONTROL 範本]**

   選取 `Adobe Analytics Configuration`

* Select **[!UICONTROL Create]**
   * 啟動配置頁並開啟對 `Analytics Settings` 話框

### Analytics設定對話方塊 {#analytics-settings-dialog}

初次建立新Analytics設定時，會顯示設定，並顯示新對話方塊以輸入Analytics設定。 此對話方塊需要從 [帳戶代表處取得](#prerequisites) 必要的帳戶資訊。

![chlimage_1-267](assets/chlimage_1-267.png)

* **[!UICONTROL 公司]**

   與Adobe Analytics帳戶關聯的公司

* **[!UICONTROL 使用者名稱]**

   獲授權管理Analytics帳戶之使用者的登入使用者名稱

* **[!UICONTROL 密碼]**

   授權使用者的登入密碼

* **[!UICONTROL 資料中心]**

   選取代管報表套裝的Analytics資料中心

* **[!UICONTROL 不要新增追蹤標記至頁面]**

   保留為預設值（未勾選）

* **[!UICONTROL 使用 AppMeasurement]**

   保留為預設值（未勾選）

* **[!UICONTROL 不要每晚匯入頁面印象 (作者)]**

   保留為預設值（未勾選）

* **[!UICONTROL 不要每晚匯入頁面印象 (發佈)]**

   保留為預設值（勾選）

要保存設定：


* 選擇 **[!UICONTROL 連線至Analytics]**

   * 如果未成功，

      * 驗證條目是否不包含前導空格
      * 試用不同的資料中心
      * 聯絡您的帳戶代表

* 選擇「確 **[!UICONTROL 定」]**


![chlimage_1-268](assets/chlimage_1-268.png)

### 建立框架 {#create-framework}

成功設定Adobe Analytics的基本連線後，必須建立或編輯社群網站的架構。 此架構的目的是將社群功能(AEM)變數對應至Analytics（報表套裝）變數。

* 選取 `[+]` 可用架構旁 **[!UICONTROL 的圖示]** ，以建立新架構

![chlimage_1-269](assets/chlimage_1-269.png)

* **[!UICONTROL 標題]**

   （必要）架構的顯示標題

   例如，輸入 *Enablement Community Framework*

* **[!UICONTROL 名稱]**

   （可選）如果未指定，名稱將預設為從標題派生的有效節點名稱。

   For example, enter *communities*

* **[!UICONTROL 範本]**

   選取 `Adobe Analytics Framework`

* Select **[!UICONTROL Create]**

建立Analytics架構會開啟要進行設定的架構。

## AEM Analytics Framework設定 {#aem-analytics-framework-configuration}

此架構的目的是將AEM變數對應至Analytics變數（evar和事件）。 可用於對應的Analytics變數 [在報表套裝中定義](#adobe-analytics-report-suite-for-video-reporting)。

![chlimage_1-270](assets/chlimage_1-270.png)

### 選擇報表套裝 {#select-report-suite}

選取已針對視訊報表設定的報表套裝。

如果報表套裝尚未建立或未正確設定，請參閱上一節：\
[適用於視訊報告的Adobe Analytics報表套裝](#adobe-analytics-report-suite-for-video-reporting)

不需要Sidekick且可將其最小化，以免妨礙存取「報表套裝」設定。

#### 選擇「新增項目」前後的報表套裝對話方塊 {#report-suites-dialog-before-and-after-selecting-add-item}

![chlimage_1-271](assets/chlimage_1-271.png)

1. 選取「 **[!UICONTROL 新增項目」+]** 兩個下拉式方塊出現
1. 選擇與 `Report suite` 公司帳戶關聯的報表套裝應可供選擇
1. 在打 **[!UICONTROL 開的對話框中]** ，選擇「是」: ```Load default server settings? Do you want to load the default server settings and overwrite current values in the Server section?```
1. 選擇 `Run Mode`\
   選擇發 **[!UICONTROL 布]**

![chlimage_1-272](assets/chlimage_1-272.png)

Analytic雲端服務與架構現已完成。 在啟用此Analytics服務後，社群網站建立後，即會定義映射。

## 啟用社群網站的Analytics {#enable-analytics-for-a-community-site}

### 啟用新社群網站 {#enable-for-new-community-site}

若要在建立新社群網站時 [新增Analytics雲端服務](sites-console.md):


* 在步驟3中
* 在「分 [析」標籤下](sites-console.md#analytics):

   * 勾選「啟 **[!UICONTROL 用Analytics]** 」核取方塊
   * 從下拉式方塊中選擇架構

* （可選）返回Analytics架構設定以調整變數映射。

### 啟用現有社群網站 {#enable-for-existing-community-site}

若要將Analytics雲端服務新增至現有 [的社群網站](sites-console.md#modifying-site-properties):


* 導覽至「社 **[!UICONTROL 群>網站主控台]** 」
* 選擇社群網站的「編輯網站」圖示
* 選取「設定」
* 在「分析」區段中：

   * 勾選「啟 **[!UICONTROL 用Analytics]** 」核取方塊
   * 從下拉式方塊中選擇架構


* （可選）返回Analytics架構設定以調整變數映射。

### 啟用自訂網站 {#enable-for-customized-sites}

為了讓Analytics追蹤和匯入能正常運作於社群網站，必須有具有類別和href屬 `scf-js-site-title` 性的頁面元素。 頁面上只應存在一個此類元素，例如社群網站的未修改 `sitepage.hbs` 指令碼中。 值會擷 `siteUrl` 取並傳送至Adobe Analytics作為網 *站路徑*。

```xml
# present in default sitepage.hbs
# only one scf-js-site-title class should be included
# this example sets it to be hidden as it serves no visual purpose
<div
    class="navbar-brand scf-js-site-title"
    href="{{siteUrl}}.html"
    style="visibility: hidden;"
>
</div>
```

對於覆 **蓋指令碼的自訂社群網站** ，請確 `sitepage.hbs` 定元素已存在。 變 `siteUrl`數會在伺服器上轉譯後，再提供給用戶端。

對於包 **含Communities元件的一般AEM網站** ，但不是使用網站建立精靈 [建立的AEM網站](sites-console.md)，則必須新增元素。 href的值應為網站的路徑。 例如，如果網站路徑為 `/content/my/company/en`，則使用：

```xml
<div
    class="navbar-brand scf-js-site-title"
    href="/content/my/company/en.html"
    style="visibility: hidden;"
>
</div>
```

## 社群分析功能 {#analytics-for-communities-features}

Analytics會自動用於數個Communities功能。

作者環境的 [OSGi組態](../../help/sites-deploying/configuring-osgi.md), `AEM Communities Analytics Component Configuration`提供已為Analytics所創作的元件清單。 變數的自動對應由列出的元件決定。

如果建立了Analytics專用的新自訂元件，則應將其新增至此已設定元件清單。

### 元件配置 {#component-configuration}

![chlimage_1-273](assets/chlimage_1-273.png)

注意： 元 `journal` 件用於實作部落格功能。

### 將Analytics對應至AEM變數 {#mapped-analytics-to-aem-variables}

在啟用Analytics並選取雲端設定架構的情況下儲存社群網站後，AEM變數會自動對應至分別以evar1和event1開頭的Analytics evar和事件，並遞增1。

如果使用現有報表套裝來映射evar1到evar11和event1到event7中的任何變數，則必須重新 [](#modifying-analytics-variable-mapping) 映射AEM變數並還原原始映射。

以下是遵循快速入門教學課程後的預 [設映射範例](getting-started-enablement.md):

![chlimage_1-274](assets/chlimage_1-274.png)

#### 與每個事件一起傳送的eVar映射 {#map-of-evars-sent-with-each-event}

|  | 啟用資源類型 | 網站標題 | 函式類型 | 群組標題 | 群組路徑 | UGC類型 | UGC標題 | 使用者（會員） | UGC路徑 | 網站路徑 |
|------------------------|------------------------|-----------|--------------|------------|-----------|---------|----------|--------------|---------|----------|
|  | **eVar1** | **eVar2** | **eVar3** | **eVar4** | **eVar5** | **eVar6** | **eVar7** | **eVar8** | **eVar9** | **eVar10** |
| event1資源播放 | (a) | - | - | - | - | - | - | - | (i) | - |
| event2SCFView | (a) | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |
| event3SCFCreate（貼文） | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |
| event4SCFFollow | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |
| event5SCFVoteUp | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |
| event6SCFVoteDown | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |
| event7SCFRate | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |

**eVar值的範例：**

* [MIME類型](https://www.iana.org/assignments/media-types): video/mp4
* [Community site title](sites-console.md#step13asitetemplate): Geometrixx Communities
* [社群函式名稱](functions.md): 論壇
* [社群群組名稱](creating-groups.md#creating-a-new-group): 遠足
* 社群群組內容的路徑： /content/sites/communities/tw/groups/hiking
* [UGC元件resourceType](essentials.md): social/forum/components/hbs/topic
* UGC元件標題： 遠足主題
* 登入（可授權的Id）: aaron.mcdonald@mailinator.com
* SRP到UGC的路徑： /content/usergenerated/asi/.../forum/jmtz-topic3或元 *件的路徑*: /content/sites/communities/tw/jcr:content/content/primary/forum
* 社群網站內容的路徑： /content/sites/community/tw

### 修改Analytics變數對應 {#modifying-analytics-variable-mapping}

在社群網站啟用Analytics後，可從架構設定看到Analytics evar和事件對應至AEM變數。

啟用Analytics後，在社群網站發佈之前，從左側導軌拖曳所需的Analytics evar或事件並拖曳至對應表格的相關列，即可在架構中變更對應。

若要避免重複映射，請務必將滑鼠指標暫留在行上並選取Analytics變數元素右側的「X」，以移除已取代的Analytics evar或事件。

如果「社群」evar和事件覆寫報表套裝中預先存在的映射，則為避免資料遺失，請將「社群」功能的AEM變數指派給其他Analytics evar和／或事件，並還原原始映射。

>[!CAUTION]
>
>在啟用Analytics的情況下發佈社群網站前，請務必重 [新對應](#publishing-the-community-site) ，否則就有資料遺失的風險。

#### 範例步驟1: 將Analytics evar14拖曳至對應表格 {#example-step-dragging-analytics-evar-into-mapping-table}

![chlimage_1-275](assets/chlimage_1-275.png)

#### 範例步驟2: 選取&#39;x&#39;以移除已取代的evar11 {#example-step-selecting-x-to-remove-replaced-evar}

![chlimage_1-276](assets/chlimage_1-276.png)

#### 範例步驟3: AEM var eventdata.siteId已重新映射至Analytics evar14 {#example-step-aem-var-eventdata-siteid-remapped-to-analytics-evar}

![chlimage_1-277](assets/chlimage_1-277.png)

## 發佈社群網站 {#publishing-the-community-site}

### 驗證Analytics與AEM變數對應 {#verify-analytics-to-aem-variable-mapping}

在發佈社群網站（也發佈Analytics雲端服務和架構）之前，最好先驗證變數對應。

請參閱章節：

* [將Analytics對應至AEM變數](#mapped-analytics-to-aem-variables)
* [修改Analytics變數對應](#modifying-analytics-variable-mapping)

>[!CAUTION]
>
>**若使用現有報表套裝，且報表套裝已在**
>
>* **`evar1`** through **`evar11`**
>* **`event1`** through **`event7`**

>
>
**然後，在社群網站發佈之前，** 請務必還原預先存在的對應，並將自動映射的社群AEM變數（當社群網站的Analytics啟用時）移至其他Analytics變數。 此重新映射應在所有社區元件中保持一致。
>
>如果不這樣做，可能會導致無法恢復的資料丟失。

### 主要發行者 {#primary-publisher}

當選擇的部署是發 [布場](topologies.md#tarmk-publish-farm)，則必須將一個AEM發佈例項識別為主要發佈者，以輪詢Adobe Analytics，以便將報表資料寫入 [SRP](working-with-srp.md)。

By default, the `AEM Communities Publisher Configuration` OSGi configuration identifies its publish instance as the primary publisher, such that all publish instances in a publish farm would self-identify as the primary.

因此，必須編輯所有次要發佈例項上的設定，以取消勾選「主要發佈者」核 **取方塊** 。

For specific instructions, see the primary publisher section of [Deploying Communities](deploy-communities.md#primary-publisher).

>[!CAUTION]
>
>It is important that the primary publisher be configured to prevent polling from multiple publish instances.

### Replicate the Crypto Key {#replicate-the-crypto-key}

Adobe Analytics認證會加密。 To faciitate the replication or transmission of encrypted analytics credentials between author and publishers, all AEM instances must share the same primary encryption key.

To do so, follow the instructions at [Replicate the Crypto Key](deploy-communities.md#replicate-the-crypto-key).

### Publish Community Site and Analytics Cloud Service {#publish-community-site-and-analytics-cloud-service}

在社群網站啟用Analytics雲端服務後，並視需要調整Analytics與 [AEM變數的對應](#mapped-analytics-to-aem-variables)，就必須透過 [（重新）發佈社群網站，將設定複製至發佈環境](sites-console.md#publishing-the-site)。

## 從Analytics取得報表 {#obtaining-reports-from-analytics}

### 報表管理 {#report-management}

作者和主要發行者的 [OSGi設定](../../help/sites-deploying/configuring-osgi.md)`AEM Communities Analytics Report Management`，用於查詢Analytics。

在作者上，查詢是即時報告。

在主要發佈者上，查詢可用來提供資訊，以準備報表匯入工具的Analytic資料匯入。

查詢間隔預設為10秒。

### 報表匯入工具 {#report-importer}

一旦發佈啟用Analytics的社群網站後，主要發行者的 [](../../help/sites-deploying/configuring-osgi.md)`AEM Communities Analytics Report Importer`OSGi組態即可設定為針對CRXDE中未個別設定的組態設定預設輪詢間隔。

輪詢間隔控制向Adobe Analytics請求提取並保存到 [SRP中的資料的頻率](working-with-srp.md)。

當資料可歸類為「大資料」時，更頻繁的投票可能會給社群網站帶來很大的負載。

預設輪詢 **導入間隔** 設定為12小時。

![chlimage_1-278](assets/chlimage_1-278.png)

### 元件報表自訂 {#component-report-customization}

目前，若要自訂要追蹤的量度，系統會在儲存庫中建立節點，以定義要針對該量度產生報表的時段。

論壇主題是目前此項自訂的唯一範例：

* 在主要發行者上
* 使用管理權限登入
* 導覽至 [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)

   * 例如， [http://localhost:4503/crx/de](http://localhost:4503/crx/de)

* Under the `jcr:content` node of the language root

   * 例如， `/content/sites/engage/en/jcr:content`

* Navigate to the component configured for Analytics reporting

   * 例如， `analytics/reportConfigs/social_forum_components_hbs_topic`

* Notice the time periods created

   * `last30Days`
   * `last90Days`
   * `thisYear`

* Notice the `total`node

   * 修改屬 `interval` 性將覆寫「報表匯入工具」間隔
   * 值以秒為單位，並設為4小時（14400秒）

![chlimage_1-279](assets/chlimage_1-279.png)

## 在Analytics中管理使用者資料 {#manage-user-data-in-analytics}

Adobe Analytics provides APIs that allow you to access, export, and delete user data. 如需詳細資訊，請參 [閱提交存取權和刪除請求](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/gdpr-submit-access-delete.html)。

## 資源 {#resources}

* Adobe Marketing Cloud: [Analytics Help and Reference](https://docs.adobe.com/content/help/en/analytics/landing/home.html)
* AEM: [Integrating with Adobe Analytics](../../help/sites-administering/adobeanalytics.md)
* AEM: [Analytics with External Providers](../../help/sites-administering/external-providers.md)


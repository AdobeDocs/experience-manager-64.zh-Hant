---
title: Communities功能的Analytics設定
seo-title: Analytics Configuration for Communities Features
description: 為社群設定分析
seo-description: Configure analytics for Communities
uuid: 625a253f-b198-40e8-b34c-dff337fb0eff
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 36ea97a4-4e13-4e89-866b-495f3c30cb94
role: Admin
exl-id: cb2f61df-73bb-47f7-86ce-feda4772c8d0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2800'
ht-degree: 4%

---

# Communities功能的Analytics設定 {#analytics-configuration-for-communities-features}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 概觀 {#overview}

Adobe Analytics和Adobe Experience Manager(AEM)都是Adobe Marketing Cloud的解決方案。

Adobe Analytics可針對AEM Communities進行設定，以便成員與支援的社群功能互動時，事件會傳送至Adobe Analytics，並從中產生報表。

例如，當啟用社群網站的成員檢視指派給他們的視訊資源時，資源播放器會將事件傳送至Analytics，包括視訊心率資料。 從社群網站，管理員可以查看有關播放視訊的各種報表。

此外，對於以下情況，也需要分析：

* 在發佈環境中：

   * 社群報告 [趨勢](trends.md)
   * 允許網站訪客依「檢視次數最多」、「最活躍」、「最喜歡」排序
   * 查看UGC清單上的計數

* 在製作環境中：

   * 在 [成員管理控制台](members.md) （檢視、貼文、追隨、按贊）
   * 啟用資源的趨勢摘要、視訊心率和視訊裝置 [報告](reports.md)

支援的社群功能包括：

* [啟用資源](resources.md)
* [論壇](forum.md)
* [QnA](working-with-qna.md)
* [部落格](blog-feature.md)
* [檔案庫](file-library.md)
* [日曆](calendar.md)

本檔案的本節說明如何將Analytics報表套裝與Communities功能連結。 基本步驟為：

1. [複製加密密鑰](#replicate-the-crypto-key) 確保在所有AEM執行個體上正確進行加密/解密
1. 準備Adobe Analytics [報表套裝](#adobe-analytics-report-suite-for-video-reporting)
1. 建立AEM Analytics [雲端服務](#aem-analytics-cloud-service-configuration) 和 [框架](#aem-analytics-framework-configuration)
1. [啟用Analytics](#enable-analytics-for-a-community-site) 用於社區站點
1. [驗證](#verify-analytics-to-aem-variable-mapping) Analytics與AEM變數的對應
1. 識別 [主要發佈者](#primary-publisher)
1. [發佈](#publish-community-site-and-analytics-cloud-service) 社群網站
1. 設定 [匯入報表資料](#obtaining-reports-from-analytics) 從Adobe Analytics到社群網站

## 必備條件 {#prerequisites}

若要設定Analytics for Communities功能，請與您的帳戶代表合作，以設定Adobe Analytics帳戶，並 [報表套裝](#adobe-analytics-report-suite-for-video-reporting). 建立後，應提供下列資訊：

* 公司名稱

   與Adobe Analytics帳戶相關聯的公司
* 使用者名稱

   獲授權管理Analytics帳戶之使用者的登入使用者名稱

   （應包含網站服務存取權限）

* 密碼

   授權用戶的登錄密碼

* Analytics資料中心

   帳戶的Analytics資料中心URL

* 報表套裝

   要使用的Analytics報表套裝名稱

## Adobe Analytics視訊報表報表套裝 {#adobe-analytics-report-suite-for-video-reporting}

使用Adobe Marketing Cloud的 [報表套裝管理器](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/new-report-suite/new-report-suite.html)，您可以設定Analytics報表套裝，讓社群網站能夠提供社群功能的報表。

登入 [Adobe Marketing Cloud](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/home.html) with [公司名稱和使用者名稱](analytics.md#prerequisites)，則可設定新的或現有的報表套裝以：

* [11轉換變數](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/conversion-variables/conversion-var-admin.html) (evar)

   * **`evar1`** through **`evar11`** 已啟用
   * 可以重新使用（重新命名）現有的eVar，或建立新eVar以用於Communities功能

* [7成功事件](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/success-events/success-event.html) （事件）

   * **`event1`** through **`event7`** 已啟用
   * 類型 **`Counter`**

      * 非 **`Counter (no subrelations)`**
   * 可以重新使用（重新命名）現有事件，或建立新事件以用於Communities功能


* [視訊管理](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html)

   * 視訊報表主控台

      * 啟用 `Video Core`
      * 選擇保存
   * 視訊核心測量主控台

      * 選取 `Use Solution Variables`
      * 選擇保存


若使用 **新報表套裝**，請注意，新報表套裝可能只有4個evar和6個事件變數，而Communities需要11個evar和7個事件變數。

若使用 **現有報表套裝**，則可能需要 [修改變數對應](#modifying-analytics-variable-mapping) 先為社群網站啟用Analytics架構。 如對社群專用變數有任何疑慮，請連絡您的客戶代表。

>[!CAUTION]
>
>**若使用的現有報表套裝已在**
>
>* **`evar1`** through **`evar11`**
>* **`event1`** through **`event7`**
>
>**然後在社群網站發佈之前，** 請務必移動在社群網站啟用AEM時自動對應至Analytics變數的Analytics變數，以還原原先存在的對應。
>
>若要還原預先存在的對應，並將AEM變數移至其他Analytics變數，請參閱 [修改Analytics變數對應](#modifying-analytics-variable-mapping).
>
>若無法這麼做，可能會導致無法復原的資料遺失。

### 視訊心率分析 {#video-heartbeat-analytics}

若Video Heartbeat Analytics獲得授權，則 `Marketing Cloud Org Id` 已指派。

若要在 [設定Analytics報表套裝以進行視訊報表](#adobe-analytics-report-suite-for-video-reporting):

* 建立 [Analytics雲端服務](#aem-analytics-cloud-service-configuration)
* 啟用 [社群網站的Analytics](#enable-analytics-for-a-community-site)
* 關聯 `Marketing Cloud Org Id` 與社群網站

此 `Marketing Cloud Org Id` 可於 [社群網站建立](sites-console.md#enablement) 或更新 [修改](sites-console.md#modifying-site-properties) 社區站點屬性。 [](#aem-analytics-cloud-service-configuration)

![chlimage_1-264](assets/chlimage_1-264.png)

啟用視訊心率分析時，視訊播放器的Javascript(JS)程式碼會實例化視訊心率程式庫程式碼（亦在JS中），其會處理每10秒傳送視訊狀態更新至Analytics視訊追蹤伺服器（不可設定）的所有邏輯，並最終傳送視訊工作階段的累積報表至主要Analytics伺服器。

若未啟用，視訊心率程式碼將不會具現化，且只會將視訊進度和繼續位置追蹤保存至SRP以供報告。

## AEM Analytics Cloud服務設定 {#aem-analytics-cloud-service-configuration}

若要使用製作執行個體上的標準UI，建立整合Adobe Analytics與AEM社群網站的新Analytics整合：

* 從全局導航： **[!UICONTROL 工具>部署>Cloud Services]**
* 向下捲動至 **[!UICONTROL Adobe Analytics]**
* 選取 **[!UICONTROL 立即配置]** 或 **[!UICONTROL 顯示配置]**

![chlimage_1-265](assets/chlimage_1-265.png)

### 建立配置對話框 {#create-configuration-dialog}

* 選擇 `[+]` 表徵圖 **[!UICONTROL 可用配置]** 建立新配置

在「建立配置」對話框中，要輸入的值標識配置。

![chlimage_1-266](assets/chlimage_1-266.png)

* **[!UICONTROL 標題]**

   （必要）設定的顯示標題。

   例如，輸入 *啟用社群分析*

* **[!UICONTROL 名稱]**

   （可選）如果未指定，則名稱將預設為從標題派生的有效節點名稱。

   例如，輸入 *社群*


* **[!UICONTROL 範本]**

   選取 `Adobe Analytics Configuration`

* 選擇 **[!UICONTROL 建立]**
   * 啟動配置頁面並開啟 `Analytics Settings` 對話

### Analytics設定對話方塊 {#analytics-settings-dialog}

初始建立新Analytics設定時，會顯示設定，並顯示新對話方塊，供您輸入Analytics設定。 此對話方塊需要 [必備帳戶資訊](#prerequisites) 從客戶代表處獲得。

![chlimage_1-267](assets/chlimage_1-267.png)

* **[!UICONTROL 公司]**

   與Adobe Analytics帳戶相關聯的公司

* **[!UICONTROL 使用者名稱]**

   獲授權管理Analytics帳戶之使用者的登入使用者名稱

* **[!UICONTROL 密碼]**

   授權用戶的登錄密碼

* **[!UICONTROL 資料中心]**

   選取托管報表套裝的Analytics資料中心

* **[!UICONTROL 不要新增追蹤標記至頁面]**

   保留為預設值（未勾選）

* **[!UICONTROL 使用 AppMeasurement]**

   保留為預設值（未勾選）

* **[!UICONTROL 不要每晚匯入頁面印象 (作者)]**

   保留為預設值（未勾選）

* **[!UICONTROL 不要每晚匯入頁面印象 (發佈)]**

   保留為預設值（已勾選）

若要儲存設定：


* 選擇 **[!UICONTROL 連線至Analytics]**

   * 若未成功，

      * 驗證條目是否包含前導空格
      * 嘗試其他資料中心
      * 請連絡您的客戶代表

* 選擇 **[!UICONTROL 確定]**


![chlimage_1-268](assets/chlimage_1-268.png)

### 建立框架 {#create-framework}

成功設定與Adobe Analytics的基本連線後，必須建立或編輯社群網站的架構。 此架構的目的是將Communities功能(AEM)變數對應至Analytics（報表套裝）變數。

* 選擇 `[+]` 表徵圖 **[!UICONTROL 可用架構]** 建立新框架

![chlimage_1-269](assets/chlimage_1-269.png)

* **[!UICONTROL 標題]**

   （必要）架構的顯示標題

   例如，輸入 *啟用社群架構*

* **[!UICONTROL 名稱]**

   （可選）如果未指定，則名稱將預設為從標題派生的有效節點名稱。

   例如，輸入 *社群*

* **[!UICONTROL 範本]**

   選取 `Adobe Analytics Framework`

* 選擇 **[!UICONTROL 建立]**

建立Analytics架構會開啟設定的架構。

## AEM Analytics架構設定 {#aem-analytics-framework-configuration}

此架構的用途是將AEM變數對應至Analytics變數（evar和事件）。 可用於對應的Analytics變數為 [在報表套裝中定義](#adobe-analytics-report-suite-for-video-reporting).

![chlimage_1-270](assets/chlimage_1-270.png)

### 選取報表套裝 {#select-report-suite}

選取已針對視訊報表設定的報表套裝。

如果報表套裝尚未建立或未正確設定，請參閱上一節：\
[Adobe Analytics視訊報表報表套裝](#adobe-analytics-report-suite-for-video-reporting)

不需要Sidekick，且可盡可能最小化，以免妨礙存取報表套裝設定。

#### 選取「新增項目」前後的報表套裝對話方塊 {#report-suites-dialog-before-and-after-selecting-add-item}

![chlimage_1-271](assets/chlimage_1-271.png)

1. 選擇 **[!UICONTROL 新增項目+]** 兩個下拉框出現
1. 選擇 `Report suite` 與公司帳戶相關聯的報表套裝應可供選取
1. 選擇 **[!UICONTROL 是]** 在開啟的對話方塊中： ```Load default server settings? Do you want to load the default server settings and overwrite current values in the Server section?```
1. 選擇 `Run Mode`\
   選擇 **[!UICONTROL 發佈]**

![chlimage_1-272](assets/chlimage_1-272.png)

Analytic雲服務和架構現已完成。 一旦建立社群網站並啟用此Analytics服務，就會定義對應。

## 為社群網站啟用Analytics {#enable-analytics-for-a-community-site}

### 為新社區站點啟用 {#enable-for-new-community-site}

若要在 [建立新的社群站點](sites-console.md):


* 在步驟3中
* 在 [ANALYTICS標籤](sites-console.md#analytics):

   * 檢查 **[!UICONTROL 啟用Analytics]** 核取方塊
   * 從下拉式方塊中選擇架構

* （可選）返回Analytics架構設定以調整變數對應。

### 為現有社區站點啟用 {#enable-for-existing-community-site}

將Analytics雲端服務新增至 [現有社群網站](sites-console.md#modifying-site-properties):


* 導覽至 **[!UICONTROL 社群>網站]** 主控台
* 選擇社區站點的「編輯站點」表徵圖
* 選取設定
* 在Analytics區段中：

   * 檢查 **[!UICONTROL 啟用Analytics]** 核取方塊
   * 從下拉式方塊中選擇架構


* （可選）返回Analytics架構設定以調整變數對應。

### 為自訂網站啟用 {#enable-for-customized-sites}

為了讓Analytics追蹤和匯入正常運作，社群網站會使用 `scf-js-site-title` 類和href屬性必須存在。 頁面上只應存在一個此類元素，例如未修改的元素 `sitepage.hbs` 社群網站的指令碼。 的值 `siteUrl` 會擷取並傳送至Adobe Analytics，作為 *網站路徑*.

```xml
# present in default sitepage.hbs

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
# only one scf-js-site-title class should be included

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
# this example sets it to be hidden as it serves no visual purpose

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
<div
    class="navbar-brand scf-js-site-title"
    href="{{siteUrl}}.html"
    style="visibility: hidden;"
>
</div>
```

若 **自訂社群網站** 覆蓋 `sitepage.hbs` 指令碼，確定元素存在。 此 `siteUrl`變數會在提供給用戶端之前，於伺服器上呈現時設定。

若 **一般AEM網站** 包含Communities元件，但不會使用 [網站建立精靈](sites-console.md)，則必須新增元素。 href的值應為網站路徑。 例如，如果網站路徑為 `/content/my/company/en`，然後使用：

```xml
<div
    class="navbar-brand scf-js-site-title"
    href="/content/my/company/en.html"
    style="visibility: hidden;"
>
</div>
```

## Analytics for Communities功能 {#analytics-for-communities-features}

Analytics會自動用於數個Communities功能。

作者環境的 [OSGi配置](../../help/sites-deploying/configuring-osgi.md), `AEM Communities Analytics Component Configuration`，提供已為Analytics所創作的元件清單。 變數的自動對應由列出的元件決定。

如果已建立為Analytics創作的新自訂元件，則應將其新增至已設定元件的清單。

### 元件配置 {#component-configuration}

![chlimage_1-273](assets/chlimage_1-273.png)

注意：the `journal` 元件可用來實作部落格功能。

### 將Analytics對應至AEM變數 {#mapped-analytics-to-aem-variables}

在啟用Analytics並選取雲端設定架構後，儲存社群網站時，AEM變數會自動對應至分別以evar1和event1開頭的Analytics evar和事件，並增加1。

如果使用將evar1到evar11以及event1到event7中任何變數對應的現有報表套裝，則必須 [重新映射AEM變數](#modifying-analytics-variable-mapping) 並恢復原始映射。

以下是遵循 [快速入門教學課程](getting-started-enablement.md):

![chlimage_1-274](assets/chlimage_1-274.png)

#### 隨每個事件傳送的eVar地圖 {#map-of-evars-sent-with-each-event}

|  | 啟用資源類型 | 網站標題 | 函式類型 | 群組標題 | 群組路徑 | UGC類型 | UGC標題 | 用戶（成員） | UGC路徑 | 網站路徑 |
|------------------------|------------------------|-----------|--------------|------------|-----------|---------|----------|--------------|---------|----------|
|  | **eVar1** | **eVar2** | **eVar3** | **eVar4** | **eVar5** | **eVar6** | **eVar7** | **eVar8** | **eVar9** | **eVar10** |
| event1資源播放 | (a) | - | - | - | - | - | - | - | (i) | - |
| event2SCFView | (a) | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |
| event3SCFCreate(Post) | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |
| event4SCFFollow | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |
| event5SCFVoteUp | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |
| event6SCFVoteDown | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |
| event7SCFRate | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |

**eVar值的範例：**

* [MIME類型](https://www.iana.org/assignments/media-types):video/mp4
* [社群網站標題](sites-console.md#step13asitetemplate):Geometrixx社群
* [社區函式名稱](functions.md):論壇
* [社區組名稱](creating-groups.md#creating-a-new-group):徒步旅行
* 社群群組內容路徑：/content/sites/communities/en/groups/hiking
* [UGC元件resourceType](essentials.md):social/forum/components/hbs/topic
* UGC元件標題：健行主題
* 登入（可授權Id）:aaron.mcdonald@mailinator.com
* SRP到UGC的路徑：/content/usergenerated/asi/.../forum/jmtz-topic3或 *要遵循的元件路徑*:/content/sites/communities/en/jcr:content/content/primary/forum
* 社群網站內容路徑：/content/sites/community/en

### 修改Analytics變數對應 {#modifying-analytics-variable-mapping}

為社群網站啟用Analytics後，可從架構設定看到Analytics evar和事件對應至AEM變數。

啟用Analytics後，在社群網站發佈前，您可將所需的Analyticsevar或事件從左側邊欄拖曳至對應表格中的相關列，以在架構中變更對應。

若要避免重複對應，請務必將游標移至該列並選取Analytics變數元素右側顯示的「X」，以移除該列中已取代的Analytics evar或事件。

如果Communities evar和事件覆寫報表套裝中預先存在的對應，則為避免資料遺失，請將Communities功能的AEM變數指派給其他Analytics evar和/或事件，並還原原始對應。

>[!CAUTION]
>
>在社群網站之前重新映射非常重要 [已發佈](#publishing-the-community-site) 若啟用Analytics，則資料遺失的風險。

#### 範例步驟1:將Analytics evar14拖曳至對應表格 {#example-step-dragging-analytics-evar-into-mapping-table}

![chlimage_1-275](assets/chlimage_1-275.png)

#### 範例步驟2:選取「x」以移除已取代的evar11 {#example-step-selecting-x-to-remove-replaced-evar}

![chlimage_1-276](assets/chlimage_1-276.png)

#### 範例步驟3:AEM var eventdata.siteId重新對應至Analytics evar14 {#example-step-aem-var-eventdata-siteid-remapped-to-analytics-evar}

![chlimage_1-277](assets/chlimage_1-277.png)

## 發佈社群網站 {#publishing-the-community-site}

### 驗證Analytics與AEM變數的對應 {#verify-analytics-to-aem-variable-mapping}

發佈社群網站（亦會發佈Analytics雲端服務和架構）前，最好先驗證變數對應。

請參閱以下章節：

* [將Analytics對應至AEM變數](#mapped-analytics-to-aem-variables)
* [修改Analytics變數對應](#modifying-analytics-variable-mapping)

>[!CAUTION]
>
>**若使用的現有報表套裝已在**
>
>* **`evar1`** through **`evar11`**
>* **`event1`** through **`event7`**
>
>**然後在社群網站發佈之前，** 請務必還原原先現有的對應，並將自動對應的Communities AEM變數（當為社群網站啟用Analytics時）移至其他Analytics變數。 此重新對應應在所有Communities元件之間保持一致。
>
>若無法這麼做，可能會導致無法復原的資料遺失。

### 主要發行者 {#primary-publisher}

當選擇的部署為 [發佈農場](topologies.md#tarmk-publish-farm)，則必須將一個AEM發佈例項識別為主要發佈者，以輪詢Adobe Analytics以寫入報表資料 [SRP](working-with-srp.md).

依預設， `AEM Communities Publisher Configuration` OSGi設定會將其發佈執行個體識別為主要發佈者，這樣發佈伺服器陣列中的所有發佈執行個體都會自行識別為主要發佈者。

因此，必須編輯所有次要發佈執行個體上的設定，以取消勾選 **主要發行者** 核取方塊。

如需特定指示，請參閱 [部署社群](deploy-communities.md#primary-publisher).

>[!CAUTION]
>
>請務必將主要發佈者設定為防止從多個發佈執行個體進行輪詢。

### 複製加密密鑰 {#replicate-the-crypto-key}

Adobe Analytics憑證會經過加密。 為方便製作者與發佈者之間復寫或傳輸加密的分析憑證，所有AEM執行個體必須共用相同的主要加密金鑰。

若要這麼做，請依照 [複製加密密鑰](deploy-communities.md#replicate-the-crypto-key).

### 發佈社群網站和Analytics Cloud服務 {#publish-community-site-and-analytics-cloud-service}

為社群網站啟用Analytics雲端服務後，如有必要，請 [Analytics與AEM變數的對應已經過調整](#mapped-analytics-to-aem-variables)，則必須透過將設定複製至發佈環境 [（重新）發佈社群網站](sites-console.md#publishing-the-site).

## 從Analytics取得報表 {#obtaining-reports-from-analytics}

### 報表管理 {#report-management}

作者和主要發行者的 [OSGi配置](../../help/sites-deploying/configuring-osgi.md), `AEM Communities Analytics Report Management`，用於查詢Analytics。

在作者上，查詢適用於即時報表。

在主要發佈者上，查詢可用來提供資訊，以準備報表匯入工具的Analytic資料匯入。

查詢間隔預設為10秒。

### 報表匯入工具 {#report-importer}

發佈已啟用Analytics的社群網站後，即為主要發行者的 [OSGi配置](../../help/sites-deploying/configuring-osgi.md), `AEM Communities Analytics Report Importer`，則可設定為針對未在CRXDE中個別設定的這些設定，設定預設輪詢間隔。

輪詢間隔會控制向Adobe Analytics提出要提取及儲存至的資料請求的頻率 [SRP](working-with-srp.md).

當資料可歸類為「大資料」時，更頻繁的輪詢可能會給社群網站帶來大量負載。

預設輪詢 **匯入間隔** 設為12小時。

![chlimage_1-278](assets/chlimage_1-278.png)

### 元件報表自訂 {#component-report-customization}

目前，若要自訂要追蹤的量度，系統會在儲存庫中建立節點，定義要針對該量度產生報表的時段。

論壇主題目前是此自訂的唯一範例：

* 在主要發佈者上
* 使用管理權限登入
* 導覽至 [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)

   * 例如， [http://localhost:4503/crx/de](http://localhost:4503/crx/de)

* 在 `jcr:content` 語言根節點

   * 例如 `/content/sites/engage/en/jcr:content`

* 導覽至為Analytics報表設定的元件

   * 例如 `analytics/reportConfigs/social_forum_components_hbs_topic`

* 注意建立的時段

   * `last30Days`
   * `last90Days`
   * `thisYear`

* 請注意 `total`節點

   * 修改 `interval` 屬性會覆寫Report Importer間隔
   * 值以秒為單位，設為4小時(14400秒)

![chlimage_1-279](assets/chlimage_1-279.png)

## 在Analytics中管理使用者資料 {#manage-user-data-in-analytics}

Adobe Analytics提供可讓您存取、匯出和刪除使用者資料的API。 如需詳細資訊，請參閱 [提交存取和刪除請求](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/gdpr-submit-access-delete.html).

## 資源 {#resources}

* Adobe Marketing Cloud: [Analytics說明與參考](https://experienceleague.adobe.com/docs/analytics/landing/home.html)
* AEM: [與Adobe Analytics整合](../../help/sites-administering/adobeanalytics.md)
* AEM: [Analytics與外部提供者](../../help/sites-administering/external-providers.md)

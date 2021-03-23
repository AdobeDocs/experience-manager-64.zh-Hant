---
title: 過時和移除的功能
description: 針對Adobe Experience Manager6.4中已過時和已移除功能的發行說明。
translation-type: tm+mt
source-git-commit: 5b00783e4471a6b142ab17a7bc4a647ab04aec5f
workflow-type: tm+mt
source-wordcount: '1281'
ht-degree: 14%

---


# 過時和移除的功能 {#deprecated-and-removed-features}

Adobe 持續評估產品功能，以更新或替代的方式來改善或取代舊功能，以提升客戶享有的整體價值，且隨時謹慎考慮是否回溯相容。

若要傳達 AEM 功能即將移除/取代的訊息，請套用下列規則：

1. 首先需公告功能已過時。雖然已過時，但功能仍可用，但無法進一步增強。
1. 在下列主要版本中，將最早移除已過時的功能。 將公佈實際的移除目標日期。

此程序可讓客戶在功能真正移除之前，至少還有一個發行週期，讓實作適應過時功能的新版本或後續版本。

## 過時的功能 {#deprecated-features}

下表列出已標示為已停用6.4的功AEM能和功能。通常，計畫在未來版本中移除的功能會先設為不建議使用，並提供其他選項。

建議客戶檢視是否在目前的部署中使用這些功能，並規劃變更實作，改為使用所提供的替代方案。

<!-- TBD: This MD table is a replacement of the HTML table below. However, it generates validation error hence commenting and replacing with inline text. Restore if required. -->

| 區域 | 功能 | 替代方案 |
|---|---|---|
| UI | Adobe不打算對Classic UI做進一步的增強。 AEM 6.4包含Classic UI，而舊版升級的客戶可依原樣繼續使用。 請注意，Classic UI在遭淘汰時仍完全受支援。 <ul> <li>`/libs/cq/core/content/welcome.html` </li> <li> `/siteadmin` </li> <li> `/damadmin` </li> <li> `/mcmadmin` </li> <li> `/inbox` </li> <li> `/tagging` </li> <li> `/cf#` （頁面編輯器） </li><li> `/libs/launches/content/admin.html` </li> <li> `/libs/cq/workflow/content/console.html` </li> </ul> | 建議客戶改用新的UIAEM。 |
| 元件 | Adobe不打算對下面列出的基礎元件進行進一步的增強。 AEM6.4包含Foundation Components，而舊版升級的客戶可依原樣繼續使用。 請注意，Foundation Components在遭淘汰時仍完全受支援。 <ul> <li> foundation/components/account/accountname </li> <li> foundation/components/account/actions </li> <li> foundation/components/account/passwordreset </li> <li> foundation/components/account/requestconfirmation </li> <li> foundation/components/adaptive image </li> <li> foundation/components/assetsharepage </li> <li> foundation/components/breadcrumb </li> <li> foundation/components/form/creditcard </li> <li> foundation/components/listchildren </li> <li> foundation/components/login </li> <li> foundation/components/logo </li> <li> foundation/components/mobilefooter </li> <li> foundation/components/mobileimage </li> <li> foundation/components/mobilelist </li> <li> foundation/components/mobilelogo </li> <li> foundation/components/mobilereference </li> <li> foundation/components/mobiletextimage </li> <li> foundation/components/mobiletopnav </li> <li> foundation/components/search </li> <li> foundation/components/sitemap </li> <li> foundation/components/table </li> <li> foundation/components/toolbar </li> <li> foundation/components/topnav </li> <li> foundation/components/userinfo </li> </ul> | 建議客戶將核心元件用於未來的專案。 現有網站不需要變更。 |
| 元件 | Adobe不打算對下面列出的基礎元件進行進一步的增強。 AEM6.4包含Foundation Components，而舊版升級的客戶可依原樣繼續使用。 請注意，Foundation Components在遭淘汰時仍完全受支援。 <ul><li>foundation/components/timing</li></ul> | Adobe不打算提供更換。 |
| 門戶Director | PortalDirector是一組功能，允許通過第三方服AEM務器中的Portlet托管內容。 Adobe不打算在下列位置下進一步增強入口網站Director功能。 AEM6.4包含入口網站Director，從舊版升級的客戶可依現狀繼續使用。 請注意，Portal Direct在遭淘汰時仍完全受支援。 <ul><li>/libs/portal/director</li></ul> | Adobe不打算提供更換。 |
| Portlet元件 | /foundation/components/portlet下的Portlet元件允許將JSR Portlet作為元件AEM托管。 Adobe不打算對Portlet元件功能進行進一步的增強。 AEM 6.4包含Portlet元件，從舊版升級的客戶可以按原樣繼續使用。 請注意，Portlet元件在被淘汰時仍完全受支援。 | Adobe不打算提供更換。 |
| 表單 | 由於不再支援Adobe中心產品，因此已不再支援Adobe中心移轉橋接服務。 | 無取代 |
| 表單 | 不建議在Query和OperationOptions中使用JSONObject。 不建議使用下列API: <ul><li>`setArguments(JSONObject arguments)`</li><li> `JSONObject getArguments()`</li><li>`OperationOptions(String operationId, JSONObject arguments)`</li><li>`JSONObject getArguments()`</li><li> `void setArguments(JSONObject arguments)`</li></ul> | 使用`IValueMap` API |
| 表單 | 已過時的Central Migration Bridge服務。 | 不提供任何替代項目。 |
| 資產 | 資產卸載已從6.4開始AEM停用。 |  |
| 開發人員 | Lodash/下划線客戶端庫。 Adobe不打算進一步維護和更新作為分發的一部分附帶的Lodash/下划線客戶端庫（快速入門） | Adobe建議仍需使用Lodash/底線的客戶將程式碼新增至其專案程式碼庫。 |

<!-- Original HTML table that came from helpx during migration.

<table> 
 <tbody>
  <tr>
   <td>Area</td> 
   <td>Feature</td> 
   <td>Replacement</td> 
  </tr>
  <tr>
   <td>UI</td> 
   <td><p>Adobe does not plan to make further enhancements to the Classic UI. AEM 6.4 has the Classic UI included, and customers upgrading from earlier releases can keep using it as is. Note that Classic UI remains fully supported while being deprecated. </p> 
    <ul> 
     <li>/libs/cq/core/content/welcome.html</li> 
     <li>/siteadmin</li> 
     <li>/damadmin</li> 
     <li>/mcmadmin</li> 
     <li>/inbox</li> 
     <li>/tagging</li> 
     <li>/cf# (Page Editor)</li> 
     <li>/libs/launches/content/admin.html</li> 
     <li>/libs/cq/workflow/content/console.html</li> 
    </ul> </td> 
   <td><p>Customers are advised to switch to use the new AEM UI.</p> <p> </p> </td> 
  </tr>
  <tr>
   <td>Components</td> 
   <td><p>Adobe does not plan to make further enhancements to the Foundation Components listed below. AEM 6.4 has the Foundation Components included, and customers upgrading from earlier releases can keep using them as is. Note that Foundation Components remain fully supported while being deprecated. </p> 
    <ul> 
     <li>foundation/components/account/accountname</li> 
     <li>foundation/components/account/actions</li> 
     <li>foundation/components/account/passwordreset</li> 
     <li>foundation/components/account/requestconfirmation</li> 
     <li>foundation/components/adaptiveimage</li> 
     <li>foundation/components/assetsharepage</li> 
     <li>foundation/components/breadcrumb</li> 
     <li>foundation/components/form/creditcard</li> 
     <li>foundation/components/listchildren</li> 
     <li>foundation/components/login</li> 
     <li>foundation/components/logo</li> 
     <li>foundation/components/mobilefooter</li> 
     <li>foundation/components/mobileimage</li> 
     <li>foundation/components/mobilelist</li> 
     <li>foundation/components/mobilelogo</li> 
     <li>foundation/components/mobilereference</li> 
     <li>foundation/components/mobiletextimage</li> 
     <li>foundation/components/mobiletopnav</li> 
     <li>foundation/components/search</li> 
     <li>foundation/components/sitemap</li> 
     <li>foundation/components/table</li> 
     <li>foundation/components/toolbar</li> 
     <li>foundation/components/topnav</li> 
     <li>foundation/components/userinfo</li> 
    </ul> </td> 
   <td>Customers are advised to use the Core Components for future projects. Existing sites do not need to be changed.</td> 
  </tr>
  <tr>
   <td>Components</td> 
   <td><p>Adobe does not plan to make further enhancements to the Foundation Components listed below. AEM 6.4 has the Foundation Components included, and customers upgrading from earlier releases can keep using them as is. Note that Foundation Components remain fully supported while being deprecated.</p> 
    <ul> 
     <li>foundation/components/timing</li> 
    </ul> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Portal Director</td> 
   <td><p>The Portal Director is a set of features, that enables the hosting of AEM content via Portlet in 3rd party servers.</p> <p>Adobe does not plan to make further enhancements to the Portal Director feature under the location listed below. AEM 6.4 has the Portal Director included, and customers upgrading from earlier releases can keep using it as is. Note that Portal Direct remains fully supported while being deprecated.</p> 
    <ul> 
     <li>/libs/portal/director</li> 
    </ul> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Portlet Component</td> 
   <td><p>Portlet Components under /foundation/components/portlet enables the hosting of JSR Portlets in AEM as components.</p> <p>Adobe does not plan to make further enhancements to the Portlet Component feature. AEM 6.4 has the Portlet Component included, and customers upgrading from earlier releases can keep using it as is. Note that Portlet Component remains fully supported while being deprecated.</p> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td><p>Support for Adobe Central Migration Bridge service has been deprecated as Adobe Central product is no longer supported.</p> </td> 
   <td>No replacement </td> 
  </tr>
    <tr>
   <td>Forms</td> 
   <td><p>Deprecated use of JSONObject in Query and OperationOptions. The following APIs are deprecated:
   <ul><li>setArguments(JSONObject arguments)</li><li>JSONObject getArguments()</li><li>OperationOptions(String operationId, JSONObject arguments</li><li>JSONObject getArguments()</li><li>void setArguments(JSONObject arguments)</li></ul>
   </p> </td> 
   <td>Use the IValueMap API </td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td><p>Deprecated Central Migration Bridge service</p> </td> 
   <td> No replacement </td> 
  </tr>
  <tr>
   <td>Assets</td> 
   <td><p>Assets Offloading has been deprecated starting with AEM 6.4</p> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>
-->

## 已移除功能{#removed-features}

下表列出已從6.4移除的AEM功能。舊版的這些功能標示為
已過時。

| 區域 | 功能 | 替代方案 |
|---|---|---|
| 分析Activity Map | 包含在中的Activity Map版本AEM。 | 由於 Adobe Analytics API 中的安全性變更，AEM 中包含的 Activity Map 版本已無法再使用。現在應使用Adobe Analytics提供的[ActivityMap外掛程式。](https://docs.adobe.com/content/help/zh-Hant/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html) |
| 元件-Forms | 表單驗證碼(foundation/components/form/captcha) | 請改用Google的ReCaptcha元件 |
| 元件 | 投影片（基礎／元件／投影片） | 無取代 |
| 元件 | Flash（基礎／元件/flash） | 無取代 |
| 元件 | 已移除對視訊元件（基礎／元件／視訊）中播放SWF檔案的支援 | 使用無Flash視訊格式。 |
| 元件 | 產品表(commerce/components/product_table) | 無取代 |
| 任務管理 | 傳統UI任務管理(/libs/cq/taskmanagement/content/taskmanager.html) | 自6.0起已過時。使用與工作流UI結合的新任務管理。 |
| 工作流程 | 5.6-6.2之間使用的通知UI(/libs/cq/workflow/content/notifications.html) | 工作流程收件匣/aem/inbox |
| 表單 | 已移除使用PDF產生器的PDF/E-1格式Export PDF。 | PDF產生器繼續支援將PDF匯出為PDF/A-1a/b、PDF/A-2a/b和PDF/A-3a/b格式。 |
| 表單 | 已移除檔案片段內影像的支援。 | 互動式通訊提供直接在印刷和網頁頻道使用影像的功能。 |
| 表單 | 現場升級 | 不提供現場升級支援 |
| 表單 | TarMK到DocumentMK遷移的側面 | 您可以從舊式系統匯出資料，然後匯入新安裝的系統。 如需詳細指示，請參閱AEM Forms的JEE升級檔案 |
| 表單 | AEM Forms的JEE 32位元安裝程式未提供。 | Adobe已停止運送JEE 32位元安裝程式的AEM Forms。 您可以繼續使用64位元安裝程式，將AEM Forms安裝在JEE上。 |
| 表單 | 移除在檔案片段元件中使用DAM影像的支援。 | 您可以在互動式通訊的列印頻道中使用影像和圖表元件。 如果您使用最適化檔案的檔案片段元件進行最適化表單，則在升級至AEM6.4Forms後，它會停止運作。 |
| 表單 | 移除最適化檔案功能 | 您可以使用互動式通訊功能來建立平面和網路通訊。 如果您使用「最適化檔案」，請安裝相容性套件以繼續使用現有的最適化檔案 |
| 表單 | 已移除JEE專用登陸頁面上的AEM Forms。 | AEM Forms的JEE登陸頁面已取代AEM為登陸頁面(/aem/start.html) |
| 表單 | 已移除預設驗證碼的支援 | 使用Google提供的reCAPTCHA服務。 |
| 表單 | 已移除Designer中對flash欄位的AEM支援。 設AEM計人員不允許編輯表單中使用的Flash欄位。 | 您可以使AEM用舊版的Designer來編輯此類表格。 |
| 社群 | 已移除對驗證驗證的支援。 | 使用自訂的captcha整合（例如Google的reCAPTCHA）進行驗證。 |

## 下一版的預發佈{#pre-announcement-for-next-release}

下表提供未來版本的變更清單，這些變更並未過時，但可能會影響客戶。 這些是為規劃目的而提供的。

| 區域 | 功能 | 公告 |
|---|---|---|
| 瀏覽器支援 | Microsoft Internet Explorer | AEM 6.4是支援Microsoft Internet Explorer 11的最後一個版本。 |
| Foundation | UI架構 | Adobe在2019年淘汰了Coral UI 2元件。 AEM 6.4完全以Coral UI 3(隨AEM6.2推出)為基礎。 Adobe建議已使用Coral 2建立自訂UI的客戶和合作夥伴，將這些UI重構至Coral 3。 Adobe提供將Coral 2對話框轉換為Coral 3 - [閱讀更多資訊。](/help/sites-developing/modernization-tools.md) |

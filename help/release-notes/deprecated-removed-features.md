---
title: 過時和移除的功能
description: Adobe Experience Manager 6.4中已棄用和已移除功能的發行說明。
exl-id: 2fe0dad7-fc78-4aac-afa3-79a278008453
source-git-commit: dcc36e499517f3f35d5f1d849802c4a5c35121bd
workflow-type: tm+mt
source-wordcount: '1310'
ht-degree: 13%

---

# 過時和移除的功能 {#deprecated-and-removed-features}

Adobe 持續評估產品功能，以更新或替代的方式來改善或取代舊功能，以提升客戶享有的整體價值，且隨時謹慎考慮是否回溯相容。

若要傳達 AEM 功能即將移除/取代的訊息，請套用下列規則：

1. 首先需公告功能已過時。雖然已過時，但功能仍可供使用，但不會進一步增強。
1. 下列主要版本將盡早移除已棄用的功能。 將公佈實際的移除日期。

此程序可讓客戶在功能真正移除之前，至少還有一個發行週期，讓實作適應過時功能的新版本或後續版本。

## 過時的功能 {#deprecated-features}

下表列出AEM 6.4已標示為過時的功能。一般而言，未來版本中預計移除的功能會先設為過時，並提供替代選項。

建議客戶檢視是否在目前的部署中使用這些功能，並規劃變更實作，改為使用所提供的替代方案。

<!-- TBD: This MD table is a replacement of the HTML table below. However, it generates validation error hence commenting and replacing with inline text. Restore if required. -->

| 區域 | 功能 | 替代方案 |
|---|---|---|
| UI | Adobe不打算對傳統UI進行進一步的增強。 AEM 6.4已包含傳統UI，而從舊版升級的客戶可繼續依原樣使用。 請注意，舊版UI仍完全受支援。 <ul> <li>`/libs/cq/core/content/welcome.html` </li> <li> `/siteadmin` </li> <li> `/damadmin` </li> <li> `/mcmadmin` </li> <li> `/inbox` </li> <li> `/tagging` </li> <li> `/cf#` （頁面編輯器） </li><li> `/libs/launches/content/admin.html` </li> <li> `/libs/cq/workflow/content/console.html` </li> </ul> | 建議客戶改用新的AEM UI。 |
| 元件 | Adobe不打算對下列Foundation元件進行進一步的增強。 AEM 6.4已包含Foundation元件，從舊版升級的客戶可繼續依原樣使用。 請注意，Foundation元件在淘汰時仍完全受支援。 <ul> <li> foundation/components/account/accountname </li> <li> foundation/components/account/actions </li> <li> foundation/components/account/passwordeset </li> <li> foundation/components/account/requestconfirmation </li> <li> 基礎/元件/自適應影像 </li> <li> foundation/components/assetsharepage </li> <li> foundation/components/breadcrum </li> <li> foundation/components/form/creditcard </li> <li> foundation/components/listchildren </li> <li> foundation/components/login </li> <li> foundation/components/logo </li> <li> foundation/components/mobilefooter </li> <li> foundation/components/mobileimage </li> <li> foundation/components/mobilelist </li> <li> foundation/components/mobilelogo </li> <li> foundation/components/mobilereference </li> <li> foundation/components/mobiletextimage </li> <li> foundation/components/mobiletopnav </li> <li> foundation/components/search </li> <li> foundation/components/sitemap </li> <li> foundation/components/table </li> <li> foundation/components/toolbar </li> <li> foundation/components/topnav </li> <li> foundation/components/userinfo </li> </ul> | 建議客戶在未來專案中使用核心元件。 不需要變更現有網站。 |
| 元件 | Adobe不打算對下列Foundation元件進行進一步的增強。 AEM 6.4已包含Foundation元件，從舊版升級的客戶可繼續依原樣使用。 請注意，Foundation元件在淘汰時仍完全受支援。 <ul><li>基礎/元件/計時</li></ul> | Adobe不計畫提供替代。 |
| 入口網站Director | Portal Director是一組功能，可在第三方伺服器中通過Portlet托管AEM內容。 Adobe不打算對下列位置下的Portal Director功能進一步增強。 AEM 6.4已包含入口網站Director，從舊版升級的客戶可繼續依原樣使用。 請注意，Portal Direct在淘汰時仍完全受支援。 <ul><li>/libs/portal/director</li></ul> | Adobe不計畫提供替代。 |
| Portlet元件 | /foundation/components/portlet下的Portlet元件允許將AEM中的JSR Portlet作為元件進行托管。 Adobe不打算對Portlet元件功能進行進一步的增強。 AEM 6.4包含Portlet元件，從舊版升級的客戶可以繼續使用。 請注意，Portlet元件在過時時仍完全受支援。 | Adobe不計畫提供替代。 |
| Forms | 由於不再支援Adobe中心產品，已不再支援Adobe中心移轉橋服務。 | 無替換 |
| Forms | 已棄用在Query和OperationOptions中使用JSONObject。 不建議使用下列API: <ul><li>`setArguments(JSONObject arguments)`</li><li> `JSONObject getArguments()`</li><li>`OperationOptions(String operationId, JSONObject arguments)`</li><li>`JSONObject getArguments()`</li><li> `void setArguments(JSONObject arguments)`</li></ul> | 使用`IValueMap` API |
| Forms | 已棄用的中央遷移橋服務。 | 不提供替代。 |
| 資產 | 自AEM 6.4起，已不再使用「資產卸載」。 |  |
| 開發人員 | Lodash/underscore客戶端庫。 Adobe不計畫進一步維護和更新作為分發（快速入門）的Lodash/underscore客戶端庫 | Adobe建議仍需使用Lodash/底線的客戶，將其程式碼新增至其專案程式碼基底。 |

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

## 移除的功能 {#removed-features}

下表列出已從AEM 6.4中移除的功能。先前版本的這些功能標示為
已棄用。

| 區域 | 功能 | 替代方案 |
|---|---|---|
| 與[!DNL Experience Cloud]整合 | 您可以透過[!DNL Adobe I/O]使用設定，將資產與[!DNL Experience Cloud]同步。 [!DNL Adobe Experience Cloud] 先前稱為 [!DNL Adobe Marketing Cloud]。 | 如果您有任何查詢，請聯繫[Adobe客戶支援](https://experienceleague.adobe.com/?support-solution=General#support)。 |
| AnalyticsActivity Map | AEM中包含的Activity Map版本。 | 由於 Adobe Analytics API 中的安全性變更，AEM 中包含的 Activity Map 版本已無法再使用。現在應該使用Adobe Analytics](https://docs.adobe.com/content/help/zh-Hant/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html)提供的[ActivityMap外掛程式。 |
| 元件 — Forms | 表單驗證碼（基礎/元件/表單/驗證碼） | 請改用ReCaptcha by Google元件 |
| 元件 | 投影片放映（基礎/元件/投影片放映） | 無替換 |
| 元件 | Flash(foundation/components/flash) | 無替換 |
| 元件 | 移除對視訊元件(foundation/components/video)中播放SWF檔案的支援 | 使用無快閃記憶體視訊格式。 |
| 元件 | 產品表(commerce/components/product_table) | 無替換 |
| 任務管理 | 傳統UI任務管理(/libs/cq/taskmanagement/content/taskmanager.html) | 自6.0起已棄用。請使用與工作流UI結合的新任務管理。 |
| 工作流程 | 在5.6到6.2之間使用的通知UI(/libs/cq/workflow/content/notifications.html) | 工作流程收件匣/aem/收件匣 |
| Forms | 已移除使用「Export PDF產生器」的PDF/E-1格式。 | PDF產生器繼續支援將PDF導出為PDF/A-1a/b、PDF/A-2a/b和PDF/A-3a/b格式。 |
| Forms | 已移除對檔案片段內影像的支援。 | 互動式通訊提供直接在列印和網頁頻道中使用影像的功能。 |
| Forms | 外置升級 | 不支援非現場升級 |
| Forms | 從TarMK移轉至DocumentMK的邊級 | 您可以從舊系統匯出資料，然後在新安裝的系統中匯入。 如需詳細指示，請參閱JEE升級檔案上的AEM Forms |
| Forms | AEM Forms on JEE 32位元安裝程式不可用。 | Adobe已停止在JEE 32位元安裝程式上運送AEM Forms。 您可以繼續使用64位元安裝程式，在JEE上安裝AEM Forms。 |
| Forms | 移除在檔案片段元件中使用DAM影像的支援。 | 您可以在互動式通訊的列印通道中使用影像和圖表元件。 如果您在適用性表單中使用適用性檔案的檔案片段元件，則在升級至AEM 6.4 Forms後，該元件會停止運作。 |
| Forms | 移除最適化檔案功能 | 您可以使用互動式通訊功能來建立印刷式和網頁式通訊。 如果您使用適用性檔案，請安裝相容性套件以繼續使用現有的適用性檔案 |
| Forms | 移除JEE專用登陸頁面上的AEM Forms。 | AEM Forms on JEE登陸頁面已取代為AEM登陸頁面(/aem/start.html) |
| Forms | 移除預設驗證碼的支援 | 使用Google提供的reCAPTCHA服務。 |
| Forms | 移除AEM Designer中Flash欄位的支援。 AEM Designer不允許編輯表單中使用的Flash欄位。 | 您可以使用發行於舊版的AEM Designer來編輯這類表單。 |
| 社群 | 已移除驗證碼驗證的支援。 | 使用自訂驗證碼整合(例如Google的reCAPTCHA)進行驗證。 |

## 下次發行的預先公告 {#pre-announcement-for-next-release}

下表提供未來版本的變更清單，這些變更不會過時，但可能會影響客戶。 這些是為規劃目的而提供的。

| 區域 | 功能 | 公告 |
|---|---|---|
| 瀏覽器支援 | Microsoft Internet Explorer | AEM 6.4是支援Microsoft Internet Explorer 11的最後一個版本。 |
| Foundation | UI架構 | Adobe在2019年淘汰Coral UI 2元件。 AEM 6.4完全以Coral UI 3為基礎(隨AEM 6.2推出)。 Adobe建議已使用Coral 2建立自訂UI的客戶和合作夥伴，將這些UI重構至Coral 3。 Adobe提供將Coral 2對話方塊轉換為Coral 3 - [了解詳情。](/help/sites-developing/modernization-tools.md) |

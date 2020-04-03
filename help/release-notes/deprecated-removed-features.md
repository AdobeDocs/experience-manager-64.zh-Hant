---
title: 過時和移除的功能
seo-title: 過時和移除的功能
description: Adobe Experience Manager 6.4中已過時和已移除功能的發行說明。
seo-description: Adobe Experience Manager 6.4中已過時和已移除功能的發行說明。
uuid: 2619039b-72b4-4c6c-a813-90eed622b423
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 15819d42-4897-40fa-a013-e019d1580fa2
translation-type: tm+mt
source-git-commit: d79b5f7204cb7a00cef6d31a1fdd2cbe93a6cfbe

---


# 過時和移除的功能 {#deprecated-and-removed-features}

Adobe 持續評估產品功能，以更新或替代的方式來改善或取代舊功能，以提升客戶享有的整體價值，且隨時謹慎考慮是否回溯相容。

若要傳達 AEM 功能即將移除/取代的訊息，請套用下列規則：

1. 首先需公告功能已過時。雖然已過時，但功能仍可用，但無法進一步增強。
1. 在下列主要版本中，將最早移除已過時的功能。 將公佈實際的移除目標日期。

此程序可讓客戶在功能真正移除之前，至少還有一個發行週期，讓實作適應過時功能的新版本或後續版本。

## Deprecated Features {#deprecated-features}

本節列出已標示為不再提倡的AEM 6.4功能。通常，計畫在未來版本中移除的功能會先設為不建議使用，並提供其他選項。

建議客戶檢視是否在目前的部署中使用這些功能，並規劃變更實作，改為使用所提供的替代方案。

<table> 
 <tbody>
  <tr>
   <td>區域</td> 
   <td>功能</td> 
   <td>替代方案</td> 
  </tr>
  <tr>
   <td>UI</td> 
   <td><p>Adobe不打算對Classic UI做進一步的增強。 AEM 6.4包含Classic UI，而從舊版升級的客戶可依現狀繼續使用。 請注意，Classic UI在遭淘汰時仍完全受支援。 </p> 
    <ul> 
     <li>/libs/cq/core/content/welcome.html</li> 
     <li>/siteadmin</li> 
     <li>/damadmin</li> 
     <li>/mcmadmin</li> 
     <li>/inbox</li> 
     <li>/tagging</li> 
     <li>/cf#（頁面編輯器）</li> 
     <li>/libs/launches/content/admin.html</li> 
     <li>/libs/cq/workflow/content/console.html</li> 
    </ul> </td> 
   <td><p>建議客戶改用新的AEM UI。</p> <p> </p> </td> 
  </tr>
  <tr>
   <td>元件</td> 
   <td><p>Adobe不打算對下列的Foundation Components進行進一步的增強。 AEM 6.4包含Foundation Components，而從舊版升級的客戶可依現狀繼續使用這些元件。 請注意，Foundation Components在遭淘汰時仍完全受支援。 </p> 
    <ul> 
     <li>foundation/components/account/accountname</li> 
     <li>foundation/components/account/actions</li> 
     <li>foundation/components/account/passwordreset</li> 
     <li>foundation/components/account/requestconfirmation</li> 
     <li>foundation/components/adaptive image</li> 
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
   <td>建議客戶將核心元件用於未來的專案。 現有網站不需要變更。</td> 
  </tr>
  <tr>
   <td>元件</td> 
   <td><p>Adobe不打算對下列的Foundation Components進行進一步的增強。 AEM 6.4包含Foundation Components，而從舊版升級的客戶可依現狀繼續使用這些元件。 請注意，Foundation Components在遭淘汰時仍完全受支援。</p> 
    <ul> 
     <li>foundation/components/timing</li> 
    </ul> </td> 
   <td>在寫作時，並不打算提供替代品。</td> 
  </tr>
  <tr>
   <td>入口網站主管</td> 
   <td><p>Portal Director是一組功能，可讓您在協力廠商伺服器中透過Portlet代管AEM內容。</p> <p>Adobe不打算在下列位置下進一步增強Portal Director功能。 AEM 6.4已隨附入口網站控制器，而從舊版升級的客戶可依現狀繼續使用。 請注意，Portal Direct在遭淘汰時仍完全受支援。</p> 
    <ul> 
     <li>/libs/portal/director</li> 
    </ul> </td> 
   <td>在寫作時，並不打算提供替代品。</td> 
  </tr>
  <tr>
   <td>Portlet元件</td> 
   <td><p>/foundation/components/portlet下的Portlet元件允許將AEM中的JSR Portlet作為元件托管。</p> <p>Adobe不打算對Portlet元件功能做進一步的增強。 AEM 6.4包含Portlet元件，而從舊版升級的客戶可依現狀繼續使用。 請注意，Portlet元件在被淘汰時仍完全受支援。</p> </td> 
   <td>在寫作時，並不打算提供替代品。</td> 
  </tr>
  <tr>
   <td>表單</td> 
   <td><p>Adobe Central Migration Bridge服務已不再支援，因為Adobe Central產品不再受支援。</p> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>資產</td> 
   <td><p>已淘汰資產卸載（從AEM 6.4開始）</p> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## Removed Features {#removed-features}

本節列出已從AEM 6.4移除的功能。舊版的這些功能已標示為不建議使用。

<table> 
 <tbody>
  <tr>
   <td><strong>區域</strong></td> 
   <td><strong>功能</strong></td> 
   <td><strong>替代方案</strong></td> 
  </tr>
  <tr>
   <td>Analytics Activity Map</td> 
   <td>AEM中包含的Activity Map版本。</td> 
   <td>由於Adobe Analytics API中的安全性變更，無法再使用AEM中包含的Activity Map版本。<br><br>現在 <a href="https://docs.adobe.com/content/help/en/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html">應使用Adobe Analytics提供的</a> ActivityMap外掛程式。</td> 
  </tr>
  <tr>
   <td>元件</td> 
   <td>表單驗證碼<br /> (foundation/components/form/captcha)</td> 
   <td>請改用Google的ReCaptcha元件</td> 
  </tr>
  <tr>
   <td>元件</td> 
   <td>投影片<br /> （基礎／元件／投影片）</td> 
   <td>無取代</td> 
  </tr>
  <tr>
   <td>元件</td> 
   <td>Flash<br /> （基礎／元件/Flash）</td> 
   <td>無取代</td> 
  </tr>
  <tr>
   <td>元件</td> 
   <td>已移除在視訊元件(基礎／元件<br /> /視訊)中播放SWF檔案的支援</td> 
   <td>使用無Flash視訊格式。</td> 
  </tr>
  <tr>
   <td>元件</td> 
   <td>產品表<br /> (commerce/components/product_table)</td> 
   <td>無取代</td> 
  </tr>
  <tr>
   <td>任務管理</td> 
   <td>傳統UI任務管理<br /> (/libs/cq/taskmanagement/content/taskmanager.html)</td> 
   <td>自6.0起已過時。使用與工作流UI結合的新任務管理。</td> 
  </tr>
  <tr>
   <td>工作流程</td> 
   <td>5.6-6.2之間使用的通知UI<br /> (/libs/cq/workflow/content/notifications.html)</td> 
   <td>工作流程收件匣/aem/inbox</td> 
  </tr>
  <tr>
   <td>表單</td> 
   <td>已移除使用PDF產生器將PDF轉存為PDF/E-1格式。</td> 
   <td>PDF產生器繼續支援將PDF匯出為PDF/A-1a/b、PDF/A-2a/b和PDF/A-3a/b格式。</td> 
  </tr>
  <tr>
   <td>表單</td> 
   <td>已移除最適化表單中預設AEM Captcha服務的支援。 </td> 
   <td>請改用Google的ReCaptcha。</td> 
  </tr>
  <tr>
   <td>表單</td> 
   <td>已移除檔案片段內影像的支援。 </td> 
   <td>互動式通訊提供直接在印刷和網頁頻道使用影像的功能。<br /> </td> 
  </tr>
    <tr>
   <td>表單</td> 
   <td> 現場升級 </td> 
   <td>不提供現場升級支援 <br/> </td> 
  </tr>
  <tr>
   <td>表單</td> 
   <td> TarMK到DocumentMK遷移的側面 </td> 
   <td> 您可以從舊式系統匯出資料，然後匯入新安裝的系統。 如需詳細指示，請參閱JEE升級檔案上的AEM Forms <br/> </td> 
  </tr>
    <tr>
   <td>表單</td> 
 <td>AEM Forms on JEE 32位元安裝程式不提供。</td> 
   <td>Adobe已停止在JEE 32位元安裝程式上運送AEM Forms。 您可以繼續使用64位元安裝程式，在JEE上安裝AEM Forms。 </td>  
  </tr>
    <tr>
    <td>表單</td> 
    <td>移除在檔案片段元件中使用DAM影像的支援。</td> 
    <td> 您可以在互動式通訊的列印頻道中使用影像和圖表元件。 如果您在最適化表單中使用最適化檔案的檔案片段元件，在升級至AEM 6.4 Forms後它就會停止運作。 </td>  
  </tr>
  <tr>
   <td>表單</td> 
   <td> 移除最適化檔案功能</td> 
   <td> 您可以使用互動式通訊功能來建立平面和網路通訊。 <br/> </td> 
  </tr>
    <tr>
    <td>表單</td> 
    <td>已移除JEE特定登陸頁面上的AEM Forms。</td> 
    <td>AEM Forms on JEE著陸頁面已取代為AEM著陸頁面(/aem/start.html) </td>  
  </tr>
   <tr>
   <td>表單</td> 
   <td>已移除預設驗證碼的支援</td> 
   <td>使用Google提供的reCAPTCHA服務。</td> 
  </tr>
  <tr>
   <td>社群</td> 
   <td>已移除對驗證驗證的支援。</td> 
   <td>使用自訂的captcha整合（例如Google的reCAPTCHA）進行驗證。</td> 
  </tr>
 </tbody>
</table>

## 下一版產品的預發佈 {#pre-announcement-for-next-release}

本節用於在未來版本中預先發佈變更，這些變更不會過時，但會影響客戶。 這些是為規劃目的而提供的。

<table> 
 <tbody>
  <tr>
   <td>區域<br /> </td> 
   <td>功能<br /> </td> 
   <td>公告</td> 
  </tr>
  <tr>
   <td>瀏覽器支援</td> 
   <td>Microsoft Internet Explorer</td> 
   <td>AEM 6.4是支援Microsoft Internet Explorer 11的最後一個版本。</td> 
  </tr>
  <tr>
   <td>基礎</td> 
   <td>UI架構</td> 
   <td>Adobe在2019年淘汰了Coral UI 2元件。 AEM 6.4完全以Coral UI 3（隨AEM 6.2推出）為基礎。 Adobe建議已使用Coral 2建立自訂UI的客戶和合作夥伴，將這些UI重構至Coral 3。 Adobe提供工具，將Coral 2對話方塊轉換為Coral 3 —— 閱 <a href="/help/sites-developing/dialog-conversion.md">讀更多</a>。</td> 
  </tr>
 </tbody>
</table>

---
title: 設定和部署AEM畫面
seo-title: 設定和部署畫面
description: AEM Screens播放器適用於Android、Chrome OS、iOS和Windows。 本頁面說明AEM畫面的設定和部署，並摘要播放器裝置的h/w選取方針。
seo-description: AEM Screens播放器適用於Android、Chrome OS、iOS和Windows。 本頁面說明AEM畫面的設定和部署，並摘要播放器裝置的h/w選取方針。
uuid: 8ee5311f-b377-4035-af77-e1391a840745
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: administering
discoiquuid: a94d0891-d75f-482e-8d2a-e0cbf953a9de
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# 設定和部署AEM畫面{#configuring-and-deploying-aem-screens}

本頁說明如何在您的裝置上安裝和設定畫面播放器，並涵蓋下列主題：

* 安裝AEM Screens Player
* 伺服器組態
* 播放器裝置的硬體選擇指南
* 後續步驟

## 安裝AEM Screens Player {#installing-aem-screens-player}

AEM Screens播放器適用於Android、Chrome OS、iOS和Windows。

若要下 **載AEM Screens Player**，請造訪 [**AEM 6.4 Player下載頁面&#x200B;**](https://download.macromedia.com/screens/)。

>[!NOTE]
>
>下載最新的播放器(*.exe*)後，請依照播放器上的步驟完成臨機安裝：
>
>1. 長按左上角以開啟管理面板。
>1. 從左側 **動作功能表導覽至** 「設定」，然後在 **Server中輸入AEM例項的位置位址，然後按一下「儲** 存」 ****。
   >
   >
1. 按一下左 **側動作功能表** 中的「註冊」連結，以及下列步驟以完成裝置註冊程式。
>



### 其他資源 {#additional-resources}

如需深入資訊，請參閱下列主題：

* 若要下載Android Player，請造 **訪Google Play**。 若要瞭解實作Android Watchdog的相關資訊，請參閱實作 **[Android播放器](implementing-android-player.md)**。

* 若要實作Chrome OS Player，請參閱 [Chrome Management Console](implementing-chrome-os-player.md) ，以取得詳細資訊。
* 若要設定AEM Screens Windows player，請參閱「 [實作Windows Player](implementing-windows-player.md)」。

## Server Configuration {#server-configuration}

>[!NOTE]
>
>**重要**:
>
>AEM Screens播放器不會使用跨網站偽造要求(CSRF)代號。 因此，若要設定AEM伺服器並讓AEM伺服器準備好用於AEM畫面，請允許空的反向連結，以略過反向連結篩選。

### 必備條件 {#prerequisites}

下列關鍵點可協助您設定AEM伺服器並讓AEM伺服器準備好用於AEM畫面：

#### 允許空的反向連結請求 {#allow-empty-referrer-requests}

請依照下列步驟來啟用Apache Sling Referrer Filter Allow Empty。 這是AEM Screens player和AEM Screens伺服器之間最佳化控制通訊協定所需的。

1. 導覽至**Adobe Experience Manager Web Console設定**，透過AEM實例—>槌子圖示—> **Operations** —> **Web Console**。

   ![screen_shot_2019-02-11at15405pm](assets/screen_shot_2019-02-11at15405pm.png)

1. **Adobe Experience Manager Web Console設定隨即開啟** 。 搜尋sling referrer。

   若要搜尋sling referrer屬性，請按 **Command+F** for **Mac** , **Control+F** for **** Windows。

   ![screen_shot_2019-02-11at15629pm](assets/screen_shot_2019-02-11at15629pm.png)

1. 勾選「 **允許空白** 」選項，如下圖所示。

   ![screen_shot_2018-12-04at22911pm](assets/screen_shot_2018-12-04at22911pm.png)

1. 按一 **下「儲存** 」以啟用Apache Sling Referrer Filter Allow Empty。

#### 為AEM螢幕啟用Touch UI {#enable-touch-ui-for-aem-screens}

AEM Screens需要TOUCH UI，無法與Adobe Experience Manager(AEM)的CLASSIC UI搭配使用。

1. 導覽至 *&lt;yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. 請確定「預 **設編寫UI** 」模式已設 **為TOUCH**，如下圖所示

或者，您也可以使用*&lt;yourAuthorInstance> *->* （槌子圖示）* -> **Operations** ->**Web Console** ，並搜索 **** WCM編寫模式服務WorkUi。

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>您隨時都可以使用使用者偏好設定，為特定使用者啟用Classic UI。

#### NOSAMPLECONTENT執行模式中的AEM {#aem-in-nosamplecontent-runmode}

在生產中執行AEM會使 **用NOSAMPLECONTENT** 執行模式。 將 *X-Frame-Options=SAMEORIGIN* （在其他回應標題區段中）的標題從

[http://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet](http://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet).

這是AEM Screens Player播放線上頻道的必要項。

#### 密碼限制 {#password-restrictions}

對 ***DeviceServiceImpl進行最新變更***，您不必移除密碼限制。

您可以從 ***下列連結設定DeviceServiceImpl*** ，以在為畫面裝置使用者建立密碼時啟用密碼限制：

[http://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService](http://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService)

請依照下列步驟來設定 ***DeviceServiceImpl***:

1. 透過 **AEM例項** —> hammer圖示—> **Operations** —> **Web Console導覽至Adobe Experience Manager Web Console Configuration**。

1. **Adobe Experience Manager Web Console設定隨即開啟** 。 搜尋裝置服務。 要搜索屬性，請按 **Command+F** ( **Mac)和Control+F(****Windows)** ( **** Windows)。

![screen_shot_2019-02-21at24951pm](assets/screen_shot_2019-02-21at24951pm.png)

#### Dispatcher Configuration {#dispatcher-configuration}

對於**Dispatcher,**將客戶端標頭添加到。any檔案。 允許下列標題透過：

* &quot;X-Requested-With&quot;
* &quot;X-SET-HEARTBEAT&quot;
* &quot;X-REQUEST-COMMAND&quot;

#### Java編碼 {#java-encoding}

將 ***Java編碼設為*** Unicode。 例如， *Dfile.encoding=Cp1252* 將無法運作。

>[!NOTE]
>
>**建議：**
>
>建議在生產使用中，將HTTPS用於AEM Screens Server。

## 播放器裝置的硬體選擇指南 {#hardware-selection-guidelines-for-player-device}

下節提供畫面專案的硬體選擇指南：

* 請務必 ***為PC播放********* 器和顯示面板或投影儀提供商業級或工業級元件。

* 與為數位標牌市場服務的廠商永遠互動。
* 始終考慮環境因素，如環境溫度和相對濕度。
* 請隨時查看電源要求和電源調節。
* 仔細審查應用程式所需的效能需求和I/O埠。

下表摘要了AEM Screens專案的硬體組態及一般使用案例：

<table> 
 <tbody> 
  <tr> 
   <td>播放器設定</td> 
   <td>處理器</td> 
   <td>記憶體</td> 
   <td>儲存固態硬碟</td> 
   <td>GPU</td> 
   <td>顯示</td> 
   <td>I/O</td> 
   <td>典型使用案例</td> 
  </tr> 
  <tr> 
   <td>基本</td> 
   <td>雙核、i3或入門級四核英特爾®凌動處理器</td> 
   <td><p>4GB記憶體</p> <p>2MB快取</p> </td> 
   <td><p>·ChromeOS 32 GB</p> <p>·Windows 128GB</p> </td> 
   <td>OnBoard</td> 
   <td>1920x1080</td> 
   <td>DVI、 <br /> 乙太網／無線<br /> 、2個USB</td> 
   <td> 
    <ul> 
     <li>標準全螢幕循環 <br /> </li> 
     <li>日分割</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>標準</td> 
   <td>四核、英特爾®酷睿i5處理器</td> 
   <td><p>8GB記憶體</p> <p>4MB快取</p> </td> 
   <td>128 GBB</td> 
   <td>OnBoard</td> 
   <td>3840x2160(4K)</td> 
   <td>DVI、HDMI<br /> 乙太網／無線<br /> ,2個USB</td> 
   <td> 
    <ul> 
     <li>單一來源動態內容 </li> 
     <li>簡單的互動功能</li> 
     <li> 1-3個區域佈局</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>進階</td> 
   <td>四核超線程，英特爾®酷睿i7處理器</td> 
   <td><p>16GB的記憶體</p> <p>8MB快取</p> </td> 
   <td>256 GB</td> 
   <td>Discreet GPU</td> 
   <td>3840x2160(4K)</td> 
   <td>DVI、HDMI<br /> 乙太網／無線<br /> 4個USB</td> 
   <td> 
    <ul> 
     <li>4個或多個內容區域，並行視訊播放</li> 
     <li> 多頁互動</li> 
     <li>多來源資料觸發器</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## 後續步驟 {#the-next-steps}

在安裝並設定Screens播放器後，請依照下列主題開始：

1. [建立和管理畫面專案](creating-a-screens-project.md)
1. [建立和管理渠道](managing-channels.md)
1. [建立和管理位置](managing-locations.md)
1. [建立和管理顯示](managing-displays.md)
1. [指派渠道](channel-assignment.md)
1. [管理裝置](managing-devices.md)
1. [註冊設備](device-registration.md)
1. [指派裝置](managing-devices.md)
1. [建立和管理計畫](managing-schedules.md)
1. [AEM Screens 播放器](working-with-screens-player.md)
1. [設備控制中心故障排除](monitoring-screens.md)


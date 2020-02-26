---
title: Adobe Analytics與AEM Screens整合
seo-title: Adobe Analytics與AEM Screens整合
description: 請依照本頁瞭解AEM Screens與Adobe Analytics的立即可用整合，並提供您播放證明。
seo-description: 請依照本頁瞭解AEM Screens與Adobe Analytics的立即可用整合，並提供您播放證明。
uuid: f4f71c85-ab6b-4e4d-94d3-5ba55ec0a246
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: administering
discoiquuid: 2784b590-3402-492f-94a6-36fe16633e89
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Adobe Analytics與AEM Screens整合{#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>只有在您已安裝AEM 6.4.2 Feature Pack 2和AEM 6.3.3 Feature Pack 4時，才能使用此AEM Screens功能。

>若要存取其中一個功能套件，您必須聯絡Adobe支援並要求存取權。 一旦您擁有權限，就可從「套件共用」下載。
>
本節涵蓋下列主題：

* **概覽**
* **架構細節**
* **配置屬性**

## 概覽 {#overview}

***AEM Screens運用Adobe Analytics*** ，讓您能夠達成市場上獨一無二的目標——跨通道分析，協助將位置顯示的內容與其他資料來源建立關聯。

AEM Screens提供與Adobe Analytics的立即可用整合，並提供您播放證明。

本節說明連接AEM Screens專案與Adobe Analytics時涉及的下列功能：

* 允許依裝置提供播放報告證明
* 允許依資產提供播放證明報告
* 確保所有播放器事件都已擷取並加上時間戳記
* 如果播放未連線至網路，請確保所有播放器事件都儲存在本機

因此，Adobe Analytics與AEM Screens的整合會強制執行下列 *目標*:

* 實現數位標牌實作的投資報酬率
* 將Analytics整合為基礎，以便日後能夠收集和分析使用資訊

## 架構細節 {#architectural-details}

以下架構圖說明Adobe Analytics與AEM畫面的整合：

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## 在AEM畫面中啟用Adobe Analytics {#enabling-adobe-analytics-in-aem-screens}

您可從OSGi主控台設定Adobe Analytics設定。

導覽至 **Adobe Experience Manager Web Console設定** ，以設定適用於AEM畫面的Adobe Analytics，如下圖所示：

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

### 配置屬性 {#configuring-the-properties}

>[!CAUTION]
在您設定屬性之前，請連絡您的Adobe關係管理員以建立票證，以取得 **Analytics API金鑰****和Analytics Project** ，以便與AEM Screens搭配使用。

下表反白顯示用於設定AEM畫面的Adobe Analytics的屬性及其說明：

<table> 
 <tbody>
  <tr>
   <td><strong>屬性</strong></td> 
   <td><strong>說明</strong></td> 
  </tr>
  <tr>
   <td><strong>Analytics URL</strong></td> 
   <td>從播放器張貼分析資料的URL<br /> </td> 
  </tr>
  <tr>
   <td><strong>Analytics API金鑰</strong></td> 
   <td>驗證至Adobe Analytics伺服器（由帳戶管理員提供）的API金鑰</td> 
  </tr>
  <tr>
   <td><strong>Analytics專案</strong></td> 
   <td>AEM Screens專案已設定在您的分析上，以接收資料（由帳戶管理員提供）</td> 
  </tr>
  <tr>
   <td><strong>環境</strong></td> 
   <td><p>舞台或生產環境。</p> <p><em>針對開發／階段</em> - https://cc-api-data-stage.adobe.io/ingest/<br /> <em>For Production</em> - https://cc-api-data.adobe.io/ingest/</p> </td> 
  </tr>
  <tr>
   <td><strong>Analytics傳送頻率</strong></td> 
   <td>從播放器傳送分析資料的頻率（以分鐘為單位）。 預設為15分鐘。</td> 
  </tr>
 </tbody>
</table>

>[!NOTE]
依預設，**Analytics傳送頻率**為15分鐘。

#### 在AEM畫面中使用Adobe Analytics服務 {#using-adobe-analytics-service-in-aem-screens}

此藍本會透過來自韌體和儀器畫面核心元件中分析服務的REST呼叫來叫用Analytics API，以明確建立和傳送特定使用案例的事件，同時允許從自訂開發頻道傳送任何自訂訊息至Analytics的擴充性。

Analytics事件會離線儲存在indexedDB中，稍後會將其分塊並傳送至雲端。

>[!NOTE]
若要進一步了 ***解***&#x200B;事件的排序和標準資料模型&#x200B;***，請參閱「AEM Screens」（AEM畫面開發人員）區段中的「*** Configuring Adobe Analytics for AEM Screens [](configuring-adobe-analytics-aem-screens.md) 」（設定Adobe Analytics for AEM畫面）。


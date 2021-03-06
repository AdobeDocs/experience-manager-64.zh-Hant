---
title: Dynamic Media 6.4的存放庫重新調整
seo-title: Dynamic Media 6.4的存放庫重新調整
description: 了解如何進行必要的變更，以移轉至AEM 6.4 for Dynamic Media中的新存放庫結構。
seo-description: 了解如何進行必要的變更，以移轉至AEM 6.4 for Dynamic Media中的新存放庫結構。
uuid: e26d61a4-47b6-493a-9ba2-4c58b200ddd9
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 61cd5751-0dc8-48e0-873e-3a64899489bb
feature: 升級
exl-id: 1323ee60-c80c-4eed-b3e5-aa0f0c07e6ee
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 4%

---

# Dynamic Media存放庫重新調整AEM 6.4{#dynamic-media-repository-restructuring-in-aem}

如上層[AEM 6.4](/help/sites-deploying/repository-restructuring.md)中的存放庫重組頁面所述，升級至AEM 6.4的客戶應使用此頁面評估與影響Dynamic Media解決方案的存放庫變更相關的工作量。 AEM 6.4升級程式中有些變更需要付出大量工作，有些則可延後至6.5升級。

**6.5之前的升級**

* [自訂最適化視訊編碼設定](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#custom-adaptive-video-encoding-configurations)
* [Dynamic Media(DMS7)雲端設定](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#dynamic-media-dms-cloud-configuration)
* [Dynamic Media（DM混合）Cloud Service設定](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#cloudserviceconfiguration)
* [Dynamic Media - YouTubeCloud Service設定](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#youtubecloudserviceconfiguration)
* [雜項](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#misc)

## 在6.5之前升級{#prior-to-upgrade}

### 自訂最適化視訊編碼設定{#custom-adaptive-video-encoding-configurations}

<table> 
 <tbody>
  <tr>
   <td><strong>上一位置</strong></td> 
   <td><code>/etc/dam/video/dynamicmedia</code></td> 
  </tr>
  <tr>
   <td><strong>新位置</strong></td> 
   <td><code>/conf/global/settings/dam/dm/presets/video/jcr:content</code></td> 
  </tr>
  <tr>
   <td><strong>重組指導</strong></td> 
   <td><p>您可以執行下列移轉指令碼，以移轉至新位置：</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>或者，您也可以在AEM UI中編輯設定，變更將儲存至新位置。</p> </td> 
  </tr>
  <tr>
   <td><strong>附註</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Dynamic Media(DMS7)雲配置{#dynamic-media-dms-cloud-configuration}

<table> 
 <tbody>
  <tr>
   <td><strong>上一位置</strong></td> 
   <td><code>/etc/cloudservices/dmscene7</code></td> 
  </tr>
  <tr>
   <td><strong>新位置</strong></td> 
   <td><code>/conf/global/settings/cloudservices/dmscene7</code></td> 
  </tr>
  <tr>
   <td><strong>重組指導</strong></td> 
   <td><p>客戶可以在此位置運行遷移指令碼：<br /> </p> 
    <ul> 
     <li><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li> 
     <li>重新啟動Dynamic Media OSGi套件組合。</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>附註</strong></td> 
   <td>N/A</td> 
  </tr>
 </tbody>
</table>

### Dynamic Media（DM混合）Cloud Service設定 {#cloudserviceconfiguration}

<table> 
 <tbody>
  <tr>
   <td><strong>上一位置</strong></td> 
   <td><code>/etc/cloudservices/dynamicmediaservices</code></td> 
  </tr>
  <tr>
   <td><strong>新位置</strong></td> 
   <td><code>/conf/global/settings/dam/dm/cloudservices/dynamicmediaservices</code></td> 
  </tr>
  <tr>
   <td><strong>重組指導</strong></td> 
   <td><p>您可以執行下列移轉指令碼，以符合最新模型：</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.jso</em></p> </td> 
  </tr>
  <tr>
   <td><strong>附註</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### Dynamic Media - YouTubeCloud Service設定  {#youtubecloudserviceconfiguration}

<table> 
 <tbody>
  <tr>
   <td><strong>上一位置</strong></td> 
   <td><code>/etc/cloudservices/youtube</code></td> 
  </tr>
  <tr>
   <td><strong>新位置</strong></td> 
   <td><code>/libs/settings/dam/dm/youtube</code></td> 
  </tr>
  <tr>
   <td><strong>重組指導</strong></td> 
   <td><p>1.從YouTube<br /> 2取消發佈所有視訊。 使用新的觸控式UI（來自<code>/conf</code>）建立YouTube設定，包括從舊位置<br /> 3複製所有通道。 將所有影片發佈回YouTube。</p> <p>此工作流程會產生新的YouTube URL。 如果您在建立新的觸控式UI YouTube設定前未取消發佈，則「屬性」下會列出多個YouTube URL，因為如果有機會，重新建立的管道會再次發佈。 這表示您的「屬性」下會列出無用的URL。</p> </td> 
  </tr>
  <tr>
   <td><strong>附註</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>

### 雜項 {#misc}

<table> 
 <tbody>
  <tr>
   <td><strong>上一位置</strong></td> 
   <td><code>/etc/dam/imageserver/macros</code></td> 
  </tr>
  <tr>
   <td><strong>新位置</strong></td> 
   <td><code>/conf/global/settings/dam/dm/presets/macro</code></td> 
  </tr>
  <tr>
   <td><strong>重組指導</strong></td> 
   <td><p>客戶可執行以下移轉指令碼。</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>或者，您也可以在AEM UI中編輯設定，變更將儲存至新位置。</p> </td> 
  </tr>
  <tr>
   <td><strong>附註</strong></td> 
   <td>不適用</td> 
  </tr>
 </tbody>
</table>

<table> 
 <tbody>
  <tr>
   <td><strong>上一位置</strong></td> 
   <td><code>/etc/dam/presets/analytics</code></td> 
  </tr>
  <tr>
   <td><strong>新位置</strong></td> 
   <td><code>/libs/settings/dam/dm/analytics</code></td> 
  </tr>
  <tr>
   <td><strong>重組指導</strong></td> 
   <td><p>客戶可執行以下移轉指令碼。</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> </td> 
  </tr>
  <tr>
   <td><strong>附註</strong></td> 
   <td>不適用</td> 
  </tr>
 </tbody>
</table>

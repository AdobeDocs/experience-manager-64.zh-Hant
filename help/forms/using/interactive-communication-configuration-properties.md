---
title: 互動式通信配置屬性
seo-title: 互動式通信配置屬性
description: 編輯Interactive Communications的預設配置屬性
seo-description: 編輯Interactive Communications的預設配置屬性
uuid: 793da9c0-7e8b-464c-b41d-559a72fac9eb
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: interactive-communications
discoiquuid: 1aef2a51-4391-4075-8841-a62ace5606f9
feature: 互動式通訊
exl-id: 2caf7242-8588-4fc9-9429-40e24416d6eb
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 6%

---

# 互動式通信配置屬性{#interactive-communications-configuration-properties}

編輯Interactive Communications的預設配置屬性

「互動式通訊」包含安裝[AEM Forms附加元件](/help/forms/using/installing-configuring-aem-forms-osgi.md)套件後自動設定的屬性。 互動式通訊作者可使用&#x200B;**Adobe Experience Manager Web主控台設定**&#x200B;頁面編輯這些預設設定屬性。

使用下列URL開啟「**Adobe Experience Manager Web Console設定**」頁面：

https://&lt;server>:&lt;port>/&lt;contextPath>/system/console/configMgr

配置屬性包括：

* [檔案片段設定](#document-fragments-configuration)
* [建立通信配置](#create-correspondence-configuration)
* [最適化表單與互動式通訊Web通道設定](#adaptive-form-and-interactive-communication-web-channel-configuration)
* [最適化表單與互動式通訊Web通道主題設定](#adaptive-form-and-interactive-communication-web-channel-theme-configuration)

## 文檔片段配置{#document-fragments-configuration}

點選&#x200B;**Adobe Experience Manager Web Console Configuration**&#x200B;頁面上的&#x200B;**檔案片段設定** ，以檢視檔案片段的設定屬性。

<table> 
 <tbody> 
  <tr> 
   <td>屬性</td> 
   <td>說明</td> 
   <td>預設</td> 
   <td>可接受的值</td> 
  </tr> 
  <tr> 
   <td>資料顯示格式</td> 
   <td>建立「打印」和「Web」通道的「互動式通信」時，可用的欄位、變數和表單資料模型元素的區域設定特定顯示格式。</td> 
   <td> 
    <ul> 
     <li>locale = en_US、de_DE、fr_FR和ja_JP</li> 
     <li>dateFormat = dd-MM-yyyy</li> 
     <li>numberDecimalSeparator = 。</li> 
     <li>numberGroupSeparator = ,</li> 
     <li>numberUseGroupSeparator = true</li> 
    </ul> </td> 
   <td><p>—</p> </td> 
  </tr> 
  <tr> 
   <td>縮排</td> 
   <td>應用於清單文檔片段中文本的單個縮進單位的寬度。</td> 
   <td>12.7毫米</td> 
   <td>數量</td> 
  </tr> 
  <tr> 
   <td>羅馬數字最小寬度</td> 
   <td>在清單文檔片段中使用羅馬數字時，應應用於項目符號或數字欄位的最小寬度。 </td> 
   <td>12.7毫米</td> 
   <td>數量</td> 
  </tr> 
  <tr> 
   <td>數字最小寬度</td> 
   <td>在清單文檔片段中使用除羅馬數字之外的編號清單時，應應用於項目符號或編號欄位的最小寬度。</td> 
   <td>8.0毫米</td> 
   <td>數量</td> 
  </tr> 
 </tbody> 
</table>

## 建立通信配置{#create-correspondence-configuration}

點選&#x200B;**Adobe Experience Manager Web Console Configuration**&#x200B;頁面上的&#x200B;**建立通信設定** ，以檢視代理UI的設定屬性。

| 屬性 | 說明 | 預設 | 可接受的值 |
|---|---|---|---|
| 顯示要編輯的已解析內容 | 選取核取方塊，在編輯代理UI上的文字模組時顯示已解析的內容（實際值而非預留位置）。 | 未選擇 | 不適用 |
| 預覽期間套用浮水印 | 選中複選框，以在預覽模式下將水印應用到互動式通信的打印通道。 | 未選擇 | 不適用 |

## 最適化表單與互動式通訊Web通道配置{#adaptive-form-and-interactive-communication-web-channel-configuration}

點選&#x200B;**Adobe Experience Manager Web Console Configuration**&#x200B;頁面上的&#x200B;**適用性表單和互動式通訊Web通道設定** ，以檢視適用性Forms和互動式通訊Web通道的設定屬性。 下表介紹了與Interactive Communications相關的屬性：

| 屬性 | 說明 | 預設 | 可接受的值 |
|---|---|---|---|
| 顯示佔位符 | 選取核取方塊，即可針對適用性表單和互動式通訊中包含的欄位顯示預留位置。 | 已選取 | 不適用 |
| 最大快取條目數 | 設定使用快取記憶體可擷取的最大適用性表單和互動式通訊數量。 | 100 | 數量 |
| 使檔案名稱唯一 | 選取核取方塊，在適用性Forms和互動式通訊中為包含作為附件的檔案指定唯一名稱。 | 未選擇 | 不適用 |

## 最適化表單與互動式通訊Web通道主題配置{#adaptive-form-and-interactive-communication-web-channel-theme-configuration}

點選&#x200B;**Adobe Experience Manager Web控制台配置**&#x200B;頁面上的&#x200B;**適用性表單和互動式通信Web通道主題配置**&#x200B;以查看適用性Forms和互動式通信Web通道主題的配置屬性。

<table> 
 <tbody> 
  <tr> 
   <td>屬性</td> 
   <td>說明</td> 
   <td>預設</td> 
   <td>可接受的值</td> 
  </tr> 
  <tr> 
   <td>字型清單名稱</td> 
   <td>建立最適化Forms和互動式通訊時可用的字型清單。</td> 
   <td><p>喬治亞</p> <p>Book Antiqua</p> <p>Times New Roman</p> <p>Arial</p> <p>Arial Black</p> <p>影響</p> <p>Palatino Linotype</p> </td> 
   <td>所有有效的Adobe伺服器字型</td> 
  </tr> 
 </tbody> 
</table>

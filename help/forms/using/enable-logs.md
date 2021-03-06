---
title: 啟用HTML5表單記錄
seo-title: 啟用HTML5表單記錄
description: 記錄器公用程式會啟用表單的記錄，並協助您偵錯表單相關問題。
seo-description: 記錄器公用程式會啟用表單的記錄，並協助您偵錯表單相關問題。
uuid: d6279092-57f3-4fc6-b41b-9caf65459d4d
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 23bc7cd2-7d06-4ef8-977a-778e290daef9
feature: 行動表單
exl-id: c7953d1b-a332-4138-b744-516f3881cd4d
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 5%

---

# 啟用HTML5表單{#enable-logging-for-html-forms}的記錄

您可以配置記錄器實用程式，以開始為HTML5表單建立記錄。 記錄器公用程式有各種層級，您可以根據需求設定層級。 HTML5表單有伺服器和用戶端元件。 您可以為這兩個元件設定記錄檔。

## 配置伺服器端記錄{#configuring-server-side-logging}

執行下列步驟來設定伺服器端記錄檔：

1. 前往 `https://[server]:[port]/system/console/configMgr`. 找到並開啟&#x200B;*Apace Sling記錄器configuration*&#x200B;選項。 隨即出現對話方塊：

   ![ Apace Sling記錄器配置選項對話框](assets/logconfig.png)

   Apace Sling記錄器配置選項

1. 將&#x200B;**記錄層級**&#x200B;變更為&#x200B;**Debug**。

1. 指定&#x200B;**日誌檔案**&#x200B;的名稱和路徑。

   >[!NOTE]
   >
   >若要在HTML5表單記錄目錄中產生記錄檔，請在檔案名稱前新增……/logs/。

1. 將&#x200B;**Logger**&#x200B;更改為&#x200B;**HTMLFormsPerfLogger。**&#x200B;按一下「**儲存**」。

## 配置客戶端日誌{#configuring-client-logging}

您可以使用下列方法來啟用HTML5表單中的用戶端記錄：

* 使用名為`log`的請求參數
* 使用CQ Configuration Manager

### 使用請求參數{#enabling-logging-using-request-parameter}啟用記錄

使用此方法，您可以產生特定請求的記錄。 請求參數的名稱為&#x200B;**log**。 記錄URL如下：

`https://<server>:<port>/content/xfaforms/profiles/test.html?contentRoot=<path of the folder containing form xdp>&template=<name of the xdp>&log=<log configuration>.`

日誌配置由日誌級別和記錄器類別組成。

#### 日誌目標{#log-destination}

<table> 
 <tbody> 
  <tr> 
   <th><strong>記錄目標</strong></th> 
   <th><strong>說明</strong></th> 
  </tr> 
  <tr> 
   <td>1</td> 
   <td>記錄檔會導向至瀏覽器<strong>主控台</strong></td> 
  </tr> 
  <tr> 
   <td>2</td> 
   <td>記錄會在用戶端的JavaScript物件中收集，並可發佈至<strong>Server</strong> </td> 
  </tr> 
  <tr> 
   <td>3</td> 
   <td>上述兩個選項<br /> </td> 
  </tr> 
 </tbody> 
</table>

#### 日誌級別{#log-levels}

<table> 
 <tbody> 
  <tr> 
   <th>記錄層級</th> 
   <th>說明</th> 
  </tr> 
  <tr> 
   <td>0</td> 
   <td>關閉<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>3</td> 
   <td>致命<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>2</td> 
   <td>錯誤<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>3</td> 
   <td>警告<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>4</td> 
   <td>資訊<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>5</td> 
   <td>DEBUG<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>6</td> 
   <td>TRACE<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>7</td> 
   <td>全部<br type="_moz" /> </td> 
  </tr> 
 </tbody> 
</table>

#### 記錄器類別{#logger-categories}

<table> 
 <tbody> 
  <tr> 
   <th>記錄類別</th> 
   <th>說明</th> 
  </tr> 
  <tr> 
   <td>a</td> 
   <td>xfa（指令碼引擎相關記錄檔）</td> 
  </tr> 
  <tr> 
   <td>b</td> 
   <td>xfaView（佈局引擎相關日誌）<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>c</td> 
   <td>xfaPerf（與效能相關的日誌）<br type="_moz" /> </td> 
  </tr> 
 </tbody> 
</table>

#### 日誌配置{#log-configuration}

在記錄URL中，記錄設定查詢字串參數的定義如下：

`{destination}-{a level}-{b level}-{c level}`

例如：

<table> 
 <tbody> 
  <tr> 
   <th>記錄配置</th> 
   <th>說明</th> 
  </tr> 
  <tr> 
   <td>2-a4-b5-c6<br type="_moz" /> </td> 
   <td>目的地：伺服器<br /> xfa級別：INFO<br /> xfaView級別：DEBUG<br /> xfaPerf級別：TRACE</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>每個日誌類別a(xfa)、b(xfaView)和c(xfaPerf)的預設日誌級別為2(ERROR)。 因此，對於日誌配置：2-b6，不同類別的記錄層級為：\
>a(xfa):2（預設級別錯誤）\
>b(xfaView):6(用戶指定的TRACE)\
>a(xfaPerf):2（預設級別錯誤）

### 使用Configuration Manager {#enabling-logging-using-configuration-manager}啟用記錄

如果您使用Configuration Manager來啟用記錄，則會為每個呈現請求產生記錄，直到再次停用記錄為止。

1. 在`https://[server]:[port]/system/console/configMgr`登入CQ Configuration Manager，並使用管理員憑證登入。
1. 搜尋並按一下&#x200B;**行動Forms設定**。
1. 在「調試選項」文本框中，按上一節所述輸入日誌配置，例如&#x200B;**2-a4-b5-c6**

   ![表單設定](assets/forms_configuration.png)

   表單設定

## 上傳記錄{#uploading-logs}

如果目標設定為1，則所有客戶端指令碼日誌消息都將定向到控制台。 如果管理員需要這些日誌以及伺服器日誌，請將目標級別設定為2。 在此層級，所有記錄會收集在用戶端的JS物件中，如果表單呈現為預設設定檔，則工具列中的&#x200B;**反白顯示現有欄位**&#x200B;按鈕左側會顯示&#x200B;**傳送記錄**&#x200B;按鈕。 當使用者按一下連結時，所有收集的記錄都會張貼至伺服器，並記錄在伺服器上設定的錯誤記錄檔中。

預設情況下，所有資訊都將添加到/crx-repository/logs/目錄的error.log檔案中。

要更改日誌檔案的位置和名稱：

1. 以管理員身分登入Configuration Manager。 Configuration Manager的預設URL為`https://[*Server*]:[*Port*]/system/console/configMgr`。
1. 按一下&#x200B;**Apache Sling Logging Logger Configuration**。 對話方塊隨即顯示。

   ![logconfig-1](assets/logconfig-1.png)

1. 將&#x200B;**記錄層級**&#x200B;變更為Debug。

1. 指定&#x200B;**日誌檔案**&#x200B;的路徑和名稱。

   >[!NOTE]
   >
   >要在保存其他日誌檔案的同一目錄中建立日誌，請在「日誌檔案」屬性中指定……/logs/&lt;filename>。

1. 將&#x200B;**Logger**&#x200B;更改為&#x200B;**HTMLFormsPerfLogger**，然後按一下&#x200B;**Save**。

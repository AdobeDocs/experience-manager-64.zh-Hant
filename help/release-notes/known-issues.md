---
title: AEM 6.4的已知問題
seo-title: AEM 6.4的已知問題
description: Adobe Experience Manager 6.4的已知問題
seo-description: Adobe Experience Manager 6.4的已知問題。
uuid: 1733f15e-9c4f-4db3-98ee-25c2ea606f0d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 266634ab-21d3-4aac-acfa-b799a7485507
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 1%

---


# 已知問題 {#known-issues}

本頁列出2018年4月發行的Adobe Experience Manager 6.4已知問題。 有關已知問題的詳細資訊，請[聯繫支援](https://helpx.adobe.com/tw/support/experience-manager.html)。

## 混合設備{#hybrid-devices}

不支援混合裝置。 使用此類裝置時可能會遇到各種問題。 下列建議的程式有助於解決許多問題：

如果您使用Google Chrome做為瀏覽器：

* 在地址欄中鍵入`chrome://flags/` ，然後按Enter。
* 按一下「啟用觸控事件>停用」。
* 重新啟動瀏覽器（所有標籤和視窗）。

如果您使用Mozilla Firefox做為瀏覽器：

* 在地址欄中鍵入`about:config` ，然後按Enter。
* 將設定篩選為`dom.w3c`。
* 請確定設定為`0`和`false`。
* 重新啟動瀏覽器。

如果您使用Microsoft Edge做為瀏覽器：

* 在地址欄中鍵入`about:flags` ，然後按Return。
* 依序捲動至「實驗性功能」**[!UICONTROL Touch]**。
* 按一下「**[!UICONTROL 啟用觸控事件]**」。
* 選擇&#x200B;**[!UICONTROL 始終關閉]**。
* 重新啟動瀏覽器。

## 平台 {#platform}

* **操作儀表板：當備** 份檔案缺少。zip副檔名時，不顯示進度欄。(GRANITE-10713)
* **HTL:** Java使用物件在套件宣告中包含尾隨空白字元，會凍結SightlyJavaCompilerService(GRANITE-20836)
* **即使在configuration.delete()(GRANITE-20618)之後，Apache Felix/Sling:** Config檔案仍然存在於儲存庫中
* **雲端設定：** 編輯設定容器後，主控台中斷(GRANITE-20726)
* **安全性：** IMS整合失敗，無法與自訂內容路徑整合(GRANITE-20639)
* **安全性：改** 善SSO、外部和預設LoginModules的預設JAAS排名(GRANITE-20590)
* **工具- CRX DE Lite：屬** 性檢視的脊線不斷上移(GRANITE-12040)
* **工具- CRX DE Lite:** 除非您連按兩下「屬性名稱」(GRANITE-12351)，否則無法儲存對「長」值類型的變更

* **工具- CRX DE Lite:** ctrl+F搜尋開啟的文字檔案會停留在RegExp搜尋(GRANITE-5996)

* **工具- CRX DE Lite：在重新命** 名節點後不顯示節點屬性(GRANITE-7160)
* **UI：下** 拉式「更多……」 在IE和Firefox的快顯元素中開啟時，不會顯示所有元素(GRANITE-16326)
* **UI：使** 用固定欄版面搭配2個並排欄時，資訊工具提示會隱藏(GRANITE-16869)
* **UI：模** 擬為不存在的使用者時發生未處理的錯誤(GRANITE-23228)。[實作錯誤處理常式](/help/sites-developing/customizing-errorhandler-pages.md)以自訂錯誤訊息的解決方法。

* **Omnisearch：使** 用反斜線原因例外的搜尋(GRANITE-11769)
* **Omnisearch：在清** 單檢視中開啟「檢視設定」會導致搜尋篩選器變更(GRANITE-16524)
* **Omnisearch：從** 網站進行資產搜尋時顯示的欄設定清單錯誤(GRANITE-16527)

* **Omnisearch：左** 側邊欄謂語與Omnisearch伺服器要求相符(GRANITE-20524)
* **Omnisearch:** Omnisearch不支援內容路徑(GRANITE-16044)

## 資產 {#assets}

* **搜尋**:如果搜尋字串以空格 [OAK-4786開頭，則搜尋不會傳回任何結果](https://issues.apache.org/jira/browse/OAK-4786)

* **搜尋**:在傳統UI和標籤中，搜尋中不顯示(CQ-4235239)

* **UI**:「複製——貼上」和「全選」後，資產UI會停止回應(CQ-4236142)

* **UI**:延遲載入後無法移動資產(CQ-4236134)

* **報表**:資產修改報告建立時出錯(CQ-4239744)

* **報表**:排程的定期資產報表產生失敗（有些報表仍佇列中）(CQ-4239089)

* **中繼資料**:在將多值文字欄位新增至資產結構描述時，必要欄位階層式規則無法運作(CQ-4239333)

* **BrandPortal**:發佈至BrandPortal無法用於系列(CQ-4238731)

* **上傳**:上傳檔案名稱中具有特殊字元的資產時，不會針對每個資產顯示有關不允許字元的驗證錯誤訊息。雖然僅針對第一個資產顯示，但介面會清楚指出不允許提供資產的檔案名稱。 (CQ-4256876)

## 社群 {#communities}

* **協調** -無法從大量協調UI中將父貼文刪除為單一刪除作業(CQ-4236797)

* **控制台** -忘記使用者名稱或密碼連結會重新導向至登入頁面，而非對應的密碼擷取表單(CQ-4237682)

## 表單 {#forms}

### 安裝與部署

* （僅限AEM Forms JEE）當執行Configuration Manager時啟動JBoss應用程式伺服器時，會傳回EJB呼叫和引導失敗錯誤。 但是，您可以忽略它們。 (Ref# CQ-4229793)
* 當AEM Forms啟動時，會出現`SAX Security Manager could not be setup`警告。 (CQ-4297403)

### 互動式通訊

* 代理UI需要一段時間來載入包含圖表或影像元素的互動式通訊。 (CQ-4236630)
* 列印預覽中的資料顯示格式為dd-mm-yyyy，而網頁預覽中的資料顯示格式為`dd-mmm-yy`(CQ-4237045)
* 互動式通訊網路頻道僅支援有序和無序清單。 在清單檔案片段中，互動式通訊的Web頻道不支援複合清單和縮排。 (CQ-4233672)
* 當網頁頻道與列印頻道同步時，會發現下列問題：

   * 首次從列印頻道切換時，網頁頻道需要一段時間才能同步。
   * 如果列印頻道包含未設定的圖表元件，則網頁頻道不會同步。 若要解決此問題，請刪除圖表元件並再次同步。
   * 同步有時會失敗，並出現「同步即時副本時發生錯誤」錯誤。 若要解決此問題，請重新整理頁面。
   * 當表格中的第一欄是列印渠道範本中的標題欄時，版面片段中的靜態文字會以表格儲存格名稱取代。
   * 無法在任何位置新增元件或資產，而非在網路頻道通訊的底部。 若要將它放置在其他位置，請在網頁頻道底部新增面板，然後使用內容樹狀結構重新排序。
   * 可將內容移入Web頻道的繼承目標區域，而不移除即時副本繼承。

(CQ-4239780)

### 資料整合

* SOAP型網站服務的驗證設定不可見，因此無法在雲端服務中設定。 要解決此問題：

   1. 在CRXDE Lite控制台中，轉至以下節點。\
      /libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices/\
      wsdlauthenticsetts/items/fixedcolumns/items/container/items/wsdl/items/\
      選取「驗證／項目／自訂」。
   1. 將value屬性的值更新為與text屬性的值相同。
   1. 按一下「全部儲存」以儲存設定。

(CQ-4238462)

### Adobe Sign整合

* Adobe Sign排程器會間歇性停止運作，因此表單待審簽署不會移至提交。 若要解決此問題，請從https://[*server*]:[*port*]/system/console/bundles的AEM網頁主控台重新啟動&#x200B;**Apache Sling Scheduler Support**&#x200B;套件。

### 最適化表單製作

* 最適化表單中的Chart元件所佔用的空間比一般的要多。
* 在Forms Manager UI中儲存最適化表單、最適化表單片段或互動式通訊的屬性時，會傳回例外。
* 在Android 6.0 Samsung裝置上，不會執行最適化表單文字方塊的指定字元數上限。 (Ref# CQ-4235205)

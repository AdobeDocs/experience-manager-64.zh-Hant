---
title: AEM 6.4的已知問題
seo-title: Known Issues in AEM 6.4
description: Adobe Experience Manager 6.4的已知問題
seo-description: Known Issues in Adobe Experience Manager 6.4.
uuid: 1733f15e-9c4f-4db3-98ee-25c2ea606f0d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 266634ab-21d3-4aac-acfa-b799a7485507
exl-id: ba65e853-d69a-4341-93c3-5628c60c403b
source-git-commit: 7f80933dfe8439bbd57ef85ece96399f7ec39f64
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 3%

---

# 已知問題 {#known-issues}

本頁保留2018年4月發行的Adobe Experience Manager 6.4已知問題清單。 如需已知問題的詳細資訊， [聯絡支援](https://helpx.adobe.com/tw/support/experience-manager.html).

## 混合裝置 {#hybrid-devices}

不支援混合裝置。 使用此類裝置時可能會遇到各種問題。 下列建議的程式有助於解決許多問題：

如果您使用Google Chrome作為瀏覽器：

* 類型 `chrome://flags/` 在地址欄中，然後按Enter鍵。
* 按一下「啟用觸控事件>停用」。
* 重新啟動瀏覽器（所有頁簽和窗口）。

如果您使用Mozilla Firefox作為瀏覽器：

* 類型 `about:config` 在地址欄中，然後按Enter鍵。
* 將設定篩選為 `dom.w3c`.
* 確認設定為 `0` 和 `false`.
* 重新啟動瀏覽器。

如果您使用Microsoft Edge作為瀏覽器：

* 類型 `about:flags` 在地址欄中，然後按返回。
* 然後滾動到實驗功能 **[!UICONTROL 觸控]**.
* 按一下 **[!UICONTROL 啟用接觸事件]**.
* 選擇 **[!UICONTROL 始終關閉]**.
* 重新啟動瀏覽器。

## 平台 {#platform}

* **操作儀表板：** 備份檔案缺少.zip副檔名時，進度列不會顯示。 (GRANITE-10713)
* **HTL:** 套件宣告中尾隨空白字元的Java Use物件會凍結SightlyJavaCompilerService(GRANITE-20836)
* **Apache Felix/Sling:** 即使在configuration.delete()之後，設定檔案仍會存在於存放庫中(GRANITE-20618)
* **雲端設定：** 編輯設定容器後主控台損毀(GRANITE-20726)
* **安全性：** IMS整合因自訂內容路徑而失敗(GRANITE-20639)
* **安全性：** 改善SSO、外部和預設登入模組的預設JAAS排名(GRANITE-20590)
* **工具 — CRX DE Lite:** 屬性檢視脊線持續上升(GRANITE-12040)
* **工具 — CRX DE Lite:** 除非您連按兩下「屬性名稱」(GRANITE-12351)，否則無法儲存對「長」值類型的變更

* **工具 — CRX DE Lite:** 開啟的文字檔案上的ctrl+F搜尋會卡在RegExp搜尋上(GRANITE-5996)

* **工具 — CRX DE Lite:** 更名節點後未顯示節點屬性(GRANITE-7160)
* **UI:** 按一下「更多……」 在IE和Firefox的彈出式元素開啟時，不會顯示所有元素(GRANITE-16326)
* **UI:** 使用固定欄版面配置並排2個欄時，資訊工具提示會隱藏(GRANITE-16869)
* **UI:** 模擬不存在的用戶時出現未處理的錯誤(GRANITE-23228)。 因應措施 [實作錯誤處理常式](/help/sites-developing/customizing-errorhandler-pages.md) 自訂錯誤訊息。

* **Omnisearch:** 具有反斜線原因異常的搜索(GRANITE-11769)
* **Omnisearch:** 在清單檢視中開啟「檢視設定」會導致搜尋篩選條件變更(GRANITE-16524)
* **Omnisearch:** 從網站搜尋資產時顯示的欄設定清單錯誤(GRANITE-16527)

* **Omnisearch:** 左側邊欄述詞與Omnisearch伺服器請求(GRANITE-20524)一起運作
* **Omnisearch:** Omnisearch不支援內容路徑(GRANITE-16044)

## 資產 {#assets}

* **搜尋**:如果搜尋字串的開頭為空白字元，搜尋不會傳回任何結果 [OAK-4786](https://issues.apache.org/jira/browse/OAK-4786)

* **搜尋**:在傳統UI中，「搜尋」中不會顯示標籤(CQ-4235239)

* **UI**:複製貼上和全部選取後，資產UI會停止回應(CQ-4236142)

* **UI**:延遲載入後無法移動資產(CQ-4236134)

* **報表**:建立資產修改報表時出錯(CQ-4239744)

* **報表**:排程的一般資產報表產生失敗失敗（部分報表仍排入佇列）(CQ-4239089)

* **中繼資料**:將多值文字欄位新增至資產結構時，必要欄位階層式規則無法運作(CQ-4239333)

* **BrandPortal**:發佈至BrandPortal無法用於集合(CQ-4238731)

* **上傳**:上傳檔案名稱中含有特殊字元的資產時，不會針對每個資產顯示關於不允許的字元的驗證錯誤訊息。 雖然只會針對第一個資產顯示，但介面會向使用者清楚指出不允許提供資產的檔案名稱。 (CQ-4256876)

## 社群 {#communities}

* **協調**  — 無法從大量協調UI中以單一刪除操作的形式刪除父貼文(CQ-4236797)

* **主控台**  — 忘記使用者名稱或密碼連結會重新導向至登入頁面，而非對應的密碼擷取表單(CQ-4237682)

## Forms {#forms}

### 安裝和部署

* (僅限AEM Forms JEE)執行Configuration Manager時引導JBoss應用程式伺服器時，會傳回EJB呼叫和引導失敗錯誤。 但您可以忽略它們。 (參考編號 CQ-4229793)
* AEM Forms啟動時， `SAX Security Manager could not be setup` 警告出現。 (CQ-4297403)

### 互動式通訊

* 代理UI需要一段時間來載入包含圖表或影像元素的互動式通訊。 (CQ-4236630)
* 列印預覽中的資料顯示格式為dd-mm-yyyy，而Web預覽中為 `dd-mmm-yy` (CQ-4237045)
* 互動式通信Web通道僅支援有序和無序清單。 在清單檔案片段中，互動式通訊的Web通道不支援複合清單和縮排。 (CQ-4233672)
* 當網頁管道與列印管道同步時，會發現下列問題：

   * 首次從列印通道切換時，Web通道需要一段時間才能同步。
   * 如果打印通道包括未配置的圖表元件，則Web通道不會同步。 若要解決此問題，請刪除圖表元件並再次同步。
   * 同步有時會因「同步即時副本時發生錯誤」錯誤而失敗。 若要解決問題，請重新整理頁面。
   * 當表格中的第一欄是列印管道範本中的標題欄時，版面片段中的靜態文字會以表格儲存格名稱取代。
   * 無法在除Web通道通信底部的任何位置添加元件或資產。 若要將其置於其他位置，請在Web頻道底部新增面板，並使用內容樹狀結構重新排序。
   * 可將內容移至Web頻道的繼承目標區域，而不移除即時副本繼承。

(CQ-4239780)

### 資料整合

* 基於SOAP的Web服務的驗證配置不可見，因此無法在雲服務中配置。 若要解決此問題：

   1. 在CRXDE Lite主控台中，前往下列節點。\
      /libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices/\
      wsdlauthenticsettings/items/fixedcolumns/items/container/items/wsdl/items/\
      選取驗證/項目/自訂。
   1. 將value屬性的值更新為與text屬性的值相同。
   1. 按一下「全部儲存」以儲存設定。

(CQ-4238462)

### Adobe Sign整合

* Adobe Sign排程器間歇性停止運作，因此表單待定符號不會移至提交。 若要解決問題，請重新啟動 **Apache Sling排程器支援** 從AEM web主控台套件： https://[*伺服器*]:[*埠*]/system/console/bundles。

### 適用性Forms製作

* 適用性表單中的圖表元件佔用的空間通常比較多。
* 在Forms Manager UI中儲存適用性表單、適用性表單片段或互動式通訊的屬性時，會傳回例外狀況。
* Android 6.0 Samsung 裝置不遵循為適用性表單文字方塊指定的字元數上限。(參考編號 CQ-4235205)
* 當您從Apple iOS裝置提交包含標準HTML上傳欄位的表單時，有時不會傳送檔案內容，而會在另一端收到0位元組檔案。 Apple iOS 15.1已修正問題。


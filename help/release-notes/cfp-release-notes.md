---
title: AEM 6.4 Cumulative Fix Pack發行說明
description: Adobe Experience Manager 6.4 Cumulative Fix Pack的發行說明。
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '2158'
ht-degree: 1%

---


# AEM 6.4 Cumulative Fix Pack發行說明 {#aem-cumulative-fix-pack-release-notes}

## 發行資訊 {#release-information}

| 產品 | **Adobe Experience Manager(AEM)6.4** |
|---|---|
| 版本 | 6.4.8.1 |
| 類型 | 累積修補程式套件 |
| 日期 | 2020年6月04日 |
| 先決條件 | [AEM 6.4 Service Pack 8(6.4.8.0)](sp-release-notes.md) |
| 下載URL | AEM 6.4.8.1軟體散 [發](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fcumulativefixpack%2Faem-6.4.8-cfp-1.0.zip) |

## AEM 6.4.8.1包含的功能 {#what-s-included-in-aem}

AEM Cumulative Fix Pack 6.4.8.1是重要的更新，包含自2020年3月AEM 6.4 Service Pack 8(6.4.8.0)全面推出以來的數項內部和客戶修正。

AEM Cumulative Fix Pack 6.4.8.1需仰賴AEM 6.4 Service Pack 8。 因此，在安裝AEM 6.4 Service Pack 8後，您必須安裝AEM Cumulative Fix Pack 6.4.8.1套件。

AEM 6.4.8.1的一些主要亮點是：

* 已移除與Adobe Experience Manager的套件共用整合。
* 內建儲存庫(Apache Jackrabbit Oak)已更新至1.8.21版。

如需CFP和其他發行類型的詳細資訊，請參閱 [AEM Update Release Vehicle Definitions](../sites-deploying/update-release-vehicle-definitions.md)

## 變更清單 {#list-of-changes}

Adobe Experience Manager 6.4.8.1可修正下列問題。

### 網站 {#sites-6481}

* 當LiveCopy中的本機元件名稱與Blueprint中的元件名稱相同，且元件從Blueprint中推出時，_msm_moved詞語不會新增至本機元件的名稱(NPR-33207)。
* 附加至原始請求的參數不會包含在重新導向URL中(NPR-33174)。
* 當Coral.Select選項設定emptyOption=true或包含值= &quot;&quot;的預設項目時，dropdownshowhide.js檔案會遇到錯誤：未捕獲的類型錯誤：component.getValue不是函式(NPR-33163)。
* 當元件包含另一個元件作為資料儲存資源時，父容器元件預留位置會以內部元件預留位置(NPR-33119)取代。
* 當內容片段以架構為基礎且包含強制文字區域或路徑欄位時，內容片段無法儲存(NPR-33007)
* 當您使用「現成可用的體驗」片段元件建立自訂元件並在AEM Sites頁面中使用時，AEM不會顯示自訂元件的參考（使用）(NPR-32852)。
* 當AEM Sites頁面是包含多個即時副本的大型內容集的一部分時，頁面版本歷史記錄預覽無法載入(NPR-32772)。
* 當您促銷啟動時，它會將&quot;cq:LiveRelations&quot;混合加入啟動中新增的每個元件。 它會影響所有啟動，而不論啟動是否已建立且未選取—  繼承來源頁面即時資料—  選項(NPR-32664)。
* 當分頁開始時，「體驗片段選擇器」不會載入所有項目(NPR-32605)。
* 無法建立AEM Sites頁面的啟動。 啟動建立會導致錯誤(NPR-32544)。
* 「管理出版物」在啟動工作流程的要求中不包含參考資產(NPR-32463)。
* Dispatcher health check在日 `Invalid cookie header` 志檔案中顯示警告消息(NPR-33630)。
* Salesforce整合易受SSRF(NPR-32671)的影響。
* PreferencesServlet中反映的XSS(NPR-33439)。

### 資產 {#assets-6481}

* 資產計數不會因清單檢視中選取項目的變更而改變(NPR-33285)。

* 在選擇父節點（其中顯示單個子資料夾），然後選擇子資料夾(NPR-33284)時，未啟用「下一個」按鈕。

* 當啟用DMS7或混合模式時，對於沒有資料庫根目錄讀取存取權的使用者，Touch UI無法轉譯（有錯誤）(NPR-33175)。

* 資料夾和資產名稱中發生的GB18030字元在下載的zip檔案中會變更為空白(NPR-33150)。

* 在智慧型裁切資產時會建立額外的資料夾，而資產位於父資料夾內，其名稱中 `.` 含點字元(NPR-32755)。

* 不會觸發延遲載入，且選取來檢閱通知收件匣中的工作時，不會顯示超過100個資產(NPR-32749)。

* 共用系列的連結頁面因coral-info的變更而中斷(NPR-32510)。

* 大量上傳時的資產處理會卡住(CQ-4293916)。

* Experience Manager中的SSRF弱點(NPR-33437)。

### 平台 {#platform-6481}

* 如果 [!DNL Sling] 在下面建立了 `sling:match` 映射條目，則不會調 `/etc/maps` 用篩選器(NPR-33308)。
* 在停用頁面時觸發所有刷新代理(NPR-32941)。
* 當您使用 `ScriptProcessor` API來精簡JavaScript程式庫時，記錄檔會顯示錯誤訊息，指出JavaScript程式碼不符合嚴格模式。 API不提供啟用或停用嚴格模式的選項。 (NPR-32746)。
* 當SQL查詢執行較長時間（例如7小時）時，AEM會停止回應(NPR-33043)。

### 使用者介面{#ui-6481}

* 當您使用選擇對話框搜索或瀏覽路徑時，選擇對話框將顯示所選JCR節點的所有內容，而不只顯示影像(NPR-32712)。

### 翻譯專案 {#tranlation-6481}

* 在運 `NullPointerException` 行翻譯作業的日誌中出現錯誤(NPR-32220)。

### 整合 {#integrations-6481}

* JSON的跨網站指令碼(NPR-32745)。

### 社群 {#communities-6481}

* 建立新群組後，作者不會重新導向至 [!DNL Internet Explorer] 11號的「社群群組」區段(NPR-33202)。
* 存取「活動串流」頁 [!UICONTROL 面時發生錯誤] (NPR-33152)。
* 編輯群 [!DNL Communities] 組並變更縮圖影像並不會更新群組縮圖影像(NPR-32603)。
* 建立使用者產生的內容(UGC)的通知和訂閱版本時，會儲存來源頁面的錯誤ID(CQ-4289703)。
* 跨網站指令碼問題(NPR-33212)。

### 工作流程 {#workflow-6481}

* 當使用者完成包含「對話參與者」步驟的工作流程時，某些元件不會顯示在彈出的 [!UICONTROL 對話方塊中] (NPR-32989)。

* 左側 [!UICONTROL 導軌中的] 「時間軸」選項的載入時間比預期要長(NPR-32850)。

### 表單 {#forms-6481}

>[!NOTE]
>
>AEM Cumulative Fix Pack不包含AEM Forms的修正。 它們是使用個別的Forms附加套件傳送。 此外，還會發行包含JEE上AEM Forms修正的累積安裝程式。 如需詳細資訊，請 [參閱「安裝AEM Forms附加元件套件](#install-aem-forms-add-on-package) 」 [和「安裝AEM Forms JEE安裝程式」](#install-aem-forms-jee-installer)。

* 通信管理：當用戶貼上來自文檔的 [!DNL Word] 內容時，文本文檔片段不保留格式(NPR-33213)。
* 最適化表單：自適應表單字典中字串的新行將字 `&#xa;` 符添加到字典(NPR-33265)。
* 最適化表單：用戶無法保存具有多個附件的自適應表單(NPR-33214)。
* 最適化表單： `AddInstance` 和 `RemoveInstance` Instance Manager類別的方法不會在上為延遲載入片段新增動態 [!DNL Internet Explorer 11] 例項數(NPR-33201)。
* 最適化表單：內嵌在頁面中的最適化表單上啟 [!DNL Sites] 用的Analytics不會記錄「提交」和「放棄」事件的資料(NPR-31359)。
* 最適化表單：當使用者將檔案的內容貼入 [!DNL Word] 最適化表單並送出時，提交的最適化表單包含Unicode字元。 此外，PDF轉換為PDF/A失敗，因為Unicode字元(NPR-33348)。
* 後端整合：表單資料模型請求會因重新整理Token因非作用中狀態不正確而失敗(NPR-33168)。
* 檔案服務：由於伺服器上的Gibsonjar遺失，PDF服務無法將PDF檔案 [!DNL WebLogic] 轉 [!DNL Linux] 換為PostScript(NPR-33515、CQ-4292239)。
* 檔案服務：當使用者將文字檔案轉換為PDF時，日文字元無法正確顯示(NPR-33239)。
* 將XSS與GuideSOMProviderServlet一起儲存(NPR-32701)。


## Install 6.4.8.1 {#install}

### 設定需求 {#setup-requirements}

<!--

>[!NOTE]
>
>For successful installation of AEM 6.4.6.0 on the instance, it is strongly recommended to upgrade the version of com.adobe.granite.oak.s3connector to 1.8.4 for the customers who are on the older version of s3 connector.
>The process of upgrading the com.adobe.granite.oak.s3connector is available at [https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html](https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html).
>Download the latest version of com.adobe.granite.oak.s3connector from: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

-->

>[!CAUTION]
>
>適用於已安裝在AEM 6.4的功能套件客戶。Adobe提供的選購功能套件與發行版本和Service Pack有相依性。 如果您已安裝任何功能套件，請聯絡AEM客戶服務團隊，以驗證這些功能套件與AEM 6.4累積修補程式套件的相容性。

* AEM 6.4.8.1需要AEM 6.4.8.0。請造訪升 [級檔案](../sites-deploying/upgrade.md) ，以取得詳細指示。
* 在使用MongoDB和多個執行個體的部署中，使用「套件管理員」將AEM 6.4.8.1安裝在其中一個「作者」執行個體上。
* 在安裝累積修補程式套件之前，請確定您有AEM例項的快照或最新備份。
* 在安裝之前重新啟動實例。 雖然只有在實例仍處於更新模式時才需要（這是剛從舊版更新實例時），但通常建議在實例運行較長時間時使用。

>[!NOTE]
>
>Adobe不建議移除或解除安裝AEM 6.4.8.1套件。

### 安裝Cumulative Fix Pack {#install-cumulative-fix-pack}

請執行下列步驟，在現有的AEM 6.4.8.0例項上安裝Cumulative Fix Pack:

1. 按一下「 [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-1.0.zip) （軟體分發）」連結以下載軟體包。

1. 開啟「 [套件管理器](http://localhost:4502/crx/packmgr/index.jsp) 」，然後按一 **[!UICONTROL 下「上傳套件]** 」以上傳套件。

1. 選擇軟體包名稱，然後按一下 **[!UICONTROL 安裝]**。

>[!NOTE]
>
>**在安裝6.4.8.1時，Package Manager UI上的對話有時會無法正常退出**
>
>因此，建議您先等待錯誤記錄穩定，再存取執行個體。 在確保安裝成功之前，用戶必須等待與卸載更新程式包相關的特定日誌。 通常在Safari上會發生，但在任何瀏覽器上都會偶爾發生。

### 自動安裝 {#auto-installation}

有兩種方式可自動將AEM 6.4.8.1安裝至執行中的例項：

答：將套件放入……*/crx-quickstart/install* folder wher the server is running. 軟體包會自動安裝。

B.使用「 [套件管理員」的HTTP API](https://docs.adobe.com/content/docs/en/crx/2-3/how_to/package_manager.html) —— 請務必使用 `cmd=install&recursive=true` -以便安裝巢狀套件。

>[!NOTE]
>
>AEM 6.4.8.1不支援Bootstrap安裝。

### 驗證安裝 {#validate-install}

1. 「產品資訊」頁面(*/system/console/productinfo*)現在應在「已安裝產品」下方顯示更新版本字串「Adobe Experience Manager, Version 6.4.8.1」。
1. 所有OSGI組合在OSGI主控台中都是ACTIVE或FRAGMENT(使用Web主控台：/system/console/bundles)。
1. OSGI套件org.apache.jackrabbit.oak-core是1.8.17版或更新版本(使用Web Console:/system/console/bundles)。

若要決定此版AEM Sites和Assets的認證執行平台，請參閱「技術 [需求」](../sites-deploying/technical-requirements.md)。

>[!NOTE]
>成功安裝套件時，會出現資訊性訊息，指出內容套件已成功安裝，例如 **「Content Package AEM-6.4-Service-Pack-7已成功安裝」。**

### 更新動態媒體檢視器(5.10.1) {#update-dynamic-media-viewers}

AEM 6.4.8.1包含新版動態媒體檢視器(5.10.1)，可讓您在「影像預設集」頁面上檢查重複名稱。 建議動態媒體客戶執行下列命令，將方塊檢視器預設集調整為最新狀態。

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

將新的檢視器預設集複製至/conf位置。

### 安裝AEM Forms附加元件套件 {#install-aem-forms-add-on-package}

>[!NOTE]
>
>如果您不使用AEM Forms，請略過。 AEM Forms中的修正是透過個別的附加套件傳送。

1. 請確定您已安裝AEM Cumulative Fix Pack。
1. 下載作業系統的 [AEM Forms版本中列出的對應表格附加元件套件](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) 。
1. 如安裝AEM Forms附加元件套件中所述，安 [裝表單附加元件套件](https://docs.adobe.com/content/help/en/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package)。

### 安裝AEM Forms JEE安裝程式 {#install-aem-forms-jee-installer}

>[!NOTE]
>
>如果您未在JEE上使用AEM Forms，請略過。 AEM Forms JEE中的修正會透過個別安裝程式提供。

如需有關安裝AEM Forms JEE累積安裝程式和部署後設定的詳細資訊，請參閱 [AEM Forms JEE修補程式安裝程式0016](https://helpx.adobe.com/aem-forms/quick-fixes/6-4/jee-patch-0016.html)。

### Uber Jar {#uber-jar}

Adobe Public Maven儲存庫中提供AEM 6.4.8.1版的Uber Jar [](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.4.8.1/)。

要在Maven項目中使用Uber Jar，請參閱文章「 [How to use Uber jar](../sites-developing/ht-projects-maven.md) and include the following dependency in your project POM:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8.1</version>
      <classifier>apis</classifier>
      <scope>provided</scope>
</dependency>
```

## 已移除／已過時的功能 {#removed-deprecated-features}

本節列出已從AEM 6.4移除或淘汰的功能和功能。

| 區域 | 功能 | 替代方案 | 版本 |
|---|---|---|---|
| 資產 | 管理子資產的標籤動作 | 無更換 | AEM 6.4.2.0 |
| 資產與Adobe Creative Cloud整合 | [AEM to Creative Cloud資料夾共用](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) ，已在AEM 6.2中推出，讓創意使用者可存取AEM的資產。 Creative Cloud應用程式中發行的新功能Adobe Asset Link提供更佳的使用者體驗，並可直接從Photoshop、InDesign和Illustrator內部，以更強大的方式存取AEM中的資產。 Adobe不會進一步增強資料夾共用功能。 雖然AEM中包含此功能，但客戶會收到（我們強烈建議您使用此取代項目）。 | Adobe Asset Link或案頭應用程式。 如需詳細資訊，請參 [閱AEM Creative Cloud整合文章](/help/assets/aem-cc-integration-best-practices.md) 。 | AEM 6.4.4.0 |

## 已知問題 {#known-issues}

* 在安裝AEM 6.4.8.1時，83版的更新 [!DNL Chrome] 會造成建立封裝時發生問題。 使用其他可用的瀏覽器(例如 [!DNL Internet Explorer] 和 [!DNL Firefox]或其他AEM標準套件安裝選項)來解決問題。 安裝AEM 6.4.8.1後，問題就解決。

* 無法使用AEM預設郵件寄件者，將電子郵件傳送至遠端SMTP伺服器，因為它僅允許使用TLS v1.2進行通訊。從中刪 `javax.mail:mail:1.5.0-b01` 除包 `system/console` 並刷新包以解決問題。

如需AEM 6.4.8.0 Service Pack已知問題的詳細資訊，請參閱 [AEM 6.4.8.0 Service Pack發行說明](sp-release-notes.md)。

## 隨附的OSGi組合和內容套件 {#osgi-bundles-and-content-packages-included}

下列文字檔案列出AEM 6.4.8.1中包含的OSGi組合和內容封裝。

AEM 6.4.8.1隨附的OSGi搭售清單

[取得檔案](assets/6.4.8.1_osgi_bundles.txt)

AEM 6.4.8.1內容套件清單

[取得檔案](assets/6.4.8.1_content_packages.txt)

## 實用資源 {#helpful-resources}

* [AEM 6.4版本注意事項](../release-notes/release-notes.md)
* [AEM產品頁面](https://www.adobe.com/solutions/web-experience-management.html)
* [AEM 6.4 檔案](https://helpx.adobe.com/tw/support/experience-manager/6-4.html)
* 訂閱 [Adobe優先產品更新](https://www.adobe.com/subscription/priority-product-update.html)

## 受限制的網站 {#restricted-sites-new}

這些網站僅提供給客戶使用。 如果您是客戶，需要存取權，請聯絡您的Adobe客戶經理。

* [產品下載，請造訪licensing.adobe.com](https://licensing.adobe.com/)
* [聯絡客戶支援](https://docs.adobe.com/content/help/en/customer-one/using/home.html)

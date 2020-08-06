---
title: AEM常見問答集
seo-title: AEM 6.4常見問題
description: 使用這些常見問答集來瞭解、設定和疑難排解AEM中的常見工作流程或問題。
seo-description: 使用這些常見問答集來瞭解、設定和疑難排解AEM中的常見工作流程或問題。
uuid: af197bcc-2c61-4c64-b781-f24d83c27c82
contentOwner: jsyal
discoiquuid: c66b65af-443f-4fc2-b775-9f4e3c60285a
translation-type: tm+mt
source-git-commit: f5b45b2c8bfcf9d82ddc08b05b5fff22937fa9fd
workflow-type: tm+mt
source-wordcount: '1545'
ht-degree: 0%

---


# AEM常見問答集{#aem-faqs}

請依照本頁取得某些AEM疑難排解和設定問題的解答。

## 網站 {#sites}

### 如何配置無二進位分發？ {#how-do-i-configure-binary-less-distribution}

通過共用資料儲存進行部署時支援無二進位分發，並且涉及使用基於Vault的分發包導出器(工廠PID: `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`)套件產生器。

在啟用無二進位模式後，分發的內容封裝會包含二進位檔的參考，而非實際二進位檔。

### 如何啟用無二進位散發？ {#how-do-i-enable-binary-less-distribution}

若要啟用無二進位散發，請使用共用的blob存放區進行部署。\
在OSGI `useBinaryReferences` 配置中檢查屬性，並查看您的代理正在使用的出廠PID( `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`*)*。

### 在AEM網站主控台中導覽頁面階層時，如何自訂錯誤訊息？ {#how-can-i-customize-the-error-messages-while-navigating-page-hierarchy-in-aem-sites-console}

檢查個人設定（JS尚未微調）的「網路」面板（Chrome瀏覽器）。

查看 `Initiator` 列以確定請求的發起者。 它提供進行AJAX調用的檔案和行號。 之後，您可以追蹤錯誤處理功能，並依需求變更錯誤訊息。

### 如何在AEM中建立內容作者的語言復本時啟用權限？ {#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

若要建立語言複製功能，內容作者需要位於位置的 `/content/projects` 權限。

如果作者也需要管理專案，因應措施是將作者新增至群 `project-administrators` 組。

### 如何在建立專案的語言副本時變更格式？ {#how-to-change-the-format-while-creating-language-copy-for-a-project}

在建立翻譯專案之前，先在根目錄中建立語言根目錄和語言副本。

例如，\
在中建立名稱為( `/content/geometrixx` 標題為法 `fr_LU` 文（盧森堡）)的語言根目錄。 隨後，從「參考」面板建立頁面的語言副本，並導航到中 `Create structure only` 的選項 `Create & Translate`。 最後，建立翻譯項目，然後將語言副本添加到翻譯作業。

如需詳細資訊，請參閱下列其他資源：

* [準備翻譯內容](/help/sites-administering/tc-prep.md)
* [管理翻譯專案](/help/sites-administering/tc-manage.md)

### 如何審核AEM功能，例如登入嘗試和ACL或權限變更？ {#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM已推出記錄管理變更的功能，以提供更佳的疑難排解和稽核。 依預設，資訊會記錄在檔案 `error.log` 中。 為了更輕鬆地進行監控，建議將監控重新導向至個別的記錄檔。\
若要將輸出重新導向至個別的記錄檔，請參 [閱「如何在AEM中稽核使用者管理作業」](/help/sites-administering/audit-user-management-operations.md)。

### 如何依預設啟用SSL? {#how-to-enable-ssl-by-default}

Adobe Experience Manager(AEM)6.4隨附於SSL精靈，並提供使用者介面來設定Jetty和Granite Jetty SSL支援。

若要依預設啟用SSL，請依預 [設參閱SSL](/help/sites-administering/ssl-by-default.md)。

### 從行動應用程式使用AEM的Content Services時，建議使用什麼架構，最好是React Native? {#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

Content Services是以Sling Models為基礎，而AEM開發人員必須為匯出的每個元件提供Sling Model pojo。

若要瞭解如何從React應用程式使用AEM內容服務，請參閱「 [AEM Content Services快速入門」教學課程](https://helpx.adobe.com/experience-manager/kt/sites/using/content-services-tutorial-use.html) 。

此外，如果開發人員想要匯出元件樹狀結構，他們也可以實作 `ComponentExporter` 和 `ContainerExporter` 介面，並使用 `ModelFactory` 來循環子元件並傳回其模型表示。 請參閱以下資源：

[1] [Adobe-Marketing-Cloud/aem-core-wcm-components](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[2] [Apache Sling:: Sling Models](https://sling.apache.org/documentation/bundles/models.html)

### 如何停用AEM 6.4調查快顯視窗？ {#how-to-disable-aem-survey-pop-up}

您可以使用Touch UI或Web Console來選擇加入使用統計資料收集。 如需詳細指示，請參 [閱選擇匯總使用統計資料收集](/help/sites-deploying/opt-in-aggregated-usage-statistics.md)。

### 是否有好的資源來強調升級至AEM 6.4的主要功能？ {#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

請參閱 [瞭解升級AEM的理由](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html) ，該說明為考慮升級至最新版Adobe Experience Manager的客戶，對主要功能的高階細分。

### 如何設定AEM例項以使用PorterStem篩選器？ {#how-to-configure-an-aem-instance-to-use-the-porterstem-filter}

PorterStem濾鏡採用Porter Stem Algorithm for English。 結果與Snowball Porter Stemmer搭配使用 *language=&quot;English&quot;引數類似* 。 但是，此調整器直接使用Java編碼，並不基於Snowball。 它不接受受保護字詞的清單，而且僅適用於英文文字。

Oak公開一組lucene-provides分析器設定元素，以用於AEM。 若要瞭解如何使用篩選器，請參閱 **Simple搜尋實作指南中的**[Apache Oak Analyzers](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)。

### 如何執行完整的重新索引？ {#how-to-perform-a-full-re-indexing}

應始終對重新索引進行處理，並適當考慮它對AEM整體效能的影響，並在活動量較低或維護期間執行。

請參閱查詢 [和索引的最佳做法](/help/sites-deploying/best-practices-for-queries-and-indexing.md) ，瞭解重新建立索引的理由。

### 我們是否支援Design Importer中的精簡JS lib? {#do-we-support-minified-js-libs-in-design-importer}

您需要將Adobe Granite HTML Library Manager的JS處理器預設configs屬性變更為 ***min:gcc***。 若要成功匯入設計套件，建議在用戶端程式庫中加入預先微調的第三方程式庫。

## 資產 {#assets}

### 上傳MP4檔案（例如使用拖放方法）時，「資產」工作流程為何會重複執行？ {#why-the-assets-workflow-repeats-itself-while-uploading-mp-files-for-example-using-drag-and-drop-method}

如果使用者，上傳影片檔案在資產節點下沒有刪除權限，則刪除區塊節點會失敗，而上傳會重新啟動。

### 一次可使用AEM 6.4操作的數位資產數目上限為何？ {#what-is-the-maximum-number-of-digital-assets-that-can-be-operated-with-aem-at-a-time}

Adobe Experience Manager(AEM)6.4目前可讓您一次上傳最多2 GB的資產。

如需可搭配AEM 6.4運作的資產最大數量的詳細資訊，請參閱「資產 [調整指南」](/help/assets/assets-sizing-guide.md)。

### 建立語言副本時OOTB配置的預設設定是什麼？ {#what-are-the-default-settings-for-ootb-configurations-while-creating-language-copy}

透過傳統UI建立語言復本時，資產不會移至新語言階層下方，而是從語言主版使用。

但是，當您透過Touch UI(**References** -> **Update Language Copy**)建立語言副本時，會以新語言建立新的DAM資料夾，並從中參考資產。

這是OOTB配置的預設設定。 您可以在「轉 **譯」設定中設定「轉** 譯頁面資產 **=** 不轉譯」。\
對於AEM 6.4，請選 **擇「工具** > **雲端服務** > **翻譯雲端服務**」。

### 如何停用造成AEM SegmentStore(AEM 6.3.1.1)指數成長的AEM元件？ {#how-to-disable-an-aem-component-causing-exponential-growth-for-the-aem-segmentstore-aem}

您可以停用OSGi元件停用程式。 若要使用此服務，請參 [閱OSGi Component Disabler](https://adobe-consulting-services.github.io/acs-aem-commons/features/osgi-disablers/component-disabler/index.html)。

因應措施是，您也可以透過UI或在每次AEM重新啟動後，透過命令( `curl` 範例)手動停用元件。

`curl -u admin:$(pass CQ_Admin) 'http://localhost:4502/system/console/components/com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporter' --data 'action=disable'`

### 如何使用AEM 6.4例項設定資產分析？ {#how-to-configure-asset-insights-with-aem-instance}

若要設定並設定透過Adobe Activation(DTM)部署的Experience Manager資產前瞻分析，請參閱「使用AEM [資產設定資產前瞻分析」](https://helpx.adobe.com/experience-manager/kt/assets/using/asset-insights-tutorial-setup.html)。

### 如何自訂管理控制台？ {#how-to-customize-admin-consoles}

AEM提供多種機制，讓您自訂製作執行個體的控制台和頁面製作功能。
要瞭解如何建立自定義控制台和自定義控制台的預設視圖，請參閱自 [定義控制台](/help/sites-developing/customizing-consoles-touch.md)。

### CoralUI 2和CoralUI 3元件之間有何差異？ {#what-is-the-difference-between-coralui-and-coralui-based-components}

Granite UI Foundation的全新Sling元件集是為Coral3建立，位於 [/libs/granite/ui/components/coral/foundation下。](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html) 其中一組是以CoralUI 2為基礎的元件，另一組是以CoralUI 3為基礎的元件。 新集將不只是舊集的複製貼上，而是會加以清理（例如，簡化、移除已過時的功能）。 因此，建議頁面僅使用以CoralUI 3為基礎或以CoralUI 2為基礎的集合。

如需詳細資訊，請參閱 [CoralUI 3架構的移轉指南](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html)。

### 如何自訂AEM Assets中的搜尋元件？ {#how-to-customize-the-search-component-in-aem-assets}

如需搜尋大幅提升／排名和進一步實作資訊的詳細資訊，請參 [閱簡易搜尋實作指南。](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)

「簡單搜尋」實作是2017年峰會實驗室AEM Search Demystified的教材。

### 如果客戶只購買AEM中的「網站」授權，他們是否仍可存取「資產」? {#if-a-customer-buys-only-sites-license-in-aem-do-they-still-have-access-to-assets}

否，客戶無法存取「資產」（或「網站」以外的任何項目）。 即使所有Adobe Experience Manager(AEM)內部部署都包含在JAR中，客戶仍只能取得授權存取其合約中授權之JAR中的元件。 如果他們想要探索其他元件，可以使用AEM試用程式長達45天，或簽署$0的銷售訂單，以授權他們評估（無生產用途）命名的元件，例如「資產」。

請參閱下列資源，以進一步瞭解AEM內部部署軟體和Adobe Managed Services:

* [Adobe Experience Manager內部部署軟體](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html)

* [Adobe Experience Manager Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html)

### 客戶如何延伸頁面或資產的預設屬性？ {#how-to-extend-default-properties-page-or-asset}

若要瞭解如何擴充頁面或資產的預設屬性，請參閱下列資源：

* [資產中的中繼資料結構](/help/assets/metadata-schemas.md)
* [自訂頁面屬性的檢視](/help/sites-developing/page-properties-views.md)

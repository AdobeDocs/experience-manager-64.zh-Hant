---
title: 常見AEM問答
seo-title: AEM 6.4常見問題
description: 使用這些常見問答集來瞭解、設定和疑難排解中的常見工作流程或AEM問題。
seo-description: 使用這些常見問答集來瞭解、設定和疑難排解中的常見工作流程或AEM問題。
uuid: af197bcc-2c61-4c64-b781-f24d83c27c82
contentOwner: jsyal
discoiquuid: c66b65af-443f-4fc2-b775-9f4e3c60285a
exl-id: 76110cf4-0fd8-4203-b256-c0818a1b64d2
source-git-commit: edba9586711ee5c0e5549dbe374226e878803178
workflow-type: tm+mt
source-wordcount: '1545'
ht-degree: 0%

---

# AEM常見問答{#aem-faqs}

請依照本頁取得疑難排解和設AEM定問題的解答。

## 網站 {#sites}

### 如何配置無二進位分發？{#how-do-i-configure-binary-less-distribution}

通過共用資料儲存進行部署時支援無二進位分發，並且涉及使用基於Vault的分發包導出器(工廠PID:`org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`)套件產生器。

在啟用無二進位模式後，分發的內容封裝會包含二進位檔的參考，而非實際二進位檔。

### 如何啟用無二進位散發？{#how-do-i-enable-binary-less-distribution}

若要啟用無二進位散發，請使用共用的blob存放區進行部署。\
在OSGI配置中檢查`useBinaryReferences`屬性，並檢查您的代理使用的工廠PID(`org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`*)*。

### 如何在網站主控台中導覽頁面階層時自訂錯AEM誤訊息？{#how-can-i-customize-the-error-messages-while-navigating-page-hierarchy-in-aem-sites-console}

檢查個人設定（JS尚未微調）的「網路」面板（Chrome瀏覽器）。

檢視`Initiator`欄，以判斷請求的啟動者。 它提供進行呼叫的檔案AJAX和行號。 之後，您可以追蹤錯誤處理功能，並依需求變更錯誤訊息。

### 如何在中建立內容作者語言副本時啟用權AEM限？{#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

若要建立語言複製功能，內容作者需要`/content/projects`位置的權限。

如果作者也需要管理專案，因應措施是將作者新增至`project-administrators`群組。

### 如何在建立專案的語言副本時變更格式？{#how-to-change-the-format-while-creating-language-copy-for-a-project}

在建立翻譯專案之前，先在根目錄中建立語言根目錄和語言副本。

例如，\
在`/content/geometrixx`建立名稱為`fr_LU`的語言根目錄(標題為法文（盧森堡）)。 隨後，從參考面板建立頁面的語言副本，並導航至`Create & Translate`中的`Create structure only`選項。 最後，建立翻譯項目，然後將語言副本添加到翻譯作業。

如需詳細資訊，請參閱下列其他資源：

* [準備翻譯內容](/help/sites-administering/tc-prep.md)
* [管理翻譯專案](/help/sites-administering/tc-manage.md)

### 如何審AEM核登錄嘗試和ACL或權限更改等功能？{#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM引入了記錄管理更改的功能，以便更好地進行故障排除和審計。 預設情況下，資訊記錄在`error.log`檔案中。 為了更輕鬆地進行監控，建議將監控重新導向至個別的記錄檔。\
要將輸出重定向到單獨的日誌檔案，請參閱[](/help/sites-administering/audit-user-management-operations.md)中的「如何審計用戶管AEM理操作」。

### 如何依預設啟用SSL?{#how-to-enable-ssl-by-default}

Adobe Experience Manager(AEM)6.4隨SSL精靈提供，並提供使用者介面來設定Jetty和Granite Jetty SSL支援。

若要依預設啟用SSL，請參閱[SSL依預設](/help/sites-administering/ssl-by-default.md)。

### 從行動應用程式使用內容服務(AEM最好是React Native)時，建議使用什麼架構？{#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

Content Services是以Sling Models為基礎，而開發人AEM員必須為匯出的每個元件提供Sling Model pojo。

要瞭解如何從React應AEM用程式使用內容服務，請參閱[開始使用AEMContent Services](https://helpx.adobe.com/experience-manager/kt/sites/using/content-services-tutorial-use.html)教學課程。

此外，如果開發人員想要匯出元件樹狀結構，他們也可以實作`ComponentExporter`和`ContainerExporter`介面，並使用`ModelFactory`來重複子元件並傳回其模型表示法。 請參閱以下資源：

[1] [Adobe-Marketing-Cloud/aem-core-wcm-components](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[2] [Apache Sling::Sling Models](https://sling.apache.org/documentation/bundles/models.html)

### 如何停用AEM6.4調查快顯視窗？{#how-to-disable-aem-survey-pop-up}

您可以使用Touch UI或Web Console來選擇加入使用統計資料收集。 如需詳細指示，請參閱[選擇匯總使用統計資料收集](/help/sites-deploying/opt-in-aggregated-usage-statistics.md)。

### 是否有好的資源可強調升級至AEM6.4的主要功能？{#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

請參閱[瞭解升級理由AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html)，說明考慮升級至最新版Adobe Experience Manager的客戶的主要功能高階劃分。

### 如何設定例AEM項以使用PorterStem篩選器？{#how-to-configure-an-aem-instance-to-use-the-porterstem-filter}

PorterStem濾鏡採用Porter Stem Algorithm for English。 結果與使用Snowball Porter Stemmer和&#x200B;*language=&quot;English&quot;*&#x200B;引數類似。 但是，此調整器直接使用Java編碼，並不基於Snowball。 它不接受受保護字詞的清單，而且僅適用於英文文字。

Oak公開一組lucene-provides分析器配置元素，用於AEM。 要瞭解如何使用篩選器，請參閱[Simple search implementation guide](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)中的&#x200B;**Apache Oak Analyzers**。

### 如何執行完整的重新索引？{#how-to-perform-a-full-re-indexing}

應始終對重新編製索引進行處理，並適當考慮其對整AEM體效能的影響，並在活動量較低或維護時間較長的期間執行。

請參閱[查詢和索引的最佳做法](/help/sites-deploying/best-practices-for-queries-and-indexing.md)以瞭解重新索引的原因。

### 我們是否支援Design Importer中的精簡JS lib?{#do-we-support-minified-js-libs-in-design-importer}

您需要將AdobeGranite HTML Library Manager的JS處理器預設configs屬性變更為&#x200B;***min:gcc***。 若要成功匯入設計套件，建議在用戶端程式庫中加入預先微調的第三方程式庫。

## 資產 {#assets}

### 上傳MP4檔案（例如使用拖放方法）時，「資產」工作流程為何會重複執行？{#why-the-assets-workflow-repeats-itself-while-uploading-mp-files-for-example-using-drag-and-drop-method}

如果使用者，上傳影片檔案在資產節點下沒有刪除權限，則刪除區塊節點會失敗，而上傳會重新啟動。

### 一次可以使用6.4操作的數AEM位資產的最大數量是多少？{#what-is-the-maximum-number-of-digital-assets-that-can-be-operated-with-aem-at-a-time}

Adobe Experience ManagerAEM()6.4目前可讓您一次上傳最多2 GB的資產。

有關可以使用6.4操作的資產數量上限的AEM其他資訊，請參閱[資產調整指南](/help/assets/assets-sizing-guide.md)。

### 建立語言副本時OOTB配置的預設設定是什麼？{#what-are-the-default-settings-for-ootb-configurations-while-creating-language-copy}

透過傳統UI建立語言復本時，資產不會移至新語言階層下方，而是從語言主版使用。

但是，當您透過Touch UI（**References** -> **更新語言副本**）建立語言副本時，會以新語言建立新的DAM資料夾，並從中參考資產。

這是OOTB配置的預設設定。 您可以在翻譯配置中設定&#x200B;**翻譯頁面資產** = **不翻譯**。\
對於AEM6.4,**工具** > **Cloud Services** > **翻譯雲服務**。

### 如何停用AEMSegmentStore(AEM 6.3.1.1)AEM造成指數式增長的元件？{#how-to-disable-an-aem-component-causing-exponential-growth-for-the-aem-segmentstore-aem}

您可以停用OSGi元件停用程式。 要使用此服務，請參見[OSGi Component Disabler](https://adobe-consulting-services.github.io/acs-aem-commons/features/osgi-disablers/component-disabler/index.html)。

因應措施是，您也可以透過UI或`curl`命令（範例如下），在每次重新啟動後手動停用元AEM件。

`curl -u admin:$(pass CQ_Admin) 'http://localhost:4502/system/console/components/com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporter' --data 'action=disable'`

### 如何設定具有AEM6.4例項的資產分析？{#how-to-configure-asset-insights-with-aem-instance}

若要設定並設定透過Adobe啟動(DTM)部署的Experience Manager資產前瞻分析，請參閱[使用AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/asset-insights-tutorial-setup.html)設定資產前瞻分析。

### 如何自訂管理控制台？{#how-to-customize-admin-consoles}

提AEM供各種機制，讓您自訂製作執行個體的控制台和頁面製作功能。
要瞭解如何建立自定義控制台並自定義控制台的預設視圖，請參閱[自定義控制台](/help/sites-developing/customizing-consoles-touch.md)。

### CoralUI 2和CoralUI 3元件之間有何差異？{#what-is-the-difference-between-coralui-and-coralui-based-components}

Granite UI Foundation的一組新Sling元件是為Coral3建立，位於[/libs/granite/ui/components/coral/foundation下方。](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html) 其中一組是以CoralUI 2為基礎的元件，另一組是以CoralUI 3為基礎的元件。新集將不只是舊集的複製貼上，而是會加以清理（例如，簡化、移除已過時的功能）。 因此，建議頁面僅使用以CoralUI 3為基礎或以CoralUI 2為基礎的集合。

如需詳細資訊，請參閱[Migration Guide to CoralUI 3-based](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html)。

### 如何自訂AEM Assets的搜尋元件？{#how-to-customize-the-search-component-in-aem-assets}

若要瞭解搜尋大幅提升／排名和進一步實作資訊，請參閱[簡易搜尋實作指南。](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html)

「簡單」搜尋實作是2017年峰會實驗室搜尋解說AEM明檔案。

### 如果客戶只購買Sites授權，AEM他們是否仍可存取Assets?{#if-a-customer-buys-only-sites-license-in-aem-do-they-still-have-access-to-assets}

否，客戶無法存取「資產」（或「網站」以外的任何項目）。 即使所有Adobe Experience Manager(AEM)內部部署都包含在JAR中，客戶也僅有權訪問其合同中授予其許可的JAR中的元件。 如果他們想要探索其他元件，可以使用試用AEM程式長達45天，或簽署$0的銷售訂單，授權他們評估（無生產用途）命名的元件，例如「資產」。

請參閱下列資源，以進一步了AEM解內部部署軟體和Adobe Managed Services:

* [Adobe Experience Manager內部部署軟體](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html)

* [Adobe Experience ManagerManaged Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html)

### 客戶如何延伸頁面或資產的預設屬性？{#how-to-extend-default-properties-page-or-asset}

若要瞭解如何擴充頁面或資產的預設屬性，請參閱下列資源：

* [資產中的中繼資料結構](/help/assets/metadata-schemas.md)
* [自訂頁面屬性的檢視](/help/sites-developing/page-properties-views.md)

---
cloud: Experience Cloud
product: adobe experience manager
solution: Experience Manager, Experience Manager Sites, Experience Manager 6.4
audience: end-user
user-guide-title: AEM 6.4 Deploying 指南
breadcrumb-title: Deploying 指南
user-guide-description: 進一步了解 Adobe Experience Manager 6.4 的安裝、部署和架構，包括我們的 Adobe Managed Services 雲端部署。
feature: Deploying
role: Architect
source-git-commit: cda63b9ece88d8172fa4d9817e315c9cff88c224
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 9%

---


# AEM 6.4 Deploying使用手冊 {#deploying}

+ [Deploying使用手冊](home.md)
+ AEM Platform {#introduction}簡介
   + [AEM Platform簡介](platform.md)
   + [技術需求](technical-requirements.md)
   + [AEM 6.4中的儲存元素](storage-elements-in-aem-6.md)
   + [AEM與MongoDB](aem-with-mongodb.md)
+ 部署AEM {#deploying}
   + [部署和維護](deploy.md)
   + [建議的部署](recommended-deploys.md)
   + [應用程式伺服器安裝](application-server-install.md)
   + [自定義獨立安裝](custom-standalone-install.md)
   + [命令行開始和停止](command-line-start-and-stop.md)
   + [在AEM 6中配置節點儲存區和資料儲存區](data-store-config.md)
   + [修訂清除](revision-cleanup.md)
   + [如何使用TarMK冷待機執行AEM](tarmk-cold-standby.md)
   + [AEM 6.4中的RDBMS支援](rdbms-support-in-aem.md)
   + [Oak查詢和索引](queries-and-indexing.md)
   + [透過Oak-run Jar建立索引](indexing-via-the-oak-run-jar.md)
   + [Oak-run.jar索引使用案例](oak-run-indexing-usecases.md)
   + [疑難排解Oak索引](troubleshooting-oak-indexes.md)
   + [選擇匯總的使用情況統計資訊收集](opt-in-aggregated-usage-statistics.md)
   + [疑難排解](troubleshooting.md)
+ 配置AEM {#configuring}
   + [基本配置概念](configuring.md)
   + [記錄](configure-logging.md)
   + [配置OSGi](configuring-osgi.md)
   + [OSGi組態設定](osgi-configuration-settings.md)
   + [執行模式](configure-runmodes.md)
   + [Web 主控台](web-console.md)
   + [複寫](replication.md)
   + [使用Mutual SSL進行複製](mssl-replication.md)
   + [疑難排解復寫](troubleshoot-rep.md)
   + [靜態對象的過期](expiration-static-objects.md)
   + [版本清除](version-purging.md)
   + [監視和維護您的AEM例項](monitoring-and-maintaining.md)
   + [卸載作業](offloading.md)
   + [單一登入](single-sign-on.md)
   + [資源映射](resource-mapping.md)
   + [透過SSL啟用HTTP](https://experienceleague.adobe.com/docs/experience-manager-64/administering/security/ssl-by-default.html)
   + [一致性和遍歷檢查](consistency-check.md)
   + [效能准則](performance-guidelines.md)
   + [效能最佳化](configuring-performance.md)
   + [資產效能指南](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/performance-tuning-guidelines.html)
   + [設定作法文章](ht-deploy.md)
   + [移除Geometrixx網站](removing-the-geometrixx-sites.md)
   + [配置Web控制台](configuring-web-console.md)
+ 升級至AEM 6.4 {#upgrading}
   + [升級至AEM 6.4](upgrade.md)
   + [規劃升級](upgrade-planning.md)
   + [使用模式檢測器評估升級複雜性](pattern-detector.md)
   + [AEM 6.4的向後相容性](backward-compatibility.md)
   + [升級程式](upgrade-procedure.md)
   + [使用離線重新索引以減少升級期間的停機時間](upgrade-offline-reindexing.md)
   + [執行就地升級](in-place-upgrade.md)
   + [延遲內容移轉](lazy-content-migration.md)
   + [使用CRX2Oak移轉工具](using-crx2oak.md)
   + [升級前維護任務](pre-upgrade-maintenance-tasks.md)
   + [升級後檢查和疑難排解](post-upgrade-checks-and-troubleshooting.md)
   + [升級自訂搜尋Forms](upgrading-custom-search-forms.md)
   + [可持續升級](sustainable-upgrades.md)
   + [升級程式碼和自訂](upgrading-code-and-customizations.md)
   + [應用程式伺服器安裝的升級步驟](app-server-upgrade.md)
   + [升級後卸載的過時套件組合清單](obsolete-bundles.md)
+ 資料庫重組{#restructuring}
   + [AEM 6.4中的存放庫重新調整架構](repository-restructuring.md)
   + [AEM 6.4中的常見存放庫重新調整架構](all-repository-restructuring-in-aem-6-4.md)
   + [AEM 6.4中的Sites存放庫重新調整](sites-repository-restructuring-in-aem-6-4.md)
   + [AEM 6.4中的資產存放庫重新調整架構](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/repository-restructuring.html)
   + [Dynamic Media 6.4中的存放庫重新調整架構](dynamicmedia-repository-restructuring-in-aem-6-4.md)
   + [Forms 6.4中的存放庫重新調整架構](forms-repository-restructuring-in-aem-6-4.md)
   + [AEM 6.4中的電子商務存放庫重新調整](ecommerce-repository-restructuring-in-aem-6-4.md)
   + [6.4中的AEM Communities存放庫重新調整](communities-repository-restructuring-in-aem-6-4.md)
+ 電子商務 {#ecommerce}
   + [電子商務概述](ecommerce.md)
   + [SAPCommerce Cloud](sap-commerce-cloud.md)
   + [SalesforceCommerce Cloud](https://github.com/adobe/commerce-salesforce)
   + [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)
+ 最佳作法 {#practices}
   + [部署最佳實務](best-practices.md)
   + [效能樹](performance-tree.md)
   + [效能測試最佳實務](best-practices-for-performance-testing.md)
   + [查詢和建立索引的最佳實務](best-practices-for-queries-and-indexing.md)
   + [適用於客戶的使用者介面Recommendations](ui-recommendations.md)
   + [效能和可擴充性](performance.md)


<!--

To be removed:
[Quickstart for AEM Screens](setting-up-a-basic-project-screens.md)
[Device Control Center](device-control-center.md)
[repository-restructuring-in-aem64](repository-restructuring-in-aem64.md)
[Web Console] (configuring-web-console.md)
[Configuring and Deploying AEM Screens](configuring-screens-introduction.md)
[Kickstart Guide](kickstart-for-aem-screens.md)
/help/sites/deploying/using/performance-lp.md
/help/sites-deploying/do-not-delete-performance-guidelines-pdf.md
/help/sites-deploying/removing-the-geometrixx-sites.md
/help/sites-deploying/consistency-check.md

Redirects:
[(Enabling HTTP Over SSL)](config-ssl.md) redirect to /content/help/en/experience-manager/6-4/sites-administering/ssl-by-default
-->

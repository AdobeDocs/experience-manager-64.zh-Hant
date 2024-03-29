---
cloud: Experience Cloud
product: adobe experience manager
solution: Experience Manager, Experience Manager Sites
audience: end-user
user-guide-title: AEM 6.4 Developing 使用指南
breadcrumb-title: Developing 指南
user-guide-description: 本指南說明如何建立 AEM 執行個體。
feature: Developing
role: Developer
hide: true
source-git-commit: b61797a9096c0473658d6aabfb584a53e42095b7
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 25%

---


# AEM 6.4 Developing 使用指南 {#developing}

+ [開發使用手冊概述](home.md)
+ 開發人員簡介{#introduction}
   + [開發 AEM Sites 快速入門 - WKND 教學課程](getting-started.md)
   + [AEM核心概念](the-basics.md)
   + [AEM觸控式UI的結構](touch-ui-structure.md)
   + [AEM觸控式UI的概念](touch-ui-concepts.md)
   + [AEM開發 — 准則和最佳實務](dev-guidelines-bestpractices.md)
   + [使用用戶端程式庫](clientlibs.md)
   + [開發與頁面差異](pagediff.md)
   + [編輯器限制](editor-limitations.md)
   + [CSRF保護框架](csrf-protection.md)
   + [資料模型 — 大衛·紐謝勒的模型](model-data.md)
   + [貢獻AEM](contributing-to-cq.md)
   + [安全性](security.md)
   + [參考資料](reference-materials.md)
   + [建立功能齊全的網站（傳統UI）](website.md)
   + [設計與設計工具（傳統UI）](designer.md)
+ 平台{#platform}
   + [Sling 速查表](sling-cheatsheet.md)
   + [使用 Sling 介面卡](sling-adapters.md)
   + [標籤程式庫](taglib.md)
   + 範本{#templates}
      + [範本](templates.md)
      + [頁面範本 — 可編輯 ](page-templates-editable.md)
      + [頁面範本 — 靜態](page-templates-static.md)
      + [內容片段範本](content-fragment-templates.md)
      + [最適化範本轉譯](templates-adaptive-rendering.md)
   + [在AEM中使用Sling Resource Merger](sling-resource-merger.md)
   + [覆蓋](overlays.md)
   + [命名慣例](naming-conventions.md)
   + [建立新的Granite UI欄位元件](granite-ui-component.md)
   + 查詢產生器{#query-builder}
      + [為查詢產生器實作自訂述詞求值器](implementing-custom-predicate-evaluator.md)
      + [查詢產生器述詞參考](querybuilder-predicate-reference.md)
      + [查詢產生器 API](querybuilder-api.md)
   + 標記{#tagging}
      + [標記](tags.md)
      + [AEM 標記框架](framework.md)
      + [在AEM應用程式中建立標籤](building.md)
   + [自訂由錯誤處理常式顯示的頁面](customizing-errorhandler-pages.md)
   + [自訂節點類型](custom-nodetypes.md)
   + [為圖形渲染添加字型](adding-fonts.md)
   + [連接到SQL資料庫](jdbc.md)
   + [將URL外部化](externalizer.md)
   + [為卸載建立並佔用作業](dev-offloading.md)
   + [設定Cookie使用情形](cookie-optout.md)
   + [如何以程式設計方式存取AEM JCR](access-jcr.md)
   + [將服務與JMX控制台整合](jmx-integration.md)
   + [開發大量編輯器](dev-bulk-editor.md)
   + [開發報表](dev-reports.md)
   + 電子商務{#ecommerce}
      + [電子商務](ecommerce.md)
      + [開發（一般）](generic.md)
      + [使用SAP開發Commerce Cloud](sap-commerce-cloud.md)
+ 元件{#components}
   + [核心元件](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)
   + [樣式系統](https://experienceleague.adobe.com/docs/experience-manager-64/authoring/siteandpage/style-system.html)
   + [元件概觀](components.md)
   + [AEM元件 — 基本概念](components-basics.md)
   + [開發AEM元件](developing-components.md)
   + [開發AEM元件 — 程式碼範例](developing-components-samples.md)
   + [內容服務的 JSON 匯出工具](json-exporter.md)
   + [為元件啟用 JSON 匯出](json-exporter-components.md)
   + [影像編輯器](image-editor.md)
   + [裝飾標記](decoration-tag.md)
   + [使用隱藏條件](hide-conditions.md)
   + [配置多個就地編輯器](multiple-inplace-editors.md)
   + [開發人員模式](developer-mode.md)
   + [測試您的UI](hobbes.md)
   + [內容片段的元件](components-content-fragments.md)
   + [取得JSON格式的頁面資訊](pageinfo.md)
   + 國際化{#internationalization}
      + [國際化元件](i18n.md)
      + [國際化UI字串](i18n-dev.md)
      + [使用翻譯工具管理字典](i18n-translator.md)
      + [擷取字串以進行轉譯](i18n-extract.md)
   + 傳統UI元件{#classic-ui-components}
      + [開發AEM元件（傳統UI）](developing-components-classic.md)
      + [使用和擴充Widget（傳統UI）](widgets.md)
      + [使用xtype（傳統UI）](xtypes.md)
      + [開發Forms（傳統UI）](developing-forms.md)
+ Headless 體驗管理{#headless}
   + [無頭與混合搭配AEM](https://business.adobe.com/content/dam/dx/us/en/products/experience-manager/sites/headless-content-management-system/pdfs/aem-hybrid-architecture-wp-1-18-19.pdf)
   + [為元件啟用 JSON 匯出](https://experienceleague.adobe.com/docs/experience-manager-64/developing/components/json-exporter-components.html)
   + 單頁應用程式{#spas}
      + [SPA 簡介和逐步解說](spa-walkthrough.md)
      + [SPA WKND 教學課程](spa-wknd.md)
      + [AEM中的SPA快速入門 — React](spa-getting-started-react.md)
      + [AEM中SPA快速入門 — Angular](spa-getting-started-angular.md)
      + [針對 SPA 實作 React元件](spa-implementing-react-component.md)
      + [SPA 深入探討](spa-deep-dives.md)
      + [SPA 編輯器概觀](spa-overview.md)
      + [針對 AEM 開發 SPA](spa-architecture.md)
      + [SPA 藍圖](spa-blueprint.md)
      + [SPA 頁面元件](spa-page-component.md)
      + [動態模型到元件對應 適用於SPA](spa-dynamic-model-to-component-mapping.md)
      + [SPA模型路由](spa-routing.md)
      + [SPA與Adobe Experience Platform Launch整合](spa-launch.md)
      + [SPA和伺服器端轉譯](spa-ssr.md)
      + [SPA參考資料](spa-reference-materials.md)
   + [HTTP API](https://experienceleague.adobe.com/docs/experience-manager-64/assets/extending/mac-api-assets.html)
   + [內容片段](https://experienceleague.adobe.com/docs/experience-manager-64/assets/fragments/content-fragments.html)
   + [體驗片段](https://experienceleague.adobe.com/docs/experience-manager-64/authoring/authoring/experience-fragments.html)
+ 開發工具{#devtools}
   + [開發工具](dev-tools.md)
   + [AEM 現代化工具](modernization-tools.md)
   + [對話方塊編輯器](dialog-editor.md)
   + [對話方塊轉換工具](dialog-conversion.md)
   + [使用CRXDE Lite開發](developing-with-crxde-lite.md)
   + [使用Maven管理套件](vlt-mavenplugin.md)
   + [如何使用Eclipse開發AEM專案](howto-projects-eclipse.md)
   + [如何使用Apache Maven建立AEM專案](ht-projects-maven.md)
   + [如何使用IntelliJ IDEA開發AEM專案](ht-intellij.md)
   + [如何使用VLT工具](ht-vlttool.md)
   + [如何使用代理伺服器工具](ht-proxy-server.md)
   + [AEM Brackets擴充功能](aem-brackets.md)
   + [Eclipse 適用的 AEM 開發人員工具](aem-eclipse.md)
   + [AEM Repo Tool](aem-repo-tool.md)
+ 個人化{#personlization}
   + [ContextHub](contexthub.md)
   + [ContextHub Javascript API參考資料](contexthub-api.md)
   + [延伸 ContextHub](ch-extend.md)
   + [新增ContextHub至頁面及存取商店](ch-adding.md)
   + [範例ContextHub存放區候選項](ch-samplestores.md)
   + [範例ContextHub UI模組類型](ch-samplemodules.md)
   + [ContextHub 診斷](ch-diagnostics.md)
   + [針對目標內容開發](target.md)
   + ClientContext{#client-context}
      + [詳細的客戶端上下文](client-context.md)
      + [用戶端內容Javascript API](ccjsapi.md)
+ 擴充AEM{#extending-aem}
   + [自訂頁面編寫](customizing-page-authoring-touch.md)
   + [自訂主控台](customizing-consoles-touch.md)
   + [自訂頁面屬性的檢視](page-properties-views.md)
   + [設定頁面以大量編輯頁面屬性](bulk-editing.md)
   + [自訂和擴充內容片段](customizing-content-fragments.md)
   + 延伸工作流程{#extending-workflows}
      + [開發和延伸工作流程](workflows.md)
      + [建立工作流模型](workflows-models.md)
      + [延伸工作流程功能](workflows-customizing-extending.md)
      + [以程式設計方式與工作流程互動](workflows-program-interaction.md)
      + [工作流程步驟參考](workflows-step-ref.md)
      + [工作流程最佳實務](workflows-best-practices.md)
      + [工作流程處理序參考](workflows-process-ref.md)
   + [擴展多站點管理器](extending-msm.md)
   + 追蹤與分析{#extending-analytics}
      + [擴充事件追蹤](extending-analytics.md)
      + [將Adobe Analytics追蹤新增至元件](extending-analytics-components.md)
      + [自訂Adobe Analytics架構](extending-analytics-framework.md)
      + [為Analytics實作伺服器端頁面命名](extending-analytics-pa-naming.md)
   + 雲端服務{#extending-cloud-services}
      + [雲端服務設定](extending-cloud-config.md)
      + [建立自訂Cloud Service](extending-cloud-config-custom-cloud.md)
   + [建立自訂擴充功能](extending-campaign-extensions.md)
   + Forms{#extending-forms}
      + [建立自訂表單對應](extending-campaign-form-mapping.md)
      + [使用Adobe Campaign表單元件建立自訂AEM頁面範本](extending-campaign-custom-template.md)
      + [Request Analysis Script](analyze-request.md)
   + [將服務與JMX控制台整合](https://experienceleague.adobe.com/docs/experience-manager-64/developing/platform/jmx-integration.html)
   + [開發大量編輯器](https://experienceleague.adobe.com/docs/experience-manager-64/developing/platform/dev-bulk-editor.html)
   + 擴充傳統UI{#extending-classic-ui}
      + [自訂網站主控台（傳統UI）](customizing-siteadmin.md)
      + [自訂歡迎控制台（傳統UI）](customizing-the-welcome-console.md)
      + [開發報表](https://experienceleague.adobe.com/docs/experience-manager-64/developing/platform/dev-reports.html)
+ 測試{#testing}
   + [規劃](planning.md)
   + [需要哪些測試環境？](test-environments.md)
   + [定義測試案例](test-cases.md)
   + [測試 — 何時與誰？](when-who.md)
   + [編譯測試計畫](test-plan.md)
   + [追蹤結果並提供意見](results-and-feedback.md)
   + [測試和追蹤工具](tools.md)
   + [接受與簽核](acceptance-signoff.md)
   + [下一個版本……](the-next-release.md)
   + [核取清單](checklists.md)
   + [艱難的一天](tough-day.md)
   + [測試您的UI](https://experienceleague.adobe.com/docs/experience-manager-64/developing/components/hobbes.html)
+ 最佳作法{#bestpractices}
   + [最佳實務概述](best-practices.md)
   + [AEM開發准則和最佳實務](https://experienceleague.adobe.com/docs/experience-manager-64/developing/introduction/dev-guidelines-bestpractices.html)
   + [開發最佳實務](development-practices.md)
   + [內容架構](content-architecture.md)
   + [軟體體系結構](software-architecture.md)
   + We.Retail參考實作{#we-retail}
      + [We.Retail參考實作](we-retail.md)
      + [在We.Retail中嘗試內容片段](we-retail-content-fragments.md)
      + [在We.Retail中試用核心元件](we-retail-core-components.md)
      + [在We.Retail中試用可編輯的範本](we-retail-editable-templates.md)
      + [在We.Retail中嘗試回應式版面](we-retail-responsive-layout.md)
      + [在We.Retail中嘗試全球化網站結構](we-retail-globalized-site-structure.md)
      + [在We.Retail中嘗試體驗片段](we-retail-experience-fragments.md)
   + [編碼提示](coding-tips.md)
   + [程式碼陷阱](code-pitfalls.md)
   + [OSGI套件組合](osgi-bundles.md)
   + [JCR整合](jcr-integration.md)
   + [程式碼範例](code-samples.md)
   + [疑難排解慢速查詢](troubleshooting-slow-queries.md)
+ 行動網站{#mobileweb}
   + [行動網站](mobile-web.md)
   + [建立裝置群組篩選器](groupfilters.md)
   + [網頁的回應式設計](responsive.md)
   + [為行動裝置建立網站](mobile.md)
   + [模擬器](emulators.md)

<!--
Deleted link to broken helpx video:
    + [Understanding Content Fragments and Content Services in AEM](https://helpx.adobe.com/experience-manager/kt/sites/using/content-fragments-content-services-feature-video-understand.html)
-->

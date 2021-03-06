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
source-git-commit: 35aea0e087334a1c1e6a708f2182bd9dee799dc0
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 15%

---


# AEM 6.4 Developing 使用指南 {#developing}

+ [開發使用手冊概述](home.md)
+ 開發人員簡介{#introduction}
   + [開始開發 AEM Sites - WKND 教學課程](getting-started.md)
   + [核AEM心概念](the-basics.md)
   + [啟用觸摸AEM的UI的結構](touch-ui-structure.md)
   + [啟用觸摸AEM的UI的概念](touch-ui-concepts.md)
   + [開AEM發 — 指南和最佳做法](dev-guidelines-bestpractices.md)
   + [使用用戶端端程式庫](clientlibs.md)
   + [開發和頁面差異](pagediff.md)
   + [編輯器限制](editor-limitations.md)
   + [CSRF保護框架](csrf-protection.md)
   + [資料建模 — 大衛·紐謝勒模型](model-data.md)
   + [貢獻AEM](contributing-to-cq.md)
   + [安全性](security.md)
   + [參考材料](reference-materials.md)
   + [建立功能齊全的網站（經典UI）](website.md)
   + [設計和設計器（經典UI）](designer.md)
+ 平台{#platform}
   + [Sling 速查表](sling-cheatsheet.md)
   + [使用 Sling 介面卡](sling-adapters.md)
   + [標籤庫](taglib.md)
   + 範本{#templates}
      + [範本](templates.md)
      + [頁面模板 — 可編輯 ](page-templates-editable.md)
      + [頁面模板 — 靜態](page-templates-static.md)
      + [內容片段模板](content-fragment-templates.md)
      + [自適應模板渲染](templates-adaptive-rendering.md)
   + [Sling資源合併的應用研AEM究](sling-resource-merger.md)
   + [覆蓋](overlays.md)
   + [命名約定](naming-conventions.md)
   + [建立新花崗岩UI欄位元件](granite-ui-component.md)
   + 查詢產生器{#query-builder}
      + [為查詢生成器實現自定義謂詞計算器](implementing-custom-predicate-evaluator.md)
      + [查詢生成器謂詞引用](querybuilder-predicate-reference.md)
      + [查詢產生器 API](querybuilder-api.md)
   + 標記{#tagging}
      + [標記](tags.md)
      + [標AEM記框架](framework.md)
      + [將標籤構建到應AEM用程式](building.md)
   + [自定義錯誤處理程式顯示的頁](customizing-errorhandler-pages.md)
   + [自定義節點類型](custom-nodetypes.md)
   + [添加圖形渲染的字型](adding-fonts.md)
   + [連接到SQL資料庫](jdbc.md)
   + [外部化URL](externalizer.md)
   + [建立和使用卸載作業](dev-offloading.md)
   + [配置Cookie使用](cookie-optout.md)
   + [如何以寫程式方式訪問AEMJCR](access-jcr.md)
   + [將服務與JMX控制台整合](jmx-integration.md)
   + [開發批量編輯器](dev-bulk-editor.md)
   + [開發報告](dev-reports.md)
   + 電子商務{#ecommerce}
      + [電子商務](ecommerce.md)
      + [開發（通用）](generic.md)
      + [使用SAPCommerce Cloud開發](sap-commerce-cloud.md)
+ 元件{#components}
   + [核心元件](https://docs.adobe.com/content/help/zh-Hant/experience-manager-core-components/using/introduction.html)
   + [樣式系統](https://experienceleague.adobe.com/docs/experience-manager-64/authoring/siteandpage/style-system.html)
   + [元件概述](components.md)
   + [組AEM件 — 基礎](components-basics.md)
   + [開發組AEM件](developing-components.md)
   + [開發AEM元件 — 代碼示例](developing-components-samples.md)
   + [Content Services的JSON導出器](json-exporter.md)
   + [為元件啟用JSON導出](json-exporter-components.md)
   + [影像編輯器](image-editor.md)
   + [裝飾標記](decoration-tag.md)
   + [使用隱藏條件](hide-conditions.md)
   + [配置多個就地編輯器](multiple-inplace-editors.md)
   + [開發人員模式](developer-mode.md)
   + [測試您的UI](hobbes.md)
   + [內容片段的元件](components-content-fragments.md)
   + [獲取JSON格式的頁資訊](pageinfo.md)
   + 國際化{#internationalization}
      + [國際化元件](i18n.md)
      + [國際化UI字串](i18n-dev.md)
      + [使用翻譯器管理詞典](i18n-translator.md)
      + [提取用於翻譯的字串](i18n-extract.md)
   + 經典UI元件{#classic-ui-components}
      + [開AEM發元件（經典UI）](developing-components-classic.md)
      + [使用和擴展小部件（經典UI）](widgets.md)
      + [使用xtypes（經典UI）](xtypes.md)
      + [開發Forms（經典UI）](developing-forms.md)
+ 無頭式體驗管理{#headless}
   + [無頭和混AEM合](https://business.adobe.com/content/dam/dx/us/en/products/experience-manager/sites/headless-content-management-system/pdfs/aem-hybrid-architecture-wp-1-18-19.pdf)
   + [為元件啟用JSON導出](https://experienceleague.adobe.com/docs/experience-manager-64/developing/components/json-exporter-components.html)
   + 單頁應用程式{#spas}
      + [介SPA紹和漫遊](spa-walkthrough.md)
      + [WKND教SPA程](spa-wknd.md)
      + [入門 — SPA反AEM應](spa-getting-started-react.md)
      + [入門 — SPAAngular](spa-getting-started-angular.md)
      + [針對 SPA 實作 React元件](spa-implementing-react-component.md)
      + [深SPA潛](spa-deep-dives.md)
      + [編SPA輯器概述](spa-overview.md)
      + [開SPA發AEM](spa-architecture.md)
      + [藍SPA圖](spa-blueprint.md)
      + [頁SPA面元件](spa-page-component.md)
      + [動態模型到元件的映SPA射](spa-dynamic-model-to-component-mapping.md)
      + [模SPA型路由](spa-routing.md)
      + [和SPAAdobe Experience Platform Launch](spa-launch.md)
      + [和SPA伺服器端呈現](spa-ssr.md)
      + [參SPA考材料](spa-reference-materials.md)
   + [HTTP API](https://experienceleague.adobe.com/docs/experience-manager-64/assets/extending/mac-api-assets.html)
   + [內容片段](https://experienceleague.adobe.com/docs/experience-manager-64/assets/fragments/content-fragments.html)
   + [體驗片段](https://experienceleague.adobe.com/docs/experience-manager-64/authoring/authoring/experience-fragments.html)
   + [瞭解中的內容片段和內容服AEM務](https://helpx.adobe.com/experience-manager/kt/sites/using/content-fragments-content-services-feature-video-understand.html)
+ 開發工具{#devtools}
   + [開發工具](dev-tools.md)
   + [AEM 現代化工具](modernization-tools.md)
   + [對話框編輯器](dialog-editor.md)
   + [對話框轉換工具](dialog-conversion.md)
   + [用CRXDE Lite開發](developing-with-crxde-lite.md)
   + [使用Maven管理包](vlt-mavenplugin.md)
   + [如何利用EclipseAEM開發項目](howto-projects-eclipse.md)
   + [如何使用Apache AEM Maven生成項目](ht-projects-maven.md)
   + [如何利用IntelliJ IDEAAEM開發項目](ht-intellij.md)
   + [如何使用VLT工具](ht-vlttool.md)
   + [如何使用代理伺服器工具](ht-proxy-server.md)
   + [括弧AEM擴展](aem-brackets.md)
   + [用AEM於Eclipse的開發人員工具](aem-eclipse.md)
   + [AEM Repo Tool](aem-repo-tool.md)
+ 個性化{#personlization}
   + [ContextHub](contexthub.md)
   + [ContextHub Javascript API參考](contexthub-api.md)
   + [擴展ContextHub](ch-extend.md)
   + [將ContextHub添加到頁面和訪問儲存](ch-adding.md)
   + [示例ContextHub儲存候選](ch-samplestores.md)
   + [示例ContextHub UI模組類型](ch-samplemodules.md)
   + [ContextHub診斷](ch-diagnostics.md)
   + [為目標內容開發](target.md)
   + ClientContext{#client-context}
      + [客戶端上下文詳細資訊](client-context.md)
      + [客戶端上下文Javascript API](ccjsapi.md)
+ 擴展AEM{#extending-aem}
   + [自定義頁面創作](customizing-page-authoring-touch.md)
   + [自定義控制台](customizing-consoles-touch.md)
   + [自定義頁面屬性的視圖](page-properties-views.md)
   + [配置頁面以批量編輯頁面屬性](bulk-editing.md)
   + [自訂和擴充內容片段](customizing-content-fragments.md)
   + 擴展工作流{#extending-workflows}
      + [開發和延伸工作流程](workflows.md)
      + [建立工作流模型](workflows-models.md)
      + [延伸工作流程功能](workflows-customizing-extending.md)
      + [以寫程式方式與工作流交互](workflows-program-interaction.md)
      + [工作流程步驟參考](workflows-step-ref.md)
      + [工作流最佳實踐](workflows-best-practices.md)
      + [工作流程處理序參考](workflows-process-ref.md)
   + [擴展多站點管理器](extending-msm.md)
   + 跟蹤和分析{#extending-analytics}
      + [擴展事件跟蹤](extending-analytics.md)
      + [將Adobe Analytics跟蹤添加到元件](extending-analytics-components.md)
      + [自定義Adobe Analytics框架](extending-analytics-framework.md)
      + [為分析實現伺服器端頁面命名](extending-analytics-pa-naming.md)
   + 雲端服務{#extending-cloud-services}
      + [雲端服務設定](extending-cloud-config.md)
      + [建立自定義Cloud Service](extending-cloud-config-custom-cloud.md)
   + [建立自定義擴展](extending-campaign-extensions.md)
   + 表單{#extending-forms}
      + [建立自定義表單映射](extending-campaign-form-mapping.md)
      + [使用Adobe CampaignAEM表單元件建立自定義頁面模板](extending-campaign-custom-template.md)
      + [請求分析指令碼](analyze-request.md)
   + [將服務與JMX控制台整合](https://experienceleague.adobe.com/docs/experience-manager-64/developing/platform/jmx-integration.html)
   + [開發批量編輯器](https://experienceleague.adobe.com/docs/experience-manager-64/developing/platform/dev-bulk-editor.html)
   + 擴展經典UI{#extending-classic-ui}
      + [自定義網站控制台(Classic UI)](customizing-siteadmin.md)
      + [自定義歡迎控制台(Classic UI)](customizing-the-welcome-console.md)
      + [開發報告](https://experienceleague.adobe.com/docs/experience-manager-64/developing/platform/dev-reports.html)
+ 測試{#testing}
   + [規劃](planning.md)
   + [需要哪些Test環境？](test-environments.md)
   + [定義Test案例](test-cases.md)
   + [測試 — 何時和誰？](when-who.md)
   + [編譯Test計畫](test-plan.md)
   + [跟蹤結果並提供反饋](results-and-feedback.md)
   + [測試和跟蹤工具](tools.md)
   + [接受和簽收](acceptance-signoff.md)
   + [下一版……](the-next-release.md)
   + [檢查清單](checklists.md)
   + [艱難的一天](tough-day.md)
   + [測試您的UI](https://experienceleague.adobe.com/docs/experience-manager-64/developing/components/hobbes.html)
+ 最佳作法{#bestpractices}
   + [最佳做法概述](best-practices.md)
   + [開發AEM指南和最佳做法](https://experienceleague.adobe.com/docs/experience-manager-64/developing/introduction/dev-guidelines-bestpractices.html)
   + [開發最佳做法](development-practices.md)
   + [內容體系結構](content-architecture.md)
   + [軟體體系結構](software-architecture.md)
   + We.Retail Reference實施{#we-retail}
      + [We.Retail Reference實施](we-retail.md)
      + [在We.Retail中嘗試內容片段](we-retail-content-fragments.md)
      + [在We.Retail中嘗試核心元件](we-retail-core-components.md)
      + [在We.Retail中嘗試可編輯模板](we-retail-editable-templates.md)
      + [在We.Retail中嘗試響應式佈局](we-retail-responsive-layout.md)
      + [We.Retail的全球化網站結構嘗試](we-retail-globalized-site-structure.md)
      + [We.Retail體驗片段的嘗試](we-retail-experience-fragments.md)
   + [編碼提示](coding-tips.md)
   + [代碼陷阱](code-pitfalls.md)
   + [OSGI捆綁包](osgi-bundles.md)
   + [JCR整合](jcr-integration.md)
   + [程式碼範例](code-samples.md)
   + [排除慢速查詢的故障](troubleshooting-slow-queries.md)
+ 移動Web{#mobileweb}
   + [移動Web](mobile-web.md)
   + [建立設備組篩選器](groupfilters.md)
   + [網頁響應性設計](responsive.md)
   + [為移動設備建立站點](mobile.md)
   + [模擬器](emulators.md)

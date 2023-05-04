---
title: 需要哪些測試環境？
seo-title: Which Test Environments are needed?
description: 應將數個環境視為測試的一部分
seo-description: Several environments should be considered as part of testing
uuid: bb725e50-edae-4c20-8107-d1c8df2e60e2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: db528b9b-3407-462d-8254-20b3cc2c3ccf
exl-id: c3c7c007-4814-4bd1-987e-534df4575a4a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 2%

---

# 需要哪些測試環境？{#which-test-environments-will-be-needed}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

若要定義測試的設定，您應考量下列事項：

**開發**  — 適用於單元和某些整合測試。

**測試**  — 用於大多數測試。

**即時**  — 最終效能和壓力測試。 也是客戶的接受測試。

您也需要決定需要哪個執行個體（通常所有測試層級至少各一個執行個體）:

**作者**  — 此例項可讓作者輸入及發佈內容。

**發佈**  — 此例項以發佈的形式呈現網站，供訪客存取。

應與Dispatcher一起測試。

最後，必須考慮實際硬體 — 在盡可能接近最終即時環境的配置中，對系統進行任何效能測試。 因此，也建議將專案啟動分割為：

**軟式啟動**  — 降低可用性；可讓您在生產環境的實際條件下，有時間進行效能測試、調整和最佳化。

**硬啟動**  — 完全可用。

---
title: AEM Communities概觀
seo-title: AEM Communities概觀
description: AEM Communities功能與設定概觀
seo-description: AEM Communities功能與設定概觀
uuid: 6e3ac9d2-ca31-40ea-8cab-b8451074c498
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 418cc919-0ae3-4c6c-8566-7e9a206f02a8
translation-type: tm+mt
source-git-commit: 1375282df15b1a1a1ab5ed760190af8d6288970e
workflow-type: tm+mt
source-wordcount: '1407'
ht-degree: 1%

---


# AEM Communities概觀{#aem-communities-overview}

Adobe Experience Manager(AEM)Communities提供快速建立內部部署社群網站的功能，可改善效能、改善網站管理，並鼓勵網站訪客轉換為有價值的社群成員。

<!--
Contact your account representative for information regarding licensing of AEM Communities as well as additional licensing for enablement features and Adobe Analytics.
-->

## 社群功能{#communities-features}

AEM Communities可讓您與網站訪客建立關係，透過部落格、問答和事件日曆提供資訊，同時透過論壇、留言和其他社群內容(通常稱為使用者產生的內容(UGC))獲得見解。

此外，AEM Communities還可讓受信任的成員在發佈環境中協調、使用Twitter和Facebook進行社交登入、社群內容的內嵌轉譯、從已發佈的社群網站建立社群群組、評分獎章、檔案分享、通知和活動串流。

使用GitHub.com公開提供的[AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki)或與新的We.Retail參考實作搭配使用，可展示社群功能。

## 社群網站 {#community-sites}

社群網站是使用簡單精靈建立的AEM網站，可產生網站，其中包含許多預先連線至網站的常用功能。

[站點建立嚮導](sites-console.md) :

* 根據選定的[社區站點模板](sites.md)組合站點的功能，即
   * 由[社區函式](#community-functions)構建
   * 可選[社區組](#communitygroups)功能
* 使用設定來設定：
   * 審核
   * 登入
   * 轉換
* 提供基本功能：
   * 自適應設計：使用[Twitter引導主題](https://getbootstrap.com)
   * 登入：自助註冊、[社交登入](social-login.md)、使用者設定檔
   * 通知：會員會看到與他們相關的事件
   * 訊息：會員可以在社群網站內傳送或接收訊息
   * 搜尋：能夠在社群網站內搜尋
   * 語言切換：能夠為[多語種站點](../../help/sites-administering/translation.md)選擇語言
   * 管理：存取權，讓授權會員在社群網站中協調和管理使用者
* 免除許多頁面層級的製作步驟：
   * 品牌：可選上傳橫幅影像，以便顯示在社群網站的所有頁面上
   * 導覽功能表：為社群網站範本中包含的功能提供導覽連結

若要體驗快速建立新社群網站的便利性，請造訪[AEM Communities](getting-started.md)快速入門。

## 社群內容永續性{#community-content-persistence}

為改善社群內容的效能與同步化，AEM Communities需要專為所有AEM（作者和發佈）例項之間共用的使用者產生內容(UGC)而設定的公用儲存。

社區內容可通過儲存資源提供器(SRP)輕鬆訪問，該提供器提供一個層，用於將訪問與底層拓撲分開，並支援UGC的公共儲存。

若要進一步瞭解社群內容永續性和建議的部署，請造訪：

* [社群內容儲存](working-with-srp.md):討論UGC的可用SRP儲存選項
* [建議的拓撲](topologies.md):討論基於使用案例和SRP選擇的拓撲
* [升級至AEM 6.3 Communities](upgrade.md):提供移至AEM 6.3時有關UGC的實用資訊。

## Communities Console {#communities-consoles}

在作者環境中，全域導覽主控台提供對[Communities主控台](consoles.md)的存取，其中包含：

* [Sitesconsole](sites-console.md) 

   * 網站建立
   * 網站編輯
   * 網站管理
   * [社群群群組](groups.md) 主控台

* [協調控](moderation.md) 制台

   * 作者和發佈環境的常見大量協調UI
   * 新的篩選條件

* [成員和組管](members.md) 理控制台

   * 提供從作者環境建立和管理發布端使用者（成員）的能力
   * 提供禁止成員的能力
   * 提供從作者環境建立和管理發布端使用者群組（成員群組）的能力

* [Reportsconsole(報](reports.md) 告控制台)

   * 提供產生指派、貼文和檢視報告的能力

* [資源](resources.md) 控制台

   * 提供建立啟用資源和學習途徑的能力
   * 提供對啟用資源和學習路徑報告的存取

全域工具主控台可存取下列社群工具：

* [網站範本控](tools.md#sitetemplatesconsole) 制台

   * 建立和管理社群網站範本

* [群組範本控](tools.md#grouptemplatesconsole) 制台

   * 建立和管理社群群組範本

* [社群功能](tools.md#communityfunctionsconsole) 主控台

   * 建立和管理社群功能

* [儲存配置](tools.md#storageconfiguratonconsole) 控制台

   * 選擇並配置站點的[公共儲存](working-with-srp.md)

* [元件指南](components-guide.md)

   * 一個示例站點[社區元件](http://localhost:4502/editor.html/content/community-components/en.html)，它提供了所有社區元件的示例及其預設配置，並能夠對它們進行實驗

## 社群網站範本 {#community-site-templates}

社群網站的建立是以選擇社群網站範本為基礎，以快速設定獨立於任何範例網站的社群網站。

社群網站範本由社群功能和社群群組範本組成，提供社群網站的結構，包括登入、使用者設定檔、傳訊、網站選單、搜尋、主題和品牌功能。

請參閱[網站範本主控台](sites.md)。

## 社群功能 {#community-functions}

社群體驗預期的功能眾所周知。 有了AEM Communities，這些功能即可做為建置區塊，稱為社群功能。

社群功能是一般的AEM頁面，由連線到功能的元件組成，可輕鬆整合到社群網站範本中。

請參閱[社群功能控制台](functions.md)。

## 社群群組和群組範本{#community-groups-and-group-templates}

社群群組功能是讓來自作者和發佈環境的授權使用者和社群成員在社群網站中動態建立子社群的能力。

當模板的結構包含[組函式](functions.md#groups-function)時，可從作者環境在現有社區站點中建立社區組（子社區）或在現有組內嵌套。

建立社區組需要選擇提供社區組頁面設計的社區組模板。 將「群組」功能新增至範本結構時，其設定為指定一個群組範本，或在建立新社群群組時提供範本選擇。

另請參閱:

* [網站群組主控台](groups.md) -在作者環境中建立子社群
* [群組範本主控台](tools-groups.md) -建立群組的網站結構
* [AEM Communities快速入門](getting-started.md) -快速建立社群網站（包括巢狀群組）的教學課程

## 社群元件{#community-components}

建立社群網站的[社群元件](author-communities.md)可用於將社群功能新增至任何AEM網站。

[社群元件指南](components-guide.md)可供互動探索元件。

## 社區類型{#types-of-communities}

### 參與社群{#engagement-community}

參與社群是社群網站，主要吸引客戶提供資訊、徵求意見，並讓客戶以社群成員的身分互動。

參與社群的功能可能包括：

* 登入
* 傳送訊息
* 論壇
* 評論
* 評論
* 評等
* 投票
* 部落格
* 群組
* 日曆
* 轉換
* 審核
* 通知
* 計分和徽章
* Analytics報表

若要體驗快速建立新參與社群的簡易性，請造訪[AEM Communities](getting-started.md)快速入門。

### 啟用社群{#enablement-community}

啟用社群是包含線上學習功能的社群網站。

啟用社群的功能可能包括：

* [參與社群](#engagement-community)的所有功能
* 可指派內容和學習資源給成員和成員群組
* 支援SCORM內容，例如測驗和測試
* 跟蹤任務完成
* 存取報告與分析
* 透過論壇、訊息、留言和評分進行學習資源相關對話的能力

當配置[啟用附加元件](enablement.md)時，可建立啟用社區，該附加元件需要額外的許可以用於生產環境。 啟用社群網站將包含[指派函式](#community-functions)。

若要體驗建立新啟用社群的便利性，請造訪[AEM Communities for Enablement](getting-started-enablement.md)快速入門。

## AEM Demo Machine {#aem-demo-machine}

[AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine)管理並執行AEM [Sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites)、[Assets](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets)、[Communities](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities)、[Apps](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps)和[Forms&lt;a111/>的示範程式，這通常需要更多的設定，而不只是啟動QuickStart實例。 ](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms)AEM Demo Machine將設定額外的[基礎架構](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure)，例如MongoDB、Solr、MySQL、FFmpeg和電子郵件伺服器。

AEM Demo Machine由

* A [圖形用戶介面](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface)
* 具有可配置[屬性](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties)和[目標](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line)的Apache ANT指令碼
* 要安裝的軟體包
AEM Demo Machine已在Windows、MacOS和Linux上成功測試CQ 5.5、CQ 5.6.1、AEM 6.0、AEM 6.1、AEM 6.2和AEM 6.3。

AEM Demo Machine需要有效的AEM授權。

>[!NOTE]
>
>檢視AEM Demo Machine(13:26)的[影片簡介](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be)。

## AEM Communities Documentation {#aem-communities-documentation}

* 請造訪[部署社群](deploy-communities.md)以瞭解建議的部署。

* 請造訪[管理社群網站](administer-landing.md)，以瞭解如何建立社群網站、新增社群群組、設定社群網站範本、協調社群內容、管理成員、標籤、通知、計分和標章。

* 請造訪[開發社群](communities.md)以瞭解社交元件架構(SCF)和自訂社群元件和功能。

* 請造訪[編寫社群元件](author-communities.md)，以瞭解如何編寫和設定社群元件。


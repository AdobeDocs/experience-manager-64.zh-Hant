---
title: AEM Communities概述
seo-title: AEM Communities概述
description: AEM Communities功能與設定的概觀
seo-description: AEM Communities功能與設定的概觀
uuid: 6e3ac9d2-ca31-40ea-8cab-b8451074c498
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 418cc919-0ae3-4c6c-8566-7e9a206f02a8
exl-id: 3a8b21f8-75da-4867-9a8a-80fddf7946ed
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1407'
ht-degree: 1%

---

# AEM Communities概述{#aem-communities-overview}

Adobe Experience Manager(AEM)Communities可讓您快速建立內部部署社群網站，進而改善效能、改善網站管理，並鼓勵將網站訪客轉換為有價值的社群成員。

<!--
Contact your account representative for information regarding licensing of AEM Communities as well as additional licensing for enablement features and Adobe Analytics.
-->

## 社區功能{#communities-features}

AEM Communities可讓您與網站訪客建立關係，透過部落格、問答和事件日曆進行通知，同時透過論壇、留言和其他社群內容(通常稱為使用者產生的內容(UGC))獲得深入分析。

此外，AEM Communities還允許發佈環境中受信任的成員進行協調、使用Twitter和Facebook進行社交登入、內嵌社群內容翻譯、從已發佈的社群網站建立社群群組、評分以授予徽章、檔案共用、通知和活動資料流。

可使用GitHub.com上公開提供的[AEM示範電腦](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki)，或透過新的We.Retail參考實作來示範社群功能。

## 社群網站 {#community-sites}

社群網站是使用簡單精靈建立的AEM網站，可產生預先連線至網站的許多常見功能的網站。

[站點建立嚮導](sites-console.md):

* 根據所選[社區站點模板](sites.md)組合站點的功能，該模板為
   * 從[community函式](#community-functions)建立
   * 可選[社區組](#communitygroups)功能
* 使用設定進行配置：
   * 審核
   * 登入
   * 轉換
* 提供基本功能：
   * 回應式設計：使用[TwitterBootstrap主題](https://getbootstrap.com)
   * 登入：自行註冊、[社交登入](social-login.md)、使用者設定檔
   * 通知：成員們看到與他們相關的事件
   * 傳訊：成員可以在社區站點內發送或接收消息
   * 搜尋：可在社群網站內搜尋
   * 語言切換：為[多語言站點](../../help/sites-administering/translation.md)選擇語言的能力
   * 管理：授權成員的存取權，以協調和管理社群網站內的使用者
* 消除了許多頁面層級的製作步驟：
   * 品牌推廣：選擇性上傳橫幅影像，以在社群網站的所有頁面上顯示
   * 導覽功能表：為社區站點模板中包含的功能提供導航連結

若要快速建立新社群網站的便利性，請造訪[AEM Communities快速入門](getting-started.md)。

## 社群內容持續性{#community-content-persistence}

為了改善社群內容的效能與同步，AEM Communities需要專門針對在所有AEM（製作和發佈）執行個體之間共用的使用者產生內容(UGC)的通用存放區。

通過儲存資源提供器(SRP)輕鬆訪問社區內容，該提供器提供一個層，以將訪問與基礎拓撲分開，並支援UGC的公共儲存。

若要進一步了解社群內容持續性和建議的部署，請造訪：

* [社群內容儲存](working-with-srp.md):討論UGC的可用SRP儲存選項
* [建議的拓撲](topologies.md):基於用例和SRP選擇討論拓撲
* [升級至AEM 6.3 Communities](upgrade.md):提供移至AEM 6.3時與UGC相關的實用資訊。

## Communities控制台{#communities-consoles}

在製作環境中，全域導覽主控台提供對[Communities主控台](consoles.md)的存取，其中包含：

* [](sites-console.md) Siteconsole

   * 網站建立
   * 網站編輯
   * 網站管理
   * [社群群](groups.md) 組主控台

* [](moderation.md) Moderationconsole

   * 適用於製作和發佈環境的常見大量協調UI
   * 新篩選條件

* [成員和群](members.md) 組管理控制台

   * 提供從製作環境建立及管理發布端使用者（成員）的功能
   * 提供禁止成員的能力
   * 提供從製作環境建立和管理發布端使用者群組（成員群組）的功能

* [](reports.md) Reportsconsole

   * 提供產生工作分配、貼文和檢視報表的能力

* [](resources.md) Resourcesconsole

   * 提供建立啟用資源和學習路徑的功能
   * 提供啟用資源和學習路徑報表的存取權

全局工具控制台提供對以下Communities工具的訪問：

* [網站范](tools.md#sitetemplatesconsole) 本

   * 建立和管理社區站點模板

* [群組範本](tools.md#grouptemplatesconsole) 控制台

   * 建立和管理社群群組範本

* [社群功能](tools.md#communityfunctionsconsole) 主控台

   * 建立和管理社區功能

* [儲存配](tools.md#storageconfiguratonconsole) 置控制台

   * 選擇並配置站點的[公共儲存](working-with-srp.md)

* [元件指南](components-guide.md)

   * 一個示例站點[社區元件](http://localhost:4502/editor.html/content/community-components/en.html)，它提供了所有社區元件的示例，以及其預設配置和實驗功能

## 社群網站範本 {#community-site-templates}

社群網站的建立是根據社區網站模板的選擇，以快速設定獨立於任何示例網站的社區網站。

由社區功能和社區組模板組成的社區站點模板提供了社區站點的結構，包括登錄、用戶配置檔案、消息、站點菜單、搜索、主題和品牌特徵。

請參閱[網站範本主控台](sites.md)。

## 社群功能 {#community-functions}

社群體驗預期的功能眾所周知。 透過AEM Communities，這些功能可作為建置組塊，稱為社群功能。

社群功能是一般AEM頁面，由連線至功能中的元件所組成，這些元件可輕鬆整合至社群網站範本中。

請參閱[社群函式控制台](functions.md)。

## 社區組和組模板{#community-groups-and-group-templates}

社群群組功能是讓來自製作和發佈環境的授權使用者和社群成員在社群網站內動態建立子社群的能力。

當範本的結構包含[群組函式](functions.md#groups-function)時，可從製作環境中，在現有社群網站內建立或巢狀內建立社群群組（子社群）。

建立社群群組需要選取社群群組範本，以提供社群群組頁面的設計。 將「組」函式添加到模板結構時，該函式配置為指定一個組模板，或在建立新的社區組時提供模板選項。

另請參閱:

* [網站群組主控台](groups.md)  — 在製作環境中建立子社群
* [群組範本主控台](tools-groups.md)  — 為群組建立網站結構
* [AEM Communities快速入門](getting-started.md)  — 快速建立社群網站（包括巢狀群組）的教學課程

## 社區元件{#community-components}

建立社群網站的[社群元件](author-communities.md)可用於將社群功能新增至任何AEM網站。

[社群元件指南](components-guide.md)可供互動探索各元件。

## 社區類型{#types-of-communities}

### 參與社群{#engagement-community}

參與社群是社群網站，主要讓客戶提供相關資訊、徵求意見，並允許客戶以社群成員的身分互動。

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

若要快速建立新參與社群的便利性，請造訪[AEM Communities快速入門](getting-started.md)。

### 啟用社群{#enablement-community}

培訓社群是社群網站，包含線上學習功能。

啟用社群的功能可能包括：

* [參與社群](#engagement-community)的所有功能
* 能夠將內容和學習資源分配給成員和成員組
* 支援SCORM內容，例如測驗和測試
* 跟蹤任務完成
* 存取報告與分析
* 能夠通過論壇、報文傳送、評論和評分就學習資源進行對話

當[啟用附加元件設定](enablement.md)時，可建立啟用社群，這需要額外的授權才能在生產環境中使用。 啟用社群網站將包含[指派函式](#community-functions)。

若要輕鬆建立新的啟用社群，請造訪[啟用AEM Communities快速入門](getting-started-enablement.md)。

## AEM示範電腦{#aem-demo-machine}

[AEM演示電腦](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine)管理並運行AEM [Sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites)、[Assets](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets)、[Communities](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities)、[Apps](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps)和[Forms](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms)的演示，這通常比啟動快速啟動實例更需要設定。 AEM演示電腦將設定其他[基礎架構](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure)，如MongoDB、Solr、MySQL、FFmpeg和電子郵件伺服器。

AEM Demo Machine由

* [圖形用戶介面](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface)
* 具有可配置[properties](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties)和[targets](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line)的Apache ANT指令碼
* 要安裝的軟體包
已在Windows、MacOS和Linux上使用CQ 5.5、CQ 5.6.1、AEM 6.0、AEM 6.1、AEM 6.2和AEM 6.3成功測試AEM示範電腦。

AEM Demo Machine需要有效的AEM授權。

>[!NOTE]
>
>查看AEM演示電腦的[視頻簡介](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be) (13:26)。

## AEM Communities檔案{#aem-communities-documentation}

* 請造訪[部署Communities](deploy-communities.md)以了解建議的部署。

* 請訪問[管理社群網站](administer-landing.md)以了解如何建立社群網站、新增社群群組、設定社群網站範本、協調社群內容、管理成員、標籤、通知、評分和徽章。

* 請造訪[開發社群](communities.md)以了解社交元件架構(SCF)和自訂社群元件和功能。

* 請造訪[編寫社群元件](author-communities.md)，了解如何使用和設定社群元件。

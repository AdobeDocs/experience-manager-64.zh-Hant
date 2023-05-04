---
title: Tally Essentials
seo-title: Tally Essentials
description: 計分類概覽
seo-description: Tally class overview
uuid: c369c6a1-9ced-4b5c-af43-8c03236eaa52
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 9941ba90-3d40-4c90-bca8-5db49603cbfa
exl-id: f04ec253-08b8-4ee2-9873-4a51549daeba
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 1%

---

# Tally Essentials {#tally-essentials}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Tally是抽象類，提供一種從成員收集反饋的標準方法，以了解他們如何評估特定產品和服務。 不支援匿名反饋。 網站訪客必須註冊並登入才能參與並登入，以變更其意見反應。 登入需求可防止多則貼文，以便協調及提高意見的價值。

可通過擴展抽象計數類來建立自定義計數元件。

[贊](essentials-liking.md) 是一種簡單的表達積極意見的理解。

[投票](essentials-voting.md) 是表達正面或負面意見的簡單形式的統計。

[評等](rating-basics.md) 是使用星號系統來表達從正面到負面的一系列觀點的統計。

自AEM 6.1起， *輪詢* 元件已無法使用。

[評論](reviews-basics.md) 是SCF元件，是 [評論](essentials-comments.md) 和 [評分](rating-basics.md).

## 用戶端的要點 {#essentials-for-client-side}

* [用戶端自訂](client-customize.md)

## 伺服器端的Essentials {#essentials-for-server-side}

* [Tally API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [計數端點](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [伺服器端自訂](server-customize.md)

### 訪問已發佈的記錄(UGC) {#accessing-posted-tallies-ugc}

UGC應使用其中一種標準的協調方法來協調。\
請參閱 [協調使用者產生的內容](moderate-ugc.md).

自AEM 6.1社群起，請使用 [公用商店](working-with-srp.md) 針對UGC包括可程式化地存取UGC，而無論選擇的儲存選項（例如ASRP、MSRP或JSRP）。

**UGC在存放庫中的位置和格式可能會變更，恕不另行警告**.

請參閱：

* [儲存資源提供程式概述](srp.md)  — 簡介和存放庫使用概觀
* [SRP和UGC要點](srp-and-ugc.md) - SRP實用程式方法和示例
* [使用SRP存取UGC](accessing-ugc-with-srp.md)  — 編碼准則
* [SocialUtils重構](socialutils.md)  — 將已棄用的實用程式方法映射到當前SRP實用程式方法

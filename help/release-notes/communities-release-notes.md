---
title: AEM Communities發行說明
seo-title: AEM Communities
description: Adobe Experience Manager 6.4 Communities的發行說明。
seo-description: Adobe Experience Manager 6.4 Communities的發行說明。
uuid: 2de9f511-2a61-4003-9b2c-d6728bc9d57a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 55a0b70e-5212-408b-8560-6e758bd8bb10
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 4%

---


# AEM Communities發行說明{#aem-communities-release-notes}

本節提供自6.3版本起對AEM Communities的改進。 若要詳細瞭解新功能，請參閱[「AEM 6.4 Communities的新增功能](/help/communities/whats-new-aem-communities.md)」。

要獲得最新版本，請參閱文檔的[部署社區](/help/communities/deploy-communities.md#latest-releases)部分。

## 主要改進{#main-improvements}

社群網站:

* 社群管理員現在可以：

   * 永久刪除社群網站
   * 為社區站點選擇上下文感知配置資料夾

社群群組:

* 社群管理員現在可以：

   * 永久刪除社群群組
   * 以多種語言建立社群群組
   * 在社群群組中新增啟用目錄和指派

* 啟用管理員現在可以

   * 在社群群組中建立並指派資源和學習路徑

檔案庫:

* 社群成員現在對檔案庫有多項增強功能，例如排序順序、標籤……

通知:

* 社群成員現在會在核准經過協調程式的貢獻時收到通知

審核:

* 自動化垃圾訊息偵測篩選
* 社群協調者有其他「協調」篩選條件（例如已回答／未回答的問題）
* 社群協調者可將協調書籤及連結至預先定義的篩選（例如，所有待核准的貼文）

與AEM 6.4的基本變更整體相容。

注意：AEM 6.3也提供這些功能。請查看AEM Communities的發行說明，以瞭解[6.3](https://helpx.adobe.com/tw/experience-manager/6-3/release-notes.html)。

## 已知問題 {#known-issues}

* **協調** -無法從大量協調UI中將父貼文刪除為單一刪除作業(CQ-4236797)
* **控制台** -忘記使用者名稱或密碼連結會重新導向至登入頁面，而非對應的密碼擷取表單(CQ-4237682)

## 選擇功能{#select-features}

專家評分（由Sensei *提供支援）-可讓遊戲化，這是鼓勵和獎勵寶貴社群行為的有效方式。*&#x200B;它也可用於識別專家以用於建議或行銷。

## 演示{#demonstrations}

使用GitHub.com公開提供的[AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki)，當使用AEM Communities示範案例時，以及新的We.Retail參考實作時，可展示所有這些功能。

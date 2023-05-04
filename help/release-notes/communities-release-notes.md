---
title: AEM Communities發行說明
seo-title: AEM Communities
description: Adobe Experience Manager 6.4 Communities專屬發行說明。
seo-description: Release notes specific to Adobe Experience Manager 6.4 Communities.
uuid: 2de9f511-2a61-4003-9b2c-d6728bc9d57a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 55a0b70e-5212-408b-8560-6e758bd8bb10
exl-id: 3a341e72-01c5-4c63-8942-6320e5b08440
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 5%

---

# AEM Communities發行說明 {#aem-communities-release-notes}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

本節提供自6.3版以來AEM Communities的改善項目資訊。 若要進一步了解新功能，請參閱 [AEM 6.4社群的新功能](/help/communities/whats-new-aem-communities.md).

若要取得最新版本，請參閱 [部署社群](/help/communities/deploy-communities.md#latest-releases) 一節。

## 主要改善 {#main-improvements}

社群網站:

* 社群管理員現在可以：

   * 永久刪除社群網站
   * 為社群網站選取內容感知設定資料夾

社群群組:

* 社群管理員現在可以：

   * 永久刪除社群組
   * 以多種語言建立社群群組
   * 在社群群組中新增啟用目錄和指派

* 啟用管理員現在可以

   * 在社群群組中建立並指派資源和學習路徑

檔案庫:

* 社群成員現在對檔案庫有多項增強功能，例如排序順序、標籤……

通知:

* 社群成員現在會在核准經過協調程式的貢獻時收到通知

審核:

* 自動垃圾郵件檢測篩選器
* 社群協調者有其他「協調」篩選條件（例如已回答/未回答的問題）
* 社群協調者可將協調書籤及連結至預先定義的篩選條件（例如所有待核准的貼文）

與AEM 6.4的基礎變更整體相容。

注意：AEM 6.3也提供這些功能。請參閱AEM Communities發行說明，了解 [6.3](https://helpx.adobe.com/tw/experience-manager/6-3/release-notes.html).

## 已知問題 {#known-issues}

* **協調**  — 無法從大量協調UI中以單一刪除操作的形式刪除父貼文(CQ-4236797)
* **主控台**  — 忘記使用者名稱或密碼連結會重新導向至登入頁面，而非對應的密碼擷取表單(CQ-4237682)

## 選擇功能 {#select-features}

專家評分(*由Sensei提供*) — 用來啟用遊戲化，這是鼓勵和獎勵寶貴社群行為的有效方式。 它也可用於識別專家以供建議或行銷之用。

## 示威 {#demonstrations}

所有這些功能都可透過 [AEM示範電腦](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) 使用AEM Communities示範案例時，以及新的We.Retail參考實作時，可在GitHub.com上公開取得。

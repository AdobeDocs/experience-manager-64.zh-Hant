---
title: 企業 DevOps
seo-title: Enterprise DevOps
description: 了解輕鬆部署、簡化共同作業所需的程序、方法和溝通方式。
seo-description: Learn about the processes, methods and communication required to ease deployment and simplify collaboration.
uuid: ca4806d2-c845-4c18-9498-4b66f0980a5e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/MANAGING
topic-tags: managing
content-type: reference
discoiquuid: 934eda2a-bd3b-4018-86dc-dbb01d246386
exl-id: 7d1145e8-d7f7-4cc7-9dd9-ee8ce04e43d4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1025'
ht-degree: 91%

---

# 企業 DevOps{#enterprise-devops}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

DevOps 涵蓋下列工作所需的程序、方法和溝通方式：

* 輕鬆地在各種環境中部署您的軟體。
* 簡化開發、測試和部署團隊間的共同作業。

DevOps 旨在避免下列問題：

* 人為錯誤。
* 被遺忘的元素；例如檔案、設定詳細資訊。
* 不一致；例如開發人員的本機環境與其他環境間的差異。

## 環境 {#environments}

Adobe Experience Manager(AEM)部署通常由多個環境組成，用於不同層級的不同用途：

* [開發](#development)
* [品質保證](#quality-assurance)
* [預備](#staging)
* [生產](#production-author-and-publish)

>[!NOTE]
>
>在生產環境中，必須至少有一個作者環境和一個發佈環境。
>
>我們建議由作者和發佈環境組成所有其他環境，以便反映生產環境，並啟用初期測試。

### 開發 {#development}

開發人員負責開發和自訂所提出的專案 (無論是網站、行動應用程式或 DAM 實作等)，並具備所有必要的功能。上述功能為：

* 開發和自訂必要的要素；例如範本、元件、工作流程、應用程式
* 實現設計
* 開發必要的服務和指令碼以實作所需功能

[開發](/help/sites-developing/best-practices.md)環境的設定可能取決於多種因素，但通常包括：

* 具備版本控制、可提供整合程式碼庫的整合開發系統。這可用來合併來自每個開發人員使用之個別開發環境的程式碼。
* 屬於每個開發人員的個人環境；通常位於他們的本機電腦上。程式碼會透過版本控制系統，以適當間隔同步

根據您的系統規模，開發環境可同時擁有作者執行個體和發佈執行個體。

### 品質保證 {#quality-assurance}

品質保證團隊會使用此環境，以全面 [測試](/help/sites-developing/test-plan.md) 新系統；設計和功能。 此環境應同時具備作者環境、發佈環境及適當的內容，並提供所有啟用完整測試套件所需的服務。

### 預備 {#staging}

預備環境必須是生產環境的鏡像 (包括設定、程式碼和內容)：

* 此環境用於測試要用來實作實際部署的指令碼。
* 在部署至生產環境之前，可使用此環境進行最終測試 (設計、功能和介面)。
* 雖然預備環境未必與生產環境完全相同，但應該盡量使兩者相似，以便啟用效能與負載測試。

### 生產：作者與發佈 {#production-author-and-publish}

生產環境包含實際[製作與發佈](/help/sites-authoring/author.md#concept-of-authoring-and-publishing)實作所需的環境。

生產環境至少會由一個製作環境和一個發佈環境組成：

* 輸入內容的[製作](#author)執行個體。
* 可供您的訪客/使用者使用的內容之[發佈](#publish)執行個體。

根據專案的規模，生產環境通常由多個製作和/或發佈執行個體組成。在較低的層級中，也可以將存放庫與多個執行個體一起加入叢集。

#### 作者 {#author}

製作執行個體通常位於內部防火牆後。您和您的同事將在此環境中執行製作任務，例如：

* 管理整個系統
* 輸入內容
* 設定內容的配置和設計
* 為發佈環境啟用內容

已啟用的內容會封裝並放置在作者環境的複製佇列中。接著，複製程序會將內容傳輸至發佈環境。

為了將發佈環境中產生的資料反向複製回製作環境，製作環境中的複製接聽程式將輪詢發佈環境，並從發佈環境的反向複製寄件匣中擷上述內容。

#### 發佈 {#publish}

發佈環境通常位於非軍事區域 (DMZ) 中。無論是在公開或內部網路中，訪客都將在此環境中存取您的內容 (例如：透過網站或行動應用程式) 並與之互動。發佈環境：

* 可保留從作者環境複製的內容
* 供訪客使用該內容
* 儲存訪客產生的使用者資料，例如留言或其他提交的表單
* 可以設定將上述使用者資料新增至寄件匣，以便反向複製回作者環境

發佈環境會不斷即時產生您的內容，而且可針對個別使用者個人化內容。

## 程式碼動向 {#code-movement}

程式碼應一律由下向上傳播：

* 程式碼最初在本機開發，然後在開發環境中整合
* 接著在 QA 環境進行徹底測試
* 然後在預備環境中再次測試
* 此時，才可以將程式碼部署至生產環境

通常會透過在不同內容存放庫間匯出和匯入封裝，來轉移程式碼 (例如自訂的 Web 應用程式功能和設計範本)。這代表可以將此複寫設定為自動程序。

AEM專案常會觸發程式碼部署：

* 自動：用於轉移至開發和 QA 環境。
* 手動：部署至預備和生產環境的方式比較需要控制，通常以手動進行；不過，也可視需要採取自動化部署。

![chlimage_1](assets/chlimage_1.png)

## 內容動向 {#content-movement}

為生產而建立的內容應&#x200B;**一律**&#x200B;在生產作者執行個體上編寫。

內容不應隨程式碼從較低層級的環境移至較高層級的環境，因為讓作者在本機或較低層級的環境中建立內容，再將內容移至生產環境並非明智作法，而且可能會造成錯誤和不一致。

生產內容應從生產環境移至預備環境，以確保預備環境提供有效率且精確的測試環境。

>[!NOTE]
>
>這並不表示預備內容需要持續與生產同步，定期更新便已足夠 (尤其在測試新的程式碼疊代前。)QA 和開發環境中的內容不需要頻繁更新，只需良好呈現生產內容即可。

內容可經由下列途徑轉移：

* 在不同環境間：透過匯出和匯入套件。
* 在不同執行個體之間 — 透過直接複製([AEM復寫](/help/sites-deploying/replication.md))內容（使用HTTP或HTTPS、連線）。

![chlimage_1-1](assets/chlimage_1-1.png)

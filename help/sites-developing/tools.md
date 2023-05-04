---
title: 測試和追蹤工具
seo-title: Testing and Tracking Tools
description: AEM提供測試元件UI的架構，以及測試和偵錯元件的機制
seo-description: AEM provides a framework for testing component UI and a mechanism for testing and debugging components
uuid: 29c43202-0a4e-41ba-9176-92fa77c627d5
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 0f977264-fe58-4478-bd38-aca5c75f36aa
exl-id: 9387cdb4-f8de-4229-90d1-59218ac17561
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 2%

---

# 測試和追蹤工具{#testing-and-tracking-tools}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 測試 {#testing}

AEM提供：

* [測試元件UI的架構](/help/sites-developing/hobbes.md).
* [用於測試和調試元件的機制](/help/sites-developing/developer-mode.md).

以下是兩種開放原始碼測試工具：

**硒**

Selenium用於在每個活動有一個使用者的瀏覽器中進行函式測試。 它將測試步驟（點按）記錄為HTML表或Java類。

如需詳細資訊，請參閱 [https://www.seleniumhq.org/](https://www.seleniumhq.org/).

**JMeter**

JMeter用於追蹤請求，可用於功能、效能和壓力測試。

如需詳細資訊，請參閱 [http://jakarta.apache.org/jmeter/](http://jakarta.apache.org/jmeter/).

還有許多專用工具用於自動化測試和管理測試計畫。

## 追蹤 {#tracking}

您可輕鬆使用下列工具。 但是，所有情況下的一個關鍵問題是項目團隊的所有成員（合作夥伴和客戶）都能獲得資料。

**布吉拉**

可依您自己的需求設定的錯誤追蹤系統。

**試算表**

雖然不是專門用於跟蹤錯誤的工具，但電子錶格經常被誤用於此目的，因為它們易於理解，而且大多數用戶都有其功能的經驗。

如果這些用於追蹤，則：

* 應該保持簡單。
* 個別電子錶格的數量應保持在最低水準。
* 必須定期更新。
* 只應維護一個主副本，每個人都應知道主副本的位置。
* 所有項目成員都應能訪問它們。
* 如果安全性是問題（通常發生在大型公司），並且無法進行共同訪問，則只要每個人都知道這些是副本，並且無法更新，就可能分發副本。

此外，還有許多專用工具可追蹤錯誤和功能需求。

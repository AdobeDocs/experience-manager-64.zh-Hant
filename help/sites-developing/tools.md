---
title: 測試和追蹤工具
seo-title: 測試和追蹤工具
description: AEM提供測試元件UI的架構，以及測試和除錯元件的機制
seo-description: AEM提供測試元件UI的架構，以及測試和除錯元件的機制
uuid: 29c43202-0a4e-41ba-9176-92fa77c627d5
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 0f977264-fe58-4478-bd38-aca5c75f36aa
translation-type: tm+mt
source-git-commit: 60f36a33471dbbd9ca877dbbedc82ade606a125c
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---


# 測試和追蹤工具{#testing-and-tracking-tools}

## 測試 {#testing}

AEM提供：

* [測試元件UI的架構](/help/sites-developing/hobbes.md)。
* [測試和除錯元件的機制](/help/sites-developing/developer-mode.md)。

以下是兩種開放原始碼測試工具：

**硒**

Selenium用於瀏覽器中的函式測試，每個活動有一個用戶。 它會將測試步驟（點按）記錄為HTML表格或Java類別。

如需詳細資訊，請參 [閱https://www.seleniumhq.org/](https://www.seleniumhq.org/)。

**JMeter**

JMeter用於跟蹤請求，可用於功能、效能和壓力測試。

如需詳細資訊，請參 [閱http://jakarta.apache.org/jmeter/](http://jakarta.apache.org/jmeter/)。

此外，還有許多專屬工具可自動化測試和管理測試計畫。

## 追蹤 {#tracking}

您可輕鬆使用下列工具。 但是，所有情況下的一個關鍵問題是，項目團隊的所有成員（合作夥伴和客戶）都可以獲得資料。

**布齊拉**

可依您自己的需求設定的錯誤追蹤系統。

**試算表**

雖然並非特別是錯誤追蹤工具，但試算表通常會因此遭濫用，因為試算表易於理解，而且大部分使用者都有其功能經驗。

如果這些用於追蹤，則：

* 應該保持簡單。
* 個別試算表的數量應保持在最低。
* 必須定期更新。
* 只應維護一個主副本，每個人都應知道主副本的位置。
* 所有專案成員都應可存取這些項目。
* 如果安全性有問題（通常發生在大公司）且無法進行共同存取，則只要每個人都知道這些是副本，而且無法更新，就可以分發副本。

此外，還有許多專屬工具可追蹤錯誤和功能需求。

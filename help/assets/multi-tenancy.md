---
title: 適用於系列、程式碼片段和程式碼片段範本的多租用功能
description: 根據客戶組織隔離CRX儲存庫中的內容，以防止未經授權的訪問。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---


# 適用於系列、程式碼片段和程式碼片段範本的多租用功能 {#multi-tenancy-for-collections-snippets-and-snippet-templates}

多租賃功能可讓您根據組織首碼和組織ID，在CRX中區隔內容，以保護內容不受其他組織使用者未經授權的存取。

Adobe Experience Manager(AEM)Assets會將每個組織的資料儲存在不同的路徑中。 每個組織特定路徑都由組織首碼和組織ID來識別。
它包含在CRX中儲存不同類型資產的傳統位置。

例如，如果您建立名為的檔案夾， `Demo`AEM資產預設會將檔案夾儲存在CRX `../content/dam/Demo` 的位置。 啟用多租賃功能後，您可以將資料儲存在 `../content/dam/<organization prefix>/<organization id>Demo`。

例如，對於指派給組織的AEM Assets（隨選）的Adobe Marketing Cloud使用者 `aodpremium` ，您可以使用多租賃功能來設定下列內容路徑 `../content/dam/mac/aodpremiumDemo`、區隔內容。 在此範例中 `mac` 是組織首碼， `aodpremium` 是組織ID。

根據使用者的組織和ID，此限定路徑會顯示在AEM Assets介面和各種精靈中，包括「移動」和「程式碼片段建立」精靈，以強制進行區隔。

透過多租賃功能，您可以劃分下列資產和元件類型：

* 集合
* 公開系列
* 目錄（包括「新增／選擇頁面」精靈）
* 範本
* 程式碼片段範本
* 燈箱

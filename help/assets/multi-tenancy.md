---
title: 適用於系列、程式碼片段和程式碼片段範本的多租用功能
description: 根據客戶組織隔離CRX儲存庫中的內容，以防止未經授權的訪問。
contentOwner: AG
feature: Collections
role: Architect,Administrator,Leader
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 1%

---


# 系列、程式碼片段和程式碼片段範本的多租賃{#multi-tenancy-for-collections-snippets-and-snippet-templates}

多租賃功能可讓您根據組織首碼和組織ID，在CRX中區隔內容，以保護內容不受其他組織使用者未經授權的存取。

Adobe Experience Manager(AEM)資產會將每個組織的資料儲存在不同的路徑中。 每個組織特定路徑都由組織首碼和組織ID來識別。
它包含在CRX中儲存不同類型資產的傳統位置。

例如，如果您建立名為`Demo`的檔案夾，AEM預設會將檔案夾儲存在CRX的`../content/dam/Demo`位置。 啟用多租賃功能後，您可以在`../content/dam/<organization prefix>/<organization id>Demo`中儲存資料。

例如，對於指派給`aodpremium`組織的Adobe Marketing CloudAEM Assets（隨選）用戶，您可以使用多租賃功能來配置到`../content/dam/mac/aodpremiumDemo`的下列路徑，並分隔內容。 在此範例中，`mac`是組織首碼，`aodpremium`是組織ID。

根據使用者的組織和ID，此合格路徑會顯示在AEM Assets介面和各種精靈中，包括「移動」和「程式碼片段」建立精靈，以執行區段。

透過多租賃功能，您可以劃分下列資產和元件類型：

* 集合
* 公開系列
* 目錄（包括「新增／選擇頁面」精靈）
* 範本
* 程式碼片段範本
* 燈箱

---
title: 集合、片段和程式碼片段範本的多租用戶
description: 根據客戶組織隔離CRX存放庫中的內容，以防止未經授權的存取。
contentOwner: AG
feature: 集合
role: Architect,Admin,Leader
exl-id: d00a671a-6707-4941-868d-fa13510b7b60
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 1%

---

# 集合、片段和程式碼片段範本的多租用戶 {#multi-tenancy-for-collections-snippets-and-snippet-templates}

多租用戶功能可讓您根據組織首碼和組織ID來分隔CRX中的內容，以保護內容不會受到其他組織的使用者未經授權的存取。

Adobe Experience Manager(AEM)Assets會以不同路徑儲存每個組織的資料。 每個組織特定路徑都由組織首碼和組織ID識別。
包含在CRX中儲存不同資產類型的傳統位置。

例如，如果您建立名為`Demo`的資料夾，AEM資產預設會將資料夾儲存在CRX中的`../content/dam/Demo`位置。 啟用多租用戶功能後，您可以在`../content/dam/<organization prefix>/<organization id>Demo`儲存資料。

例如，對於指派給`aodpremium`組織的AEM Assets的Adobe Marketing Cloud使用者（隨選），您可以使用多租用戶功能，將下列路徑設為`../content/dam/mac/aodpremiumDemo`，並區隔內容。 在此範例中，`mac`是組織首碼，而`aodpremium`是組織ID。

根據使用者的組織和ID，此合格路徑會顯示在AEM Assets介面和各種精靈中，包括執行分段的移動和程式碼片段建立精靈。

多租用戶功能可讓您劃分下列資產和元件類型：

* 集合
* 公用集合
* 目錄（包括「添加/選擇頁面」嚮導）
* 範本
* 程式碼片段範本
* Lightbox

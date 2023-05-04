---
title: 集合、片段和程式碼片段範本的多租用戶
description: 根據客戶組織隔離CRX存放庫中的內容，以防止未經授權的存取。
contentOwner: AG
feature: Collections
role: Architect,Admin,Leader
exl-id: d00a671a-6707-4941-868d-fa13510b7b60
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 2%

---

# 集合、片段和程式碼片段範本的多租用戶 {#multi-tenancy-for-collections-snippets-and-snippet-templates}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

多租用戶功能可讓您根據組織首碼和組織ID來分隔CRX中的內容，以保護內容不會受到其他組織的使用者未經授權的存取。

Adobe Experience Manager(AEM)Assets會以不同路徑儲存每個組織的資料。 每個組織特定路徑都由組織首碼和組織ID識別。
包含在CRX中儲存不同資產類型的傳統位置。

例如，若您建立的資料夾名稱為 `Demo`, AEM資產預設會儲存資料夾於 `../content/dam/Demo` CRX中的位置。 啟用多租用戶功能後，您可以將資料儲存在 `../content/dam/<organization prefix>/<organization id>Demo`.

例如，針對指派給的AEM Assets的Adobe Marketing Cloud使用者（隨選） `aodpremium` 組織，您可以使用多租用者功能，設定以下路徑至 `../content/dam/mac/aodpremiumDemo`，分隔內容。 在此範例中 `mac` 是組織首碼和 `aodpremium` 是組織ID。

根據使用者的組織和ID，此合格路徑會顯示在AEM Assets介面和各種精靈中，包括執行分段的移動和程式碼片段建立精靈。

多租用戶功能可讓您劃分下列資產和元件類型：

* 集合
* 公用集合
* 目錄（包括「添加/選擇頁面」嚮導）
* 範本
* 程式碼片段範本
* Lightbox

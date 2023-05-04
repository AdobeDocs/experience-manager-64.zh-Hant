---
title: 為Microsoft SharePoint配置連接器
seo-title: Configuring Connector for Microsoft SharePoint
description: 設定Microsoft SharePoint的Connector ，以啟用AEM表單與Microsoft SharePoint之間的通訊。
seo-description: Configure Connector for Microsoft SharePoint to enable communication between AEM forms and Microsoft SharePoint.
uuid: f1561b41-da20-4220-b13a-e78472a9449f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 0ec881c9-8dcc-4847-9edf-24d9e6c4a7ea
exl-id: 9bd396a3-5da9-4355-ad76-e7132ac8aed8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 3%

---

# 為Microsoft SharePoint配置連接器 {#configuring-connector-for-microsoft-sharepoint}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Microsoft SharePoint的Connector可啟用AEM表單與Microsoft SharePoint之間的通訊。 如需其他背景資訊，請參閱 [服務參考](https://www.adobe.com/go/learn_aemforms_services_63).

1. 在管理控制台中，按一下「服務>Microsoft SharePoint的連接器」 。
1. 為您的SharePoint伺服器指定下列設定：

   **SharePoint伺服器主機名：** SharePoint伺服器上Web應用程式的主機名埠號，格式為 `[hostname]:[port]`.

   **用戶名：** 用來連線至SharePoint伺服器的使用者帳戶。

   **密碼：** 用來連線至SharePoint伺服器的使用者帳戶密碼

   **域名：** SharePoint伺服器所在的網域。

1. 按一下「儲存」。

## Microsoft SharePoint設定服務 {#microsoft-sharepoint-configuration-service}

Microsoft SharePoint設定服務 `(MSSharePointConfigService)` 可讓您指定具有模擬權限的AEM forms使用者的認證。 有關模擬權限的資訊，請參見 [為Microsoft SharePoint配置連接器](https://help.adobe.com/en_US/AEMForms/6.1/SharePointConfig/index.html). 請依照下列步驟，指定 `MSSharePointConfigService`:

1. 在管理控制台中，按一下「服務」>「應用程式和服務」>「服務管理」。
1. 導覽服務清單，然後按一下 `MSSharePointConfigService`.
1. 在「設定」頁面上指定下列設定：

   * 具有模擬權限的用戶的用戶名
   * 上述用戶的密碼

1. 按一下「儲存」。

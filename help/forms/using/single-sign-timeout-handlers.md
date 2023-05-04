---
title: 單一登入和逾時處理常式
seo-title: Single Sign On and timeout handlers
description: 如何設定AEM Forms工作區的工作階段逾時值。
seo-description: How-to set the session timeout value for AEM Forms workspace.
uuid: 17583fd5-6453-41d3-bb63-a639983fbea9
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 698990a2-dd3f-480f-9d15-d87563860297
exl-id: eb7afdd3-0901-4dfb-b23c-88c46b5a4fb5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 2%

---

# 單一登入和逾時處理常式 {#single-sign-on-and-timeout-handlers}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

AEM Forms工作區已啟用SSO。 如果使用者已登入AEM Forms應用程式(例如Forms Manager或PDF產生器使用者介面)，並在相同的瀏覽器工作階段中存取AEM Forms工作區，則使用者會登入AEM Forms工作區，反之亦然。

## 在AEM Forms工作區中處理伺服器逾時 {#handling-server-timeout-in-nbsp-aem-forms-workspace}

可在管理控制台中設定使用者的工作階段逾時。

若要設定逾時，請登入 `https://[server]:[port]/adminui`，導覽至 **「設定」>「用戶管理」>「配置」>「配置高級系統屬性」**，並進行所需的設定。

在AEM Forms工作區中，逾時的處理方式為：

* 使用者的工作階段期間可用於回應 `initialize` 調用以初始化用戶會話。
* 彈出式對話方塊會通知使用者工作階段即將到期，也就是工作階段到期的15秒。

在此快顯對話方塊中：

* 按一下「確定」結束用戶會話。
* 按一下取消以重新初始化用戶會話。

>[!NOTE]
>
>若未採取任何動作，系統會在工作階段過期前三秒自動將使用者登出AEM Forms工作區。

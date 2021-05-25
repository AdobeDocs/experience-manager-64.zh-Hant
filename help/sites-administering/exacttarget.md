---
title: 與ExactTarget整合
seo-title: 與ExactTarget整合
description: 了解如何將AEM與ExactTarget整合。
seo-description: 了解如何將AEM與ExactTarget整合。
uuid: dafa0a1a-2d1e-40fc-a729-f2ce7ebc7807
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: d1cff2bb-9fdf-49cb-a695-d437bba5653d
exl-id: 943e5199-271f-4015-a9f7-4d39c00deabe
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# 與ExactTarget整合{#integrating-with-exacttarget}

將AEM與Exact Target整合可讓您透過Exact Target管理並傳送在AEM中建立的電子郵件。 它也可讓您透過AEM頁面上的AEM表單，使用Exact Target的銷售機會管理功能。

整合提供下列功能：

* 可在AEM中建立電子郵件，並發佈至Exact Target進行分送。
* 設定AEM表單動作以建立「精確目標」訂閱者的功能。

設定ExactTarget後，您就可以將電子報或電子郵件發佈至ExactTarget。 請參閱[將電子郵件發佈至電子郵件服務](/help/sites-authoring/personalization.md)。

## 建立ExactTarget配置{#creating-an-exacttarget-configuration}

ExactTarget設定可透過雲端服務或工具新增。 本節將說明兩種方法。

### 透過Cloudservices {#configuring-exacttarget-via-cloudservices}設定ExactTarget

若要在Cloud Services中建立ExactTarget設定：

1. 在歡迎頁面上，按一下&#x200B;**Cloud Services**。 （或直接訪問`https://<hostname>:<port>/etc/cloudservices.html`。）
1. 按一下&#x200B;**ExactTarget**，然後按一下&#x200B;**Configure**。 「ExactTarget」設定視窗隨即開啟。

   ![chlimage_1-182](assets/chlimage_1-182.png)

1. 輸入標題和名稱（可選），然後按一下「**Create**」。 ** ExactTarget設定**配置窗口開啟。

   ![chlimage_1-31](assets/chlimage_1-31.jpeg)

1. 輸入使用者名稱、密碼並選取API端點(例如&#x200B;**https://webservice.exacttarget.com/Service.asmx**)。
1. 按一下「**連線至ExactTarget」。** 成功連線後，您會看到成功對話方塊。按一下&#x200B;**OK**&#x200B;退出窗口。

   ![chlimage_1-32](assets/chlimage_1-32.jpeg)

1. 選擇帳戶（如果可用）。 帳戶適用於Enterprise 2.0客戶。 按一下&#x200B;**「確定」**。

   ExactTarget已設定。 您可以按一下「**編輯**」來編輯配置。 您可以按一下&#x200B;**前往ExactTarget**&#x200B;來前往ExactTarget。

1. AEM現在提供資料擴充功能。 您可以匯入ExactTarget資料擴充功能欄。 除了成功建立ExactTarget設定外，按一下出現的「+」符號即可進行設定。 您可以從下拉式清單中選取任何現有的資料擴充功能。 如需如何設定資料擴充功能的詳細資訊，請參閱[ExactTarget檔案](https://help.exacttarget.com/en/documentation/exacttarget/subscribers/data_extensions_and_data_relationships)。

   匯入的資料擴充功能欄稍後可透過&#x200B;**文字和個人化**&#x200B;元件使用。

   ![chlimage_1-33](assets/chlimage_1-33.jpeg)

### 透過工具{#configuring-exacttarget-via-tools}設定ExactTarget

若要在工具中建立ExactTarget設定：

1. 在歡迎頁面上，按一下&#x200B;**工具**。 或直接前往`https://<hostname>:<port>/misadmin#/etc`導覽至該處。
1. 選擇&#x200B;**工具**，然後選擇&#x200B;**Cloud Services配置，**&#x200B;然後選擇&#x200B;**ExactTarget**。
1. 按一下&#x200B;**New**&#x200B;以開啟**建立頁面**視窗。

   ![chlimage_1-34](assets/chlimage_1-34.jpeg)

1. 輸入&#x200B;**Title**&#x200B;和（可選）**Name**，然後按一下&#x200B;**Create**。
1. 按上一步步驟4所述輸入配置資訊。 請依照該程式完成ExactTarget的設定。

### 添加多個配置{#adding-multiple-configurations}

若要新增多個設定：

1. 在歡迎頁面上，按一下&#x200B;**Cloud Services**，然後按一下&#x200B;**ExactTarget**。 按一下&#x200B;**顯示配置**&#x200B;按鈕，如果有一個或多個ExactTarget配置可用，該按鈕將出現。 列出所有可用的配置。
1. 按一下「可用配置」旁的&#x200B;**+**&#x200B;符號。 這將開啟&#x200B;**建立配置**&#x200B;窗口。 請依照先前的配置過程建立新配置。

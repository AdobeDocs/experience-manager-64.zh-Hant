---
title: 發佈AEM Forms應用程式
seo-title: Distribute AEM Forms app
description: 使用移動設備管理(MDM)在移動設備上大規模部署應用。
seo-description: Use Mobile Device Management (MDM) for the large-scale deployment of apps on mobile devices.
uuid: 8a2ce42b-5e9b-42c1-a945-c069f6152f6e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 5756cb52-dd47-4277-981c-fd0af9a20638
exl-id: c1bf0a0e-70f7-41dd-8b1a-c114d89a265b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 1%

---

# 發佈AEM Forms應用程式 {#distribute-aem-forms-app}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

移動設備管理(MDM)支援在移動設備上大規模部署應用。

>[!NOTE]
>
>此分送僅適用於iOS和Android裝置。

## MDM解決方案通常提供的主要功能： {#main-features-generally-provided-by-mdm-solutions}

* 在企業環境中啟用設備註冊
* 允許配置和更新設備設定
* 強制遵守安全性。
* 對公司資源的安全移動訪問

MDM解決方案與移動應用管理一起，允許您管理企業內的移動設備上的內部、公共和購買的應用。

MDM管理員可將ipa和apk檔案上載到MDM伺服器，並控制可訪問ipa或apk檔案的用戶。 管理員也可以控制與每個應用程式對應的設定檔設定。

## 影響AEM Forms應用程式的設定檔設定 {#profile-settings-affecting-the-aem-forms-app-br}

裝置上的下列設定檔設定將影響裝置上AEM Forms應用程式的運作：

* **允許使用相機** 在 **裝置功能** 節

如果禁用 **允許使用相機**，此 [照片注釋](/help/forms/using/add-attachments.md) 將無法運作。 您必須啟用此選項，才能在應用程式中使用相機。

* **需要設備上的密碼** 在「密碼策略」部分

啟用 **應用程式資料加密**，建議您啟用 **密碼** 在您的裝置上。 如果未在設備上設定密碼，則儲存在設備上的應用程式資料不會加密。

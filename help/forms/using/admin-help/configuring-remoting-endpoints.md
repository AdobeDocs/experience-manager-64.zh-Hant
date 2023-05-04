---
title: 配置遠程處理端點
seo-title: Configuring Remoting endpoints
description: 了解如何配置遠程端點。
seo-description: Learn how to configure remoting endpoints.
uuid: 4d4f9274-dcae-4b9f-975a-575376c2f89c
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: aab9d622-d76b-4100-9ca6-e5b86f543381
exl-id: d8e31f99-0558-4634-ae35-f4a09f34ad6d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

---

# 配置遠程處理端點 {#configuring-remoting-endpoints}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

遠端端點可讓使用Flex建置的應用程式，使用(AEM forms遭取代)AEM forms Remoting叫用服務。 系統會自動為每個已激活的服務建立遠程端點。 建立與端點同名的Flex目的地，Flex用戶端可建立指向此目的地的遠端物件，以叫用相關服務上的作業。

## 遠程處理端點設定 {#remoting-endpoint-settings}

**Flex用戶端驗證方法：** 確定當調用的服務啟用安全性時，伺服器向客戶端發送的響應類型，調用的操作不支援匿名調用，並且客戶端傳入的憑據不是或無效。

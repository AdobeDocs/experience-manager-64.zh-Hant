---
title: 為AEM應用程式進行配置
seo-title: Configuring for AEM Apps
description: 了解如何設定AEM應用程式。
seo-description: Learn how to configure AEM Apps.
uuid: ab9acd93-da7f-4bb7-8d26-224044899068
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 34f24837-f5e2-41f0-a359-fdb695e1b8f2
exl-id: 593a588c-02f1-4b48-ac57-9348d6652bcc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 3%

---

# 為AEM應用程式進行配置{#configuring-for-aem-apps}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager應用程式可透過空中(OTA)更新應用程式的內容。 更新的內容會儲存在發佈執行個體上。 若要允許裝置上的應用程式連線至發佈執行個體並檢查是否有更新，必須將發佈執行個體設定為允許空的反向連結標題。

## 設定空的反向連結標題 {#configuring-empty-referrer-header}

若要設定反向連結篩選服務：

* 開啟Apache Felix主控台(**配置**):
* https://&lt;server>:&lt;port_number>/system/console/configMgr
* 以管理員身分登入。
* 在 **配置** 菜單，選擇 *Apache Sling反向連結篩選器*
* 勾選「允許空白」欄位，以允許空白/遺失的反向連結標題。
* 按一下 **儲存** 來儲存變更。

![chlimage_1-58](assets/chlimage_1-58.png)

請參閱 [OSGI組態設定](/help/sites-deploying/osgi-configuration-settings.md) 和 [安全性檢查清單 — 跨網站請求偽造問題](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) 以取得詳細資訊。

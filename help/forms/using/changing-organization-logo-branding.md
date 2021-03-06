---
title: 更改組織標識以用於品牌
seo-title: 更改組織標識以用於品牌
description: 若要品牌化AEM Forms工作區，請自訂預設標誌，以提供貴組織的標誌。
seo-description: 若要品牌化AEM Forms工作區，請自訂預設標誌，以提供貴組織的標誌。
uuid: f0c340ee-2e54-4bb0-9c30-383cc1bbadb8
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 2c651302-f4ef-4211-b897-f5942ed0ffb1
exl-id: 890e98af-0491-4b59-9a9b-6c245db54f0f
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# 更改品牌{#changing-the-organization-logo-for-branding}的組織徽標

組織標誌會顯示在AEM Forms工作區的左上角。 若要更新標誌，請遵循AEM Forms工作區自訂的[一般步驟](/help/forms/using/generic-steps-html-workspace-customization.md#generic-steps-for-html-workspace-customization)，然後遵循下列步驟。

1. 建立標誌並將檔案命名為`NewWorkspace.png`。 使用WebDAV客戶端將影像檔案放置在/apps/ws/images資料夾中。

   >[!NOTE]
   >
   >標誌影像的建議大小為218 px × 20 px。

   >[!NOTE]
   >
   >有關WebDAV訪問的詳細資訊，請參閱[https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html)。

1. 通過添加以下樣式，在/apps/ws/css/newStyle.css中參考樣式表中的新徽標影像。

   ```css
   #logo {
   
          background: url(../images/NewWorkspace.png) no-repeat 14px 11px; 
         }
   ```

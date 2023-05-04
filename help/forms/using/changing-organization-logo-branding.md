---
title: 更改組織標識以用於品牌
seo-title: Changing the organization logo for branding
description: 若要品牌化AEM Forms工作區，請自訂預設標誌，以提供貴組織的標誌。
seo-description: To brand AEM Forms workspace provide the logo of your organization by customizing the default logo.
uuid: f0c340ee-2e54-4bb0-9c30-383cc1bbadb8
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 2c651302-f4ef-4211-b897-f5942ed0ffb1
exl-id: 890e98af-0491-4b59-9a9b-6c245db54f0f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 2%

---

# 更改組織標識以用於品牌 {#changing-the-organization-logo-for-branding}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

組織標誌會顯示在AEM Forms工作區的左上角。 若要更新標誌，請遵循 [AEM Forms工作區自訂的一般步驟](/help/forms/using/generic-steps-html-workspace-customization.md#generic-steps-for-html-workspace-customization) 然後執行下列步驟。

1. 建立標誌並將檔案命名為 `NewWorkspace.png`. 使用WebDAV客戶端將影像檔案放置在/apps/ws/images資料夾中。

   >[!NOTE]
   >
   >標誌影像的建議大小為218 px × 20 px。

   >[!NOTE]
   >
   >有關WebDAV訪問的詳細資訊，請參見 [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html).

1. 通過添加以下樣式，在/apps/ws/css/newStyle.css中參考樣式表中的新徽標影像。

   ```css
   #logo {
   
          background: url(../images/NewWorkspace.png) no-repeat 14px 11px; 
         }
   ```

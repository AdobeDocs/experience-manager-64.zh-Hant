---
title: 更新檔案的連結
seo-title: Updating the link to the documentation
description: 如何更新AEM Forms工作區中工作區說明連結的目的地，以指向您的自訂檔案連結。
seo-description: How-to update the destination of Workspace Help link in AEM Forms workspace to point to your custom documentation link.
uuid: 64056d10-1451-44ed-8f25-81a21037dc75
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 788c427f-190f-4580-9efd-6a4c4a008837
exl-id: 68fe3f97-ded8-4223-b4b9-02704077e37e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 5%

---

# 更新檔案的連結 {#updating-the-link-to-the-documentation}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

您可以選取 **說明>工作區說明**. 它指向Adobe網站上的線上文檔。 不過，您可以更新它以指向任何其他URL。

請考量下列使用案例，其中您可能想要變更預設說明URL:

* 以您所選擇的語言提供本地化說明。
* 為您的自訂工作區提供自訂說明內容。

要更新聯機文檔的URL，請遵循 [自訂的一般步驟](/help/forms/using/generic-steps-html-workspace-customization.md) 然後執行下列步驟。

1. 複製 `userinfo.html` 檔案 `/libs/ws/js/runtime/templates` to `/apps/ws/js/runtime/templates`.
1. 變更：

   ```
   <ul class="helpmenu">
     <li>            
       <a href="https://www.adobe.com/go/learn_aemforms_documentation_63" title="<%= $.t('index.header.dropdown.WorkspaceHelp')%>" target="_blank"><%= $.t('index.header.dropdown.WorkspaceHelp')%></a>
     </li>
   ```

   至

   ```
   <ul class="helpmenu">
     <li>            
       <a href="<!--place new help url here-->" title="<%= $.t('index.header.dropdown.WorkspaceHelp')%>" target="_blank"><%= $.t('index.header.dropdown.WorkspaceHelp')%></a>
     </li>
   ```

1. 請執行下列動作：

   1. 開啟/apps/ws/js/registry.js進行編輯。
   1. 搜尋和取代 `text!/lc/libs/ws/js/runtime/templates/userinfo.html` with `text!/lc/apps/ws/js/runtime/templates/userinfo.html`.

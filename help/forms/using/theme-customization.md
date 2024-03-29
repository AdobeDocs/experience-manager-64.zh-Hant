---
title: 主題自訂
seo-title: Theme Customization
description: 如何自訂AEM Forms應用程式的主題。
seo-description: How to customize the theme of your AEM Forms app.
uuid: 36632e67-1cc6-416d-ae80-d84bbabab4bd
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: c72f608e-052a-4bf9-b7bc-ddf57483af35
exl-id: fb1e0bec-c943-4468-920d-8ef360a01365
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 2%

---

# 主題自訂 {#theme-customization}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

您可以自訂HTML程式碼和CSS檔案，為AEM Forms應用程式提供獨特的組織專屬外觀和風格。 例如，您可以更改任務或起始點的背景顏色和高度。 下列範例提供變更的指示：

* 顯示說明以取代說明
* 顯示路由數
* 背景漸層顏色

## 步驟 {#steps}

1. 開啟您的專案。

   * iOS，開啟 `Capture.xcodeproj` 在Xcode中
   * 若為Android，請在Eclipse中開啟Android專案。
   * 對於Windows，請開啟 `MWSWindows.sln` 在Visual Studio。

1. 導覽至範本資料夾。

   * 在Xcode中，導覽至 **擷取> www > wsmobile > js >執行階段>範本** 檔案夾。
   * 在Eclipse中，導覽至 **「資產」 > 「www」 > 「js」 > 「執行階段」** 檔案夾。
   * 在Visual Studio中，導覽至 **MWSwindows > www > wsmobile > js > runtime >範本** 檔案夾。

1. 開啟 `template.html` 檔案進行編輯。
1. 找出下列字串：

   ```
   <%if ( (task.description !== "") && (task.description !== null) && (typeof task.description !== null) && (typeof task.description !== 'undefined') ) {%>
                  <div class="description_details">
                    <%= task.description %>
                  </div>
                 <%} else 
   ```

   替換為 `<%`.

1. 在 `template.html` 檔案：

   ```
   <ul id="task_menu_list">
                                   <li class="approve" title="<%= task.availableCommands.directCommands[0]%>" data-routename="<%= task.availableCommands.directCommands[0]%>">
                                       <%= task.availableCommands.directCommands[0]%>
                                   </li>
                                   <li class="reject last" title="<%= task.availableCommands.directCommands[1]%>" data-routename="<%= task.availableCommands.directCommands[1]%>">
                                       <%= task.availableCommands.directCommands[1]%>
                                   </li>
   ```

1. 對下一行加上註解並儲存檔案。

   ```
   task.availableCommands.directCommands[1]%>">
   <%= task.availableCommands.directCommands[1]%>
   </li>
   ```

1. 導覽至CSS資料夾。

   * 在Xcode中，導覽至 **Capture > www > wsmobile > css**.
   * 在Eclipse中，導覽至 **assets > www > wsmobile > css**.
   * 在Visual Studio中，導航至 **MWSWindows > www > wsmobile > css**.

1. 開啟 `_style.css` 檔案進行編輯。
1. 若為背景影像，請變更 `#323232` to `#fff`.
1. 儲存變更並關閉 `_style.css` 檔案。
1. 開啟AEM Forms應用程式。

   AEM Forms應用程式現在會顯示指示，而非說明。

---
title: 更改介面的顏色配置
seo-title: Changing the color scheme of the interface
description: 如何選擇性修改AEM Forms工作區使用者介面部分的色彩配置。
seo-description: How to modify the color scheme of AEM Forms workspace user interface portions selectively.
uuid: 32c32f7a-8271-4d2c-8a1f-ad5ab3c90b83
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 18dab82a-badf-4c32-83a2-cd5cb04cae89
exl-id: efbb9a9e-0ddf-49f2-bcb8-14cd0c6de5ee
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 1%

---

# 更改介面的顏色配置 {#changing-the-color-scheme-of-the-interface}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

您可以修改AEM Forms工作區使用者介面部分的色彩配置，以符合您的需求。 以下是一些代表性色彩配置自訂的範例。 除了本文討論的步驟外，請參閱 [AEM Forms工作區自訂的一般步驟](/help/forms/using/generic-steps-html-workspace-customization.md).

## 頂端導覽列 {#top-navigation-bar}

### 使用背景影像 {#using-background-image}

更新AEM Forms工作區頂端的導覽列。

1. 建立背景影像以更新顏色。 將檔案命名為newBackground.jpg。
1. 使用WebDAV客戶端上載/apps/ws/images資料夾中的背景影像檔案。

   >[!NOTE]
   >
   >有關WebDAV訪問的詳細資訊，請參見 [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html).

1. 在/apps/ws/css/newStyle.css中新增下列樣式，以參考新的背景影像。

   ```css
   #header {
       background:#292929 url(../images/newBackground.jpg) repeat-x;
   }
   ```

### 在CSS中使用color屬性 {#using-color-property-in-css}

1. 在newStyle.css中，在/apps/ws/css中新增下列樣式

   ```css
   #header {
   background : none;
   background-color: gray;
   }
   ```

## 類別元件 {#category-component}

類別元件會在左側面板中顯示您的工作的各種類別。 若要變更其顏色，請在 `.category` 元素。

## 任務元件 {#task-component}

任務顯示在名為TaskList Component的中間面板中。 要更改其顏色，請修改與樣式表中的.task選擇器關聯的樣式。

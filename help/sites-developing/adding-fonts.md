---
title: 為圖形渲染添加字型
seo-title: Adding Fonts for Graphic-Rendering
description: AEM可讓您產生圖形，並納入從內容動態擷取的文字
seo-description: AEM allows you to generate graphics incorporating text dynamically taken from your content
uuid: 67d9b10f-e986-4d29-bde2-10e08075fe17
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 6af48ef5-75e6-4b66-bc0d-ecf254b1c4ef
exl-id: f29868e3-d05c-4898-94d1-0c77ab6b72eb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 2%

---

# 為圖形渲染添加字型{#adding-fonts-for-graphic-rendering}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

AEM可讓您產生圖形，並納入從內容動態擷取的文字。

要執行此操作，您也可以載入並使用您自己的字型。

目前所有Java平台實作都支援 [TrueType](https://en.wikipedia.org/wiki/Truetype) 字型。

1. 開啟CRXDE Lite並導覽至您的專案應用程式資料夾：

   `/apps/<your-project>/`

1. 在 `/apps/<your-project>/` 建立新節點：

   * **名稱**: `fonts`
   * **類型**: `sling:Folder`

   儲存所有變更。

1. 將字型檔案複製到此資料夾中；例如，使用WebDAV。

   >[!NOTE]
   >
   >儲存庫中的字型檔案必須有尾碼 `*.ttf` 或 `*.TTF`.

1. 更新 [OSGi配置](/help/sites-deploying/configuring-osgi.md) of [Day Commons GFX字型幫助程式](/help/sites-deploying/osgi-configuration-settings.md). 將路徑添加到字型資料夾；即。 `/apps/<your-project>/fonts`.

1. 返回CRXDE Lite。 您現在應該會看到 `.fontlist` 資料夾中包含匯入字型名稱的節點。

   這些字型現在已可用於Java API。

如需如何將字型與Java API搭配使用的完整詳細資訊，請參閱 [Java API的字型類別檔案](https://download.oracle.com/javase/6/docs/api/java/awt/Font.html).

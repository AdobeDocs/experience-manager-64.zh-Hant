---
title: 比較AEM Assets和AEM Media Library中的可用功能
description: AEM Assets和AEM Media Library的常見問題，包括差異。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 6a1013715c538c39eaf40a22dbffc7f2df36f968
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---


# AEM Assets與AEM MediaLibrary {#aem-assets-vs-aem-medialibrary}

Adobe Experience Manager(AEM)Assets是AEM平台不可或缺的一部分。 此順暢整合被視為AEM的主要優點，可確保內容管理的一致性，並提高內容作者的生產力。

## 常見問題 {#frequently-asked-questions}

### 什麼是AEM Assets?{#what-is-aem-assets}

AEM Assets是AEM Platform上的應用程式，可讓我們的客戶在網路儲存庫中管理其數位資產（影像、視訊、檔案和音訊片段）。 AEM Assets包含中繼資料支援、轉譯、Digital Asset Management Finder和AEM Assets Administration UI。

### 什麼是AEM Media Library?{#what-is-the-aem-media-library}

AEM Media Library是AEM WCM內容存放庫的指定部分，影像和其他共用資源都會儲存在此處。 「媒體庫」使用AEM WCM的「數位資產管理」功能。

### 我可從不屬於AEM WCM的AEM Assets獲得哪些資訊？{#what-do-i-get-from-aem-assets-that-is-not-part-of-aem-wcm}

AEM Assets客戶僅能使用的獨特功能包括：

1. 擷取和編輯除標題、標籤和說明以外之中繼資料的能力。
1. 「AEM資產管理員」，可從歡迎畫面按一下`siteadmin`旁的第二個按鈕，即可使用。
1. 所有與「數位資產管理」相關的工作流程步驟，即AEM資產擷取、AEM資產刪除、AEM資產子資產處理、AEM資產中繼資料擷取。
1. 庫，包括`dam` im包空間。

使用這些功能需要有效的AEM Assets授權。

### AEM Assets是否可以個別套件使用？{#is-aem-assets-available-as-a-separate-package}

否. 為方便安裝和部署，所有AEM應用程式和附加元件都以單一套件形式提供，並包含所有功能。 這並不表示您擁有使用套件中所有功能的權限。

#### 我想編輯數位資產的中繼資料。 我需要AEM資產嗎？{#i-want-to-edit-metadata-of-digital-assets-do-i-need-aem-assets}

如果您打算編輯除標題、說明和標籤以外的中繼資料，則必須取得AEM Assets的授權。

#### 我想在匯入時自動調整影像大小。 我需要AEM資產嗎？{#i-want-to-automatically-resize-images-upon-import-do-i-need-aem-assets}

否. AEM媒體庫包含調整靜態影像大小和自動工作流程導向轉換功能以及管理轉譯的功能。 這些功能不需要AEM Assets授權。

### 我想使用自訂的影像元件來調整影像大小。 我需要AEM資產嗎？{#i-want-to-resize-images-using-a-customized-image-component-do-i-need-aem-assets}

影像元件是AEM WCM的一部分。 影像元件（但也由AEM Assets）使用的圖形庫是AEM平台的一部分，不需要AEM Assets授權。

### 如果我未授權AEM Assets，該如何防止使用者使用AEM Assets?{#how-can-i-prevent-my-users-from-using-aem-assets-if-i-did-not-license-aem-assets}

您可以從AEM移除所有AEM Assets專屬的工作流程、元件、分類、選項和AEM Assets管理員。 如此可避免使用者意外使用您未授權的AEM Assets功能。

### 我想要將影像新增至頁面，並想要裁切這些影像並調整其大小。 我需要AEM資產嗎？{#i-want-to-add-images-to-a-page-and-want-to-crop-and-resize-these-images-do-i-need-aem-assets}

在此使用案例中，您不需要購買AEM Assets，即使使用媒體程式庫也不需要在網站上使用影像，因為智慧型影像元件可讓您直接上傳影像至頁面。

>[!MORELIKETHIS]
>
>* [功能差異的詳細清單](https://docs.adobe.com/content/help/en/experience-manager-65/assets/administer/medialibrary.html#listoffeatures)


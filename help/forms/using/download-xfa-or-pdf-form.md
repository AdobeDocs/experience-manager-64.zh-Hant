---
title: 下載XFA或PDF表單範本
seo-title: Download an XFA or a PDF form template
description: 您可以將表單從存放庫匯出至本機系統，並將下載的表單移轉至新存放庫。
seo-description: You can export forms from the repository to the local system and migrate the downloaded forms to new repository.
uuid: 5f7fbd14-cb9d-4749-8708-7efe49df89d7
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: 6699e0e7-fd42-41ae-86a2-3b940d905111
role: Admin
exl-id: 68d881c6-7507-4018-b40e-205604221d0c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 1%

---

# 下載XFA或PDF表單範本 {#download-an-xfa-or-a-pdf-form-template}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

如名稱所示，下載操作可讓您將表單從存放庫匯出至本機系統。 結合上傳操作，此操作可協助您將表單從一個存放庫移轉至另一個存放庫。

在AEM Forms中，下列資產類型支援下載操作：

* 表單範本(XFA Forms)
* PDF forms
* 文檔(一般PDF檔案)

AEM Forms支援個別或在包含一或多個支援表單的資料夾中下載這些表單類型。

除了這些資產，您還可以下載 `Resource` 資產類型（如果資產存在於資料夾中）。 本功能可讓您下載XFA表單所參考的資源及表單。

## 下載一或多個表單 {#download-one-or-more-forms}

1. 登入AEM Forms使用者介面： `https://<server>:<port>/aem/forms.html`.

1. 導覽至您要下載的資產位置。

1. 選取資產。 按一下 **[!UICONTROL 下載]** ![aem6forms_download](assets/aem6forms_download.png) 圖示。

   >[!NOTE]
   >
   >您只能選擇一個表單進行下載。 如果要下載多份表單，您必須將其下載為資料夾。

1. 在出現的對話方塊中，按一下 **[!UICONTROL 下載]**.

   AEM Forms會產生包含所選檔案或所選資料夾的ZIP檔案。

   如果您要下載資料夾，資料夾內支援的資產會以其現有階層下載。

   ZIP檔案會儲存至 `Downloads` 資料夾。

## 上傳作業的相關考量事項 {#related-considerations-for-the-upload-operation}

* 您可以將ZIP檔案上傳至相同存放庫或其他存放庫中的任何其他位置
* 上傳作業期間會保留資料夾中資產的階層
* 下載前對下載的資產所做的任何中繼資料變更，都會在上傳時反映

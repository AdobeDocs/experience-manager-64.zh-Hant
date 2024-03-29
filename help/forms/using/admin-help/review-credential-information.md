---
title: 查看憑據使用資訊
seo-title: Review credential use information
description: 了解如何查看憑據使用資訊。
seo-description: Learn how to review credential use information.
uuid: 02af75f9-c235-470d-a98b-a2102aa31381
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: cdf61cff-768b-49f7-9926-400bc96b0708
exl-id: abd62cca-edf0-4b44-94c3-7af3116b0c54
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 2%

---

# 查看憑據使用資訊 {#review-credential-use-information}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

憑證包含的資訊說明其預期用途，可透過Acrobat Reader DC擴充功能一般使用者Web應用程式存取。 您可以使用此資訊來確定安裝的憑據類型（評估或生產）及其有效日期。

1. 開啟Web瀏覽器並輸入此URL:

   http://localhost網站：*[埠]*/ReaderExtensions(其中 *[埠]* 是應用程式伺服器的埠號)

1. 使用預設用戶名和密碼登錄：

   用戶名：管理員

   密碼：密碼

   >[!NOTE]
   >
   >您必須擁有管理員或超級用戶權限才能使用預設用戶名和密碼登錄。 若要允許其他使用者存取Acrobat Reader DC擴充功能，請在「使用者管理」中建立使用者帳戶，並授與使用者Acrobat Reader DC擴充功能Web應用程式角色。

1. 從「選擇憑據」清單中選擇憑據別名，並複查「到期日」和「預定使用通知」中包含的資訊。

>[!NOTE]
>
>憑據的到期日也可在管理控制台的「設定」>「信任儲存管理」>「本地憑據」頁的「到期日」下。

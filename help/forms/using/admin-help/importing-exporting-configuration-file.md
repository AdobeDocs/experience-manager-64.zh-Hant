---
title: 匯入和匯出設定檔
seo-title: Importing and exporting the configuration file
description: 了解如何匯入和匯出設定檔，以編輯伺服器偏好設定或設定其他AEM表單產品例項。
seo-description: Learn how to import and export the configuration file in order to edit server preferences or configure another AEM forms product instance.
uuid: 32e8a709-2d7c-4740-9533-d53aa751bc58
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: c1636537-f7dc-48d8-a3f0-9052bcd28b62
exl-id: dbad776a-60fd-4fcc-ba2a-a2f379f5462c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 1%

---

# 匯入和匯出設定檔 {#importing-and-exporting-the-configuration-file}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

使用「手動配置」頁可以下載XML格式的配置設定副本。 此檔案中的設定控制所有伺服器首選項。 然後，您可以編輯檔案，並將其上傳回伺服器。 您也可以使用檔案來設定其他AEM Forms產品例項。

為了避免安全風險，導出的配置檔案中不包含目錄伺服器的綁定密碼值。 先更新XML檔案中的密碼，然後再將檔案導入新系統。

>[!NOTE]
>
>匯入設定檔案會根據檔案中的資訊重新設定AEM表單。 只有熟悉AEM表單產品和XML的系統管理員或專業服務顧問才應考慮修改配置檔案。 他們可能需要編輯配置檔案，例如，以重新配置損壞的設定。

**匯出設定資訊**

1. 在管理控制台中，按一下「設定」 > 「使用者管理」 > 「設定」 > 「匯入和匯出設定檔」 。
1. 按一下「匯出」。 如果您使用Microsoft Internet Explorer，系統會提示您指定儲存檔案的位置。 如果您使用Firefox，檔案會儲存在案頭上。

**匯入設定資訊**

1. 在管理控制台中，按一下「設定」 > 「使用者管理」 > 「設定」 > 「匯入和匯出設定檔」 。
1. 按一下「瀏覽」以查找配置檔案，按一下「導入」，然後按一下「確定」。

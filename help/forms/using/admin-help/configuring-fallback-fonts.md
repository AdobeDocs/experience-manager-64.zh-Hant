---
title: 配置後援字型
seo-title: Configuring fallback fonts
description: 了解如何設定備援字型。
seo-description: Learn how to configure fallback fonts.
uuid: 2745541c-8c6d-4bb4-aa14-ec19afd6bc35
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d997a268-a40a-462d-badd-94f0731f7ba4
feature: PDF Generator
exl-id: 6942b6fc-8d04-429f-8433-1ab74c68fcc1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 1%

---

# 配置後援字型 {#configuring-fallback-fonts}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

如果伺服器上沒有預設字型，可以手動配置FontManagerResources.properties檔案，將預設AEM表單字型映射為後退（或替代）。 此屬性檔案位於adobe-fontmanager.jar檔案中。

>[!NOTE]
>
>後援字型配置也適用於組合器服務。

1. 導覽至adobe-livecycle-*[appserver]*.ear檔案 *[aem-forms根]*/configurationManager/export目錄，建立備份副本，然後取消對原始副本的封裝。
1. 找到adobe-fontmanager.jar檔案並將其取消封裝。
1. 找到FontManagerResources.properties檔案，並在文本編輯器中開啟它。
1. 視需要修改一般字型和備援字型位置和名稱，並儲存檔案。

   FontManagerResources.properties檔案中的字型條目與 *[aem-forms根]*/fonts目錄。 如果指定的字型不是預設的AEM表單字型，則必須在此目錄結構內（在現有目錄內或新建立的目錄中）安裝這些字型。

   >[!NOTE]
   >
   >如果指定的字型或預設字型不包含特定的unicode字元，或者如果不可用，則根據以下優先順序從後援字型取用該字元：

   * 地區特定字型
   * 未設定區域設定時的ROOT字型
   * 一般字型，按後援表格中的順序集搜索

1. 重新封裝adobe-fontmanager.jar檔案。
1. 重新封裝adobe-livecycle-*[appserver]*.ear檔案，然後手動或執行Configuration Manager重新部署。

>[!NOTE]
>
>請勿使用Configuration Manager重新封裝adobe-livecycle-[appserver].ear檔案，因為此檔案會以AEM表單預設值覆寫您的修改。

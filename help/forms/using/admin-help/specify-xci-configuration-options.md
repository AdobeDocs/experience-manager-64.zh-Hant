---
title: 指定XCI配置選項
seo-title: Specify XCI configuration options
description: 了解如何指定XCI設定選項。
seo-description: Learn how to specify XCI configuration options.
uuid: cf9e544d-63cd-4fad-8f89-bdb46eeef409
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: f38ebd69-8d1c-49b6-824f-4bf0ec8a8953
exl-id: 5156bb1c-8ad6-498c-aaf7-6474ffa8c83c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 4%

---

# 指定XCI配置選項 {#specify-xci-configuration-options}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

輸出可讓您指定用於呈現的自訂XCI檔案。 (請參閱 [指定輸出的檔案位置](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).) 依預設，輸出會覆寫XCI檔案中指定的部分選項，包括：

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

您可以為上述選項選取取消覆寫的選項，在此情況下，「輸出」會使用自訂XCI檔案中指定的值。

1. 在管理控制台中，按一下「服務>輸出」。
1. 選中或取消選中「使用系統預設XCI選項」複選框。 選中此選項時，輸出將對資料包、建立者、製作者和compressObjectStream設定使用其預設值。 取消選取此選項時，輸出會使用自訂XCI檔案中指定的值。
1. 按一下「儲存」。

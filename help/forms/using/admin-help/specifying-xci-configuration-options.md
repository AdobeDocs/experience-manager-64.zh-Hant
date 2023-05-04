---
title: 指定XCI配置選項
seo-title: Specifying XCI configuration options
description: 了解如何指定XCI設定選項。
seo-description: Learn how to specify XCI configuration options.
uuid: 5d3c10c1-4a93-4336-b311-20faaf835b9f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 162c9fda-f4d4-4ad5-a9ab-7554828e821c
exl-id: 7a13b13f-3eee-4fc0-8957-bd42f43119e9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 4%

---

# 指定XCI配置選項 {#specifying-xci-configuration-options}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Forms可讓您指定用於轉譯的自訂XCI檔案。 (請參閱 [配置Forms位置](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).) 依預設，Forms會覆寫XCI檔案中指定的部分選項，包括：

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

您可以為上述選項選取取消覆寫的選項，在此情況下，Forms將使用自訂XCI檔案中指定的值。

1. 在管理主控台中，按一下「服務> Forms」。
1. 選中或取消選中「使用系統預設XCI選項」複選框。 選取此選項時，Forms會對資料包、建立者、製作者和compressObjectStream設定使用其預設值。 取消選取此選項時，Forms會使用自訂XCI檔案中指定的值。
1. 按一下「儲存」。

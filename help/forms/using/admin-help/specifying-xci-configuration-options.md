---
title: 指定XCI配置選項
seo-title: 指定XCI配置選項
description: 了解如何指定XCI設定選項。
seo-description: 了解如何指定XCI設定選項。
uuid: 5d3c10c1-4a93-4336-b311-20faaf835b9f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 162c9fda-f4d4-4ad5-a9ab-7554828e821c
exl-id: 7a13b13f-3eee-4fc0-8957-bd42f43119e9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 1%

---

# 指定XCI配置選項{#specifying-xci-configuration-options}

Forms可讓您指定用於轉譯的自訂XCI檔案。 (請參閱[設定Forms的位置](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms)。) 依預設，Forms會覆寫XCI檔案中指定的部分選項，包括：

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

您可以為上述選項選取取消覆寫的選項，在此情況下，Forms將使用自訂XCI檔案中指定的值。

1. 在管理主控台中，按一下「服務> Forms」。
1. 選中或取消選中「使用系統預設XCI選項」複選框。 選取此選項時，Forms會對資料包、建立者、製作者和compressObjectStream設定使用其預設值。 取消選取此選項時，Forms會使用自訂XCI檔案中指定的值。
1. 按一下「儲存」。

---
title: 指定安全設定
seo-title: Specify security settings
description: 了解如何指定安全設定。
seo-description: Learn how to specify security settings.
uuid: c86ba195-010d-40d6-9f9d-4cb4c364d104
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 3c017f9a-aa7f-4d12-ba8b-9fd92c029157
exl-id: 3cc39a24-dbdf-4a4c-9c96-4d39d8cff20d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 6%

---

# 指定安全設定 {#specify-security-settings}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

通過輸出，可以控制XML輸入中的外部實體是否被解析。 預設會解決這些問題，但您可以變更此行為以提高AEM表單系統的安全性。

**防止處理包含外部實體引用的XML資料檔案**

1. 在管理控制台中，按一下「服務>輸出」。
1. 清除「解析外部實體」(Resolve External Entities)複選框。
1. 按一下「儲存」。

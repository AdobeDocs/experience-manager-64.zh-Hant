---
title: 更改字元集
seo-title: Change the character set
description: 您可以指定用於對輸出流進行編碼的字元集。 了解如何變更字元集。
seo-description: You can specify the character set used to encode the output stream. Learn how you can change the character set.
uuid: ecb0c3ff-368c-4553-80e4-aa35fc15af62
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 811b31f8-5465-4fb2-b1f9-513936041771
exl-id: 7961efc6-4b11-423a-871d-7b37e3f36781
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 4%

---

# 更改字元集 {#change-the-character-set}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

您可以指定用於對輸出流進行編碼的字元集。

1. 在管理控制台中，按一下 **[!UICONTROL 服務>輸出]**.
1. 在「國際化」下，在「字元集」清單中，選擇一個字元集。 此設定取決於 `TransformationFormat` 和 `PrintFormat` 透過API指定。 要指定列出的字元集以外的字元集，請選擇「自定義」並在顯示的框中指定編碼值。

   若 `TransformationFormat` 是PDF和PDF/A或 `PrintFormat` 是PCL、PostScript、Zebra標籤、IPL、DPL、TPCL、GenericColorPCL或GenericPSLevel3，則僅支援特定字元集。

   字元集必須是有效的規範名稱。 預設值為ISO-8859-1。

1. 按一下「**[!UICONTROL 儲存]**」。

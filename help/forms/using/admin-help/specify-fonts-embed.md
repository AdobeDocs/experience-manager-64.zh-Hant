---
title: 指定要嵌入的字型
seo-title: Specify fonts to embed
description: 了解如何指定要內嵌的字型。
seo-description: Learn how to specify fonts to embed.
uuid: 02da5c00-0467-4633-a076-c36725cbfbad
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 180f0448-d507-4b6d-bb8a-d12a434e1250
exl-id: e24f4123-bed3-4096-b3fb-22deb1c1e9b9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 2%

---

# 指定要嵌入的字型{#specify-fonts-to-embed}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

您可以指定哪些字型始終嵌入或從不嵌入由輸出使用的表單。 嵌入字型會增加表單的檔案大小。 嵌入用戶在其系統上不太可能擁有的異常字型，並且不嵌入他們將安裝的常見字型。

>[!NOTE]
>
>如果您已為「輸出」指定自訂XCI檔案，XCI檔案中的內嵌字型選項會覆寫這些設定。 (請參閱 [指定輸出的檔案位置](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).)

1. 在管理控制台中，按一下「服務>輸出」。
1. 在「字型嵌入設定」下，在「始終嵌入字型」框中，鍵入要與表單嵌入的字型的名稱，並以逗號分隔。 指定的字型只有在窗體中使用時才會嵌入生成的窗體。 如果已在傳遞至服務的XCI檔案中開啟內嵌字型選項，則會忽略此設定。 在這種情況下，PDF中使用的所有字型都始終被嵌入。
1. 在「永不嵌入字型」框中，鍵入不要與表單嵌入的字型的名稱，並以逗號分隔。 您指定的字型不會嵌入到PDF中，即使這些字型用於生成的PDF中亦然。 如果傳遞至服務的XCI檔案中的內嵌字型選項已關閉，則會忽略此設定。 在這種情況下，PDF中使用的字型均不嵌入。
1. 按一下「儲存」。

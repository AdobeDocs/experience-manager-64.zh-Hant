---
title: 命名慣例
seo-title: Naming Conventions
description: Java包名稱中的連字型大小
seo-description: Hyphens in Java Package Name
uuid: 48086e6c-c35b-4ffc-b216-d01feca7bf9a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 5271feb9-70c6-4c82-8ac7-34a63d80e3aa
exl-id: f5a63642-9f2c-436f-bd40-4459545a0ddf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 5%

---

# 命名慣例 {#naming-conventions}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## Java包名稱中的連字型大小 {#hyphens-in-java-package-name}

為Java類建立位置時，請注意，包名稱必須與儲存庫資料夾位置的名稱匹配，並且路徑中的任何連字型大小都會正確轉義。

雖然在AEM開發中建議在存放庫項目名稱中使用連字型大小，但在Java套件名稱中使用連字型大小是非法的。

基礎CRX平台必須能夠區分實際底線「_&#39;和連字型大小&#39;-&#39;。 因此，在JCR中，連字型大小必須替換為其unicode值(u002d)，並以下划線「_&#39;。

例如，如果存放庫路徑為 **/apps/my-example/component/info/Info.java**，套件名稱應為 `java package apps.my_002dexample.component.info;`

請注意，底線也必須同樣逸出，這樣 `_` com `_005f`.

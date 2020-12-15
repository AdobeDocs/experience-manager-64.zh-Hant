---
title: 啟用重複檢測
description: 瞭解如何在AEM中啟用重複資產的偵測。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 26e860cd513d70d748f872e2ce445a042d075bc6
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---


# 啟用重複檢測{#enabling-duplicate-detection}

如果您嘗試上傳存在於Adobe Experience Manager(AEM)Assets中的資產，重複偵測功能會將其識別為重複。 預設會停用重複偵測。 要啟用該功能，請執行以下步驟：

1. 開啟&#x200B;**[!UICONTROL Adobe Experience Manager Web Console Configuration]**&#x200B;頁面，網址為`https://[server]:[port]/system/console/configMgr`。
1. 編輯servlet **[!UICONTROL Day CQ DAM Create Asset]**&#x200B;的配置。
1. 選擇&#x200B;**[!UICONTROL detect duplicate]**&#x200B;選項，然後按一下／點選&#x200B;**[!UICONTROL Save]**。

   ![在servlet中選擇檢測重複選項](assets/chlimage_1-377.png)

AEM Assets現在已啟用偵測重複功能。 當使用者嘗試上傳AEM中存在的資產時，系統會檢查衝突並指出衝突。 資產使用儲存在`jcr:content/metadata/dam:sha1`的SHA-1雜湊來識別，這表示不論檔案名稱為何，都會偵測到重複資產。

>[!MORELIKETHIS]
>
>* [現有儲存庫中重複的資產（社區成員的教程）](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)


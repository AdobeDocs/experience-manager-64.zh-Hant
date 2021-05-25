---
title: 啟用重複檢測
description: 了解如何在AEM中啟用重複資產的偵測。
contentOwner: AG
feature: 資產管理，資產報表
role: Business Practitioner,Administrator
exl-id: 138cf649-9e21-415e-9861-b07caacc85db
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# 啟用重複檢測{#enabling-duplicate-detection}

如果您嘗試上傳Adobe Experience Manager(AEM)資產中存在的資產，重複偵測功能會將其識別為重複。 預設會停用重複偵測。 要啟用該功能，請執行以下步驟：

1. 在`https://[server]:[port]/system/console/configMgr`開啟&#x200B;**[!UICONTROL Adobe Experience Manager Web控制台配置]**&#x200B;頁。
1. 編輯Servlet **[!UICONTROL Day CQ DAM Create Asset]**&#x200B;的設定。
1. 選取&#x200B;**[!UICONTROL 偵測重複]**&#x200B;選項，然後按一下/點選&#x200B;**[!UICONTROL 儲存]**。

   ![在servlet中選擇檢測重複選項](assets/chlimage_1-377.png)

偵測重複功能現在已在AEM Assets中啟用。 當使用者嘗試上傳AEM中存在的資產時，系統會檢查衝突並指出衝突。 系統會使用儲存在`jcr:content/metadata/dam:sha1`的SHA-1雜湊來識別資產，這表示系統會無論檔案名稱為何都偵測到重複資產。

>[!MORELIKETHIS]
>
>* [在現有存放庫中複製資產（社群成員的教學課程）](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)


---
title: 啟用重複檢測
description: 了解如何在AEM中啟用重複資產的偵測。
contentOwner: AG
feature: Asset Management,Asset Reports
role: User,Admin
exl-id: 138cf649-9e21-415e-9861-b07caacc85db
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 2%

---

# 啟用重複檢測 {#enabling-duplicate-detection}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

如果您嘗試上傳Adobe Experience Manager Assets中存在的資產，重複偵測功能會將其識別為重複。 預設會停用重複偵測。 要啟用該功能，請執行以下步驟：

1. 開啟 **[!UICONTROL Adobe Experience Manager Web主控台設定]** 頁面 `https://[server]:[port]/system/console/configMgr`.
1. 編輯servlet的配置 **[!UICONTROL 日CQ DAM建立資產]**.
1. 選取 **[!UICONTROL 偵測重複]** 選項，然後按一下/點選 **[!UICONTROL 儲存]**.

   ![在servlet中選擇檢測重複選項](assets/chlimage_1-377.png)

現在已在 [!DNL Experience Manager] 資產。 當使用者嘗試上傳AEM中存在的資產時，系統會檢查衝突並指出衝突。 會使用儲存於的SHA-1雜湊來識別資產 `jcr:content/metadata/dam:sha1`，表示系統會在檔案名稱無關的情況下偵測重複資產。

>[!MORELIKETHIS]
>
>* [在現有存放庫中複製資產（社群成員的教學課程）](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)


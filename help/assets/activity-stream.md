---
title: 時間軸中的活動資料流
description: 本文說明如何在時間軸上顯示資產的活動記錄。
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: 52fa2d59-177f-49ca-a480-7213ce0ca7d7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 23%

---

# 時間軸中的活動資料流 {#activity-stream-in-timeline}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

此功能會顯示時間軸上資產的活動記錄。 如果您在 [!DNL Adobe Experience Manager Assets]，活動資料流功能會更新時間軸以反映活動。

活動資料流中記錄下列操作：

* 建立
* 刪除
* 下載（包括轉譯）
* 發佈
* 未發佈
* 批准
* 拒絕
* 移動

將從儲存日誌檔案的CRX位置提取要在時 `/var/audit/com.day.cq.dam/content/dam` 間軸中顯示的活動日誌。

此外，當上傳新資產或修改現有資產並透過簽入Experience Manager時，會記錄時間軸活動 [Adobe資產連結](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) 或 [[!DNL Experience Manager] 案頭應用程式](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html).

>[!NOTE]
>
>時間軸中不會顯示暫時性工作流程，因為不會儲存這些工作流程的歷史資訊。

若要檢視活動資料流，請對資產執行一或多個操作、選取資產，然後選擇 **[!UICONTROL 時間表]** 從GlobalNav清單中。

![時間表–3](assets/timeline-3.png)

時間軸會顯示您對資產執行之作業的活動資料流。

![activity_stream](assets/activity_stream.png)

>[!NOTE]
>
>「發佈」和「取消發佈」任 **務的預設日** 志存 **儲位置為**`/var/audit/com.day.cq.replication/content`。對於 **移動** ，預設位置為 `/var/audit/com.day.cq.wcm.core.page`。

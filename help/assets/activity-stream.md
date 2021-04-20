---
title: 時間軸中的活動串流
description: '本文說明如何在時間軸上顯示資產的活動記錄檔。 '
contentOwner: AG
feature: Asset Management
role: Business Practitioner,Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 33%

---


# 時間軸中的活動串流{#activity-stream-in-timeline}

此功能會在時間軸上顯示資產的活動記錄。 如果您在Adobe Experience Manager(AEM)資產中執行下列任一資產相關作業，「活動串流」功能會更新時間軸以反映活動。

活動流中記錄了以下操作：

* 建立
* 刪除
* 下載（包括轉譯）
* 發佈
* 未發佈
* 批准
* 拒絕
* 移動

將從儲存日誌檔案的CRX位置提取要在時 `/var/audit/com.day.cq.dam/content/dam` 間軸中顯示的活動日誌。

此外，當上傳新資產或修改現有資產並透過 [Adobe Asset Link](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) 或 [AEM案頭應用程式簽入AEM時，會記錄時間軸活動](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html)。

>[!NOTE]
>
>暫時性工作流程不會顯示在時間軸中，因為不會儲存這些工作流程的歷史記錄資訊。

若要檢視活動串流，請對資產執行一或多個作業，選取資產，然後從GlobalNav清單中選擇&#x200B;**[!UICONTROL Timeline]**。

![timeline-3](assets/timeline-3.png)

時間軸會顯示您對資產執行之作業的活動資料流。

![activity_stream](assets/activity_stream.png)

>[!NOTE]
>
>「發佈」和「取消發佈」任 **務的預設日** 志存 **儲位置為**`/var/audit/com.day.cq.replication/content`。對於 **移動** ，預設位置為 `/var/audit/com.day.cq.wcm.core.page`。

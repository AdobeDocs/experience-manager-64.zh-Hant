---
title: 在 [!DNL Adobe Experience Manager]中配置非同步操作。
description: 以非同步方式完成某些耗用大量資源的任務，以優化 [!DNL Experience Manager Assets]中的效能。
contentOwner: AG
feature: 資產管理
role: Business Practitioner
exl-id: 0abdfe87-d932-41dd-b1e6-9f5fa5b924fe
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 22%

---

# 非同步操作{#asynchronous-operations}

為減少對效能的不利影響，[!DNL Adobe Experience Manger Assets]以非同步方式處理某些長時間執行且耗用大量資源的資產操作。 非同步處理包括將多個任務排入隊列，並最終根據系統資源的可用性以串列方式執行這些任務。 這些操作包括：

* 刪除多項資產。
* 移動多項資產或參照眾多的資產.
* 大量匯出和匯入資產中繼資料。

您可以從&#x200B;**[!UICONTROL 非同步作業狀態]**&#x200B;頁面檢視非同步任務的狀態。

>[!NOTE]
>
>預設情況下，[!DNL Assets]任務並行執行。 如果`N`是CPU內核數，預設情況下`N/2`任務可以並行執行。 要使用任務隊列的自定義設定，請從[!UICONTROL Web控制台]修改&#x200B;**[!UICONTROL 非同步操作預設隊列]**&#x200B;配置。 如需詳細資訊，請參閱[佇列設定](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations)。

## 監視非同步操作狀態{#monitoring-the-status-of-asynchronous-operations}

每當[!DNL Assets]以非同步方式處理操作時，您會在[!DNL Experience Manager] [收件匣](/help/sites-authoring/inbox.md)中並透過電子郵件收到通知。 如要檢視非同步操作的詳細狀態，請導覽至&#x200B;**[!UICONTROL 「非同步作業狀態」]**&#x200B;頁面。

1. 在[!DNL Experience Manager]介面中，按一下&#x200B;**[!UICONTROL Operations]** > **[!UICONTROL Jobs]**。

1. 進入&#x200B;**[!UICONTROL 「非同步作業狀態」]**&#x200B;頁面後，即可檢視操作的詳細資訊。

   ![非同步操作的狀態和詳細資訊](assets/job_status.png)

   要確定操作的進度，請參閱&#x200B;**[!UICONTROL 狀態]**&#x200B;列。 系統會根據進度顯示下列其中一種狀態：

   * **[!UICONTROL 執行中]**：正在處理操作。
   * **[!UICONTROL 成功]**：操作完成.
   * **[!UICONTROL 失敗]**&#x200B;或&#x200B;**[!UICONTROL 錯誤]**：無法處理操作.
   * **[!UICONTROL 已排程]**：操作已排程，等待稍後處理.

1. 要停止活動操作，請從清單中選擇操作，然後從工具欄按一下&#x200B;**[!UICONTROL Stop]** ![stop表徵圖](assets/do-not-localize/stop_icon.svg)。

1. 若要檢視額外詳細資訊，例如說明和記錄，請選取操作，然後從工具列按一下&#x200B;**[!UICONTROL Open]** ![open_icon](assets/do-not-localize/edit_icon.svg)。 此時將顯示任務詳細資訊頁。

   ![元資料導入任務的詳細資訊](assets/job_details.png)

1. 若要從清單中刪除操作，請選取工具列中的&#x200B;**[!UICONTROL 「刪除」]**。若要以 CSV 檔案格式下載詳細資訊，請按&#x200B;**[!UICONTROL 「下載」]**。

   >[!NOTE]
   >
   >如果任務的狀態為活動或已排入隊列，則無法刪除該任務。

## 清除已完成的任務{#purge-completed-tasks}

[!DNL Experience Manager Assets] 每天01時執行清除任務，以刪除超過一天的已完成非同步任務。

<!-- TBD: Find out from the engineering team and mention the time zone of this 1:00 am task.
-->

您可以修改清除任務的計畫以及在刪除完成任務之前保留其詳細資訊的持續時間。 您也可以配置在任何時間點保留詳細資訊的已完成任務的最大數量。

1. 在[!DNL Experience Manager]介面中，按一下&#x200B;**[!UICONTROL 工具]** > **[!UICONTROL 操作]** > **[!UICONTROL Web控制台]**。
1. 開啟「**[!UICONTROL Adobe CQ DAM非同步作業清除已排程]**」任務。
1. 指定已完成任務刪除後的天數閾值，以及詳細資訊保留在歷史記錄中的任務的最大天數。 儲存變更。

   ![非同步任務清除排程配置](assets/purge_job.png)

## 配置非同步刪除操作的閾值{#configure-thresholds-for-asynchronous-delete-operations}

如果要刪除的資產或資料夾數量超過設定的臨界值，系統就會以非同步方式執行刪除操作。

1. 在[!DNL Experience Manager]介面中，按一下&#x200B;**[!UICONTROL 工具]** > **[!UICONTROL 操作]** > **[!UICONTROL Web控制台]**。
1. 在[!UICONTROL Web控制台]中，開啟&#x200B;**[!UICONTROL 非同步刪除操作作業處理]**&#x200B;配置。
1. 在&#x200B;**[!UICONTROL 資產數上限]**&#x200B;方塊中，指定要非同步刪除資產、資料夾或參考的上限數字。 儲存變更。

   ![設定任務刪除資產的臨界值限制](assets/delete_threshold.png)

## 配置非同步移動操作的閾值{#configure-thresholds-for-asynchronous-move-operations}

如果要移動的資產、資料夾或參考數量超過設定的臨界值，系統就會以非同步方式執行移動操作。

1. 在[!DNL Experience Manager]介面中，按一下「工具」**[!UICONTROL >「**[!UICONTROL &#x200B;操作」]**>「**[!UICONTROL  Web控制台」]**。]**
1. 在[!UICONTROL Web控制台]中，開啟&#x200B;**[!UICONTROL 非同步移動操作作業處理]**&#x200B;配置。
1. 在&#x200B;**[!UICONTROL 資產/參照數上限]**&#x200B;方塊中，指定要非同步移動資產、資料夾或參照的上限數字。 儲存變更。

   ![設定移動資產任務的臨界值限制](assets/move_threshold.png)

>[!MORELIKETHIS]
>
>* [以Experience Manager設定電子郵件](/help/sites-administering/notification.md)。
>* [大量匯入和匯出資產的中繼資料](/help/assets/metadata-import-export.md)。


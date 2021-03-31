---
title: 在 [!DNL Adobe Experience Manager]中配置非同步操作。
description: 以非同步方式完成某些資源密集型任務，以優化 [!DNL Experience Manager Assets]中的效能。
contentOwner: AG
feature: 資產管理
role: 業務從業人員
translation-type: tm+mt
source-git-commit: 4acf159ae1b9923a9c93fa15faa38c7f4bc9f759
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 22%

---


# 非同步操作{#asynchronous-operations}

為了減少對效能的不利影響，[!DNL Adobe Experience Manger Assets]非同步處理某些長期運行和資源密集型資產操作。 非同步處理包括將多個任務入隊並最終以串列方式執行這些任務，這取決於系統資源的可用性。 這些操作包括：

* 刪除多項資產。
* 移動多項資產或參照眾多的資產.
* 大量匯出和匯入資產中繼資料。

您可以從&#x200B;**[!UICONTROL 非同步作業狀態]**&#x200B;頁面檢視非同步作業的狀態。

>[!NOTE]
>
>預設情況下，[!DNL Assets]任務並行執行。 如果`N`是CPU內核數，則預設情況下，`N/2`任務可以並行執行。 要使用任務隊列的自定義設定，請修改[!UICONTROL Web控制台]中的&#x200B;**[!UICONTROL 非同步操作預設隊列]**&#x200B;配置。 如需詳細資訊，請參閱[佇列設定](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations)。

## 監視非同步操作的狀態{#monitoring-the-status-of-asynchronous-operations}

每當[!DNL Assets]以非同步方式處理操作時，您會在[!DNL Experience Manager] [收件箱](/help/sites-authoring/inbox.md)中收到通知，並通過電子郵件發送。 如要檢視非同步操作的詳細狀態，請導覽至&#x200B;**[!UICONTROL 「非同步作業狀態」]**&#x200B;頁面。

1. 在[!DNL Experience Manager]介面中，按一下&#x200B;**[!UICONTROL 操作]** > **[!UICONTROL 作業]**。

1. 進入&#x200B;**[!UICONTROL 「非同步作業狀態」]**&#x200B;頁面後，即可檢視操作的詳細資訊。

   ![非同步操作的狀態和詳細資訊](assets/job_status.png)

   要確定操作的進度，請參閱&#x200B;**[!UICONTROL Status]**&#x200B;列。 系統會根據進度顯示下列其中一種狀態：

   * **[!UICONTROL 執行中]**：正在處理操作。
   * **[!UICONTROL 成功]**：操作完成.
   * **[!UICONTROL 失敗]**&#x200B;或&#x200B;**[!UICONTROL 錯誤]**：無法處理操作.
   * **[!UICONTROL 已排程]**：操作已排程，等待稍後處理.

1. 要停止活動操作，請從清單中選擇該操作，然後從工具欄中按一下&#x200B;**[!UICONTROL Stop]** ![stop表徵圖](assets/do-not-localize/stop_icon.svg)。

1. 要查看額外詳細資訊，例如說明和日誌，請選擇操作，然後從工具欄中按一下&#x200B;**[!UICONTROL Open]** ![open_icon](assets/do-not-localize/edit_icon.svg)。 此時將顯示任務詳細資訊頁。

   ![中繼資料匯入工作的詳細資訊](assets/job_details.png)

1. 若要從清單中刪除操作，請選取工具列中的&#x200B;**[!UICONTROL 「刪除」]**。若要以 CSV 檔案格式下載詳細資訊，請按&#x200B;**[!UICONTROL 「下載」]**。

   >[!NOTE]
   >
   >如果任務的狀態為活動或已排隊，則不能刪除該任務。

## 清除完成的任務{#purge-completed-tasks}

[!DNL Experience Manager Assets] 每天01時執行清除任務，以刪除已完成的已超過一天的非同步任務。

<!-- TBD: Find out from the engineering team and mention the time zone of this 1:00 am task.
-->

您可以修改清除任務的調度以及刪除完成任務之前保留其詳細資訊的持續時間。 您也可以設定在任何時間點保留詳細資料的已完成任務數上限。

1. 在[!DNL Experience Manager]介面中，按一下「工具」>「操作」>「操作」]**>「Web控制台」]**。******[!UICONTROL **[!UICONTROL 
1. 開啟&#x200B;**[!UICONTROL Adobe CQDAM非同步作業清除計畫任務]**。
1. 指定刪除已完成任務的天數閾值，以及歷史記錄中保留詳細資訊的最大任務數。 儲存變更。

   ![用於調度非同步任務清除的配置](assets/purge_job.png)

## 配置非同步刪除操作的閾值{#configure-thresholds-for-asynchronous-delete-operations}

如果要刪除的資產或檔案夾數目超過設定的臨界值數目，則會非同步執行刪除作業。

1. 在[!DNL Experience Manager]介面中，按一下「工具」>「操作」>「操作」]**>「Web控制台」]**。******[!UICONTROL **[!UICONTROL 
1. 在[!UICONTROL Web控制台]中，開啟&#x200B;**[!UICONTROL 非同步刪除操作作業處理]**&#x200B;配置。
1. 在&#x200B;**[!UICONTROL 資產的臨界值數]**&#x200B;方塊中，指定臨界值數字以非同步刪除資產、檔案夾或參考。 儲存變更。

   ![設定要刪除資產的任務的臨界值限制](assets/delete_threshold.png)

## 配置非同步移動操作的閾值{#configure-thresholds-for-asynchronous-move-operations}

如果要移動的資產、資料夾或引用數量超過設定的閾值數量，將非同步執行移動操作。

1. 在[!DNL Experience Manager]介面中，按一下「工具」>「操作」****>**** > 「Web控制台」]**。**[!UICONTROL 
1. 在[!UICONTROL Web控制台]中，開啟&#x200B;**[!UICONTROL 非同步移動操作作業處理]**&#x200B;配置。
1. 在&#x200B;**[!UICONTROL 資產／參考的臨界值數]**&#x200B;方塊中，指定臨界值數以非同步地移動資產、檔案夾或參考。 儲存變更。

   ![設定要移動資產之任務的臨界值限制](assets/move_threshold.png)

>[!MORELIKETHIS]
>
>* [以Experience Manager配置電子郵件](/help/sites-administering/notification.md)。
>* [大量匯入和匯出資產的中繼資料](/help/assets/metadata-import-export.md)。


---
title: 在中設定非同步操作 [!DNL Adobe Experience Manager].
description: 以非同步方式完成一些耗用大量資源的任務，以在 [!DNL Experience Manager Assets].
contentOwner: AG
feature: Asset Management
role: User
exl-id: 0abdfe87-d932-41dd-b1e6-9f5fa5b924fe
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 21%

---

# 非同步操作 {#asynchronous-operations}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

為減少對效能的不利影響， [!DNL Adobe Experience Manger Assets] 以非同步方式處理某些長時間執行且耗用大量資源的資產作業。 非同步處理包括將多個任務排入隊列，並最終根據系統資源的可用性以串列方式執行這些任務。 這些操作包括：

* 刪除多項資產.
* 移動多項資產或參照眾多的資產.
* 大量匯出和匯入資產中繼資料。

您可以從 **[!UICONTROL 非同步作業狀態]** 頁面。

>[!NOTE]
>
>依預設， [!DNL Assets] 任務並行執行。 若 `N` 是CPU核心數， `N/2` 預設情況下，任務可並行執行。 要使用任務隊列的自定義設定，請修改 **[!UICONTROL 非同步操作預設隊列]** 配置 [!UICONTROL Web主控台]. 如需詳細資訊，請參閱[佇列設定](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations)。

## 監控非同步操作的狀態 {#monitoring-the-status-of-asynchronous-operations}

每當 [!DNL Assets] 以非同步方式處理操作，您會在 [!DNL Experience Manager] [收件匣](/help/sites-authoring/inbox.md) 並通過電子郵件。 如要檢視非同步操作的詳細狀態，請導覽至&#x200B;**[!UICONTROL 「非同步作業狀態」]**&#x200B;頁面。

1. 在 [!DNL Experience Manager] 介面按一下 **[!UICONTROL 操作]** > **[!UICONTROL 工作]**.

1. 進入&#x200B;**[!UICONTROL 「非同步作業狀態」]**&#x200B;頁面後，即可檢視操作的詳細資訊。

   ![非同步操作的狀態和詳細資訊](assets/job_status.png)

   若要確定操作進度，請參閱 **[!UICONTROL 狀態]** 欄。 系統會根據進度顯示下列其中一種狀態：

   * **[!UICONTROL 執行中]**：正在處理操作.
   * **[!UICONTROL 成功]**：操作完成.
   * **[!UICONTROL 失敗]**&#x200B;或&#x200B;**[!UICONTROL 錯誤]**：無法處理操作.
   * **[!UICONTROL 已排程]**：操作已排程，等待稍後處理.

1. 要停止活動操作，請從清單中選擇該操作，然後按一下 **[!UICONTROL 停止]** ![停止表徵圖](assets/do-not-localize/stop_icon.svg) 的上界。

1. 若要檢視額外詳細資訊（例如說明和記錄），請選取操作，然後按一下 **[!UICONTROL 開啟]** ![open_icon](assets/do-not-localize/edit_icon.svg) 的上界。 此時將顯示任務詳細資訊頁。

   ![元資料導入任務的詳細資訊](assets/job_details.png)

1. 若要從清單中刪除操作，請選取工具列中的&#x200B;**[!UICONTROL 「刪除」]**。若要以 CSV 檔案格式下載詳細資訊，請按&#x200B;**[!UICONTROL 「下載」]**。

   >[!NOTE]
   >
   >如果任務的狀態為活動或已排入隊列，則無法刪除該任務。

## 清除已完成的任務 {#purge-completed-tasks}

[!DNL Experience Manager Assets] 每天01時執行清除任務，以刪除超過一天的已完成非同步任務。

<!-- TBD: Find out from the engineering team and mention the time zone of this 1:00 am task.
-->

您可以修改清除任務的計畫以及在刪除完成任務之前保留其詳細資訊的持續時間。 您也可以配置在任何時間點保留詳細資訊的已完成任務的最大數量。

1. 在 [!DNL Experience Manager] 介面按一下 **[!UICONTROL 工具]** > **[!UICONTROL 操作]** > **[!UICONTROL Web主控台]**.
1. 開啟 **[!UICONTROL Adobe CQ DAM非同步作業清除已排程]** 任務。
1. 指定已完成任務刪除後的天數閾值，以及詳細資訊保留在歷史記錄中的任務的最大天數。 儲存變更。

   ![非同步任務清除排程配置](assets/purge_job.png)

## 設定非同步刪除操作的閾值 {#configure-thresholds-for-asynchronous-delete-operations}

如果要刪除的資產或資料夾數量超過設定的臨界值，系統就會以非同步方式執行刪除操作。

1. 在 [!DNL Experience Manager] 介面按一下 **[!UICONTROL 工具]** > **[!UICONTROL 操作]** > **[!UICONTROL Web主控台]**.
1. 從 [!UICONTROL Web主控台]，開啟 **[!UICONTROL 非同步刪除操作作業處理]** 設定。
1. 在 **[!UICONTROL 資產數量上限]** 方塊中指定非同步刪除資產、資料夾或參考的臨界值。 儲存變更。

   ![設定任務刪除資產的臨界值限制](assets/delete_threshold.png)

## 為非同步移動操作配置閾值 {#configure-thresholds-for-asynchronous-move-operations}

如果要移動的資產、資料夾或參考數量超過設定的臨界值，系統就會以非同步方式執行移動操作。

1. 在 [!DNL Experience Manager] 介面，按一下 **[!UICONTROL 工具]** > **[!UICONTROL 操作]** > **[!UICONTROL Web主控台]**.
1. 從 [!UICONTROL Web主控台]，開啟 **[!UICONTROL 非同步移動操作作業處理]** 設定。
1. 在 **[!UICONTROL 資產/參考的臨界值數]** 框中，指定要非同步移動資產、資料夾或參考的臨界值。 儲存變更。

   ![設定移動資產任務的臨界值限制](assets/move_threshold.png)

>[!MORELIKETHIS]
>
>* [在Experience Manager中配置電子郵件](/help/sites-administering/notification.md).
>* [大量匯入和匯出資產的中繼資料](/help/assets/metadata-import-export.md)。


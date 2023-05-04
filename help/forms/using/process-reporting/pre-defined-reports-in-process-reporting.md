---
title: 在進程報告中預先定義的報告
seo-title: Pre-defined reports in Process Reporting
description: 在JEE上查詢AEM Forms處理資料，以建立有關長時間執行的處理程式、處理持續時間和工作流程量的報表
seo-description: Query for AEM Forms on JEE process data to create reports on long running processes, Process duration, and Workflow volume
uuid: ba3a1809-270e-4c94-ade4-d2f6af86d860
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 6320c632-c7ec-4e56-9d12-cd27e3e9306e
exl-id: 21f5fb7e-53b3-485d-9b6a-813182f14781
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 1%

---

# 在進程報告中預先定義的報告 {#pre-defined-reports-in-process-reporting}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

AEM Forms Process Reporting隨附於以下項目 *現成可用* 報表：

* **[長時間運行的進程](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-long-running-processes-p)**:所有AEM Forms程式的報表，這些程式需要超過指定的時間才能完成

* **[流程持續時間圖](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-process-duration-report-br-p)**:指定AEM Forms程式的報表（依期間）

* **[工作流量](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-workflow-volume-report-p)**:按日期列出的指定進程的運行實例和已完成實例的報告

## 長時間運行的進程 {#long-running-processes}

「長時間執行的程式」報表會顯示已花費超過指定時間完成的AEM Forms程式。

### 要執行長時間運行的進程報告 {#to-execute-a-long-running-process-report-br}

1. 要查看「流程報告」中的預定義報告清單，請在 **流程報告** 樹視圖，按一下 **報表** 節點。
1. 按一下 **長時間運行的進程** 報表節點。

   ![long_running_node](assets/long_running_node.png)

   選取報表時， **報表參數** 面板會顯示在樹視圖的右側。

   ![長時間運行的進程報告參數面板](assets/report_parameters_panel.png)

   參數:

   * **持續時間**(*強制*):指定持續時間和時間單位。 顯示已執行超過指定持續時間的所有AEM Forms程式。
   * **開始時間** (*可選*):選擇日期。 篩選報表以顯示指定日期之後開始的處理例項。
   * **開始於之前** (*可選*):選擇日期。 篩選報表以顯示指定日期之前開始的處理例項。

1. 按一下 **開始** 來執行報表。

   報表會顯示在 **報表** 小組 **流程報告** 窗口。

   ![long_running_processes](assets/long_running_processes.png)

   使用 **報表** 面板，對報表執行下列操作。

   * **重新整理**:重新整理報表，將最新資料放在儲存中
   * **更改圖例顏色**:選擇並更改報表圖例的顏色
   * **匯出至CSV**:將報表中的資料匯出及下載為逗號分隔的檔案

## 「Process Duration」報告 {#process-duration-report-br}

「處理期間」報表會依每個執行個體已執行的天數，顯示Forms處理的例項數。

### 要執行「進程持續時間」報告 {#to-execute-a-process-duration-report-br}

1. 若要在「處理報告」中檢視預先定義的報表，請在 **流程報告** 樹視圖，按一下 **報表** 節點。
1. 按一下 **進程持續時間** 報表節點。

   ![process_duration_node](assets/process_duration_node.png)

   選取報表時， **報表參數** 面板會顯示在樹視圖的右側。

   ![長時間運行的進程報告參數面板](assets/process_duration_params.png)

   參數:

   * **選擇進程** (*強制*):選取AEM Forms程式。

1. 按一下 **開始** 來執行報表。

   報表會顯示在 **報表** 面板。

   ![process_duration_report](assets/process_duration_report.png)

   使用 **報表** 面板，對報表執行下列操作。

   * **重新整理**:重新整理報表，將最新資料放在儲存中
   * **更改圖例顏色**:選擇並更改報表圖例的顏色
   * **匯出至CSV**:將報表中的資料匯出及下載為逗號分隔的檔案

## 工作流量報告 {#workflow-volume-report}

「工作流量」報表會依日曆日顯示目前執行中和已完成的AEM Forms程式例項數。

### 要執行工作流卷報告 {#to-execute-a-workflow-volume-report-br}

1. 若要在「處理報告」中檢視預先定義的報表，請在 **流程報告** 樹視圖，按一下 **報表** 節點。
1. 按一下 **工作流量** 報表節點。

   ![workflow_volume_node](assets/workflow_volume_node.png)

   選取報表時， **報表參數** 面板會顯示在樹視圖的右側。

   ![長時間運行的進程報告參數面板](assets/workflow_volume_params.png)

   參數:

   * **選擇進程**(*強制*):選取AEM Forms程式。
   * **開始時間** (*可選*):選擇日期。 篩選報表以顯示指定日期之後開始的處理例項。
   * **開始於之前** (*可選*):選擇日期。 篩選報表以顯示指定日期之前開始的處理例項。

1. 按一下 **開始** 來執行報表。

   報表會顯示在 **報表** 小組 **流程報告** 窗口。

   ![workflow_volume_report](assets/workflow_volume_report.png)

   使用 **報表** 面板，對報表執行下列操作。

   * **重新整理**:重新整理報表，將最新資料放在儲存中
   * **更改圖例顏色**:選擇並更改報表圖例的顏色
   * **匯出至CSV**:將報表中的資料匯出及下載為逗號分隔的檔案

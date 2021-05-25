---
title: 在進程報告中預先定義的報告
seo-title: 在進程報告中預先定義的報告
description: 在JEE上查詢AEM Forms處理資料，以建立有關長時間執行的處理程式、處理持續時間和工作流程量的報表
seo-description: 在JEE上查詢AEM Forms處理資料，以建立有關長時間執行的處理程式、處理持續時間和工作流程量的報表
uuid: ba3a1809-270e-4c94-ade4-d2f6af86d860
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 6320c632-c7ec-4e56-9d12-cd27e3e9306e
exl-id: 21f5fb7e-53b3-485d-9b6a-813182f14781
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# 進程報告中的預定義報告{#pre-defined-reports-in-process-reporting}

AEM Forms Process Reporting隨附下列&#x200B;*out-of-the-box*&#x200B;報表：

* **[長時間運行的進程](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-long-running-processes-p)**:所有AEM Forms程式的報表，這些程式需要超過指定的時間才能完成

* **[流程持續時間圖](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-process-duration-report-br-p)**:指定AEM Forms程式的報表（依期間）

* **[工作流量](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md#p-workflow-volume-report-p)**:按日期列出的指定進程的運行實例和已完成實例的報告

## 長運行進程{#long-running-processes}

「長時間執行的程式」報表會顯示已花費超過指定時間完成的AEM Forms程式。

### 要執行長運行進程報告{#to-execute-a-long-running-process-report-br}

1. 要查看「進程報告」中預定義的報告的清單，請在&#x200B;**Process Reporting**&#x200B;樹視圖上，按一下&#x200B;**Reports**&#x200B;節點。
1. 按一下&#x200B;**長運行進程**&#x200B;報告節點。

   ![long_running_node](assets/long_running_node.png)

   選取報表時，樹狀檢視右側會顯示&#x200B;**報表參數**&#x200B;面板。

   ![長時間運行的進程報告參數面板](assets/report_parameters_panel.png)

   參數:

   * **持續時間**(*必要*):指定持續時間和時間單位。顯示已執行超過指定持續時間的所有AEM Forms程式。
   * **開始於** (*選用*):選擇日期。篩選報表以顯示指定日期之後開始的處理例項。
   * **開始於** (*選用*):選擇日期。篩選報表以顯示指定日期之前開始的處理例項。

1. 按一下&#x200B;**Go**&#x200B;以執行報表。

   報告顯示在&#x200B;**Process Reporting**&#x200B;窗口右側的&#x200B;**Report**&#x200B;面板中。

   ![long_running_processes](assets/long_running_processes.png)

   使用&#x200B;**Report**&#x200B;面板右上角的選項，對報表執行下列操作。

   * **重新整理**:重新整理報表，將最新資料放在儲存中
   * **更改圖例顏色**:選擇並更改報表圖例的顏色
   * **匯出至CSV**:將報表中的資料匯出及下載為逗號分隔的檔案

## 進程持續時間報告{#process-duration-report-br}

「處理期間」報表會依每個執行個體已執行的天數，顯示Forms處理的例項數。

### 要執行「進程持續時間」報告{#to-execute-a-process-duration-report-br}

1. 要查看「進程報告」中預定義的報告，請在&#x200B;**「進程報告」**&#x200B;樹視圖上，按一下&#x200B;**「報告」**&#x200B;節點。
1. 按一下&#x200B;**處理持續時間**&#x200B;報表節點。

   ![process_duration_node](assets/process_duration_node.png)

   選取報表時，樹狀檢視右側會顯示&#x200B;**報表參數**&#x200B;面板。

   ![長時間運行的進程報告參數面板](assets/process_duration_params.png)

   參數:

   * **選擇進程** (*強制*):選取AEM Forms程式。

1. 按一下&#x200B;**Go**&#x200B;以執行報表。

   報告顯示在「流程報告」窗口右側的&#x200B;**Report**&#x200B;面板中。

   ![process_duration_report](assets/process_duration_report.png)

   使用&#x200B;**Report**&#x200B;面板右上角的選項，對報表執行下列操作。

   * **重新整理**:重新整理報表，將最新資料放在儲存中
   * **更改圖例顏色**:選擇並更改報表圖例的顏色
   * **匯出至CSV**:將報表中的資料匯出及下載為逗號分隔的檔案

## 工作流卷報告{#workflow-volume-report}

「工作流量」報表會依日曆日顯示目前執行中和已完成的AEM Forms程式例項數。

### 要執行工作流卷報告{#to-execute-a-workflow-volume-report-br}

1. 要查看「進程報告」中預定義的報告，請在&#x200B;**「進程報告」**&#x200B;樹視圖上，按一下&#x200B;**「報告」**&#x200B;節點。
1. 按一下「**工作流卷**」報表節點。

   ![workflow_volume_node](assets/workflow_volume_node.png)

   選取報表時，樹狀檢視右側會顯示&#x200B;**報表參數**&#x200B;面板。

   ![長時間運行的進程報告參數面板](assets/workflow_volume_params.png)

   參數:

   * **選擇進程**(*強制*):選取AEM Forms程式。
   * **開始於** (*選用*):選擇日期。篩選報表以顯示指定日期之後開始的處理例項。
   * **開始於** (*選用*):選擇日期。篩選報表以顯示指定日期之前開始的處理例項。

1. 按一下&#x200B;**Go**&#x200B;以執行報表。

   報告顯示在&#x200B;**Process Reporting**&#x200B;窗口右側的&#x200B;**Report**&#x200B;面板中。

   ![workflow_volume_report](assets/workflow_volume_report.png)

   使用&#x200B;**Report**&#x200B;面板右上角的選項，對報表執行下列操作。

   * **重新整理**:重新整理報表，將最新資料放在儲存中
   * **更改圖例顏色**:選擇並更改報表圖例的顏色
   * **匯出至CSV**:將報表中的資料匯出及下載為逗號分隔的檔案

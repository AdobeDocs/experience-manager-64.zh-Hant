---
title: 適用於社群的FFmpeg
seo-title: 適用於社群的FFmpeg
description: 如何安裝和配置FFmpeg for Communities
seo-description: 如何安裝和配置FFmpeg for Communities
uuid: ef2f821c-70e9-4889-a8d7-a93b10a1d428
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 739ec991-552b-42cd-85cd-984d1c9fe8fd
role: Administrator
exl-id: 9ed54ee3-3509-4a43-a710-90f4543ccaf3
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# 社區的FFmpeg {#ffmpeg-for-communities}

## 概覽 {#overview}

FFmpeg是轉換和串流音訊與視訊的解決方案，安裝後可用來正確轉碼[視訊資產](../../help/sites-authoring/default-components-foundation.md#video)，以及AEM Communities的啟用功能。

FFmpeg用於製作環境，以取得上傳的啟用資源的中繼資料，並產生縮圖以在列出啟用資源時顯示。

## 安裝FFmpeg {#installing-ffmpeg}

FFmpeg應安裝在托管AEM *author*&#x200B;例項的伺服器上。

1. 前往[https://www.ffmpeg.org](https://www.ffmpeg.org/)
1. 下載適用於您特定環境（Macintosh、Windows或Linux）的最新版FFmpeg

   * 由於舊版中的安全漏洞，請務必保持FFmpeg最新

1. 按照作業系統的說明安裝FFmpeg。

1. 請確保在系統路徑中設定了FFmpeg執行檔。

   您應該可以從系統中的任何目錄運行FFmpeg。

   * 例如， `ffmpeg -version`

## 配置FFmpeg轉碼服務{#configure-ffmpeg-transcoding-service}

依預設，安裝FFmpeg時，會根據DAM更新資產工作流程定義來設定多個轉譯（轉譯）。

由於轉譯需要CPU資源，因此建議修改目標轉譯清單。 在大多數情況下，不需要轉碼。

若要修改「DAM更新資產」工作流程，並在此範例中，關閉轉碼：

* 以管理權限登入製作例項
* 從全局導航：**[!UICONTROL 工具>工作流>模型]**
* 找出&#x200B;**[!UICONTROL DAM更新資產]**
* 按兩下以開啟要在傳統UI中編輯的工作流程

   產生的位置：[http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html](http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html)

* 按兩下&#x200B;**[!UICONTROL FFmpeg轉碼]**&#x200B;步驟以訪問「步驟屬性」對話框
* 在&#x200B;**[!UICONTROL Process]**&#x200B;頁簽下：

   * **[!UICONTROL 圖]**:清除所有條目以禁用轉碼預設值：  `profile:firefoxhq,profile:hq,profile:flv,profile:iehq`

![chlimage_1-372](assets/chlimage_1-372.png)

* 選擇&#x200B;**[!UICONTROL OK]**&#x200B;以關閉`Step Properties`對話框

* 選擇&#x200B;**[!UICONTROL 保存]**&#x200B;以保存`DAM Update Asset`工作流

   （左上角）

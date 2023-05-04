---
title: 適用於社群的FFmpeg
seo-title: FFmpeg for Communities
description: 如何安裝和配置FFmpeg for Communities
seo-description: How to install and configure FFmpeg for Communities
uuid: ef2f821c-70e9-4889-a8d7-a93b10a1d428
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 739ec991-552b-42cd-85cd-984d1c9fe8fd
role: Admin
exl-id: 9ed54ee3-3509-4a43-a710-90f4543ccaf3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 2%

---

# 適用於社群的FFmpeg {#ffmpeg-for-communities}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 概觀 {#overview}

FFmpeg是轉換和串流音訊和視訊的解決方案，安裝後用於適當轉碼 [影片資產](../../help/sites-authoring/default-components-foundation.md#video) 以及AEM Communities啟用功能。

FFmpeg用於製作環境，以取得上傳的啟用資源的中繼資料，並產生縮圖以在列出啟用資源時顯示。

## 安裝FFmpeg {#installing-ffmpeg}

FFmpeg應安裝在托管AEM的伺服器上 *作者* 例項。

1. 前往 [https://www.ffmpeg.org](https://www.ffmpeg.org/)
1. 下載適用於您特定環境（Macintosh、Windows或Linux）的最新版FFmpeg

   * 由於舊版中的安全漏洞，請務必保持FFmpeg最新

1. 按照作業系統的說明安裝FFmpeg。

1. 請確保在系統路徑中設定了FFmpeg執行檔。

   您應該可以從系統中的任何目錄運行FFmpeg。

   * 例如， `ffmpeg -version`

## 配置FFmpeg轉碼服務 {#configure-ffmpeg-transcoding-service}

依預設，安裝FFmpeg時，會根據DAM更新資產工作流程定義來設定多個轉譯（轉譯）。

由於轉譯需要CPU資源，因此建議修改目標轉譯清單。 在大多數情況下，不需要轉碼。

若要修改「DAM更新資產」工作流程，並在此範例中，關閉轉碼：

* 以管理權限登入製作例項
* 從全局導航： **[!UICONTROL 「工具」>「工作流」>「模型」]**
* 找出 **[!UICONTROL DAM更新資產]**
* 按兩下以開啟要在傳統UI中編輯的工作流程

   產生的位置： [http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html](http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html)

* 按兩下 **[!UICONTROL FFmpeg轉碼]** 訪問「步驟屬性」對話框的步驟
* 在 **[!UICONTROL 程式]** 標籤：

   * **[!UICONTROL 區段]**:清除所有條目以禁用轉碼預設值： `profile:firefoxhq,profile:hq,profile:flv,profile:iehq`

![chlimage_1-372](assets/chlimage_1-372.png)

* 選擇 **[!UICONTROL 確定]** 關閉 `Step Properties` 對話

* 選擇 **[!UICONTROL 儲存]** 來儲存 `DAM Update Asset` 工作流程

   （左上角）

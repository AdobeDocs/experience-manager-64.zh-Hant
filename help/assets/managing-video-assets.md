---
title: 管理影片資產
description: 瞭解如何上傳、預覽、註解和發佈視訊資產。
uuid: 56a8c221-409f-4605-97b1-a054dd2abfab
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: f341fae1-dda3-4917-b6db-ad02fec63702
translation-type: tm+mt
source-git-commit: 38d3a204e3ef038ef4f848e12b9fc73f127ec488
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 8%

---


# 管理影片資產 {#managing-video-assets}

瞭解如何在Adobe Experience Manager(AEM)Assets中管理和編輯視訊資產。 此外，如果您取得使用Dynamic Media的授權，請參閱 [Dynamic Media Video檔案](video.md)。

## 上傳和預覽視訊資產 {#uploading-and-previewing-video-assets}

AEM Assets會使用副檔名MP4產生視訊資產的預覽。 如果資產的格式不是MP4，請安裝FFmpeg套件以產生預覽。 Fmpeg會建立OGG和MP4類型的視訊轉譯。 您可以在AEM Assets使用者介面中預覽這些轉譯。

1. 在「數位資產」檔案夾或子檔案夾中，導覽至您要新增數位資產的位置。
1. 若要上傳資產，請按一下或點選工 **[!UICONTROL 具列中的]** 「建立」，然後選擇「 **[!UICONTROL 檔案」]**。 或者，直接將它拖曳至資產區域。 如需 [上傳作業的詳細資訊](managing-assets-touch-ui.md#uploading-assets) ，請參閱上傳資產。
1. 若要在「卡片」檢視中預覽影片，請點選影 **[!UICONTROL 片資產]** 上的「播放」按鈕。

   ![chlimage_1-201](assets/chlimage_1-201.png)

   您只能在「卡片」檢視中暫停 **[!UICONTROL 或播放]** 影片。 「清單」檢視中無法使用「播放／暫 **[!UICONTROL 停]** 」按鈕。

1. 點選資 **[!UICONTROL 訊卡上的]** 「編輯」圖示，在「詳細資訊」檢視中預 **[!UICONTROL 覽視訊]** 。

   視訊會在瀏覽器的原生視訊播放器中播放。 您可以播放、暫停、控制音量，以及將視訊縮放至全螢幕。

   ![chlimage_1-202](assets/chlimage_1-202.png)

## 上傳大於2 GB資產的設定 {#configuration-to-upload-video-assets-that-are-larger-than-gb}

依預設，AEM資產不會讓您上傳任何大於2 GB的資產，因為檔案大小限制。 不過，您可以進入CRXDE Lite並在目錄下建立節點，以覆蓋此限 `/apps` 制。 節點必須具有相同的節點名稱、目錄結構和順序的可比節點屬性。

除了AEM Assets組態外，請變更下列組態以上傳大型資產：

* 增加代號過期時間。 請參 [!UICONTROL 閱網頁主控台中的] Adobe Granite CSRF Servlet `https://[aem_server]:[port]/system/console/configMgr`。 如需詳細資訊，請參 [閱CSRF保護](/help/sites-developing/csrf-protection.md)。
* 增加Dispatcher `receiveTimeout` 配置中的。 如需詳細資訊，請參 [閱Experience Manager Dispatcher設定](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#renders-options)。

>[!NOTE]
>
>AEM Classic使用者介面沒有2GB檔案大小限制。 此外，大型視訊的端對端工作流程也未完全受支援。

要配置較高的檔案大小限制，請在目錄中執行以下 `/apps` 步驟。

1. 在 AEM 中，點選&#x200B;**[!UICONTROL 「工具」>「一般」>「CRXDE Lite」]**。
1. 在 **[!UICONTROL CRXDE Lite]** 頁面的左側目錄視窗中，導覽至 `/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`。 要查看目錄窗口，請按一下「觸 `>>` 摸」表徵圖。
1. From the toolbar, tap **[!UICONTROL Overlay Node]**. 或者，從上 **[!UICONTROL 下文選單選取]** 「覆蓋節點」。
1. 在「覆蓋 **[!UICONTROL 節點」對話方]** ，點選「 **[!UICONTROL 確定」]**。

   ![chlimage_1-203](assets/chlimage_1-203.png)

1. 重新整理瀏覽器。 覆蓋節點 `/jcr_root/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload` 被選取。
1. 在「屬 **[!UICONTROL 性]** 」索引標籤中，輸入適當的值（以位元組為單位），將大小限制增加到所需大小。 例如，輸入下列值，將大小限制提高到30 GB:

   `{sizeLimit : "32212254720"}`

1. 在工具列中，點選「全 **[!UICONTROL 部儲存」]**。
1. 在AEM中，點選「 **[!UICONTROL 工具 > 作業 > Web Console]**」。
1. 在 **[!UICONTROL Adobe Experience Manager Web Console Bundles]** ( **[!UICONTROL Adobe Experience Manager Web Console Bundles]** )頁面的表格「Name **[!UICONTROL 」（名稱）欄下，找到並點選「]** Adobe Granite Workflow External Process Job Handler」。
1. In the **[!UICONTROL Adobe Granite Workflow External Process Job Handler]** page, set the seconds for both **[!UICONTROL Default Timeout]** and **[!UICONTROL Max Timeout]** fields to `18000` (five hours).
1. 點選「 **[!UICONTROL 儲存]**」。
1. 在AEM中，點選「工 **[!UICONTROL 具>工作流程>模型」]**。
1. 在「工作 **[!UICONTROL 流程模型]** 」頁面上，選 **[!UICONTROL 取「動態媒體編碼視訊]**」，然後點選「 **[!UICONTROL 編輯」]**。
1. 在「工 **[!UICONTROL 作流程]** 」頁面上，點選兩 **[!UICONTROL 下「動態媒體視訊服務程式」元件]** 。
1. 在「步 **[!UICONTROL 驟屬性]** 」對話框的「常用」頁籤下，展開「 **[!UICONTROL 高級設定」]******。
1. 在「逾 **[!UICONTROL 時]** 」欄位中，指定值 `18000`，然後點選「確定」以返回「動態媒體編碼 ******** 視訊」工作流程頁面。
1. 在頁面頂端的「動態媒體編碼視訊」頁 **[!UICONTROL 面標題下方]** ，點選「 **[!UICONTROL 儲存」]**。

## 發佈視訊資產 {#publishing-video-assets}

發佈視訊資產後，您就可透過URL或內嵌在網頁上，將其加入網頁。 請參閱 [發佈資產](publishing-dynamicmedia-assets.md)。

## 註解視訊資產 {#annotating-video-assets}

1. 從「資產」主控台，點選資 **[!UICONTROL 產卡片上的]** 「編輯」圖示以顯示資產詳細資訊頁面。
1. 點選「 **[!UICONTROL 預覽]** 」圖示以播放影片。
1. 若要註解視訊，請點選「注 **[!UICONTROL 解]** 」按鈕。 在視訊中的特定時點（畫格）加入註解。

   在加上註解時，您可以在畫布上繪圖，並在繪圖中加入註解。 注釋會自動儲存在Adobe Experience Manager Assets中。

   ![chlimage_1-204](assets/chlimage_1-204.png)

   要退出注釋嚮導，請按一下「關 **[!UICONTROL 閉」]**。

1. To jump to a specific point in the video, specify the time in seconds in the text field and click **[!UICONTROL Jump]**. For example, to skip the first 20 seconds of video, enter `20` in the text field.

   ![chlimage_1-205](assets/chlimage_1-205.png)

1. 按一下注釋可在時間軸中查看。 點選「 **[!UICONTROL 刪除]** 」(Delete)，從時間軸移除注釋。

   ![chlimage_1-206](assets/chlimage_1-206.png)

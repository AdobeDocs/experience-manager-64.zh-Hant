---
title: 管理影片資產
description: 了解如何上傳、預覽、注釋和發佈視訊資產。
uuid: 56a8c221-409f-4605-97b1-a054dd2abfab
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: f341fae1-dda3-4917-b6db-ad02fec63702
feature: Asset Management,Video
role: User
exl-id: eb652414-5b10-45af-a8b6-f1de649994c5
source-git-commit: 937c9425e276f67486fba1d4563799fe68d35cc7
workflow-type: tm+mt
source-wordcount: '787'
ht-degree: 8%

---

# 管理影片資產 {#managing-video-assets}

了解如何在Adobe Experience Manager Assets中管理和編輯視訊資產。 此外，如果您有權使用Dynamic Media，請參閱[Dynamic Media視訊檔案](video.md)。

## 上傳和預覽視訊資產 {#uploading-and-previewing-video-assets}

[!DNL Experience Manager] Assets會以MP4擴充功能產生視訊資產的預覽。如果資產的格式不是MP4，請安裝FFmpeg套件以產生預覽。 FFmpeg建立OGG和MP4類型的視頻轉譯。 您可以在[!DNL Experience Manager] Assets使用者介面中預覽這些轉譯。

1. 在「數位資產」資料夾或子資料夾中，導覽至您要新增數位資產的位置。
1. 若要上傳資產，請按一下或點選工具列中的「**[!UICONTROL 建立]**」，然後選擇「**[!UICONTROL 檔案]**」。 或者，直接將其拖曳至資產區域。 如需上傳操作的詳細資訊，請參閱[上傳資產](managing-assets-touch-ui.md#uploading-assets)。
1. 若要在「卡片」檢視中預覽視訊，請點選視訊資產上的&#x200B;**[!UICONTROL 播放]**&#x200B;按鈕。

   ![chlimage_1-201](assets/chlimage_1-201.png)

   您只能在&#x200B;**[!UICONTROL Card]**&#x200B;檢視中暫停或播放視訊。 **[!UICONTROL List]**&#x200B;檢視中沒有「播放/暫停」按鈕可用。

1. 點選卡片上的&#x200B;**[!UICONTROL Edit]**&#x200B;圖示，以在&#x200B;**[!UICONTROL Details]**&#x200B;檢視中預覽視訊。

   視訊會在瀏覽器的原生視訊播放器中播放。 您可以播放、暫停、控制音量，以及將視訊縮放至全螢幕。

   ![chlimage_1-202](assets/chlimage_1-202.png)

## 上傳大於2 GB資產的設定 {#configuration-to-upload-video-assets-that-are-larger-than-gb}

根據預設，由於檔案大小限制，[!DNL Experience Manager]資產不會讓您上傳超過2 GB的任何資產。 但是，您可以轉到CRXDE Lite並在`/apps`目錄下建立節點來覆寫此限制。 節點必須具有相同的節點名稱、目錄結構和順序的可比節點屬性。

除了[!DNL Experience Manager]資產設定，請變更下列設定以上傳大型資產：

* 增加代號過期時間。 請參閱`https://[aem_server]:[port]/system/console/configMgr`的Web主控台中的[!UICONTROL AdobeGranite CSRF Servlet]。 有關詳細資訊，請參見[CSRF protection](/help/sites-developing/csrf-protection.md)。
* 增加Dispatcher設定中的`receiveTimeout`。 如需詳細資訊，請參閱[Experience ManagerDispatcher設定](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#renders-options)。

>[!NOTE]
>
>[!DNL Experience Manager]傳統用戶介面沒有2 GB檔案大小限制。 此外，大型視訊的端對端工作流程也未完全支援。

要配置更高的檔案大小限制，請在`/apps`目錄中執行以下步驟。

1. 在 AEM 中，點選&#x200B;**[!UICONTROL 「工具」>「一般」>「CRXDE Lite」]**。
1. 在&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;頁的左側目錄窗口中，導航到`/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`。 要查看目錄窗口，請按`>>`表徵圖。
1. 從工具列中，點選&#x200B;**[!UICONTROL 覆蓋節點]**。 或者，從上 **[!UICONTROL 下文選單選取]** 「覆蓋節點」。
1. 在「覆蓋 **[!UICONTROL 節點」對話方]** ，點選「 **[!UICONTROL 確定」]**。

   ![chlimage_1-203](assets/chlimage_1-203.png)

1. 重新整理瀏覽器。 已選取覆蓋節點`/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`。
1. 在&#x200B;**[!UICONTROL Properties]**&#x200B;標籤中，以位元組為單位輸入適當值，以將大小限制增加到所需的大小。 例如，輸入`32212254720`值，將大小限制增加為30 GB。

1. 從工具列中，點選&#x200B;**[!UICONTROL 全部儲存]**。
1. 在AEM中，點選「 **[!UICONTROL 工具 > 作業 > Web Console]**」。
1. 在「**[!UICONTROL Adobe Experience Manager Web控制台套件組合]**」頁面的表格&#x200B;**[!UICONTROL 名稱]**&#x200B;欄下，找到並點選「AdobeGranite工作流程外部流程作業處理常式&#x200B;]**」。**[!UICONTROL 
1. 在「**[!UICONTROL AdobeGranite工作流外部進程作業處理程式]**」頁中，將&#x200B;**[!UICONTROL 預設超時]**&#x200B;和&#x200B;**[!UICONTROL 最大超時]**&#x200B;欄位的秒數設定為`18000`（5小時）。
1. 點選&#x200B;**[!UICONTROL 儲存]**。
1. 在AEM中，點選&#x200B;**[!UICONTROL 工具>工作流程>模型]**。
1. 在「**[!UICONTROL 工作流模型]**」頁上，選擇「**[!UICONTROL Dynamic Media編碼視頻]**」，然後點選「**[!UICONTROL 編輯]**」。
1. 在&#x200B;**[!UICONTROL Workflow]**&#x200B;頁面上，點選兩下&#x200B;**[!UICONTROL Dynamic Media視訊服務程式]**&#x200B;元件。
1. 在「步 **[!UICONTROL 驟屬性]** 」對話框的「常用」頁籤下，展開「 **[!UICONTROL 高級設定」]******。
1. 在「逾 **[!UICONTROL 時]** 」欄位中，指定值 `18000`，然後點選「確定」以返回「動態媒體編碼 ******** 視訊」工作流程頁面。
1. 在頁面頂端附近，在&#x200B;**[!UICONTROL Dynamic Media編碼視訊]**&#x200B;頁面標題下方，點選&#x200B;**[!UICONTROL 儲存]**。

## 發佈視訊資產 {#publishing-video-assets}

視訊資產發佈後，您就可以透過URL或內嵌在網頁中，加入這些資產。 請參閱[發佈資產](publishing-dynamicmedia-assets.md)。

## 為視訊資產加上注釋 {#annotating-video-assets}

1. 從「資產」主控台，點選資產卡片上的&#x200B;**[!UICONTROL 編輯]**&#x200B;圖示，以顯示資產詳細資訊頁面。
1. 點選&#x200B;**[!UICONTROL 預覽]**&#x200B;圖示以播放視訊。
1. 若要為視訊加上注釋，請點選&#x200B;**[!UICONTROL Annotate]**&#x200B;按鈕。 在視訊中的特定時間點（幀）新增附註。

   在批注時，您可以在畫布上繪圖，並在繪圖中包括注釋。 註解會自動儲存在Adobe Experience Manager Assets中。

   ![chlimage_1-204](assets/chlimage_1-204.png)

   要退出注釋嚮導，請點選&#x200B;**[!UICONTROL Close]**。

1. 若要跳至視訊中的特定點，請在文字欄位中指定時間（以秒為單位），然後按一下&#x200B;**[!UICONTROL Jump]**。 例如，若要略過前20秒的視訊，請在文字欄位中輸入`20`。

   ![chlimage_1-205](assets/chlimage_1-205.png)

1. 按一下注釋以在時間軸中查看。 點選&#x200B;**[!UICONTROL Delete]**&#x200B;以從時間軸中移除註解。

   ![chlimage_1-206](assets/chlimage_1-206.png)

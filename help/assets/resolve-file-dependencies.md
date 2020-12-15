---
title: 解決檔案相依性
seo-title: 解決檔案相依性
description: 如何在自動解析失敗時解決3D檔案相依性，例如紋理映射檔案。
seo-description: 如何在自動解析失敗時解決3D檔案相依性，例如紋理映射檔案。
uuid: 49cefabf-147b-4a78-90f3-0f2d6a8e8cae
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 05b7410b-82a1-4267-ac07-2edbc29e9ee8
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---


# 解決檔案相關性{#resolving-file-dependencies}

主要3D模型檔案相依性（例如紋理映射檔案）會盡可能自動解析。 此功能是透過讓AEM在Asset檔案夾附近搜尋3D檔案中具有相同名稱的檔案來完成。 如果在「建立預覽處理」階段中無法解析一或多個相依性，資產的資訊卡會在「資訊卡檢視」**[!UICONTROL 中顯示下列紅色橫幅訊息：]**

![chlimage_1-124](assets/chlimage_1-124.png)

**要解決檔案依賴性**:

1. 在&#x200B;**[!UICONTROL 卡片檢視]**&#x200B;中，將指標暫留在卡片上的&#x200B;**[!UICONTROL 未解決的相依性]**&#x200B;橫幅訊息上，然後點選&#x200B;**[!UICONTROL 驚嘆號]**&#x200B;圖示。

   ![chlimage_1-125](assets/chlimage_1-125.png)

1. 在「**[!UICONTROL 中繼資料屬性]**」頁面上，點選「**[!UICONTROL 相依性]**」標籤。

   AEM無法自動解析的檔案會列在&#x200B;**[!UICONTROL 原始路徑]**&#x200B;欄下方，以紅色表示。

1. 執行下列一或多個作業：

   * **瀏覽並選擇相依項**。(此選項假定您已上傳相關檔案。

      1. 點選紅色路徑左側的&#x200B;**[!UICONTROL 檔案瀏覽]**&#x200B;圖示。
      1. 在&#x200B;**[!UICONTROL 選擇內容]**&#x200B;頁面上，瀏覽至遺失的檔案，然後點選檔案的卡片以選取它。
      1. 在&#x200B;**[!UICONTROL 選擇內容]**&#x200B;頁的左上角，點選&#x200B;**[!UICONTROL 關閉]**（X圖示）以返回&#x200B;**[!UICONTROL 查看屬性]**&#x200B;頁。
   * **上傳相依性**。（此選項假設您尚未上傳遺失的檔案。）

      1. 請注意遺失的路徑和檔案名稱。
      1. 在屬性頁面的右上角附近，點選&#x200B;**[!UICONTROL Close]**。

   上傳檔案後，會返回至「檢視屬性>相依性&#x200B;**[!UICONTROL 」頁面。]**&#x200B;新上傳的資產現在會正確列為參考的資產。

   * **忽略相依項**。

      如果不再需要遺失的相依性，請在&#x200B;**[!UICONTROL 參考資產]**&#x200B;欄下，在遺失檔案左側的文字欄位中輸入`n/a`，讓AEM 3D忽略檔案。



1. 在&#x200B;**[!UICONTROL 檢視屬性]**&#x200B;頁面的右上角，點選&#x200B;**[!UICONTROL 儲存]**。
1. 點選「**[!UICONTROL 關閉]**」返回「卡片檢視」。****

   資產會自動重新處理，並具有新解析的相依性。


---
title: 搜尋視訊資產
description: 使用關鍵字、檔案屬性（如Mime類型、大小或最近修改的時間戳記），快速在中找到您的檔案 [!DNL Experience Manager] 資產。
contentOwner: AG
feature: Video,Search
role: User
exl-id: d5f0beb2-e59f-47cd-8e83-698d8a1dcec3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 3%

---

# 搜尋視訊資產 {#searching-video-assets}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

為了節省瀏覽可能數百個視訊的時間和精力，請使用關鍵字、檔案屬性（如檔案類型）或最近修改的時間戳記來快速找到您的檔案。

如果您沒有看到要查找的檔案，可以按一下搜索結果底部的選項之一來更改搜索的整個範圍。 例如，如果在文檔庫中搜索檔案，但找不到該檔案，則可以按一下庫，將搜索展開到其餘的庫。 如需詳細資訊，請參閱 [查找檔案或資料夾](https://windows.microsoft.com/en-us/windows7/find-a-file-or-folder).

您可以根據下列一或多個屬性來搜尋數位資產：

| 搜尋欄位 | 搜索屬性值 |
|---|---|
| Mime 類型 | [!UICONTROL 影像], [!UICONTROL 檔案], [!UICONTROL 多媒體], [!UICONTROL 封存]，或其他 |
| [!UICONTROL 上次修改時間] | 小時、日、周、月或年。 |
| [!UICONTROL 檔案大小] | 小、中或大。 |
| [!UICONTROL 發佈] 狀態 | 已發佈或未發佈。 |
| [!UICONTROL 核准] 狀態 | 已核准或已拒絕。 |
| [!UICONTROL 方向] | 水準、垂直或方形。 |
| [!UICONTROL Style] | 顏色或黑白。 |
| 視訊高度 | 指定為最小值和最大值。值僅儲存在視訊轉譯的中繼資料中。 |
| 視訊寬度 | 指定為最小值和最大值。值僅儲存在視訊轉譯的中繼資料中。 |
| 視訊格式 | DVI、Flash、MPEG4、MPEG、OGG Theora、QuickTime、Windows Media。Value儲存在源視頻和任何格式副本的元資料中。 |
| 視訊轉碼器 | x264.值只會儲存在視訊轉譯的中繼資料中。 |
| 視訊位元速率 | 指定為最小值和最大值。值僅儲存在視訊轉譯的中繼資料中。 |
| 音訊轉碼器 | Libvorbis、Lame Mp3、AAC Encoding.Value僅儲存在視頻轉譯的元資料中。 |
| 音訊位元速率 | 指定為最小值和最大值。值僅儲存在視訊轉譯的中繼資料中。 |

1. 在 **[!UICONTROL Experience Manager]** 頁面，在左側邊欄中，點選 **[!UICONTROL 資產]**.

   如果左側邊欄不可見，請點選「切換邊欄」圖示（圖示中的線段會是深灰色或藍色）。

1. 開啟最能作為搜尋起點的資料夾。
1. 在工具列上，點選「搜尋」圖示（放大鏡）。
1. 執行下列任一操作來搜尋視訊資產：

   * 使用關鍵字進行搜索

      在「輸入關鍵字」欄位中，開始鍵入，然後按Enter鍵。

      系統會根據您輸入的關鍵字來篩選目前的檢視。 如果您的關鍵字與檔案的名稱、中繼資料標籤或其他屬性相符，則檔案會顯示為搜尋結果。

   * 使用屬性進行搜索

      若要根據視訊類型等屬性來搜尋視訊檔案，您可以選取視訊或音訊屬性來縮小搜尋範圍。 例如，展開「視訊格式」下拉式清單，然後檢查一或多個值。 有些屬性會要求您輸入最小值和最大值。

   * 使用關鍵字和屬性進行搜索

      輸入關鍵字，而非按Enter，請展開視訊或音訊屬性清單，然後設定您想要的值。

1. （可選）在頁面底部附近，點選 **[!UICONTROL 儲存智慧型集合]**，輸入搜尋的名稱。 檢查 **[!UICONTROL 公開]** 如果您希望已儲存的搜尋可供Adobe Experience Manager帳戶的其他使用者使用。 如果希望搜索僅在登錄到帳戶時才可供使用，請取消選中。 點選 **[!UICONTROL 儲存]**.

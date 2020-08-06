---
title: 視訊轉譯
description: 視訊轉譯
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# 視訊轉譯 {#video-renditions}

Adobe Experience Manager(AEM)Assets會針對各種格式的視訊資產產生視訊轉譯，包括OGG、FLV等。

AEM Assets支援媒體資產的靜態和動態轉譯（DM編碼轉譯）。

靜態轉譯是使用FFMPEG（安裝在系統路徑上且可用）以原生方式產生，並儲存在內容儲存庫中。

DM編碼的轉譯會儲存在Proxy伺服器中，並在執行時期提供。

AEM資產在用戶端上提供這些轉譯的播放支援。

若要檢視特定視訊資產的轉譯，請開啟其資產頁面，然後點選「全域導覽」圖示。 然後，從清 **[!UICONTROL 單中選擇]** 「轉譯」。

![chlimage_1-478](assets/chlimage_1-478.png)

視訊轉譯的清單會顯示在「轉譯 **[!UICONTROL 」面板中]** 。

![chlimage_1-479](assets/chlimage_1-479.png)

若要為DM編碼轉譯配置代理伺服器，請 [配置Dynamic Media Cloud服務。](config-dynamic.md)

若要使用所需參數產生視訊轉譯，請 [建立對應的視訊描述檔](video-profiles.md)。

在您設定代理伺服器並建立視訊設定檔後，您可以將此視訊預設集加入處理設定檔，並將處理設定檔套用至資料夾。

>[!NOTE]
>
>在Internet Explorer 11上，OGG和WAV檔案無法播放音訊。 副檔名為OGG或WAV的資產，在資產詳細資料頁面上會顯示錯誤「無效來源」。
>
>在MS Edge和iPad上，OGG檔案不會播放，並產生「不支援的格式」錯誤。

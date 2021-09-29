---
title: 視訊轉譯
description: 視訊轉譯
contentOwner: AG
feature: Video,Renditions
role: User
exl-id: 9fc93034-e83a-42b5-901d-7867b4a850a8
source-git-commit: 1e3cd6ce3138113721183439f7cfb9daed6e0e58
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---

# 視訊轉譯 {#video-renditions}

Adobe Experience Manager Assets會針對各種格式的視訊資產產生視訊轉譯，包括OGG、FLV等。

AEM Assets支援媒體資產的靜態和動態轉譯（DM編碼的轉譯）。

靜態轉譯是使用FFMPEG（安裝在系統路徑上且可用）以原生方式產生，並儲存在內容存放庫中。

DM編碼的轉譯會儲存在代理伺服器中，並在執行階段提供。

AEM資產在用戶端上為這些轉譯提供播放支援。

若要檢視特定視訊資產的轉譯，請開啟其資產頁面，然後點選「全域導覽」圖示。 然後，從清單中選擇&#x200B;**[!UICONTROL 轉譯]**。

![chlimage_1-478](assets/chlimage_1-478.png)

視訊轉譯清單會顯示在&#x200B;**[!UICONTROL 轉譯]**&#x200B;面板中。

![chlimage_1-479](assets/chlimage_1-479.png)

若要為DM編碼的轉譯設定代理伺服器，請[設定Dynamic Media雲端服務。](config-dynamic.md)

若要使用所需參數產生視訊轉譯，請[建立對應的視訊設定檔](video-profiles.md)。

設定代理伺服器並建立視訊設定檔後，您可以將此視訊預設集包含在處理設定檔中，並將處理設定檔套用至資料夾。

>[!NOTE]
>
>Internet Explorer 11上的OGG和WAV檔案無法播放音訊。 副檔名為OGG或WAV的資產詳細資訊頁面上會顯示「來源無效」錯誤。
>
>在MS Edge和iPad上，OGG檔案不會播放，並引發「不支援的格式」錯誤。

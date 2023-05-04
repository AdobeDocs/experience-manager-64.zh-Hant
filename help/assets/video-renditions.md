---
title: 視訊轉譯
description: 視訊轉譯
contentOwner: AG
feature: Video,Renditions
role: User
exl-id: 9fc93034-e83a-42b5-901d-7867b4a850a8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 2%

---

# 視訊轉譯 {#video-renditions}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets會針對各種格式的視訊資產產生視訊轉譯，包括OGG、FLV等。

AEM Assets支援媒體資產的靜態和動態轉譯（DM編碼的轉譯）。

靜態轉譯是使用FFMPEG（安裝在系統路徑上且可用）以原生方式產生，並儲存在內容存放庫中。

DM編碼的轉譯會儲存在代理伺服器中，並在執行階段提供。

AEM資產在用戶端上為這些轉譯提供播放支援。

若要檢視特定視訊資產的轉譯，請開啟其資產頁面，然後點選「全域導覽」圖示。 然後，選擇 **[!UICONTROL 轉譯]** 從清單中。

![chlimage_1-478](assets/chlimage_1-478.png)

視訊轉譯的清單會顯示在 **[!UICONTROL 轉譯]** 中。

![chlimage_1-479](assets/chlimage_1-479.png)

若要為DM編碼的轉譯設定代理伺服器， [設定Dynamic Media雲端服務。](config-dynamic.md)

若要使用所需參數產生視訊轉譯， [建立對應的視訊設定檔](video-profiles.md).

設定代理伺服器並建立視訊設定檔後，您可以將此視訊預設集包含在處理設定檔中，並將處理設定檔套用至資料夾。

>[!NOTE]
>
>Internet Explorer 11上的OGG和WAV檔案無法播放音訊。 副檔名為OGG或WAV的資產詳細資訊頁面上會顯示「來源無效」錯誤。
>
>在MS Edge和iPad上，OGG檔案不會播放，且會引發「不支援的格式」錯誤。

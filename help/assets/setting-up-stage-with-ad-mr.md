---
title: 用Autodesk Maya和Mental Ray建立標準舞台
seo-title: 用Autodesk Maya和Mental Ray建立標準舞台
description: Autodesk Maya與Mental Ray如何搭建標準舞台
seo-description: Autodesk Maya與Mental Ray如何搭建標準舞台
uuid: 3895fda6-29ae-46f5-b2bc-abc989808648
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: da8fc33b-84ae-4ead-87bb-5a7870a38b1f
translation-type: tm+mt
source-git-commit: 4b05b24a91ba9c31a19a5a96fb481d2ffc4c9bfc
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---


# 使用Autodesk Maya和Mental Ray {#setting-up-a-standard-stage-with-autodesk-maya-and-mental-ray}建立標準舞台

1. 在瑪雅，創造一個新的空曠場景。
1. 建立代表模型的（臨時）引用。 如此有助於評估光源、設定相機和設定轉譯器。

1. 照常加燈。 目前，AEM 3D支援下列光源類型：

   * 方向燈
   * 專色燈
   * 點光源

   當舞台上傳至AEM 3D時，其他光線類型會被忽略或轉換為上述支援的其中一種類型。 當您檢視資產時，以及使用內建的快速調整轉譯器進行演算時，會使用轉換的類型。 使用Maya演算時，會使用原始的光源類型。

1. 建立接地平面（如果需要），並應用合適的材料。

   Adobe建議您將地面平面設為單面。 如此可確保您可以在AEM 3D中從下方檢視資產，而不需隱藏底層平面。

1. （可選）建立和設定相機。

   讓相機向要插入資產的場景中心「看」。 請確定您已將相機設定為可轉譯。

1. 使用Mental Ray建立演算。

   使用下列建議設定「演算設定」:

   * **[!UICONTROL 公]** 用標籤

      取消選中所有可轉換相機的&#x200B;**[!UICONTROL Alpha色版（遮色片）]**&#x200B;複選框。

   * **[!UICONTROL Qualitytab]** 

      * **[!UICONTROL 整體]** `- 0.5` 品質或以下
      * **[!UICONTROL 間接擴散(GI)模式]** -  `Final Gather`
      * **[!UICONTROL 篩選大小]** -  `2.0`、  `2.0`
   * 以您預期使用的一般影像大小來轉換場景。 視需要調整光源或「演算」設定，或兩者皆可達成所需結果。

      請注意，使用Mental Ray進行演算時，使用影像光源會非常緩慢，而且需要耗用大量CPU。 Adobe建議您設定仍能產生所需演算品質的最低品質設定。


1. 刪除在步驟2中建立的參照。

1. 儲存場景，然後退出Autodesk Maya。
1. 將場景上傳至AEM，並等待上傳處理完成。

   請參閱[上傳資產](managing-assets-touch-ui.md#uploading-assets)。

   如果AEM伺服器上未設定Autodesk® Maya®，請從Maya匯出FBX並上傳至AEM。

1. 在AEM中開啟資產屬性。 將&#x200B;**[!UICONTROL Title]**&#x200B;設定為適當的字串，該字串將出現在&#x200B;**[!UICONTROL 舞台選擇器]**&#x200B;下拉式清單中。 驗證&#x200B;**[!UICONTROL Class]**&#x200B;是否設定為&#x200B;**[!UICONTROL 3D Stage]**。 儲存並退出。
1. 開啟3D資產、選取新階段，並驗證它是否預覽並如預期呈現。


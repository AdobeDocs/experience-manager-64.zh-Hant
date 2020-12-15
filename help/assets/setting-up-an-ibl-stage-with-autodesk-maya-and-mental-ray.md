---
title: 用Autodesk Maya和Mental Ray建立IBL舞台
seo-title: 用Autodesk Maya和Mental Ray建立IBL舞台
description: Autodesk Maya與Mental Ray如何搭建IBL舞台
seo-description: Autodesk Maya與Mental Ray如何搭建IBL舞台
uuid: 353ff561-0d30-4d62-8cad-68890c883c92
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 752e521f-198f-425a-abfa-051993f9c694
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---


# 使用Autodesk Maya和Mental Ray {#setting-up-an-ibl-stage-with-autodesk-maya-and-mental-ray}設定IBL舞台

1. 在瑪雅，創造一個新的空曠場景。

1. 建立代表模型的（臨時）引用。 如此有助於評估光源、設定相機和設定轉譯器。
1. 設定影像光源。

   1. 在&#x200B;**[!UICONTROL Render Settings]**&#x200B;中，選擇&#x200B;**[!UICONTROL Render Render Using:mentalray]**，並開啟「場景」標籤。
   1. 開啟&#x200B;**[!UICONTROL Render Environment]** accordion，然後按一下&#x200B;**[!UICONTROL Render Create Image Based Lighting]**。
   1. 按一下框表徵圖，該表徵圖在框的左側具有右箭頭，以選擇IBL節點`mentalRayIblShape1`，然後退出&#x200B;**[!UICONTROL 渲染設定]**。
   1. 在&#x200B;**[!UICONTROL 屬性編輯器]**&#x200B;中，選擇轉換節點`mentalRayIbl1`，然後將轉換節點更名為`AdobeIbl`。
   1. 設定節點的「縮放」(Scale of the node)，使環境球體顯著大於此階段中要顯示的最大3D對象（例如`10000,10000,10000`）。
   1. 選擇`AdobeIblShape`節點，並按如下方式進行配置：

      * **[!UICONTROL 映射]** -球形
      * **[!UICONTROL 類型]** -影像檔案
      * **[!UICONTROL 發光]** -真
   1. 將所需的32位元TIFF影像附加至`AdobeIbl`節點。


1. 設定地面飛機。

   * 建立適合的平面作為接地平面，並調整其大小以合理擬合IBL球體，通過坐標原點。
   * 將&#x200B;**[!UICONTROL 使用背景]**&#x200B;材料附加到接地平面並將其命名為`AdobeUseBackground`並將其附加到接地平面對象。

1. （可選）建立和設定相機。

   讓相機向要插入資產的場景中心「看」。 請確定您已將相機設定為可轉譯。

1. 使用Mental Ray建立演算。

   使用下列建議設定「演算設定」。****

   * **[!UICONTROL 公]** 用標籤

      取消選中所有&#x200B;**[!UICONTROL 可轉換相機]**&#x200B;的&#x200B;**[!UICONTROL Alpha色版（遮色片）]**&#x200B;核取方塊。

   * **[!UICONTROL Qualitytab]** 

      * **整體品質** -或 `0.5` 更低
      * **間接擴散(GI)模式** -  `Final Gather`
      * **篩選大小** -  `2.0`、  `2.0`
   * 以您預期使用的一般影像大小來轉換場景。 視需要調整光源、演算設定或兩者，以達成您想要的結果。

      請注意，使用Mental Ray進行演算時，使用影像光源會非常緩慢，而且需要耗用大量CPU。 Adobe建議您設定仍能產生所需演算品質的最低品質設定。


1. 刪除在步驟2中建立的參照。

1. 儲存場景，然後退出Autodesk Maya。

1. 將場景和IBL PTIFF上傳至AEM，並等待上傳處理完成。

   請參閱[上傳資產](managing-assets-touch-ui.md#uploading-assets)。

1. 解決任何檔案相依性。

   請參閱[解決檔案相關性](resolve-file-dependencies.md)。

   AEM 3D可能無法偵測在舞台中設定的IBL影像。 在這種情況下，必須手動解決缺少的從屬關係。 您可以為每個缺失的從屬關係指定相同的先前上載IBL PTIFF影像。 或者，您可以指派不同的影像來進一步控制IBL效果。 解決相依性後，請務必點選&#x200B;**[!UICONTROL Save]**&#x200B;以開始重新處理。

1. 在AEM中開啟資產屬性。 將&#x200B;**[!UICONTROL Title]**&#x200B;設定為適當的字串，該字串將出現在&#x200B;**[!UICONTROL 舞台選擇器]**&#x200B;下拉式清單中。 驗證&#x200B;**[!UICONTROL Class]**&#x200B;是否設定為&#x200B;**[!UICONTROL 3D Stage]**。 儲存並退出。

1. 開啟3D資產、選取新階段，並驗證它是否預覽並如預期呈現。


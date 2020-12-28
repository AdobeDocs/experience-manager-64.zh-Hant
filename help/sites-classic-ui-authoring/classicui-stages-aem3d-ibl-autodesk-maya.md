---
title: 用Autodesk Maya和Mental Ray建立IBL舞台
seo-title: 用Autodesk Maya和Mental Ray建立IBL舞台
description: 瞭解如何使用Autodesk Maya和Mental Ray建立IBL舞台。
seo-description: 瞭解如何使用Autodesk Maya和Mental Ray建立IBL舞台。
uuid: 99878112-74c1-4a52-a7c2-c39927ce0e2a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 00f7ed25-276b-42c2-ae4c-11de357a9ec6
translation-type: tm+mt
source-git-commit: e0ce860380a28a9dcaa6f8ce94ad278cdbe49fad
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---


# 使用Autodesk Maya和Mental Ray設定IBL舞台{#setting-up-an-ibl-stage-with-autodesk-maya-and-mental-ray}

1. 在瑪雅，創造一個新的空曠場景。

1. 建立代表模型的（臨時）引用。 如此有助於評估光源、設定相機和設定轉譯器。
1. 設定影像光源。

   1. 在渲染設定中，選擇&#x200B;**[!UICONTROL 渲染使用：mentalray]**，並開啟&#x200B;**[!UICONTROL Scene]**&#x200B;標籤。
   1. 開啟&#x200B;**[!UICONTROL Environment]** accordion，然後按一下&#x200B;**[!UICONTROL 建立基於影像的照明]**。
   1. 按一下框表徵圖（框表徵圖在框的左側有右箭頭）以選擇IBL節點`mentalRayIblShape1`，然後退出「渲染設定」(Render Settings)]。[!UICONTROL 
   1. 在&#x200B;**[!UICONTROL 屬性編輯器]**&#x200B;中，選擇轉換節點`mentalRayIbl1`，然後將轉換節點更名為`AdobeIbl`。

   1. 設定節點的[!UICONTROL Scale]，使環境球體顯著大於此階段中要顯示的最大3D對象（例如`10000,10000,10000`）。
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

   使用下列建議設定「演算設定」。

   * **[!UICONTROL 公]** 用標籤

      取消選中所有可轉換相機的&#x200B;**[!UICONTROL Alpha色版（遮色片）]**&#x200B;複選框。

   * **[!UICONTROL Qualitytab]** 

      * **[!UICONTROL 整體品質]** -或 `0.5` 更低
      * **[!UICONTROL 間接擴散(GI)模式]** -  `Final Gather`
      * **[!UICONTROL 篩選大小]** -  `2.0`、  `2.0`
   * 以您預期使用的一般影像大小來轉換場景。 視需要調整光源、演算設定或兩者，以達成您想要的結果。

      請注意，使用Mental Ray進行演算時，使用影像光源會非常緩慢，而且需要耗用大量CPU。 Adobe建議您設定仍能產生所需演算品質的最低品質設定。


1. 刪除在步驟2中建立的參照。

1. 儲存場景，然後退出Autodesk Maya。

1. 將場景和IBL PTIFF上傳至AEM，並等待上傳處理完成。

   請參閱[上傳資產](/help/assets/managing-assets-touch-ui.md#uploading-assets)。

1. 解決任何檔案相依性。

   請參閱[解決檔案相關性](/help/sites-classic-ui-authoring/classicui-upload-proc-3d-resolve-dependencies.md)。

   AEM 3D可能無法偵測在舞台中設定的IBL影像。 在這種情況下，必須手動解決缺少的從屬關係。 您可以為每個缺失的從屬關係指定相同的先前上載IBL PTIFF影像。 或者，您可以指派不同的影像來進一步控制IBL效果。 解決相依性後，請務必點選&#x200B;**Save**&#x200B;以開始重新處理。

1. 在AEM中開啟資產屬性。 將「標題」設定為將出現在「舞台選擇器」下拉式清單中的適當字串。 驗證&#x200B;**[!UICONTROL Class]**&#x200B;是否設定為&#x200B;**[!UICONTROL 3D Stage]**。 儲存並退出。

1. 開啟3D資產、選取新階段，並驗證它是否預覽並如預期呈現。


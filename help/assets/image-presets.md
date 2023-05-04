---
title: 套用Dynamic Media影像預設集
seo-title: Applying Dynamic Media image presets
description: 了解如何在Dynamic Media中套用影像預設集
seo-description: Learn how to apply image presets in Dynamic Media
uuid: 8bafcbd0-6df0-4d5b-b2f7-116ddb4ec060
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 5c1f60ac-3741-4002-9c5d-c128f118342b
exl-id: 07a4f315-a60e-456b-b02d-035b3f6ad9ad
feature: Image Presets
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 10%

---

# 套用Dynamic Media影像預設集 {#applying-image-presets}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

「影像預設集」可讓資產以動態方式傳送不同大小、不同格式的影像，或以其他動態產生的影像屬性。 在導出影像時，可以選擇預設集，該預設集還會按照管理員指定的規範重新格式化影像。

此外，您也可以選擇回應式(由 **[!UICONTROL RESS]** 按鈕)。

本節說明如何使用影像預設集。 [管理員可以建立和配置影像預設集](managing-image-presets.md).

>[!NOTE]
>
>智慧型影像處理可與您現有的影像預設集搭配使用，並會在傳送時的最後毫秒內運用智慧，根據瀏覽器或網路連線速度進一步縮小影像檔案大小。 請參閱 [智慧型影像](imaging-faq.md) 以取得更多資訊。

您可以隨時預覽影像，將影像預設集套用至影像。

**套用Dynamic Media影像預設集**:

1. 開啟資產，在左側導軌中，點選下拉式選單，然後點選 **[!UICONTROL 轉譯]**.

   >[!NOTE]
   >
   >* 靜態轉譯會顯示在窗格的上半部。 動態轉譯會顯示在下半部。 僅限動態轉譯，您可以使用URL來顯示影像。 此 **[!UICONTROL URL]** 按鈕時，僅當您選取動態轉譯時才會顯示。 此 **[!UICONTROL RESS]** 按鈕時，才會顯示。
   >
   >* 當您選取 **[!UICONTROL 轉譯]** 在資產的「詳細資料」檢視中。 您可以增加所檢視的預設集數目。請參閱 [增加顯示的影像預設集數目](managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display).


   ![chlimage_1-208](assets/chlimage_1-208.png)

1. 執行下列任一操作：

   * 選取動態轉譯以預覽影像預設集。
   * 點選 **[!UICONTROL URL]**, **[!UICONTROL 內嵌]**，或 **[!UICONTROL RESS]** 以顯示快顯視窗。

   >[!NOTE]
   >
   >如果資產和 *影像預設集尚未發佈* ，則 **[!UICONTROL URL按鈕(或]** URL **[!UICONTROL 和]****** RESS按鈕 (如果適用) 不可用。
   >
   >另請注意，影像預設集會自動發佈在Dynamic Media伺服器上。

---
title: Target與體驗片段整合
seo-title: Target與體驗片段整合
description: Target與體驗片段整合
seo-description: Target與體驗片段整合
uuid: 621f57d4-3b8d-49ea-b193-8530c8fbd74e
contentOwner: carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6911c8e3-b12c-466e-8255-5dcd09557d35
translation-type: tm+mt
source-git-commit: 4e5d3c0ae71f601bcf39fa768c8b5ac86decc1eb
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 0%

---


# Target與體驗片段整合{#target-integration-with-experience-fragments}

>[!NOTE]
>
>此功能需要 [AEM 6.4 Service Pack 2(6.4.2.0)或更新版本的應用程式](/help/release-notes/sp-release-notes.md) 。

您可以將 [在Adobe Experience Manager](/help/sites-authoring/experience-fragments.md)(AEM)中建立的Experience片段匯出至Adobe Target。 然後，您就可以在Target活動中將它們當做選件，以大規模測試和個人化體驗。 這可讓您結合AEM的簡單易用和強大功能，以及Target中的強大自動智慧(AI)和機器學習(ML)功能。

## 必備條件 {#prerequisites}

需要執行各種動作：

1. 您必須將AEM與Target整合。 如需 [詳細資訊，請參閱「與Adobe Target整合](/help/sites-administering/target.md) 」。
1. 體驗片段是從作者例項匯出，因此您必須在作者例項上設定連結外部化 [](/help/sites-developing/externalizer.md) ，以確保發佈例項的任何連結外部化。

## 新增雲端設定 {#add-the-cloud-configuration}

在匯出片段之前，您需要將 **Adobe Target的Cloud Configuration** （雲端設定）新增至 **** 片段或資料夾：

1. 導覽至 **Experience片段主控台** 。
1. 開啟 **適當資料夾** 或片段的頁面屬性。

   >[!NOTE]
   >
   >如果您將雲端設定新增至「體驗片段」父資料夾，則所有子資料夾都會繼承此設定。
   >
   >如果您將雲端組態新增至Experience Fragment本身，則所有變數都會繼承組態。

1. 選擇「 **雲端服務** 」標籤。

1. 在「 **雲端服務設定**」下方，從下拉式清 **單中選取「Adobe Target** 」。
1. 在 **Adobe Target下**，選取適當的設定。

1. **儲存並關閉**.

## 將體驗片段匯出至Target {#exporting-an-experience-fragment-to-target}

>[!NOTE]
>
>對於媒體資產（例如影像），只會將參考匯出至Target。 資產本身仍會儲存在AEM Assets中，並會從AEM發佈例項傳送。
>
>因此，必須先發佈包含所有相關資產的體驗片段，再匯出至Target。

若要將體驗片段從AEM匯出至Target（在指定雲端設定後）:

1. 導覽至體驗片段主控台。
1. 選取您要匯出至目標的體驗片段。

   >[!NOTE]
   >
   >它必須是體驗片段Web變數。

1. 點選／按一 **下「匯出至Adobe Target**」。

   >[!NOTE]
   >
   >如果體驗片段已匯出，請在Adobe Target中選 **取「更新」**。

1. 點選／按一 **下「匯出」，不需發佈** , **或視需要發佈** 。

   >[!NOTE]
   >
   >選取** Publish**將立即發佈體驗片段並傳送至Target。

1. 點選／按一 **下確認** 對話方塊中的確定。

   您的體驗片段現在應該位於Target中。

>[!NOTE]
>
>或者，您也可以使用「頁面資訊」功能表中的類似指令，從頁面編輯器 [執行匯出](/help/sites-authoring/author-environment-tools.md#page-information) 。

## 在Target中使用您的體驗片段 {#using-your-experience-fragments-in-target}

執行前述工作後，體驗片段會顯示在Target的「選件」頁面上。 請檢視特定的Target [檔案](https://experiencecloud.adobe.com/resources/help/en_US/target/target/aem-experience-fragments.html) ，以瞭解您可在其中取得哪些成果。

## 刪除已匯出至Target的體驗片段 {#deleting-an-experience-fragment-already-exported-to-target}

刪除已匯出至Target的體驗片段，如果該片段已用於Target中的選件，可能會造成問題。 當AEM傳送片段內容時，刪除片段會導致選件無法使用。

要避免這種情況：

* 如果「體驗片段」目前未用於活動，AEM可讓使用者刪除片段，而不會顯示警告訊息。
* 如果Target中的活動目前正在使用體驗片段，則會出現錯誤訊息，警告AEM使用者刪除片段對活動可能造成的後果。

   AEM中的錯誤訊息並未禁止使用者（強制）刪除「體驗片段」。 如果刪除體驗片段：

   * 含AEM體驗片段的Target選件可能會顯示不想要的行為

      * 當「體驗片段HTML」推送至Target時，選件仍可能會呈現
      * 如果在AEM中也刪除了參照的資產，「體驗片段」中的任何參照可能無法正常運作。
   * 當然，由於AEM中已不存在體驗片段，因此無法進一步修改體驗片段。



---
title: Target與體驗片段整合
seo-title: Target Integration with Experience Fragments
description: Target與體驗片段整合
seo-description: Target Integration with Experience Fragments
uuid: 621f57d4-3b8d-49ea-b193-8530c8fbd74e
contentOwner: carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6911c8e3-b12c-466e-8255-5dcd09557d35
exl-id: dbde3cb6-4132-4462-bd4c-0e4439110e2e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 1%

---

# Target與體驗片段整合{#target-integration-with-experience-fragments}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>此功能需要應用 [AEM 6.4 Service Pack 2(6.4.2.0)](/help/release-notes/sp-release-notes.md) 或更新版本。

您可以匯出 [體驗片段](/help/sites-authoring/experience-fragments.md)，在Adobe Experience Manager(AEM)中建立，並傳送至Adobe Target。 然後可在Target活動中作為選件，以大規模測試並個人化體驗。 這可讓您結合AEM的易用性和強大功能，以及Target中強大的自動化智慧(AI)和機器學習(ML)功能。

## 必備條件 {#prerequisites}

需要執行各種動作：

1. 您必須整合AEM與Target。 請參閱 [與Adobe Target整合](/help/sites-administering/target.md) 以取得更多資訊。
1. 體驗片段會從製作例項匯出，因此您需要 [配置Link Externalizer](/help/sites-developing/externalizer.md) 例項上，以確保任何連結已外部化以用於發佈例項。

## 新增雲端設定 {#add-the-cloud-configuration}

匯出片段之前，您需要新增 **雲端設定** for **Adobe Target** 至片段或資料夾：

1. 導覽至 **體驗片段** 控制台。
1. 開啟 **頁面屬性** ，以取得適當的資料夾或片段。

   >[!NOTE]
   >
   >如果您將雲端設定新增至體驗片段上層資料夾，設定會由所有子項繼承。
   >
   >如果您將雲端設定新增至體驗片段本身，則設定會由所有變數繼承。

1. 選取 **Cloud Services** 標籤。

1. 在 **Cloud Service配置**，選取 **Adobe Target** 從下拉式清單中。
1. 在 **Adobe Target**，請選取適當的設定。

1. **儲存並關閉**.

## 將體驗片段匯出至Target {#exporting-an-experience-fragment-to-target}

>[!NOTE]
>
>若為媒體資產（例如影像），則只會將參考匯出至Target。 資產本身會保存在AEM Assets中，並從AEM發佈例項傳送。
>
>因此，匯出至Target之前，必須先發佈體驗片段及所有相關資產。

若要將體驗片段從AEM匯出至Target（指定雲端設定後）:

1. 導覽至體驗片段主控台。
1. 選取您要匯出至目標的體驗片段。

   >[!NOTE]
   >
   >必須是體驗片段Web變數。

1. 點選/按一下 **匯出至Adobe Target**.

   >[!NOTE]
   >
   >如果體驗片段已匯出，請選取 **Adobe Target中的更新**.

1. 點選/按一下 **不發佈即可匯出** 或 **發佈** 視需要。

   >[!NOTE]
   >
   >選取** Publish**會立即發佈體驗片段並將其傳送至Target。

1. 點選/按一下 **確定** 在確認對話方塊中。

   您的體驗片段現在應位於Target中。

>[!NOTE]
>
>或者，您也可以使用 [頁面資訊](/help/sites-authoring/author-environment-tools.md#page-information) 功能表。

## 在Target中使用體驗片段 {#using-your-experience-fragments-in-target}

執行先前的工作後，體驗片段會顯示在Target的「選件」頁面上。 請看 [特定Target檔案](https://experiencecloud.adobe.com/resources/help/en_US/target/target/aem-experience-fragments.html) 了解你能在那裡實現什麼。

## 刪除已匯出至Target的體驗片段 {#deleting-an-experience-fragment-already-exported-to-target}

刪除已匯出至Target的體驗片段，如果該片段已用於Target中的選件，則可能會造成問題。 刪除片段會導致選件無法使用，因為AEM正在傳送片段內容。

要避免這種情況：

* 如果活動中目前未使用體驗片段，AEM可讓使用者刪除片段，而不含警告訊息。
* 如果Target中的活動目前正在使用體驗片段，則會出現錯誤訊息，警告AEM使用者刪除片段對活動可能造成的後果。

   AEM中的錯誤訊息並未禁止使用者（強制）刪除體驗片段。 如果刪除體驗片段：

   * 具有AEM體驗片段的Target選件可能會顯示不適當的行為

      * 由於體驗片段HTML推送至Target，選件可能仍會呈現
      * 如果參考的資產也在AEM中刪除，體驗片段中的任何參考可能也無法正常運作。
   * 當然，由於體驗片段已不存在，因此無法對體驗片段進行任何進一步修改。

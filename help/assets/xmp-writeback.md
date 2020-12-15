---
title: XMP回寫至轉譯
description: 瞭解XMP回寫功能如何將資產的中繼資料變更傳播至資產的所有或特定轉譯。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 31d652ee04fe75e96f96c9ddc5a6f2c3c64bd630
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 3%

---


# XMP回寫到轉譯{#xmp-writeback-to-renditions}

Adobe Experience Manager(AEM)Assets中的此XMP回寫功能會將資產中繼資料變更複製至資產的轉譯。

當您從AEM Assets中變更資產的中繼資料，或在上傳資產時，變更最初會儲存在Crx-De的資產節點中。

XMP回寫功能會將中繼資料變更傳播至資產的所有或特定轉譯。

考慮將`Classic Leather`資產[!UICONTROL Title]屬性修改為`Nylon`的藍本。

![中繼資料](assets/metadata.png)

在此情況下，AEM Assets會針對儲存在資產階層中的資產中繼資料，在`dc:title`參數中儲存對&#x200B;**[!UICONTROL Title]**&#x200B;屬性的變更。

![metadata_stored](assets/metadata_stored.png)

不過，AEM Assets不會自動將任何中繼資料變更傳播至資產的轉譯。

XMP回寫功能可讓您將中繼資料變更傳播至資產的所有或特定轉譯。 不過，這些變更不會儲存在資產階層的中繼資料節點下。 此功能會在二進位檔案中內嵌轉譯的變更。

## 啟用XMP回寫{#enabling-xmp-writeback}

若要啟用上傳資產時中繼資料變更，將其傳播至資產的轉譯，請在Configuration Manager中修改&#x200B;**Adobe CQ DAM Rendition Maker**&#x200B;組態。

1. 從`https://[aem_server]:[port]/system/console/configMgr`開啟Configuration Manager。
1. 開啟&#x200B;**[!UICONTROL Adobe CQ DAM Rendition Maker]**&#x200B;組態。
1. 選擇&#x200B;**[!UICONTROL 傳播XMP]**&#x200B;選項，然後保存更改。

   ![chlimage_1-346](assets/chlimage_1-346.png)

## 為特定轉譯啟用XMP回寫{#enabling-xmp-writeback-for-specific-renditions}

若要讓「XMP回寫」功能將中繼資料變更傳播至選取的轉譯，請將這些轉譯指定至「DAM中繼資料回寫」工作流程的「XMP回寫程式」工作流程步驟。 依預設，此步驟會以原始轉譯設定。

對於「XMP回寫」功能，將中繼資料傳播至轉譯縮圖140.100.png和319.319.png，請執行這些步驟。

1. 在Experience Manager中，導覽至「**[!UICONTROL 工具>工作流程>模型]**」。
1. 從[!UICONTROL Models]頁面，開啟&#x200B;**[!UICONTROL DAM元資料回寫]**&#x200B;工作流模型。
1. 在「 **[!UICONTROL DAM中繼資料回寫]** 」屬性頁面中，開啟 **[!UICONTROL 「XMP回寫程式」步驟]** 。
1. 在「步 **[!UICONTROL 驟屬性]** 」對話方塊中，點選/按一下「 **[!UICONTROL 處理]** 」標籤。
1. 在&#x200B;**[!UICONTROL 參數]**&#x200B;框中，添加`rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`。 點選／按一下&#x200B;**[!UICONTROL 確定]**。

   ![step_properties](assets/step_properties.png)

1. 若要使用新屬性重新產生動態媒體影像的金字塔TIFF轉譯，請將&#x200B;**[!UICONTROL 動態媒體處理影像資產]**步驟新增至DAM中繼資料回寫工作流程。
PTIFF轉譯只會在「動態媒體混合」模式中建立並儲存在本機。 儲存工作流程。

中繼資料變更會傳播至資產的轉譯`thumbnail.140.100.png`和`thumbnail.319.319.png`，而非其他轉譯。

>[!NOTE]
>
>有關64位元Linux中的XMP回寫問題，請參閱[如何在64位元RedHat Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html)上啟用XMP回寫。
>
>如需支援平台的詳細資訊，請參閱[XMP中繼資料回寫必要條件](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back)。

## 篩選XMP中繼資料{#filtering-xmp-metadata}

[!DNL Experience Manager Assets] 支援從資產二進位檔案讀取並在收錄資產時儲存在JCR中的XMP中繼資料的封鎖清單和允許的屬性／節點清單篩選。

使用封鎖清單進行篩選可讓您匯入所有XMP中繼資料屬性，但為排除指定的屬性除外。 不過，對於資產類型（例如具有大量XMP中繼資料的INDD檔案）（例如1000個節點，具有10,000個屬性），篩選的節點名稱不一定都會事先知道。 如果使用封鎖清單進行篩選可讓大量包含大量XMP中繼資料的資產匯入，AEM例項或叢集可能會遇到穩定性問題，例如阻塞的觀察佇列。

透過允許的清單篩選XMP中繼資料可讓您定義要匯入的XMP屬性，以解決此問題。 如此，就會忽略任何其他或未知的XMP屬性。 為了向後相容性，您可以將其中某些屬性新增至使用封鎖清單的篩選器。

>[!NOTE]
>
>篩選只適用於資產二進位檔中衍生自XMP來源的屬性。 對於從非XMP來源衍生的屬性（例如EXIF和IPTC格式），篩選無法運作。 例如，資產建立日期儲存在EXIF TIFF中名為`CreateDate`的屬性中。 AEM會將此值儲存在名為`exif:DateTimeOriginal`的中繼資料欄位中。 由於來源是非XMP來源，因此篩選不適用於此屬性。

1. 從`https://[aem_server]:[port]/system/console/configMgr`開啟Configuration Manager。
1. 開啟&#x200B;**[!UICONTROL Adobe CQ DAM XmpFilter]**&#x200B;組態。
1. 要通過允許的清單應用過濾，請選擇&#x200B;**[!UICONTROL 將允許清單應用到XMP屬性]**，並在&#x200B;**[!UICONTROL 允許的XML名稱用於XMP過濾]**&#x200B;框中指定要導入的屬性。

   ![chlimage_1-347](assets/chlimage_1-347.png)

1. 若要在透過允許的清單套用篩選後篩選已封鎖的XMP屬性，請在&#x200B;**[!UICONTROL 「XMP篩選的封鎖XML名稱」方塊中指定這些屬性。]**&#x200B;儲存變更。

   >[!NOTE]
   >
   >預設情況下，**[!UICONTROL 將塊清單應用於XMP屬性]**&#x200B;選項處於選中狀態。 換言之，預設會啟用使用封鎖清單進行篩選。 要禁用此類過濾，請取消選擇&#x200B;**[!UICONTROL 將塊清單應用於XMP屬性]**&#x200B;選項。

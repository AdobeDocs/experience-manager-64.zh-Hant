---
title: XMP回寫至轉譯
description: 了解XMP回寫功能如何將資產的中繼資料變更傳播至資產的所有或特定轉譯。
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 456f8c91-aacf-4db5-a329-2d1650ff0f2f
source-git-commit: 1e3cd6ce3138113721183439f7cfb9daed6e0e58
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 3%

---

# XMP回寫至轉譯 {#xmp-writeback-to-renditions}

[!DNL Adobe Experience Manager Assets]中的此XMP回寫功能會將中繼資料變更複製到原始資產的轉譯。 當您從資產內變更資產的中繼資料，或在上傳資產時，變更最初儲存在資產階層的中繼資料節點中。

XMP回寫功能可讓您將中繼資料變更傳播至資產的所有或特定轉譯。 該功能僅寫回那些使用`jcr`命名空間的元資料屬性，即，名為`dc:title`的屬性被寫回，但名為`mytitle`的屬性沒有。

假設您將`Classic Leather`資產[!UICONTROL 標題]屬性修改為`Nylon`的案例。

![中繼資料](assets/metadata.png)

在此情況下， [!DNL Experience Manager]資產會針對儲存於資產階層的資產中繼資料，在`dc:title`參數中儲存對&#x200B;**[!UICONTROL Title]**&#x200B;屬性的變更。

![metadata_stored](assets/metadata_stored.png)

不過，[!DNL Experience Manager Assets]不會自動將任何中繼資料變更傳播至資產的轉譯。 請參閱[如何啟用XMP回寫](#enabling-xmp-writeback)。

## 啟用XMP回寫 {#enabling-xmp-writeback}

若要在上傳資產時啟用中繼資料變更以傳播至資產的轉譯，請在Configuration Manager中修改&#x200B;**Adobe CQ DAM Rendition Maker**&#x200B;設定。

1. 從`https://[aem_server]:[port]/system/console/configMgr`開啟Configuration Manager。
1. 開啟&#x200B;**[!UICONTROL Adobe CQ DAM Rendition Maker]**&#x200B;設定。
1. 選擇&#x200B;**[!UICONTROL 傳播XMP]**&#x200B;選項，然後保存更改。

   ![chlimage_1-346](assets/chlimage_1-346.png)

## 為特定轉譯啟用XMP回寫 {#enabling-xmp-writeback-for-specific-renditions}

若要讓XMP回寫功能傳播中繼資料變更以選取轉譯，請指定這些轉譯至DAM中繼資料回寫工作流程的XMP回寫程式工作流程步驟。 依預設，此步驟會以原始轉譯設定。

對於XMP回寫功能，將中繼資料傳播至轉譯縮圖140.100.png和319.319.png，請執行這些步驟。

1. 在Experience Manager中，導覽至&#x200B;**[!UICONTROL 工具>工作流程>模型]**。
1. 從[!UICONTROL Models]頁面，開啟&#x200B;**[!UICONTROL DAM中繼資料回寫]**&#x200B;工作流程模型。
1. 在「 **[!UICONTROL DAM中繼資料回寫]** 」屬性頁面中，開啟 **[!UICONTROL 「XMP回寫程式」步驟]** 。
1. 在「步 **[!UICONTROL 驟屬性]** 」對話方塊中，點選/按一下「 **[!UICONTROL 處理]** 」標籤。
1. 在&#x200B;**[!UICONTROL 引數]**&#x200B;框中，添加`rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`。 點選/按一下&#x200B;**[!UICONTROL 確定]**。

   ![step_properties](assets/step_properties.png)

1. 若要使用新屬性重新產生Dynamic Media影像的金字塔TIFF轉譯，請將&#x200B;**[!UICONTROL Dynamic Media處理影像資產]**步驟新增至「DAM中繼資料回寫」工作流程。
PTIFF轉譯只會以Dynamic Media混合模式建立並儲存在本機。 儲存工作流程。

中繼資料變更會傳播至資產的轉譯`thumbnail.140.100.png`和`thumbnail.319.319.png`，而非其他轉譯。

>[!NOTE]
>
>有關64位Linux中的XMP回寫問題，請參閱[如何在64位RedHat Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html)上啟用XMP回寫。
>
>如需支援平台的詳細資訊，請參閱[XMP中繼資料回寫必要條件](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back)。

## 篩選XMP中繼資料 {#filtering-xmp-metadata}

[!DNL Experience Manager Assets] 支援封鎖清單和允許的清單篩選XMP中繼資料的屬性/節點，這些中繼資料會從資產二進位檔讀取，並在內嵌資產時儲存在JCR中。

使用封鎖清單進行篩選可讓您匯入除了為排除指定的屬性以外的所有XMP中繼資料屬性。 但是，對於具有大量XMP中繼資料的資產類型（例如1000個節點，具有10,000個屬性），要篩選的節點名稱並不總是事先知道。 如果使用封鎖清單進行篩選可匯入大量具有大量XMP中繼資料的資產，[!DNL Experience Manager]例項或叢集可能會遇到穩定性問題，例如觀察佇列阻塞。

透過允許的清單篩選XMP中繼資料可讓您定義要匯入的XMP屬性，借此解決此問題。 如此一來，會忽略任何其他或未知的XMP屬性。 為了向後相容性，您可以將其中一些屬性新增到使用已封鎖清單的篩選器中。

>[!NOTE]
>
>篩選只適用於資產二進位檔中從XMP來源衍生的屬性。 對於從非XMP來源衍生的屬性（例如EXIF和IPTC格式），篩選無法運作。 例如，資產建立日期儲存在EXIF TIFF中名為`CreateDate`的屬性中。 [!DNL Experience Manager] 將此值儲存在名為的中繼資料欄位 `exif:DateTimeOriginal`中。由於來源為非XMP來源，因此篩選對此屬性無效。

1. 從`https://[aem_server]:[port]/system/console/configMgr`開啟Configuration Manager。
1. 開啟&#x200B;**[!UICONTROL Adobe CQ DAM XmpFilter]**&#x200B;設定。
1. 要通過允許的清單應用篩選，請選擇&#x200B;**[!UICONTROL 將允許清單應用到XMP屬性]**，並指定要在&#x200B;**[!UICONTROL 允許的XML名稱中導入的屬性，以用於XMP過濾]**&#x200B;框。

   ![chlimage_1-347](assets/chlimage_1-347.png)

1. 若要在透過允許的清單套用篩選後篩除已封鎖的XMP屬性，請在「XMP篩選的已封鎖XML名稱」方塊中指定這些屬性。**** 儲存變更。

   >[!NOTE]
   >
   >預設會選取「**[!UICONTROL 將封鎖清單套用至XMP屬性]**」選項。 換言之，預設會啟用使用封鎖清單進行篩選。 要禁用此類篩選，請取消選擇&#x200B;**[!UICONTROL Apply Blocklist to XMP Properties]**&#x200B;選項。

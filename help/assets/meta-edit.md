---
title: 如何編輯或新增中繼資料
description: 了解中的資產中繼資料 [!DNL Experience Manager] 資產是您編輯資產中繼資料的各種方式。
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: f0522343-f8a9-4d89-8ce8-b3357ae3fe70
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 8%

---

# 如何編輯或新增中繼資料 {#how-to-edit-or-add-metadata}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

中繼資料是可搜尋資產的其他相關資訊。 上傳影像時，會自動擷取它。 您可以編輯現有中繼資料，或將新中繼資料屬性新增至現有欄位（例如，中繼資料欄位空白時）。

因為公司需要受控和可靠的元資料辭匯， [!DNL Experience Manager] 資產不允許臨機新增新中繼資料屬性。 雖然作者無法為資產新增中繼資料欄位，但開發人員可以。 請參閱 [為資產建立新的中繼資料屬性](meta-edit.md#editing-metadata-schema).

## 編輯資產的中繼資料 {#editing-metadata-for-an-asset}

若要編輯中繼資料：

1. 執行下列任一項作業：

   * 從「資產」UI中，選取資產，然後按一下/點選 **[!UICONTROL 檢視屬性]** 圖示。
   * 從資產縮圖中選取 **[!UICONTROL 檢視屬性]** 快速動作。
   * 從資產頁面，按一下/點選 **[!UICONTROL 檢視屬性]** 圖示 ![資訊圖示](assets/do-not-localize/info_icon.png) 的上界。

   資產頁面會顯示資產的所有中繼資料。 此中繼資料上傳（擷取）至 [!DNL Experience Manager] 資產。

   ![chlimage_1-169](assets/chlimage_1-169.png)

1. 視需要對各種標籤下的中繼資料進行編輯，在完成時，按一下工具列中的「儲存 **** 」以儲存您所做的變更。按一下/點 **[!UICONTROL 選「關閉]** 」，返回「資產」網頁介面。

   >[!NOTE]
   >
   >如果文字欄位空白，則沒有現有的中繼資料集。 您可以在欄位中輸入值，並儲存它以新增該中繼資料屬性。

對資產中繼資料所做的任何變更，都會回寫至原始二進位檔，作為其XMP資料的一部分。 這是透過AEM中繼資料回寫工作流程完成。 對現有屬性所做的變更(例如 `dc:title`)覆寫和新建立的屬性(包括自訂屬性，如 `cq:tags`)會與結構一起新增。

支援並啟用XMP回寫，適用於 [技術要求。](/help/sites-deploying/technical-requirements.md)

## 編輯中繼資料結構 {#editing-metadata-schema}

如需如何編輯中繼資料結構的詳細資訊，請參閱 [編輯中繼資料結構表單](metadata-schemas.md#editing-metadata-schema-forms).

## 在中註冊自訂命名空間 [!DNL Experience Manager] {#registering-a-custom-namespace-within-aem}

您可以在AEM中新增您自己的命名空間。 就像有預先定義的命名空間，例如cq、jcr和sling，您也可以擁有儲存庫中繼資料和xml處理的命名空間。

1. 轉至節點類型管理頁 `https://[AEM_server]:[port]/crx/explorer/nodetypes/index.jsp`.
1. 按一下或點選 **[!UICONTROL 命名空間]** 頁面頂端。 命名空間管理頁面會顯示在視窗中。

1. 若要新增命名空間，請按一下或點選 **[!UICONTROL 新增]** 在底部。
1. 在XML命名空間約定中指定自定義命名空間（以URI的形式指定ID以及ID的關聯前置詞），然後按一下或點選 **[!UICONTROL 儲存]**.

## 提示和限制 {#best-practices-limitations}

* 透過觸控式UI更新中繼資料會變更 `dc` 命名空間。 透過HTTP API進行的任何更新都會變更 `jcr` 命名空間。 請參閱 [如何使用HTTP API更新中繼資料](/help/assets/mac-api-assets.md#update-asset-metadata).

>[!MORELIKETHIS]
>
>* [關於Assets中的中繼資料及其需求](metadata.md)


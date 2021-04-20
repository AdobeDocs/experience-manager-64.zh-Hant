---
title: 大量編輯多個資產和系列的中繼資料
description: 瞭解如何同時編輯許多資產和系列的中繼資料，以快速傳播常見的中繼資料變更。
contentOwner: AG
feature: Asset Management,Metadata,Collections
role: Business Practitioner
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 14%

---


# 管理多個資產和系列{#managing-multiple-assets-and-collections}

瞭解如何同時編輯多個資產和系列的中繼資料，以快速傳播常見的中繼資料變更。

AdobeEnterprise Manager(AEM)資產可讓您同時編輯多個資產的中繼資料，以便快速將一般中繼資料變更大量傳播至資產。 您也可以大量編輯多個系列的中繼資料。

使用「屬性」頁面，對多個資產或系列執行中繼資料變更：

* 將中繼資料屬性變更為公用值
* 新增或修改標籤

要自定義元資料屬性頁，包括添加、修改、刪除元資料屬性，請使用方案編輯器。

>[!NOTE]
>
>大量編輯方法適用於資料夾或系列中的可用資產。 對於跨資料夾可用或符合一般准則的資產，可從資產搜尋結果大量更新中繼資料。

## 編輯多個資產的中繼資料屬性{#editing-metadata-properties-of-multiple-assets}

1. 在「資產」使用者介面中，導覽至您要編輯的資產所在的位置。
1. 選取您要編輯其常用屬性的資產。
1. 在工具列中，按一下「屬性&#x200B;****」以開啟所選資產的屬性頁面。
1. 修改各種標籤下所選資產的中繼資料屬性。
1. 若要檢視特定資產的中繼資料，請取消在清單中選取剩餘資產。 如果您取消在[!UICONTROL 屬性]頁面上選取一些資產，則不會更新這些資產的中繼資料。
1. 要為資產選擇不同的元資料模式，請按一下工具欄中的&#x200B;**[!UICONTROL Settings]** ，然後選擇模式。 按一下&#x200B;**[!UICONTROL 「儲存並關閉」]**。
1. 若要在包含多個值的欄位中，將新中繼資料與現有中繼資料一起附加，請選取「附 **[!UICONTROL 加模式」]**。如果您未選取此選項，新的中繼資料會取代欄位中現有的中繼資料。按一下&#x200B;**[!UICONTROL 提交]**。

![中繼資料結構大量套用至多個資產](assets/metadata-schema-bulk-edit.gif)

>[!CAUTION]
>
>對於單值欄位，即使您選擇「附加模式」，新元資料也不會附加到欄位中的現 **[!UICONTROL 有值]**。

## 設定大量中繼資料更新的限制{#configure-limit-for-bulk-metadata-update}

若要防止DOS類似情況，請AEM限制Sling請求中支援的參數數。 一次更新許多資產的中繼資料時，您可能會達到限制，而且無法針對更多資產更新中繼資料。 AEM在日誌中生成以下警告：

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

若要變更限制，請存取&#x200B;**[!UICONTROL 工具>作業> Web Console]**，並變更[!UICONTROL Apache Sling請求參數處理] OSGi組態中的[!UICONTROL 最大POST參數]值。

>[!MORELIKETHIS]
>
>* [大量編輯多個系列的中繼資料](managing-collections-touch-ui.md#editing-collection-metadata-in-bulk)
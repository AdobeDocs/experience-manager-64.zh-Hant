---
title: 製作表格欄位的內容相關說明
seo-title: 製作表格欄位的內容相關說明
description: 'AEM Forms可讓您將內容相關說明新增至最適化表單欄位和面板，例如文字或多媒體，包括影片。 '
seo-description: 'AEM Forms可讓您將內容相關說明新增至最適化表單欄位和面板，例如文字或多媒體，包括影片。 '
uuid: 07427ddd-9d35-41f6-a807-0e418aade199
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 893a72c7-d68f-464f-9765-ec2272189e58
translation-type: tm+mt
source-git-commit: 49b7cff2c1583ee1eb929434f27c1989558e197f
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---


# 製作{#authoring-in-context-help-for-form-fields}表單欄位的內容相關說明

## 簡介 {#introduction}

有些情況下，一般使用者在填寫表格時無法確定如何在特定表格欄位中填寫詳細資料。 為瞭解決這些問題，最適化表單支援在表單欄位中新增文字或豐富式內容說明。 它有助於改善表單填寫體驗，並避免使用者的歧義。

本文討論表單作者在製作最適化表單時如何新增內容相關說明。

## 新增內容相關說明{#add-in-context-help}

您可以使用側邊欄屬性標籤的「說明內容」區段中的下列選項，來指定內容相關說明。

* [簡短說明](/help/forms/using/authoring-in-field-help.md#p-short-description-p)
* [詳細說明](/help/forms/using/authoring-in-field-help.md#p-long-description-p)

![表格欄位的內容相關說明](assets/descriptions.png)

>[!NOTE]
>
>詳細說明會覆寫「簡短說明」。 如果您同時指定了兩者，則只會顯示「詳細說明」。

### 簡短說明{#short-description}

「簡短說明」欄位是提供填入表單欄位的快速和簡短提示。 將滑鼠暫留在欄位上時，「簡短說明」欄位中指定的文字會顯示為工具提示。

![新增表格欄位內文說明的簡短說明](assets/tooltip.png)

>[!NOTE]
>
>選擇&#x200B;**一律顯示簡短說明**&#x200B;以永久顯示欄位下方的說明文字。

![欄位下方的永久簡短內容相關說明](assets/short1.png)

### 詳細說明{#long-description}

您可以使用「詳細說明」欄位來指定長篇文字或內嵌多媒體內容，包括視訊，做為內容相關說明。 例如，下圖顯示如何將視訊內嵌為內容相關說明。

![新增豐富式媒體作為表格欄位的內容相關說明](assets/long-descriptions.png)

新增詳細說明會顯示&#x200B;**?** 表徵圖。按一下圖示會顯示在詳細說明區段中新增的內容。

![豐富式媒體內容相關說明範例](assets/photoshop.png)

### 面板級幫助{#panel-level-help}

除了表格欄位的內容相關說明外，您也可以在面板編輯對話方塊的「說明內容」索引標籤中，在面板層級指定說明。

![新增表格面板的內容相關說明](assets/panel-level-help.png)

新增面板說明會顯示&#x200B;**?** 表徵圖。按一下圖示會顯示在面板編輯對話方塊的「說明內容」區段中新增的內容。

![表單面板層級的內容相關說明範例](assets/photoshop-1.png)


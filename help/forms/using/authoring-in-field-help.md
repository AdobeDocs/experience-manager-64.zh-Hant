---
title: 為表單欄位編寫內容說明
seo-title: Authoring in-context help for form fields
description: AEM Forms可讓您將內容內說明新增至最適化表單欄位和面板，如文字或多媒體，包括影片。
seo-description: AEM Forms allows you to add in-context help to adaptive form fields and panels, as text or rich media, including videos.
uuid: 07427ddd-9d35-41f6-a807-0e418aade199
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 893a72c7-d68f-464f-9765-ec2272189e58
feature: Adaptive Forms
exl-id: 0c761c0c-fbe4-4129-8a90-c4ef1127a762
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 1%

---

# 為表單欄位編寫內容說明 {#authoring-in-context-help-for-form-fields}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 簡介 {#introduction}

有時，一般使用者填寫表單時不確定如何填寫特定表單欄位的詳細資料。 為了解決這些問題，適用性表單支援將文字或豐富內容說明新增至表單欄位。 有助於改善表單填寫體驗，並避免使用者產生任何模糊情形。

本文探討表單作者在編寫適用性Forms時如何新增內容說明。

## 添加上下文內幫助 {#add-in-context-help}

您可以使用側邊欄中屬性標籤的「說明內容」區段中的下列選項來指定內容內說明。

* [簡短說明](/help/forms/using/authoring-in-field-help.md#p-short-description-p)
* [詳細說明](/help/forms/using/authoring-in-field-help.md#p-long-description-p)

![表單欄位的內容內容說明](assets/descriptions.png)

>[!NOTE]
>
>長說明會覆寫短說明。 如果您已同時指定兩者，則只會顯示「長說明」。

### 簡短說明 {#short-description}

「簡短說明」欄位是提供有關填寫表單欄位的快速簡短提示。 在「簡短說明」欄位中指定的文字，在將滑鼠游標暫留在欄位上時會顯示為工具提示。

![為表單欄位新增內容內說明的簡短說明](assets/tooltip.png)

>[!NOTE]
>
>選擇 **一律顯示簡短說明** ，在欄位下永久顯示幫助文本。

![欄位下的永久短內容幫助](assets/short1.png)

### 詳細說明 {#long-description}

您可以使用「長說明」欄位，將長文字或內嵌多媒體內容（包括視訊）指定為內容內容說明。 例如，下圖顯示如何以內容內說明的形式內嵌視訊。

![將多媒體新增為表單欄位的內容內容說明](assets/long-descriptions.png)

新增長說明會顯示 **?** 圖示。 按一下圖示即可顯示詳細說明區段中新增的內容。

![多媒體內容內容說明範例](assets/photoshop.png)

### 面板層級說明 {#panel-level-help}

除了表單欄位的上下文幫助外，您還可以在面板編輯對話框的「幫助內容」頁簽中的面板級別指定幫助。

![為表單面板新增內容內容說明](assets/panel-level-help.png)

新增面板的說明會顯示 **?** 圖示。 按一下圖示即可顯示面板編輯對話方塊的「說明內容」區段中新增的內容。

![表單面板層級的內容內文說明範例](assets/photoshop-1.png)

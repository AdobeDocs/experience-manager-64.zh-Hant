---
title: 使用表單資料模型
seo-title: 使用表單資料模型
description: 了解如何使用表單資料模型來建立及使用最適化表單和互動式通訊。
seo-description: 了解如何使用表單資料模型來建立及使用最適化表單和互動式通訊。
uuid: 9a8bd44a-34a1-41ef-a57b-d5e3dd0a77ee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: 7a1bfd43-39b1-478b-a294-92c78eaebbf2
feature: 表單資料模型
exl-id: 39408af6-439c-4ade-8062-155be9141dfa
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1276'
ht-degree: 0%

---

# 使用表單資料模型{#use-form-data-model}

![](do-not-localize/data-integeration.png)

AEM Forms資料整合可讓您使用不同的後端資料來源來建立表單資料模型，以便在各種最適化表單和互動式通訊工作流程中當作結構描述。 它需要配置資料源，並根據資料源中可用的資料模型對象和服務建立表單資料模型。 如需詳細資訊，請參閱下列內容：

* [AEM Forms資料整合](/help/forms/using/data-integration.md)
* [設定資料來源](/help/forms/using/configure-data-sources.md)
* [建立表單資料模型](/help/forms/using/create-form-data-models.md)
* [使用表單資料模型](/help/forms/using/work-with-form-data-model.md)

表單資料模型是JSON結構描述的擴充功能，可用於：

* [建立最適化表單和片段](#create-af)
* [建立互動式通訊和建置區塊，例如文字、清單和條件片段](#create-ic)
* [使用範例資料預覽互動式通訊](#preview-ic)
* [預填最適化表單和互動式通訊](#prefill)
* [將提交的最適化表單資料寫入資料來源](#write-af)
* [使用最適化表單規則叫用服務](#invoke-services)

## 建立最適化表單和片段{#create-af}

您可以根據表單資料模型建立[適用性表單](/help/forms/using/creating-adaptive-form.md)和[適用性表單片段](/help/forms/using/adaptive-form-fragments.md)。 建立最適化表單或最適化表單片段時，請執行下列動作以使用表單資料模型：

1. 在「添加屬性」螢幕的「表單模型」頁簽中，從&#x200B;**[!UICONTROL 「從]**&#x200B;中選擇」下拉清單中選擇&#x200B;**[!UICONTROL 「表單資料模型」]**。

   ![create-af-1](assets/create-af-1.png)

1. 點選以展開&#x200B;**[!UICONTROL 選取表單資料模型]**。 會列出所有可用的表單資料模型。

   從資料模型中選取。

   ![create-af-2](assets/create-af-2.png)

1. （**僅適用性表單片段**）您可以根據表單資料模型中的一個資料模型物件，建立最適化表單片段。 展開&#x200B;**[!UICONTROL 表單資料模型定義]**&#x200B;下拉式清單。 它列出指定表單資料模型中的所有資料模型對象。 從清單中選取資料模型物件。

   ![create-af-3](assets/create-af-3.png)

建立以表單資料模型為基礎的最適化表單或最適化表單片段後，表單資料模型物件會以最適化表單編輯器顯示在內容瀏覽器的&#x200B;**[!UICONTROL 資料模型物件]**&#x200B;標籤中。

>[!NOTE]
>
>對於最適化表單片段，只有在創作時選取的資料模型物件及其相關的資料模型物件會顯示在「資料模型物件」索引標籤中。

![data-model-objects-tab](assets/data-model-objects-tab.png)

您可以將資料模型物件拖放至最適化表單或片段，以新增表單欄位。 新增的表單欄位會保留中繼資料屬性，並與資料模型物件屬性系結。 系結可確保表單提交時欄位值會在對應的資料來源中更新，並在表單轉譯時預填。

## 建立互動式通信{#create-ic}

您可以根據表單資料模型建立互動式通訊，以便使用來自已設定資料來源的資料預先填入互動式通訊。 此外，互動式通信的構建模組（如文本、清單和條件文檔片段）可以基於表單資料模型。

建立互動式通訊或檔案片段時，您可以選擇表單資料模型。 下圖顯示了「建立交互通信」對話框的「常規」頁簽。

![create-ic](assets/create-ic.png)

「建立互動式通信」對話框的「常規」頁簽

如需詳細資訊，請參閱：

[建立互動式通訊](/help/forms/using/create-interactive-communication.md)

[互動式通訊中的文字](/help/forms/using/texts-interactive-communications.md)

[互動式通訊中的條件](/help/forms/using/conditions-interactive-communications.md)

[清單片段](/help/forms/using/lists.md)

## 預覽範例資料{#preview-ic}

表單資料模型編輯器可讓您為表單資料模型中的資料模型物件產生和編輯範例資料。 您可以使用此資料來預覽和測試互動式通訊和最適化表單。 您必須先產生範例資料，然後才能依照[使用表單資料模型](/help/forms/using/work-with-form-data-model.md#sample)中所述進行預覽。

若要預覽與範例表單資料模型資料的互動式通訊：

1. 在AEM製作例項上，導覽至&#x200B;**[!UICONTROL Forms > Forms與檔案]**。
1. 選擇互動式通信，然後點選工具欄中的&#x200B;**[!UICONTROL 預覽]**&#x200B;以選擇&#x200B;**[!UICONTROL Web通道]**、**[!UICONTROL 打印通道]**&#x200B;或&#x200B;**[!UICONTROL 兩個通道]**&#x200B;以預覽互動式通信。
1. 在「預覽&#x200B;[*頻道*]」對話方塊中，確定已選取「表單資料模型的測試資料&#x200B;]**」，然後點選「**[!UICONTROL &#x200B;預覽&#x200B;]**」。**[!UICONTROL 

互動式通訊隨即開啟，其中包含預填的範例資料。

![網頁預覽](assets/web-preview.png)

同樣地，若要預覽含有範例資料的最適化表單，請在製作模式中開啟最適化表單，然後點選&#x200B;**[!UICONTROL 預覽]**。

## 使用表單資料模型服務預填 {#prefill}

AEM Forms提供現成可用的表單資料模型預填服務，讓您能夠根據表單資料模型啟用最適化表單和互動式通訊。 預填充服務以自適應形式和交互通信查詢資料模型對象的資料源，並相應地在呈現表單或通信時預填充資料。

若要為最適化表單啟用「表單資料模型預填服務」，請開啟「適用性表單容器」屬性，然後從「基本」設定追蹤器的「預填服務」下拉式清單中選取「**[!UICONTROL 表單資料模型預填服務]**」。 ****&#x200B;然後，儲存屬性。

![預填服務](assets/prefill-service.png)

若要在互動式通訊中設定表單資料模型預填服務，您可以在建立預填服務下拉式清單中選取「表單資料模型預填服務」，或之後透過修改屬性來建立預填服務。

![edit-ic-props](assets/edit-ic-props.png)

編輯互動式通信的屬性對話框

## 將提交的最適化表單資料寫入資料來源{#write-af}

當使用者根據表單資料模型提交表單時，您可以設定表單以將資料模型物件的已提交資料寫入其資料來源。 為了達成此使用案例，AEM Forms提供[表單資料模型提交動作](/help/forms/using/configuring-submit-actions.md)，且僅可立即用於根據表單資料模型的最適化表單。 它會將資料模型物件的已提交資料寫入其資料來源中。

要配置「表單資料模型提交」操作，請開啟「適用性表單容器」屬性，並在「提交」折疊式功能表下的「提交操作」下拉清單中選擇&#x200B;**[!UICONTROL 「使用表單資料模型提交」]**。 然後，瀏覽並從要提交&#x200B;]**的資料模型對象的**[!UICONTROL &#x200B;名稱下拉清單中選擇資料模型對象。 儲存屬性。

在表單提交時，將配置的資料模型對象的資料寫入相應的資料源。

![資料提交](assets/data-submission.png)

您也可以使用二進位資料模型物件屬性，將表單附件提交至資料來源。 執行以下操作將附件提交到JDBC資料源：

1. 將包含二進位屬性的資料模型物件新增至表單資料模型。
1. 在最適化表單中，從「元件」瀏覽器將&#x200B;**[!UICONTROL 檔案附件]**&#x200B;元件拖放至最適化表單。
1. 點選以選取新增的元件，然後點選![settings_icon](assets/settings_icon.png)以開啟元件的「屬性」瀏覽器。
1. 在「系結參考」欄位中，點選![foldersearch_18](assets/foldersearch_18.png)並導覽至選取您在表單資料模型中新增的二進位屬性。 視需要設定其他屬性。

   點選![check-button](assets/check-button.png)以儲存屬性。 附件欄位現在已綁定到表單資料模型的二進位屬性。

1. 在適用性表單容器屬性的「提交」區段中，啟用&#x200B;**[!UICONTROL 提交表單附件]**。 它會在提交表單時將二進位屬性欄位中的附件提交給資料來源。

## 使用規則{#invoke-services}在適用性表單中叫用服務

在以表單資料模型為基礎的最適化表單中，您可以[建立規則](/help/forms/using/rule-editor.md)來叫用表單資料模型中設定的服務。 規則中的&#x200B;**[!UICONTROL 調用服務]**&#x200B;操作列出表單資料模型中的所有可用服務，並允許您為服務選擇輸入和輸出欄位。 您也可以使用&#x200B;**設定值**&#x200B;規則類型來叫用表單資料模型服務，並將欄位值設為服務傳回的輸出。

例如，以下規則調用以員工ID作為輸入的獲取服務，並且返回的值將填充到窗體中相應的「從屬ID」、「姓氏」、「名字」和「性別」欄位中。

![調用服務](assets/invoke-service.png)

此外，您還可以使用`guidelib.dataIntegrationUtils.executeOperation` API在規則編輯器的程式碼編輯器中撰寫JavaScript。 如需API詳細資訊，請參閱[叫用表單資料模型服務的API](/help/forms/using/invoke-form-data-model-services.md)。

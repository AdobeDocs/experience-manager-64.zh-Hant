---
title: 多步驟表單序列簡介
seo-title: 多步驟表單序列簡介
description: 透過AEM Forms，您可以定義表單面板的順序，讓使用者在其中導覽及填入最適化表單。
seo-description: 透過AEM Forms，您可以定義表單面板的順序，讓使用者在其中導覽及填入最適化表單。
uuid: b2b94e4c-0c28-47ba-8e23-fd8742baf71c
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 4a51ebc4-e019-4fc5-93a1-d97f695126f5
feature: 適用性表單
exl-id: eec8bcbe-e2ba-42f1-98ea-08a4ca723e48
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# 多步驟表單序列{#introduction-to-multi-step-form-sequence}簡介

適用性表單可讓表單作者輕鬆建立多步驟資料擷取體驗。 內建支援可建立多個面板，並將每個面板與不同的導覽模式建立關聯。 表單作者可將邏輯區段中的表單欄位分組，並將群組表示為面板。 使用面板佈局控制面板之間的整體導航。 作者可以選擇以不同的版面排列面板，例如使用「精靈」版面依序放置面板，或使用「標籤式版面」以臨機方式放置面板。 如需面板配置的相關資訊，請參閱適用性表單的[配置功能](/help/forms/using/layout-capabilities-adaptive-forms.md)。

在一般的表單填寫體驗中，涉及的步驟不只是擷取資料。 完整的表單提交可包括其他步驟，例如以數位方式簽署表單、驗證表單中填入的資訊、處理付款等。 它不同個案。

如果您的使用案例要求執行資料擷取的一組步驟，或有需要執行特定步驟的法規，AEM Forms會提供跨表單強制執行此通用結構的方法。 表單結構的有預謀實施定義了表單的步驟順序。 ![多步驟表單序列範例](assets/formpipeline.png)

讓我們舉個使用案例，說明您需要建立表單填寫、驗證、簽署和確認步驟的順序。 建立此類序列的步驟如下：

1. 定義表單範本，並新增必要的面板。 請注意，序列中的每個步驟都應有一個面板。 不過，您可以在面板內包含子面板。

   在此範例中，我們可新增下列面板：

   * **填寫**:它包含用於擷取資料的表單欄位。在此，您可以包含巢狀子面板，以針對不同類型的資訊建立區段，例如個人、家庭、財務等。
   * **驗證**:其中包 **** 含可用於XFA型最適化表單的Verifycomponent。它會以唯讀模式顯示在「填充」面板中擷取的資訊，以供驗證。
   * **電子簽名**:其中包 **** 含可用於XFA型最適化表單的Sign元件。它提供下列簽名服務：

      * Adobe Document Cloud eSign Services
      * 手寫簽名
   * **確認**:它包含摘要元 **** 件，在使用者簽署表單並到達序列中的確認（摘要）步驟後，會顯示確認表單提交的訊息。作者可以設定摘要元件的文字、顯示感謝訊息、顯示產生的PDF的連結等。


1. 將根面板的佈局選為&#x200B;**[!UICONTROL Wizard]**。
1. 完成其餘步驟以建立表單範本。 如需詳細資訊，請參閱[建立自訂最適化表單範本](/help/forms/using/custom-adaptive-forms-templates.md)。

在表單模板中定義表單序列後，您可以使用它建立表單，該表單將基本結構定義為已定位的序列，但您始終可以定制表單以滿足您的要求。

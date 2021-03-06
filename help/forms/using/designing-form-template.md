---
title: 為HTML5表單設計表單範本
seo-title: 為HTML5表單設計表單範本
description: 'AEM Forms提供將XFA表單範本轉譯為HTML5格式。 表單設計人員可以使用設計工具設計表單範本，並使用HTML5轉譯功能。 '
seo-description: 'AEM Forms提供將XFA表單範本轉譯為HTML5格式。 表單設計人員可以使用設計工具設計表單範本，並使用HTML5轉譯功能。 '
uuid: 41a00ec5-d7f9-4717-a961-00d20d8e7b2a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: e135fa01-fede-4285-b4dd-2d23acbb4d26
feature: 行動表單
exl-id: 248e56c7-51b7-41d3-8bc9-a5d737bf178b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# 設計HTML5表單的表單模板{#designing-form-templates-for-html-forms}

AEM中的HTML5表單元件提供將XFA表單範本轉譯為HTML5格式。 表單設計人員可以使用[Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63)來設計表單範本，並使用HTML5轉譯功能。 這些表單範本及其資產可位於AEM存放庫、檔案系統，或透過http公開。 不過，如果您打算使用Forms Manager管理表單，範本和資產應位於AEM存放庫。

雖然HTML5表單在很大程度上符合PDF forms的行為，但兩種格式中都有某些功能不適用於其他格式。 例如，在Adobe Reader中，如何套用條碼至PDF表單，會因行動表單而異，或表單的數位簽署方式也會因格式而異。 如需此類變異的詳細資訊，請參閱[HTML5表單與PDF forms之間的功能區分](/help/forms/using/feature-differentiation-html5-forms-pdf-forms.md)。

如需常見XFA功能，請參閱下列最佳實務和准則，以設計可同時以兩種格式運作的表單。

## AEM Forms Designer中用於HTML5 Forms {#capabilities-in-aem-forms-designer-for-html-forms}的功能

### 預覽HTML {#preview-html}

「預覽HTML」頁簽會在「設計」模式中添加，以便「表單設計者」在設計過程中以HTML5格式預覽表單。 如需如何在AEM Forms Designer中啟用和設定此功能的詳細資訊，請參閱[預覽HTML](/help/forms/using/preview-xdp-forms-html.md)。

### 手寫簽名{#scribble-signature}

HTML5表單的主要目標為觸控裝置。 因此，AEM Forms Designer中新增了新的手寫簽名控制項。 您可以按一下或拖放表單範本上的手寫簽名控制項並加以設定。 在HTML5轉譯中會以手寫欄位呈現，且可用於在觸控裝置上手寫簽名。 在桌上型電腦上，它可作為手寫欄位使用滑鼠控制。 有關如何使用此功能的詳細資訊，請參閱[XFA手寫欄位](/help/forms/using/scribble-signature.md)。

![4](assets/4.png)

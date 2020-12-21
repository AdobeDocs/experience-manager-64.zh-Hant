---
title: 設計HTML5表單的表單範本
seo-title: 設計HTML5表單的表單範本
description: 'AEM Forms提供將XFA表單範本轉換為HTML5格式的功能。 表單設計人員可使用設計人員來設計表單範本，並使用HTML5轉譯功能。 '
seo-description: 'AEM Forms提供將XFA表單範本轉換為HTML5格式的功能。 表單設計人員可使用設計人員來設計表單範本，並使用HTML5轉譯功能。 '
uuid: 41a00ec5-d7f9-4717-a961-00d20d8e7b2a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: e135fa01-fede-4285-b4dd-2d23acbb4d26
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---


# 設計HTML5表單的表單範本{#designing-form-templates-for-html-forms}

AEM中的HTML5表單元件提供將XFA表單範本轉換為HTML5格式。 表單設計人員可使用[Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63)來設計表單範本，並使用HTML5轉譯功能。 這些表單範本及其資產可以駐留在AEM儲存庫、檔案系統或透過http公開。 不過，如果您打算使用Forms Manager管理表單，範本和資產應位於AEM儲存庫中。

雖然HTML5表格在很大程度上與PDF表格的行為相符，但這兩種格式中都有某些功能不適用於其他格式。 例如，Adobe Reader中PDF表單上套用條碼的方式會因行動表單而異，或表格的數位簽署方式也會因格式而異。 如需此類變化的詳細資訊，請參閱[HTML5表單與PDF表單的功能區隔](/help/forms/using/feature-differentiation-html5-forms-pdf-forms.md)。

如需常見的XFA功能，請參閱下列最佳實務和准則，以設計兩種格式的表格。

## AEM Forms Designer for HTML5 Forms {#capabilities-in-aem-forms-designer-for-html-forms}的功能

### 預覽HTML {#preview-html}

「預覽HTML」索引標籤會新增至「表單設計人員的設計」模式中，以在設計程式期間預覽HTML5格式的表單。 如需如何在AEM Forms Designer中啟用和設定此功能的詳細資訊，請參閱「預覽HTML[」。](/help/forms/using/preview-xdp-forms-html.md)

### 塗鴉簽名{#scribble-signature}

HTML5表單的主要目標是觸控裝置。 因此，AEM Forms Designer中新增了新的塗鴉簽名控制項。 您可以按一下或拖放表格範本上的塗鴉簽名控制項，並加以設定。 它會在HTML5轉譯中呈現為塗鴉欄位，並可用於在觸控裝置上塗鴉簽名。 在桌上型電腦上，它可使用滑鼠控制項，做為塗鴉欄位。 如需如何使用此功能的詳細資訊，請參閱[XFA塗鴉欄位](/help/forms/using/scribble-signature.md)。

![4](assets/4.png)

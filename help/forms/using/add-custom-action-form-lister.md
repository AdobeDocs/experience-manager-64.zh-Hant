---
title: 在表單清單項目上新增自訂動作
seo-title: 在表單清單項目上新增自訂動作
description: 表單開發人員可在表單入口網站頁面上的表單清單中新增更多動作。 依預設，表單清單可讓您存取表單、填寫表單並提交。
seo-description: 表單開發人員可在表單入口網站頁面上的表單清單中新增更多動作。 依預設，表單清單可讓您存取表單、填寫表單並提交。
uuid: 02c64f7d-f726-4a5b-a303-ec96934e9c01
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: 0e0a9b6b-fd2f-4cec-b233-500c940ee4d5
exl-id: d8f60be3-474a-4dd1-aaa5-7b6a97e1a9bd
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# 在表單清單項{#adding-custom-action-on-form-lister-items}上添加自定義操作

在AEM Forms中，您可以建立列出可用表單的入口網站頁面。 依預設，您可以在入口網頁上搜尋和列出表單。 您可以開啟表單以填寫並提交資訊。 入口網站頁面上所列的表單僅可立即使用呈現動作。 若要深入了解入口網站頁面上的可用動作，請參閱[建立表單入口網頁](/help/forms/using/creating-form-portal-page.md)。

您可以將其他選項新增至入口網頁。 您可以自訂表單入口網站的範本，以自訂這些選項或動作。

本文將示範如何直接從表單入口網站頁面建立按鈕，以傳送表單的連結。 此自訂需要更新Search &amp; Lister元件的範本。

以下提供將動作新增至範本所需的程式碼。 程式碼片段中的`onclick`屬性有透過電子郵件傳送表單連結的指令碼。

```mxml
<div class="__FP_boxes-container __FP_single-color">
    <div class="boxes __FP_boxes __FP_single-color" data-repeatable="true">
  <div class="__FP_boxes-thumbnail">
            <img src ="${contextPath}${path}/jcr:content/renditions/cq5dam.thumbnail.319.319.png">
        </div>
        <h3 class="__FP_single-color" title="${name}" tabindex="0">${name}</h3>
        <p>${description}</p>
        <div class="boxes-icon-cont __FP_boxes-icon-cont">
            <div class="op-dow">
                <a href="${formUrl}" target="_blank" class="__FP_button ${htmlStyle}" title="${config-htmlLinkText}">Apply</a>
                <a class="__FP_button" title="Email a friend" href="#" onclick="javascript:window.location=&apos;mailto:?subject=Interesting information&body=I thought you might find {name} form helpful :  &apos;+window.location.protocol+window.location.host+&apos;${formUrl}&apos; ;">Email</a>
                <a href="${pdfUrl}" class="__FP_button ${pdfStyle}" title="${config-pdfLinkText}">Download</a>
            </div>
        </div>
    </div>
</div>
```

您可以在自訂範本中新增類似動作。 若要定義JavaScript函式，請在頁面層級指令碼上新增函式，並將其與必要的HTML元素連結。 在上述範例中，`onclick`運算式是連結的函式。

對範本進行編輯後，範例入口網頁會包含一個按鈕，可透過電子郵件傳送表單連結，如下所示。

![email](assets/email.png)

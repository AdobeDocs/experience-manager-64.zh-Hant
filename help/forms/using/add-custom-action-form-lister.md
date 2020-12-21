---
title: 在表單清單項上添加自定義操作
seo-title: 在表單清單項上添加自定義操作
description: 表單開發人員可在表單入口網頁的表單清單中新增更多動作。 依預設，表單清單可讓您存取表單、填寫表單並送出。
seo-description: 表單開發人員可在表單入口網頁的表單清單中新增更多動作。 依預設，表單清單可讓您存取表單、填寫表單並送出。
uuid: 02c64f7d-f726-4a5b-a303-ec96934e9c01
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: 0e0a9b6b-fd2f-4cec-b233-500c940ee4d5
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# 在表單清單項{#adding-custom-action-on-form-lister-items}上添加自定義操作

在AEM Forms中，您可以建立列出可用表單的入口網頁。 依預設，您可以搜尋並列出入口網站頁面上的表單。 您可以開啟表單以填寫和提交資訊。 入口網站頁面上列出的表單，現在只提供轉譯動作。 若要進一步瞭解入口網頁上的可用動作，請參閱[建立表單入口網頁](/help/forms/using/creating-form-portal-page.md)。

您可以新增其他選項至入口網站頁面。 您可以自訂表單入口網站的範本，自訂這些選項或動作。

本文將展示如何建立按鈕，以直接從表單入口網頁傳送表單連結。 此自訂作業需要更新Search &amp; Lister元件的範本。

下面提供將動作新增至範本所需的程式碼。 程式碼片段中的`onclick`屬性包含透過電子郵件傳送表單連結的指令碼。

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

您可以在自訂範本中新增類似動作。 若要定義JavaScript函式，請在頁面層級指令碼上新增該函式，並將其連結至必要的HTML元素。 在上述範例中，`onclick`運算式是連結的函式。

對範本進行編輯後，範例入口網頁會包含一個按鈕，可透過電子郵件傳送表單的連結，如下所示。

![email](assets/email.png)


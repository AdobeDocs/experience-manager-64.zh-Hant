---
title: 中XMP繼資料
description: 瞭解AEM AssetsXMP用於中繼資料管理的（可擴充中繼資料平台）中繼資料標準。 為XMP各種應用程式建立、處理和交換中繼資料提供標準格式。
contentOwner: AG
feature: Metadata
role: Business Practitioner,Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 19%

---


# XMP 中繼資料 {#xmp-metadata}

(可XMP擴充中繼資料平台)是AEM Assets用於所有中繼資料管理的中繼資料標準。 為XMP各種應用程式建立、處理和交換中繼資料提供標準格式。

除了提供可嵌入所有檔案格式的通用中繼資料編碼外XMP，還提供多樣化的[內容模型](xmp.md#xmp-core-concepts)，並受Adobe](xmp.md#advantages-of-xmp)等公司支援[，讓與AEM Assets合作的使用者擁有強大的平台來建立。

[規XMP格](https://www.adobe.com/devnet/xmp.html)可從Adobe獲得。

## 什麼XMP?{#what-is-xmp}

AEM Assets本XMP身支援以Adobe為首的可擴展元資料平台。 XMP是處理和儲存數位資產中標準化和專屬中繼資料的標準。 設XMP計為通用標準，可讓多個應用程式有效地處理中繼資料。

例如，生產專業人員可使用Adobe應用程式內建XMP的支援，跨多種檔案格式傳遞資訊。 AEM Assets儲存庫提取元XMP資料並使用它管理內容生命週期，並提供建立自動化工作流的能力。

XMP透過提供資料模型、儲存模型和結構，標準化中繼資料的定義、建立和處理方式。 本節將介紹這些概念。

EXIF、ID3或Microsoft Office的所有舊式中繼資料都會自動轉譯為XMP，可加以擴充以支援客戶特定的中繼資料架構，例如產品型錄。

中的元XMP資料由一組屬性組成。 這些屬性一律與\
特定實體稱為資源；即，屬性是關於資源的。 在這種情況XMP下，資源始終是資產。

### Adobe {#adobe}

Adobe首先引XMP入了Adobe Acrobat軟體產品的標準。 自那以來，該XMP標準得到廣泛採用。

### XMP生態系統{#xmp-ecosystem}

XMP定義了 [中繼資料](https://en.wikipedia.org/wiki/Metadata) 模型，可與任何已定義的中繼資料項目集搭配使用。XMP也定義了基本屬性的特定結構 [](https://en.wikipedia.org/wiki/XML_schema) ，這些基本屬性可用於記錄資源在經過多個處理步驟 (從被拍攝、掃描或創作為文字) 、通過照片編輯步驟(如 [](https://en.wikipedia.org/wiki/Image_scanner)[](https://en.wikipedia.org/wiki/Cropping_%28image%29) or color adjustment)到組合成最終影像時的歷史記錄。XMP可讓每個軟體程式或裝置沿途將其資訊新增至數位資源，然後再保留在最終數位檔案中。

XMP最常是使用 [W3C](https://en.wikipedia.org/wiki/World_Wide_Web_Consortium)[Resource Description Framework](https://en.wikipedia.org/wiki/Resource_Description_Framework) (RDF)的子集進行序列化和儲存，該子集又以 [XML表示](https://en.wikipedia.org/wiki/XML)。

## &lt;a0/XMP>的優點{#advantages-of-xmp}

與其XMP他編碼標準和模式相比，具有以下優勢：

* 基XMP於元資料的功能非常強大，而且細緻。
* 可讓XMP您對一個屬性有多個值。
* XMP有標準化編碼，讓您輕鬆交換中繼資料。
* 可XMP擴充。 您可以新增其他資訊至資產。

### 可擴充 {#extensible}

此標XMP準可擴充，讓您在資料中新增自訂的中繼資料類XMP型。 而EXIF則否——它有固定的屬性清單，無法延伸。

>[!NOTE]
>
>通XMP常不允許嵌入二進位資料類型。 若要將二進位資XMP料（例如縮圖影像）傳入，必須以XML友好格式（例如Base64）加以編碼。

## XMP核心概念{#xmp-core-concepts}

以下各節介紹的核心概念XMP，包括名稱空間和圖式、屬性和值，以及語言替代。

### 名稱空間和圖式集{#namespaces-and-schemata}

架XMP構是一組通用XML命名空間中的屬性名稱，其中包含\
資料類型和描述性資訊。 架構XMP由其XML命名空間URI標識。 使用名稱空間可防止名稱相同但含義不同之不同結構中屬性之間的衝突。

例如，兩個獨立設計結構中的&#x200B;**Creator**&#x200B;屬性可能代表資產的建立者，也可能代表資產建立者的應用程式(例如Adobe Photoshop)。

### 屬性和值{#properties-and-values}

可XMP以包括來自一個或多個方案的屬性。

例如，許多Adobe應用程式使用的典型子集可能包括：

* 都柏林核心架構：dc:title, dc:creator, dc:subject, dc:format, dc:rights
* XMP基本架構：xmp:CreateDate, xmp:CreatorTool, xmp:ModifyDate, xmp:metadataDate
* XMP權限管理架構xmpRights:WebStatement, xmpRights:Marked
* XMP媒體管理架構xmpMM:DocumentID

### 語言替代項目{#language-alternatives}

提XMP供將&#x200B;**xml:lang**&#x200B;屬性新增至文字屬性的功能，以指定文字的語言。

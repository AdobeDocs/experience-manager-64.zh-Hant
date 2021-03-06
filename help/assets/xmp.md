---
title: XMP中繼資料
description: 了解 [!DNL Experience Manager] Assets用於中繼資料管理的XMP（可擴充中繼資料平台）中繼資料標準。 XMP提供標準格式，供多種應用程式建立、處理和交換中繼資料。
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 32c4ca3d-2e9e-46a3-b4c7-70dcc50daaaa
source-git-commit: 1e3cd6ce3138113721183439f7cfb9daed6e0e58
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 19%

---

# XMP 中繼資料 {#xmp-metadata}

XMP（可擴充中繼資料平台）是[!DNL Experience Manager]資產用於所有中繼資料管理的中繼資料標準。 XMP提供標準格式，供多種應用程式建立、處理和交換中繼資料。

除了提供可嵌入到所有檔案格式的通用元資料編碼，XMP還提供豐富的[內容模型](xmp.md#xmp-core-concepts)，並受Adobe](xmp.md#advantages-of-xmp)和其他公司支援[，因此XMP的用戶與[!DNL Experience Manager] Assets結合後，擁有強大的平台可以構建。

[XMP規格](https://www.adobe.com/devnet/xmp.html)可從Adobe取得。

## 什麼是XMP? {#what-is-xmp}

[!DNL Experience Manager] Assets原本支援XMP — 由Adobe牽頭的可擴充中繼資料平台。XMP是處理和儲存數位資產中標準化和專屬中繼資料的標準。 XMP的設計是通用標準，可讓多個應用程式有效處理中繼資料。

例如，生產專業人員可在Adobe的應用程式中使用內建的XMP支援，以傳遞多種檔案格式的資訊。 [!DNL Experience Manager]資產存放庫會擷取XMP中繼資料，並使用中繼資料來管理內容生命週期，並提供建立自動化工作流程的功能。

XMP借由提供資料模型、儲存模型和結構，標準化中繼資料的定義、建立和處理方式。 本節將介紹所有這些概念。

來自EXIF、ID3或Microsoft Office的所有舊式中繼資料都會自動轉譯為XMP，這可以延伸以支援客戶專屬的中繼資料結構，例如產品目錄。

XMP中的中繼資料包含一組屬性。 這些屬性一律與\
稱為資源的特定實體；也就是說，屬性是關於資源。 在XMP的情況下，資源一律為資產。

### Adobe {#adobe}

Adobe先在Adobe Acrobat軟體產品中導入XMP標準。 此後，XMP標準被廣泛採用。

### XMP生態系統 {#xmp-ecosystem}

XMP定義了 [中繼資料](https://en.wikipedia.org/wiki/Metadata) 模型，可與任何已定義的中繼資料項目集搭配使用。XMP也定義了基本屬性的特定結構 [](https://en.wikipedia.org/wiki/XML_schema) ，這些基本屬性可用於記錄資源在經過多個處理步驟 (從被拍攝、掃描或創作為文字) 、通過照片編輯步驟(如 [](https://en.wikipedia.org/wiki/Image_scanner)[](https://en.wikipedia.org/wiki/Cropping_%28image%29) or color adjustment)到組合成最終影像時的歷史記錄。XMP可讓每個軟體程式或裝置沿途將其資訊新增至數位資源，然後再保留在最終數位檔案中。

XMP最常是使用 [W3C](https://en.wikipedia.org/wiki/World_Wide_Web_Consortium)[Resource Description Framework](https://en.wikipedia.org/wiki/Resource_Description_Framework) (RDF)的子集進行序列化和儲存，該子集又以 [XML表示](https://en.wikipedia.org/wiki/XML)。

## XMP的優點 {#advantages-of-xmp}

XMP比其他編碼標準和架構有下列優點：

* XMP型中繼資料功能強大且微調。
* XMP可讓您擁有一個屬性的多個值。
* XMP具有標準化編碼，可讓您輕鬆交換中繼資料。
* XMP可擴充。 您可以將其他資訊新增至資產。

### 可擴充 {#extensible}

XMP標準的設計可擴充，可讓您將自訂中繼資料類型新增至XMP資料。 EXIF則否 — 它有無法擴充的固定屬性清單。

>[!NOTE]
>
>XMP通常不允許嵌入二進位資料類型。 若要在XMP中傳送二進位資料（例如縮圖影像），必須以XML友好格式（例如Base64）來編碼。

## XMP核心概念 {#xmp-core-concepts}

以下各節將說明XMP的核心概念，包括命名空間和架構、屬性和值，以及語言替代項目。

### 命名空間和架構 {#namespaces-and-schemata}

XMP架構是通用XML命名空間中的一組屬性名稱，包含\
資料類型和描述性資訊。 XMP架構由其XML命名空間URI標識。 使用命名空間可避免名稱相同但含義不同之不同結構中的屬性之間產生衝突。

例如，兩個獨立設計結構中的&#x200B;**Creator**&#x200B;屬性可能代表建立資產的人員，也可能代表建立資產的應用程式(例如Adobe Photoshop)。

### 屬性和值 {#properties-and-values}

XMP可包含一或多個結構中的屬性。

例如，許多Adobe應用程式使用的典型子集可能包括：

* 都柏林核心架構：dc:title, dc:creator,dc:subject,dc:format, dc:rights
* XMP基本結構：xmp:CreateDate, xmp:CreatorTool, xmp:ModifyDate, xmp:metadataDate
* XMP權限管理結構：xmpRights:WebStatement, xmpRights:Marked
* XMP媒體管理結構：xmpMM:DocumentID

### 替代語言 {#language-alternatives}

XMP可讓您將&#x200B;**xml:lang**&#x200B;屬性新增至文字屬性，以指定文字的語言。

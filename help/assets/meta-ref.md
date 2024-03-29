---
title: 中繼資料結構參考
description: 了解描述資產中繼資料的標準慣例，包括Dublin Core、IPTC和其他中繼資料結構。
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 883bebc6-8bbc-43b1-91e5-9e2bf2470b6e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 3%

---

# 中繼資料結構參考 {#metadata-schemata-reference}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

以下引用包括有關特定元資料結構（按字母順序）的資訊，以及屬性及其定義的清單。

## 都柏林核心 {#dublin-core}

都柏林核心中繼資料提供一套標準化的慣例，用於描述資產，以便更容易找到。 在 [!DNL Experience Manager] Assets, the Dublin Core描述數字資產，包括視頻、聲音、影像和文檔。

簡單的都柏林核心元資料元素集(DCMES)包含下表中列出的15個元資料元素。 每個都柏林核心元素都是選用元素，且可重複。 您可以像新增或刪除媒體類型特定中繼資料一樣，新增或刪除都柏林核心中繼資料資訊。

除了DCMES之外，還有由Dublin Core Initiative建立的其他元資料元素。 請參閱 [都柏林核心計畫](https://dublincore.org/) 以取得更多資訊。

| 屬性 | 說明 |
|---|---|
| 貢獻者 | 負責對內容作出貢獻的人員或公司。 |
| 覆蓋 | 資產涵蓋的地理位置或時段。 |
| 建立者 | 負責建立內容的人員或公司。 |
| 日期 | 與資產相關聯的日期或期間。 |
| 說明 | 資產的詳細資訊。 |
| 格式 | 資產的檔案格式、實體媒體或維度。 [!DNL Experience Manager] 使用dc:format表示資產的mime類型。 |
| 識別碼 | 資產的唯一參考。 |
| 語言 | 資產的語言（例如，英文）。 |
| 發佈者 | 負責使資產可用的人員或公司。 |
| 關係 | 相關資產。 |
| 權利 | 關於誰擁有此資產的權限的資訊。 |
| source | 資產衍生自的相關資產。 |
| 主旨 | 資產主題。 |
| 標題 | 資產的名稱。 |
| 類型 | 資產的性質或類型。 |

## IPTC {#iptc}

國際新聞電信理事會(IPTC)是全球新聞機構的聯合體，其目標之一是制定和維護技術標準。 IPTC為影像定義了一套照片元資料標準，這些標準幾乎在攝影師中被普遍接受。 這些元資料標準是20世紀90年代建立的稱為IPTC資訊交換模型(IIM)的更廣泛標準的一部分。

雖然IPTC標頭資訊已被XMP取代，但XMP可使用IPTC核心架構和擴充架構。 在映像程式中，XMP和IPTC屬性都同步。

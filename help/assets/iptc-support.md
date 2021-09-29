---
title: 支援IPTC元資料
description: 了解Adobe Experience Manager Assets如何透過Adobe Bridge和其他創意應用程式支援新增至資產的IPTC中繼資料、創意評等和關鍵字。
contentOwner: AG
feature: Metadata
role: User,Admin,Leader
exl-id: 3e22e8e4-3675-4d6d-94f4-fc1a4d4801e8
source-git-commit: 1e3cd6ce3138113721183439f7cfb9daed6e0e58
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 7%

---

# 支援IPTC元資料 {#support-for-iptc-metadata}

了解Adobe Experience Manager Assets如何透過Adobe Bridge和其他創意應用程式支援新增至資產的IPTC中繼資料、創意評等和關鍵字。

Adobe Experience Manager Assets支援IPTC中繼資料標準，此標準被廣泛用於描述資產。 這樣，[!DNL Experience Manager Assets]增強了各方對其影像的接受，包括攝影師、創意機構、圖書館、博物館等。

資產的預設中繼資料結構現在整合了IPTC核心和IPTC擴充功能中繼資料結構，以定義完整的中繼資料屬性，讓使用者能新增關於影像中顯示之人員、位置和產品的精確且可靠資料。 此外，也支援建立影像的日期、名稱和識別碼，以及彈性的權限資訊表達方式。

資產的「屬性」頁面現在包含個別的標籤，以在可編輯欄位中顯示IPTC核心和IPTC擴充功能中繼資料。

1. 從「資產」使用者介面中選取影像。
1. 按一下或點選工具列中的&#x200B;**[!UICONTROL 屬性]**&#x200B;圖示。
1. 在「屬性」頁面中，按一下/點選&#x200B;**[!UICONTROL IPTC]**&#x200B;標籤以檢視資產的IPTC中繼資料。
1. 視需要編輯IPTC元資料屬性。

   ![iptc_tab](assets/iptc_tab.png)

1. 按一下/點選「 **[!UICONTROL IPTC擴充功能」標籤]** ，以檢視資產的IPTC擴充功能中繼資料。
1. 視需要編輯ITPC擴充功能中繼資料屬性。
1. 點選/按一下&#x200B;**[!UICONTROL 儲存並關閉]**&#x200B;以儲存變更。

## 創意評分支援 {#creative-rating-support}

除了顯示個別使用者評等和匯總評等外，「屬性」頁面現在還會顯示透過Adobe Bridge和其他創意應用程式指派給資產的評等

這些評等可在「進階」標 **[!UICONTROL 簽的「創作評分]** 」區段 **[!UICONTROL 下取得]** 。

此評等是唯讀屬性，範圍介於1到5之間。 您可以從「搜尋面板」根據資產的創作評等來搜尋資產。

不過，此屬性目前未編列索引，以避免與使用者所做的自訂變更產生任何衝突。

## 關鍵字支援 {#keyword-support}

「屬性」頁面的&#x200B;**[!UICONTROL IPTC]**&#x200B;標籤也會顯示透過Adobe Bridge和其他創意應用程式新增至資產的關鍵字。 您也可以編輯這些關鍵字，並從&#x200B;**[!UICONTROL IPTC]**&#x200B;標籤新增更多關鍵字。

![關鍵字](assets/keywords.png)

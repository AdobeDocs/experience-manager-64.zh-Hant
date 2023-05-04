---
title: 支援IPTC元資料
description: 了解Adobe Experience Manager Assets如何透過Adobe Bridge和其他創意應用程式支援新增至資產的IPTC中繼資料、創意評等和關鍵字。
contentOwner: AG
feature: Metadata
role: User,Admin,Leader
exl-id: 3e22e8e4-3675-4d6d-94f4-fc1a4d4801e8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 7%

---

# 支援IPTC元資料 {#support-for-iptc-metadata}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

了解Adobe Experience Manager Assets如何透過Adobe Bridge和其他創意應用程式支援新增至資產的IPTC中繼資料、創意評等和關鍵字。

Adobe Experience Manager Assets支援IPTC中繼資料標準，此標準被廣泛用於描述資產。 這邊， [!DNL Experience Manager Assets] 增強了攝影師、創意機構、圖書館、博物館等各方對其影像的接受度。

資產的預設中繼資料結構現在整合了IPTC核心和IPTC擴充功能中繼資料結構，以定義完整的中繼資料屬性，讓使用者能新增關於影像中顯示之人員、位置和產品的精確且可靠資料。 此外，也支援建立影像的日期、名稱和識別碼，以及彈性的權限資訊表達方式。

資產的「屬性」頁面現在包含個別的標籤，以在可編輯欄位中顯示IPTC核心和IPTC擴充功能中繼資料。

1. 從「資產」使用者介面中選取影像。
1. 按一下或點選 **[!UICONTROL 屬性]** 圖示。
1. 在「屬性」頁面中，按一下/點選 **[!UICONTROL IPTC]** 頁簽，查看資產的IPTC元資料。
1. 視需要編輯IPTC元資料屬性。

   ![iptc_tab](assets/iptc_tab.png)

1. 按一下/點選「 **[!UICONTROL IPTC擴充功能」標籤]** ，以檢視資產的IPTC擴充功能中繼資料。
1. 視需要編輯ITPC擴充功能中繼資料屬性。
1. 點選/按一下 **[!UICONTROL 儲存並關閉]** 以儲存變更。

## 創意評分支援 {#creative-rating-support}

除了顯示個別使用者評等和匯總評等外，「屬性」頁面現在還會顯示透過Adobe Bridge和其他創意應用程式指派給資產的評等

這些評等可在「進階」標 **[!UICONTROL 簽的「創作評分]** 」區段 **[!UICONTROL 下取得]** 。

此評等是唯讀屬性，範圍介於1到5之間。 您可以從「搜尋面板」根據資產的創作評等來搜尋資產。

不過，此屬性目前未編列索引，以避免與使用者所做的自訂變更產生任何衝突。

## 關鍵字支援 {#keyword-support}

此 **[!UICONTROL IPTC]** 屬性頁面的索引標籤也會顯示透過Adobe Bridge和其他創意應用程式新增至資產的關鍵字。 您也可以編輯這些關鍵字，並從 **[!UICONTROL IPTC]** 標籤。

![關鍵字](assets/keywords.png)

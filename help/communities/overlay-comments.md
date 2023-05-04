---
title: 覆蓋圖註解元件
seo-title: Overlay Comments Component
description: 覆蓋圖注釋元件概觀
seo-description: Overlay Comments component overview
uuid: 634240e2-99bb-4107-89f5-c66d53e2515d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 4849da13-518c-40c8-b80e-1b2264d7f8f5
exl-id: 31528814-02bc-4978-87fa-5c8074b454ed
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 3%

---

# 覆蓋圖註解元件 {#overlay-comments-component}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

其意圖 [覆蓋](client-customize.md#overlays) 預設元件是全局更改元件的外觀或行為，以用於元件的所有相對參照。 在/libs資料夾中搜尋之前，會仰賴Sling的性質來解析至/apps資料夾。 因此，元件的路徑與預設元件的路徑相同，只是它位於/apps資料夾中，而不是/libs資料夾中。

## 範例 {#example}

假設您要修改留言功能，以便變更留言標題，使其符合您網站的設計，以便不再顯示任何留言的頭像。 隱藏頭像的解決方案是使用CSS，或如此處所述，在應用程式資料夾中覆蓋header.jsp，這樣包含頭像的HTML就不會傳送給用戶端。

若要覆蓋留言，您必須：

1. [「注釋」頁](overlay-create-comments-page.md)
1. [建立節點](overlay-create-nodes.md)
1. [更改外觀](overlay-alter-appearance.md)

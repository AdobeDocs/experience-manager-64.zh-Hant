---
title: 覆蓋圖註解元件
seo-title: 覆蓋圖註解元件
description: 覆蓋圖注釋元件概觀
seo-description: 覆蓋圖注釋元件概觀
uuid: 634240e2-99bb-4107-89f5-c66d53e2515d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 4849da13-518c-40c8-b80e-1b2264d7f8f5
exl-id: 31528814-02bc-4978-87fa-5c8074b454ed
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---

# 覆蓋注釋元件{#overlay-comments-component}

[覆蓋](client-customize.md#overlays)預設元件的意圖是全局更改元件的外觀或行為，以便對元件進行所有相對引用。 在/libs資料夾中搜尋之前，會仰賴Sling的性質來解析至/apps資料夾。 因此，元件的路徑與預設元件的路徑相同，只是它位於/apps資料夾中，而不是/libs資料夾中。

## 範例 {#example}

假設您要修改留言功能，以便變更留言標題，使其符合您網站的設計，以便不再顯示任何留言的頭像。 隱藏頭像的解決方案是使用CSS，或如此處所述，在應用程式資料夾中覆蓋header.jsp，這樣包含頭像的HTML就不會傳送給用戶端。

若要覆蓋留言，您必須：

1. [「注釋」頁](overlay-create-comments-page.md)
1. [建立節點](overlay-create-nodes.md)
1. [更改外觀](overlay-alter-appearance.md)

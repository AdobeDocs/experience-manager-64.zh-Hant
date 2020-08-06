---
title: 覆蓋注釋元件
seo-title: 覆蓋注釋元件
description: 覆蓋註解元件概觀
seo-description: 覆蓋註解元件概觀
uuid: 634240e2-99bb-4107-89f5-c66d53e2515d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 4849da13-518c-40c8-b80e-1b2264d7f8f5
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---


# 覆蓋注釋元件 {#overlay-comments-component}

覆蓋缺 [省元件](client-customize.md#overlays) （對於元件的所有相對參照）的意圖是全局更改元件的外觀或行為。 在/libs檔案夾中搜尋前，會依循sling的性質來解析至/apps檔案夾。 因此，元件的路徑與預設元件的路徑相同，只不過它位於/apps檔案夾而非/libs檔案夾中。

## 範例 {#example}

假設您想要修改註解功能，以符合您網站的設計，方法是變更註解標題，以便不再顯示任何註解的頭像。 隱藏頭像的解決方案是使用CSS，或如此處所述，在apps資料夾中覆蓋header.jsp，讓包含頭像的HTML永遠不會傳送給用戶端。

若要覆蓋注釋，您必須：

1. [「注釋」頁](overlay-create-comments-page.md)
1. [建立節點](overlay-create-nodes.md)
1. [改變外觀](overlay-alter-appearance.md)


---
title: 資產測試的命名慣例
seo-title: Naming conventions for assets
description: 儲存庫中的節點受Java內容儲存庫的命名慣例的約束。 不過，Adobe Experience Manager會進一步規範資產節點名稱。
seo-description: Nodes in the repository are subject to naming conventions of the Java Content Repository. However, Adobe Experience Manager imposes further conventions for the name of asset nodes.
uuid: 6b622a60-90e8-461e-9b67-42c11c7038f9
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 55e66c66-0120-4ed4-94c5-d65a434bb59b
exl-id: 3dc38c37-f2a0-44f5-90f6-fee8c6f84ff4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 4%

---

# 資產測試的命名慣例{#naming-conventions-for-assets-testing}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

儲存庫中的節點受 [Java內容儲存庫](/help/sites-developing/the-basics.md#java-content-repository). 不過，Adobe Experience Manager會進一步規範資產節點名稱。

## 傳統 UI {#classic-ui}

傳統UI實施更嚴格的限制：

* 當節點名稱明確時，驗證資產名稱，條件為：

   * 提供資產標題以便轉換為節點名稱
   * 提供了顯式節點名

* 有效字元（從傳統UI內建立資產時，只有這些字元才有效）:

   * &#39;a&#39;到&#39;z&#39;
   * &#39;A&#39;到&#39;Z&#39;
   * &#39;0&#39;到&#39;9&#39;
   * _（下划線）
   * `-` （破折號/減號）

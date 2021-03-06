---
title: 資產測試的命名慣例
seo-title: 資產的命名慣例
description: 儲存庫中的節點受Java內容儲存庫的命名慣例的約束。 不過，Adobe Experience Manager會進一步規範資產節點名稱。
seo-description: 儲存庫中的節點受Java內容儲存庫的命名慣例的約束。 不過，Adobe Experience Manager會進一步規範資產節點名稱。
uuid: 6b622a60-90e8-461e-9b67-42c11c7038f9
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 55e66c66-0120-4ed4-94c5-d65a434bb59b
exl-id: 3dc38c37-f2a0-44f5-90f6-fee8c6f84ff4
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 1%

---

# 資產測試的命名慣例{#naming-conventions-for-assets-testing}

儲存庫中的節點受[Java內容儲存庫](/help/sites-developing/the-basics.md#java-content-repository)的命名慣例的約束。 不過，Adobe Experience Manager會進一步規範資產節點名稱。

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

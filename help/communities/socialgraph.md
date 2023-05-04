---
title: 使用社交圖表
seo-title: Using Social Graph
description: 將下列元件新增至頁面
seo-description: Adding a Following component to a page
uuid: 8be6334b-e6c9-40bc-90a8-750b98419470
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 0ce57ab1-e4c6-4c38-963d-556eef8757f2
exl-id: ab829d28-278d-4139-af16-edcc24b3d56b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 4%

---

# 使用社交圖表 {#using-social-graph}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 簡介 {#introduction}

社群成員遵循的能力 [活動](activities.md) 並透過兩個元件來建立： `Follow`和 `Following`.

此 `Follow`元件必須與其他資源相關聯，並且此關聯已為社群成員和功能建立。

此 `Following`元件僅列出當前成員後面或當前成員後面的成員。 此成員間關係的社交圖表包含在為 [社群網站](overview.md#communitiessites).

## 將後續內容新增至頁面 {#adding-following-to-a-page}

如果需要新增 `Following`在製作模式中，找到元件至頁面 `Communities / Following` 並將其拖曳至應該出現社交圖表的頁面上。

如需必要資訊，請造訪 [Communities元件基本知識](basics.md).

當 [必要的用戶端程式庫](essentials-socialgraph.md#essentials-for-client-side) 包含在內，以下為方式 `Following` 元件隨即出現：

![chlimage_1-447](assets/chlimage_1-447.png)

## 配置以下內容 {#configuring-following}

目前，必須設定屬性，才能判斷元件是否顯示 `follows`關係，或 `following`關係。

## 其他資訊 {#additional-information}

如需詳細資訊，請參閱 [社交圖表要點](essentials-socialgraph.md) 頁面。

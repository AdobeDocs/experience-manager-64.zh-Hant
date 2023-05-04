---
title: 編輯 Launch
seo-title: Editing Launches
description: 為頁面（或一組頁面）建立啟動後，您可以編輯頁面啟動復本中的內容。
seo-description: When a launch has been created for a page (or set of pages) you can edit the content in the launch copy of the page(s).
uuid: 3a310eeb-553d-4d2b-98b5-c5bc523b2aca
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 666b967a-e94b-4f94-a676-00adf150580f
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
exl-id: 98bccd13-431a-4cba-bb93-75cdcc98830a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 4%

---

# 編輯 Launch{#editing-launches}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 編輯啟動頁面 {#editing-launch-pages}

為頁面（或一組頁面）建立啟動後，您可以編輯頁面啟動復本中的內容。

1. 開啟頁面進行編輯。
1. 在Sidekick中，選取 **版本設定** 標籤，然後展開 **啟動** 群組。 目前正在編輯的啟動標題會使用粗體字型。

   ![chlimage_1-13](assets/chlimage_1-13.jpeg)

1. 選取您要處理的啟動，然後按一下 **交換機**.
1. 開始編輯。

   >[!NOTE]
   >
   >您可以使用 **頁面** sidekick索引標籤，以執行動作，例如 **建立子頁**，其中包括。

## 編輯Launch設定 {#editing-a-launch-configuration}

建立啟動後，您可以變更啟動名稱和啟動日期。 您也可以指定要與啟動相關聯的影像。

1. 開啟啟動管理頁面([http://localhost:4502/libs/launches/content/admin.html](http://localhost:4502/libs/launches/content/admin.html))。

1. 選取所需的啟動，然後按一下 **編輯** 要開啟對話框：

   * 在 **一般** 頁簽，您可以編輯：

      * **標題**
      * **上線日期**:這等同於啟動日期
      * **生產就緒**

      請參閱 [啟動 — 事件順序](/help/sites-authoring/launches.md#launches-the-order-of-events) 以了解這些欄位的用途和互動。

   * 在 **影像** 頁簽，您可以上傳影像檔案。


1. 按一下「**儲存**」。

## 探索頁面的啟動狀態 {#discovering-the-launch-status-of-a-page}

當您編輯頁面的啟動時，有關啟動的資訊會顯示在 **版本設定** 標籤：

* 啟動的名稱。
* 上次變更後的時間。
* 執行上次變更的使用者。
* 的狀態 **生產就緒** 標幟(orange=not set)green=set)。

![chlimage_1-186](assets/chlimage_1-186.png)

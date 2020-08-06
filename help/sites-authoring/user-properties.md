---
title: 設定帳戶環境
seo-title: 設定帳戶環境
description: AEM提供您設定帳戶的功能，以及作者環境的某些方面
seo-description: AEM提供您設定帳戶的功能，以及作者環境的某些方面
uuid: 01e76771-9ac8-4919-9e50-0a63826177d1
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 6afbc889-c613-40e6-8a25-1570dff32d60
translation-type: tm+mt
source-git-commit: cfa09d2f1a78eac609cb6df7817234559c8d26dc
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 8%

---


# 設定帳戶環境{#configuring-your-account-environment}

AEM提供您設定帳戶的功能，以及作者環境的某些方面。

Using the [User](/help/sites-authoring/user-properties.md#user-settings) option in the [header](/help/sites-authoring/basic-handling.md#the-header) and the associated [My Preferences](#my-preferences) dialog, you can modify your user options.

## 使用者設定 {#user-settings}

「用 **戶設定** 」對話框允許您訪問：

* 模擬為

   * 使用 [Impersonate(模擬](/help/sites-administering/security.md#impersonating-another-user) )功能，使用者可以代表其他使用者工作。

* 設定檔

   * 提供使用者設定的方便 [連結](/help/sites-administering/security.md))

* [我的喜好設定](/help/sites-authoring/user-properties.md#my-preferences)

   * 指定使用者專屬的各種偏好設定

![screen_shot_2018-03-20at103808](assets/screen_shot_2018-03-20at103808.png)

## 我的喜好設定 {#my-preferences}

「我 **的偏好設定** 」對話方塊是透過頁首中的「使 [用者](/help/sites-authoring/user-properties.md#user-settings) 」選項來存取。

每位使用者都可自行設定特定屬性。

![screen_shot_2018-03-20at102118](assets/screen_shot_2018-03-20at102118.png)

* **語言**

   這定義了編寫環境的UI使用的語言。 從可用清單中選擇所需的語言。

   此配置也用於傳統UI。

* **視窗管理**

   這會定義行為或開啟視窗。 選擇以下任一項：

   * **多個Windows** （預設）

      * 頁面將在新視窗中開啟。
   * **單一視窗**

      * 頁面將在目前視窗中開啟。


* **顯示資產桌面動態**

   這個選項需要AEM案頭應用程式才能使用。

* **附註顏色**

   這定義了建立批注時使用的預設顏色。

   * 按一下顏色區塊以開啟色票選取器以選取顏色。
   * 或者，在欄位中輸入所要色彩的十六進位程式碼。

* **相對日期顯示**

   為了改善可讀性，AEM會在過去七天內將日期轉譯為相對日期（例如，三天前），而將舊日期轉譯為確切日期（例如，2017年3月20日）。

   此選項定義系統中日期的顯示方式。 可使用下列選項：

   * **一律顯示確切日期**: 一律會顯示確切日期（從不是相對日期）。
   * **1天**: 相對日期會顯示為一天內的日期，否則會顯示確切日期。
   * **7天（預設值）**: 相對日期會顯示在7天內的日期，否則會顯示確切的日期。
   * **1個月**: 相對日期會顯示一個月內的日期，否則會顯示確切日期。
   * **1年**: 相對日期會顯示在一年內的日期，否則會顯示確切的日期。
   * **一律顯示相對日期**: 不會顯示確切日期，只顯示相對日期。

* **啟用快速鍵**

   AEM支援許多鍵盤快速鍵，讓撰寫工作更有效率。

   * [編輯頁面的鍵盤快速鍵](/help/sites-authoring/page-authoring-keyboard-shortcuts.md)
   * [控制台的鍵盤快速鍵](/help/sites-authoring/keyboard-shortcuts.md)

   此選項可啟用鍵盤快速鍵。 依預設會啟用這些功能，但可停用（例如，如果使用者有特定的協助工具需求）。

* **使用傳統製作體驗**

   此選項可啟 [用傳統的UI](/help/sites-classic-ui-authoring/home.md)-based頁面編寫。 預設會使用標準UI。

* **啟用資產首頁**

   只有在系統管理員為整個組織啟用資產首頁體驗時，此選項才可用。


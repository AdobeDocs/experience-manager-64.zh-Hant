---
title: 選取您的UI
seo-title: Selecting your UI
description: 設定您要在AEM中使用的介面
seo-description: Configure which interface you will use to work in AEM
uuid: af956219-178e-477b-a0cd-dd2341ed2ff0
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 9cadec1b-f435-4fd8-b4bc-1a23a0cf11f3
exl-id: 415efbe0-95f5-4c9e-ac33-c4a384a8271e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 2%

---

# 選取您的UI{#selecting-your-ui}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 了解UI

製作環境允許：

* [製作](/help/sites-authoring/author.md) (包括 [頁面編寫](/help/sites-authoring/author-environment-tools.md), [管理資產](/help/assets/home.md), [社群](/help/communities/author-communities.md))

* [管理](/help/sites-administering/home.md) 產生和維護網站上的內容時所需的任務

提供兩個圖形用戶介面來實現此目的。 可透過任何現代瀏覽器存取。

1. 觸控式UI

   * 這是現代的預設AEM UI。
   * 它主要呈灰色，介面乾淨平整。
   * 設計用於觸控式和桌上型電腦裝置，但所有裝置的外觀和感覺都一樣 [檢視和選取資源](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) 略有不同（點選與點按）。

      * 桌面:

   ![screen_shot_2018-03-23at115248](assets/screen_shot_2018-03-23at115248.png)

   * 平板電腦（或寬度小於1024像素的台式機）:

   ![screen_shot_2018-03-23at115505](assets/screen_shot_2018-03-23at115505.png)

1. 傳統 UI

   * 這是舊版UI，已在AEM中提供多年。
   * 主要是綠色。
   * 專為在桌上型電腦上使用而設計。
   * 以下檔案著重於現代UI。 如需在傳統UI中編寫的相關資訊，請參閱 [傳統UI的製作檔案](/help/sites-classic-ui-authoring/classicui.md).

   ![chlimage_1-232](assets/chlimage_1-232.png)

## 切換UI

雖然觸控式UI現在是標準UI，而且 [特徵奇偶校驗](../release-notes/touch-ui-features-status.md) 網站的管理與編輯工作已接近完成，因此有時使用者會想要切換至 [傳統UI](/help/sites-classic-ui-authoring/classicui.md). 執行此作業有數個選項。

>[!NOTE]
>
>如需與傳統UI功能比對狀態的詳細資訊，請參閱 [觸控式UI功能比較](../release-notes/touch-ui-features-status.md) 檔案。

您可以定義要使用哪個UI的不同位置：

* [設定您執行個體的預設UI](#configuring-the-default-ui-for-your-instance)  — 這會將預設UI設為在使用者登入時顯示，不過使用者可以覆寫此UI，並為其帳戶或目前的工作階段選取不同的UI。

* [為您的帳戶設定傳統UI編寫](/help/sites-authoring/select-ui.md#setting-classic-ui-authoring-for-your-account)  — 這會將UI設為編輯頁面時的預設值，不過使用者可以覆寫此UI，並為其帳戶或目前的工作階段選取不同的UI。

* [切換為目前工作階段的傳統UI](#switching-to-classic-ui-for-the-current-session)  — 這會切換至目前工作階段的傳統UI。

* 針對 [頁面編寫系統會在與UI的關係中進行特定覆寫](#ui-overrides-for-the-editor).

>[!CAUTION]
>
>切換至傳統UI的各種選項不會立即立即可用，您必須為執行個體特別設定。
>
>請參閱 [啟用對傳統UI的訪問](/help/sites-administering/enable-classic-ui.md) 以取得更多資訊。

>[!NOTE]
>
>從舊版升級的執行個體將保留傳統UI以進行頁面編寫。
>
>升級後，頁面編寫不會自動切換至觸控式UI，但您可以使用 [OSGi配置](/help/sites-deploying/configuring-osgi.md) 的 **WCM編寫UI模式服務** ( `AuthoringUIMode` 服務)。 請參閱 [編輯器的UI覆寫](#ui-overrides-for-the-editor).

## 設定您執行個體的預設UI {#configuring-the-default-ui-for-your-instance}

系統管理員可以使用設定在啟動和登入時顯示的UI [根對應](/help/sites-deploying/osgi-configuration-settings.md).

使用者預設值或工作階段設定可覆寫此值。

## 為您的帳戶設定傳統UI編寫 {#setting-classic-ui-authoring-for-your-account}

每個使用者都可以存取 [使用者偏好設定](/help/sites-authoring/user-properties.md) 以定義他/她是否想要使用傳統UI進行頁面編寫（而非預設UI）。

作業設定可以覆寫此值。

## 切換為目前工作階段的傳統UI {#switching-to-classic-ui-for-the-current-session}

使用觸控式UI案頭時，使用者可能會想要回復成傳統（僅限案頭）UI。 有數種方法可切換至目前工作階段的傳統UI:

* **導覽連結**

   >[!CAUTION]
   >
   >這個切換至傳統UI的選項不會立即立即可用，您必須針對執行個體特別設定。
   >
   >
   >請參閱 [啟用對傳統UI的訪問](/help/sites-administering/enable-classic-ui.md) 以取得更多資訊。

   如果已啟用此功能，每當您在適用的主控台上滑鼠時，就會出現圖示（螢幕的符號），點選/按一下此圖示，就會在傳統UI中開啟適當的位置。

   例如， **網站** to **siteadmin**:

   ![screen_shot_2018-03-23at111924](assets/screen_shot_2018-03-23at111924.png)

* **URL**

   歡迎使用的URL可存取傳統UI，位於 `welcome.html`. 例如：

   `http://localhost:4502/welcome.html`

   >[!NOTE]
   >
   >可透過 `sites.html`. 例如：
   >
   >
   >`http://localhost:4502/sites.html`

### 編輯頁面時切換至傳統UI {#switching-to-classic-ui-when-editing-a-page}

>[!CAUTION]
>
>這個切換至傳統UI的選項不會立即立即可用，您必須針對執行個體特別設定。
>
>請參閱 [啟用對傳統UI的訪問](/help/sites-administering/enable-classic-ui.md) 以取得更多資訊。

如果已啟用， **開啟傳統UI** 可從 **頁面資訊** 對話框：

![chlimage_1-49](assets/chlimage_1-49.png)

### 編輯器的UI覆寫 {#ui-overrides-for-the-editor}

在進行頁面編寫時，由用戶或系統管理員定義的設定可由系統覆蓋。

* 編寫頁面時：

   * 使用存取頁面時，強制使用傳統編輯器 `cf#` 中。 例如：

      `http://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

   * 使用時，強制使用觸控式編輯器 `/editor.html` 在URL中或使用觸控裝置時。 例如：

      `http://localhost:4502/editor.html/content/geometrixx/en/products/triangle.html`

* 任何強制都是暫時的，且僅對瀏覽器工作階段有效

   * Cookie集的設定取決於是否啟用觸控( `editor.html`)或classic( `cf#`)。

* 開啟頁面時 `siteadmin`，會檢查是否存在：

   * Cookie
   * 用戶首選項
   * 若兩者皆不存在，則會預設為 [OSGi配置](/help/sites-deploying/configuring-osgi.md) 的 **WCM編寫UI模式服務** ( `AuthoringUIMode` 服務)。

>[!NOTE]
>
>若 [使用者已定義頁面製作偏好設定](#setting-classic-ui-authoring-for-your-account)，則不會透過變更OSGi屬性來覆寫。

>[!CAUTION]
>
>由於使用Cookie（如前所述），因此不建議使用下列任一項：
>
>* 手動編輯URL — 非標準URL可能導致未知情況且缺乏功能。
>* 讓兩個編輯器同時開啟 — 例如，在個別視窗中。
>


---
title: 選擇您的UI
seo-title: 選擇您的UI
description: 設定您要在AEM中使用的介面
seo-description: 設定您要在AEM中使用的介面
uuid: af956219-178e-477b-a0cd-dd2341ed2ff0
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 9cadec1b-f435-4fd8-b4bc-1a23a0cf11f3
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 1%

---


# 選擇您的UI{#selecting-your-ui}

## 瞭解UI

作者環境允許：

* [製作](/help/sites-authoring/author.md) (包括 [頁面製作](/help/sites-authoring/author-environment-tools.md), [管理資產](/help/assets/home.md), [社群](/help/communities/author-communities.md))

* [管理](/help/sites-administering/home.md) ，產生和維護網站內容時所需的工作

為此，提供了兩個圖形用戶介面。 這些功能可透過任何現代化瀏覽器存取。

1. 觸控式UI

   * 這是現代的預設AEM UI。
   * 它以灰色為主，介面簡潔平整。
   * 設計用於觸控和桌上型裝置時，所有裝置的外觀和感覺都相同，但檢視和選取資源 [的方式略有不同](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) （點選與點選）。

      * 桌面:

   ![screen_shot_2018-03-23at115248](assets/screen_shot_2018-03-23at115248.png)

   * 平板電腦裝置（或桌上型電腦，寬度小於1024像素）:

   ![screen_shot_2018-03-23at115505](assets/screen_shot_2018-03-23at115505.png)

1. 傳統 UI

   * 這是舊版UI，在AEM中已提供多年。
   * 它主要是綠色的。
   * 它是專為桌上型裝置所設計。
   * 以下說明檔案著重於現代UI。 如需在傳統UI中製作內容的詳細資訊，請參 [閱Classic UI的製作檔案](/help/sites-classic-ui-authoring/classicui.md)。

   ![chlimage_1-232](assets/chlimage_1-232.png)

## 切換UI

雖然觸控式使用者介面現在已成為標準的使用者介面，而且 [](../release-notes/touch-ui-features-status.md) ，網站的管理與編輯已接近功能均等，但有時使用者可能會想要切換至 [傳統使用者介面](/help/sites-classic-ui-authoring/classicui.md)。 有幾種方法可做到這一點。

>[!NOTE]
>
>如需與傳統UI功能對等狀態的詳細資訊，請參閱 [Touch UI功能對等檔案](../release-notes/touch-ui-features-status.md) 。

您可以定義要使用哪些UI的不同位置：

* [為您的例項設定預設UI](#configuring-the-default-ui-for-your-instance) —— 這會將預設UI設定為在使用者登入時顯示，但使用者可能可以覆寫此UI，並為其帳戶或目前作業選取不同的UI。

* [為您的帳戶設定傳統UI編寫](/help/sites-authoring/select-ui.md#setting-classic-ui-authoring-for-your-account) -雖然使用者可以覆寫此UI，並為其帳戶或目前作業選取不同的UI，但這會將UI設定為編輯頁面時的預設UI。

* [切換至目前作業的傳統UI](#switching-to-classic-ui-for-the-current-session) —— 此切換至目前作業的傳統UI。

* 在製作頁面 [時，系統會針對UI進行特定覆寫](#ui-overrides-for-the-editor)。

>[!CAUTION]
>
>切換至傳統UI的各種選項並非立即現成可用，必須為您的例項特別設定。
>
>如需詳 [細資訊，請參閱啟用Classic UI](/help/sites-administering/enable-classic-ui.md) 。

>[!NOTE]
>
>從舊版升級的例項將保留用於頁面製作的傳統UI。
>
>升級後，頁面製作不會自動切換至觸控式UI，但您可以使用 [WCM Authoring UI Mode Service](/help/sites-deploying/configuring-osgi.md) （服務）的 **OSGi設定來**`AuthoringUIMode` 設定此設定。 請參 [閱編輯器的UI覆蓋](#ui-overrides-for-the-editor)。

## 為實例配置預設UI {#configuring-the-default-ui-for-your-instance}

系統管理員可以使用根映射來配置在啟動和登錄時顯示的 [UI](/help/sites-deploying/osgi-configuration-settings.md)。

用戶預設值或會話設定可以覆蓋此選項。

## 設定帳戶的傳統UI編寫 {#setting-classic-ui-authoring-for-your-account}

每位使用者都可存取其使 [用者偏好](/help/sites-authoring/user-properties.md) ，以定義他／她是否想要使用傳統UI來製作頁面（而非預設UI）。

這可以由會話設定覆蓋。

## 切換至目前作業的傳統UI {#switching-to-classic-ui-for-the-current-session}

當使用觸控式UI案頭使用者可能想要回復為傳統（僅限桌上型）UI。 有幾種方法可切換至目前作業的傳統UI:

* **導覽連結**

   >[!CAUTION]
   >
   >切換至傳統UI的這個選項不會立即現成可用，必須為您的例項特別設定。
   >
   >
   >如需詳 [細資訊，請參閱啟用Classic UI](/help/sites-administering/enable-classic-ui.md) 。

   如果啟用此功能，每當您在滑鼠移過適用的主控台時，就會出現圖示（螢幕的符號），點選／按一下此功能，就會開啟傳統UI中的適當位置。

   例如，從網站到網站 **管理員** 的 **連結**:

   ![screen_shot_2018-03-23at111924](assets/screen_shot_2018-03-23at111924.png)

* **URL**

   您可以使用歡迎畫面的URL，在中存取傳統UI `welcome.html`。 例如：

   `http://localhost:4502/welcome.html`

   >[!NOTE]
   >
   >可透過存取觸控式使用者介面 `sites.html`。 例如：
   >
   >
   >`http://localhost:4502/sites.html`

### 編輯頁面時切換至傳統UI {#switching-to-classic-ui-when-editing-a-page}

>[!CAUTION]
>
>切換至傳統UI的這個選項不會立即現成可用，必須為您的例項特別設定。
>
>如需詳 [細資訊，請參閱啟用Classic UI](/help/sites-administering/enable-classic-ui.md) 。

如果啟用， **則可從「頁面資訊** 」對話方 **塊中開啟Classic UI** :

![chlimage_1-49](assets/chlimage_1-49.png)

### 編輯器的UI覆蓋 {#ui-overrides-for-the-editor}

在製作頁面時，由用戶或系統管理員定義的設定可由系統覆蓋。

* 編寫頁面時：

   * 使用URL中的頁面存取時，會強制使用 `cf#` 傳統編輯器。 例如：

      `http://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

   * 在URL中使用或在使用觸控裝置時， `/editor.html` 會強制使用觸控式編輯器。 例如：

      `http://localhost:4502/editor.html/content/geometrixx/en/products/triangle.html`

* 任何強制動作都是暫時的，且僅適用於瀏覽器作業

   * Cookie集的設定將視使用的是啟用觸控( `editor.html`)還是傳統( `cf#`)而定。

* 當透過開啟頁 `siteadmin`面時，會檢查是否存在：

   * Cookie
   * 使用者偏好設定
   * 如果兩者均不存在，則預設為 [WCM Authoring UI Mode Service](/help/sites-deploying/configuring-osgi.md) ( **service)**`AuthoringUIMode` OSGi組態中設定的定義。

>[!NOTE]
>
>如果 [使用者已定義頁面製作的偏好設定](#setting-classic-ui-authoring-for-your-account)，將不會變更OSGi屬性來覆寫。

>[!CAUTION]
>
>由於使用Cookie（如前所述），因此不建議您執行下列任一動作：
>
>* 手動編輯URL —— 非標準URL可能導致未知情況及功能不足。
>* 讓兩個編輯器同時開啟——例如，在個別視窗中。

>




---
title: 初始沙盒內容
seo-title: 初始沙盒內容
description: 建立內容
seo-description: 建立內容
uuid: 9810fe47-8d1a-4238-9b9c-0cc47c63d97a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: e8f28cd5-7950-4aab-bf62-3d4ed3d33cbd
translation-type: tm+mt
source-git-commit: 2d1e39120d79de029927011d48f7397b53ad91bc
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 2%

---


# 初始沙盒內容{#initial-sandbox-content}

在本節中，您將建立以下所有頁面，這些頁面均使用[頁面模板](initial-app.md#createthepagetemplate):

* SCF沙盒網站，此網站會重新導向至首頁的英文版

   * SCF沙盒——網站英文版的首頁

      * SCF播放——要播放的首頁的子項

雖然本教學課程不深入探討[語言副本](../../help/sites-administering/tc-prep.md)，但是其設計方式是讓根頁面透過HTML標題實作使用者偏好語言的偵測，並重新導向至該語言的適當首頁面。 慣例是使用雙字母國家／地區代碼作為頁面的節點名稱，例如英文為&quot;en&quot;、法文為&quot;fr&quot;等。

## 建立首頁{#create-first-pages}

現在有[頁面範本](initial-app.md#createthepagetemplate)，我們可以在/content目錄中建立網站的根頁面。

1. 標準UI目前提供建立網站的藍圖。 由於本教學課程是建立簡單網站，因此傳統的UI十分實用。

   若要切換至傳統UI，請選取全域導覽，並將滑鼠指標暫留在「專案」圖示的右側。 選擇出現的&#x200B;*Switch to Classic UI*&#x200B;表徵圖：

   ![chlimage_1-36](assets/chlimage_1-36.png)

   切換至傳統UI的能力必須由管理員[啟用。](../../help/sites-administering/enable-classic-ui.md)

1. 從[傳統UI歡迎頁面](http://localhost:4502/welcome.html)選擇&#x200B;**[!UICONTROL 網站]**。

   ![chlimage_1-37](assets/chlimage_1-37.png)

   或者，瀏覽至[/siteadmin，直接存取網站的傳統UI。](http://localhost:4502/siteadmin)

1. 在瀏覽器窗格中，選擇&#x200B;**[!UICONTROL 網站]**，然後在工具列中選擇&#x200B;**[!UICONTROL 新建>新頁面]**。

   在&#x200B;**[!UICONTROL 建立頁面]**&#x200B;對話框中，輸入以下內容：

   * 標題: `SCF Sandbox Site`
   * 名稱: `an-scf-sandbox`
   * 選擇&#x200B;**[!UICONTROL SCF沙盒播放模板]**
   * 按一下&#x200B;**[!UICONTROL 建立]**

   ![chlimage_1-38](assets/chlimage_1-38.png)

1. 在瀏覽器窗格中，選擇您剛建立的頁面`/Websites/SCF Sandbox Site`，然後按一下&#x200B;**[!UICONTROL 新建>新建頁面]**:

   * 標題: `SCF Sandbox`
   * 名稱: `en`
   * 選擇&#x200B;**SCF沙盒播放模板**
   * 按一下&#x200B;**建立**

1. 在瀏覽器窗格中，選擇您剛建立的頁面`/Websites/SCF Sandbox Site/SCF Sandbox`，然後按一下&#x200B;**[!UICONTROL 新建>新建頁面]**

   * 標題: `SCF Play`
   * 名稱: `play`
   * 選擇&#x200B;**[!UICONTROL SCF沙盒播放模板]**
   * 按一下&#x200B;**[!UICONTROL 建立]**

1. 網站現在會以此方式出現在網站主控台中。 請注意，在瀏覽器窗格中選擇的項目的子頁面會顯示在右窗格中，供管理。

   ![chlimage_1-39](assets/chlimage_1-39.png)

   這是使用網站工具和模板建立內容的儲存庫視圖：

   ![chlimage_1-40](assets/chlimage_1-40.png)

## 添加設計路徑{#add-the-design-path}

當使用「工具」控制台的設計部分建立` [/etc/designs/an-scf-sandbox](setup-website.md#setupthedesigntreeetcdesigns)`時，屬性&quot;

* `cq:template="/libs/wcm/core/templates/designpage"`

已定義，提供使用`currentDesign.getPath()`在指令檔中參考設計資產的可選功能。 例如

* &lt;>


   * 名稱: `cq:designPath`
   * 類型: `String`
   * 值: `/etc/designs/an-scf-sandbox`

* 按一下綠色`[+] Add`

儲存庫應如下所示：

![chlimage_1-41](assets/chlimage_1-41.png)

* 按一下&#x200B;**[!UICONTROL 保存全部]**

[ 難以拯救？重新登入！]

>[!NOTE]
>
>cq:designPath的使用是選擇性的，與clientlibs[的使用無關，這些是SCF元件使用](develop-app.md#includeclientlibsintemplate)clientlibs[來管理其JS和CSS時的必要項。](client-customize.md#clientlibs-for-scf)


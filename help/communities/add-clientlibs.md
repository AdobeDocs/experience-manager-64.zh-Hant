---
title: 新增Clientlibs
seo-title: 新增Clientlibs
description: 新增ClientLibraryFolder
seo-description: 新增ClientLibraryFolder
uuid: cdc1d258-2011-4517-9206-dd2b5d1f7e0d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: c84040b0-7850-4960-b676-ffa0a74c8cb2
translation-type: tm+mt
source-git-commit: 805e4411930749ff4b6b05ea4a8b87b4f96d72fd
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 1%

---


# 新增Clientlibs {#add-clientlibs}

## 新增ClientLibraryFolder(clientlibs) {#add-a-clientlibraryfolder-clientlibs}

建立名為的ClientLibraryFolder, `clientlibs`其中將包含用於呈現您網站頁面的JS和CSS。

給 `categories`予此用戶端程式庫的屬性值是用來直接從內容頁面包含此clientlib，或將其內嵌在其他clientlib中的識別碼。

1. 使用 **[!UICONTROL CRXDE Lite]**，展開 `/etc/designs`

1. 右鍵按一下並 `an-scf-sandbox` 選取 `Create Node`

   * 名稱: `clientlibs`
   * 類型: `cq:ClientLibraryFolder`

1. Click **[!UICONTROL OK]**

![chlimage_1-220](assets/chlimage_1-220.png)

在新節 **[!UICONTROL 點的]** 「屬性」選 `clientlibs` 項卡中，輸入 **`categories`** 屬性：

* 名稱： **[!UICONTROL 類別]**
* 類型： **[!UICONTROL 字串]**
* 值： **[!UICONTROL apps.an-scf-sandbox]**
* Click **[!UICONTROL Add]**
* 按一下「 **[!UICONTROL 全部儲存」]**

注意：使用「應用程式」來預設類別值。 是將「擁有的應用程式」識別為位於/apps資料夾而非/libs的慣例。  重要：新增預留位 `js.txt` 置和 `css.txt` 檔案。 （沒有cq:ClientLibraryFolder，它並非正式。）


1. 按一下滑鼠右鍵 **`/etc/designs/an-scf-sandbox/clientlibs`**
1. 選擇 **[!UICONTROL 建立檔案……]**
1. Enter **[!UICONTROL Name]**: `css.txt`

1. 選擇 **[!UICONTROL 建立檔案……]**
1. Enter **[!UICONTROL Name]**: `js.txt`

1. 按一下「 **[!UICONTROL 全部儲存」]**

![chlimage_1-221](assets/chlimage_1-221.png)

css.txt和js.txt的第一行會識別從中可找到下列檔案清單的基本位置。

請嘗試將css.txt的內容設定為：

```
#base=.
 style.css
```

然後，在clientlibs下建立名為style.css的檔案，並將內容設定為：

`body {`

`background-color: #b0c4de;`

`}`

## 嵌入SCF客戶端 {#embed-scf-clientlibs}

在節 **[!UICONTROL 點的]** 「屬性」 `clientlibs` 標籤中，輸入多值String屬性 **[!UICONTROL embed]**。 這將嵌入SCF [元件的必要客戶端庫(clientlibs)](client-customize.md#clientlibs-for-scf)。 在本教學課程中，我們將新增Communities元件所需的許多clientlib。

**請注意** ，這可能是生產網站所需使用的方法，因為有考慮到每個頁面所下載的clientlib的便利性與大小／速度。

如果僅在單一頁面上使用一項功能，您可以直接在頁面上包含該功能的完整clientlib，例如&lt;% ui:includeClientLib類別=cq.social.hbs.forum&quot; %>

在本例中，我們將它們全部包括在內，因此，我們希望使用更基本的SCF客戶端libs，即作者clientlibs:

* 名稱: **`embed`**
* 類型: **`String`**

* 按一下 **`Multi`**
* 值: **`cq.social.scf`**

   *&lt;enter>將彈出對話框*

   *在每個&#x200B;**[項目後]**，按一下+以新增下列clientlib類別：*

   * **`cq.ckeditor`**
   * **`cq.social.author.hbs.comments`**
   * **`cq.social.author.hbs.forum`**
   * **`cq.social.author.hbs.rating`**
   * **`cq.social.author.hbs.reviews`**
   * **`cq.social.author.hbs.voting`**
   * Click **[!UICONTROL OK]**

* 按一下「 **[!UICONTROL 全部儲存」]**

![chlimage_1-222](assets/chlimage_1-222.png)

這是現在 `/etc/designs/an-scf-sandbox/clientlibs` 在儲存庫中的顯示方式：

![chlimage_1-223](assets/chlimage_1-223.png)

## 在PlayPage範本中包含Clientlibs {#include-clientlibs-in-playpage-template}

如果頁面 `apps.an-scf-sandbox` 上未包含ClientLibraryFolder類別，SCF元件將無法正常工作，也無法設定樣式，因為不提供必要的Javascript和樣式。

例如，如果不包含clientlibs,SCF注釋元件將顯示為未樣式化：

![chlimage_1-224](assets/chlimage_1-224.png)

一旦包含apps.an-scf-sandbox clientlibs後，SCF注釋元件就會顯示樣式：

![chlimage_1-225](assets/chlimage_1-225.png)

include語句屬於指令碼 `<head>` 的部 `<html>` 分。 預設值 **`foundation head.jsp`** 包含可重疊的指令碼： **`headlibs.jsp`**.

**複製headlibs.jsp並包含clientlibs:**

1. 使用 **[!UICONTROL CRXDE Lite]**，選取 **`/libs/foundation/components/page/headlibs.jsp`**
1. 按一下右鍵並選 **[!UICONTROL 擇「複製]** 」(Copy)（或從工具欄中選擇「複製」）
1. 選取 **`/apps/an-scf-sandbox/components/playpage`**
1. 按一下右鍵並選 **[!UICONTROL 擇「貼上]** 」（或從工具欄中選擇「貼上」）
1. 按兩下以 **`headlibs.jsp`** 開啟它
1. 在檔案結尾附加下列行

   **`<ui:includeClientLib categories="apps.an-scf-sandbox"/>`**

1. 按一下「 **[!UICONTROL 全部儲存」]**


```xml
<%@ page session="false" %><%
%><%@include file="/libs/foundation/global.jsp" %><%
%><ui:includeClientLib categories="cq.foundation-main"/><%
%>
<cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
<% currentDesign.writeCssIncludes(pageContext); %>
<ui:includeClientLib categories="apps.an-scf-sandbox"/>
```

在瀏覽器中載入您的網站，並查看背景是否不是藍色。

[http://localhost:4502/content/an-scf-sandbox/en/play.html](http://localhost:4502/content/an-scf-sandbox/en/play.html)

![chlimage_1-226](assets/chlimage_1-226.png)

## 保存您的作品 {#saving-your-work-so-far}

此時，存在極簡的沙盒，因此在播放時，如果儲存庫損壞並且您希望重頭開始，您可以關閉伺服器、更名或刪除資料夾crx-quickstart/、開啟伺服器、上傳和安裝此保存的軟體包，而不必重複這些最基本的步驟。

此套件存在於「建 [](create-sample-page.md) 立範例頁面」教學課程中，供迫不及待要跳入並開始播放的使用者使用……

要建立包：


* 從 **[!UICONTROL CRXDE Lite]**，按一下「套 [件」圖示](http://localhost:4502/crx/packmgr/)
* 按一下「 **[!UICONTROL 建立套件」]**

   * 封裝名稱: `an-scf-sandbox-minimal-pkg`
   * 版本: `0.1`
   * 群組：&lt;leave as default>
   * Click **[!UICONTROL OK]**

* 按一下「 **[!UICONTROL 編輯」]**

   * 「選擇篩 **[!UICONTROL 選器]** 」頁籤

      * 按一下「 **[!UICONTROL 新增篩選」]**
      * 根路徑：&lt;browse to `/apps/an-scf-sandbox`>
      * 按一下「完 **[!UICONTROL 成」]**
      * 按一下「 **[!UICONTROL 新增篩選」]**
      * 根路徑：&lt;browse to `/etc/designs/an-scf-sandbox`>
      * 按一下「完 **[!UICONTROL 成」]**
      * 按一下「 **[!UICONTROL 新增篩選」]**
      * 根路徑：&lt;browse to `/content/an-scf-sandbox`>
      * 按一下「完 **[!UICONTROL 成」]**
   * Click **[!UICONTROL Save]**


* 按一下「建 **[!UICONTROL 立」]**

現在，您可以選取「 **[!UICONTROL Download]** 」（下載）以儲存至磁碟並將它上傳至其他位置的「 **[!UICONTROL Upload Package]** 」（上傳套件），並選取「 **[!UICONTROL More」（更多）>「Replicate]** 」（複製），將沙盒推送至localhost發佈例項，以擴展沙盒的領域。

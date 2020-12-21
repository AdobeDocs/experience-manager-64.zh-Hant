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


# 添加Clientlibs {#add-clientlibs}

## 新增ClientLibraryFolder(clientlibs){#add-a-clientlibraryfolder-clientlibs}

建立名為`clientlibs`的ClientLibraryFolder，其中包含用於呈現您網站頁面的JS和CSS。

給予此客戶端庫的`categories`屬性值是用於直接從內容頁面包含此客戶端庫或將其嵌入到其他客戶端庫的標識符。

1. 使用&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;展開`/etc/designs`

1. 按一下右鍵`an-scf-sandbox`並選擇`Create Node`

   * 名稱: `clientlibs`
   * 類型: `cq:ClientLibraryFolder`

1. 按一下&#x200B;**[!UICONTROL 確定]**

![chlimage_1-220](assets/chlimage_1-220.png)

在新`clientlibs`節點的&#x200B;**[!UICONTROL 屬性]**&#x200B;頁籤中，輸入&#x200B;**`categories`**&#x200B;屬性：

* 名稱：**[!UICONTROL 類別]**
* 類型：**[!UICONTROL 字串]**
* 值：**[!UICONTROL apps.an-scf-sandbox]**
* 按一下&#x200B;**[!UICONTROL 添加]**
* 按一下&#x200B;**[!UICONTROL 保存全部]**

注意：使用「應用程式」來預設類別值。 是將「擁有的應用程式」識別為位於/apps資料夾而非/libs的慣例。  重要：添加佔位符`js.txt`和`css.txt`檔案。 （沒有cq:ClientLibraryFolder，它並非正式。）


1. 按一下右鍵&#x200B;**`/etc/designs/an-scf-sandbox/clientlibs`**
1. 選擇&#x200B;**[!UICONTROL 建立檔案……]**
1. 輸入&#x200B;**[!UICONTROL 名稱]**:`css.txt`

1. 選擇&#x200B;**[!UICONTROL 建立檔案……]**
1. 輸入&#x200B;**[!UICONTROL 名稱]**:`js.txt`

1. 按一下&#x200B;**[!UICONTROL 保存全部]**

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

## 嵌入SCF Clientlibs {#embed-scf-clientlibs}

在`clientlibs`節點的&#x200B;**[!UICONTROL 屬性]**&#x200B;標籤中，輸入多值字串屬性&#x200B;**[!UICONTROL embed]**。 這將嵌入SCF元件](client-customize.md#clientlibs-for-scf)所需的[客戶端庫(clientlibs)。 在本教學課程中，我們將新增Communities元件所需的許多clientlib。

**請注** 意，這可能是生產網站所需的方法，因為有考慮到每個頁面所下載的clientlibs的便利性與大小／速度。

如果僅在單一頁面上使用一項功能，您可以直接在頁面上包含該功能的完整clientlib，例如&lt;% ui:includeClientLib類別=cq.social.hbs.forum&quot; %>

在本例中，我們將它們全部包括在內，因此，我們希望使用更基本的SCF客戶端libs，即作者clientlibs:

* 名稱: **`embed`**
* 類型: **`String`**

* 按一下 **`Multi`**
* 值: **`cq.social.scf`**

   *&lt;enter> 將彈出對話框*

   *在每個&#x200B;**[項]**目後按一下+，新增下列clientlib類別：*

   * **`cq.ckeditor`**
   * **`cq.social.author.hbs.comments`**
   * **`cq.social.author.hbs.forum`**
   * **`cq.social.author.hbs.rating`**
   * **`cq.social.author.hbs.reviews`**
   * **`cq.social.author.hbs.voting`**
   * 按一下&#x200B;**[!UICONTROL 確定]**

* 按一下&#x200B;**[!UICONTROL 保存全部]**

![chlimage_1-222](assets/chlimage_1-222.png)

以下是`/etc/designs/an-scf-sandbox/clientlibs`現在應如何顯示在儲存庫中：

![chlimage_1-223](assets/chlimage_1-223.png)

## 在PlayPage範本{#include-clientlibs-in-playpage-template}中包含Clientlibs

如果頁面上未包括`apps.an-scf-sandbox` ClientLibraryFolder類別，SCF元件將無法正常工作，也無法設定樣式，因為必要的Javascript和樣式將不可用。

例如，如果不包含clientlibs,SCF注釋元件將顯示為未樣式化：

![chlimage_1-224](assets/chlimage_1-224.png)

一旦包含apps.an-scf-sandbox clientlibs後，SCF注釋元件就會顯示樣式：

![chlimage_1-225](assets/chlimage_1-225.png)

include語句屬於`<html>`指令碼的`<head>`部分。 預設&#x200B;**`foundation head.jsp`**&#x200B;包含可重疊的指令碼：**`headlibs.jsp`**。

**複製headlibs.jsp並包含clientlibs:**

1. 使用&#x200B;**[!UICONTROL CRXDE Lite]**，選擇&#x200B;**`/libs/foundation/components/page/headlibs.jsp`**
1. 按一下右鍵並選擇&#x200B;**[!UICONTROL Copy]**（或從工具欄中選擇「複製」）
1. 選取 **`/apps/an-scf-sandbox/components/playpage`**
1. 按一下右鍵並選擇&#x200B;**[!UICONTROL 貼上]**（或從工具欄中選擇貼上）
1. 按兩下&#x200B;**`headlibs.jsp`**&#x200B;將其開啟
1. 在檔案結尾附加下列行

   **`<ui:includeClientLib categories="apps.an-scf-sandbox"/>`**

1. 按一下&#x200B;**[!UICONTROL 保存全部]**


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

## 目前保存您的工作{#saving-your-work-so-far}

此時，存在極簡的沙盒，因此在播放時，如果儲存庫損壞並且您希望重頭開始，您可以關閉伺服器、更名或刪除資料夾crx-quickstart/、開啟伺服器、上傳和安裝此保存的軟體包，而不必重複這些最基本的步驟。

此套件存在於[建立範例頁面](create-sample-page.md)教學課程中，供迫不及待要跳入並開始播放的使用者使用……

要建立包：


* 在&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;中，按一下[包表徵圖](http://localhost:4502/crx/packmgr/)
* 按一下&#x200B;**[!UICONTROL 建立包]**

   * 封裝名稱: `an-scf-sandbox-minimal-pkg`
   * 版本: `0.1`
   * 群組：&lt;leave as default>
   * 按一下&#x200B;**[!UICONTROL 確定]**

* 按一下&#x200B;**[!UICONTROL 編輯]**

   * 選擇&#x200B;**[!UICONTROL Filters]**&#x200B;頁籤

      * 按一下&#x200B;**[!UICONTROL 添加filter]**
      * 根路徑：&lt;browse to `/apps/an-scf-sandbox`
      * 按一下&#x200B;**[!UICONTROL 完成]**
      * 按一下&#x200B;**[!UICONTROL 添加filter]**
      * 根路徑：&lt;browse to `/etc/designs/an-scf-sandbox`
      * 按一下&#x200B;**[!UICONTROL 完成]**
      * 按一下&#x200B;**[!UICONTROL 添加filter]**
      * 根路徑：&lt;browse to `/content/an-scf-sandbox`
      * 按一下&#x200B;**[!UICONTROL 完成]**
   * 按一下&#x200B;**[!UICONTROL 保存]**


* 按一下&#x200B;**[!UICONTROL Build]**

現在，您可以選取&#x200B;**[!UICONTROL Download]**&#x200B;將它儲存至磁碟和&#x200B;**[!UICONTROL Upload Package]**&#x200B;其他地方，並選取&#x200B;**[!UICONTROL More > Replicate]**，將沙盒推送至localhost發佈例項，以擴展您的沙盒領域。

---
title: 自訂主控台
seo-title: 自訂主控台
description: AEM提供多種機制，讓您自訂製作執行個體的主控台
seo-description: AEM提供多種機制，讓您自訂製作執行個體的主控台
uuid: f10cea87-ef8a-468e-94ca-89a1017dcf44
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 221ed05b-855d-4dc2-9df6-12fdeabb157a
exl-id: 31bced35-4845-40d1-9bfd-5c75d54e1a83
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 0%

---

# 自訂主控台{#customizing-the-consoles}

>[!CAUTION]
>
>本檔案說明如何在現代化、觸控式UI中自訂主控台，且不適用於傳統UI。

AEM提供多種機制，讓您可自訂製作例項的主控台（和[頁面製作功能](/help/sites-developing/customizing-page-authoring-touch.md)）。

* Clientlibs

   Clientlibs可讓您擴充預設實作以實現新功能，同時重複使用標準函式、物件和方法。 自訂時，您可以在`/apps.`下建立自己的clientlib，例如，它可以保留自訂元件所需的程式碼。

* 覆蓋

   覆蓋是根據節點定義，並可讓您以您自己的自訂功能（在`/apps`中）覆蓋標準功能（在`/libs`中）。 建立覆蓋時不需要原始資料的1:1副本，因為Sling資源合併允許繼承。

這些功能可用於擴充AEM主控台的許多方式。 下面（以高級別）列出了一小部分選項。

>[!NOTE]
>
>如需詳細資訊，請參閱：
>
>* 使用並建立[clientlibs](/help/sites-developing/clientlibs.md)。
>* 使用並建立[覆蓋](/help/sites-developing/overlays.md)。
>* [Granite](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html)

>
>
[AEM Gems](https://docs.adobe.com/content/ddc/en/gems.html)工作階段 — [針對AEM 6.0](https://docs.adobe.com/content/ddc/en/gems/user-interface-customization-for-aem-6.html)自訂使用者介面中也涵蓋此主題。

>[!CAUTION]
>
>您&#x200B;***必須***&#x200B;不要變更`/libs`路徑中的任何項目。
>
>這是因為下次升級執行個體時會覆寫`/libs`的內容（而當您套用Hotfix或Feature Pack時，很可能會覆寫）。
>
>設定和其他變更的建議方法為：
>
>1. 在`/apps`下重新建立所需項（即`/libs`中存在的項）
   >
   >
1. 在`/apps`內進行任何更改

>



例如，`/libs`結構內的下列位置可重疊：

* 主控台（任何以Granite UI頁面為基礎的主控台）;例如：

   * `/libs/wcm/core/content`

<!-- Needs a review by Engineering -->
<!--
* secondary (inner) rails; for example:

    * `/libs/wcm/core/content/search`

* toolbar(s) (dependent on console; for example sites):

    * default 

      `/libs/wcm/core/content/sites/jcr:content/body/content/header/items/default`

    * selection mode

      `/libs/wcm/core/content/sites/jcr:content/body/content/header/items/selection`

* help menu options (dependent on console; for example sites):

    * `/libs/wcm/core/content/sites/jcr:content/body/help`

* information shown on the card view (dependent on console; for example sites):

    * `/libs/wcm/core/content/sites/jcr:content/body/content/content/items/childpages`

-->
>[!NOTE]
>
>如需進一步提示和工具，請參閱知識庫文章[疑難排解AEM TouchUI問題](https://helpx.adobe.com/experience-manager/kb/troubleshooting-aem-touchui-issues.html)。

<!-- Needs a review by Engineering -->
<!--
## Code Samples {#code-samples}

Various packages have been made available on Github. These provide code samples related to the tasks covered on this page.

### aem-admin-extension-new-console {#aem-admin-extension-new-console}

`aem-admin-extension-new-console` is a sample package showing how to [create a new AEM 6 console](#create-a-custom-console). This package provides a UI for managing [Launches](/help/sites-authoring/launches.md) and adds a link in the navigation:

CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-admin-extension-new-console project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-new-console)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-new-console/archive/master.zip)

### aem-admin-extension-customize-sites {#aem-admin-extension-customize-sites}

`aem-admin-extension-customize-sites` is a sample package showing how to customize an existing AEM 6 admin console. This package provides updates to Sites administration:

CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-admin-extension-customize-sites project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-customize-sites)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-customize-sites/archive/master.zip)
-->

<!-- Needs a review by Engineering -->
<!--
## Create a Custom Console {#create-a-custom-console}

1. You can create a custom console with related actions; for example, Launches at the top level (below Sites):

   This involves:

    * creating the root space definition of your new console ``; for example:

        * `/apps/<yourProject>/admin/ext/launches`

    * this can contain (according to requirements):

        * the corresponding [clientlibs](/help/sites-developing/clientlibs.md) for custom actions and `less`/ `css` definitions

            * `/apps/<yourProject>/admin/ext/launches/clientlibs`

        * components that need to be redefined/adjusted; for example, the breadcrumbs, datasource and the launch

            * `/apps/<yourProject>/admin/ext/launches/components`

        * the Granite UI page resource:

            * `/apps/<yourProject>/admin/ext/launches/content/jcr:content`

              property: `sling:resourceType`

        * the page definition of the console

            * `/apps/<yourProject>/admin/ext/launches/content/jcr:content/head`
            * `/apps/<yourProject>/admin/ext/launches/content/jcr:content/body`

   ![chlimage_1-236](assets/chlimage_1-236.png)

   To use the new console (for example in the [rail for navigation](#add-new-navigation-option-to-rail)) an ID is used, so that it can be explicitly referenced. The ID is used to connect the console and its navigation definition. The ID is defined in the `rail` node of the page; for example, for the Sites console:

    * the rail node is: 

      `/libs/wcm/core/content/sites/jcr:content/body/rail`

        * here the `currentId` property is defined: 

          `currentId` = `cq-sites`

   For the Launches console example:

    * the node is:

        * `/apps/<yourProject>/admin/ext/launches/content/jcr:content/body/rail`

    * with the following properties:

        * `currentId` = `cq-launches`
        * `sling:resourceType` = `granite/ui/components/endor/navcolumns`
        * `srcPath` = `cq/core/content/nav`
-->

## 自定義控制台的預設視圖{#customizing-the-default-view-for-a-console}

您可以自訂主控台的預設檢視（欄、卡片、清單）:

1. 您可以從以下位置覆蓋所需條目，以重新排序視圖：

   `/libs/wcm/core/content/sites/jcr:content/views`

   第一個項目將是預設項目。

   可用的節點與可用的視圖選項相關聯：

   * `column`
   * `card`
   * `list`

1. 例如，在清單的覆蓋中：

   `/apps/wcm/core/content/sites/jcr:content/views/list`

   定義下列屬性：

   * **名稱**:  `sling:orderBefore`
   * **類型**:  `String`
   * **值**:  `column`

<!-- Needs a review by Engineering -->
<!--
`aem-admin-extension-customize-sites` is a sample package showing how to customize an existing AEM 6 admin console. This package provides updates to Sites administration:

CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-admin-extension-customize-sites project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-customize-sites)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-customize-sites/archive/master.zip)
-->

<!-- Needs a review by Engineering -->
<!--
### Add New Navigation Option to Rail {#add-new-navigation-option-to-rail}

1. You can add a navigation entry in the rail (for example, a [custom console](#create-a-custom-console) such as Launches).

   To do this, you create an overlay of:

   `/libs/cq/core/content/nav`

   In the `/apps` overlay:

   `/apps/cq/core/content/nav`

   Create the new nodes and properties:

   ![chlimage_1-237](assets/chlimage_1-237.png)

    * Extend navigation:

        * `/apps/cq/core/content/nav/launches`

    * Specify location in the tree:

        * property: `sling:orderBefore`

    * To create the connection, the `id` property references (i.e. must be the same as) the `currentID` property [for the appropriate console](#create-a-custom-console):

        * property: `id`
        * value: same as for your console (e.g. `cq-launches`) 

          for example: the same value as the `currentId` property on:

          `/apps/<yourProject>/admin/ext/launches/content/jcr:content/body/rail`
-->

## 將新操作添加到工具欄{#add-new-action-to-the-toolbar}

1. 您可以建立自己的元件，並包含自訂動作的對應用戶端程式庫。 例如，**提升至Twitter**&#x200B;動作位於：

   `/apps/wcm/core/clientlibs/sites/js/twitter.js`

   接著，即可將此連結至主控台上的工具列項目：

   `/apps/<yourProject>/admin/ext/launches`

   例如，在選擇模式中：

   `content/jcr:content/body/content/header/items/selection/items/twitter`

## 將工具欄操作限制為特定組{#restrict-a-toolbar-action-to-a-specific-group}

1. 您可以使用自訂轉譯條件來覆蓋標準動作，並強加在轉譯前必須履行的特定條件。

   例如，建立元件以根據群組控制呈現條件：

   `/apps/myapp/components/renderconditions/group`

1. 若要將這些套用至Sites主控台上的「建立網站」動作：

   `/libs/wcm/core/content/sites`

   建立覆蓋：

   `/apps/wcm/core/content/sites`

1. 然後新增動作的呈現條件：

   `jcr:content/body/content/header/items/default/items/create/items/createsite/rendercondition`

   使用此節點上的屬性，可以定義允許執行特定操作的`groups`;例如`administrators`

<!-- Needs a review by Engineering -->
<!--
## Remove Access to Navigation Option on Rail {#remove-access-to-navigation-option-on-rail}

1. You can rename a navigation entry in the rail by overlaying the required entry from under:

   `/libs/cq/core/content/nav`

   The nodes available correlate to the navigation options in the rail:

    * `projects`
    * `sites`
    * `assets`
    * `apps`
    * `forms`
    * `screens`
    * `personalization`
    * `commerce`
    * `tools`
    * `communities`

1. For example, on a overlay at:

   `/apps/cq/core/content/nav/sites`

   Define the following property:

    * **Name**: `sling:hideResource`
    * **Type**: `String` 
    * **Value**: `true`

`aem-admin-extension-customize-sites` is a sample package showing how to customize an existing AEM 6 admin console. This package provides updates to Sites administration:

CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-admin-extension-new-console project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-new-console)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-new-console/archive/master.zip)
-->

<!-- Needs a review by Engineering -->
<!--
## Restrict Access to Navigation Option on Rail {#restrict-access-to-navigation-option-on-rail}

You can restrict access to a navigation option using ACLs:

1. Open the [user and/or group management](/help/sites-administering/security.md) and select the user/group you want to restrict access for.

   >[!NOTE]
   >
   >Avoid assigning/restricting permissions on a user-by-user basis. It is [recommended to use groups](/help/sites-administering/security.md#best-practices).

1. Remove access [permissions](/help/sites-administering/security.md#permissions) to the appropriate node(s) under `/libs/cq/core/content/nav/sites`. These correlate to the navigation options in the rail:

    * `projects`
    * `sites`
    * `assets`
    * `apps`
    * `forms`
    * `screens`
    * `personalization`
    * `commerce`
    * `tools`
    * `communities`
-->

## 自定義清單視圖{#customizing-columns-in-the-list-view}中的列

>[!NOTE]
>
>此功能已針對文字欄位欄位最佳化；對於其他資料類型，可以覆蓋`/apps`中的`cq/gui/components/siteadmin/admin/listview/columns/analyticscolumnrenderer`。

<!-- Needs a review by Engineering -->
<!--
CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-sites-extension-listview-columns project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sites-extension-listview-columns)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-sites-extension-listview-columns/archive/master.zip)
-->

要自定義清單視圖中的列：

1. 覆蓋可用欄的清單。

   * 在節點上：

      `/apps/wcm/core/content/common/availablecolumns`

   * 新增欄或移除現有欄。
   如需詳細資訊，請參閱[使用覆蓋（和Sling Resource Merger）](/help/sites-developing/overlays.md) 。

1. （可選）:

   * 如果要插入其他資料，需要使用` [PageInforProvider](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageInfoProvider.html)`

      `pageInfoProviderType` 屬性.
   例如，請參閱下方附加的類別/套件組合（來自GitHub）。

1. 您現在可以在清單檢視的欄設定器中選取欄。

## 篩選資源{#filtering-resources}

使用主控台時，常見的使用案例是使用者必須從資源（例如頁面、元件、資產等）中選取。 這可以採用清單的形式，例如，作者必須從中選擇項目。

為了使清單保持在合理的大小以及與使用案例相關的大小，可以以自訂述詞的形式實施篩選器。 如需詳細資訊，請參閱[本文](/help/sites-developing/customizing-page-authoring-touch.md#filtering-resources)。

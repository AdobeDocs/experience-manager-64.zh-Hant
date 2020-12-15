---
title: 使用3D Sites元件
seo-title: 使用3D Sites元件
description: AEM 3D包含AEM Sites元件，可用來實作網頁上3D模型的互動式檢視。
seo-description: AEM 3D包含AEM Sites元件，可用來實作網頁上3D模型的互動式檢視。
uuid: 4f06bab3-1e31-49ef-89e3-b26195966538
contentOwner: Rick Brough
topic-tags: 3D
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: 9017ab55-6d4a-4306-922f-223ab1b2504b
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '1041'
ht-degree: 0%

---


# 使用3D Sites元件{#working-with-the-d-sites-component}

AEM 3D包含AEM Sites元件，您可用來實作網頁上3D模型的互動式檢視。

新增3D元件後，您可以[檢視該元件中的3D資產。](viewing-3d-assets.md)

## 將3D元件添加到頁面模板{#adding-the-d-component-to-the-page-template}

您必須先在頁面中啟用3D元件，才能將它放在頁面上。 如需在範本中啟用元件的詳細資訊，請參閱[編輯範本](/help/sites-authoring/templates.md#editing-a-template-layout-template-author)。

**將3D元件新增至頁面範本**:

1. 導覽至&#x200B;**[!UICONTROL 工具>一般>範本]**。

1. 導覽至您要在中啟用3D元件的頁面範本，然後選取範本。

1. 點選&#x200B;**[!UICONTROL 編輯]**&#x200B;以開啟範本。
1. 在頁面右上角的下拉式功能表中，選取&#x200B;**[!UICONTROL 結構]**&#x200B;模式（如果尚未啟用）。

   ![image2017-11-14_15-33-57](assets/image2017-11-14_15-33-57.png)

1. 點選&#x200B;**[!UICONTROL 版面容器]**&#x200B;區域以選取它。

1. 點選&#x200B;**[!UICONTROL Policy]**&#x200B;按鈕以開啟&#x200B;**[!UICONTROL Policy Editor]**。
1. 在&#x200B;**[!UICONTROL 屬性]**&#x200B;區段中，選擇&#x200B;**[!UICONTROL 3D]**&#x200B;複選標籤，然後點選&#x200B;**[!UICONTROL 完成]**&#x200B;以儲存變更並關閉&#x200B;**[!UICONTROL 原則編輯器]**。

   您現在可以將3D Sites元件置於使用此範本的所有頁面上。

## 將3D檢視器元件新增至網頁{#adding-the-d-viewer-component-to-a-web-page}

>[!CAUTION]
>
>此AEM 3D版本僅支援每個網頁上一個3D元件例項。 同一頁面上的多個3D元件無法正常運作。

**若要將3D檢視器元件新增至網頁**:

1. 開啟「AEM網站」，並選取您要新增3D元件的網頁。

1. 點選「**[!UICONTROL 編輯]**（鉛筆）」圖示，將頁面開啟至頁面編輯器。 請確定已選取頁面右上方附近的&#x200B;**[!UICONTROL 編輯]**&#x200B;模式。

   ![image2017-11-14_15-44-40](assets/image2017-11-14_15-44-40.png)

1. 點選滑軌選擇器以開啟側面板。

1. 點選加號圖示以開啟&#x200B;**[!UICONTROL 元件]**&#x200B;清單。

1. 將&#x200B;**[!UICONTROL 3D檢視器]**&#x200B;元件從&#x200B;**[!UICONTROL 元件]**&#x200B;清單拖曳至您要3D檢視器出現的頁面位置。

## 配置3D元件{#configuring-the-d-component}

1. 在「AEM Sites」頁面編輯器中，選取您先前新增至頁面的&#x200B;**[!UICONTROL 3D檢視器]**&#x200B;元件。

1. 點選&#x200B;**[!UICONTROL Configuration]**&#x200B;圖示（扳手）以開啟元件設定對話方塊。

   可以設定以下元件屬性：

   <table> 
    <tbody> 
    <tr> 
    <td>屬性</td> 
    <td>說明</td> 
    <td>適用性</td> 
    </tr> 
    <tr> 
    <td>高度 (px)</td> 
    <td>以像素為單位指定所需的3D元件高度。 如果保留空白，預設值為600像素。</td> 
    <td> </td> 
    </tr> 
    <tr> 
    <td>階段名稱</td> 
    <td><p>從可用階段清單中選擇3D階段。 舞台提供背景和照明。</p> <p>請參閱<a href="/help/assets/about-the-use-of-stages-in-aem-3d.md" target="_blank">關於AEM 3D Sites</a>中階段的使用。</p> </td> 
    <td>已忽略Adobe Dimension資產。</td> 
    </tr> 
    <tr> 
    <td>自動回轉速度(RPM)</td> 
    <td><p>3D檢視器在載入並重設後，會持續環繞相機。 當用戶啟動手動軌道操作時，自動自旋終止。</p> <p>您可以使用下列值，以RPM指定回轉速度：</p> 
        <ul> 
        <li>將正值設為向右旋轉</li> 
        <li>將負值設為左旋轉</li> 
        <li>設定0值以停用自動回轉。</li> 
        </ul> <p>預設值為3 RPM，相當於每次完整旋轉20秒。<br /> <br /> <strong>注意：</strong> 回轉速度假設為60/秒影格速率。通常，在功能更強大的圖形硬體上，小型到中型機型可達到此速度。 較大機型或較慢的裝置會以較低的速率自動旋轉。</p> </td> 
    <td>已忽略Adobe Dimension資產。</td> 
    </tr> 
    <tr> 
    <td>導覽按鈕顏色</td> 
    <td>使用檢色器為檢視器的控制按鈕選擇主要顏色。</td> 
    <td>Adobe Dimension資產已忽略。</td> 
    </tr> 
    <tr> 
    <td>導覽暫留色彩</td> 
    <td>使用檢色器為檢視器的控制按鈕選擇暫留／選取的顏色。</td> 
    <td>已忽略Adobe Dimension資產。</td> 
    </tr> 
    <tr> 
    <td>顯示色票</td> 
    <td>供日後使用。</td> 
    <td>已忽略Adobe Dimension資產。</td> 
    </tr> 
    <tr> 
    <td>顯示GLTF相機預設集</td> 
    <td>顯示或隱藏Adobe Dimension資產中可能存在的相機預設集。</td> 
    <td>僅限Adobe Dimension資產。</td> 
    </tr> 
    <tr> 
    <td>GLTF背景顏色</td> 
    <td>如果3D模型不包含背景，則預設背景顏色。</td> 
    <td>僅限Adobe Dimension資產。</td> 
    </tr> 
    </tbody> 
   </table>

1. 點選核取標籤以儲存變更。

   除了元件配置對話框中的可用設定外，還提供了一些全局配置設定，這些設定可通過CRXDE Lite進行修改。
如需這些全域設定的詳細資訊，請參閱[進階組態設定](advanced-config-3d.md)。

## 為元件{#assigning-a-d-model-to-the-component}指定3D模型

1. 在「AEM Sites」頁面編輯器中，按一下「**[!UICONTROL 資產]**」圖示，以開啟側面板中的「資產」清單。

1. 選擇&#x200B;**[!UICONTROL 3D Models]**&#x200B;篩選器可隱藏不想要的資產類型。

   ![screen_shot_2017-12-11at124258](assets/screen_shot_2017-12-11at124258.png)

1. 搜尋或捲動至您要在編輯之頁面上檢視的3D資產。

1. 將3D資產從&#x200B;**[!UICONTROL Assets]**&#x200B;清單拖曳至先前放在頁面上的&#x200B;**[!UICONTROL 3D檢視器]**&#x200B;元件。

   Adobe Dimension資產是使用以glTF Open Standard為基礎的新檢視器技術來轉譯，而所有其他3D資產類型則仰賴傳統的AEM 3D webGL檢視器。 元件會根據3D模型類型自動選取適當的檢視器。

## 預覽具有3D元件{#previewing-a-web-page-that-has-a-d-component}的網頁

當網頁處於&#x200B;**[!UICONTROL 編輯]**&#x200B;模式時，3D元件顯示3D模型，但無法與模型交互。

您可以在頁面編輯器中預覽網頁，並完整存取3D元件的功能。

另請參閱[在Sites 3D元件](viewing-3d-assets.md#viewing-d-assets-in-the-sites-d-component)中查看3D資產。

**若要預覽包含3D元件的網頁**:

1. 執行下列任一項作業：

   * 在頁面右上方附近，按一下「預覽&#x200B;****」以進入預覽模式。
   * 從瀏覽器的頁面URL刪除`/edit.html`。

## 發佈頁面和資產{#publishing-the-page-and-assets}

如需如何發佈資產的詳細資訊，請參閱[發佈資產](managing-assets-touch-ui.md)。 如需如何發佈頁面的詳細資訊，請參閱[發佈頁面](/help/sites-authoring/publishing-pages.md)。

>[!NOTE]
>
>使用&#x200B;**[!UICONTROL 頁面資訊]**&#x200B;功能表上的&#x200B;**[!UICONTROL 發佈頁面]**&#x200B;功能表項目，將發佈頁面和所有主要頁面相依性。 以此方式發佈頁面時，不會發佈3D模型和／或3D階段可能參照的次要相依性，例如紋理映射和IBL影像。
>
>Adobe建議您直接從AEM Assets發佈所有3D資產及其相依性，然後再發佈參照這些資產的網頁。


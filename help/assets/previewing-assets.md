---
title: 預覽 Dynamic Media 資產
seo-title: 預覽 Dynamic Media 資產
description: 瞭解如何在動態媒體中預覽資產
seo-description: 瞭解如何在動態媒體中預覽資產
uuid: f0ff2fc4-a263-4dbe-ba46-b07077b49ae0
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 77296bff-8429-4240-af93-26076ae431ec
translation-type: tm+mt
source-git-commit: 8c6fdcea0def7720062edfc564c536f8d47e8402
workflow-type: tm+mt
source-wordcount: '1028'
ht-degree: 5%

---


# 預覽 Dynamic Media 資產 {#previewing-assets}

您可以使 **[!UICONTROL 用「預覽]** 」，查看客戶在其網頁瀏覽器中檢視動態媒體數位資產時的外觀。 指派給資產的預設內嵌、跨裝置檢視器會用於「預 **[!UICONTROL 覽」]**。

檢視器是各種設定或「預設集」的集合，例如檢視器顯示大小、縮放行為、色彩配置、邊框、字型等，可決定使用者在電腦螢幕和行動裝置上檢視多媒體資產的方式。

除了使用視訊、回轉集和影像集的專用預覽功能外，您也可以使用您建立的檢視器預設集來預覽資產。 或者，使用影像預設集來預覽影像的轉譯。

* [套用影像預設集](image-presets.md)
* [套用檢視器預設集](viewer-presets.md)

>[!NOTE]
>
>當您在AEM的網頁 (網站) 上時，無法在「編輯」模式中預 **[!UICONTROL 覽資產]** 。您必須按一下右 **[!UICONTROL 上角的]** 「預覽 **** 」，以前往「預覽」模式。

**若要預覽資產**:

1. From **Adobe Experience Manager**, on the **[!UICONTROL Navigation]** page, tap **[!UICONTROL Asset]s **, then**[!UICONTROL Files ]**to access assets.
1. 在頁面的右上角附近，從「檢視」下拉式清單 **[!UICONTROL 中]** ，點選「清 **[!UICONTROL 單檢視」]**。
1. （可選）使用 **[!UICONTROL Type]** 欄，依您要預覽的類型排序資產。
1. 在「標 **[!UICONTROL 題]** 」欄下方，按一下您要預覽之資產的標題名稱（而非縮圖影像）。
1. 視您所點按的資產類型而定，執行下列任一項作業：

<table> 
 <tbody>
  <tr>
   <td><strong>您點選的資產類型</strong><br /> </td> 
   <td><strong>能夠在特定轉譯中預覽資產嗎？</strong></td> 
   <td><strong>能夠在特定檢視器中預覽資產？</strong></td> 
  </tr>
  <tr>
   <td><p>影像</p> </td> 
   <td>是</td> 
   <td>是</td> 
   <td><p><strong>在特定轉譯中預覽資產</strong></p> 
    <ul> 
     <li>在頁面的左上角附近，按一下圖示以顯示下拉式清單。 按一 <strong>下清 </strong>單中的「轉譯」，然後選取您要預覽的特定轉譯。</li> 
    </ul> <p><strong>若要在特定檢視器中預覽資產</strong></p> 
    <ul> 
     <li>在頁面的左上角附近，按一下圖示以顯示下拉式清單。 按一 <strong>下清單中的</strong> 「檢視器」，然後選取您要套用至資產的檢視器。</li> 
    </ul> <p>使用 <strong>+</strong> 和 <strong>-圖 </strong>示分別增加或減少所選影像的縮放。 按一 <strong>下「重設</strong> 」，將影像還原為原始縮放。<br /> 如果您使用行動裝置，請點選兩下影像，依步驟放大。 達到最大縮放時，再點兩下影像以重設縮放狀態。 拖曳影像以進行平移。</p> <p>若要在使用者介面中啟用或停用檢視器預設集，請參閱「管 <a href="/help/assets/managing-viewer-presets.md">理檢視器預設集」</a>。<br /> </p> </td> 
  </tr>
  <tr>
   <td>多媒體</td> 
   <td>是</td> 
   <td>是</td> 
   <td><p><strong>在特定轉譯中預覽資產</strong></p> 
    <ul> 
     <li>在頁面的左上角附近，按一下圖示以顯示下拉式清單。 按一 <strong>下清 </strong>單中的「轉譯」，然後選取您要預覽的特定轉譯。</li> 
    </ul> <p>選取較高解析度的視訊轉譯以進行預覽，可能會導致視訊出現截斷。 這是因為轉譯預覽會在用於預覽的內嵌檢視器中，顯示客戶將看到的精確解析度。</p> <p>當您在「資產」層級預覽最適化視訊集時，轉譯會分組為一個播放體驗。 也就是說，最適化視訊的大小會適當調整，以便在檢視裝置和連線速度時，使用最佳解析度來檢視和播放。<br /> </p> <p><strong>若要在特定檢視器中預覽資產</strong></p> 
    <ul> 
     <li>在頁面的左上角附近，按一下圖示以顯示下拉式清單。 按一 <strong>下清單中的</strong> 「檢視器」，然後選取您要套用至資產的檢視器。</li> 
    </ul> <p>若要在使用者介面中啟用或停用檢視器預設集，請參閱「管 <a href="/help/assets/managing-viewer-presets.md">理檢視器預設集」</a>。</p> </td> 
  </tr>
  <tr>
   <td>影像集</td> 
   <td>否</td> 
   <td>是</td> 
   <td><p><strong>若要在特定檢視器中預覽資產</strong></p> 
    <ul> 
     <li>在頁面的左上角附近，按一下圖示以顯示下拉式清單。 按一 <strong>下清單中的</strong> 「檢視器」，然後選取您要套用至資產的檢視器。</li> 
    </ul> <p>使用 <strong>+</strong> 和 <strong>-圖 </strong>示分別增加或減少所選影像的縮放。 按一 <strong>下「重設</strong> 」，將影像還原為原始縮放。<br /> 如果您使用行動裝置，請點選兩下影像，依步驟放大。 達到最大縮放時，再點兩下影像以重設縮放狀態。 拖曳影像以進行平移。</p> <p>若要在使用者介面中啟用或停用檢視器預設集，請參閱「管 <a href="/help/assets/managing-viewer-presets.md">理檢視器預設集」</a>。</p> </td> 
  </tr>
  <tr>
   <td>回轉集</td> 
   <td>否</td> 
   <td>是</td> 
   <td><p><strong>若要在特定檢視器中預覽資產</strong></p> 
    <ul> 
     <li>在頁面的左上角附近，按一下圖示以顯示下拉式清單。 按一 <strong>下清單中的</strong> 「檢視器」，然後選取您要套用至資產的檢視器。</li> 
    </ul> <p>使用 <strong>+</strong> 和 <strong>-圖 </strong>示分別增加或減少所選影像的縮放。 按一 <strong>下「重設</strong> 」，將影像還原為原始縮放。<br /> 如果您使用行動裝置，請點選兩下影像，依步驟放大。 達到最大縮放時，再點兩下影像以重設縮放狀態。 拖曳影像以進行平移。</p> <p>若要在使用者介面中啟用或停用檢視器預設集，請參閱「管 <a href="/help/assets/managing-viewer-presets.md">理檢視器預設集」</a>。</p> </td> 
  </tr>
  <tr>
   <td>混合媒體集</td> 
   <td>否</td> 
   <td>是</td> 
   <td><p><strong>若要在特定檢視器中預覽資產</strong></p> 
    <ul> 
     <li>在頁面的左上角附近，按一下圖示以顯示下拉式清單。 按一 <strong>下清單中的</strong> 「檢視器」，然後選取您要套用至資產的檢視器。</li> 
    </ul> <p>使用 <strong>+</strong> 和 <strong>-圖 </strong>示分別增加或減少所選影像的縮放。 按一 <strong>下「重設</strong> 」，將影像還原為原始縮放。<br /> 如果您使用行動裝置，請點選兩下影像，依步驟放大。 達到最大縮放時，再點兩下影像以重設縮放狀態。 拖曳影像以進行平移。</p> <p>若要在使用者介面中啟用或停用檢視器預設集，請參閱「管 <a href="/help/assets/managing-viewer-presets.md">理檢視器預設集」</a>。</p> </td> 
  </tr>
  <tr>
   <td>轉盤集</td> 
   <td>否</td> 
   <td>是</td> 
   <td><p><strong>若要在特定檢視器中預覽資產</strong></p> 
    <ul> 
     <li>在頁面的左上角附近，按一下圖示以顯示下拉式清單。 選取您要套用至資產的檢視器。</li> 
    </ul> <p>若要在使用者介面中啟用或停用檢視器預設集，請參閱「管 <a href="/help/assets/managing-viewer-presets.md">理檢視器預設集」</a>。</p> </td> 
  </tr>
 </tbody>
</table>


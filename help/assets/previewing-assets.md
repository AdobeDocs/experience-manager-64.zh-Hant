---
title: 預覽 Dynamic Media 資產
seo-title: Previewing Dynamic Media assets
description: 了解如何在Dynamic Media中預覽資產
seo-description: Learn how to preview assets in Dynamic Media
uuid: f0ff2fc4-a263-4dbe-ba46-b07077b49ae0
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 77296bff-8429-4240-af93-26076ae431ec
exl-id: ec05569a-6449-4430-9b9f-7ab051f44970
feature: Asset Management,Renditions
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 5%

---

# 預覽 Dynamic Media 資產 {#previewing-assets}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

您可以使用 **[!UICONTROL 預覽]** 查看Dynamic Media數位資產在客戶透過其自己的網頁瀏覽器檢視時的外觀。 指派給資產的預設內嵌、跨裝置檢視器會用於 **[!UICONTROL 預覽]**.

檢視器是各種設定或「預設集」的集合，例如檢視器的顯示大小、縮放行為、色彩配置、邊框、字型等，可決定使用者在其電腦螢幕和行動裝置上檢視多媒體資產的方式。

除了使用視訊、回轉集和影像集的專用預覽功能外，您也可以使用您建立的檢視器預設集來預覽資產。 或者，使用影像預設集來預覽影像的轉譯。

* [套用影像預設集](image-presets.md)
* [套用檢視器預設集](viewer-presets.md)

>[!NOTE]
>
>當您在AEM的網頁 (網站) 上時，無法在「編輯」模式中預 **[!UICONTROL 覽資產]** 。您必須按一下右 **[!UICONTROL 上角的]** 「預覽 **** 」，以前往「預覽」模式。

**若要預覽資產**:

1. 從 **Adobe Experience Manager**，在 **[!UICONTROL 導覽]** 頁面，點選 **[!UICONTROL 資產]s**，然後 **[!UICONTROL 檔案]** 存取資產。
1. 在頁面的右上角附近，從 **[!UICONTROL 檢視]** 下拉式清單，點選 **[!UICONTROL 清單檢視]**.
1. （選用）使用 **[!UICONTROL 類型]** 欄，依您要預覽的類型來排序資產。
1. 在 **[!UICONTROL 標題]** 欄，按一下您要預覽之資產的標題名稱（而非縮圖影像）。
1. 視您所點按的資產類型而定，執行下列任一項作業：

<table> 
 <tbody>
  <tr>
   <td><strong>您點選的資產類型</strong><br /> </td> 
   <td><strong>能否在特定轉譯中預覽資產？</strong></td> 
   <td><strong>能否在特定檢視器中預覽資產？</strong></td> 
  </tr>
  <tr>
   <td><p>影像</p> </td> 
   <td>是</td> 
   <td>是</td> 
   <td><p><strong>在特定轉譯中預覽資產</strong></p> 
    <ul> 
     <li>在頁面的左上角附近，按一下圖示以顯示下拉式清單。 按一下 <strong>轉譯 </strong>從清單中，選擇要預覽的特定轉譯。</li> 
    </ul> <p><strong>在特定檢視器中預覽資產</strong></p> 
    <ul> 
     <li>在頁面的左上角附近，按一下圖示以顯示下拉式清單。 按一下 <strong>檢視器</strong> 從清單中，選取您要套用至資產的檢視器。</li> 
    </ul> <p>使用 <strong>+</strong> 和 <strong>- </strong>表徵圖，以分別增加或減少所選影像的縮放。 按一下 <strong>重設</strong> 將影像返回到原始縮放。<br /> 如果您在行動裝置上，請點選兩下影像以依步驟放大。 達到最大縮放時，請再次點選兩下影像以重設縮放狀態。 拖過影像以平移。</p> <p>若要在使用者介面中啟用或停用檢視器預設集，請參閱 <a href="/help/assets/managing-viewer-presets.md">管理檢視器預設集</a>.<br /> </p> </td> 
  </tr>
  <tr>
   <td>多媒體</td> 
   <td>是</td> 
   <td>是</td> 
   <td><p><strong>在特定轉譯中預覽資產</strong></p> 
    <ul> 
     <li>在頁面的左上角附近，按一下圖示以顯示下拉式清單。 按一下 <strong>轉譯 </strong>從清單中，選擇要預覽的特定轉譯。</li> 
    </ul> <p>選取要預覽的高解析度視訊轉譯可能會導致視訊顯示為截斷。 這是因為轉譯預覽會在用於預覽的內嵌檢視器內容中，顯示客戶將看到的確切解析度。</p> <p>在資產層級預覽最適化視訊集時，轉譯會分組為一個播放體驗。 也就是說，最適化視訊的大小已適當調整，以便在檢視裝置和連線速度的情境下，使用最佳解析度來檢視及播放。<br /> </p> <p><strong>在特定檢視器中預覽資產</strong></p> 
    <ul> 
     <li>在頁面的左上角附近，按一下圖示以顯示下拉式清單。 按一下 <strong>檢視器</strong> 從清單中，選取您要套用至資產的檢視器。</li> 
    </ul> <p>若要在使用者介面中啟用或停用檢視器預設集，請參閱 <a href="/help/assets/managing-viewer-presets.md">管理檢視器預設集</a>.</p> </td> 
  </tr>
  <tr>
   <td>影像集</td> 
   <td>否</td> 
   <td>是</td> 
   <td><p><strong>在特定檢視器中預覽資產</strong></p> 
    <ul> 
     <li>在頁面的左上角附近，按一下圖示以顯示下拉式清單。 按一下 <strong>檢視器</strong> 從清單中，選取您要套用至資產的檢視器。</li> 
    </ul> <p>使用 <strong>+</strong> 和 <strong>- </strong>表徵圖，以分別增加或減少所選影像的縮放。 按一下 <strong>重設</strong> 將影像返回到原始縮放。<br /> 如果您在行動裝置上，請點選兩下影像以依步驟放大。 達到最大縮放時，請再次點選兩下影像以重設縮放狀態。 拖過影像以平移。</p> <p>若要在使用者介面中啟用或停用檢視器預設集，請參閱 <a href="/help/assets/managing-viewer-presets.md">管理檢視器預設集</a>.</p> </td> 
  </tr>
  <tr>
   <td>回轉集</td> 
   <td>否</td> 
   <td>是</td> 
   <td><p><strong>在特定檢視器中預覽資產</strong></p> 
    <ul> 
     <li>在頁面的左上角附近，按一下圖示以顯示下拉式清單。 按一下 <strong>檢視器</strong> 從清單中，選取您要套用至資產的檢視器。</li> 
    </ul> <p>使用 <strong>+</strong> 和 <strong>- </strong>表徵圖，以分別增加或減少所選影像的縮放。 按一下 <strong>重設</strong> 將影像返回到原始縮放。<br /> 如果您在行動裝置上，請點選兩下影像以依步驟放大。 達到最大縮放時，請再次點選兩下影像以重設縮放狀態。 拖過影像以平移。</p> <p>若要在使用者介面中啟用或停用檢視器預設集，請參閱 <a href="/help/assets/managing-viewer-presets.md">管理檢視器預設集</a>.</p> </td> 
  </tr>
  <tr>
   <td>混合媒體集</td> 
   <td>否</td> 
   <td>是</td> 
   <td><p><strong>在特定檢視器中預覽資產</strong></p> 
    <ul> 
     <li>在頁面的左上角附近，按一下圖示以顯示下拉式清單。 按一下 <strong>檢視器</strong> 從清單中，選取您要套用至資產的檢視器。</li> 
    </ul> <p>使用 <strong>+</strong> 和 <strong>- </strong>表徵圖，以分別增加或減少所選影像的縮放。 按一下 <strong>重設</strong> 將影像返回到原始縮放。<br /> 如果您在行動裝置上，請點選兩下影像以依步驟放大。 達到最大縮放時，請再次點選兩下影像以重設縮放狀態。 拖過影像以平移。</p> <p>若要在使用者介面中啟用或停用檢視器預設集，請參閱 <a href="/help/assets/managing-viewer-presets.md">管理檢視器預設集</a>.</p> </td> 
  </tr>
  <tr>
   <td>輪播集</td> 
   <td>否</td> 
   <td>是</td> 
   <td><p><strong>在特定檢視器中預覽資產</strong></p> 
    <ul> 
     <li>在頁面的左上角附近，按一下圖示以顯示下拉式清單。 選取您要套用至資產的檢視器。</li> 
    </ul> <p>若要在使用者介面中啟用或停用檢視器預設集，請參閱 <a href="/help/assets/managing-viewer-presets.md">管理檢視器預設集</a>.</p> </td> 
  </tr>
 </tbody>
</table>

---
title: 使用AEM 3D資產
seo-title: 使用3D資產
description: 瞭解如何在AEM 3D中使用3D資產
seo-description: 瞭解如何在AEM 3D中使用3D資產
uuid: a1c1bb29-9d3d-4025-8142-ed9719434bf9
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: introduction
content-type: reference
discoiquuid: 32143da1-09c8-45ce-b50d-32adf6efe383
translation-type: tm+mt
source-git-commit: 11b65cf2d180f04168d4c5d0929957c95a372e3c
workflow-type: tm+mt
source-wordcount: '1192'
ht-degree: 0%

---


# 使用AEM 3D資產 {#working-with-d-assets}

>[!IMPORTANT]
>
>不再支援AEM 6.4中的AEM 3D。 Adobe建議您將 [AEM中的3D資產功能當做雲端服務](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html)[或AEM 6.5.3或更新版本使用。](https://docs.adobe.com/content/help/en/experience-manager-65/assets/dynamic/assets-3d.html)

AEM 3D(Adobe Experience Manager 3D)可讓您上傳、管理、檢視和演算3D內容。 已針對個別物件最佳化檢視和轉換支援。

另請參閱 [AEM 3D發行說明](/help/release-notes/aem3d-release-notes.md)。

另請參 [閱安裝和設定AEM 3D](install-config-3d.md)。

## 關於AEM 3D中的模型和階段 {#about-models-and-stages-in-aem-d}

AEM 3D可讓您在預先定義的「階段」環境中檢視和演算高品質的靜態、獨立3D模型。 基本上，舞台可為3D場景提供「光源」，並可在原生應用程式（例如Autodesk® Maya®或Autodesk 3ds Max®）中演算。 此外，舞台可以任選地包括預定義的相機、背景和地面幾何。

上傳的包含光源的3D檔案會假設為舞台。 您可以在資產詳細資料頁面中開啟資產，將這些資產回復為簡單的3D物件。 點選「 **[!UICONTROL View Properties]**(檢視屬性 **[!UICONTROL )」，然後點選「]** Basic（基本）」標籤。 在「中繼資料」標題下方的「資產類別」下拉式清單中，選取 **[!UICONTROL 3D物件]**。

當您建立3D模型以用於AEM 3D時，請注意下列事項：

* 您的3D模型檔案只應包含一個物件，不含背景、地面、場景光源或相機。
* 將模型置於接地平面上方。 當您使用提供地面平面的舞台檢視或演算時，此定位特別重要。 配置設定可用（預設為啟用），當使用快速調整預覽或渲染時，該配置設定會使對象移動到地面平面上方。 此設定不會影響使用協力廠商轉譯器（例如，透過Maya）進行轉譯，因此，不位於地面平面上方的物件可能會部分隱藏。
* 定位模型，使其能夠以坐標系原點(0,0,0)的橫向合理居中。 如此可確保您獲得良好的互動式檢視體驗。
* 除了紋理映射外，還支援外部檔案參照。 因此，您必須先將任何參考內容內嵌在主要模型檔案中，才能將其上傳至AEM。

   請參 [閱關於在AEM中上傳和處理3D資產](upload-processing-3d-assets.md)。

* 一般場景照明由舞台提供。 因此，Adobe不建議您將光源加入3D模型檔案。 可在模型中包含光源。 但是，它們必須僅特定於模型。 例如，可能需要加入額外的光源，以使被其他部分遮住的部分物件變亮。 因此，光是舞台燈就看不到。

## AEM 3D中支援的檔案 {#supported-files-in-aem-d}

典型的3D資產具有主模型檔案，且無或多個參照檔案。 參考的檔案包括紋理地圖或 **IBL（影像光源）影像** 。

### 關於主3D模型檔案 {#about-the-primary-d-model-file}

主3D模型檔案包含實際的3D模型幾何和應用於模型曲面的（預設）材料的定義。 AEM 3D支援下列主要3D模型檔案格式：

* Wavefront OBJ檔案格式(`.obj`)

   OBJ格式需要一個或多個單獨的外部MTL檔案（材料模板庫）(`.mtl`)。

* Autodesk FBX(Filmbox)檔案格式(`.fbx`)

   Autodesk 3D檔案交換格式；二進位和ASCII格式。

   當您在協力廠商應用程式中建立FBX檔案時，Adobe建議使用下列組態設定（請參閱下表）。 這些設定可協助您針對想要在AEM中使用的3D檔案取得最佳效果。 選項名稱取自「 **[!UICONTROL Autodesk Maya FBX導出選項」(Autodesk Maya FBX Export Options]** )對話框。

<table> 
 <tbody> 
  <tr> 
   <td><strong>「Autodesk Maya FBX導出」對話框中的選項</strong></td> 
   <td><strong>說明</strong></td> 
  </tr> 
  <tr> 
   <td>保留參照<br /> </td> 
   <td><p>取消選取.</p> <p>AEM 3D目前不支援外部參照。</p> </td> 
  </tr> 
  <tr> 
   <td>平滑網格<br /> </td> 
   <td>選取.</td> 
  </tr> 
  <tr> 
   <td>將NURBS曲面轉換為</td> 
   <td><strong>軟體渲染網格</strong></td> 
  </tr> 
  <tr> 
   <td>動畫</td> 
   <td><p>選擇或取消選擇。</p> <p>如果您選擇選取此選項，AEM 3D會忽略檔案中的動畫資訊。</p> </td> 
  </tr> 
  <tr> 
   <td>相機</td> 
   <td><p>選取 <strong>3D階段</strong>。</p> <p>取消選取3D模型。</p> </td> 
  </tr> 
  <tr> 
   <td>光源</td> 
   <td><p>選取 <strong>3D階段</strong>。</p> <p>取消選取 <strong>3D模型</strong>。</p> </td> 
  </tr> 
  <tr> 
   <td>設備——自動</td> 
   <td>選取. AEM 3D在匯入時轉換。</td> 
  </tr> 
  <tr> 
   <td>軸轉換——向上軸</td> 
   <td><p><strong>Y-up</strong></p> <p>從Maya匯出時，Y-up會提供一致的結果，而且是此AEM 3D版本中FBX檔案的偏好坐標系。</p> </td> 
  </tr> 
  <tr> 
   <td>內嵌媒體</td> 
   <td>兩個選項都受支援。 如果選取內嵌，AEM 3D會將內嵌媒體擷取至與模型檔案同名且附加在其上的相鄰 <code>.fbm</code> 資料夾。</td> 
  </tr> 
  <tr> 
   <td>FBX檔案格式——類型</td> 
   <td>支 <strong>援二 </strong>進位 <strong>或 </strong>ASCII格式。</td> 
  </tr> 
  <tr> 
   <td>FBX檔案格式——版本</td> 
   <td>建議使用FBX 2014/2015。 其他版本也可能正常運作。</td> 
  </tr> 
 </tbody> 
</table>

如果在AEM製作伺服器上安裝並設定Autodesk Maya，則支援下列其他檔案格式：

* 瑪雅汽車旅館

   ASCII和二 `.ma` 進位格 `.mb` 式。

* `Jupiter Tesselation (ISO 14306-1).jt`。

   業界標準的CAD資料交換、協作和產品視覺化格式。

### 支援紋理對應檔案 {#support-for-texture-map-files}

3D模型檔案中的材料定義可以包括對提供紋理映射的外部影像檔案的參照。 AEM 3D支援下列類型的紋理對應檔案：

* 擴散顏色紋理
* 鏡面顏色紋理
* 環境色彩紋理
* 置換圖（也稱為凹凸圖）
* 一般地圖
* 不透明度地圖
* 粗糙度地圖（又稱為光澤、反射率或余弦功率地圖）

主要3D模型檔案中的材質可參照AEM 3D忽略的其他類型地圖。

### IBL（影像光源）影像 {#ibl-image-based-lighting-images}

定義舞台的3D模型檔案可以引用單個IBL環境映像。 目前，AEM 3D僅支援32位元經緯度格式的TIFF影像，以用於擴散IBL和反射。 對於球面場景背景，也支援8位元RGB影像。

請參 [閱關於使用IBL階段](working-with-ibl-stages.md)。

>[!NOTE]
>
>主3D模型檔案中除上述參照之外的檔案參照當前將被忽略。 AEM 3D不支援輔助3D模型檔案的參照。
Y-up是本版次FBX檔案的首選坐標系。

## 主3D模型檔案中的材料著色 {#material-shading-in-a-primary-d-model-file}

原始原生模型檔案可包含與著色器（例如Blinn、Lambert或程式著色器）一起使用的材質定義。 只有當您使用對應的原生應用程式（例如Autodesk Maya）進行演算時，才支援這些可能複雜的材質。

為了便於查看或在使用預設的Rapid Refine™渲染器進行渲染時，所有材料都是簡化的、替換的或兩者兼有的，以便與類似Phong的著色器一起使用。 此著色器支援有限的屬性集。 忽略材料定義中的其它屬性。

請參 [閱檢視3D資產](viewing-3d-assets.md)。

請參 [閱演算3D資產](rendering-3d-assets.md)。

## 在主3D模型檔案中命名材料 {#naming-materials-in-a-primary-d-model-file}

曲 *面被定義為* 由相同材料覆蓋的3D模型的曲面面積。 此材料還提供曲面的名稱。 因此，Adobe建議您依此命名主要3D模型檔案中包含的材質。 例如，使用特定名稱（例如&quot;Body&quot;、&quot;Windows&quot;、&quot;Tires&quot;或&quot;Rims&quot;），較之使用模糊名稱（例如&quot;Red&quot;、&quot;Glass&quot;、&quot;Rubber&quot;、&quot;Aluminum&quot;）。


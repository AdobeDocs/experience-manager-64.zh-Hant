---
title: 關於在AEM中上傳和處理3D資產
seo-title: 關於在AEM中上傳和處理3D資產
description: 上傳和處理3D資產的最佳實務。
seo-description: 上傳和處理3D資產的最佳實務。
uuid: d8abf460-adff-4f0f-92ae-2c8651a17488
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: a0319701-21eb-4b7f-8b2e-ac81a7a75875
translation-type: tm+mt
source-git-commit: 5acb16b1734331767554261bbcf9640947f2e23f
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 1%

---


# 關於在AEM中上傳和處理3D資產 {#about-the-uploading-and-processing-of-d-assets-in-aem}

使用標準上傳或同步機制，將3D資產及其相關參照的檔案匯入AEM Assets。

請參閱 [上傳資產](managing-assets-touch-ui.md#uploading-assets)。

Adobe建議您在上傳主要3D模型檔案之前或同時上傳所有參照的檔案。 但是，這並非必要條件。

上傳完成時，會轉換您的3D檔案，並套用其他處理程式，以準備資產供檢視和轉譯。

## 上傳3D資產的最佳實務 {#best-practices-for-uploading-d-assets}

* 通常，您在AEM Assets檔案夾階層中上傳3D內容的位置沒有限制。 不過，AEM 3D的自動化檔案相依性解決方案有範圍限制，可控制搜尋大型資產儲存庫所花的時間。 因此，Adobe建議您在上傳3D資產及其檔案依存項時，在合理的距離內，在每個檔案（共同的祖父資料夾）附近執行此動作。 解決檔案相依性後，您可以任意移動3D資產及其相依項，而不會遺失已建立的關係。
* Adobe建議您在上傳前，先決定3D內容的一 *致資* 料夾結構。 以下提示是一些建議的方法，您可以採用：

   * **為您上傳的每個3D資產維護個別資料夾**。

      該資料夾同時包含主3D模型檔案及其所有從屬項。 雖然將所有資產和依存對象放入一個檔案夾很容易實施，但瀏覽內容卻很麻煩。 這也使模型之間共用依存對象（紋理映射）變得複雜。

   * **將模型保留在一個資料夾中，並將從屬對象保留在同級或子資料夾中**。

      這種方法支援模型之間的依存關係共用。 但是，如果資產數量龐大，就很難找到特定的依存對象。

   * **模型和依存對象的獨立並行資料夾層次**。

      您可以對此方法建立模型，以瞭解3D製作應用程式（例如Autodesk Maya）偏好儲存內容的方式。

* 除非也移除參照相依資產的相關3D資產或資產，否則不應刪除相依資產。 不過，您可以自由刪除3D資產，而不需刪除其相依資產。 如果意外丟失了相關性，您可以輕鬆解決相關性，以恢復該相關性。

   請參閱解決檔案相依性。

## 上傳3D檔案時的效能考量 {#performance-considerations-when-uploading-d-files}

轉換和處理3D檔案通常會耗用伺服器上的大量CPU和記憶體資源。 這也需要相當長的時間。 處理時間通常會因模型大小和伺服器功能而大不相同。 例如，一個面積小於100k的典型小型模型，通常在1分鐘內就可供檢視； 在2-3分鐘內完全處理。 然而，擁有100萬張以上臉孔的大型模型需要數十分鐘才能完全處理。

視需要將轉換、處理和轉換工作排入佇列，以避免伺服器速度變慢太多。 訊息「正在等待處理……」 在您上傳資產時 **[!UICONTROL ，卡片檢視]** (Card View)中有時會顯示。 此狀態表示在處理當前資產之前，必須完成其他處理或渲染作業。

機制可限制CPU用於擷取處理和演算。 如需如 [何設定CPU限制](advanced-config-3d.md) ，請參閱進階組態設定。

## 監控已上傳3D檔案的處理狀態 {#monitoring-the-processing-status-of-your-uploaded-d-files}

僅 **[!UICONTROL 在卡片檢視]** ，處理狀態和進度會顯示為資產卡片上的進度橫幅。 每個上傳的3D模型通常會經歷下列4-6個順序處理階段：

<table> 
 <tbody> 
  <tr> 
   <td><strong>處理階段</strong><br /> </td> 
   <td><strong>處理名稱</strong></td> 
   <td><strong>說明</strong></td> 
  </tr> 
  <tr> 
   <td>1</td> 
   <td>處理</td> 
   <td>基本的初始處理和中繼資料擷取。</td> 
  </tr> 
  <tr> 
   <td>2</td> 
   <td>轉換格式</td> 
   <td>3D模型正從原生格式（Autodesk® Maya®或Autodesk® 3ds Max®）轉換為中介格式(FBX)。</td> 
  </tr> 
  <tr> 
   <td>3</td> 
   <td>建立預覽</td> 
   <td>FBX或OBJ檔案已收錄並處理。 會盡可能評估和解析檔案相依性作為資產參照。</td> 
  </tr> 
  <tr> 
   <td>4</td> 
   <td>建立底影</td> 
   <td>選填。可讓您在3D物件下方的地面平面上產生環境遮擋陰影。 請參 <a href="/help/assets/advanced-config-3d.md">閱進階組態設定</a> ，以啟用或停用此處理。</td> 
  </tr> 
  <tr> 
   <td>5<br /> </td> 
   <td>建立光線圖</td> 
   <td>選填。可讓您提高互動式預覽的品質，並使用預設轉譯器加速轉譯。 請參 <a href="/help/assets/advanced-config-3d.md">閱進階組態設定</a> ，以啟用或停用此處理。</td> 
  </tr> 
  <tr> 
   <td>6<br /> </td> 
   <td>建立動畫</td> 
   <td>選填。可讓您演算簡單動畫，然後在「卡片檢視」中當做視覺縮圖使用。 請參 <a href="/help/assets/advanced-config-3d.md">閱進階組態設定</a> ，以啟用或停用此處理。</td> 
  </tr> 
  <tr> 
   <td>7<br /> </td> 
   <td>等待處理</td> 
   <td>顯示其他3D資產具有處理優先順序時。 例如，先前已上傳但尚未完成處理的資產。</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>您可以在「詳細資料檢視」中檢 **[!UICONTROL 視3D資產]** ，或在「建立預覽」階段完成後進行演算。 您不需要等待所有處理階段完成。


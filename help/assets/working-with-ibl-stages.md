---
title: 關於使用IBL階段
seo-title: 關於使用IBL階段
description: AEM 3D支援使用內建的Adobe Rapid Refine™轉譯器和協力廠商轉譯器，以影像為基礎的光源(IBL)進行互動式檢視和轉譯。
seo-description: AEM 3D支援使用內建的Adobe Rapid Refine™轉譯器和協力廠商轉譯器，以影像為基礎的光源(IBL)進行互動式檢視和轉譯。
uuid: 495ba9cc-02f5-4ce5-9503-9f61ca5482db
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 658ff671-16b9-41bd-ba24-b77a32b3346b
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '848'
ht-degree: 0%

---


# 關於使用IBL階段{#about-working-with-ibl-stages}

AEM 3D支援使用內建的Adobe Rapid Refine™轉譯器和協力廠商轉譯器，以影像為基礎的光源(IBL)進行互動式檢視和轉譯。 您可以使用常用的編寫工具（例如Autodesk® Maya®或Autodesk® 3ds Max®）來建立IBL階段。

## IBL的影像{#images-for-ibl}

用於影像光源的影像應具有HDR（高動態範圍），以獲得最佳效果。 它們必須採用平／長格式，具有球形映射，提供對環境的全面覆蓋。

目前，AEM 3D僅支援32位元TIFF。 如有必要，請使用Adobe Photoshop或類似的工具，在「Adobe Photoshop TIFF匯出」對話方塊中使用下列設定，將HDR影像轉換為TIFF:

* **[!UICONTROL 位元深度]** - 32位元（浮動）
* **[!UICONTROL 像素順序]** -交錯(RGBRGB)
* **[!UICONTROL 影像壓縮]** - LZW
* **[!UICONTROL 位元組順序]** - IBM PC

雖然單一HDR影像通常足以處理IBL階段，但AEM 3D可允許最多3個不同的影像，以提供對IBL效果的額外控制：

* **漫射照明環境影像** -這種影像應該是HDR影像，但可以相對小，因為在使用影像進行漫射照明之前，會對影像進行大量濾波。
* **反射環境影像** -此類影像用於在對象曲面中建立反射。它可以是尺寸和解析度的標準8位元RGB影像，提供所要的反射品質和清晰度。 如果指定HDR影像，AEM 3D會先將它轉換為8位元RGB，再使用專屬演算法。
* **背景環境影像** -此類型的影像會當做背景使用。它可以是標準的8位元RGB影像，而且應具備舞台背景所需的大小／解析度／細節層級。 如果指定HDR影像，AEM 3D會使用專屬演算法將其轉換為8位元RGB。

>[!NOTE]
>
>對於某些IBL影像，轉換算法可能存在一定的困難。 此困難可能導致背景在「預覽」或使用「快速調整」演算時過於亮或飽和。 在這種情況下，Adobe建議您使用Photoshop或類似的工具，手動將IBL影像轉換為8位元RGB影像。 請個別上傳此影像，並將它附加至舞台，做為背景環境影像。 漫射光源和反射環境影像必須永遠是32位元TIFF。

## 調整IBL舞台外觀{#adjusting-the-ibl-stage-appearance}

可以使用以下階段屬性微調IBL階段的外觀：

<table> 
 <tbody> 
  <tr> 
   <td><strong>屬性</strong><br /> </td> 
   <td><strong>說明</strong></td> 
  </tr> 
  <tr> 
   <td>IBL Sun詳細資訊</td> 
   <td><p>可讓您調整模擬太陽的輔助光源的方向和強度。 <span class="diff-html-added">該光源增加照明亮度並使物體在地面上投下陰影。使用快速調整演算和使用Google Chrome預覽時，支援陰影投影；但是，其他瀏覽器目前不支援它。</span></p> 
    <ul> 
     <li><strong>lat</strong> -太陽光源的垂直位置(<code>0.0</code>-<code>1.0</code>)。<br /> 水準線( <code>0.0</code> 漫射照明環境影像的垂直中心); <code>1.0</code> 位於天頂（漫射照明環境影像的上邊緣）。</li> 
     <li><strong>long</strong> -太陽光源的水準位置(<code>0.0</code>-<code>1.0</code>)。<br /> 0.0的設定與左側對應；1.0對應於漫射照明環境影像的右邊緣。<br /> </li> 
     <li><strong>bright</strong> -太陽光源的亮度。增加這個值，使陽光源變亮；降低此值以變暗。 <br /> 設定會關閉 <code>0</code> 輔助光源並停用投影陰影。該參數不影響環境反射。<br /> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>IBL相機高度</td> 
   <td>如果IBL背景在水準線附近出現失真，通過調整該屬性可以減少或消除失真。<br /> </td> 
  </tr> 
  <tr> 
   <td>環境照明</td> 
   <td><p><span class="diff-html-added">可讓您控制漫射光源。 如果漫射照明環境影像異常亮或暗（例如夜景），您可能需要手動調整此屬性以校正照明亮度。</span></p> 
    <ul> 
     <li><strong>r、g、b</strong> -目前未使用。</li> 
     <li><strong>bright</strong> -亮 <span class="diff-html-added">度倍增器。增大或減小該值可增加或減小總照明強度（基本IBL照明和日光源的亮度）。</span></li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## 增加IBL級球底直徑{#increasing-the-spherical-background-diameter-of-an-ibl-stage}

IBL級使用球形背景影像，預設情況下，球形背景影像直徑為20米。 這種平台對10米以上的物體非常適用。 但是，如果顯示較大的對象，則可以增加IBL舞台的球面背景直徑。

**要增加IBL級的球背景直徑**:

1. 在CRXDE Lite中，導覽至您要增加其球面背景直徑的舞台。 例如，

   `/content/dam/test3d/stage-helipad.fbx`

1. 將舞台節點展開到`jcr:content/metadata`。
1. 將屬性`dam:gPlaneRadius`設為所需的毫米值。

   為提高轉換效率，Adobe建議您將此值限制在您要在舞台上顯示的最大物件的最大尺寸。

   例如，如果`dam:gPlaneRadius=20000`，則長度為20米的噴射平面模型會顯示良好。

1. 在「CRXDE Lite」頁面的左上角附近，點選「Save All（全部保存）」。****


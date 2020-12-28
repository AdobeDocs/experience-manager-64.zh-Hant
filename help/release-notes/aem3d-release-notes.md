---
title: AEM 3D發行說明
seo-title: AEM 3D發行說明
description: Adobe Experience Manager Assets中3D內容的發行說明。
seo-description: Adobe Experience Manager Assets中3D內容的發行說明。
uuid: 6675951f-86f0-4ec5-97e4-d247f6faf913
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes, 3D
content-type: reference
discoiquuid: 9789d031-fb7e-415a-a9c3-8b8fde978238
translation-type: tm+mt
source-git-commit: 9710c9931b4f17073c712f5869a1843c1d99ee8e
workflow-type: tm+mt
source-wordcount: '1983'
ht-degree: 0%

---


# AEM 3D發行說明{#aem-d-release-notes}

>[!IMPORTANT]
>
>不再支援AEM 6.4中的AEM 3D功能套件。 Adobe建議您將[AEM中的3D資產功能當做雲端服務](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html)或[AEM 6.5.3或更新版本使用。](https://docs.adobe.com/content/help/en/experience-manager-65/assets/dynamic/assets-3d.html)

AEM-6.4-DynamicMedia-3D 3.1.0版（2018年10月10日）

AEM 3D功能套件可支援AEM Assets中的3D內容。 它提供上傳、管理、預覽和演算3D資產的功能。 針對個別物件（而非具有多個物件的複雜場景）最佳化檢視和演算支援。

AEM 3D支援Adobe Dimension(Dn)和glTF資產類型。 這些資產類型的實施方式與本檔案所述之傳統3D類型的實施方式大不相同。 請參閱[使用Adobe Dimension資產](/help/assets/working-dimension-assets.md)。

另外還包含伺服器端與Autodesk® Maya®的整合（僅限Windows）。 當您在與AEM相同的伺服器上安裝和設定Maya時，您就可支援原生Maya檔案格式，包括使用NVIDIA® Mentary® Standalone plug-in for Maya的高品質轉譯。 在伺服器上安裝和設定3ds Max可支援原生。max檔案格式。

請參閱[與Autodesk Maya](/help/assets/integrate-maya-with-3d.md)整合。

另請參閱[安裝和配置AEM 3D資產](/help/assets/install-config-3d.md)和[高級配置設定](/help/assets/advanced-config-3d.md)。

另請參閱[使用3D資產](/help/assets/assets-3d.md)。

## 系統要求{#system-requirements}

**必備條件**

* AEM 6.4.2(AEM 6.4 with Service Pack 2)
* Autodesk® FBX® SDK 2016.1.2

**支援的作業系統**

* Microsoft Windows 2012 Server或更新版本
* Apple OS X El Capitan 10.6或更新版本
* RedHat Enterprise Linux 7.3

**AEM Assets支援的網頁瀏覽器**

* Google Chrome 53或更新版本（建議）。
* Apple Safari 9.1或更新版本。
* Firefox 48或更新版本。
* Microsoft Edge 25.10586或更新版本。

其他瀏覽器可能不支援在AEM中互動檢視3D內容。 只有Google Chrome才支援「預覽」中的投影。

**硬體需求與建議**

* CPU —— 電腦的CPU對3D處理和渲染要求很高。 因此，建議使用最少8個CPU核心的現代伺服器。
* 記憶體——建議最少32 GB。
* 大容量儲存——建議使用高頻寬SSD儲存。

   上傳時，3D資產會轉換為專屬格式，以便快速互動檢視。 視3D資產類型而定，需要2-3倍於已上傳3D資產大小的儲存空間。

另請參閱[使用3D資產](/help/assets/assets-3d.md)。

## 安裝和設定AEM 3D {#installing-and-configuring-aem-d}

請參閱[安裝和設定AEM 3D](/help/assets/install-config-3d.md)。

另請參閱[「整合AEM 3D與Autodesk Maya](/help/assets/integrate-maya-with-3d.md)」和[「整合AEM 3D與Autodesk 3ds Max](/help/assets/integrating-aem-3d-with-autodesk-3ds-max.md)」。

## 支援的3D檔案格式{#supported-d-file-formats}

| 格式 | 說明 | 平台 | 附註 |
|--- |--- |--- |--- |
| DN | Adobe Dimension | 全部 | 需要存取雲端轉換服務。 |
| GLTZ | Zipped gITF | 全部 |  |
| GLB | 二進位gITF | 全部 | 僅下載（GLB轉譯會針對DN資產建立）。 |
| OBJ | Wavefront OBJ 3D | 全部 |  |
| FBX | Autodesk FBX(Kaydara Filmbox) | 全部 | Autodesk FBX SDK必須安裝在「作者」節點上。 |
| MA, MB | Native Autodesk Maya | 僅限Windows | Autodesk Maya在「作者」節點上必須啟用這些檔案格式。 請參閱[整合AEM 3D與Autodesk Maya](/help/assets/integrate-maya-with-3d.md)。 |
| JT | Siemens PLM Open CAD | 僅限Windows | Autodesk Maya在「作者」節點上必須啟用這些檔案格式。 請參閱[整合AEM 3D與Autodesk Maya](/help/assets/integrate-maya-with-3d.md)。 |
| * | Autodesk Maya支援的其他3D輸入格式可以啟用。 請參閱[啟用Maya](/help/assets/integrate-maya-with-3d.md#enabling-additional-formats-supported-by-maya)支援的其他格式。 | 僅限Windows | Autodesk Maya在「作者」節點上必須啟用這些檔案格式。 請參閱[整合AEM 3D與Autodesk Maya](/help/assets/integrate-maya-with-3d.md)。 |
| 最大值 | 原生Autodesk 3ds Max | 僅限Windows | 作者節點上需要有Autodesk 3ds Max才能啟用此檔案格式。 請參閱[整合AEM 3D與Autodesk 3ds Max](/help/assets/integrating-aem-3d-with-autodesk-3ds-max.md)。 |

## 增強功能與新功能{#enhancements-and-new-features}

3.0版

* 支援Autodesk 3ds Max原生檔案格式。
* 各種變更和錯誤修正可改善穩定性、品質和使用體驗。
* 配置設定已移到`/libs/settings/dam/v3d/`

第3.1版

* 對Adobe Dimension原生檔案格式(.dn)的支援有限。
* glTF資產的全新3D檢視器。
* Amazon AWS中托管的雲端Adobe管理轉換服務的新介面。 最初，此服務僅從Dn轉換為glTF格式。

## 限制與已知問題{#restrictions-and-known-issues}

### Adobe Dimension支援{#adobe-dimension-support}

* 此AEM3D版本對使用Adobe Dimension建立的。dn檔案的支援有限。
* 在上傳處理期間，AEM會運用雲端、Adobe代管的轉換服務，從原生。dn檔案建立glTF轉譯。 需要訪問轉換服務和選定的Amazon AWS端點。
* 提供新的glTF檢視器，可支援在AEM資產和網站／畫面中檢視Dn資產。 尚未提供檢視器中階段的支援。
* Dn模型可嵌入顯示的IBL光源和背景（如果存在）。 或者，檢視器會套用預設光源或預設背景顏色，或兩者皆適用。
* Dn資產尚未提供高品質的轉換功能。
* 依存項（例如紋理對應）會內嵌在Dn資產中，且無法在AEM中明確管理。

### 相容性{#compatibility}

* **不支援以Windows服務的形式運行（僅限Windows）** -這可能有效，但尚未測試。
* **Dynamic Media** ( `dynamicmedia-scene7` 模式)- AEM3D與隨AEM 6.4發行的全新Dynamic Media解決方案的相容性尚未完全驗證。如果動態媒體和AEM3D已部署在一起，建議您僅將3D資產及其相依性置於未指派給動態媒體的AEM Assets存放庫區域。 對於3D階段所需但動態媒體不支援的32位元TIFF檔案，此建議尤其重要。

### 一般 {#general}

* **解決相依性捷徑** -此捷徑可在3D資產的卡片檢視中使用。「卡片檢視」中的資產卡片會顯示「未解決的相依性」橫幅。 此快捷方式會開啟&#x200B;**基本屬性**&#x200B;頁籤，而不是&#x200B;**相關性**&#x200B;頁籤。 解決方法：手動導航至「相關性」頁籤。

* **舞台選取器不可用** -包含光源的3D資產會由AEM自動標籤為3D階段。「詳細資訊」視圖中沒有階段選擇器可用於階段。 要將3D資產標籤為3D對象，請導航至&#x200B;**基本屬性**，將&#x200B;**資產類**&#x200B;更改為&#x200B;**3D對象**，然後按一下&#x200B;**保存**。

* **下載具有從屬和轉譯的3D資產**  ****  **** -從AEM下載同時勾選「從屬和轉譯」的3D資產時，下載內容不僅包含主要3D資產的轉譯，也包含所有從屬者的轉譯。

* **Autodesk 3ds Max整合** -目前不支援使用3ds Max進行演算。

### 檔案類型限制{#file-type-restrictions}

* **Mathematica(.ma)檔案** - Mathematica檔案使用與原生Maya檔案相同的檔案尾碼。當安裝Feature Pack並啟用Maya .ma檔案格式時，AEM3D嘗試將Maya檔案當成Maya檔案。 這些資產會在「卡片」檢視中顯示錯誤橫幅。

* **Targa(.tga)影像檔案** -較舊的3D模型檔案可能包含對TGA檔案的引用。AEM不支援此格式。 Adobe建議您在將3D資產上傳至AEM之前，先將這些檔案轉換為不同格式。
* **HDR影像** - HDR影像用於具有影像光源(IBL)的舞台。目前，僅支援32位元TIFF影像。
* **32位元TIFF影像** - 32位元TIFF影像用於具有影像光源的舞台。AEM不支援為這些資產建立轉譯，因此會產生空白的縮圖，而且無法預覽。 當與IBL階段一起使用時，資產仍可正常運作。
* **Autodesk 3ds Max(.max)檔案** -如果Autodesk 3ds Max已安裝並設定在「作者」節點上，AEM支援擷取和轉換。max檔案。目前不支援將。max檔案當做階段使用。

### 自動相關性解析{#automatic-dependency-resolution}

* **上載後未解決的檔案相關性** -使用相同的上載操作上載3D資產及其依存對象時，有些依存對象可能無法自動解決。如果相依檔案較大，則更可能發生此問題。 要更正此問題，請訪問資產的&#x200B;**屬性／相依性**&#x200B;頁，該頁在上載後顯示未解決的從屬關係。 現在應顯示先前未解決的依存對象。 按一下&#x200B;**儲存**&#x200B;以完成資產。 為防止將來出現此問題，您可以在上載3D對象之前，先上載單獨事務中的所有依存對象。

* **區分大小寫** -自動相依性解析會嘗試以區分大小寫的方式比對檔案名稱。例如，如果3D資產中找到的原始相依性是`image.jpg`，則該相依性會解析為名為`Image.jpg`、`image.JPG`的資產，或任何其他案例變更。

### 3D階段{#d-stages}

* **階段的縮圖** -階段的自動產生縮圖可能無法精確表示階段。
* **非IBL級的舞台幾何** -快速調整渲染器不會使用非IBL光源（包括背景和地面平面）從舞台渲染幾何。此類幾何仍會在資產「細節」(Detail)視圖（3D預覽）中合理顯示。

* **具有IBL光源的FBX階段** -您可以使用IBL光源上傳FBX階段。但是，FBX格式沒有傳輸IBL映像名稱的規定。 因此，檔案相依性解析失敗。 上傳後，必須手動將IBL映像分配給舞台。 您可以將相同的32位元TIFF影像指派給&#x200B;**漫射照明環境影像**、**反射環境影像**&#x200B;和&#x200B;**背景環境影像**&#x200B;這三個相依性，或是指派不同的影像。

* **IBL階段的背景影像** -對於某些IBL場景，背景影像可能質量較差，如過亮或過模糊。為了最大化IBL階段的影像背景視覺品質，Adobe建議您準備個別的高解析度8位元JPEG影像，並將它附加至IBL階段，做為&#x200B;**背景環境影像**。

* **使用IBL舞台向Maya轉譯時的黑色影像** -此問題可能是由於Maya找不到IBL影像相依性，因為舞台所參照的原始IBL影像已由不同名稱的影像取代。為避免此問題，請確保Maya IBL階段所引用的三個相關性中至少有一個與Maya檔案中的原始IBL檔案引用同名。
* **IBL舞台的反背景影像** - IBL舞台的影像被有意水準翻轉，以匹配隨Autodesk Maya提供的NVIDIA心理射線渲染器的行為。解決方法：在上傳IBL階段之前，請先翻轉這些影像。
* **IBL階段亮度** -自動分析IBL影像可能會導致場景太暗或太亮。要調整IBL級的照明亮度，請導航至&#x200B;**基本屬性**&#x200B;並根據需要調整&#x200B;**環境照明**&#x200B;的&#x200B;**bright**&#x200B;值。

### AEM Sites 3D元件{#aem-sites-d-component}

* **每頁一個3D元件** -目前，每個網頁僅允許一個3D元件例項。如果將多個3D元件新增至相同頁面，則3D元件無法正確運作。
* **在Sites中預覽時遺失3D檢視** -當您使用 **** Previewin Sites時，必須在瀏覽器中重新載入頁面，才能完全初始化3D檢視器。當您在「作者」節點或「發佈」節點上直接檢視網頁時（即從路徑中移除`edit.html`時），這並不是問題。

* **iOS裝置無法使用全螢幕模式** -全螢幕按鈕在iOS裝置上不可用，不論使用的瀏覽器為何。

### 發佈3D內容{#publishing-d-content}

* **3D元件設定** -您必須在所有作用中的發佈節點上安裝3D功能套件，而且每個節點都必須使用 **CRXDE** Liteto的相同設定選項來設定，位於 `/libs/settings/dam/v3D/WebGLSites`。

* **發佈後遺失紋理、背景或光源** - AEM Sites中的 **** Publishmechanism會自動發佈頁面的主要相依性，包括3D模型和3D元件參照的3D階段。3D階段和3D模型通常依賴IBL影像和紋理地圖的次要資產，而「網站發佈」機制不會自動發佈。 解決方法：從「網站」發佈網頁之前，先從「資產」發佈所有3D資產。 這樣做可確保3D資產的所有相依性都可在「發佈」節點上使用。

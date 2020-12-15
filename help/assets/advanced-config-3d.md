---
title: 進階組態設定
seo-title: 進階組態設定
description: 瞭解適用於Maya和非Maya部署之AEM 3D整合的進階組態設定。
seo-description: 瞭解適用於Maya和非Maya部署之AEM 3D整合的進階組態設定。
uuid: 016e7745-e3c3-4d77-b95a-c0e671d719e2
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: e43fd002-2954-4ef1-ac2b-e8d45afa75be
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '1383'
ht-degree: 1%

---


# 高級配置設定{#advanced-configuration-settings}

雖然預設組態設定適合一般使用案例，但有時可能需要您進行變更。

下列進階組態設定適用於Maya和非Maya部署的AEM 3D整合。

所有設定都可使用AEM中的&#x200B;**CRXDE Lite**&#x200B;存取（**[!UICONTROL 工具>一般> CRXDE Lite]**）。

>[!NOTE]
>
>如果您重新安裝套件，它會將所有設定重設為預設值。

>[!CAUTION]
>
>編輯下表中未列出的任何設定可能會產生非預期或不想要的程式行為。

## 資產類型配置{#asset-types-configuration}

在AEM的&#x200B;**CRXDE Lite**（**[!UICONTROL 工具>一般> CRXDE Lite]**）中，存取下列組態：

| 路徑 | 說明 |
|---|---|
| `/libs/settings/dam/v3D/assetTypes/*/Conversion` | 指定擷取期間建立之中介3D格式的檔案類型。 &#39;fbx&#39;和&#39;obj&#39;檔案格式必須為空，或&#39;fbx&#39;格式必須由Maya啟用。 |
| `/libs/settings/dam/v3D/assetTypes/*/Enabled` | 設為true或false，以在&#x200B;**[!UICONTROL assetTypes]**&#x200B;清單中啟用或停用此項目。 |
| `/libs/settings/dam/v3D/assetTypes/*/Extension` | 指定一個或多個以逗號分隔的檔案字尾或要與此資產類型關聯的副檔名。 |
| `/libs/settings/dam/v3D/assetTypes/*/IngestRegime` | 對於FBX和OBJ檔案格式，必須為`native`，對於Maya啟用的格式，必須為`maya`。 |
| `/libs/settings/dam/v3D/assetTypes/*/MimeType` | 指定此資產類型的MIME類型。 對於Maya啟用的格式，建議使用`application/x-ext`，其中`ext`是指定為`Extension`值的字串。 |

## 擷取設定{#ingestion-configuration}

在AEM的&#x200B;**CRXDE Lite**（**[!UICONTROL 工具>一般> CRXDE Lite]**）中，存取下列組態：

<table> 
 <tbody> 
  <tr> 
   <td><strong>路徑</strong></td> 
   <td><strong>說明</strong></td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/addGroundPlaneImageOnIngest</td> 
   <td>在使用IBL舞台檢視或演算時，可產生環境遮擋陰影。 套用至使用RapidRefine預覽和演算</td> 
  </tr> 
  <tr> 
   <td><p>/libs/settings/dam/v3D/settings/cleanupRenderWorkDir</p> </td> 
   <td>設為<strong>false</strong>，以便在轉換和轉譯後，將暫存檔案保留在MayaWork檔案夾中。 在除錯Maya轉換和轉換問題時可能很有用。</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/invokeAnimationOnIngest</td> 
   <td><p>啟用後，ImageMagick會安裝在伺服器上，並設定magickPath。 「快速調整」可用來建立3D物件的簡單動畫，這些物件在「卡片檢視」和其他檢視中當做縮圖使用。</p> <p>建立動畫會在擷取程式期間耗用大量CPU資源。</p> </td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/invokeLightMapsOnIngest</td> 
   <td>可在擷取時自動建立光線地圖。 設為<strong>false</strong>以停用自動建立光線圖；這可大幅降低CPU的耗用量，並降低使用快速調整功能進行預覽和轉換的品質。 不會影響瑪雅的演算。</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/gPlaneZero</td> 
   <td><p>當設為<strong>true</strong>（預設）時，如有必要，將對象垂直移動，以確保對象的所有部分都在接地平面上(y=0)。</p> <p>當設為<strong>false</strong>（預設值）時，物件不會重新定位，而且可能會被舞台的接地平面部分隱藏。 （僅適用於使用快速調整功能進行預覽和演算）。 不過，這不會影響Maya的演算。 當設為<strong>true</strong>時，物件在Maya中的垂直位置可能與預覽或使用快速調整演算時不同。</p> </td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/Paths/magickPath</td> 
   <td>ImageMagick轉換實用程式的路徑和名稱。 如果啟用動畫縮圖建立，則需要絕對路徑。</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/MaxCpuPercentage</td> 
   <td><p>指定最多使用多少CPU來擷取3D資產。</p> <p>值越高，收件速度越快，但AEM整體回應速度可能越低。 此設定是近似的。 即，隨著可用CPU核心數目的增加，精度也會提高。</p> </td> 
  </tr> 
 </tbody> 
</table>

## 雲端服務組態設定{#cloud-services-configuration-settings}

您的Adobe客戶經理、布建專家或支援代表會提供下列設定的值。

| **路徑** | **說明** |
|---|---|
| `/libs/settings/dam/v3D/services/aws/accountId` | Adobe AWS帳戶的帳戶ID。 |
| `/libs/settings/dam/v3D/services/aws/bucketName` | S3傳輸桶的名稱；通常`aem3d`。 |
| `/libs/settings/dam/v3D/services/aws/customerId` | Adobe指派給您組織的唯一ID。 用作AWS Cognito用戶ID。 |
| `/libs/settings/dam/v3D/services/aws/encryptedPassword` | 與此customerId關聯的密碼。 用作AWS Cognito密碼。 |
| `/libs/settings/dam/v3D/services/aws/region` | 部署雲服務的AWS地區。 |
| `/libs/settings/dam/v3D/services/aws/userPoolId` | 適用的AWS Cognito用戶池ID。 |
| `/libs/settings/dam/v3D/services/dncr/clientId` | 用於dncr轉換服務的AWS Cognito客戶端ID。 |

## 常見處理設定{#common-processing-settings}

在AEM的&#x200B;**CRXDE Lite**（**[!UICONTROL 工具>一般> CRXDE Lite]**）中，存取下列組態：

| **路徑** | **說明** |
|---|---|
| `/libs/settings/dam/v3D/Paths/mayaWorkPath` | Maya轉換和轉換工作資料夾的名稱和位置。 如果資料夾不存在，則會自動建立該資料夾。 |
| `/libs/settings/dam/v3D/Paths/maxWorkPath` | 3ds最大轉換的工作資料夾的名稱和位置。 如果資料夾不存在，則會自動建立該資料夾。 |
| `/libs/settings/dam/v3D/settings/debugNative` | 設為&#x200B;**[!UICONTROL true]**，可在格式轉換和使用RapidRefine轉譯器轉譯時建立除錯資訊。 |

## 渲染器配置{#renderer-configuration}

在AEM的&#x200B;**CRXDE Lite**（**[!UICONTROL 工具>一般> CRXDE Lite]**）中，存取下列組態：

| **路徑** | **說明** |
|---|---|
| `/libs/settings/dam/v3D/settings/dynamicIBL` | 當設為&#x200B;**[!UICONTROL true]**&#x200B;且預先產生的光對應無法使用（即invokeLightMapsOnIngest=false）時，快速調整轉譯器會在轉譯期間建立光對應，以改善轉譯品質。 此設定可大幅增加演算時間。 設為&#x200B;**[!UICONTROL false]**&#x200B;會將這種情況下的CPU使用量降至最低，但可能導致較低的演算品質。 |
| `/libs/settings/dam/v3D/renderers/*/Enabled` | 分別設為&#x200B;**[!UICONTROL true]**&#x200B;或&#x200B;**[!UICONTROL false]**&#x200B;以啟用或停用轉譯器。 |
| `/libs/settings/dam/v3D/renderers/*/Display` | 可讓您變更在「演算」面板的「演算器」選取器中，針對啟用的演算器所顯示的字串。 |
| `/libs/settings/dam/v3D/renderers/*/MaxCpuPercentage` | 指定最多使用多少CPU來呈現3D場景。 值越高，轉譯速度越快，但AEM的整體回應速度可能越慢。 此設定是近似的。 即，隨著可用CPU核心數目的增加，精度也會提高。 |

## 3D資產預覽設定{#d-asset-preview-settings}

在AEM的&#x200B;**CRXDE Lite**（**[!UICONTROL 工具>一般> CRXDE Lite]**）中，存取下列組態：

| 路徑 | 說明 |
|---|---|
| `/libs/settings/dam/v3D/WebGLSites/autoSpin` | 設為&#x200B;**[!UICONTROL true]**&#x200B;或&#x200B;**[!UICONTROL false]**，以啟用或停用頁面載入時的自動回轉（自動相機軌道）。 |
| `/libs/settings/dam/v3D/WebGLSites/autoSpinAfterReset` | 設為&#x200B;**[!UICONTROL true]**，以在按下&#x200B;**[!UICONTROL Reset]**&#x200B;後重新啟動自動回轉。 停用自動回轉時忽略。 |
| `/libs/settings/dam/v3D/WebGLSites/autoSpinSpeed` | 指定自動回轉的速度（每分鐘轉數）和方向，其中由右至左的值為負值，而由左至右的旋轉為正值。 |
| `/libs/settings/dam/v3D/WebGL/continueRotate` | 設為&#x200B;**[!UICONTROL false]**，以停用對觸控和滑鼠手勢的檢視器回應逐漸淡出的持續功能。 |
| `/libs/settings/dam/v3D/WebGL/curtainColor` | 指定載入窗簾的顏色，可選擇覆蓋載入和初始化期間3D資產預覽的視區。 R,G,B值，每個顏色分量在0到255之間。 |
| `/libs/settings/dam/v3D/WebGL/fadeCurtains` | 當設為&#x200B;**[!UICONTROL true]**&#x200B;時，載入幕會在檢視器初始化的後半段逐漸淡出。 當設為&#x200B;**[!UICONTROL false]**&#x200B;時，簾布保持不透明，直到裝載和初始化完成。 |
| `/libs/settings/dam/v3D/WebGL/showCurtains` | 設為&#x200B;**[!UICONTROL true]**&#x200B;或&#x200B;**[!UICONTROL false]**，以啟用或停用3D資產預覽的載入幕。 |
| `/libs/settings/dam/v3D/WebGL/spinHeight` | 當自動回轉啟用並啟用時，相機的垂直位置會自動相對於3D物件的高度調整。 當設為0.5時，相機會垂直放置在物件高度的1/2處，這會導致水準線在視區中垂直置中。 值越大，相機會向下看物件並提高演算的水準線高度，值越小，相機就會向上看物件並降低水準線。 |

## 3D Sites元件設定{#d-sites-component-settings}

在AEM的&#x200B;**CRXDE Lite**（**[!UICONTROL 工具>一般> CRXDE Lite]**）中，存取下列組態：

| 路徑 | 說明 |
|---|---|
| `/libs/settings/dam/v3D/WebGLSites/autoSpinAfterReset` | 設為&#x200B;**[!UICONTROL true]**，以在按住家後重新啟用自動旋轉（自動相機軌道）。 停用自動回轉時忽略。 |
| `/libs/settings/dam/v3D/WebGLSites/continueRotate` | 設為&#x200B;**[!UICONTROL false]**，以停用對觸控和滑鼠手勢的檢視器回應逐漸淡出的持續功能。 |
| `/libs/settings/dam/v3D/WebGLSites/curtainColor` | 指定載入時可以選擇性地覆蓋3D Sites元件視區的載入窗簾的顏色。 R,G,B值，每個顏色分量在0到255之間。 |
| `/libs/settings/dam/v3D/WebGLSites/fadeCurtains` | 當設為&#x200B;**[!UICONTROL true]**&#x200B;時，載荷簾將在裝載和初始化的後半部分逐漸淡出。 當設為&#x200B;**[!UICONTROL false]**&#x200B;時，簾布保持不透明，直到裝載和初始化完成。 |
| `/libs/settings/dam/v3D/WebGLSites/showCurtains` | 設為&#x200B;**[!UICONTROL true]**&#x200B;或&#x200B;**[!UICONTROL false]**，以啟用或停用3D網站元件的載入簾幕。 |
| `/libs/settings/dam/v3D/WebGLSites/spinHeight` | 當自動回轉啟用並啟用時，相機的垂直位置會自動相對於3D物件的高度調整。 當設為0.5時，相機會垂直放置在物件高度的1/2處，這會導致水準線在視區中垂直置中。 值越大，相機會向下看物件並提高演算的水準線高度，值越小，相機就會向上看物件並降低水準線。 |


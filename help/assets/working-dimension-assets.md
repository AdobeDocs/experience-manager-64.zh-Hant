---
title: 使用Adobe Dimension資產
description: 在AEM 3D中使用Adobe Dimension資產。
contentOwner: Rick Brough
topic-tags: 3D
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
translation-type: tm+mt
source-git-commit: 6be46f6986d1631f711cfd4464cc4f2d17014681
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---


# 使用Adobe Dimension資產{#working-with-adobe-dimension-assets}

>[!IMPORTANT]
>
>不再支援AEM 6.4中的AEM 3D功能套件。 Adobe建議您將[AEM中的3D資產功能當做雲端服務](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html#dynamicmedia)或[AEM 6.5.3或更新版本。](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/assets-3d.html#dynamic) 使用Adobe Dimension資產時。

AEM 3D功能套件可支援AEM Assets、AEM Sites和AEM Screens中的Adobe Dimension資產（`.dn`檔案）。

以glTF Open Standard為基礎的全新3D檢視器，提供Adobe Dimension資產的預覽、網站和畫面檢視功能。

## 關於雲端轉換服務{#about-the-cloud-based-conversion-service}

當Dimension資產上傳至AEM時，檔案副本會轉送至Amazon AWS中代管的Adobe管理雲端服務。 此服務會從Adobe專屬的Dimension檔案格式轉換為開放標準glTF格式。 轉換的3D模型封裝為二進位glTF(`.glb`)。 AEM會將轉換後的模型與主要的Dimension資產儲存為轉譯。

您可以使用下列兩種方式之一來設定`.glb`轉換格式（如需指示，請參閱[安裝和設定AEM 3D](install-config-3d.md)）:

* 當使用Adobe glTF檢視器在AEM Assets、AEM Sites或AEM Screens中檢視Dimension資產時，可加入Adobe專用的擴充功能，以發揮最大的視覺品質。 這會使`.glb`轉譯與大部分的協力廠商應用程式不相容。
* 排除Adobe專用的擴充功能，以與協力廠商應用程式相容。 `.glb`這會限制在AEM Assets、AEM Sites或AEM Screens（例如，無IBL光源）中檢視時的視覺品質，以模擬一般協力廠商應用程式的品質。

將Dimension/glTF檔案傳輸到Amazon AWS或從Amazon AWS傳輸檔案及其在AWS中的臨時儲存完全安全。 這些檔案在Amazon AWS中保存的時間最短；通常在正常操作期間不超過幾分鐘。

若要啟用維度資產支援，您必須從Adobe取得存取轉換服務的認證。 請參閱[安裝和設定AEM 3D](install-config-3d.md)。

>[!NOTE]
>
>如果您安裝並使用提供的認證，您瞭解並同意您的Adobe Dimension 3D資產將轉移至Amazon AWS中代管的Adobe管理、雲端轉換服務，並由其處理。

### 在AEM資產上檢視{#viewing-on-aem-assets}

AEM 3D功能套件包含以glTF Open Standard為基礎的新檢視器，此標準用於檢視Adobe Dimension資產。 當在AEM Assets的「詳細資訊」檢視中開啟Dimension檔案或壓縮的glTF，或在AEM Sites的3D元件時，會自動選取此檢視器。

請注意，glTF檢視器的使用者介面與所有其他3D資產類型所使用的標準3D檢視器有些不同。

#### 另請參閱下列：{#see-also-the-following}

* [AEM 3D發行說](/help/release-notes/aem3d-release-notes.md) 明，以瞭解Dn資產和glTF檢視器的限制和限制。
* [使用3D Sites元件，以](using-the-3d-sites-component.md) 取得Adobe Dimension資產專屬的元件屬性。
* [安裝和設定AEM 3](install-config-3d.md) To configure the cloud-based conversion service.


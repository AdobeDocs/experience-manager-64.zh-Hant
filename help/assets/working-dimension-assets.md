---
title: 使用Adobe Dimension資產
description: 在3D中使用Adobe DimensionAEM資產。
contentOwner: Rick Brough
topic-tags: 3D
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
exl-id: be8f6361-607d-4529-aef0-e8978dfd04b4
feature: 3D Assets
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# 使用Adobe Dimension資產{#working-with-adobe-dimension-assets}

>[!IMPORTANT]
>
>不AEM再支援AEM6.4版的3D功能套件。 Adobe建議您使用[中的3D資產功AEM能作為Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html#dynamicmedia)或&lt;a2/AEM> 6.5.3或更高版本。[](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/assets-3d.html#dynamic) 與Adobe Dimension資產搭配使用。

3D功AEM能套件支援AEM Assets、AEM Sites和AEM Screens的Adobe Dimension資產（`.dn`檔案）。

以glTF Open Standard為基礎的全新3D檢視器，提供Adobe Dimension資產的預覽和網站與畫面檢視功能。

## 關於雲端轉換服務{#about-the-cloud-based-conversion-service}

當Dimension資產上傳到AEM時，檔案副本將轉發到AmazonAWS中托管的Adobe管理雲服務。 此服務會從Adobe專有Dimension檔案格式轉換為開放標準glTF格式。 轉換的3D模型封裝為二進位glTF(`.glb`)。 將AEM已轉換的模型與主要Dimension資產一起儲存為轉譯。

您可以使用下列兩種方式之一來設定`.glb`轉換格式(請參閱[安裝和設定AEM3D](install-config-3d.md)以取得指示):

* 在使用AdobeglTF檢視器檢視AEM Assets、AEM Sites或AEM Screens的Dimension資產時，加入特定Adobe擴充功能，以提高視覺品質。 這會使`.glb`轉譯與大部分的協力廠商應用程式不相容。
* 排除Adobe專用的擴充功能，以達成`.glb`轉譯與協力廠商應用程式的相容性。 這會限制在AEM Assets、AEM Sites或AEM Screens（例如，無IBL光源）檢視時的視覺品質，以模擬一般協力廠商應用程式的品質。

將Dimension/glTF檔案傳輸到AmazonAWS或從AWS傳輸，以及它們在AWS中的臨時儲存完全安全。 這些檔案在AmazonAWS中的存留時間最短；通常在正常操作期間不超過幾分鐘。

若要啟用對Dimension資產的支援，您必須從Adobe取得存取轉換服務的認證。 請參閱[安裝和配AEM置3D](install-config-3d.md)。

>[!NOTE]
>
>如果您安裝和使用提供的認證，您瞭解並同意您的Adobe Dimension3D資產將轉移至AmazonAWS中托管的Adobe管理、雲基轉換服務，並由其處理。

### 在AEM Assets查看{#viewing-on-aem-assets}

3D功AEM能套件包含以glTF Open Standard為基礎的新檢視器，用於檢視Adobe Dimension資產。 在AEM Assets的「細節」(Detail)視圖中開啟Dimension檔案或壓縮的glTF或在AEM Sites的3D元件時，此查看器將自動選中。

請注意，glTF檢視器的使用者介面與所有其他3D資產類型所使用的標準3D檢視器有些不同。

#### 另請參閱下列：{#see-also-the-following}

* [3D發AEM行說明，以](/help/release-notes/aem3d-release-notes.md) 瞭解適用於Dn資產和glTF檢視器的限制和限制。
* [使用3D Sites元件，以取](using-the-3d-sites-component.md) 得Adobe Dimension資產專屬的元件屬性。
* [安裝和設AEM定3](install-config-3d.md) 以設定雲端轉換服務。

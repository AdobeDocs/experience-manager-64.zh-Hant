---
title: AEM 6.4的回溯相容性
seo-title: AEM 6.4的回溯相容性
description: 瞭解如何讓您的應用程式和設定與AEM 6.4相容
seo-description: 瞭解如何讓您的應用程式和設定與AEM 6.4相容
uuid: 2fa8525e-7f3b-4096-ac85-01c2c76bc9ac
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: 5e76fe09-4d37-4c8c-8baf-97e75689bd26
translation-type: tm+mt
source-git-commit: 6fc1a2502187be0fbbfbea516788e705f1a2697c
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---


# AEM 6.4{#backward-compatibility-in-aem}的回溯相容性

## 概覽 {#overview}

>[!NOTE]
>
>如需不在「相容性套件」範圍內的內容和設定變更清單，請參閱「AEM 6.4[中的資料庫重組」。](/help/sites-deploying/repository-restructuring.md)

在AEM 6.4中，所有功能都已在開發時考慮到向後相容性。

在大多數情況下，執行AEM 6.3的客戶在進行升級時，不必變更程式碼或自訂設定。 對於AEM 6.1和6.2客戶，沒有比升級至6.3時所面臨的額外突破性變更。

如果功能無法保持向後相容，則可透過安裝6.3版的相容性套件來達成套件和內容的向後相容性（如需下載位置的詳細資訊，請參閱以下設定）。 此相容性套件將可恢復與AEM 6.3相容之應用程式的相容性。

「相容性套件」可讓您在相容性模式下執行AEM，並針對新的AEM功能延遲自訂開發：

>[!NOTE]
>
>請注意，相容性套件只是暫時性解決方案，可延遲AEM 6.4相容所需的開發，如果您無法在升級後立即透過開發解決相容性問題，建議將它當成最後一個選項。 強烈建議在您決定繼續6.4自訂開發並運用完整的6.4功能後，切換至原生模式並解除安裝相容性套件。

![screen_shot_2018-04-05at4339pm](assets/screen_shot_2018-04-05at43339pm.png)

Compatibility Package有兩種模式：**啟用路由**&#x200B;和&#x200B;**禁用路由**。

這可讓AEM 6.4以三種模式執行：

**原生模式：**

原生模式適用於想要使用AEM 6.4所有新功能並準備進行一些開發的客戶，讓他們的自訂功能可搭配所有新功能運作。

這表示在升級後，您可能需要立即對您的應用程式進行調整。

**相容模式：已安裝相容包並啟用了路由**

相容性模式適用於具有向後不相容介面的定製的客戶。 這可讓AEM在相容模式下執行，並針對與部分自訂程式碼不相容的新AEM功能，延遲所需的自訂開發。

**舊模式：已安裝相容包且禁用路由**

舊版模式適用於具有自訂介面的客戶，這些介面是根據AEM中已移出相容性套件的舊版或已過時代碼。

![image2018-2-12_23-58-37](assets/image2018-2-12_23-58-37.png)

## 設定方法 {#how-to-set-up}

AEM 6.3 Compatibility Package可使用Package Manager以套件形式安裝。 您可從「軟體散發」網站下載[AEM 6.3相容性套件。](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/compatpack/aem-compat-cq64-to-cq63)

在安裝Compatibility Package後，可以使用OSGI配置中的交換機啟用或禁用路由，如下所示：

![screen_shot_2017-11-27at122421pm](assets/screen_shot_2017-11-27at122421pm.png)

安裝並設定相容性軟體包後，將根據已選擇的相容性模式使用這些功能。

---
title: AEM 6.4的向後相容性
seo-title: Backward Compatibility in AEM 6.4
description: 了解如何讓您的應用程式和設定與AEM 6.4相容
seo-description: Learn how to keep your apps and configurations compatible with AEM 6.4
uuid: 2fa8525e-7f3b-4096-ac85-01c2c76bc9ac
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: 5e76fe09-4d37-4c8c-8baf-97e75689bd26
feature: Upgrading
exl-id: 5798100a-e03a-43f8-9189-ae51c06e192b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 1%

---

# AEM 6.4的向後相容性{#backward-compatibility-in-aem}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

## 概觀 {#overview}

>[!NOTE]
>
>有關不在相容性包範圍內的內容和配置更改的清單，請參見 [AEM 6.4中的存放庫重新調整架構](/help/sites-deploying/repository-restructuring.md).

在AEM 6.4中，所有功能都是針對回溯相容性而開發。

在大多數情況下，執行AEM 6.3的客戶在執行升級時，不應變更程式碼或自訂。 對於AEM 6.1和6.2客戶，升級至6.3期間不會遇到其他重大變更。

對於無法保持功能向後相容的例外情況，可通過安裝6.3版的相容性包來實現套件和內容的向後相容（有關下載位置的詳細資訊，請參閱下面的設定）。 此相容性套件將恢復與AEM 6.3相容的應用程式的相容性。

相容性套件可讓您以相容模式執行AEM，並根據新的AEM功能推遲自訂開發：

>[!NOTE]
>
>請注意，相容性套件僅是暫時性解決方案，可延遲AEM 6.4相容所需的開發，只有在升級後立即透過開發解決相容性問題時，才建議使用此套件作為最後選項。 強烈建議您切換至原生模式，並在您決定繼續進行6.4型自訂開發並使用完整的6.4功能時解除安裝相容性套件。

![screen_shot_2018-04-05at43339pm](assets/screen_shot_2018-04-05at43339pm.png)

相容性包有兩種模式： **已啟用路由** 和 **已禁用路由**.

這可讓AEM 6.4以三種模式執行：

**本機模式：**

原生模式適用於想使用AEM 6.4的所有新功能，且已準備好執行一些開發，讓其自訂功能可搭配所有新功能運作的客戶。

這表示升級後，您可能需要立即對應用程式進行調整。

**相容性模式：安裝相容性包並啟用路由**

相容性模式適用於具有自訂介面且無法回溯相容的客戶。 這可讓AEM以相容模式執行，並針對與您某些自訂程式碼不相容的新AEM功能，延後所需的自訂開發。

**舊模式：安裝的相容性包禁用路由**

舊版模式適用於具有自訂介面的客戶，這些介面是根據相容性套件中已移出之AEM的舊版或已棄用的程式碼。

![image2018-2-12_23-58-37](assets/image2018-2-12_23-58-37.png)

## 設定方法 {#how-to-set-up}

AEM 6.3相容性套件可使用套件管理器以套件形式安裝。 您可以下載 [來自Software Distribution的AEM 6.3相容性套件](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/compatpack/aem-compat-cq64-to-cq63) 頁簽。

安裝相容性套件後，即可使用OSGI配置中的交換機來啟用或禁用路由，如下所示：

![screen_shot_2017-11-27at122421pm](assets/screen_shot_2017-11-27at122421pm.png)

安裝並設定相容性軟體包後，將根據已選擇的相容性模式使用功能。

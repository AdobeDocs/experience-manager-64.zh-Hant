---
title: 升級至AEM 6.4
seo-title: 升級至AEM 6.4
description: 了解將舊版AEM安裝升級至AEM 6.4的基本知識。
seo-description: 了解將舊版AEM安裝升級至AEM 6.4的基本知識。
uuid: aa878528-5161-4df3-9fed-cc779fb6bdbe
contentOwner: sarchiz
topic-tags: upgrading
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
discoiquuid: 81ceb91d-039e-45f0-9b0c-b8233901dea8
targetaudience: target-audience upgrader
feature: 升級
exl-id: 791da16c-bf2c-47a9-86a4-0a601a1b017e
source-git-commit: edba9586711ee5c0e5549dbe374226e878803178
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 3%

---

# 升級至AEM 6.4{#upgrading-to-aem}

在本節中，我們會說明將AEM安裝升級至AEM 6.4:

* [規劃升級](/help/sites-deploying/upgrade-planning.md)
* [使用模式檢測器評估升級複雜性](/help/sites-deploying/pattern-detector.md)
* [AEM 6.4的向後相容性](/help/sites-deploying/backward-compatibility.md)
* [升級程式](/help/sites-deploying/upgrade-procedure.md)
* [升級程式碼和自訂](/help/sites-deploying/upgrading-code-and-customizations.md)
* [升級前維護任務](/help/sites-deploying/pre-upgrade-maintenance-tasks.md)
* [執行就地升級](/help/sites-deploying/in-place-upgrade.md)
* [升級後檢查和疑難排解](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md)
* [可持續升級](/help/sites-deploying/sustainable-upgrades.md)
* [延遲內容移轉](/help/sites-deploying/lazy-content-migration.md)
* [AEM 6.4中的存放庫重新調整架構](/help/sites-deploying/repository-restructuring.md)

為了更方便參考這些程式中涉及的AEM例項，本文中會使用下列辭彙：

* *source*&#x200B;例項是您要升級的AEM例項。
* *target*&#x200B;例項是您要升級的例項。

>[!NOTE]
>
>為了改善升級的可靠性，AEM 6.4進行了全面的儲存庫重組。 如需如何與新結構一致的詳細資訊，請參閱AEM 6.4](/help/sites-deploying/repository-restructuring.md)中的[存放庫重新調整

## 變更為何？{#what-has-changed}

以下是過去數個AEM版本中備注的重大變更：

AEM 6.0推出新的Jackrabbit Oak存放庫。 持久性管理器被[微內核](/help/sites-deploying/recommended-deploys.md)替換。 自6.1版開始，不再支援CRX2。 需要執行名為crx2oak的移轉工具，才能從5.6.1例項移轉CRX2存放庫。 如需詳細資訊，請參閱[使用CRX2OAK移轉工具](/help/sites-deploying/using-crx2oak.md)。

如果要使用Assets Insights ，而您要從AEM 6.2以前的版本進行升級，則必須移轉資產，並透過JMX Bean產生ID。 在我們的內部測試中，TarMK環境上的125,000個資產會在一小時內移轉，但您的結果可能會有所不同。

AEM 6.3導入了`SegmentNodeStore`的新格式，此格式是TarMK實作的基礎。 如果您從AEM 6.3以前的版本升級，則升級過程中需要進行存放庫移轉，涉及系統停機。

Adobe工程估計這要20分鐘左右。 請注意，不需要重新索引。 此外，新版crx2oak工具已發行，可搭配新的存放庫格式使用。

**如果從AEM 6.3升級至AEM 6.4，則不需要進行此移轉。**

升級前維護任務已優化，以支援自動化。

crx2oak工具命令列使用選項已變更為適合自動化，並支援更多升級路徑。

升級後檢查也使自動化更加方便。

修訂的定期垃圾收集和資料儲存垃圾收集現在是需要定期執行的例行維護任務。 導入AEM 6.3後，Adobe支援並建議進行線上修訂清除。 有關如何配置這些任務的資訊，請參閱[修訂清除](/help/sites-deploying/revision-cleanup.md)。

**AEM 6.4** 推出模式偵 [測](/help/sites-deploying/pattern-detector.md) 器，以評估您開始規劃升級時的升級複雜性。6.4還著重於功能的[向後相容性](/help/sites-deploying/backward-compatibility.md)。 最後，還新增了[可持續升級](/help/sites-deploying/sustainable-upgrades.md)的最佳實務。

如需最新AEM版本中其他變更項目的詳細資訊，請參閱完整發行說明：

* [https://helpx.adobe.com/tw/experience-manager/6-2/release-notes.html](https://helpx.adobe.com/tw/experience-manager/6-2/release-notes.html)
* [https://helpx.adobe.com/tw/experience-manager/6-3/release-notes.html](https://helpx.adobe.com/tw/experience-manager/6-3/release-notes.html)
* [https://helpx.adobe.com/tw/experience-manager/6-4/release-notes.html](https://helpx.adobe.com/tw/experience-manager/6-4/release-notes.html)

## 升級概述{#upgrade-overview}

升級AEM是多步驟程式，有時為多月程式。 以下概述概述了升級專案中的內容，以及本檔案中包含的內容：

![screen_shot_2018-03-30at80708am](assets/screen_shot_2018-03-30at80708am.png)

## 升級流程，帶6.4升級改進{#upgrade-overview-1}

下圖說明整體建議流程，重點說明升級方法。 請注意，我們引入的新功能有參考。 升級應從模式偵測器開始（請參閱[使用模式偵測器評估升級複雜度](/help/sites-deploying/pattern-detector.md)），這可讓您根據產生的報表模式，決定要採取哪個路徑來與AEM 6.4相容。

6.4的重點是讓所有新功能向後相容，但在您仍看到某些向後相容問題時，相容性模式可讓您暫時推遲開發，以保持自訂程式碼與6.4相容。此方法可協助您在升級後立即避免開發工作(請參閱AEM 6.4](/help/sites-deploying/backward-compatibility.md)中的[向後相容)。

最後，在您的6.4開發週期中，「可持續升級」（請參閱[可持續升級](/help/sites-deploying/sustainable-upgrades.md)）中引入的功能可幫助您遵循最佳做法，使未來的升級更加高效和無縫。

![6_4_upgrade_overviewflowchart-newpage3](assets/6_4_upgrade_overviewflowchart-newpage3.png)

---
title: 版本清除
seo-title: 版本清除
description: 本文說明版本清除的可用選項。
seo-description: 本文說明版本清除的可用選項。
uuid: 6140c87e-ae1c-409d-bdbb-71b397f0b738
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 56f36dcf-8fbd-43f8-bf74-e88d5b686160
translation-type: tm+mt
source-git-commit: 510b6765e11a5b3238407322d847745f09183d63

---


# 版本清除{#version-purging}

在標準安裝中，當您在更新內容後啟動頁面時，AEM會建立新版本的頁面或節點。

>[!NOTE]
>
>如果未進行任何內容變更，您會看到訊息，指出頁面已啟動，但不會建立新版本

您可以使用側點的「版本控制」標籤， **在要求時** ，建立其他版本。 這些版本儲存在儲存庫中，並可以根據需要進行還原。

這些版本不會清除，因此儲存庫大小會隨著時間而增長，因此需要進行管理。

AEM隨附各種機制，可協助您管理您的儲存庫：

* 版本 [管理器](#version-manager)

   這可設定為在建立新版本時清除舊版本。

* 清除 [版本工具](/help/sites-deploying/monitoring-and-maintaining.md#version-purging)

   這是監視和維護儲存庫的一部分。

   它允許您根據以下參數進行干預，以刪除節點的舊版本或節點層次：

   * 儲存庫中要保存的最大版本數。

      超過此數目時，會移除最舊的版本。

   * 儲存庫中任何版本的最大存留期。

      當版本的年齡超過此值時，會從儲存庫中清除它。

* 「版 [本清除」維護任務](/help/sites-administering/operations-dashboard.md#automated-maintenance-tasks)。 您可以計畫「版本清除」維護任務，以自動刪除舊版。 因此，這將手動使用「版本清除」工具的需求降至最低。

>[!CAUTION]
>
>為了優化儲存庫大小，您應經常運行版本清除任務。 當流量有限時，應排程工作在營業時間以外的時間。

## 版本管理員 {#version-manager}

除了通過清除工具明確清除外，還可以將「版本管理器」配置為在建立新版本時清除舊版本。

要配置版本管理器，請為以下項目建立配置：

`PID com.day.cq.wcm.core.impl.VersionManagerImpl`

可使用下列選項：

* `versionmanager.createVersionOnActivation` (布林值，預設值：true)

   是否在啟動頁面時建立版本。

   除非將複製代理配置為禁止建立版本，否則將建立版本， Version Manager將遵守該版本

   只有在versionmanager.ivPaths中包含的路徑上進行啟動時，才會建立版本（請參閱下面）。

* `versionmanager.ivPaths` (字串[]，預設值：{&quot;/&quot;})

   如果versionmanager.createVersionOnActivation為true，則在啟動時隱式建立版本的路徑。

* `versionmanager.purgingEnabled` (布林值，預設值：false)

   是否在建立新版本時啟用清除

* `versionmanager.purgePaths` (字串[]，預設值：{&quot;/content&quot;})

   建立新版本時，要清除版本的路徑。

* `versionmanager.maxAgeDays` (int，預設值：30)

   清除時，任何舊於此值的版本都將被移除。 如果此值小於1，則不會根據版本的年齡執行清除

* `versionmanager.maxNumberVersions` （int，預設值5）

   清除後，任何早於第n個最新版本的版本都將被刪除。 如果此值小於1，則不會根據版本數執行清除

* `versionmanager.minNumberVersions` （int，預設值0）

   不論年齡為何，最低版本數。 如果此值設為小於1的值，則不會保留最低版本數。

>[!NOTE]
>
>建議不要在儲存庫中保留大量版本。 因此，在配置版本清除操作時請注意不要從清除中排除太多版本，否則儲存庫大小將無法正確優化。 如果您因業務需求而保留大量版本，請聯絡Adobe支援以尋找最佳化儲存庫大小的其他方法。

### 結合保留選項 {#combining-retention-options}

定義應如何保留的版本( `maxAgeDays`、 `maxNumberVersions`、 `minNumberVersions`)的選項，可根據您的需求加以組合。

例如，定義要保留的最大版本數AND要保留的最舊版本時：

* 設定:

   * `maxNumberVersions` = 7
   * `maxAgeDays` = 30

* 使用:

   * 過去60天內製作了10個版本
   * 其中3個版本是在過去30天內建立

* Will means that:

   * 最後3個版本將會保留

例如，在定義要保留的最大AND最小版本數和要保留的最舊版本時：

* 設定:

   * `maxNumberVersions` = 3
   * `maxAgeDays` = 30
   * `minNumberVersions` = 3

* 使用:

   * 60天前製作的5個版本

* Will means that:

   * 3個版本將保留

## 清除版本工具 {#purge-versions-tool}

清除 [版本工具](/help/sites-deploying/monitoring-and-maintaining.md#purgeversionstool) ，用於清除儲存庫中節點版本或節點層次結構。 其主要用途是通過刪除節點的舊版本來幫助您減小儲存庫的大小。

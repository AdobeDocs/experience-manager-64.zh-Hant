---
title: 升級程式碼和自訂
seo-title: 升級程式碼和自訂
description: 進一步了解如何升級AEM中的自訂程式碼。
seo-description: 進一步了解如何升級AEM中的自訂程式碼。
uuid: d4b6717c-41da-4dcc-b85c-51842192ca8d
contentOwner: sarchiz
topic-tags: upgrading
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
discoiquuid: ba8efc24-a34c-477b-8c6d-6e8f893eb999
targetaudience: target-audience upgrader
feature: 升級
exl-id: ed67e664-3be0-4337-85bd-cd042915b021
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2227'
ht-degree: 0%

---

# 升級代碼和自定義{#upgrading-code-and-customizations}

規劃升級時，需要調查並處理實作的下列方面。

* [升級程式碼庫](#upgrade-code-base)
* [與6.4儲存庫結構一致](#align-repository-structure)
* [AEM自訂](#aem-customizations)
* [測試程式](#testing-procedure)

## 概覽 {#overview}

1. **模式偵測器**  — 如升級規劃中所述並在本頁中詳細說明，執行模式偵測器，以取得模式偵測器報表，其中包含除了AEM Target版本中無法使用的API/套件組合外，還需要處理之區域的詳細資訊。 [](/help/sites-deploying/pattern-detector.md) 「模式偵測」報表應可指出程式碼中有任何不相容之處，如果沒有相容，表示您的部署已相容6.4，您仍可以選擇進行新開發，以利用6.4功能，但您不僅需要它來維護相容性。 如果報告了不相容，則可以選擇a)以相容模式運行，並推遲新的6.4功能或相容性的開發；b)升級後決定進行開發，然後移至步驟2。 如需詳細資訊，請參閱AEM 6.4](/help/sites-deploying/backward-compatibility.md)中的[向後相容性。

1. **開發6.4適用的程式碼基底**  — 為Target版本的程式碼基底建立專用的分支或存放庫。使用升級前相容性中的資訊來規劃要更新的代碼區域。
1. **使用6.4 Uber jar編譯**  — 更新程式碼基底POM以指向6.4 Uber jar，並針對此編譯程式碼。
1. **更新AEM自訂**  - AEM的任何自訂或擴充功能應更新/驗證以在6.4中運作，並新增至6.4程式碼基底。包含UI搜尋Forms、資產自訂、任何使用/mnt/覆蓋的項目

1. **部署至6.4環境**  — 在開發/QA環境中，應備妥AEM 6.4的乾淨例項（製作+發佈）。應部署更新的程式碼基底和具有代表性的內容範例（來自目前的生產環境）。
1. **QA驗證和錯誤修正**  - QA應驗證6.4的製作和發佈例項上的應用程式。發現的任何錯誤都應修正並提交至6.4程式碼基底。視需要重複開發週期，直到所有錯誤都修正完畢。

繼續升級之前，您應該有穩定的應用程式程式碼基底，且已針對AEM的目標版本進行徹底測試。 根據測試中的觀察，可以有方法最佳化自訂程式碼。 這可能包括重構程式碼以避免遍歷儲存庫、自訂索引以最佳化搜尋，或在JCR中使用無序節點等。

除了升級程式碼基底和自訂以與新AEM版本搭配使用的選項外， 6.4也有助於使用「回溯相容性」功能更有效率地管理您的自訂，如[本頁面](/help/sites-deploying/backward-compatibility.md)所述。

如上所述並如下圖所示，在第一步中執行[模式偵測器](/help/sites-deploying/pattern-detector.md)將幫助您評估升級的整體複雜性，以及您是否要以相容模式執行或更新您的自訂項目以使用所有新AEM 6.4功能。 如需詳細資訊，請參閱AEM 6.4](/help/sites-deploying/backward-compatibility.md)中的[向後相容性頁面。
[ ![screen_shot_2018-03-30at175257](assets/screen_shot_2018-03-30at175257.png)](assets/upgrade-code-base-highlevel.png)

## 升級代碼庫{#upgrade-code-base}

### 在版本控制項{#create-a-dedicated-branch-for-6-4-code-in-version-control}中為6.4代碼建立專用分支

您的AEM實作所需的所有程式碼和設定，都應使用某種版本控制來管理。 應建立版本控制中的專用分支，以管理目標版本AEM中程式碼基底所需的任何變更。 在此分支中，會針對AEM的目標版本進行程式碼基底的反覆測試，並管理後續的錯誤修正。

### 更新AEM Uber Jar版本{#update-the-aem-uber-jar-version}

AEM Uber jar會在Maven專案的`pom.xml`中，將所有AEM API視為單一相依性。 將Uber Jar納入為單一相依性，而非納入個別AEM API相依性，永遠是最佳作法。 升級程式碼基底時，應變更Uber Jar的版本，以指向AEM的目標版本。 如果您的專案是在AEM版本上開發，Uber Jar尚未存在時，所有個別AEM API相依性都應移除，並取代為目標AEM版本僅包含Uber Jar一次。 接著，應根據新版Uber Jar重新編譯程式碼基底。 任何已棄用的API或方法都應更新，以與AEM的目標版本相容。

```
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.4.0</version>
    <classifier>apis</classifier>
    <scope>provided</scope>
</dependency>
```

### 淘汰管理資源解析器{#phase-out-use-of-administrative-resource-resolver}的使用

透過`SlingRepository.loginAdministrative()`和`ResourceResolverFactory.getAdministrativeResourceResolver()`使用管理工作階段在AEM 6.0之前的程式碼基底中相當普遍。由於這些方法的存取範圍太廣，因此安全性原因已遭取代。 [在未來的Sling版本中，這些方法將遭到移除](https://sling.apache.org/documentation/the-sling-engine/service-authentication.html#deprecation-of-administrative-authentication)。強烈建議重構任何程式碼，以改用服務使用者。 有關服務用戶和[如何逐步淘汰管理會話的更多資訊，請參見此處](/help/sites-administering/security-service-users.md#how-to-phase-out-admin-sessions)。

### 查詢和Oak索引{#queries-and-oak-indexes}

在升級程式碼基底時，必須徹底測試程式碼基底中查詢的使用。 對於從Jackrabbit 2(6.0以上的AEM版本)升級的客戶，這點尤其重要，因為Oak不會自動為內容編列索引，且可能需要建立自訂索引。 如果從AEM 6.x版升級，現成可用的Oak索引定義可能已變更，且可能會影響現有查詢。

有幾種工具可用於分析和檢查查詢效能：

* [AEM索引工具](/help/sites-deploying/queries-and-indexing.md)

* [操作診斷工具 — 查詢效能](/help/sites-administering/operations-dashboard.md#diagnosis-tools)

* [橡木工具](https://oakutils.appspot.com/)。這是開放原始碼工具，不由Adobe維護。

### 傳統UI編寫{#classic-ui-authoring}

AEM 6.4仍提供傳統UI編寫功能，但已淘汰。 如需詳細資訊，請參閱[此處](/help/release-notes/deprecated-removed-features.md#pre-announcement-for-next-release)。 如果您的應用程式目前在傳統UI製作環境上執行，建議升級至AEM 6.4並繼續使用傳統UI。 接著，您就可以將移轉至觸控式UI的計畫為個別專案，以在數個開發週期中完成。 若要在AEM 6.4中使用傳統UI，需要將數個OSGi設定提交至程式碼基底。 有關如何配置的詳細資訊，請參閱[此處](/help/sites-administering/enable-classic-ui.md)。

>[!NOTE]
>
>若要協助您遠離傳統UI並運用最新的AEM技術，請考慮運用[AEM現代化工具](/help/sites-developing/modernization-tools.md)，讓您更輕鬆進行移轉。

## 與6.4儲存庫結構{#align-repository-structure}一致

為了讓升級更輕鬆，並確保配置在升級期間不會被覆蓋，6.4版中的儲存庫將重組，以將內容與配置分開。

因此，許多設定必須移至不再如過去般位於`/etc`下。 若要查看AEM 6.4更新版本中必須審查和滿足的完整存放庫重組問題，請參閱AEM 6.4](/help/sites-deploying/repository-restructuring.md)中的[存放庫重組。

## AEM自訂{#aem-customizations}

需要識別來源版本中AEM製作環境的所有自訂項目。 識別後，建議將每個自訂內容儲存在版本控制中，或至少儲存為內容套件的一部分。 所有自訂項目都應在生產升級前，於執行AEM目標版本的QA或測試環境中部署和驗證。

### 一般{#overlays-in-general}覆蓋

通常會使用/apps底下的其他節點覆蓋/libs下的節點和/或檔案，以將AEM擴充至現成可用的功能。 這些覆蓋應在版本控制中受到追蹤，並針對AEM的目標版本進行測試。 如果檔案（無論是JS、JSP、HTL）已覆蓋，建議您對已增強的功能留下註解，以便在目標版AEM上更輕鬆地進行回歸測試。 有關一般覆蓋的詳細資訊，請參閱[此處](/help/sites-developing/overlays.md)。 如需特定AEM覆蓋的指示，請參閱下方。

### 升級自訂搜尋Forms {#upgrading-custom-search-forms}

為了正常運作，自訂搜尋刻面在升級後需要進行一些手動調整。 如需詳細資訊，請參閱[升級自訂搜尋Forms](/help/sites-deploying/upgrading-custom-search-forms.md)。

### 資產UI自訂{#assets-ui-customizations}

>[!NOTE]
>
>只有從AEM 6.2以前的版本升級時，才需要此程式。

具有自訂Assets部署的執行個體需要準備以進行升級。 這是為了確保所有自訂內容都與新的6.4節點結構相容所需。

您可以執行下列動作，準備對Assets UI的自訂：

1. 在需要升級的執行個體上，前往`https://server:port/crx/de/index.jsp`開啟CRXDE Lite

1. 前往下列節點：

   * `/apps/dam/content`

1. 將內容節點更名為&#x200B;**content_backup**。 要執行此操作，請按一下右鍵窗口左側的瀏覽器窗格，然後選擇&#x200B;**更名**。

1. 重新命名節點後，在`/apps/dam`下建立名為&#x200B;**content**&#x200B;的新節點，並將其節點類型設定為&#x200B;**sling:Folder**。

1. 將&#x200B;**content_backup**&#x200B;的所有子節點移至新建立的內容節點。 要執行此操作，請按一下右鍵瀏覽器窗格中的每個子節點，然後選擇&#x200B;**Move**。

1. 刪除&#x200B;**content_backup**&#x200B;節點。

1. `/apps/dam`下方更新的節點類型`sling:Folder`應理想地保存到版本控制中，並與代碼庫一起部署，或至少備份為內容包。

### 產生現有資產的資產ID {#generating-asset-ids-for-existing-assets}

若要為現有資產產生資產ID，請在您升級AEM執行個體以執行AEM 6.4時升級資產。這是啟用[Assets Insights功能](/help/assets/touch-ui-asset-insights.md)的必要項目。 如需詳細資訊，請參閱[新增內嵌程式碼](/help/assets/touch-ui-using-page-tracker.md#adding-embed-code)。

若要升級資產，請在JMX主控台中設定「關聯資產ID」套件。 根據存放庫中的資產數量，`migrateAllAssets`可能需要很長時間。 我們的內部測試估計，TarMK上的12.5萬個資產大約需要1小時。

![1487758945977](assets/1487758945977.png)

如果您需要整個資產子集的資產ID，請使用`migrateAssetsAtPath` API。

對於所有其他用途，請使用`migrateAllAssets()` API。

### InDesign指令碼自定義{#indesign-script-customizations}

Adobe建議將自訂指令碼放在`/apps/settings/dam/indesign/scripts`位置。 有關InDesign指令碼自定義的詳細資訊，請參見[此處](/help/assets/indesign.md#configuring-the-aem-assets-workflow)。

### 恢復ContextHub配置{#recovering-contexthub-configurations}

ContextHub設定會受升級影響。 有關如何恢復現有ContextHub配置的說明，請在[此處](/help/sites-administering/contexthub-config.md#recovering-contexthub-configurations-after-upgrading)找到。

### 工作流自定義{#workflow-customizations}

通常會更新現成可用的修改工作流程，以新增或移除不需要的功能。 DAM更新資產工作流程是自訂的常見工作流程。 自訂實作所需的所有工作流程都應備份並儲存在版本控制項中，因為升級期間可能會加以覆寫。

### 可編輯的範本 {#editable-templates}

>[!NOTE]
>
>只有使用AEM 6.2的可編輯範本進行網站升級時，才需要執行此程式

AEM 6.2和6.3之間更改了可編輯模板的結構。如果您從6.2或更早版本升級，並且使用可編輯模板構建站點內容，則需要使用[響應式節點清理工具](https://github.com/Adobe-Marketing-Cloud/aem-sites-template-migration)。 此工具的用途是在&#x200B;_**升級後執行**_，以清理內容。 它需要同時在製作和發佈層級上執行。

### CUG實作變更{#cug-implementation-changes}

封閉使用者群組的實作已大幅變更，以解決舊版AEM的效能和可擴充性限制。 舊版CUG已於6.3中淘汰，而新實作僅支援觸控式UI。 如果您從6.2或更舊版本升級，則可在[此處](/help/sites-administering/closed-user-groups.md#upgrade-cug)找到要遷移到新CUG實作的說明。

## 測試過程{#testing-procedure}

應為測試升級準備全面的測試計畫。 必須先在較低的環境中測試升級的代碼庫和應用程式。 發現的任何錯誤都應以迭代方式修正，直到程式碼基底穩定為止，只有在此時才應升級較高層級的環境。

### 測試升級過程{#testing-the-upgrade-procedure}

應在開發和QA環境中測試此處概述的升級過程，如自訂執行手冊中所述（請參閱[規劃升級](/help/sites-deploying/upgrade-planning.md)）。 應重複升級過程，直到所有步驟都記錄在升級運行手冊中，並且升級過程順利。

### 實作測試區域{#implementation-test-areas-}

以下是任何AEM實作的重要區域，在環境升級並部署升級的程式碼基底後，應由您的測試計畫涵蓋。

<table> 
 <tbody> 
  <tr> 
   <td><strong>功能測試區</strong></td> 
   <td><strong>說明</strong></td> 
  </tr> 
  <tr> 
   <td>發佈的網站</td> 
   <td>透過Dispatcher在發佈層級<br />上測試AEM實作和相關的程式碼。 應包含頁面更新和<br />快取失效的條件。</td> 
  </tr> 
  <tr> 
   <td>製作</td> 
   <td>在製作層級上測試AEM實作和相關聯的程式碼。 應包含頁面、元件編寫和對話方塊。</td> 
  </tr> 
  <tr> 
   <td>與Marketing Cloud解決方案的整合</td> 
   <td>驗證與Analytics、DTM和Target等產品的整合。</td> 
  </tr> 
  <tr> 
   <td>與協力廠商系統的整合</td> 
   <td>任何第三方整合都應在製作和發佈層級上進行驗證。</td> 
  </tr> 
  <tr> 
   <td>驗證、安全性和權限</td> 
   <td>任何驗證機制（如LDAP/SAML）都應經過驗證。<br /> 權限和群組應同時在「作者」和「發佈者」上<br /> 測試。</td> 
  </tr> 
  <tr> 
   <td>查詢</td> 
   <td>應測試自訂索引和查詢以及查詢效能。</td> 
  </tr> 
  <tr> 
   <td>UI自訂</td> 
   <td>製作環境中AEM UI的任何擴充功能或自訂項目。</td> 
  </tr> 
  <tr> 
   <td>工作流程</td> 
   <td>自訂和/或現成可用的工作流程和功能。</td> 
  </tr> 
  <tr> 
   <td>效能測試</td> 
   <td>應同時在模擬實際情況的製作和發佈層級上執行負載測試。</td> 
  </tr> 
 </tbody> 
</table>

### 文檔測試計畫和結果{#document-test-plan-and-results}

應建立涵蓋上述實作測試區域的測試計畫。 在許多情況下，依「作者」和「發佈」任務清單來區隔測試計畫是有意義的。 升級生產環境之前，應先在開發、QA和預備環境上執行此測試計畫。 測試結果和效能量度應在較低環境中擷取，以便在升級預備和生產環境時提供比較。

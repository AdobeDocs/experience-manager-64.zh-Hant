---
title: 升級至 AEM 6.4 Forms
seo-title: 升級至 AEM 6.4 Forms
description: '您可以執行從6.1 AEMForms、AEM 6.2Forms和LiveCycleES4 SP1到AEM6.3Forms的直接升級。 '
seo-description: '您可以執行從6.1 AEMForms、AEM 6.2Forms和LiveCycleES4 SP1到AEM6.3Forms的直接升級。 '
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
role: 管理員
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1703'
ht-degree: 0%

---


# 升級AEM至JEE上的6.4Forms版{#upgrade-to-aem-forms-jee}

請根據您的環境，使用下列升級途徑之一。

## AEM JEE上的6.2Forms,AEM或JEE上的6.3Forms, AEM > JEE上的6.4Forms, {#aem-forms-jee-62-63-to-64}

執行下列程式，將JEE的AEM現有6.2Forms版或JEE的AEM6.3Forms版升級至AEMJEE的6.4Forms版：

1. 從&lt;AEMa0/>Adobe授權網站(LWS)](https://licensing.adobe.com/)下載JEE版6.4Forms安裝程式。 [您需要有效的維護與支援合約才能下載安裝程式。
1. 請參閱[升級檢查清單和planning](https://www.adobe.com/go/learn_aemfroms_upgrade_checklist_63)瞭解如何執行檢查以確保成功升級。
1. 請參閱[準備升級至AEM Forms](https://www.adobe.com/go/learn_aemforms_prepareupgrade_63)以瞭解並執行各項任務，確保在最短的伺服器停機時間內正確運行升級。
1. 根據您現有的環境和應用程式伺服器，選擇下列其中一份檔案並依照指示進行。

   * [針對JBossAEM從6.2或AEM6.3Forms升級AEM至6.4Forms](assets/upgrade-jboss.pdf)
   * [WebLogic從AEM6.2或AEM6.3Forms升級AEM至6.4Forms](assets/upgrade-weblogic.pdf)
   * [WebSphere從AEM6.2或AEM6.3Forms升級AEM至6.4Forms](assets/upgrade-websphere.pdf)
   * [從AEM6.2或AEM6.3Forms升級AEM至6.4Forms](assets/upgrade-turnkey.pdf)

## AEM JEE上的6.0FormsAEM > JEE上的6.3Forms{#aem-forms-jee-60-to-63}

不提供從LiveCycleES2、LiveCycleES3、AEM6.0Forms、AEM 6.1Forms到AEM6.4Forms的直接升級。 您可以執行LiveCycle或AEM Forms的一或多個版本的中級升級，然後從6.AEM4Forms升級。 有關中間版本和相應升級說明的清單，請參閱[選擇升級路徑](upgrade.md)。

## LiveCycleES4 SP1 > AEM 6.4FormsJEE {#livecycle-es4sp1-forms-jee}

在JEE上將LiveCycleES4 SP1升級至AEM6.4Forms是現場升級，因為它需要將資產和資料從舊版移轉至新的受支援應用程式伺服器、作業系統和資料庫執行個體（新版本）。

以下概述將現有LiveCycleES4 SP1伺服器升級到AEM6.4Forms的過程。 如需詳細指示，請參閱程式結束時列出的檔案。

1. 升級前：

   1. 從&lt;AEMa0/>Adobe授權網站(LWS)](https://licensing.adobe.com/)下載JEE版6.4Forms安裝程式。 [您需要有效的維護與支援合約才能下載安裝程式。
   1. 決定要使用的內容儲存庫（CRX儲存庫）類型。 只有少數AEM Forms的JEE功能使用內容儲存庫永續性來儲存內容和資產。 只有在您計畫在JEE功能上使用此類AEM Forms時，才安裝和配置內容儲存庫：

      * 在LiveCycleES4 SP1中，「通信管理」、「Forms門戶」、「HTML工作區」和「流程報告」功能使用「內容儲存庫」。 如果您未在LiveCycleES4中使用這些功能，並計畫不在AEM Forms使用這些功能，則不需要「內容儲存庫」。
      * 在AEM Forms、Forms、通信管理、HTML5Forms(在LiveCycleES4 SP1中稱為移動Forms)、Forms門戶、HTML工作區、流程報告、以Forms為中心的OSGi工作流，功能使用內容儲存庫。 如果您打算將AEM Forms用於這些功能，則需要「內容儲存庫」。
      * 您不需要Content Repository才能使用AEM FormsDocument Security。

      此外，LiveCycle和AEM Forms的儲存類型不同。 有關可用的儲存庫類型和相關資訊，請參閱[選擇AEM Forms安裝的持久性類型](/help/forms/using/choosing-persistence-type-for-aem-forms.md)。

   1. 建立LiveCycleES4 SP1內容和資料的備份：

      建立LiveCycleES4 SP1資料庫、全局資料儲存(GDS)和crx-repository（文檔安全性不需要）的備份。 如果您要升級至MongoMK或RDBMK永續性，請將LiveCycleES4 SP1對應管理資產匯出為。cmp檔案，並將資產形成為AEM套件。

   1. 確保JEE上的6.4Forms支援您現有的平台(即應用程式伺服器、資料庫、作業系統、Adobe Acrobat、協力廠商應用程式和硬AEM體)。 有關支援的硬體和軟體的資訊，請參閱[支援的平台組合](/help/forms/using/aem-forms-jee-supported-platforms.md)文檔。

      如果建立資料庫的新實例，請將步驟3中備份的資料導入資料庫。 有關如何將資料導入資料庫的資訊，請參見相應資料庫供應商的文檔。

      >[!NOTE]
      >
      >如果您使用RDBMK持久性格式，請為在JEE上在AEM Forms運行的儲存庫持久性和文檔服務使用單個資料庫。


1. 執行升級：

   1. 在新AEM伺服器上，通過運行安裝程式在JEE上安裝6.4Forms。 安裝程式會將所有必要檔案置於您的電腦上，並置於一個安裝目錄結構中。
   1. 安裝完成後，運行&#x200B;**Configuration Manager**&#x200B;以配置各種AEM Forms模組並設定適當的配置。 除了配置設定外，它還允許指定全局資料儲存(GDS)和crx-repository的路徑。

      >[!NOTE]
      >
      >在「升級任務選擇」螢幕上，選擇「從Adobe Experience Manager Forms6.2.0 ]**升級」選項。**[!UICONTROL **[!UICONTROL 從Adobe Experience Manager Forms6.2.0]**&#x200B;升級選項允許配置管理器從LiveCycleES4 SP1升級到FormsAEM6.4。

   1. (AEM Forms文檔安全模組不需要)將內容導入內容儲存庫(CRX-Repository)到AEM6.4Forms伺服器。

      >[!NOTE]
      >
      >* 升級crx-repository並遷移內容後，請更改管理員帳戶的密碼。 有關詳細說明，請參閱[更改現有用戶的密碼](/help/sites-administering/granite-user-group-admin.md)。


1. 執行部署後工作，以驗證登入認證、設定檔案服務、通訊管理、檔案安全性等，視您的使用案例而定。
1. 驗證伺服器是否升級成功：

   在升級的AEM Forms伺服器上執行一些例行操作，以確保伺服器升級成功。 您可以填寫並送出一些已轉換的表格，或保護檔案，以確保成功升級。

   >[!NOTE]
   >
   >在AEMForms6.4中，crx-repository的結構已經更改。 升級至AEM6.4表格後，請使用重新建立的變更路徑進行自訂。 有關更改路徑的完整清單，請參見[Forms6.4&lt;a1/AEM>中的資料庫重組。](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)

**根據您現有的環境和應用程式伺服器，選擇下列其中一份檔案，並依照詳細指示進行：**

* [從LiveCycleES4 SP1升級至AEM6.4FormsJBoss](assets/upgrade-jboss-livecycle.pdf)
* [從LiveCycleES4 SP1升級至AEM6.4FormsWebLogic](assets/upgrade-weblogic-livecycle.pdf)
* [從LiveCycleES4 SP1升級至AEM6.4FormsWebSphere](assets/upgrade-websphere-livecycle.pdf)
* [使用JBoss Tunkly從LiveCycleES4 SP1升級AEM到6.4Forms](assets/upgrade-turnkey-livecycle.pdf)

<!--Theses sections used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

## LiveCycleES3 > AEM 6.4FormsJEE {#livecycle-es3-forms-jee}

在JEE上將LiveCycleES3升級至AEM6.4Forms是現場升級，因為它需要將資產和資料從舊版移轉至新的受支援應用程式伺服器、作業系統和資料庫執行個體（新版本）。

以下是將現有LiveCycleES3伺服器升級到6.4FormsAEM的過程概述。 如需詳細指示，請參閱程式結束時列出的檔案。

1. 升級前：

   1. 從&lt;AEMa0/>Adobe授權網站(LWS)](https://licensing.adobe.com/)下載JEE版6.4Forms安裝程式。 [您需要有效的維護與支援合約才能下載安裝程式。
   1. 決定要使用的內容儲存庫（CRX儲存庫）類型。 只有少數AEM Forms的JEE功能使用內容儲存庫永續性來儲存內容和資產。 只有在您計畫在JEE功能上使用此類AEM Forms時，才安裝和配置內容儲存庫：

      * 在AEM Forms、Forms、通信管理、HTML5Forms、Forms門戶、HTML工作區、流程報告和以Forms為中心的OSGi功能工作流程中，使用內容儲存庫。 如果您打算將AEM Forms用於這些功能，則需要「內容儲存庫」。
      * 您不需要Content Repository才能使用AEM FormsDocument Security。

      此外，LiveCycle和AEM Forms的儲存類型不同。 有關可用的儲存庫類型和相關資訊，請參閱[選擇AEM Forms安裝的持久性類型](/help/forms/using/choosing-persistence-type-for-aem-forms.md)。

   1. 建立LiveCycleES3資料庫、全局資料儲存(GDS)和內容儲存庫的備份（文檔安全不需要）。 如果您要升級到MongoMK或RDBMK持久性，請將LiveCycleES3通信管理資產導出為存檔。
   1. 確保JEE上的6.4Forms支援您現有的平台(即應用程式伺服器、資料庫、作業系統、Adobe Acrobat、協力廠商應用程式和硬AEM體)。 有關支援的硬體和軟體的資訊，請參閱[支援的平台組合](/help/forms/using/aem-forms-jee-supported-platforms.md)文檔。

      如果建立資料庫的新實例，請將步驟3中備份的資料導入資料庫。 有關如何將資料導入資料庫的資訊，請參見相應資料庫供應商的文檔。

      >[!NOTE]
      >
      >如果您使用RDBMK持久性格式，請對在JEE上的AEM Forms上運行的儲存庫持久性和文檔服務使用單個資料庫。


1. 執行升級：

   1. 在新AEM伺服器上，通過運行安裝程式在JEE上安裝6.4Forms。 安裝程式會將所有必要檔案置於您的電腦上，並置於一個安裝目錄結構中。
   1. 安裝完成後，運行&#x200B;**Configuration Manager**&#x200B;以配置各種AEM Forms模組並設定適當的配置。 除了配置設定外，它還允許指定全局資料儲存(GDS)和crx-repository的路徑。

      >[!NOTE]
      >
      >在「升級任務選擇」螢幕上，選擇「從Adobe Experience Manager Forms6.2.0 ]**升級」選項。**[!UICONTROL **[!UICONTROL 從Adobe Experience Manager Forms6.2.0]**&#x200B;升級選項允許配置管理器從LiveCycleES3升級AEM到6.4Forms。

   1. (AEM Forms文檔安全模組不需要)升級CRX儲存庫並將其導入AEM到6.4Forms伺服器。

      >[!NOTE]
      >
      >升級crx-repository並遷移內容後，請更改管理員帳戶的密碼。 有關詳細說明，請參閱[更改現有用戶的密碼](/help/sites-administering/granite-user-group-admin.md)。
1. 執行部署後工作，以驗證登入認證、設定檔案服務、通訊管理、檔案安全性等，視您的使用案例而定。
1. 驗證伺服器是否升級成功：

   在升級的AEM Forms伺服器上執行一些例行操作，以確保伺服器升級成功。 您可以填寫並送出一些已轉換的表格，或保護檔案，以確保成功升級。

   >[!NOTE]
   >
   >在AEMForms6.4中，crx-repository的結構已經更改。 升級至AEM6.4表格後，請使用重新建立的變更路徑進行自訂。 有關更改路徑的完整清單，請參見[Forms6.4&lt;a1/AEM>中的資料庫重組。](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)

**根據您現有的環境和應用程式伺服器，選擇下列其中一份檔案，並依照詳細指示進行：**

* [針對JBoss從LiveCycleES3升AEM級到6.4Forms](assets/upgrade-jboss-livecycle-es3.pdf)
* [從LiveCycleES3升級至AEM6.4FormsWebLogic](assets/upgrade-weblogic-livecycle-es3.pdf)
* [從LiveCycleES3升級至AEM6.4FormsWebSphere](assets/upgrade-websphere-livecycle-es3.pdf)
* [使用JBoss Tunkly從LiveCycleES3升級AEM到6.4Forms](assets/upgrade-turnkey-livecycle-es3.pdf)

---
title: 升級至AEM 6.4 Forms
seo-title: 升級至AEM 6.4 Forms
description: '您可以從AEM 6.1 Forms、AEM 6.2 Forms和LiveCycle ES4 SP1直接升級至AEM 6.3 Forms。 '
seo-description: '您可以從AEM 6.1 Forms、AEM 6.2 Forms和LiveCycle ES4 SP1直接升級至AEM 6.3 Forms。 '
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
translation-type: tm+mt
source-git-commit: ffa45c8fa98e1ebadd656ea58e4657b669ddd830
workflow-type: tm+mt
source-wordcount: '1702'
ht-degree: 0%

---


# 升級至JEE上的AEM 6.4 Forms {#upgrade-to-aem-forms-jee}

請根據您的環境，使用下列升級途徑之一。

## AEM 6.2 Forms on JEE，或AEM 6.3 Forms on JEE > AEM 6.4 Forms on JEE {#aem-forms-jee-62-63-to-64}

請執行下列程式，將JEE上的現有AEM 6.2 Forms或JEE上的AEM 6.3 Forms升級至JEE上的AEM 6.4 Forms:

1. 從[Adobe授權網站(LWS)](https://licensing.adobe.com/)下載AEM 6.4 Forms on JEE安裝程式。 您需要有效的維護與支援合約才能下載安裝程式。
1. 請參閱[升級檢查清單和planning](https://www.adobe.com/go/learn_aemfroms_upgrade_checklist_63)瞭解如何執行檢查以確保成功升級。
1. 請參閱[準備升級至AEM Forms](https://www.adobe.com/go/learn_aemforms_prepareupgrade_63)以學習並執行各項工作，確保在伺服器停機時間最短的情況下正確執行升級。
1. 根據您現有的環境和應用程式伺服器，選擇下列其中一份檔案並依照指示進行。

   * [從AEM 6.2或AEM 6.3 Forms升級至AEM 6.4 Forms for JBoss](assets/upgrade-jboss.pdf)
   * [從AEM 6.2或AEM 6.3 Forms升級至AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic.pdf)
   * [從AEM 6.2或AEM 6.3 Forms升級至AEM 6.4 Forms for WebSphere](assets/upgrade-websphere.pdf)
   * [從AEM 6.2或AEM 6.3 Forms升級至AEM 6.4 Forms for JBoss Tunkly](assets/upgrade-turnkey.pdf)

## AEM 6.0 Forms on JEE > AEM 6.3 Forms on JEE {#aem-forms-jee-60-to-63}

目前不提供從LiveCycle ES2、LiveCycle ES3、AEM 6.0 Forms、AEM 6.1 Forms直接升級至AEM 6.4 Forms的功能。 您可以執行一或多個LiveCycle或AEM Forms版本的中階升級，然後從AEM 6.4 Forms升級。 有關中間版本和相應升級說明的清單，請參閱[選擇升級路徑](upgrade.md)。

## LiveCycle ES4 SP1 > AEM 6.4 Forms on JEE {#livecycle-es4sp1-forms-jee}

將LiveCycle ES4 SP1升級至JEE上的AEM 6.4 Forms是現場升級，因為它需要將資產和資料從舊版移轉至支援應用程式伺服器、作業系統和資料庫的新執行個體（新版本）。

以下是將現有LiveCycle ES4 SP1伺服器升級至AEM 6.4 Forms的程式概觀。 如需詳細指示，請參閱程式結束時列出的檔案。

1. 升級前：

   1. 從[Adobe授權網站(LWS)](https://licensing.adobe.com/)下載AEM 6.4 Forms on JEE安裝程式。 您需要有效的維護與支援合約才能下載安裝程式。
   1. 決定要使用的內容儲存庫（CRX儲存庫）類型。 只有少數AEM Forms on JEE功能會使用「內容儲存庫」永續性來儲存內容和資產。 只有當您打算在JEE功能上使用此類AEM Forms時，才安裝和設定內容儲存庫：

      * 在LiveCycle ES4 SP1中，「對應管理」、「表單入口網站」、「HTML工作區」和「流程報表」功能都使用「內容儲存庫」。 如果您未在LiveCycle ES4中使用這些功能，並打算不在AEM Forms中使用這些功能，則不需要「內容儲存庫」。
      * 在AEM Forms、Adaptive Forms、Correponsement Management、HTML5 Forms（在LiveCycle ES4 SP1中稱為Mobile Forms）、Forms Portal、HTML Workspace、Process Reporting、OSGi上以表單為中心的工作流程中，功能使用內容儲存庫。 如果您打算針對這些功能使用AEM Forms，則需要「內容儲存庫」。
      * AEM Forms Document Security不需要Content Repository。

      此外，LiveCycle和AEM Forms的儲存庫類型不同。 如需可用的儲存庫類型和相關資訊，請參閱[選擇AEM Forms安裝的永續性類型](/help/forms/using/choosing-persistence-type-for-aem-forms.md)。

   1. 建立LiveCycle ES4 SP1內容與資料的備份：

      建立LiveCycle ES4 SP1資料庫、全域資料儲存(GDS)和crx-repository（檔案安全性不需要）的備份。 如果您要升級至MongoMK或RDBMK永續性，請將LiveCycle ES4 SP1對應管理資產匯出為。cmp檔案，並將資產表單為AEM套件。

   1. 確保JEE上的AEM 6.4 Forms支援您現有的平台（即應用程式伺服器、資料庫、作業系統、Adobe Acrobat、協力廠商應用程式和硬體）。 有關支援的硬體和軟體的資訊，請參閱[支援的平台組合](/help/forms/using/aem-forms-jee-supported-platforms.md)文檔。

      如果建立資料庫的新實例，請將步驟3中備份的資料導入資料庫。 有關如何將資料導入資料庫的資訊，請參見相應資料庫供應商的文檔。

      >[!NOTE]
      >
      >如果您使用RDBMK永續性格式，請針對在JEE上的AEM Forms上執行的儲存庫永續性和檔案服務使用單一資料庫。


1. 執行升級：

   1. 執行安裝程式，將AEM 6.4 Forms安裝在新伺服器上的JEE上。 安裝程式會將所有必要檔案置於您的電腦上，並置於一個安裝目錄結構中。
   1. 安裝完成後，請執行&#x200B;**Configuration Manager**&#x200B;以設定各種AEM Forms模組並設定適當的組態。 除了配置設定外，它還允許指定全局資料儲存(GDS)和crx-repository的路徑。

      >[!NOTE]
      >
      >在「升級任務選擇」螢幕上，選擇「從Adobe Experience Manager Forms 6.2.0 **[!UICONTROL 升級」選項。]****[!UICONTROL 從Adobe Experience Manager Forms 6.2.0]**&#x200B;升級選項可讓組態管理員從LiveCycle ES4 SP1升級至AEM 6.4 Forms。

   1. （AEM Forms檔案安全性模組不需要）將內容匯入內容存放庫(CRX-Repository)至AEM 6.4 Forms伺服器。

      >[!NOTE]
      >
      >* 升級crx-repository並遷移內容後，請更改管理員帳戶的密碼。 有關詳細說明，請參閱[更改現有用戶的密碼](/help/sites-administering/granite-user-group-admin.md)。


1. 執行部署後工作，以驗證登入認證、設定檔案服務、通訊管理、檔案安全性等，視您的使用案例而定。
1. 驗證伺服器是否升級成功：

   在已升級的AEM Forms伺服器上執行幾項例行作業，以確保伺服器已成功升級。 您可以填寫並送出一些已轉換的表格，或保護檔案，以確保成功升級。

   >[!NOTE]
   >
   >在AEM 6.4 Forms中，crx-repository的結構已變更。 升級至AEM 6.4表單後，請使用您重新建立的自訂變更路徑。 如需已變更路徑的完整清單，請參閱「AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)中的[ Forms Repository Restructing」。

**根據您現有的環境和應用程式伺服器，選擇下列其中一份檔案，並依照詳細指示進行：**

* [從LiveCycle ES4 SP1升級至AEM 6.4 Forms for JBoss](assets/upgrade-jboss-livecycle.pdf)
* [從LiveCycle ES4 SP1升級至AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic-livecycle.pdf)
* [從LiveCycle ES4 SP1升級至AEM 6.4 Forms for WebSphere](assets/upgrade-websphere-livecycle.pdf)
* [使用JBoss Tunklyek從LiveCycle ES4 SP1升級至AEM 6.4 Forms](assets/upgrade-turnkey-livecycle.pdf)

<!--Theses sections used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

## LiveCycle ES3 > AEM 6.4 Forms on JEE {#livecycle-es3-forms-jee}

將LiveCycle ES3升級至JEE上的AEM 6.4 Forms是現場升級，因為它需要將資產和資料從舊版移轉至支援應用程式伺服器、作業系統和資料庫的新執行個體（新版本）。

以下是將現有LiveCycle ES3伺服器升級為AEM 6.4 Forms的程式概觀。 如需詳細指示，請參閱程式結束時列出的檔案。

1. 升級前：

   1. 從[Adobe授權網站(LWS)](https://licensing.adobe.com/)下載AEM 6.4 Forms on JEE安裝程式。 您需要有效的維護與支援合約才能下載安裝程式。
   1. 決定要使用的內容儲存庫（CRX儲存庫）類型。 只有少數AEM Forms on JEE功能會使用「內容儲存庫」永續性來儲存內容和資產。 只有當您打算在JEE功能上使用此類AEM Forms時，才安裝和設定內容儲存庫：

      * 在AEM Forms、Adaptive Forms、Correponsement Management、HTML5 Forms、Forms Portal、HTML Workspace、Process Reporting和以Forms為中心的OSGi功能工作流程中，使用「內容儲存庫」。 如果您打算針對這些功能使用AEM Forms，則需要「內容儲存庫」。
      * AEM Forms Document Security不需要Content Repository。

      此外，LiveCycle和AEM Forms的儲存庫類型不同。 如需可用的儲存庫類型和相關資訊，請參閱[選擇AEM Forms安裝的永續性類型](/help/forms/using/choosing-persistence-type-for-aem-forms.md)。

   1. 建立LiveCycle ES3資料庫、全域資料儲存(GDS)和內容儲存庫（檔案安全性不需要）的備份。 如果您要升級至MongoMK或RDBMK永續性，請將LiveCycle ES3對應管理資產匯出為封存。
   1. 確保JEE上的AEM 6.4 Forms支援您現有的平台（即應用程式伺服器、資料庫、作業系統、Adobe Acrobat、協力廠商應用程式和硬體）。 有關支援的硬體和軟體的資訊，請參閱[支援的平台組合](/help/forms/using/aem-forms-jee-supported-platforms.md)文檔。

      如果建立資料庫的新實例，請將步驟3中備份的資料導入資料庫。 有關如何將資料導入資料庫的資訊，請參見相應資料庫供應商的文檔。

      >[!NOTE]
      >
      >如果您使用RDBMK永續性格式，請針對在JEE上的AEM Forms上執行的儲存庫永續性和檔案服務使用單一資料庫。


1. 執行升級：

   1. 執行安裝程式，將AEM 6.4 Forms安裝在新伺服器上的JEE上。 安裝程式會將所有必要檔案置於您的電腦上，並置於一個安裝目錄結構中。
   1. 安裝完成後，請執行&#x200B;**Configuration Manager**&#x200B;以設定各種AEM Forms模組並設定適當的組態。 除了配置設定外，它還允許指定全局資料儲存(GDS)和crx-repository的路徑。

      >[!NOTE]
      >
      >在「升級任務選擇」螢幕上，選擇「從Adobe Experience Manager Forms 6.2.0 **[!UICONTROL 升級」選項。]****[!UICONTROL 從Adobe Experience Manager Forms 6.2.0]**&#x200B;升級選項可讓組態管理員從LiveCycle ES3升級至AEM 6.4 Forms。

   1. （AEM Forms檔案安全性模組不需要）升級並將CRX儲存庫匯入AEM 6.4 Forms伺服器。

      >[!NOTE]
      >
      >升級crx-repository並遷移內容後，請更改管理員帳戶的密碼。 有關詳細說明，請參閱[更改現有用戶的密碼](/help/sites-administering/granite-user-group-admin.md)。
1. 執行部署後工作，以驗證登入認證、設定檔案服務、通訊管理、檔案安全性等，視您的使用案例而定。
1. 驗證伺服器是否升級成功：

   在已升級的AEM Forms伺服器上執行幾項例行作業，以確保伺服器已成功升級。 您可以填寫並送出一些已轉換的表格，或保護檔案，以確保成功升級。

   >[!NOTE]
   >
   >在AEM 6.4 Forms中，crx-repository的結構已變更。 升級至AEM 6.4表單後，請使用您重新建立的自訂變更路徑。 如需已變更路徑的完整清單，請參閱「AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)中的[ Forms Repository Restructing」。

**根據您現有的環境和應用程式伺服器，選擇下列其中一份檔案，並依照詳細指示進行：**

* [從LiveCycle ES3升級至AEM 6.4 Forms for JBoss](assets/upgrade-jboss-livecycle-es3.pdf)
* [從LiveCycle ES3升級至AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic-livecycle-es3.pdf)
* [從LiveCycle ES3升級至AEM 6.4 Forms for WebSphere](assets/upgrade-websphere-livecycle-es3.pdf)
* [使用JBoss Tunklyek從LiveCycle ES3升級至AEM 6.4 Forms](assets/upgrade-turnkey-livecycle-es3.pdf)
